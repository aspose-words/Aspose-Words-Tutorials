---
"description": "Scopri come formattare i numeri degli assi dei grafici utilizzando Aspose.Words per .NET con questa guida passo passo. Migliora la leggibilità e la professionalità dei tuoi documenti senza sforzo."
"linktitle": "Formato numerico per asse in un grafico"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Formato numerico per asse in un grafico"
"url": "/it/net/programming-with-charts/number-format-for-axis/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formato numerico per asse in un grafico

## Introduzione

Ciao! Hai mai lavorato con grafici nei tuoi documenti e desiderato poter formattare i numeri sugli assi per renderli più professionali? Beh, sei fortunato! In questo tutorial, approfondiremo come ottenere proprio questo risultato utilizzando Aspose.Words per .NET. Questa potente libreria ti permette di gestire i documenti Word in modo semplicissimo. E oggi ci concentreremo su come rinnovare gli assi dei grafici con formati numerici personalizzati.

## Prerequisiti

Prima di iniziare, assicuriamoci che tu abbia tutto il necessario. Ecco una breve lista di controllo:

- Aspose.Words per .NET: assicurati di averlo installato. In caso contrario, puoi [scaricalo qui](https://releases.aspose.com/words/net/).
- .NET Framework: assicurati di aver installato un framework .NET compatibile.
- Ambiente di sviluppo: un IDE come Visual Studio funzionerà perfettamente.
- Conoscenza di base di C#: ti aiuterà a seguire gli esempi di codifica.

## Importa spazi dei nomi

Per prima cosa, devi importare gli spazi dei nomi necessari nel tuo progetto. È come gettare le fondamenta prima di costruire una casa. Aggiungi le seguenti direttive using all'inizio del tuo file di codice:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Reporting;
```

Ora scomponiamo il processo in passaggi semplici e facili da seguire.

## Fase 1: Impostazione del documento

Titolo: Inizializza il tuo documento

Per prima cosa, devi creare un nuovo documento e un generatore di documenti. Considera questo passaggio come la preparazione della tela e del pennello prima di iniziare il tuo capolavoro.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Qui, `dataDir` è il percorso verso la directory dei documenti in cui salverai il file finale. `Document` E `DocumentBuilder` sono classi di Aspose.Words che aiutano a creare e manipolare documenti Word.

## Passaggio 2: inserimento di un grafico

Titolo: Aggiungi un grafico al tuo documento

Ora aggiungiamo un grafico al documento. È qui che inizia la magia. Inseriremo un istogramma che fungerà da tela bianca.

```csharp
Shape shape = builder.InsertChart(ChartType.Column, 432, 252);
Chart chart = shape.Chart;
```

IL `InsertChart` Il metodo inserisce nel documento un grafico del tipo specificato (colonna in questo caso) e delle dimensioni specificate.

## Passaggio 3: personalizzazione della serie di grafici

Titolo: Popola il tuo grafico con i dati

Ora dobbiamo aggiungere alcuni dati al nostro grafico. Questo passaggio è simile a quello di riempire il grafico con informazioni significative.

```csharp
chart.Series.Clear();
chart.Series.Add("Aspose Series 1",
    new string[] { "Item 1", "Item 2", "Item 3", "Item 4", "Item 5" },
    new double[] { 1900000, 850000, 2100000, 600000, 1500000 });
```

Qui stiamo aggiungendo una nuova serie chiamata "Aspose Series 1" con cinque punti dati. `Series.Clear` metodo garantisce che tutti i dati preesistenti vengano rimossi prima di aggiungere la nostra nuova serie.

## Passaggio 4: formattazione dei numeri degli assi

Titolo: Abbellisci i numeri dei tuoi assi

Infine, formattiamo i numeri sull'asse Y per renderli più leggibili. È come dare gli ultimi ritocchi alla tua opera d'arte.

```csharp
chart.AxisY.NumberFormat.FormatCode = "#,##0";
```

IL `FormatCode` La proprietà consente di impostare un formato personalizzato per i numeri sull'asse. In questo esempio, `#,##0` assicura che i numeri grandi vengano visualizzati con virgole per le migliaia.

## Passaggio 5: salvataggio del documento

Titolo: Salva il tuo capolavoro

Ora che tutto è pronto, è il momento di salvare il documento. Questo passaggio è la grande rivelazione del tuo lavoro.

```csharp
doc.Save(dataDir + "WorkingWithCharts.NumberFormatForAxis.docx");
```

Qui, il `Save` metodo salva il documento nel percorso specificato con il nome file `WorkingWithCharts.NumberFormatForAxis.docx`.

## Conclusione

Ed ecco fatto! Hai formattato correttamente i numeri sull'asse Y del tuo grafico utilizzando Aspose.Words per .NET. Questo non solo rende i tuoi grafici più professionali, ma ne migliora anche la leggibilità. Aspose.Words offre una vasta gamma di funzionalità che possono aiutarti a creare splendidi documenti Word programmandoli. Quindi, perché non approfondire ulteriormente e scoprire cos'altro puoi fare?

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria che consente agli sviluppatori di creare, manipolare e convertire documenti Word a livello di programmazione.

### Posso formattare altri aspetti del grafico oltre ai numeri degli assi?
Assolutamente! Aspose.Words per .NET consente di formattare titoli, etichette e persino di personalizzare l'aspetto del grafico.

### È disponibile una versione di prova gratuita di Aspose.Words per .NET?
Sì, puoi ottenere un [prova gratuita qui](https://releases.aspose.com/).

### Posso utilizzare Aspose.Words per .NET con altri linguaggi .NET oltre a C#?
Sì, Aspose.Words per .NET è compatibile con qualsiasi linguaggio .NET, inclusi VB.NET e F#.

### Dove posso trovare una documentazione più dettagliata?
La documentazione dettagliata è disponibile su [Pagina di documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}