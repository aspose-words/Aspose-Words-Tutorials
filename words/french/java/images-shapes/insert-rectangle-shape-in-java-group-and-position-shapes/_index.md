---
category: general
date: 2026-07-26
description: Insérer une forme rectangulaire en Java avec Aspose.Words. Apprenez comment
  définir la taille de la forme, positionner la forme et regrouper les formes dans
  un fichier DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: fr
lastmod: 2026-07-26
og_description: Insérez une forme rectangulaire en Java pour créer des graphiques
  DOCX riches. Suivez ce guide étape par étape pour définir la taille de la forme,
  positionner la forme et regrouper les formes sans effort.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Insérer une forme rectangulaire en Java – Maîtriser le groupement et le
  positionnement
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Insérer une forme rectangulaire en Java – Regrouper et positionner les formes
url: /fr/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une forme rectangulaire en Java – Regrouper et positionner les formes

Vous avez déjà eu besoin d'**insérer une forme rectangulaire** dans un document Word en écrivant du code Java ? Vous n'êtes pas le seul — les développeurs qui créent des rapports, des factures ou des modèles personnalisés rencontrent ce problème tout le temps. La bonne nouvelle, c'est qu'avec quelques lignes d'Aspose.Words for Java, vous pouvez **insérer une forme rectangulaire**, **définir la taille de la forme**, **positionner la forme**, et même **comment regrouper les formes** afin qu'elles se déplacent comme une seule unité.

Dans ce guide, nous parcourrons l’ensemble du processus, de la création d’un document vierge à l’enregistrement d’un `.docx` contenant deux rectangles soigneusement regroupés. À la fin, vous saurez **comment ajouter une forme rectangulaire**, contrôler leurs dimensions, les placer exactement où vous le souhaitez, et les regrouper dans un groupe réutilisable. Aucune bibliothèque externe en dehors d’Aspose.Words n’est requise, et le code fonctionne avec Java 8 et plus.

## Prérequis

- Java 8 ou version ultérieure installé (j’utilise JDK 17, mais tout ce qui supporte Maven convient)
- Aspose.Words for Java 23.9 ou plus – ajoutez la dépendance à votre `pom.xml` ou téléchargez le JAR
- Une compréhension de base de la syntaxe Java (si vous pouvez écrire une méthode `main`, vous êtes prêt)
- Un IDE ou éditeur de texte de votre choix (IntelliJ IDEA, Eclipse, VS Code…)

> **Pro tip :** Si vous utilisez Maven, la dépendance ressemble à ceci :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Maintenant que les bases sont en place, plongeons dans le code.

## Insérer une forme rectangulaire et définir sa taille

La première chose à faire est de créer un nouveau `Document` et un `DocumentBuilder`. Le builder est votre « stylo » qui dessine les formes sur la page. Ci‑dessous, nous **insérons une forme rectangulaire** et définissons immédiatement **la taille de la forme** à 100 × 80 points.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Remarquez comment les appels `setWidth`/`setHeight` **définissent la taille de la forme** en points (1 pt ≈ 1/72 pouce). Vous pouvez également utiliser `setSize` si vous préférez une méthode unique, mais les appels explicites rendent l’intention parfaitement claire.

## Positionner la forme sur la page

Après avoir créé le premier rectangle, nous devons **positionner la forme** du second afin qu’il ne chevauche pas le premier. Le positionnement fonctionne de la même façon : vous définissez les propriétés `Left` et `Top` relatives à l’origine du groupe.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Si vous vous demandez pourquoi nous utilisons `setLeft` au lieu de `setX`, c’est parce qu’Aspose.Words adopte le système de coordonnées classique de Windows GDI — `Left` est le décalage horizontal, `Top` le décalage vertical. Modifier ces valeurs vous permet d’ajuster finement la mise en page sans manipuler de tableaux ou de paragraphes.

## Comment regrouper les formes

