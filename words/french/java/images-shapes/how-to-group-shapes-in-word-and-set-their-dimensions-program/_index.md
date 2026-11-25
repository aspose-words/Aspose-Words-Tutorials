---
category: general
date: 2026-11-25
description: Comment regrouper des formes dans Word en utilisant Java et comment définir
  les dimensions des formes dans un fichier DOCX avec Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: fr
lastmod: 2026-11-25
og_description: Comment regrouper des formes dans Word avec l’API Aspose.Words Java
  et définir rapidement la taille des formes. Suivez la solution complète étape par
  étape.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Comment regrouper des formes dans Word et définir leurs dimensions – Guide
  Java
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Comment regrouper des formes dans Word et définir leurs dimensions par programmation
url: /fr/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans Word et définir leurs dimensions par programme

Si vous avez besoin de **comment regrouper des formes dans Word** et de contrôler leur taille exacte, ce guide vous montre une solution complète et exécutable. En utilisant Aspose.Words for Java, vous pouvez créer un rectangle, une ellipse, les ajouter à un `GroupShape`, puis **comment définir les dimensions d’une forme** telles que la largeur et la hauteur dans un seul fichier DOCX.

Vous apprendrez à :

* Créer un nouveau document Word à partir de zéro.  
* Insérer un `GroupShape` (nouvelle API dans la version 24.9).  
* Ajouter un rectangle et une ellipse au groupe.  
* **Définir la taille de la forme Word** précisément avec `setWidth` et `setHeight`.  
* Enregistrer le document sur le disque.

Aucun outil externe n’est requis — seulement Java 17+, Maven et la bibliothèque Aspose.Words for Java.

## Prérequis

* Java Development Kit 17 ou plus récent.  
* Maven (ou Gradle) pour la gestion des dépendances.  
* Aspose.Words for Java 24.9 ou ultérieur (l’API `GroupShape` a été introduite dans la version 24.9).  
* Familiarité de base avec la syntaxe Java et les concepts orientés objet.

Si vous n’avez pas encore ajouté Aspose.Words à votre projet, incluez la dépendance Maven suivante :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Étape 1 : Créer un nouveau document et un DocumentBuilder

La classe `Document` représente l’ensemble du fichier Word, tandis que `DocumentBuilder` fournit un moyen pratique d’ajouter du contenu.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Pourquoi cette étape ?*  
Créer un `Document` vierge vous donne une toile propre. `DocumentBuilder` est l’assistant de haut niveau qui vous permet d’insérer des paragraphes, des tableaux et, dans ce cas, des formes.

## Étape 2 : Insérer un GroupShape (nouvelle API dans la version 24.9)

Un `GroupShape` agit comme un conteneur ; toute forme que vous ajoutez devient partie du même groupe visuel.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Pourquoi utiliser `GroupShape` ?*  
Regrouper les formes simplifie le déplacement, la rotation ou l’application de formatage à plusieurs objets à la fois. L’API a été ajoutée dans la version 24.9, donc les versions antérieures ne compileront pas cette ligne.

## Étape 3 : Créer un rectangle, définir sa taille et l’ajouter au groupe

Ici nous démontrons **comment définir les dimensions d’une forme** pour un rectangle.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Pourquoi définir explicitement la largeur et la hauteur ?*  
Word stocke la taille des formes en points. En appelant `setWidth` et `setHeight` vous contrôlez l’empreinte visuelle exacte, ce qui est essentiel lorsque vous avez besoin d’une mise en page précise ou lors de l’exportation en PDF.

## Étape 4 : Créer une ellipse, définir sa taille et l’ajouter au même groupe

La même technique **définir la taille de la forme Word** fonctionne pour tout type de forme.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Pourquoi ajouter l’ellipse au même `GroupShape` ?*  
Les deux formes se déplaceront ensemble comme une unité. Cela est utile pour créer des icônes, des logos ou des diagrammes complexes qui doivent rester alignés.

## Étape 5 : Enregistrer le document avec les formes groupées

Enfin, persistez le fichier DOCX sur le disque.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

L’exécution de ce programme produit un fichier nommé **GroupShape.docx** contenant un rectangle et une ellipse groupés. Lorsque vous ouvrez le fichier dans Microsoft Word, vous verrez les deux formes se comporter comme un seul objet — vous pouvez les faire glisser, les redimensionner ou les faire pivoter ensemble.

### Résultat attendu

* Un document Word (`GroupShape.docx`) d’une page.  
* Un `GroupShape` contenant un rectangle de 100 × 50 pt et une ellipse de 80 × 80 pt.  
* Sélectionner l’une des formes sélectionne tout le groupe.

## Questions fréquentes et cas particuliers

### Comment modifier la position des formes groupées ?

Après avoir créé le `GroupShape`, vous pouvez définir ses propriétés `left` et `top` :

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Ces coordonnées sont également exprimées en points.

### Et si je dois ajouter plus de deux formes ?

`GroupShape` fonctionne comme n’importe quel autre nœud conteneur. Appelez `groupShape.appendChild(yourShape)` pour chaque forme supplémentaire. L’API ne limite pas le nombre d’enfants.

### Puis‑je appliquer un style (couleur de remplissage, épaisseur de ligne) à des formes individuelles ?

Oui. Chaque objet `Shape` expose des propriétés de formatage :

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Le code fonctionne‑t‑il avec les versions plus anciennes d’Aspose.Words ?

La méthode `insertGroupShape` a été introduite dans la version 24.9. Si vous utilisez une version antérieure, vous devrez créer un `GroupShape` manuellement via l’arbre de nœuds, ce qui est plus complexe. La mise à jour est la voie recommandée.

## Astuces professionnelles

* **Utilisez les points pour la cohérence** — l’unité interne de Word est le point (1/72 pouce). Convertir depuis des pixels ou des centimètres peut entraîner des tailles inattendues.  
* **Regroupez avant de positionner** — positionnez le `GroupShape` après avoir ajouté tous ses enfants ; sinon vous devrez recalculer les décalages.  
* **Réutilisez le DocumentBuilder** — vous pouvez insérer plusieurs groupes dans le même document en déplaçant le curseur du builder (`builder.moveTo`) avant chaque appel à `insertGroupShape`.

## Conclusion

Vous disposez maintenant d’un exemple complet, de bout en bout, de **comment regrouper des formes dans Word** et **comment définir les dimensions d’une forme** en utilisant Aspose.Words for Java. Le tutoriel a couvert la création d’un document, l’insertion d’un `GroupShape`, l’ajout d’un rectangle et d’une ellipse, la définition de leur taille exacte, puis l’enregistrement du résultat.  

À partir d’ici, vous pouvez explorer :

* Ajouter des zones de texte ou des images au même groupe.  
* Animer les formes groupées avec les fonctionnalités SmartArt de Word (via l’API).  
* Exporter les formes groupées en PDF ou SVG pour une utilisation web.

N’hésitez pas à expérimenter avec différents types de formes, tailles et positions — le regroupement vous offre un contrôle puissant sur des mises en page complexes dans les documents Word.


## Que devez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}