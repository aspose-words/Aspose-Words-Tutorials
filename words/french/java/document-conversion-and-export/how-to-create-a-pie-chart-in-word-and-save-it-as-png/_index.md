---
category: general
date: 2026-10-07
description: Apprenez à créer un diagramme circulaire dans Word, à ajouter des séries
  de données et à enregistrer le graphique au format PNG en utilisant Java. Suivez
  le guide étape par étape pour des résultats rapides.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: fr
lastmod: 2026-10-07
og_description: 'Créer rapidement un diagramme circulaire dans Word : ce tutoriel
  montre comment ajouter des séries de données, générer le graphique et enregistrer
  le graphique Word sous forme d’image (PNG). Suivez l’exemple complet de code.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Créer un diagramme circulaire dans Word et l’exporter au format PNG – guide
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Comment créer un diagramme circulaire dans Word et l’enregistrer au format
  PNG
url: /fr/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un diagramme circulaire dans Word et l’enregistrer en PNG

Si vous devez **créer des diagrammes circulaires** dans un fichier Microsoft Word, ce guide vous montre exactement comment le faire avec Java. Vous apprendrez également comment **ajouter des séries de données** au diagramme et **enregistrer le diagramme en PNG** afin que le visuel puisse être réutilisé en dehors de Word.

Générer un diagramme directement dans un document vous évite d’exporter les données vers un outil graphique séparé. À la fin de ce tutoriel, vous disposerez d’un fichier Word entièrement fonctionnel contenant un diagramme circulaire et une image PNG correspondante sur le disque.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java 17 ou version ultérieure installé.
* Le **GroupDocs.Viewer for Java** (ou une bibliothèque compatible qui fournit les classes `Document`, `Chart`, `ChartType` et `ImageSaveOptions`).
* Un projet Maven ou Gradle où vous pouvez ajouter la dépendance de la bibliothèque.
* Un document Word d’entrée (`input.docx`) situé dans un dossier que vous pouvez référencer depuis le code.

Si vous utilisez Maven, ajoutez la dépendance (remplacez `VERSION` par la dernière version) :

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Comment créer un diagramme circulaire dans Word

Le cœur de la solution repose sur trois actions :

1. Charger le fichier source `.docx`.
2. **Ajouter des séries de données** à un nouvel objet `Chart` de type `PIE`.
3. **Enregistrer le diagramme en PNG** afin d’obtenir un fichier image à côté du document Word.

Chaque étape est expliquée en détail ci‑dessous, suivie du code Java exact dont vous avez besoin.

### Étape 1 : Charger le document source

Vous devez ouvrir le fichier Word qui contiendra le diagramme. La classe `Document` lit le contenu du `.docx` en mémoire.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Pourquoi c’est important* : charger le document crée un modèle mutable. Toutes les opérations de diagramme suivantes modifient cette représentation en mémoire, que vous persistez ensuite sur le disque.

### Étape 2 : Ajouter des séries de données au diagramme

Créer un **diagramme circulaire** commence par une instance `Chart`. Le constructeur reçoit le `Document` parent et le type de diagramme (`ChartType.PIE`). Une fois l’objet diagramme créé, vous le remplissez avec des valeurs numériques et des libellés optionnels.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Pourquoi c’est important* : la méthode `add` **ajoute des séries de données** au diagramme. Chaque entrée dans `values` devient une part du cercle, tandis que `categories` fournit les libellés de légende. Vous pouvez fournir n’importe quel nombre de points ; la bibliothèque calculera automatiquement les angles des parts.

### Étape 3 : Enregistrer le diagramme en PNG

Une fois le diagramme intégré au document, vous pouvez exporter la représentation visuelle. La méthode `save` de l’objet diagramme sous‑jacent écrit un fichier PNG sur le système de fichiers.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Pourquoi c’est important* : enregistrer le diagramme en PNG vous fournit une image raster qui peut être intégrée dans des pages web, des e‑mails ou des rapports sans nécessiter le fichier Word original. L’objet `ImageSaveOptions` vous permet de contrôler le format, la résolution et d’autres paramètres d’exportation.

## Générer un diagramme circulaire dans Word – personnaliser l’apparence

Au‑delà des étapes de base, vous pouvez souhaiter personnaliser les couleurs, les titres ou les libellés de données. La plupart des bibliothèques exposent un objet `ChartOptions` ou similaire. Voici un exemple rapide qui ajoute un titre et modifie les couleurs des parts :

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Ces personnalisations sont facultatives mais illustrent comment vous pouvez **générer un diagramme circulaire dans Word** qui correspond à votre identité visuelle.

## Enregistrer le diagramme Word en image – approches alternatives

Si vous avez uniquement besoin de l’image et non du diagramme dans le document, vous pouvez ignorer l’insertion de la forme du diagramme dans le fichier Word et appeler directement la méthode `save` après avoir créé le diagramme. Le code reste identique ; vous omettez simplement les étapes qui ajoutent le diagramme au corps du document.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

Cette technique est utile lorsque vous générez de nombreux diagrammes dans un processus par lots et que vous ne vous souciez que de la sortie PNG.

## Exemple complet et exécutable

Copiez la classe suivante dans votre projet, ajustez les chemins de fichiers, puis exécutez‑la. Le programme :

1. Charger `input.docx`.
2. **Créer un diagramme circulaire**, **ajouter des séries de données**, et l’intégrer dans le document.
3. **Enregistrer le diagramme en PNG** (`radial.png`).
4. Enregistrer le fichier Word modifié sous `output.docx`.



## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un diagramme en colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Créer un diagramme de dispersion Word avec Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insérer un diagramme en colonnes dans Word avec Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}