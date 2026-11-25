---
category: general
date: 2026-11-25
description: Apprenez à créer un diagramme circulaire en Java, à insérer ce diagramme
  dans un document Word, à exploser une part du diagramme et à changer l'orientation
  du graphique avec des exemples de code clairs.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: fr
lastmod: 2026-11-25
og_description: Créer un diagramme circulaire en Java, l’insérer dans un document,
  éclater une tranche du diagramme et modifier l’orientation du graphique avec un
  code étape par étape.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Créer un diagramme circulaire en Java – insérer, exploser une part et faire
  pivoter
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Comment créer un diagramme circulaire, l’insérer et personnaliser son orientation
  en Java
url: /fr/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un diagramme circulaire, l'insérer et personnaliser l'orientation en Java

Si vous devez **créer un diagramme circulaire** dans un document Word, ce guide vous montre exactement comment le faire. Vous verrez comment **insérer un diagramme circulaire**, exploser une tranche pour la mettre en évidence, et **modifier l'orientation du diagramme** avec une simple rotation.

Le tutoriel couvre tout ce dont vous avez besoin — de la configuration de la bibliothèque Aspose.Words for Java à la production d'un fichier `.docx` final affichant un diagramme circulaire tourné et explosé. Aucune documentation externe n'est requise ; suivez simplement les étapes et exécutez le code.

## Prérequis

* Java 17 ou version ultérieure installé.
* Maven ou Gradle pour gérer les dépendances.
* Une licence valide d'Aspose.Words for Java (ou utilisez le mode d'évaluation gratuit).

Ajoutez la dépendance Aspose.Words à votre `pom.xml` (Maven) ou `build.gradle` (Gradle). Exemple pour Maven :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Astuce :** Gardez la version de la bibliothèque à jour ; la dernière version (24.10 au moment de la rédaction) inclut des corrections de bugs pour le rendu des diagrammes.

## Étape 1 : Créer un diagramme circulaire et l'insérer dans le document

La première étape consiste à **créer des objets diagramme circulaire** et à les intégrer dans un fichier Word. Le code ci‑dessous crée un document simple, ajoute un espace réservé pour le diagramme, et insère un diagramme circulaire de taille 400 × 300 pixels.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Pourquoi c'est important :** `builder.insertChart` crée un espace réservé pour le diagramme que Aspose.Words convertit automatiquement en un diagramme OOXML lors de l'enregistrement du document. L'argument `ChartType.PIE` indique à la bibliothèque de rendre un diagramme circulaire, répondant ainsi à l'exigence **insérer un diagramme circulaire**.

## Étape 2 : Exploser une tranche du diagramme circulaire pour mettre en évidence un segment

Explooser une tranche attire l'attention sur un point de données particulier. La ligne suivante explose la première tranche (index 0) de 10 points :

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Vous pouvez modifier l'index pour cibler une autre tranche, ou ajuster la distance d'explosion pour un effet plus subtil. Exploser une tranche est la méthode standard pour **exploser une tranche de diagramme circulaire** dans Aspose.Words.

## Étape 3 : Modifier l'orientation du diagramme en le faisant pivoter

Faire pivoter le diagramme offre une nouvelle perspective visuelle. Utilisez `setRotationAngle` pour faire pivoter l'ensemble du diagramme dans le sens des aiguilles d'une montre (l'angle est mesuré en degrés).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

L'appel ci‑dessus satisfait les exigences **faire pivoter le diagramme circulaire** et **modifier l'orientation du diagramme**. Tout angle compris entre 0 et 360 degrés est accepté.

## Exemple complet exécutable

En rassemblant tous les éléments, voici un programme complet et autonome qui crée un diagramme circulaire, explose une tranche et fait pivoter le diagramme. Exécutez‑le depuis votre IDE ou depuis la ligne de commande avec `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Résultat attendu

* Un fichier nommé **CreatePieChartDemo.docx** apparaît dans le répertoire de travail.
* L'ouverture du fichier dans Microsoft Word affiche un diagramme circulaire de 400 × 300 pixels.
* La première tranche (Q1) est décalée vers l'extérieur de 10 points, créant un effet **exploser une tranche de diagramme circulaire**.
* L'ensemble du diagramme est incliné de 45 degrés, démontrant **modifier l'orientation du diagramme** et **faire pivoter le diagramme circulaire**.

## Variations courantes et cas limites

| Situation | Comment adapter le code |
|-----------|--------------------------|
| **Different chart size** | Change the `400, 300` arguments in `insertChart`. |
| **Multiple series** | Add more `ChartSeries` objects to `chart.getSeries()`. |
| **Explode a different slice** | Use `setExplode(sliceIndex, distance)` with the desired `sliceIndex`. |
| **No rotation needed** | Omit the `setRotationAngle` call or set the angle to `0`. |
| **Export to PDF instead of DOCX** | After building the document, call `doc.save("output.pdf")` with the PDF format. |

> **Attention :** Utiliser une distance d'explosion négative déclenche `IllegalArgumentException`. Fournissez toujours une valeur non négative.

## Astuce de performance

Si vous générez de nombreux diagrammes dans une boucle, réutilisez un seul `DocumentBuilder` et appelez `insertChart` uniquement à chaque itération. Cela réduit la consommation de mémoire et accélère le traitement.

## Conclusion

Vous savez maintenant comment **créer un diagramme circulaire**, **insérer un diagramme circulaire**, **exploser une tranche de diagramme circulaire** et **faire pivoter un diagramme circulaire** en utilisant Aspose.Words for Java. L'exemple complet montre le flux de travail complet — de l'initialisation du document à l'enregistrement d'un fichier visualisant un diagramme circulaire tourné et explosé.

Ensuite, vous pourriez explorer **la modification de l'orientation du diagramme** davantage en appliquant des effets 3 D, ou expérimenter d'autres types de diagrammes tels que **Bar** ou **Line**. Les mêmes modèles d'API s'appliquent, ainsi étendre ce tutoriel est simple.

N'hésitez pas à modifier les données, l'index de la tranche ou l'angle de rotation pour répondre à vos besoins de reporting, et partagez vos résultats avec la communauté !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment insérer un diagramme circulaire dans un document Word avec Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [Comment exploser une tranche de diagramme circulaire en Java – tutoriel de diagramme Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}