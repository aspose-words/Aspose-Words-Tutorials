---
date: 2025-12-22
description: Scopri come esportare markdown convertendo documenti Word in Markdown
  con Aspose.Words per Java. Questa guida passo passo copre l'allineamento delle tabelle,
  la gestione delle immagini e molto altro.
linktitle: Saving Documents as Markdown
second_title: Aspose.Words Java Document Processing API
title: Come esportare Markdown con Aspose.Words per Java
url: /it/java/document-loading-and-saving/saving-documents-as-markdown/
weight: 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come esportare Markdown con Aspose.Words per Java

## Introduzione all'esportazione di Markdown in Aspose.Words per Java

In questo tutorial passo‑a‑passo, **imparerai a esportare markdown** dai documenti Word usando Aspose.Words per Java. Markdown è un linguaggio di markup leggero perfetto per la documentazione, i generatori di siti statici e molte piattaforme di pubblicazione. Alla fine di questa guida sarai in grado di **convertire Word in markdown**, personalizzare l'allineamento delle tabelle e **gestire le immagini in markdown** senza sforzo.

## Risposte rapide
- **Qual è la classe principale per salvare come Markdown?** `MarkdownSaveOptions`
- **Le immagini possono essere incorporate automaticamente?** Sì – imposta la cartella delle immagini tramite `setImagesFolder`.
- **Come controllo l'allineamento delle tabelle?** Usa `TableContentAlignment` (LEFT, RIGHT, CENTER, AUTO).
- **Quali sono i requisiti minimi?** JDK 8+ e libreria Aspose.Words per Java.
- **È disponibile una versione di prova?** Sì, scaricala dal sito di Aspose.

## Che cosa significa “come esportare markdown”?
Esportare markdown significa prendere un documento Word a rich‑text (`.docx`) e produrre un file di testo semplice `.md` che conserva intestazioni, tabelle e immagini nella sintassi Markdown.

## Perché usare Aspose.Words per Java per convertire docx con immagini?
Aspose.Words gestisce layout complessi, immagini incorporate e strutture di tabelle senza perdere fedeltà. Inoltre ti offre un controllo granulare sull'output Markdown, come l'allineamento delle tabelle e la gestione della cartella delle immagini.

## Prerequisiti

- Java Development Kit (JDK) installato sul tuo sistema.
- Libreria Aspose.Words per Java. Puoi scaricarla da [qui](https://releases.aspose.com/words/java/).

## Passo 1: Creare un semplice documento Word

Per prima cosa, costruiremo un piccolo documento che contiene una tabella. Questo ci permetterà di dimostrare **la personalizzazione dell'allineamento delle tabelle** più avanti.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table with two cells
builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT);
builder.write("Cell1");

builder.insertCell();
builder.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);
builder.write("Cell2");

// Save the document as Markdown
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
doc.save("output.md", saveOptions);
```

Nello snippet sopra:

1. Creiamo un nuovo `Document`.
2. Utilizziamo `DocumentBuilder` per inserire una tabella a due celle.
3. Applichiamo l'allineamento del paragrafo **a destra** e **centrato** all'interno di ciascuna cella.
4. Salviamo il file come Markdown usando `MarkdownSaveOptions`.

## Passo 2: Personalizzare l'allineamento del contenuto della tabella

Aspose.Words ti consente di decidere come le celle della tabella vengono renderizzate nel Markdown finale. Puoi forzare l'allineamento a sinistra, destra, centro, oppure lasciare che la libreria decida automaticamente in base al primo paragrafo di ogni colonna.

```java
// Set the table content alignment to left
saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
doc.save("left_alignment.md", saveOptions);

// Set the table content alignment to right
saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
doc.save("right_alignment.md", saveOptions);

// Set the table content alignment to center
saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
doc.save("center_alignment.md", saveOptions);

