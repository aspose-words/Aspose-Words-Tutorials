---
title: Esporta i segnalibri dell'intestazione e del piè di pagina del documento Word in un documento PDF
linktitle: Esporta i segnalibri dell'intestazione e del piè di pagina del documento Word in un documento PDF
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come esportare i segnalibri di intestazione e piè di pagina da un documento Word in PDF utilizzando Aspose.Words per .NET con la nostra guida dettagliata.
weight: 10
url: /it/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Esporta i segnalibri dell'intestazione e del piè di pagina del documento Word in un documento PDF

## Introduzione

Convertire documenti Word in PDF è un'attività comune, soprattutto quando si desidera condividere o archiviare documenti preservandone la formattazione. A volte, questi documenti contengono importanti segnalibri nelle intestazioni e nei piè di pagina. In questo tutorial, illustreremo il processo di esportazione di questi segnalibri da un documento Word a un PDF utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

- Aspose.Words per .NET: devi avere Aspose.Words per .NET installato. Puoi scaricarlo da[Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: imposta il tuo ambiente di sviluppo. Puoi usare Visual Studio o qualsiasi altro IDE compatibile con .NET.
- Conoscenza di base di C#: è richiesta familiarità con la programmazione in C# per seguire gli esempi di codice.

## Importazione degli spazi dei nomi

Per prima cosa, devi importare i namespace necessari nel tuo progetto C#. Aggiungi queste righe in cima al tuo file di codice:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Scomponiamo il processo in semplici passaggi.

## Passaggio 1: inizializzare il documento

Il primo passo è caricare il tuo documento Word. Ecco come puoi farlo:

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

In questo passaggio, devi semplicemente specificare il percorso della directory del documento e caricare il documento Word.

## Passaggio 2: configurare le opzioni di salvataggio PDF

Successivamente, è necessario configurare le opzioni di salvataggio del PDF per garantire che i segnalibri nelle intestazioni e nei piè di pagina vengano esportati correttamente.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Qui stiamo impostando il`PdfSaveOptions` . IL`DefaultBookmarksOutlineLevel` la proprietà imposta il livello di struttura per i segnalibri e il`HeaderFooterBookmarksExportMode` La proprietà garantisce che venga esportata solo la prima occorrenza dei segnalibri nelle intestazioni e nei piè di pagina.

## Passaggio 3: Salva il documento come PDF

Infine, salva il documento come PDF con le opzioni configurate.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

In questo passaggio, salvi il documento nel percorso specificato con le opzioni che hai configurato.

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi facilmente esportare i segnalibri dalle intestazioni e dai piè di pagina di un documento Word in un PDF usando Aspose.Words per .NET. Questo metodo assicura che importanti aiuti alla navigazione all'interno del documento siano conservati nel formato PDF, rendendo più facile per i lettori navigare nel documento.

## Domande frequenti

### Posso esportare tutti i segnalibri dal documento Word in PDF?

 Sì, puoi. Nel`PdfSaveOptions`, se necessario, puoi modificare le impostazioni per includere tutti i segnalibri.

### Cosa succede se voglio esportare i segnalibri anche dal corpo del documento?

 Puoi configurare il`OutlineOptions` In`PdfSaveOptions` per includere segnalibri dal corpo del documento.

### È possibile personalizzare i livelli dei segnalibri nel PDF?

 Assolutamente! Puoi personalizzare il`DefaultBookmarksOutlineLevel` proprietà per impostare diversi livelli di struttura per i segnalibri.

### Come faccio a gestire i documenti senza segnalibri?

Se il tuo documento non ha segnalibri, il PDF verrà generato senza alcun contorno di segnalibri. Assicurati che il tuo documento contenga segnalibri se ne hai bisogno nel PDF.

### Posso usare questo metodo per altri tipi di documenti come DOCX o RTF?

Sì, Aspose.Words per .NET supporta vari tipi di documenti, tra cui DOCX, RTF e altri.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
