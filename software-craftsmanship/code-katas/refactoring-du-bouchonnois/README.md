---
description: >-
  Kata de refactoring pour apprendre des techniques telles que Property-Based
  Testing, Approval Testing, Strangler, Functional Programming, ....
---

# Refactoring du Bouchonnois

Ce kata a pour objectif de s'exercer au refactoring sur un code existant afin de :

* Identifier certains `smells` dans notre code
* Comprendre quelle pratique et/ou outil peuvent nous aider pour surpasser ces `smells`
* Pratiquer dans 1 environnement `safe` en dehors de son code de production

<figure><img src="../../../.gitbook/assets/image (715).png" alt=""><figcaption></figcaption></figure>

Le kata est disponible sur github [ici](https://github.com/ythirion/refactoring-du-bouchonnois/).

## Le contexte

Nos vaillants chasseurs du Bouchonnois ont besoin de pouvoir gérer leurs parties de chasse.\
Ils ont commencé à faire développer 1 système de gestion par une l'entreprise `Toshiba` mais ne sont pas satisfaits.

L'entreprise leur parle d'une soit-disante `dette technique` qui les ralentit dans le développement de nouvelles features...

Nos vaillants chasseurs du Bouchonnois ont besoin de pouvoir gérer leurs parties de chasse.\
Ils ont commencé à faire développer 1 système de gestion par une l'entreprise `Toshiba` mais ne sont pas satisfaits.

L'entreprise leur parle d'une soit-disante `dette technique` qui les ralentit dans le développement de nouvelles features...

<figure><img src="../../../.gitbook/assets/image (716).png" alt=""><figcaption></figcaption></figure>

> Les chasseurs comptent sur nous pour améliorer la situation.

## Example Mapping

Ils ont fait quelques ateliers avec `Toshiba` et ont réussi à clarifier ce qui est attendu du système. Pour ce faire, ils ont utilisé le format `Example Mapping` à découvrir [ici](https://xtrem-tdd.netlify.app/Flavours/example-mapping).

Voici l'Example Mapping qui a servi d'alignement pour développer ce système.

<figure><img src="../../../.gitbook/assets/image (717).png" alt=""><figcaption><p>Example Mapping du Bouchonnois</p></figcaption></figure>

Version PDF disponible [ici](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/example-mapping/example-mapping.pdf).

## Facilitation

#### Pré-requis

Le code est disponible en `.NET 7`.

Voici la liste des packages utilisés :

* `xUnit`
* `FluentAssertions`
* `Verify.xUnit`
* `FSCheck`
* `TngTech.ArchUnitNET.xUnit`
* `LanguageExt.Core`
* `FluentAssertions.LanguageExt`

Afin d'améliorer le code on te propose de suivre les étapes ci-dessous : &#x20;

{% content-ref url="step-1-se-faire-une-idee-du-code.md" %}
[step-1-se-faire-une-idee-du-code.md](step-1-se-faire-une-idee-du-code.md)
{% endcontent-ref %}

* [2. Treat Warnings as Errors](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/02.treat-warnings-as-errors.md)
* [3. Let's kill some mutants](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/03.kill-mutants.md)
* [4. Améliorer la lisibilité des tests](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/04.improve-tests-readability.md)
* [5. "Approve" everything](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/05.approve-everything.md)
* [6. "Properties" everywhere](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/06.properties.md)
* [7. Tests d'architecture](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/07.architecture-tests.md)
* [8. Use Cases](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/08.use-cases.md)
* [9. Tell Don't Ask](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/09.tell-dont-ask.md)
* [10. Commands](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/10.commands.md)
* [11. Plus d'exceptions](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/11.avoid-exceptions.md)
* [12. Event Sourcing](https://github.com/ythirion/refactoring-du-bouchonnois/blob/main/facilitation/12.event-sourcing.md)

Pour chaque étape :

* une proposition de solution "_étape par étape_" est proposée
* il existe 1 branche / étape

<figure><img src="../../../.gitbook/assets/image (718).png" alt=""><figcaption></figcaption></figure>

### Objectifs pédagogiques

À travers ces différentes étapes j'ai essayé d'introduire les sujets suivants :

* Example Mapping
* Static Code Analysis / Linter
* Treat Warnings as Errors
* Mutation Testing
* Test Data Builders
* Approval Testing
* Automated Refactoring
* Property-Based Testing
* Tests d'Architecture
* Test-Driven Development
* Clean Architecture
* Domain Driven Design
* Tell Don't Ask
* Functional Programming
* Avoid Primitives
* Avoid Exceptions
* Architecture Decision Records
* Event Sourcing
* ...

Bon voyage 🤩
