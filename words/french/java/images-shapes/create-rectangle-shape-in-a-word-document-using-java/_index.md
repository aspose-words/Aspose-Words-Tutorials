---
category: general
date: 2026-11-15
description: Créer une forme rectangulaire dans Word avec Java et apprendre à ajouter
  des formes à Word, à définir les dimensions de la forme et à enregistrer le document
  Word efficacement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: fr
lastmod: 2026-11-15
og_description: Créer une forme rectangulaire dans un document Word en utilisant Java.
  Apprenez à ajouter des formes à Word, à définir les dimensions des formes et à enregistrer
  le document Word en quelques minutes.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Créer une forme rectangulaire dans Word avec Java – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Créer une forme rectangulaire dans un document Word avec Java
url: /fr/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer une forme rectangulaire dans un document Word avec Java

Si vous devez **créer une forme rectangulaire** à l’intérieur d’un fichier Word, ce guide vous montre exactement comment le faire avec Java. Vous verrez comment **ajouter des formes à Word**, contrôler le **set shape dimensions**, puis **save Word document** sans quitter votre IDE.

Dans les sections qui suivent, vous obtiendrez un exemple complet et exécutable, une explication de chaque ligne, ainsi que des astuces pour les pièges courants tels que les problèmes de dimensionnement et la compatibilité du document. Aucun référentiel externe n’est requis — seulement la bibliothèque Aspose.Words for Java.

## Ce que vous allez apprendre

* Comment initialiser un `Document` et un `DocumentBuilder`.
* Comment insérer un **group shape** et placer un rectangle à l’intérieur.
* Comment **define shape size** en utilisant `setWidth` et `setHeight`.
* Comment **save Word document** au format `.docx`.
* Gestion des cas limites pour différentes tailles de page et réglages DPI.

### Prérequis

* Java 17 ou ultérieur (le code compile également avec Java 8).
* Aspose.Words for Java 23.10 ou plus récent – vous pouvez l’obtenir depuis Maven Central.
* Une compréhension de base de la syntaxe Java et des concepts orientés objet.

> **Astuce pro :** Si vous prévoyez d’ajouter d’autres formes plus tard (par ex., des cercles ou des zones de texte), conservez‑les dans le même `GroupShape`. Cela rend le déplacement, la rotation ou le formatage de l’ensemble beaucoup plus simples.

## Étape 1 : Initialiser le document et le builder

La première étape consiste à créer un fichier Word vierge et un `DocumentBuilder` qui vous permet d’écrire du contenu.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Pourquoi c’est important :* Un `Document` représente le fichier complet, tandis que `DocumentBuilder` fournit des méthodes de haut niveau pour insérer du texte, des tableaux et des **shapes**. Sans le builder, vous devriez manipuler les nœuds de bas niveau manuellement.

## Étape 2 : Insérer un group shape pour contenir plusieurs formes

Un **group shape** agit comme un conteneur ; vous pouvez y ajouter plusieurs formes et les traiter comme un seul objet par la suite (par ex., les déplacer ou les faire pivoter ensemble).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Pourquoi utiliser un group shape ?* Si vous décidez plus tard d’ajouter des flèches, des cercles ou des libellés autour du rectangle, le groupe maintient tout aligné. Il simplifie également le workflow **add shapes to Word** car vous n’avez besoin que d’un appel à `appendChild` pour chaque nouvelle forme.

## Étape 3 : Créer la forme rectangulaire

Nous créons maintenant le rectangle réel qui vivra à l’intérieur du groupe. Le constructeur `Shape` nécessite le `Document` propriétaire et le type de forme souhaité.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Pourquoi un rectangle ?* `ShapeType.RECTANGLE` est le primitive le plus courant pour mettre en évidence des sections, créer des espaces réservés ou dessiner de simples maquettes UI directement dans Word.

## Étape 4 : Définir la taille du rectangle

Définir les dimensions est l’endroit où **set shape dimensions** devient crucial. Vous pouvez utiliser n’importe quelle unité de mesure prise en charge par Aspose.Words ; la valeur par défaut est le point (1 pt = 1/72 pouce).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Remarque :** Si vous préférez les millimètres, appelez `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` où `1.39 in ≈ 35 mm`. Cela montre la flexibilité de **define shape size**.

