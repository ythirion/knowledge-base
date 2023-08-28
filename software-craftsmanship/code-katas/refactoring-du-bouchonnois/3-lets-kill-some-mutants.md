# Step 3 : Let's kill some mutants

Prendre quelques instants pour découvrir la page [`Mutation Testing`](https://xtrem-tdd.netlify.app/flavours/mutation-testing/).

Durant cette étape:

* Lancer [`stryker`](https://stryker-mutator.io/docs/stryker-net/introduction/)
  * Analyser les mutants survivants
* `Tuer` autant de mutants que possible (atteindre un score de mutation d'au moins 90%)

<figure><img src="../../../.gitbook/assets/step3.webp" alt=""><figcaption><p>Step 3 : Let's kill some mutants</p></figcaption></figure>

## Différents mutants

### [String mutation](https://stryker-mutator.io/docs/mutation-testing-elements/supported-mutators/#string-literal)

`Stryker` parvient à muter des `string` dans le code de production et ce changement n'est détecté par aucun test.

C'est le cas pour 2 classes : `ChasseurInconnu` et `PartieDeChasseService`.&#x20;

<figure><img src="../../../.gitbook/assets/string-mutation1.webp" alt="" width="375"><figcaption><p>String mutation 1</p></figcaption></figure>

<figure><img src="../../../.gitbook/assets/string-mutation2.webp" alt=""><figcaption><p>String mutation 2</p></figcaption></figure>

`Celà fait-il du sens de vérifier ce genre de strings depuis nos tests?`

### [Statement mutation](https://stryker-mutator.io/docs/mutation-testing-elements/supported-mutators/#string-literal)

`Stryker` parvient à supprimer certains blocs de code, tels que :

#### **Ajout d'événements dans l'aggrégat `PartieDeChasse`**

<figure><img src="../../../.gitbook/assets/statement-mutation1.webp" alt=""><figcaption><p>Statement mutation 1</p></figcaption></figure>

**Sauvegarde via repository**

<figure><img src="../../../.gitbook/assets/statement-mutation2.webp" alt=""><figcaption><p>Statement mutation 2</p></figcaption></figure>

### [Linq Mutation](https://stryker-mutator.io/docs/mutation-testing-elements/supported-mutators/#strykernet)

`Stryker` parvient à changer certaines expressions `LinQ`.

<figure><img src="../../../.gitbook/assets/linq-mutation.webp" alt=""><figcaption><p>LinQ mutation</p></figcaption></figure>

## `Tuer` les mutants

### **ChasseurInconnu**

On ajoute l'assertion du message `métier` dans les tests en repartant des tests listés dans le rapport de stryker:

```csharp
[Fact]
public void EchoueCarLeChasseurNestPasDansLaPartie()
{
    ...
    chasseurInconnuVeutTirer
        .Should()
        .Throw<ChasseurInconnu>()
        .WithMessage("Chasseur inconnu Chasseur inconnu");

    repository.SavedPartieDeChasse().Should().BeNull();
}
```

On peut alors relancer `stryker`, notre score de mutation passe de `79.03%` à `79.84%`... on a encore du boulot mais on avance.

### PartieDeChasseService

On doit ajouter la vérification d'événements et de sauvegarde de la partie de chasse dans nos tests.

```csharp
[Fact]
public void EchoueAvecUnChasseurNayantPlusDeBalles()
{
    ...
    var service = new PartieDeChasseService(repository, () => DateTime.Now);
    var tirerSansBalle = () => service.TirerSurUneGalinette(id, "Bernard");

    tirerSansBalle.Should().Throw<TasPlusDeBallesMonVieuxChasseALaMain>();
    repository.SavedPartieDeChasse()!
        .Events
        .Should()
        .HaveCount(1)
        .And
        .EndWith(new Event(new DateTime(),"Bernard veut tirer sur une galinette -> T'as plus de balles mon vieux, chasse à la main"));
}
```

:red\_circle: Nous avons un problème avec la gestion du temps ici...

```csharp
[Fact]
public void EchoueAvecUnChasseurNayantPlusDeBalles()
{
    var now = new DateTime(2024, 6, 6, 14, 50, 45);

    var service = new PartieDeChasseService(repository, () => now);
    var tirerSansBalle = () => service.TirerSurUneGalinette(id, "Bernard");

    tirerSansBalle.Should().Throw<TasPlusDeBallesMonVieuxChasseALaMain>();
    repository
        .SavedPartieDeChasse()!
        .Events
        .Should()
        .HaveCount(1)
        .And
        .EndWith(new Event(now,
            "Bernard veut tirer sur une galinette -> T'as plus de balles mon vieux, chasse à la main"));
}
```

:green\_circle: Nous changeons la manière dont on gère le temps dans ce test. Le score de mutation monte alors à `82.26%`.

On continue à tuer les autres mutants "similaires".

```csharp
[Fact]
public void EchoueSiLaPartieDeChasseEstTerminée()
{
    ...

    var now = new DateTime(2024, 6, 6, 14, 50, 45);
    var service = new PartieDeChasseService(repository, () => now);

    var tirerQuandTerminée = () => service.TirerSurUneGalinette(id, "Chasseur inconnu");

    tirerQuandTerminée.Should()
        .Throw<OnTirePasQuandLaPartieEstTerminée>();

    repository
        .SavedPartieDeChasse()!
        .Events
        .Should()
        .HaveCount(1)
        .And
        .EndWith(new Event(now, "Chasseur inconnu veut tirer -> On tire pas quand la partie est terminée"));
}
```

:blue\_circle: On a de la duplication dans les assertions, on en profite alors pour les mutualiser.

```csharp
public class PartieDeChasseServiceTests
{
    private static readonly DateTime Now = new(2024, 6, 6, 14, 50, 45);
    private static readonly Func<DateTime> TimeProvider = () => Now;

    private static void AssertLastEvent(PartieDeChasse partieDeChasse,
        string expectedMessage)
        => partieDeChasse.Events.Should()
            .HaveCount(1)
            .And
            .EndWith(new Event(Now, expectedMessage));
    
    ...
    
    [Fact]
    public void EchoueAvecUnChasseurNayantPlusDeBalles()
    {
        ...
        var service = new PartieDeChasseService(repository, TimeProvider);
        var tirerSansBalle = () => service.TirerSurUneGalinette(id, "Bernard");

        tirerSansBalle.Should().Throw<TasPlusDeBallesMonVieuxChasseALaMain>();
        AssertLastEvent(repository.SavedPartieDeChasse()!,
            "Bernard veut tirer sur une galinette -> T'as plus de balles mon vieux, chasse à la main");
    }
```

Après être repassé sur tous les tests et amélioré les assertions nous avons un score de mutation de `96.72%`.

### LinQ mutation

Ces mutations sont un peu particulières dans notre cas :

```csharp
// On vérifie que le chasseur existe
if (partieDeChasse.Chasseurs.Exists(c => c.Nom == chasseur))
{
    // L'utilisation de First est dès lors "safe"
    var chasseurQuiTire = partieDeChasse.Chasseurs.First(c => c.Nom == chasseur);
    ...
}
```

> De plus, en intégrant le mutant dans le code de production celui-ci ne compile plus...

On va changer le code de production afin de faire en sorte que ce mutant ne puisse plus être généré :

```csharp
if (partieDeChasse.Chasseurs.Exists(c => c.Nom == chasseur))
{
    var chasseurQuiTire = partieDeChasse.Chasseurs.Find(c => c.Nom == chasseur)!;
    ...
}
```

On répète la même stratégie pour les autres mutations jusqu'à atteindre `100%` en score de mutation 👍.

Nouveau rapport `SonarCloud` disponible [ici](https://sonarcloud.io/summary/overall?id=ythirion\_refactoring-du-bouchonnois\&branch=steps%2F03-kill-mutants).

## Reflect

Pour créer de bons tests, il est important de `toujours se concentrer sur l'écriture de bonnes assertions` et encore mieux développer en utilisant T.D.D.

Lorsqu'on écrit des tests (a priori ou posteriori), il est important d'avoir en tête certains principes tels que les [Test Desiderata](https://kentbeck.github.io/TestDesiderata/).

<figure><img src="../../../.gitbook/assets/kill-mutants.webp" alt="" width="199"><figcaption></figcaption></figure>
