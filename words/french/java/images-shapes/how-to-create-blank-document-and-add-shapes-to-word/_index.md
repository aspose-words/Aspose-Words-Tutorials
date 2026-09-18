---
category: general
date: 2026-09-18
description: Créer un document vierge et insérer des formes dans Word avec Aspose.Words
  – apprenez comment ajouter une forme triangulaire et plus.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: fr
lastmod: 2026-09-18
og_description: Créez un document vierge dans Word avec Aspose.Words et apprenez à
  insérer une forme de triangle, à regrouper des formes et d'autres graphiques. Suivez
  ce guide complet.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Créer un document vierge et ajouter des formes à Word – guide étape par
  étape
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Comment créer un document vierge et ajouter des formes dans Word
url: /fr/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document vierge et ajouter des formes à Word

Si vous devez **créer un document vierge** puis l'enrichir avec des graphiques, ce guide vous montre exactement comment procéder. Nous allons parcourir la création d'un fichier Word à partir de zéro et **ajouter des formes à Word**, y compris **comment insérer une forme de triangle**, en utilisant Aspose.Words for Java.

Vous terminerez le tutoriel avec un fichier *.docx* prêt à l'emploi contenant une forme groupée contenant un triangle. Les étapes couvrent tout, de la configuration du projet à l'enregistrement du **create word document** final. Aucun outil externe n'est requis au-delà d'Aspose.Words.

## Prérequis

* Java 17 ou version ultérieure installé  
* Maven ou Gradle pour la gestion des dépendances  
* Une licence Aspose.Words for Java (l'évaluation gratuite fonctionne pour cette démonstration)  

Si vous préférez un autre système de construction, ajustez la syntaxe des dépendances en conséquence. Le code fonctionne sur n'importe quelle plateforme qui prend en charge Java.

## Créer un document vierge avec Aspose.Words

La première opération consiste à **créer un document vierge** en mémoire. Aspose.Words fournit une classe `Document` qui représente un fichier Word sans aucun contenu.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

Le constructeur `new Document()` crée une structure *.docx* vide, que vous pouvez ensuite remplir avec des paragraphes, des tableaux ou des graphiques. Comme le document est vierge, vous avez un contrôle total sur chaque élément que vous ajoutez.

## Ajouter des formes à Word – insertion d'une forme groupée

Une forme groupée vous permet de traiter plusieurs graphiques comme une seule unité. Cela est utile lorsque vous souhaitez déplacer ou redimensionner plusieurs formes ensemble.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` est l'API principale pour ajouter du contenu. L'appel `insertGroupShape` crée un conteneur de 300 × 300 points (environ 4 × 4 pouces). Après cet appel, le curseur est positionné *à l'intérieur* du groupe, prêt pour des formes supplémentaires.

### Pourquoi utiliser une forme groupée ?

Le groupement maintient les graphiques liés alignés et facilite l'application d'un formatage uniforme. Si vous décidez plus tard de déplacer le triangle, tout le groupe se déplace ensemble, préservant la mise en page.

## Comment insérer une forme de triangle à l'intérieur du groupe

Nous abordons maintenant **comment insérer un triangle**. Le triangle est l'une des valeurs intégrées de `ShapeType`.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

L'appel `moveTo` garantit que le point d'insertion du builder est le premier paragraphe du groupe. `insertShape` ajoute ensuite un triangle de 60 × 60 points. Comme le curseur est à l'intérieur du groupe, le triangle devient un enfant de la forme groupée.

**Conseils pour ajouter une forme de triangle** :
* La taille est mesurée en points ; 72 points correspondent à un pouce. Ajustez les dimensions selon votre mise en page.  
* Si vous avez besoin d'une orientation différente, utilisez `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` pour aligner la forme à l'intérieur du groupe.  
* Le triangle hérite du remplissage et du style de ligne du groupe, sauf si vous les remplacez avec `shape.getFillColor()` ou `shape.getStrokeColor()`.

## Enregistrer le document – create word document

Après avoir construit les graphiques, vous enregistrez le fichier. Cette étape finalise l'opération **create word document**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` écrit la représentation en mémoire sur le disque sous forme de document Word standard. Vous pouvez ouvrir `ExtendedGroup.docx` avec Microsoft Word, LibreOffice ou tout visualiseur supportant le format OOXML. Le fichier affichera une forme groupée contenant un triangle, exactement comme construit par le code.

## Exemple complet exécutable

En assemblant toutes les pièces, voici le programme complet que vous pouvez copier, compiler et exécuter :

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Résultat attendu

Lorsque vous ouvrez `ExtendedGroup.docx`, vous verrez une seule forme groupée occupant le centre de la page. À l'intérieur de ce groupe, un petit triangle apparaît à la position par défaut. Le triangle peut être sélectionné et déplacé comme partie du groupe, confirmant que **add shapes to word** a fonctionné comme prévu.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|--------|
| *Puis-je ajouter plus d'une forme à l'intérieur du groupe ?* | Oui. Après avoir inséré le triangle, gardez le curseur à l'intérieur du groupe et appelez à nouveau `builder.insertShape` avec un `ShapeType` différent. |
| *Et si je veux que le triangle soit rouge ?* | Récupérez le `Shape` retourné par `insertShape` et appelez `shape.getFillColor().setColor(Color.RED)`. |
| *Cela fonctionne-t-il avec les anciens fichiers .doc ?* | Aspose.Words enregistre dans le format que vous spécifiez. Utilisez `doc.save("file.doc", SaveFormat.DOC)` pour créer un document Word hérité. |
| *Comment changer la bordure du groupe ?* | Utilisez `group.getStrokeColor().setColor(Color.BLUE)` et `group.setLineWeight(2.0)` pour personnaliser le contour. |
| *Existe-t-il un moyen de faire pivoter le triangle ?* | Appelez `shape.getRotation()` pour définir un angle en degrés. |

## Astuces professionnelles

* **Réutilisez le builder** – créer un nouveau `DocumentBuilder` pour chaque forme ajoute une surcharge. Conservez un seul builder par document.  
* **Conversion d'unités** – si vous travaillez avec des millimètres, convertissez-les en points (`points = mm * 2.83465`).  
* **Performance** – pour les gros documents, appelez `doc.updatePageLayout()` une seule fois après avoir ajouté toutes les formes.

## Conclusion

Vous savez maintenant comment **créer un document vierge**, **ajouter des formes à Word**, et plus spécifiquement **comment insérer une forme de triangle** en utilisant Aspose.Words for Java. L'exemple complet montre le flux de travail complet, d'un fichier vide à un **create word document** enregistré contenant un triangle groupé.

À partir de là, vous pouvez explorer d'autres valeurs `ShapeType`, appliquer des styles personnalisés, ou combiner plusieurs groupes pour créer des diagrammes complexes. Expérimentez avec différentes tailles, couleurs et positions pour maîtriser l'automatisation de Word en Java.

--- 

*Prêt à automatiser votre prochain rapport ? Clonez l'exemple, ajustez les dimensions et intégrez le code dans votre propre application dès aujourd'hui.*

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Créer un document Word vierge avec une forme de rectangle ombré – Guide étape par étape](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Créer une forme de rectangle dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}