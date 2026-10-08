---
category: general
date: 2026-10-07
description: Impara come creare un documento Word e inserire un grafico a torta usando
  Aspose.Words in C#. La guida mostra anche come generare un file Word con etichette
  di grafico personalizzate.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- generate word file
- customize pie chart
- how to add pie chart
language: it
lastmod: 2026-10-07
og_description: Crea un documento Word e inserisci un grafico a torta in C#. Segui
  questa guida passo‑passo per generare un file Word con etichette del grafico completamente
  personalizzate.
og_image_alt: Screenshot of a Word document that contains a customized pie chart created
  with C#
og_title: Crea un documento Word con un grafico a torta personalizzato in C#
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to create word document and insert pie chart using Aspose.Words
    in C#. The guide also shows how to generate word file with custom chart labels.
  headline: How to create word document with a customized pie chart in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- Chart
title: Come creare un documento Word con un grafico a torta personalizzato in C#
url: /it/net/programming-with-charts/how-to-create-word-document-with-a-customized-pie-chart-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word con un grafico a torta personalizzato in C#

Se hai bisogno di **create word document** programmaticamente, questo tutorial ti mostra come **insert pie chart** e personalizzare le sue etichette dei dati usando Aspose.Words per .NET. Imparerai anche come **generate word file** che contiene un grafico completamente stilizzato, coprendo tutto, dalla configurazione del progetto al salvataggio del documento finale.

La guida percorre ogni passaggio necessario per aggiungere un grafico, regolare le posizioni delle etichette, abilitare le linee guida e infine salvare il risultato come file `.docx`. Non sono necessari strumenti esterni oltre alla libreria Aspose.Words, e il codice sorgente completo è fornito così puoi copiarlo, incollarlo ed eseguirlo immediatamente.

## Prerequisiti

* .NET 6.0 SDK o versioni successive installate  
* Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione gratuita)  
* Un IDE come Visual Studio 2022 o Visual Studio Code  

Dovrai inoltre aggiungere i seguenti pacchetti NuGet al tuo progetto:

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.Drawing.Charts
```

Questi pacchetti espongono le classi `Document`, `DocumentBuilder` e le classi correlate ai grafici utilizzate negli esempi seguenti.

## Crea documento Word e aggiungi un grafico

Il primo passo è **create word document** e ottenere un `DocumentBuilder` che ti permette di inserire contenuti. Il builder funziona come un cursore posizionato all'interno del documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

L'oggetto `Document` rappresenta l'intero file Word, mentre il `DocumentBuilder` fornisce metodi come `InsertChart` che inseriscono oggetti direttamente nel flusso del documento.

## Inserisci un grafico a torta nel documento

Ora che il builder è pronto, puoi **insert pie chart** con una dimensione specifica. Il grafico viene aggiunto nella posizione corrente del builder.

```csharp
        // Step 3: Insert a pie chart with the desired size (400x300 points)
        Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

        // Populate the chart with sample data
        pieChart.Series.Clear();
        ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                                new[] { 25.0, 35.0, 20.0, 20.0 });
```

`InsertChart` restituisce un oggetto `Chart` che puoi manipolare ulteriormente. I dati di esempio creano quattro sezioni che rappresentano le vendite trimestrali.

## Personalizza le etichette dei dati del grafico a torta

Per rendere il grafico più leggibile, spesso è necessario **customize pie chart** le etichette—posizionarle al di fuori delle sezioni e mostrare le linee guida. È qui che entra in gioco `ChartDataLabelCollection`.

```csharp
        // Step 4: Get the data label collection of the first series
        ChartDataLabelCollection dataLabels = pieChart.Series[0].DataLabels;

        // Step 5: Position the data labels outside each slice
        dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

        // Step 6: Enable leader lines for clearer label connections
        dataLabels.ShowLeaderLines = true;

        // Optional: Show the actual value and percentage
        dataLabels.ShowValue = true;
        dataLabels.ShowPercentage = true;
```

Impostare `Position` su `OutsideEnd` sposta ogni etichetta oltre il bordo della sezione, mentre `ShowLeaderLines` disegna una linea che collega l'etichetta alla sua sezione. Le flag opzionali `ShowValue` e `ShowPercentage` forniscono ai lettori sia i numeri grezzi sia le percentuali relative.

**Suggerimento professionale:** Se hai bisogno di formattare il carattere dell'etichetta, usa `dataLabels.Font` per impostare dimensione, colore e stile. Questo garantisce che il grafico corrisponda al branding aziendale.

## Salva e genera il file Word

Dopo che il grafico è completamente configurato, puoi **generate word file** salvando l'istanza `Document` su disco. Scegli il formato `.docx` per la massima compatibilità con le versioni moderne di Word.

```csharp
        // Step 7: Save the document with the customized chart
        string outputPath = @"C:\Temp\CustomPieChart.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Quando apri `CustomPieChart.docx`, vedrai un grafico a torta con quattro sezioni, ciascuna etichettata al di fuori della sezione, collegata da linee guida e che mostra sia il valore che la percentuale.

![Screenshot di un documento Word che contiene un grafico a torta personalizzato creato con C#](image-placeholder.png)

*L'immagine mostra il risultato finale del tutorial **create word document**.*

## Varianti comuni e casi limite

| Scenario | Come adattare il codice |
|----------|------------------------|
| **Serie multiple** | Aggiungi oggetti `ChartSeries` aggiuntivi a `pieChart.Series`. Ogni serie può avere la propria collezione `DataLabels` per uno styling indipendente. |
| **Dimensione del grafico diversa** | Modifica i parametri di larghezza e altezza in `InsertChart(width, height)`. I valori sono in punti (1 pt ≈ 1/72 in). |
| **Titolo del grafico** | Usa `pieChart.Title.Text = "Quarterly Sales"` per aggiungere un titolo descrittivo. |
| **Esporta in PDF** | Chiama `document.Save("Report.pdf", SaveFormat.Pdf);` dopo che il grafico è stato creato. |
| **Gestione della licenza** | Posiziona il tuo file di licenza (`Aspose.Words.lic`) nella cartella dell'applicazione e caricalo con `new License().SetLicense("Aspose.Words.lic");` prima di creare il documento. |

Queste varianti ti permettono di rispondere alla domanda **how to add pie chart** in molti scenari reali, dai report semplici ai dashboard complessi.

## Conclusione

Ora sai come **create word document**, **insert pie chart** e **customize pie chart** le etichette usando Aspose.Words per .NET. L'esempio completo dimostra un flusso di lavoro pulito: inizializzare il documento, aggiungere un grafico, regolare il posizionamento delle etichette dei dati, abilitare le linee guida e infine **generate word file** che può essere condiviso con chiunque.

Prova ad estendere questo tutorial sperimentando con diversi tipi di grafico (`ChartType.Column`, `ChartType.Line`) o applicando palette di colori personalizzate per abbinare il tuo brand. Se incontri problemi, consulta la documentazione di Aspose.Words o esplora argomenti correlati come “how to add pie chart” con serie multiple e fonti di dati dinamiche.

Buon coding, e sentiti libero di condividere i tuoi risultati o fare domande di follow‑up nei commenti!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)
- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}