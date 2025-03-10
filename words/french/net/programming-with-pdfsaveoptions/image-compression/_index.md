---
title: Compression d'image dans un document PDF
linktitle: Compression d'image dans un document PDF
second_title: API de traitement de documents Aspose.Words
description: Découvrez comment compresser des images dans des documents PDF à l'aide d'Aspose.Words pour .NET. Suivez ce guide pour optimiser la taille et la qualité des fichiers.
weight: 10
url: /fr/net/programming-with-pdfsaveoptions/image-compression/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Compression d'image dans un document PDF

## Introduction

À l'ère du numérique, la gestion de la taille des documents est essentielle pour les performances et l'efficacité du stockage. Que vous ayez affaire à des rapports volumineux ou à des présentations complexes, il est essentiel de réduire la taille des fichiers sans sacrifier la qualité. La compression d'images dans les documents PDF est une technique clé pour atteindre cet objectif. Si vous travaillez avec Aspose.Words pour .NET, vous avez de la chance ! Ce didacticiel vous guidera tout au long du processus de compression d'images dans des documents PDF à l'aide d'Aspose.Words pour .NET. Nous explorerons différentes options de compression et comment les appliquer efficacement pour garantir que vos PDF sont optimisés en termes de qualité et de taille.

## Prérequis

Avant de plonger dans le didacticiel, assurez-vous de disposer des prérequis suivants :

