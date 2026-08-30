---
category: general
date: 2026-08-14
description: Créer un bouton ActiveX docx en Java avec Aspose.Words. Apprenez comment
  ajouter un bouton de formulaire dans Word de façon programmatique et enregistrer
  le document.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: fr
lastmod: 2026-08-14
og_description: Créer un bouton ActiveX dans un fichier docx en Java avec Aspose.Words.
  Ce guide vous montre comment ajouter un bouton de formulaire dans Word, le configurer
  et enregistrer le fichier.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Créer un bouton ActiveX docx en Java – tutoriel étape par étape
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Créer un bouton ActiveX docx en Java – guide complet de programmation
url: /fr/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Créer un bouton ActiveX docx en Java – guide complet de programmation

Si vous devez **créer un bouton ActiveX docx** en Java, ce guide vous accompagne pas à pas. Vous verrez comment ajouter un bouton de formulaire dans Word, configurer ses propriétés et produire un fichier .docx prêt à l’emploi.

Travailler avec des contrôles ActiveX est une exigence courante lors de l’automatisation de formulaires Word hérités. Dans ce tutoriel, vous apprendrez à **ajouter un bouton de formulaire word** à l’aide de la bibliothèque Aspose.Words for Java, afin d’incorporer des contrôles interactifs sans édition manuelle.

## Ce dont vous avez besoin

Avant de commencer, assurez‑vous d’avoir :

* Java 17 ou supérieur (le code compile avec des versions antérieures, mais Java 17 est recommandé).
* Aspose.Words for Java 23.10 ou plus récent – téléchargez le JAR depuis le site Aspose ou ajoutez la dépendance Maven.
* Un IDE (IntelliJ IDEA, Eclipse ou VS Code) ou un simple éditeur de texte et des outils de construction en ligne de commande.
* Des connaissances de base en syntaxe Java et en programmation orientée objet.

## Comment créer un bouton ActiveX docx avec Aspose.Words

Les étapes suivantes montrent la séquence exacte requise pour **créer des objets bouton ActiveX docx** et les intégrer dans un document Word.

### Étape 1 : Configurer le projet et importer Aspose.Words

Ajoutez la dépendance Aspose.Words à votre `pom.xml` si vous utilisez Maven :

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Ou, si vous préférez Gradle :

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Une fois la dépendance résolue, importez les classes requises dans votre fichier source Java :

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Ces imports vous donnent accès à `Document`, `DocumentBuilder` et à l’API `Forms2OleControl` utilisée pour insérer des contrôles ActiveX.

### Étape 2 : Créer un nouveau document vierge

Instanciez un objet `Document`, qui représente un fichier Word vide prêt à recevoir du contenu.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Créer le document en premier garantit que le constructeur suivant travaille sur une toile propre.

### Étape 3 : Initialiser un DocumentBuilder

`DocumentBuilder` fournit une interface fluide pour insérer du texte, des images et des contrôles. Attachez‑le au document que vous venez de créer.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Le builder suit la position actuelle du curseur à l’intérieur du document, de sorte que l’insertion suivante se fasse exactement à l’endroit souhaité.

### Étape 4 : Insérer un contrôle ActiveX CommandButton

Utilisez la méthode `insertForms2OleControl` pour intégrer un ActiveX `CommandButton`. Cette méthode renvoie une instance de `Forms2OleControl` que vous pouvez configurer davantage.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

À ce stade, le fichier .docx contient un espace réservé pour un bouton, mais il n’a pas encore de légende visuelle ni de taille.

### Étape 5 : Configurer les propriétés du bouton

Définissez le nom du contrôle, sa légende et ses attributs de mise en page. Ces valeurs déterminent l’apparence du bouton dans Word et la façon dont vous pourrez le référencer ultérieurement via VBA ou des scripts d’automatisation.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Astuce :** Word mesure les positions en points (1 pt ≈ 1/72 in). Ajustez `setTop` et `setLeft` pour aligner le bouton avec le contenu environnant.

### Étape 6 : Enregistrer le document

Enfin, écrivez le document sur le disque. Utilisez l’extension `.docx` pour conserver le fichier au format moderne Office Open XML.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Lorsque vous ouvrirez le fichier résultant dans Microsoft Word, vous verrez un bouton **Submit** positionné aux coordonnées que vous avez spécifiées. Cliquer sur le bouton dans Word ne déclenchera aucune action à moins d’y associer du code VBA, mais le contrôle est pleinement fonctionnel pour les flux de travail basés sur des formulaires.

## Questions fréquentes et cas particuliers

| Question | Réponse |
|----------|---------|
| **Ai‑je besoin d’une version spéciale de Word ?** | Les contrôles ActiveX sont pris en charge dans la version de bureau de Microsoft Word sous Windows. Ils ne sont pas disponibles dans Word pour Mac ou Word Online. |
| **Puis‑je l’utiliser avec des fichiers `.doc` ?** | Oui. Enregistrez le document avec l’extension `.doc` (`document.save("ActiveXButton.doc")`). La même API fonctionne pour le format binaire plus ancien. |
| **Que faire si le bouton n’apparaît pas ?** | Vérifiez que **Fichier → Options → Centre de confiance → Paramètres du Centre de confiance → Paramètres ActiveX** autorise les contrôles ActiveX. Assurez‑vous également que le document n’est pas ouvert en « Vue protégée ». |
| **Puis‑je ajouter d’autres contrôles ActiveX ?** | Absolument. Remplacez `Forms2OleControlType.COMMAND_BUTTON` par `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, etc. |
| **Existe‑t‑il une limite de taille ?** | La taille du contrôle est limitée uniquement par la mise en page de la page. Des dimensions très grandes peuvent entraîner un débordement de mise en page. |

## Exemple complet et exécutable

Voici une classe Java complète que vous pouvez copier, compiler et exécuter. Elle comprend tous les imports, la méthode `main` et des commentaires en ligne pour plus de clarté.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Résultat attendu :** Après l’exécution du programme, `ActiveXButton.docx` apparaît dans le répertoire de travail. L’ouvrir dans Microsoft Word montre un bouton **Submit** cliquable positionné près du coin supérieur‑gauche de la première page.

## Conclusion

Vous savez maintenant comment **créer des objets bouton ActiveX docx** en Java à l’aide d’Aspose.Words, et vous avez vu comment **ajouter un bouton de formulaire word** aux documents de façon programmatique. Les étapes — configuration du projet, création du document, insertion du contrôle, configuration de ses propriétés et enregistrement — couvrent l’ensemble du flux de travail du début à la fin.

Ensuite, vous pourriez explorer :

* Ajouter des macros VBA qui répondent au clic du bouton.
* Incorporer d’autres contrôles ActiveX tels que des cases à cocher ou des listes déroulantes.
* Automatiser la génération de formulaires multi‑pages avec plusieurs éléments interactifs.

N’hésitez pas à expérimenter avec les tailles, les positions et les légendes pour répondre à vos exigences de conception de formulaire. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s’appuient sur les techniques démontrées dans ce guide. Chaque ressource inclut des exemples de code complets et fonctionnels avec des explications pas à pas pour vous aider à maîtriser des fonctionnalités API supplémentaires et à explorer des approches d’implémentation alternatives dans vos propres projets.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}