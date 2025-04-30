---
"description": "Apprenez à convertir un document Word en image indexée 1Bpp avec Aspose.Words pour .NET. Suivez notre guide étape par étape pour une conversion facile."
"linktitle": "Format 1Bpp indexé"
"second_title": "API de traitement de documents Aspose.Words"
"title": "Format 1Bpp indexé"
"url": "/fr/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format 1Bpp indexé

## Introduction

Vous êtes-vous déjà demandé comment enregistrer un document Word en image noir et blanc en quelques lignes de code ? Ça tombe bien ! Aujourd'hui, nous vous présentons une petite astuce astucieuse utilisant Aspose.Words pour .NET pour convertir vos documents en images indexées de 1 Bpp. Ce format est idéal pour certains types d'archivage numérique, l'impression ou pour gagner de la place. Nous détaillons chaque étape pour vous simplifier la tâche. Prêt à vous lancer ? C'est parti !

## Prérequis

Avant de nous salir les mains, il y a quelques éléments que vous devez mettre en place :

- Aspose.Words pour .NET : assurez-vous que la bibliothèque est installée. Vous pouvez [téléchargez-le ici](https://releases.aspose.com/words/net/).
- Environnement de développement .NET : Visual Studio est une bonne option, mais vous pouvez utiliser n’importe quel environnement avec lequel vous êtes à l’aise.
- Connaissances de base de C# : ne vous inquiétez pas, nous allons rester simples, mais une petite familiarité avec C# vous aidera.
- Un document Word : Ayez un exemple de document Word prêt à être converti.

## Importer des espaces de noms

Tout d'abord, nous devons importer les espaces de noms nécessaires. C'est essentiel car cela nous permet d'accéder aux classes et méthodes nécessaires depuis Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Étape 1 : Configurez votre répertoire de documents

Vous devrez spécifier le chemin d'accès à votre répertoire de documents. C'est là que votre document Word est stocké et que l'image convertie sera enregistrée.

```csharp
// Chemin d'accès à votre répertoire de documents
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Étape 2 : Charger le document Word

Maintenant, chargeons le document Word dans un Aspose.Words `Document` objet. Cet objet représente votre fichier Word et vous permet de le manipuler.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Étape 3 : Configurer les options d’enregistrement de l’image

Ensuite, nous devons configurer le `ImageSaveOptions`C'est ici que la magie opère. Nous allons configurer l'image pour qu'elle soit enregistrée au format PNG avec un mode couleur indexé de 1 Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png : Cela spécifie que nous voulons enregistrer le document sous forme d'image PNG.
- PageSet(1) : cela indique que nous ne convertissons que la première page.
- ImageColorMode.BlackAndWhite : cela définit l'image en noir et blanc.
- ImagePixelFormat.Format1bppIndexed : cela définit le format de l'image sur 1 Bpp indexé.

## Étape 4 : Enregistrer le document en tant qu’image

Enfin, nous enregistrons le document sous forme d’image en utilisant le `Save` méthode de la `Document` objet.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Conclusion

Et voilà ! En quelques lignes de code, vous avez transformé votre document Word en une image indexée de 1 bpp grâce à Aspose.Words pour .NET. Cette méthode est incroyablement utile pour créer des images à fort contraste et peu encombrantes à partir de vos documents. Vous pouvez désormais l'intégrer facilement à vos projets et workflows. Bon codage !

## FAQ

### Qu'est-ce qu'une image indexée 1Bpp ?
Une image indexée 1Bpp (1 bit par pixel) est un format d'image en noir et blanc où chaque pixel est représenté par un seul bit, soit 0, soit 1. Ce format est très efficace en termes d'espace.

### Puis-je convertir plusieurs pages d’un document Word à la fois ?
Oui, vous pouvez. Modifiez le `PageSet` propriété dans le `ImageSaveOptions` pour inclure plusieurs pages ou le document entier.

### Ai-je besoin d’une licence pour utiliser Aspose.Words pour .NET ?
Oui, Aspose.Words pour .NET nécessite une licence pour bénéficier de toutes ses fonctionnalités. Vous pouvez obtenir une [licence temporaire ici](https://purchase.aspose.com/temporary-license/).

### Vers quels autres formats d’image puis-je convertir mon document Word ?
Aspose.Words prend en charge différents formats d'image, notamment JPEG, BMP et TIFF. Il suffit de modifier le `SaveFormat` dans le `ImageSaveOptions`.

### Où puis-je trouver plus de documentation sur Aspose.Words pour .NET ?
Vous trouverez une documentation détaillée sur le [Page de documentation d'Aspose.Words pour .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}