Vous pourriez vous demander : « Pourquoi se donner la peine de créer un groupe ? » Regrouper a du sens lorsque vous voulez que les formes se déplacent ensemble, tournent comme une unité, ou partagent un style commun. Dans l’extrait ci‑dessus, nous avons déjà créé un `GroupShape` via `builder.insertGroupShape`. Cet objet est essentiellement un conteneur — pensez‑y comme à un dossier qui contient d’autres fichiers de forme.

> **Pourquoi c’est important :** Si vous décidez plus tard d’ajouter une légende ou de faire pivoter tout le diagramme, vous n’avez besoin de modifier que le groupe, pas chaque rectangle individuellement.

## Comment ajouter un rectangle à un groupe

L’acte de **comment ajouter un rectangle** au groupe consiste simplement à appeler `group.appendChild(rectangle)`. En coulisses, Aspose.Words met à jour la collection interne du groupe et recalcule automatiquement la boîte englobante afin que le groupe conserve sa largeur et hauteur déclarées.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Vous pouvez expérimenter avec d’autres `ShapeType` — `ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, etc.—et le même modèle `appendChild` fonctionne.

## Enregistrer le document

Enfin, nous persistons le document sur le disque. Le chemin peut être absolu ou relatif ; assurez‑vous simplement que le dossier existe.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Lorsque vous ouvrez `GroupShape.docx` dans Microsoft Word, vous verrez deux rectangles côte à côte, tous deux enfermés dans une boîte gris clair. Sélectionner la boîte grise mettra en surbrillance les deux rectangles à la fois — preuve que **comment regrouper les formes** fonctionne réellement.

![Rectangles groupés dans un document Word](placeholder-image.png){: .center-image alt="Exemple d’insertion de forme rectangulaire montrant deux rectangles groupés dans un fichier DOCX généré par Java"}

*Texte alternatif de l’image (SEO) :* **exemple d’insertion de forme rectangulaire montrant deux rectangles groupés dans un fichier DOCX généré par Java**.

## Résultat attendu

- Un fichier `GroupShape.docx` situé dans le dossier `output`.
- Dans le document : un groupe de 400 × 200 pt contenant deux rectangles (100 × 80 pt et 120 × 60 pt) positionnés respectivement à (20, 30) et (150, 50).
- Le groupe possède une bordure noire fine et un remplissage gris clair, rendant le regroupement visuellement évident.

Ouvrez le fichier et essayez de faire glisser la boîte grise — les deux rectangles devraient se déplacer ensemble. S’ils ne bougent pas, revérifiez que vous avez bien appelé `group.appendChild` pour chaque forme.

## Problèmes courants & cas limites

| Problème | Pourquoi cela se produit | Solution |
|----------|--------------------------|----------|
| **Les rectangles apparaissent en dehors de la page** | Les valeurs `Left`/`Top` dépassent les dimensions du groupe | Augmentez la taille du groupe (`insertGroupShape(width, height)`) ou réduisez les décalages |
| **Le groupe disparaît après l’enregistrement** | Les propriétés `Width`/`Height` du groupe sont à 0 | Fournissez des dimensions non nulles lors de l’appel à `insertGroupShape` |
| **Les couleurs des formes sont incorrectes** | Le remplissage par défaut est transparent ; Word peut l’afficher en blanc | Définissez explicitement `setFillColor` ou utilisez `ShapeStyle` |
| **Exception `ArgumentOutOfRangeException`** | Utilisation de coordonnées négatives | Gardez `Left` et `Top` non négatifs |

Traiter ces points dès le départ vous évite les maux de tête du type « pourquoi ma forme disparaît ? » que rencontrent de nombreux débutants.

## Récapitulatif & prochaines étapes

Nous avons couvert le cycle complet d’**insertion d’une forme rectangulaire** en Java : création d’un document, **définition de la taille de la forme**, **positionnement de la forme**, **comment regrouper les formes**, et **comment ajouter un rectangle** à ce groupe. L’exemple complet, exécutable, se trouve dans le bloc de code ci‑dessus, et vous pouvez le coller directement dans un projet Maven pour voir le résultat.

Et après ? Essayez d’expérimenter avec :

- Ajouter du texte à l’intérieur de chaque rectangle via

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}