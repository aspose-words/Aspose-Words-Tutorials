---
category: general
date: 2026-07-29
description: 'Tutoriel Java pour définir la taille du bouton : apprenez comment insérer
  un bouton de commande ActiveX dans un document Word en utilisant Java et Aspose.Words,
  ainsi que le dimensionnement et la création d’un document vierge.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: fr
lastmod: 2026-07-29
og_description: Le guide Set Button Size Java montre comment insérer un bouton de
  commande ActiveX dans un fichier Word en Java, ajuster sa taille et enregistrer
  le document de façon programmatique.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Définir la taille du bouton Java – Ajouter un bouton de commande ActiveX
  à Word avec Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Définir la taille du bouton Java – Insérer un bouton de commande ActiveX dans
  Word
url: /fr/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# définir la taille du bouton java – Insérer un bouton de commande ActiveX dans Word

Vous êtes-vous déjà demandé **comment définir la taille du bouton java** lorsque vous automatisez des documents Word ? Peut‑être construisez‑vous un outil de reporting qui nécessite un bouton « Submit » cliquable directement dans le fichier .docx. Dans ce tutoriel, nous parcourrons l’ensemble du processus : création d’un document Word vierge, insertion d’un bouton de commande ActiveX, et définition explicite de sa largeur et de sa hauteur — le tout avec Java et Aspose.Words.

Nous répondrons également à la question récurrente « comment insérer activex » qui revient souvent chez les développeurs. À la fin, vous disposerez d’un programme exécutable qui génère un fichier Word contenant un bouton de commande parfaitement dimensionné, prêt à être personnalisé davantage.

---

## Ce dont vous aurez besoin

