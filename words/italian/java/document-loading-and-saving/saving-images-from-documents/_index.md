---
date: 2025-12-27
description: Scopri come salvare una pagina come JPEG ed estrarre le immagini dai
  documenti Word utilizzando Aspose.Words per Java. Include suggerimenti per impostare
  la luminosità dell’immagine, la risoluzione e creare TIFF multipagina.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Come salvare una pagina come JPEG ed estrarre immagini dai documenti con Aspose.Words
  per Java
url: /it/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Salva pagina come JPEG ed estrai immagini dai documenti in Aspose.Words per Java

In questo tutorial scoprirai come **save page as jpeg** da un documento Word e come **extract images from Word** file usando Aspose.Words per Java. Esamineremo scenari reali come impostare la luminosità dell'immagine, regolare la risoluzione dell'immagine in Java e creare un TIFF multipagina. Ogni passaggio include snippet di codice pronti da eseguire così potrai copiare, incollare e vedere i risultati immediatamente.

## Risposte rapide
- **Posso salvare una singola pagina come JPEG?** Sì – usa `ImageSaveOptions` con `setPageSet(new PageSet(pageIndex))`.
- **Come cambio la luminosità dell'immagine?** Chiama `options.setImageBrightness(floatValue)` (intervallo 0‑1).
- **Cosa fare se ho bisogno di un TIFF multipagina?** Imposta un `PageSet` che copra le pagine desiderate e scegli un metodo di compressione TIFF.
- **Come posso controllare la risoluzione dell'immagine?** Usa `setResolution(floatDpi)` o `setHorizontalResolution(floatDpi)`.
- **Ho bisogno di una licenza per la produzione?** È necessaria una licenza valida di Aspose.Words per l'uso non‑trial.

## Cos'è “save page as jpeg”?
Salvare una pagina come JPEG significa convertire una singola pagina di un documento Word in un file immagine raster (JPEG). È utile per generare anteprime, creare miniature o incorporare pagine di documenti in pagine web dove il rendering PDF non è pratico.

## Perché estrarre immagini dai documenti Word?
Molti flussi di lavoro aziendali richiedono di estrarre le grafiche originali (loghi, diagrammi, foto) da un file DOCX per riutilizzo, archiviazione o analisi. Aspose.Words rende semplice estrarre ogni immagine nel suo formato nativo senza perdita di qualità.

## Prerequisiti
- Java Development Kit (JDK 8 o successivo) installato.
- Libreria Aspose.Words per Java aggiunta al tuo progetto. Scaricala da [here](https://releases.aspose.com/words/java/).
- Un documento Word di esempio (ad es., `Rendering.docx`) posizionato in una directory nota.

## Passo 1: Salva immagini come TIFF con controllo della soglia (Crea TIFF multipagina)
Per generare un TIFF ad alto contrasto in scala di grigi puoi controllare la soglia di binarizzazione. È utile quando ti serve una versione stampabile in bianco‑nero del documento.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Passo 2: Salva una pagina specifica come TIFF multipagina
Se ti serve un TIFF che contenga solo un sottoinsieme di pagine (ad es., pagine 1‑2), configura un `PageSet`. Questo dimostra **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Passo 3: Salva immagini come PNG indicizzato a 1 BPP
Quando ti servono PNG ultra‑leggeri in bianco‑nero (1 bit per pixel), imposta il formato pixel di conseguenza. È utile per incorporare grafiche semplici in scenari a bassa larghezza di banda.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Passo 4: Salva una pagina come JPEG con personalizzazione (Imposta luminosità e risoluzione immagine)
Qui **save page as jpeg** mentre regoli luminosità, contrasto e risoluzione—perfetto per creare miniature o anteprime pronte per il web.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Passo 5: Utilizzare un callback di salvataggio pagina (Personalizzazione avanzata)
Un callback ti consente di rinominare dinamicamente ogni file di output, utile quando si esportano molte pagine contemporaneamente.

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

## Codice sorgente completo per tutti gli scenari
Di seguito è presente una singola classe che contiene tutti i metodi mostrati sopra. Puoi eseguire ogni test singolarmente.

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

## Problemi comuni e soluzioni
- **“Unable to locate the document file”** – Verifica che il percorso del file utilizzi il separatore corretto (`/` o `\\`) per il tuo OS.
- **Images appear blank** – Assicurati di impostare un `ImageColorMode` appropriato (ad es., `GRAYSCALE` per TIFF).
- **Out‑of‑memory errors on large documents** – Processa le pagine in batch regolando l'intervallo `PageSet`.
- **JPEG quality looks poor** – Aumenta la risoluzione con `setHorizontalResolution` o `setResolution`.

## Domande frequenti

**Q: Come cambio il formato immagine quando salvo con Aspose.Words per Java?**  
A: Imposta il formato desiderato in `ImageSaveOptions`. Per PNG, puoi semplicemente istanziare `ImageSaveOptions` e assegnare `SaveFormat.PNG` se necessario.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Posso personalizzare le impostazioni di compressione per le immagini TIFF?**  
A: Sì. Usa `setTiffCompression` per scegliere un algoritmo di compressione come `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Come posso salvare una pagina specifica da un documento come immagine separata?**  
A: Usa il metodo `setPageSet` con un indice di pagina singolo.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Come applico impostazioni personalizzate alle immagini JPEG durante il salvataggio?**  
A: Regola proprietà come luminosità, contrasto e risoluzione tramite `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Come posso usare un callback per personalizzare il salvataggio delle immagini?**  
A: Implementa `IPageSavingCallback` e assegnalo con `setPageSavingCallback`.

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

## Conclusione
Ora disponi di una toolbox completa per **saving page as jpeg**, estrarre immagini, controllare la luminosità dell'immagine, impostare la risoluzione dell'immagine in Java e creare file TIFF multipagina con Aspose.Words per Java. Sperimenta con diverse impostazioni `ImageSaveOptions` per adattarle alle esigenze del tuo progetto e esplora l'API più ampia di Aspose.Words per ulteriori capacità di manipolazione dei documenti.

---

**Ultimo aggiornamento:** 2025-12-27  
**Testato con:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}