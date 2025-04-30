---
"description": "Leer hoe je afbeeldingen uit documenten kunt opslaan met Aspose.Words voor Java met onze uitgebreide stapsgewijze handleiding. Pas formaten, compressie en meer aan."
"linktitle": "Afbeeldingen uit documenten opslaan"
"second_title": "Aspose.Words Java Documentverwerking API"
"title": "Afbeeldingen opslaan uit documenten in Aspose.Words voor Java"
"url": "/nl/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Afbeeldingen opslaan uit documenten in Aspose.Words voor Java


## Inleiding tot het opslaan van afbeeldingen uit documenten in Aspose.Words voor Java

In deze tutorial laten we zien hoe je afbeeldingen uit documenten kunt opslaan met Aspose.Words voor Java. We bespreken verschillende scenario's en aanpassingsmogelijkheden voor het opslaan van afbeeldingen. Deze handleiding bevat stapsgewijze instructies met broncodevoorbeelden.

## Vereisten

Voordat u begint, moet u ervoor zorgen dat de Aspose.Words voor Java-bibliotheek in uw project is geïntegreerd. U kunt deze downloaden van [hier](https://releases.aspose.com/words/java/).

## Stap 1: Afbeeldingen opslaan als TIFF met drempelcontrole

Om afbeeldingen op te slaan in TIFF-formaat met drempelcontrole, volgt u deze stappen:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Stap 2: Een specifieke pagina opslaan als een TIFF met meerdere pagina's

Om een specifieke pagina als een TIFF-bestand met meerdere pagina's op te slaan, gebruikt u de volgende code:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Stap 3: Afbeeldingen opslaan als 1 BPP geïndexeerde PNG

Om afbeeldingen op te slaan als 1 BPP geïndexeerde PNG, volgt u deze stappen:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Stap 4: Een pagina opslaan als JPEG met aanpassing

Gebruik deze code om een specifieke pagina als JPEG op te slaan met aanpassingsopties:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Stap 5: Gebruik van de callback voor paginaopslag

U kunt een callback gebruiken om het opslaan van pagina's aan te passen. Hier is een voorbeeld:

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

## Volledige broncode voor het opslaan van afbeeldingen uit documenten in Aspose.Words voor Java

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
	// Stel de "PageSet" in op "0" om alleen de eerste pagina van een document te converteren.
	options.setPageSet(new PageSet(0));
	// Wijzig de helderheid en het contrast van de afbeelding.
	// Beide hebben een schaal van 0-1 en staan standaard op 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Wijzig de horizontale resolutie.
	// De standaardwaarde voor deze eigenschappen is 96,0, voor een resolutie van 96 dpi.
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

## Conclusie

Je hebt geleerd hoe je afbeeldingen uit documenten kunt opslaan met Aspose.Words voor Java. Deze voorbeelden demonstreren verschillende aanpassingsopties voor het opslaan van afbeeldingen, waaronder opmaak, compressie en callbackgebruik. Ontdek meer mogelijkheden met de krachtige mogelijkheden van Aspose.Words voor Java.

## Veelgestelde vragen

### Hoe wijzig ik de afbeeldingsindeling bij het opslaan met Aspose.Words voor Java?

U kunt het afbeeldingsformaat wijzigen door het gewenste formaat in het veld 'Afbeelding' op te geven. `ImageSaveOptions`Om bijvoorbeeld als PNG op te slaan, gebruikt u `SaveFormat.PNG` zoals weergegeven in de code:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Kan ik de compressie-instellingen voor TIFF-afbeeldingen aanpassen?

Ja, u kunt de compressie-instellingen voor TIFF-afbeeldingen aanpassen. Om de compressiemethode bijvoorbeeld in te stellen op CCITT_3, gebruikt u de volgende code:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Hoe kan ik een specifieke pagina uit een document opslaan als een aparte afbeelding?

Om een specifieke pagina als afbeelding op te slaan, gebruikt u de `setPageSet` methode in `ImageSaveOptions`Om bijvoorbeeld alleen de eerste pagina op te slaan, stelt u de `PageSet` naar `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Sla de eerste pagina op als afbeelding
```

### Hoe pas ik aangepaste instellingen toe op JPEG-afbeeldingen bij het opslaan?

U kunt aangepaste instellingen toepassen op JPEG-afbeeldingen met behulp van `ImageSaveOptions`Pas eigenschappen zoals helderheid, contrast en resolutie aan. Om bijvoorbeeld de helderheid naar 0,3 en het contrast naar 0,7 te wijzigen, gebruikt u deze code:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Hoe kan ik een callback gebruiken voor het aanpassen van het opslaan van afbeeldingen?

Om een callback te gebruiken voor het aanpassen van het opslaan van afbeeldingen, stelt u de `PageSavingCallback` in `ImageSaveOptions`. Maak een klasse die de `IPageSavingCallback` interface en overschrijven de `pageSaving` methode.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Maak vervolgens een klasse die de `IPageSavingCallback` interface en pas de bestandsnaam en locatie aan in de `pageSaving` methode.

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