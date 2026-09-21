---
category: general
date: 2026-09-21
description: Come creare un istogramma in Word con Aspose.Words. Scopri come impostare
  gli intervalli dell'istogramma e configurarli per una visualizzazione precisa dei
  dati.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create histogram in word
- how to set histogram bins
- configure histogram bins
language: it
lastmod: 2026-09-21
og_description: Come creare un istogramma in Word con Aspose.Words. Questo tutorial
  ti mostra come impostare gli intervalli dell'istogramma e configurare gli intervalli
  dell'istogramma per grafici accurati.
og_image_alt: Screenshot of a Word document showing a histogram chart created with
  Aspose.Words
og_title: Crea un istogramma in Word con Aspose.Words – guida completa
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  headline: How to create histogram in Word with Aspose.Words
  type: TechArticle
- description: How to create histogram in Word with Aspose.Words. Learn how to set
    histogram bins and configure histogram bins for precise data visualisation.
  name: How to create histogram in Word with Aspose.Words
  steps:
  - name: Prepare the development environment.
    text: Prepare the development environment.
  - name: Build a blank Word document and obtain a `DocumentBuilder`.
    text: Build a blank Word document and obtain a `DocumentBuilder`.
  - name: Insert a histogram chart and adjust its properties.
    text: Insert a histogram chart and adjust its properties.
  - name: Save the document and verify the result.
    text: Save the document and verify the result.
  type: HowTo
tags:
- histogram
- Aspose.Words
- C#
- Word automation
title: Come creare un istogramma in Word con Aspose.Words
url: /it/net/programming-with-charts/how-to-create-histogram-in-word-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un istogramma in Word con Aspose.Words

Se hai bisogno di creare un istogramma in Word, Aspose.Words rende il processo semplice. Questa guida ti accompagna passo passo, dalla configurazione del progetto alla configurazione dei contenitori dell'istogramma per una chiara presentazione dei dati. Vedrai anche come impostare i contenitori dell'istogramma e configurarli per soddisfare i requisiti del tuo report.

## Come creare un istogramma in Word – flusso di lavoro generale

Il flusso di lavoro complessivo è composto da quattro fasi logiche:

1. Preparare l'ambiente di sviluppo.  
2. Creare un documento Word vuoto e ottenere un `DocumentBuilder`.  
3. Inserire un grafico a istogramma e regolare le sue proprietà.  
4. Salvare il documento e verificare il risultato.

Ogni fase è descritta in dettaglio di seguito, e il codice sorgente completo è fornito alla fine dell'articolo.

## Configurare l'ambiente di sviluppo

Prima di scrivere qualsiasi codice, assicurati di avere i seguenti prerequisiti:

| Prerequisito | Motivo |
|--------------|--------|
| .NET 6.0 o versioni successive | Fornisce l'ambiente di runtime per i progetti C#. |
| Visual Studio 2022 (o qualsiasi IDE che supporti .NET) | Consente di compilare e fare il debug del campione. |
| Pacchetto NuGet Aspose.Words per .NET | Fornisce le classi `Document`, `DocumentBuilder` e chart. |

Puoi aggiungere il pacchetto Aspose.Words con la CLI di NuGet:

```bash
dotnet add package Aspose.Words
```

> **Consiglio professionale:** usa una versione fissa (ad es., `23.9.0`) in produzione per evitare cambiamenti inattesi che interrompono il funzionamento.

## Inserire un grafico a istogramma

Con l'ambiente pronto, crea un nuovo progetto console e apri il file `Program.cs`. Le prime due righe di codice istanziano un documento vuoto e un `DocumentBuilder` che ti permette di manipolare il documento:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Create a new blank document and a DocumentBuilder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Successivamente, chiama `InsertChart` per aggiungere un istogramma. Il metodo richiede il tipo di grafico, la larghezza e l'altezza in punti:

```csharp
// Insert a histogram chart with a specific size (400x300 points)
Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);
```

A questo punto il documento contiene un segnaposto di istogramma vuoto. Quando apri il file *.docx* generato, vedrai un'area del grafico grigia pronta per i dati.

