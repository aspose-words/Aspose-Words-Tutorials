---
title: Inserisci immagine mobile nel documento Word
linktitle: Inserisci immagine mobile nel documento Word
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come inserire un'immagine mobile in un documento Word usando Aspose.Words per .NET con questa guida dettagliata passo dopo passo. Perfetta per migliorare i tuoi documenti.
weight: 10
url: /it/net/add-content-using-documentbuilder/insert-floating-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci immagine mobile nel documento Word

## Introduzione

Immagina di creare un report o una proposta sbalorditivi in cui le immagini sono posizionate perfettamente per completare il tuo testo. Con Aspose.Words per .NET, puoi ottenere questo risultato senza sforzo. Questa libreria fornisce potenti funzionalità per la manipolazione dei documenti, rendendola una soluzione di riferimento per gli sviluppatori. In questo tutorial, ci concentreremo sull'inserimento di un'immagine mobile utilizzando la classe DocumentBuilder. Che tu sia uno sviluppatore esperto o alle prime armi, questa guida ti guiderà attraverso ogni passaggio.

## Prerequisiti

Prima di iniziare, assicuriamoci di avere tutto il necessario per iniziare:

1.  Aspose.Words per .NET: puoi scaricare la libreria da[Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
2. Visual Studio: qualsiasi versione che supporti lo sviluppo .NET.
3. Conoscenza di base di C#: sarà utile comprendere le basi della programmazione in C#.
4. File immagine: file immagine che si desidera inserire, ad esempio un logo o una foto.

## Importazione degli spazi dei nomi

Per usare Aspose.Words nel tuo progetto, devi importare i namespace necessari. Questo si fa aggiungendo le seguenti righe in cima al tuo file C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Una volta stabiliti questi prerequisiti e namespace, siamo pronti per iniziare il nostro tutorial.

Analizziamo il processo di inserimento di un'immagine mobile in un documento Word in passaggi gestibili. Ogni passaggio verrà spiegato in dettaglio per garantire che tu possa seguire senza intoppi.

## Passaggio 1: imposta il tuo progetto

Per prima cosa, crea un nuovo progetto C# in Visual Studio. Puoi scegliere un'app console per semplicità.

1. Aprire Visual Studio e creare un nuovo progetto.
2. Selezionare "App console (.NET Core)" e fare clic su "Avanti".
3. Assegna un nome al tuo progetto e scegli una posizione in cui salvarlo. Fai clic su "Crea".
4. Installa Aspose.Words per .NET tramite NuGet Package Manager. Fai clic con il pulsante destro del mouse sul tuo progetto in Solution Explorer, seleziona "Manage NuGet Packages" e cerca "Aspose.Words". Installa la versione più recente.

## Passaggio 2: inizializzare Document e DocumentBuilder

Ora che il progetto è impostato, inizializziamo gli oggetti Document e DocumentBuilder.

1.  Crea una nuova istanza di`Document` classe:

```csharp
Document doc = new Document();
```

2. Inizializza un oggetto DocumentBuilder:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

 IL`Document` l'oggetto rappresenta il documento Word e l'`DocumentBuilder` aiuta ad aggiungervi contenuti.

## Passaggio 3: definire il percorso dell'immagine

Poi, specifica il percorso del tuo file immagine. Assicurati che la tua immagine sia accessibile dalla directory del tuo progetto.

Definire la directory dell'immagine e il nome del file immagine:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

 Sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo in cui è archiviata l'immagine.

## Passaggio 4: Inserisci l'immagine mobile

Dopo aver impostato tutto, inseriamo l'immagine mobile nel documento.

 Utilizzare il`InsertImage` metodo del`DocumentBuilder` classe per inserire l'immagine:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Ecco cosa significa ogni parametro:
- `imagePath`: Percorso del file immagine.
- `RelativeHorizontalPosition.Margin`: La posizione orizzontale rispetto al margine.
- `100`: Spostamento orizzontale dal margine (in punti).
- `RelativeVerticalPosition.Margin`: La posizione verticale rispetto al margine.
- `100`: Spostamento verticale dal margine (in punti).
- `200`: Larghezza dell'immagine (in punti).
- `100`: Altezza dell'immagine (in punti).
- `WrapType.Square`: Stile di avvolgimento del testo attorno all'immagine.

## Passaggio 5: Salvare il documento

Infine, salva il documento nella posizione desiderata.

1. Specificare il percorso del file di output:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Salva il documento:

```csharp
doc.Save(outputPath);
```

Il tuo documento Word con l'immagine mobile è ora pronto!

## Conclusione

Inserire un'immagine mobile in un documento Word usando Aspose.Words per .NET è un processo semplice se suddiviso in passaggi gestibili. Seguendo questa guida, puoi aggiungere immagini dall'aspetto professionale ai tuoi documenti, migliorandone l'aspetto visivo. Aspose.Words fornisce una solida API che semplifica la manipolazione dei documenti, sia che tu stia lavorando su report, proposte o qualsiasi altro tipo di documento.

## Domande frequenti

### Posso inserire più immagini utilizzando Aspose.Words per .NET?

 Sì, puoi inserire più immagini ripetendo l'operazione`InsertImage` metodo per ogni immagine con i parametri desiderati.

### Come faccio a cambiare la posizione dell'immagine?

 Puoi regolare il`RelativeHorizontalPosition`, `RelativeVerticalPosition`e parametri di offset per posizionare l'immagine come necessario.

### Quali altri tipi di wrap sono disponibili per le immagini?

 Aspose.Words supporta vari tipi di wrap come`Inline`, `TopBottom`, `Tight`, `Through`, e altro ancora. Puoi scegliere quello che meglio si adatta al layout del tuo documento.

### Posso usare formati di immagine diversi?

Sì, Aspose.Words supporta un'ampia gamma di formati immagine, tra cui JPEG, PNG, BMP e GIF.

### Come posso ottenere una prova gratuita di Aspose.Words per .NET?

 Puoi ottenere una prova gratuita da[Pagina di prova gratuita di Aspose](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
