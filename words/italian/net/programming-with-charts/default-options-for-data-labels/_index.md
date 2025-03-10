---
title: Imposta le opzioni predefinite per le etichette dati in un grafico
linktitle: Imposta le opzioni predefinite per le etichette dati in un grafico
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come impostare le opzioni predefinite per le etichette dati in un grafico usando Aspose.Words per .NET. Segui la nostra guida passo passo per creare e personalizzare i grafici senza sforzo.
weight: 10
url: /it/net/programming-with-charts/default-options-for-data-labels/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta le opzioni predefinite per le etichette dati in un grafico

## Introduzione

Ciao! Non vedi l'ora di immergerti nel mondo dell'automazione dei documenti? Oggi esploreremo come usare Aspose.Words per .NET per creare documenti straordinari a livello di programmazione. Aspose.Words è una potente libreria che ti consente di manipolare i documenti Word con facilità e in questo tutorial ci concentreremo sull'impostazione delle opzioni predefinite per le etichette dati in un grafico. Che tu sia uno sviluppatore esperto o un principiante, questa guida ti guiderà attraverso ogni passaggio per farti iniziare subito a lavorare.

## Prerequisiti

Prima di iniziare, assicuriamoci di avere tutto ciò che ti serve per seguire questo tutorial. Ecco una rapida checklist:

- Visual Studio o qualsiasi altro IDE compatibile con .NET: qui scriverai ed eseguirai il tuo codice.
-  Aspose.Words per .NET: puoi[Scarica l'ultima versione](https://releases.aspose.com/words/net/) e installalo nel tuo progetto.
- Conoscenza di base della programmazione C#: sebbene questa guida sia adatta ai principianti, una minima familiarità con C# sarà utile.
- .NET Framework installato: assicurati di aver installato .NET Framework sul tuo computer.
-  Una licenza temporanea per Aspose.Words: Ottienine una[Qui](https://purchase.aspose.com/temporary-license/) per sbloccare tutte le funzionalità.

Una volta soddisfatti questi prerequisiti, siamo pronti a partire!

## Importazione degli spazi dei nomi

Per prima cosa, impostiamo il nostro progetto e importiamo i namespace necessari. Questi namespace sono essenziali per accedere alla funzionalità Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.ReportingServices;
```

## Passaggio 1: creare un nuovo documento


 Il viaggio inizia con la creazione di un nuovo documento e l'inizializzazione di un`DocumentBuilder` . IL`DocumentBuilder` La classe fornisce un set di metodi per manipolare facilmente il contenuto del documento.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Crea un nuovo documento
Document doc = new Document();

// Inizializza DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Spiegazione

 In questo passaggio, abbiamo impostato il documento e il generatore che utilizzeremo per inserire e formattare il nostro contenuto. Il`dataDir` La variabile contiene il percorso in cui salveremo il nostro documento finale.

## Passaggio 2: inserire un grafico

 Successivamente, aggiungeremo un grafico a torta al nostro documento. Il`InsertChart` metodo del`DocumentBuilder` la classe rende tutto questo semplicissimo.

```csharp
// Inserire un grafico a torta
Shape shape = builder.InsertChart(ChartType.Pie, 432, 252);

// Accedi all'oggetto grafico
Chart chart = shape.Chart;
```

### Spiegazione

Qui, stiamo inserendo un grafico a torta nel nostro documento. Il`InsertChart` Il metodo richiede il tipo di grafico, la larghezza e l'altezza come parametri. Dopo aver inserito il grafico, accediamo all'oggetto grafico per manipolarlo ulteriormente.

## Passaggio 3: personalizzare la serie di grafici

Ora, cancelleremo tutte le serie esistenti nel grafico e aggiungeremo la nostra serie personalizzata. Questa serie rappresenterà i nostri punti dati.

```csharp
// Cancella serie di grafici esistenti
chart.Series.Clear();

// Aggiungi una nuova serie al grafico
ChartSeries series = chart.Series.Add("Aspose Series 1",
    new string[] { "Category 1", "Category 2", "Category 3" },
    new double[] { 2.7, 3.2, 0.8 });
```

### Spiegazione

In questo passaggio, ci assicuriamo che il nostro grafico sia vuoto cancellando qualsiasi serie preesistente. Quindi, aggiungiamo una nuova serie con categorie e valori personalizzati, che saranno visualizzati nel nostro grafico a torta.

## Passaggio 4: impostare le opzioni predefinite per le etichette dati

Le etichette dati sono essenziali per rendere informativo il tuo grafico. Imposteremo le opzioni per mostrare percentuale, valore e personalizzare il separatore.

```csharp
// Accedi alla raccolta di etichette dati
ChartDataLabelCollection labels = series.DataLabels;

// Imposta le opzioni dell'etichetta dati
labels.ShowPercentage = true;
labels.ShowValue = true;
labels.ShowLeaderLines = false;
labels.Separator = " - ";
```

### Spiegazione

 Qui stiamo accedendo al`DataLabels`proprietà della nostra serie per personalizzare l'aspetto e le informazioni visualizzate su ogni etichetta dati. Abbiamo scelto di mostrare sia la percentuale che il valore, nascondere le linee guida e impostare un separatore personalizzato.

## Passaggio 5: Salvare il documento

Infine, salveremo il nostro documento nella directory specificata. Questo passaggio assicura che tutte le nostre modifiche vengano scritte in un file.

```csharp
// Salva il documento
doc.Save(dataDir + "WorkingWithCharts.DefaultOptionsForDataLabels.docx");
```

### Spiegazione

 In quest'ultimo passaggio, salviamo il nostro documento utilizzando il`Save` metodo. Il documento verrà salvato nella directory specificata da`dataDir`, con il nome "WorkingWithCharts.DefaultOptionsForDataLabels.docx".

## Conclusione

Ed ecco fatto! Hai creato con successo un documento Word con un grafico a torta personalizzato usando Aspose.Words per .NET. Questa potente libreria semplifica l'automazione della creazione e della manipolazione dei documenti, facendoti risparmiare tempo e fatica. Che tu stia generando report, fatture o qualsiasi altro tipo di documento, Aspose.Words ti copre.

 Sentiti libero di esplorare il[Documentazione di Aspose.Words](https://reference.aspose.com/words/net/) per altre funzionalità ed esempi. Buona programmazione!

## Domande frequenti

### Posso usare Aspose.Words gratuitamente?
Puoi utilizzare Aspose.Words gratuitamente con un[licenza temporanea](https://purchase.aspose.com/temporary-license/) o esplora le sue caratteristiche utilizzando il[prova gratuita](https://releases.aspose.com/).

### Come posso ottenere supporto per Aspose.Words?
 Puoi ottenere supporto tramite[Forum di supporto di Aspose.Words](https://forum.aspose.com/c/words/8).

### Posso aggiungere altri tipi di grafici?
 Sì, Aspose.Words supporta vari tipi di grafici, come grafici a barre, a linee e a colonne. Controlla[documentazione](https://reference.aspose.com/words/net/) per maggiori dettagli.

### Aspose.Words è compatibile con .NET Core?
 Sì, Aspose.Words è compatibile con .NET Core. Puoi trovare maggiori informazioni in[documentazione](https://reference.aspose.com/words/net/).

### Come posso acquistare una licenza per Aspose.Words?
 Puoi acquistare una licenza da[Negozio Aspose](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
