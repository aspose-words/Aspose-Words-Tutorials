---
title: Afficher Masquer les signets dans un document Word
linktitle: Afficher Masquer les signets dans un document Word
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment afficher ou masquer dynamiquement des signets dans un document Word à l'aide d'Aspose.Words for .NET avec notre guide étape par étape. Parfait pour les développeurs.
weight: 10
url: /fr/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Afficher Masquer les signets dans un document Word

## Introduction

Avez-vous déjà eu besoin de masquer ou d'afficher dynamiquement certaines parties de votre document Word ? Eh bien, vous avez de la chance ! Avec Aspose.Words pour .NET, vous pouvez facilement gérer la visibilité du contenu mis en signet dans vos documents. Ce didacticiel vous guidera tout au long du processus d'affichage et de masquage des signets dans un document Word à l'aide d'Aspose.Words pour .NET. Nous détaillerons le code étape par étape. Ainsi, que vous soyez un développeur chevronné ou un débutant, vous trouverez ce guide facile à suivre.

## Conditions préalables

Avant de plonger dans le code, assurons-nous que vous disposez de tout ce dont vous avez besoin :

1.  Aspose.Words for .NET : assurez-vous que la bibliothèque Aspose.Words for .NET est installée. Sinon, vous pouvez le télécharger[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : un IDE comme Visual Studio.
3. Connaissance de base de C# : Une connaissance de la programmation C# sera bénéfique.
4. Un document Word : un exemple de document Word avec des signets.

## Importer des espaces de noms

Avant de commencer avec le code, vous devez importer les espaces de noms nécessaires. Ajoutez ce qui suit au début de votre fichier C# :

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Étape 1 : Chargez votre document

Tout d’abord, vous devez charger le document Word contenant les signets. Voici comment procéder :

```csharp
// Le chemin d'accès au répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Explication

- dataDir : Il s'agit du chemin du répertoire où se trouve votre document Word.
-  Document doc : Ceci initialise une nouvelle instance du`Document` classe avec votre fichier spécifié.

## Étape 2 : Afficher ou masquer le contenu mis en favoris

Ensuite, nous définirons une méthode pour afficher ou masquer le contenu mis en signet. Voici la méthode complète :

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD bookmark}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Explication

- Bookmark bm : récupère le signet du document.
- Générateur DocumentBuilder : aide à naviguer et à modifier le document.
- Champ Champ : Insère un champ IF pour vérifier l'état du signet.
- Node currentNode : parcourt les nœuds pour trouver le début et la fin du champ.

## Étape 3 : Exécuter la fonction Afficher/Masquer

 Maintenant, tu dois appeler le`ShowHideBookmarkedContent` méthode, en passant le document, le nom du signet et l'indicateur de visibilité :

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Explication

- doc : votre objet document.
- "MyBookmark1" : Le nom du signet que vous souhaitez afficher/masquer.
- false : l'indicateur de visibilité (true pour afficher, false pour masquer).

## Étape 4 : Enregistrez votre document

Enfin, enregistrez le document modifié :

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Explication

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Le chemin et le nom du nouveau document dans lequel les modifications seront enregistrées.

## Conclusion

Et voila! Vous avez appris avec succès comment afficher et masquer les signets dans un document Word à l'aide d'Aspose.Words pour .NET. Cette technique peut être incroyablement utile pour générer dynamiquement des documents avec un contenu conditionnel.

## FAQ

### Qu’est-ce qu’Aspose.Words pour .NET ?
Aspose.Words for .NET est une puissante bibliothèque de traitement de documents qui permet aux développeurs de créer, modifier et convertir des documents Word par programme.

### Comment puis-je obtenir Aspose.Words pour .NET ?
 Vous pouvez télécharger Aspose.Words pour .NET à partir de[ici](https://releases.aspose.com/words/net/). Un essai gratuit est également disponible.

### Puis-je utiliser cette méthode pour d’autres types de signets ?
Oui, cette méthode peut être adaptée pour gérer la visibilité des éventuels signets de votre document Word.

### Que faire si mon document ne contient pas le signet spécifié ?
Si le signet n'existe pas, la méthode générera une erreur. Assurez-vous que le signet existe avant d’essayer de l’afficher/masquer.

### Comment puis-je obtenir de l'aide si je rencontre des problèmes ?
 Vous pouvez obtenir le soutien de la communauté Aspose[ici](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
