---
category: general
date: 2026-07-16
description: Définir la taille du bouton de manière programmatique dans un document
  Word à l'aide d'Aspose.Words pour Java. Apprenez comment insérer un bouton ActiveX,
  définir l'emplacement du bouton et plus encore.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size
- insert activex button
- programmatically add button
- set button location
- create word document button
language: fr
lastmod: 2026-07-16
og_description: Définir la taille du bouton dans un document Word avec Java. Ce guide
  étape par étape montre comment insérer un bouton ActiveX, définir la position du
  bouton et ajouter le bouton de façon programmatique.
og_image_alt: Screenshot of a Word document where the button size has been set using
  Aspose.Words for Java
og_title: Définir la taille du bouton dans Word avec Java – Tutoriel complet Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  headline: Set Button Size in Word with Java – Complete Aspose.Words Guide
  type: TechArticle
- description: Set button size programmatically in a Word document using Aspose.Words
    for Java. Learn how to insert ActiveX button, set button location and more.
  name: Set Button Size in Word with Java – Complete Aspose.Words Guide
  steps:
  - name: Expected Output Screenshot
    text: '![Word document showing the inserted button with the set button size](https://example.com/images/set-button-size.png
      "Screenshot of a Word file where the button size has been set using Aspose.Words
      for Java")'
  - name: “Can I set the button size using centimeters instead of points?”
    text: Word’s API only accepts points, but you can convert centimeters to points
      (`points = cm * 28.3465`). Write a small helper method if you prefer metric
      units.
  - name: “What if I need the button to appear on a specific page?”
    text: After inserting the button, you can move the cursor to a particular page
      using `builder.moveToPage(pageNumber)`. Insert the control right after the move,
      then set its location as shown above.
  - name: “Does this work with .doc (Word 97‑2003) files?”
    text: Yes—Aspose.Words automatically handles older formats. Just change the file
      extension in `doc.save("Demo.doc")`.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Définir la taille du bouton dans Word avec Java – Guide complet d'Aspose.Words
url: /fr/java/using-document-elements/set-button-size-in-word-with-java-complete-aspose-words-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir la taille du bouton dans Word avec Java – Guide complet Aspose.Words

Vous êtes‑vous déjà demandé comment **définir la taille du bouton** à l'intérieur d'un fichier Word sans ouvrir l'interface utilisateur ? Vous n'êtes pas le seul. Lorsque vous devez générer un document rempli de formulaires à la volée — par exemple, un paquet d'intégration avec un bouton « Submit », le faire de manière programmatique vous fait gagner des heures de travail manuel.

Dans ce tutoriel, nous passerons en revue les étapes exactes pour **insérer un bouton ActiveX**, ajuster ses dimensions, le positionner correctement, puis enfin enregistrer le fichier. À la fin, vous pourrez **ajouter programmatique un bouton** à n'importe quel document Word en utilisant Aspose.Words for Java.

## Prérequis – Ce qu'il vous faut avant de commencer

- **Java Development Kit (JDK) 8+** – le code s'exécute sur n'importe quel JDK récent.
- **Aspose.Words for Java** library (téléchargez le dernier JAR depuis le site officiel).  
- Un **IDE** de votre choix — IntelliJ IDEA, Eclipse, ou même un simple éditeur de texte fonctionne.
- Une connaissance de base de la syntaxe Java ; aucune connaissance approfondie de l'automatisation Word n'est requise.

> *Astuce :* Gardez le JAR Aspose.Words dans le classpath de votre projet, sinon vous rencontrerez `ClassNotFoundException` dès que vous tenterez d'importer `com.aspose.words.*`.

## Étape 1 : Créer un nouveau document Word

La première chose que nous faisons est de créer un document vierge et un `DocumentBuilder`. Pensez au builder comme un stylo qui nous permet de dessiner n'importe quoi à l'intérieur du fichier.

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty document.
        Document doc = new Document();

        // DocumentBuilder gives us a fluent API to add content.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Pourquoi c'est important :** L'objet `Document` représente le fichier .docx complet, tandis que le `DocumentBuilder` est le cheval de bataille qui nous permet d'insérer des paragraphes, des tableaux et — oui — des contrôles ActiveX.

## Étape 2 : Insérer un bouton ActiveX – Le moment « Insert ActiveX Button »

Nous insérons maintenant réellement **un bouton activex** dans le document. Aspose.Words expose une méthode pratique `insertForms2OleControl` qui renvoie un objet `Forms2OleControl`.

```java
        // Insert an ActiveX CommandButton control.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");   // Programmatic name.
        commandButton.setCaption("Submit");   // Text shown on the button.
```

> *Que se passe-t-il en coulisses ?* `Forms2OleControlType.COMMAND_BUTTON` indique à Word que nous voulons un CommandButton classique, le même type que vous déposeriez depuis l'onglet Développeur dans l'interface.

## Étape 3 : Définir la taille et la position du bouton – La logique centrale « Set Button Size »

C'est ici que le mot‑clé principal brille. Nous allons **définir la taille du bouton** et également **définir la position du bouton** afin que le contrôle apparaisse exactement où nous le souhaitons sur la page.

```java
        // Position the button (distance from the left/top edges in points).
        commandButton.setLeft(100);   // 100 points from the left margin.
        commandButton.setTop(150);    // 150 points from the top margin.

        // Set the button's dimensions.
        commandButton.setWidth(80);   // Width = 80 points.
        commandButton.setHeight(30);  // Height = 30 points.
```