![Segnaposto dell'istogramma in documento Word](/images/histogram-placeholder.png){: .img-fluid alt="Screenshot di un documento Word che mostra un segnaposto del grafico a istogramma creato con Aspose.Words"}

## Come impostare i contenitori dell'istogramma

Un istogramma visualizza la distribuzione di dati numerici raggruppando i valori in *contenitori*. La proprietà `HistogramBins` controlla quanti contenitori il grafico visualizza. Impostare questa proprietà prima di aggiungere i dati garantisce che il grafico riservi il numero corretto di barre.

```csharp
// Set the number of bins (bars) in the histogram
histogram.HistogramBins = 10;
```

Puoi regolare il conteggio dei contenitori per adattarlo alla granularità del tuo set di dati. Ad esempio, un set di dati che va da 0 a 100 con un conteggio di contenitori pari a 10 crea intervalli di 10 unità ciascuno (0‑9, 10‑19, …, 90‑100).

> **Perché è importante:** scegliere troppo pochi contenitori può nascondere pattern importanti, mentre troppi contenitori possono produrre un grafico rumoroso. Prova alcuni valori per trovare il punto ottimale per i tuoi dati specifici.

## Configurare i contenitori dell'istogramma per una migliore leggibilità

Oltre al numero di contenitori, spesso vuoi etichettare ogni contenitore affinché i lettori possano vedere il conteggio esatto. La proprietà `ShowBinLabels` attiva o disattiva la visibilità di queste etichette:

```csharp
// Display the value of each bin on the chart
histogram.ShowBinLabels = true;
```

Quando `ShowBinLabels` è impostato su `true`, Word visualizza un'etichetta numerica sopra ogni barra. Questo piccolo passaggio di configurazione migliora notevolmente l'interpretabilità del grafico, soprattutto nei report in cui il pubblico potrebbe non avere il set di dati originale.

Puoi anche personalizzare l'aspetto dell'etichetta, come la dimensione del carattere o il colore, tramite l'oggetto `HistogramLabel` (disponibile nelle versioni successive di Aspose.Words). Il frammento seguente dimostra una regolazione comune:

```csharp
// Optional: make bin labels bold and increase font size
histogram.HistogramLabel.Font.Size = 10;
histogram.HistogramLabel.Font.Bold = true;
```

> **Caso limite:** se imposti `HistogramBins` a un valore superiore al numero di punti dati distinti, alcuni contenitori appariranno vuoti. Il grafico verrà comunque renderizzato correttamente, ma l'aspetto visivo potrebbe risultare sparso. Considera di ridurre il conteggio dei contenitori in tali scenari.

## Aggiungere una serie di dati all'istogramma

Un istogramma richiede una singola serie di dati che rappresenta i valori numerici sottostanti. Puoi popolare la serie usando un array, una `List<double>` o qualsiasi collezione enumerabile. Di seguito trovi un esempio conciso che aggiunge un set di dati casuale:

```csharp
// Create a data series for the histogram
ChartSeries series = histogram.Series[0];
double[] sampleData = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
series.DataPoints.AddRange(sampleData);
```

Il metodo `AddRange` converte ogni valore in un contenitore secondo i `HistogramBins` definiti in precedenza. Dopo questo passaggio, il grafico visualizza un istogramma completamente popolato.

## Salvare e visualizzare il documento risultante

Infine, scrivi il documento su disco. Puoi scegliere qualsiasi percorso accessibile dalla tua applicazione. La riga seguente salva il file come `output.docx`:

```csharp
// Save the document so you can view the chart
doc.Save("output.docx");
```

Apri `output.docx` in Microsoft Word per vedere un istogramma con dieci contenitori, valori etichettati e i dati di esempio forniti. Il grafico avrà un aspetto simile all'immagine seguente:

![Istogramma completato in Word](/images/histogram-complete.png){: .img-fluid alt="Documento Word che mostra un grafico a istogramma completato con dieci contenitori e etichette"}

## Esempio completo, eseguibile

Unendo tutti i pezzi, ecco un programma autonomo che puoi copiare, incollare ed eseguire:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a histogram chart (400×300 points)
        Chart histogram = builder.InsertChart(ChartType.Histogram, 400, 300);

        // 3️⃣ Configure the histogram
        histogram.HistogramBins = 10;          // How to set histogram bins
        histogram.ShowBinLabels = true;       // Configure histogram bins to show labels
        histogram.HistogramLabel.Font.Size = 10;
        histogram.HistogramLabel.Font.Bold = true;

        // 4️⃣ Add a data series
        ChartSeries series = histogram.Series[0];
        double[] data = { 12, 45, 23, 67, 34, 89, 54, 31, 22, 78, 41, 60 };
        series.DataPoints.AddRange(data);

        // 5️⃣ Save the document
        doc.Save("output.docx");
    }
}
```

**Output previsto:** aprendo `output.docx` si visualizza un istogramma con dieci barre equidistanti, ciascuna etichettata con il proprio conteggio. Il grafico riflette la distribuzione dell'array `data`, rendendo le tendenze immediatamente visibili.

## Domande comuni e risoluzione dei problemi

| Domanda | Risposta |
|----------|--------|
| *E se ho bisogno di più di una serie di dati?* | Gli istogrammi tipicamente rappresentano una singola distribuzione. Se ti servono più serie, considera l'uso di un grafico a colonne. |
| *Posso modificare le dimensioni del grafico dopo l'inserimento?* | Sì. Regola le proprietà `histogram.Width` e `histogram.Height`, oppure chiama nuovamente `builder.InsertChart` con dimensioni diverse. |
| *Funziona con .NET Framework 4.8?* | Assolutamente. Aspose.Words supporta .NET Framework 4.5 e versioni successive, quindi lo stesso codice funziona senza modifiche. |
| *Come esportare il grafico come immagine?* | Usa `histogram.ToImage()` per ottenere un `System.Drawing.Image`, quindi salvalo con `image.Save("chart.png")`. |

## Conclusione

Ora sai come creare un istogramma in Word usando Aspose.Words, come impostare i contenitori dell'istogramma e come configurarli per un output chiaro e etichettato. L'esempio completo dimostra un approccio pronto per la produzione che puoi adattare a qualsiasi scenario di reporting basato sui dati.  

Successivamente, esplora argomenti correlati come **come creare grafici a torta in Word**, **personalizzare i colori dei grafici** e **incorporare fonti dati Excel**. Ognuno di questi si basa sullo stesso flusso di lavoro `DocumentBuilder`, così potrai estendere la soluzione con il minimo sforzo.

Buon lavoro con i grafici!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Come creare PDF da Word – Guida completa C#](/words/english/net/basic-conversions/how-to-create-pdf-from-word-complete-c-guide/)
- [Come caricare documenti Word usando Aspose.Words LoadOptions](/words/english/net/programming-with-loadoptions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}