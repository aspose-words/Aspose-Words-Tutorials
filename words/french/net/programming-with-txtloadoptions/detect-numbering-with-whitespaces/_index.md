---
title: Détecter la numérotation avec des espaces
linktitle: Détecter la numérotation avec des espaces
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment utiliser Aspose.Words pour .NET pour détecter la numérotation avec des espaces dans les documents en texte brut et garantir que vos listes sont correctement reconnues.
weight: 10
url: /fr/net/programming-with-txtloadoptions/detect-numbering-with-whitespaces/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Détecter la numérotation avec des espaces

## Introduction

Aspose.Words pour les passionnés de .NET ! Aujourd'hui, nous nous penchons sur une fonctionnalité fascinante qui peut faciliter la gestion des listes dans les documents en texte brut. Avez-vous déjà eu affaire à des fichiers texte dans lesquels certaines lignes sont censées être des listes, mais elles ne s'affichent pas correctement une fois chargées dans un document Word ? Eh bien, nous avons un tour dans notre sac : détecter la numérotation avec des espaces. Ce tutoriel vous expliquera comment utiliser la fonction`DetectNumberingWithWhitespaces` option dans Aspose.Words pour .NET pour garantir que vos listes sont correctement reconnues, même lorsqu'il y a des espaces entre les nombres et le texte.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Aspose.Words pour .NET : vous pouvez le télécharger à partir du[Sorties d'Aspose](https://releases.aspose.com/words/net/) page.
- Environnement de développement : Visual Studio ou tout autre IDE C#.
- .NET Framework installé sur votre machine.
- Connaissances de base de C# : comprendre les bases vous aidera à suivre les exemples.

## Importer des espaces de noms

Avant de vous lancer dans le code, assurez-vous que les espaces de noms nécessaires sont importés dans votre projet. Voici un extrait rapide pour vous aider à démarrer :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Décomposons le processus en étapes simples et faciles à gérer. Chaque étape vous guidera à travers le code nécessaire et vous expliquera ce qui se passe.

## Étape 1 : Définissez votre répertoire de documents

Tout d'abord, définissons le chemin d'accès à votre répertoire de documents. C'est là que vos fichiers d'entrée et de sortie seront stockés.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : créer un document en texte brut

Ensuite, nous allons créer un document en texte brut sous forme de chaîne. Ce document contiendra des parties qui pourront être interprétées comme des listes.

```csharp
const string textDoc = "Full stop delimiters:\n" +
                       "1. First list item 1\n" +
                       "2. First list item 2\n" +
                       "3. First list item 3\n\n" +
                       "Right bracket delimiters:\n" +
                       "1) Second list item 1\n" +
                       "2) Second list item 2\n" +
                       "3) Second list item 3\n\n" +
                       "Bullet delimiters:\n" +
                       "• Third list item 1\n" +
                       "• Third list item 2\n" +
                       "• Third list item 3\n\n" +
                       "Whitespace delimiters:\n" +
                       "1 Fourth list item 1\n" +
                       "2 Fourth list item 2\n" +
                       "3 Fourth list item 3";
```

## Étape 3 : Configurer LoadOptions

 Pour détecter la numérotation avec des espaces, nous devons définir le`DetectNumberingWithWhitespaces` option pour`true` dans un`TxtLoadOptions` objet.

```csharp
TxtLoadOptions loadOptions = new TxtLoadOptions { DetectNumberingWithWhitespaces = true };
```

## Étape 4 : Charger le document

 Maintenant, chargeons le document en utilisant le`TxtLoadOptions` en tant que paramètre. Cela garantit que la quatrième liste (avec des espaces) est détectée correctement.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(textDoc)), loadOptions);
```

## Étape 5 : Enregistrer le document

Enfin, enregistrez le document dans le répertoire spécifié. Vous obtiendrez ainsi un document Word contenant les listes correctement détectées.

```csharp
doc.Save(dataDir + "WorkingWithTxtLoadOptions.DetectNumberingWithWhitespaces.docx");
```

## Conclusion

Et voilà ! Avec seulement quelques lignes de code, vous maîtrisez l'art de détecter la numérotation avec des espaces dans les documents en texte brut à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité peut s'avérer extrêmement pratique pour gérer différents formats de texte et garantir que vos listes sont représentées avec précision dans vos documents Word. Ainsi, la prochaine fois que vous rencontrerez ces listes délicates, vous saurez exactement quoi faire.

## FAQ

###  Qu'est-ce que`DetectNumberingWithWhitespaces` in Aspose.Words for .NET?
`DetectNumberingWithWhitespaces` est une option dans`TxtLoadOptions` cela permet à Aspose.Words de reconnaître les listes même lorsqu'il y a un espace entre la numérotation et le texte de l'élément de la liste.

### Puis-je utiliser cette fonctionnalité pour d’autres délimiteurs comme les puces et les crochets ?
 Oui, Aspose.Words détecte automatiquement les listes avec des délimiteurs courants tels que des puces et des crochets.`DetectNumberingWithWhitespaces` aide spécifiquement avec les listes qui contiennent des espaces.

###  Que se passe-t-il si je n'utilise pas`DetectNumberingWithWhitespaces`?
Sans cette option, les listes avec des espaces entre la numérotation et le texte pourraient ne pas être reconnues comme des listes et les éléments pourraient apparaître comme des paragraphes simples.

### Cette fonctionnalité est-elle disponible dans d’autres produits Aspose ?
Cette fonctionnalité spécifique est adaptée à Aspose.Words pour .NET, conçue pour gérer le traitement des documents Word.

### Comment puis-je obtenir une licence temporaire pour Aspose.Words pour .NET ?
 Vous pouvez obtenir une licence temporaire auprès de la[Licence temporaire Aspose](https://purchase.aspose.com/temporary-license/) page.


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
