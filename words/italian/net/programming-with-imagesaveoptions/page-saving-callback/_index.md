---
title: Richiamo di salvataggio pagina
linktitle: Richiamo di salvataggio pagina
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come salvare ogni pagina di un documento Word come un'immagine PNG separata utilizzando Aspose.Words per .NET con la nostra guida dettagliata e passo dopo passo.
weight: 10
url: /it/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Richiamo di salvataggio pagina

## Introduzione

Ciao! Hai mai sentito la necessità di salvare ogni pagina di un documento Word come immagini separate? Forse vuoi suddividere un report di grandi dimensioni in elementi visivi facilmente digeribili o forse hai bisogno di creare miniature per un'anteprima. Qualunque sia il motivo, usare Aspose.Words per .NET rende questo compito un gioco da ragazzi. In questa guida, ti guideremo attraverso il processo di impostazione di un callback di salvataggio delle pagine per salvare ogni pagina di un documento come un'immagine PNG individuale. Cominciamo subito!

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

1.  Aspose.Words per .NET: se non lo hai già fatto, scaricalo e installalo da[Qui](https://releases.aspose.com/words/net/).
2. Visual Studio: dovrebbe funzionare qualsiasi versione, ma per questa guida utilizzerò Visual Studio 2019.
3. Conoscenza di base di C#: per seguire il corso è necessaria una conoscenza di base di C#.

## Importazione degli spazi dei nomi

Per prima cosa, dobbiamo importare i namespace necessari. Questo ci aiuta ad accedere alle classi e ai metodi richiesti senza dover digitare ogni volta il namespace completo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Passaggio 1: imposta la directory dei documenti

Bene, iniziamo definendo il percorso per la directory del tuo documento. È qui che si trova il tuo documento Word di input e dove verranno salvate le immagini di output.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Passaggio 2: carica il documento

Successivamente, caricheremo il documento che vuoi elaborare. Assicurati che il tuo documento ("Rendering.docx") sia nella directory specificata.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 3: configurare le opzioni di salvataggio dell'immagine

Dobbiamo configurare le opzioni per salvare le immagini. In questo caso, stiamo salvando le pagine come file PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Qui,`PageSet` specifica l'intervallo di pagine da salvare e`PageSavingCallback` punta alla nostra classe di callback personalizzata.

## Passaggio 4: implementare il callback di salvataggio della pagina

Ora implementiamo la classe di callback che gestisce il modo in cui viene salvata ogni pagina.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Questa classe implementa il`IPageSavingCallback` interfaccia e all'interno del`PageSaving` metodo, definiamo il modello di denominazione per ogni pagina salvata.

## Passaggio 5: Salvare il documento come immagini

Infine, salviamo il documento utilizzando le opzioni configurate.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Conclusione

Ed ecco fatto! Hai impostato con successo un callback di salvataggio pagina per salvare ogni pagina di un documento Word come un'immagine PNG separata usando Aspose.Words per .NET. Questa tecnica è incredibilmente utile per varie applicazioni, dalla creazione di anteprime di pagina alla generazione di singole immagini di pagina per i report. 

Buona programmazione!

## Domande frequenti

### Posso salvare le pagine in formati diversi dal PNG?  
 Sì, puoi salvare le pagine Indiversi formati come JPEG, BMP e TIFF modificando il`SaveFormat` in `ImageSaveOptions`.

### Cosa succede se voglio salvare solo pagine specifiche?  
 È possibile specificare le pagine che si desidera salvare regolando il`PageSet` parametro in`ImageSaveOptions`.

### È possibile personalizzare la qualità dell'immagine?  
 Assolutamente! Puoi impostare proprietà come`ImageSaveOptions.JpegQuality` per controllare la qualità delle immagini in uscita.

### Come posso gestire in modo efficiente documenti di grandi dimensioni?  
Per documenti di grandi dimensioni, si consiglia di elaborare le pagine in batch per gestire in modo efficace l'utilizzo della memoria.

### Dove posso trovare maggiori informazioni su Aspose.Words per .NET?  
 Dai un'occhiata al[documentazione](https://reference.aspose.com/words/net/) per guide ed esempi completi.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
