---
title: Ukládání obrázků z dokumentů v Aspose.Words pro Java
linktitle: Ukládání obrázků z dokumentů
second_title: Aspose.Words Java Document Processing API
description: Naučte se ukládat obrázky z dokumentů pomocí Aspose.Words for Java s naším komplexním průvodcem krok za krokem. Přizpůsobte si formáty, kompresi a další.
weight: 17
url: /cs/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání obrázků z dokumentů v Aspose.Words pro Java


## Úvod do ukládání obrázků z dokumentů v Aspose.Words pro Javu

V tomto tutoriálu prozkoumáme, jak ukládat obrázky z dokumentů pomocí Aspose.Words for Java. Pokryjeme různé scénáře a možnosti přizpůsobení pro ukládání obrázků. Tato příručka poskytuje podrobné pokyny s příklady zdrojového kódu.

## Předpoklady

 Než začnete, ujistěte se, že máte do projektu integrovanou knihovnu Aspose.Words for Java. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/).

## Krok 1: Ukládání obrázků jako TIFF s ovládáním prahu

Chcete-li uložit obrázky ve formátu TIFF s kontrolou prahu, postupujte takto:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Krok 2: Uložení konkrétní stránky jako vícestránkový TIFF

Chcete-li uložit konkrétní stránku jako vícestránkový TIFF, použijte následující kód:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Krok 3: Uložení obrázků jako 1 BPP indexovaný PNG

Chcete-li uložit obrázky jako index PNG s indexem 1 BPP, postupujte takto:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Krok 4: Uložení stránky jako JPEG s přizpůsobením

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

K přizpůsobení ukládání stránky můžete použít zpětné volání. Zde je příklad:

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
	// Chcete-li převést pouze první stránku dokumentu, nastavte "PageSet" na "0".
	options.setPageSet(new PageSet(0));
	// Změňte jas a kontrast obrázku.
	// Oba jsou na stupnici 0-1 a ve výchozím nastavení jsou na 0,5.
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

Naučili jste se ukládat obrázky z dokumentů pomocí Aspose.Words for Java. Tyto příklady demonstrují různé možnosti přizpůsobení pro ukládání obrázků, včetně použití formátu, komprese a zpětného volání. Prozkoumejte další možnosti s výkonnými schopnostmi Aspose.Words for Java.

## FAQ

### Jak změním formát obrázku při ukládání pomocí Aspose.Words for Java?

 Formát obrázku můžete změnit zadáním požadovaného formátu v`ImageSaveOptions` . Chcete-li například uložit jako PNG, použijte`SaveFormat.PNG` jak je uvedeno v kódu:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Mohu upravit nastavení komprese pro obrázky TIFF?

Ano, můžete upravit nastavení komprese obrazu TIFF. Chcete-li například nastavit metodu komprese na CCITT_3, použijte následující kód:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Jak mohu uložit konkrétní stránku z dokumentu jako samostatný obrázek?

 Chcete-li uložit konkrétní stránku jako obrázek, použijte`setPageSet`metoda v`ImageSaveOptions` . Chcete-li například uložit pouze první stránku, nastavte`PageSet` na`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Uložte první stránku jako obrázek
```

### Jak použiji vlastní nastavení na obrázky JPEG při ukládání?

Vlastní nastavení můžete použít na obrázky JPEG pomocí`ImageSaveOptions`. Upravte vlastnosti, jako je jas, kontrast a rozlišení. Chcete-li například změnit jas na 0,3 a kontrast na 0,7, použijte tento kód:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Jak mohu použít zpětné volání pro přizpůsobení ukládání obrázků?

 Chcete-li použít zpětné volání pro přizpůsobení ukládání obrázků, nastavte`PageSavingCallback` v`ImageSaveOptions` . Vytvořte třídu, která implementuje`IPageSavingCallback` rozhraní a přepsat`pageSaving` metoda.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 Poté vytvořte třídu, která implementuje`IPageSavingCallback` rozhraní a přizpůsobit název souboru a umístění v`pageSaving` metoda.

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
