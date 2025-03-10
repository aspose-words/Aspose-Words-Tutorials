---
title: Insérer un document lors du publipostage
linktitle: Insérer un document lors du publipostage
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment insérer des documents dans des champs de publipostage à l'aide d'Aspose.Words pour .NET dans ce didacticiel complet, étape par étape.
weight: 10
url: /fr/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insérer un document lors du publipostage

## Introduction

Bienvenue dans le monde de l'automatisation des documents avec Aspose.Words pour .NET ! Vous êtes-vous déjà demandé comment insérer dynamiquement des documents dans des champs spécifiques d'un document principal lors d'une opération de publipostage ? Eh bien, vous êtes au bon endroit. Ce didacticiel vous guidera étape par étape dans le processus d'insertion de documents dans des champs de publipostage à l'aide d'Aspose.Words pour .NET. C'est comme assembler les pièces d'un puzzle, où chaque pièce s'emboîte parfaitement. Alors, plongeons-nous !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

1.  Aspose.Words pour .NET : vous pouvez[téléchargez la dernière version ici](https://releases.aspose.com/words/net/) . Si vous devez acheter une licence, vous pouvez le faire[ici](https://purchase.aspose.com/buy) . Alternativement, vous pouvez obtenir un[permis temporaire](https://purchase.aspose.com/temporary-license/) ou essayez-le avec un[essai gratuit](https://releases.aspose.com/).
2. Environnement de développement : Visual Studio ou tout autre IDE C#.
3. Connaissances de base de C# : la familiarité avec la programmation C# fera de ce tutoriel un jeu d'enfant.

## Importer des espaces de noms

Tout d'abord, vous devez importer les espaces de noms nécessaires. Ceux-ci sont en quelque sorte les éléments de base de votre projet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Décomposons le processus en étapes faciles à gérer. Chaque étape s'appuiera sur la précédente pour vous conduire à une solution complète.

## Étape 1 : Configuration de votre répertoire

Avant de pouvoir commencer à insérer des documents, vous devez définir le chemin d'accès à votre répertoire de documents. C'est là que vos documents sont stockés.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Chargement du document principal

Ensuite, vous chargez le document principal. Ce document contient les champs de fusion dans lesquels d'autres documents seront insérés.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Étape 3 : Définition du rappel de fusion de champs

Pour gérer le processus de fusion, vous devez définir une fonction de rappel. Cette fonction sera chargée d'insérer les documents dans les champs de fusion spécifiés.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Étape 4 : Exécution du publipostage

Il est maintenant temps d'exécuter le publipostage. C'est là que la magie opère. Vous devez spécifier le champ de fusion et le document qui doit être inséré dans ce champ.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Étape 5 : enregistrement du document

Une fois le publipostage terminé, vous enregistrez le document modifié. Ce nouveau document contiendra le contenu inséré exactement là où vous le souhaitez.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Étape 6 : création du gestionnaire de rappel

Le gestionnaire de rappel est une classe qui effectue un traitement spécial pour le champ de fusion. Il charge le document spécifié dans la valeur du champ et l'insère dans le champ de fusion actuel.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Étape 7 : Insertion du document

Cette méthode insère le document spécifié dans le paragraphe ou la cellule de tableau actuel.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Conclusion

Et voilà ! Vous avez réussi à insérer des documents dans des champs spécifiques lors d'une opération de publipostage à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité puissante peut vous faire gagner beaucoup de temps et d'efforts, en particulier lorsque vous traitez de gros volumes de documents. Considérez-la comme un assistant personnel qui s'occupe de tout le travail à votre place. Alors, allez-y et essayez-la. Bon codage !

## FAQ

### Puis-je insérer plusieurs documents dans différents champs de fusion ?
Oui, vous pouvez. Spécifiez simplement les champs de fusion appropriés et les chemins de document correspondants dans le`MailMerge.Execute` méthode.

### Est-il possible de formater le document inséré différemment du document principal ?
 Absolument ! Vous pouvez utiliser le`ImportFormatMode` paramètre dans le`NodeImporter` pour contrôler le formatage.

### Que faire si le nom du champ de fusion est dynamique ?
Vous pouvez gérer les noms de champs de fusion dynamiques en les transmettant comme paramètres au gestionnaire de rappel.

### Puis-je utiliser cette méthode avec différents formats de fichiers ?
Oui, Aspose.Words prend en charge divers formats de fichiers, notamment DOCX, PDF, etc.

### Comment gérer les erreurs lors du processus d’insertion de documents ?
Implémentez la gestion des erreurs dans votre gestionnaire de rappel pour gérer toutes les exceptions pouvant survenir.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
