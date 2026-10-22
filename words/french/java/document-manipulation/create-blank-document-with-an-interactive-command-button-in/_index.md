---
category: general
date: 2026-09-18
description: Créer un document vierge en Java et ajouter un bouton ActiveX. Apprenez
  comment insérer un bouton de commande, créer un formulaire interactif et enregistrer
  un document Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- create interactive form
- add activex button
- how to insert command button
- create word document
language: fr
lastmod: 2026-09-18
og_description: Créez un document vierge en Java et intégrez un bouton de commande
  ActiveX. Suivez ce guide étape par étape pour créer un formulaire interactif et
  enregistrer le fichier Word.
og_image_alt: Screenshot of a Word document showing a clickable ActiveX command button
og_title: Créer un document vierge avec un bouton de commande interactif dans Word
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  headline: Create blank document with an interactive command button in Word using
    Java
  type: TechArticle
- description: Create blank document in Java and add an ActiveX button. Learn how
    to insert command button, build an interactive form, and save a Word document.
  name: Create blank document with an interactive command button in Word using Java
  steps:
  - name: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
    text: 'Load the existing document: `Document doc = new Document("ExistingForm.docx");`'
  - name: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
    text: 'Move the builder to the desired location: `builder.moveToParagraph(5, 0);
      // 6th paragraph, first node`'
  - name: Insert the button as shown in Step 3.
    text: Insert the button as shown in Step 3.
  - name: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
    text: Adjust the button’s `Top`/`Left` based on the paragraph’s layout.
  type: HowTo
tags:
- Aspose.Words
- Java
- ActiveX
- Word automation
title: Créer un document vierge avec un bouton de commande interactif dans Word en
  utilisant Java
url: /fr/java/document-manipulation/create-blank-document-with-an-interactive-command-button-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un document vierge avec un bouton de commande interactif dans Word à l'aide de Java

Si vous devez **créer un document vierge** qui contient un bouton cliquable, ce guide vous montre exactement comment le faire avec Aspose.Words for Java. Vous apprendrez à créer un formulaire interactif, ajouter un bouton ActiveX, et enfin enregistrer le fichier Word — le tout en quelques étapes concises.

Intégrer un bouton de commande transforme un .docx statique en un formulaire fonctionnel avec lequel les utilisateurs finaux peuvent interagir directement dans Microsoft Word. Ce tutoriel couvre également **comment insérer un bouton de commande**, la gestion des pièges courants, et l'extension de la solution pour des formulaires plus complexes.

## Prérequis

Avant de commencer, assurez‑vous d’avoir :

* Java 17 ou version ultérieure (le code se compile avec JDK 17+)
* Aspose.Words for Java 23.9 ou plus récent – la bibliothèque fournit `Document`, `DocumentBuilder` et `Forms2OleControl`.
* Un IDE ou un outil de construction (Maven/Gradle) capable d'ajouter la dépendance Aspose.Words.
* Connaissances de base de la syntaxe Java et des concepts de documents Word.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

## Étape 1 : Créer un document vierge

La première opération consiste à instancier un nouvel objet `Document`. Cet objet représente un fichier Word vide prêt à recevoir du contenu.

```java
// Step 1: Create a new blank document
Document doc = new Document();
```

Créer un document vierge vous offre une toile propre, ce qui est essentiel lorsque vous souhaitez **créer un document Word** de manière programmatique sans aucun modèle préexistant.

## Étape 2 : Initialiser un DocumentBuilder

`DocumentBuilder` est la classe principale pour ajouter du texte, des tableaux et des contrôles de formulaire. Elle agit sur le `Document` que vous venez de créer.

