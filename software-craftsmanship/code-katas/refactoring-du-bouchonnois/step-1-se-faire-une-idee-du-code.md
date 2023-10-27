# 1) Se faire une idée du code

Imagine que tu dois reprendre la maintenance évolutive du système de gestion des parties de chasse de nos chers chasseurs du bouchonnois.

Afin de te faire un premier feeling sur le code, on va analyser certains éléments factuels.

<figure><img src="../../../.gitbook/assets/step1.webp" alt=""><figcaption><p>Step 1 - se faire une idée de la code base</p></figcaption></figure>

## Check-list

On dresse une check-list de choses à vérifier / analyser :

* [ ] Compiler afin de valider qu'on est en capacité de compiler / exécuter le code
  * Analyser les potentiels `Warning` à la compilation
* [ ] Analyser la structure de la solution afin de comprendre l'architecture en place
* [ ] Regarder quels packages sont référencés afin de comprendre les interactions potentielles du système

### Récolter des metrics

Nos outils et l'écosystème de développement nous permettent de récolter rapidement des metrics permettant d'observer de manière assez factuelle la qualité du code :

* [ ] Récupérer le `code coverage`
* [ ] Mettre en place un outil d'analyse static de code
* [ ] Utiliser un Linter
* [ ] Identifier s'il y a des [`hotspots`](https://understandlegacycode.com/blog/focus-refactoring-with-hotspots-analysis/) et où ils sont localisés
* [ ] Revue de la qualité des tests

## Compiler

Lancer une première compilation afin d'identifier de potentiels problèmes.&#x20;

<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption><p>Première compilation...</p></figcaption></figure>

On a déjà une première boucle de feedback de la part de notre compilateur nous indiquant que certains `fields` sont déclarés comme `non-nullable` mais pas initialisés.

## Analyser la structure

La structure d'une solution / projet est un indicateur de l'architecture sous-jacente. L'observer nous permet de comprendre a minima le design du système.

