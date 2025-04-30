---
"description": "Guida passo passo per ridurre le dimensioni del PDF ridimensionando i font WMF alle dimensioni del metafile durante la conversione in PDF con Aspose.Words per .NET."
"linktitle": "Riduci le dimensioni del PDF con Scala i caratteri WMF alle dimensioni del Metafile"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Riduci le dimensioni del PDF con Scala i caratteri WMF alle dimensioni del Metafile"
"url": "/it/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Riduci le dimensioni del PDF con Scala i caratteri WMF alle dimensioni del Metafile

## Introduzione

Quando si lavora con file PDF, in particolare quelli generati da documenti Word contenenti grafica WMF (Windows Metafile), la gestione delle dimensioni può diventare un aspetto cruciale della gestione dei documenti. Un modo per controllare le dimensioni del PDF è regolare il rendering dei font WMF all'interno del documento. In questo tutorial, esploreremo come ridurre le dimensioni del PDF ridimensionando i font WMF alle dimensioni del metafile utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di procedere, assicurati di avere quanto segue:

1. Aspose.Words per .NET: assicurati di aver installato la libreria Aspose.Words. In caso contrario, puoi [scaricalo qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: questo tutorial presuppone che tu abbia configurato un ambiente di sviluppo .NET (come Visual Studio) in cui puoi scrivere ed eseguire codice C#.
3. Nozioni di base sulla programmazione .NET: sarà utile avere familiarità con i concetti base della programmazione .NET e con la sintassi C#.
4. Documento Word con grafica WMF: avrai bisogno di un documento Word contenente grafica WMF. Puoi usare il tuo documento o crearne uno per testare.

## Importa spazi dei nomi

Per prima cosa, devi importare gli spazi dei nomi necessari nel tuo progetto C#. Questo ti darà accesso alle classi e ai metodi necessari per lavorare con Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: caricare il documento Word

Per iniziare, caricare il documento Word contenente la grafica WMF. Questo viene fatto utilizzando `Document` classe da Aspose.Words.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Carica il documento
Document doc = new Document(dataDir + "WMF with text.docx");
```

Qui, `dataDir` è un segnaposto per il percorso della directory dei documenti. Creiamo un'istanza di `Document` classe passando il percorso del file Word. Questo carica il documento in memoria, pronto per ulteriori elaborazioni.

## Passaggio 2: configurare le opzioni di rendering dei metafile

Successivamente, è necessario configurare le opzioni di rendering dei metafile. In particolare, impostare `ScaleWmfFontsToMetafileSize` proprietà a `false`. Controlla se i font WMF vengono ridimensionati in base alle dimensioni del metafile.

```csharp
// Crea una nuova istanza di MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

IL `MetafileRenderingOptions` La classe fornisce opzioni per il rendering dei metafile (come WMF). Impostando `ScaleWmfFontsToMetafileSize` A `false`, stai indicando ad Aspose.Words di non ridimensionare i font in base alle dimensioni del metafile, il che può aiutare a ridurre le dimensioni complessive del PDF.

## Passaggio 3: imposta le opzioni di salvataggio PDF

Ora, configura le opzioni di salvataggio del PDF per utilizzare le opzioni di rendering dei metafile appena impostate. Questo indica ad Aspose.Words come gestire i metafile quando si salva il documento in formato PDF.

```csharp
// Crea una nuova istanza di PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

IL `PdfSaveOptions` La classe consente di specificare varie impostazioni per il salvataggio del documento in formato PDF. Assegnando le impostazioni precedentemente configurate `MetafileRenderingOptions` al `MetafileRenderingOptions` proprietà di `PdfSaveOptions`, ti assicuri che il documento venga salvato in base alle impostazioni di rendering dei metafile desiderate.

## Passaggio 4: salva il documento come PDF

Infine, salva il documento Word in formato PDF utilizzando le opzioni di salvataggio configurate. In questo modo, tutte le impostazioni, comprese le opzioni di rendering dei metafile, verranno applicate al PDF di output.


```csharp
// Salva il documento come PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

In questo passaggio, il `Save` metodo del `Document` La classe viene utilizzata per esportare il documento in un file PDF. Viene specificato il percorso in cui verrà salvato il PDF, insieme al `PdfSaveOptions` che includono le impostazioni di rendering dei metafile.

## Conclusione

Ridimensionando i font WMF alle dimensioni di un metafile, è possibile ridurre significativamente le dimensioni dei file PDF generati da documenti Word. Questa tecnica aiuta a ottimizzare l'archiviazione e la distribuzione dei documenti senza compromettere la qualità del contenuto visivo. Seguendo i passaggi descritti sopra, i file PDF saranno più gestibili ed efficienti in termini di dimensioni.

## Domande frequenti

### Che cos'è WMF e perché è importante per le dimensioni del PDF?

WMF (Windows Metafile) è un formato grafico utilizzato in Microsoft Windows. Può contenere sia dati vettoriali che bitmap. Poiché i dati vettoriali possono essere ridimensionati e manipolati, è importante gestirli correttamente per evitare file PDF inutilmente grandi.

### In che modo il ridimensionamento dei font WMF in base alle dimensioni del metafile influisce sul PDF?

Ridimensionare i font WMF in base alle dimensioni del metafile può aiutare a ridurre le dimensioni complessive del PDF, evitando il rendering dei font ad alta risoluzione che potrebbe aumentare le dimensioni del file.

### Posso usare altri formati metafile con Aspose.Words?

Sì, Aspose.Words supporta vari formati di metafile, tra cui EMF (Enhanced Metafile) oltre a WMF.

### Questa tecnica è applicabile a tutti i tipi di documenti Word?

Sì, questa tecnica può essere applicata a qualsiasi documento Word che contenga grafica WMF, contribuendo a ottimizzare le dimensioni del PDF generato.

### Dove posso trovare maggiori informazioni su Aspose.Words?

Puoi esplorare di più su Aspose.Words in [Documentazione di Aspose.Words](https://reference.aspose.com/words/net/)Per download, prove e supporto, visita il sito [Pagina di download di Aspose.Words](https://releases.aspose.com/words/net/), [Acquista Aspose.Words](https://purchase.aspose.com/buy), [Prova gratuita](https://releases.aspose.com/), [Licenza temporanea](https://purchase.aspose.com/temporary-license/), E [Supporto](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}