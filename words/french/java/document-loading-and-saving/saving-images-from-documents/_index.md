---
date: 2025-12-27
description: Apprenez à enregistrer une page au format JPEG et à extraire des images
  de documents Word à l'aide d'Aspose.Words pour Java. Inclut des conseils pour régler
  la luminosité de l'image, la résolution et créer un TIFF multipage.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Comment enregistrer une page au format JPEG et extraire les images des documents
  avec Aspose.Words pour Java
url: /fr/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Enregistrer une page au format JPEG et extraire les images des documents avec Aspose.Words for Java

Dans ce tutoriel, vous découvrirez comment **enregistrer une page au format jpeg** à partir d’un document Word et comment **extraire les images d’un fichier Word** en utilisant Aspose.Words for Java. Nous parcourrons des scénarios concrets tels que le réglage de la luminosité d’une image, l’ajustement de la résolution d’image en Java, et la création d’un TIFF multipage. Chaque étape comprend des extraits de code prêts à l’emploi que vous pouvez copier‑coller et voir les résultats immédiatement.

## Réponses rapides
- **Puis‑je enregistrer une seule page au format JPEG ?** Oui – utilisez `ImageSaveOptions` avec `setPageSet(new PageSet(pageIndex))`.
- **Comment modifier la luminosité d’une image ?** Appelez `options.setImageBrightness(floatValue)` (plage 0‑1).
- **Et si j’ai besoin d’un TIFF multipage ?** Définissez un `PageSet` couvrant les pages souhaitées et choisissez une méthode de compression TIFF.
- **Comment contrôler la résolution de l’image ?** Utilisez `setResolution(floatDpi)` ou `setHorizontalResolution(floatDpi)`.
- **Ai‑je besoin d’une licence pour la production ?** Une licence valide d’Aspose.Words est requise pour une utilisation non‑d’évaluation.

## Qu’est‑ce que « save page as jpeg » ?
Enregistrer une page au format JPEG signifie convertir une page unique d’un document Word en un fichier image raster (JPEG). Cela est utile pour la génération d’aperçus, la création de vignettes ou l’intégration de pages de document dans des pages web lorsque le rendu PDF n’est pas pratique.

## Pourquoi extraire les images des documents Word ?
De nombreux flux de travail métier nécessitent d’extraire les graphiques d’origine (logos, diagrammes, photos) d’un fichier DOCX pour les réutiliser, les archiver ou les analyser. Aspose.Words simplifie l’extraction de chaque image dans son format natif sans perte de qualité.

## Prérequis
- Java Development Kit (JDK 8 ou supérieur) installé.
- Bibliothèque Aspose.Words for Java ajoutée à votre projet. Téléchargez‑la depuis [here](https://releases.aspose.com/words/java/).
- Un document Word d’exemple (par ex., `Rendering.docx`) placé dans un répertoire connu.

## Étape 1 : Enregistrer les images au format TIFF avec contrôle du seuil (Créer un TIFF multipage)
Pour générer un TIFF en niveaux de gris à fort contraste, vous pouvez contrôler le seuil de binarisation. Cela est pratique lorsque vous avez besoin d’une version imprimable noir‑et‑blanc de votre document.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Étape 2 : Enregistrer une page spécifique au format TIFF multipage
Si vous avez besoin d’un TIFF contenant uniquement un sous‑ensemble de pages (par ex., pages 1‑2), configurez un `PageSet`. Cela illustre **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Étape 3 : Enregistrer les images au format PNG indexé 1 BPP
Lorsque vous avez besoin de PNG noir‑et‑blanc ultra‑légers (1 bit par pixel), définissez le format de pixel en conséquence. Cela est utile pour intégrer des graphiques simples dans des scénarios à bande passante limitée.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Étape 4 : Enregistrer une page au format JPEG avec personnalisation (Définir la luminosité et la résolution de l’image)
Ici nous **save page as jpeg** tout en ajustant la luminosité, le contraste et la résolution — parfait pour créer des vignettes ou des aperçus prêts pour le web.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Étape 5 : Utiliser un rappel d’enregistrement de page (personnalisation avancée)
Un rappel vous permet de renommer chaque fichier de sortie dynamiquement, ce qui est utile lors de l’exportation de nombreuses pages en une fois.

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

## Code source complet pour tous les scénarios
Ci‑dessous se trouve une classe unique contenant chaque méthode démontrée précédemment. Vous pouvez exécuter chaque test individuellement.

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
	// Set the "PageSet" to "0" to convert only the first page of a document.
	options.setPageSet(new PageSet(0));
	// Change the image's brightness and contrast.
	// Both are on a 0-1 scale and are at 0.5 by default.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Change the horizontal resolution.
	// The default value for these properties is 96.0, for a resolution of 96dpi.
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

## Problèmes courants et solutions
- **« Unable to locate the document file »** – Vérifiez que le chemin du fichier utilise le séparateur correct (`/` ou `\\`) pour votre OS.
- **Les images apparaissent vides** – Assurez‑vous de définir un `ImageColorMode` approprié (par ex., `GRAYSCALE` pour le TIFF).
- **Erreurs de mémoire insuffisante sur de gros documents** – Traitez les pages par lots en ajustant la plage du `PageSet`.
- **La qualité du JPEG semble mauvaise** – Augmentez la résolution avec `setHorizontalResolution` ou `setResolution`.

## Foire aux questions

**Q : Comment changer le format d’image lors de l’enregistrement avec Aspose.Words for Java ?**  
R : Définissez le format souhaité dans `ImageSaveOptions`. Pour le PNG, il suffit d’instancier `ImageSaveOptions` et d’assigner `SaveFormat.PNG` si nécessaire.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q : Puis‑je personnaliser les paramètres de compression pour les images TIFF ?**  
R : Oui. Utilisez `setTiffCompression` pour choisir un algorithme de compression tel que `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q : Comment enregistrer une page spécifique d’un document en tant qu’image séparée ?**  
R : Utilisez la méthode `setPageSet` avec un indice de page unique.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q : Comment appliquer des paramètres personnalisés aux images JPEG lors de l’enregistrement ?**  
R : Ajustez des propriétés comme la luminosité, le contraste et la résolution via `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q : Comment utiliser un rappel pour personnaliser l’enregistrement des images ?**  
R : Implémentez `IPageSavingCallback` et assignez‑le avec `setPageSavingCallback`.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Conclusion
Vous disposez maintenant d’une boîte à outils complète pour **saving page as jpeg**, extraire des images, contrôler la luminosité d’une image, définir la résolution d’image en Java, et créer des fichiers TIFF multipage avec Aspose.Words for Java. Expérimentez avec différents paramètres `ImageSaveOptions` pour répondre aux besoins de votre projet, et explorez l’API Aspose.Words plus large pour encore plus de possibilités de manipulation de documents.

---

**Dernière mise à jour :** 2025-12-27  
**Testé avec :** Aspose.Words for Java 24.12 (dernière version au moment de la rédaction)  
**Auteur :** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}