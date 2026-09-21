---
category: general
date: 2026-09-21
description: Créer un document Word de manière programmatique avec Java. Apprenez
  à regrouper des formes dans Word, insérer une forme rectangulaire, définir la taille
  de la forme et ajouter des formes à un document Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to group shapes in word
- how to insert rectangle shape
- add shapes to word document
- set shape size word
language: fr
lastmod: 2026-09-21
og_description: 'Créer un document Word programmatique avec Java : ce guide montre
  comment regrouper des formes dans Word, insérer des formes rectangulaires, définir
  la taille des formes et ajouter des formes à un document Word.'
og_image_alt: Screenshot of a Java program creating a Word document with grouped shapes
og_title: Créer un document Word par programmation, regrouper les formes en Java
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically using Java. Learn how to group
    shapes in Word, insert a rectangle shape, set shape size, and add shapes to a
    Word document.
  headline: Create word document programmatically, group shapes in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Word automation
- Shapes
title: Créer un document Word de façon programmatique, regrouper les formes en Java
url: /fr/java/images-shapes/create-word-document-programmatically-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word programmatique, regrouper des formes en Java

Si vous devez **créer un document Word programmatique**, ce guide vous accompagne à travers une solution complète. Vous verrez comment **regrouper des formes dans Word**, insérer un rectangle, définir sa taille, et ajouter d'autres formes — le tout en utilisant Java et la bibliothèque Aspose.Words for Java.

Le tutoriel couvre chaque étape, de la configuration du projet à l'enregistrement du fichier .docx final. À la fin, vous serez capable de générer un document Word contenant un rectangle et une image enveloppés dans un même groupe, ce qui facilite leur déplacement ou redimensionnement simultané. Aucune expérience préalable avec l'API Aspose.Words n'est requise, mais vous devez disposer d'un environnement de développement Java de base.

## Pré-requis

* Java Development Kit (JDK) 8 ou plus récent  
* Maven ou Gradle pour la gestion des dépendances  
* Aspose.Words for Java 23.9 (ou la dernière version) – la bibliothèque est gratuite pour l'évaluation  
* Un fichier image (par ex., `sample.jpg`) placé dans un répertoire connu  

Avoir ces éléments prêts garantit que le code s'exécute sans configuration supplémentaire.

## Étape 1 : Configurer le projet et importer Aspose.Words

Créez un projet Maven (ou ajoutez la dépendance à votre `pom.xml` existant) :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Si vous préférez Gradle, ajoutez ce qui suit à `build.gradle` :

```gradle
implementation 'com.aspose:aspose-words:23.9'
```

Après résolution de la dépendance, importez les classes requises dans votre fichier source Java :

```java
import com.aspose.words.*;
import java.io.File;
```

## Étape 2 : Créer le document Word programmatique

La première opération dans tout scénario d'automatisation consiste à instancier un objet `Document` et un `DocumentBuilder`. Le builder simplifie l'insertion de texte, d'images et de formes.

```java
public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

À ce stade, le document n'existe que en mémoire. Vous pouvez maintenant commencer à ajouter des formes.

## Étape 3 : Insérer une forme rectangle – comment insérer une forme rectangle

Un rectangle est une `Shape` de base avec `ShapeType.RECTANGLE`. Vous contrôlez ses dimensions avec `setWidth`, `setHeight`, et le positionnez avec `setTop` et `setLeft`.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);
        rectangle.setTop(10.0);
        rectangle.setLeft(10.0);

        // Optional: give the rectangle a visible fill and line color
        rectangle.getFillColor().setColor(java.awt.Color.LIGHT_GRAY);
        rectangle.getStrokeColor().setColor(java.awt.Color.DARK_GRAY);
```

**Pourquoi c'est important :** Définir explicitement la taille et la position (`set shape size word`) garantit que le rectangle apparaît exactement où vous l'attendez, quel que soit le layout par défaut du document.

## Étape 4 : Insérer une image – ajouter des formes au document Word

Le `DocumentBuilder` peut insérer une image directement depuis un chemin de fichier. Après l'insertion, vous pouvez repositionner l'image comme n'importe quelle autre forme.

```java
        // Insert an image; replace the path with your own image location
        String imagePath = "YOUR_DIRECTORY/sample.jpg";
        if (!new File(imagePath).exists()) {
            throw new IllegalArgumentException("Image file not found: " + imagePath);
        }
        Shape picture = builder.insertImage(imagePath);
        picture.setTop(70.0);
        picture.setLeft(10.0);
```

Le rectangle et l'image sont maintenant des formes indépendantes dans le document.

## Étape 5 : Regrouper les formes – comment regrouper des formes dans Word

Regrouper des formes est utile lorsque vous souhaitez les déplacer ou les redimensionner comme une seule unité. Aspose.Words fournit un conteneur `GroupShape` à cet effet.

```java
        // Create a GroupShape that will contain the rectangle and the picture
        GroupShape group = builder.insertGroupShape();

        // Append the rectangle and picture to the group
        group.appendChild(rectangle);
        group.appendChild(picture);
```

Lorsque le groupe est enregistré, Word traite les deux enfants comme un seul objet logique. Vous pourrez ensuite sélectionner le groupe et le faire glisser, et le rectangle ainsi que l'image suivront.

## Étape 6 : Enregistrer le document

Enfin, écrivez le document sur le disque. Le chemin doit être accessible en écriture par le processus Java.

```java
        // Save the document with the grouped shapes
        String outputPath = "YOUR_DIRECTORY/GroupShapeExample.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

L'exécution de la méthode `main` produit un fichier nommé **GroupShapeExample.docx**. Ouvrez-le dans Microsoft Word pour voir un rectangle et une image verrouillés ensemble dans un groupe. Sélectionner le groupe vous permet de déplacer les deux objets simultanément, confirmant que le regroupement a réussi.

## Résultat attendu

* Un fichier Word (`GroupShapeExample.docx`) situé dans le répertoire que vous avez spécifié.  
* À l'intérieur du fichier, un rectangle (remplissage gris clair) apparaît dans le coin supérieur gauche, et l'image se trouve directement en dessous.  
* Les deux objets font partie d'un même groupe, donc déplacer l'un déplace l'autre.

## Variations courantes et cas limites

| Situation | Recommendation |
|-----------|----------------|
| **Différents formats d'image** | Aspose.Words prend en charge PNG, BMP, GIF et TIFF. Utilisez l'extension de fichier appropriée dans `insertImage`. |
| **Dimensions négatives** | L'API lève `ArgumentException`. Validez toujours la largeur et la hauteur avant d'appeler `setWidth` / `setHeight`. |
| **Documents volumineux** | Regrouper de nombreuses formes peut augmenter la taille du fichier. Envisagez de fusionner les formes en une seule image lorsque les performances sont critiques. |
| **Compatibilité des versions de Word** | GroupShape fonctionne avec Word 2007 (`.docx`) et versions ultérieures. Pour les anciens fichiers `.doc`, le groupe sera aplati. |
| **Positionnement dynamique** | Utilisez des calculs basés sur la taille de la page (`doc.getFirstSection().getPageSetup().getPageWidth()`) si vous avez besoin d'un placement adaptatif. |

**Astuce :** Après avoir créé le groupe, vous pouvez modifier

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer un document Word Java – Ajouter une forme rectangle avec effet d'ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Créer une forme rectangle dans Word avec Java – Guide complet](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Créer une forme groupe dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}