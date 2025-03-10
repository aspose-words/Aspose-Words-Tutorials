---
title: Insérer une table des matières dans un document Word
linktitle: Insérer une table des matières dans un document Word
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer une table des matières dans Word à l'aide d'Aspose.Words pour .NET. Suivez notre guide étape par étape pour une navigation fluide dans les documents.
weight: 10
url: /fr/net/add-content-using-documentbuilder/insert-table-of-contents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer une table des matières dans un document Word

## Introduction
Dans ce didacticiel, vous apprendrez à ajouter efficacement une table des matières (TOC) à vos documents Word à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité est essentielle pour organiser et parcourir de longs documents, améliorer la lisibilité et fournir un aperçu rapide des sections du document.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

- Compréhension de base de C# et du framework .NET.
- Visual Studio installé sur votre machine.
-  Bibliothèque Aspose.Words pour .NET. Si vous ne l'avez pas encore installée, vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/net/).

## Importer des espaces de noms

Pour commencer, importez les espaces de noms nécessaires dans votre projet C# :

```csharp
using Aspose.Words;
using Aspose.Words.Builder;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

Décomposons le processus en étapes claires :

## Étape 1 : Initialiser le document Aspose.Words et DocumentBuilder

 Tout d’abord, initialisez un nouveau Aspose.Words`Document` objet et un`DocumentBuilder` travailler avec:

```csharp
// Initialiser le document et DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : Insérer la table des matières

 Maintenant, insérez la table des matières à l'aide de la`InsertTableOfContents` méthode:

```csharp
// Insérer la table des matières
builder.InsertTableOfContents("\\o \"1-3\" \\h \\z \\u");
```

## Étape 3 : démarrer le contenu du document sur une nouvelle page

Pour garantir une mise en forme correcte, démarrez le contenu réel du document sur une nouvelle page :

```csharp
// Insérer un saut de page
builder.InsertBreak(BreakType.PageBreak);
```

## Étape 4 : Structurez votre document avec des titres

Organisez le contenu de votre document à l’aide de styles de titre appropriés :

```csharp
// Définir les styles de titre
builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 1.1");
builder.Writeln("Heading 1.2");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading1;
builder.Writeln("Heading 2");
builder.Writeln("Heading 3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.1");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading3;
builder.Writeln("Heading 3.1.1");
builder.Writeln("Heading 3.1.2");
builder.Writeln("Heading 3.1.3");

builder.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
builder.Writeln("Heading 3.2");
builder.Writeln("Heading 3.3");
```

## Étape 5 : Mettre à jour et remplir la table des matières

Mettre à jour la table des matières pour refléter la structure du document :

```csharp
// Mettre à jour les champs de la table des matières
doc.UpdateFields();
```

## Étape 6 : Enregistrer le document

Enfin, enregistrez votre document dans un répertoire spécifié :

```csharp
// Enregistrer le document
string dataDir = "YOUR_DOCUMENT_DIRECTORY_PATH";
doc.Save(dataDir + "InsertTableOfContentsUsingAsposeWords.docx");
```

## Conclusion

L'ajout d'une table des matières à l'aide d'Aspose.Words pour .NET est simple et améliore considérablement la convivialité de vos documents. En suivant ces étapes, vous pouvez organiser et parcourir efficacement des documents complexes.

## FAQ

### Puis-je personnaliser l’apparence de la table des matières ?
Oui, vous pouvez personnaliser l’apparence et le comportement de la table des matières à l’aide des API Aspose.Words pour .NET.

### Aspose.Words prend-il en charge la mise à jour automatique des champs ?
Oui, Aspose.Words vous permet de mettre à jour des champs tels que la table des matières de manière dynamique en fonction des modifications apportées au document.

### Puis-je générer plusieurs tables des matières dans un seul document ?
Aspose.Words prend en charge la génération de plusieurs tables des matières avec différents paramètres dans un seul document.

### Aspose.Words est-il compatible avec différentes versions de Microsoft Word ?
Oui, Aspose.Words assure la compatibilité avec différentes versions des formats Microsoft Word.

### Où puis-je trouver plus d'aide et de support pour Aspose.Words ?
 Pour plus d'assistance, visitez le[Forum Aspose.Words](https://forum.aspose.com/c/words/8) ou consultez le[documentation officielle](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
