---
category: general
date: 2026-07-29
description: Insérez un diagramme circulaire à l'aide d'Aspose.Words pour Java et
  apprenez comment générer un diagramme en anneau, formater le diagramme circulaire,
  formater le diagramme Word et personnaliser la taille du diagramme.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: fr
lastmod: 2026-07-29
og_description: Insérez un graphique circulaire avec Aspose.Words pour Java et apprenez
  rapidement à créer un graphique en anneau, à formater le graphique circulaire, à
  formater le graphique Word et à personnaliser la taille du graphique pour des documents
  professionnels.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Insérer un diagramme circulaire en Java – Tutoriel complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Insérer un diagramme circulaire en Java avec Aspose.Words – Guide complet
url: /fr/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un diagramme circulaire dans Java avec Aspose.Words – Guide complet

Vous êtes-vous déjà demandé comment **insérer un diagramme circulaire** dans un document Word depuis du code Java ? Vous n'êtes pas le seul — de nombreux développeurs rencontrent cet obstacle lorsqu'ils ont besoin d'une façon rapide et programmatique de visualiser des données. La bonne nouvelle ? Avec Aspose.Words for Java, vous pouvez le faire en quelques lignes, et en même temps vous pouvez également **générer un diagramme en anneau**, **formater le diagramme circulaire**, **formater le diagramme Word**, et **personnaliser la taille du diagramme** pour correspondre à votre identité visuelle.

Dans ce tutoriel, nous parcourrons un exemple réel qui commence par créer un document vierge, y insérer un diagramme circulaire, ajuster quelques propriétés visuelles, puis enregistrer le fichier. À la fin, vous disposerez d’un extrait réutilisable que vous pourrez coller dans n’importe quel projet Java nécessitant l’automatisation de diagrammes. Pas de bibliothèques supplémentaires, pas de manipulation manuelle d’Interop Office — juste du Java propre et compilé.

## Ce dont vous avez besoin

- **Java 17** (ou toute version récente du JDK ; l’API est rétrocompatible)
- **Aspose.Words for Java** 22.12 ou plus récent – vous pouvez récupérer l’artifact Maven ou le .jar depuis le site Aspose.
- Un IDE modeste (IntelliJ IDEA, Eclipse, VS Code…) – tout ce qui vous permet d’exécuter une méthode `main`.
- Facultatif : un fichier de licence si vous ne voulez pas le filigrane d’évaluation.

Si vous avez tout cela, passons directement au code.

## Étape 1 : Insérer un diagramme circulaire avec Aspose.Words

La première chose que nous faisons est **insérer un diagramme circulaire** dans un document vierge. Cette étape prépare le terrain pour tout le reste, car l’objet diagramme nous donne accès aux séries, aux points de données et aux ajustements visuels.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Pourquoi c’est important :** `DocumentBuilder.insertChart` crée non seulement le diagramme mais renvoie également un objet `Chart` que nous pouvons manipuler. Les arguments de largeur et de hauteur vous permettent de **personnaliser la taille du diagramme** dès la création, évitant ainsi un redimensionnement ultérieur.

## Étape 2 : Générer un diagramme en anneau (optionnel)

Si votre conception nécessite un trou au centre—pensez à un diagramme en anneau classique—Aspose le fait en une seule ligne. La même instance `Chart` peut être convertie d’un diagramme circulaire ordinaire à un diagramme en anneau en ajustant la taille du trou.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Astuce :** La taille du trou ne prend effet que pour `ChartType.DONUT`. Si vous conservez le type `PIE`, l’appel est ignoré, alors n’hésitez pas à expérimenter.

## Étape 3 : Formater les tranches du diagramme circulaire

Un bon rendu met souvent en avant une tranche particulière. Ici nous **formatons le diagramme circulaire** en faisant exploser la première tranche de 20 points vers l’extérieur. Cela attire l’œil du lecteur vers le point de donnée le plus important.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Pro tip :** Vous pouvez parcourir `pieChart.getSeries()` si vous avez plusieurs séries et définir des couleurs, bordures ou libellés de données individuels. C’est ainsi que l’on **formate le diagramme Word** avec un style riche.

