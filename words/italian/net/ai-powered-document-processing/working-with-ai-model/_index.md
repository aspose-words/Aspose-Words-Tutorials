---
title: Lavorare con il modello AI
linktitle: Lavorare con il modello AI
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come usare Aspose.Words per .NET per riassumere i documenti con AI. Semplici passaggi per migliorare la gestione dei documenti.
weight: 10
url: /it/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lavorare con il modello AI

## Introduzione

Benvenuti nell'affascinante mondo di Aspose.Words per .NET! Se hai mai desiderato portare la gestione dei documenti a un livello superiore, sei nel posto giusto. Immagina di avere la possibilità di riassumere automaticamente documenti di grandi dimensioni con solo poche righe di codice. Sembra fantastico, vero? In questa guida, ci immergiamo nell'uso di Aspose.Words per generare riepiloghi di documenti utilizzando potenti modelli di linguaggio AI come GPT di OpenAI. Che tu sia uno sviluppatore che cerca di migliorare le tue applicazioni o un appassionato di tecnologia desideroso di imparare qualcosa di nuovo, questo tutorial ti copre.

## Prerequisiti

Prima di rimboccarci le maniche e iniziare a programmare, ecco alcuni elementi essenziali che devi avere a disposizione:

1. Visual Studio installato: assicurati di avere Visual Studio installato sul tuo computer. Puoi scaricarlo gratuitamente se non lo hai già.
  
2. .NET Framework: assicurati di utilizzare una versione compatibile di .NET Framework per Aspose.Words. Supporta sia .NET Framework che .NET Core.

3.  Aspose.Words per .NET: dovrai scaricare e installare Aspose.Words. Puoi prendere l'ultima versione[Qui](https://releases.aspose.com/words/net/).

4. Una chiave API per i modelli AI: per utilizzare la sintesi AI, avrai bisogno di accedere a un modello AI. Ottieni la tua chiave API da piattaforme come OpenAI o Google.

5. Conoscenza di base di C#: per sfruttare al meglio questo tutorial è necessaria una conoscenza di base della programmazione in C#.

Hai capito tutto? Fantastico! Passiamo alla parte divertente: importare i pacchetti richiesti.

## Importa pacchetti

Per sfruttare i poteri di Aspose.Words e lavorare con i modelli AI, iniziamo importando i pacchetti necessari. Ecco come fare:

### Crea un nuovo progetto

Per prima cosa, avvia Visual Studio e crea un nuovo progetto di applicazione console.

1. Aprire Visual Studio.
2. Fare clic su "Crea un nuovo progetto".
3. Seleziona "App console (.NET Framework)" o "App console (.NET Core)" in base alla configurazione.
4. Assegna un nome al progetto e specifica la posizione.

### Installa Aspose.Words e pacchetti modello AI

Per utilizzare Aspose.Words, è necessario installare il pacchetto tramite NuGet.

1. Fai clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegli "Gestisci pacchetti NuGet".
2. Cerca "Aspose.Words" e fai clic su "Installa".
3. Se si utilizzano pacchetti specifici di modelli di intelligenza artificiale (come OpenAI), assicurarsi che siano installati.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
Congratulazioni! Con i pacchetti pronti, approfondiamo la nostra implementazione.

## Passaggio 1: imposta le directory dei documenti

Nel nostro codice definiremo le directory per gestire dove vengono archiviati i nostri documenti e dove verrà inviato il nostro output. 

```csharp
// La tua directory dei documenti
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// La tua directory ArtifactsDir
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

-  Qui, sostituisci`YOUR_DOCUMENT_DIRECTORY` con la posizione in cui sono archiviati i tuoi documenti e`YOUR_ARTIFACTS_DIRECTORY` dove vuoi salvare i file riepilogati.

## Passaggio 2: caricare i documenti

Poi, caricheremo i documenti che vogliamo riassumere nel nostro programma. È facile come bere un bicchier d'acqua! Ecco come fare:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- Adatta i nomi dei file a quelli che hai salvato. L'esempio presuppone che tu abbia due documenti denominati "Big document.docx" e "Document.docx".

## Passaggio 3: inizializzare il modello AI

Il nostro prossimo passo è stabilire una connessione con il modello AI. È qui che entra in gioco la chiave API che hai ottenuto in precedenza.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- Assicurati di avere la tua chiave API archiviata come variabile d'ambiente. È come tenere al sicuro la tua salsa segreta!

## Passaggio 4: generare un riepilogo per il primo documento

Ora, creiamo un sommario per il nostro primo documento. Imposteremo anche i parametri per definire la lunghezza del sommario.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- Questo frammento riassume il primo documento e salva l'output nella directory degli artefatti specificata. Sentiti libero di modificare la lunghezza del riepilogo a tuo piacimento!

## Passaggio 5: generare un riepilogo per più documenti

Ti senti avventuroso? Puoi anche riassumere più documenti contemporaneamente! Ecco come fare:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- Proprio così, stai riassumendo due documenti contemporaneamente! Che efficienza, vero?

## Conclusione

Ed ecco fatto! Seguendo questa guida, hai padroneggiato l'arte di riassumere documenti usando Aspose.Words per .NET e potenti modelli AI. È una funzionalità entusiasmante che può farti risparmiare un sacco di tempo, sia per uso personale che per l'integrazione in applicazioni professionali. Ora vai avanti, scatena la potenza dell'automazione e guarda la tua produttività salire alle stelle!

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria che consente agli sviluppatori di creare, modificare, convertire e riprodurre documenti Word a livello di programmazione.

### Come posso ottenere una chiave API per i modelli di intelligenza artificiale?
Puoi ottenere una chiave API da provider AI come OpenAI o Google. Assicurati di creare un account e segui le loro istruzioni per generare la tua chiave.

### Posso usare Aspose.Words per altri formati di file?
Sì! Aspose.Words supporta vari formati di file, tra cui DOCX, RTF e HTML, offrendo funzionalità estese che vanno oltre i semplici documenti di testo.

### Esiste una versione gratuita di Aspose.Words?
Aspose offre una prova gratuita, che ti consente di testare le sue funzionalità. Puoi scaricarlo dal loro sito.

### Dove posso trovare altre risorse per Aspose.Words?
 Puoi controllare la documentazione[Qui](https://reference.aspose.com/words/net/) per guide e approfondimenti completi.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
