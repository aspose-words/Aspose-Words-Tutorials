---
category: general
date: 2026-11-25
description: Masquez une forme dans Word avec Aspose.Words et apprenez à créer un
  document Word avec Aspose tout en insérant une forme rectangulaire en quelques lignes
  de code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide shape in word
- create word document aspose
- insert rectangle shape word
- Aspose.Words shape handling
- hide Word objects programmatically
language: fr
lastmod: 2026-11-25
og_description: Masquer une forme dans Word avec Aspose.Words. Ce tutoriel vous montre
  comment créer un document Word avec Aspose, insérer une forme rectangulaire dans
  Word et la masquer par programmation.
og_image_alt: Screenshot of a hidden rectangle shape inside a Word document created
  with Aspose.Words
og_title: Masquer une forme dans Word avec Aspose.Words – guide rapide étape par étape
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  headline: How to hide shape in Word using Aspose.Words
  type: TechArticle
- description: Hide shape in Word with Aspise.Words and learn to create Word document
    aspose while you insert rectangle shape word in just a few lines of code.
  name: How to hide shape in Word using Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17+ (or .NET 6+ if you prefer C#—the API calls are analogous). *
      Aspose.Words for Java 24.x (the latest version at the time of writing). * An
      IDE such as IntelliJ IDEA, Eclipse, or VS Code.'
  - name: Create a Word document aspose
    text: First, instantiate a blank `Document` and a `DocumentBuilder`. The builder
      provides a fluent API for adding content, including shapes.
  - name: Insert rectangle shape word
    text: Now we add a rectangle shape. The `insertShape` method requires the shape
      type and its dimensions in points (1 point = 1/72 inch).
  - name: Hide the shape so it does not appear in the layout
    text: Aspose.Words mirrors the Microsoft Word *Hidden* attribute. Setting it to
      `true` tells Word to omit the shape from rendering, while keeping the object
      in the document structure.
  - name: Save and verify the result
    text: Finally, write the document to disk. Open the file in Microsoft Word to
      confirm that the rectangle is not visible. You can also inspect the underlying
      XML to see the hidden flag.
  - name: (Optional) Unhide the shape later
    text: If you need to make the shape visible again, load the document, locate the
      shape, and set `hidden` to `false`.
  - name: What the output files contain
    text: '* **HideShapeResult.docx** – the rectangle is hidden; the page looks empty.
      * **UnhiddenShape.docx** – the same rectangle is visible, showing a red box
      with a black outline.'
  - name: Next steps
    text: '* Explore **conditional content** by combining hidden shapes with mail‑merge
      fields. * Learn how to **hide text runs** (`Run.setHidden(true)`) for more granular
      control. * Check the Aspose.Words documentation on **document protection** to
      prevent users from accidentally unhiding shapes.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape manipulation
title: Comment masquer une forme dans Word avec Aspose.Words
url: /fr/java/images-shapes/how-to-hide-shape-in-word-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment masquer une forme dans Word avec Aspose.Words

Si vous devez **masquer une forme dans Word** lors de la génération de documents de façon programmatique, Aspose.Words le rend très simple. Dans ce guide, vous verrez exactement comment créer un document Word avec Aspose, insérer une forme rectangle dans Word, puis masquer cette forme afin qu’elle n’apparaisse pas dans la mise en page. Un exemple complet et exécutable est fourni afin que vous puissiez le copier‑coller dans votre IDE et voir immédiatement le résultat.

Vous terminerez ce tutoriel avec un fichier Word contenant un rectangle masqué — utile pour les espaces réservés, le contenu conditionnel ou les métadonnées qui doivent rester invisibles pour le lecteur. Aucun outil externe n’est requis au-delà de la bibliothèque Aspose.Words pour Java (ou .NET).

## Ce que vous allez apprendre

* Comment **créer un document Word avec Aspose** à partir de zéro.  
* Comment **insérer une forme rectangle dans Word** à l’aide du `DocumentBuilder`.  
* Comment définir la propriété `hidden` de la forme afin qu’elle ne soit pas rendue dans la mise en page finale.  
* Comment vérifier que la forme est masquée et comment la rendre visible à nouveau si nécessaire.  

### Prérequis

* Java 17+ (ou .NET 6+ si vous préférez C# — les appels d’API sont analogues).  
* Aspose.Words pour Java 24.x (la dernière version au moment de la rédaction).  
* Un IDE tel qu’IntelliJ IDEA, Eclipse ou VS Code.  

> **Astuce :** Utilisez la licence temporaire gratuite d’Aspose si vous n’avez pas encore de licence commerciale. La bibliothèque fonctionne sans licence pour l’évaluation, mais une licence supprime les filigranes d’évaluation.

## Masquer une forme dans Word avec Aspose.Words

Les étapes principales sont :

1. **Créer un nouveau `Document`.**  
2. **Insérer une forme rectangle** à l’aide de `DocumentBuilder`.  
3. **Marquer la forme comme masquée** afin qu’elle n’apparaisse pas à l’ouverture du fichier.  

Chaque étape est détaillée ci‑dessous avec le code et les explications.

### Étape 1 : Créer un document Word avec Aspose

Tout d’abord, instanciez un `Document` vierge et un `DocumentBuilder`. Le builder fournit une API fluide pour ajouter du contenu, y compris des formes.

```java
// Step 1: Create a new document and a DocumentBuilder to work with it
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // Load a free evaluation license (optional for production)
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // Create an empty Word document
        Document doc = new Document();

        // DocumentBuilder lets us add text, tables, shapes, etc.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Pourquoi c’est important :**  
Créer un `Document` vierge vous donne une toile propre. Le `DocumentBuilder` est la méthode recommandée pour modifier le document car il suit automatiquement le point d’insertion actuel et gère la gestion des sections/pages pour vous.

### Étape 2 : Insérer une forme rectangle dans Word

Nous ajoutons maintenant une forme rectangle. La méthode `insertShape` nécessite le type de forme et ses dimensions en points (1 point = 1/72 pouce).

```java
        // Step 2: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

        // Optional: give the shape a visible fill and outline so you can see it before hiding
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);
```

**Pourquoi c’est important :**  
`insertShape` crée un objet de dessin qui vit dans la partie *drawing* du document. En spécifiant la taille, vous contrôlez l’espace que la forme occuperait si elle était visible. Le style optionnel vous aide à vérifier la forme avant de la masquer.

### Étape 3 : Masquer la forme afin qu’elle n’apparaisse pas dans la mise en page

Aspose.Words reflète l’attribut *Hidden* de Microsoft Word. Le définir à `true` indique à Word d’omettre la forme du rendu, tout en conservant l’objet dans la structure du document.

```java
        // Step 3: Hide the shape so it does not appear in the layout
        rectangle.setHidden(true);
```

**Pourquoi c’est important :**  
Une forme masquée peut toujours être accédée programmatique (par ex., pour un traitement conditionnel) et peut être rendue visible plus tard en basculant la propriété. C’est idéal pour des scénarios tels que les **espaces réservés conditionnels** qui ne doivent apparaître que pour certains publics.

### Étape 4 : Enregistrer et vérifier le résultat

Enfin, écrivez le document sur le disque. Ouvrez le fichier dans Microsoft Word pour confirmer que le rectangle n’est pas visible. Vous pouvez également inspecter le XML sous‑jacent pour voir le drapeau masqué.

```java
        // Save the document
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

**Sortie attendue :**  
L’exécution du programme affiche :

```
Document saved to HideShapeResult.docx
```

Lorsque vous ouvrez *HideShapeResult.docx* dans Word, la page apparaît vide (ou contient tout autre contenu que vous avez ajouté avant la forme). Le rectangle est présent dans le XML du fichier (`<w:hidden>` attribute) mais n’est pas rendu.

### Étape 5 : (Facultatif) Rendre la forme visible plus tard

Si vous devez rendre la forme visible à nouveau, chargez le document, localisez la forme et définissez `hidden` à `false`.

```java
        // Load the document again
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
```

**Pourquoi c’est important :**  
Pouvoir basculer le drapeau masqué vous donne un contrôle total sur la génération dynamique de documents — par ex., vous pouvez créer un document maître avec tous les éléments optionnels masqués, puis les rendre visibles sélectivement selon les préférences de l’utilisateur.

## Exemple complet et exécutable (créer document Word avec Aspose, insérer une forme rectangle dans Word, masquer la forme)

Voici le programme complet que vous pouvez compiler et exécuter directement.

```java
// HideShapeExample.java
import com.aspose.words.*;

public class HideShapeExample {
    public static void main(String[] args) throws Exception {
        // ---- License (optional for evaluation) ----
        // License license = new License();
        // license.setLicense("Aspose.Words.lic");

        // ---- Step 1: Create a new document ----
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // ---- Step 2: Insert rectangle shape ----
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle.getFillColor().setRGB(255, 0, 0); // red fill for visual check
        rectangle.getStroke().setColor(java.awt.Color.BLACK);
        rectangle.getStroke().setWeight(1.0);

        // ---- Step 3: Hide the shape ----
        rectangle.setHidden(true);

        // ---- Step 4: Save the document ----
        String outPath = "HideShapeResult.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);

        // ---- Optional Step 5: Unhide and save a second file ----
        Document loadedDoc = new Document(outPath);
        Shape hiddenRect = (Shape) loadedDoc.getChild(NodeType.SHAPE, 0, true);
        hiddenRect.setHidden(false);
        loadedDoc.save("UnhiddenShape.docx");
        System.out.println("Unhidden document saved to UnhiddenShape.docx");
    }
}
```

**Exécution du code**

```bash
javac -cp "aspose-words-24.10.jar" HideShapeExample.java
java -cp ".:aspose-words-24.10.jar" HideShapeExample
```

Remplacez `aspose-words-24.10.jar` par la version réelle que vous avez téléchargée.

### Ce que contiennent les fichiers de sortie

* **HideShapeResult.docx** – le rectangle est masqué ; la page semble vide.  
* **UnhiddenShape.docx** – le même rectangle est visible, affichant une boîte rouge avec un contour noir.

## Questions fréquentes & gestion des cas particuliers

| Question | Réponse |
|----------|---------|
| *Le rectangle masqué affecte‑t‑il la pagination ?* | Non. Les objets masqués sont ignorés par le moteur de mise en page, ils ne poussent donc pas le texte vers une nouvelle page. |
| *Puis‑je masquer d’autres objets Word (par ex., images, tableaux) ?* | Oui. La plupart des sous‑classes de `Node` (y compris `Shape`, `Paragraph`, `Run`) exposent une méthode `setHidden(boolean)`. |
| *Et si le document contient déjà des formes ?* | Utilisez `doc.getChildNodes(NodeType.SHAPE, true)` pour parcourir et masquer uniquement les formes ciblées. |
| *Le masquage d’une forme augmente‑t‑il la taille du fichier ?* | Légèrement, car le XML de la forme reste présent. L’impact est négligeable pour des documents typiques. |
| *Le drapeau masqué survit‑il lors de l’enregistrement au format PDF ?* | Lors de la conversion en PDF, les formes masquées sont omises par défaut. Vous pouvez contrôler ce comportement avec `PdfSaveOptions` si nécessaire. |

## Bonnes pratiques lors de la manipulation d’objets masqués

* **Nommez vos formes** avec `setName("MyPlaceholder")`. Cela facilite leur localisation ultérieure.  
* **Regroupez les objets masqués liés** dans un `GroupShape` si vous devez basculer la visibilité de plusieurs éléments à la fois.  
* **Documentez le but** des éléments masqués dans des commentaires ou un fichier de spécifications séparé — les futurs mainteneurs apprécieront le contexte.  
* **Évitez l’abus des objets masqués** ; ils augmentent la complexité du document et peuvent perturber les utilisateurs qui inspectent le XML manuellement.  

## Conclusion

Vous savez maintenant comment **masquer une forme dans Word** avec Aspose.Words, comment **créer un document Word avec Aspose**, et comment **insérer une forme rectangle dans Word** avant de la masquer. L’exemple montre le cycle complet : création, insertion, masquage, enregistrement et, éventuellement, affichage. Appliquez ces techniques pour créer des rapports dynamiques, des modèles conditionnels ou tout flux de travail automatisé Word où des espaces réservés invisibles sont nécessaires.

### Prochaines étapes

* Explorez le **contenu conditionnel** en combinant les formes masquées avec des champs de publipostage.  
* Apprenez à **masquer des exécutions de texte** (`Run.setHidden(true)`) pour un contrôle plus granulaire.  
* Consultez la documentation Aspose.Words sur la **protection de document** afin d’empêcher les utilisateurs de rendre les formes visibles par inadvertance.

Bon codage, et que vos fichiers Word générés restent épurés tout en conservant les données masquées dont vous avez besoin !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word programmatique, ajouter et masquer une forme en Java avec Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [Comment masquer une forme dans un document Word en Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Créer un document .docx vierge et ajouter une forme rectangle masquée avec Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}