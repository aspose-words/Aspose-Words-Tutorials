---
title: Formato 1Bpp indicizzato
linktitle: Formato 1Bpp indicizzato
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come convertire un documento Word in un'immagine indicizzata 1Bpp usando Aspose.Words per .NET. Segui la nostra guida passo passo per una conversione semplice.
weight: 10
url: /it/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formato 1Bpp indicizzato

## Introduzione

Ti sei mai chiesto come salvare un documento Word come immagine in bianco e nero con solo poche righe di codice? Bene, sei fortunato! Oggi ci immergiamo in un piccolo trucco carino che usa Aspose.Words per .NET che ti consente di convertire i tuoi documenti in immagini indicizzate 1Bpp. Questo formato è perfetto per alcuni tipi di archiviazione digitale, stampa o quando hai bisogno di risparmiare spazio. Analizzeremo ogni passaggio per renderlo il più semplice possibile. Pronti a iniziare? Immergiamoci!

## Prerequisiti

Prima di sporcarci le mani, ecco alcune cose che devi mettere in atto:

-  Aspose.Words per .NET: assicurati di avere la libreria installata. Puoi[scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo .NET: Visual Studio è una buona opzione, ma puoi utilizzare qualsiasi ambiente con cui ti trovi a tuo agio.
- Conoscenza di base di C#: non preoccuparti, lasceremo perdere la semplicità, ma un po' di familiarità con C# ti sarà utile.
- Un documento Word: tieni pronto un documento Word di esempio da convertire.

## Importazione degli spazi dei nomi

Innanzitutto, dobbiamo importare i namespace necessari. Questo è fondamentale perché ci consente di accedere alle classi e ai metodi di cui abbiamo bisogno da Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: imposta la directory dei documenti

Dovrai specificare il percorso della directory del tuo documento. È qui che è archiviato il tuo documento Word e dove verrà salvata l'immagine convertita.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: caricare il documento Word

 Ora carichiamo il documento Word in Aspose.Words`Document` oggetto. Questo oggetto rappresenta il tuo file Word e ti consente di manipolarlo.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 3: configurare le opzioni di salvataggio dell'immagine

 Successivamente, dobbiamo impostare il`ImageSaveOptions`È qui che avviene la magia. Lo configureremo per salvare l'immagine in formato PNG con modalità colore indicizzata 1Bpp.

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

 Infine, salviamo il documento come immagine utilizzando il`Save` metodo del`Document` oggetto.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Conclusione

Ed ecco fatto! Con solo poche righe di codice, hai trasformato il tuo documento Word in un'immagine indicizzata 1Bpp usando Aspose.Words per .NET. Questo metodo è incredibilmente utile per creare immagini ad alto contrasto e a basso consumo di spazio dai tuoi documenti. Ora, puoi facilmente integrarlo nei tuoi progetti e flussi di lavoro. Buona codifica!

## Domande frequenti

### Cos'è un'immagine indicizzata 1Bpp?
Un'immagine indicizzata a 1 Bpp (1 bit per pixel) è un formato di immagine in bianco e nero in cui ogni pixel è rappresentato da un singolo bit, 0 o 1. Questo formato è altamente efficiente in termini di spazio.

### Posso convertire più pagine di un documento Word contemporaneamente?
 Sì, puoi. Modificare il`PageSet` proprietà nella`ImageSaveOptions` per includere più pagine o l'intero documento.

### Ho bisogno di una licenza per utilizzare Aspose.Words per .NET?
 Sì, Aspose.Words per .NET richiede una licenza per la piena funzionalità. Puoi ottenere una[licenza temporanea qui](https://purchase.aspose.com/temporary-license/).

### In quali altri formati immagine posso convertire il mio documento Word?
 Aspose.Words supporta vari formati di immagine, tra cui JPEG, BMP e TIFF. Basta cambiare il`SaveFormat` nel`ImageSaveOptions`.

### Dove posso trovare ulteriore documentazione su Aspose.Words per .NET?
 Puoi trovare la documentazione dettagliata su[Pagina di documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
