---
category: general
date: 2026-11-15
description: Modifiez un document Word de façon programmatique pour insérer un bouton
  de commande. Apprenez comment ajouter un bouton, définir le nom du bouton de commande
  et créer un bouton de formulaire Word en quelques minutes.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: fr
lastmod: 2026-11-15
og_description: Modifiez un document Word de façon programmatique et insérez un bouton
  de commande. Ce guide montre comment ajouter un bouton, définir le nom du bouton
  de commande et créer rapidement un bouton de formulaire Word.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Modifier un document Word par programmation – ajouter un bouton de commande
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Modifier un document Word de façon programmatique et ajouter un bouton de commande
url: /fr/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modifier un document Word programmé et ajouter un bouton de commande

Si vous devez **modifier un document Word programmé**, le moyen le plus rapide est d'utiliser l'API Aspose.Words. Ce tutoriel vous montre exactement **comment ajouter des contrôles de bouton**, configurer leur légende, et **définir le nom du bouton de commande** afin que le document puisse agir comme un formulaire simple. À la fin, vous disposerez d'un *.docx* entièrement modifiable contenant un bouton de commande fonctionnel prêt pour le traitement en aval.

Vous apprendrez comment **insérer le texte du bouton de commande**, **créer le texte du bouton de formulaire**, et gérer les propriétés du bouton sans ouvrir Word manuellement. La seule condition préalable est un environnement de développement Java de base et la bibliothèque Aspose.Words for Java.

## Prérequis

