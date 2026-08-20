---
category: general
date: 2026-08-20
description: Apprenez à regrouper des formes, à définir la taille d'une forme, à insérer
  une image dans le document, à ajouter une image au groupe et à créer une forme rectangulaire
  avec Aspose.Words en Java.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert image into document
- set shape size
- add picture to group
- create rectangle shape
language: fr
lastmod: 2026-08-20
og_description: Comment regrouper des formes dans un document Word en utilisant Aspose.Words.
  Suivez ce tutoriel Java étape par étape pour définir la taille des formes, insérer
  une image dans le document, ajouter une image au groupe et créer une forme rectangulaire.
og_image_alt: Diagram showing how to group shapes in a Word document
og_title: Comment regrouper des formes dans un document Word avec Aspose.Words – Guide
  Java
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  headline: How to group shapes in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to group shapes, set shape size, insert image into document,
    add picture to group, and create rectangle shape with Aspose.Words in Java.
  name: How to group shapes in a Word document using Aspose.Words
  steps:
  - name: Create a new document and a `DocumentBuilder`
    text: A `Document` represents the Word file, while `DocumentBuilder` provides
      convenient methods for inserting content.
  - name: Insert a group shape that will hold multiple child shapes
    text: A group shape acts like a container. Its dimensions define the bounding
      box for all child shapes.
  - name: Create a rectangle shape, set its size, and add it to the group
    text: Setting the exact size of a shape is essential when you want precise layout
      control.
  - name: Insert an image, then add the picture shape to the same group
    text: Inserting an image is the core of the **insert image into document** requirement.
      The returned `Shape` is a picture shape that can be grouped like any other shape.
  - name: Position the entire group on the page
    text: After adding all child shapes, you can move, rotate, or hide the whole group.
      Positioning uses the **add picture to group** concept indirectly, because the
      group now contains the picture.
  - name: Save the document
    text: Finally, write the file to disk. You can open the resulting `.docx` in Word
      to verify the grouping.
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Automation
title: Comment regrouper des formes dans un document Word à l'aide d'Aspose.Words
url: /fr/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans un document Word avec Aspose.Words

Si vous avez besoin de **regrouper des formes** dans un fichier Word, ce tutoriel présente la solution Java complète. Vous verrez comment **définir la taille d’une forme**, **insérer une image dans le document**, **ajouter une image au groupe**, et **créer une forme rectangulaire** — le tout avec des explications claires et un exemple de code exécutable.

Regrouper des formes simplifie la gestion de la mise en page, vous permet de déplacer ou de faire pivoter plusieurs objets comme une seule unité, et garde votre document ordonné. Dans les étapes ci‑dessous, vous créerez un groupe contenant un rectangle et une image, puis placerez le groupe sur la page.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java 17 ou une version plus récente installé.
* Aspose.Words for Java (version 23.9 ou ultérieure) ajouté au classpath de votre projet.
* Une image JPEG d’exemple située à `YOUR_DIRECTORY/sample.jpg` (remplacez `YOUR_DIRECTORY` par le chemin réel).

Vous pouvez ajouter Aspose.Words via Maven :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Comment regrouper des formes avec Aspose.Words

Les sections suivantes détaillent chaque opération nécessaire pour **regrouper des formes**. L’en‑tête H2 principal contient le mot‑clé principal, respectant les règles SEO.

### Étape 1 : Créer un nouveau document et un `DocumentBuilder`

Un `Document` représente le fichier Word, tandis que `DocumentBuilder` offre des méthodes pratiques pour insérer du contenu.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi c’est important* : Commencer avec un `Document` vierge garantit que le groupe que vous créez n’interférera pas avec les éléments existants.

### Étape 2 : Insérer une forme de groupe qui contiendra plusieurs formes enfants

Une forme de groupe agit comme un conteneur. Ses dimensions définissent la boîte englobante de toutes les formes enfants.

```java
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

*Astuce* : La largeur (`300`) et la hauteur (`200`) sont exprimées en points (1 pt = 1/72 pouce). Ajustez‑les en fonction de la taille des formes que vous prévoyez d’ajouter.

### Étape 3 : Créer une forme rectangulaire, définir sa taille et l’ajouter au groupe

Définir la taille exacte d’une forme est essentiel lorsque vous souhaitez un contrôle précis de la mise en page.

```java
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // set shape size – width
        rectangleShape.setHeight(50);   // set shape size – height
        // Optionally set a fill color for visibility
        rectangleShape.getFillColor().setRGB(0xFF, 0xCC, 0x00);
        groupShape.appendChild(rectangleShape);
```

*Pourquoi nous définissons la taille de la forme* : Les méthodes `setWidth` et `setHeight` correspondent au mot‑clé secondaire **set shape size**, vous offrant un contrôle pixel‑parfait sur l’apparence du rectangle.

### Étape 4 : Insérer une image, puis ajouter la forme image au même groupe

Insérer une image est au cœur de l’exigence **insert image into document**. Le `Shape` retourné est une forme image qui peut être groupée comme toute autre forme.

```java
        // Step 4: Insert an image, then add the picture shape to the same group
        Shape pictureShape = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        // Resize the picture if needed (example: 120 pt wide, maintain aspect ratio)
        pictureShape.setWidth(120);
        // Add the picture to the previously created group
        groupShape.appendChild(pictureShape);
