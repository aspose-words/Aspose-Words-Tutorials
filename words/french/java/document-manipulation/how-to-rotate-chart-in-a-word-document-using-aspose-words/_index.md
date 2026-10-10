---
category: general
date: 2026-10-10
description: Apprenez à faire pivoter un graphique dans un fichier Word et à modifier
  le graphique dans Word pour changer la taille d’un graphique en anneau avec un exemple
  complet en Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: fr
lastmod: 2026-10-10
og_description: Comment faire pivoter un graphique dans un fichier Word et modifier
  le graphique dans Word pour changer la taille du graphique en anneau en utilisant
  Aspose.Words pour Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Comment faire pivoter un graphique dans un document Word – guide Java étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Comment faire pivoter un graphique dans un document Word à l'aide d'Aspose.Words
url: /fr/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment faire pivoter un graphique dans un document Word avec Aspose.Words

Si vous avez besoin de **how to rotate chart** à l'intérieur d'un fichier Microsoft Word, ce guide vous montre les étapes exactes. Vous apprendrez également comment **modify chart in Word** pour **change doughnut chart size** sans quitter votre code Java.

L'automatisation de Word ressemble souvent à une série d'appels d'API déconnectés, mais avec Aspose.Words vous pouvez traiter un graphique comme n'importe quel autre nœud de document. À la fin de ce tutoriel, vous disposerez d'un programme exécutable qui charge un `.docx` existant, fait pivoter un graphique en anneau de 45°, réduit le trou à 50 % du rayon, et enregistre le résultat dans un nouveau fichier.

## Prérequis

* Java 17 ou version supérieure installé.
* Maven (ou Gradle) pour gérer les dépendances.
* Un document Word d'entrée (`input.docx`) contenant déjà un graphique en anneau.
* Une licence valide d'Aspose.Words for Java (ou utilisez le mode d'évaluation).

## Étape 1 : Configurer le projet Maven

Créez un nouveau projet Maven ou ajoutez la dépendance suivante à votre `pom.xml` existant :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

L'exécution de `mvn clean install` téléchargera la bibliothèque et rendra les classes disponibles sur votre classpath.

## Étape 2 : Charger le document Word contenant un graphique

La première opération consiste à ouvrir le document existant. La classe `Document` représente le fichier complet.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Le chargement du fichier **ne** le modifie **pas** ; il crée simplement une représentation en mémoire que vous pouvez interroger et modifier.

## Étape 3 : Créer un DocumentBuilder pour la navigation

`DocumentBuilder` vous offre une API de type curseur pour parcourir l'arbre du document. Nous l'utiliserons pour localiser la première forme de graphique.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Le builder commence au début du document, mais vous pouvez le déplacer vers n'importe quel nœud ultérieurement si nécessaire.

## Étape 4 : Récupérer la première forme de graphique

Les graphiques sont stockés sous forme de nœuds `Shape`. En filtrant les nœuds enfants de type `NodeType.SHAPE`, nous pouvons extraire l'objet graphique.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Si le document contient plusieurs graphiques, vous pouvez itérer sur `getChildNodes` et vérifier chaque `Shape` avec `hasChart()` avant de le caster.

## Étape 5 : Faire pivoter le graphique (how to rotate chart)

Un graphique en anneau est essentiellement un graphique circulaire avec un trou. Le faire pivoter modifie l'angle de départ de la première tranche.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

La méthode `setStartAngle` attend un double représentant les degrés. Les valeurs positives font pivoter dans le sens des aiguilles d'une montre, tandis que les valeurs négatives font pivoter dans le sens inverse.

## Étape 6 : Modifier la taille du trou de l'anneau (change doughnut chart size)

La taille du trou est exprimée comme une fraction du rayon du graphique. Une valeur de `0.5` signifie que le trou occupe 50 % du rayon total.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Astuce :** La plage valide est `0.0` (pas de trou, c’est‑à‑dire un graphique circulaire normal) à `0.9` (anneau très fin). Les valeurs en dehors de cette plage déclencheront une `IllegalArgumentException`.

## Étape 7 : Enregistrer le document modifié

Enfin, écrivez les modifications sur le disque.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Lorsque vous ouvrez `DoughnutFormatted.docx` dans Microsoft Word, vous verrez le graphique en anneau pivoté de 45° et le trou réduit à la moitié de sa taille d'origine.

## Exemple complet, exécutable

En assemblant toutes les pièces, voici le programme complet que vous pouvez copier‑coller dans votre IDE :

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Résultat attendu

L'exécution du programme affiche :

```
Chart rotated and doughnut size changed successfully.
```

L'ouverture de `DoughnutFormatted.docx` montre un graphique en anneau dont la première tranche commence à la position 45° et dont le rayon interne occupe la moitié du rayon externe.

## Variations courantes et cas limites

| Situation | Ce qu'il faut ajuster | Pourquoi c'est important |
|-----------|-----------------------|---------------------------|
| **Graphiques multiples** | Boucler sur `getChildNodes(NodeType.SHAPE, true)` et vérifier `shape.hasChart()` pour chaque élément | Assure que vous modifiez le graphique souhaité plutôt que le premier |
| **Graphique à barres ou en ligne** | `setStartAngle` ne s'applique pas ; utilisez `chart.getSeries().get(0).setFillFormat(...)` pour d'autres ajustements visuels | Tous les types de graphiques ne supportent pas la rotation ; seuls les graphiques en anneau/circulaire possèdent un angle de départ |
| **Graphique sans trou d'anneau** | Ignorer `setDoughnutHoleSize` ou d'abord convertir le type de graphique en anneau via `chart.setChartType(ChartType.DONUT)` | Modifier la taille du trou sur un graphique qui n'est pas en anneau déclenche une exception |
| **Documents volumineux** | Utilisez `DocumentBuilder.moveToDocumentStart()` et `builder.moveToNode(chartShape)` pour une navigation ciblée | Améliore les performances en évitant le parcours complet des nœuds non pertinents |

## Astuces pro pour une manipulation fiable des graphiques

* **Mémorisez la référence du graphique** – Si vous prévoyez de modifier plusieurs propriétés, conservez une variable locale `Chart` plutôt que d'appeler à plusieurs reprises `chartShape.getChart()`.
* **Validez les valeurs d'entrée** – Avant d'appeler `setStartAngle` ou `setDoughnutHoleSize`, vérifiez la plage afin d'éviter les erreurs d'exécution.
* **Utilisez une licence** – Le mode d'évaluation insère un filigrane sur la première page. Appliquer une licence (`License license = new License(); license.setLicense("Aspose.Words.lic");`) le supprime.

## Prochaines étapes

Maintenant que vous savez **how to rotate chart** et **change doughnut chart size**, vous pouvez explorer d'autres scénarios **modify chart in Word** :

* Modifier les couleurs des tranches avec `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Ajouter des étiquettes de données en appelant `chart.getSeries().get(0).setHasDataLabel(true)`.
* Exporter le graphique en tant qu'image en utilisant `chart.toImage(300, 300, ImageType.PNG)`.

Chaque extension suit le même schéma : obtenir l'objet `Chart`, appeler le setter approprié, puis enregistrer le document.

**Vous venez de maîtriser la rotation et le redimensionnement des graphiques en anneau dans Word avec Java.** N'hésitez pas à adapter le code à d'autres types de graphiques, à l'intégrer dans un pipeline de génération de documents plus vaste, ou à le combiner avec Aspose.Slides pour l'automatisation de PowerPoint. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques présentées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment créer un graphique en colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Masquer l'axe du graphique dans un document Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insérer un graphique à bulles dans un document Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}