---
category: general
date: 2026-10-04
description: Apprenez à détacher une part dans un graphique Word, à détacher une part
  d’un diagramme circulaire et à modifier la taille d’un graphique en anneau grâce
  à un exemple Java étape par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: fr
lastmod: 2026-10-04
og_description: Comment exploser une part dans un graphique Word et personnaliser
  les graphiques en secteurs ou en anneaux avec Java. Suivez l'exemple complet pour
  modifier le graphique dans Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Comment exploser une tranche dans un graphique Word – guide complet Java
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Comment détacher une part dans un graphique Word et personnaliser son apparence
url: /fr/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment exploser une tranche dans un graphique Word et personnaliser son apparence

Si vous avez besoin de **how to explode slice** dans un graphique Word, ce guide vous montre exactement comment faire. Que vous prépariez une présentation de vente ou un rapport financier, exploser une tranche de diagramme circulaire ou ajuster le trou d’un graphique en anneau peut faire ressortir les données les plus importantes. Dans les sections suivantes, vous apprendrez également comment **modify chart in Word**, **explode pie chart slice**, **change doughnut chart size**, et **customize pie chart word** documents en utilisant Aspose.Words for Java.

Vous terminerez ce tutoriel avec un programme Java complet, prêt à être exécuté, qui charge un fichier `.docx`, explose la première tranche d’un diagramme circulaire, modifie la taille du trou d’un graphique en anneau et enregistre le résultat. Aucun script externe ni aucune édition manuelle ne sont nécessaires.

## Prérequis

- Java 17 ou version ultérieure installé sur votre machine de développement.  
- Maven 3.6+ (ou Gradle) pour gérer les dépendances.  
- Bibliothèque Aspose.Words for Java (l’essai gratuit fonctionne pour le développement).  
- Un document Word (`input.docx`) contenant au moins un graphique (circulaire ou en anneau).

## Étape 1 : Ajouter Aspose.Words à votre projet

Si vous utilisez Maven, ajoutez la dépendance suivante à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Pour Gradle, placez ceci dans `build.gradle` :

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Astuce :** Gardez votre version de bibliothèque à jour ; les nouvelles versions ajoutent la prise en charge de types de graphiques supplémentaires et améliorent les performances.

## Étape 2 : Charger le document Word qui contient un graphique

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Pourquoi c’est important :** Charger le document crée une représentation en mémoire que Aspose.Words peut parcourir. Sans cet objet, vous ne pouvez pas accéder aux nœuds du graphique.

## Étape 3 : Récupérer le premier graphique du document

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Explication :** `NodeType.SHAPE` couvre tous les objets de dessin, y compris les graphiques. L’argument `true` indique à Aspose de rechercher de façon récursive, garantissant que le premier graphique soit trouvé même s’il est imbriqué dans un tableau.

## Étape 4 : Exploser la première tranche d’un diagramme circulaire

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Comment ça fonctionne :** La méthode `setExplosion` prend une valeur numérique qui détermine la distance à laquelle la tranche s’éloigne du centre. Une valeur de `20` est visuellement perceptible sans perturber la mise en page du graphique.

## Étape 5 : Ajuster la taille du trou d’un graphique en anneau

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Pourquoi cela aide :** Un trou d’anneau plus grand peut améliorer la lisibilité lorsque vous avez de nombreux points de données. La méthode `setDoughnutHoleSize` attend un pourcentage (0‑100).

## Étape 6 : Enregistrer le document modifié

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Résultat attendu

- La première tranche du premier diagramme circulaire est décalée vers l’extérieur, la faisant ressortir.
- Si le graphique est un anneau, le trou central s’étend à 40 % du rayon du graphique.
- Le fichier résultant `PieChart.docx` peut être ouvert dans Microsoft Word, LibreOffice ou tout visualiseur compatible, affichant les modifications visuelles appliquées par programme.

## Exemple complet et exécutable

Ci-dessous se trouve le programme complet en un seul bloc. Copiez‑le dans `ChartExploder.java`, ajustez les chemins de fichiers, et exécutez‑le avec `mvn compile exec:java` (ou la configuration d’exécution de votre IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

L’exécution de ce code **modify chart in Word**, **explode pie chart slice**, et **change doughnut chart size** automatiquement.

## Questions fréquentes et cas particuliers

| Question | Answer |
|----------|--------|
| *Et si le document contient plusieurs graphiques ?* | L’exemple cible le graphique **premier** (`NodeType.SHAPE, 0`). Pour travailler avec d’autres graphiques, modifiez l’indice ou parcourez `doc.getChildNodes(NodeType.SHAPE, true)` et filtrez par `shape.getChart() != null`. |
| *Puis‑je exploser une tranche autre que la première ?* | Oui. Accédez à la série souhaitée via `chart.getSeries().get(seriesIndex)` et appelez `setExplosion(value)`. Les indices commencent à zéro. |
| *Cela fonctionne‑t‑il avec les fichiers Word 2007‑2021 ?* | Aspose.Words prend en charge les fichiers `.doc`, `.docx`, `.dot` et `.dotx`. Le même code fonctionne sur toutes les versions car la bibliothèque abstrait le format de fichier. |
| *Et si le graphique est un histogramme ou un graphique en ligne ?* | `setExplosion` et `setDoughnutHoleSize` ne s’appliquent qu’aux graphiques de type circulaire. Le code ignore en toute sécurité ces opérations lorsque le type de graphique diffère. |
| *Ai‑je besoin d’une licence pour Aspose.Words ?* | Une licence d’évaluation gratuite supprime la limite de 30 jours mais ajoute un filigrane. Pour la production, achetez une licence afin de supprimer le filigrane et débloquer toutes les fonctionnalités. |

## Conclusion

Vous savez maintenant **how to explode slice** dans un graphique Word, comment **modify chart in Word**, et comment **change doughnut chart size** en utilisant Aspose.Words for Java. L’exemple complet montre le flux de travail complet — du chargement d’un document, à la localisation du graphique, en passant par l’application de réglages visuels, jusqu’à l’enregistrement du résultat — afin que vous puissiez intégrer ces étapes dans n’importe quel pipeline de reporting ou de génération de documents.

**Étapes suivantes**

- Explorez d’autres personnalisations de graphiques telles que changer les couleurs, ajouter des étiquettes de données, ou changer le type de graphique (`chart.setChartType(ChartType.BAR_CLUSTERED)`).
- Combinez cette logique avec Aspose.PDF pour générer une version PDF du même rapport.
- Automatisez le processus pour un lot de documents en parcourant les fichiers d’un répertoire.

N’hésitez pas à expérimenter différentes valeurs d’explosion ou pourcentages de trou d’anneau pour correspondre à vos directives de conception. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un graphique en colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Masquer l’axe du graphique dans un document Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insérer un graphique à bulles dans un document Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}