1. Aspose.Words pour .NET : vous devez avoir installé Aspose.Words pour .NET. Vous pouvez le télécharger à partir du[Site Web d'Aspose](https://releases.aspose.com/words/net/).

2. Connaissances de base de C# : une familiarité avec la programmation C# vous aidera à comprendre les exemples de code fournis dans ce didacticiel.

3. Environnement de développement : assurez-vous d’avoir configuré un environnement de développement .NET, tel que Visual Studio.

4. Exemple de document : préparez un exemple de document Word (par exemple, « Rendering.docx ») pour tester la compression de l'image.

5. Licence Aspose : si vous utilisez une version sous licence d'Aspose.Words pour .NET, assurez-vous que la licence est correctement configurée. Si vous avez besoin d'une licence temporaire, vous pouvez en obtenir une auprès de[Page de licence temporaire d'Aspose](https://purchase.aspose.com/temporary-license/).

## Importer des espaces de noms

Pour commencer à compresser des images dans des documents PDF à l'aide d'Aspose.Words pour .NET, vous devez importer les espaces de noms nécessaires. Voici comment procéder :

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Ces espaces de noms donnent accès aux fonctionnalités principales nécessaires pour manipuler des documents Word et les enregistrer au format PDF avec diverses options.

## Étape 1 : Configurez votre répertoire de documents

Avant de commencer à coder, définissez le chemin d'accès à votre répertoire de documents. Cela vous aidera à localiser et à enregistrer facilement vos fichiers.

```csharp
// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Remplacer`"YOUR DOCUMENT DIRECTORY"` avec le chemin où votre document d'exemple est stocké.

## Étape 2 : Charger le document Word

 Ensuite, chargez votre document Word dans un`Aspose.Words.Document` objet. Cela vous permettra de travailler avec le document par programmation.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Ici,`"Rendering.docx"` est le nom de votre exemple de document Word. Assurez-vous que ce fichier se trouve dans le répertoire spécifié.

## Étape 3 : Configurer la compression d’image de base

 Créer un`PdfSaveOptions`objet pour configurer les options d'enregistrement PDF, y compris la compression d'image. Définissez l'`ImageCompression`propriété à`PdfImageCompression.Jpeg` utiliser la compression JPEG pour les images.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
	// Compresser des images avec JPEG
    ImageCompression = PdfImageCompression.Jpeg,
	// Facultatif : Conserver les champs de formulaire dans le PDF
    PreserveFormFields = true
};
```

## Étape 4 : Enregistrer le document avec une compression de base

Enregistrez le document Word au format PDF avec les options de compression d'image configurées. Cela appliquera la compression JPEG aux images du PDF.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);
```

 Dans cet exemple, le PDF de sortie est nommé`"WorkingWithPdfSaveOptions.PdfImageCompression.pdf"`Ajustez le nom du fichier selon vos besoins.

## Étape 5 : Configurer la compression avancée avec la conformité PDF/A

 Pour une compression encore meilleure, notamment si vous devez respecter les normes PDF/A, vous pouvez configurer des options supplémentaires.`Compliance`propriété à`PdfCompliance.PdfA2u` et ajuster le`JpegQuality` propriété.

```csharp
PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	// Définir la conformité à PDF/A-2u
    Compliance = PdfCompliance.PdfA2u,
	// Utiliser la compression JPEG
    ImageCompression = PdfImageCompression.Jpeg,
	// Ajustez la qualité JPEG pour contrôler le niveau de compression
    JpegQuality = 100 
};
```

## Étape 6 : Enregistrer le document avec une compression avancée

Enregistrez le document Word au format PDF avec les paramètres de compression avancés. Cette configuration garantit que le PDF respecte les normes PDF/A et utilise une compression JPEG de haute qualité.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
```

 Ici, le PDF de sortie est nommé`"WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf"`. Modifiez le nom du fichier selon vos préférences.

## Conclusion

La réduction de la taille des documents PDF en compressant les images est une étape essentielle pour optimiser les performances et le stockage des documents. Avec Aspose.Words pour .NET, vous disposez d'outils puissants pour contrôler efficacement la compression des images. En suivant les étapes décrites dans ce didacticiel, vous pouvez vous assurer que vos documents PDF sont à la fois de haute qualité et compacts. Que vous ayez besoin d'une compression de base ou avancée, Aspose.Words offre la flexibilité nécessaire pour répondre à vos besoins.


## FAQ

### Qu'est-ce que la compression d'image dans les PDF ?
La compression d'image réduit la taille du fichier des documents PDF en diminuant la qualité des images, ce qui contribue à optimiser le stockage et les performances.

### Comment Aspose.Words pour .NET gère-t-il la compression d'image ?
Aspose.Words pour .NET fournit le`PdfSaveOptions` classe, qui vous permet de définir diverses options de compression d'image, y compris la compression JPEG.

### Puis-je utiliser Aspose.Words pour .NET pour me conformer aux normes PDF/A ?
Oui, Aspose.Words prend en charge la conformité PDF/A, vous permettant d'enregistrer des documents dans des formats répondant aux normes d'archivage et de conservation à long terme.

### Quel est l’impact de la qualité JPEG sur la taille du fichier PDF ?
Des paramètres de qualité JPEG plus élevés donnent une meilleure qualité d'image mais des tailles de fichier plus grandes, tandis que des paramètres de qualité inférieure réduisent la taille du fichier mais peuvent affecter la clarté de l'image.

### Où puis-je trouver plus d'informations sur Aspose.Words pour .NET ?
 Vous pouvez en savoir plus sur Aspose.Words pour .NET sur leur[Documentation](https://reference.aspose.com/words/net/), [Soutien](https://forum.aspose.com/c/words/8) , et[Télécharger](https://releases.aspose.com/words/net/) pages.

### Exemple de code source pour la compression d'images avec Aspose.Words pour .NET

```csharp

// Le chemin vers le répertoire des documents.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");

PdfSaveOptions saveOptions = new PdfSaveOptions
{
	ImageCompression = PdfImageCompression.Jpeg, PreserveFormFields = true
};

doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression.pdf", saveOptions);

PdfSaveOptions saveOptionsA2U = new PdfSaveOptions
{
	Compliance = PdfCompliance.PdfA2u,
	ImageCompression = PdfImageCompression.Jpeg,
	JpegQuality = 100, // Utilisez la compression JPEG à 50 % de qualité pour réduire la taille du fichier.
};



doc.Save(dataDir + "WorkingWithPdfSaveOptions.PdfImageCompression_A2u.pdf", saveOptionsA2U);
	
```
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
