---
title: Ressources d'exportation
linktitle: Ressources d'exportation
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment exporter des ressources telles que des feuilles de style CSS et des polices tout en enregistrant des documents Word au format HTML à l'aide d'Aspose.Words pour .NET. Suivez notre guide étape par étape.
weight: 10
url: /fr/net/programming-with-htmlsaveoptions/export-resources/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ressources d'exportation

## Introduction

Bonjour à tous les passionnés de technologie ! Si vous avez déjà eu besoin de convertir des documents Word en HTML, vous êtes au bon endroit. Aujourd'hui, nous plongeons dans le monde merveilleux d'Aspose.Words pour .NET. Cette puissante bibliothèque facilite le travail avec les documents Word par programmation. Dans ce didacticiel, nous allons parcourir les étapes à suivre pour exporter des ressources, telles que des polices et du CSS, lors de l'enregistrement d'un document Word au format HTML à l'aide d'Aspose.Words pour .NET. Attachez vos ceintures pour une aventure amusante et informative !

## Prérequis

Avant de nous plonger dans le code, assurons-nous que vous disposez de tout ce dont vous avez besoin pour commencer. Voici une liste de contrôle rapide :

1.  Visual Studio : Assurez-vous que Visual Studio est installé sur votre ordinateur. Vous pouvez le télécharger à partir du[Site Web de Visual Studio](https://visualstudio.microsoft.com/).
2.  Aspose.Words pour .NET : vous aurez besoin de la bibliothèque Aspose.Words pour .NET. Si vous ne l'avez pas encore, téléchargez une version d'essai gratuite sur[Sorties d'Aspose](https://releases.aspose.com/words/net/) ou l'acheter auprès du[Boutique Aspose](https://purchase.aspose.com/buy).
3. Connaissances de base de C# : une compréhension fondamentale de C# vous aidera à suivre les exemples de code.

Vous avez tout compris ? Super ! Passons à l'importation des espaces de noms nécessaires.

## Importer des espaces de noms

Pour utiliser Aspose.Words pour .NET, vous devez inclure les espaces de noms pertinents dans votre projet. Voici comment procéder :

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ces espaces de noms sont essentiels pour accéder aux classes et méthodes Aspose.Words que nous utiliserons dans notre didacticiel.

Décomposons le processus d'exportation de ressources lors de l'enregistrement d'un document Word au format HTML. Nous procéderons étape par étape, afin qu'il soit facile à suivre.

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, vous devez spécifier le chemin d'accès à votre répertoire de documents. C'est là que se trouve votre document Word et où le fichier HTML sera enregistré.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin réel vers votre répertoire.

## Étape 2 : Charger le document Word

 Ensuite, chargeons le document Word que vous souhaitez convertir en HTML. Pour ce tutoriel, nous utiliserons un document nommé`Rendering.docx`.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Cette ligne de code charge le document à partir du répertoire spécifié.

## Étape 3 : Configurer les options d’enregistrement HTML

Pour exporter des ressources telles que CSS et des polices, vous devez configurer le`HtmlSaveOptions`. Cette étape est cruciale pour garantir que votre sortie HTML est bien structurée et inclut les ressources nécessaires.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External,
    ExportFontResources = true,
    ResourceFolder = dataDir + "Resources",
    ResourceFolderAlias = "http://exemple.com/resources"
};
```

Décomposons ce que fait chaque option :
- `CssStyleSheetType = CssStyleSheetType.External`: Cette option spécifie que les styles CSS doivent être enregistrés dans une feuille de style externe.
- `ExportFontResources = true`:Cela permet l'exportation de ressources de polices.
- `ResourceFolder = dataDir + "Resources"`:Spécifie le dossier local dans lequel les ressources (comme les polices et les fichiers CSS) seront enregistrées.
- `ResourceFolderAlias = "http://example.com/resources"`: Définit un alias pour le dossier de ressources, qui sera utilisé dans le fichier HTML.

## Étape 4 : Enregistrer le document au format HTML

Une fois les options d'enregistrement configurées, l'étape finale consiste à enregistrer le document sous forme de fichier HTML. Voici comment procéder :

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
```

Cette ligne de code enregistre le document au format HTML, ainsi que les ressources exportées.

## Conclusion

Et voilà ! Vous avez exporté avec succès des ressources tout en enregistrant un document Word au format HTML à l'aide d'Aspose.Words pour .NET. Grâce à cette puissante bibliothèque, la gestion des documents Word par programmation devient un jeu d'enfant. Que vous travailliez sur une application Web ou que vous ayez simplement besoin de convertir des documents pour une utilisation hors ligne, Aspose.Words est là pour vous.

## FAQ

### Puis-je exporter des images avec des polices et du CSS ?
 Oui, vous pouvez ! Aspose.Words pour .NET prend également en charge l'exportation d'images. Assurez-vous simplement de configurer le`HtmlSaveOptions` par conséquent.

### Existe-t-il un moyen d’intégrer CSS au lieu d’utiliser une feuille de style externe ?
 Absolument. Vous pouvez définir`CssStyleSheetType` à`CssStyleSheetType.Embedded` si vous préférez les styles intégrés.

### Comment puis-je personnaliser le nom du fichier HTML de sortie ?
 Vous pouvez spécifier n'importe quel nom de fichier que vous souhaitez dans le`doc.Save` méthode. Par exemple,`doc.Save(dataDir + "CustomFileName.html", saveOptions);`.

### Aspose.Words prend-il en charge d'autres formats en plus du HTML ?
 Oui, il prend en charge divers formats, notamment PDF, DOCX, TXT, etc. Découvrez le[documentation](https://reference.aspose.com/words/net/) pour une liste complète.

### Où puis-je obtenir plus de soutien et de ressources ?
Pour plus d'aide, visitez le[Forum d'assistance Aspose.Words](https://forum.aspose.com/c/words/8) . Vous pouvez également trouver une documentation détaillée et des exemples sur le[Site Web d'Aspose](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