> **Pourquoi cela vous concerne :** Les points sont l'unité de mesure native dans Word (1 point = 1/72 pouce). En ajustant `setLeft`, `setTop`, `setWidth` et `setHeight`, vous obtenez un contrôle pixel‑parfait — plus de « ça a l'air correct sur mon écran mais pas à l'imprimante ».
> *Erreur courante :* Oublier de définir la largeur ou la hauteur laissera le bouton à la taille par défaut, qui peut être trop petite pour cliquer. Spécifiez toujours les deux.

## Étape 4 : Enregistrer le document – « Create Word Document Button » terminé

Enfin, nous écrivons le fichier sur le disque. Le nom suggère que nous **créons un bouton de document Word** à l'intérieur d'un .docx.

```java
        // Persist the document to the file system.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Lorsque vous ouvrez `CommandButtonDemo.docx` dans Microsoft Word, vous verrez un bouton **Submit** placé à 100 pt du bord gauche et 150 pt du haut, avec une taille de 80 × 30 pt. Le cliquer dans l'interface déclenchera le comportement ActiveX par défaut (que vous pouvez ensuite connecter avec VBA si besoin).

### Capture d'écran du résultat attendu

![Document Word affichant le bouton inséré avec la taille du bouton définie](https://example.com/images/set-button-size.png "Capture d'écran d'un fichier Word où la taille du bouton a été définie à l'aide d'Aspose.Words for Java")

*Texte alternatif :* définir la taille du bouton dans un document Word avec Java

## Étape 5 (Facultatif) : Ajouter d'autres contrôles ou styliser le bouton

Si vous devez **ajouter programmatique un bouton** de contrôle au-delà d'un seul bouton Submit, répétez simplement le bloc d'insertion avec de nouveaux noms et légendes. Vous pouvez également ajuster la police, la couleur d'arrière‑plan, ou même lier des macros VBA plus tard.

```java
        // Example: Adding a Cancel button next to Submit.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);   // Position it 90 points to the right of Submit.
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);
```

> *Conseil :* Gardez toutes les dimensions des boutons cohérentes pour un rendu professionnel. Une façon rapide est de stocker la largeur/hauteur dans des constantes.

## Questions fréquentes & cas limites

### « Puis‑je définir la taille du bouton en centimètres au lieu de points ? »

L'API de Word n'accepte que les points, mais vous pouvez convertir les centimètres en points (`points = cm * 28.3465`). Écrivez une petite méthode d'aide si vous préférez les unités métriques.

### « Et si je veux que le bouton apparaisse sur une page spécifique ? »

Après avoir inséré le bouton, vous pouvez déplacer le curseur vers une page particulière en utilisant `builder.moveToPage(pageNumber)`. Insérez le contrôle juste après le déplacement, puis définissez sa position comme indiqué ci‑dessus.

### « Cela fonctionne‑t‑il avec les fichiers .doc (Word 97‑2003) ? »

Oui — Aspose.Words gère automatiquement les formats anciens. Changez simplement l'extension du fichier dans `doc.save("Demo.doc")`.

## Exemple complet et exécutable

Ci‑dessous se trouve le programme complet que vous pouvez copier‑coller dans une classe Java et exécuter immédiatement (en supposant que le JAR Aspose.Words soit dans le classpath).

```java
import com.aspose.words.*;

public class InsertCommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first ActiveX CommandButton.
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");

        // 3️⃣ Set button location and size – the core set button size logic.
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // 4️⃣ (Optional) Add a second button for illustration.
        Forms2OleControl cancelBtn = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
        cancelBtn.setName("cmdCancel");
        cancelBtn.setCaption("Cancel");
        cancelBtn.setLeft(190);
        cancelBtn.setTop(150);
        cancelBtn.setWidth(80);
        cancelBtn.setHeight(30);

        // 5️⃣ Save the document – you’ve now created a Word document button.
        doc.save("CommandButtonDemo.docx");
    }
}
```

Exécutez le programme, ouvrez le `CommandButtonDemo.docx` généré, et vous verrez deux boutons correctement dimensionnés prêts à l'interaction.

## Conclusion – Vous avez maîtrisé la définition de la taille du bouton dans Word

Nous venons de parcourir une solution complète, de bout en bout, pour **définir la taille du bouton** et **définir la position du bouton** à l'aide d'Aspose.Words for Java. En suivant les étapes, vous pouvez **insérer un bouton activex**, **ajouter programmatique un bouton** de contrôle, et finalement **créer des éléments de bouton de document Word** qui se comportent exactement comme vous le souhaitez.

Et ensuite ? Essayez d'intégrer le bouton à l'intérieur d'une cellule de tableau, ou d'attacher une macro VBA qui valide les champs du formulaire avant la soumission. Le même schéma fonctionne pour d'autres contrôles ActiveX comme les cases à cocher ou les listes déroulantes — il suffit de remplacer `Forms2OleControlType.COMMAND_BUTTON` par la valeur d'énumération appropriée.

Si vous rencontrez des problèmes, laissez un commentaire ci‑dessous. Bon codage, et profitez de la puissance de la création automatisée de documents Word !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment définir LoadOptions dans Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Comment supprimer les pieds‑de‑page des documents Word avec Aspose.Words for Java](/words/english/java/document-manipulation/removing-content-from-documents/)
- [Aspose.Words Java : Guide complet du traitement des documents Word](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}