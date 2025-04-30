---
"description": "Découvrez comment enregistrer des images à partir de documents avec Aspose.Words pour Java grâce à notre guide complet étape par étape. Personnalisez les formats, la compression et bien plus encore."
"linktitle": "Sauvegarde d'images à partir de documents"
"second_title": "API de traitement de documents Java Aspose.Words"
"title": "Enregistrer des images à partir de documents dans Aspose.Words pour Java"
"url": "/fr/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer des images à partir de documents dans Aspose.Words pour Java


## Introduction à l'enregistrement d'images à partir de documents dans Aspose.Words pour Java

Dans ce tutoriel, nous découvrirons comment enregistrer des images à partir de documents avec Aspose.Words pour Java. Nous aborderons différents scénarios et options de personnalisation pour l'enregistrement d'images. Ce guide fournit des instructions étape par étape avec des exemples de code source.

## Prérequis

Avant de commencer, assurez-vous d'avoir intégré la bibliothèque Aspose.Words pour Java à votre projet. Vous pouvez la télécharger ici. [ici](https://releases.aspose.com/words/java/).

## Étape 1 : Enregistrement des images au format TIFF avec contrôle de seuil

Pour enregistrer des images au format TIFF avec contrôle de seuil, procédez comme suit :

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Étape 2 : Enregistrer une page spécifique au format TIFF multipage

Pour enregistrer une page spécifique au format TIFF multipage, utilisez le code suivant :

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Étape 3 : Enregistrement des images au format PNG indexé 1 BPP

Pour enregistrer des images au format PNG indexé 1 BPP, procédez comme suit :

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Étape 4 : Enregistrer une page au format JPEG avec personnalisation

Pour enregistrer une page spécifique au format JPEG avec des options de personnalisation, utilisez ce code :

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Étape 5 : Utilisation du rappel d'enregistrement de page

Vous pouvez utiliser un rappel pour personnaliser l'enregistrement des pages. Voici un exemple :

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
doc.save("Your Directory Path" + "PageSavingCallback.png", imageSaveOptions);
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Code source complet pour l'enregistrement d'images à partir de documents dans Aspose.Words pour Java

```java
public void exposeThresholdControlForTiffBinarization() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setTiffCompression(TiffCompression.CCITT_3);
		saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
		saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
		saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.ExposeThresholdControlForTiffBinarization.tiff", saveOptions);
}
@Test
public void getTiffPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.MultipageTiff.tiff");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(new PageRange(0, 1))); saveOptions.setTiffCompression(TiffCompression.CCITT_4); saveOptions.setResolution(160f);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetTiffPageRange.tiff", saveOptions);
}
@Test
public void format1BppIndexed() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(1));
		saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
		saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
}
@Test
public void getJpegPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions options = new ImageSaveOptions();
	// Définissez « PageSet » sur « 0 » pour convertir uniquement la première page d'un document.
	options.setPageSet(new PageSet(0));
	// Modifiez la luminosité et le contraste de l'image.
	// Les deux sont sur une échelle de 0 à 1 et sont à 0,5 par défaut.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Changer la résolution horizontale.
	// La valeur par défaut de ces propriétés est 96,0, pour une résolution de 96 dpi.
	options.setHorizontalResolution(72f);
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
}
@Test
public static void pageSavingCallback() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
	{
		imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
		imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
}
private static class HandlePageSavingCallback implements IPageSavingCallback
{
	public void pageSaving(PageSavingArgs args)
	{
		args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
	}
```

## Conclusion

Vous avez appris à enregistrer des images à partir de documents avec Aspose.Words pour Java. Ces exemples illustrent différentes options de personnalisation pour l'enregistrement d'images, notamment le format, la compression et l'utilisation de fonctions de rappel. Explorez d'autres possibilités grâce aux puissantes fonctionnalités d'Aspose.Words pour Java.

## FAQ

### Comment modifier le format de l'image lors de l'enregistrement avec Aspose.Words pour Java ?

Vous pouvez modifier le format de l'image en spécifiant le format souhaité dans le `ImageSaveOptions`. Par exemple, pour enregistrer au format PNG, utilisez `SaveFormat.PNG` comme indiqué dans le code :

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Puis-je personnaliser les paramètres de compression pour les images TIFF ?

Oui, vous pouvez personnaliser les paramètres de compression des images TIFF. Par exemple, pour définir la méthode de compression sur CCITT_3, utilisez le code suivant :

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Comment puis-je enregistrer une page spécifique d’un document en tant qu’image distincte ?

Pour enregistrer une page spécifique en tant qu'image, utilisez le `setPageSet` méthode dans `ImageSaveOptions`. Par exemple, pour enregistrer uniquement la première page, définissez le `PageSet` à `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Enregistrer la première page en tant qu'image
```

### Comment appliquer des paramètres personnalisés aux images JPEG lors de l'enregistrement ?

Vous pouvez appliquer des paramètres personnalisés aux images JPEG à l'aide de `ImageSaveOptions`Ajustez les propriétés comme la luminosité, le contraste et la résolution. Par exemple, pour régler la luminosité à 0,3 et le contraste à 0,7, utilisez ce code :

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Comment puis-je utiliser un rappel pour personnaliser l'enregistrement d'image ?

Pour utiliser un rappel pour personnaliser l'enregistrement d'image, définissez le `PageSavdansgCallback` in `ImageSaveOptions`. Créez une classe qui implémente le `IPageSavingCallback` interface et remplacer le `pageSaving` méthode.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Ensuite, créez une classe qui implémente le `IPageSavingCallback` interface et personnaliser le nom et l'emplacement du fichier dans le `pageSaving` méthode.

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}