Pour en savoir plus : [Screaming Architecture](https://blog.cleancoder.com/uncle-bob/2011/09/30/Screaming-Architecture.html).

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt="" width="350"><figcaption><p>Arborescence du projet</p></figcaption></figure>

Ici on peut tout de suite comprendre plusieurs éléments :

* Bonne nouvelle !!! la solution comprend des tests automatisés
* Le projet `Bouchonnois` semble être organisé autour d'un `Domain Model`
  * Une abstraction de repository semble servir de `port`
  * Le service `PartieDeChasseService` doit être le point d'entrée du système
  * Que fait la classe `Terrain` dans le répertoir `Service` ?
* Il y a une gestion d'Exceptions métiers et non pas des exceptions génériques

## Analyser les références

On jette un oeil sur les packages référencés afin de comprendre si le système intéragit avec d'autres systèmes (via gRPC, REST API, Integration Bus, Cloud Services, ...)

<img src="../../../.gitbook/assets/image (2).png" alt="" data-size="original">

A part les références au framework, aucune dépendance n'est "exotique". Les seuls packages utilisés sont ceux pour les tests.

## Code Coverage

#### Via Rider

On lance nos tests en activant le `code coverage`:&#x20;

<figure><img src="../../../.gitbook/assets/image (3).png" alt=""><figcaption><p>Code coverage</p></figcaption></figure>

Super nouvelle !!! on a du code source couvert à 100%.

#### En ligne de commande

Pour ce faire on peut utiliser `dotCover` :&#x20;

```sh
dotnet tool install --global JetBrains.dotCover.GlobalTool
dotnet dotcover test --dcReportType=HTML
```

Cela va générer 1 rapport `html` :&#x20;

<figure><img src="../../../.gitbook/assets/dotcover-report.webp" alt=""><figcaption><p>dotcover report</p></figcaption></figure>

Super nouvelle !!! on a du code source couvert à 100%.

> Est-ce que cela suffit pour nous rendre complètement confiant vis-à-vis de nos futurs refactorings ?

## Analyse static de code

Nous allons dès maintenant mettre en place un outil d'analyse static de code ([SonarCloud](https://www.sonarsource.com/products/sonarcloud/) ici) et automatiser son lancement via notre chaine de build. Celà nous permettra tout au long de l'atelier de vérifier l'impact de nos améliorations sur le code.

En utilisant `github` on peut profiter des `github actions` pour ce faire:

```yaml
name: SonarCloud
on:
  push:
    branches:
      - main
      - steps/01-gather-metrics
jobs:
  build:
    name: Build and analyze
    runs-on: windows-latest
    steps:
      - name: Set up JDK 11
        uses: actions/setup-java@v3
        with:
          java-version: 11
          distribution: 'zulu' # Alternative distribution options are available.
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0  # Shallow clones should be disabled for a better relevancy of analysis
      - name: Cache SonarCloud packages
        uses: actions/cache@v3
        with:
          path: ~\sonar\cache
          key: ${{ runner.os }}-sonar
          restore-keys: ${{ runner.os }}-sonar
      - name: Cache SonarCloud scanner
        id: cache-sonar-scanner
        uses: actions/cache@v3
        with:
          path: .\.sonar\scanner
          key: ${{ runner.os }}-sonar-scanner
          restore-keys: ${{ runner.os }}-sonar-scanner
      - name: Install SonarCloud scanner
        if: steps.cache-sonar-scanner.outputs.cache-hit != 'true'
        shell: powershell
        run: |
          New-Item -Path .\.sonar\scanner -ItemType Directory
          dotnet tool update dotnet-sonarscanner --tool-path .\.sonar\scanner
      - name: Build and analyze
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
        shell: powershell
        run: |
          // On lance l'analyse 
          dotnet tool install --global dotnet-coverage
          .\.sonar\scanner\dotnet-sonarscanner begin /k:"ythirion_refactoring-du-bouchonnois" /o:"ythirion" /d:sonar.login="${{ secrets.SONAR_TOKEN }}" /d:sonar.host.url="https://sonarcloud.io" /d:sonar.cs.vscoveragexml.reportsPaths=coverage.xml
          dotnet build
          // On ajoute le rapport de coverage
          dotnet-coverage collect "dotnet test" -f xml -o "coverage.xml"
          .\.sonar\scanner\dotnet-sonarscanner end /d:sonar.login="${{ secrets.SONAR_TOKEN }}"
```

Après un premier lancement on obtient ce dashboard.&#x20;

<figure><img src="../../../.gitbook/assets/image (4).png" alt=""><figcaption><p>Rapport Sonarcloud</p></figcaption></figure>

D'après l'outil la solution est plutôt en bonne santé:

* 35 code smells
* 100% de coverage
* MAIS 7.3% de duplication

<figure><img src="../../../.gitbook/assets/image (5).png" alt=""><figcaption><p>Complécité cyclomatique</p></figcaption></figure>

&#x20;Il y a 1 code smell qualifié de `critical` qui doit attirer notre attention. En effet, la complexité cyclomatique de la classe `PartieDeChasseService` est très élevée.

Une méthode a une complexité de 20...

Cette classe est un service qui ne devrait avoir qu'une logique d'orchestration:

* Charger 1 `Aggregate` depuis son repository
* Appeler la méthode métier sur cet `Aggregate`
* Sauver le nouvel état à l'aide du même repository

On peut alors catégoriser le code de cette manière:&#x20;

Ainsi, on peut voir :&#x20;

<figure><img src="../../../.gitbook/assets/image (6).png" alt=""><figcaption><p>4 types de code : 1 domaine anémique...</p></figcaption></figure>

* les classes actuellement dans notre `Domain` sont complètement anémiques : ne comprennent aucun comportement

```csharp
// Uniquement des get / set
// 1 classe totalement anémique
public class PartieDeChasse
{ 
    public Guid Id { get; set; }
    public List<Chasseur> Chasseurs { get; set; }
    public Terrain Terrain { get; set; }
    public PartieStatus Status { get; set; }
    public List<Event> Events { get; set; }
}
```

* le service `PartieDeChasseService` contient des comportements qui devraient être dans le `Domain`

```csharp
// Des règles métiers disséminées partout dans le Service
if (partieDeChasse.Terrain.NbGalinettes != 0)
{
    if (partieDeChasse.Status != PartieStatus.Apéro)
    {
        if (partieDeChasse.Status != PartieStatus.Terminée)
        {
            if (partieDeChasse.Chasseurs.Exists(c => c.Nom == chasseur))
            {
                var chasseurQuiTire = partieDeChasse.Chasseurs.First(c => c.Nom == chasseur);

                if (chasseurQuiTire.BallesRestantes == 0)
                {
```

## Linter

Afin d'avoir le feedback de l'analyse static de code dans notre `IDE` on peut installer le plugin [`sonarlint`](https://www.sonarsource.com/products/sonarlint/). Le linter nous fournira le même feedback que `SonarCloud` mais sans avoir à lancer une analyse complète.

<figure><img src="../../../.gitbook/assets/image (7).png" alt=""><figcaption><p>SonarLint</p></figcaption></figure>

On peut le configurer afin de le "binder" avec notre projet dans `sonarcloud` afin que l'analyse en local se fasse avec le même set de règles que dans la version cloud. Pour celà il suffit de suivre la documentation disponible [ici](https://github.com/SonarSource/sonarlint-intellij/wiki/Bind-to-SonarQube-or-SonarCloud).

## Hotspots

On va utiliser `codescene`, une plate-forme faisant à la fois de l'analyse static de code mais également de l'analyse "comportementale" du code permettant de :

* Identifier de potentiels `hotspots`
* Comprendre la diffusion de la connaissance sur une code base donnée
* Identifier du couplage temporel
* ...

Après avoir lancé une première analyse on a déjà quelques indications sur la santé globale de notre code d'après cet outil...&#x20;

<figure><img src="../../../.gitbook/assets/image (8).png" alt=""><figcaption><p>Rapport de Codescene</p></figcaption></figure>

On va mettre l'accent sur les `hotspots` pour identifier où sont les morceaux de code à problèmes.&#x20;

![](<../../../.gitbook/assets/image (9).png>)

Comme illustré ci-dessus, les hotspots sont des morceaux de code complexes qui ont tendance à être modifiés de manière très régulière...&#x20;

<figure><img src="../../../.gitbook/assets/image (10).png" alt=""><figcaption><p>Hotspot analysis</p></figcaption></figure>

Il apparait que nous avons 2 hotspots dans la solution :

* `PartieDeChasseService`
* `PartieDeChasseServiceTests` et ses 1131 lignes de code

## Badges

Lorsque l'on utilise des outils, il est important de rendre visible les "choses". Nous allons donc faire en sorte que le résultat de nos outils d'analyse (sonarcloud et codescene) soient visibles à l'ouverture du fichier `README` en ajoutant des badges dans le `markdown`.

```markdown
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=ythirion_refactoring-du-bouchonnois&metric=alert_status)](https://sonarcloud.io/summary/new_code?id=ythirion_refactoring-du-bouchonnois) 
[![Coverage](https://sonarcloud.io/api/project_badges/measure?project=ythirion_refactoring-du-bouchonnois&metric=coverage)](https://sonarcloud.io/summary/new_code?id=ythirion_refactoring-du-bouchonnois) 
[![Code Smells](https://sonarcloud.io/api/project_badges/measure?project=ythirion_refactoring-du-bouchonnois&metric=code_smells)](https://sonarcloud.io/summary/new_code?id=ythirion_refactoring-du-bouchonnois) 
[![Lines of Code](https://sonarcloud.io/api/project_badges/measure?project=ythirion_refactoring-du-bouchonnois&metric=ncloc)](https://sonarcloud.io/summary/new_code?id=ythirion_refactoring-du-bouchonnois) 
[![CodeScene Code Health](https://codescene.io/projects/39213/status-badges/code-health)](https://codescene.io/projects/39213) 
[![CodeScene System Mastery](https://codescene.io/projects/39213/status-badges/system-mastery)](https://codescene.io/projects/39213)	
```

## Revue de la qualité des tests

Nous avons vu précédemment que le coverage est à 100% sur cette solution. Mais qu'en est-il de leur qualité ?

C'est ce qu'on va vérifier en lançant une analyse à l'aide de `stryker`. C'est un outil de [mutation testing](https://xtrem-tdd.netlify.app/Flavours/mutation-testing) signifiant qu'il va créer des versions mutantes de notre code de production et vérifier que les tests vont bien identifier ces mutants (au moins 1 test doit échouer pour chaque mutant généré).

Pour le lancer, il suffit d'installer `stryker` puis de l'exécuter:

```shell
dotnet tool install -g dotnet-stryker
dotnet stryker
```

Voici le résultat du lancement de stryker:&#x20;

<figure><img src="../../../.gitbook/assets/image (11).png" alt=""><figcaption><p>Rapport Stryker</p></figcaption></figure>

Intéressant, malgré nos 100% de code coverage on obtient un score de mutation qui est autour de `79%`... Celà signifie que notre `filet de sécurité` ne nous couvre pas aussi bien qu'escompté.

Si on analyse le mutant ci-dessous, on voit que stryker a retiré certains appels.&#x20;

<figure><img src="../../../.gitbook/assets/image (12).png" alt=""><figcaption><p>Statement mutation example</p></figcaption></figure>

On peut alors comprendre que certains `side-effects` du service ne sont pas toujours validés par nos tests:

* Appelle à la méthode `Save` du repository
* Ajout d'événements dans la `PartieDeChasse`
* ...

Il va y avoir un petit peu de travail au niveau de nos tests afin d'améliorer leur couverture réelle.

> Pour revenir sur le code coverage, c'est un excellent indicateur négatif (avoir 0% de coverage montre qu'il y a un effort à fournir) mais un mauvais positif (avoir 100% ne signifie qu'on peut être confiant vis-à-vis de notre filet de sécurité).

## Reflect

* [x] Compiler afin de valider qu'on est en capacité de compiler / exécuter le code
  * Analyser les potentiels `Warning` à la compilation
* [x] Analyser la structure de la solution afin de comprendre l'architecture en place
* [x] Regarder quels packages sont référencés afin de comprendre les interactions potentielles du système
* [x] Récupérer le `code coverage`
* [x] Mettre en place un outil d'analyse static de code
* [x] Utiliser un Linter
* [x] Identifier s'il y a des [`hotspots`](https://understandlegacycode.com/blog/focus-refactoring-with-hotspots-analysis/) et où ils sont localisés
* [x] Revue de la qualité des tests

<figure><img src="../../../.gitbook/assets/image (13).png" alt="" width="199"><figcaption></figcaption></figure>

A l'aide de ces éléments nous avons pu identifier certains axes d'amélioration :

* Fixer les `warnings` de compilation
  * Mettre en place une politique : `0 tolérance aux warnings`
* Améliorer les tests afin d'atteindre un score de mutation proche des 100%
* Splitter le service `PartieDeChasseService`
  * Mettre le comportement business dans le `Domain`
  * Rendre le `Domain` riche et non plus anémique
  * Le décomposer : 1 classe par comportement (handlers)
* Eliminer les `code smells` idenfiés par `sonar`
  * Fait au fur et à mesure

> Code disponible [ici](https://github.com/ythirion/refactoring-du-bouchonnois/tree/steps/01-gather-metrics).
