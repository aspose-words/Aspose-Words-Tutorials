---
category: general
date: 2026-09-27
description: Apprenez à insérer un diagramme circulaire dans un document Word avec
  Java, à créer un diagramme circulaire dans Word et à afficher les pourcentages sur
  le diagramme pour une meilleure compréhension des données.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: fr
lastmod: 2026-09-27
og_description: Comment insérer un diagramme circulaire dans un document Word avec
  Java. Ce guide vous montre comment créer un diagramme circulaire dans Word, afficher
  les pourcentages sur le diagramme circulaire et ajouter des lignes de repère.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Comment insérer un diagramme circulaire dans un document Word en Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Comment insérer un diagramme circulaire dans un document Word à l’aide de Java
url: /fr/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment insérer un diagramme circulaire dans un document Word avec Java

Si vous devez **insérer un diagramme circulaire** dans un fichier Word, ce guide vous accompagne pas à pas dans le processus complet. Vous verrez comment **créer un diagramme circulaire dans Word**, afficher les pourcentages sur chaque part et ajouter des lignes de repère pour un rendu soigné.

L’automatisation Word peut parfois sembler lourde, mais avec Aspose.Words for Java vous pouvez générer des documents entièrement formatés de façon programmatique. À la fin de ce tutoriel, vous disposerez d’un extrait Java exécutable qui produit un document Word contenant un diagramme circulaire stylisé.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

- Java 17 ou une version ultérieure installée
- Maven ou Gradle pour gérer les dépendances
- Aspose.Words for Java (version 23.11 ou plus récente) ajouté à votre projet
- Une connaissance de base de la syntaxe Java

Aucune expérience préalable avec les API de graphiques n’est requise ; les étapes ci‑dessous couvrent tout, de la configuration du projet à la sortie finale.

## Étape 1 : Configurer la dépendance Maven

Ajoutez la bibliothèque Aspose.Words à votre `pom.xml`. Cette dépendance unique vous donne accès aux classes `Document`, `DocumentBuilder` et aux classes de graphiques.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Si vous utilisez Gradle, l’équivalent est :

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Astuce :** Utilisez la dernière version stable pour bénéficier des corrections de bugs et des nouvelles fonctionnalités de graphiques.

## Étape 2 : Créer un nouveau document et un builder

L’objet `Document` représente le fichier Word, tandis que `DocumentBuilder` vous permet d’insérer du contenu. C’est la base pour **ajouter un graphique à un document Word**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Le builder est maintenant prêt à placer des objets n’importe où dans le document.

## Étape 3 : Insérer un diagramme circulaire

Aspose.Words prend en charge plusieurs types de graphiques ; nous choisissons `ChartType.PIE`. La taille est exprimée en points (1 point = 1/72 pouce).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

À ce stade, le graphique contient une série de données par défaut avec des valeurs factices. Vous pourrez remplacer ces valeurs plus tard si nécessaire.

## Étape 4 : Accéder à la série du graphique

Un diagramme circulaire possède une seule série qui contient les valeurs des parts. Récupérez‑la pour appliquer le formatage.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Étape 5 : Faire exploser la première part

Faire exploser une part attire l’attention sur un point de données particulier. C’est un indicateur visuel courant lorsqu’on veut mettre en avant une métrique clé.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Étape 6 : Afficher les pourcentages sur chaque part

Afficher les pourcentages directement sur le graphique améliore la compréhension des données. Cela répond à l’exigence **afficher les pourcentages sur le diagramme circulaire**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Étape 7 : Ajouter des lignes de repère pour des libellés plus clairs

Les lignes de repère relient les libellés des parts à leurs sections correspondantes, éliminant toute ambiguïté. Cela satisfait **comment ajouter des lignes de repère**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Étape 8 : Enregistrer le document

Enfin, écrivez le document sur le disque. Vous pouvez choisir n’importe quel dossier où vous avez les droits d’écriture.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

L’exécution du programme crée `output/PieFormatted.docx`. Ouvrez le fichier dans Microsoft Word, et vous verrez un diagramme circulaire où :

- La première part est explosée.
- Chaque part affiche sa valeur en pourcentage.
- Des lignes de repère pointent des pourcentages vers les parts correspondantes.

### Résultat attendu

![Diagramme circulaire formaté dans Word](/images/pie-formatted.png){: .center-image alt="Diagramme circulaire formaté inséré dans un document Word"}

La capture d’écran (le texte alternatif utilise le mot‑clé principal) illustre l’apparence finale : un diagramme circulaire propre, axé sur les données, prêt pour les rapports, les propositions ou les tableaux de bord.

## Variations courantes et cas limites

### Modifier les valeurs des parts

Si vous avez besoin de données personnalisées, remplacez les valeurs de la série par défaut :

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Séries multiples (diagramme en anneau)

Alors qu’un simple diagramme circulaire possède une série, Aspose.Words prend également en charge les diagrammes en anneau avec plusieurs séries. Remplacez `ChartType.PIE` par `ChartType.DONUT` et répétez les étapes de configuration des séries.

### Exportation en PDF

Si votre flux de travail en aval nécessite un PDF, appelez `doc.save("output/PieFormatted.pdf");` après la création du graphique. La mise en page visuelle reste identique.

## Listing complet du code source

Voici le fichier Java complet, autonome, que vous pouvez copier‑coller dans votre IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Compilez et exécutez le programme avec `mvn compile exec:java -Dexec.mainClass=PieChartExample` (ou la commande équivalente sous Gradle). Le fichier Word généré contiendra le diagramme circulaire entièrement formaté.

## Conclusion

Vous savez maintenant **comment insérer un diagramme circulaire** dans un document Word avec Java, **comment créer un diagramme circulaire dans Word**, **comment afficher les pourcentages sur le diagramme circulaire**, et **comment ajouter un graphique à un document Word** avec des lignes de repère. L’exemple complet montre chaque étape, explique pourquoi le code est écrit ainsi et propose des astuces de personnalisation.

Ensuite, vous pourrez explorer :

- Ajouter des libellés de données avec des polices personnalisées (**variations d’affichage des pourcentages sur le diagramme circulaire**)
- Combiner plusieurs graphiques dans un même document (**cas d’utilisation d’ajout de graphique à un document Word**)
- Automatiser la génération de rapports avec des tableaux et des graphiques combinés

N’hésitez pas à expérimenter avec les couleurs, l’ordre des parts ou l’exportation en PDF. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un diagramme en colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Masquer les axes du graphique dans un document Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Créer un graphique linéaire dans Word avec Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}