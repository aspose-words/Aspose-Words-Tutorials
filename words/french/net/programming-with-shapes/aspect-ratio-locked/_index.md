---
"description": "Apprenez à verrouiller les proportions des formes dans vos documents Word avec Aspose.Words pour .NET. Suivez ce guide étape par étape pour conserver les proportions de vos images et formes."
"linktitle": "Rapport hauteur/largeur verrouillé"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Rapport hauteur/largeur verrouillé"
"url": "/fr/net/programming-with-shapes/aspect-ratio-locked/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rapport hauteur/largeur verrouillé

## Introduction

Vous êtes-vous déjà demandé comment conserver les proportions parfaites des images et des formes dans vos documents Word ? Il est parfois nécessaire de s'assurer que vos images et formes ne soient pas déformées lors du redimensionnement. C'est là que le verrouillage des proportions s'avère utile. Dans ce tutoriel, nous allons découvrir comment définir les proportions des formes dans les documents Word avec Aspose.Words pour .NET. Nous détaillerons le processus en étapes faciles à suivre, afin que vous puissiez appliquer ces compétences à vos projets en toute confiance.

## Prérequis

Avant de plonger dans le code, passons en revue ce dont vous avez besoin pour commencer :

- Bibliothèque Aspose.Words pour .NET : vous devez avoir installé Aspose.Words pour .NET. Si ce n'est pas déjà fait, vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
- Environnement de développement : Assurez-vous de disposer d'un environnement de développement .NET. Visual Studio est un choix courant.
- Connaissances de base en C# : une certaine familiarité avec la programmation C# sera utile.

## Importer des espaces de noms

Commençons par importer les espaces de noms nécessaires. Ces espaces nous donneront accès aux classes et méthodes nécessaires pour travailler avec les documents et formes Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Étape 1 : Configurez votre répertoire de documents

Avant de commencer à manipuler les formes, nous devons créer un répertoire où seront stockés nos documents. Pour plus de simplicité, nous utiliserons un espace réservé. `YOUR DOCUMENT DIRECTORY`. Remplacez ceci par le chemin réel vers votre répertoire de documents.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Créer un nouveau document

Nous allons ensuite créer un document Word avec Aspose.Words. Ce document servira de canevas pour ajouter des formes et des images.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Ici, nous créons une instance du `Document` classe et utilise un `DocumentBuilder` pour nous aider à construire le contenu du document.

## Étape 3 : Insérer une image

Insérons maintenant une image dans notre document. Nous utiliserons `InsertImage` méthode de la `DocumentBuilder` classe. Assurez-vous d'avoir une image dans votre répertoire spécifié.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

Remplacer `dataDir + "Transparent background logo.png"` avec le chemin vers votre fichier image.

## Étape 4 : Verrouiller le rapport hauteur/largeur

Une fois l'image insérée, nous pouvons verrouiller son format. Ce verrouillage garantit que les proportions de l'image restent constantes lors du redimensionnement.

```csharp
shape.AspectRatioLocked = true;
```

Paramètre `AspectRatioLocked` à `true` garantit que l'image conserve son rapport hauteur/largeur d'origine.

## Étape 5 : Enregistrer le document

Enfin, nous enregistrerons le document dans le répertoire spécifié. Cette étape enregistrera toutes les modifications apportées au fichier.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusion

Félicitations ! Vous avez appris à définir les proportions des formes dans vos documents Word avec Aspose.Words pour .NET. En suivant ces étapes, vous pouvez garantir que vos images et formes conservent leurs proportions, donnant à vos documents un aspect professionnel et soigné. N'hésitez pas à tester différentes images et formes pour découvrir comment fonctionne la fonction de verrouillage des proportions dans différents scénarios.

## FAQ

### Puis-je déverrouiller le rapport hauteur/largeur après l'avoir verrouillé ?
Oui, vous pouvez déverrouiller le rapport hauteur/largeur en définissant `shape.AspectRatioLocked = false`.

### Que se passe-t-il si je redimensionne une image avec un rapport hauteur/largeur verrouillé ?
L'image sera redimensionnée proportionnellement, en conservant son rapport largeur/hauteur d'origine.

### Puis-je appliquer cela à d’autres formes en plus des images ?
Absolument ! La fonction de verrouillage du rapport hauteur/largeur s'applique à n'importe quelle forme, y compris les rectangles, les cercles, etc.

### Aspose.Words pour .NET est-il compatible avec .NET Core ?
Oui, Aspose.Words pour .NET prend en charge .NET Framework et .NET Core.

### Où puis-je trouver plus de documentation sur Aspose.Words pour .NET ?
Vous trouverez une documentation complète [ici](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}