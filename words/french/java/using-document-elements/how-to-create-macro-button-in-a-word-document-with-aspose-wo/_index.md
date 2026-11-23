---
category: general
date: 2026-11-22
description: Créer un bouton macro dans un document Word en utilisant Java. Apprenez
  à insérer un bouton de commande, à définir le texte du bouton et à lier la macro
  au bouton pour des documents interactifs.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: fr
lastmod: 2026-11-22
og_description: Créer un bouton macro dans un document Word en utilisant Java. Ce
  tutoriel montre comment insérer un bouton de commande, définir le texte du bouton
  et lier la macro au bouton pour une interactivité complète.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Créer un bouton macro dans un document Word avec Java – guide étape par
  étape
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Comment créer un bouton macro dans un document Word avec Aspose.Words pour
  Java
url: /fr/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comment créer un bouton macro dans un document Word avec Aspose.Words pour Java

Si vous devez **créer un bouton macro** dans un fichier Word, ce guide vous accompagne à travers les étapes exactes requises. Vous apprendrez comment **insérer un bouton de commande**, **définir le texte du bouton**, et **lier une macro au bouton** afin que le document devienne entièrement interactif.

Les développeurs intègrent souvent des contrôles OLE pour déclencher des macros VBA depuis un document. Ce tutoriel couvre le flux de travail complet, de la configuration du projet à un exemple Java exécutable qui ajoute un **bouton interactif** à un fichier .docx. Aucun script externe n’est nécessaire — tout s’exécute à l’intérieur du processus Java.

## Prérequis

Avant de commencer, assurez-vous d’avoir :

* JDK 17 ou version ultérieure installé.
* Maven 3.8+ (ou Gradle) pour la gestion des dépendances.
* Aspose.Words for Java 23.9 ou plus récent – la bibliothèque fournit les API `DocumentBuilder` et OLE control.
* Une connaissance de base de Java et des macros VBA.

Si l’un de ces éléments manque, installez‑le d’abord ; le reste du tutoriel suppose qu’ils sont disponibles.

## Comment créer un bouton macro avec Aspose.Words pour Java

Le cœur de la solution se compose de quatre actions :

1. **Insérer un bouton de commande** contrôle OLE dans le document.
2. **Définir le texte du bouton** (légende) que l’utilisateur voit.
3. **Lier une macro au bouton** afin que le clic exécute la routine VBA souhaitée.
4. **Enregistrer le document** avec la macro intégrée.

Chaque action est expliquée dans sa propre section ci‑dessous.

### Étape 1 : Insérer un bouton de commande dans le document

`DocumentBuilder.insertForms2OleControl` crée un contrôle OLE du type spécifié. La constante `Forms2OleControlType.COMMAND_BUTTON` indique à Aspose.Words de générer un bouton de commande pouvant héberger une macro.

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Pourquoi c’est important :** Le contrôle OLE agit comme un conteneur pour la macro. Sans l’insérer, il n’y a aucun élément visuel sur lequel l’utilisateur peut cliquer.

### Étape 2 : Définir le texte du bouton (légende)

La légende est le libellé visible sur le bouton. Utilisez `setCaption` pour définir ce que l’utilisateur voit.

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Pourquoi c’est important :** Un texte de bouton clair améliore l’utilisabilité. La méthode `setCaption` met à jour la propriété `Caption` du contrôle OLE, que Word rend comme libellé du bouton.

### Étape 3 : Lier une macro au bouton

Une macro est identifiée par son nom, par exemple `MyMacro`. La méthode `setOnClick` stocke ce nom dans le gestionnaire d’événement `OnClick` du bouton.

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Pourquoi c’est important :** Lier une macro crée le comportement interactif. Lorsque l’utilisateur clique sur le bouton dans Word, la routine VBA associée s’exécute.

### Étape 4 : Ajouter un bouton interactif à un document Word

