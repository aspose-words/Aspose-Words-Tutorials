---
category: general
date: 2026-11-22
description: Ajouter une forme rectangulaire dans un document Word avec Java, définir
  la taille de la forme, regrouper plusieurs formes et ajouter la forme au groupe
  efficacement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: fr
lastmod: 2026-11-22
og_description: Ajouter une forme rectangulaire dans un document Word avec Java, puis
  définir la taille de la forme, regrouper plusieurs formes et ajouter une forme au
  groupe dans un seul flux de travail.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Ajouter une forme rectangulaire et regrouper des formes en Java – guide
  complet
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Ajouter une forme rectangulaire et regrouper les formes en Java
url: /fr/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter une forme rectangulaire et regrouper des formes en Java

Si vous devez **ajouter une forme rectangulaire** à un document Word avec Java, ce guide vous accompagne pas à pas. Vous apprendrez également à **définir la taille de la forme**, **regrouper plusieurs formes**, et **ajouter une forme à un groupe** sans quitter l’IDE.

Travailler avec des graphiques vectoriels à l’intérieur d’un fichier DOCX ressemble souvent à jongler avec des API distinctes. À la fin de ce tutoriel, vous disposerez d’un programme autonome qui crée un rectangle, une ellipse, et toutes les formes supplémentaires dont vous pourriez avoir besoin, puis les regroupe afin qu’elles se déplacent comme un seul objet. Aucun outil externe n’est requis au‑delà d’Aspose.Words for Java.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java 17 ou version ultérieure installé.
* Maven 3.8+ (ou Gradle) pour gérer les dépendances.
* Une licence valide d’Aspose.Words for Java (l’évaluation fonctionne pour les tests).
* Un IDE tel qu’IntelliJ IDEA ou VS Code, bien que tout éditeur de texte convienne.

Ces exigences permettent au code de se compiler et de s’exécuter dans n’importe quel environnement de développement moderne.

## Étape 1 : Configurer le projet Maven

Créez un nouveau projet Maven ou ajoutez la dépendance Aspose.Words à un `pom.xml` existant :

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

La dépendance importe toutes les classes nécessaires à la manipulation de documents, y compris `Document`, `DocumentBuilder`, `Shape` et `GroupShape`. Maven téléchargera automatiquement les JARs lorsque vous exécuterez `mvn compile`.

## Étape 2 : Charger le document et créer un DocumentBuilder

Un `DocumentBuilder` fournit l’API fluide pour insérer du contenu. Chargez un DOCX existant ou démarrez à partir d’un document vierge :

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Créer le builder dès le départ vous donne un curseur positionné au début du document, prêt pour l’insertion de formes.

## Ajouter une forme rectangulaire à un document Word

### Étape 3 : Insérer la forme rectangulaire

Le rectangle est le premier élément visuel que nous voulons placer dans le document. En utilisant le constructeur `Shape` avec `ShapeType.RECTANGLE`, vous obtenez un objet entièrement modifiable.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Ajouter le rectangle à ce stade n’affecte pas la mise en page tant que sa taille n’est pas définie et qu’il n’est pas ajouté à un conteneur.

### Définir la taille et les dimensions de la forme

#### Étape 4 : Définir la largeur et la hauteur

