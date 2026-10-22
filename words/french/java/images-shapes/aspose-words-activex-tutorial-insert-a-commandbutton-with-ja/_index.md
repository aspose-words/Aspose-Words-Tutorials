---
category: general
date: 2026-08-07
description: Le tutoriel Aspose.Words ActiveX montre comment ajouter un contrôle CommandButton
  à un document Word en utilisant Java. Découvrez le code complet, la configuration
  et les étapes d’enregistrement.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose words activex tutorial
- aspose.words java
- activeX control java
- documentbuilder insert control
- forms2olecontrol usage
language: fr
lastmod: 2026-08-07
og_description: Le tutoriel Aspose.Words ActiveX explique comment intégrer un contrôle
  ActiveX CommandButton dans un document Word en utilisant Java. Suivez l'exemple
  complet pour créer, configurer et enregistrer le document.
og_image_alt: Screenshot of a Word document with a CommandButton added via Aspose.Words
  ActiveX tutorial
og_title: Tutoriel ActiveX Aspose.Words – Guide Java étape par étape
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  headline: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  type: TechArticle
- description: Aspose.Words ActiveX tutorial shows how to add a CommandButton control
    to a Word document using Java. Learn the full code, configuration, and saving
    steps.
  name: Aspose.Words ActiveX tutorial – insert a CommandButton with Java
  steps:
  - name: Initialize a `Document` and `DocumentBuilder`.
    text: Initialize a `Document` and `DocumentBuilder`.
  - name: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
    text: Insert a `Forms2OleControl` of type `COMMAND_BUTTON`.
  - name: Set the button’s name, caption, size, and position.
    text: Set the button’s name, caption, size, and position.
  - name: Save the document as a .docx file that contains the ActiveX control.
    text: Save the document as a .docx file that contains the ActiveX control.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
title: Tutoriel Aspose.Words ActiveX – insérer un CommandButton avec Java
url: /fr/java/images-shapes/aspose-words-activex-tutorial-insert-a-commandbutton-with-ja/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutoriel Aspose.Words ActiveX – insérer un CommandButton avec Java

Si vous devez intégrer un contrôle ActiveX dans un fichier Word, ce **tutoriel Aspose.Words ActiveX** vous guide à travers l'ensemble du processus. Vous verrez comment créer un document vierge, insérer un CommandButton, définir ses propriétés et enregistrer le résultat — le tout avec du code Java simple.

L'exemple utilise l'API Aspose.Words for Java, qui élimine le besoin de Microsoft Office sur le serveur de construction. À la fin de ce guide, vous pourrez générer des fichiers .docx contenant des contrôles CommandButton pleinement fonctionnels, prêts à être utilisés dans des environnements Windows.

## Prérequis

- Java Development Kit (JDK) 8 ou version plus récente installé.
- Maven ou un autre outil de construction pour gérer les dépendances.
- Une licence Aspose.Words for Java (ou une clé d'évaluation temporaire) pour éviter les filigranes d'évaluation.
- Familiarité de base avec la syntaxe Java et la programmation orientée objet.

> **Astuce :** Ajoutez la dépendance Maven Aspose.Words à votre `pom.xml` pour permettre à l'IDE de résoudre automatiquement les classes :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version -->
</dependency>
```

## Étape 1 : Créer un nouveau document vierge et un `DocumentBuilder`

La classe `Document` représente le fichier Word en mémoire, tandis que `DocumentBuilder` fournit une API fluide pour éditer le document. L'initialisation des deux objets prépare le document pour des modifications ultérieures.

```java
import com.aspose.words.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Create an empty Word document
        Document document = new Document();

        // DocumentBuilder lets you add text, tables, and controls
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Pourquoi c'est important :**  
`DocumentBuilder` suit la position actuelle du curseur, de sorte que toute opération d'insertion ultérieure — comme l'ajout d'un contrôle — apparaît exactement à l'endroit souhaité.

## Étape 2 : Insérer un contrôle ActiveX CommandButton

Aspose.Words expose `Forms2OleControl` pour les objets ActiveX. La méthode `insertForms2OleControl` nécessite le type de contrôle, que vous spécifiez via l'énumération `Forms2OleControlType`.

```java
        // Insert a CommandButton ActiveX control at the current cursor location
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Explication :**  
Le contrôle inséré est un objet basé sur COM que Word affichera comme un bouton cliquable lorsque le document sera ouvert dans un environnement Windows.

## Étape 3 : Configurer les propriétés du bouton

Après l'insertion, vous pouvez ajuster le nom, la légende, la taille et la position du bouton. Ces propriétés influencent l'apparence et le comportement du contrôle dans Word.

```java
        // Set the logical name used by VBA or external scripts
        commandButton.setName("cmdSubmit");

        // Text displayed on the button face
        commandButton.setCaption("Submit");

        // Position the button 100 points from the left margin and 150 points from the top
        commandButton.setLeft(100);
        commandButton.setTop(150);

        // Define the button’s dimensions (width × height) in points
        commandButton.setWidth(80);
        commandButton.setHeight(30);
```

**Pourquoi ces paramètres sont importants :**  

- **Name** – Permet aux macros VBA de référencer le contrôle (`ActiveDocument.Forms("cmdSubmit")`).
- **Caption** – Détermine l'étiquette visible sur laquelle les utilisateurs cliquent.
- **Left / Top** – Contrôle le placement par rapport aux marges de la page.
- **Width / Height** – Garantit une taille visuelle cohérente sur différentes résolutions d'écran.

## Étape 4 : Enregistrer le document

Appeler `save` écrit la représentation en mémoire dans un fichier physique. Vous pouvez choisir n'importe quel format supporté (`.docx`, `.doc`, `.pdf`, etc.). Pour ce tutoriel, nous conservons le format Word natif.

```java
        // Persist the document with the embedded ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

**Résultat :**  
L'ouverture de `ActiveXDemo.docx` dans Microsoft Word affiche un CommandButton libellé **Submit** positionné aux coordonnées spécifiées. Cliquer sur le bouton déclenche le comportement par défaut (aucun code VBA n'est attaché par défaut).