## Étape 4 : Ajouter des données au diagramme

Un diagramme sans données n’est qu’une forme décorative. Alimentons‑le avec un jeu de données simple—par exemple, les chiffres de ventes trimestrielles.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Pourquoi nous faisons cela :** En ajoutant explicitement des objets `ChartPoint`, nous garantissons que le diagramme reflète notre logique métier. Les appels `setShowCategoryName` et `setShowValue` font partie du **formatage du diagramme circulaire** pour afficher à la fois les libellés et les valeurs.

## Étape 5 : Affiner l’apparence (personnaliser la taille et le style du diagramme)

Au‑delà des dimensions initiales, vous pouvez ajuster la légende, le titre ou même la police utilisée pour les libellés de données. Tout cela relève de la **personnalisation de la taille du diagramme** et du formatage global.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Cas limite :** Si vous décidez plus tard d’exporter le document en PDF, les données vectorielles du diagramme restent nettes parce que la taille est définie en points, pas en pixels. C’est un avantage pour le **formatage du diagramme Word** et les formats en aval.

## Étape 6 : Enregistrer et visualiser le document

L’étape finale est aussi simple que d’appeler `doc.save`. Cela crée un fichier `.docx` que vous pouvez ouvrir avec Microsoft Word, LibreOffice ou tout visualiseur supportant le format OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Résultat :** Ouvrez `PieChart.docx` et vous verrez un diagramme circulaire (ou en anneau) correctement dimensionné avec une tranche explosée, un titre et une légende—le tout généré sans jamais toucher à l’interface utilisateur.

### Résultat attendu

| Élément | Ce que vous verrez |
|---------|--------------------|
| Type de diagramme | Diagramme circulaire (ou en anneau si `holeSize` > 0) |
| Explosion de tranche | Première tranche décalée de 20 pts |
| Légende | Positionnée à droite |
| Titre | “Quarterly Sales Distribution” en gras 14 pt |
| Libellés de données | Nom de catégorie et valeur affichés sur chaque tranche |
| Document | Un fichier Word `.docx` standard prêt à être partagé |

## Questions fréquentes & pièges courants

- **Ai‑je besoin d’une licence ?**  
  La version d’évaluation fonctionne pour les tests, mais ajoute un filigrane. Déposez votre fichier `aspose.words.lic` dans le classpath pour un rendu propre.

- **Puis‑je l’utiliser avec Maven ?**  
  Bien sûr. Ajoutez la dépendance suivante à votre `pom.xml` :

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **Et si j’ai plus d’une série ?**  
  Parcourez `pieChart.getSeries()` et appliquez `setExplosion`, `setFillColor` ou d’autres réglages par série. C’est ainsi que l’on **formate le diagramme circulaire** pour des données multidimensionnelles.

- **Le diagramme est‑il éditable dans Word après génération ?**  
  Oui—une fois enregistré, vous pouvez ouvrir le document et ajuster manuellement les couleurs, les polices, ou même convertir le diagramme circulaire en diagramme à barres si besoin.

## Conclusion

Nous venons **d’insérer un diagramme circulaire** dans un document Word avec Aspose.Words for Java, montré comment **générer un diagramme en anneau**, démontré plusieurs façons de **formater le diagramme circulaire**, couvert les meilleures pratiques de **formatage du diagramme Word**, et appris à **personnaliser la taille du diagramme** pour un rendu soigné. L’exemple complet et exécutable ci‑dessus peut être intégré à n’importe quel projet Java, vous offrant une automatisation instantanée des diagrammes sans la surcharge de l’interop COM ou des installations Office.

Et après ? Essayez de remplacer la source de données par une base de données en temps réel, ajoutez des couleurs conditionnelles selon des seuils, ou exportez le même document en PDF pour un rapport prêt à imprimer. Chaque étape s’appuie sur les bases que nous avons posées, rendant la transition fluide.

Si vous rencontrez des problèmes ou avez des idées d’améliorations supplémentaires—peut‑être un diagramme à barres empilées ou un diagramme linéaire—laissez un commentaire ci‑dessous. Bon diagrammage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}