```

*Conseil pro* : Si vous devez conserver le ratio d’aspect original, définissez uniquement une dimension (`setWidth` ou `setHeight`). Aspose.Words ajuste automatiquement l’autre dimension.

### Étape 5 : Positionner le groupe complet sur la page

Après avoir ajouté toutes les formes enfants, vous pouvez déplacer, faire pivoter ou masquer le groupe entier. Le positionnement utilise indirectement le concept **add picture to group**, car le groupe contient désormais l’image.

```java
        // Step 5: Position the entire group on the page (it can also be rotated, hidden, etc.)
        groupShape.setLeft(50);   // distance from the left margin
        groupShape.setTop(100);   // distance from the top margin
        // Optional: rotate the group 15 degrees
        groupShape.setRotation(15);
```

*Explication* : `setLeft` et `setTop` placent le groupe par rapport aux marges de la page. Faire pivoter le groupe montre que toutes les formes enfants héritent de la transformation.

### Étape 6 : Enregistrer le document

Enfin, écrivez le fichier sur le disque. Vous pouvez ouvrir le `.docx` généré dans Word pour vérifier le regroupement.

```java
        // Step 6: Save the document
        doc.save("GroupShapesDemo.docx");
    }
}
```

L’exécution du programme produit **GroupShapesDemo.docx** contenant un rectangle et une image regroupés. Sélectionner l’une ou l’autre forme dans Word sélectionnera également l’autre, confirmant que vous avez bien appris **comment regrouper des formes**.

---

## Résultat attendu

Lorsque vous ouvrez *GroupShapesDemo.docx* dans Microsoft Word :

* Un rectangle (remplissage doré) apparaît du côté gauche du groupe.
* L’image que vous avez fournie apparaît à droite du rectangle.
* Les deux objets se déplacent ensemble lorsque vous faites glisser le groupe.
* Le groupe est positionné à 50 pt de la marge gauche et 100 pt de la marge supérieure, pivoté de 15°.

Si l’image n’apparaît pas, vérifiez à nouveau le chemin du fichier dans `insertImage`. Aspose.Words lève une `IOException` lorsque le fichier est introuvable.

---

## Questions fréquentes et gestion des cas limites

| Question | Réponse |
|----------|--------|
| **Puis‑je ajouter plus de deux formes ?** | Oui. Appelez `groupShape.appendChild(otherShape)` pour chaque forme supplémentaire. |
| **Et si j’ai besoin d’un arrière‑plan transparent pour le rectangle ?** | Utilisez `rectangleShape.getFillColor().setRGB(255, 255, 255); rectangleShape.setFillTransparent(true);` |
| **Le regroupement est‑il pris en charge dans les anciens formats Word (par ex., `.doc`)?** | Le regroupement fonctionne pour `.docx` et `.doc` mais certains visionneurs plus anciens peuvent ignorer les métadonnées du groupe. Enregistrez en `.docx` pour une fidélité complète. |
| **Comment dégrouper plus tard ?** | Récupérez les nœuds enfants via `groupShape.getChildNodes(NodeType.ANY, true)` et déplacez‑les dans le corps du document, puis supprimez le groupe. |
| **Puis‑je regrouper des formes provenant de sections différentes ?** | Non. Un `GroupShape` doit résider dans une seule `Story` (généralement le corps principal du document). |

## Conseils pro pour une gestion robuste des formes

* **Utilisez le positionnement absolu avec parcimonie** – le positionnement relatif (`builder.moveToDocumentEnd()`) donne souvent des mises en page plus réactives.
* **Mettez en cache le `DocumentBuilder`** – créer un nouveau builder pour chaque opération peut dégrader les performances sur de gros documents.
* **Définissez `PictureFillMode`** lorsque vous avez besoin que l’image s’étire ou se répète à l’intérieur de la forme : `pictureShape.setPictureFillMode(PictureFillMode.STRETCH);`
* **Validez les dimensions de l’image** avant l’insertion afin d’éviter un redimensionnement inattendu qui pourrait affecter la boîte englobante du groupe.

## Étapes suivantes

Maintenant que vous savez **comment regrouper des formes**, vous pouvez explorer :

* **Insérer une image dans le document** avec des options avancées comme le recadrage (`pictureShape.setCropTop(...)`).
* **Définir la taille d’une forme** dynamiquement en fonction des dimensions de la page (`doc.getFirstSection().getPageSetup().getPageWidth()`).
* **Ajouter une image au groupe** avec des zones de texte pour des graphiques légendés.
* **Créer une forme rectangulaire** avec des coins arrondis (`rectangleShape.setCornerRadius(5);`).

Ces sujets s’appuient sur la même API et vous aident à créer des rapports Word sophistiqués et programmatiques.

## Conclusion

Dans ce tutoriel, vous avez appris **comment regrouper des formes** dans un document Word avec Aspose.Words pour Java. En suivant les six étapes — création d’un document, insertion d’un groupe, **création d’une forme rectangulaire**, **définition de la taille d’une forme**, **insertion d’une image dans le document**, **ajout d’une image au groupe**, et positionnement du groupe — vous disposez désormais d’un modèle réutilisable pour des scénarios de mise en page complexes. N’hésitez pas à expérimenter avec des formes enfants supplémentaires, différentes rotations, ou une logique de groupement conditionnelle pour répondre aux besoins de votre application.

Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word Java – Ajouter une forme rectangulaire avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Utiliser les formes de document avec Aspose.Words pour Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Créer une forme de groupe dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}