---
date: 2025-12-27
description: Lär dig hur du sparar en sida som JPEG och extraherar bilder från Word‑dokument
  med Aspose.Words för Java. Inkluderar tips för att justera bildens ljusstyrka, upplösning
  och skapa flersidiga TIFF‑filer.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Hur man sparar en sida som JPEG och extraherar bilder från dokument med Aspose.Words
  för Java
url: /sv/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Spara sida som JPEG och extrahera bilder från dokument i Aspose.Words för Java

I den här handledningen kommer du att upptäcka hur du **sparar sida som jpeg** från ett Word‑dokument och hur du **extraherar bilder från Word**‑filer med Aspose.Words för Java. Vi går igenom verkliga scenarier som att ställa in bildens ljusstyrka, justera bildens upplösning i Java och skapa en flersidig TIFF. Varje steg innehåller färdiga kodexempel som du kan kopiera, klistra in och se resultatet omedelbart.

## Snabba svar
- **Kan jag spara en enskild sida som JPEG?** Ja – använd `ImageSaveOptions` med `setPageSet(new PageSet(pageIndex))`.
- **Hur ändrar jag bildens ljusstyrka?** Anropa `options.setImageBrightness(floatValue)` (0‑1‑intervall).
- **Vad gör jag om jag behöver en flersidig TIFF?** Ställ in ett `PageSet` som täcker de önskade sidorna och välj en TIFF‑komprimeringsmetod.
- **Hur kan jag kontrollera bildens upplösning?** Använd `setResolution(floatDpi)` eller `setHorizontalResolution(floatDpi)`.
- **Behöver jag en licens för produktion?** En giltig Aspose.Words‑licens krävs för icke‑testanvändning.

## Vad betyder “save page as jpeg”?
Att spara en sida som JPEG innebär att konvertera en enskild sida i ett Word‑dokument till en rasterbildfil (JPEG). Detta är användbart för att skapa förhandsgranskningar, miniatyrbilder eller för att bädda in dokumentsidor i webbsidor där PDF‑rendering inte är praktiskt.

## Varför extrahera bilder från Word‑dokument?
Många affärsprocesser kräver att man drar ut de ursprungliga grafikerna (logotyper, diagram, foton) från en DOCX‑fil för återanvändning, arkivering eller analys. Aspose.Words gör det enkelt att extrahera varje bild i dess ursprungliga format utan att förlora kvalitet.

## Förutsättningar
- Java Development Kit (JDK 8 eller senare) installerat.
- Aspose.Words for Java‑biblioteket tillagt i ditt projekt. Ladda ner det från [here](https://releases.aspose.com/words/java/).
- Ett exempel‑Word‑dokument (t.ex. `Rendering.docx`) placerat i en känd katalog.

## Steg 1: Spara bilder som TIFF med tröskelkontroll (Skapa flersidig TIFF)
För att generera en högkontrast, gråskala‑TIFF kan du kontrollera binäriseringströskeln. Detta är praktiskt när du behöver en utskrivbar, svart‑vit version av ditt dokument.

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
Om du behöver en TIFF som bara innehåller ett urval av sidor (t.ex. sidor 1‑2), konfigurera ett `PageSet`. Detta demonstrerar **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Steg 3: Spara bilder som 1 BPP indexerad PNG
När du behöver ultralätta svart‑vita PNG‑filer (1 bit per pixel), ställ in pixelformatet därefter. Detta är användbart för att bädda in enkla grafik i scenarier med låg bandbredd.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Steg 4: Spara en sida som JPEG med anpassning (Ställ in bildens ljusstyrka & upplösning)
Här **sparar vi sida som jpeg** samtidigt som vi justerar ljusstyrka, kontrast och upplösning—perfekt för att skapa miniatyrbilder eller web‑klara förhandsgranskningar.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Steg 5: Använda en Page‑Saving‑callback (Avancerad anpassning)
En callback låter dig döpa om varje utdatafil dynamiskt, vilket är användbart när du exporterar många sidor samtidigt.

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

## Komplett källkod för alla scenarier
Nedan finns en enda klass som innehåller alla metoder som demonstrerats ovan. Du kan köra varje test individuellt.

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

## Vanliga problem och lösningar
- **“Unable to locate the document file”** – Verifiera att filvägen använder rätt separator (`/` eller `\\`) för ditt OS.
- **Images appear blank** – Se till att du ställer in ett lämpligt `ImageColorMode` (t.ex. `GRAYSCALE` för TIFF).
- **Out‑of‑memory errors on large documents** – Processa sidor i batcher genom att justera `PageSet`‑intervallet.
- **JPEG quality looks poor** – Öka upplösningen med `setHorizontalResolution` eller `setResolution`.

## Vanliga frågor

**Q: Hur ändrar jag bildformatet när jag sparar med Aspose.Words för Java?**  
A: Ställ in önskat format i `ImageSaveOptions`. För PNG kan du helt enkelt instansiera `ImageSaveOptions` och tilldela `SaveFormat.PNG` om det behövs.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Kan jag anpassa komprimeringsinställningarna för TIFF‑bilder?**  
A: Ja. Använd `setTiffCompression` för att välja en komprimeringsalgoritm såsom `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Hur kan jag spara en specifik sida från ett dokument som en separat bild?**  
A: Använd `setPageSet`‑metoden med ett enskilt sidindex.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Hur tillämpar jag anpassade inställningar på JPEG‑bilder vid sparande?**  
A: Justera egenskaper som ljusstyrka, kontrast och upplösning via `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Hur kan jag använda en callback för att anpassa bildsparande?**  
A: Implementera `IPageSavingCallback` och tilldela den med `setPageSavingCallback`.

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

## Slutsats
Du har nu en komplett verktygslåda för **saving page as jpeg**, extrahering av bilder, kontroll av bildens ljusstyrka, inställning av bildens upplösning i Java och skapande av flersidiga TIFF‑filer med Aspose.Words för Java. Experimentera med olika `ImageSaveOptions`‑inställningar för att passa ditt projekts behov, och utforska det bredare Aspose.Words‑API‑et för ännu fler dokumentmanipuleringsmöjligheter.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}