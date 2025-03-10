---
title: Salvataggio di immagini da documenti in Aspose.Words per Java
linktitle: Salvataggio delle immagini dai documenti
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come salvare le immagini dai documenti usando Aspose.Words per Java con la nostra guida completa passo dopo passo. Personalizza formati, compressione e altro.
weight: 17
url: /it/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvataggio di immagini da documenti in Aspose.Words per Java


## Introduzione al salvataggio di immagini da documenti in Aspose.Words per Java

In questo tutorial, esploreremo come salvare le immagini dai documenti usando Aspose.Words per Java. Tratteremo vari scenari e opzioni di personalizzazione per il salvataggio delle immagini. Questa guida fornisce istruzioni dettagliate con esempi di codice sorgente.

## Prerequisiti

 Prima di iniziare, assicurati di avere la libreria Aspose.Words for Java integrata nel tuo progetto. Puoi scaricarla da[Qui](https://releases.aspose.com/words/java/).

## Passaggio 1: salvataggio delle immagini come TIFF con controllo soglia

Per salvare le immagini in formato TIFF con controllo della soglia, seguire questi passaggi:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Passaggio 2: salvataggio di una pagina specifica come TIFF multipagina

Per salvare una pagina specifica come TIFF multipagina, utilizzare il seguente codice:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Passaggio 3: salvataggio delle immagini come PNG indicizzato a 1 BPP

Per salvare le immagini come PNG indicizzato a 1 BPP, seguire questi passaggi:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Passaggio 4: salvataggio di una pagina in formato JPEG con personalizzazione

Per salvare una pagina specifica come JPEG con opzioni di personalizzazione, utilizzare questo codice:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Passaggio 5: utilizzo del callback di salvataggio della pagina

Puoi usare un callback per personalizzare il salvataggio delle pagine. Ecco un esempio:

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

## Codice sorgente completo per salvare le immagini dai documenti in Aspose.Words per Java

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
	// Impostare "PageSet" su "0" per convertire solo la prima pagina di un documento.
	options.setPageSet(new PageSet(0));
	// Modifica la luminosità e il contrasto dell'immagine.
	// Entrambi sono su una scala da 0 a 1 e di default sono impostati su 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Cambia la risoluzione orizzontale.
	// Il valore predefinito per queste proprietà è 96,0, per una risoluzione di 96 dpi.
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

## Conclusione

Hai imparato come salvare le immagini dai documenti usando Aspose.Words per Java. Questi esempi dimostrano varie opzioni di personalizzazione per il salvataggio delle immagini, tra cui formato, compressione e utilizzo di callback. Esplora altre possibilità con le potenti capacità di Aspose.Words per Java.

## Domande frequenti

### Come posso modificare il formato dell'immagine quando salvo con Aspose.Words per Java?

 È possibile modificare il formato dell'immagine specificando il formato desiderato nel`ImageSaveOptions` Ad esempio, per salvare come PNG, utilizzare`SaveFormat.PNG` come mostrato nel codice:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Posso personalizzare le impostazioni di compressione per le immagini TIFF?

Sì, puoi personalizzare le impostazioni di compressione delle immagini TIFF. Ad esempio, per impostare il metodo di compressione su CCITT_3, usa il seguente codice:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Come posso salvare una pagina specifica di un documento come immagine separata?

 Per salvare una pagina specifica come immagine, utilizzare`setPageSet`metodo in`ImageSaveOptions` Ad esempio, per salvare solo la prima pagina, impostare`PageSet` A`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Salva la prima pagina come immagine
```

### Come faccio ad applicare impostazioni personalizzate alle immagini JPEG durante il salvataggio?

È possibile applicare impostazioni personalizzate alle immagini JPEG utilizzando`ImageSaveOptions`. Regola proprietà come luminosità, contrasto e risoluzione. Ad esempio, per modificare la luminosità a 0,3 e il contrasto a 0,7, usa questo codice:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Come posso utilizzare un callback per personalizzare il salvataggio delle immagini?

 Per utilizzare un callback per personalizzare il salvataggio delle immagini, impostare`PageSavingCallback` In`ImageSaveOptions` . Crea una classe che implementa il`IPageSavingCallback` interfaccia e sovrascrivere il`pageSaving` metodo.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 Quindi, crea una classe che implementa il`IPageSavingCallback` interfaccia e personalizzare il nome del file e la posizione in`pageSaving` metodo.

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
