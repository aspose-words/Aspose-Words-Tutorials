---
"description": "Apprenez à gérer la substitution de polices sans suffixes dans Aspose.Words pour .NET. Suivez notre guide étape par étape pour garantir des documents impeccables à chaque fois."
"linktitle": "Obtenir une substitution sans suffixes"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Obtenir une substitution sans suffixes"
"url": "/fr/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Obtenir une substitution sans suffixes

## Introduction

Bienvenue dans ce guide complet sur la gestion de la substitution de polices avec Aspose.Words pour .NET. Si vous avez déjà rencontré des problèmes d'affichage de polices dans vos documents, vous êtes au bon endroit. Ce tutoriel vous guidera étape par étape pour gérer efficacement la substitution de polices sans suffixes.

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous de disposer des éléments suivants :

- Connaissances de base de C# : comprendre la programmation C# facilitera le suivi et la mise en œuvre des étapes.
- Bibliothèque Aspose.Words pour .NET : téléchargez et installez la bibliothèque à partir du [lien de téléchargement](https://releases.aspose.com/words/net/).
- Environnement de développement : configurez un environnement de développement tel que Visual Studio pour écrire et exécuter votre code.
- Exemple de document : Un exemple de document (par exemple, `Rendering.docx`) avec lesquels travailler pendant ce tutoriel.

## Importer des espaces de noms

Tout d’abord, nous devons importer les espaces de noms nécessaires pour accéder aux classes et méthodes fournies par Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Étape 1 : Définir le répertoire des documents

Pour commencer, indiquez le répertoire où se trouve votre document. Cela vous aidera à localiser le document sur lequel vous souhaitez travailler.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Configurer le gestionnaire d'avertissement de substitution

Ensuite, nous devons configurer un gestionnaire d'avertissement qui nous avertira en cas de substitution de police lors du traitement du document. Ceci est essentiel pour détecter et gérer tout problème de police.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Étape 3 : Ajouter des sources de polices personnalisées

Dans cette étape, nous ajouterons des sources de polices personnalisées afin qu'Aspose.Words puisse localiser et utiliser les polices appropriées. Ceci est particulièrement utile si vous avez des polices spécifiques stockées dans des répertoires personnalisés.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

Dans ce code :
- Nous récupérons les sources de polices actuelles et en ajoutons une nouvelle `FolderFontSource` pointant vers notre répertoire de polices personnalisées (`C:\\MyFonts\\`).
- Nous mettons ensuite à jour les sources de polices avec cette nouvelle liste.

## Étape 4 : Enregistrer le document

Enfin, enregistrez le document après avoir appliqué les paramètres de substitution de police. Pour ce tutoriel, nous l'enregistrerons au format PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Étape 5 : Créer la classe de gestionnaire d'avertissements

Pour gérer efficacement les avertissements, créez une classe personnalisée qui implémente le `IWarningCallback` interface. Cette classe capturera et enregistrera tous les avertissements de substitution de police.

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
- Le `Warning` la méthode capture les avertissements liés à la substitution de police.
- Le `FontWarnings` la collection stocke ces avertissements pour une inspection ou une journalisation ultérieure.

## Conclusion

Vous maîtrisez désormais la gestion de la substitution de polices sans suffixes avec Aspose.Words pour .NET. Grâce à ces connaissances, vos documents conserveront l'apparence souhaitée, quelles que soient les polices disponibles sur le système. Continuez à expérimenter avec différents paramètres et sources pour exploiter pleinement la puissance d'Aspose.Words.

## FAQ

### Comment puis-je utiliser des polices provenant de plusieurs répertoires personnalisés ?

Vous pouvez ajouter plusieurs `FolderFontSource` instances à la `fontSources` répertoriez et mettez à jour les sources de polices en conséquence.

### Où puis-je télécharger une version d'essai gratuite d'Aspose.Words pour .NET ?

Vous pouvez télécharger une version d'essai gratuite à partir du [Page d'essai gratuite d'Aspose](https://releases.aspose.com/).

### Puis-je gérer plusieurs types d’avertissements à l’aide de `IWarningCallback`?

Oui, le `IWarningCallback` L'interface vous permet de gérer différents types d'avertissements, pas seulement la substitution de police.

### Où puis-je obtenir de l'aide pour Aspose.Words ?

Pour obtenir de l'aide, visitez le [Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8).

### Est-il possible d'acheter une licence temporaire ?

Oui, vous pouvez obtenir un permis temporaire auprès du [page de licence temporaire](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}