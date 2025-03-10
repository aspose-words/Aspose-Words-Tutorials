---
title: Barré
linktitle: Barré
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment appliquer une mise en forme barrée au texte à l'aide d'Aspose.Words pour .NET grâce à notre guide étape par étape. Améliorez vos compétences en matière de traitement de documents.
weight: 10
url: /fr/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Barré

## Introduction

Bienvenue dans ce guide détaillé sur la façon d'appliquer une mise en forme barrée au texte à l'aide d'Aspose.Words pour .NET. Si vous cherchez à améliorer vos compétences en matière de traitement de documents et à ajouter une touche unique à votre texte, vous êtes au bon endroit. Plongeons-nous dans le vif du sujet !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

-  Aspose.Words pour .NET : Téléchargez-le[ici](https://releases.aspose.com/words/net/).
- .NET Framework : assurez-vous que .NET Framework est installé sur votre système.
- Environnement de développement : un IDE comme Visual Studio.
- Connaissances de base de C# : Une familiarité avec la programmation C# est nécessaire.

## Importer des espaces de noms

Pour commencer, vous devrez importer les espaces de noms nécessaires. Ceux-ci sont essentiels pour accéder à la bibliothèque Aspose.Words et à ses fonctionnalités.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Initialiser le DocumentBuilder

 Le`DocumentBuilder` class est un outil puissant dans Aspose.Words qui vous permet d'ajouter facilement du contenu à votre document.

```csharp
// Initialiser un DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Étape 2 : définir la propriété Barré

Appliquons maintenant la propriété strikethrough à notre texte. Cela implique de définir la`StrikeThrough` propriété de la`Font` s'opposer à`true`.

```csharp
// Barré le texte.
builder.Font.StrikeThrough = true;
```

## Étape 3 : Écrivez du texte barré

 Avec la propriété barrée définie, nous pouvons maintenant ajouter notre texte.`Writeln` la méthode ajoutera le texte au document.

```csharp
// Écrivez du texte barré.
builder.Writeln("This text will be StrikeThrough");
```

## Conclusion

Et voilà ! Vous avez ajouté avec succès une mise en forme barrée à votre texte à l'aide d'Aspose.Words pour .NET. Cette puissante bibliothèque ouvre un monde de possibilités pour le traitement et la personnalisation des documents. Que vous créiez des rapports, des lettres ou tout autre type de document, la maîtrise de ces fonctionnalités améliorera sans aucun doute votre productivité et la qualité de vos résultats.

## FAQ

### Qu'est-ce que Aspose.Words pour .NET ?
Aspose.Words pour .NET est une puissante bibliothèque de traitement de documents qui permet aux développeurs de créer, manipuler et convertir des documents Word par programmation.

### Puis-je utiliser Aspose.Words pour .NET dans un projet commercial ?
 Oui, vous pouvez utiliser Aspose.Words pour .NET dans des projets commerciaux. Pour connaître les options d'achat, visitez le site[page d'achat](https://purchase.aspose.com/buy).

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?
 Oui, vous pouvez télécharger une version d'essai gratuite[ici](https://releases.aspose.com/).

### Comment obtenir de l'assistance pour Aspose.Words pour .NET ?
Vous pouvez obtenir le soutien de la communauté Aspose et des experts sur le[Forum de soutien](https://forum.aspose.com/c/words/8).

### Puis-je appliquer d’autres options de formatage de texte à l’aide d’Aspose.Words pour .NET ?
Absolument ! Aspose.Words pour .NET prend en charge une large gamme d'options de formatage de texte, notamment le gras, l'italique, le soulignement, etc.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
