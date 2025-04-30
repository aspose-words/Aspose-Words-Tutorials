---
"description": "Découvrez comment configurer la fonctionnalité d’unité de mesure dans Aspose.Words pour .NET pour préserver la mise en forme du document lors de la conversion ODT."
"linktitle": "Unité de mesure"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Unité de mesure"
"url": "/fr/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Unité de mesure

## Introduction

Avez-vous déjà dû convertir vos documents Word vers différents formats, mais avec une unité de mesure spécifique pour votre mise en page ? Que vous utilisiez des pouces, des centimètres ou des points, il est crucial de garantir l'intégrité de votre document pendant la conversion. Dans ce tutoriel, nous vous expliquerons comment configurer la fonctionnalité d'unité de mesure dans Aspose.Words pour .NET. Cette fonctionnalité puissante garantit que la mise en forme de votre document est conservée exactement comme vous le souhaitez lors de la conversion au format ODT (Open Document Text).

## Prérequis

Avant de plonger dans le code, vous aurez besoin de quelques éléments pour commencer :

1. Aspose.Words pour .NET : Assurez-vous d'avoir installé la dernière version d'Aspose.Words pour .NET. Si ce n'est pas déjà fait, vous pouvez la télécharger ici. [ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : un IDE comme Visual Studio pour écrire et exécuter votre code C#.
3. Connaissances de base de C# : comprendre les bases de C# vous aidera à suivre le didacticiel.
4. Un document Word : Préparez un exemple de document Word que vous pouvez utiliser pour la conversion.

## Importer des espaces de noms

Avant de commencer à coder, vérifions que les espaces de noms nécessaires sont importés. Ajoutez les directives using suivantes en haut de votre fichier de code :

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Configurez votre répertoire de documents

Tout d'abord, vous devez définir le chemin d'accès à votre répertoire de documents. C'est là que se trouve votre document Word et où le fichier converti sera enregistré.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Remplacer `"YOUR DOCUMENTS DIRECTORY"` avec le chemin d'accès réel à votre répertoire. Cela garantit que votre code sait où trouver votre document Word.

## Étape 2 : Charger le document Word

Ensuite, vous devez charger le document Word à convertir. Pour ce faire, utilisez l'outil `Document` classe d'Aspose.Words.

```csharp
// Charger le document Word
Document doc = new Document(dataDir + "Document.docx");
```

Assurez-vous que votre document Word, nommé « Document.docx », est présent dans le répertoire spécifié.

## Étape 3 : Configurer l’unité de mesure

Maintenant, configurons l'unité de mesure pour la conversion ODT. C'est là que la magie opère. Nous allons configurer `OdtSaveOptions` utiliser les pouces comme unité de mesure.

```csharp
// Configuration des options de sauvegarde avec la fonctionnalité « Unité de mesure »
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

Dans cet exemple, nous définissons l'unité de mesure en pouces. Vous pouvez également choisir d'autres unités, comme `OdtSaveMeasureUnit.Centimeters` ou `OdtSaveMeasureUnit.Points` en fonction de vos besoins.

## Étape 4 : Convertir le document en ODT

Enfin, nous allons convertir le document Word au format ODT en utilisant le fichier configuré. `OdtSaveOptions`.

```csharp
// Convertir le document en ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Cette ligne de code enregistre le document converti dans le répertoire spécifié avec la nouvelle unité de mesure appliquée.

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement configurer la fonctionnalité d'unité de mesure dans Aspose.Words pour .NET afin de préserver la mise en page de votre document lors de la conversion. Que vous travailliez avec des pouces, des centimètres ou des points, ce tutoriel vous montre comment maîtriser facilement la mise en forme de votre document.

## FAQ

### Qu'est-ce qu'Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante permettant de travailler avec des documents Word par programmation. Elle permet aux développeurs de créer, modifier, convertir et traiter des documents Word sans recourir à Microsoft Word.

### Puis-je utiliser d’autres unités de mesure que les pouces ?
Oui, Aspose.Words pour .NET prend en charge d'autres unités de mesure, telles que les centimètres et les points. Vous pouvez spécifier l'unité souhaitée à l'aide du `OdtSaveMeasureUnit` énumération.

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?
Oui, vous pouvez télécharger une version d'essai gratuite d'Aspose.Words pour .NET à partir de [ici](https://releases.aspose.com/).

### Où puis-je trouver la documentation pour Aspose.Words pour .NET ?
Vous pouvez accéder à la documentation complète d'Aspose.Words pour .NET à l'adresse [ce lien](https://reference.aspose.com/words/net/).

### Comment puis-je obtenir de l'aide pour Aspose.Words pour .NET ?
Pour obtenir de l'aide, vous pouvez visiter le forum Aspose.Words à l'adresse [ce lien](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}