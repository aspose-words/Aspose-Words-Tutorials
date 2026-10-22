---
category: general
date: 2026-10-16
description: Apprenez à regrouper des formes dans Word en utilisant Java. Ce tutoriel
  montre comment ajouter une forme rectangulaire, définir la taille et les dimensions
  de la forme, et enregistrer le document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- set shape dimensions
- rectangle shape code
language: fr
lastmod: 2026-10-16
og_description: Regroupez des formes dans Word avec Java. Ajoutez une forme rectangle,
  définissez la taille et les dimensions de la forme, et créez des documents professionnels
  de manière programmatique.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Regrouper des formes dans Word avec Java – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  headline: How to group shapes in Word with Java – complete guide
  type: TechArticle
- description: Learn how to group shapes in Word using Java. This tutorial shows how
    to add rectangle shape, set shape size and dimensions, and save the document.
  name: How to group shapes in Word with Java – complete guide
  steps:
  - name: Expected output
    text: '- A file named **GroupShapeDemo.docx** appears in the project folder. -
      Opening the file in Word shows two shapes (a rectangle and an ellipse) that
      are grouped together. - Dragging either shape moves the whole group, confirming
      that **group shapes in word** works as intended.'
  - name: Pro tip
    text: 'When you need to **set shape dimensions** based on dynamic data (e.g.,
      a barcode length), calculate the width/height in points first:'
  - name: What’s next?
    text: '- Explore **add rectangle shape** variations such as rounded corners (`ShapeType.RECTANGLE`
      with `setCornerRadius`). - Combine **group shapes in word** with tables or charts
      for richer documents. - Look into the Aspose.Words API for **text wrapping**
      (`shape.setWrapType(WrapType.SQUARE)`) to control'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Comment regrouper des formes dans Word avec Java – guide complet
url: /fr/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans Word avec Java – guide complet

Si vous devez **regrouper des formes dans Word** de manière programmatique, ce tutoriel vous fournit une solution prête à l’emploi. Vous verrez comment **ajouter une forme rectangle**, ajuster sa taille, définir les dimensions de la forme, et enfin enregistrer un fichier DOCX contenant un rectangle groupé et une ellipse.

Regrouper des formes dans Word est utile pour créer des diagrammes complexes, créer des composants graphiques réutilisables, ou simplement garder des objets liés ensemble lorsque le document est modifié ultérieurement. Le code utilise la bibliothèque Aspose.Words for Java, qui fonctionne avec n’importe quel JDK récent et ne nécessite pas l’installation de Microsoft Word.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

| Exigence | Raison |
|----------|--------|
| Java 17 (ou version ultérieure) | La bibliothèque cible les environnements d’exécution Java modernes. |
| Aspose.Words for Java (dernière version) | Fournit les classes `Document`, `DocumentBuilder`, `GroupShape` et `Shape` utilisées dans l’exemple. |
| Un IDE ou un outil de construction (Maven/Gradle) | Pour compiler et exécuter l’exemple. |
| Connaissances de base de la syntaxe Java | Nécessaires pour comprendre le flux du code. |

Ajoutez la dépendance Aspose.Words à votre projet. Pour Maven :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version> <!-- Use the latest version -->
</dependency>
```

Ou pour Gradle :

```gradle
implementation 'com.aspose:aspose-words:23.10'
```

## Vue d’ensemble de la solution

Le tutoriel suit un schéma clair **problème → solution → explication** :

1. **Créer un nouveau document Word** et obtenir un `DocumentBuilder`.  
2. **Insérer un conteneur `GroupShape`** qui contiendra plusieurs formes.  
3. **Ajouter un rectangle**, définir sa largeur/hauteur (l’étape **set shape size**), et l’attacher au groupe.  
4. **Ajouter une ellipse**, la positionner à l’intérieur du même groupe, et également définir ses dimensions.  
5. **Enregistrer** le document sur le disque.

Chaque étape inclut le **pourquoi** du code, afin que vous compreniez ce que fait l’API et comment l’adapter à d’autres scénarios.

## Étape 1 : Créer le document et un DocumentBuilder

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to work with it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Pourquoi c’est important :** `Document` représente l’ensemble du fichier DOCX, tandis que `DocumentBuilder` est un assistant qui vous permet d’insérer du contenu sans gérer les nœuds de bas niveau. Les créer d’abord vous donne une toile vierge pour toutes les opérations de forme suivantes.

## Étape 2 : Insérer un conteneur GroupShape

```java
        // Step 2: Insert a GroupShape container that will hold multiple shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Un `GroupShape` fonctionne comme un **dossier** pour les objets de dessin. Lorsque vous déplacez, faites pivoter ou supprimez le groupe, toutes les formes enfants le suivent automatiquement. C’est le cœur du **group shapes in word**.

## Étape 3 : Ajouter une forme rectangle – le code de la forme rectangle

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape width in points
        rectangleShape.setHeight(50);   // set shape height in points
        groupShape.appendChild(rectangleShape);
