---
category: general
date: 2026-09-21
description: Impara a creare un grafico a torta e a inserirlo in Word usando Aspose.Words,
  aggiungere etichette dati al grafico a torta e mostrare le percentuali sul grafico
  a torta in pochi passaggi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- insert chart into word
- add data labels to pie chart
- show percentages on pie chart
- how to display percentages in chart
language: it
lastmod: 2026-09-21
og_description: Crea un grafico a torta in Word usando Aspose.Words, inserisci il
  grafico in Word, aggiungi etichette dati al grafico a torta e mostra le percentuali
  sul grafico a torta—tutto con esempi di codice chiari.
og_image_alt: Screenshot of a Word document containing a pie chart with percentage
  data labels displayed outside each slice
og_title: Crea un grafico a torta in Word con Aspose.Words – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
- description: Learn how to create pie chart and insert chart into Word using Aspose.Words,
    add data labels to pie chart, and show percentages on pie chart in just a few
    steps.
  name: How to create pie chart in a Word document with Aspose.Words
  steps:
  - name: Expected output
    text: 'When you open the generated document, you should see:'
  - name: Adding a title to the chart
    text: '```csharp chart.Title.Text = "Sales Distribution Q1"; chart.Title.Show
      = true; ```'
  - name: Changing slice colors
    text: '```csharp series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
      series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen; ```'
  - name: Handling an empty series
    text: 'If your data source might be empty, guard against `IndexOutOfRangeException`:'
  - name: Exporting to PDF instead of Word
    text: '```csharp doc.Save("PieChart.pdf", SaveFormat.Pdf); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- charting
- Word automation
title: Come creare un grafico a torta in un documento Word con Aspose.Words
url: /it/net/programming-with-charts/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico a torta in un documento Word con Aspose.Words

Se hai bisogno di **creare un grafico a torta** programmaticamente, Aspose.Words lo rende semplice. In questo tutorial vedrai come **inserire un grafico in Word**, configurare le serie, **aggiungere etichette dati al grafico a torta**, e infine **mostrare le percentuali sul grafico a torta** in modo che il visual trasmetta valori esatti. Alla fine avrai un esempio completo e eseguibile che potrai inserire in qualsiasi progetto .NET.

Questa guida copre tutto ciò che devi sapere: i pacchetti NuGet richiesti, il codice C# completo, spiegazioni sul perché ogni chiamata API è importante e suggerimenti per personalizzare il grafico. Non è necessaria alcuna documentazione esterna—basta copiare, eseguire e adattare.

## Prerequisiti

* .NET 6.0 SDK o versioni successive installate.  
* Visual Studio 2022 (o qualsiasi IDE che supporti .NET).  
* Una licenza Aspose.Words per .NET (la versione di prova gratuita funziona per i test).  
* Familiarità di base con C# e le strutture dei documenti Word.

Se hai già tutto questo, puoi passare direttamente al codice.

## Passo 1: Configurare il progetto e importare Aspose.Words

Crea un nuovo progetto console e aggiungi il pacchetto NuGet Aspose.Words:

```bash
dotnet new console -n PieChartDemo
cd PieChartDemo
dotnet add package Aspose.Words
```

Il pacchetto include lo spazio dei nomi `Aspose.Words.Drawing.Charts`, che contiene le classi `Chart` e `ChartSeries` che utilizzeremo.

> **Consiglio professionale:** Mantieni il file di licenza (`Aspose.Words.lic`) nella radice del progetto e caricalo all'avvio per evitare filigrane di valutazione.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: Apply your license
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");
```

## Passo 2: Creare un documento vuoto e un DocumentBuilder

Un `Document` rappresenta il file Word, mentre `DocumentBuilder` fornisce un'API fluida per inserire contenuti.

```csharp
        // Create a new blank document
        Document doc = new Document();

        // DocumentBuilder will let us add a chart
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:** Il `DocumentBuilder` mantiene il punto di inserimento corrente, garantendo che il grafico appaia esattamente dove desideri nel flusso del documento.

## Passo 3: Inserire un grafico a torta nel documento Word

Ora **inseriamo un grafico in Word**. Il metodo `InsertChart` accetta il tipo di grafico, la larghezza e l'altezza (in punti).

```csharp
        // Insert a pie chart of size 400x300 points
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

A questo punto il grafico contiene una serie di dati predefinita con valori segnaposto (25, 25, 25, 25). Puoi sostituirli in seguito se necessario.

## Passo 4: Accedere alla prima serie e personalizzare le etichette dati

Un grafico a torta tipicamente ha una sola serie. Per **aggiungere etichette dati al grafico a torta**, la recuperiamo e abilitiamo la visualizzazione delle percentuali.

```csharp
        // Access the first (and only) series of the chart
        ChartSeries series = chart.Series[0];

        // Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // Position the labels outside the slices for readability
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

