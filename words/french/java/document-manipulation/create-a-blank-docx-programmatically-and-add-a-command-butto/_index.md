---
category: general
date: 2026-10-20
description: Créer un fichier DOCX vierge de manière programmatique et y intégrer
  un bouton de commande en Java. Découvrez le code complet pour créer un document
  Word, l’enregistrer avec le bouton et définir la légende du bouton de commande.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: fr
lastmod: 2026-10-20
og_description: Créez un DOCX vierge par programmation et intégrez un bouton de commande.
  Suivez ce guide Java étape par étape pour enregistrer le document Word avec le bouton
  et définir la légende du bouton de commande.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Créer un DOCX vierge par programmation – ajouter un bouton de commande
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Créer un DOCX vierge par programmation et ajouter un bouton de commande
url: /fr/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un DOCX vierge programmé et ajouter un bouton de commande

Si vous devez **créer un blank DOCX programmatically**, ce tutoriel vous montre comment intégrer un bouton de commande directement dans le fichier. Vous obtiendrez le *create word document code* complet qui enregistre un document Word avec un bouton, vous permet de **set command button caption**, et fonctionne avec la dernière bibliothèque Aspose.Words for Java.

Intégrer des contrôles interactifs dans un fichier DOCX est utile lorsque vous souhaitez distribuer des modèles qui déclenchent des macros, lancent des programmes externes, ou simplement guident les utilisateurs avec un bouton cliquable « Click Me ». Les étapes ci‑dessous couvrent tout, de l'initialisation d'un document vierge à la persistance du fichier final sur le disque.

## Prérequis

* Java 17 ou une version plus récente installé.  
* Maven (ou votre outil de construction préféré) pour gérer les dépendances.  
* Aspose.Words for Java 23.9 ou ultérieur. Ajoutez la dépendance à votre `pom.xml` :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Un IDE tel qu'IntelliJ IDEA ou VS Code (tout éditeur supportant Java fonctionne).

## Créer un DOCX vierge programmé – étape par étape

Les sections suivantes décomposent le processus en étapes claires et numérotées. Chaque étape explique **pourquoi** elle est nécessaire, pas seulement **quoi** taper.

### Étape 1 : Initialiser un nouveau document vierge

Un document vierge est la toile sur laquelle vous placerez le bouton de commande. Aspose.Words fournit la classe `Document` à cet effet.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Pourquoi c’est important* : Commencer avec un `Document` vide garantit qu'aucun formatage caché ou contrôle existant n'interfère avec le bouton que vous ajouterez plus tard.

### Étape 2 : Configurer un `DocumentBuilder`

`DocumentBuilder` est un assistant qui vous permet d'insérer du contenu, y compris des contrôles OLE, sans gérer la manipulation de nœuds de bas niveau.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Pourquoi c’est important* : Le builder maintient la position actuelle du curseur, de sorte que le bouton sera placé exactement où vous le spécifiez.

### Étape 3 : Insérer un bouton de commande OLE

Word considère les contrôles interactifs comme des objets OLE (Object Linking and Embedding). Aspose.Words expose `Forms2OleControl` à cet effet.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Pourquoi c’est important* : L’insertion du contrôle crée un espace réservé que vous pouvez configurer ultérieurement (type, légende, position).

### Étape 4 : Configurer le bouton – type, légende et emplacement

Vous devez définir le type du contrôle (`COMMANDBUTTON`), définir une légende visible par l'utilisateur, et le placer sur la page.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Pourquoi c’est important* :  
* **Type** indique à Word que le contrôle se comporte comme un bouton cliquable.  
* **Caption** est le texte que l'utilisateur voit ; le modifier correspond à **set command button caption**.  
* **Left** et **Top** contrôlent le placement exact, ce qui est essentiel lorsque vous **add command button word** des documents qui nécessitent une mise en page précise.

### Étape 5 : Enregistrer le document avec le bouton intégré

Enfin, écrivez le fichier sur le disque. Le fichier résultant peut être ouvert dans Microsoft Word, où le bouton sera pleinement fonctionnel.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Pourquoi c’est important* : Cette étape **saves Word with button** afin que le contrôle persiste d’une machine à l’autre. Le fichier peut être distribué comme modèle ou utilisé dans des pipelines de génération de rapports automatisés.

## Exemple complet fonctionnel

Copiez la classe entière ci‑dessous dans un fichier nommé `CommandButtonDemo.java`, ajustez `YOUR_DIRECTORY` à un chemin réel, et exécutez‑la avec `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Résultat attendu

Lorsque vous ouvrez `CommandButton.docx` dans Microsoft Word :

* Le document est complètement vierge sauf un bouton libellé **Click Me**.  
* Cliquer sur le bouton affichera le comportement par défaut de Word (il ne fait rien à moins qu'une macro ne soit attachée), confirmant que le contrôle OLE a été correctement intégré.

## Questions fréquentes & cas particuliers

| Question | Réponse |
|----------|--------|
| **Puis-je changer la taille du bouton ?** | Oui. Utilisez `commandButton.setWidth(double)` et `commandButton.setHeight(double)` pour ajuster les dimensions en points. |
| **Et si j’ai besoin d’une macro attachée au bouton ?** | Le bouton lui‑même n’est qu’un contrôle OLE. Vous devez ajouter une macro VBA au document manuellement ou via les utilitaires `addMacro` de l’API `Document` d’Aspose.Words. |
| **Le bouton fonctionnera‑t‑il dans LibreOffice ?** | LibreOffice prend en charge des contrôles OLE limités. Le bouton apparaît, mais son comportement au clic peut différer. |
| **Comment ajouter plusieurs boutons ?** | Répétez les Étapes 3‑4 avec une nouvelle instance de `Forms2OleControl`. Ajustez `setLeft`/`setTop` pour chaque bouton afin d’éviter le chevauchement. |
| **Le code est‑il compatible avec .NET ?** | La même logique s’applique, mais vous utiliseriez les classes `Aspose.Words` pour .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Conseils du terrain

* **Astuce pro** : Utilisez `builder.moveToDocumentEnd()` avant d’insérer le bouton si vous le voulez à la toute fin du document, quel que soit le contenu précédent.  
* **Attention** : Des valeurs très petites de `Left`/`Top` peuvent placer le bouton en dehors de la zone imprimable, le rendant invisible dans la vue mise en page de Word.  
* **Note de performance** : Insérer de nombreux contrôles OLE peut augmenter la taille du fichier. Si vous avez seulement besoin d’un indice visuel, envisagez d’utiliser une simple `Shape` avec un hyperlien à la place.

## Conclusion

Vous savez maintenant comment **create a blank DOCX programmatically** et intégrer un bouton de commande entièrement fonctionnel en Java. Le tutoriel a couvert l’ensemble du flux de travail *create word document code*, a démontré comment **save Word with button**, a montré la bonne façon d’**add command button word** les éléments, et a expliqué comment **set command button caption**.

À partir d’ici, vous pouvez :

* Ajouter d’autres contrôles OLE (cases à cocher, listes déroulantes) pour des formulaires plus riches.  
* Attacher des macros VBA pour que le bouton exécute des actions personnalisées.  
* Combiner cette technique avec la fusion de documents pour des modèles dynamiques et interactifs.

N’hésitez pas à expérimenter avec les styles de bouton, les positions et les contrôles supplémentaires pour répondre à vos exigences métier spécifiques. Bon codage

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l’API et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Créer un document Word vierge avec un bouton de commande – guide étape par étape](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Comment insérer un bouton ActiveX dans Word – définir la légende du bouton](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Créer un document Word vierge avec Java – guide complet Aspose.Words](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}