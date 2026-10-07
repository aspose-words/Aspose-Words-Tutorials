---
category: general
date: 2026-09-27
description: Créer un graphique radial en Java et l’insérer dans Word. Apprenez à
  définir la taille du graphique, ajouter des séries de données et générer un document
  Word vierge.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: fr
lastmod: 2026-09-27
og_description: Créer un graphique radial en Java, puis l’insérer dans Word. Ce guide
  montre comment définir la taille du graphique, ajouter des séries de données et
  créer un document Word vierge.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Créer un graphique radial et insérer le graphique dans Word avec Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Créer un graphique radial et l’insérer dans Word avec Java
url: /fr/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un graphique radial et insérer le graphique dans Word avec Java

Si vous devez **créer un graphique radial** dans un fichier Word en utilisant Java, ce tutoriel vous montre exactement comment faire. Vous verrez comment **insérer le graphique dans Word**, définir les dimensions du graphique, et créer un **document Word vierge** à partir de zéro.

Nous parcourrons chaque étape requise, de l'initialisation du document à l'ajout d'une série de données et à l'enregistrement du `.docx` final. À la fin, vous disposerez d'un fichier Word pleinement fonctionnel contenant un graphique radial, et vous comprendrez **comment définir la taille du graphique** et **ajouter une série de données au graphique** pour de futures personnalisations.

## Prérequis

* Java 17 ou version ultérieure (le code se compile avec n'importe quel JDK moderne)
* Aspose.Words for Java 24.9 ou plus récent – la méthode `setShowGraduations` n'est disponible qu'à partir de cette version
* Un IDE ou un outil de construction (Maven/Gradle) capable d'inclure le JAR Aspose.Words
* Familiarité de base avec la syntaxe Java et la gestion des dépendances Maven/Gradle

> **Astuce :** Si vous utilisez Maven, ajoutez ce qui suit à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Étape 1 : Créer un document Word vierge

Un document vierge est la toile sur laquelle le graphique sera placé. La classe `Document` représente l'ensemble du fichier `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Créer un document vierge garantit qu'aucun contenu préexistant n'interfère avec la mise en page du graphique.

## Étape 2 : Initialiser un DocumentBuilder

`DocumentBuilder` fournit des méthodes pratiques pour insérer des objets, du texte et d'autres éléments dans le document.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Le constructeur sera ensuite utilisé pour **insérer le graphique dans Word**.

## Étape 3 : Construire le graphique radial

Aspose.Words prend en charge de nombreux types de graphiques ; `ChartType.RADIAL` crée un graphique radial (polaire).

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

À ce stade, le graphique existe mais n'a aucune donnée, taille ou option visuelle.

## Étape 4 : Ajouter une série de données au graphique

Un graphique sans série de données est vide. La méthode `add` prend un nom de série et un tableau de valeurs.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Vous pouvez ajouter plusieurs séries en appelant `add` de façon répétée. Cela satisfait l'exigence **add data series chart**.

## Étape 5 : Activer les graduations (optionnel)

Les graduations sont les lignes de grille radiales qui améliorent la lisibilité. Elles ne sont disponibles qu'à partir de la version 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Si vous utilisez une version plus ancienne d'Aspose.Words, cette ligne générera une exception — vérifiez donc d'abord la version de votre bibliothèque.

## Étape 6 : Définir les dimensions du graphique

Contrôler la taille du graphique vous permet de l'ajuster correctement aux marges de la page. Cela répond à **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Vous pouvez ajuster les valeurs de largeur et de hauteur pour correspondre à vos besoins de mise en page. Rappelez‑vous que 1 point ≈ 1/72 pouce.

## Étape 7 : Insérer le graphique dans le document Word

Le graphique est maintenant prêt à être placé. La méthode `insertChart` de `DocumentBuilder` gère l'insertion.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Ceci est le cœur de l'opération **insert chart into word**.

## Étape 8 : Enregistrer le document

Enfin, écrivez le document sur le disque. Le fichier contiendra le graphique radial que vous venez de créer.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

L'exécution du programme génère `RadialChart.docx` dans le répertoire de travail du projet. L'ouverture du fichier dans Microsoft Word affiche un graphique radial avec trois points de données et des graduations visibles.

### Résultat attendu

* Un fichier Word nommé `RadialChart.docx`
* À l'intérieur du fichier, une seule page contenant un graphique radial de taille 400 × 300 points
* Le graphique affiche une série intitulée **Series 1** avec les valeurs **10, 20, 30**
* Les graduations (lignes de grille radiales) sont visibles autour du graphique

## Variations courantes et cas limites

| Situation | Ce qu'il faut changer | Raison |
|-----------|-----------------------|--------|
| **Multiple series** | Appeler `chart.getSeries().add(...)` pour chaque série | Permet la visualisation comparative des données |
| **Different chart type** | Remplacer `ChartType.RADIAL` par `ChartType.COLUMN` (ou tout autre) | Utiliser le type de graphique qui représente le mieux vos données |
| **Custom colors** | Accéder à `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Améliore l'identité visuelle |
| **Older Aspose.Words version** | Omettre la ligne `setShowGraduations` ou mettre à jour la bibliothèque | Empêche `NoSuchMethodError` |
| **Saving to a different format** | Utiliser `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Génère un PDF au lieu d'un DOCX |

## Exemple complet exécutable

Ci-dessous le programme Java complet et autonome. Copiez‑le dans un fichier nommé `RadialChartExample.java`, ajoutez la dépendance Aspose.Words, puis exécutez‑le.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Conclusion

Vous savez maintenant comment **create radial chart** programmatically, **add data series chart**, contrôler **how to set chart size**, et **insert chart into Word** en partant d'un **blank Word document**. L'exemple utilise Aspose.Words for Java 24.9, mais les mêmes concepts s'appliquent à d'autres bibliothèques de graphiques qui exposent une API similaire.

### Prochaines étapes

* Explorez d'autres types de graphiques (`ChartType.PIE`, `ChartType.LINE`, etc.) – cela renvoie au mot‑clé secondaire **insert chart into word**.
* Personnalisez les libellés des axes, les légendes et les couleurs pour correspondre à vos directives de marque.
* Générez des graphiques dynamiquement à partir de requêtes de base de données ou de fichiers CSV.
* Convertissez le `.docx` résultant en PDF pour la distribution (`doc.save("output.pdf", SaveFormat.PDF)`).

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer un graphique en colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Créer un document Word Java – Ajouter une forme rectangle avec effet d'ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insérer un graphique en aires dans un document Word](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}