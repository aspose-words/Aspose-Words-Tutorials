---
category: general
date: 2026-06-20
description: Enregistrez un document Word avec Aspose.Words en Java tout en ajoutant
  une forme rectangulaire et en appliquant une ombre. Apprenez comment insérer une
  forme étape par étape.
draft: false
keywords:
- save word document
- add rectangle shape
- apply shadow to shape
- how to add shadow
- how to insert shape
language: fr
og_description: Enregistrez un document Word avec Aspose.Words Java. Ce guide montre
  comment ajouter une forme rectangulaire, appliquer une ombre et l’insérer dans un
  paragraphe.
og_title: Enregistrer le document Word – Ajouter une forme rectangulaire et une ombre
  en Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  headline: Save Word Document – Add Rectangle Shape & Shadow in Java
  type: TechArticle
- description: Save Word document using Aspose.Words in Java while adding a rectangle
    shape and applying a shadow. Learn how to insert shape step‑by‑step.
  name: Save Word Document – Add Rectangle Shape & Shadow in Java
  steps:
  - name: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
    text: '**Compile** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`'
  - name: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
    text: '**Execute** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`'
  - name: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
    text: '**Open** `shadow.docx` in Microsoft Word or LibreOffice. You should see
      the rectangle with a soft black shadow anchored at the start of the first paragraph.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the target `Section` or `PageSetup` and insert the shape
      into a paragraph located on that page.
    question: Can I add the shape to a specific page?
  - answer: Absolutely. Aspose.Words abstracts the format, so the same code **saves
      a Word document** whether it’s `.doc` or `.docx`.
    question: Does this work with .doc files?
  - answer: 'Replace `ShapeType.RECTANGLE` with `ShapeType.ELLIPSE`. All shadow properties
      remain the same. --- ## Conclusion You now know how to **save a Word document**
      while **adding a rectangle shape**, **applying a shadow**, and **inserting the
      shape** into the first paragraph—all with a handful of clean Ja'
    question: What if I need a different shape, like an ellipse?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word Automation
title: Enregistrer le document Word – Ajouter une forme rectangulaire et une ombre
  en Java
url: /fr/java/images-shapes/save-word-document-add-rectangle-shape-shadow-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer un document Word – Ajouter une forme rectangle et une ombre en Java

Vous êtes-vous déjà demandé comment **enregistrer un document Word** après avoir personnalisé sa mise en page ? Vous n’êtes pas seul — la plupart des développeurs rencontrent ce problème lorsqu’ils doivent enrichir un fichier DOCX de façon programmatique. La bonne nouvelle, c’est qu’avec Aspose.Words for Java vous pouvez **enregistrer un document Word**, placer une forme rectangle exactement où vous le souhaitez, et même ajouter une ombre subtile à cette forme.

Dans ce tutoriel, nous parcourrons l’ensemble du processus : charger un fichier existant, **ajouter une forme rectangle**, configurer son **ombre**, insérer la forme dans le premier paragraphe, puis **enregistrer le document Word**. À la fin, vous disposerez d’un programme Java exécutable qui produit un fichier `shadow.docx` soigné—sans aucune manipulation manuelle.

> **Ce dont vous aurez besoin**  
> * Java 17 (ou tout JDK récent)  
> * Bibliothèque Aspose.Words for Java (Maven/Gradle ou le JAR)  
> * Un fichier DOCX d’entrée (`input.docx`) dans un dossier connu  

Si vous avez ces éléments de base, plongeons‑y.

---

## Enregistrer un document Word – Exemple complet en Java

