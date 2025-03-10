---
title: Vérifiez l'effet de texte DrawingML
linktitle: Vérifiez l'effet de texte DrawingML
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment vérifier les effets de texte DrawingML dans les documents Word à l'aide d'Aspose.Words pour .NET grâce à notre guide détaillé, étape par étape. Améliorez vos documents en toute simplicité.
weight: 10
url: /fr/net/working-with-fonts/check-drawingml-text-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vérifiez l'effet de texte DrawingML

## Introduction

Bienvenue dans un autre tutoriel détaillé sur l'utilisation d'Aspose.Words pour .NET ! Aujourd'hui, nous plongeons dans le monde fascinant des effets de texte DrawingML. Que vous cherchiez à améliorer vos documents Word avec des ombres, des reflets ou des effets 3D, ce guide vous montrera comment vérifier ces effets de texte dans vos documents à l'aide d'Aspose.Words pour .NET. Commençons !

## Prérequis

Avant de passer au didacticiel, vous devez remplir quelques conditions préalables :

-  Bibliothèque Aspose.Words pour .NET : assurez-vous que la bibliothèque Aspose.Words pour .NET est installée. Vous pouvez la télécharger à partir du[Page de sortie d'Aspose](https://releases.aspose.com/words/net/).
- Environnement de développement : vous devez disposer d’un environnement de développement configuré, tel que Visual Studio.
- Connaissances de base de C# : Une certaine familiarité avec la programmation C# sera utile.

## Importer des espaces de noms

Tout d'abord, vous devez importer les espaces de noms nécessaires. Ces espaces de noms vous donneront accès aux classes et méthodes requises pour manipuler les documents Word et vérifier les effets de texte DrawingML.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Guide étape par étape pour vérifier les effets de texte de DrawingML

Maintenant, décomposons le processus en plusieurs étapes, ce qui le rendra plus facile à suivre.

## Étape 1 : Charger le document

La première étape consiste à charger le document Word dans lequel vous souhaitez vérifier les effets de texte DrawingML. 

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

Cet extrait de code charge le document nommé « DrawingML text effects.docx » à partir de votre répertoire spécifié.

## Étape 2 : Accéder à la collection Runs

Ensuite, nous devons accéder à la collection d'exécutions dans le premier paragraphe du document. Les exécutions sont des portions de texte avec le même formatage.

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

Cette ligne de code récupère les exécutions du premier paragraphe de la première section du document.

## Étape 3 : Obtenir la police de la première exécution

Nous allons maintenant récupérer les propriétés de police de la première exécution dans la collection d'exécutions. Cela nous permet de vérifier les différents effets de texte DrawingML appliqués au texte.

```csharp
Font runFont = runs[0].Font;
```

## Étape 4 : vérifier les effets de texte DrawingML

Enfin, nous pouvons vérifier différents effets de texte DrawingML tels que l'ombre, l'effet 3D, la réflexion, le contour et le remplissage.

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

 Ces lignes de code s'imprimeront`true` ou`false` selon que chaque effet de texte DrawingML spécifique est appliqué ou non à la police de l'exécution.

## Conclusion

Félicitations ! Vous venez d'apprendre à vérifier les effets de texte DrawingML dans les documents Word à l'aide d'Aspose.Words pour .NET. Cette fonctionnalité puissante vous permet de détecter et de manipuler par programmation une mise en forme de texte sophistiquée, vous offrant ainsi un meilleur contrôle sur vos tâches de traitement de documents.


## FAQ

### Qu'est-ce qu'un effet de texte DrawingML ?
Les effets de texte DrawingML sont des options de formatage de texte avancées dans les documents Word, notamment les ombres, les effets 3D, les reflets, les contours et les remplissages.

### Puis-je appliquer des effets de texte DrawingML à l'aide d'Aspose.Words pour .NET ?
Oui, Aspose.Words pour .NET vous permet à la fois de vérifier et d'appliquer les effets de texte DrawingML par programmation.

### Ai-je besoin d'une licence pour utiliser Aspose.Words pour .NET ?
 Oui, Aspose.Words pour .NET nécessite une licence pour bénéficier de toutes les fonctionnalités. Vous pouvez obtenir une[permis temporaire](https://purchase.aspose.com/temporary-license/) pour évaluation.

### Existe-t-il un essai gratuit disponible pour Aspose.Words pour .NET ?
 Oui, vous pouvez télécharger un[essai gratuit](https://releases.aspose.com/) pour essayer Aspose.Words pour .NET avant d'acheter.

### Où puis-je trouver plus de documentation sur Aspose.Words pour .NET ?
 Vous trouverez une documentation détaillée sur le[Page de documentation d'Aspose.Words pour .NET](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
