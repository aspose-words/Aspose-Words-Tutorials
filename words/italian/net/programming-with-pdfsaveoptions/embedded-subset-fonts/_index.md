---
"description": "Riduci le dimensioni dei file PDF incorporando solo i sottoinsiemi di font necessari utilizzando Aspose.Words per .NET. Segui la nostra guida passo passo per ottimizzare i tuoi PDF in modo efficiente."
"linktitle": "Incorpora i font del sottoinsieme nel documento PDF"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Incorpora i font del sottoinsieme nel documento PDF"
"url": "/it/net/programming-with-pdfsaveoptions/embedded-subset-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Incorpora i font del sottoinsieme nel documento PDF

## Introduzione

Avete mai notato come alcuni file PDF siano molto più grandi di altri, anche quando contengono contenuti simili? Il colpevole spesso risiede nei font. Incorporare i font in un PDF garantisce che il file appaia identico su qualsiasi dispositivo, ma può anche far aumentare le dimensioni del file. Fortunatamente, Aspose.Words per .NET offre una pratica funzionalità per incorporare solo i sottoinsiemi di font necessari, mantenendo i PDF snelli ed efficienti. Questo tutorial vi guiderà passo dopo passo in questo processo.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

- Aspose.Words per .NET: puoi scaricarlo [Qui](https://releases.aspose.com/words/net/).
- Ambiente .NET: assicurati di disporre di un ambiente di sviluppo .NET funzionante.
- Conoscenza di base di C#: la familiarità con la programmazione C# ti aiuterà a seguire il corso.

## Importa spazi dei nomi

Per utilizzare Aspose.Words per .NET, è necessario importare gli spazi dei nomi necessari nel progetto. Aggiungeteli all'inizio del file C#:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: caricare il documento

Per prima cosa, dobbiamo caricare il documento Word che vogliamo convertire in PDF. Questo si fa usando `Document` classe fornita da Aspose.Words.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Questo frammento di codice carica il documento che si trova in `dataDir`Assicurati di sostituire `"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo del tuo documento.

## Passaggio 2: configurare le opzioni di salvataggio PDF

Successivamente, configuriamo il `PdfSaveOptions` per garantire che vengano incorporati solo i sottoinsiemi di font necessari. Impostando `EmbedFullFonts` A `false`, diciamo ad Aspose.Words di incorporare solo i glifi utilizzati nel documento.

```csharp
// Il PDF di output conterrà sottoinsiemi dei font presenti nel documento.
// Nei font PDF sono inclusi solo i glifi utilizzati nel documento.
PdfSaveOptions saveOptions = new PdfSaveOptions { EmbedFullFonts = false };
```

Questo piccolo ma fondamentale passaggio aiuta a ridurre significativamente le dimensioni del file PDF.

## Passaggio 3: salva il documento come PDF

Infine, salviamo il documento come PDF utilizzando il `Save` metodo, applicando il configurato `PdfSaveOptions`.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf", saveOptions);
```

Questo codice genererà un file PDF con il nome `WorkingWithPdfSaveOptions.EmbedSubsetFonts.pdf` nella directory specificata, con incorporati solo i sottoinsiemi di font necessari.

## Conclusione

Ed ecco fatto! Seguendo questi semplici passaggi, puoi ridurre efficacemente le dimensioni dei tuoi file PDF incorporando solo i sottoinsiemi di font necessari utilizzando Aspose.Words per .NET. Questo non solo consente di risparmiare spazio di archiviazione, ma garantisce anche tempi di caricamento più rapidi e prestazioni migliori, soprattutto per i documenti con un numero elevato di font.

## Domande frequenti

### Perché dovrei incorporare solo sottoinsiemi di font in un PDF?
Incorporando solo i sottoinsiemi di font necessari è possibile ridurre significativamente le dimensioni del file PDF senza compromettere l'aspetto e la leggibilità del documento.

### Posso tornare a incorporare tutti i font, se necessario?
Sì, puoi. Imposta semplicemente il `EmbedFullFonts` proprietà a `true` nel `PdfSaveOptions`.

### Aspose.Words per .NET supporta altre funzionalità di ottimizzazione PDF?
Assolutamente sì! Aspose.Words per .NET offre una gamma di opzioni per ottimizzare i PDF, tra cui la compressione delle immagini e la rimozione degli oggetti inutilizzati.

### Quali tipi di font possono essere incorporati in sottoinsiemi utilizzando Aspose.Words per .NET?
Aspose.Words per .NET supporta l'incorporamento di sottoinsiemi per tutti i font TrueType utilizzati nel documento.

### Come posso verificare quali font sono incorporati nel mio PDF?
Puoi aprire il PDF in Adobe Acrobat Reader e controllare le proprietà nella scheda Caratteri per vedere i caratteri incorporati.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}