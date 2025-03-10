---
title: Salvataggio di documenti come Markdown in Aspose.Words per Java
linktitle: Salvataggio dei documenti come Markdown
second_title: API di elaborazione dei documenti Java Aspose.Words
description: Scopri come convertire i documenti Word in Markdown con Aspose.Words per Java. Questa guida passo passo riguarda l'allineamento delle tabelle, la gestione delle immagini e altro ancora.
weight: 18
url: /it/java/document-loading-and-saving/saving-documents-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salvataggio di documenti come Markdown in Aspose.Words per Java


## Introduzione al salvataggio di documenti come Markdown in Aspose.Words per Java

In questa guida passo passo, mostreremo come salvare documenti come Markdown usando Aspose.Words per Java. Markdown è un linguaggio di markup leggero che viene comunemente usato per formattare documenti di testo. Con Aspose.Words per Java, puoi convertire facilmente i tuoi documenti Word in formato Markdown. Tratteremo diversi aspetti del salvataggio di file Markdown, tra cui l'allineamento del contenuto della tabella e la gestione delle immagini.

## Prerequisiti

Prima di iniziare, assicurati di disporre dei seguenti prerequisiti:

- Java Development Kit (JDK) installato sul sistema.
-  Aspose.Words per la libreria Java. Puoi scaricarla da[Qui](https://releases.aspose.com/words/java/).

## Passaggio 1: creazione di un documento Word

Iniziamo creando un documento Word che poi convertiremo in formato Markdown. Puoi personalizzare questo documento in base alle tue esigenze.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Inserisci una tabella con due celle
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Salva il documento come Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

 In questo esempio, creiamo una semplice tabella con due celle e impostiamo l'allineamento dei paragrafi all'interno di queste celle. Quindi, salviamo il documento come Markdown utilizzando`MarkdownSaveOptions`.

## Passaggio 2: personalizzare l'allineamento del contenuto della tabella

Aspose.Words per Java consente di personalizzare l'allineamento del contenuto della tabella quando si salva come Markdown. È possibile allineare il contenuto della tabella a sinistra, a destra, al centro o lasciare che venga determinato automaticamente in base al primo paragrafo in ogni colonna della tabella.

Ecco come personalizzare l'allineamento del contenuto della tabella:

```java
// Imposta l'allineamento del contenuto della tabella a sinistra
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Imposta l'allineamento del contenuto della tabella a destra
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Imposta l'allineamento del contenuto della tabella al centro
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

//Imposta l'allineamento del contenuto della tabella su automatico (determinato dal primo paragrafo)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

 Cambiando il`TableContentAlignment` proprietà, è possibile controllare il modo in cui il contenuto all'interno delle tabelle viene allineato durante la conversione in Markdown.

## Fase 3: Gestione delle immagini

 Per includere immagini nel tuo documento Markdown, devi specificare la cartella in cui si trovano le immagini. Aspose.Words per Java ti consente di impostare la cartella delle immagini in`MarkdownSaveOptions`.

Ecco come impostare la cartella delle immagini e salvare il documento con le immagini:

```java
// Carica un documento contenente immagini
Document doc = new Document("document_with_images.docx");

// Imposta il percorso della cartella delle immagini
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Salvare il documento con le immagini
doc.save("document_with_images.md", saveOptions);
```

 Assicurati di sostituire`"document_with_images.docx"` con il percorso al documento Word contenente immagini e`"images_folder/"` con il percorso effettivo della cartella in cui sono archiviate le immagini.

## Codice sorgente completo per salvare i documenti come Markdown in Aspose.Words per Java

```java
public void autoTableContentAlignment() throws Exception
{
	Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
	builder.write("Cell1");
	builder.insertCell();
	builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
	builder.write("Cell2");
	// Fa sì che tutti i paragrafi all'interno della tabella siano allineati.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// In questo caso l'allineamento verrà preso dal primo paragrafo nella colonna corrispondente della tabella.
	saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.AutoTableContentAlignment.md", saveOptions);
}
@Test
public void setImagesFolder() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Image bullet points.docx");
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions(); { saveOptions.setImagesFolder("Your Directory Path" + "Images"); }
	try(ByteArrayOutputStream stream = new ByteArrayOutputStream())
	{
		doc.save(stream, saveOptions);
	}
}
```

## Conclusione

In questa guida, abbiamo esplorato come salvare documenti come Markdown usando Aspose.Words per Java. Abbiamo trattato la creazione di un documento Word, la personalizzazione dell'allineamento del contenuto della tabella e la gestione delle immagini nei file Markdown. Ora puoi convertire in modo efficiente i tuoi documenti Word in formato Markdown, rendendoli adatti a varie piattaforme di pubblicazione e necessità di documentazione.

## Domande frequenti

### Come faccio a installare Aspose.Words per Java?

 Aspose.Words per Java può essere installato includendo la libreria nel tuo progetto Java. Puoi scaricare la libreria da[Qui](https://releases.aspose.com/words/java/) e seguire le istruzioni di installazione fornite nella documentazione.

### Posso convertire documenti Word complessi con tabelle e immagini in Markdown?

Sì, Aspose.Words per Java supporta la conversione di documenti Word complessi con tabelle, immagini e vari elementi di formattazione in Markdown. Puoi personalizzare l'output Markdown in base alla complessità del tuo documento.

### Come posso gestire le immagini nei file Markdown?

 Per includere immagini nei file Markdown, impostare il percorso della cartella delle immagini utilizzando`setImagesFolder`metodo in`MarkdownSaveOptions`. Assicurarsi che i file immagine siano archiviati nella cartella specificata e Aspose.Words per Java gestirà di conseguenza i riferimenti alle immagini.

### È disponibile una versione di prova di Aspose.Words per Java?

Sì, puoi ottenere una versione di prova di Aspose.Words per Java dal sito web di Aspose. La versione di prova ti consente di valutare le capacità della libreria prima di acquistare una licenza.

### Dove posso trovare altri esempi e documentazione?

 Per ulteriori esempi, documentazione e informazioni dettagliate su Aspose.Words per Java, visitare il sito[documentazione](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
