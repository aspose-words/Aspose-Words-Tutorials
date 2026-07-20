---
category: general
date: 2026-07-20
description: Créer un document Word vierge en Java avec Aspose.Words. Apprenez comment
  créer un groupe, insérer une forme rectangulaire et intégrer une image dans la forme.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create group
- add image word document
- insert rectangle shape
- embed image in shape
language: fr
lastmod: 2026-07-20
og_description: Créer un document Word vierge en Java avec Aspose.Words. Ce guide
  montre comment créer un groupe, insérer une forme rectangulaire et intégrer une
  image dans la forme pour des fichiers Word dynamiques.
og_image_alt: Screenshot of a blank Word document containing a grouped shape with
  a rectangle and an embedded image
og_title: Créer un document Word vierge avec forme groupée – Guide Java
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  headline: Create blank word document with grouped shape – Java guide
  type: TechArticle
- description: Create blank word document in Java using Aspose.Words. Learn how to
    create group, insert rectangle shape, and embed image in shape.
  name: Create blank word document with grouped shape – Java guide
  steps:
  - name: '`output.docx` appears in the project folder.'
    text: '`output.docx` appears in the project folder.'
  - name: Opening the file shows a single page with a grouped shape.
    text: Opening the file shows a single page with a grouped shape.
  - name: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
    text: Inside the group, the rectangle is positioned at the top‑left, and the image
      sits directly below it.
  - name: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
    text: Selecting the group in Word highlights both child objects, confirming they
      are truly grouped.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Créer un document Word vierge avec une forme groupée – Guide Java
url: /fr/java/images-shapes/create-blank-word-document-with-grouped-shape-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document Word vierge avec forme groupée – Guide Java

Vous vous êtes déjà demandé comment **créer un document Word vierge** qui contient déjà une forme groupée élégante ? Peut-être que vous créez un modèle de rapport, ou que vous avez besoin d'un espace réservé pour un logo et une légende. Dans tous les cas, le problème est courant : vous commencez avec un fichier vide, puis vous devez ajouter un groupe, déposer un rectangle à l'intérieur, et enfin intégrer une image — tout cela par programme.

Dans ce tutoriel, nous parcourrons un exemple Java complet, prêt à l'exécution, qui fait exactement cela. Vous apprendrez **comment créer un groupe**, **insérer une forme rectangle**, et **ajouter une image au document Word** à l'intérieur du même groupe. À la fin, vous disposerez d'un fichier Word qui ressemble à un modèle soigné, prêt pour une personnalisation supplémentaire.

> **Ce que vous obtiendrez :** une classe Java entièrement fonctionnelle, des explications étape par étape, des astuces pour gérer les chemins de fichiers, et un aperçu du résultat attendu. Aucune documentation externe requise — tout ce dont vous avez besoin se trouve ici.

---

## Créer un document Word vierge – Vue d'ensemble étape par étape

La première chose dont nous avons besoin est un véritable fichier Word vierge. Aspose.Words rend cela trivial : il suffit d'instancier la classe `Document` avec son constructeur par défaut. Cela vous fournit une toile vierge, équivalente à ouvrir Word et cliquer sur **Nouveau → Document vierge**.

```java
import com.aspose.words.*;

public class GroupShapeExample {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Pourquoi commencer avec un document vierge ?**  
> Un document vierge garantit qu'aucun style ou section caché n'interfère avec les formes que vous ajouterez plus tard. Il maintient également la taille du fichier au minimum, ce qui est pratique lorsque vous générez des dizaines de fichiers dans un traitement par lots.

---

## Comment créer un groupe et ajouter des formes

Une **forme groupée** est essentiellement un conteneur pouvant contenir plusieurs formes enfants — pensez-y comme un dossier pour les objets de dessin. En groupant, vous pouvez déplacer, redimensionner ou faire pivoter l'ensemble avec une seule commande.

```java
        // 2️⃣ Insert a group shape 200x200 points
        GroupShape group = builder.insertGroupShape(200.0, 200.0);
```

La méthode `insertGroupShape` renvoie un objet `GroupShape` que nous utiliserons comme parent pour le rectangle et l'image. La taille est exprimée en points (1 point = 1/72 pouce), donc 200 points vous donnent approximativement une boîte de 2,78 × 2,78 pouces.

> **Astuce pro :** Si vous avez besoin que le groupe soit transparent, définissez `group.setFillColor(Color.getWhite());` après sa création.

Maintenant que le groupe existe, nous devons indiquer au builder où placer les formes suivantes. Le curseur du builder doit être positionné à l'intérieur du premier paragraphe du groupe.

```java
        // Move the cursor to the first paragraph of the group
        builder.moveTo(group.getFirstParagraph());
```

---

## Insérer une forme rectangle à l'intérieur du groupe

Un rectangle est souvent utilisé comme espace réservé pour du texte ou comme indication visuelle. L'ajouter comme **premier enfant** du groupe garantit qu'il se trouve derrière les images suivantes.

```java
        // 3️⃣ Insert a rectangle (100x50 points) as the first child
        builder.insertShape(ShapeType.RECTANGLE, 100.0, 50.0);
