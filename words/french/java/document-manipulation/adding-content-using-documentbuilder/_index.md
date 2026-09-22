---
date: 2026-01-01
description: Apprenez à créer des champs de formulaire et à ajouter du texte, des
  tableaux, des images, des hyperliens et plus encore en utilisant Aspose.Words for
  Java DocumentBuilder. Un guide étape par étape pour les développeurs.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Comment créer des champs de formulaire et ajouter du contenu à l'aide de DocumentBuilder
  dans Aspose.Words pour Java
url: /fr/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ajouter du contenu avec DocumentBuilder dans Aspose.Words pour Java

## Introduction à l’ajout de contenu avec DocumentBuilder dans Aspose.Words pour Java

Dans ce guide étape par étape, vous allez **créer des champs de formulaire** et ajouter une variété de contenus — texte, tableaux, règles horizontales, HTML, hyperliens, images, et plus encore — dans un document Word avec Aspose.Words pour Java. Que vous construisiez un rapport, un modèle de contrat ou un formulaire interactif, la classe `DocumentBuilder` vous offre un contrôle granulaire sur chaque élément. Plongeons‑y !

## Réponses rapides
- **Comment créer des champs de formulaire ?** Utilisez `insertTextInput`, `insertCheckBox` ou `insertComboBox` sur un `DocumentBuilder`.
- **Quelle méthode ajoute du texte brut ?** Appelez `builder.write("Your text")` ou `builder.writeln("Your text")`.
- **Puis‑je insérer une règle horizontale ?** Oui — `builder.insertHorizontalRule()` ajoute un séparateur de ligne.
- **Comment intégrer du HTML ?** Utilisez `builder.insertHtml("<p>HTML content</p>")`.
- **Comment ajouter une image en ligne ?** `builder.insertImage("path/to/image.png")` place l’image dans le flux de texte.

## Qu’est‑ce que DocumentBuilder et pourquoi l’utiliser pour créer des champs de formulaire ?

`DocumentBuilder` est l’API fluide d’Aspose.Words pour construire et modifier des documents Word de façon programmatique. Elle masque la structure bas‑niveau OpenXML, vous permettant de vous concentrer sur *ce que* vous voulez ajouter—comme les **champs de formulaire**—au lieu de *comment* le XML apparaît. Cela le rend idéal pour générer des formulaires dynamiques, des contrats ou tout document nécessitant une interaction utilisateur.

## Prérequis

Avant de commencer, assurez‑vous d’avoir la bibliothèque Aspose.Words pour Java installée dans votre projet. Vous pouvez la télécharger [ici](https://releases.aspose.com/words/java/).

## Ajout de texte (how to add text)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Ajout de tableaux

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Ajout d’une règle horizontale (add horizontal rule)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Ajout de champs de formulaire (create form fields)

### Champ de texte

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Case à cocher

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Liste déroulante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Insertion de HTML (insert html word)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Insertion d’hyperliens (how to add hyperlink)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Ajout d’une table des matières

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Ajout d’images

### Image en ligne (insert inline image)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Image flottante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Ajout de paragraphes

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Déplacement du curseur (Step 10)

Vous pouvez contrôler la position du curseur dans le document à l’aide de méthodes comme `moveToParagraph`, `moveToCell`, etc.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Voici quelques opérations courantes que vous pouvez réaliser avec le `DocumentBuilder` d’Aspose.Words pour Java. Explorez la documentation de la bibliothèque pour des fonctionnalités avancées et des options de personnalisation. Bonne création de documents !

## Conclusion

Dans ce guide complet, nous avons montré comment **créer des champs de formulaire** et ajouter divers types de contenu — texte, tableaux, règles horizontales, HTML, hyperliens, table des matières, images, paragraphes formatés et navigation du curseur—en utilisant le `DocumentBuilder` d’Aspose.Words pour Java. Vous disposez maintenant d’une base solide pour générer des documents Word dynamiques et interactifs de façon programmatique.

## FAQ

### Q : Qu’est‑ce qu’Aspose.Words pour Java ?

R : Aspose.Words pour Java est une bibliothèque Java qui permet aux développeurs de créer, modifier et manipuler des documents Microsoft Word de façon programmatique. Elle offre un large éventail de fonctionnalités pour la génération de documents, le formatage et l’insertion de contenu.

### Q : Comment ajouter une table des matières à mon document ?

R : Pour ajouter une table des matières, utilisez le `DocumentBuilder` pour insérer un champ TOC, puis appelez `doc.updateFields()` après avoir ajouté votre contenu.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q : Comment insérer des images dans un document avec Aspose.Words pour Java ?

R : Vous pouvez insérer des images, en ligne ou flottantes, en utilisant le `DocumentBuilder`.

#### Image en ligne :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Image flottante :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q : Puis‑je formater le texte et les paragraphes lors de l’ajout de contenu ?

R : Oui, vous pouvez formater le texte et les paragraphes avec le `DocumentBuilder`. Définissez les propriétés de police, l’alignement des paragraphes, l’indentation, etc., avant d’écrire le contenu.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q : Comment déplacer le curseur à un emplacement précis dans le document ?

R : Utilisez des méthodes telles que `moveToParagraph`, `moveToCell`, etc., pour positionner le curseur avant d’insérer du nouveau contenu.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Ces réponses couvrent les scénarios les plus courants lors de l’utilisation du `DocumentBuilder` d’Aspose.Words pour Java. Pour plus de détails, consultez la [documentation de la bibliothèque](https://reference.aspose.com/words/java/) ou rejoignez la communauté Aspose.Words pour obtenir de l’aide.

---

**Dernière mise à jour :** 2026-01-01  
**Testé avec :** Aspose.Words pour Java 24.12  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}