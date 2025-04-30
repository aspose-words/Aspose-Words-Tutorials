---
"description": "Découvrez comment désactiver les sauts de ligne sur plusieurs pages dans les documents Word à l’aide d’Aspose.Words pour .NET afin de maintenir la lisibilité et la mise en forme des tableaux."
"linktitle": "Format de ligne Désactiver le saut de page"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Format de ligne Désactiver le saut de page"
"url": "/fr/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format de ligne Désactiver le saut de page

## Introduction

Lorsque vous travaillez avec des tableaux dans des documents Word, il est important de veiller à ce que les lignes ne soient pas coupées d'une page à l'autre, ce qui est essentiel pour garantir la lisibilité et la mise en forme de vos documents. Aspose.Words pour .NET offre un moyen simple de désactiver les sauts de ligne entre les pages.

Dans ce didacticiel, nous vous expliquerons le processus de désactivation des sauts de ligne sur plusieurs pages d'un document Word à l'aide d'Aspose.Words pour .NET.

## Prérequis

Avant de commencer, assurez-vous de disposer des prérequis suivants :
- Bibliothèque Aspose.Words pour .NET installée.
- Un document Word avec un tableau qui s'étend sur plusieurs pages.

## Importer des espaces de noms

Tout d’abord, importez les espaces de noms nécessaires dans votre projet :

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Étape 1 : Charger le document

Chargez le document contenant le tableau qui s’étend sur plusieurs pages.

```csharp
// Chemin d'accès à votre répertoire de documents 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Étape 2 : Accéder au tableau

Accédez au premier tableau du document. Cela suppose que le tableau à modifier est le premier du document.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Étape 3 : Désactiver la répartition entre les pages pour toutes les lignes

Parcourez chaque ligne du tableau et définissez le `AllowBreakAcrossPages` propriété à `false`Cela garantit que les lignes ne seront pas divisées en plusieurs pages.

```csharp
// Désactiver la séparation entre les pages pour toutes les lignes du tableau.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Étape 4 : Enregistrer le document

Enregistrez le document modifié dans le répertoire spécifié.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Conclusion

Dans ce tutoriel, nous avons montré comment désactiver les sauts de ligne entre les pages d'un document Word à l'aide d'Aspose.Words pour .NET. En suivant les étapes décrites ci-dessus, vous pouvez garantir que les lignes de votre tableau restent intactes et ne se divisent pas entre les pages, préservant ainsi la lisibilité et la mise en forme du document.

## FAQ

### Puis-je désactiver les sauts de ligne sur plusieurs pages pour une ligne spécifique au lieu de toutes les lignes ?  
Oui, vous pouvez désactiver les sauts de ligne pour des lignes spécifiques en accédant à la ligne souhaitée et en définissant son `AllowBreakAcrossPages` propriété à `false`.

### Cette méthode fonctionne-t-elle pour les tableaux avec des cellules fusionnées ?  
Oui, cette méthode fonctionne pour les tableaux contenant des cellules fusionnées. La propriété `AllowBreakAcrossPages` s'applique à la ligne entière, quelle que soit la fusion des cellules.

### Cette méthode fonctionnera-t-elle si la table est imbriquée dans une autre table ?  
Oui, vous pouvez accéder aux tables imbriquées et les modifier de la même manière. Assurez-vous de référencer correctement la table imbriquée par son index ou d'autres propriétés.

### Comment puis-je vérifier si une ligne permet une répartition sur plusieurs pages ?  
Vous pouvez vérifier si une ligne permet une répartition sur plusieurs pages en accédant à la `AllowBreakAcrossPages` propriété de la `RowFormat` et vérifier sa valeur.

### Existe-t-il un moyen d’appliquer ce paramètre à tous les tableaux d’un document ?  
Oui, vous pouvez parcourir tous les tableaux du document et appliquer ce paramètre à chacun d'eux.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}