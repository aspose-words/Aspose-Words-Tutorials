---
"description": "Découvrez comment éviter que les tableaux ne s'entassent sur plusieurs pages dans vos documents Word grâce à Aspose.Words pour .NET. Suivez notre guide pour conserver des documents professionnels et lisibles."
"linktitle": "Gardez la table ensemble"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Gardez la table ensemble"
"url": "/fr/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gardez la table ensemble

## Introduction

Avez-vous déjà ressenti de la frustration lorsqu'un tableau de votre document Word se divise en deux pages ? C'est comme si vos informations soigneusement mises en page s'interrompaient soudainement à mi-chemin ! Conserver les tableaux sur une seule page est essentiel pour la lisibilité et la présentation. Qu'il s'agisse d'un rapport, d'une proposition de projet ou simplement d'un document personnel, la division des tableaux peut être assez perturbante. Heureusement pour nous, Aspose.Words pour .NET propose une solution astucieuse. Dans ce tutoriel, nous vous expliquerons comment conserver l'intégrité et la netteté de vos tableaux. C'est parti !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1. Aspose.Words pour .NET - Si vous ne l'avez pas encore installé, vous pouvez le télécharger à partir de [ici](https://releases.aspose.com/words/net/).
2. Un document Word avec un tableau - Nous travaillerons avec un exemple de document contenant un tableau s'étendant sur plusieurs pages.
3. Connaissances de base de C# - Ce didacticiel suppose que vous avez une compréhension de base de la programmation C#.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires. Cela nous donnera accès aux classes et méthodes nécessaires depuis Aspose.Words pour .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Décomposons le processus en étapes simples et compréhensibles. Nous commencerons par charger notre document et terminerons par enregistrer le document mis à jour, où le tableau reste intact.

## Étape 1 : Charger le document

Pour travailler avec un document Word, nous devons d'abord le charger. Nous utiliserons l' `Document` classe pour ça.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Étape 2 : Accéder au tableau

Ensuite, nous devons obtenir la table que nous souhaitons conserver. Nous supposerons qu'il s'agit de la première table du document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Étape 3 : Définir KeepWithNext pour les paragraphes

Pour éviter que le tableau ne soit divisé en plusieurs pages, nous devons définir le `KeepWithNext` propriété pour chaque paragraphe du tableau, à l'exception des derniers paragraphes de la dernière ligne.

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

## Étape 4 : Enregistrer le document

Enfin, nous enregistrons le document mis à jour. Cela appliquera nos modifications et garantira que le tableau reste cohérent sur une seule page.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Conclusion

Et voilà ! En quelques lignes de code, vous pouvez éviter que vos tableaux ne se répartissent sur plusieurs pages de vos documents Word. Cette solution simple et efficace garantit des tableaux clairs et professionnels, améliorant ainsi la lisibilité de vos documents. Aspose.Words pour .NET simplifie la gestion de ces problèmes de mise en forme et vous permet de vous concentrer sur la création de contenu de qualité.

## FAQ

### Puis-je conserver plusieurs tables ensemble en utilisant cette méthode ?  
Oui, vous pouvez appliquer la même logique à plusieurs tables en parcourant chaque table de votre document.

### Que faire si mon tableau est trop grand pour tenir sur une seule page ?  
Si un tableau est trop grand pour tenir sur une seule page, il s'étendra sur plusieurs pages. Cette méthode garantit que les petits tableaux restent intacts sans être fractionnés.

### Existe-t-il un moyen d’automatiser cela pour tous les tableaux d’un document ?  
Oui, vous pouvez parcourir tous les tableaux de votre document et appliquer le `KeepWithNext` propriété à chaque paragraphe.

### Ai-je besoin d’une licence payante pour Aspose.Words pour .NET ?  
Vous pouvez commencer avec un essai gratuit à partir de [ici](https://releases.aspose.com/), mais pour une fonctionnalité complète, une licence payante est recommandée.

### Puis-je appliquer une autre mise en forme au tableau tout en le gardant ensemble ?  
Absolument ! Vous pouvez formater votre tableau selon vos besoins tout en veillant à ce qu'il reste cohérent sur une seule page.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}