- **Java Development Kit (JDK) 8 ou plus récent** – le code se compile avec n'importe quel JDK récent.  
- **Aspose.Words for Java** (la dernière version en date de juillet 2026). Téléchargez le JAR depuis le [site Aspose](https://products.aspose.com/words/java) ou via Maven :  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Un IDE ou un éditeur de texte simple — IntelliJ IDEA, Eclipse ou VS Code feront l'affaire.  
- Un dossier où vous souhaitez que le **CommandButton.docx** généré soit enregistré.

C’est tout. Aucun library d’interop Office supplémentaire, aucun tour de COM, juste du Java pur.

## Implémentation étape par étape

Nous allons diviser la solution en cinq étapes logiques. Chaque étape possède son propre titre H2 ; l’une d’elles contient notre **mot‑clé principal** pour le SEO.

### 1. Configurer le projet et importer Aspose.Words

Tout d’abord, créez un nouveau projet Maven (ou Gradle) et ajoutez la dépendance Aspose.Words indiquée ci‑dessus. Ensuite, importez les classes requises dans votre fichier source Java :

```java
import com.aspose.words.*;
```

> **Astuce :** Si vous utilisez un IDE, laissez‑le auto‑importer les classes. Cela évite beaucoup de frappes et prévient les fautes de frappe.

### 2. java créer un document Word vierge

Maintenant, nous allons réellement **java créer un document Word** vierge. C’est la base sur laquelle nous **insérerons le bouton de commande word** plus tard.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

L’objet `Document` représente l’ensemble du fichier Word en mémoire. À ce stade, le fichier n’a ni pages, ni texte — juste une page blanche.

### 3. Initialiser DocumentBuilder et insérer le contrôle ActiveX

`DocumentBuilder` est un assistant qui nous permet d’ajouter du contenu, des paragraphes, des tableaux et, oui, des contrôles ActiveX. Voici où nous répondons à **comment insérer activex** :

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` est le wrapper d’Aspose autour d’un objet OLE. En spécifiant `COMMANDBUTTON`, nous indiquons à Word d’insérer un bouton de commande ActiveX classique.

### 4. Comment définir la taille du bouton Java – Ajuster largeur et hauteur

Voici le cœur du tutoriel : **comment définir la taille du bouton java**. Le contrôle expose plusieurs propriétés de mise en page — `Left`, `Top`, `Width` et `Height`. Les définir directement contrôle l’apparence du bouton sur la page.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Pourquoi ces nombres ? Dans Word, un point équivaut à 1/72 de pouce. Ainsi, une largeur de `120` points correspond à environ 1,67 pouces — suffisamment grand pour une étiquette lisible, sans être envahissant. Ajustez les valeurs selon votre mise en page ; les mêmes propriétés répondent également à la requête **comment définir le bouton** que vous pourriez avoir.

> **Remarque :** Si vous avez besoin d’un autre type de bouton (par ex., une case à cocher), remplacez `Forms2OleControlType.COMMANDBUTTON` par la valeur d’énumération appropriée.

### 5. Enregistrer le document

Enfin, persistez le document sur le disque :

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Remplacez `YOUR_DIRECTORY` par un chemin absolu ou relatif sur votre machine. Après l’exécution du programme, ouvrez le fichier généré dans Microsoft Word. Vous verrez un bouton libellé « Click Me » positionné à 100 pts du bord gauche et 200 pts du bord supérieur, dimensionné exactement comme nous l’avons défini.

---

## Exemple complet fonctionnel

Voici la classe Java complète, prête à être exécutée. Copiez‑collez‑la dans `CommandButtonActiveX.java`, ajustez le chemin de sortie, puis lancez **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Résultat attendu :** L’ouverture de `CommandButton.docx` dans Word affiche une page unique avec un bouton cliquable « Click Me » placé approximativement au centre de la page. Les dimensions du bouton correspondent aux valeurs que vous avez définies, confirmant que **définir la taille du bouton java** fonctionne comme prévu.

---

## Questions fréquentes et cas particuliers

### Que faire si le bouton n’apparaît pas dans Word ?

- **Vérifiez la version de Word.** Les contrôles ActiveX nécessitent la version de bureau de Word ; Word Online les supprime.
- **Assurez‑vous que la licence Aspose.Words est appliquée** (si vous utilisez une édition payante). Une version d’évaluation non licenciée peut ajouter un filigrane mais affichera tout de même le contrôle.

### Puis‑je modifier la police ou la couleur du bouton ?

Oui. Après l’insertion du contrôle, vous pouvez accéder à son objet OLE sous‑jacent et manipuler les propriétés VBA. C’est un sujet plus avancé — consultez `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` pour un texte rouge, par exemple.

### Comment gérer l’événement de clic du bouton ?

Les boutons de commande ActiveX déclenchent un événement VBA `Click`. Pour rendre le bouton fonctionnel, vous devez intégrer une macro dans le même document. Aspose.Words peut ajouter un module de macro via l’API `Document.getMacros()`, mais le code de la macro doit être écrit en VBA.

### Et les autres types de boutons ?

Aspose.Words prend en charge de nombreuses valeurs `Forms2OleControlType` : `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, etc. Remplacez simplement la constante d’énumération dans l’appel `insertForms2OleControl` pour expérimenter.

---

## Astuces pro pour un code prêt pour la production

1. **Utilisez des constantes pour les valeurs de mise en page** – cela facilite les ajustements futurs.  
2. **Encapsulez le chemin de sauvegarde dans un objet `Path`** pour éviter les séparateurs spécifiques à la plateforme.  
3. **Libérez le Document** (ou utilisez try‑with‑resources) si vous traitez de nombreux fichiers dans une boucle.  
4. **Validez le dossier de sortie** avant d’appeler `save` afin d’éviter les `FileNotFoundException`.

---

## Conclusion

Vous venez d’apprendre **définir la taille du bouton java** en créant un fichier Word vierge, en insérant un bouton de commande ActiveX, et en configurant précisément ses dimensions — le tout avec quelques lignes de code Java. Cela couvre l’essentiel de **comment insérer activex**, **comment définir le bouton**, **java créer un document Word vierge**, et **insérer le bouton de commande word** dans un exemple autonome.

Prochaines étapes ? Essayez de personnaliser le libellé du bouton, d’ajouter une macro pour réagir aux clics, ou d’insérer plusieurs contrôles sur la même page. Vous pouvez également explorer la conversion du .docx résultant en PDF avec Aspose.Words, en conservant le bouton sous forme d’image statique.

N’hésitez pas à expérimenter, et si vous rencontrez un problème, laissez un commentaire ci‑dessous. Bon codage !


## Que devriez‑vous apprendre ensuite ?


Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques présentées dans ce guide. Chaque ressource inclut des exemples de code complets avec des explications pas à pas pour vous aider à maîtriser d’autres fonctionnalités de l’API et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Comment charger des documents Word avec Aspose.Words Java : guide complet](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Comment enregistrer un document au format PDF avec Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}