- Java 17 ou ultérieur (le code fonctionne également avec Java 8+)
- Aspose.Words for Java (télécharger depuis [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Un document Word existant (`input.docx`) que vous souhaitez modifier
- Familiarité avec Maven ou Gradle pour ajouter la dépendance Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Étape 1 : Charger le document Word

La première opération lorsque vous **modifiez un document Word programmé** consiste à charger le fichier source dans un objet `Document`. Cet objet représente l'intégralité du fichier Word en mémoire, vous permettant de manipuler son contenu.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Pourquoi c'est important :** Charger le document crée une structure de type DOM que Aspose.Words peut parcourir et modifier. Ignorer cette étape vous laisserait sans cible pour l'insertion du bouton.

## Étape 2 : Créer un `DocumentBuilder` pour modifier le document

Un `DocumentBuilder` agit comme un curseur à l'intérieur du fichier Word. Il vous permet d'insérer du texte, des images et des contrôles de formulaire à la position actuelle.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Astuce :** Si vous avez besoin du bouton dans un paragraphe spécifique, déplacez d'abord le builder avec `builder.moveToParagraph(index, true);`.

## Étape 3 : Insérer un Forms2OleControl (bouton de commande)

Nous répondons maintenant à la question centrale **comment ajouter un bouton** dans un fichier Word. La méthode `insertForms2OleControl()` crée un bouton de commande *Forms2.0* hérité, qui est le contrôle le plus compatible entre les versions de Word.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Cas particulier :** Le contrôle Forms2.0 n'est visible que dans le *Mode Conception* de Word. Si vous avez besoin d'un bouton ActiveX plus récent, envisagez `insertOleControl()` à la place, mais le contrôle hérité fonctionne pour la plupart des scénarios d'automatisation.

## Étape 4 : Configurer les propriétés du bouton

Après avoir inséré le contrôle, vous pouvez **définir le nom du bouton de commande** et **insérer le texte du bouton de commande** (légende) pour le rendre convivial.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Pourquoi ces propriétés ?**  
> - `setName` attribue au bouton un identifiant que VBA ou des outils externes peuvent référencer.  
> - `setCaption` est l'étiquette visible, créant effectivement **le texte du bouton de formulaire** sur lequel les utilisateurs finaux cliquent.

Vous pouvez également ajuster la taille, la position, ou ajouter une macro en accédant à l'objet OLE sous-jacent, mais ces sujets dépassent le cadre de ce guide rapide.

## Étape 5 : Enregistrer le document modifié

Enfin, persistez les modifications dans un nouveau fichier. Cette étape **crée le texte du bouton de formulaire** dans le document de sortie.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Résultat :** En ouvrant `output.docx` dans Microsoft Word, vous verrez un bouton intitulé « Submit ». Lorsque vous passez Word en *Mode Conception* (Développeur → Mode Conception), vous pouvez double‑cliquer sur le bouton pour y attacher une macro ou simplement l'utiliser comme espace réservé dans un formulaire.

### Résultat attendu

Lorsque vous ouvrez le fichier enregistré :

- Le point d’insertion du curseur est remplacé par un bouton.
- Le bouton affiche la légende **Submit**.
- Le nom interne du bouton est **cmdSubmit**, que vous pouvez référencer dans VBA ou des scripts d'automatisation externes.

## Questions fréquentes et variantes

### Comment ajouter un bouton à un paragraphe spécifique ?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Comment insérer un bouton dans une cellule de tableau ?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Que faire si j’ai besoin d’un bouton plus grand ?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Comment **insérer le texte du bouton de commande** en utilisant un autre langage (par ex., C#) ?

La même logique s'applique ; remplacez la syntaxe Java par les équivalents C# :

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Astuces professionnelles et pièges

- **Astuce pro :** Appelez toujours `builder.moveToDocumentEnd()` avant d'insérer un bouton si vous le voulez à la toute fin du document.  
- **Attention :** Enregistrer dans le même fichier que celui ouvert peut corrompre le document en cas d'exception. Utilisez un chemin de sortie distinct comme indiqué.  
- **Compatibilité :** Le bouton Forms2.0 hérité fonctionne dans Word 2007‑2021. Pour Word sur le web, envisagez d'utiliser des contrôles de contenu à la place.  
- **Performance :** Charger des documents très volumineux (>100 Mo) peut consommer beaucoup de mémoire. Utilisez `Document.load(InputStream, LoadOptions)` avec `LoadOptions.setLoadFormat(LoadFormat.DOCX)` pour limiter l'utilisation des ressources.

## Exemple complet fonctionnel

Voici le programme Java complet, prêt à être exécuté. Copiez‑le dans une classe nommée `WordButtonDemo.java`, ajustez les chemins de fichiers, et exécutez `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Exécutez le programme et ouvrez `output.docx` pour vérifier que le bouton apparaît comme prévu.

## Conclusion

Vous savez maintenant comment **modifier un document Word programmé** pour **insérer le texte du bouton de commande**, **créer le texte du bouton de formulaire**, et **définir le nom du bouton de commande** en utilisant Aspose.Words for Java. Cette approche élimine la modification manuelle, permet le traitement par lots des formulaires, et s'intègre parfaitement aux flux de travail automatisés.

Ensuite, vous pourriez explorer :

- Ajouter des macros VBA au bouton (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Utiliser des **contrôles de contenu** pour des expériences de formulaire plus riches (`builder.insertCheckBox()` etc.)  
- Automatiser l'insertion massive à travers plusieurs documents avec une boucle  

N'hésitez pas à expérimenter la taille, la position et la gestion des événements du bouton pour l'adapter à votre scénario spécifique. Bon codage !

## Que devriez‑vous apprendre ensuite ?

Les tutoriels suivants couvrent des sujets étroitement liés qui s'appuient sur les techniques démontrées dans ce guide. Chaque ressource comprend des exemples de code complets et fonctionnels avec des explications étape par étape pour vous aider à maîtriser des fonctionnalités supplémentaires de l'API et explorer des approches d'implémentation alternatives dans vos propres projets.

- [Comment ajouter un bouton de commande programmé dans un document Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Créer un document Word programmé et ajouter un bouton ActiveX](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Ajouter un bouton de commande à un document Word avec Aspose.Words – Guide complet](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}