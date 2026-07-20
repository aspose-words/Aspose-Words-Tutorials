---
category: general
date: 2026-07-20
description: Insérer un diagramme circulaire en Java avec un guide étape par étape.
  Apprenez comment éclater une tranche, comment faire pivoter le diagramme circulaire,
  mettre en évidence une tranche du diagramme circulaire et personnaliser une tranche
  du diagramme circulaire.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: fr
lastmod: 2026-07-20
og_description: Insérer un diagramme circulaire en Java et maîtriser comment éclater
  une tranche, comment faire pivoter le diagramme circulaire, mettre en évidence une
  tranche du diagramme circulaire et personnaliser la tranche du diagramme circulaire
  pour des rapports visuels soignés.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Insérer un camembert en Java – Exploser, faire pivoter et mettre en évidence
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Insérer un diagramme circulaire en Java – Éclater, faire pivoter et mettre
  en évidence les parts
url: /fr/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un diagramme circulaire dans Java – Exploser, faire pivoter et mettre en évidence les parts

Vous avez déjà eu besoin d’**insérer un diagramme circulaire** dans un rapport Java mais vous ne saviez pas comment faire ressortir une part ? Vous n’êtes pas seul. Que vous construisiez un tableau de bord, génériez une facture ou visualisiez simplement les résultats d’une enquête, un diagramme circulaire bien stylisé peut transformer des chiffres bruts en informations immédiatement compréhensibles.

Dans ce tutoriel vous verrez un exemple complet, prêt à l’exécution, qui montre comment insérer un diagramme circulaire, **comment exploser une part**, **comment faire pivoter le diagramme circulaire**, et même **mettre en évidence une part du diagramme circulaire** avec des couleurs personnalisées. À la fin, vous disposerez d’un extrait réutilisable que vous pourrez intégrer dans n’importe quel projet Java utilisant la populaire bibliothèque *JFreeChart* (ou toute API similaire).

## Prérequis

- Java 17 ou supérieur (le code compile avec des versions antérieures, mais nous utiliserons la syntaxe moderne `var` pour plus de concision).  
- Maven ou Gradle pour récupérer la dépendance `org.jfree:jfreechart`.  
- Une compréhension de base des classes Java et du concept de constructeur de diagramme.  

Si vous n’avez jamais ajouté une bibliothèque à un projet Maven, insérez simplement ceci dans votre `pom.xml` :

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

C’est tout — aucune configuration supplémentaire requise.

## Étape 1 : Insérer le diagramme circulaire – Créer le builder et l’objet Chart

Première chose à faire : nous avons besoin d’un *builder* (pensez à une usine) qui sait comment produire des diagrammes. Dans JFreeChart, le `ChartFactory` fait le gros du travail.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Pourquoi commencer par le jeu de données ? Parce que le diagramme lui‑même n’est qu’un enveloppe visuelle autour des nombres. En **insérant le diagramme circulaire** ici, nous disposons déjà d’une toile de 400 × 300 (la taille sera appliquée plus tard lors du rendu en image).

## Étape 2 : Comment exploser une part – Mettre en avant le premier segment

Maintenant que le diagramme existe, faisons ressortir la première part. Exploser une part la décale légèrement du cercle, attirant ainsi le regard du lecteur.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Remarquez que nous utilisons la phrase **how to explode slice** dans le nom de la méthode ; cela rend l’intention très claire. La méthode `setExplodePercent` prend une clé (l’étiquette de la part) et un pourcentage, vous permettant d’ajuster la distance de « pop‑out » selon vos besoins.

## Étape 3 : Comment faire pivoter le diagramme circulaire – Modifier l’angle de départ

Un diagramme circulaire par défaut commence à la position 12 heures. Parfois, vous voulez que la première part débute ailleurs — peut‑être pour s’aligner avec une maquette de design ou correspondre à un autre diagramme.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Appeler `rotateChart(chart, 45)` fait pivoter l’ensemble du diagramme afin que la part « Apples » commence à un angle de 45 degrés, exactement ce que la consigne **how to rotate pie chart** demande.

## Étape 4 : Mettre en évidence une part du diagramme circulaire – Couleurs et libellés personnalisés

En plus d’exploser, vous pourriez vouloir donner à une part une couleur unique ou un libellé en gras pour réellement **highlight pie chart slice**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Ici nous avons **customize pie chart slice** en modifiant sa couleur (`paint`) et le style du libellé. N’hésitez pas à changer la couleur ou la police pour correspondre à votre palette de marque.

## Étape 5 : Rendre le diagramme en image (optionnel mais pratique)

La plupart des applications réelles ont besoin du diagramme sous forme de PNG, JPEG, voire PDF. Voici une façon rapide d’écrire le diagramme dans un fichier.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

L’exécution du flux complet produira un PNG 400 × 300 qui ressemble à ceci :

![Insert pie chart example](image.png){: alt="Exemple d’insertion de diagramme circulaire montrant une part explosée et pivotée"}

## Exemple complet fonctionnel

En rassemblant le tout, voici une méthode `main` que vous pouvez copier‑coller dans une nouvelle classe Java et exécuter :

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Résultat attendu

L’exécution du programme crée un fichier nommé **fruit-pie.png**. Ouvrez‑le et vous verrez :

- Un diagramme circulaire 400 × 300 intitulé « Fruit Distribution ».  
- La part « Apples » explosée vers l’extérieur de 15 %.  
- L’ensemble du diagramme pivoté de sorte que « Apples » commence à la position de 45 degrés.  
- La part explosée

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Insert Scatter Chart](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Insert Area Chart](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}