**Perché impostiamo `ShowPercentage`:** Questo flag indica ad Aspose.Words di calcolare il contributo di ogni fetta e di renderlo come percentuale. La proprietà `Position` assicura che l'etichetta non si sovrapponga alla fetta, migliorando la leggibilità—soprattutto quando le fette sono piccole.

## Passo 5: (Opzionale) Sostituire i dati segnaposto

Se desideri valori specifici, sostituisci i punti predefiniti:

```csharp
        // Clear existing points
        series.Points.Clear();

        // Add custom data points
        series.Points.Add(new ChartPoint(40)); // 40%
        series.Points.Add(new ChartPoint(30)); // 30%
        series.Points.Add(new ChartPoint(20)); // 20%
        series.Points.Add(new ChartPoint(10)); // 10%
```

Le percentuali visualizzate si adegueranno automaticamente per riflettere i nuovi valori.

## Passo 6: Salvare il documento

Infine, scrivi il documento su disco. L'estensione determina il formato; `.docx` crea un file Word moderno.

```csharp
        // Save the document containing the pie chart
        doc.Save("PieChart.docx");
    }
}
```

Eseguendo il programma viene generato un file chiamato **PieChart.docx** nella cartella di output. Aprendolo in Microsoft Word si vede un grafico a torta con ogni fetta etichettata con la sua percentuale, posizionata all'esterno delle fette.

### Output previsto

Quando apri il documento generato, dovresti vedere:

* Un unico grafico a torta, di dimensioni 400 × 300 pt.  
* Quattro fette (o quante punti hai aggiunto).  
* Etichette percentuali come “40 %”, “30 %”, ecc., visualizzate all'esterno di ogni fetta.

Se le etichette appaiono all'interno delle fette, verifica nuovamente che `ChartDataLabelPosition.OutsideEnd` sia stato impostato correttamente.

## Passo 7: Varianti comuni e casi limite

### Aggiungere un titolo al grafico

```csharp
chart.Title.Text = "Sales Distribution Q1";
chart.Title.Show = true;
```

### Cambiare i colori delle fette

```csharp
series.Points[0].Format.Fill.ForeColor = System.Drawing.Color.LightBlue;
series.Points[1].Format.Fill.ForeColor = System.Drawing.Color.LightGreen;
```

### Gestire una serie vuota

Se la tua fonte dati potrebbe essere vuota, proteggi il codice da `IndexOutOfRangeException`:

```csharp
if (series.Points.Count == 0)
{
    // Provide a fallback to avoid runtime errors
    series.Points.Add(new ChartPoint(100));
}
```

### Esportare in PDF invece di Word

La stessa logica di rendering del grafico si applica; Aspose.Words converte automaticamente il layout Word in PDF.

```csharp
doc.Save("PieChart.pdf", SaveFormat.Pdf);
```

## Elenco completo del codice sorgente

Di seguito trovi il programma completo, pronto per l'esecuzione. Copialo in `Program.cs` ed esegui `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Optional: apply your license to remove evaluation watermarks
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Create a DocumentBuilder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a pie chart (400x300 points)
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 4. Access the first series
        ChartSeries series = chart.Series[0];

        // 5. Show percentages on each slice
        series.DataLabels.ShowPercentage = true;

        // 6. Position data labels outside the slices
        series.DataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Optional: replace placeholder data with custom values
        series.Points.Clear();
        series.Points.Add(new ChartPoint(40));
        series.Points.Add(new ChartPoint(30));
        series.Points.Add(new ChartPoint(20));
        series.Points.Add(new ChartPoint(10));

        // Optional: add a title
        chart.Title.Text = "Quarterly Sales Breakdown";
        chart.Title.Show = true;

        // 7. Save the document
        doc.Save("PieChart.docx"); // Change extension to .pdf for PDF output
    }
}
```

## Conclusione

Ora sai come **creare un grafico a torta** in un file Word usando Aspose.Words, **inserire un grafico in Word**, **aggiungere etichette dati al grafico a torta**, e **mostrare le percentuali sul grafico a torta**. L'esempio dimostra l'intero flusso di lavoro—dalla configurazione del progetto al documento finale—così da poterlo adattare a dashboard, report o generazione automatica di fatture.

Successivamente, esplora argomenti correlati come **come visualizzare le percentuali nelle legende dei grafici**, personalizzare i colori del grafico o convertire il documento Word in PDF per la distribuzione. Sperimenta con diversi tipi di grafico (Bar, Line) usando lo stesso metodo `InsertChart` per ampliare le tue capacità di automazione.

Buon lavoro con i grafici!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Inserire un grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Creare un grafico a dispersione Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Inserire un grafico ad area in un documento Word | Aspose.Words per .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}