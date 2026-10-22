---
category: general
date: 2026-09-18
description: Apprenez à créer un document Word et à insérer un graphique circulaire
  avec Aspose.Words pour Java. Comprend les étapes de rotation du graphique circulaire
  et de génération du fichier Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: fr
lastmod: 2026-09-18
og_description: Créez un document Word et insérez un diagramme circulaire à l'aide
  de Java. Suivez ce guide pour faire pivoter le diagramme circulaire, éclater les
  parts et générer un fichier Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Créer un document Word avec un diagramme circulaire – guide Java étape par
  étape
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Comment créer un document Word avec un diagramme circulaire en Java
url: /fr/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word avec un diagramme circulaire en Java

Si vous devez **créer un document Word** qui visualise des données, ce guide vous montre comment le faire avec Aspose.Words for Java. Vous apprendrez à insérer un diagramme circulaire, à éclater une tranche, à faire pivoter le diagramme, puis à **générer un fichier Word** que vous pourrez ouvrir dans Microsoft Word.

Créer des rapports qui combinent texte et graphiques ne nécessite pas d’outil graphique séparé. À la fin de ce tutoriel, vous disposerez d’un programme complet et exécutable qui crée un fichier .docx contenant un diagramme circulaire entièrement configuré.

## Prérequis

- Java 17 ou version ultérieure (le code se compile également avec Java 8+)
- Maven ou Gradle pour la gestion des dépendances
- Licence Aspose.Words for Java (l’essai gratuit suffit pour cet exemple)
- Familiarité de base avec la syntaxe Java

## Étape 1 : Configurer le projet Maven

Créez un nouveau projet Maven et ajoutez la dépendance Aspose.Words dans le fichier `pom.xml` :

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Astuce :** Gardez le numéro de version à jour ; les versions plus récentes ajoutent des améliorations et des corrections de bugs liées aux types de graphiques.

## Étape 2 : Créer un nouveau document Word

La première opération lorsque vous **créez un document Word** de façon programmatique consiste à instancier un objet `Document`. Cet objet représente l’ensemble du fichier .docx en mémoire.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

La classe `Document` est le point d’entrée pour toutes les fonctionnalités de traitement de texte. Aucun fichier n’est encore écrit sur le disque ; tout se passe en RAM jusqu’à l’appel à `save`.

## Étape 3 : Insérer un diagramme circulaire

Un `DocumentBuilder` vous permet d’ajouter du contenu au document. Avec `insertChart` vous pouvez **insérer des diagrammes circulaires** directement.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` indique à Aspose.Words de créer un diagramme circulaire. Les dimensions sont exprimées en points (1 pt ≈ 1/72 in). Après cet appel, le diagramme apparaît dans un nouveau paragraphe.

## Étape 4 : Remplir le diagramme avec des données

Un diagramme circulaire nécessite une série de valeurs. Ici nous ajoutons trois catégories : « Apples », « Bananas » et « Cherries ».

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

La méthode `add` construit la série et crée automatiquement les entrées de légende. Vous pouvez réutiliser ce modèle pour tout jeu de données numériques.

## Étape 5 : Mettre en évidence la première tranche

Éclater une tranche attire l’attention sur une valeur particulière. La première tranche (index 0) est éclatée de 20 points.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Définir `explode` sur la série affecte l’ensemble du diagramme, de sorte que seul le premier point de données est décalé.

## Étape 6 : Faire pivoter un diagramme circulaire

Faire pivoter le diagramme améliore l’équilibre visuel, surtout lorsque la plus grande tranche n’est pas en haut. La méthode `setRotationAngle` attend un angle en degrés.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Une rotation de 45° déplace l’angle de départ dans le sens des aiguilles d’une montre, rendant le diagramme plus lisible dans de nombreuses mises en page.

## Étape 7 : Enregistrer le document et générer un fichier Word

Enfin, écrivez le document sur le disque. Cette étape **génère un fichier Word** qui peut être ouvert avec Microsoft Word, LibreOffice ou tout visualiseur compatible.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

La méthode `save` détecte automatiquement l’extension .docx et écrit un package compatible Word. Le dossier `output` doit exister ou vous pouvez le créer programmatique­ment.

### Résultat attendu

Après l’exécution du programme, ouvrez `output/PieChart.docx`. Vous devriez voir :

- Une page unique contenant un diagramme circulaire de 400 × 300 pt.
- La tranche « Apples » éclatée vers l’extérieur de 20 pt.
- L’ensemble du diagramme pivoté de 45° dans le sens des aiguilles d’une montre.
- Une légende correspondant aux trois catégories de fruits.

## Variantes courantes et cas limites

### Insertion de plusieurs diagrammes

Si vous avez besoin de plusieurs diagrammes, appelez à nouveau `builder.insertChart` après avoir déplacé le curseur :

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Modification des couleurs du diagramme

Vous pouvez personnaliser les couleurs des tranches via la collection `getPoints()` de la série :

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Gestion de grands ensembles de données

Pour des ensembles contenant plus de 10 tranches, envisagez d’utiliser un diagramme en anneau (`ChartType.DOUGHNUT`) afin de garder la visualisation claire.

## Conclusion

Vous savez maintenant comment **créer un document Word**, **insérer un diagramme circulaire**, **faire pivoter le diagramme circulaire** et **générer un fichier Word** en utilisant Aspose.Words for Java. La solution complète montre le flux de travail complet, de l’initialisation du document à la sortie finale du fichier, en couvrant le « comment » et le « pourquoi » de chaque étape.

Ensuite, explorez des sujets connexes tels que **comment créer des données de diagramme circulaire** à partir d’une base de données, ajouter des libellés de données, ou exporter le diagramme en image. Expérimentez avec différents types de graphiques (barres, lignes, anneau) pour élargir votre boîte à outils d’automatisation Word.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}