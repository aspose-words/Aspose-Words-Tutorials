---
category: general
date: 2026-07-16
description: Comment insérer un groupe de formes en Java avec Aspose.Words – ajouter
  une forme rectangle, définir les dimensions de la forme, et créer un rectangle et
  un cercle colorés.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: fr
lastmod: 2026-07-16
og_description: 'Comment insérer un groupe de formes en Java : guide pratique pour
  ajouter une forme rectangle, définir les dimensions de la forme et créer un rectangle
  et un cercle colorés avec Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Insérer une forme groupée en Java – Tutoriel complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Comment insérer un groupe de formes en Java – Guide complet
url: /fr/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# comment insérer une forme groupée en Java – Guide complet

Vous vous êtes déjà demandé **comment insérer une forme groupée** dans un document Word en utilisant Java ? Vous n'êtes pas le seul. Que vous construisiez un générateur de rapports ou un créateur de flyers dynamiques, regrouper les formes garde votre mise en page propre et votre code gérable.

Dans ce tutoriel, nous parcourrons les étapes exactes pour **ajouter une forme rectangle**, **définir les dimensions de la forme**, et **créer un rectangle coloré** ainsi que **créer un cercle coloré** en utilisant la bibliothèque Aspose.Words. À la fin, vous disposerez d’un programme exécutable qui génère un fichier .docx contenant un rectangle bleu et un cercle rouge soigneusement enveloppés dans un groupe.

## Prérequis

- Java 17 (ou tout JDK récent) installé et configuré.
- Maven ou Gradle pour gérer les dépendances.
- Aspose.Words for Java 23.9 ou plus récent – vous pouvez le récupérer depuis Maven Central.
- Une compréhension de base de la syntaxe Java – rien de compliqué requis.

Si l’un de ces éléments vous manque, téléchargez le JDK depuis le site d’Oracle et ajoutez la dépendance Aspose.Words à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Maintenant que les bases sont posées, mettons‑nous au travail.

## comment insérer une forme groupée – Vue d’ensemble

L’idée principale est simple : créer un `Document`, ouvrir un `DocumentBuilder`, insérer une **forme groupée**, puis placer des formes individuelles (un rectangle et un cercle) dans ce groupe. Le groupe agit comme un conteneur, ainsi le déplacer plus tard déplacera tout ce qu’il contient – idéal pour les mises en page complexes.

Voici le code complet, prêt à être exécuté. N’hésitez pas à le copier‑coller dans une nouvelle classe Java nommée `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Astuce :** Les valeurs `setLeft` et `setTop` sont relatives à l’origine du groupe, pas à la page. Cela rend le repositionnement de l’ensemble du groupe très simple plus tard.

### Que s’est‑il passé ?

1. **Document & Builder** – Nous créons un fichier Word vide et un `DocumentBuilder` qui nous permet d’insérer du contenu.
2. **Forme groupée** – `builder.insertGroupShape()` crée un conteneur. Pensez‑y comme à un dossier pour les objets de dessin.
3. **Rectangle bleu** – Nous instancions une `Shape` de type `RECTANGLE`, définissons sa taille, la positionnons et la remplissons en bleu – c’est l’étape **create colored rectangle**.
4. **Cercle rouge** – Même schéma, mais en utilisant `ELLIPSE` pour un cercle parfait, puis le remplissant en rouge – c’est la partie **create colored circle**.
5. **Enregistrement** – Enfin nous sauvegardons le tout dans `GroupShapeDemo.docx`.

Exécutez le programme (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) et ouvrez le fichier résultant. Vous devriez voir un rectangle bleu à gauche et un cercle rouge à droite, tous deux enfermés dans une même boîte groupée.

## Ajouter une forme rectangle

Si vous avez seulement besoin d’un rectangle sans regroupement, vous pouvez ignorer l’appel `insertGroupShape()` et ajouter le rectangle directement au corps du document. Cependant, le regroupement vous offre la flexibilité de déplacer, faire pivoter ou supprimer plusieurs formes en une seule opération.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Remarquez comment nous avons utilisé la logique **add rectangle shape** ici. Le rectangle apparaît sur la page comme un objet indépendant. Dans la plupart des scénarios réels, vous préférerez cependant le groupe, car il préserve le positionnement relatif.

## Définir les dimensions de la forme

Lorsque vous voyez des méthodes comme `setWidth` et `setHeight`, rappelez‑vous qu’elles acceptent des **points** (1/72 pouce). Si vous préférez les millimètres, convertissez d’abord :

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Cet extrait montre **set shape dimensions** avec une conversion d’unité – pratique lorsque vos spécifications de conception proviennent d’une maquette UI utilisant le système métrique.

## Créer un rectangle coloré

Colorer une forme est aussi simple que d’appeler `getFill().setForeColor()`. Vous pouvez passer n’importe quel `java.awt.Color`. Vous voulez un dégradé ? Utilisez `setForeColor` pour la couleur de départ et `setBackColor` pour la couleur finale.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

C’est une façon rapide de **create colored rectangle** avec un remplissage en dégradé au lieu d’une teinte unie.

## Créer un cercle coloré

Les cercles ne sont que des ellipses avec une largeur et une hauteur égales. La même logique de couleur s’applique :

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Si vous avez besoin d’un remplissage transparent, définissez le canal alpha :

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Vous avez maintenant maîtrisé la technique **create colored circle**.

## Enregistrer le document

Aspose.Words vous permet d’exporter vers de nombreux formats : DOCX, PDF, HTML, PNG, ce que vous voulez. Pour cette démo, nous restons sur le DOCX car il préserve parfaitement les formes vectorielles.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Changer le `SaveFormat` suffit pour générer une version PDF de la même œuvre groupée.

## Pièges courants et comment les éviter

- **Oublié d’ajouter la forme au groupe ?** La forme apparaîtra sur la page mais ne se déplacera pas avec le groupe. Appelez toujours `group.appendChild(yourShape)`.

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word Java – Ajouter une forme rectangle avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Créer une forme rectangle dans Word avec Aspose.Words – Guide étape par étape](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}