```

Le rectangle hérite du système de coordonnées du groupe, ainsi sa taille de 100 × 50 points sera centrée par défaut. Vous pouvez le styliser davantage — ajouter une bordure, changer la couleur de remplissage, ou appliquer une ombre — en accédant à l'objet `Shape` retourné.

```java
        // Optional styling (commented out for brevity)
        // Shape rect = builder.getCurrentShape();
        // rect.setFillColor(Color.getLightGray());
        // rect.setStrokeColor(Color.getBlack());
```

---

## Ajouter une image au document Word – intégrer l'image dans la forme

Passons maintenant à la partie amusante : **intégrer une image dans la forme**. Nous insérerons une image JPEG comme deuxième enfant du même groupe. Comme le curseur est toujours à l'intérieur du groupe, l'image deviendra automatiquement un nœud enfant.

```java
        // 4️⃣ Insert an image (make sure the path is correct)
        builder.insertImage("sample.jpg");   // <-- replace with your image path
```

Si le fichier image n'est pas trouvé, Aspose.Words lève une `FileNotFoundException`. Pour éviter cela, placez `sample.jpg` dans le répertoire de travail du projet ou utilisez un chemin absolu.

> **Et si vous avez besoin d'un format d'image différent ?**  
> Aspose.Words prend en charge PNG, BMP, GIF, TIFF, et même SVG. Il suffit de changer l'extension du fichier et la bibliothèque gérera la conversion.

---

## Enregistrer le document et voir le résultat

Enfin, nous persistons le document en mémoire sur le disque. Le `.docx` résultant contiendra une seule page avec une forme groupée contenant à la fois le rectangle et l'image.

```java
        // 5️⃣ Save the document to verify the output
        doc.save("output.docx");
    }
}
```

Lorsque vous ouvrez `output.docx` dans Microsoft Word, vous devriez voir un groupe de 200 × 200 points dans le coin supérieur gauche. À l'intérieur du groupe, un rectangle gris clair se trouve en haut, et directement en dessous l'image que vous avez spécifiée apparaît, parfaitement alignée.

![Grouped shape example](grouped-shape.png){:alt="Capture d'écran d'un document Word vierge avec une forme groupée contenant un rectangle et une image intégrée"}

---

## Variations courantes et gestion des cas limites

| Scénario | Ce qu'il faut changer | Pourquoi c'est important |
|----------|-----------------------|--------------------------|
| **Taille de groupe différente** | Ajustez les paramètres de `insertGroupShape(width, height)` | Des groupes plus grands peuvent accueillir des mises en page plus complexes. |
| **Images multiples** | Appelez `builder.insertImage()` de façon répétée après vous être déplacé au paragraphe du groupe à chaque fois | Chaque appel ajoute un nouvel enfant ; vous pouvez également les positionner en utilisant `Shape.setLeft()` / `setTop()`. |
| **Chemins d'image dynamiques** | Utilisez `String.format("images/%s.jpg", imageName)` | Rend le code réutilisable pour le traitement par lots. |
| **Enregistrement en PDF** | Remplacez `doc.save("output.pdf")` | Aspose.Words peut convertir à la volée, vous permettant de générer des PDF directement. |
| **Rotation du groupe** | `group.setRotation(45);` | Utile pour des filigranes décoratifs ou des en-têtes stylisés. |

---

## Résultat attendu et vérification

Après avoir exécuté la classe :

1. `output.docx` apparaît dans le dossier du projet.  
2. L'ouverture du fichier montre une seule page avec une forme groupée.  
3. À l'intérieur du groupe, le rectangle est positionné en haut à gauche, et l'image se trouve directement en dessous.  
4. Sélectionner le groupe dans Word met en surbrillance les deux objets enfants, confirmant qu'ils sont réellement groupés.

Si l'une de ces étapes échoue, vérifiez à nouveau le chemin de l'image et assurez‑vous que le JAR Aspose.Words est présent dans votre classpath.

---

## Conclusion

Vous savez maintenant **comment créer un document Word vierge** et l'enrichir d'une forme groupée contenant un rectangle et une image intégrée. En maîtrisant **comment créer un groupe**, **insérer une forme rectangle**, et **ajouter une image au document Word**, vous pouvez créer des modèles Word sophistiqués entièrement en code — aucune retouche manuelle requise.

Prêt pour le prochain défi ? Essayez d'ajouter des zones de texte à l'intérieur du même groupe, ou expérimentez différents styles de forme pour correspondre à l'identité visuelle de votre entreprise. Vous pourriez même générer une bibliothèque complète de rapports où chaque document commence avec cette mise en page exacte.

Bonne programmation, et n'hésitez pas à partager vos propres variantes dans les commentaires ci‑dessous !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Créer un document Word Java – Ajouter une forme rectangle avec effet d'ombre](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words pour Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Comment créer des documents PDF avec Aspose.Words pour Java | API de traitement de documents](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}