---
category: general
date: 2026-08-07
description: Comment exploser une part de camembert en Java avec Aspose.Words. Apprenez
  à ajouter des lignes de repère au camembert, créer un graphique Word et personnaliser
  les parts du camembert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: fr
lastmod: 2026-08-07
og_description: Comment exploser une part de camembert en Java avec Aspose.Words.
  Ce guide vous montre comment ajouter des lignes de repère au camembert, créer des
  graphiques Word et personnaliser les parts du graphique circulaire pour un impact
  visuel clair.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Comment détacher un segment de camembert en Java – Guide Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Comment exploser une part de camembert en Java – Tutoriel de graphique Aspose.Words
url: /fr/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment exploser une tranche de camembert en Java – Tutoriel de graphique Aspose.Words

Si vous devez savoir **comment exploser une tranche de camembert** dans un document Word en utilisant Java, ce tutoriel vous couvre. Nous vous montrerons également **comment ajouter des lignes de repère aux graphiques en camembert**, **java create word chart** objects, et **customize pie chart slices** pour un résultat soigné. À la fin de ce guide, vous disposerez d’un exemple complet et exécutable que vous pourrez intégrer à n’importe quel projet Java.

![Comment exploser une tranche de camembert en Java – graphique Aspose.Words](/images/pie-chart-exploded.png)

## Prérequis

* Java Development Kit (JDK) 8 ou supérieur.
* Maven ou Gradle pour la gestion des dépendances.
* Une licence Aspose.Words for Java (l'évaluation gratuite fonctionne à des fins d'apprentissage).
* Familiarité de base avec la syntaxe Java et les concepts orientés objet.

> **Astuce :** Bien qu'Aspose.Words propose un essai gratuit, l'achat d'une licence supprime le filigrane d'évaluation des documents générés.

## Ce que couvre ce tutoriel

* Créer un nouveau document Word à partir de zéro.  
* Insérer un **pie chart** à l'aide du `DocumentBuilder`.  
* **Exploding a pie slice** pour mettre en évidence un point de données.  
* **Adding leader lines to pie** pour un étiquetage plus clair.  
* Personnaliser l'apparence des tranches, comme les couleurs et les bordures.  
* Enregistrer le document sur le disque et vérifier le résultat.

---

## Comment exploser une tranche de camembert avec Aspose.Words en Java

La première étape consiste à configurer l'objet graphique et à exploser la tranche souhaitée. Aspose.Words expose le graphique via la classe `Shape`, et chaque tranche est un `ChartPoint`. En définissant la propriété `Explosion`, vous contrôlez la distance à laquelle la tranche se déplace vers l'extérieur.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Pourquoi cela fonctionne :**  
`setExplosion(20)` indique au moteur du graphique de décaler la tranche de 20 points par rapport au centre du graphique. La valeur est relative ; des nombres plus grands créent un effet plus spectaculaire. Vous pouvez exploser n'importe quelle tranche en modifiant l'index (`get(1)`, `get(2)`, …).

## Ajouter des lignes de repère au camembert pour des libellés plus clairs

Les lignes de repère relient le libellé d'une tranche à son bord, ce qui est particulièrement utile lorsque les tranches sont éclatées ou lorsque le graphique contient de nombreuses petites sections. L'appel `setLeaderLines(true)` active cette fonctionnalité pour l'ensemble de la série.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Pourquoi vous avez besoin de lignes de repère :**  
Lorsqu'une tranche est éclatée, le libellé par défaut peut chevaucher d'autres éléments. Les lignes de repère maintiennent la lisibilité du libellé en dessinant une courte ligne de la tranche vers la zone de texte.

## Java create Word chart – insertion de séries de données

Un graphique sans données n'est pas très utile. Vous devez remplir les séries avec des catégories et des valeurs. Ci-dessous, nous ajoutons trois catégories représentant la part de marché.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Explication :**  
`ChartSeries` contient à la fois les catégories (les noms des tranches) et les valeurs numériques. Activer `ShowCategoryName` et `ShowPercentage` rend le graphique auto‑explicatif, ce qui se combine bien avec les lignes de repère que nous avons ajoutées précédemment.

## Personnaliser les tranches du graphique en camembert au‑delà de l'explosion

Au‑delà de l'explosion d'une tranche, vous souhaitez souvent ajuster les couleurs, les bordures, voire masquer complètement une tranche. L'extrait suivant montre trois personnalisations courantes :

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Pourquoi personnaliser les tranches :**  
Des couleurs personnalisées permettent au graphique de correspondre à l'identité visuelle de l'entreprise, tandis que les bordures améliorent la lisibilité sur les pages imprimées. Masquer une tranche est utile lorsque vous souhaitez conserver le modèle de données intact mais omettre temporairement une catégorie de la sortie visuelle.

## Enregistrer le document et vérifier le résultat

Enfin, écrivez le document sur le disque. Vous pouvez ouvrir le `.docx` généré dans Microsoft Word, LibreOffice ou tout visualiseur prenant en charge le format.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Résultat attendu :**  
Lorsque vous ouvrez `PieChartDemo.docx`, vous voyez un graphique en camembert où la première tranche (Product A) est éclatée vers l'extérieur, les lignes de repère pointent de chaque tranche vers son libellé, et les tranches apparaissent dans les couleurs personnalisées vert, bleu et orange. La tranche masquée (Product C) ne sera pas visible, mais les pourcentages s'additionneront toujours à 100 % car les données restent dans les séries du graphique.

---

## Exemple complet et exécutable

Voici le programme complet que vous pouvez copier, coller et exécuter après avoir ajouté la dépendance Aspose.Words à votre projet.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dépendance (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer un graphique en colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Comment charger des documents Word avec Aspose.Words Java : guide complet](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}