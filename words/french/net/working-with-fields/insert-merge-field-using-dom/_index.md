---
title: Insérer un champ de fusion à l'aide de DOM
linktitle: Insérer un champ de fusion à l'aide de DOM
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer et configurer des champs de fusion dans des documents Word à l'aide d'Aspose.Words pour .NET avec ce didacticiel complet, étape par étape.
weight: 10
url: /fr/net/working-with-fields/insert-merge-field-using-dom/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un champ de fusion à l'aide de DOM

## Introduction

Si vous travaillez avec le traitement de documents dans .NET, vous avez probablement déjà rencontré Aspose.Words. Cette puissante bibliothèque offre un large éventail de fonctionnalités pour manipuler des documents Word par programmation. Dans ce didacticiel, nous nous concentrerons sur une fonctionnalité spécifique : l'insertion d'un champ de fusion à l'aide du modèle d'objet de document (DOM) dans Aspose.Words pour .NET. Ce guide vous guidera à chaque étape, de la configuration de votre environnement à l'insertion et à la mise à jour d'un champ de fusion dans un document Word.

## Prérequis

Avant de plonger dans le code, assurons-nous que vous disposez de tout ce dont vous avez besoin pour suivre ce tutoriel.

1. Connaissances de base de C# : vous devez être à l’aise avec la programmation C#.
2. Visual Studio installé : assurez-vous que Visual Studio ou tout autre IDE C# est installé sur votre ordinateur.
3.  Aspose.Words pour .NET : téléchargez et installez la dernière version d'Aspose.Words pour .NET à partir du[Communiqués de presse](https://releases.aspose.com/words/net/).
4.  Licence valide : Si vous n'avez pas de licence, vous pouvez en obtenir une[permis temporaire](https://purchase.aspose.com/temporary-license/) pour évaluation.

## Étape 1 : Configurez votre projet

Tout d’abord, configurons un nouveau projet dans Visual Studio.

1. Ouvrez Visual Studio.
2. Créer un nouveau projet : allez dans Fichier > Nouveau > Projet. Sélectionnez une application console C#.
3. Nommez votre projet : donnez à votre projet un nom significatif et cliquez sur Créer.

## Étape 2 : Installer Aspose.Words

Pour utiliser Aspose.Words, vous devez l'ajouter à votre projet. Cela peut être fait via le gestionnaire de packages NuGet.

1. Ouvrez le gestionnaire de packages NuGet : cliquez avec le bouton droit sur votre projet dans l’Explorateur de solutions, puis sélectionnez Gérer les packages NuGet.
2. Rechercher Aspose.Words : dans le gestionnaire de packages NuGet, recherchez « Aspose.Words ».
3. Installer le package : cliquez sur Installer pour ajouter Aspose.Words à votre projet.

## Étape 3 : Importer les espaces de noms

Pour commencer à utiliser Aspose.Words, vous devez importer les espaces de noms nécessaires dans votre projet. Voici comment procéder :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

## Étape 4 : Initialisez votre document

Maintenant que tout est configuré, créons un nouveau document Word et initialisons le DocumentBuilder.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Créez le document et le DocumentBuilder.
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 5 : Déplacez le curseur vers un paragraphe spécifique

Ensuite, nous devons déplacer le curseur vers un paragraphe spécifique du document où nous souhaitons insérer le champ de fusion.

```csharp
Paragraph para = (Paragraph) doc.GetChild(NodeType.Paragraph, 0, true);
builder.MoveTo(para);
```

## Étape 6 : insérer le champ de fusion

 L'insertion d'un champ de fusion est simple. Nous allons utiliser le`InsertField` méthode de la`DocumentBuilder` classe.

```csharp
// Insérer un champ de fusion de champ.
FieldMergeField field = (FieldMergeField)builder.InsertField(FieldType.FieldMergeField, false);
```

## Étape 7 : Configurer le champ de fusion

Après avoir inséré le champ de fusion, vous pouvez définir diverses propriétés pour le configurer selon vos besoins.

```csharp
field.FieldName = "Test1";
field.TextBefore = "Test2";
field.TextAfter = "Test3";
field.IsMapped = true;
field.IsVerticalFormatting = true;
```

## Étape 8 : Mettre à jour et enregistrer le document

Enfin, mettez à jour le champ pour vous assurer que tous les paramètres sont appliqués et enregistrez le document.

```csharp
// Mettre à jour le champ.
field.Update();

// Sauvegarder le document.
doc.Save(dataDir + "InsertionChampMergeChamp.docx");
```

## Conclusion

En suivant ces étapes, vous pouvez facilement insérer et configurer des champs de fusion dans un document Word à l'aide d'Aspose.Words pour .NET. Ce didacticiel a couvert les étapes essentielles de la configuration de votre environnement à l'enregistrement du document final. Avec Aspose.Words, vous pouvez automatiser des tâches complexes de traitement de documents, rendant vos applications .NET plus puissantes et plus efficaces.

## FAQ

###  Qu'est-ce qu'un champ de fusion ?
Un champ de fusion est un espace réservé dans un document qui peut être remplacé dynamiquement par des données provenant d'une source de données, telle qu'une base de données ou un fichier CSV.

###  Puis-je utiliser Aspose.Words gratuitement ?
 Aspose.Words propose un essai gratuit que vous pouvez télécharger[ici](https://releases.aspose.com/)Pour une utilisation à long terme, vous devrez acheter une licence.

###  Comment obtenir une licence temporaire pour Aspose.Words ?
 Vous pouvez obtenir une licence temporaire sur le site Web d'Aspose[ici](https://purchase.aspose.com/temporary-license/).

### Quelles versions de .NET sont prises en charge par Aspose.Words ?
Aspose.Words prend en charge plusieurs versions de .NET, notamment .NET Framework, .NET Core et .NET Standard.

###  Où puis-je trouver la documentation de l'API pour Aspose.Words ?
 La documentation de l'API est disponible[ici](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
