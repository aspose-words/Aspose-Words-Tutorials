---
"description": "Apprenez à fractionner des tableaux dans des documents Word avec Aspose.Words pour .NET. Notre guide étape par étape simplifie et optimise la gestion des tableaux."
"linktitle": "Table divisée"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Table divisée"
"url": "/fr/net/programming-with-tables/split-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Table divisée

## Introduction

Avez-vous déjà travaillé avec un grand tableau dans un document Word et souhaité le diviser en deux tableaux plus petits et plus faciles à gérer ? Aujourd'hui, nous allons voir comment y parvenir avec Aspose.Words pour .NET. Que vous ayez affaire à des tableaux de données volumineux ou à des structures de documents complexes, le fractionnement des tableaux peut améliorer la lisibilité et l'organisation. Explorons la procédure étape par étape pour fractionner un tableau avec Aspose.Words pour .NET.

## Prérequis

Avant de commencer le didacticiel, assurez-vous de disposer des éléments suivants :

1. Bibliothèque Aspose.Words pour .NET : Assurez-vous d'avoir téléchargé et installé la bibliothèque Aspose.Words pour .NET. Vous pouvez l'obtenir sur le site [Page de publication d'Aspose](https://releases.aspose.com/words/net/).
2. Environnement de développement : configurez un environnement de développement avec prise en charge de .NET Framework, tel que Visual Studio.
3. Exemple de document : Préparez un document Word (`Tables.docx`) avec au moins une table pour appliquer l'opération de fractionnement.

## Importer des espaces de noms

Tout d'abord, importez les espaces de noms nécessaires dans votre projet. Cela vous permettra d'accéder aux classes et méthodes fournies par Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Étape 1 : Charger le document

Commençons par charger le document contenant le tableau à fractionner. Assurez-vous de spécifier le chemin d'accès correct à votre document.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Étape 2 : Identifier la table à diviser

Ensuite, identifiez et récupérez la table à fractionner. Dans cet exemple, nous ciblerons la première table du document.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Étape 3 : Sélectionnez la ligne à fractionner

Déterminez la ligne où vous souhaitez diviser le tableau. Ici, nous divisons le tableau à partir de la troisième ligne (incluse).

```csharp
Row row = firstTable.Rows[2];
```

## Étape 4 : Créer un nouveau conteneur de table

Créez un nouveau conteneur de table pour contenir les lignes qui seront déplacées de la table d'origine.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Étape 5 : Insérer le nouveau conteneur de table

Insérez le nouveau conteneur de table juste après la table d’origine dans le document.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Étape 6 : ajouter un paragraphe tampon

Ajoutez un paragraphe tampon entre les deux tableaux pour garantir qu'ils restent séparés.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## Étape 7 : Déplacer les lignes vers la nouvelle table

Déplacer les lignes de la table d'origine vers le nouveau conteneur. Cette boucle se poursuit jusqu'à ce que la ligne spécifiée (inclusivement) soit déplacée.

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## Étape 8 : Enregistrer le document

Enfin, enregistrez le document modifié avec les tableaux divisés.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Conclusion

Et voilà ! En suivant ces étapes, vous pouvez facilement fractionner un tableau dans un document Word avec Aspose.Words pour .NET. Cette approche vous permet de gérer plus efficacement les tableaux volumineux, améliorant ainsi la lisibilité et l'organisation de vos documents. Essayez-la et constatez à quel point elle simplifie votre travail avec les tableaux dans vos documents Word.

## FAQ

### Puis-je diviser un tableau en plusieurs lignes ?
Oui, vous pouvez diviser un tableau en plusieurs lignes en répétant le processus pour chaque point de division.

### Qu'advient-il de la mise en forme du tableau d'origine ?
Le nouveau tableau hérite de la mise en forme du tableau d'origine. Toute modification de mise en forme spécifique peut être appliquée au nouveau tableau selon les besoins.

### Est-il possible de fusionner à nouveau des tables ?
Oui, vous pouvez fusionner des tables en déplaçant des lignes d'une table à une autre à l'aide de méthodes similaires.

### Cette méthode fonctionne-t-elle avec des tableaux imbriqués ?
Oui, Aspose.Words pour .NET prend également en charge les opérations sur les tables imbriquées.

### Puis-je automatiser ce processus pour plusieurs documents ?
Absolument ! Vous pouvez créer un script ou une application pour automatiser le fractionnement de tableaux pour plusieurs documents.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}