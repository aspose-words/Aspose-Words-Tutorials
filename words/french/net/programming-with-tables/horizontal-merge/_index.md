---
"description": "Apprenez à fusionner horizontalement des cellules dans un document Word à l'aide d'Aspose.Words pour .NET avec ce didacticiel détaillé étape par étape."
"linktitle": "Fusion horizontale"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Fusion horizontale"
"url": "/fr/net/programming-with-tables/horizontal-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Fusion horizontale

## Introduction

Salut ! Prêt à plonger dans l'univers d'Aspose.Words pour .NET ? Aujourd'hui, nous allons aborder une fonctionnalité très utile : la fusion horizontale dans les tableaux. Cela peut paraître un peu technique, mais pas d'inquiétude, je suis là pour vous aider. À la fin de ce tutoriel, vous maîtriserez parfaitement la fusion de cellules dans vos documents Word par programmation. Alors, retroussons nos manches et commençons !

## Prérequis

Avant de passer aux choses sérieuses, il y a quelques éléments que vous devrez mettre en place :

1. Bibliothèque Aspose.Words pour .NET : Si ce n'est pas déjà fait, téléchargez la bibliothèque Aspose.Words pour .NET. Vous pouvez la récupérer. [ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : assurez-vous de disposer d’un environnement de développement approprié, tel que Visual Studio.
3. Connaissances de base de C# : Une compréhension de base de la programmation C# sera bénéfique.

Une fois que vous avez réglé ces problèmes, vous êtes prêt à partir !

## Importer des espaces de noms

Avant de plonger dans le code, vérifions que les espaces de noms nécessaires sont importés. Dans votre projet C#, assurez-vous d'inclure :

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Très bien, décomposons le processus de fusion horizontale des cellules d’un tableau dans un document Word à l’aide d’Aspose.Words pour .NET.

## Étape 1 : Configuration de votre document

Tout d’abord, nous devons créer un nouveau document Word et initialiser le `DocumentBuilder`:

```csharp
// Chemin d'accès à votre répertoire de documents 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Cet extrait de code configure un nouveau document et prépare le `DocumentBuilder` pour l'action.

## Étape 2 : Insertion de la première cellule

Ensuite, nous commençons par insérer la première cellule et la marquer pour la fusion horizontale :

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

Ici, nous insérons une nouvelle cellule et définissons sa `HorizontalMerge` propriété à `CellMerge.First`, indiquant que cette cellule est le début d'une séquence de cellules fusionnées.

## Étape 3 : Insertion de la cellule fusionnée

Maintenant, nous insérons la cellule qui sera fusionnée avec la précédente :

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

Cette cellule est configurée pour fusionner avec la cellule précédente en utilisant `CellMerge.Previous`. Remarquez comment nous terminons la ligne avec `builder.EndRow()`.

## Étape 4 : Insertion de cellules non fusionnées

Pour illustrer la différence, insérons quelques cellules non fusionnées :

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Ici, nous insérons deux cellules sans fusion horizontale. Ceci illustre le comportement des cellules lorsqu'elles ne font pas partie d'une séquence fusionnée.

## Étape 5 : Finition de la table

Enfin, nous terminons le tableau et sauvegardons le document :

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Cet extrait de code complète le tableau et enregistre le document dans le répertoire spécifié.

## Conclusion

Et voilà ! Vous venez de maîtriser l'art de fusionner horizontalement des cellules dans un document Word avec Aspose.Words pour .NET. En suivant ces étapes, vous pouvez créer facilement des structures de tableaux complexes. Continuez à expérimenter et à explorer les possibilités d'Aspose.Words pour rendre vos documents aussi dynamiques et flexibles que vous le souhaitez. Bon codage !

## FAQ

### Qu'est-ce qu'Aspose.Words pour .NET ?
Aspose.Words pour .NET est une bibliothèque puissante qui permet aux développeurs de créer, modifier et manipuler des documents Word par programmation dans des applications .NET.

### Puis-je fusionner des cellules verticalement avec Aspose.Words pour .NET ?
Oui, vous pouvez également fusionner des cellules verticalement en utilisant le `CellFormat.VerticalMerge` propriété.

### L'utilisation d'Aspose.Words pour .NET est-elle gratuite ?
Aspose.Words pour .NET propose un essai gratuit, mais pour bénéficier de toutes les fonctionnalités, vous devrez acheter une licence. Vous pouvez obtenir une licence temporaire. [ici](https://purchase.aspose.com/temporary-license/).

### Comment puis-je en savoir plus sur Aspose.Words pour .NET ?
Vous pouvez explorer la documentation détaillée [ici](https://reference.aspose.com/words/net/).

### Où puis-je obtenir de l'aide pour Aspose.Words pour .NET ?
Pour toute question ou problème, vous pouvez visiter le forum d'assistance Aspose [ici](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}