---
title: Tableau divisé
linktitle: Tableau divisé
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment fractionner des tableaux dans des documents Word à l'aide d'Aspose.Words pour .NET. Notre guide étape par étape rend la gestion des tableaux simple et efficace.
weight: 10
url: /fr/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tableau divisé

## Introduction

Vous êtes-vous déjà retrouvé à travailler avec un grand tableau dans un document Word et vous avez souhaité pouvoir le diviser en deux tableaux plus petits et plus faciles à gérer ? Aujourd'hui, nous allons vous expliquer comment y parvenir à l'aide d'Aspose.Words pour .NET. Que vous ayez affaire à des tableaux de données volumineux ou à des structures de documents complexes, le fractionnement des tableaux peut contribuer à améliorer la lisibilité et l'organisation. Explorons le processus étape par étape pour diviser un tableau à l'aide d'Aspose.Words pour .NET.

## Prérequis

Avant de passer au didacticiel, assurez-vous de disposer des éléments suivants :

1.  Bibliothèque Aspose.Words pour .NET : assurez-vous d'avoir téléchargé et installé la bibliothèque Aspose.Words pour .NET. Vous pouvez l'obtenir à partir du[Page de sortie d'Aspose](https://releases.aspose.com/words/net/).
2. Environnement de développement : configurez un environnement de développement avec prise en charge de .NET Framework, tel que Visual Studio.
3. Exemple de document : Préparez un document Word (`Tables.docx`) avec au moins une table pour appliquer l'opération de fractionnement.

## Importer des espaces de noms

Tout d'abord, importez les espaces de noms nécessaires à votre projet. Cela vous permet d'accéder aux classes et méthodes fournies par Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Étape 1 : Charger le document

Commençons par charger le document contenant le tableau que vous souhaitez diviser. Assurez-vous de spécifier le chemin correct vers votre document.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Étape 2 : Identifier la table à diviser

Ensuite, identifiez et récupérez la table que vous souhaitez fractionner. Dans cet exemple, nous ciblerons la première table du document.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Étape 3 : sélectionnez la ligne à fractionner

Déterminez la ligne sur laquelle vous souhaitez diviser le tableau. Ici, nous divisons le tableau à partir de la troisième ligne (incluse).

```csharp
Row row = firstTable.Rows[2];
```

## Étape 4 : Créer un nouveau conteneur de table

Créez un nouveau conteneur de table pour contenir les lignes qui seront déplacées de la table d'origine.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Étape 5 : insérer le nouveau conteneur de table

Insérez le nouveau conteneur de table juste après la table d’origine dans le document.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Étape 6 : ajouter un paragraphe tampon

Ajoutez un paragraphe tampon entre les deux tableaux pour garantir qu’ils restent séparés.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## Étape 7 : Déplacer les lignes vers la nouvelle table

Déplacez les lignes de la table d'origine vers le nouveau conteneur de table. Cette boucle continue jusqu'à ce que la ligne spécifiée (inclusive) soit déplacée.

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## Étape 8 : Enregistrer le document

Enfin, enregistrez le document modifié avec les tableaux divisés.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement fractionner un tableau dans un document Word à l'aide d'Aspose.Words pour .NET. Cette approche vous aide à gérer plus efficacement les tableaux volumineux, améliorant ainsi la lisibilité et l'organisation de vos documents. Essayez-le et voyez comment il simplifie votre travail avec les tableaux dans les documents Word.

## FAQ

### Puis-je diviser un tableau en plusieurs lignes ?
Oui, vous pouvez diviser un tableau en plusieurs lignes en répétant le processus pour chaque point de division.

### Qu'advient-il de la mise en forme du tableau d'origine ?
Le nouveau tableau hérite de la mise en forme du tableau d'origine. Toute modification de mise en forme spécifique peut être appliquée au nouveau tableau selon les besoins.

### Est-il possible de fusionner à nouveau des tables ?
Oui, vous pouvez fusionner des tables en déplaçant des lignes d'une table à une autre en utilisant des méthodes similaires.

### Cette méthode fonctionne-t-elle avec des tableaux imbriqués ?
Oui, Aspose.Words pour .NET prend également en charge les opérations sur les tables imbriquées.

### Puis-je automatiser ce processus pour plusieurs documents ?
Absolument ! Vous pouvez créer un script ou une application pour automatiser le processus de fractionnement de tableau pour plusieurs documents.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
