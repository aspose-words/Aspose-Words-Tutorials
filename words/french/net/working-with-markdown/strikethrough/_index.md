---
"description": "Apprenez à appliquer une mise en forme barrée à du texte avec Aspose.Words pour .NET grâce à notre guide étape par étape. Améliorez vos compétences en traitement de documents."
"linktitle": "Barré"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Barré"
"url": "/fr/net/working-with-markdown/strikethrough/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Barré

## Introduction

Bienvenue dans ce guide détaillé expliquant comment appliquer la mise en forme barrée à du texte avec Aspose.Words pour .NET. Si vous souhaitez améliorer vos compétences en traitement de documents et apporter une touche unique à votre texte, vous êtes au bon endroit. C'est parti !

## Prérequis

Avant de commencer, assurez-vous de disposer des éléments suivants :

- Aspose.Words pour .NET : téléchargez-le [ici](https://releases.aspose.com/words/net/).
- .NET Framework : assurez-vous que .NET Framework est installé sur votre système.
- Environnement de développement : un IDE comme Visual Studio.
- Connaissances de base en C# : Une familiarité avec la programmation C# est nécessaire.

## Importer des espaces de noms

Pour commencer, vous devrez importer les espaces de noms nécessaires. Ils sont essentiels pour accéder à la bibliothèque Aspose.Words et à ses fonctionnalités.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Initialiser DocumentBuilder

Le `DocumentBuilder` class est un outil puissant dans Aspose.Words qui vous permet d'ajouter facilement du contenu à votre document.

```csharp
// Initialiser un DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Étape 2 : définir la propriété Barré

Appliquons maintenant la propriété barrée à notre texte. Cela implique de définir `StrikeThrough` propriété de la `Font` s'opposer à `true`.

```csharp
// Barré le texte.
builder.Font.StrikeThrough = true;
```

## Étape 3 : Écrivez du texte barré

Avec la propriété barrée définie, nous pouvons maintenant ajouter notre texte. `Writeln` la méthode ajoutera le texte au document.

```csharp
// Écrivez du texte barré.
builder.Writeln("This text will be StrikeThrough");
```

## Conclusion

Et voilà ! Vous avez réussi à ajouter la mise en forme barrée à votre texte grâce à Aspose.Words pour .NET. Cette puissante bibliothèque ouvre un monde de possibilités pour le traitement et la personnalisation de vos documents. Que vous créiez des rapports, des lettres ou tout autre type de document, la maîtrise de ces fonctionnalités améliorera sans aucun doute votre productivité et la qualité de vos résultats.

## FAQ

### Qu'est-ce qu'Aspose.Words pour .NET ?
Aspose.Words pour .NET est une puissante bibliothèque de traitement de documents qui permet aux développeurs de créer, manipuler et convertir des documents Word par programmation.

### Puis-je utiliser Aspose.Words pour .NET dans un projet commercial ?
Oui, vous pouvez utiliser Aspose.Words pour .NET dans des projets commerciaux. Pour connaître les options d'achat, consultez le site [page d'achat](https://purchase.aspose.com/buy).

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?
Oui, vous pouvez télécharger un essai gratuit [ici](https://releases.aspose.com/).

### Comment obtenir de l'assistance pour Aspose.Words pour .NET ?
Vous pouvez obtenir le soutien de la communauté Aspose et des experts sur le [forum d'assistance](https://forum.aspose.com/c/words/8).

### Puis-je appliquer d’autres options de formatage de texte à l’aide d’Aspose.Words pour .NET ?
Absolument ! Aspose.Words pour .NET prend en charge un large éventail d'options de mise en forme de texte, notamment le gras, l'italique, le soulignement, etc.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}