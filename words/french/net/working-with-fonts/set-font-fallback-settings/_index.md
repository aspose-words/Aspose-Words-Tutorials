---
title: Définir les paramètres de secours des polices
linktitle: Définir les paramètres de secours des polices
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment configurer les paramètres de police de secours dans Aspose.Words pour .NET. Ce guide complet garantit que tous les caractères de vos documents s'affichent correctement.
weight: 10
url: /fr/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Définir les paramètres de secours des polices

## Introduction

Lorsque vous travaillez avec des documents contenant divers éléments de texte, tels que des langues différentes ou des caractères spéciaux, il est essentiel de s'assurer que ces éléments s'affichent correctement. Aspose.Words pour .NET propose une fonctionnalité puissante appelée Paramètres de remplacement des polices, qui permet de définir des règles de remplacement des polices lorsque la police d'origine ne prend pas en charge certains caractères. Dans ce guide, nous découvrirons comment configurer les paramètres de remplacement des polices à l'aide d'Aspose.Words pour .NET dans un didacticiel étape par étape.

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous de disposer des prérequis suivants :

- Connaissances de base de C# : Familiarité avec le langage de programmation C# et le framework .NET.
-  Aspose.Words pour .NET : téléchargez et installez à partir du[lien de téléchargement](https://releases.aspose.com/words/net/).
- Environnement de développement : une configuration comme Visual Studio pour écrire et exécuter votre code.
-  Exemple de document : Ayez un exemple de document (par exemple,`Rendering.docx`) prêt pour les tests.
- Règles de secours des polices XML : préparez un fichier XML définissant les règles de secours des polices.

## Importer des espaces de noms

Pour utiliser Aspose.Words, vous devez importer les espaces de noms nécessaires. Cela permet d'accéder à diverses classes et méthodes nécessaires au traitement des documents.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Étape 1 : Définir le répertoire des documents

Tout d'abord, définissez le répertoire où est stocké votre document. Ceci est essentiel pour localiser et traiter votre document.

```csharp
// Le chemin vers le répertoire des documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Charger le document

 Chargez votre document dans un Aspose.Words`Document` objet. Cette étape vous permet de travailler avec le document par programmation.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 3 : Configurer les paramètres de police

 Créer un nouveau`FontSettings` objet et chargez les paramètres de repli des polices à partir d'un fichier XML. Ce fichier XML contient les règles de repli des polices.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Étape 4 : appliquer les paramètres de police au document

 Affecter le configuré`FontSettings`au document. Cela garantit que les règles de repli des polices sont appliquées lors du rendu du document.

```csharp
doc.FontSettings = fontSettings;
```

## Étape 5 : Enregistrer le document

Enfin, enregistrez le document. Les paramètres de police de secours seront utilisés pendant l'opération d'enregistrement pour garantir une substitution de police appropriée.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## Fichier XML : règles de repli pour les polices

Voici un exemple de ce à quoi devrait ressembler votre fichier XML définissant les règles de secours des polices :

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Conclusion

En suivant ces étapes, vous pouvez configurer et utiliser efficacement les paramètres de police de secours dans Aspose.Words pour .NET. Cela garantit que vos documents affichent correctement tous les caractères, même si la police d'origine ne prend pas en charge certains caractères. La mise en œuvre de ces paramètres améliorera considérablement la qualité et la lisibilité de vos documents.

## FAQ

### Q1 : Qu'est-ce que Font Fallback ?

Font Fallback est une fonctionnalité qui permet la substitution de polices lorsque la police d'origine ne prend pas en charge certains caractères, garantissant ainsi un affichage correct de tous les éléments de texte.

### Q2 : Puis-je spécifier plusieurs polices de secours ?

Oui, vous pouvez spécifier plusieurs polices de secours dans les règles XML. Aspose.Words vérifiera chaque police dans l'ordre spécifié jusqu'à ce qu'il en trouve une qui prenne en charge le caractère.

### Q3 : Où puis-je télécharger Aspose.Words pour .NET ?

 Vous pouvez le télécharger à partir du[Page de téléchargement d'Aspose](https://releases.aspose.com/words/net/).

### Q4 : Comment créer le fichier XML pour les règles de secours des polices ?

Le fichier XML peut être créé à l'aide de n'importe quel éditeur de texte. Il doit suivre la structure illustrée dans l'exemple fourni dans ce tutoriel.

### Q5 : Existe-t-il un support disponible pour Aspose.Words ?

 Oui, vous pouvez trouver de l'aide sur le[Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