```

- **add rectangle shape** – Le constructeur `Shape` reçoit `ShapeType.RECTANGLE`, ce qui indique à Aspose.Words de rendre un contour rectangulaire.  
- **set shape size** – `setWidth` et `setHeight` définissent les **dimensions de la forme** en points (1 pt = 1/72 in). C’est la façon la plus courante de contrôler la taille visuelle.  
- **Why we use `appendChild`** – Il attache le rectangle au `GroupShape` afin qu’il se déplace avec le groupe.

## Étape 4 : Ajouter une ellipse et la positionner à l’intérieur du groupe

```java
        // Step 4: Create an ellipse, set its size and position inside the group, then add it
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);      // set shape width
        ellipseShape.setHeight(80);     // set shape height (making it a circle)
        ellipseShape.setLeft(120);      // position relative to the group container
        groupShape.appendChild(ellipseShape);
```

L’ellipse montre **set shape dimensions** au‑delà d’un simple rectangle. En appelant `setLeft`, nous contrôlons le décalage horizontal à l’intérieur du groupe, ce qui est utile lors de l’arrangement de plusieurs objets.

## Étape 5 : Enregistrer le document

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Lorsque vous ouvrez *GroupShapeDemo.docx* dans Microsoft Word, vous verrez un rectangle et une ellipse verrouillés ensemble à l’intérieur d’un seul groupe. Sélectionner l’une ou l’autre forme sélectionnera le groupe entier — exactement ce à quoi vous vous attendez avec **group shapes in word**.

## Exemple complet, exécutable

En assemblant toutes les pièces, voici le fichier source complet que vous pouvez copier dans votre IDE :

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will hold the rectangle and ellipse
        GroupShape groupShape = builder.insertGroupShape();

        // Add a rectangle (add rectangle shape) and define its size (set shape size)
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        groupShape.appendChild(rectangleShape);

        // Add an ellipse, set its dimensions, and position it inside the group
        Shape ellipseShape = new Shape(document, ShapeType.ELLIPSE);
        ellipseShape.setWidth(80);
        ellipseShape.setHeight(80);
        ellipseShape.setLeft(120);      // horizontal offset relative to the group
        groupShape.appendChild(ellipseShape);

        // Save the document to the local file system
        document.save("GroupShapeDemo.docx");
    }
}
```

### Résultat attendu

- Un fichier nommé **GroupShapeDemo.docx** apparaît dans le dossier du projet.  
- L’ouverture du fichier dans Word montre deux formes (un rectangle et une ellipse) qui sont groupées ensemble.  
- Faire glisser l’une ou l’autre forme déplace tout le groupe, confirmant que **group shapes in word** fonctionne comme prévu.

## Variations courantes et cas limites

| Scénario | Ce qu’il faut modifier | Pourquoi |
|----------|------------------------|----------|
| **Different shape types** (e.g., triangle) | Utilisez `ShapeType.TRIANGLE` ou toute autre valeur d’énumération lors de la construction de `Shape`. | Permet de créer des diagrammes plus complexes. |
| **Setting fill color** | Appelez `shape.getFillColor().setColor(Color.BLUE);` après la création de la forme. | Améliore l’apparence visuelle sans affecter le groupement. |
| **Rotating the group** | `groupShape.setRotationAngle(45);` | Fait pivoter toutes les formes enfants ensemble, utile pour les icônes. |
| **Adding text inside a shape** | `shape.appendChild(new Paragraph(document));` puis ajoutez un `Run` avec du texte. | Transforme la forme en étiquette ou appel. |
| **Saving to a stream** | `ByteArrayOutputStream out = new ByteArrayOutputStream(); document.save(out, SaveFormat.DOCX);` | Utile pour les services web qui renvoient directement le document. |

### Astuce pro

Lorsque vous devez **set shape dimensions** en fonction de données dynamiques (par ex., la longueur d’un code‑barres), calculez d’abord la largeur/hauteur en points :

```java
double inches = 2.5;
int points = (int)(inches * 72); // 1 inch = 72 points
shape.setWidth(points);
```

Cela évite les valeurs codées en dur et rend votre code adaptable.

## Conclusion

Vous savez maintenant comment **group shapes in Word** avec Java, comment **add rectangle shape**, et comment **set shape size** ainsi que **set shape dimensions** avec un code concis et prêt pour la production. En suivant les étapes ci‑dessus, vous pouvez créer des groupes graphiques réutilisables, les intégrer dans des rapports automatisés, ou développer des outils de diagramme personnalisés sans jamais ouvrir Word manuellement.

### Et après ?

- Explorez les variantes **add rectangle shape** telles que les coins arrondis (`ShapeType.RECTANGLE` avec `setCornerRadius`).  
- Combinez **group shapes in word** avec des tableaux ou des graphiques pour des documents plus riches.  
- Examinez l’API Aspose.Words pour **text wrapping** (`shape.setWrapType(WrapType.SQUARE)`) afin de contrôler comment le texte environnant interagit avec vos graphiques groupés.

N’hésitez pas à expérimenter, à adapter le **rectangle shape code**, et à partager vos résultats.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}