---
title: Képek mentése dokumentumokból az Aspose.Words for Java programban
linktitle: Képek mentése a dokumentumokból
second_title: Aspose.Words Java Document Processing API
description: Átfogó, lépésenkénti útmutatónkkal megtudhatja, hogyan menthet képeket dokumentumokból az Aspose.Words for Java használatával. Testreszabhatja a formátumokat, a tömörítést és egyebeket.
weight: 17
url: /hu/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Képek mentése dokumentumokból az Aspose.Words for Java programban


## Bevezetés a képek dokumentumokból történő mentésébe az Aspose.Words for Java programban

Ebben az oktatóanyagban megvizsgáljuk, hogyan lehet képeket menteni dokumentumokból az Aspose.Words for Java használatával. A képmentés különféle forgatókönyveivel és testreszabási lehetőségeivel foglalkozunk. Ez az útmutató lépésről lépésre tartalmazza a forráskód-példákat.

## Előfeltételek

 Mielőtt elkezdené, győződjön meg arról, hogy az Aspose.Words for Java könyvtár integrálva van a projektjébe. Letöltheti innen[itt](https://releases.aspose.com/words/java/).

## 1. lépés: Képek mentése TIFF formátumban a Threshold Control segítségével

Ha a képeket TIFF formátumban szeretné menteni küszöbérték-szabályozással, kövesse az alábbi lépéseket:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## 2. lépés: Adott oldal mentése többoldalas TIFF formátumban

Egy adott oldal többoldalas TIFF-fájlként történő mentéséhez használja a következő kódot:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## 3. lépés: Képek mentése 1 BPP-vel indexelt PNG-ként

Ha 1 BPP-vel indexelt PNG-ként szeretné menteni a képeket, kövesse az alábbi lépéseket:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 4. lépés: Oldal mentése JPEG formátumban testreszabással

Egy adott oldal testreszabási lehetőségekkel rendelkező JPEG formátumban történő mentéséhez használja ezt a kódot:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## 5. lépés: Az Oldalmentés Visszahívás használata

Az oldalmentés személyre szabásához használhatja a visszahívást. Íme egy példa:

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

## Teljes forráskód képek mentéséhez az Aspose.Words for Java dokumentumaiból

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
	// Állítsa a "PageSet" értéket "0"-ra, ha csak a dokumentum első oldalát szeretné konvertálni.
	options.setPageSet(new PageSet(0));
	// Módosítsa a kép fényerejét és kontrasztját.
	// Mindkettő 0-1 skálán van, és alapértelmezés szerint 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Módosítsa a vízszintes felbontást.
	// Ezeknek a tulajdonságoknak az alapértelmezett értéke 96,0, 96 dpi felbontás esetén.
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

## Következtetés

Megtanulta, hogyan menthet képeket dokumentumokból az Aspose.Words for Java használatával. Ezek a példák a képmentés különféle testreszabási lehetőségeit mutatják be, beleértve a formátumot, a tömörítést és a visszahívási használatot. Fedezzen fel további lehetőségeket az Aspose.Words segítségével a Java erőteljes képességeiért.

## GYIK

### Hogyan változtathatom meg a képformátumot az Aspose.Words for Java segítségével történő mentéskor?

 Módosíthatja a képformátumot a kívánt formátum megadásával a`ImageSaveOptions` . Például a PNG formátumban történő mentéshez használja a`SaveFormat.PNG` a kódban látható módon:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Testreszabhatom a TIFF-képek tömörítési beállításait?

Igen, testreszabhatja a TIFF képtömörítési beállításokat. Például a tömörítési módszer CCITT_3 értékre állításához használja a következő kódot:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Hogyan menthetek egy adott oldalt egy dokumentumból külön képként?

 Egy adott oldal képként való mentéséhez használja a`setPageSet`módszer be`ImageSaveOptions` . Például, ha csak az első oldalt szeretné menteni, állítsa be a`PageSet` hogy`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Mentse el az első oldalt képként
```

### Hogyan alkalmazhatok egyéni beállításokat a JPEG képekre mentéskor?

Egyéni beállításokat alkalmazhat a JPEG képekre a használatával`ImageSaveOptions`. Az olyan tulajdonságok beállítása, mint a fényerő, kontraszt és felbontás. Ha például a fényerőt 0,3-ra és a kontrasztot 0,7-re szeretné módosítani, használja ezt a kódot:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Hogyan használhatom a visszahívást a képmentés testreszabásához?

 Ha visszahívást szeretne használni a képmentés testreszabásához, állítsa be a`PageSavingCallback` be`ImageSaveOptions` . Hozzon létre egy osztályt, amely megvalósítja a`IPageSavingCallback` felületet, és felülírja a`pageSaving` módszer.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 Ezután hozzon létre egy osztályt, amely megvalósítja a`IPageSavingCallback` felületet, és testreszabhatja a fájl nevét és helyét a`pageSaving` módszer.

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
