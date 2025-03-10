---
title: Obtenir une substitution sans suffixes
linktitle: Obtenir une substitution sans suffixes
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment gérer la substitution de polices sans suffixes dans Aspose.Words pour .NET. Suivez notre guide étape par étape pour garantir que vos documents sont toujours parfaits.
weight: 10
url: /fr/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obtenir une substitution sans suffixes

## Introduction

Bienvenue dans ce guide complet sur la gestion de la substitution de polices à l'aide d'Aspose.Words pour .NET. Si vous avez déjà eu des problèmes avec des polices qui n'apparaissent pas correctement dans vos documents, vous êtes au bon endroit. Ce didacticiel vous guidera pas à pas dans la gestion efficace de la substitution de polices sans suffixes.

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous de disposer des éléments suivants :

- Connaissances de base de C# : comprendre la programmation C# facilitera le suivi et la mise en œuvre des étapes.
-  Bibliothèque Aspose.Words pour .NET : téléchargez et installez la bibliothèque à partir du[lien de téléchargement](https://releases.aspose.com/words/net/).
- Environnement de développement : configurez un environnement de développement comme Visual Studio pour écrire et exécuter votre code.
-  Exemple de document : Un exemple de document (par exemple,`Rendering.docx`) avec lesquels travailler pendant ce tutoriel.

## Importer des espaces de noms

Tout d’abord, nous devons importer les espaces de noms nécessaires pour accéder aux classes et méthodes fournies par Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Étape 1 : Définir le répertoire des documents

Pour commencer, spécifiez le répertoire dans lequel se trouve votre document. Cela vous aidera à localiser le document sur lequel vous souhaitez travailler.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Configurer le gestionnaire d'avertissement de substitution

Ensuite, nous devons configurer un gestionnaire d'avertissement qui nous avertira chaque fois qu'une substitution de police se produit pendant le traitement du document. Cela est essentiel pour détecter et gérer tout problème de police.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Étape 3 : ajouter des sources de polices personnalisées

Dans cette étape, nous allons ajouter des sources de polices personnalisées pour garantir qu'Aspose.Words puisse localiser et utiliser les polices appropriées. Cela est particulièrement utile si vous avez des polices spécifiques stockées dans des répertoires personnalisés.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

Dans ce code :
-  Nous récupérons les sources de polices actuelles et en ajoutons une nouvelle`FolderFontSource` pointant vers notre répertoire de polices personnalisées (`C:\\MyFonts\\`).
- Nous mettons ensuite à jour les sources de polices avec cette nouvelle liste.

## Étape 4 : Enregistrer le document

Enfin, enregistrez le document après avoir appliqué les paramètres de substitution de police. Pour ce tutoriel, nous l'enregistrerons au format PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Étape 5 : créer la classe de gestionnaire d’avertissements

 Pour gérer efficacement les avertissements, créez une classe personnalisée qui implémente le`IWarningCallback` interface. Cette classe capturera et enregistrera tous les avertissements de substitution de police.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

Dans cette classe :
-  Le`Warning`la méthode capture les avertissements liés à la substitution de police.
-  Le`FontWarnings` la collection stocke ces avertissements pour une inspection ou une journalisation ultérieure.

## Conclusion

Vous maîtrisez désormais le processus de gestion de la substitution de polices sans suffixes à l'aide d'Aspose.Words pour .NET. Ces connaissances garantiront que vos documents conservent l'apparence souhaitée, quelles que soient les polices disponibles sur le système. Continuez à expérimenter avec différents paramètres et sources pour exploiter pleinement la puissance d'Aspose.Words.

## FAQ

### Comment puis-je utiliser des polices provenant de plusieurs répertoires personnalisés ?

 Vous pouvez ajouter plusieurs`FolderFontSource` des cas à la`fontSources` répertoriez et mettez à jour les sources de polices en conséquence.

### Où puis-je télécharger un essai gratuit d'Aspose.Words pour .NET ?

 Vous pouvez télécharger une version d'essai gratuite à partir du[Page d'essai gratuite d'Aspose](https://releases.aspose.com/).

###  Puis-je gérer plusieurs types d’avertissements à l’aide de`IWarningCallback`?

 Oui, le`IWarningCallback` L'interface vous permet de gérer différents types d'avertissements, pas seulement la substitution de police.

### Où puis-je obtenir de l'aide pour Aspose.Words ?

 Pour obtenir de l'aide, visitez le[Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8).

### Est-il possible d'acheter une licence temporaire ?

 Oui, vous pouvez obtenir un permis temporaire auprès du[page de licence temporaire](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
