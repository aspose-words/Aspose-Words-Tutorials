---
title: Ajout de contenu à l'aide de DocumentBuilder dans Aspose.Words pour Java
linktitle: Ajout de contenu à l'aide de DocumentBuilder
second_title: API de traitement de documents Java Aspose.Words
description: Maîtrisez la création de documents avec Aspose.Words pour Java. Un guide étape par étape pour ajouter du texte, des tableaux, des images et plus encore. Créez de superbes documents Word sans effort.
weight: 26
url: /fr/java/document-manipulation/adding-content-using-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ajout de contenu à l'aide de DocumentBuilder dans Aspose.Words pour Java


## Introduction à l'ajout de contenu à l'aide de DocumentBuilder dans Aspose.Words pour Java

Dans ce guide étape par étape, nous allons découvrir comment utiliser Aspose.Words pour DocumentBuilder de Java pour ajouter différents types de contenu à un document Word. Nous aborderons l'insertion de texte, de tableaux, de règles horizontales, de champs de formulaire, de HTML, d'hyperliens, de tables des matières, d'images en ligne et flottantes, de paragraphes, etc. Commençons !

## Prérequis

 Avant de commencer, assurez-vous que la bibliothèque Aspose.Words pour Java est configurée dans votre projet. Vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/java/).

## Ajout de texte

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer un paragraphe de texte simple
builder.write("This is a simple text paragraph.");

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Ajout de tableaux

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

//Démarrer une table
Table table = builder.startTable();

// Insérer des cellules et du contenu
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// Finir la table
builder.endTable();

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Ajout d'une règle horizontale

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer une règle horizontale
builder.insertHorizontalRule();

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Ajout de champs de formulaire

### Champ de saisie de texte

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer un champ de saisie de texte
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

### Champ de formulaire de case à cocher

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer un champ de formulaire de case à cocher
builder.insertCheckBox("CheckBox", true, true, 0);

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

### Champ de formulaire de zone de liste déroulante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Définir les éléments de la zone de liste déroulante
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insérer un champ de formulaire de zone de liste déroulante
builder.insertComboBox("DropDown", items, 0);

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Ajout de HTML

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer du contenu HTML
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Ajout d'hyperliens

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer un lien hypertexte
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", faux);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Ajout d'une table des matières

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer une table des matières
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Ajouter du contenu au document
// ...

// Mettre à jour la table des matières
doc.updateFields();

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Ajout d'images

### Image en ligne

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer une image en ligne
builder.insertImage("path/to/your/image.png");

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

### Image flottante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer une image flottante
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Ajout de paragraphes

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Définir la mise en forme des paragraphes
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

// Insérer un paragraphe
builder.writeln("This is a formatted paragraph.");

// Enregistrer le document
doc.save("path/to/your/document.docx");
```

## Étape 10 : Déplacer le curseur

 Vous pouvez contrôler la position du curseur dans le document à l'aide de diverses méthodes telles que`moveToParagraph`, `moveToCell`et plus encore. Voici un exemple :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Déplacer le curseur vers un paragraphe spécifique
builder.moveToParagraph(2, 0);

// Ajouter du contenu à la nouvelle position du curseur
builder.writeln("This is the 3rd paragraph.");
```

Voici quelques opérations courantes que vous pouvez effectuer à l'aide d'Aspose.Words pour DocumentBuilder de Java. Explorez la documentation de la bibliothèque pour découvrir des fonctionnalités plus avancées et des options de personnalisation. Bonne création de documents !


## Conclusion

Dans ce guide complet, nous avons exploré les capacités d'Aspose.Words pour DocumentBuilder de Java pour ajouter différents types de contenu aux documents Word. Nous avons abordé le texte, les tableaux, les règles horizontales, les champs de formulaire, le HTML, les hyperliens, la table des matières, les images, les paragraphes et le mouvement du curseur.

## FAQ

### Q : Qu'est-ce qu'Aspose.Words pour Java ?

R : Aspose.Words for Java est une bibliothèque Java qui permet aux développeurs de créer, modifier et manipuler des documents Microsoft Word par programmation. Elle offre une large gamme de fonctionnalités pour la génération de documents, la mise en forme et l'insertion de contenu.

### Q : Comment puis-je ajouter une table des matières à mon document ?

 : Pour ajouter une table des matières, utilisez le`DocumentBuilder` pour insérer un champ de table des matières dans votre document. Assurez-vous de mettre à jour les champs du document après avoir ajouté du contenu pour remplir la table des matières. Voici un exemple :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer un champ de table des matières
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Ajouter du contenu au document
// ...

// Mettre à jour la table des matières
doc.updateFields();
```

### Q : Comment insérer des images dans un document à l’aide d’Aspose.Words pour Java ?

 R : Vous pouvez insérer des images, en ligne et flottantes, à l'aide de l'`DocumentBuilder`Voici des exemples des deux :

#### Image en ligne :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer une image en ligne
builder.insertImage("path/to/your/image.png");
```

#### Image flottante :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insérer une image flottante
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q : Puis-je formater du texte et des paragraphes lors de l’ajout de contenu ?

 R : Oui, vous pouvez formater du texte et des paragraphes à l'aide de l'`DocumentBuilder`. Vous pouvez définir les propriétés de police, l'alignement des paragraphes, l'indentation, etc. Voici un exemple :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Définir la police et la mise en forme des paragraphes
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

// Insérer un paragraphe formaté
builder.writeln("This is a formatted paragraph.");
```

### Q : Comment puis-je déplacer le curseur vers un emplacement spécifique dans le document ?

 R : Vous pouvez contrôler la position du curseur à l’aide de méthodes telles que`moveToParagraph`, `moveToCell`et plus encore. Voici un exemple :

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Déplacer le curseur vers un paragraphe spécifique
builder.moveToParagraph(2, 0);

// Ajouter du contenu à la nouvelle position du curseur
builder.writeln("This is the 3rd paragraph.");
```

Voici quelques questions et réponses courantes pour vous aider à démarrer avec Aspose.Words pour DocumentBuilder de Java. Si vous avez d'autres questions ou si vous avez besoin d'aide supplémentaire, reportez-vous à la[documentation de la bibliothèque](https://reference.aspose.com/words/java/) ou demandez de l'aide à la communauté Aspose.Words et aux ressources d'assistance.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
