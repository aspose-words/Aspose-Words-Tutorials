---
title: Copier le texte marqué d'un signet dans un document Word
linktitle: Copier le texte marqué d'un signet dans un document Word
second_title: API de traitement de documents Aspose.Words
description: Copiez sans effort le texte marqué d'un signet entre des documents Word à l'aide d'Aspose.Words pour .NET. Découvrez comment procéder avec ce guide étape par étape.
weight: 10
url: /fr/net/programming-with-bookmarks/copy-bookmarked-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Copier le texte marqué d'un signet dans un document Word

## Introduction

Vous avez déjà eu besoin de copier des sections spécifiques d'un document Word vers un autre ? Eh bien, vous avez de la chance ! Dans ce didacticiel, nous vous expliquerons comment copier du texte marqué d'un signet d'un document Word vers un autre à l'aide d'Aspose.Words pour .NET. Que vous créiez un rapport dynamique ou automatisiez la génération de documents, ce guide vous simplifiera le processus.

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Bibliothèque Aspose.Words pour .NET : vous pouvez la télécharger à partir de[ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Visual Studio ou tout autre environnement de développement .NET.
- Connaissances de base de C# : Familiarité avec la programmation C# et le framework .NET.

## Importer des espaces de noms

Pour commencer, assurez-vous que vous avez importé les espaces de noms nécessaires dans votre projet :

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Étape 1 : Charger le document source

Tout d’abord, vous devez charger le document source qui contient le texte marqué comme signet que vous souhaitez copier.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

 Ici,`dataDir` est le chemin d'accès à votre répertoire de documents, et`Bookmarks.docx` est le document source.

## Étape 2 : Identifier le signet

Ensuite, identifiez le signet que vous souhaitez copier à partir du document source.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

 Remplacer`"MyBookmark1"` avec le nom réel de votre signet.

## Étape 3 : Créer le document de destination

Créez maintenant un nouveau document dans lequel le texte marqué comme signet sera copié.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Étape 4 : Importer le contenu ajouté aux favoris

 Pour garantir que les styles et la mise en forme sont préservés, utilisez`NodeImporter` pour importer le contenu marqué d'un signet du document source vers le document de destination.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Étape 5 : définir la méthode AppendBookmarkedText

C'est ici que la magie opère. Définissez une méthode pour gérer la copie du texte marqué d'un signet :

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Étape 6 : Enregistrer le document de destination

Enfin, enregistrez le document de destination pour vérifier le contenu copié.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Conclusion

Et voilà ! Vous avez copié avec succès le texte marqué d'un signet d'un document Word vers un autre à l'aide d'Aspose.Words pour .NET. Cette méthode est très efficace pour automatiser les tâches de manipulation de documents, rendant votre flux de travail plus efficace et rationalisé.

## FAQ

### Puis-je copier plusieurs signets à la fois ?
Oui, vous pouvez parcourir plusieurs signets et utiliser la même méthode pour copier chacun d'eux.

### Que se passe-t-il si le signet n'est pas trouvé ?
 Le`Range.Bookmarks` la propriété reviendra`null`, assurez-vous donc de gérer ce cas pour éviter les exceptions.

### Puis-je conserver la mise en forme du signet d’origine ?
 Absolument ! En utilisant`ImportFormatMode.KeepSourceFormatting` garantit que la mise en forme d'origine est préservée.

### Existe-t-il une limite à la taille du texte marqué comme signet ?
Il n'y a pas de limite spécifique, mais les performances peuvent varier avec des documents extrêmement volumineux.

### Puis-je copier du texte entre différents formats de documents Word ?
Oui, Aspose.Words prend en charge différents formats Word et la méthode fonctionne sur ces formats.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
