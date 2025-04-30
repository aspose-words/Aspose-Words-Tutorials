---
"description": "Converti pagine specifiche di documenti Word in JPEG con impostazioni personalizzate utilizzando Aspose.Words per .NET. Scopri come regolare luminosità, contrasto e risoluzione passo dopo passo."
"linktitle": "Ottieni intervallo di pagine JPEG"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Ottieni intervallo di pagine JPEG"
"url": "/it/net/programming-with-imagesaveoptions/get-jpeg-page-range/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ottieni intervallo di pagine JPEG

## Introduzione

Convertire documenti Word in immagini può essere incredibilmente utile, sia che si tratti di creare miniature, visualizzare in anteprima documenti online o condividere contenuti in un formato più accessibile. Con Aspose.Words per .NET, puoi convertire facilmente pagine specifiche dei tuoi documenti Word in formato JPEG, personalizzando al contempo diverse impostazioni come luminosità, contrasto e risoluzione. Scopriamo insieme come farlo passo dopo passo!

## Prerequisiti

Prima di iniziare, ti serviranno alcune cose:

- Aspose.Words per .NET: assicurati di aver installato Aspose.Words per .NET. Puoi [scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: ambiente di sviluppo AC# come Visual Studio.
- Documento di esempio: un documento Word con cui lavorare. Puoi utilizzare qualsiasi file .docx per questo tutorial.
- Conoscenza di base del linguaggio C#: familiarità con la programmazione C#.

Una volta che avrete tutto pronto, cominciamo!

## Importa spazi dei nomi

Per utilizzare Aspose.Words per .NET, è necessario importare gli spazi dei nomi necessari all'inizio del codice. Questo garantisce l'accesso a tutte le classi e i metodi necessari per la manipolazione dei documenti.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: carica il documento

Per prima cosa, dobbiamo caricare il documento Word che vogliamo convertire. Supponiamo che il nostro documento si chiami `Rendering.docx` e si trova nella directory specificata dal segnaposto `YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Questo codice inizializza il percorso verso il tuo documento e lo carica in un Aspose.Words `Document` oggetto.

## Passaggio 2: imposta ImageSaveOptions

Successivamente, imposteremo il `ImageSaveOptions` per specificare come vogliamo che venga generato il nostro JPEG. Questo include l'impostazione dell'intervallo di pagine, della luminosità dell'immagine, del contrasto e della risoluzione.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // Converti solo la prima pagina
options.ImageBrightness = 0.3f;   // Imposta la luminosità
options.ImageContrast = 0.7f;     // Imposta contrasto
options.HorizontalResolution = 72f; // Imposta risoluzione
```

## Passaggio 3: salvare il documento come JPEG

Infine, salviamo il documento come file JPEG utilizzando le impostazioni che abbiamo definito.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

Questo codice salva la prima pagina di `Rendering.docx` come immagine JPEG con le impostazioni di luminosità, contrasto e risoluzione specificate.

## Conclusione

Ed ecco fatto! Hai convertito con successo una pagina specifica di un documento Word in un'immagine JPEG con impostazioni personalizzate utilizzando Aspose.Words per .NET. Questo processo può essere personalizzato per soddisfare diverse esigenze, che si tratti di preparare immagini per un sito web, creare anteprime di documenti o altro ancora.

## Domande frequenti

### Posso convertire più pagine contemporaneamente?
Sì, puoi specificare un intervallo di pagine utilizzando `PageSet` proprietà in `ImageSaveOptions`.

### Come faccio a regolare la qualità dell'immagine?
È possibile regolare la qualità del JPEG utilizzando `JpegQuality` proprietà in `ImageSaveOptions`.

### Posso salvare le immagini in altri formati?
Sì, Aspose.Words supporta vari formati di immagine come PNG, BMP e TIFF. Modifica il `SaveFormat` In `ImageSaveOptions` di conseguenza.

### C'è un modo per visualizzare in anteprima l'immagine prima di salvarla?
Sarà necessario implementare separatamente un meccanismo di anteprima, poiché Aspose.Words non fornisce una funzionalità di anteprima integrata.

### Come posso ottenere una licenza temporanea per Aspose.Words?
Puoi richiedere un [licenza temporanea qui](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}