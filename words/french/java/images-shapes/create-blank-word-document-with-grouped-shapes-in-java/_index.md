---
category: general
date: 2026-08-07
description: Créer un document Word vierge avec des formes groupées en Java à l'aide
  d'Aspose.Words. Apprenez comment regrouper les formes, définir leur taille et les
  ajouter à Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: fr
lastmod: 2026-08-07
og_description: Créer un document Word vierge avec des formes groupées en Java. Suivez
  ce guide pour définir la taille des formes, ajouter des formes à Word et maîtriser
  le regroupement des formes.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Créer un document Word vierge avec des formes groupées – Tutoriel Java
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Créer un document Word vierge avec des formes groupées en Java
url: /fr/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge avec des formes groupées en Java

Si vous devez **create blank Word document** qui contient plusieurs formes disposées comme une seule unité, ce tutoriel vous montre exactement comment. Vous verrez un exemple complet et exécutable qui démontre **how to group shape** des objets, ajuste leurs dimensions, et **add shapes to Word** en utilisant Aspose.Words for Java.

Le guide parcourt chaque étape — de la configuration du projet à l’enregistrement du fichier .docx final — afin que vous puissiez copier le code directement dans votre propre application. Aucune référence externe n’est requise, et la solution fonctionne avec Aspose.Words 23.9 ou ultérieur.

## Prérequis

* Java 17 (ou tout JDK pris en charge)
* Maven ou Gradle pour la gestion des dépendances
* Une licence Aspose.Words for Java (ou une clé d’évaluation temporaire)
* Un fichier image d’exemple (par ex., `sample.jpg`) placé dans un répertoire connu

Si l’un de ces éléments manque, installez‑le d’abord ; le reste du tutoriel suppose que l’environnement est prêt.

## Étape 1 : Ajouter Aspose.Words à votre projet

Ajoutez la dépendance Aspose.Words à votre `pom.xml` (Maven) ou `build.gradle` (Gradle). Cette bibliothèque fournit les classes `Document`, `DocumentBuilder`, `GroupShape` et `Shape` utilisées plus tard.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Pourquoi c’est important :** Sans la bibliothèque, aucune des API de traitement Word n’est disponible, et vous ne pouvez pas **create blank Word document** programmétiquement.

## Étape 2 : Créer un document Word vierge

La première action concrète consiste à instancier un objet `Document`, qui représente un **blank Word document** en mémoire.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* crée un **blank Word document** avec les paramètres par défaut (page A4, marges par défaut). Le `DocumentBuilder` associé vous permet d’insérer du contenu à la position actuelle du curseur.

## Étape 3 : Insérer une forme groupée (how to group shape)

Une *group shape* agit comme un conteneur pour d’autres formes. Dans cette étape, vous apprenez **how to group shape** des objets afin qu’ils se déplacent ensemble.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

La méthode `insertGroupShape` place le conteneur à la position du curseur du builder. Le groupement est essentiel lorsque vous souhaitez traiter plusieurs dessins comme une seule entité — c’est le cœur de la fonctionnalité **group shapes word**.

## Étape 4 : Créer un rectangle et définir sa taille

Ajoutez maintenant un rectangle au groupe. Cela démontre **set shape size**, qui est nécessaire pour une mise en page précise.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Pourquoi définir les dimensions ?* Appeler explicitement `setWidth` et `setHeight` garantit que le rectangle apparaît exactement comme prévu, indépendamment des styles de forme par défaut du document.

## Étape 5 : Insérer une image et l’ajouter au groupe

L’ajout d’une image montre un autre cas d’utilisation courant pour **add shapes to word**. L’image devient partie du même groupe, se déplaçant avec le rectangle.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Si le fichier image est manquant, Aspose.Words lève une exception. Un conseil pratique consiste à vérifier le chemin au préalable :

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Étape 6 : Enregistrer le document contenant les formes groupées

Enfin, persistez le **blank Word document** (désormais rempli d’une forme groupée) sur le disque.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Lorsque vous ouvrez `GroupShapeDemo.docx` dans Microsoft Word, vous verrez un seul objet groupé contenant un rectangle et une image. Sélectionner n’importe quelle partie du groupe déplace l’ensemble du conteneur, confirmant que les formes ont été correctement **grouped**.

### Résultat attendu

* Un fichier nommé `GroupShapeDemo.docx` dans le répertoire spécifié.
* L’ouverture du fichier montre un conteneur de 300 × 200 points avec :
  * Un rectangle de 100 × 50 points positionné à (20, 20).
  * Une image positionnée à (150, 30) à l’intérieur du même conteneur.

## Cas limites et variantes

| Situation | Comment le gérer |
|-----------|-----------------|
| **Different page size** | Call `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` before inserting the group. |
| **Multiple groups** | Repeat steps 3‑5 with a new `GroupShape` instance; each group can be positioned independently. |
| **Rotating shapes** | Use `shape.setRotationAngle(45.0);` to rotate a rectangle or picture before appending it to the group. |
| **Non‑image shapes** | Create `Shape` objects of type `ShapeType.ELLIPSE`, `ShapeType.LINE`, etc., and append them just like the rectangle. |
| **Large images** | Scale the picture with `picture.setWidth(80.0); picture.setHeight(60.0);` to keep the group within its original bounds. |

Ces variantes vous permettent d’adapter le modèle de base à un large éventail de scénarios de génération de documents.

## Conseils pratiques tirés de l’expérience

* **Pro tip :** Définissez les propriétés `RelativeHorizontalPosition` et `RelativeVerticalPosition` du groupe sur `RelativeHorizontalPosition.PAGE` et `RelativeVerticalPosition.PAGE` si vous souhaitez que le groupe reste ancré à la page plutôt qu’au curseur.
* **Watch out for :** Ajouter une forme qui dépasse les dimensions du groupe ; la forme sera rognée dans Word. Ajustez la taille du groupe avec `group.setWidth()` et `group.setHeight()` en conséquence.
* **Performance note :** Si vous générez de nombreux documents dans une boucle, réutilisez une seule instance de `DocumentBuilder` et appelez `doc.clone()` pour réduire la surcharge de création d’objets.

## Conclusion

Vous savez maintenant comment **create blank Word document** contenant une collection groupée de formes en utilisant Aspose.Words for Java. Le tutoriel a couvert le flux de travail complet : configuration de la bibliothèque, création du document, insertion d’un groupe, **set shape size**, **add shapes to word**, et enregistrement du résultat. 

À partir de là, vous pouvez explorer des fonctionnalités plus avancées telles que le groupement de graphiques, l’application de styles à des formes individuelles, ou l’exportation du document en PDF. Chacun de ces sujets repose sur les mêmes principes démontrés dans ce guide.

---

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités d’API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word Java – Ajouter une forme rectangle avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insérer des formes dans des documents Word avec Aspose.Words pour .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}