// Set the table content alignment to auto (determined by first paragraph)
saveOptions.setTableContentAlignment(TableContentAlignment.AUTO);
doc.save("auto_alignment.md", saveOptions);
```

Modificando la proprietà `TableContentAlignment` controlli **la personalizzazione dell'allineamento della tabella** per l'output Markdown.

## Passo 3: Gestire le immagini durante l'esportazione in markdown

Quando un documento contiene immagini, vorrai che queste appaiano correttamente nel file `.md` generato. Imposta la cartella in cui Aspose.Words deve salvare le immagini estratte.

```java
// Load a document containing images
Document doc = new Document("document_with_images.docx");

// Set the images folder path
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
saveOptions.setImagesFolder("images_folder/");

// Save the document with images
doc.save("document_with_images.md", saveOptions);
```

Sostituisci `"document_with_images.docx"` con il percorso del tuo file sorgente e `"images_folder/"` con la posizione in cui desideri che le immagini vengano salvate. Il Markdown risultante conterrà collegamenti alle immagini che puntano a questa cartella, permettendoti di **gestire le immagini in markdown** senza problemi.

## Codice sorgente completo per salvare documenti come Markdown in Aspose.Words per Java

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
	// Makes all paragraphs inside the table to be aligned.
	MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();
	{
		saveOptions.setTableContentAlignment(TableContentAlignment.LEFT);
	}
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.LeftTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.RIGHT);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.RightTableContentAlignment.md", saveOptions);
	saveOptions.setTableContentAlignment(TableContentAlignment.CENTER);
	doc.save("Your Directory Path" + "WorkingWithMarkdownSaveOptions.CenterTableContentAlignment.md", saveOptions);
	// The alignment in this case will be taken from the first paragraph in corresponding table column.
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

## Problemi comuni e soluzioni

| Problema | Soluzione |
|----------|-----------|
| Le immagini non compaiono nel file `.md` | Verifica che `setImagesFolder` punti a una directory scrivibile e che la cartella sia referenziata correttamente nel Markdown generato. |
| L'allineamento della tabella sembra errato | Usa `TableContentAlignment.AUTO` per lasciare che Aspose.Words inferisca il miglior allineamento basandosi sul primo paragrafo di ogni colonna. |
| Il file di output è vuoto | Assicurati che l'oggetto `Document` contenga effettivamente del contenuto prima di chiamare `save`. |

## Domande frequenti

**D: Come installo Aspose.Words per Java?**  
R: Aspose.Words per Java può essere installato includendo la libreria nel tuo progetto Java. Puoi scaricare la libreria da [qui](https://releases.aspose.com/words/java/) e seguire le istruzioni di installazione fornite nella documentazione.

**D: Posso convertire documenti Word complessi con tabelle e immagini in Markdown?**  
R: Sì, Aspose.Words per Java supporta la conversione di documenti Word complessi con tabelle, immagini e vari elementi di formattazione in Markdown. Puoi personalizzare l'output Markdown in base alla complessità del tuo documento.

**D: Come posso gestire le immagini nei file Markdown?**  
R: Imposta il percorso della cartella delle immagini usando il metodo `setImagesFolder` in `MarkdownSaveOptions`. Assicurati che i file immagine siano salvati nella cartella specificata; Aspose.Words genererà i corretti collegamenti Markdown alle immagini.

**D: È disponibile una versione di prova di Aspose.Words per Java?**  
R: Sì, puoi ottenere una versione di prova di Aspose.Words per Java dal sito Aspose. La versione di prova ti consente di valutare le funzionalità della libreria prima di acquistare una licenza.

**D: Dove posso trovare più esempi e documentazione?**  
R: Per ulteriori esempi, documentazione e informazioni dettagliate su Aspose.Words per Java, visita la [documentazione](https://reference.aspose.com/words/java/).

---

**Ultimo aggiornamento:** 2025-12-22  
**Testato con:** Aspose.Words per Java 24.12 (ultima versione al momento della stesura)  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}