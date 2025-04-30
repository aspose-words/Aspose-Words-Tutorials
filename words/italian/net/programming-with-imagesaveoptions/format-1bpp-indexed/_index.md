---
"description": "Scopri come convertire un documento Word in un'immagine indicizzata 1Bpp utilizzando Aspose.Words per .NET. Segui la nostra guida passo passo per una conversione semplice."
"linktitle": "Formato 1Bpp indicizzato"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Formato 1Bpp indicizzato"
"url": "/it/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formato 1Bpp indicizzato

## Introduzione

Vi siete mai chiesti come salvare un documento Word come immagine in bianco e nero con poche righe di codice? Beh, siete fortunati! Oggi sveleremo un piccolo trucco che vi permetterà di convertire i vostri documenti in immagini indicizzate a 1 bit per pagina (Bpp) utilizzando Aspose.Words per .NET. Questo formato è perfetto per alcuni tipi di archiviazione digitale, stampa o quando è necessario risparmiare spazio. Analizzeremo ogni passaggio per renderlo semplicissimo. Pronti a iniziare? Cominciamo!

## Prerequisiti

Prima di sporcarci le mani, ecco alcune cose che devi mettere in atto:

- Aspose.Words per .NET: assicurati di aver installato la libreria. Puoi [scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo .NET: Visual Studio è una buona opzione, ma puoi utilizzare qualsiasi ambiente con cui ti trovi a tuo agio.
- Conoscenza di base di C#: non preoccuparti, lasceremo perdere la difficoltà, ma un po' di familiarità con C# sarà utile.
- Un documento Word: tieni pronto un documento Word di esempio da convertire.

## Importa spazi dei nomi

Per prima cosa, dobbiamo importare i namespace necessari. Questo è fondamentale perché ci permette di accedere alle classi e ai metodi di cui abbiamo bisogno da Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: imposta la directory dei documenti

Dovrai specificare il percorso della directory del documento. È qui che verrà salvato il documento Word e l'immagine convertita.

```csharp
// Percorso alla directory dei documenti
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: caricare il documento Word

Ora carichiamo il documento Word in un Aspose.Words `Document` oggetto. Questo oggetto rappresenta il tuo file Word e ti consente di manipolarlo.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 3: configurare le opzioni di salvataggio dell'immagine

Successivamente, dobbiamo impostare il `ImageSaveOptions`È qui che avviene la magia. Lo configureremo per salvare l'immagine in formato PNG con modalità colore indicizzata a 1 Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: specifica che vogliamo salvare il documento come immagine PNG.
- PageSet(1): indica che stiamo convertendo solo la prima pagina.
- ImageColorMode.BlackAndWhite: imposta l'immagine in bianco e nero.
- ImagePixelFormat.Format1bppIndexed: imposta il formato dell'immagine su indicizzato a 1 Bpp.

## Passaggio 4: salvare il documento come immagine

Infine, salviamo il documento come immagine utilizzando il `Save` metodo del `Document` oggetto.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Conclusione

Ed ecco fatto! Con poche righe di codice, hai trasformato il tuo documento Word in un'immagine indicizzata a 1 bit per pagina utilizzando Aspose.Words per .NET. Questo metodo è incredibilmente utile per creare immagini ad alto contrasto e a basso consumo di spazio dai tuoi documenti. Ora puoi integrarlo facilmente nei tuoi progetti e flussi di lavoro. Buona programmazione!

## Domande frequenti

### Cos'è un'immagine indicizzata 1Bpp?
Un'immagine indicizzata a 1 Bpp (1 bit per pixel) è un formato di immagine in bianco e nero in cui ogni pixel è rappresentato da un singolo bit, 0 o 1. Questo formato è molto efficiente in termini di spazio.

### Posso convertire più pagine di un documento Word contemporaneamente?
Sì, puoi. Modifica il `PageSet` proprietà nella `ImageSaveOptions` per includere più pagine o l'intero documento.

### Ho bisogno di una licenza per utilizzare Aspose.Words per .NET?
Sì, Aspose.Words per .NET richiede una licenza per la piena funzionalità. Puoi ottenere una [licenza temporanea qui](https://purchase.aspose.com/temporary-license/).

### In quali altri formati immagine posso convertire il mio documento Word?
Aspose.Words supporta vari formati di immagine, tra cui JPEG, BMP e TIFF. Basta cambiare il `SaveFormat` nel `ImageSaveOptions`.

### Dove posso trovare ulteriore documentazione su Aspose.Words per .NET?
Puoi trovare la documentazione dettagliata su [Pagina di documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}