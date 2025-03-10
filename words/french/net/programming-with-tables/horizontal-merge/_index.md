---
title: Fusion horizontale
linktitle: Fusion horizontale
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment fusionner horizontalement des cellules dans un document Word à l'aide d'Aspose.Words pour .NET avec ce didacticiel détaillé, étape par étape.
weight: 10
url: /fr/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Fusion horizontale

## Introduction

Bonjour ! Vous êtes prêt à plonger dans le monde d'Aspose.Words pour .NET ? Aujourd'hui, nous allons aborder une fonctionnalité très utile : la fusion horizontale dans les tableaux. Cela peut sembler un peu technique, mais ne vous inquiétez pas, je suis là pour vous. À la fin de ce tutoriel, vous serez un pro de la fusion de cellules dans vos documents Word par programmation. Alors, retroussons nos manches et commençons !

## Prérequis

Avant de passer aux choses sérieuses, vous devez mettre en place quelques éléments :

1. Bibliothèque Aspose.Words pour .NET : Si vous ne l'avez pas déjà fait, téléchargez la bibliothèque Aspose.Words pour .NET. Vous pouvez la récupérer[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : assurez-vous de disposer d’un environnement de développement approprié, tel que Visual Studio.
3. Connaissances de base de C# : Une compréhension de base de la programmation C# sera bénéfique.

Une fois que vous avez réglé ces problèmes, vous êtes prêt à partir !

## Importer des espaces de noms

Avant de plonger dans le code, assurons-nous que nous avons importé les espaces de noms nécessaires. Dans votre projet C#, assurez-vous d'inclure :

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Très bien, décomposons le processus de fusion horizontale des cellules d’un tableau dans un document Word à l’aide d’Aspose.Words pour .NET.

## Étape 1 : Configuration de votre document

 Tout d’abord, nous devons créer un nouveau document Word et initialiser le`DocumentBuilder`:

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Cet extrait de code configure un nouveau document et prépare le`DocumentBuilder` pour l'action.

## Étape 2 : insertion de la première cellule

Ensuite, nous commençons par insérer la première cellule et la marquer pour la fusion horizontale :

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Ici, nous insérons une nouvelle cellule et définissons sa`HorizontalMerge`propriété à`CellMerge.First`, indiquant que cette cellule est le début d'une séquence de cellules fusionnées.

## Étape 3 : insertion de la cellule fusionnée

Maintenant, nous insérons la cellule qui sera fusionnée avec la précédente :

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Cette cellule est configurée pour fusionner avec la cellule précédente en utilisant`CellMerge.Previous` . Remarquez comment nous terminons la ligne avec`builder.EndRow()`.

## Étape 4 : insertion de cellules non fusionnées

Pour illustrer la différence, insérons quelques cellules non fusionnées :

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Ici, nous insérons deux cellules sans fusion horizontale. Cela montre comment les cellules se comportent lorsqu'elles ne font pas partie d'une séquence fusionnée.

## Étape 5 : Finition de la table

Enfin, nous terminons le tableau et sauvegardons le document :

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Cet extrait de code complète le tableau et enregistre le document dans le répertoire spécifié.

## Conclusion

Et voilà ! Vous venez de maîtriser l'art de fusionner horizontalement des cellules dans un document Word à l'aide d'Aspose.Words pour .NET. En suivant ces étapes, vous pouvez créer facilement des structures de tableau complexes. Continuez à expérimenter et à explorer les capacités d'Aspose.Words pour rendre vos documents aussi dynamiques et flexibles que vous le souhaitez. Bon codage !

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, modifier et manipuler des documents Word par programmation dans des applications .NET.

### Puis-je fusionner des cellules verticalement avec Aspose.Words pour .NET ?
 Oui, vous pouvez également fusionner des cellules verticalement en utilisant le`CellFormat.VerticalMerge` propriété.

### L'utilisation d'Aspose.Words pour .NET est-elle gratuite ?
 Aspose.Words pour .NET propose un essai gratuit, mais pour bénéficier de toutes les fonctionnalités, vous devrez acheter une licence. Vous pouvez obtenir une licence temporaire[ici](https://purchase.aspose.com/temporary-license/).

### Comment puis-je en savoir plus sur Aspose.Words pour .NET ?
 Vous pouvez explorer la documentation détaillée[ici](https://reference.aspose.com/words/net/).

### Où puis-je obtenir de l'aide pour Aspose.Words pour .NET ?
 Pour toute question ou problème, vous pouvez visiter le forum d'assistance Aspose[ici](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
