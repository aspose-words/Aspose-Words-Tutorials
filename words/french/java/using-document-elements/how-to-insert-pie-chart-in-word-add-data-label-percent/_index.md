---
category: general
date: 2026-07-20
description: Comment insérer un graphique circulaire dans Word avec Aspose.Words.
  Apprenez à ajouter les pourcentages d’étiquettes de données et à les afficher sur
  le graphique pour des documents professionnels.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: fr
lastmod: 2026-07-20
og_description: Comment insérer un graphique circulaire dans Word avec Aspose.Words.
  Ce guide montre comment ajouter le pourcentage d’étiquette de données et afficher
  les pourcentages sur le graphique en quelques lignes seulement.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: Comment insérer un graphique circulaire dans Word – guide rapide
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: Comment insérer un graphique en secteurs dans Word – ajouter le pourcentage
  d’étiquette de données
url: /fr/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# comment insérer un pie chart dans Word – ajouter le pourcentage d'étiquette de données

Vous vous êtes déjà demandé **comment insérer un pie chart** dans un document Word sans vous battre avec l'interface ? Vous n'êtes pas seul. Dans de nombreux scénarios de reporting, vous devez *ajouter un pie chart à Word* et, plus important encore, **afficher le pourcentage sur le pie chart** afin que les lecteurs comprennent immédiatement la répartition des données.

Dans ce tutoriel, nous parcourrons le processus complet en utilisant Aspose.Words for Java. À la fin, vous saurez exactement comment **ajouter le pourcentage d'étiquette de données**, **afficher les pourcentages sur le graphique**, et obtenir un pie chart soigné qui apparaît correctement du premier coup. Aucun plugin supplémentaire, aucune retouche manuelle—juste du code propre que vous pouvez intégrer dans n'importe quel projet.

---

## Prérequis

- Java 17 (ou version ultérieure) – la version LTS actuelle prise en charge par Aspose.Words.
- Aspose.Words for Java 24.x (la dernière au moment de la rédaction, juillet 2026).
- Une configuration basique Maven ou Gradle pour récupérer la bibliothèque.
- Un IDE de votre choix (IntelliJ IDEA, Eclipse, VS Code… tout convient).

Si vous avez déjà tout cela, super—plongeons-y.

---

## Étape 1 : Configurer le projet et importer la bibliothèque

Tout d'abord, ajoutez la dépendance Aspose.Words à votre `pom.xml` (Maven) ou `build.gradle` (Gradle). Cela vous donne accès aux classes `Document`, `DocumentBuilder` et aux classes de graphiques.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Astuce :** Gardez le numéro de version à jour ; les nouvelles versions ajoutent souvent des correctifs liés aux graphiques qui rendent **l'affichage des pourcentages sur le graphique** plus fiable.

---

## Étape 2 : Créer un nouveau document Word et un builder

Le builder est votre couteau suisse pour insérer du contenu. Ici, nous créons un nouveau document et y attachons un `DocumentBuilder`.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Pourquoi avons‑nous besoin d'un builder ? Il abstrait les structures OpenXML de bas niveau, nous permettant de nous concentrer sur *ce que* nous voulons—comme **ajouter un pie chart à Word**—au lieu de *comment* le XML apparaît.

---

## Étape 3 : Insérer le pie chart

Voici le cœur de **comment insérer un pie chart**. Nous demandons au builder de placer un pie chart d'une taille spécifique. Les dimensions sont en points (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

À ce stade, le graphique est vide, mais l'espace réservé est déjà dans le document. Vous venez d'**ajouter un pie chart à Word** de façon programmatique.

---

## Étape 4 : Remplir le graphique avec des données

Un pie chart nécessite au moins une série de valeurs. Alimentons‑le avec des données d'exemple représentant la part de marché.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Si vous avez besoin de plusieurs séries (pie charts empilés, doughnuts, etc.), vous pouvez appeler `pieChart.getSeries().add()` et répéter les étapes. La même logique s'applique lorsque vous voulez **afficher les pourcentages sur le graphique** pour chaque tranche.

---

## Étape 5 : **add data label percent** – afficher les pourcentages sur les tranches

C'est la partie que la plupart des développeurs oublient : configurer les étiquettes de données pour afficher les pourcentages. Sans cela, le graphique ne montre que des nombres bruts, ce qui peut être ambigu.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

L'appel `setShowPercent(true)` indique à Aspose.Words de rendre l'étiquette sous la forme « 30 % », « 45 % », etc. C’est exactement ainsi que vous **affichez le pourcentage sur le pie chart** sans aucun travail de formatage supplémentaire.

