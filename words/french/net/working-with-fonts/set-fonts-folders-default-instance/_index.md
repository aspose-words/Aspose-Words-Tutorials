---
title: Définir l'instance par défaut des dossiers de polices
linktitle: Définir l'instance par défaut des dossiers de polices
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment définir des dossiers de polices pour l'instance par défaut dans Aspose.Words pour .NET avec ce didacticiel étape par étape. Personnalisez vos documents Word sans effort.
weight: 10
url: /fr/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir l'instance par défaut des dossiers de polices

## Introduction

Bonjour à tous les codeurs ! Si vous travaillez avec des documents Word dans .NET, vous savez probablement à quel point il est important d'avoir des polices de caractères parfaitement adaptées. Aujourd'hui, nous allons découvrir comment définir des dossiers de polices pour l'instance par défaut à l'aide d'Aspose.Words pour .NET. Imaginez avoir toutes vos polices personnalisées à portée de main, ce qui permet à vos documents d'avoir exactement l'apparence que vous souhaitez. Cela semble génial, n'est-ce pas ? Commençons !

## Prérequis

Avant de plonger dans les détails, assurons-nous que vous disposez de tout ce dont vous avez besoin :
-  Aspose.Words pour .NET : assurez-vous que la bibliothèque est installée. Sinon, vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Visual Studio ou tout autre IDE compatible .NET.
- Connaissances de base de C# : vous devez être à l’aise avec la programmation C#.
- Dossier Polices : un répertoire contenant vos polices personnalisées.

## Importer des espaces de noms

Tout d'abord, importons les espaces de noms nécessaires. Cela permet d'accéder aux classes et méthodes requises pour définir le dossier des polices.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Décomposons le processus en étapes simples et digestes.

## Étape 1 : Définir le répertoire de données

Tout grand voyage commence par une seule étape, et la nôtre commence par la définition du répertoire dans lequel votre document est stocké. C'est là qu'Aspose.Words recherchera votre document Word.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ici, remplacez`"YOUR DOCUMENT DIRECTORY"` avec le chemin d'accès réel vers votre répertoire de documents. C'est là que se trouve votre document source et où la sortie sera enregistrée.

## Étape 2 : définir le dossier des polices

 Maintenant, indiquons à Aspose.Words où trouver vos polices personnalisées. Pour cela, définissez le dossier des polices à l'aide de l'`FontSettings.DefaultInstance.SetFontsFolder` méthode.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 Dans cette ligne,`"C:\\MyFonts\\"` est le chemin d'accès à votre dossier de polices personnalisées. Le deuxième paramètre,`true`, indique que les polices de ce dossier doivent être analysées de manière récursive.

## Étape 3 : Chargez votre document

 Une fois le dossier des polices défini, l'étape suivante consiste à charger votre document Word dans Aspose.Words. Cela se fait à l'aide de`Document` classe.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Ici,`dataDir + "Rendering.docx"` fait référence au chemin complet de votre document Word. Assurez-vous que votre document se trouve dans le répertoire spécifié.

## Étape 4 : Enregistrer le document

La dernière étape consiste à enregistrer votre document après avoir défini le dossier des polices. Cela garantit que vos polices personnalisées sont correctement appliquées dans la sortie.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Cette ligne enregistre votre document au format PDF avec les polices personnalisées appliquées. Le fichier de sortie sera situé dans le même répertoire que votre document source.

## Conclusion

Et voilà ! La configuration des dossiers de polices pour l'instance par défaut dans Aspose.Words pour .NET est un jeu d'enfant lorsque vous la décomposez en étapes simples. En suivant ce guide, vous pouvez vous assurer que vos documents Word s'affichent exactement comme vous le souhaitez, avec toutes vos polices personnalisées en place. Alors allez-y, essayez-le et faites briller vos documents !

## FAQ

### Puis-je définir plusieurs dossiers de polices ?
 Oui, vous pouvez définir plusieurs dossiers de polices en utilisant le`SetFontsFolders` méthode qui accepte un tableau de chemins de dossiers.

### Quels formats de fichiers Aspose.Words prend-il en charge pour l'enregistrement de documents ?
Aspose.Words prend en charge divers formats, notamment DOCX, PDF, HTML, EPUB, etc.

### Est-il possible d'utiliser des polices en ligne dans Aspose.Words ?
Non, Aspose.Words ne prend actuellement en charge que les fichiers de polices locaux.

### Comment puis-je m’assurer que mes polices personnalisées sont intégrées dans le PDF enregistré ?
 En définissant le`FontSettings` correctement et en s'assurant que les polices sont disponibles, Aspose.Words les intégrera dans la sortie PDF.

### Que se passe-t-il si une police n'est pas trouvée dans le dossier spécifié ?
Aspose.Words utilisera une police de secours si la police spécifiée n'est pas trouvée.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
