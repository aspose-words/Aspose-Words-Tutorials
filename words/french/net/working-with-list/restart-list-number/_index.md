---
title: Numéro de la liste de redémarrage
linktitle: Numéro de la liste de redémarrage
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment redémarrer les numéros de liste dans les documents Word à l'aide d'Aspose.Words pour .NET. Ce guide détaillé de 2 000 mots couvre tout ce que vous devez savoir, de la configuration à la personnalisation avancée.
weight: 10
url: /fr/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Numéro de la liste de redémarrage

## Introduction

Vous cherchez à maîtriser l'art de la manipulation de listes dans vos documents Word à l'aide d'Aspose.Words pour .NET ? Eh bien, vous êtes au bon endroit ! Dans ce tutoriel, nous allons nous plonger dans le redémarrage des numéros de liste, une fonctionnalité astucieuse qui fera passer vos compétences en automatisation de documents au niveau supérieur. Attachez vos ceintures et commençons !

## Prérequis

Avant de passer au code, assurons-nous que vous disposez de tout ce dont vous avez besoin :

1.  Aspose.Words pour .NET : vous devez avoir installé Aspose.Words pour .NET. Si vous ne l'avez pas encore installé, vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : assurez-vous de disposer d’un environnement de développement adapté comme Visual Studio.
3. Connaissances de base de C# : une compréhension de base de C# vous aidera à suivre le didacticiel.

## Importer des espaces de noms

Tout d'abord, importons les espaces de noms nécessaires. Ceux-ci sont essentiels pour accéder aux fonctionnalités d'Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Décomposons maintenant le processus en étapes faciles à suivre. Nous aborderons tous les aspects, de la création d'une liste à la reprise de sa numérotation.

## Étape 1 : Configurez votre document et votre générateur

Avant de pouvoir commencer à manipuler des listes, vous avez besoin d'un document et d'un DocumentBuilder. DocumentBuilder est votre outil de référence pour ajouter du contenu à votre document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Étape 2 : Créez et personnalisez votre première liste

Ensuite, nous allons créer une liste basée sur un modèle et personnaliser son apparence. Dans cet exemple, nous utilisons le format de nombre arabe avec des parenthèses.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Ici, nous avons défini la couleur de la police sur rouge et aligné le texte à droite.

## Étape 3 : Ajoutez des éléments à votre première liste

 Votre liste étant prête, il est temps d'ajouter quelques éléments. Le DocumentBuilder`ListFormat.List` la propriété aide à appliquer le format de liste au texte.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Étape 4 : Redémarrer la numérotation de la liste

Pour réutiliser la liste et recommencer sa numérotation, vous devez créer une copie de la liste d'origine. Cela vous permet de modifier la nouvelle liste de manière indépendante.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

Dans cet exemple, la nouvelle liste commence au numéro 10.

## Étape 5 : Ajouter des éléments à la nouvelle liste

Comme précédemment, ajoutez des éléments à votre nouvelle liste. Cela montre que la liste redémarre au nombre spécifié.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Étape 6 : Enregistrez votre document

Enfin, enregistrez votre document dans le répertoire spécifié.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Conclusion

La restauration des numéros de liste dans les documents Word à l'aide d'Aspose.Words pour .NET est simple et incroyablement utile. Que vous génériez des rapports, créiez des documents structurés ou que vous ayez simplement besoin d'un meilleur contrôle sur vos listes, cette technique est faite pour vous.

## FAQ

### Puis-je utiliser d’autres modèles de liste en plus de NumberArabicParenthesis ?

Absolument ! Aspose.Words propose différents modèles de listes tels que des puces, des lettres, des chiffres romains, etc. Vous pouvez choisir celui qui correspond le mieux à vos besoins.

### Comment puis-je changer le niveau de la liste ?

 Vous pouvez modifier le niveau de la liste en modifiant le`ListLevels` propriété. Par exemple,`list1.ListLevels[1]` ferait référence au deuxième niveau de la liste.

### Puis-je recommencer la numérotation à n’importe quel numéro ?

 Oui, vous pouvez définir le numéro de départ sur n'importe quelle valeur entière à l'aide de la`StartAt` propriété du niveau de la liste.

### Est-il possible d'avoir un formatage différent pour différents niveaux de liste ?

En effet ! Chaque niveau de liste peut avoir ses propres paramètres de formatage, tels que la police, l'alignement et le style de numérotation.

### Que faire si je souhaite continuer la numérotation à partir d’une liste précédente au lieu de recommencer ?

Si vous souhaitez continuer la numérotation, vous n'avez pas besoin de créer une copie de la liste. Continuez simplement à ajouter des éléments à la liste d'origine.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
