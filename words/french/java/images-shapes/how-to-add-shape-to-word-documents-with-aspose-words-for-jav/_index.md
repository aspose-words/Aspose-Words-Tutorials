---
category: general
date: 2026-11-22
description: Apprenez comment ajouter une forme à Word en utilisant Aspose.Words pour
  Java – insérez un rectangle et masquez‑le de manière programmatique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: fr
lastmod: 2026-11-22
og_description: Ajoutez une forme à Word avec Aspose.Words pour Java. Ce tutoriel
  montre comment insérer un rectangle, masquer la forme et enregistrer le document.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Ajouter une forme à Word avec Aspose.Words – Guide Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Comment ajouter une forme aux documents Word avec Aspose.Words pour Java
url: /fr/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment ajouter une forme aux documents Word avec Aspose.Words for Java

Si vous devez **ajouter une forme à des documents Word** de manière programmatique, Aspose.Words for Java le rend simple. Dans ce guide, vous apprendrez **comment insérer une forme**, contrôler sa visibilité, et **comment masquer une forme** afin que le fichier final ressemble exactement à ce que vous attendez.

Vous parcourrez un exemple complet et exécutable qui charge un fichier `.docx` existant, insère un rectangle, le masque et enregistre le résultat. Aucun script externe ni aucune étape manuelle n’est requis, et le tutoriel couvre les variantes courantes telles que la création d’un nouveau document à partir de zéro ou le masquage d’une forme uniquement lors de l’impression.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java 17 (ou version ultérieure) installé – les versions antérieures fonctionnent mais la dernière LTS offre de meilleures performances.  
* Maven 3.8+ pour la gestion des dépendances.  
* Une licence valide d’Aspose.Words for Java (l’évaluation gratuite suffit pour l’apprentissage).  
* Un IDE ou éditeur de texte de votre choix (par ex., IntelliJ IDEA, VS Code).

## Étape 1 : Ajouter Aspose.Words à votre projet Maven

Ajoutez la dépendance suivante à votre `pom.xml`. Cela récupère la dernière version stable (en novembre 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Astuce :** Utilisez une clause `<scope>provided</scope>` si vous prévoyez de distribuer le JAR avec votre propre logique de licence.

## Ajouter une forme à Word – initialisation du document

La première étape fonctionnelle consiste à obtenir un objet `Document`. Vous pouvez soit charger un fichier existant, soit en créer un nouveau.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Pourquoi c’est important* : la classe `Document` est le point d’entrée pour toutes les manipulations Word. Charger un fichier existant préserve les styles, en‑têtes et pieds‑de‑page, tandis qu’un nouveau document vous donne une page blanche.

## Comment insérer une forme dans un document Word

Ensuite, créez un `DocumentBuilder` pour modifier le contenu du document. Le builder vous fournit des méthodes pour insérer du texte, des tableaux et des **formes**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

L’appel `insertShape` renvoie un objet `Shape` que vous pouvez configurer davantage (couleur, bordure, texte, etc.). Les dimensions sont exprimées en points (1 pt = 1/72 in).

*Pourquoi utiliser un rectangle* : les rectangles sont le conteneur le plus courant pour les annotations, filigranes ou espaces réservés. Vous pouvez remplacer `ShapeType.RECTANGLE` par `ShapeType.ELLIPSE`, `ShapeType.LINE`, etc., selon vos besoins visuels.

## Comment masquer une forme dans Word

Parfois, vous avez besoin qu’une forme existe pour les calculs de mise en page mais qu’elle n’apparaisse pas dans le rendu final. Aspose.Words fournit la méthode `setHidden(true)` pour cela.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Le drapeau « hidden » fonctionne comme l’option de formatage **Hidden** dans Microsoft Word : la forme est omise du rendu visuel mais reste présente dans le modèle d’objet du document. Ceci est utile pour :

* Stocker des métadonnées ou des marqueurs que votre application lira plus tard.  
* Créer des espaces réservés qui sont supprimés juste avant la publication.  
* Contrôler la visibilité selon les formats de sortie (par ex., masquer en HTML mais conserver en PDF).

> **Remarque :** Les formes masquées sont toujours exportées vers PDF par défaut. Si vous devez également les exclure du PDF, définissez `rectangle.getWrapType( ) = WrapType.NONE` et ajustez la propriété `Hidden` en conséquence.

## Étape 4 : Enregistrer le document modifié

Enfin, persistez les modifications dans un nouveau fichier.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Lorsque vous ouvrez `output.docx` dans Microsoft Word, le rectangle ne sera pas visible, mais il restera présent dans l’arbre du document. Vous pouvez vérifier sa présence programmatique en rechargeant le fichier et en appelant `Shape.isHidden()`.

### Résultat attendu

* Le fichier `output.docx` s’ouvre sans aucune forme visible.  
* Si vous inspectez le document avec Aspose.Words (par ex., `doc.getChildNodes(NodeType.SHAPE, true).size()`), le nombre de formes sera **1**, confirmant que la forme existe mais est masquée.

## Variantes avancées et cas limites

### 1. Créer une forme dans un document vierge

Si vous partez de zéro, remplacez la ligne de chargement par :

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Positionner la forme avec précision

Par défaut, `insertShape` place la forme à l’emplacement actuel du curseur. Pour la positionner de façon absolue :

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Contrôler la visibilité selon le format de sortie

Si vous avez besoin que la forme soit visible dans l’interface Word mais masquée lors de l’exportation en PDF, utilisez `Shape.setWrapType(WrapType.NONE)` conjointement avec `Hidden` :

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Ajouter du texte à l’intérieur de la forme

Un rectangle peut contenir un cadre de texte :

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Vous pouvez alors masquer la zone de texte avec le même appel `setHidden(true)`.

## Problèmes courants et comment les éviter

| Symptom | Cause | Fix |
|---------|-------|-----|
| La forme apparaît même après `setHidden(true)` | Le document a été enregistré avant que le drapeau hidden ne soit défini. | Assurez‑vous d’appeler `setHidden(true)` **avant** `doc.save()`. |
| La taille de la forme semble déformée | Confusion entre points et pixels sur des écrans haute‑DPI. | Utilisez des points (72 pt = 1 in) pour une taille cohérente sur toutes les plateformes. |
| La forme masquée s’imprime tout de même | Certaines imprimantes ignorent le drapeau hidden. | Définissez `Shape.setWrapType(WrapType.NONE)` et désactivez également `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Conclusion

Vous savez maintenant comment **ajouter une forme à des documents Word** en utilisant Aspose.Words for Java, **comment insérer une forme**, et **comment masquer une forme** afin qu’elle reste invisible pour les utilisateurs finaux tout en faisant partie de la structure du document. L’exemple complet ci‑dessus charge un fichier, insère un rectangle, le masque et enregistre le résultat, couvrant à la fois les cas d’usage typiques et plusieurs cas limites.

À partir de là, vous pouvez explorer des sujets connexes tels que **comment insérer une forme** avec des couleurs de remplissage personnalisées, **comment masquer une forme dans Word** pour une impression conditionnelle, ou l’automatisation du traitement en masse de documents avec Aspose.Words. Expérimentez avec différentes valeurs de `ShapeType`, options de positionnement et drapeaux de visibilité pour les adapter à votre flux de travail spécifique.

Bon codage, et profitez de la flexibilité que la manipulation programmatique de Word apporte à vos applications Java !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}