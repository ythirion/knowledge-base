---
description: Workshop to demo the power of CrimeScene and the ideas behind it.
---

# Workshop

### Objectives :

* Understand how to fix technical debt with Code Analysis.

## Connection - 10'

In pair answer to those questions, in your team :

* What is technical debt ?
* What is the difference between technical debt and legacy code ?
* How do you quantify your technical debt ?
* How do you use your Static Code Analysis tools ?
* What could be improved ?

## Concepts - 20'

Go through this page

{% content-ref url="./" %}
[.](./)
{% endcontent-ref %}

![](<../../.gitbook/assets/Software-Design X-Rays.png>)

## Concrete Practice - 20'

In pair select 1 exercise (in each exercise you will investigate in a code base of your choice with [CodeScene](https://codescene.io/)) - **15'**

* Find Refactoring Candidates :
  * [ASP .NET Core](https://codescene.io/projects/1690/jobs/52744/results/code/hotspots/system-map)
  * [Docker](https://codescene.io/projects/169/jobs/3964/results/code/hotspots/system-map)
  * [Rails](https://codescene.io/projects/1699/jobs/4265/results/code/hotspots/system-map)
* Prioritize Hotspots :
  * [Linux](https://codescene.io/projects/1740/jobs/4358/results/code/hotspots/system-map)
* Identify change patterns :
  * [e-Commerce site](https://codescene.io/projects/1593/jobs/3920/results/code/temporalcoupling/by-commits)
  * [PhpSpreadSheet](https://codescene.io/projects/1579/jobs/3839/results/code/temporalcoupling/by-commits)
* Find the Experts in [Kubernetes](https://codescene.io/projects/1823/jobs/4598/results/social/knowledge/individuals)
* Off-boarding, what if someone leaves the project?
  * [Clojure](https://codescene.io/projects/1824/jobs/4597/results/social/knowledge/individuals?aspect=loss)
  * [Git](https://codescene.io/projects/1664/jobs/4156/results/social/knowledge/individuals?aspect=loss)

#### Collective debriefing - What are your findings ?

## Conclusion - 10'

There is so much more to do with what we already have.

#### Demo of CodeCharta with SonarQube Data :

![](<../../.gitbook/assets/image (594).png>)

#### Demo of code-forensics

* Clone a repository
* Run analysis through :

```bash
sh run-analysis.sh --projectName=<project> --repositoryPath=<path>
```

{% embed url="https://github.com/ythirion/code-forensics" %}

![](<../../.gitbook/assets/image (595).png>)

#### Resources

* [Codecharta](https://github.com/MaibornWolff/codecharta)
* [CodeScene](https://codescene.com/)
* [Code-maat](https://github.com/adamtornhill/code-maat)
* [code-forensics](https://github.com/smontanari/code-forensics)
* [code-forensics scripts](https://github.com/ythirion/code-forensics)
