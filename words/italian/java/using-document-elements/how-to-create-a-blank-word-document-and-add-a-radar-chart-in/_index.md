---
category: general
date: 2026-09-21
description: Crea un documento Word vuoto e impara come inserire un grafico radar
  in un file Word usando DocumentBuilder – guida passo‑passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert radar chart
- insert chart word file
- generate word document chart
- add radial chart word
language: it
lastmod: 2026-09-21
og_description: Crea un documento Word vuoto e inserisci un grafico radar in un file
  Word con Aspose.Words. Segui questo tutorial per generare rapidamente un grafico
  in un documento Word.
og_image_alt: Screenshot showing a blank Word document with a radar chart inserted
og_title: Crea un documento Word vuoto e aggiungi un grafico radar – guida completa
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  headline: How to create a blank Word document and add a radar chart in C#
  type: TechArticle
- description: Create blank Word document and learn how to insert radar chart in a
    Word file using DocumentBuilder – step‑by‑step guide.
  name: How to create a blank Word document and add a radar chart in C#
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 or later (the code also works with .NET Framework 4.6+). * Aspose.Words
      for .NET (NuGet package `Aspose.Words` version 23.9 or newer). * Basic familiarity
      with C# and Visual Studio or your preferred IDE.'
  - name: Expected output
    text: '* A `RadialChartExample.docx` file on your desktop. * The first page contains
      a radar chart with five data points labeled “Series 1”. * No additional text
      appears because the document started blank.'
  - name: 1. Changing chart size after insertion
    text: 'If the initial dimensions don’t fit your layout, resize the chart like
      this:'
  - name: 2. Inserting the chart into a specific location
    text: You can move the builder’s cursor to a bookmark, table cell, or paragraph
      before calling `InsertChart`.
  - name: 3. Customizing chart appearance
    text: Aspose.Words exposes the full chart object model, allowing you to set titles,
      axis labels, and colors.
  - name: 4. Dealing with missing fonts
    text: 'If the target environment lacks a font used in the chart, Aspose.Words
      substitutes a default font. To guarantee consistency, embed the required fonts:'
  - name: 5. Exporting to other formats
    text: 'The same document can be saved as PDF, HTML, or PNG without extra code
      changes:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart generation
title: Come creare un documento Word vuoto e aggiungere un grafico radar in C#
url: /it/java/using-document-elements/how-to-create-a-blank-word-document-and-add-a-radar-chart-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto e aggiungere un grafico radar in C#

Se hai bisogno di **creare un documento Word vuoto** e incorporare un grafico radar (radiale), questo tutorial fornisce una soluzione pronta all'uso. Vedrai come utilizzare Aspose.Words .NET per generare il file, inserire il grafico e salvare il risultato—tutto in pochi passaggi concisi.

Un documento vuoto fornisce una tela pulita per qualsiasi scenario di reporting automatizzato, e aggiungere un grafico radar ti consente di visualizzare dati multidimensionali direttamente dentro Word. Alla fine di questa guida sarai in grado di generare un grafico in un documento Word senza modifiche manuali.

## Cosa imparerai

* Come **creare un documento Word vuoto** programmaticamente con C#.
* Il codice esatto per **inserire un grafico radar** usando `DocumentBuilder`.
* Modi per **inserire un grafico in un file Word** e personalizzarne le dimensioni.
* Come **generare un grafico in un documento Word** e verificare l'output.
* Suggerimenti per **aggiungere file Word con grafico radiale**, inclusi gli errori comuni.

### Prerequisiti

* .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.6+).
* Aspose.Words per .NET (pacchetto NuGet `Aspose.Words` versione 23.9 o successiva).
* Familiarità di base con C# e Visual Studio o l'IDE preferito.

## Creare un documento Word vuoto con C#

Il primo passo è istanziare un oggetto `Document` vuoto. Questo oggetto rappresenta un file `.docx` completamente vuoto.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Step 1: Create a new blank document
Document doc = new Document();
```

`Document` crea la struttura del file ma non contiene ancora sezioni o pagine. Aspose.Words aggiunge automaticamente una sezione predefinita quando inizi ad aggiungere contenuti, motivo per cui il passaggio successivo funziona senza configurazioni aggiuntive.

## Come inserire un grafico radar nel file Word

Un grafico radar (chiamato anche grafico radiale) visualizza i punti dati su assi che si irradiano da un punto centrale. Aspose.Words fornisce `DocumentBuilder.insertChart` per questo scopo.

```csharp
// Step 2: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(doc);

// Step 3: Insert a radar (radial) chart with the desired size (width: 400pt, height: 300pt)
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`InsertChart` restituisce un oggetto `Chart` che puoi configurare ulteriormente. Il grafico appare nella prima pagina del documento vuoto perché il builder è posizionato all'inizio del documento per impostazione predefinita.

## Inserire un grafico in un file Word – aggiungere serie di dati

