---
title: Définir les dossiers de polices Système et dossier personnalisé
linktitle: Définir les dossiers de polices Système et dossier personnalisé
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment définir des dossiers de polices système et personnalisés dans des documents Word à l'aide d'Aspose.Words pour .NET, en garantissant que vos documents s'affichent correctement dans différents environnements.
weight: 10
url: /fr/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir les dossiers de polices Système et dossier personnalisé

## Introduction

Imaginez que vous rédigez un document avec un style de police unique et que vous découvrez que les polices ne s'affichent pas correctement sur une autre machine. Frustrant, n'est-ce pas ? C'est là qu'entre en jeu la configuration des dossiers de polices. Avec Aspose.Words pour .NET, vous pouvez définir des dossiers de polices système et personnalisés pour garantir que vos documents s'affichent toujours comme prévu. Voyons comment vous pouvez y parvenir.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Bibliothèque Aspose.Words pour .NET : si vous ne l'avez pas déjà fait, téléchargez-la[ici](https://releases.aspose.com/words/net/).
- Environnement de développement : un IDE comme Visual Studio.
- Connaissances de base de C# : la familiarité avec C# vous aidera à suivre les exemples de code.

## Importer des espaces de noms

Tout d’abord, importez les espaces de noms nécessaires dans votre projet :

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Maintenant, décomposons le processus en étapes simples.

## Étape 1 : Charger le document

 Pour commencer, chargez votre document Word dans un fichier Aspose.Words`Document` objet. Ce document sera celui dans lequel vous souhaitez définir les dossiers de polices.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 2 : Initialiser les paramètres de police

 Créer une nouvelle instance de`FontSettings`. Cet objet vous permettra de gérer les sources de polices.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Étape 3 : Récupérer les sources des polices système

Récupérez les sources de polices système par défaut. Sur une machine Windows, cela inclut généralement le répertoire « Windows\Fonts »\" répertoire.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Étape 4 : ajouter un dossier de polices personnalisé

Ajoutez un dossier personnalisé contenant vos polices supplémentaires. Cela est utile si vous avez des polices spécifiques qui ne sont pas installées dans le répertoire des polices système.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Étape 5 : mettre à jour les sources de polices

 Convertissez la liste des sources de polices en un tableau et définissez-le sur`FontSettings` objet.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Étape 6 : Appliquer les paramètres de police au document

 Enfin, appliquez la configuration`FontSettings` dans votre document et enregistrez-le dans le format souhaité, tel que PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez vous assurer que vos documents Word utilisent les polices appropriées, qu'il s'agisse de polices système ou de polices personnalisées stockées dans un répertoire spécifique. Cette configuration permet de maintenir l'intégrité de l'apparence de votre document dans différents environnements.

## FAQ

### Que se passe-t-il si une police est manquante dans les dossiers système et personnalisés ?

Aspose.Words utilisera une police par défaut pour remplacer la police manquante, garantissant que le document reste lisible.

### Puis-je ajouter plusieurs dossiers de polices personnalisés ?

 Oui, vous pouvez ajouter plusieurs dossiers de polices personnalisés en répétant le processus de création`FolderFontSource` objets et les ajouter à la liste des sources de polices.

### Est-il possible d'utiliser des chemins réseau pour les dossiers de polices personnalisés ?

 Oui, vous pouvez spécifier un chemin réseau dans le`FolderFontSource` constructeur.

### Quels formats de fichiers Aspose.Words prend-il en charge pour l'enregistrement de documents ?

Aspose.Words prend en charge divers formats, notamment DOCX, PDF, HTML, etc.

### Comment gérer les notifications de substitution de police ?

 Vous pouvez gérer les notifications de substitution de police en utilisant le`FontSettings` classe`FontSubstitutionWarning`événement.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
