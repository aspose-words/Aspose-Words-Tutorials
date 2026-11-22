---
category: general
date: 2026-11-22
description: Créez un diagramme circulaire en Java et apprenez à définir la taille
  du graphique, ajouter des étiquettes de données, afficher les pourcentages et faire
  pivoter la première tranche pour un impact visuel clair.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: fr
lastmod: 2026-11-22
og_description: Créer un diagramme circulaire en Java, puis définir la taille du graphique,
  afficher les pourcentages sur les libellés de données et faire pivoter la première
  tranche — le tout dans un exemple unique et exécutable.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Créer un diagramme circulaire avec taille personnalisée, libellés et rotation
  en Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Créer un diagramme circulaire avec taille personnalisée, étiquettes de données
  et rotation en Java
url: /fr/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un diagramme circulaire avec taille personnalisée, étiquettes de données et rotation en Java

Si vous devez **create pie chart** en Java, ce guide vous accompagne tout au long du processus. Vous apprendrez comment **set chart size**, activer **show percentages pie chart**, ajouter **data labels pie chart**, et **rotate pie chart slice** afin que la première tranche commence à un angle de 45 degrés.

L’exemple utilise **Aspose.Slides for Java**, une bibliothèque largement utilisée pour manipuler les fichiers PowerPoint. Les mêmes concepts s’appliquent à d’autres bibliothèques de graphiques ; il suffit de remplacer les appels d’API par les équivalents de votre boîte à outils.

## Prérequis

* Java 17 ou version ultérieure installé  
* Maven 3.8+ (ou Gradle) pour la gestion des dépendances  
* Une compréhension de base de la syntaxe Java  
* Accès au binaire Aspose.Slides for Java (vous pouvez obtenir un essai gratuit sur le site officiel)

Ajoutez la dépendance à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Créer un diagramme circulaire – exemple complet

Le programme suivant crée une diapositive PowerPoint contenant un diagramme circulaire avec une taille personnalisée, des étiquettes de données en pourcentage et une première tranche tournée.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Pourquoi chaque étape est importante

| Étape | Objectif | Comment cela se rapporte aux mots‑clés |
|------|----------|----------------------------------------|
| **Insérer le graphique** | **Create pie chart** – l’objet principal qui rendra le visuel. | Satisfait directement l’exigence *create pie chart*. |
| **Définir les dimensions** | L’appel `addChart(..., 400, 300)` montre **set chart size**. | Contrôle la largeur (400 px) et la hauteur (300 px). |
| **Afficher les pourcentages** | `setShowPercentage(true)` fait que le graphique **show percentages pie chart** sur chaque tranche. | Les utilisateurs ont souvent besoin des pourcentages plutôt que des valeurs brutes. |
| **Ajouter des étiquettes de données** | La configuration `DataLabelFormat` ajoute **data labels pie chart** avec la visibilité souhaitée. | Les étiquettes améliorent la lisibilité et sont personnalisables. |
| **Faire pivoter la tranche** | `setFirstSliceAngle(45)` fait pivoter le graphique afin que la première tranche commence à un angle de 45 degrés, remplissant **rotate pie chart slice**. | Améliore l’accent visuel sur une tranche particulière. |

## Décomposition étape par étape

### 1. Insérer un diagramme circulaire et définir la taille du graphique

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*La méthode `addChart` crée le graphique et définit simultanément **set chart size** à 400 × 300 points.*  
Si vous avez besoin d’une taille différente, ajustez les deux derniers arguments.

### 2. Remplir le graphique avec des données

La démonstration ajoute trois catégories et une seule série. Remplacez les nombres codés en dur par des données provenant d’une base de données, d’un CSV ou d’une saisie utilisateur selon les besoins.

### 3. Afficher les pourcentages sur chaque tranche

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Activer `setShowPercentage(true)` garantit que le graphique **show percentages pie chart** calcule automatiquement la part de chaque tranche dans le total.*

### 4. Ajouter des étiquettes de données détaillées

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Vous pouvez activer d’autres options d’étiquette (`setShowValue`, `setShowSeriesName`, etc.) pour personnaliser l’expérience **add data labels pie chart**.

### 5. Faire pivoter la première tranche

```java
chart.setFirstSliceAngle(45);
```

*Appeler `setFirstSliceAngle(45)` **rotate pie chart slice** afin que le premier segment commence à un angle de 45 degrés, le faisant ressortir.*

### 6. Enregistrer et visualiser le résultat

L’exécution du programme produit `output/PieChartDemo.pptx`. Ouvrez-le dans PowerPoint ou tout visualiseur compatible pour voir le diagramme circulaire final :

![Create pie chart example](images/pie_chart_example.png){.align-center alt="Capture d’écran d’un diagramme circulaire créé avec taille personnalisée, étiquettes de pourcentage et première tranche tournée"}

L’image ci‑dessus montre le résultat du **create pie chart**, confirmant que la taille, les étiquettes, les pourcentages et la rotation sont correctement appliqués.

## Variantes courantes et cas limites

| Situation | Ajustement |
|-----------|------------|
| **Dimensions du graphique différentes** | Modifiez les paramètres de largeur/hauteur dans `addChart`. |
| **Séries multiples** | Ajoutez des objets `IChartSeries` supplémentaires ; chaque série peut avoir ses propres paramètres d’étiquette. |
| **Format d’étiquette personnalisé** | Utilisez `series.getDataLabelFormat().setNumberFormat("0.0%")` pour contrôler le nombre de décimales. |
| **Faire pivoter à un autre angle** | Passez n’importe quel entier (0‑360) à `setFirstSliceAngle`. |
| **Exporter en image** | Après l’enregistrement, appelez `chart.writeAsSvg(outPath)` ou `chart.writeAsPng(outPath)` pour une version raster. |

> **Pro tip:** Si vous prévoyez de générer de nombreux graphiques dans une boucle, réutilisez le même objet `Presentation` et ne remplacez que les données du graphique. Cela réduit la consommation de mémoire et accélère le traitement.

## Conclusion

Vous savez maintenant comment **create pie chart** en Java, **set chart size**, activer **show percentages pie chart**, **add data labels pie chart**, et **rotate pie chart slice** pour un meilleur accent visuel. L’exemple complet et exécutable montre chaque étape, de l’initialisation à l’enregistrement du fichier PowerPoint final.

### Et après ?

* Explorez d’autres types de graphiques (Bar, Line, Area) en utilisant le même enum `ChartType`.  
* Combinez plusieurs graphiques sur une même diapositive pour des tableaux de bord.  
* Exportez les graphiques en PNG ou SVG pour les utiliser dans des applications web.  

N’hésitez pas à expérimenter avec les couleurs, les légendes et les effets d’animation — vos visualisations de données ne sont limitées que par votre imagination. Bon charting !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [comment insérer un diagramme circulaire dans Word – ajouter le pourcentage d’étiquette de données](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Comment éclater une tranche de diagramme circulaire en Java – tutoriel de graphique Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Insérer un diagramme circulaire en Java – éclater, pivoter et mettre en évidence les tranches](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}