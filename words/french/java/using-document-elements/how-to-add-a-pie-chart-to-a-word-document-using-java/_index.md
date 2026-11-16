---
category: general
date: 2026-11-15
description: Apprenez à ajouter un diagramme circulaire à un document Word avec Aspose.Words
  for Java. Inclut la conversion en anneau, une tranche éclatée et un exemple complet
  de code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: fr
lastmod: 2026-11-15
og_description: Ajoutez un diagramme circulaire à un document Word à l’aide d’Aspose.Words
  for Java. Ce tutoriel montre comment éclater une tranche et transformer le graphique
  en diagramme en anneau.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Ajouter un diagramme circulaire à un document Word avec Java – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Comment ajouter un diagramme circulaire à un document Word avec Java
url: /fr/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter un diagramme circulaire à un document Word – guide complet Java

Si vous devez **ajouter un diagramme circulaire à un document Word** de façon programmatique, ce tutoriel vous montre exactement comment le faire avec Aspose.Words for Java. Vous verrez le flux complet : chargement d’un DOCX, création d’un diagramme circulaire, éclatement de la première tranche et conversion du diagramme en anneau en définissant une taille de trou.

Le guide couvre également les variantes courantes — comme l’ajout de plusieurs séries, la personnalisation des couleurs et la gestion de documents contenant déjà des diagrammes — afin que vous puissiez adapter le code à des projets réels tels que les rapports automatisés ou les présentations dynamiques.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java 17 ou ultérieur (le code compile également avec JDK 11+)
* Maven 3.6+ ou Gradle pour la gestion des dépendances
* Une licence Aspose.Words for Java (l’essai gratuit suffit pour les tests)
* Une compréhension de base de la syntaxe Java et de la structure d’un projet Maven

## Étape 1 : Configurer le projet Maven et importer Aspose.Words

Créez un nouveau projet Maven (ou ajoutez‑le à un projet existant) et incluez la dépendance Aspose.Words :

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Astuce :** Si vous utilisez Gradle, l’entrée équivalente est `implementation 'com.aspose:aspose-words:24.9'`.

La dépendance apporte les classes `Document`, `Chart` et `ChartType` dont vous aurez besoin pour manipuler les diagrammes.

## Étape 2 : Charger le document cible

Vous pouvez partir d’un fichier `.docx` existant ou créer un nouveau document vierge. L’exemple ci‑dessous charge un modèle nommé `input.docx` situé dans le dossier `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Si le fichier n’existe pas, Aspose.Words créera automatiquement un nouveau document vide lorsque vous appellerez `new Document()` sans nom de fichier.

## Étape 3 : Créer un diagramme circulaire et l’insérer dans le document

Aspose.Words considère un diagramme comme une forme qui peut être placée partout où un paragraphe peut apparaître. Le code suivant crée un **diagramme circulaire**, ajoute une série de données unique et insère le diagramme après le premier paragraphe.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Pourquoi cette étape est importante :**  
* `ChartType.PIE` indique à Aspose.Words de rendre un diagramme circulaire traditionnel.  
* Ajouter une série avec à la fois des libellés de catégorie et des valeurs numériques remplit automatiquement les tranches.  
* Insérer le diagramme en tant qu’enfant d’un `Paragraph` maintient le flux du document intact.

## Étape 4 : Éclater la première tranche pour la mettre en évidence

Une *tranche éclatée* attire l’attention sur un point de données particulier. L’API expose `setExplode(boolean)` sur un objet `ChartSeries`. Le définir sur la première série (indice 0) fait sortir la première tranche.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Question fréquente :** *Et si j’ai plusieurs séries ?*  
> Vous pouvez cibler une série spécifique par son indice, par ex. `pieChart.getSeries().get(1).setExplode(true)` pour la deuxième série.

## Étape 5 : Convertir le diagramme circulaire en anneau en définissant une taille de trou

Un diagramme en anneau est essentiellement un diagramme circulaire avec un centre creux. Aspose.Words vous permet de définir la taille du trou en pourcentage du rayon du diagramme.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

La méthode `setHoleSize` accepte des valeurs de **0** (diagramme circulaire normal) à **100** (complètement vide). Une valeur autour de **30‑40** donne un anneau visuellement équilibré.

## Étape 6 : Enregistrer et vérifier le résultat

Après toutes les modifications, enregistrez le document. La ligne suivante écrit le fichier dans le dossier `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Résultat attendu

Ouvrez `final-pie-doughnut.docx` dans Microsoft Word :

* Un diagramme en anneau apparaît à l’endroit du premier paragraphe.  
* La tranche « Apples » est éclatée (légèrement séparée du reste).  
* Le diagramme montre quatre tranches libellées *Apples*, *Bananas*, *Cherries*, *Dates* avec les pourcentages que vous avez fournis.

Si vous préférez une sortie PDF, changez le `SaveFormat` en `SaveFormat.PDF`.

## Gestion des cas limites et des variantes

### Ajout de plusieurs séries

Si vous avez besoin de plusieurs séries (par ex. anneau empilé), ajoutez‑les séquentiellement :

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Couleurs personnalisées

Vous pouvez attribuer une couleur à chaque tranche via `ChartDataPoint.setFillFormat().setSolidFillColor()` :

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Travailler avec un diagramme existant

Si le document contient déjà un diagramme et que vous ne souhaitez que le modifier, localisez la forme du diagramme :

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Gestion de la licence

Aspose.Words nécessite une licence pour une utilisation en production. Placez votre fichier `Aspose.Words.lic` dans le classpath et chargez‑le au démarrage de l’application :

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Ne pas définir de licence ajoutera un filigrane au document généré.

## Exemple complet, exécutable

Voici la classe Java complète qui intègre chaque étape décrite. Copiez‑la dans `src/main/java/com/example/AddPieChart.java` et exécutez `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

L’exécution du programme produit le diagramme en anneau décrit précédemment. Ajustez les `categories`, `values` ou `holeSize` selon vos données.

## Conclusion

Vous savez maintenant comment **ajouter un diagramme circulaire à un document Word** en utilisant Java et Aspose.Words. Le tutoriel a couvert le chargement d’un document, la création d’un diagramme circulaire, l’éclatement d’une tranche, la transformation du diagramme en anneau, ainsi que la gestion des variantes courantes telles que plusieurs séries, les couleurs personnalisées et les diagrammes existants. Avec cette base, vous pouvez créer des outils de reporting automatisés, générer des présentations dynamiques ou intégrer des visualisations riches directement dans des fichiers Word.

### Que explorer ensuite

* **add bar chart to Word document** – étapes similaires mais en utilisant `ChartType.BAR`.  
* **customize chart legends and titles** – utilisez `pieChart.getTitle().setText("…")` et `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **export the Word document as PDF** – changez le `SaveFormat` en `PDF` pour des fichiers prêts à la distribution.  
* **populate chart data from a database** – remplacez les tableaux statiques par les résultats d’une requête JDBC.

N’hésitez pas à expérimenter avec différents types de diagrammes, sources de données et options de style. Bon codage !

## What Should You Learn Next?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}