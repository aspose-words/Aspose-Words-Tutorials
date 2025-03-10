---
title: Définir la position des notes de bas de page et de fin de note
linktitle: Définir la position des notes de bas de page et de fin
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment définir les positions des notes de bas de page et de fin dans les documents Word à l'aide d'Aspose.Words pour .NET avec ce guide détaillé étape par étape.
weight: 10
url: /fr/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir la position des notes de bas de page et de fin de note

## Introduction

Si vous travaillez avec des documents Word et que vous devez gérer efficacement les notes de bas de page et les notes de fin, Aspose.Words pour .NET est la bibliothèque qu'il vous faut. Ce didacticiel vous guidera dans la définition des positions des notes de bas de page et des notes de fin dans un document Word à l'aide d'Aspose.Words pour .NET. Nous décomposerons chaque étape pour la rendre facile à suivre et à mettre en œuvre.

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous de disposer des éléments suivants :

-  Bibliothèque Aspose.Words pour .NET : vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/net/).
- Visual Studio : toute version récente fonctionnera correctement.
- Connaissances de base de C# : comprendre les bases vous aidera à suivre facilement.

## Importer des espaces de noms

Tout d’abord, importez les espaces de noms nécessaires dans votre projet C# :

```csharp
using System;
using Aspose.Words;
```

## Étape 1 : Charger le document Word

Pour commencer, vous devez charger votre document Word dans l'objet Document Aspose.Words. Cela vous permettra de manipuler le contenu du document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Dans ce code, remplacez`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel où se trouve votre document.

## Étape 2 : définir la position de la note de bas de page

Ensuite, vous définirez la position des notes de bas de page. Aspose.Words pour .NET vous permet de positionner les notes de bas de page soit en bas de la page, soit sous le texte.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

 Ici, nous avons configuré les notes de bas de page pour qu'elles apparaissent sous le texte. Si vous les préférez en bas de la page, utilisez`FootnotePosition.BottomOfPage`.

## Étape 3 : définir la position de la note de fin

De la même manière, vous pouvez définir la position des notes de fin. Les notes de fin peuvent être positionnées soit à la fin de la section, soit à la fin du document.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

 Dans cet exemple, les notes de fin sont placées à la fin de chaque section. Pour les placer à la fin du document, utilisez`EndnotePosition.EndOfDocument`.

## Étape 4 : Enregistrer le document

Enfin, enregistrez le document pour appliquer les modifications. Assurez-vous de spécifier le chemin d'accès et le nom corrects pour le document de sortie.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Cette ligne enregistre le document modifié dans le répertoire spécifié.

## Conclusion

Définir la position des notes de bas de page et de fin de document dans les documents Word à l'aide d'Aspose.Words pour .NET est simple une fois que vous connaissez les étapes. En suivant ce guide, vous pouvez personnaliser vos documents en fonction de vos besoins, en vous assurant que les notes de bas de page et de fin de document sont positionnées exactement là où vous le souhaitez.

## FAQ

### Puis-je définir des positions différentes pour des notes de bas de page ou des notes de fin individuelles ?

Non, Aspose.Words pour .NET définit la position de toutes les notes de bas de page et de fin d'un document de manière uniforme.

### Aspose.Words pour .NET est-il compatible avec toutes les versions de documents Word ?

Oui, Aspose.Words pour .NET prend en charge une large gamme de formats de documents Word, notamment DOC, DOCX, RTF, etc.

### Puis-je utiliser Aspose.Words pour .NET avec d’autres langages de programmation ?

Aspose.Words pour .NET est conçu pour les applications .NET, mais vous pouvez l'utiliser avec n'importe quel langage pris en charge par .NET comme C#, VB.NET, etc.

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?

 Oui, vous pouvez obtenir un essai gratuit[ici](https://releases.aspose.com/).

### Où puis-je trouver une documentation plus détaillée sur Aspose.Words pour .NET ?

 Une documentation détaillée est disponible[ici](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
