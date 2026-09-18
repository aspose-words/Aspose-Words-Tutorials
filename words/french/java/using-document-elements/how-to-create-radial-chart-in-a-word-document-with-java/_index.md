---
category: general
date: 2026-09-18
description: Apprenez à créer un graphique radial dans un document Word en Java, à
  ajouter des étiquettes de données au graphique et à insérer des données de série
  avec un exemple de code complet.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: fr
lastmod: 2026-09-18
og_description: Créer un graphique radial dans un document Word à l'aide de Java,
  ajouter des étiquettes de données au graphique et insérer les données de la série
  dans un seul tutoriel.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Créer un graphique radial dans Word avec Java – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Comment créer un graphique radial dans un document Word avec Java
url: /fr/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un graphique radial dans un document Word avec Java

Si vous devez créer un graphique radial dans un document Word, ce guide vous montre les étapes exactes. Vous apprendrez également comment ajouter des étiquettes de données au graphique et insérer des données de séries afin que le graphique soit prêt pour la présentation.

Générer un graphique de manière programmatique élimine le travail de mise en forme manuelle et garantit la cohérence entre les rapports. Le tutoriel suppose que vous avez des connaissances de base en Java et qu’une version récente de la bibliothèque Aspose.Words for Java est installée.

## Ce dont vous avez besoin

* Java 17 ou plus récent  
* Aspose.Words for Java (version 23.12 ou ultérieure)  
* Un IDE ou un outil de construction capable de résoudre les dépendances Maven/Gradle  

Avoir ces prérequis installés vous permet d’exécuter l’exemple sans configuration supplémentaire.

## Comment créer un graphique radial dans un document Word

La première étape consiste à créer un fichier Word vierge qui accueillera le graphique. Un document vierge offre une toile propre et évite les styles non intentionnels.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` représente le fichier .docx complet, tandis que `DocumentBuilder` fournit des méthodes pour insérer des éléments tels que des paragraphes, des tableaux et des graphiques.

## Comment insérer le graphique

Ensuite, vous insérez le graphique lui‑-même. La méthode `insertChart` crée un objet graphique et le place à la position actuelle du curseur du builder.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Un graphique polaire représente les points de données autour d’un axe central, ce qui est idéal pour afficher des informations cycliques. Les dimensions sont exprimées en points (1 pt ≈ 1/72 pouce).

## Ajouter des données de séries au graphique

Un graphique sans données de séries est vide. Vous pouvez ajouter une série manuellement ou la lier à une source de données. L’exemple ci‑dessous ajoute une seule série avec trois points de données.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` reçoit un nom de série, une liste d’étiquettes de catégorie et une liste de valeurs numériques correspondantes. Vous pouvez répéter ce bloc pour ajouter des séries supplémentaires (`addSeriesData`).

## Ajouter des étiquettes de données au graphique pour la première série

Les étiquettes de données rendent le graphique lisible sans survoler les points. La ligne suivante active les étiquettes de valeur pour la première série.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Définir `showValue` à `true` affiche la valeur de chaque point directement sur le graphique. Vous pouvez également activer les noms de catégorie, les pourcentages ou les lignes de repère via le même objet `DataLabelFormat`.

## Enregistrer le fichier Word

Une fois le graphique configuré, écrivez le document sur le disque. Choisissez un emplacement auquel votre application peut accéder.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Le fichier `RadialChart.docx` contient maintenant un graphique radial entièrement fonctionnel avec des étiquettes de données.

## Exemple complet fonctionnel

Ci‑dessous se trouve un programme autonome que vous pouvez copier, compiler et exécuter. Il montre le flux de travail complet, de la création d’un document Word vierge à l’enregistrement d’un graphique radial avec des étiquettes de données.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Résultat attendu**

Lorsque vous ouvrez `output/RadialChart.docx` dans Microsoft Word, vous verrez un graphique radial intitulé *Quarterly Sales*. Chaque point affiche sa valeur numérique (par ex., « 15000 ») à côté du marqueur.

## Variations courantes et cas limites

| Situation | Modification recommandée |
|-----------|--------------------------|
| Vous avez besoin d’un type de graphique différent | Remplacez `ChartType.POLAR` par toute autre valeur d’énumération `ChartType` (par ex., `ChartType.COLUMN`). |
| Le graphique doit utiliser une plage Excel externe | Utilisez `chart.setDataRange("Sheet1!A1:B5")` après avoir créé le graphique et chargé le classeur. |
| Vous souhaitez masquer la légende | `chart.getLegend().setVisible(false);` |
| Le document doit être enregistré au format PDF | Appelez `doc.save("RadialChart.pdf");` – Aspose.Words convertit automatiquement le graphique. |

Ces ajustements conservent la logique de base tout en adaptant le résultat aux exigences spécifiques.

## Astuces professionnelles

* **Réutiliser le builder** – Vous pouvez insérer plusieurs graphiques dans le même document en appelant `builder.insertChart` de façon répétée.  
* **Performance** – Lors de la génération de nombreux graphiques, créez une seule instance de `DocumentBuilder` et réutilisez‑la pour réduire la surcharge d’allocation d’objets.  
* **Style** – L’apparence du graphique (couleurs, épaisseur des lignes) est contrôlée via les méthodes `getSeries().get(i).getFormat()` de l’objet `Chart`. Expérimentez ces paramètres pour correspondre à l’identité visuelle de l’entreprise.  

## Conclusion

Vous savez maintenant comment créer un graphique radial dans un document Word avec Java, ajouter des données de séries et des étiquettes de données au graphique avant d’enregistrer le fichier. L’exemple complet peut être étendu pour gérer des séries supplémentaires, des styles personnalisés ou des formats de sortie alternatifs.

Explorez des sujets connexes tels que **how to insert chart** à partir de sources de données externes, **create blank word** documents avec des modèles prédéfinis, et **add series data** dynamiquement depuis des bases de données. Expérimentez différents types de graphiques pour découvrir quelle visualisation communique le mieux vos données.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un graphique en colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Créer un document Word Java – Ajouter une forme rectangle avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Définir les options par défaut pour les étiquettes de données dans un graphique](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}