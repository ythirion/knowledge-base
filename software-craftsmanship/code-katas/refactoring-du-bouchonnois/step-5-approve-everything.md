# Step 5 : "Approve Everything"

Il y a quelques tests pour lesquels nous avons énormément de lignes d'assertions. Nous allons les retravailler afin de les transformer en `Approval Tests`.

* Prendre du temps pour comprendre ce qui se cache derrière cette notion d'[Approval Testing](https://github.com/ythirion/approval-testing-kata#2-approval-testing)
* Identifier des tests sur lesquels on pourrait utiliser cette technique
* Refactorer un test existant en utilisant la librairie [Verify](https://github.com/VerifyTests/Verify)

<figure><img src="../../../.gitbook/assets/step5.webp" alt=""><figcaption><p>Step 5 : "Approve Everything"</p></figcaption></figure>

### Identification des tests

On pourrait utiliser cette technique pour les tests suivants :

* `DemarrerUnePartieDeChasse.AvecPlusieursChasseurs`
  * Limitera les asserts à une seule ligne
  * Moins de maintenance et assertions plus lisibles
* `ConsulterStatus` : `QuandLaPartieVientDeDémarrer` / `QuandLaPartieEstTerminée`
* `ScenarioTests.DéroulerUnePartie`
  * On valide le contenu d'un `string`
  * Cela évitera de stocker ce string dans le code (sera stocké sous forme de ressource)

### Refactorer `ScenarioTests.DéroulerUnePartie`

* On commence par ajouter la dépendance sur notre librairie d'Approval Testing

```shell
dotnet add package Verify.xUnit
```

* On peut ensuite extraire le contenu de l'assertion dans un fichier "Approved" ici "verified"
  * On crée un fichier appelé : `ScenarioTests.DéroulerUnePartie.verified.txt` (`[Nom de la classe de tests].[Nom du test].verified.txt`)
  * C'est sur base de ce fichier que l'assertion se fera via `Verify`&#x20;

<figure><img src="../../../.gitbook/assets/approved-content.webp" alt=""><figcaption><p>Approved Content</p></figcaption></figure>

* On transforme le test en `Approval Test` en
  * Ajoutant l'annotation `UsesVerify` sur la classe de test
  * Changeant la méthode de test pour que celle-ci renvoie une `Task`

```csharp
[UsesVerify]
public class ScenarioTests
{
    [Fact]
    public Task DéroulerUnePartie()
    {
        var time = new DateTime(2024, 4, 25, 9, 0, 0);
        var repository = new PartieDeChasseRepositoryForTests();
        var service = new PartieDeChasseService(repository, () => time);
        var chasseurs = new List<(string, int)>
        {
            ("Dédé", 20),
            ("Bernard", 8),
            ("Robert", 12)
        };
        var terrainDeChasse = ("Pitibon sur Sauldre", 4);
        var id = service.Demarrer(
            terrainDeChasse,
            chasseurs
        );

        time = time.Add(TimeSpan.FromMinutes(10));
        service.Tirer(id, "Dédé");

        time = time.Add(TimeSpan.FromMinutes(30));
        service.TirerSurUneGalinette(id, "Robert");

        time = time.Add(TimeSpan.FromMinutes(20));
        service.PrendreLapéro(id);

        time = time.Add(TimeSpan.FromHours(1));
        service.ReprendreLaPartie(id);

        time = time.Add(TimeSpan.FromMinutes(2));
        service.Tirer(id, "Bernard");

        time = time.Add(TimeSpan.FromMinutes(1));
        service.Tirer(id, "Bernard");

        time = time.Add(TimeSpan.FromMinutes(1));
        service.TirerSurUneGalinette(id, "Dédé");

        time = time.Add(TimeSpan.FromMinutes(26));
        service.TirerSurUneGalinette(id, "Robert");

        time = time.Add(TimeSpan.FromMinutes(10));
        service.PrendreLapéro(id);

        time = time.Add(TimeSpan.FromMinutes(170));
        service.ReprendreLaPartie(id);

        time = time.Add(TimeSpan.FromMinutes(11));
        service.Tirer(id, "Bernard");

        time = time.Add(TimeSpan.FromSeconds(1));
        service.Tirer(id, "Bernard");

        time = time.Add(TimeSpan.FromSeconds(1));
        service.Tirer(id, "Bernard");

        time = time.Add(TimeSpan.FromSeconds(1));
        service.Tirer(id, "Bernard");

        time = time.Add(TimeSpan.FromSeconds(1));
        service.Tirer(id, "Bernard");

        time = time.Add(TimeSpan.FromSeconds(1));
        service.Tirer(id, "Bernard");

        time = time.Add(TimeSpan.FromSeconds(1));

        try
        {
            service.Tirer(id, "Bernard");
        }
        catch (TasPlusDeBallesMonVieuxChasseALaMain)
        {
        }

        time = time.Add(TimeSpan.FromMinutes(19));
        service.TirerSurUneGalinette(id, "Robert");

        time = time.Add(TimeSpan.FromMinutes(30));
        service.TerminerLaPartie(id);

        // retourne le résultat de la méthode `Verify`
        return Verify(service.ConsulterStatus(id));
    }
}
```

> Le test passe du premier coup 👌

On va faire en sorte de le faire passer au rouge : `ne jamais croire un test qu'on a pas vu échouer`...

Pour cela le plus simple est de changer le fichier `verified`.

Notre `Approval Test` échoue, notre outil de comparaison de fichier va s'ouvrir :&#x20;

<figure><img src="../../../.gitbook/assets/compare-files.webp" alt=""><figcaption><p>Comparaison de fichiers</p></figcaption></figure>

Dès lors nous avons une arborescence de fichiers ressemblant à celà :&#x20;

<figure><img src="../../../.gitbook/assets/files.webp" alt=""><figcaption><p>Files</p></figcaption></figure>

Un élément important quand on utilise une librairie de ce genre, ajouter les fichiers `received` dans le fichier `.gitignore` :

```
# Verify
*.received.txt
```

Félicitations, notre premier test passe et on peut se fier à lui.



En revanche, le test n'est pas très lisible / maintenable :

* Beaucoup de duplication
* `try / catch` vide
* Méthode de plus de `80 loc`

On va y appliquer la fameuse [règle du boyscout](https://deviq.com/principles/boy-scout-rule).&#x20;

<figure><img src="../../../.gitbook/assets/boy-scout-rule.webp" alt="" width="375"><figcaption></figcaption></figure>

### Boy Scout Rule

* On commence par extraire des champs à partir du test via notre `IDE`&#x20;

<figure><img src="../../../.gitbook/assets/introduce-field.webp" alt=""><figcaption><p>Introduce field</p></figcaption></figure>

* Puis on configure l'extraction

<figure><img src="../../../.gitbook/assets/introduce-field-refactoring.webp" alt=""><figcaption><p>Configurer "Introduce Field"</p></figcaption></figure>

* Le résultat est :

```csharp
public class ScenarioTests
{
    private DateTime _time = new(2024, 4, 25, 9, 0, 0);
    private readonly PartieDeChasseService _service;

    public ScenarioTests()
    {
        _service = new PartieDeChasseService(
            new PartieDeChasseRepositoryForTests(),
            () => _time
        );
    }
    ....
}
```

* On va utiliser le `CommandBuilder` également
  * Afin de supprimer les `string` hardcodés

```csharp
var command = DémarrerUnePartieDeChasse()
    .Avec(("Dédé", 20), ("Bernard", 8), ("Robert", 12))
    .SurUnTerrainRicheEnGalinettes(4);

var id = _service.Demarrer(
    command.Terrain,
    command.Chasseurs
);
```

* On va ensuite supprimer la duplication en faisant une extraction des constantes : `Bernard`, `Robert`, `Dédé`, `ChasseurInconnu`
  * Pour pouvoir les utiliser dans cette classe de test également
  * On les place dans un fichier `Data`

<figure><img src="../../../.gitbook/assets/move-type.webp" alt=""><figcaption><p>Move to &#x3C;type></p></figcaption></figure>

* Notre test ressemble désormais à cela

```csharp
[Fact]
public Task DéroulerUnePartie()
{
    var command = DémarrerUnePartieDeChasse()
        .Avec((Data.Dédé, 20), (Data.Bernard, 8), (Data.Robert, 12))
        .SurUnTerrainRicheEnGalinettes(4);

    var id = _service.Demarrer(
        command.Terrain,
        command.Chasseurs
    );

    _time = _time.Add(TimeSpan.FromMinutes(10));
    _service.Tirer(id, Data.Dédé);

    _time = _time.Add(TimeSpan.FromMinutes(30));
    _service.TirerSurUneGalinette(id, Data.Robert);
    
    ....
}
```

* On va extraire une méthode à partir de cela en identifiant les similitudes et différences

```csharp
// Ajoute du temps à _time
_time = _time.Add(TimeSpan.FromMinutes(30));
// Appelle d'une méthode sur le service
_service.TirerSurUneGalinette(id, Data.Robert);

// Ajoute du temps à _time
_time = _time.Add(TimeSpan.FromMinutes(20));
// Appelle d'une méthode sur le service
_service.PrendreLapéro(id);
```

* On prépare notre `extraction` en décomposant le code ci-dessus en :

```csharp
// Extract variable
var timeToAdd = TimeSpan.FromMinutes(10);
// Refactor l'appelle en Action
var act = () => _service.Tirer(id, Data.Dédé);

_time = _time.Add(timeToAdd);
act();
```

* Extraction de la méthode

<figure><img src="../../../.gitbook/assets/extract-method.webp" alt=""><figcaption><p>Extract method</p></figcaption></figure>

* Puis on configure l'extraction

<figure><img src="../../../.gitbook/assets/configure-extract (2).webp" alt=""><figcaption><p>Configure "Extract Method"</p></figcaption></figure>

* On l'utilise partout en s'assurant que notre test reste vert
  * En rendant également `safe` l'appelle à la méthode `act`

```csharp
[UsesVerify]
public class ScenarioTests
{
    private DateTime _time = new(2024, 4, 25, 9, 0, 0);
    private readonly PartieDeChasseService _service;

    public ScenarioTests()
    {
        _service = new PartieDeChasseService(
            new PartieDeChasseRepositoryForTests(),
            () => _time
        );
    }

    [Fact]
    public Task DéroulerUnePartie()
    {
        var command = DémarrerUnePartieDeChasse()
            .Avec((Data.Dédé, 20), (Data.Bernard, 8), (Data.Robert, 12))
            .SurUnTerrainRicheEnGalinettes(4);

        var id = _service.Demarrer(
            command.Terrain,
            command.Chasseurs
        );

        After(10.Minutes(), () => _service.Tirer(id, Data.Dédé));
        After(30.Minutes(), () => _service.TirerSurUneGalinette(id, Data.Robert));
        After(20.Minutes(), () => _service.PrendreLapéro(id));
        After(1.Hours(), () => _service.ReprendreLaPartie(id));
        After(2.Minutes(), () => _service.Tirer(id, Data.Bernard));
        After(1.Minutes(), () => _service.Tirer(id, Data.Bernard));
        After(1.Minutes(), () => _service.TirerSurUneGalinette(id, Data.Dédé));
        After(26.Minutes(), () => _service.TirerSurUneGalinette(id, Data.Robert));
        After(10.Minutes(), () => _service.PrendreLapéro(id));
        After(170.Minutes(), () => _service.ReprendreLaPartie(id));
        After(11.Minutes(), () => _service.Tirer(id, Data.Bernard));
        After(1.Seconds(), () => _service.Tirer(id, Data.Bernard));
        After(1.Seconds(), () => _service.Tirer(id, Data.Bernard));
        After(1.Seconds(), () => _service.Tirer(id, Data.Bernard));
        After(1.Seconds(), () => _service.Tirer(id, Data.Bernard));
        After(1.Seconds(), () => _service.Tirer(id, Data.Bernard));
        After(1.Seconds(), () => _service.Tirer(id, Data.Bernard));
        After(19.Minutes(), () => _service.TirerSurUneGalinette(id, Data.Robert));
        After(30.Minutes(), () => _service.TerminerLaPartie(id));

        return Verify(_service.ConsulterStatus(id));
    }

    private void After(TimeSpan time, Action act)
    {
        _time = _time.Add(time);
        try
        {
            act();
        }
        catch
        {
            // ignored
        }
    }
}
```

## Refactorer `DemarrerUnePartieDeChasse.AvecPlusieursChasseurs`

* On commence par changer le test
  * Ici on va "approuver" la représentation textuelle de la `PartieDeChasse`

```csharp
[Fact]
public Task AvecPlusieursChasseurs()
{
    var command = DémarrerUnePartieDeChasse()
        .Avec((Data.Dédé, 20), (Data.Bernard, 8), (Data.Robert, 12))
        .SurUnTerrainRicheEnGalinettes();

    PartieDeChasseService.Demarrer(
        command.Terrain,
        command.Chasseurs
    );

    return Verify(Repository.SavedPartieDeChasse());
}
```

* Voici le résultat
  * Par défaut, `Verify` va scrubber les donées non déterministes (`DateTime` et `Guid` ici)

<figure><img src="../../../.gitbook/assets/verify-scrubbed-data.webp" alt=""><figcaption><p>Scrubbed data</p></figcaption></figure>

* Concernant la date, on perd 1 assertion faites dans le test avant refactoring
  * On change la configuration pour ce test

```csharp
[Fact]
public Task AvecPlusieursChasseurs()
{
    var command = DémarrerUnePartieDeChasse()
        .Avec((Data.Dédé, 20), (Data.Bernard, 8), (Data.Robert, 12))
        .SurUnTerrainRicheEnGalinettes();

    PartieDeChasseService.Demarrer(
        command.Terrain,
        command.Chasseurs
    );

    return Verify(Repository.SavedPartieDeChasse())
        // On précise qu'on ne veut pas "scubber" les DateTime
        .DontScrubDateTimes();
}
```

* On peut maintenant approver le résultat du test qui ressemble à cela

<figure><img src="../../../.gitbook/assets/verify-demarrer.webp" alt=""><figcaption><p>Verify démarrer</p></figcaption></figure>

## Impact du refactoring des tests

### Codescene

Après les refactorings des tests, on peut lancer une analyse `codescene` pour vérifier leur impact sur l'état de notre code base :&#x20;

<figure><img src="../../../.gitbook/assets/codescene-health.webp" alt=""><figcaption><p>Code health</p></figcaption></figure>

> Nous sommes passé d'une Code Health de 8,4 à 9,8 👌

Les hotspots ont changé de taille (rouges car les commits sont très récents)&#x20;

<figure><img src="../../../.gitbook/assets/codescene-hotspots.webp" alt=""><figcaption><p>Hotspots</p></figcaption></figure>

Il reste 1 `refactoring target` : `PartieDeChasseService`&#x20;

<figure><img src="../../../.gitbook/assets/codescene-refactoring-targets.webp" alt=""><figcaption><p>Refactoring target</p></figcaption></figure>

### SonarCloud

Rapport disponible [ici](https://sonarcloud.io/summary/overall?id=ythirion\_refactoring-du-bouchonnois\&branch=steps%2F05-approve-everything).

## Reflect

* Que pensez vous de cette technique ?
  * Quels autres cas d'utilisation pouvez-vous identifier ?
* Qu'est-ce que le `scrubbing` ?

<figure><img src="../../../.gitbook/assets/approved.webp" alt=""><figcaption></figcaption></figure>
