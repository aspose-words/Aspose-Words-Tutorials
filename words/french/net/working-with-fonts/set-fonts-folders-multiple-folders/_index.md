---
"description": "Apprenez à définir plusieurs dossiers de polices dans vos documents Word avec Aspose.Words pour .NET. Ce guide étape par étape vous garantit que vos documents utilisent exactement les polices dont vous avez besoin."
"linktitle": "Définir les dossiers de polices Plusieurs dossiers"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Définir les dossiers de polices Plusieurs dossiers"
"url": "/fr/net/working-with-fonts/set-fonts-folders-multiple-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Définir les dossiers de polices Plusieurs dossiers

## Introduction

Vous êtes-vous déjà demandé comment gérer plusieurs sources de polices dans vos documents Word ? Vous possédez peut-être une collection de polices dispersées dans différents dossiers et vous cherchez un moyen de garantir leur utilisation optimale dans vos documents. Eh bien, vous avez de la chance ! Aujourd'hui, nous vous expliquons comment configurer des dossiers de polices avec Aspose.Words pour .NET. Ce guide vous guidera pas à pas tout au long du processus pour que vos documents s'affichent parfaitement.

## Prérequis

Avant de commencer, assurez-vous que vous disposez de tout le nécessaire. Voici ce dont vous aurez besoin :

- Aspose.Words pour .NET : Si ce n'est pas déjà fait, téléchargez et installez Aspose.Words pour .NET. Vous pouvez l'obtenir. [ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Visual Studio ou tout autre environnement de développement compatible .NET.
- Connaissances de base de C# : une petite familiarité avec C# vous aidera à suivre les exemples.
- Fichiers de polices : assurez-vous que vos fichiers de polices sont stockés dans des répertoires auxquels vous pouvez facilement accéder.

## Importer des espaces de noms

Tout d'abord, importons les espaces de noms nécessaires dans votre projet C#. Cela vous permettra d'accéder à toutes les fonctionnalités d'Aspose.Words dont vous aurez besoin.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Avec cet ensemble, plongeons dans le guide étape par étape pour définir les dossiers de polices dans Aspose.Words pour .NET.

## Étape 1 : Chargez votre document

Commençons par charger le document Word que vous souhaitez utiliser. Assurez-vous d'avoir le chemin d'accès au document. Pour cet exemple, nous utiliserons un document nommé « Rendu.docx ».

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Ici, nous chargeons le document depuis le répertoire spécifié. C'est simple, non ?

## Étape 2 : Créer un objet FontSettings

Ensuite, nous devons créer un `FontSettings` objet. Cet objet nous permettra de gérer les sources de polices de notre document.

```csharp
FontSettings fontSettings = new FontSettings();
```

Ce `FontSettings` L'objet nous aidera à définir quels dossiers de polices utiliser.

## Étape 3 : Définir les dossiers de polices

Vient maintenant l'étape cruciale : la configuration des dossiers de polices. C'est ici que vous spécifiez les répertoires où se trouvent vos polices. Dans cet exemple, les polices se trouvent dans « C:\MyFonts » et « D:\Misc\Fonts ».

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

Le deuxième paramètre (`true`) indique que ces dossiers remplaceront les sources de polices par défaut. Si vous souhaitez également conserver les sources de polices système, vous pouvez utiliser une combinaison de `GetFontSources` et `SetFontSources`.

## Étape 4 : Appliquer les paramètres de police au document

Une fois les dossiers de polices définis, nous devons appliquer ces paramètres à notre document. Cela garantit que le document utilise les polices spécifiées lors du rendu.

```csharp
doc.FontSettings = fontSettings;
```

## Étape 5 : Enregistrer le document

Enfin, enregistrons le document. Nous l'enregistrerons au format PDF pour voir les polices en action.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

Et voilà ! Vous avez réussi à définir plusieurs dossiers de polices pour votre document.

## Conclusion

Gérer les polices de vos documents peut sembler complexe, mais avec Aspose.Words pour .NET, c'est un jeu d'enfant ! En suivant ces étapes simples, vous pouvez garantir un rendu professionnel à vos documents et utiliser les polices exactes dont vous avez besoin. Que vous travailliez sur un projet nécessitant une image de marque spécifique ou que vous souhaitiez simplement mieux contrôler l'apparence de votre document, la configuration des dossiers de polices est une compétence essentielle.

## FAQ

### Puis-je utiliser des chemins réseau pour les dossiers de polices ?
Oui, vous pouvez utiliser des chemins réseau pour vos dossiers de polices. Assurez-vous simplement que ces chemins sont accessibles depuis votre application.

### Que se passe-t-il si une police manque dans les dossiers spécifiés ?
Si une police est manquante, Aspose.Words reviendra à la police par défaut spécifiée ou utilisera une police de substitution.

### Puis-je ajouter des dossiers de polices sans remplacer les polices système ?
Absolument ! Utilisez `FontSettings.GetFontSources` pour récupérer des sources existantes et les combiner avec vos dossiers personnalisés en utilisant `FontSettings.SetFontSources`.

### Existe-t-il une limite au nombre de dossiers de polices que je peux ajouter ?
Il n'y a pas de limite stricte au nombre de dossiers de polices. Cependant, soyez attentif aux performances, car un nombre plus élevé de dossiers peut augmenter le temps de chargement des polices.

### Comment puis-je vérifier quelles polices sont utilisées dans mon document ?
Vous pouvez utiliser le `FontSettings.GetFontsSources` méthode pour récupérer et inspecter les sources de polices actuellement définies pour votre document.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}