---
"description": "Découvrez comment afficher et masquer le contenu marqué d'un signet dans les documents Word à l'aide d'Aspose.Words pour .NET avec ce guide détaillé étape par étape."
"linktitle": "Afficher/Masquer le contenu marqué d'un signet dans un document Word"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Afficher/Masquer le contenu marqué d'un signet dans un document Word"
"url": "/fr/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Afficher/Masquer le contenu marqué d'un signet dans un document Word

## Introduction

Prêt à vous lancer dans la manipulation de documents avec Aspose.Words pour .NET ? Que vous soyez développeur souhaitant automatiser vos tâches documentaires ou simplement curieux de manipuler des fichiers Word par programmation, vous êtes au bon endroit. Aujourd'hui, nous allons découvrir comment afficher et masquer le contenu marqué d'un signet dans un document Word avec Aspose.Words pour .NET. Ce guide étape par étape vous permettra de maîtriser la visibilité du contenu grâce aux signets. C'est parti !

## Prérequis

Avant de passer aux choses sérieuses, voici quelques éléments dont vous aurez besoin :

1. Visual Studio : toute version compatible avec .NET.
2. Aspose.Words pour .NET : téléchargez-le [ici](https://releases.aspose.com/words/net/).
3. Compréhension de base de C# : si vous pouvez écrire un programme simple « Hello World », vous êtes prêt à partir.
4. Un document Word avec des signets : nous utiliserons un exemple de document avec des signets pour ce didacticiel.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires. Cela nous permettra de disposer de tous les outils nécessaires à notre tâche.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Avec ces espaces de noms en place, nous sommes tous prêts à commencer notre voyage.

## Étape 1 : Configuration de votre projet

Très bien, commençons par configurer notre projet dans Visual Studio.

### Créer un nouveau projet

Ouvrez Visual Studio et créez un projet d'application console (.NET Core). Nommez-le de manière accrocheuse, par exemple « BookmarkVisibilityManager ».

### Ajouter Aspose.Words pour .NET

Vous devrez ajouter Aspose.Words pour .NET à votre projet. Pour ce faire, utilisez le gestionnaire de packages NuGet.

1. Accédez à Outils > Gestionnaire de packages NuGet > Gérer les packages NuGet pour la solution.
2. Recherchez « Aspose.Words ».
3. Installez le package.

Super ! Maintenant que notre projet est configuré, passons au chargement de notre document.

## Étape 2 : Chargement du document

Nous devons charger le document Word contenant les signets. Pour ce tutoriel, nous utiliserons un exemple de document nommé « Signets.docx ».

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Cet extrait de code définit le chemin d'accès à votre répertoire de documents et charge le document dans le `doc` objet.

## Étape 3 : Afficher/Masquer le contenu ajouté aux favoris

Vient maintenant la partie amusante : afficher ou masquer le contenu en fonction des favoris. Nous allons créer une méthode appelée `ShowHideBookmarkedContent` pour gérer ça.

Voici la méthode qui permettra de basculer la visibilité du contenu marqué :

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### Décomposition de la méthode

- Récupération de signets : `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` récupère le signet.
- Traversée de nœuds : nous parcourons les nœuds à l’intérieur du signet.
- Basculement de visibilité : si le nœud est un `Run` (une série de texte contiguë), nous définissons son `Hidden` propriété.

## Étape 4 : Application de la méthode

Avec notre méthode en place, appliquons-la pour afficher ou masquer du contenu en fonction d'un signet.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Cette ligne de code masquera le contenu du signet nommé « MyBookmark1 ».

## Étape 5 : Enregistrement du document

Enfin, sauvegardons notre document modifié.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Cela enregistre le document avec les modifications que nous avons apportées.

## Conclusion

Et voilà ! Vous venez d'apprendre à afficher et masquer le contenu marqué d'un signet dans un document Word avec Aspose.Words pour .NET. Cet outil puissant simplifie la manipulation des documents, que vous automatisiez des rapports, créiez des modèles ou amélioriez simplement vos fichiers Word. Bon codage !

## FAQ

### Puis-je activer plusieurs signets à la fois ?
Oui, vous pouvez appeler le `ShowHideBookmarkedContent` méthode pour chaque signet que vous souhaitez activer/désactiver.

### Le masquage du contenu affecte-t-il la structure du document ?
Non, masquer du contenu n'affecte que sa visibilité. Le contenu reste dans le document.

### Puis-je utiliser cette méthode pour d’autres types de contenu ?
Cette méthode active spécifiquement les exécutions de texte. Pour les autres types de contenu, vous devrez modifier la logique de parcours des nœuds.

### Aspose.Words pour .NET est-il gratuit ?
Aspose.Words propose un essai gratuit [ici](https://releases.aspose.com/), mais une licence complète est requise pour une utilisation en production. Vous pouvez l'acheter. [ici](https://purchase.aspose.com/buy).

### Comment puis-je obtenir de l’aide si je rencontre des problèmes ?
Vous pouvez obtenir du soutien de la communauté Aspose [ici](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}