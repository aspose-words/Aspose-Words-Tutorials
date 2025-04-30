---
"description": "Lär dig hur du sparar bilder från dokument med Aspose.Words för Java med vår omfattande steg-för-steg-guide. Anpassa format, komprimering och mer."
"linktitle": "Spara bilder från dokument"
"second_title": "Aspose.Words Java-dokumentbehandlings-API"
"title": "Spara bilder från dokument i Aspose.Words för Java"
"url": "/sv/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Spara bilder från dokument i Aspose.Words för Java


## Introduktion till att spara bilder från dokument i Aspose.Words för Java

I den här handledningen ska vi utforska hur man sparar bilder från dokument med Aspose.Words för Java. Vi kommer att gå igenom olika scenarier och anpassningsalternativ för att spara bilder. Den här guiden ger steg-för-steg-instruktioner med exempel på källkod.

## Förkunskapskrav

Innan du börjar, se till att du har Aspose.Words för Java-biblioteket integrerat i ditt projekt. Du kan ladda ner det från [här](https://releases.aspose.com/words/java/).

## Steg 1: Spara bilder som TIFF med tröskelkontroll

För att spara bilder i TIFF-format med tröskelkontroll, följ dessa steg:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Steg 2: Spara en specifik sida som flersidig TIFF

För att spara en specifik sida som en flersidig TIFF, använd följande kod:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Steg 3: Spara bilder som 1 BPP-indexerad PNG

För att spara bilder som 1 BPP-indexerad PNG, följ dessa steg:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Steg 4: Spara en sida som JPEG med anpassning

För att spara en specifik sida som JPEG med anpassningsalternativ, använd den här koden:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Steg 5: Använda återuppringning för att spara sidor

Du kan använda en återuppringning för att anpassa sidsparning. Här är ett exempel:

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

## Komplett källkod för att spara bilder från dokument i Aspose.Words för Java

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
	// Ställ in "PageSet" till "0" för att endast konvertera den första sidan i ett dokument.
	options.setPageSet(new PageSet(0));
	// Ändra bildens ljusstyrka och kontrast.
	// Båda är på en skala från 0–1 och är som standard på 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Ändra den horisontella upplösningen.
	// Standardvärdet för dessa egenskaper är 96,0, för en upplösning på 96 dpi.
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

## Slutsats

Du har lärt dig hur man sparar bilder från dokument med Aspose.Words för Java. Dessa exempel visar olika anpassningsalternativ för att spara bilder, inklusive format, komprimering och återuppringning. Utforska fler möjligheter med Aspose.Words för Javas kraftfulla funktioner.

## Vanliga frågor

### Hur ändrar jag bildformatet när jag sparar med Aspose.Words för Java?

Du kan ändra bildformatet genom att ange önskat format i `ImageSaveOptions`Till exempel, för att spara som PNG, använd `SaveFormat.PNG` som visas i koden:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Kan jag anpassa komprimeringsinställningarna för TIFF-bilder?

Ja, du kan anpassa inställningarna för TIFF-bildkomprimering. Om du till exempel vill ställa in komprimeringsmetoden till CCITT_3 använder du följande kod:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Hur kan jag spara en specifik sida från ett dokument som en separat bild?

För att spara en specifik sida som en bild, använd `setPageSet` metod i `ImageSaveOptions`Om du till exempel bara vill spara den första sidan ställer du in `PageSet` till `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Spara den första sidan som en bild
```

### Hur tillämpar jag anpassade inställningar på JPEG-bilder när jag sparar?

Du kan använda anpassade inställningar för JPEG-bilder med hjälp av `ImageSaveOptions`Justera egenskaper som ljusstyrka, kontrast och upplösning. För att till exempel ändra ljusstyrka till 0,3 och kontrast till 0,7, använd den här koden:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Hur kan jag använda en återanropsfunktion för att anpassa bildsparning?

För att använda en återuppringning för att anpassa bildsparning, ställ in `PageSavigCallback` in `ImageSaveOptions`Skapa en klass som implementerar `IPageSavingCallback` gränssnittet och åsidosätta `pageSaving` metod.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Skapa sedan en klass som implementerar `IPageSavingCallback` gränssnittet och anpassa filnamnet och platsen i `pageSaving` metod.

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