---
title: Exporter les signets d'en-tête, de pied de page et de document Word vers un document PDF
linktitle: Exporter les signets d'en-tête, de pied de page et de document Word vers un document PDF
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment exporter des signets d'en-tête et de pied de page d'un document Word vers PDF à l'aide d'Aspose.Words pour .NET avec notre guide étape par étape.
weight: 10
url: /fr/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exporter les signets d'en-tête, de pied de page et de document Word vers un document PDF

## Introduction

La conversion de documents Word en PDF est une tâche courante, en particulier lorsque vous souhaitez partager ou archiver des documents tout en préservant leur mise en forme. Parfois, ces documents contiennent des signets importants dans les en-têtes et les pieds de page. Dans ce didacticiel, nous allons parcourir le processus d'exportation de ces signets d'un document Word vers un PDF à l'aide d'Aspose.Words pour .NET.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

- Aspose.Words pour .NET : vous devez avoir installé Aspose.Words pour .NET. Vous pouvez le télécharger à partir de[ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Configurez votre environnement de développement. Vous pouvez utiliser Visual Studio ou tout autre IDE compatible .NET.
- Connaissances de base de C# : une familiarité avec la programmation C# est requise pour suivre les exemples de code.

## Importer des espaces de noms

Tout d’abord, vous devez importer les espaces de noms nécessaires dans votre projet C#. Ajoutez ces lignes en haut de votre fichier de code :

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Décomposons le processus en étapes faciles à suivre.

## Étape 1 : Initialiser le document

La première étape consiste à charger votre document Word. Voici comment procéder :

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

Dans cette étape, vous spécifiez simplement le chemin d’accès à votre répertoire de documents et chargez le document Word.

## Étape 2 : Configurer les options d’enregistrement PDF

Ensuite, vous devez configurer les options d’enregistrement PDF pour garantir que les signets dans les en-têtes et les pieds de page sont exportés correctement.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Ici, nous mettons en place le`PdfSaveOptions` . Le`DefaultBookmarksOutlineLevel` La propriété définit le niveau de contour des signets et le`HeaderFooterBookmarksExportMode` la propriété garantit que seule la première occurrence des signets dans les en-têtes et les pieds de page est exportée.

## Étape 3 : Enregistrer le document au format PDF

Enfin, enregistrez votre document au format PDF avec les options configurées.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

Dans cette étape, vous enregistrez le document dans le chemin spécifié avec les options que vous avez configurées.

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement exporter les signets des en-têtes et pieds de page d'un document Word vers un PDF à l'aide d'Aspose.Words pour .NET. Cette méthode garantit que les aides à la navigation importantes dans votre document sont conservées au format PDF, ce qui permet aux lecteurs de naviguer plus facilement dans votre document.

## FAQ

### Puis-je exporter tous les signets du document Word vers PDF ?

 Oui, vous pouvez. Dans le`PdfSaveOptions`, vous pouvez ajuster les paramètres pour inclure tous les signets si nécessaire.

### Que faire si je souhaite également exporter les signets du corps du document ?

 Vous pouvez configurer le`OutlineOptions` dans`PdfSaveOptions` pour inclure les signets du corps du document.

### Est-il possible de personnaliser les niveaux de signets dans le PDF ?

 Absolument ! Vous pouvez personnaliser le`DefaultBookmarksOutlineLevel` propriété permettant de définir différents niveaux de contour pour vos signets.

### Comment gérer les documents sans signets ?

Si votre document ne contient pas de signets, le PDF sera généré sans aucun signet. Assurez-vous que votre document contient des signets si vous en avez besoin dans le PDF.

### Puis-je utiliser cette méthode pour d’autres types de documents comme DOCX ou RTF ?

Oui, Aspose.Words pour .NET prend en charge différents types de documents, notamment DOCX, RTF et autres.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
