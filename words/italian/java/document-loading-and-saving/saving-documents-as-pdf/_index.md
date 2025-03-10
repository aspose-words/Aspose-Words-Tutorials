---
title: Salvataggio di documenti come PDF in Aspose.Words per Java
linktitle: Salvataggio dei documenti come PDF
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come salvare i documenti Word come PDF usando Aspose.Words per Java. Personalizza font, proprietà e qualità delle immagini. Una guida completa per la conversione in PDF.
weight: 22
url: /it/java/document-loading-and-saving/saving-documents-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvataggio di documenti come PDF in Aspose.Words per Java


## Introduzione al salvataggio di documenti in formato PDF in Aspose.Words per Java

In questa guida passo passo, esploreremo come salvare i documenti in formato PDF usando Aspose.Words per Java. Tratteremo vari aspetti della conversione PDF e forniremo esempi di codice per semplificare il processo.

## Prerequisiti

Prima di iniziare, assicurati di avere i seguenti prerequisiti:

- Java Development Kit (JDK) installato sul sistema.
-  Aspose.Words per la libreria Java. Puoi scaricarla da[Qui](https://releases.aspose.com/words/java/).

## Conversione di un documento in PDF

Per convertire un documento Word in PDF, puoi utilizzare il seguente frammento di codice:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Sostituire`"input.docx"` con il percorso del tuo documento Word e`"output.pdf"` con il percorso desiderato per il file PDF di output.

## Controllo delle opzioni di salvataggio PDF

 È possibile controllare varie opzioni di salvataggio PDF utilizzando`PdfSaveOptions` classe. Ad esempio, puoi impostare il titolo visualizzato per il documento PDF come segue:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Incorporamento di caratteri in PDF

Per incorporare i font nel PDF generato, utilizzare il seguente codice:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Personalizzazione delle proprietà del documento

Puoi personalizzare le proprietà del documento nel PDF generato. Ad esempio:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Esportazione della struttura del documento

 Per esportare la struttura del documento, impostare`exportDocumentStructure` opzione per`true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Compressione delle immagini

È possibile controllare la compressione delle immagini utilizzando il seguente codice:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Aggiornamento dell'ultima proprietà stampata

Per aggiornare la proprietà "Ultima stampa" nel PDF, utilizzare:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Rendering degli effetti 3D DML

Per il rendering avanzato degli effetti DML 3D, impostare la modalità di rendering:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Interpolazione delle immagini

È possibile abilitare l'interpolazione delle immagini per migliorarne la qualità:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Conclusione

Aspose.Words per Java offre funzionalità complete per convertire documenti Word in formato PDF con flessibilità e opzioni di personalizzazione. Puoi controllare vari aspetti dell'output PDF, inclusi font, proprietà del documento, compressione delle immagini e altro ancora.

## Domande frequenti

### Come posso convertire un documento Word in PDF utilizzando Aspose.Words per Java?

Per convertire un documento Word in PDF, utilizzare il seguente codice:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Sostituire`"input.docx"` con il percorso del tuo documento Word e`"output.pdf"` con il percorso desiderato per il file PDF di output.

### Posso incorporare i font nel PDF generato da Aspose.Words per Java?

 Sì, puoi incorporare i font nel PDF impostando`setEmbedFullFonts` opzione per`true` In`PdfSaveOptions`Ecco un esempio:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Come posso personalizzare le proprietà del documento nel PDF generato?

 È possibile personalizzare le proprietà del documento nel PDF utilizzando`setCustomPropertiesExport` opzione in`PdfSaveOptions`. Per esempio:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Qual è lo scopo della compressione delle immagini in Aspose.Words per Java?

 La compressione delle immagini consente di controllare la qualità e la dimensione delle immagini nel PDF generato. È possibile impostare la modalità di compressione delle immagini utilizzando`setImageCompression` In`PdfSaveOptions`.

### Come posso aggiornare la proprietà "Ultima stampa" nel PDF?

 È possibile aggiornare la proprietà "Ultima stampa" nel PDF impostando`setUpdateLastPrintedProperty` A`true` In`PdfSaveOptions`Ciò rifletterà l'ultima data stampata nei metadati del PDF.

### Come posso migliorare la qualità delle immagini durante la conversione in PDF?

 Per migliorare la qualità dell'immagine, abilitare l'interpolazione dell'immagine impostando`setInterpolateImages` A`true` In`PdfSaveOptions`Ciò produrrà immagini più fluide e di qualità superiore nel PDF.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
