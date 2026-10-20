---
category: general
date: 2026-10-20
description: Comment regrouper des formes dans Aspose.Words for Java – apprenez à
  insérer une forme rectangulaire, à les regrouper et à enregistrer le document dans
  un guide unique.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: fr
lastmod: 2026-10-20
og_description: Comment regrouper des formes dans Aspose.Words for Java. Ce tutoriel
  montre comment insérer une forme rectangulaire, les regrouper et exporter le résultat.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Comment regrouper des formes dans Aspose.Words pour Java – guide étape par
  étape
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Comment regrouper des formes dans Aspose.Words pour Java
url: /fr/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment regrouper des formes dans Aspose.Words pour Java

Si vous devez **comment regrouper des formes** dans un document Word en utilisant Aspose.Words pour Java, ce guide vous montre le flux de travail complet. Vous apprendrez comment **insérer une forme rectangle**, ajouter un deuxième rectangle, regrouper les deux formes, puis enregistrer le fichier — le tout avec du code clair et exécutable.

Regrouper des formes est utile lorsque vous souhaitez déplacer, faire pivoter ou styliser plusieurs dessins comme une seule unité. Que vous créiez un modèle de rapport, un diagramme ou un flyer personnalisé, maîtriser le regroupement de formes vous fait gagner du temps et maintient la cohérence de votre mise en page.

Dans ce tutoriel vous allez :

* Créer un nouveau `Document` et un `DocumentBuilder`.
* **Comment insérer un rectangle** formes avec des dimensions précises.
* Regrouper les rectangles dans un `GroupShape`.
* Enregistrer le document et vérifier le résultat.

> **Prérequis** – Vous devez disposer d'Aspose.Words pour Java (v23.12 ou ultérieure) ajouté à votre projet. Les utilisateurs de Maven peuvent inclure la dépendance indiquée ci-dessous.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Ce dont vous aurez besoin

| Élément | Raison |
|------|--------|
| Java 17+ | Fonctionnalités modernes du langage et meilleures performances |
| Aspose.Words for Java | Fournit les API `DocumentBuilder`, `Shape` et `GroupShape` |
| Un IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Pour compiler et exécuter l'exemple |
| Permission d'écriture sur un dossier | Le document sera enregistré sur le disque |

---

## Comment insérer une forme rectangle

La première étape consiste à créer un `Document` et un `DocumentBuilder`. Le builder vous fournit des méthodes telles que `insertShape` pour placer des objets de dessin.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Pourquoi c'est important** – Utiliser `insertShape` est la méthode standard **pour insérer des objets rectangle** dans Aspose.Words. Il ajoute automatiquement la forme au paragraphe courant du document, vous n'avez donc pas à gérer le OpenXML de bas niveau.

---

## Ajustement des positions du rectangle (optionnel)

Si le deuxième rectangle nécessite une position personnalisée par rapport au premier, vous pouvez modifier ses propriétés `left` et `top`. Cette étape est optionnelle mais souvent requise pour une mise en page de diagramme précise.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Astuce :** Toutes les mesures sont en points (1 pt ≈ 1/72 in). Utilisez `convertPointsToPixels` si vous avez besoin de valeurs en pixels pour des calculs basés sur l'interface utilisateur.

---

## Comment regrouper des formes

Maintenant que les rectangles existent, vous pouvez les placer dans un `GroupShape`. Le regroupement fait que les deux rectangles se comportent comme un seul objet — déplacer, faire pivoter ou formater le groupe affectera les deux formes.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Pourquoi le regroupement fonctionne** – `GroupShape` hérite de `Shape`, vous pouvez donc traiter le groupe exactement comme tout autre objet de dessin. Lorsque vous appelez `appendChild`, les formes sont retirées de leur emplacement d'origine et deviennent des enfants du groupe.

---

## Enregistrement du document contenant les formes groupées

Enfin, écrivez le document sur le disque. Le fichier contiendra un seul `GroupShape` avec deux rectangles à l'intérieur.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Résultat attendu

Ouvrez `GroupShape.docx` dans Microsoft Word :

* Vous verrez deux rectangles (bleu et vert) positionnés côte à côte.
* Sélectionner l'un ou l'autre rectangle sélectionne tout le groupe — le faire glisser déplace les deux ensemble.
* Le groupe possède une fine bordure rouge, confirmant que les propriétés du `GroupShape` sont appliquées.

Si vous cliquez avec le bouton droit sur le groupe et choisissez **Group → Ungroup**, les rectangles redeviennent des formes indépendantes, démontrant que l'opération de regroupement est réversible.

---

## Variations courantes et cas limites

| Situation | Comment le gérer |
|-----------|------------------|
| **Plus de deux formes** | Insérer chaque forme, puis ajouter toutes au même `GroupShape`. |
| **Types de formes différents** (par ex., ellipse, image) | Utiliser `builder.insertShape(ShapeType.ELLIPSE, …)` ou `builder.insertImage(...)` avant d'ajouter. |
| **Mise à l'échelle du groupe** | Appeler `group.setWidth(newWidth)` ou `group.setHeight(newHeight)` ; les enfants sont mis à l'échelle proportionnellement. |
| **Rotation du groupe** | `group.setRotationAngle(45);` fait pivoter l'ensemble autour de son centre. |
| **Conservation des positions d'origine** | Stocker les propriétés `left`/`top` de chaque forme avant le regroupement et les restaurer après le dégrouper si nécessaire. |

---

## Exemple complet et exécutable

Voici la classe Java complète que vous pouvez copier‑coller dans votre IDE. Elle inclut tous les imports, la gestion des erreurs et des commentaires pour plus de clarté.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Exécutez le programme, ouvrez le `GroupShape.docx` généré, et vous verrez les rectangles groupés exactement comme décrit.

---

## Conclusion

Vous savez maintenant **comment regrouper des formes** dans Aspose.Words pour Java, depuis la création d'un document jusqu'à l'insertion de formes rectangle, l'ajustement de leurs positions, et enfin le regroupement avec `GroupShape`. Cette technique vous permet de traiter plusieurs dessins comme une seule entité, simplifiant les ajustements de mise en page et la cohérence visuelle.

**Prochaines étapes**

* Explorez **comment insérer des rectangles** avec différents motifs de remplissage ou bordures.
* Combinez **insérer une forme rectangle** avec des zones de texte pour créer des diagrammes annotés.
* Expérimentez la rotation ou la mise à l'échelle du groupe pour produire des graphiques plus complexes.

N'hésitez pas à adapter le code pour d'autres types de formes, des groupes plus grands ou des scénarios de génération dynamique de documents. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Insérer une forme rectangle en Java – Regrouper et positionner les formes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Comment insérer une forme groupée en Java – Guide complet](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Comment appliquer une ombre à une forme dans Aspose.Words – Guide complet](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}