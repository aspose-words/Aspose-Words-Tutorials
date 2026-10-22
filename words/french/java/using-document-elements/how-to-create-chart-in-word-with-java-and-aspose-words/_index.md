---
category: general
date: 2026-09-24
description: Apprenez à créer un graphique dans Word avec Java, insérez un graphique
  radial et enregistrez le document au format docx avec Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: fr
lastmod: 2026-09-24
og_description: Créer un graphique dans Word avec Java et Aspose.Words. Ce tutoriel
  vous montre comment ajouter un graphique radial, personnaliser les données et enregistrer
  le document au format docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Créer un graphique dans Word avec Java – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Comment créer un graphique dans Word avec Java et Aspose.Words
url: /fr/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un graphique dans Word avec Java et Aspose.Words

Si vous devez **créer un graphique dans Word** depuis une application Java, ce guide vous accompagne à travers le processus complet. Vous verrez comment ajouter un graphique radial, éventuellement remplir ses séries, puis **enregistrer le document au format docx** à l’aide de la bibliothèque Aspose.Words for Java.

Générer des données visuelles à l’intérieur d’un fichier Word est une exigence fréquente pour les rapports, la facturation ou la génération automatisée de documents. À la fin de ce tutoriel, vous serez capable de créer des projets **create word document java** qui **add chart to Word** sans aucune édition manuelle.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java Development Kit (JDK) 8 ou plus récent.
* Maven ou Gradle pour la gestion des dépendances.
* Un IDE tel qu’IntelliJ IDEA, Eclipse ou VS Code.
* Une licence valide d’Aspose.Words for Java (l’essai gratuit suffit pour le développement).

Ces outils constituent la base des exemples de code qui suivent.

## Étape 1 : Configurer le projet Maven

Créez un nouveau projet Maven (ou mettez à jour un existant) et ajoutez la dépendance Aspose.Words à votre `pom.xml` :

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

L’exécution de `mvn clean install` télécharge la bibliothèque et rend les classes telles que `Document`, `DocumentBuilder` et `ChartType` disponibles sur le classpath.

> **Astuce :** Gardez la version de la bibliothèque à jour. Les nouvelles versions ajoutent des types de graphiques et améliorent les performances de rendu.

## Étape 2 : Créer un nouveau document Word

La première étape programmatique pour **create chart in Word** consiste à instancier un `Document` vide. Cet objet représente l’ensemble du package `.docx`.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` fonctionne comme un curseur ; il connaît le point d’insertion actuel et fournit des méthodes pour le texte, les tableaux et les graphiques. À ce stade, vous avez **created word document java** – une toile vierge prête à recevoir du contenu.

## Étape 3 : Insérer un graphique radial

Aspose.Words prend en charge de nombreux types de graphiques. Pour **insert radial chart**, appelez `insertChart` avec `ChartType.RADIAL`. La méthode nécessite également la largeur et la hauteur en points (1 point ≈ 1/72 pouce).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

L’objet `Shape` retourné contient le graphique sous‑jacent. Le graphique rend automatiquement les graduations pour une disposition de 24,9° , qui est la valeur par défaut des graphiques radiaux dans Word.

### Pourquoi utiliser un graphique radial ?

Un graphique radial visualise des données qui s’enroulent autour d’un cercle, ce qui le rend idéal pour montrer des motifs cycliques (par ex. ventes mensuelles, indicateurs d’horloge). La même API peut insérer des graphiques à barres, en secteurs ou en lignes, mais le type radial apporte un aspect distinctif sans code de style supplémentaire.

## Étape 4 : (Facultatif) Remplir les données de la série du graphique

Si vous souhaitez que le graphique affiche de vraies valeurs, vous devez ajouter des séries et des points. L’extrait suivant ajoute une série unique avec trois points de données :

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Vous pouvez répéter les appels `add` autant de fois que nécessaire. Aspose.Words met automatiquement à jour la représentation visuelle, de sorte que les tranches radiales s’ajustent aux nouvelles valeurs.

> **Question fréquente :** *Et si je dois lier des données provenant d’une base de données ?*  
> Récupérez les lignes, parcourez‑les dans une boucle et appelez `series.getDataPoints().add(value, label)` à l’intérieur de la boucle. L’API est thread‑safe et fonctionne avec n’importe quel `ResultSet` que vous fournissez.

## Étape 5 : Enregistrer le document au format DOCX

Lorsque le graphique est prêt, l’étape finale consiste à **save document as docx**. La méthode `save` détermine le format de sortie à partir de l’extension du fichier.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Le fichier généré contient un graphique radial pleinement fonctionnel qui peut être ouvert dans Microsoft Word, LibreOffice ou tout visualiseur supportant le format DOCX. Parce que nous avons utilisé l’extension `.docx`, Word enregistre le fichier au format Open XML, qui est la norme moderne pour les documents Word.

### Vérifier le résultat

Ouvrez `RadialChartDemo.docx` dans Word :

1. Vous devez voir une page unique avec un graphique radial centré.
2. Si vous avez ajouté des données de série, le graphique affiche quatre tranches étiquetées Q1‑Q4.
3. Clic droit sur le graphique → **Edit Data** pour confirmer le tableau de données sous‑jacent.

Si le graphique apparaît vide, revérifiez que vous avez appelé `chart.getChart()` avant d’ajouter les séries, et assurez‑vous que le curseur du `DocumentBuilder` est positionné à l’endroit où vous voulez le graphique.

## Étape 6 : Astuces avancées pour travailler avec les graphiques

| Astuce | Pourquoi c’est important |
|-----|----------------|
| **Définir le style du graphique** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Améliore la cohérence visuelle sans formater manuellement chaque élément. |
| **Redimensionner après insertion** – `chart.setWidth(500); chart.setHeight(350);` | Vous permet d’ajuster précisément la taille du graphique selon la mise en page. |
| **Ajouter un titre** – `chart.getChart().getTitle().setText("Revenue Overview");` | Donne du contexte aux lecteurs qui consultent le document sans le texte environnant. |
| **Exporter en PDF** – `doc.save("RadialChartDemo.pdf");` | Utile lorsque vous avez besoin d’une version non modifiable pour la distribution. |
| **Gestion de la licence** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Empêche l’apparition du filigrane d’évaluation dans les builds de production. |

Ces améliorations sont optionnelles mais montrent comment vous pouvez personnaliser davantage le graphique après avoir appris à **add chart to Word**.

## Conclusion

Vous disposez maintenant d’un exemple complet et autonome montrant comment **create chart in Word** avec Java, **insert radial chart**, le remplir éventuellement de données, puis **save document as docx**. Le même schéma fonctionne pour d’autres types de graphiques, vous permettant d’étendre ce tutoriel aux graphiques à barres, lignes ou secteurs selon vos besoins.

Ensuite, vous pourriez explorer :

* Des projets **create word document java** qui combinent tableaux, images et plusieurs graphiques.
* Utiliser **save document as docx** conjointement avec **save document as pdf** pour des rapports multi‑format.
* Ajouter des données dynamiques provenant d’API REST ou de bases de données à vos graphiques.

N’hésitez pas à expérimenter avec les options de style, les dimensions du graphique et les sources de données. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}