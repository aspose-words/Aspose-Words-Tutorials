---
category: general
date: 2026-10-13
description: Apprenez à créer des formes groupées dans Word avec Java. Ce guide vous
  montre comment insérer une forme groupée, ajouter une ligne au groupe et regrouper
  plusieurs formes dans tout le document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create grouped shapes
- add line to group
- group multiple shapes word
- insert group shape
language: fr
lastmod: 2026-10-13
og_description: Créez des formes groupées dans Word avec Java. Suivez ce tutoriel
  complet pour insérer une forme groupée, ajouter une ligne au groupe et regrouper
  plusieurs formes dans des documents Word.
og_image_alt: Screenshot of a Word document showing created grouped shapes
og_title: Créer des formes groupées dans Word avec Java – guide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to create grouped shapes in Word with Java. This guide shows
    you how to insert group shape, add line to group, and group multiple shapes word‑wide.
  headline: How to create grouped shapes in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Comment créer des formes groupées dans un document Word avec Java
url: /fr/java/images-shapes/how-to-create-grouped-shapes-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer des formes groupées dans un document Word avec Java

Si vous devez **créer des formes groupées** dans un fichier Microsoft Word depuis Java, ce tutoriel vous guide à travers l’ensemble du processus. Vous verrez comment **insérer une forme de groupe**, placer un rectangle et une ligne dans le même conteneur, puis enregistrer le document avec les graphiques groupés.

Regrouper des formes facilite le déplacement, le redimensionnement ou le style de plusieurs objets de dessin comme une seule unité — idéal pour les diagrammes, les organigrammes ou les décorations de page personnalisées. À la fin de ce guide, vous pourrez **ajouter une ligne au groupe**, **regrouper plusieurs formes word** dans des documents, et réutiliser la même technique pour n’importe quel nombre de formes.

## Prérequis

- Java 17 ou version ultérieure installé sur votre machine de développement.  
- Une licence Aspose.Words for Java (ou une évaluation gratuite).  
- Un projet Maven ou Gradle où vous pouvez ajouter la dépendance Aspose.Words :

```xml
<!-- Maven example -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

Aucune bibliothèque supplémentaire n’est requise.

## Étape 1 : Insérer le conteneur de forme de groupe

La première étape consiste à **insérer une forme de groupe** dans le document. Ce conteneur contiendra chaque forme suivante.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // The rest of the code will add shapes to this group
```

`builder.insertGroupShape()` crée un objet `Shape` vide de type `GROUPSHAPE`. Considérez-le comme une toile transparente pouvant contenir d’autres objets de dessin.

## Étape 2 : Ajouter un rectangle au groupe

Un rectangle sert souvent de fond visuel pour un groupe de formes.

```java
        // Create a rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);   // width in points
        rectangleShape.setHeight(50);   // height in points
        rectangleShape.setLeft(0);      // X‑coordinate inside the group
        rectangleShape.setTop(0);       // Y‑coordinate inside the group

        // Append the rectangle to the group container
        groupShape.appendChild(rectangleShape);
```

Définir `Left` et `Top` à `0` place le rectangle dans le coin supérieur‑gauche du groupe. Vous pouvez modifier ces valeurs pour décaler la forme à l’intérieur du groupe.

## Étape 3 : **Ajouter une ligne au groupe** – créer une forme de ligne

Nous **ajoutons maintenant une ligne au groupe**. La ligne apparaîtra sous le rectangle.

```java
        // Create a line shape
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);   // length of the line
        lineShape.setTop(60);      // vertical position (60 points down)

        // Append the line to the same group
        groupShape.appendChild(lineShape);
```

La propriété `Top` déplace la ligne de 60 points sous le rectangle, créant une disposition simple empilée. Vous pouvez également définir `Left` si vous avez besoin d’un décalage horizontal.

## Étape 4 : Enregistrer le document avec les formes groupées

```java
        // Save the document to a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Lorsque vous ouvrez `GroupShapeDemo.docx` dans Microsoft Word, vous verrez un seul groupe contenant à la fois le rectangle et la ligne. Sélectionner le groupe vous permet de déplacer les deux formes ensemble, ce qui montre que vous avez bien **regroupé plusieurs formes word**.

## Exemple complet, exécutable

Voici le programme complet avec tous les imports et la gestion des erreurs. Copiez‑le dans votre IDE, remplacez `YOUR_DIRECTORY` par un chemin de dossier existant, puis exécutez.

```java
import com.aspose.words.*;

