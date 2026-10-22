---
category: general
date: 2026-09-27
description: Créer un document Word vierge en Java et regrouper des formes à l’aide
  d’Aspose.Words. Apprenez à définir la taille d’une forme, à définir la couleur de
  remplissage de la forme et à ajouter un enfant au groupe.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: fr
lastmod: 2026-09-27
og_description: Créer un document Word vierge en Java avec Aspose.Words. Ce tutoriel
  montre comment regrouper des formes dans Word, définir la taille d’une forme, définir
  la couleur de remplissage d’une forme et ajouter un enfant au groupe.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Créer un document Word vierge et regrouper des formes en Java – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Comment créer un document Word vierge et regrouper des formes en Java
url: /fr/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge et regrouper des formes en Java

Si vous devez **créer un document Word vierge** de façon programmatique, ce guide vous montre exactement comment le faire avec Aspose.Words for Java. Vous apprendrez également à **regrouper des formes dans Word**, à définir la taille de chaque forme, à appliquer une couleur de remplissage, et à **ajouter un enfant au groupe** afin que les objets se comportent comme une seule unité.

Travailler avec des fichiers Word depuis le code vous évite la mise en forme manuelle et vous permet de générer automatiquement des rapports, des contrats ou des brochures marketing. À la fin de ce tutoriel, vous disposerez d’un programme Java exécutable qui produit un fichier `.docx` contenant un rectangle bleu et une image, tous deux regroupés.

## Prérequis

- Java 17 (ou tout JDK récent) installé.
- Maven ou Gradle pour gérer les dépendances.
- Une licence Aspose.Words for Java (l’évaluation gratuite fonctionne pour les tests).
- Un fichier image d’exemple (par ex., `sample.jpg`) placé dans un dossier que vous pouvez référencer depuis le code.

> **Astuce :** Conservez vos fichiers image dans un répertoire `resources` et chargez‑les avec `ClassLoader.getResourceAsStream` pour éviter les chemins absolus codés en dur.

## Étape 1 : Créer un document Word vierge et ajouter un GroupShape

La première étape consiste à instancier un nouvel objet `Document`, qui représente un fichier Word vide, puis à insérer un `GroupShape`. Le groupe servira de conteneur pour toutes les formes que vous ajouterez ultérieurement.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Pourquoi c’est important :* Un `GroupShape` vous permet de déplacer, faire pivoter ou formater plusieurs formes ensemble, ce qui est essentiel pour des mises en page complexes comme des diagrammes ou des filigranes.

## Étape 2 : Insérer un rectangle et **définir la taille de la forme**

Ensuite, créez un rectangle, définissez ses dimensions et ajoutez‑le au groupe. Cela illustre l’opération **définir la taille de la forme**.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Explication :* `setWidth` et `setHeight` contrôlent la taille exacte de la forme en points (1 point = 1/72 pouce). Ajustez ces valeurs pour répondre aux exigences de votre mise en page.

## Étape 3 : **Définir la couleur de remplissage de la forme** pour le rectangle

L’arrière‑plan du rectangle est défini en bleu à l’aide de `setFillColor`. Vous pouvez utiliser n’importe quelle constante `java.awt.Color` ou créer une couleur RVB personnalisée.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Pourquoi c’est utile :* Les couleurs de remplissage aident à différencier visuellement les objets, surtout lorsque vous exportez ensuite le document en PDF ou l’imprimez.

## Étape 4 : Insérer une image et **ajouter un enfant au groupe**

Ajoutez maintenant une image au même `GroupShape`. L’image est insérée via `DocumentBuilder.insertImage`, puis ajoutée au groupe afin qu’elle se déplace avec le rectangle.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Cas particulier :* Si le chemin de l’image est incorrect, Aspose.Words lève une `FileNotFoundException`. Utilisez un chemin relatif ou chargez l’image depuis les ressources pour éviter ce problème.

## Étape 5 : **Enregistrer le document avec les formes groupées**

Enfin, écrivez le document sur le disque. Le fichier résultant contiendra le rectangle et l’image regroupés.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Résultat attendu

- Un fichier nommé `GroupShape.docx` apparaît dans le répertoire spécifié.
- L’ouverture du fichier dans Microsoft Word affiche une page vierge avec un rectangle bleu et l’image choisie, tous deux sélectionnés comme un seul objet (vous pouvez les déplacer ou les redimensionner ensemble).

![créer un document Word vierge avec des formes groupées](/images/grouped-shapes.png "créer un document Word vierge avec des formes groupées")

*La capture d’écran ci‑dessus montre les formes groupées finales à l’intérieur du nouveau document Word créé.*

## Variations courantes et conseils supplémentaires

| Situation | Comment le gérer |
|-----------|-------------------|
| **Images multiples** | Insérez chaque image avec `builder.insertImage` et appelez `group.appendChild(picture)` pour chacune. |
| **Différents types de formes** | Utilisez `ShapeType.OVAL`, `ShapeType.LINE`, etc., lors de la construction de l’objet `Shape`. |
| **Modifier la position du groupe** | Après avoir ajouté tous les enfants, définissez `group.setLeft(x)` et `group.setTop(y)` pour déplacer le groupe entier. |
| **Exporter en PDF** | Appelez `doc.save("output.pdf")` après le groupement ; le PDF conservera le groupement. |
| **Application de licence** | Si vous utilisez la version d’évaluation, un filigrane apparaîtra. Installez une licence valide pour le supprimer. |

## Conclusion

Vous savez maintenant comment **créer un document Word vierge**, insérer un **GroupShape**, **définir la taille de la forme**, **définir la couleur de remplissage de la forme**, et **ajouter un enfant au groupe** en utilisant Aspose.Words for Java. Ce modèle vous permet de créer des mises en page complexes et programmatiques qui peuvent être modifiées ultérieurement dans Word ou exportées vers d’autres formats.

Ensuite, explorez comment **regrouper des formes dans Word** avec des zones de texte, ajouter des hyperliens aux formes, ou automatiser la génération de rapports multi‑pages. Les mêmes principes s’appliquent — créez simplement des formes supplémentaires, configurez leurs propriétés, et ajoutez‑les au même groupe.

Bonne programmation !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer une forme rectangle dans Word avec Java – Guide complet](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Créer un document Word Java – Ajouter une forme rectangle avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Créer une forme groupée dans un document Word en utilisant Aspose.Words pour .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}