```java
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Le constructeur maintient le point d’insertion actuel, de sorte que les commandes suivantes affectent l’emplacement correct dans le fichier.

## Étape 3 : Insérer un contrôle de bouton de commande Forms2Ole

Aspose.Words expose la classe `Forms2OleControl` pour les contrôles ActiveX. Pour **ajouter un bouton activex**, vous demandez un type `COMMANDBUTTON` au builder.

```java
// Step 3: Insert a Forms2Ole command button control
Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);
```

La méthode `insertForms2OleControl` insère le contrôle à l’emplacement actuel du curseur du builder. Comme le contrôle est un objet ActiveX, il ne fonctionne que dans la version de bureau de Microsoft Word, pas dans Word Online.

## Étape 4 : Configurer l’apparence et la position du bouton

Vous pouvez définir la légende, la taille et l’emplacement du bouton à l’aide des setters du contrôle. Les valeurs de position sont mesurées en points (1 point = 1/72 pouce).

```java
// Step 4: Configure the button's appearance and position
commandButton.setCaption("Click Me");   // Text shown on the button
commandButton.setTop(100);              // Distance from the top edge of the page (points)
commandButton.setLeft(100);             // Distance from the left edge of the page (points)
commandButton.setWidth(120);            // Optional: set button width
commandButton.setHeight(30);            // Optional: set button height
```

*Pourquoi configurer ces propriétés ?* Définir `Top` et `Left` garantit que le bouton apparaît à l’endroit prévu sur la page, tandis que `Caption` définit le libellé visible par l’utilisateur. Si vous omettez la largeur/hauteur, Word attribue des dimensions par défaut, qui peuvent ne pas correspondre à votre conception.

### Astuce pro
Si vous prévoyez d’ajouter plusieurs contrôles, appelez `builder.moveToDocumentEnd()` avant chaque insertion pour éviter le chevauchement des objets.

## Étape 5 : Enregistrer le document avec le bouton de commande intégré

Enfin, écrivez le document sur le disque. L’extension du fichier doit être `.docx` (ou `.doc` pour les versions plus anciennes de Word) afin de conserver le contrôle ActiveX.

```java
// Step 5: Save the document with the embedded command button
String outputPath = "C:/temp/CommandButton.docx";
doc.save(outputPath);
System.out.println("Document saved to: " + outputPath);
```

Lorsque vous ouvrez `CommandButton.docx` dans Microsoft Word, vous verrez un bouton libellé **Click Me**. En le cliquant, vous déclencherez l’action ActiveX par défaut (qui, par défaut, ne fait rien). Vous pourrez ensuite attacher une macro ou un script VBA pour définir un comportement personnalisé.

## Comment insérer un bouton de commande dans un formulaire existant (optionnel)

Si vous avez déjà un formulaire avec des champs texte et que vous souhaitez **créer un formulaire interactif** incluant un bouton, suivez ces étapes supplémentaires :

1. Charger le document existant : `Document doc = new Document("ExistingForm.docx");`
2. Déplacer le builder à l’emplacement souhaité : `builder.moveToParagraph(5, 0); // 6e paragraphe, premier nœud`
3. Insérer le bouton comme indiqué à l’Étape 3.
4. Ajuster le `Top`/`Left` du bouton en fonction de la mise en page du paragraphe.

## Cas limites et dépannage

| Situation | Ce qu’il faut vérifier | Correction recommandée |
|-----------|------------------------|------------------------|
| Le bouton n’apparaît pas dans Word | Assurez‑vous d’avoir ouvert le fichier dans la version de bureau de Word (Word Online supprime les ActiveX). | Ouvrez le fichier dans Word 2016+ version bureau. |
| La légende est tronquée | Vérifiez que la largeur du bouton est suffisante pour contenir le texte. | Augmentez `setWidth` jusqu’à ce que la légende tienne. |
| La sauvegarde génère une `IOException` | Confirmez que le répertoire de sortie existe et que vous avez les droits d’écriture. | Créez le répertoire ou exécutez le programme avec des droits élevés. |
| Plusieurs boutons se chevauchent | Le curseur du builder n’a peut‑être pas été déplacé après l’insertion précédente. | Appelez `builder.moveToDocumentEnd()` avant d’insérer chaque nouveau contrôle. |

## Exemple complet exécutable

Ci‑dessous se trouve un programme Java complet et autonome que vous pouvez copier, compiler et exécuter. Il démontre **créer un document vierge**, **ajouter un bouton activex**, et **enregistrer le document Word** en un seul flux.

```java
import com.aspose.words.*;

public class CommandButtonDemo {
    public static void main(String[] args) {
        try {
            // 1. Create a new blank document
            Document doc = new Document();

            // 2. Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Insert an ActiveX command button
            Forms2OleControl commandButton = builder.insertForms2OleControl(OleControlType.COMMANDBUTTON);

            // 4. Configure button properties
            commandButton.setCaption("Click Me");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(100);  // points from left
            commandButton.setWidth(120);
            commandButton.setHeight(30);

            // 5. Save the document
            String outPath = "CommandButton.docx";
            doc.save(outPath);
            System.out.println("Document created: " + outPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Sortie attendue**

```
Document created: CommandButton.docx
```

L’ouverture de `CommandButton.docx` affiche une page unique avec un bouton libellé **Click Me** positionné à 100 pt du haut et du bord gauche.

## Conclusion

Vous savez maintenant comment **créer un document vierge**, intégrer un **bouton ActiveX**, et transformer un simple fichier Word en **formulaire interactif**. En maîtrisant **comment insérer un bouton de commande**, vous pouvez étendre ce modèle pour ajouter des cases à cocher, des listes déroulantes, ou même une logique VBA personnalisée.

Ensuite, envisagez d’explorer ces sujets connexes :

* **Créer un formulaire interactif** avec des champs texte (`builder.insertField`)  
* **Ajouter un bouton activex** qui exécute une macro VBA (`builder.insertOleObject`)  
* **Créer un document Word** à partir d’un modèle en utilisant `Document(docTemplatePath)`  
* Convertir le .docx résultant en PDF tout en conservant le bouton (note : le PDF affichera le bouton comme une image statique).

N’hésitez pas à expérimenter la taille, la position et la légende du bouton pour correspondre à votre conception UI. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités API supplémentaires et explorer des approches d’implémentation alternatives dans vos propres projets.

- [Comment créer des champs de formulaire et ajouter du contenu avec DocumentBuilder dans Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Créer un projet VBA dans un document Word](/words/english/net/working-with-vba-macros/create-vba-project/)
- [Créer un nouveau document Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}