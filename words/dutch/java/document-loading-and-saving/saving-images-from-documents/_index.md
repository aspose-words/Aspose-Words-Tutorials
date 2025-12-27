---
date: 2025-12-27
description: Leer hoe u een pagina als JPEG opslaat en afbeeldingen uit Word‑documenten
  extraheert met Aspose.Words for Java. Inclusief tips voor het instellen van de helderheid,
  resolutie en het maken van een multipage‑TIFF.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Hoe een pagina opslaan als JPEG en afbeeldingen uit documenten extraheren met
  Aspose.Words voor Java
url: /nl/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Pagina opslaan als JPEG en afbeeldingen extraheren uit documenten in Aspose.Words voor Java

In deze tutorial ontdek je hoe je **pagina opslaat als jpeg** vanuit een Word‑document en hoe je **afbeeldingen uit Word**‑bestanden haalt met Aspose.Words voor Java. We lopen door real‑world scenario's zoals het instellen van de helderheid van een afbeelding, het aanpassen van de afbeeldingsresolutie in Java, en het maken van een multipage TIFF. Elke stap bevat kant‑klaar code‑fragmenten die je kunt kopiëren, plakken en direct resultaten zien.

## Snelle antwoorden
- **Kan ik een enkele pagina opslaan als JPEG?** Ja – gebruik `ImageSaveOptions` met `setPageSet(new PageSet(pageIndex))`.
- **Hoe wijzig ik de helderheid van een afbeelding?** Roep `options.setImageBrightness(floatValue)` aan (bereik 0‑1).
- **Wat als ik een multipage TIFF nodig heb?** Stel een `PageSet` in die de gewenste pagina's omvat en kies een TIFF‑compressiemethode.
- **Hoe kan ik de resolutie van een afbeelding regelen?** Gebruik `setResolution(floatDpi)` of `setHorizontalResolution(floatDpi)`.
- **Heb ik een licentie nodig voor productie?** Een geldige Aspose.Words‑licentie is vereist voor niet‑trial gebruik.

## Wat betekent “pagina opslaan als jpeg”?
Een pagina opslaan als JPEG betekent dat je een enkele pagina van een Word‑document converteert naar een raster‑afbeeldingsbestand (JPEG). Dit is handig voor het genereren van previews, het maken van miniaturen, of het insluiten van documentpagina's in webpagina's waar PDF‑weergave niet praktisch is.

## Waarom afbeeldingen uit Word‑documenten extraheren?
Veel bedrijfsprocessen vereisen het uitpakken van de originele grafische elementen (logo's, diagrammen, foto’s) uit een DOCX‑bestand voor hergebruik, archivering of analyse. Aspose.Words maakt het eenvoudig om elke afbeelding in zijn oorspronkelijke formaat te extraheren zonder kwaliteitsverlies.

## Voorwaarden
- Java Development Kit (JDK 8 of hoger) geïnstalleerd.
- Aspose.Words for Java‑bibliotheek toegevoegd aan je project. Download deze van [here](https://releases.aspose.com/words/java/).
- Een voorbeeld‑Word‑document (bijv. `Rendering.docx`) geplaatst in een bekende map.

## Stap 1: Afbeeldingen opslaan als TIFF met drempel‑controle (Multipage TIFF maken)
Om een hoog‑contrast, grijstinten‑TIFF te genereren kun je de binarisatiedrempel regelen. Dit is handig wanneer je een afdrukbare, zwart‑wit versie van je document nodig hebt.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Stap 2: Een specifieke pagina opslaan als Multipage TIFF
Als je een TIFF nodig hebt die alleen een subset van pagina's bevat (bijv. pagina’s 1‑2), configureer dan een `PageSet`. Dit demonstreert **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Stap 3: Afbeeldingen opslaan als 1 BPP geïndexeerde PNG
Wanneer je ultralichte zwart‑wit PNG’s (1 bit per pixel) nodig hebt, stel je het pixel‑formaat dienovereenkomstig in. Dit is nuttig voor het insluiten van eenvoudige grafische elementen in scenario’s met lage bandbreedte.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Stap 4: Een pagina opslaan als JPEG met aanpassing (Helderheid & resolutie van afbeelding instellen)
Hier **slaan we een pagina op als jpeg** terwijl we helderheid, contrast en resolutie aanpassen — perfect voor het maken van miniaturen of web‑klare previews.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Stap 5: Een pagina‑opslaan‑callback gebruiken (Geavanceerde aanpassing)
Een callback stelt je in staat elke uitvoer‑bestand dynamisch te hernoemen, wat handig is bij het exporteren van veel pagina’s tegelijk.

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

## Complete broncode voor alle scenario's
Hieronder staat een enkele klasse die elke hierboven getoonde methode bevat. Je kunt elke test afzonderlijk uitvoeren.

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

## Veelvoorkomende problemen en oplossingen
- **“Unable to locate the document file”** – Controleer of het bestandspad de juiste scheidingsteken (`/` of `\\`) voor je OS gebruikt.
- **Afbeeldingen verschijnen leeg** – Zorg ervoor dat je een geschikt `ImageColorMode` instelt (bijv. `GRAYSCALE` voor TIFF).
- **Out‑of‑memory‑fouten bij grote documenten** – Verwerk pagina's in batches door het `PageSet`‑bereik aan te passen.
- **JPEG‑kwaliteit ziet er slecht uit** – Verhoog de resolutie met `setHorizontalResolution` of `setResolution`.

## Veelgestelde vragen

**Q: Hoe wijzig ik het afbeeldingsformaat bij het opslaan met Aspose.Words voor Java?**  
A: Stel het gewenste formaat in `ImageSaveOptions`. Voor PNG kun je eenvoudig `ImageSaveOptions` instantieren en `SaveFormat.PNG` toewijzen indien nodig.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Kan ik de compressie‑instellingen voor TIFF‑afbeeldingen aanpassen?**  
A: Ja. Gebruik `setTiffCompression` om een compressie‑algoritme te kiezen, zoals `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Hoe kan ik een specifieke pagina uit een document opslaan als een aparte afbeelding?**  
A: Gebruik de `setPageSet`‑methode met een enkele pagina‑index.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Hoe pas ik aangepaste instellingen toe op JPEG‑afbeeldingen bij het opslaan?**  
A: Pas eigenschappen zoals helderheid, contrast en resolutie aan via `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Hoe kan ik een callback gebruiken voor het aanpassen van het opslaan van afbeeldingen?**  
A: Implementeer `IPageSavingCallback` en wijs deze toe met `setPageSavingCallback`.

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

## Conclusie
Je hebt nu een volledige toolbox voor **pagina opslaan als jpeg**, afbeeldingen extraheren, de helderheid van afbeeldingen regelen, de resolutie van afbeeldingen instellen in Java, en multipage TIFF‑bestanden maken met Aspose.Words voor Java. Experimenteer met verschillende `ImageSaveOptions`‑instellingen om aan de behoeften van je project te voldoen, en verken de bredere Aspose.Words‑API voor nog meer mogelijkheden voor documentmanipulatie.

---

**Laatst bijgewerkt:** 2025-12-27  
**Getest met:** Aspose.Words for Java 24.12 (latest op het moment van schrijven)  
**Auteur:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}