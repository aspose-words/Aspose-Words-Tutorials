---
"description": "Tanuld meg, hogyan menthetsz képeket dokumentumokból az Aspose.Words for Java segítségével átfogó, lépésről lépésre szóló útmutatónkkal. Testreszabhatod a formátumokat, a tömörítést és egyebeket."
"linktitle": "Képek mentése dokumentumokból"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Képek mentése dokumentumokból az Aspose.Words for Java programban"
"url": "/hu/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Képek mentése dokumentumokból az Aspose.Words for Java programban


## Bevezetés a képek mentésébe dokumentumokból az Aspose.Words for Java programban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan menthetünk képeket dokumentumokból az Aspose.Words for Java használatával. Áttekintjük a képmentés különböző forgatókönyveit és testreszabási lehetőségeit. Ez az útmutató lépésről lépésre bemutatja a forráskód példáit.

## Előfeltételek

Mielőtt elkezdenéd, győződj meg róla, hogy az Aspose.Words for Java könyvtár integrálva van a projektedbe. Letöltheted innen: [itt](https://releases.aspose.com/words/java/).

## 1. lépés: Képek mentése TIFF formátumban küszöbérték-szabályozással

A képek TIFF formátumban, küszöbérték-vezérléssel történő mentéséhez kövesse az alábbi lépéseket:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## 2. lépés: Egy adott oldal mentése többoldalas TIFF formátumban

Egy adott oldal többoldalas TIFF fájlként való mentéséhez használja a következő kódot:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## 3. lépés: Képek mentése 1 BPP indexelt PNG formátumban

Képek 1 BPP indexelt PNG formátumban történő mentéséhez kövesse az alábbi lépéseket:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## 4. lépés: Oldal mentése JPEG formátumban testreszabással

Egy adott oldal JPEG formátumban, testreszabási beállításokkal történő mentéséhez használja ezt a kódot:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## 5. lépés: Oldalmentő visszahívás használata

Visszahívás segítségével testreszabhatja az oldal mentését. Íme egy példa:

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

## Teljes forráskód képek mentéséhez dokumentumokból az Aspose.Words for Java programban

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
	// Állítsa a „PageSet” értékét „0”-ra, ha csak a dokumentum első oldalát szeretné konvertálni.
	options.setPageSet(new PageSet(0));
	// Módosítsa a kép fényerejét és kontrasztját.
	// Mindkettő 0-1 skálán van, és alapértelmezés szerint 0,5-ön állnak.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Változtasd meg a vízszintes felbontást.
	// Ezen tulajdonságok alapértelmezett értéke 96,0, ami 96 dpi felbontást jelent.
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

Megtanultad, hogyan menthetsz képeket dokumentumokból az Aspose.Words for Java segítségével. Ezek a példák a képmentés különböző testreszabási lehetőségeit mutatják be, beleértve a formátumot, a tömörítést és a visszahívási használatot. Fedezz fel további lehetőségeket az Aspose.Words for Java hatékony funkcióival.

## GYIK

### Hogyan változtathatom meg a képformátumot az Aspose.Words for Java programmal történő mentéskor?

A képformátumot a kívánt formátum megadásával módosíthatja a `ImageSaveOptions`Például PNG formátumban történő mentéshez használja a következőt: `SaveFormat.PNG` ahogy a kódban látható:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Testreszabhatom a TIFF képek tömörítési beállításait?

Igen, testreszabhatja a TIFF képtömörítési beállításait. Például a CCITT_3 tömörítési módszer beállításához használja a következő kódot:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Hogyan menthetek el egy adott oldalt egy dokumentumból külön képként?

Egy adott oldal képként való mentéséhez használja a `setPageSet` módszer `ImageSaveOptions`Például, ha csak az első oldalt szeretné menteni, állítsa be a `PageSet` hogy `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Az első oldal mentése képként
```

### Hogyan alkalmazhatok egyéni beállításokat JPEG képekre mentéskor?

Egyéni beállításokat alkalmazhat JPEG képekre a következő használatával: `ImageSaveOptions`. Állítsa be az olyan tulajdonságokat, mint a fényerő, a kontraszt és a felbontás. Például a fényerő 0,3-ra, a kontraszt pedig 0,7-re állításához használja ezt a kódot:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Hogyan használhatok visszahívást a képmentés testreszabásához?

Ha visszahívást szeretne használni a képmentés testreszabásához, állítsa be a `PageSavbangCallback` in `ImageSaveOptions`Hozz létre egy osztályt, amely megvalósítja a következőt: `IPageSavingCallback` interfész és felülírja a `pageSaving` módszer.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Ezután hozz létre egy osztályt, amely megvalósítja a `IPageSavingCallback` felületet, és szabja testre a fájlnevet és a helyet a `pageSaving` módszer.

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