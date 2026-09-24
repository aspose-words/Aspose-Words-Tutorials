---
category: general
date: 2026-09-24
description: Apprenez à créer un document Word vierge en Java et à regrouper des formes
  telles que des rectangles et des lignes à l'aide d'Aspose.Words. Comprend du code
  étape par étape.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: fr
lastmod: 2026-09-24
og_description: Créez un document Word vierge en Java et apprenez à regrouper des
  formes, ajouter une forme rectangle et définir la taille de la forme avec Aspose.Words.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Créer un document Word vierge et regrouper des formes en Java – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Comment créer un document Word vierge et regrouper des formes en Java
url: /fr/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un document Word vierge et regrouper des formes en Java

Si vous devez **créer un document Word vierge** puis organiser plusieurs objets de dessin, ce guide vous montre exactement comment faire. En utilisant Aspose.Words for Java, vous pouvez insérer une forme de groupe, ajouter une forme rectangulaire, tracer une ligne et contrôler la taille et la position de chaque forme — le tout dans un programme unique et exécutable.

Vous parcourrez chaque étape, depuis l’initialisation du document jusqu’à l’enregistrement du fichier final `.docx`. À la fin, vous comprendrez **comment regrouper des formes**, **ajouter une forme rectangulaire** et **définir la taille d’une forme** afin que vos fichiers Word apparaissent exactement comme prévu.

## Prérequis

- Java 17 ou version ultérieure (le code se compile avec n’importe quel JDK récent)
- Bibliothèque Aspose.Words for Java (téléchargez‑la depuis le [site Aspose](https://products.aspose.com/words/java))
- Un IDE ou un outil de construction (Maven/Gradle) capable d’ajouter le JAR Aspose.Words au classpath
- Connaissances de base en syntaxe Java

> **Astuce :** Utilisez Maven pour la gestion des dépendances ; ajoutez `com.aspose:aspose-words:23.12` (ou la version la plus récente) à votre `pom.xml`.

## Étape 1 : Créer un document Word vierge

La première tâche consiste à **créer un document Word vierge**. Cela vous fournit une toile propre sur laquelle vous pourrez insérer des formes ultérieurement.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Pourquoi c’est important :* Un objet `Document` représente l’ensemble du fichier `.docx`. Commencer avec un document vierge garantit qu’aucun formatage caché n’interfère avec les formes que vous ajouterez.

## Étape 2 : Insérer une forme de groupe – le conteneur pour plusieurs objets

Une **forme de groupe** agit comme un conteneur qui vous permet de déplacer, redimensionner ou faire pivoter plusieurs formes ensemble. C’est le cœur de **la façon de regrouper des formes** dans Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Explication :* La méthode `insertGroupShape` crée un objet `GroupShape` et le place à l’emplacement actuel du curseur. Toutes les formes suivantes que vous `appendChild` à ce groupe seront traitées comme une seule unité.

## Étape 3 : Ajouter une forme rectangulaire et définir sa taille

Nous **ajoutons maintenant une forme rectangulaire** au groupe et **définissons précisément la taille de la forme**.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Pourquoi vous devez définir la taille de la forme :* La largeur et la hauteur contrôlent l’apparence du rectangle sur la page. Les méthodes `setLeft` et `setTop` positionnent le rectangle par rapport à l’origine du groupe, vous offrant un contrôle de mise en page pixel‑parfait.

## Étape 4 : Ajouter une forme de ligne et configurer ses dimensions

Une ligne est un autre objet de dessin courant. Nous appliquerons une logique similaire à celle de la **forme rectangulaire** à une ligne, montrant que les mêmes principes de dimensionnement s’appliquent.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Point clé :* Même si une ligne n’a pas de hauteur, vous utilisez toujours `setWidth` pour définir sa longueur. Le positionnement (`setLeft`, `setTop`) suit le même système de coordonnées que les autres formes.

## Étape 5 : Enregistrer le document avec les formes groupées

Enfin, persistez les modifications en enregistrant le document. Cela génère un fichier `.docx` que vous pouvez ouvrir dans Microsoft Word pour vérifier le résultat.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Résultat attendu :** L’ouverture de `GroupShapeDemo.docx` affiche une page vierge contenant un rectangle et une ligne groupés. Sélectionner l’une ou l’autre forme sélectionne le groupe entier, vous permettant de les déplacer ensemble.

## Questions fréquentes et gestion des cas limites

| Question | Réponse |
|----------|--------|
| *Puis‑je ajouter plus de deux formes au groupe ?* | Oui. Appelez `group.appendChild(votreForme)` pour chaque forme supplémentaire. |
| *Et si j’ai besoin d’une unité différente (par ex., centimètres) pour la taille ?* | Aspose.Words utilise les points (1 point = 1/72 pouce). Convertissez avec `Points = centimètres * 28.3465`. |
| *Le groupe conservera‑t‑il sa mise en page lorsqu’on ouvre le document sur une autre machine ?* | Absolument. Toutes les données de taille et de position sont stockées dans le fichier `.docx`, rendant la mise en page portable. |
| *Comment dégrouper les formes plus tard ?* | Récupérez l’objet `GroupShape`, puis parcourez `group.getChildNodes(NodeType.SHAPE, true)` et déplacez chaque enfant hors du groupe. |
| *Et si je dois faire pivoter tout le groupe ?* | Utilisez `group.setRotationAngle(double angleInDegrees)` avant l’enregistrement. |

## Exemple complet et exécutable

Voici le programme complet que vous pouvez copier‑coller dans votre IDE. Il comprend tous les imports nécessaires et des commentaires.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Exécutez le programme, ouvrez `GroupShapeDemo.docx` dans Microsoft Word, et vous verrez les formes groupées exactement comme décrit.

## Conclusion

Vous savez maintenant **créer un document Word vierge**, **regrouper des formes dans Word**, **ajouter une forme rectangulaire** et **définir la taille d’une forme** en utilisant Aspose.Words for Java. En plaçant les formes à l’intérieur d’un `GroupShape`, vous obtenez un contrôle total sur le positionnement, le redimensionnement et la rotation collectifs — idéal pour les diagrammes, organigrammes ou graphiques personnalisés intégrés à des rapports automatisés.

**Prochaines étapes :**  
- Explorez **la façon de regrouper des formes** avec des objets plus complexes comme des images ou des zones de texte.  
- Expérimentez `setRotationAngle` pour faire pivoter l’ensemble du groupe.  
- Combinez cette technique avec le publipostage pour générer des documents personnalisés incluant des graphiques de marque.

N’hésitez pas à adapter le code à vos propres projets et à partager vos résultats dans les commentaires !

## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code fonctionnels complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Create rectangle shape in Word with Java – Full Guide](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}