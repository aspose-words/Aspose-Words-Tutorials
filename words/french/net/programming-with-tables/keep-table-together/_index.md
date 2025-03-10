---
title: Gardez la table ensemble
linktitle: Gardez la table ensemble
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment empêcher les tableaux de se diviser en plusieurs pages dans les documents Word à l'aide d'Aspose.Words pour .NET. Suivez notre guide pour conserver des documents professionnels et lisibles.
weight: 10
url: /fr/net/programming-with-tables/keep-table-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gardez la table ensemble

## Introduction

Vous êtes-vous déjà senti frustré lorsqu'un tableau de votre document Word se divise en deux pages ? C'est comme si vos informations soigneusement disposées décidaient soudainement de faire une pause à mi-chemin ! Il est essentiel de conserver les tableaux ensemble sur une seule page pour la lisibilité et la présentation. Qu'il s'agisse d'un rapport, d'une proposition de projet ou simplement d'un document personnel, le fait d'avoir des tableaux divisés peut être assez dérangeant. Heureusement pour nous, Aspose.Words pour .NET a un moyen astucieux de résoudre ce problème. Dans ce didacticiel, nous allons parcourir les étapes à suivre pour conserver vos tableaux intacts et nets. Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET - Si vous ne l'avez pas encore installé, vous pouvez le télécharger à partir de[ici](https://releases.aspose.com/words/net/).
2. Un document Word avec un tableau – Nous travaillerons avec un exemple de document contenant un tableau s'étendant sur plusieurs pages.
3. Connaissances de base de C# – Ce didacticiel suppose que vous avez une compréhension de base de la programmation C#.

## Importer des espaces de noms

Tout d'abord, importons les espaces de noms nécessaires. Cela nous donnera accès aux classes et méthodes dont nous avons besoin à partir d'Aspose.Words pour .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Décomposons le processus en étapes simples et digestes. Nous commencerons par charger notre document et terminerons par enregistrer le document mis à jour où le tableau reste cohérent.

## Étape 1 : Charger le document

 Pour travailler avec un document Word, nous devons d'abord le charger. Nous utiliserons le`Document` classe pour ça.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Étape 2 : Accéder au tableau

Ensuite, nous devons obtenir le tableau que nous voulons conserver. Nous supposerons qu'il s'agit du premier tableau du document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Étape 3 : définir KeepWithNext pour les paragraphes

 Pour éviter que le tableau ne soit réparti sur plusieurs pages, nous devons définir le`KeepWithNext` propriété pour chaque paragraphe du tableau, à l'exception des derniers paragraphes de la dernière ligne.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Étape 4 : Enregistrer le document

Enfin, nous enregistrons le document mis à jour. Cela appliquera nos modifications et garantira que le tableau reste cohérent sur une seule page.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Conclusion

Et voilà ! Avec seulement quelques lignes de code, vous pouvez empêcher vos tableaux de se diviser sur plusieurs pages dans vos documents Word. Cette solution simple mais efficace garantit que vos tableaux restent propres et professionnels, améliorant ainsi la lisibilité de vos documents. Aspose.Words pour .NET simplifie la gestion de ces problèmes de formatage, vous permettant de vous concentrer sur la création de contenu de qualité.

## FAQ

### Puis-je conserver plusieurs tables ensemble en utilisant cette méthode ?  
Oui, vous pouvez appliquer la même logique à plusieurs tables en parcourant chaque table de votre document.

### Que faire si mon tableau est trop grand pour tenir sur une seule page ?  
Si un tableau est trop grand pour tenir sur une seule page, il s'étendra sur plusieurs pages. Cette méthode garantit que les tableaux plus petits restent intacts sans être divisés.

### Existe-t-il un moyen d’automatiser cela pour tous les tableaux d’un document ?  
 Oui, vous pouvez parcourir tous les tableaux de votre document et appliquer le`KeepWithNext` propriété à chaque paragraphe.

### Ai-je besoin d'une licence payante pour Aspose.Words pour .NET ?  
Vous pouvez commencer avec un essai gratuit à partir de[ici](https://releases.aspose.com/), mais pour une fonctionnalité complète, une licence payante est recommandée.

### Puis-je appliquer une autre mise en forme au tableau tout en le gardant ensemble ?  
Absolument ! Vous pouvez formater votre tableau selon vos besoins tout en veillant à ce qu'il reste cohérent sur une seule page.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