Après avoir configuré le contrôle OLE, vous pouvez le positionner, le redimensionner ou ajouter du texte autour. Le `DocumentBuilder` continue d’opérer sur le document, vous permettant d’insérer des paragraphes avant ou après le bouton.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Pourquoi c’est important :** Enregistrer au format `.docm` préserve le code de la macro. Si vous enregistrez au format `.docx`, la référence à la macro est perdue.

## Exemple complet exécutable

Voici le programme Java complet, incluant les imports, la gestion des exceptions et des commentaires expliquant chaque étape. Copiez le code dans un projet Maven avec la dépendance Aspose.Words et exécutez‑le.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Résultat attendu

Exécuter le programme génère `MacroButtonDemo.docm`. L’ouverture du fichier dans Microsoft Word affiche :

* Un paragraphe contenant *« Press the button to execute the macro: »*.
* Un bouton libellé **Run Report** directement sous le paragraphe.
* Lorsque vous cliquez sur le bouton, Word tente d’exécuter la macro `MyMacro`. (Vous devez ajouter le code VBA réel au document manuellement ou via une autre étape d’automatisation.)

Si la macro n’existe pas, Word affiche un avertissement de sécurité, ce qui est le comportement standard pour les documents activés par macro.

## Variantes courantes et cas limites

| Scénario | Comment adapter le code |
|----------|--------------------------|
| **Different button caption** | Change the string passed to `setCaption`. |
| **Multiple buttons** | Call `insertForms2OleControl` repeatedly, each with its own `setCaption` and `setOnClick`. |
| **Custom macro names** | Replace `"MyMacro"` with any valid VBA procedure name, e.g., `"ExportToExcel"`. |
| **Button size constraints** | Adjust `setWidth` and `setHeight` values; Word respects the points you provide. |
| **Embedding the macro programmatically** | Use `Document.getBuiltInDocumentProperties().add("Macros", …)` or a separate VBA injection step; Aspose.Words does not write VBA code itself. |

**Astuce :** Testez toujours le `.docm` généré sur une machine dont la sécurité des macros est réglée sur *Enable all macros* pour le développement. En production, signez la macro avec un certificat de confiance pour éviter les invites de sécurité.

## Liste de vérification de dépannage

* **Le bouton n’apparaît pas** – Vérifiez que le document est enregistré au format `.docm` et ouvert dans une version de Word qui prend en charge les contrôles OLE.
* **La macro ne s’exécute pas** – Assurez‑vous que le nom de la macro correspond exactement, y compris la casse, et que la macro existe dans le projet VBA du document.
* **La légende du bouton est tronquée** – Augmentez la largeur du bouton avec `setWidth` pour accueillir un texte plus long.
* **Déplacement inattendu de la mise en page** – Utilisez `builder.moveTo` pour positionner le curseur précisément avant d’insérer le contrôle.

## Conclusion

Vous savez maintenant comment **créer un bouton macro** dans un document Word en utilisant Java, **insérer un bouton de commande**, **définir le texte du bouton**, et **lier une macro au bouton** pour une interactivité complète. L’exemple complet montre chaque appel d’API requis, explique pourquoi chaque étape est importante, et fournit des conseils pour les variantes courantes.

Ensuite, vous pourriez explorer :

* **Ajouter un bouton interactif** aux modèles existants au lieu d’un nouveau document.
* **Injecter du code VBA programmatiquement** en utilisant l’Open XML SDK ou un outil d’automatisation secondaire.
* **Combiner plusieurs contrôles OLE** (cases à cocher, listes déroulantes) pour créer des formulaires riches.

Expérimentez avec différentes légendes, noms de macro et tailles de bouton pour répondre à votre cas d’utilisation spécifique. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment insérer un bouton de commande dans un document Word en Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Comment définir la position du bouton dans un document Word avec Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Comment insérer un bouton ActiveX dans Word – Définir la légende du bouton](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}