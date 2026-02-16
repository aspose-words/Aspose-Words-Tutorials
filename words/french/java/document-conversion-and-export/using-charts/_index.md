---
date: 2026-02-16
description: Apprenez à ajouter plusieurs séries aux graphiques dans Aspose.Words
  for Java, à modifier les marques de graduation des axes, à appliquer un format numérique
  personnalisé et à générer des documents Word contenant des graphiques en lignes
  et en colonnes.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Ajouter plusieurs séries aux graphiques dans Aspose.Words pour Java
url: /fr/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter plusieurs séries aux graphiques dans Aspose.Words for Java

## Introduction à l'utilisation des graphiques dans Aspose.Words for Java

Dans ce tutoriel, vous apprendrez **comment ajouter plusieurs séries** à un graphique en utilisant Aspose.Words for Java, pourquoi la personnalisation des marques de graduation des axes et l'application d'un format numérique personnalisé sont importantes, et comment générer un document Word riche en graphiques. Que vous ayez besoin d'un graphique en courbes pour des données financières ou d'un graphique en colonnes pour des chiffres de ventes, les étapes ci‑dessous vous guideront dans la création, le style et le réglage fin des graphiques de manière programmatique.

## Réponses rapides
- **Comment ajouter plusieurs séries ?** Utilisez `chart.getSeries().add(...)` pour chaque série que vous souhaitez afficher.  
- **Puis‑je modifier les marques de graduation des axes ?** Oui – utilisez `setMajorTickMark()` et `setMinorTickMark()` sur les objets d'axe.  
- **Quel format puis‑je appliquer aux étiquettes de données ?** Tout format numérique compatible Excel, par ex., `"$"#,##0.00` ou `0.00%`.  
- **Quels types de graphiques sont pris en charge ?** Ligne, colonne, zone, bulles, nuage de points, et bien d'autres via `ChartType`.  
- **Une licence est‑elle requise pour la production ?** Une licence valide d'Aspose.Words for Java est nécessaire pour la pleine fonctionnalité.

## Qu’est‑ce que « ajouter plusieurs séries » dans un graphique ?

Ajouter plusieurs séries signifie insérer plus d'un jeu de données dans la même zone de graphique, vous permettant de comparer différentes catégories ou périodes côte à côte. Chaque série apparaît comme sa propre ligne, colonne ou ensemble de marqueurs, offrant aux lecteurs une histoire visuelle plus riche.

## Pourquoi utiliser Aspose.Words for Java pour générer des documents Word contenant des graphiques ?

- **Contrôle total** sur le type de graphique, la mise en page et le style sans ouvrir Word manuellement.  
- **Génération programmatique** qui s'intègre aux pipelines de reporting automatisés.  
- **Cross‑platform** – fonctionne sur tout environnement compatible Java.  
- **API riche** pour personnaliser les axes, les étiquettes de données et les formats numériques.

## Prérequis
- Java Development Kit (JDK) 8 ou supérieur.  
- Bibliothèque Aspose.Words for Java ajoutée à votre projet (Maven/Gradle ou JAR).  
- Une licence Aspose valide pour la production (optionnelle pour l'évaluation).

## Guide étape par étape

### Étape 1 : Créer un graphique en courbes et **ajouter plusieurs séries**
Voici le code principal qui crée un graphique en courbes, supprime les séries par défaut, puis ajoute trois séries distinctes avec des étiquettes de données personnalisées.

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

> **Astuce :** Appelez `chart.getSeries().add(...)` autant de fois que nécessaire pour **ajouter plusieurs séries** – chaque appel crée une nouvelle ligne (ou colonne, etc.) sur le même graphique.

### Étape 2 : **Créer un graphique en colonnes** (create column chart java)
L'extrait suivant montre comment insérer un simple graphique en colonnes, utile pour comparer des catégories côte à côte.

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

### Étape 3 : **Modifier les marques de graduation des axes** (change axis tick marks)
Personnaliser les axes X et Y améliore la lisibilité. Le code suivant montre comment modifier les marques de graduation, inverser l'ordre et définir des points de croisement personnalisés.

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

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Étape 4 : **Appliquer un format numérique personnalisé** (apply custom number format)
Vous pouvez formater les nombres d'axe ou les étiquettes de données avec n'importe quel modèle supporté par Excel. Voici un exemple concis qui formate l'axe Y avec un séparateur de milliers.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Étape 5 : Générer le document Word final (generate chart word document)
Après avoir configuré les séries, les axes et les étiquettes, appelez simplement `doc.save(...)` comme indiqué dans les extraits ci‑dessus. Le fichier `.docx` résultant contient des graphiques pleinement fonctionnels qui peuvent être ouverts et modifiés dans Microsoft Word.

## Cas d’utilisation courants
- **Tableaux de bord financiers** – graphiques en courbes avec plusieurs séries pour le revenu, les dépenses et le profit.  
- **Rapports de ventes** – graphiques en colonnes comparant les ventes trimestrielles par région.  
- **Suivi de projet** – graphiques en zone ou nuage de points visualisant l'avancement dans le temps.  

## Personnalisations supplémentaires des graphiques
Au‑delà des bases, vous pouvez ajuster les limites, masquer des axes (`axis.setHidden(true)`), changer les couleurs, ajouter des légendes, etc. Consultez la référence API d'Aspose.Words for Java pour la liste complète des options.

## Conclusion
Dans ce guide, nous avons vu comment **ajouter plusieurs séries** aux graphiques, créer des graphiques en courbes et en colonnes, **modifier les marques de graduation des axes**, **appliquer des formats numériques personnalisés**, et enfin **générer un document Word riche en graphiques**. Avec Aspose.Words for Java, vous disposez d'une méthode puissante, orientée code, pour intégrer des visualisations de données professionnelles directement dans vos documents.

## Foire aux questions

**Q : Comment puis‑je ajouter plusieurs séries à un graphique ?**  
R : Appelez `chart.getSeries().add()` pour chaque série que vous souhaitez afficher. Chaque appel crée un nouveau jeu de données qui apparaît comme sa propre ligne, colonne ou groupe de marqueurs.

**Q : Comment formater les étiquettes de données avec un format numérique personnalisé ?**  
R : Accédez à l'objet `DataLabels` de la série et utilisez `getNumberFormat().setFormatCode("votre modèle")`. Vous pouvez également lier le format à une cellule source avec `isLinkedToSource(true)`.

**Q : Comment puis‑je modifier les marques de graduation des axes ?**  
R : Utilisez `setMajorTickMark()` et `setMinorTickMark()` sur `ChartAxis`. Les options incluent `CROSS`, `INSIDE`, `OUTSIDE` et `NONE`.

**Q : Puis‑je créer d'autres types de graphiques comme des nuages de points ou des graphiques en zone ?**  
R : Oui – spécifiez le `ChartType` souhaité (par ex., `ChartType.SCATTER`, `ChartType.AREA`) lors de l'appel à `builder.insertChart(...)`.

**Q : Comment masquer un axe dont je n’ai pas besoin ?**  
R : Appelez `axis.setHidden(true)` sur le `ChartAxis` que vous souhaitez masquer.

---

**Dernière mise à jour :** 2026-02-16  
**Testé avec :** Aspose.Words for Java 24.11  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}