## Étape 5 : Ajouter le rectangle au group shape

En ajoutant le rectangle au groupe précédemment créé, il apparaît dans le document.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

À ce stade, le rectangle est positionné dans le coin supérieur gauche du groupe. Vous pouvez le déplacer plus tard avec `rectangle.setLeft(...)` et `rectangle.setTop(...)` si vous avez besoin d’un placement précis.

## Étape 6 : (Facultatif) Enregistrer le document pour voir le résultat

Enfin, écrivez le document sur le disque. C’est l’étape **save Word document** qui produit un fichier `.docx` que vous pouvez ouvrir avec Microsoft Word, LibreOffice ou Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

L’exécution du programme crée `RectangleShapeDemo.docx` contenant un seul rectangle à l’intérieur d’un group shape. L’ouverture du fichier montre un rectangle blanc simple—exactement de la taille que vous avez définie.

### Résultat attendu

* Un fichier Word nommé `RectangleShapeDemo.docx`.
* Dans le premier paragraphe, un group shape contenant un rectangle de 100 pt × 50 pt.
* Aucun texte n’est ajouté, donc le rectangle apparaît sur une page blanche.

## Variantes courantes et cas limites

| Situation | Comment adapter le code |
|-----------|--------------------------|
| **Différente taille de page** (par ex., A4) | Appelez `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` avant d’insérer la forme. |
| **DPI plus élevé pour l’impression** | Multipliez largeur/hauteur par le facteur DPI souhaité, par ex., `rectangle.setWidth(200 * 2);` pour une résolution double. |
| **Ajouter un libellé texte à l’intérieur du rectangle** | Créez une `Shape` de type `TEXT_BOX`, définissez son `setWidth`/`setHeight` pour correspondre au rectangle, puis ajoutez‑la au même `GroupShape`. |
| **Faire pivoter le rectangle** | Utilisez `rectangle.setRotationAngle(45);` pour pivoter de 45 degrés dans le sens horaire. |
| **Enregistrer en PDF au lieu de DOCX** | Remplacez `document.save("output.docx");` par `document.save("output.pdf");` – la même API fonctionne pour le PDF, en conservant le rectangle. |

## Astuces pro pour une implémentation robuste

1. **Réutiliser le builder** – après avoir inséré le group shape, vous pouvez continuer à ajouter des paragraphes ou des tableaux sans créer une nouvelle instance de builder.
2. **Libérer les ressources** – bien que le ramasse‑miettes de Java gère la plupart des objets, appeler explicitement `document.close();` (si vous utilisez des flux) évite les fuites de descripteurs de fichiers.
3. **Valider les dimensions** – avant d’appeler `setWidth`/`setHeight`, assurez‑vous que les valeurs sont positives ; des valeurs négatives déclenchent `IllegalArgumentException`.
4. **Compatibilité des versions** – le code fonctionne avec Aspose.Words 23.x et ultérieur. Les versions antérieures peuvent nécessiter `Shape.setSize(width, height)` au lieu des setters séparés.

## Exemple complet et exécutable

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Vérification du résultat :** Ouvrez `output/RectangleShapeDemo.docx` dans Microsoft Word. Vous devez voir un rectangle de la taille spécifiée centré en haut de la première page. Si le rectangle apparaît trop petit, ajustez les valeurs passées à `setWidth` et `setHeight`.

## Conclusion

Vous savez maintenant comment **create rectangle shape** dans un fichier Word avec Java, comment **add shapes to Word** via un `GroupShape`, comment **set shape dimensions** et **define shape size**, et enfin comment **save Word document** pour une distribution ultérieure. Le même schéma fonctionne pour d’autres types de formes, vous permettant de créer des diagrammes complexes de façon programmatique.

### Et ensuite ?

* Explorez **add shapes to Word** en insérant des cercles, des flèches ou des zones de texte.
* Combinez plusieurs formes dans un seul `GroupShape` et appliquez des transformations (rotation, retournement).
* Générez des rapports qui intègrent des graphiques sous forme de formes, puis **save Word document** en PDF pour le partage.

N’hésitez pas à expérimenter avec les dimensions, les couleurs et le positionnement pour les adapter à votre scénario spécifique. Bonne programmation !

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}