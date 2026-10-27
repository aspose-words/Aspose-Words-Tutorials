---
category: general
date: 2026-10-26
description: Apprenez à créer un document Word de façon programmatique, ajouter une
  forme et masquer un objet dans Word en utilisant Aspose.Words for Java – guide étape
  par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: fr
lastmod: 2026-10-26
og_description: Créez un document Word programmatique, apprenez à ajouter une forme
  et à masquer un objet dans Word avec Aspose.Words pour Java. Exemple complet et
  exécutable.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Créer un document Word par programmation – ajouter et masquer des formes
  en Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Créer un document Word de façon programmatique et ajouter une forme en Java
url: /fr/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word de manière programmatique et ajouter une forme en Java

Si vous devez **créer un document Word de manière programmatique**, ce tutoriel vous montre exactement comment le faire, ajouter une forme, puis masquer l’objet dans Word. Que vous construisiez un générateur de rapports ou un système de contrats automatisé, vous obtiendrez une solution complète, prête à l’emploi, en quelques minutes seulement.

Vous apprendrez à :

* Initialiser un document Word avec Aspose.Words for Java.  
* Insérer une ellipse (ou toute autre forme) en utilisant la technique **how to add shape**.  
* Masquer cette forme afin qu’elle n’apparaisse jamais à l’ouverture du fichier, répondant ainsi à la question **how to hide shape**.  

Aucun outil externe n’est requis au-delà de la bibliothèque Aspose.Words, et le code fonctionne avec Java 17 et versions ultérieures.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java Development Kit (JDK) 17 ou plus récent installé.  
* Maven ou Gradle pour gérer les dépendances (l’exemple utilise Maven).  
* Une licence valide d’Aspose.Words for Java (l’évaluation gratuite suffit pour les tests).  

Si vous êtes nouveau avec Aspose.Words, consultez le guide officiel de démarrage, mais vous n’aurez pas besoin de le lire pour suivre ce tutoriel.

## Dépendance Maven

Ajoutez la dépendance suivante à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Astuce :** Gardez le numéro de version à jour ; les nouvelles versions contiennent des corrections de bugs pour la gestion des formes.

## Étape 1 : Créer un document Word de manière programmatique – initialisation du document

La première chose à faire lorsque vous **créez un document Word de manière programmatique** est d’instancier un objet `Document`. Cet objet représente l’ensemble du fichier .docx en mémoire.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Pourquoi cette étape est importante* : La classe `Document` est le point d’entrée pour toutes les opérations de traitement Word. Sans elle, vous ne pouvez pas ajouter de pages, de paragraphes ou de formes.

## Étape 2 : How to add shape – insertion d’une ellipse

Nous abordons maintenant la partie **how to add shape** du tutoriel. Aspose.Words prend en charge de nombreux types de formes (Ellipse, Rectangle, TextBox, etc.). Ci‑dessous, nous insérons une ellipse d’une largeur et d’une hauteur de 50 points.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

La méthode `insertShape` renvoie un objet `Shape` que vous pouvez personnaliser davantage — couleur, style de ligne, rotation, etc. Les coordonnées sont exprimées en points (1/72 pouce).

*Pourquoi vous pourriez vouloir ajouter une forme* : Les formes sont utiles pour les filigranes, les éléments décoratifs ou les espaces réservés que vous masquerez ou remplacerez plus tard.

## Étape 3 : How to hide shape – rendre l’objet invisible dans Word

Pour répondre à la question **how to hide shape**, il suffit de définir la propriété `Hidden` de la forme sur `true`. Cela indique à Word de traiter la forme comme un objet masqué, de sorte qu’elle ne soit jamais rendue dans la vue du document ni à l’impression.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Si vous devez **hide object in Word** pour un utilisateur ou une condition spécifique, vous pouvez basculer cette propriété à l’exécution selon votre logique métier.

> **Remarque :** Les formes masquées font toujours partie de la structure XML du document. Elles peuvent être révélées ultérieurement en appelant `setHidden(false)`.

## Étape 4 : Enregistrer le document

Après avoir ajouté et masqué la forme, écrivez le document sur le disque.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Lorsque vous ouvrez `HiddenShapeDemo.docx` dans Microsoft Word, vous verrez une page blanche parce que l’ellipse est masquée. Le document se comporte autrement comme n’importe quel fichier Word normal.

## Exemple complet fonctionnel

En assemblant tous les éléments, voici le programme complet et exécutable :

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Sortie attendue**

```
Document created successfully.
```

L’ouverture de `HiddenShapeDemo.docx` montre une page vide ; l’ellipse masquée ne se rend pas, confirmant que l’opération **hide object in Word** a réussi.

## Cas limites et variantes

| Situation | Ce qu’il faut changer | Pourquoi |
|-----------|-----------------------|----------|
| Masquer un rectangle au lieu d’une ellipse | Utiliser `ShapeType.RECTANGLE` dans `insertShape` | Placeholder visuel différent |
| Masquer plusieurs formes à la fois | Parcourir `doc.getChildNodes(NodeType.SHAPE, true)` et appeler `setHidden(true)` | Utile pour le traitement en masse |
| Afficher la forme uniquement en mode impression | Appeler `shape.setVisible(false)` et `shape.setPrint(true)` | Word distingue la visibilité à l’écran et à l’impression |
| Utiliser une unité de mesure différente | Appeler `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | S’aligne avec vos exigences de mise en page |

## Pièges courants

* **Oublier d’appeler `setHidden(true)`** – la forme apparaîtra normalement.  
* **Enregistrer le document avant de masquer la forme** – l’ordre compte ; masquer d’abord, puis enregistrer.  
* **Utiliser une version obsolète d’Aspose.Words** – les versions antérieures peuvent ne pas contenir l’API `setHidden`.  

Testez toujours le fichier généré dans la version cible de Microsoft Word afin de vérifier que l’état masqué se comporte comme prévu.

## Conclusion

Dans ce guide, vous avez appris à **créer un document Word de manière programmatique**, **add shape**, et **hide object in Word** en utilisant Aspose.Words for Java. L’exemple complet montre les étapes exactes, de l’initialisation du document à l’enregistrement d’un fichier où la forme n’apparaît jamais.  

À partir d’ici, vous pouvez :

* Expérimenter avec d’autres types de formes (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Combiner des formes masquées avec des signets pour créer des modèles dynamiques.  
* Explorer les propriétés `setVisible` et `setPrint` pour un contrôle plus granulaire de la visibilité des objets.

Bon codage, et profitez de l’automatisation de vos documents Word !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer un document Word vierge avec Aspose.Words for Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Comment masquer une forme dans un document Word en Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Créer un document Word Java – Ajouter une forme rectangle avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}