Définir les dimensions de la forme détermine son apparence sur la page. Les valeurs de largeur et de hauteur sont mesurées en points (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Vous pouvez ajuster ces nombres pour correspondre à vos exigences de conception. Les mêmes méthodes s’appliquent à toute instance de `Shape`, vous pouvez donc les réutiliser pour des cercles, des flèches ou des dessins personnalisés.

#### Étape 5 : Insérer le rectangle dans le document

Maintenant que le rectangle possède une taille, placez‑le sur la page. La méthode `insertShape` de `DocumentBuilder` ajoute la forme à la position actuelle du curseur.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

À ce stade, le rectangle apparaît seul sur la page. Les étapes suivantes montrent comment le combiner avec d’autres formes.

## Regrouper plusieurs formes ensemble

Regrouper des formes vous permet de les déplacer, faire pivoter ou redimensionner comme une seule unité. Cela est particulièrement utile pour créer des diagrammes complexes.

### Étape 6 : Créer un conteneur de forme groupée

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

L’appel `insertGroupShape` ajoute un conteneur vide au document. Toutes les formes ajoutées à ce conteneur deviennent partie du groupe.

### Ajouter une forme au groupe

#### Étape 7 : Ajouter le rectangle au groupe

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

L’ajout déplace le rectangle du corps du document vers la collection interne du groupe. Le rectangle respecte désormais les transformations du groupe.

#### Étape 8 : Ajouter une ellipse à titre de démonstration

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

L’ellipse partage le même espace de coordonnées que le rectangle, vous pouvez donc les aligner visuellement en ajustant leurs propriétés `setLeft` et `setTop` si nécessaire.

### Étape 9 : Enregistrer le document

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

L’exécution du programme génère `output.docx`. Ouvrez le fichier dans Microsoft Word ou LibreOffice ; vous verrez un rectangle et une ellipse regroupés. Sélectionner l’une des formes met en surbrillance tout le groupe, confirmant que **ajouter une forme au groupe** a réussi.

![Add rectangle shape example in Java](image.png){alt="Exemple d’ajout d’une forme rectangulaire en Java"}

*La capture d’écran montre le rectangle et l’ellipse à l’intérieur d’un même groupe, prêts pour une manipulation conjointe.*

## Pourquoi cette approche est importante

* **Source unique de vérité** – Toutes les propriétés des formes sont définies avant la création du groupe, évitant les problèmes de mise en page.
* **Réutilisabilité** – Les mêmes méthodes `setWidth`/`setHeight` fonctionnent pour n’importe quelle forme, vous permettant d’étendre l’exemple aux flèches, étoiles ou SVG personnalisés.
* **Performance** – Le groupement réduit le nombre d’objets de dessin que le moteur de rendu Word doit gérer, ce qui améliore la vitesse d’ouverture des documents volumineux.
* **Maintenabilité** – En conservant la logique de création et de groupement des formes ensemble, les développeurs futurs peuvent modifier les dimensions ou ajouter de nouvelles formes sans fouiller dans du code non lié.

## Variantes courantes et cas limites

| Scénario | Ajustement |
|----------|------------|
| **Unités différentes** | Utilisez la conversion `PointsToPixels` ou définissez `Shape.setWrapType(WrapType.INLINE)` pour un placement en ligne. |
| **Faire pivoter le groupe** | Appelez `groupShape.setRotation(45);` pour faire pivoter toutes les formes enfants de 45°. |
| **Ajouter du texte à une forme** | Utilisez `Shape.setText("Label");` après avoir défini la taille. |
| **Dimensionnement dynamique** | Récupérez les dimensions de la page via `doc.getFirstSection().getPageSetup().getPageWidth()` et calculez les tailles de forme proportionnellement. |

Ces variantes illustrent comment le modèle de base — **ajouter une forme rectangulaire**, **définir la taille de la forme**, **regrouper plusieurs formes**, **ajouter une forme au groupe** — s’adapte à de nombreuses exigences réelles.

## Conclusion

Vous savez maintenant comment **ajouter une forme rectangulaire** à un document Word en Java, **définir la taille de la forme**, **regrouper plusieurs formes**, et **ajouter une forme au groupe** de manière propre et maintenable. L’exemple complet se compile en une seule classe exécutable, et le fichier DOCX résultant montre le résultat attendu.

À partir d’ici, vous pouvez explorer :

* Ajouter des libellés texte ou des hyperliens à chaque forme.
* Imbriquer des groupes pour créer des diagrammes hiérarchiques.
* Exporter le document en PDF tout en conservant les groupes de formes.

N’hésitez pas à expérimenter avec différentes dimensions, couleurs et types de formes supplémentaires. Maîtriser la manipulation des formes ouvre la porte à la génération automatisée de rapports, aux diagrammes dynamiques et à des expériences documentaires riches—le tout directement depuis le code Java.


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}