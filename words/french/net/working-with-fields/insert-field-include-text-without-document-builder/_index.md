---
title: Insérer un champ avec texte inclus sans générateur de documents
linktitle: Insérer FieldIncludeText sans Document Builder
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer un FieldIncludeText sans utiliser DocumentBuilder dans Aspose.Words pour .NET avec notre guide détaillé étape par étape.
weight: 10
url: /fr/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un champ avec texte inclus sans générateur de documents

## Introduction

Dans le monde de l'automatisation et de la manipulation de documents, Aspose.Words pour .NET est un outil puissant. Aujourd'hui, nous nous plongeons dans un guide détaillé sur la façon d'insérer un FieldIncludeText sans utiliser DocumentBuilder. Ce didacticiel vous guidera tout au long du processus, étape par étape, en vous assurant de comprendre chaque partie du code et son objectif.

## Prérequis

Avant de plonger dans le code, assurons-nous que vous disposez de tout ce dont vous avez besoin :

1.  Aspose.Words pour .NET : assurez-vous que la dernière version est installée. Vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement .NET : tout IDE compatible .NET comme Visual Studio.
3. Connaissances de base de C# : une connaissance de la programmation C# vous aidera à suivre.

## Importer des espaces de noms

Tout d’abord, nous devons importer les espaces de noms nécessaires. Ces espaces de noms donnent accès aux classes et méthodes nécessaires à la manipulation des documents Word.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

Décomposons maintenant l'exemple en plusieurs étapes. Chaque étape sera expliquée en détail pour plus de clarté.

## Étape 1 : définir le chemin du répertoire

La première étape consiste à définir le chemin d'accès à votre répertoire de documents. C'est là que vos documents Word seront stockés et accessibles.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Étape 2 : Créer le document et le paragraphe

Ensuite, nous créons un nouveau document et un paragraphe dans ce document. Ce paragraphe contiendra le champ FieldIncludeText.

```csharp
// Créez le document et le paragraphe.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## Étape 3 : Insérer le champ FieldIncludeText

Maintenant, nous insérons le champ FieldIncludeText dans le paragraphe. Ce champ vous permet d'inclure le texte d'un autre document.

```csharp
// Insérer le champ FieldIncludeText.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## Étape 4 : Définir les propriétés du champ

Nous devons spécifier les propriétés du champ FieldIncludeText. Cela inclut la définition du nom du signet et du chemin complet du document source.

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## Étape 5 : Ajouter un paragraphe au document

Une fois le champ configuré, nous ajoutons le paragraphe au corps de la première section du document.

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## Étape 6 : Mettre à jour le champ

Avant d’enregistrer le document, nous devons mettre à jour FieldIncludeText pour garantir qu’il récupère le contenu correct du document source.

```csharp
fieldIncludeText.Update();
```

## Étape 7 : Enregistrer le document

Enfin, nous enregistrons le document dans le répertoire spécifié.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement insérer un FieldIncludeText sans utiliser DocumentBuilder dans Aspose.Words pour .NET. Cette approche offre un moyen simplifié d'inclure du contenu d'un document dans un autre, ce qui simplifie considérablement vos tâches d'automatisation de documents.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?  
Aspose.Words for .NET est une bibliothèque puissante permettant de travailler avec des documents Word dans des applications .NET. Elle permet de créer, d'éditer et de convertir des documents par programmation.

### Pourquoi utiliser FieldIncludeText ?  
FieldIncludeText est utile pour inclure dynamiquement le contenu d'un document dans un autre, permettant ainsi des documents plus modulaires et plus faciles à gérer.

### Puis-je utiliser cette méthode pour inclure du texte provenant d’autres formats de fichiers ?  
FieldIncludeText fonctionne spécifiquement avec les documents Word. Pour d'autres formats, vous aurez peut-être besoin de méthodes ou de classes différentes fournies par Aspose.Words.

### Aspose.Words pour .NET est-il compatible avec .NET Core ?  
Oui, Aspose.Words pour .NET prend en charge .NET Framework, .NET Core et .NET 5/6.

### Comment puis-je obtenir un essai gratuit d'Aspose.Words pour .NET ?  
 Vous pouvez obtenir un essai gratuit à partir de[ici](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
