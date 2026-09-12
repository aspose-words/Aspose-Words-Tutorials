---
category: general
date: 2026-09-11
description: Comment modifier un graphique dans un document Word avec Java – apprenez
  à mettre à jour les paramètres du graphique, activer les lignes de grille, modifier
  les options du graphique et enregistrer le document mis à jour.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: fr
lastmod: 2026-09-11
og_description: Comment modifier un graphique dans un document Word avec Java. Suivez
  ce guide pour mettre à jour les paramètres du graphique, activer les quadrillages,
  changer les options du graphique et enregistrer le document mis à jour.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Comment modifier un graphique dans un document Word avec Java – guide complet
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Comment modifier un graphique dans un document Word avec Java
url: /fr/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment modifier un graphique dans un document Word avec Java

Si vous devez **modifier un graphique** dans un fichier Word, ce guide vous montre les étapes exactes. Vous apprendrez comment mettre à jour les paramètres du graphique, activer les quadrillages du graphique, modifier les options du graphique, et enfin **enregistrer le document mis à jour** sans perdre aucun formatage.

Travailler avec des graphiques de manière programmatique ressemble souvent à une opération boîte noire, surtout lorsque vous souhaitez ajuster des détails visuels tels que les graduations ou les quadrillages. Ce tutoriel couvre tout ce que vous devez savoir, du chargement du document à la persistance des modifications. Aucun outil externe n’est requis — seulement la bibliothèque Aspose.Words for Java (version 24.9 ou ultérieure).

À la fin de cet article, vous serez capable de :

* Charger un fichier `.docx` contenant un graphique.
* Localiser la forme du graphique et modifier ses propriétés.
* Activer les quadrillages du graphique (graduations) et ajuster d’autres options.
* **Enregistrer le document mis à jour** dans un nouveau fichier.

## Prérequis

* Java 17 ou version ultérieure installé sur votre machine.  
* Maven ou Gradle pour gérer les dépendances.  
* Aspose.Words for Java 24.9+ (la version qui a introduit `setShowGraduations`).  
* Un document Word (`input.docx`) contenant déjà au moins un graphique.

Si vous ne connaissez pas Aspose.Words, considérez-le comme une API complète qui vous permet de lire, modifier et écrire des documents Word de façon programmatique — similaire à la manipulation du DOM dans un navigateur web.

## Étape 1 : Configurer le projet et importer la bibliothèque

Créez un nouveau projet Maven ou ajoutez la dépendance à un projet existant :

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Astuce :** Utilisez la dernière version stable pour vous assurer de disposer de la méthode `setShowGraduations`. Les versions antérieures ne compileront pas.

## Étape 2 : Charger le document Word contenant un graphique

La première action dans tout flux de travail **modifier un graphique** consiste à charger le fichier source. Aspose.Words représente l’ensemble du document avec la classe `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

L’objet `Document` vous donne accès à chaque nœud du fichier, y compris les formes, les tableaux et les paragraphes.  

## Étape 3 : Localiser la première forme de graphique dans le document

Les graphiques sont stockés sous forme de nœuds `Shape` dont le rendu est un `Chart`. Pour modifier un graphique, vous devez d’abord récupérer ce nœud.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Si le document contient plusieurs graphiques, parcourez `shapes` et vérifiez `chartShape.getChart() != null` avant de caster. Cela évite `ClassCastException` et garantit que vous **modifiez les options du graphique** uniquement sur des objets graphiques valides.

## Étape 4 : Activer les quadrillages du graphique (graduations) – une nouvelle propriété dans la version 24.9

La propriété `setShowGraduations` active ou désactive la visibilité des quadrillages mineurs sur l’axe des valeurs. Leur activation améliore souvent la lisibilité pour des ensembles de données denses.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Pourquoi c’est important :** Les quadrillages offrent aux spectateurs une référence visuelle pour chaque point de données, facilitant la détection des tendances. La valeur par défaut est `false`, vous devez donc les activer explicitement lorsque nécessaire.

Vous pouvez également personnaliser d’autres aspects, tels que les quadrillages majeurs, les titres d’axes ou le placement de la légende. Ci‑dessous, un exemple de modification du titre du graphique et de la position de la légende — les deux faisant partie de **modifier les options du graphique**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Étape 5 : Enregistrer le document avec les paramètres du graphique mis à jour

Après avoir modifié le graphique, persistez les changements. Cette étape complète la phase **enregistrer le document mis à jour**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

L’exécution du programme générera `output.docx` où le graphique affiche désormais les quadrillages, un nouveau titre et une légende déplacée. Ouvrez le fichier dans Microsoft Word pour vérifier les changements visuels.

## Code source complet (exécutable)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Résultat attendu

Lorsque vous ouvrez `output.docx` :

* Le graphique affiche des quadrillages mineurs sur l’axe des valeurs.  
* Le titre indique **« Sales Overview 2026 »**.  
* La légende apparaît en bas du graphique.

Si le graphique original possédait déjà des quadrillages, l’apparence visuelle reste inchangée, confirmant que le code est **idempotent**.

## Questions fréquentes et gestion des cas limites

### Que faire si le document ne contient aucun graphique ?

Tenter de caster une forme qui n’est pas un graphique déclenchera une `ClassCastException`. Protégez‑vous en vérifiant le type de forme :

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Comment modifier un graphique spécifique au lieu du premier ?

Parcourez `shapes` et faites correspondre un titre connu ou un identifiant alternatif :

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Puis‑je désactiver les quadrillages ultérieurement ?

Oui, il suffit de définir la propriété à `false` :

```java
chart.setShowGraduations(false);
```

### Cette méthode fonctionne‑t‑elle avec les fichiers `.doc` (binaires) ?

Aspose.Words abstrait le format de fichier, ainsi le même code fonctionne pour `.doc` et `.docx`. Cependant, certaines fonctionnalités récentes des graphiques (comme les graduations) ne sont stockées que dans le format OOXML, vous ne verrez donc l’effet qu’en enregistrant au format `.docx`.

## Conseils pour un code prêt pour la production

* **Validez les chemins d’entrée** – utilisez `Files.exists(Paths.get(inputPath))` avant le chargement.  
* **Enveloppez les appels API** dans des blocs try‑catch pour exposer les détails de `Exception`, surtout lors du traitement de documents corrompus.  
* **Libérez les ressources** – bien qu’Aspose.Words gère la mémoire, appeler `doc.close()` (ou utiliser try‑with‑resources si disponible) peut libérer les handles natifs plus tôt.  
* **Vérification de version** – assurez‑vous que la version de la bibliothèque d’exécution est ≥ 24.9 avant d’appeler `setShowGraduations`. Vous pouvez interroger `License.getVersion()` si vous avez besoin d’une protection programmatique.

## Conclusion

Vous savez maintenant **comment modifier des graphiques** dans un document Word avec Java. Le processus — charger le document, localiser le graphique, activer les quadrillages du graphique, modifier les options du graphique, et **enregistrer le document mis à jour** — couvre les scénarios les plus courants de manipulation programmatique de graphiques.  

À partir de là, vous pouvez explorer des personnalisations supplémentaires comme changer les couleurs des séries de données, appliquer des styles de graphique, ou exporter le graphique en image. Chacune de ces tâches suit le même schéma : récupérer l’instance `Chart`, ajuster ses propriétés, et **enregistrer le document mis à jour**.

Bon codage, et n’hésitez pas à expérimenter d’autres paramètres de graphique pour répondre à vos besoins de reporting !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un graphique à colonnes avec Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Comment enregistrer un document au format PDF avec Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Définir les options par défaut pour les étiquettes de données dans un graphique](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}