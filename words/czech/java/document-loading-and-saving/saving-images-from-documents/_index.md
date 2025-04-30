---
"description": "Naučte se, jak ukládat obrázky z dokumentů pomocí Aspose.Words pro Javu s naším komplexním podrobným návodem. Přizpůsobte si formáty, kompresi a další."
"linktitle": "Ukládání obrázků z dokumentů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Ukládání obrázků z dokumentů v Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání obrázků z dokumentů v Aspose.Words pro Javu


## Úvod do ukládání obrázků z dokumentů v Aspose.Words pro Javu

V tomto tutoriálu se podíváme na to, jak ukládat obrázky z dokumentů pomocí Aspose.Words pro Javu. Probereme různé scénáře a možnosti přizpůsobení pro ukládání obrázků. Tato příručka poskytuje podrobné pokyny s příklady zdrojového kódu.

## Předpoklady

Než začnete, ujistěte se, že máte ve svém projektu integrovanou knihovnu Aspose.Words pro Javu. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/java/).

## Krok 1: Ukládání obrázků ve formátu TIFF s nastavením prahové hodnoty

Chcete-li uložit obrázky ve formátu TIFF s nastavením prahových hodnot, postupujte takto:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Krok 2: Uložení konkrétní stránky jako vícestránkového TIFF

Chcete-li uložit konkrétní stránku jako vícestránkový TIFF, použijte následující kód:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Krok 3: Uložení obrázků jako PNG s indexem 1 BPP

Chcete-li uložit obrázky jako PNG s indexem 1 BPP, postupujte takto:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Krok 4: Uložení stránky jako JPEG s úpravami

Chcete-li uložit konkrétní stránku jako JPEG s možnostmi přizpůsobení, použijte tento kód:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Krok 5: Použití zpětného volání pro ukládání stránky

Pro přizpůsobení ukládání stránky můžete použít zpětné volání. Zde je příklad:

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

## Kompletní zdrojový kód pro ukládání obrázků z dokumentů v Aspose.Words pro Javu

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
	// Nastavte „PageSet“ na „0“, chcete-li převést pouze první stránku dokumentu.
	options.setPageSet(new PageSet(0));
	// Změňte jas a kontrast obrázku.
	// Oba jsou na stupnici 0-1 a standardně jsou na 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Změňte horizontální rozlišení.
	// Výchozí hodnota pro tyto vlastnosti je 96,0 pro rozlišení 96 dpi.
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

## Závěr

Naučili jste se, jak ukládat obrázky z dokumentů pomocí Aspose.Words pro Javu. Tyto příklady demonstrují různé možnosti přizpůsobení pro ukládání obrázků, včetně formátování, komprese a použití zpětného volání. Prozkoumejte další možnosti s výkonnými funkcemi Aspose.Words pro Javu.

## Často kladené otázky

### Jak změním formát obrázku při ukládání pomocí Aspose.Words pro Javu?

Formát obrázku můžete změnit zadáním požadovaného formátu v `ImageSaveOptions`Například pro uložení jako PNG použijte `SaveFormat.PNG` jak je znázorněno v kódu:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Mohu si přizpůsobit nastavení komprese pro obrázky TIFF?

Ano, nastavení komprese obrázků TIFF si můžete přizpůsobit. Například pro nastavení metody komprese na CCITT_3 použijte následující kód:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Jak mohu uložit konkrétní stránku z dokumentu jako samostatný obrázek?

Chcete-li uložit konkrétní stránku jako obrázek, použijte `setPageSet` metoda v `ImageSaveOptions`Například chcete-li uložit pouze první stránku, nastavte `PageSet` na `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Uložit první stránku jako obrázek
```

### Jak mohu při ukládání použít vlastní nastavení na obrázky JPEG?

Vlastní nastavení pro obrázky JPEG můžete použít pomocí `ImageSaveOptions`Upravte vlastnosti, jako je jas, kontrast a rozlišení. Například pro změnu jasu na 0,3 a kontrastu na 0,7 použijte tento kód:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Jak mohu použít zpětné volání pro přizpůsobení ukládání obrázků?

Chcete-li použít zpětné volání pro přizpůsobení ukládání obrázků, nastavte `PageSavvgCallback` in `ImageSaveOptions`Vytvořte třídu, která implementuje `IPageSavingCallback` rozhraní a přepsat `pageSaving` metoda.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Pak vytvořte třídu, která implementuje `IPageSavingCallback` rozhraní a přizpůsobit název souboru a umístění v něm `pageSaving` metoda.

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