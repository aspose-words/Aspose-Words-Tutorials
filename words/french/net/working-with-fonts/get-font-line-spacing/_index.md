---
title: Obtenir l'espacement des lignes de police
linktitle: Obtenir l'espacement des lignes de police
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment obtenir l'espacement des lignes de police à l'aide d'Aspose.Words pour .NET grâce à ce didacticiel étape par étape. Idéal pour les développeurs.
weight: 10
url: /fr/net/working-with-fonts/get-font-line-spacing/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obtenir l'espacement des lignes de police

## Introduction

Aspose.Words pour .NET est une bibliothèque puissante qui vous permet de créer, de manipuler et de convertir des documents Word par programmation. Une tâche courante que vous devrez peut-être effectuer consiste à récupérer l'espacement des lignes d'une police spécifique dans un document. Dans ce didacticiel, nous vous guiderons pas à pas tout au long du processus, en veillant à ce que vous puissiez facilement obtenir l'espacement des lignes de police à l'aide d'Aspose.Words pour .NET. 

## Prérequis

Avant de plonger dans le code, assurez-vous que les conditions préalables suivantes sont remplies :

1.  Bibliothèque Aspose.Words pour .NET : téléchargez et installez la dernière version à partir de[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : assurez-vous d’avoir configuré un IDE tel que Visual Studio.
3. Connaissances de base de C# : ce didacticiel suppose que vous avez une compréhension de base de la programmation C#.

## Importer des espaces de noms

Tout d'abord, vous devez importer les espaces de noms nécessaires dans votre projet C#. Ces espaces de noms vous permettront d'accéder aux fonctionnalités d'Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Décomposons le processus d’obtention de l’espacement des lignes de police en étapes simples et gérables.

## Étape 1 : Créer un nouveau document

La première étape consiste à créer une nouvelle instance de document Word à l’aide d’Aspose.Words pour .NET.

```csharp
Document doc = new Document();
```

## Étape 2 : Initialiser DocumentBuilder

Ensuite, nous devons initialiser le`DocumentBuilder` objet. Cet objet nous aidera à construire et à manipuler le contenu du document.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 3 : définir les propriétés de la police

Maintenant, nous définissons les propriétés de police pour le texte que nous voulons insérer. Pour cet exemple, nous utiliserons la police « Calibri ».

```csharp
builder.Font.Name = "Calibri";
```

## Étape 4 : Écrire du texte dans le document

 En utilisant le`DocumentBuilder` objet, écrivez du texte dans le document. Ce texte utilisera les propriétés de police que nous avons définies à l'étape précédente.

```csharp
builder.Writeln("Sample Text");
```

## Étape 5 : Récupérer l’objet de police

Pour obtenir l'espacement des lignes, nous devons accéder à l'objet de police du texte que nous venons d'ajouter. Cela peut être fait en naviguant dans la structure du document jusqu'au premier paragraphe exécuté.

```csharp
Font font = builder.Document.FirstSection.Body.FirstParagraph.Runs[0].Font;
```

## Étape 6 : Obtenir l'espacement des lignes

Enfin, nous récupérons l’espacement des lignes de l’objet de police et l’imprimons sur la console.

```csharp
Console.WriteLine($"lineSpacing = {font.LineSpacing}");
```

## Conclusion

Et voilà ! La récupération de l'espacement des lignes de police à l'aide d'Aspose.Words pour .NET est simple lorsque vous la décomposez en ces étapes simples. Que vous créiez un nouveau document ou que vous travailliez sur un document existant, Aspose.Words fournit tous les outils dont vous avez besoin pour gérer efficacement les propriétés des polices.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, manipuler et convertir des documents Word par programmation à l'aide de C#.

### Puis-je utiliser Aspose.Words pour .NET dans d’autres langages .NET ?
Oui, vous pouvez utiliser Aspose.Words pour .NET avec n’importe quel langage .NET, y compris VB.NET et F#.

### Comment puis-je télécharger Aspose.Words pour .NET ?
 Vous pouvez télécharger la dernière version d'Aspose.Words pour .NET à partir de[ici](https://releases.aspose.com/words/net/).

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?
 Oui, vous pouvez obtenir un essai gratuit à partir de[ici](https://releases.aspose.com/).

### Où puis-je trouver la documentation d'Aspose.Words pour .NET ?
 La documentation d'Aspose.Words pour .NET est disponible[ici](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
