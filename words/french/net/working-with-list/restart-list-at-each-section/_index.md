---
title: Redémarrer la liste à chaque section
linktitle: Redémarrer la liste à chaque section
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment redémarrer des listes à chaque section dans des documents Word à l'aide d'Aspose.Words pour .NET. Suivez notre guide détaillé étape par étape pour gérer efficacement les listes.
weight: 10
url: /fr/net/working-with-list/restart-list-at-each-section/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Redémarrer la liste à chaque section

## Introduction

Créer des documents structurés et bien organisés peut parfois ressembler à résoudre un casse-tête complexe. L'une des pièces de ce casse-tête consiste à gérer efficacement les listes, en particulier lorsque vous souhaitez qu'elles redémarrent à chaque section. Avec Aspose.Words pour .NET, vous pouvez y parvenir en toute transparence. Voyons comment vous pouvez redémarrer les listes à chaque section de vos documents Word à l'aide d'Aspose.Words pour .NET.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET : téléchargez et installez la dernière version à partir du[Sorties d'Aspose](https://releases.aspose.com/words/net/) page.
2. Environnement .NET : configurez votre environnement de développement avec .NET installé.
3. Compréhension de base de C# : une connaissance du langage de programmation C# est recommandée.
4.  Licence Aspose : Vous pouvez opter pour une[permis temporaire](https://purchase.aspose.com/temporary-license/) si vous n'en avez pas.

## Importer des espaces de noms

Avant d'écrire le code, assurez-vous d'importer les espaces de noms nécessaires :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Lists;
```

Maintenant, décomposons le processus en plusieurs étapes pour le rendre facile à suivre.

## Étape 1 : Initialiser le document

Tout d’abord, vous devez créer une nouvelle instance de document.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
```

## Étape 2 : ajouter une liste numérotée

Ensuite, ajoutez une liste numérotée au document. Cette liste suivra un format de numérotation par défaut.

```csharp
doc.Lists.Add(ListTemplate.NumberDefault);
```

## Étape 3 : Accéder à la liste et définir la propriété de redémarrage

Récupérez la liste que vous venez de créer et définissez-la`IsRestartAtEachSection`propriété à`true`Cela garantit que la liste redémarre la numérotation à chaque nouvelle section.

```csharp
List list = doc.Lists[0];
list.IsRestartAtEachSection = true;
```

## Étape 4 : Créer un générateur de documents et associer la liste

 Créer un`DocumentBuilder` pour insérer du contenu dans le document et l'associer à la liste.

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
builder.ListFormat.List = list;
```

## Étape 5 : ajouter des éléments de liste et insérer un saut de section

Ajoutez maintenant des éléments à la liste. Pour illustrer la fonctionnalité de redémarrage, nous allons insérer un saut de section après un certain nombre d'éléments.

```csharp
for (int i = 1; i < 45; i++)
{
    builder.Writeln($"List item {i}");

    if (i == 15)
        builder.InsertBreak(BreakType.SectionBreakNewPage);
}
```

## Étape 6 : Enregistrer le document

Enfin, enregistrez le document avec les options appropriées pour garantir la conformité.

```csharp
OoxmlSaveOptions options = new OoxmlSaveOptions { Compliance = OoxmlCompliance.Iso29500_2008_Transitional };
doc.Save(dataDir + "WorkingWithList.RestartListAtEachSection.docx", options);		
```

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement redémarrer des listes à chaque section de vos documents Word à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité est incroyablement utile pour créer des documents bien structurés qui nécessitent des sections séparées avec leur propre numérotation de liste. Avec Aspose.Words, la gestion de ces tâches devient un jeu d'enfant, vous permettant de vous concentrer sur la création de contenu de haute qualité.

## FAQ

### Puis-je redémarrer les listes à chaque section pour différents types de listes ?
Oui, Aspose.Words pour .NET vous permet de redémarrer différents types de listes, y compris les listes à puces et numérotées.

### Que faire si je souhaite personnaliser le format de numérotation ?
 Vous pouvez personnaliser le format de numérotation en modifiant le`ListTemplate` propriété lors de la création de la liste.

### Existe-t-il une limite au nombre d’éléments dans une liste ?
Non, il n'y a pas de limite spécifique au nombre d'éléments que vous pouvez avoir dans une liste en utilisant Aspose.Words pour .NET.

### Puis-je utiliser cette fonctionnalité dans d’autres formats de documents comme PDF ?
Oui, vous pouvez utiliser Aspose.Words pour convertir des documents Word en d'autres formats comme PDF tout en conservant la structure de la liste.

### Comment puis-je obtenir un essai gratuit d'Aspose.Words pour .NET ?
 Vous pouvez obtenir un essai gratuit à partir du[Sorties d'Aspose](https://releases.aspose.com/) page.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
