---
"description": "Scopri come esportare i segnalibri di intestazione e piè di pagina da un documento Word in PDF utilizzando Aspose.Words per .NET con la nostra guida dettagliata."
"linktitle": "Esporta intestazione, piè di pagina, segnalibri del documento Word in un documento PDF"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Esporta intestazione, piè di pagina, segnalibri del documento Word in un documento PDF"
"url": "/it/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Esporta intestazione, piè di pagina, segnalibri del documento Word in un documento PDF

## Introduzione

Convertire documenti Word in PDF è un'operazione comune, soprattutto quando si desidera condividere o archiviare documenti mantenendone la formattazione. A volte, questi documenti contengono importanti segnalibri nelle intestazioni e nei piè di pagina. In questo tutorial, illustreremo il processo di esportazione di questi segnalibri da un documento Word a un PDF utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

- Aspose.Words per .NET: è necessario aver installato Aspose.Words per .NET. È possibile scaricarlo da [Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: configura il tuo ambiente di sviluppo. Puoi utilizzare Visual Studio o qualsiasi altro IDE compatibile con .NET.
- Conoscenza di base di C#: è richiesta familiarità con la programmazione C# per seguire gli esempi di codice.

## Importa spazi dei nomi

Per prima cosa, devi importare gli spazi dei nomi necessari nel tuo progetto C#. Aggiungi queste righe all'inizio del file di codice:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Analizziamo il processo in semplici passaggi.

## Passaggio 1: inizializzare il documento

Il primo passo è caricare il documento Word. Ecco come fare:

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

In questo passaggio, devi semplicemente specificare il percorso verso la directory del documento e caricare il documento Word.

## Passaggio 2: configurare le opzioni di salvataggio PDF

Successivamente, è necessario configurare le opzioni di salvataggio del PDF per garantire che i segnalibri nelle intestazioni e nei piè di pagina vengano esportati correttamente.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

Qui stiamo impostando il `PdfSaveOptions`. IL `DefaultBookmarksOutlineLevel` la proprietà imposta il livello di struttura per i segnalibri e `HeaderFooterBookmarksExportMode` La proprietà garantisce che venga esportata solo la prima occorrenza dei segnalibri nelle intestazioni e nei piè di pagina.

## Passaggio 3: salva il documento come PDF

Infine, salva il documento come PDF con le opzioni configurate.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

In questo passaggio, salvi il documento nel percorso specificato con le opzioni che hai configurato.

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi esportare facilmente i segnalibri dalle intestazioni e dai piè di pagina di un documento Word in un PDF utilizzando Aspose.Words per .NET. Questo metodo garantisce che gli strumenti di navigazione più importanti all'interno del documento vengano conservati nel formato PDF, rendendo più facile per i lettori navigare nel documento.

## Domande frequenti

### Posso esportare tutti i segnalibri dal documento Word in PDF?

Sì, puoi. Nel `PdfSaveOptions`, se necessario, puoi modificare le impostazioni per includere tutti i segnalibri.

### Cosa succede se voglio esportare i segnalibri anche dal corpo del documento?

È possibile configurare il `OutlIneOptions` in `PdfSaveOptions` per includere segnalibri dal corpo del documento.

### È possibile personalizzare i livelli dei segnalibri nel PDF?

Assolutamente! Puoi personalizzare il `DefaultBookmarksOutlineLevel` proprietà per impostare diversi livelli di struttura per i segnalibri.

### Come posso gestire i documenti senza segnalibri?

Se il documento non contiene segnalibri, il PDF verrà generato senza alcun contorno. Assicurati che il documento contenga segnalibri se ne hai bisogno nel PDF.

### Posso usare questo metodo per altri tipi di documenti come DOCX o RTF?

Sì, Aspose.Words per .NET supporta vari tipi di documenti, tra cui DOCX, RTF e altri.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}