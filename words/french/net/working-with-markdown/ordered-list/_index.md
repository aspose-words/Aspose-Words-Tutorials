---
title: Liste ordonnée
linktitle: Liste ordonnée
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment créer des listes ordonnées dans des documents Word à l'aide d'Aspose.Words pour .NET grâce à notre guide étape par étape. Idéal pour automatiser la création de documents.
weight: 10
url: /fr/net/working-with-markdown/ordered-list/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Liste ordonnée

## Introduction

Vous avez donc décidé de vous lancer dans Aspose.Words pour .NET pour créer de superbes documents Word par programmation. Excellent choix ! Aujourd'hui, nous allons vous expliquer comment créer une liste ordonnée dans un document Word. Nous procéderons étape par étape, donc que vous soyez un débutant en codage ou un professionnel chevronné, vous trouverez ce guide très utile. Commençons !

## Prérequis

Avant de plonger dans le code, vous aurez besoin de quelques éléments :

1. Aspose.Words pour .NET : assurez-vous d'avoir installé Aspose.Words pour .NET. Si ce n'est pas le cas, vous pouvez le télécharger[ici](https://releases.aspose.com/words/net/).
2. Environnement de développement : Visual Studio ou tout autre IDE compatible .NET.
3. Connaissances de base de C# : vous devez être à l’aise avec les bases de C# pour suivre facilement.

## Importer des espaces de noms

Pour utiliser Aspose.Words dans votre projet, vous devez importer les espaces de noms nécessaires. Cela revient à configurer votre boîte à outils avant de commencer à travailler.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
```

Décomposons le code en petites étapes et expliquons chaque partie. Prêt ? C'est parti !

## Étape 1 : Initialiser le document

Tout d’abord, vous devez créer un nouveau document. Considérez cela comme l’ouverture d’un document Word vierge sur votre ordinateur.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ici, nous initialisons un nouveau document et un objet DocumentBuilder. Le DocumentBuilder est comme votre stylo, vous permettant d'écrire du contenu dans le document.

## Étape 2 : Appliquer le format de liste numérotée

Appliquons maintenant un format de liste numérotée par défaut. Cela revient à configurer votre document Word pour utiliser des puces numérotées.

```csharp
builder.ListFormat.ApplyNumberDefault();
```

Cette ligne de code définit la numérotation de votre liste. Facile, n'est-ce pas ?

## Étape 3 : Ajouter des éléments à la liste

Ensuite, ajoutons quelques articles à notre liste. Imaginez que vous êtes en train de rédiger une liste de courses.

```csharp
builder.Writeln("Item 1");
builder.Writeln("Item 2");
```

Avec ces lignes, vous ajoutez les deux premiers éléments à votre liste.

## Étape 4 : indenter la liste

Et si vous souhaitez ajouter des sous-éléments sous un élément ? Faisons-le !

```csharp
builder.ListFormat.ListIndent();

builder.Writeln("Item 2a");
builder.Writeln("Item 2b");
```

 Le`ListIndent` La méthode indente la liste, créant ainsi une sous-liste. Vous créez maintenant une liste hiérarchique, un peu comme une liste de tâches imbriquée.

## Conclusion

Créer une liste ordonnée dans un document Word par programmation peut sembler intimidant au début, mais avec Aspose.Words pour .NET, c'est un jeu d'enfant. En suivant ces étapes simples, vous pouvez facilement ajouter et gérer des listes dans vos documents. Que vous génériez des rapports, créiez des documents structurés ou automatisiez simplement vos flux de travail, Aspose.Words pour .NET est là pour vous. Alors, pourquoi attendre ? Commencez à coder et voyez la magie opérer !

## FAQ

### Puis-je personnaliser le style de numérotation de la liste ?  
 Oui, vous pouvez personnaliser le style de numérotation à l'aide du`ListFormat`propriétés. Vous pouvez définir différents styles de numérotation comme des chiffres romains, des lettres, etc.

### Comment ajouter plus de niveaux d’indentation ?  
 Vous pouvez utiliser le`ListIndent` méthode plusieurs fois pour créer des niveaux plus profonds de sous-listes. Chaque appel à`ListIndent` ajoute un niveau d'indentation.

### Puis-je mélanger des puces et des listes numérotées ?  
 Absolument ! Vous pouvez appliquer différents formats de liste dans le même document à l'aide de la`ListFormat` propriété.

### Est-il possible de continuer la numérotation à partir d'une liste précédente ?  
Oui, vous pouvez continuer à numéroter en utilisant le même format de liste. Aspose.Words vous permet de contrôler la numérotation des listes sur différents paragraphes.

### Comment puis-je supprimer le format de liste ?  
 Vous pouvez supprimer le format de liste en appelant`ListFormat.RemoveNumbers()`Cela transformera les éléments de la liste en paragraphes normaux.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
