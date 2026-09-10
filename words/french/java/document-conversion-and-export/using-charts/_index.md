---
date: 2025-12-13
description: Apprenez à créer un diagramme à colonnes et à formater les étiquettes
  de données du diagramme avec Aspose.Words for Java. Explorez l'ajout de plusieurs
  séries, la modification du type d'axe et le masquage de l'axe du diagramme.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Comment créer un graphique en colonnes avec Aspose.Words pour Java
url: /fr/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un graphique en colonnes avec Aspose.Words pour Java

Dans ce tutoriel, vous allez **créer des visualisations de graphiques en colonnes** directement dans des documents Word à l'aide d'Aspose.Words pour Java. Nous parcourrons la création de différents types de graphiques, l'ajout de plusieurs séries, le formatage des étiquettes de données du graphique, la modification du type d'axe, et même la masquage d'un axe de graphique lorsque vous avez besoin d'un rendu plus épuré. À la fin, vous disposerez d’une approche solide et prête pour la production afin d’intégrer des graphiques riches dans vos documents.

## Réponses rapides
- **Quelle est la classe principale pour créer un graphique ?** `DocumentBuilder` avec `insertChart`.
- **Quelle méthode ajoute une nouvelle série ?** `chart.getSeries().add(...)`.
- **Comment formater les étiquettes de données du graphique ?** Utilisez `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Puis‑je masquer un axe ?** Oui, appelez `setHidden(true)` sur l’objet axe.
- **Ai‑je besoin d’une licence pour Aspose.Words ?** Une licence est requise pour une utilisation en production ; une version d’essai gratuite est disponible.

## Qu’est‑ce qu’un graphique en colonnes et pourquoi l’utiliser ?

Un graphique en colonnes affiche des données catégorielles sous forme de barres verticales, ce qui le rend idéal pour comparer des valeurs entre différents groupes (ventes par région, dépenses mensuelles, etc.). Dans les applications Java, générer un graphique en colonnes avec Aspose.Words vous permet d’intégrer ces visualisations directement dans des fichiers Word / DOCX sans recourir à Excel ou à des outils externes.

## Comment créer un graphique en colonnes

Voici un exemple simple qui crée un graphique en colonnes basique. Le code est identique à l’extrait original – nous n’avons ajouté que des commentaires explicatifs pour faciliter la compréhension.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Ajouter plusieurs séries

Vous pouvez **ajouter plusieurs séries** à un graphique en colonnes en appelant `chart.getSeries().add(...)` de façon répétée, comme illustré ci‑dessus. Chaque série peut disposer de son propre ensemble de catégories et de valeurs, vous permettant de comparer plusieurs jeux de données côte à côte.

## Comment créer un graphique en lignes avec des étiquettes de données personnalisées

Si vous avez besoin d’un graphique en lignes plutôt que d’un graphique en colonnes, le même principe s’applique. Cet exemple montre également comment **formater les étiquettes de données du graphique** avec différents formats numériques.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

### Ajouter des étiquettes de données

L’appel `series1.hasDataLabels(true)` **ajoute des étiquettes de données** à la série, tandis que `setShowValue(true)` rend les valeurs réelles visibles sur le graphique.

## Comment changer le type d’axe et personnaliser les propriétés de l’axe

Modifier le type d’axe (par ex., d’une date à une catégorie) vous permet de contrôler la façon dont les points de données sont tracés. Cet extrait montre également comment **masquer un axe de graphique** si vous privilégiez un design minimaliste.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Modifier le type d’axe

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **modifie le type d’axe** d’un axe basé sur les dates à un axe catégoriel, vous offrant un contrôle complet sur le placement des libellés.

## Comment formater les étiquettes de données du graphique (formats numériques)

Vous pouvez appliquer un format numérique directement à l’axe ou aux étiquettes de données. Cet exemple formate les nombres de l’axe Y avec un séparateur de milliers.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Personnalisations supplémentaires du graphique

Au‑delà des bases, vous pouvez ajuster les limites, définir des intervalles entre les libellés, masquer des axes spécifiques, etc. Consultez la documentation de l’API Aspose.Words pour Java pour obtenir la liste complète des propriétés.

## Foire aux questions

**Q : Comment ajouter plusieurs séries à un graphique ?**  
R : Utilisez `chart.getSeries().add()` pour chaque série que vous souhaitez afficher. Chaque appel peut fournir un nom unique, un tableau de catégories et un tableau de valeurs.

**Q : Comment formater les étiquettes de données du graphique avec des formats numériques personnalisés ?**  
R : Accédez à l’objet `DataLabels` d’une série et appelez `getNumberFormat().setFormatCode("votre format")`. Vous pouvez également lier le format à une cellule source avec `isLinkedToSource(true)`.

**Q : Comment masquer un axe de graphique ?**  
R : Appelez `setHidden(true)` sur le `ChartAxis` que vous souhaitez masquer (par ex., `chart.getAxisY().setHidden(true)`).

**Q : Quelle est la meilleure façon de changer le type d’axe ?**  
R : Utilisez `setCategoryType(AxisCategoryType.CATEGORY)` pour les axes catégoriels ou `AxisCategoryType.DATE` pour les axes de type date.

**Q : Comment ajouter des étiquettes de données à une série ?**  
R : Activez‑les avec `series.hasDataLabels(true)` puis configurez leur visibilité via `series.getDataLabels().setShowValue(true)`.

## Conclusion

Nous avons couvert tout ce dont vous avez besoin pour **créer des visualisations de graphiques en colonnes** avec Aspose.Words pour Java — de l’insertion de graphiques de base et de l’ajout de plusieurs séries, au formatage des étiquettes de données, à la modification du type d’axe, et au masquage des axes pour un rendu épuré. Intégrez ces techniques dans vos pipelines de génération de rapports ou de documents afin de livrer des documents Word professionnels et axés sur les données.

---

**Dernière mise à jour :** 2025-12-13  
**Testé avec :** Aspose.Words pour Java 24.12 (dernière version)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}