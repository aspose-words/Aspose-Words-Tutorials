---
date: 2025-12-27
description: Naučte se, jak uložit stránku jako JPEG a extrahovat obrázky z dokumentů
  Word pomocí Aspose.Words pro Javu. Obsahuje tipy pro nastavení jasu obrázku, rozlišení
  a vytváření více stránkových TIFF souborů.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Jak uložit stránku jako JPEG a extrahovat obrázky z dokumentů pomocí Aspose.Words
  pro Javu
url: /cs/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uložení stránky jako JPEG a extrakce obrázků z dokumentů v Aspose.Words pro Java

V tomto tutoriálu se dozvíte, jak **uložit stránku jako jpeg** z dokumentu Word a jak **extrahovat obrázky z Word** souborů pomocí Aspose.Words pro Java. Provedeme vás reálnými scénáři, jako je nastavení jasu obrázku, úprava rozlišení obrázku v Javě a vytvoření více stránkového TIFFu. Každý krok obsahuje připravené ukázky kódu, které můžete zkopírovat, vložit a okamžitě vidět výsledky.

## Rychlé odpovědi
- **Mohu uložit jednu stránku jako JPEG?** Ano – použijte `ImageSaveOptions` s `setPageSet(new PageSet(pageIndex))`.
- **Jak změním jas obrázku?** Zavolejte `options.setImageBrightness(floatValue)` (rozsah 0‑1).
- **Co když potřebuji více stránkový TIFF?** Nastavte `PageSet` pokrývající požadované stránky a vyberte metodu komprese TIFF.
- **Jak mohu ovládat rozlišení obrázku?** Použijte `setResolution(floatDpi)` nebo `setHorizontalResolution(floatDpi)`.
- **Potřebuji licenci pro produkční použití?** Platná licence Aspose.Words je vyžadována pro ne‑zkušební použití.

## Co znamená „uložit stránku jako jpeg“?
Uložení stránky jako JPEG znamená převod jedné stránky dokumentu Word do rastrového souboru obrázku (JPEG). To je užitečné pro generování náhledů, tvorbu miniatur nebo vložení stránek dokumentu do webových stránek, kde není praktické renderování PDF.

## Proč extrahovat obrázky z dokumentů Word?
Mnoho obchodních procesů vyžaduje vytažení původní grafiky (loga, diagramy, fotografie) z souboru DOCX pro opětovné použití, archivaci nebo analýzu. Aspose.Words umožňuje snadno extrahovat každý obrázek v jeho nativním formátu bez ztráty kvality.

## Požadavky
- Java Development Kit (JDK 8 nebo novější) nainstalovaný.
- Knihovna Aspose.Words pro Java přidána do vašeho projektu. Stáhněte ji z [zde](https://releases.aspose.com/words/java/).
- Ukázkový Word dokument (např. `Rendering.docx`) umístěný v známém adresáři.

## Krok 1: Uložení obrázků jako TIFF s řízením prahu (Vytvoření více stránkového TIFF)
Pro vytvoření vysoce kontrastního, černobílého TIFFu můžete řídit práh binarizace. To je užitečné, když potřebujete tisknutelnou černobílou verzi dokumentu.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Krok 2: Uložení konkrétní stránky jako více stránkový TIFF
Pokud potřebujete TIFF, který obsahuje pouze podmnožinu stránek (např. stránky 1‑2), nakonfigurujte `PageSet`. Toto demonstruje **vytvoření více stránkového TIFF**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Krok 3: Uložení obrázků jako 1 BPP indexovaný PNG
Když potřebujete ultra‑lehké černobílé PNG (1 bit na pixel), nastavte odpovídající formát pixelu. To je užitečné pro vložení jednoduché grafiky v situacích s nízkou šířkou pásma.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Krok 4: Uložení stránky jako JPEG s přizpůsobením (Nastavení jasu a rozlišení obrázku)
Zde **uložíme stránku jako jpeg** při úpravě jasu, kontrastu a rozlišení – ideální pro tvorbu miniatur nebo náhledů připravených pro web.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Krok 5: Použití zpětného volání při ukládání stránky (Pokročilé přizpůsobení)
Zpětné volání vám umožní dynamicky přejmenovat každý výstupní soubor, což je užitečné při exportu mnoha stránek najednou.

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

## Kompletní zdrojový kód pro všechny scénáře
Níže je jedna třída, která obsahuje všechny výše demonstrované metody. Každý test můžete spustit samostatně.

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

## Časté problémy a řešení
- **„Nelze najít soubor dokumentu“** – Ověřte, že cesta k souboru používá správný oddělovač (`/` nebo `\\`) pro váš OS.
- **Obrázky jsou prázdné** – Ujistěte se, že jste nastavili vhodný `ImageColorMode` (např. `GRAYSCALE` pro TIFF).
- **Chyby nedostatku paměti u velkých dokumentů** – Zpracovávejte stránky po dávkách úpravou rozsahu `PageSet`.
- **Kvalita JPEG vypadá špatně** – Zvyšte rozlišení pomocí `setHorizontalResolution` nebo `setResolution`.

## Často kladené otázky

**Q: Jak změním formát obrázku při ukládání pomocí Aspose.Words pro Java?**  
A: Nastavte požadovaný formát v `ImageSaveOptions`. Pro PNG můžete jednoduše vytvořit `ImageSaveOptions` a přiřadit `SaveFormat.PNG`, pokud je potřeba.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Mohu přizpůsobit nastavení komprese pro TIFF obrázky?**  
A: Ano. Použijte `setTiffCompression` k výběru kompresního algoritmu, například `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Jak mohu uložit konkrétní stránku z dokumentu jako samostatný obrázek?**  
A: Použijte metodu `setPageSet` s jedním indexem stránky.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Jak aplikovat vlastní nastavení na JPEG obrázky při ukládání?**  
A: Upravte vlastnosti jako jas, kontrast a rozlišení pomocí `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Jak mohu použít zpětné volání pro přizpůsobení ukládání obrázku?**  
A: Implementujte `IPageSavingCallback` a přiřaďte jej pomocí `setPageSavingCallback`.

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

## Závěr
Nyní máte kompletní sadu nástrojů pro **ukládání stránky jako jpeg**, extrakci obrázků, řízení jasu obrázku, nastavení rozlišení obrázku v Javě a vytváření více stránkových TIFF souborů s Aspose.Words pro Java. Experimentujte s různými nastaveními `ImageSaveOptions`, aby vyhovovaly potřebám vašeho projektu, a prozkoumejte širší API Aspose.Words pro ještě více možností manipulace s dokumenty.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}