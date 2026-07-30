---
date: 2025-12-27
description: Ismerje meg, hogyan menthet el egy oldalt JPEG formátumban, és hogyan
  nyerhet ki képeket Word-dokumentumokból az Aspose.Words for Java használatával.
  Tippeket tartalmaz a kép fényerőjének, felbontásának beállításához, valamint többoldalas
  TIFF létrehozásához.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Hogyan menthetünk egy oldalt JPEG-ként, és hogyan nyerhetünk ki képeket dokumentumokból
  az Aspose.Words for Java segítségével
url: /hu/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Oldal mentése JPEG‑ként és képek kinyerése dokumentumokból az Aspose.Words for Java segítségével

Ebben az útmutatóban megtudhatja, hogyan **mentse el az oldalt JPEG‑ként** egy Word‑dokumentumból, és hogyan **nyerjen ki képeket Word‑fájlokból** az Aspose.Words for Java használatával. Valós példákon keresztül mutatjuk be, hogyan állítható be a kép fényerőssége, a kép felbontása Java‑ban, valamint hogyan hozható létre többoldalas TIFF. Minden lépéshez kész‑kódú példák tartoznak, amelyeket egyszerűen másolhat, beilleszthet és azonnal láthatja az eredményt.

## Gyors válaszok
- **Menthetek egyetlen oldalt JPEG‑ként?** Igen – használja az `ImageSaveOptions`‑t a `setPageSet(new PageSet(pageIndex))` beállítással.
- **Hogyan változtathatom meg a kép fényerősségét?** Hívja a `options.setImageBrightness(floatValue)`‑t (0‑1 tartományban).
- **Mi van, ha többoldalas TIFF‑re van szükségem?** Állítson be egy `PageSet`‑et, amely lefedi a kívánt oldalakat, és válasszon TIFF‑tömörítési módszert.
- **Hogyan szabályozhatom a kép felbontását?** Használja a `setResolution(floatDpi)` vagy a `setHorizontalResolution(floatDpi)` metódust.
- **Szükség van licencre a termeléshez?** Érvényes Aspose.Words licenc szükséges a nem‑próba használathoz.

## Mi az a „save page as jpeg”?
Az oldal JPEG‑ként való mentése azt jelenti, hogy egy Word‑dokumentum egyetlen oldalát raszteres képformátumba (JPEG) konvertáljuk. Ez hasznos előnézetek, bélyegképek készítéséhez vagy a dokumentumoldalak weboldalakba való beágyazásához, ahol a PDF‑megjelenítés nem praktikus.

## Miért érdemes képeket kinyerni Word‑dokumentumokból?
Sok üzleti folyamat megköveteli az eredeti grafikák (logók, diagramok, fényképek) kinyerését egy DOCX‑fájlból újbóli felhasználás, archiválás vagy elemzés céljából. Az Aspose.Words egyszerűvé teszi minden kép natív formátumban történő kinyerését minőségvesztés nélkül.

## Előfeltételek
- Telepített Java Development Kit (JDK 8 vagy újabb).
- Az Aspose.Words for Java könyvtár hozzáadva a projekthez. Letölthető [innen](https://releases.aspose.com/words/java/).
- Egy minta Word‑dokumentum (pl. `Rendering.docx`) egy ismert könyvtárban.

## 1. lépés: Képek mentése TIFF‑ként küszöbérték‑vezérléssel (Többoldalas TIFF létrehozása)
Magas kontrasztú, szürkeárnyalatos TIFF generálásához szabályozhatja a binarizálási küszöböt. Ez akkor hasznos, ha nyomtatható, fekete‑fehér változatra van szükség.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## 2. lépés: Egy adott oldal mentése többoldalas TIFF‑ként
Ha csak egy oldalhalmazt (pl. 1‑2. oldal) tartalmazó TIFF‑re van szükség, állítson be egy `PageSet`‑et. Ez bemutatja a **create multipage tiff** funkciót.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## 3. lépés: Képek mentése 1 BPP indexelt PNG‑ként
Amikor ultra‑könnyű fekete‑fehér PNG‑kre van szükség (1 bit per pixel), állítsa be a megfelelő pixelformátumot. Alacsony sávszélességű környezetekben hasznos egyszerű grafikák beágyazásához.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 4. lépés: Oldal mentése JPEG‑ként testreszabással (kép fényerő és felbontás beállítása)
Itt **save page as jpeg**‑t hajtunk végre, miközben a fényerőt, kontrasztot és felbontást is módosítjuk – tökéletes bélyegképek vagy web‑kész előnézetek létrehozásához.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## 5. lépés: Oldal‑mentés visszahívás használata (haladó testreszabás)
A visszahívás lehetővé teszi, hogy minden kimeneti fájlt dinamikusan átnevezzünk, ami akkor hasznos, ha egyszerre sok oldalt exportálunk.

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

## Teljes forráskód minden szcenárióhoz
Az alábbi egyetlen osztály tartalmazza a fent bemutatott összes metódust. Egyenként futtathatja a teszteket.

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

## Gyakori problémák és megoldások
- **„Unable to locate the document file”** – Ellenőrizze, hogy a fájlútvonal a megfelelő elválasztót (`/` vagy `\\`) használja‑e az operációs rendszerhez.
- **A képek üresek** – Győződjön meg róla, hogy megfelelő `ImageColorMode`‑t állított be (pl. `GRAYSCALE` a TIFF‑hez).
- **Memória‑hiány nagy dokumentumoknál** – Dolgozzon oldalanként, a `PageSet`‑tartományt kisebb kötegekben állítva.
- **A JPEG minősége gyenge** – Növelje a felbontást a `setHorizontalResolution` vagy `setResolution` használatával.

## Gyakran feltett kérdések

**Q: Hogyan változtathatom meg a kép formátumát az Aspose.Words for Java‑val történő mentéskor?**  
A: Állítsa be a kívánt formátumot az `ImageSaveOptions`‑ban. PNG‑hez egyszerűen hozza létre az `ImageSaveOptions`‑t, és adja meg a `SaveFormat.PNG`‑t, ha szükséges.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Testreszabhatom a TIFF‑képek tömörítési beállításait?**  
A: Igen. Használja a `setTiffCompression`‑t, hogy kiválasszon egy tömörítési algoritmust, például `CCITT_3`‑at.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Hogyan menthetek egy adott oldalt a dokumentumból külön képként?**  
A: Használja a `setPageSet` metódust egyetlen oldal indexével.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Hogyan alkalmazhatok egyedi beállításokat JPEG‑képekre mentéskor?**  
A: Állítsa be a fényerőt, kontrasztot és felbontást az `ImageSaveOptions`‑on keresztül.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Hogyan használhatok visszahívást a kép mentés testreszabásához?**  
A: Implementálja az `IPageSavingCallback`‑et, és rendelje hozzá a `setPageSavingCallback`‑hez.

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

## Összegzés
Most már rendelkezik egy teljes eszköztárral a **saving page as jpeg**, képek kinyeréséhez, a kép fényerősségének szabályozásához, a kép felbontásának beállításához Java‑ban, valamint többoldalas TIFF‑fájlok létrehozásához az Aspose.Words for Java segítségével. Kísérletezzen különböző `ImageSaveOptions` beállításokkal, hogy megfeleljenek projektje igényeinek, és fedezze fel az Aspose.Words API további lehetőségeit a dokumentumkezelés még szélesebb körű felhasználásához.

---

**Last Updated:** 2025-12-27  
**Tested With:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}