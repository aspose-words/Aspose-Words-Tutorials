---
category: general
date: 2026-08-14
description: Regroupez des formes dans Word avec Java en utilisant Aspose.Words. Apprenez
  à créer une forme rectangulaire, à définir les dimensions de la forme et à regrouper
  plusieurs formes dans un document Word vierge.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: fr
lastmod: 2026-08-14
og_description: Regroupez des formes dans Word à l'aide d'Aspose.Words pour Java.
  Créez un document Word vierge, créez une forme rectangulaire, définissez les dimensions
  de la forme et regroupez plusieurs formes en quelques minutes.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Regrouper des formes dans Word – Exemple Java pour les développeurs
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Regrouper les formes dans Word – guide complet de programmation
url: /fr/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Regrouper des formes dans Word – guide complet de programmation

Si vous devez **regrouper des formes dans Word**, ce tutoriel vous guide à travers l’ensemble du processus avec Java et Aspose.Words. Vous apprendrez comment **créer un document Word vierge**, **créer une forme rectangulaire**, **définir les dimensions de la forme**, et enfin **regrouper plusieurs formes** afin qu’elles se comportent comme un seul objet.

Travailler avec des formes dans un fichier Word ressemble souvent à dessiner sur une toile sans pinceau. À la fin de ce guide, vous disposerez d’un extrait de code réutilisable que vous pourrez insérer dans n’importe quel projet Java, que vous génériez des rapports, des factures ou des modèles personnalisés.

## Ce dont vous aurez besoin

- Java 8 ou version supérieure
- Aspose.Words for Java (la dernière version, par ex., 24.9)
- Un IDE tel qu’IntelliJ IDEA ou Eclipse
- Une connaissance de base de la programmation orientée objet

Toutes ces prérequis sont gratuits à installer, et le code ci‑dessous se compile avec une seule dépendance Maven :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Étape 1 : Créer un document Word vierge et initialiser le builder

La première chose à faire est **de créer un document Word vierge**. Cela vous fournit une toile propre sur laquelle vous pourrez insérer des formes ultérieurement.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` représente le fichier *.docx* complet, tandis que `DocumentBuilder` est l’assistant qui insère paragraphes, tableaux et formes. L’initialisation de ces deux objets constitue la base de toute tâche d’automatisation Word.

## Étape 2 : Insérer un conteneur de forme groupée

Une **forme groupée** agit comme un dossier pouvant contenir d’autres formes. Nous créons d’abord le conteneur avec une taille fixe de 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

La méthode `insertGroupShape` renvoie un objet `GroupShape`. Toutes les formes suivantes que vous souhaitez traiter comme une unité unique doivent être ajoutées à cet objet.

## Étape 3 : Créer des formes rectangulaires et définir leurs dimensions

Nous **créons maintenant des objets de forme rectangulaire**, configurons leur taille et les positionnons à l’intérieur du groupe. Cette étape montre également comment **définir précisément les dimensions de la forme**.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Les deux rectangles partagent les mêmes dimensions, mais leurs propriétés `left` diffèrent, de sorte qu’ils apparaissent côte à côte. Vous pouvez modifier `setTop` et `setLeft` pour organiser n’importe quelle mise en page dont vous avez besoin.

## Étape 4 : Enregistrer le document contenant les rectangles groupés

Une fois les formes placées dans le groupe, il suffit d’enregistrer le `Document`. Le fichier résultant affichera deux rectangles qui se déplacent ensemble lorsqu’ils sont sélectionnés.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

L’exécution du programme crée `GroupShape.docx` dans le répertoire de travail. Ouvrez‑le avec Microsoft Word, sélectionnez un rectangle, et vous constaterez que tout le groupe se déplace comme une unité — exactement ce que les **formes groupées dans Word** sont censées faire.

![Group shapes in Word example](group-shapes.png){alt="Exemple de formes groupées dans Word"}

*Figure : Deux formes rectangulaires groupées dans un document Word.*

## Astuce : Réutiliser le même groupe de formes

Si vous devez ajouter d’autres formes plus tard (par ex., des cercles, des zones de texte), conservez une référence à `groupShape` et continuez d’appeler `appendChild`. Cela évite de recréer le conteneur et garantit que tous les membres restent synchronisés.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Cas limites et questions fréquentes

- **Que se passe‑t‑il si les formes se chevauchent ?** Le chevauchement est autorisé ; Word les rend dans l’ordre où elles ont été ajoutées. Utilisez `setZOrder` si vous avez besoin d’un empilement explicite.
- **Puis‑je regrouper des formes sur différentes pages ?** Non. Un `GroupShape` est limité à une seule page car son système de coordonnées est relatif à la page.
- **Les formes groupées héritent‑elles du formatage ?** Chaque enfant conserve son propre formatage (couleur de remplissage, style de ligne). Pour appliquer un style uniforme, parcourez `groupShape.getChildNodes()` et définissez les propriétés par programme.

## Code source complet à titre de référence

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

L’exécution du programme produit un fichier DOCX où les deux rectangles sont **groupés**. Sélectionner l’un d’eux déplace les deux, confirmant que vous avez réussi à **regrouper plusieurs formes**.

## Conclusion

Vous savez maintenant comment **regrouper des formes dans Word** avec Java, depuis **la création d’un document Word vierge** jusqu’**à la création d’une forme rectangulaire**, **la définition des dimensions de la forme**, et enfin **le regroupement de plusieurs formes** en un seul objet déplaçable. Ce modèle s’étend à n’importe quel nombre de formes et peut être combiné avec du texte, des images ou des graphiques pour créer des documents riches et programmatiques.

### Et après ?

- Explorez **le regroupement de plusieurs formes** de types différents (ellipses, flèches, zones de texte).
- Appliquez des couleurs de remplissage ou des bordures en appelant `shape.getFillColor()` et `shape.getLine().setColor()`.
- Insérez la forme groupée dans une cellule de tableau pour des rapports structurés.
- Combinez cette approche avec la fusion de courrier pour générer des contrats personnalisés incluant des graphiques de marque.

N’hésitez pas à expérimenter, à adapter les dimensions ou à intégrer du contenu supplémentaire. Une fois que vous maîtrisez le regroupement, vos scripts d’automatisation Word deviennent beaucoup plus flexibles et maintenables. Bon codage !

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}