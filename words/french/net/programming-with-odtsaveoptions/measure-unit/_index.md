---
title: Unité de mesure
linktitle: Unité de mesure
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment configurer la fonctionnalité d’unité de mesure dans Aspose.Words pour .NET pour préserver la mise en forme du document lors de la conversion ODT.
weight: 10
url: /fr/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Unité de mesure

## Introduction

Avez-vous déjà dû convertir vos documents Word en différents formats mais aviez besoin d'une unité de mesure spécifique pour votre mise en page ? Qu'il s'agisse de pouces, de centimètres ou de points, il est essentiel de garantir que votre document conserve son intégrité pendant le processus de conversion. Dans ce didacticiel, nous verrons comment configurer la fonctionnalité d'unité de mesure dans Aspose.Words pour .NET. Cette fonctionnalité puissante garantit que la mise en forme de votre document est préservée exactement comme vous le souhaitez lors de la conversion au format ODT (Open Document Text).

## Prérequis

Avant de plonger dans le code, vous aurez besoin de quelques éléments pour commencer :

1. Aspose.Words pour .NET : assurez-vous que la dernière version d'Aspose.Words pour .NET est installée. Si vous ne l'avez pas encore, vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : un IDE comme Visual Studio pour écrire et exécuter votre code C#.
3. Connaissances de base de C# : comprendre les bases de C# vous aidera à suivre le didacticiel.
4. Un document Word : Préparez un exemple de document Word que vous pouvez utiliser pour la conversion.

## Importer des espaces de noms

Avant de commencer à coder, assurons-nous que nous avons importé les espaces de noms nécessaires. Ajoutez ces directives using en haut de votre fichier de code :

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, vous devez définir le chemin d'accès à votre répertoire de documents. C'est là que se trouve votre document Word et où le fichier converti sera enregistré.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Remplacer`"YOUR DOCUMENTS DIRECTORY"` avec le chemin réel vers votre répertoire. Cela garantit que votre code sait où trouver votre document Word.

## Étape 2 : Charger le document Word

 Ensuite, vous devez charger le document Word que vous souhaitez convertir. Cela se fait à l'aide de l'`Document` classe de Aspose.Words.

```csharp
// Charger le document Word
Document doc = new Document(dataDir + "Document.docx");
```

Assurez-vous que votre document Word, nommé « Document.docx », est présent dans le répertoire spécifié.

## Étape 3 : Configurer l’unité de mesure

 Maintenant, configurons l'unité de mesure pour la conversion ODT. C'est là que la magie opère. Nous allons configurer l'`OdtSaveOptions` utiliser les pouces comme unité de mesure.

```csharp
// Configuration des options de sauvegarde avec la fonctionnalité « Unité de mesure »
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 Dans cet exemple, nous définissons l'unité de mesure sur pouces. Vous pouvez également choisir d'autres unités telles que`OdtSaveMeasureUnit.Centimeters` ou`OdtSaveMeasureUnit.Points` selon vos besoins.

## Étape 4 : Convertir le document en ODT

 Enfin, nous allons convertir le document Word au format ODT en utilisant le fichier configuré.`OdtSaveOptions`.

```csharp
// Convertir le document en ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Cette ligne de code enregistre le document converti dans le répertoire spécifié avec la nouvelle unité de mesure appliquée.

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement configurer la fonctionnalité d'unité de mesure dans Aspose.Words pour .NET pour garantir que la mise en page de votre document est préservée pendant la conversion. Que vous travailliez avec des pouces, des centimètres ou des points, ce didacticiel vous a montré comment prendre facilement le contrôle de la mise en forme de votre document.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante permettant de travailler avec des documents Word par programmation. Elle permet aux développeurs de créer, modifier, convertir et traiter des documents Word sans avoir recours à Microsoft Word.

### Puis-je utiliser d’autres unités de mesure que les pouces ?
 Oui, Aspose.Words pour .NET prend en charge d'autres unités de mesure telles que les centimètres et les points. Vous pouvez spécifier l'unité souhaitée à l'aide de l'`OdtSaveMeasureUnit` énumération.

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?
 Oui, vous pouvez télécharger une version d'essai gratuite d'Aspose.Words pour .NET à partir de[ici](https://releases.aspose.com/).

### Où puis-je trouver la documentation pour Aspose.Words pour .NET ?
 Vous pouvez accéder à la documentation complète d'Aspose.Words pour .NET à l'adresse[ce lien](https://reference.aspose.com/words/net/).

### Comment puis-je obtenir de l'aide pour Aspose.Words pour .NET ?
 Pour obtenir de l'aide, vous pouvez visiter le forum Aspose.Words à l'adresse[ce lien](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
