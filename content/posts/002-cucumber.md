+++
title = "J'aime bien les cucumbers"
date = 2026-07-29T08:30:00+02:00
draft = false
tags = ['blog', 'java', 'cucumber', 'test']
+++

## Pourquoi Cucumber (et Gherkin) me parle tant

J’utilise [Cucumber](https://cucumber.io/) pour mes tests d’intégration sur la mission où je suis actuellement. Et ce qui me plaît, c’est qu’il permet d’écrire les cas de test en langage naturel grâce à Gherkin.

Par exemple :

```gherkin
Given utilisateur non connecté
When Je veux accéder à la page d'accueil
Then Afin de voir les derniers articles publiés
```

Les deux grands atouts pour moi :

- Écrire des tests sous forme de phrases, c’est plus naturel et ça permet de se projeter.
- Pouvoir enchaîner les cas de test facilement.

Et surtout, c’est un moyen de partager une spécification vivante avec les métiers. Le scénario est écrit, partagé, validé. Si le besoin change, on modifie le Gherkin, et le code suit.

Si je devais résumer Cucumber, je commencerais par sa place dans la pyramide des tests. Moi, je m’en sers surtout pour des tests d’intégration : tester mon appli (un back Spring par exemple) en boîte noire, ou avec quelques mocks sur certains composants. Et ce que j’aime, c’est que ça me permet de valider à la fois des règles métiers concrètes **et** le bon fonctionnement de l’ensemble.

---

## Un exemple

Prenons une interface `Vehicule`, où l'on a la possibilité de mettre le régulateur à une vitesse donnée.

```java
public interface Vehicule {
    void setRegulateur(final int vitesseCible);
    int getVitesseCible();
}
```

Et un objet `Voiture` que nous voulons implémenter, héritant de `Vehicule`.

```java
public class Voiture implements Vehicule {

    public void setRegulateur(final int vitesseCible) {
        throw new Error("Not Implemented");
    }

    public int getVitesseCible() {
        throw new Error("Not Implemented");
    }
}
```

Ensuite, une fois les contrats d'interface faits, je peux rédiger les tests avec mon vocabulaire via Gherkin.

> Note : J'ai découvert qu'il y avait une option pour faire les mots clés en français, ce qui peut permettre aux rédacteurs des specs de totalement prendre en mettre les notations et de se l'approprier facilement.

```gherkin
# language: fr
Fonctionnalité: Gestion de la vitesse d'une voiture

  Scénario: La voiture accélère normalement
    Soit une voiture à l'arrêt
    Lorsque je met le régulateur à 50 km h
    Alors sa vitesse est de 50 km h

  Scénario: La voiture ne dépasse pas la vitesse maximale
    Soit une voiture roulant à 100 km h
    Lorsque je met le régulateur à 150 km h
    Alors sa vitesse est de 150 km h

  Scénario: La voiture ne peut pas dépasser 150 km h
    Soit une voiture roulant à 150 km h
    Lorsque je met le régulateur à 170 km h
    Alors sa vitesse reste à 150 km h
    Et un message "Vitesse maximale atteinte" est affiché

  Scénario: La voiture ne peut pas avoir une vitesse négative
    Soit une voiture à l'arrêt
    Lorsque je met le régulateur à -30 km h
    Alors sa vitesse reste à 0 km h
    Et un message "La vitesse ne peut pas être négative" est affiché

```

En lisant le fichier de test de voiture, je peux en déduire facilement les specs :

- Une voiture peut être à l'arrêt,
- Peut atteindre la vitesse maximale (150 km/h)
- Ne peut pas dépasser 150 km/h et affiche un message d'erreur si on le lui demande
- Ne peut pas avoir de vitesse négative et affiche un message d'erreur si on le lui demande
- Et doit rouler à la vitesse cible comme on le lui demande.

> À noter que l'inverse peut être fait : les specs peuvent être rédigées de cette manière. Cela permet au dev (ou à l'IA) de pouvoir implémenter la feature avec des tests associés.

Et enfin, en Java avec Cucumber, ça donne un test d'intégration qui lie ces scénarios à du code :

```java
import fr.rm3.Voiture;
import io.cucumber.java.en.Given;
import io.cucumber.java.en.Then;
import io.cucumber.java.en.When;

import static org.assertj.core.api.Assertions.assertThat;

public class VoitureStepDefinition {
    private Voiture voiture;
    private String messageErreur;

    @Given("une voiture à l'arrêt")
    public void uneVoitureALarret() {
        voiture = new Voiture();
    }

    @Given("une voiture roulant à {int} km h")
    public void uneVoitureRoulantAKmH(int vitesse) {
        voiture = new Voiture();
        voiture.setRegulateur(vitesse);
    }

    @When("je met le régulateur à {int} km h")
    public void jeMetLeRegulateurAKmH(int vitesse) {
        try {
            voiture.setRegulateur(vitesse);
            messageErreur = null;
        } catch (IllegalArgumentException e) {
            messageErreur = e.getMessage();
        }
    }

    @Then("sa vitesse est de {int} km h")
    public void saVitesseEstDeKmH(final int vitesse) {
        assertThat(voiture.getVitesseCible()).isEqualTo(vitesse);
    }

    @Then("sa vitesse reste à {int} km h")
    public void saVitesseResteAKmH(final int vitesse) {
        assertThat(voiture.getVitesseCible()).isEqualTo(vitesse);
    }

    @Then("un message {string} est affiché")
    public void unMessageEstAffiche(final String message) {
        assertThat(messageErreur).isEqualTo(message);
    }
}
```