Un grafico senza dati è invisibile. Popola il grafico radar con una o più serie per renderlo significativo.

```csharp
// Step 4: Populate the chart with series data
ChartSeries series = radarChart.Series.Add("Series 1");

// Add data points (example values)
series.DataPoints.Add(4);
series.DataPoints.Add(7);
series.DataPoints.Add(3);
series.DataPoints.Add(6);
series.DataPoints.Add(5);
```

Puoi aggiungere quante serie desideri. Ogni serie può avere un nome distinto, che appare nella legenda del grafico. I punti dati corrispondono agli assi radiali; l'ordine in cui li aggiungi definisce la loro posizione attorno al cerchio.

## Generare un grafico in un documento Word – salvare il file

Dopo aver costruito il grafico, persisti il documento su disco. Scegli una posizione a cui hai accesso in scrittura.

```csharp
// Step 5: Save the document containing the radar chart
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), 
                                 "RadialChartExample.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Quando apri il file `.docx` risultante in Microsoft Word, vedrai una pagina vuota con un grafico radar dimensionato a 400 × 300 punti, popolato con i dati di esempio.

### Output previsto

* Un file `RadialChartExample.docx` sul desktop.
* La prima pagina contiene un grafico radar con cinque punti dati etichettati “Series 1”.
* Nessun testo aggiuntivo appare perché il documento è iniziato vuoto.

## Aggiungere grafico radiale in Word – gestione dei casi limite comuni

### 1. Modificare le dimensioni del grafico dopo l'inserimento

Se le dimensioni iniziali non si adattano al tuo layout, ridimensiona il grafico così:

```csharp
radarChart.Width = 500;   // width in points
radarChart.Height = 350;  // height in points
```

### 2. Inserire il grafico in una posizione specifica

Puoi spostare il cursore del builder su un segnalibro, una cella di tabella o un paragrafo prima di chiamare `InsertChart`.

```csharp
builder.MoveToBookmark("ChartLocation");
Chart chartInTable = builder.InsertChart(ChartType.Radar, 350, 250);
```

### 3. Personalizzare l'aspetto del grafico

Aspose.Words espone l'intero modello di oggetti del grafico, consentendoti di impostare titoli, etichette degli assi e colori.

```csharp
radarChart.Title.Text = "Sales Performance";
radarChart.Series[0].FillFormat.ForeColor = System.Drawing.Color.Blue;
radarChart.AxisX.Title.Text = "Quarter";
radarChart.AxisY.Title.Text = "Revenue (M)";
```

### 4. Gestire i font mancanti

Se l'ambiente di destinazione non dispone di un font usato nel grafico, Aspose.Words sostituisce un font predefinito. Per garantire coerenza, incorpora i font richiesti:

```csharp
doc.FontSettings.SubstitutionSettings.DefaultFontName = "Arial";
```

### 5. Esportare in altri formati

Lo stesso documento può essere salvato come PDF, HTML o PNG senza modifiche al codice:

```csharp
doc.Save("RadialChartExample.pdf");
```

## Esempio completo, eseguibile

Unendo tutti i pezzi ottieni un unico programma che puoi copiare, incollare ed eseguire.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class RadarChartDemo
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();

        // Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a radar chart (400pt x 300pt)
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

        // Add a data series with sample values
        ChartSeries series = radarChart.Series.Add("Quarterly Sales");
        series.DataPoints.Add(4);
        series.DataPoints.Add(7);
        series.DataPoints.Add(3);
        series.DataPoints.Add(6);
        series.DataPoints.Add(5);

        // Optional: customize appearance
        radarChart.Title.Text = "Quarterly Sales Radar";
        radarChart.AxisX.Title.Text = "Quarter";
        radarChart.AxisY.Title.Text = "Units Sold";

        // Save the document
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadialChartExample.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Esegui questo programma, apri il file generato e vedrai un grafico radar professionale pronto per la distribuzione.

## Conclusione

Ora sai come **creare un documento Word vuoto**, **inserire un grafico radar** e **generare un grafico in un documento Word** usando Aspose.Words. Seguendo i passaggi sopra potrai anche **aggiungere file Word con grafico radiale** a qualsiasi pipeline di reporting automatizzato, personalizzare dimensioni, stile ed esportare in formati aggiuntivi.

**Passaggi successivi**

* Esplora altri tipi di grafico (`ChartType.Column`, `ChartType.Pie`) per ampliare il tuo toolkit di reporting.
* Combina più grafici in una singola pagina chiamando `InsertChart` più volte.
* Integra dati da un database o file CSV per popolare le serie in modo dinamico.
* Consulta la documentazione di Aspose.Words per opzioni di formattazione avanzate come etichette dati condizionali e modelli di grafico.

Sentiti libero di sperimentare con il codice, regolare le dimensioni o sostituire i dati di esempio con metriche aziendali reali. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}