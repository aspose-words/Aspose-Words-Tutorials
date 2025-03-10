---
title: Rapport hauteur/largeur verrouillé
linktitle: Rapport hauteur/largeur verrouillé
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment verrouiller le rapport hauteur/largeur des formes dans les documents Word à l'aide d'Aspose.Words pour .NET. Suivez ce guide étape par étape pour conserver les proportions de vos images et formes.
weight: 10
url: /fr/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rapport hauteur/largeur verrouillé

## Introduction

Vous êtes-vous déjà demandé comment conserver les proportions parfaites des images et des formes dans vos documents Word ? Parfois, vous devez vous assurer que vos images et vos formes ne se déforment pas lorsqu'elles sont redimensionnées. C'est là que le verrouillage du rapport hauteur/largeur s'avère utile. Dans ce didacticiel, nous allons découvrir comment définir le rapport hauteur/largeur des formes dans les documents Word à l'aide d'Aspose.Words pour .NET. Nous allons le décomposer en étapes faciles à suivre, afin que vous puissiez appliquer ces compétences à vos projets en toute confiance.

## Prérequis

Avant de plonger dans le code, passons en revue ce dont vous avez besoin pour commencer :

- Bibliothèque Aspose.Words pour .NET : vous devez avoir installé Aspose.Words pour .NET. Si ce n'est pas déjà fait, vous pouvez[téléchargez-le ici](https://releases.aspose.com/words/net/).
- Environnement de développement : assurez-vous de disposer d’un environnement de développement .NET. Visual Studio est un choix populaire.
- Connaissances de base de C# : Une certaine familiarité avec la programmation C# sera utile.

## Importer des espaces de noms

Tout d'abord, importons les espaces de noms nécessaires. Ces espaces de noms nous donneront accès aux classes et méthodes dont nous avons besoin pour travailler avec les documents et les formes Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Étape 1 : Configurez votre répertoire de documents

 Avant de commencer à manipuler des formes, nous devons configurer un répertoire dans lequel nos documents seront stockés. Pour des raisons de simplicité, nous utiliserons un espace réservé`YOUR DOCUMENT DIRECTORY`Remplacez ceci par le chemin réel vers votre répertoire de documents.

```csharp
// Chemin vers votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Créer un nouveau document

Ensuite, nous allons créer un nouveau document Word à l'aide d'Aspose.Words. Ce document servira de toile pour ajouter des formes et des images.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Ici, nous créons une instance de`Document` classe et utilise un`DocumentBuilder` pour nous aider à construire le contenu du document.

## Étape 3 : Insérer une image

 Maintenant, insérons une image dans notre document. Nous utiliserons le`InsertImage` méthode de la`DocumentBuilder`classe. Assurez-vous d'avoir une image dans votre répertoire spécifié.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Remplacer`dataDir + "Transparent background logo.png"` avec le chemin vers votre fichier image.

## Étape 4 : Verrouiller le rapport hauteur/largeur

Une fois l'image insérée, nous pouvons verrouiller son rapport hauteur/largeur. Le verrouillage du rapport hauteur/largeur garantit que les proportions de l'image restent constantes lors du redimensionnement.

```csharp
shape.AspectRatioLocked = true;
```

 Paramètre`AspectRatioLocked` à`true` garantit que l'image conserve son rapport hauteur/largeur d'origine.

## Étape 5 : Enregistrer le document

Enfin, nous allons enregistrer le document dans le répertoire spécifié. Cette étape écrit toutes les modifications que nous avons apportées au fichier du document.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusion

Félicitations ! Vous avez appris avec succès à définir le rapport hauteur/largeur des formes dans les documents Word à l'aide d'Aspose.Words pour .NET. En suivant ces étapes, vous pouvez vous assurer que vos images et formes conservent leurs proportions, ce qui donne à vos documents un aspect professionnel et soigné. N'hésitez pas à expérimenter avec différentes images et formes pour voir comment la fonction de verrouillage du rapport hauteur/largeur fonctionne dans différents scénarios.

## FAQ

### Puis-je déverrouiller le rapport hauteur/largeur après l'avoir verrouillé ?
Oui, vous pouvez déverrouiller le rapport hauteur/largeur en définissant`shape.AspectRatioLocked = false`.

### Que se passe-t-il si je redimensionne une image avec un rapport hauteur/largeur verrouillé ?
L'image sera redimensionnée proportionnellement, en conservant son rapport largeur/hauteur d'origine.

### Puis-je appliquer cela à d’autres formes en plus des images ?
Absolument ! La fonction de verrouillage du rapport hauteur/largeur peut être appliquée à n'importe quelle forme, y compris les rectangles, les cercles, etc.

### Aspose.Words pour .NET est-il compatible avec .NET Core ?
Oui, Aspose.Words pour .NET prend en charge .NET Framework et .NET Core.

### Où puis-je trouver plus de documentation sur Aspose.Words pour .NET ?
 Vous trouverez une documentation complète[ici](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
