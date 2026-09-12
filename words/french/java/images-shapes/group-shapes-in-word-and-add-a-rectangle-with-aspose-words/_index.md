---
category: general
date: 2026-09-11
description: Regroupez des formes dans Word et ajoutez une forme rectangle à l’aide
  d’Aspose.Words for Java. Apprenez à définir la taille des formes, à regrouper les
  objets et à enregistrer le document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: fr
lastmod: 2026-09-11
og_description: Regroupez des formes dans Word et ajoutez une forme rectangle à l'aide
  d'Aspose.Words pour Java. Ce tutoriel montre comment définir la taille d'une forme,
  regrouper des formes et exporter le document.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Regrouper les formes dans Word – ajouter un rectangle avec Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Regrouper les formes dans Word et ajouter un rectangle avec Aspose.Words
url: /fr/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Regrouper des formes dans Word et ajouter un rectangle avec Aspose.Words

Si vous devez **regrouper des formes dans Word** tout en ajoutant programmétiquement un rectangle, ce guide vous fournit une solution complète, prête à l’emploi. Vous verrez exactement comment insérer une forme groupée, ajouter une forme rectangle, définir la taille de la forme, puis enregistrer le document afin de visualiser immédiatement le résultat.

Travailler avec des documents Word implique souvent d’organiser plusieurs objets—images, graphiques ou formes géométriques simples—en une unité logique unique. Regrouper ces objets facilite leur déplacement, rotation ou mise en forme collective. Dans ce tutoriel, nous aborderons également **comment ajouter des formes rectangle** et **définir la taille des formes** pour un contrôle précis de la mise en page.

## Ce que vous allez apprendre

* Comment créer un nouveau document Word avec Aspose.Words for Java.  
* **Comment regrouper des formes** afin qu’elles se comportent comme un seul objet.  
* **Ajouter une forme rectangle** à un groupe et insérer une image dans le même groupe.  
* **Définir la taille des formes** pour le rectangle et l’image.  
* Enregistrer le document et l’ouvrir dans Microsoft Word pour vérifier le résultat.

### Prérequis

* Java 17 ou version ultérieure installé.  
* Maven ou Gradle pour gérer les dépendances.  
* Une licence valide d’Aspose.Words for Java (ou une clé d’évaluation gratuite).  
* Un fichier image (`sample.png`) placé dans un répertoire connu (remplacez `YOUR_DIRECTORY` par votre chemin réel).

---

## Comment regrouper des formes dans Word avec Aspose.Words

La première étape consiste à créer un `Document` et un `DocumentBuilder`. Le builder vous offre une API pratique pour insérer des formes, du texte et d’autres éléments.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Pourquoi c’est important :** `DocumentBuilder` travaille directement avec l’objet `Document` sous‑jacent, vous permettant d’insérer des formes sans manipuler manuellement les collections de nœuds de bas niveau.

### Ajouter une forme groupée

Une forme groupée est un conteneur qui peut contenir d’autres formes. Pensez‑y comme à un dossier pour les objets de dessin.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

La méthode `insertGroupShape()` crée un nœud `GroupShape` et le renvoie afin que vous puissiez y ajouter des formes enfants ultérieurement.  

---

## Ajouter une forme rectangle au groupe

Nous allons maintenant **ajouter une forme rectangle** au groupe créé précédemment. Le rectangle servira de fond ou de bordure pour l’image.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Astuce :** Définir `FillColor` et `StrokeColor` rend le rectangle visible dans le document final. Si vous omettez ces propriétés, la forme peut apparaître transparente.

### Comment ajouter un rectangle

Le code ci‑dessus montre **comment ajouter un rectangle** en créant une instance `Shape` avec `ShapeType.RECTANGLE`, puis en l’ajoutant au `GroupShape`. Ce modèle fonctionne pour tout autre type de forme (par ex., `ELLIPSE`, `POLYLINE`).

---

## Définir la taille des formes pour le rectangle et l’image

Un dimensionnement correct garantit que le rectangle et l’image s’alignent correctement. Ici, nous **définissons également la taille des formes** pour l’image que nous insérerons ensuite.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Le rectangle et l’image partagent désormais les mêmes dimensions (100 × 50 points). Parce qu’ils appartiennent au même groupe, déplacer ou faire pivoter le groupe affectera les deux formes simultanément.

> **Pourquoi harmoniser les tailles ?** Aligner les dimensions assure que l’image s’insère proprement à l’intérieur du rectangle, créant ainsi un effet « image encadrée » net.

---

## Enregistrer le document et visualiser le résultat

Enfin, nous écrivons le document sur le disque. L’ouverture du fichier dans Microsoft Word montre les formes groupées comme un seul objet sélectionnable.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Lorsque vous ouvrez `output.docx`, vous verrez un rectangle contenant l’image. Cliquer sur la forme sélectionne à la fois le rectangle et l’image parce qu’ils sont **groupés**.

![group shapes in word example](https://example.com/images/group-shapes-word.png "group shapes in word example")

*Texte alternatif de l’image :* *group shapes in word example* – un document Word affichant un rectangle et une image regroupés.

---

## Questions fréquentes et gestion des cas particuliers

| Question | Réponse |
|----------|--------|
| **Et si j’ai besoin d’une taille différente pour l’image ?** | Ajustez `picture.setWidth()` et `picture.setHeight()` après l’insertion. Le rectangle peut conserver sa taille d’origine, ou vous pouvez également le redimensionner pour qu’il corresponde. |
| **Puis‑je ajouter d’autres formes au même groupe ?** | Oui. Appelez `group.appendChild(newShape)` pour tout objet `Shape` supplémentaire. |
| **Comment faire pivoter tout le groupe ?** | Utilisez `group.setRotationAngle(double angleInRadians)`. La rotation s’applique à chaque forme enfant. |
| **Que se passe‑t‑il si le fichier image est absent ?** | `insertImage` lève une `FileNotFoundException`. Enveloppez l’appel dans un bloc try‑catch et fournissez une forme de remplacement. |
| **Est‑il possible de dégrouper plus tard ?** | Appelez `group.removeAllChildren()` pour détacher les enfants, puis réinsérez‑les individuellement dans le document. |

---

## Conclusion

Vous disposez maintenant d’un exemple complet et exécutable montrant **comment regrouper des formes dans Word**, **ajouter une forme rectangle**, **définir la taille des formes**, et **enregistrer** le document avec Aspose.Words for Java. En regroupant le rectangle et l’image, vous pouvez les déplacer, redimensionner ou faire pivoter comme une seule unité—exactement ce que requièrent de nombreux scénarios d’automatisation de documents.

À partir d’ici, vous pourriez explorer :

* Ajouter des zones de texte au même groupe (style `how to add rectangle`‑type texte).  
* Appliquer différents motifs de remplissage ou dégradés (`set shape size` combiné avec le style).  
* Utiliser la même technique pour regrouper des graphiques, tableaux ou SmartArt (`how to group shapes` sur d’autres types d’objets).  

N’hésitez pas à expérimenter avec d’autres types de formes, couleurs et options de mise en page. Bon codage !

## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Convert Word to PDF Using Aspose.Words for Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}