public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape container
        Shape groupShape = builder.insertGroupShape();

        // Step 3: Add a rectangle to the group
        Shape rectangleShape = new Shape(doc, ShapeType.RECTANGLE);
        rectangleShape.setWidth(100);
        rectangleShape.setHeight(50);
        rectangleShape.setLeft(0);
        rectangleShape.setTop(0);
        groupShape.appendChild(rectangleShape);

        // Step 4: Add a line to the group
        Shape lineShape = new Shape(doc, ShapeType.LINE);
        lineShape.setWidth(100);
        lineShape.setTop(60);
        groupShape.appendChild(lineShape);

        // Step 5: Save the document
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

### Résultat attendu

- Un fichier nommé `GroupShapeDemo.docx` apparaît dans le dossier cible.  
- L’ouverture du fichier dans Word montre un seul objet groupé contenant un rectangle en haut et une ligne en dessous.  
- Faire glisser le groupe déplace les deux formes simultanément, confirmant que vous avez **créé des formes groupées** avec succès.

## Astuces et pièges courants

- **Astuce :** Si vous devez faire pivoter ou styliser des formes individuelles à l’intérieur du groupe, appelez les setters correspondants (`setRotation`, `getFill().setForeColor`, etc.) avant de les ajouter au groupe. Le groupe conservera ces propriétés visuelles.  
- **À surveiller :** Oublier de définir la propriété `Top` pour la ligne peut entraîner un chevauchement avec le rectangle, rendant le groupe encombré.  
- **Cas limite :** Lorsque vous ajoutez plus de deux formes, rappelez‑vous que les coordonnées de chaque enfant sont relatives à l’origine du groupe (0,0). Planifiez la disposition en conséquence.  
- **Note de performance :** Regrouper un grand nombre de formes (des centaines) peut augmenter légèrement la taille du fichier, mais cela simplifie l’édition ultérieure dans Word.

## Comment **regrouper plusieurs formes word** programmatique­ment

Le modèle présenté ci‑dessus — créer un conteneur de groupe, configurer chaque forme enfant, puis l’ajouter — fonctionne pour n’importe quel nombre de formes : cercles, images, zones de texte, etc. Répétez simplement les étapes « créer forme → définir propriétés → ajouter » avant d’appeler `doc.save()`.

Si vous devez **ajouter une ligne au groupe** après que le groupe contienne déjà d’autres formes, vous pouvez récupérer le groupe existant avec :

```java
Shape existingGroup = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                                 .stream()
                                 .filter(s -> ((Shape) s).getShapeType() == ShapeType.GROUPSHAPE)
                                 .findFirst()
                                 .orElseThrow(() -> new IllegalStateException("No group found"));
existingGroup.appendChild(lineShape);
```

Cela montre que vous pouvez modifier un groupe à tout moment du cycle de vie du document.

## Conclusion

Vous savez maintenant comment **créer des formes groupées** dans un document Word en utilisant Java et Aspose.Words. En **insérant une forme de groupe**, **ajoutant une ligne au groupe**, et **regroupant plusieurs formes word**, vous pouvez construire des dessins complexes qui se comportent comme un seul objet — idéal pour les diagrammes, les modèles et la génération automatisée de rapports.

Ensuite, explorez ces sujets connexes :

- **Appliquer des styles aux formes groupées** – apprenez à définir les couleurs de remplissage, les bordures et les effets pour tous les enfants en une fois.  
- **Exporter des formes groupées en PDF** – voyez comment le même groupe persiste lors de la conversion du document.  
- **Animer des formes avec VBA** – combinez les groupes générés en Java avec des macros Word pour des documents interactifs.

N’hésitez pas à expérimenter avec différents types de formes, tailles et positions. Le regroupement vous offre la flexibilité de traiter de nombreux objets comme un seul, simplifiant à la fois le code et l’interaction utilisateur. Bon codage !

## Que devez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}