Et là, nous avons notre structure de TDD qui est mise en place. En lançant une première fois les tests, tous les tests seront au rouge. Cela s'appelle la méthode du Red Green Refactor [Détails ici](https://martinfowler.com/bliki/TestDrivenDevelopment.html) : on écrit la structure, puis on implémente les tests, on lance au rouge, puis on implémente une partie ou la totalité du code, on recommence jusqu'à ce que ça soit vert.

Voici une implémentation possible de `Voiture`

```java
public class Voiture implements Vehicule {
    private int vitesse;
    private static final int VITESSE_MAX = 150;

    @Override
    public void setRegulateur(int vitesseCible) {
        if (vitesseCible < 0) {
            throw new IllegalArgumentException("La vitesse ne peut pas être négative");
        }
        if (vitesseCible > VITESSE_MAX) {
            throw new IllegalArgumentException("Vitesse maximale atteinte");
        }
        this.vitesse = vitesseCible;
    }

    @Override
    public int getVitesseCible() {
        return vitesse;
    }
}
```

Le code source est juste ici : https://github.com/ronronan/cucumber-sample

Ce que je n'ai pas abordé dans cette article :

- Une fonctionnalité que j'aime beaucoup est la possibilité de faire des `Scenario Outline`, avec des exemples pour les mêmes tests, il y a juste les paramètres qui varient
- L'interaction avec d'autres outils comme une BDD de test, ...

## Pourquoi ça vaut le coup

- **Lisibilité** — un scénario Gherkin se lit comme une spécification, pas comme du code. N'importe qui (dev, QA, métier) peut le comprendre.
- **Documentation vivante** — les tests deviennent la source de vérité. Plus besoin d'une spec à part qui se périme ; le Gherkin est la spec.
- **Collaboration métier** — les scénarios peuvent être écrits, relus et validés par les non-techniciens. Tout le monde parle le même langage.
- **Réutilisabilité** — les steps definitions (`Given`, `When`, `Then`) se composent et se réutilisent entre scénarios, évitant la duplication de code de test.
- **TDD / BDD** — le Gherkin force à réfléchir au comportement attendu _avant_ d'écrire le code. C'est du BDD appliqué.
- **Couverture fonctionnelle** — on valide des règles métier concrètes, pas seulement des unités de code isolées.

## Limitations rencontrées

Cucumber n'est pas une solution universelle :

- **Temps d'exécution** — les tests d'intégration avec Cucumber sont plus lents que des tests unitaires. Ils ne remplacent pas une bonne pyramide de tests.
- **Maintenance des steps** — quand le vocabulaire Gherkin change, il faut mettre à jour toutes les steps definitions associées. Un step mal nommé peut devenir ambigu.
- **Verbeux pour des cas simples** — écrire un fichier `.feature` pour une règle triviale alourdit inutilement le projet. Parfois un simple test JUnit suffit.
- **Parsing fragile** — Cucumber repose sur des expressions régulières. Un espace ou un paramètre mal typé et le step n'est plus matché.
- **Discipline d'équipe** — pour que ça tienne dans la durée, toute l'équipe doit maintenir les scénarios propres. Si les `.feature` se dégradent, ils deviennent obsolètes et personne ne les lit.

Par rapport à ma mission actuelle, je rencontre aussi des "épines dans les pieds" (expression que j'utilise) :

- Actuellement, nous utilisons H2 comme base de données de test. Je serai curieux (peut-être dans un article futur) de voir ce que ça vaut avec [TestContainers](https://testcontainers.com/) et de lancer une "vraie" instance de BDD correspondant au projet.
- Aussi, pour les jeux de tests, il y a une classe utilitaire pour lire facilement des fichiers JSON et les sérialiser en objet ou liste d'objet rapidement. Cela est bien pratique, par contre, nous sommes obligés de créer des fichiers pour chaque cas de tests, ce qui multiplie considérablement le nombre de fichiers et alourdit, je trouve, le fait d'implémenter les tests. Je suis en train de réfléchir à une solution, mais pour le moment, rien ne me vient à l'esprit.

## Aparté

J'ai commencé mon nouvel boulot à berix (coucou) et ça se passe très bien. Après un peu plus de deux mois, j'ai l'impression de retrouver ce que je cherchais, un but, quelque chose à construire, sans se prendre la tête et surtout une dynamique d'avoir envie de faire bien les choses. À voir si les choses continuent ainsi 🤞

> PS: Je me suis un peu aidé de l'IA pour ajuster certains paragraphes. Cela se voit un peu, mais j'essaie au maximum de ne pas l'utiliser, sauf pour corriger à minima les fautes et certaines tournures bizarres. Mon but étant de m'améliorer en rédaction, cela serait contre productif. Aussi, je n'aime pas trop lire des articles rédigés par IA, donc pourquoi j'infligerai cela à quelqu'un alors que moi même je n'ai pas cela. Enfin, j'essaie de trouver mon rythme d'écriture, mais cela est encore compliqué (deux mois pour pondre un second article).

**À bientôt**. Ronan.