## Code source complet

En assemblant les éléments, le programme complet et exécutable ressemble à ceci :

```java
import com.aspose.words.*;
import com.aspose.words.forms.*;

public class ActiveXDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a CommandButton ActiveX control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // Step 3: Configure the button's properties
        commandButton.setName("cmdSubmit");
        commandButton.setCaption("Submit");
        commandButton.setLeft(100);
        commandButton.setTop(150);
        commandButton.setWidth(80);
        commandButton.setHeight(30);

        // Step 4: Save the document with the ActiveX control
        document.save("output/ActiveXDemo.docx");
    }
}
```

### Résultat attendu

- Un fichier nommé **ActiveXDemo.docx** situé dans le dossier `output`.
- Lorsqu'il est ouvert dans Microsoft Word (Windows), le document affiche un bouton **Submit** cliquable à la position définie.
- Le bouton peut être sélectionné, déplacé ou lié à du code VBA via l'interface Word (Développeur → Propriétés).

## Gestion des variations courantes

| Scénario | Ajustement |
|----------|------------|
| **Enregistrer sous .doc** (format hérité) | `document.save("ActiveXDemo.doc", SaveFormat.DOC);` |
| **Ajouter un gestionnaire d'événement** | Word n'expose pas les événements ActiveX via Aspose.Words. Vous devez ajouter le code VBA manuellement après la génération du document. |
| **Contrôles multiples** | Répétez le bloc d'insertion/configuration avec des valeurs différentes pour `setName` et `setCaption`. |
| **Type de contrôle différent (p. ex., CheckBox)** | Utilisez `Forms2OleControlType.CHECKBOX` dans l'appel `insertForms2OleControl`. |
| **Plateformes non Windows** | Les contrôles ActiveX ne s'affichent que dans Word sous Windows. Pour des solutions multiplateformes, envisagez les contrôles de contenu (`StructuredDocumentTag`). |

## Bonnes pratiques et pièges

- **Licence précoce** – Enregistrez votre licence Aspose.Words avant de créer le `Document` pour éviter les invites d'évaluation.
- **Système de coordonnées** – Les positions sont mesurées en points (1 pt = 1/72 in). Convertissez depuis les pixels ou centimètres si votre conception UI utilise ces unités.
- **Chemins de fichiers** – Utilisez des chemins absolus ou l'API `Paths` de Java pour éviter `FileNotFoundException` lorsque le répertoire de sortie n'existe pas.
- **Sécurité des threads** – `Document` et `DocumentBuilder` ne sont pas thread‑safe. Créez des instances séparées par thread si vous générez des documents en parallèle.
- **Tests** – Vérifiez le document généré sur la version cible de Word (par ex., Word 2016, Word 365) car les versions plus anciennes peuvent afficher les contrôles ActiveX différemment.

## Conclusion

Ce **tutoriel Aspose.Words ActiveX** montre comment ajouter programmétiquement un contrôle CommandButton à un document Word en utilisant Java. Vous avez appris comment :

1. Initialiser un `Document` et un `DocumentBuilder`.
2. Insérer un `Forms2OleControl` de type `COMMAND_BUTTON`.
3. Définir le nom, la légende, la taille et la position du bouton.
4. Enregistrer le document au format .docx contenant le contrôle ActiveX.

À partir de là, vous pouvez explorer d'autres types de contrôles, automatiser l'injection de macros VBA, ou combiner les contrôles ActiveX avec d'autres fonctionnalités d'Aspose.Words telles que la fusion de courrier et les contrôles de contenu. Expérimentez avec différentes mises en page et intégrez les documents générés dans votre pipeline de reporting plus vaste basé sur Java.

---


## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et à explorer des approches d'implémentation alternatives dans vos propres projets.

- [Utilisation des objets OLE et des contrôles ActiveX dans Aspose.Words for Java](/words/english/java/using-document-elements/using-ole-objects-and-activex/)
- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Convertir Word en RTF avec le tutoriel Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-rtf-format/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}