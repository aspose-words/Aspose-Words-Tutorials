---
category: general
date: 2026-08-23
description: Créez un document Word vierge avec Aspose.Words pour Java, apprenez à
  regrouper les formes, à colorer une forme rectangulaire, et à enregistrer le document
  au format docx en quelques minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: fr
lastmod: 2026-08-23
og_description: Créez un document Word vierge avec Aspose.Words pour Java, puis découvrez
  comment regrouper des formes, colorer une forme rectangulaire et enregistrer le
  document au format docx de manière efficace.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Créer un document Word vierge et regrouper des formes en Java – guide étape
  par étape
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Créer un document Word vierge et regrouper les formes en Java
url: /fr/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge et regrouper des formes en Java

Si vous devez **créer un document Word vierge** de manière programmatique, Aspose.Words for Java le rend simple. Ce tutoriel vous montre exactement comment **créer un document Word vierge**, insérer un **groupe de formes dans Word**, appliquer une **forme rectangle colorée**, et enfin **enregistrer le document au format docx**. À la fin, vous disposerez d’un extrait de code réutilisable que vous pourrez intégrer à n’importe quel projet Java.

Vous apprendrez :

* La dépendance Maven/Gradle requise pour Aspose.Words.
* Comment instancier un document vierge et un `DocumentBuilder`.
* Les étapes exactes pour **regrouper des formes** à l’intérieur d’un `GroupShape`.
* Comment définir les couleurs de remplissage des formes rectangle.
* Les meilleures pratiques pour **enregistrer le document au format docx** et où trouver le fichier de sortie.

Aucune expérience préalable avec Aspose.Words n’est supposée, mais vous devez être à l’aise avec le développement Java de base et disposer d’un JDK 8 ou plus récent installé.

---

## Prerequisites

| Exigence | Version / Détail |
|-------------|-------------------|
| Java Development Kit | 8 or higher |
| Build tool | Maven 3+ or Gradle 6+ |
| Aspose.Words for Java | 23.12 or later (the latest version at the time of writing) |
| IDE (optional) | IntelliJ IDEA, Eclipse, VS Code, or any Java‑compatible editor |

---

## Étape 1 : Ajouter Aspose.Words à votre projet

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Astuce :** Si vous utilisez un proxy d’entreprise, configurez Maven/Gradle pour récupérer le paquet depuis le dépôt Aspose comme décrit dans la documentation officielle.

---

## Étape 2 : **Créer un document Word vierge** avec un constructeur

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Le constructeur `Document` crée un conteneur `.docx` vide en mémoire. Le `DocumentBuilder` vous fournit une API fluide pour ajouter du contenu, y compris des formes.

---

## Étape 3 : Insérer un conteneur **groupe de formes dans Word**

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

Un `GroupShape` fonctionne comme un mini‑canvas. Toutes les formes qui y sont ajoutées se déplacent ensemble, ce qui correspond exactement à **regrouper des formes** pour assurer la cohérence de la mise en page.

---

## Étape 4 : Ajouter la première **forme rectangle colorée** (rouge)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

La constante `ShapeType.RECTANGLE` crée un simple rectangle. En appelant `getFill().setForeColor(...)`, vous contrôlez la **forme rectangle colorée**. Vous pouvez remplacer `java.awt.Color.RED` par n’importe quelle constante `java.awt.Color` ou une valeur RGB personnalisée.

---

## Étape 5 : Ajouter la deuxième **forme rectangle colorée** (vert) et la positionner

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Définir `setLeft` (ou `setTop`) déplace la forme par rapport au coin supérieur gauche du conteneur **groupe de formes dans Word**. Cela montre comment **regrouper des formes** avec un positionnement précis.

---

## Étape 6 : **Enregistrer le document au format docx** et vérifier le résultat

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

La méthode `save` écrit automatiquement un fichier `.docx` car l’extension du fichier est `.docx`. Si vous avez besoin d’un autre format (par ex., PDF), transmettez l’énumération `SaveFormat` appropriée.

> **Conseil :** Assurez‑vous que le répertoire cible (`output/` dans cet exemple) existe ou créez‑le programmatique­ment avec `new File("output").mkdirs();`.

---

## Code source complet pour copier‑coller rapidement

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Résultat attendu :** L’ouverture de `GroupShapeDemo.docx` dans Microsoft Word montre une page unique contenant deux rectangles colorés (rouge à gauche, vert à droite) qui se déplacent ensemble lorsque vous sélectionnez le groupe.

---

## Questions fréquentes et gestion des cas limites

| Question | Réponse |
|----------|--------|
| *Puis-je ajouter plus de deux formes au même groupe ?* | Oui. Appelez `groupShape.appendChild(yourShape)` pour chaque forme supplémentaire. Le groupe redimensionnera automatiquement pour englober les extents les plus éloignés, ou vous pouvez ajuster manuellement sa largeur/hauteur. |
| *Et si j’ai besoin d’un type de forme différent (par ex., ellipse) ?* | Remplacez `ShapeType.RECTANGLE` par `ShapeType.ELLIPSE`. La même logique de couleur de remplissage s’applique. |
| *Dois‑je libérer l’objet `Document` ?* | Aspose.Words gère les ressources natives en interne. Lorsque la JVM se termine, les ressources sont libérées. Pour les applications de longue durée, appelez `doc.dispose();` si vous utilisez la version **Aspose.Words for Java (Native)**. |
| *Comment changer l’ordre Z afin qu’un rectangle apparaisse au-dessus ?* | Utilisez `groupShape.insertAfter(shape, referenceShape);` ou `groupShape.insertBefore(shape, referenceShape);` pour réorganiser les enfants au sein du groupe. |
| *Puis‑je regrouper des formes à travers différentes sections ?* | Non. Un `GroupShape` doit résider dans un seul paragraphe ou conteneur de forme. Pour regrouper à travers les sections, créez des groupes séparés dans chaque section. |

---

## Conclusion

Vous savez maintenant comment **créer un document Word vierge** avec Aspose.Words for Java, **regrouper des formes dans Word**, appliquer le style de **forme rectangle colorée**, et **enregistrer le document au format docx**. Ce modèle s’étend à des mises en page plus complexes — il suffit d’ajouter des formes supplémentaires, d’ajuster les décalages, et éventuellement de définir du texte, des images ou des hyperliens à l’intérieur du groupe.

**Étapes suivantes** que vous pourriez explorer :

* Utilisez **groupe de formes dans Word** pour créer des organigrammes ou des maquettes d’interface utilisateur.
* Expérimentez **enregistrer le document au format docx** combiné avec la conversion PDF (`doc.save("out.pdf")`).
* Appliquez des dégradés ou des motifs à la **forme rectangle colorée** pour un design visuel plus riche.
* Combinez des formes groupées avec des tableaux ou des graphiques pour des documents de reporting avancés.

N’hésitez pas à modifier les dimensions, les couleurs ou les types de forme pour correspondre à l’identité visuelle de votre projet. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word Java – Ajouter une forme rectangle avec effet d’ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Comment enregistrer un document au format pdf avec Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Utilisation des formes de document dans Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}