---

## Étape 6 : Enregistrer le document

Enfin, écrivez le document sur le disque. Vous pouvez choisir `.docx`, `.pdf` ou même `.html`. Pour ce guide, nous resterons sur le format moderne `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Exécutez le programme, ouvrez `PieChartDemo.docx`, et vous verrez un pie chart soigneusement rendu avec des étiquettes de pourcentage sur chaque tranche.

---

## Résultat attendu

Ci-dessous, une capture d'écran du fichier Word généré. Remarquez comment chaque tranche affiche sa part en pourcentage—exactement ce que nous voulions en définissant **add data label percent**.

![Capture d'écran d'un document Word contenant un pie chart avec des étiquettes de pourcentage](/images/pie-chart-percent.png){.center width=600px alt="Capture d'écran montrant comment insérer un pie chart dans Word avec des étiquettes de pourcentage"}

*Le texte alternatif inclut le mot‑clé principal, satisfaisant à la fois le SEO et l'accessibilité.*

---

## Questions fréquentes & gestion des cas particuliers

| Question | Réponse |
|----------|--------|
| **Puis-je changer la police des étiquettes de pourcentage ?** | Oui. Après avoir activé `setShowPercent(true)`, récupérez l'objet `DataLabel` et ajustez sa propriété `Font` (`dataLabel.getFont().setSize(10);`). |
| **Et si j’ai besoin d’un doughnut chart au lieu d’un pie ?** | Remplacez `ChartType.PIE` par `ChartType.DOUGHNUT` dans l’appel `insertChart`. La même logique **add data label percent** fonctionne. |
| **Les versions plus anciennes de Word (2007‑2010) affichent‑elles correctement les pourcentages ?** | Aspose.Words écrit le XML sous‑jacent de manière indépendante de la version, ainsi les pourcentages apparaissent dans n’importe quel Word qui prend en charge les graphiques (2007+). |
| **Comment ajouter un titre au graphique ?** | Utilisez `pieChart.getTitle().setText("Market Share");` avant d’enregistrer. |
| **Puis‑je insérer le graphique dans un paragraphe ou une cellule de tableau spécifique ?** | Absolument. Déplacez le `DocumentBuilder` à l’emplacement souhaité (`builder.moveToParagraph(index, true);` ou `builder.moveToCell(table, row, column, true);`) avant d’appeler `insertChart`. |

---

## Astuces et conseils du terrain

- **Astuce :** Si vous prévoyez de générer de nombreux graphiques dans une boucle, réutilisez une seule instance de `DocumentBuilder` ; cela réduit la consommation de mémoire.
- **Attention :** Les tranches très petites (< 2 %). Aspose.Words peut omettre l’étiquette pour éviter l’encombrement ; vous pouvez la forcer avec `dataLabel.setShowLabel(true);`.
- **Note de performance :** Le rendu des graphiques est gourmand en CPU. Pour la génération massive de rapports, envisagez le multithreading mais assurez‑vous que chaque thread travaille sur sa propre instance de `Document`.
- **Vérification de version :** La méthode `setShowPercent` a été introduite dans Aspose.Words 22.8. Si vous utilisez une version antérieure, mettez‑à‑jour ou calculez manuellement les pourcentages et définissez‑les comme étiquettes personnalisées.

---

## Récapitulatif

Nous avons couvert **comment insérer un pie chart** dans un document Word en utilisant Aspose.Words, vous avons montré comment **ajouter le pourcentage d'étiquette de données**, et démontré la façon la plus simple d'**afficher les pourcentages sur le graphique**. Avec seulement quelques lignes de Java, vous pouvez **ajouter un pie chart à Word** et **afficher le pourcentage sur le pie chart**, transformant les nombres bruts en visuels immédiatement lisibles.

---

## Et après ?

- Expérimentez avec d'autres types de graphiques (`BAR`, `LINE`, `AREA`) et voyez comment la même logique **add data label percent** s'applique.
- Combinez les graphiques avec des tableaux pour des rapports plus riches—Aspose.Words rend trivial le placement d'un graphique à côté d'un tableau de données.
- Explorez l'exportation du même document en PDF ou HTML pour voir comment les pourcentages sont rendus selon les formats.

N'hésitez pas à ajuster les dimensions, les couleurs ou la source de données (par ex., une requête de base de données) et voyez vos rapports Word prendre vie. Si vous rencontrez un problème, laissez un commentaire ci‑dessous—bon graphique !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Insérer un graphique en colonnes dans Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insérer un graphique en aires dans un document Word | Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Insérer un graphique à bulles dans Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}