Voici le code source complet, prêt à être exécuté. Copiez‑le dans votre IDE, ajustez les chemins, puis cliquez sur **Run**.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class ShadowShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the existing document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Create a rectangle shape (the core of add rectangle shape step)
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);
        rectangle.setHeight(50.0);

        // 3️⃣ Apply shadow to shape – how to add shadow in Aspose.Words
        rectangle.getShadow().setVisible(true);
        rectangle.getShadow().setColor(java.awt.Color.BLACK);
        rectangle.getShadow().setBlurRadius(5.0);
        rectangle.getShadow().setOffsetX(4.0);
        rectangle.getShadow().setOffsetY(4.0);
        rectangle.getShadow().setTransparency(0.3);

        // 4️⃣ Insert shape into the first paragraph – how to insert shape
        Paragraph firstPara = doc.getFirstSection().getBody().getParagraphs().get(0);
        firstPara.appendChild(rectangle);

        // 5️⃣ Save the modified document – the final save word document step
        doc.save("YOUR_DIRECTORY/shadow.docx");
        System.out.println("Document saved successfully as shadow.docx");
    }
}
```

**Résultat attendu :** Après l’exécution du programme, ouvrez `shadow.docx`. Vous verrez le contenu original plus un rectangle noir de 100 × 50 pt avec une ombre douce placé au tout début du premier paragraphe.

---

## Ajouter une forme rectangle à un document Word

Pourquoi utiliser une forme rectangle ? Pensez‑y comme à une ancre visuelle—parfaite pour les encadrés, les espaces réservés ou les graphiques simples. Dans Aspose.Words, la classe `Shape` représente tous les objets de dessin, et `ShapeType.RECTANGLE` vous fournit une boîte nette sans fioritures.

**Points clés lors de l’ajout d’une forme rectangle**

- **Les unités sont en points** (1 pt = 1/72 in). Ajustez `setWidth`/`setHeight` pour correspondre à votre mise en page.  
- La forme vit dans l’arbre de nœuds du document, vous pouvez donc l’insérer partout où un `Paragraph` ou un `Run` est autorisé.  
- Vous pouvez styliser le rectangle (remplissage, couleur de trait, etc.) avant d’appliquer une ombre.

> **Astuce :** Si vous avez besoin d’un remplissage transparent, appelez `rectangle.getFill().setTransparent(true);`.

---

## Appliquer une ombre à la forme

Les ombres donnent de la profondeur. L’objet `Shadow` attaché à une `Shape` expose des propriétés qui correspondent directement aux options de l’interface Word.

| Propriété | Ce que ça fait | Valeur typique |
|-----------|----------------|----------------|
| `setVisible(true)` | Active l’ombre | `true` |
| `setColor(Color.BLACK)` | Couleur de l’ombre | `Color.BLACK` |
| `setBlurRadius(5.0)` | Douceur des bords | `5.0` |
| `setOffsetX(4.0)` / `setOffsetY(4.0)` | Déplacement horizontal/vertical | `4.0` chacun |
| `setTransparency(0.3)` | Opacité (0 = opaque, 1 = invisible) | `0.3` |

Lorsque vous vous demandez **comment appliquer une ombre à une forme**, la réponse consiste simplement à ajuster ces six propriétés. Vous pouvez expérimenter — des décalages plus grands créent un effet « levé », tandis qu’un rayon de flou plus élevé donne une apparence plus diffusée.

> **Erreur fréquente :** Oublier `setVisible(true)` laisse la forme sans ombre même si les autres propriétés sont configurées.

---

## Comment insérer la forme dans un paragraphe

Insérer une forme n’est pas de la magie ; c’est simplement de la manipulation de nœuds. La méthode `appendChild` place la forme à la fin des nœuds enfants du paragraphe. Si vous avez besoin de la forme avant le texte, utilisez `insertBefore` à la place.

```java
Paragraph para = doc.getFirstSection().getBody().getParagraphs().get(0);
para.insertBefore(rectangle, para.getFirstChild());
```

Ce petit changement répond à la question **comment insérer une forme** exactement où vous le souhaitez — avant tout texte existant, après un titre, ou même à l’intérieur d’une cellule de tableau (il suffit de récupérer d’abord le nœud `Cell` approprié).

---

## Exécuter le code et vérifier le résultat

1. **Compiler** – `javac -cp "aspose-words-xx.jar" ShadowShapeDemo.java`  
2. **Exécuter** – `java -cp ".;aspose-words-xx.jar" ShadowShapeDemo`  
3. **Ouvrir** `shadow.docx` dans Microsoft Word ou LibreOffice. Vous devriez voir le rectangle avec une ombre noire douce ancré au début du premier paragraphe.

Si la forme n’apparaît pas, vérifiez :

- Le chemin du fichier d’entrée est correct.  
- Vous utilisez une version récente d’Aspose.Words (l’API a légèrement changé avant la version 20.12).  
- Le document possède bien au moins un paragraphe (sinon `getParagraphs().get(0)` lève une `IndexOutOfBoundsException`).

---

## Questions fréquentes (FAQ)

**Q : Puis‑je ajouter la forme à une page spécifique ?**  
R : Oui. Récupérez la `Section` ou le `PageSetup` cible et insérez la forme dans un paragraphe situé sur cette page.

**Q : Cette méthode fonctionne‑t‑elle avec les fichiers .doc ?**  
R : Absolument. Aspose.Words abstrait le format, donc le même code **enregistre un document Word** qu’il s’agisse de `.doc` ou de `.docx`.

**Q : Et si je veux une forme différente, comme une ellipse ?**  
R : Remplacez `ShapeType.RECTANGLE` par `ShapeType.ELLIPSE`. Toutes les propriétés d’ombre restent identiques.

---

## Conclusion

Vous savez maintenant comment **enregistrer un document Word** tout en **ajoutant une forme rectangle**, **appliquant une ombre**, et **insérant la forme** dans le premier paragraphe—le tout avec quelques lignes Java propres. Ce modèle est extensible : changez le type de forme, ajustez les paramètres d’ombre, ou placez la forme dans des tableaux et des en‑têtes. Les possibilités sont aussi vastes que vos besoins d’automatisation de documents.

Prêt pour le prochain défi ? Essayez de superposer plusieurs formes, d’ajouter du texte à l’intérieur du rectangle, ou de générer un rapport complet avec graphiques et filigranes. Chacune de ces tâches repose sur les mêmes fondamentaux présentés ici—vous avez donc déjà une longueur d’avance.

Bon codage, et que votre automatisation Word soit exempte de bugs !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos projets.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [How to save word as pcl with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pcl-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}