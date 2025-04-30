---
"description": "Convertissez des pages spécifiques de documents Word en JPEG avec des paramètres personnalisés grâce à Aspose.Words pour .NET. Apprenez à régler la luminosité, le contraste et la résolution étape par étape."
"linktitle": "Obtenir une plage de pages Jpeg"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Obtenir une plage de pages Jpeg"
"url": "/fr/net/programming-with-imagesaveoptions/get-jpeg-page-range/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Obtenir une plage de pages Jpeg

## Introduction

Convertir des documents Word en images peut s'avérer extrêmement utile, que ce soit pour créer des vignettes, prévisualiser des documents en ligne ou partager du contenu dans un format plus accessible. Avec Aspose.Words pour .NET, vous pouvez facilement convertir des pages spécifiques de vos documents Word au format JPEG tout en personnalisant divers paramètres comme la luminosité, le contraste et la résolution. Découvrons comment procéder étape par étape !

## Prérequis

Avant de commencer, vous aurez besoin de quelques éléments en place :

- Aspose.Words pour .NET : Assurez-vous d'avoir installé Aspose.Words pour .NET. Vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
- Environnement de développement : environnement de développement AC# comme Visual Studio.
- Exemple de document : un document Word. Vous pouvez utiliser n'importe quel fichier .docx pour ce tutoriel.
- Connaissances de base en C# : Familiarité avec la programmation C#.

Une fois que vous les avez prêts, commençons !

## Importer des espaces de noms

Pour utiliser Aspose.Words pour .NET, vous devez importer les espaces de noms nécessaires au début de votre code. Cela vous garantit l'accès à toutes les classes et méthodes nécessaires à la manipulation des documents.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Chargez votre document

Tout d'abord, nous devons charger le document Word à convertir. Supposons que notre document s'appelle `Rendering.docx` et se trouve dans le répertoire spécifié par l'espace réservé `YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Ce code initialise le chemin d'accès à votre document et le charge dans un Aspose.Words `Document` objet.

## Étape 2 : Configurer ImageSaveOptions

Ensuite, nous allons configurer le `ImageSaveOptions` Pour spécifier comment notre fichier JPEG doit être généré. Cela inclut le réglage de la plage de pages, de la luminosité, du contraste et de la résolution de l'image.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // Convertir uniquement la première page
options.ImageBrightness = 0.3f;   // Régler la luminosité
options.ImageContrast = 0.7f;     // Définir le contraste
options.HorizontalResolution = 72f; // Définir la résolution
```

## Étape 3 : Enregistrer le document au format JPEG

Enfin, nous enregistrons le document sous forme de fichier JPEG en utilisant les paramètres que nous avons définis.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

Ce code enregistre la première page de `Rendering.docx` sous forme d'image JPEG avec les paramètres de luminosité, de contraste et de résolution spécifiés.

## Conclusion

Et voilà ! Vous avez réussi à convertir une page spécifique d'un document Word en image JPEG avec des paramètres personnalisés grâce à Aspose.Words pour .NET. Ce processus peut être adapté à différents besoins, que vous prépariez des images pour un site web, créiez des aperçus de documents, etc.

## FAQ

### Puis-je convertir plusieurs pages à la fois ?
Oui, vous pouvez spécifier une plage de pages à l'aide du `PageSet` propriété dans `ImageSaveOptions`.

### Comment régler la qualité de l'image ?
Vous pouvez ajuster la qualité du JPEG en utilisant le `JpegQuality` propriété dans `ImageSaveOptions`.

### Puis-je enregistrer dans d’autres formats d’image ?
Oui, Aspose.Words prend en charge différents formats d'image comme PNG, BMP et TIFF. Modifiez le `SaveFormat` dans `ImageSaveOptions` par conséquent.

### Existe-t-il un moyen de prévisualiser l'image avant de l'enregistrer ?
Vous devrez implémenter un mécanisme d'aperçu séparément, car Aspose.Words ne fournit pas de fonctionnalité d'aperçu intégrée.

### Comment obtenir une licence temporaire pour Aspose.Words ?
Vous pouvez demander un [licence temporaire ici](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}