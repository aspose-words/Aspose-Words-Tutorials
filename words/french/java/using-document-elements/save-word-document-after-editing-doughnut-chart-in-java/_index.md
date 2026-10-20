---
category: general
date: 2026-09-11
description: Enregistrez le document Word après avoir modifié un diagramme en anneau
  avec Aspose.Words for Java. Apprenez à changer la taille du trou du diagramme en
  anneau, à faire pivoter le diagramme en anneau et à modifier les propriétés du diagramme
  en anneau.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: fr
lastmod: 2026-09-11
og_description: Enregistrez le document Word après avoir modifié un graphique en anneau
  à l'aide d'Aspose.Words pour Java. Ce tutoriel montre comment changer la taille
  du trou de l'anneau, faire pivoter le graphique en anneau et personnaliser l'apparence
  du graphique.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Enregistrer le document Word après modification du graphique en anneau –
  Guide Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Enregistrer le document Word après avoir modifié le graphique en anneau en
  Java
url: /fr/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer un document Word après avoir modifié un graphique en anneau avec Java

Si vous devez **enregistrer un document Word** contenant un graphique en anneau personnalisé, ce guide vous montre exactement comment faire. En quelques lignes de Java, vous pouvez modifier le trou de l’anneau, faire pivoter le graphique en anneau, puis écrire le résultat sur le disque.

Vous verrez un exemple complet et exécutable qui utilise Aspose.Words for Java, ainsi que des conseils pour gérer plusieurs graphiques, vérifier les types de nœuds et éviter les pièges courants. Aucune référence externe n’est requise — tout ce dont vous avez besoin est inclus.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

- Java 17 ou une version plus récente installée
- Maven ou Gradle pour gérer les dépendances
- Aspose.Words for Java (version 23.9 ou ultérieure) ajouté à votre projet  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Un fichier Word (`input.docx`) contenant un seul graphique en anneau

## Étape 1 : Charger le document Word

La première étape consiste à ouvrir le fichier source. Cette étape est essentielle car chaque opération ultérieure travaille sur l’objet `Document` en mémoire.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Pourquoi ?** Le chargement du document crée une représentation DOM qui vous permet de parcourir les formes, les tableaux et les graphiques. Si le fichier ne peut pas être ouvert, Aspose.Words lève une exception, vous indiquant immédiatement que le chemin est incorrect.

## Étape 2 : Localiser la forme du graphique en anneau

Un graphique est stocké à l’intérieur d’un nœud `Shape`. Nous récupérons la première forme qui héberge un graphique et castons son rendu en `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Pourquoi ?** Vérifier `isChart()` empêche un `ClassCastException` lorsque le document contient des images ou d’autres formes avant le graphique. Cela rend le code robuste pour les documents à contenu mixte.

## Étape 3 : Modifier la taille du trou de l’anneau  

Nous éditons maintenant le trou de l’anneau. La méthode `setHoleSize` attend un pourcentage du rayon du graphique (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Pourquoi ?** Modifier le trou de l’anneau (`change doughnut hole` / `change chart hole size`) vous permet de mettre en avant ou de désactiver la zone centrale. Les valeurs en dehors de 10‑90 % sont ignorées par l’API.

## Étape 4 : Faire pivoter le graphique en anneau  

Pour contrôler où commence la première tranche, définissez l’angle de la première tranche. Cela fait effectivement **rotate doughnut chart**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Pourquoi ?** Faire pivoter le graphique est utile lorsque vous souhaitez qu’une tranche particulière apparaisse en haut ou qu’elle corresponde à une spécification de conception.

## Étape 5 : Enregistrer le document mis à jour  

Enfin, écrivez les modifications dans un nouveau fichier. C’est le moment où vous **save Word document** avec le graphique modifié.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Résultat attendu :** `output.docx` contient le contenu original, mais le graphique en anneau possède maintenant un trou de 30 % et sa première tranche débute à 45 °. L’ouverture du fichier dans Microsoft Word affichera le graphique transformé.

## Exemple complet fonctionnel

Ci‑dessous se trouve le programme complet que vous pouvez copier‑coller dans votre IDE. Il inclut tous les imports et la gestion des erreurs nécessaires pour **edit doughnut chart** et **save Word document** en toute sécurité.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Résultat attendu

Lorsque vous ouvrez `output.docx` :

- Le trou central du graphique en anneau occupe environ un tiers du rayon du graphique.  
- La première tranche commence à la position de 45 degrés, décalant l’ensemble du graphique dans le sens horaire.  

Les deux changements visuels sont reflétés immédiatement dans Word.

## Variations courantes et cas limites

| Situation | Comment gérer |
|-----------|----------------|
| **Graphiques multiples** | Parcourez `doc.getChildNodes(NodeType.SHAPE, true)` et filtrez `shape.isChart()` ; appliquez `setHoleSize` / `setFirstSliceAngle` à chaque `Chart`. |
| **Le graphique n’est pas un anneau** | Vérifiez `chart.getType()` ; n’appeler `setHoleSize` que lorsque `chart.getType() == ChartType.DOUGHNUT`. |
| **Besoin de modifier la taille du trou dynamiquement** | Calculez le pourcentage souhaité en fonction des valeurs de données, puis appelez `setHoleSize(computedValue)`. |
| **Enregistrement vers un flux** | Utilisez


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications étape par étape pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Save Word with Password using Aspose.Words for Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}