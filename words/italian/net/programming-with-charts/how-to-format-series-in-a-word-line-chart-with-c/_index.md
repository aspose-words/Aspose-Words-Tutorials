---
category: general
date: 2026-09-21
description: Come formattare le serie in un grafico a linee di Word usando C#. Impara
  a creare un documento Word, inserire un grafico a linee e applicare un formato numerico
  personalizzato.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format series
- create word document
- insert line chart
- add chart to word
- apply custom number format
language: it
lastmod: 2026-09-21
og_description: Come formattare le serie in un grafico a linee di Word usando C#.
  Questo tutorial ti mostra come creare un documento Word, inserire un grafico a linee
  e applicare un formato numerico personalizzato.
og_image_alt: Screenshot of a Word document showing a line chart with percentage‑formatted
  Y‑axis values
og_title: Come formattare le serie in un grafico a linee di Word con C# – guida passo
  passo
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: How to format series in a Word line chart using C#. Learn to create
    a Word document, insert a line chart, and apply a custom number format.
  headline: How to format series in a Word line chart with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart
- Word automation
title: Come formattare le serie in un grafico a linee di Word con C#
url: /it/net/programming-with-charts/how-to-format-series-in-a-word-line-chart-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come formattare le serie in un grafico a linee Word con C#

Se hai bisogno di **come formattare le serie** in un grafico a linee Word, questa guida ti fornisce una soluzione completa, pronta all'uso. Vedrai come **creare un documento Word**, **inserire un grafico a linee** e **applicare un formato numerico personalizzato** ai valori Y — tutto con Aspose.Words per .NET.

L'automazione di Word diventa semplice una volta compreso il modello a oggetti del grafico. Alla fine di questo tutorial avrai un file Word che contiene un grafico a linee i cui dati delle serie sono visualizzati come percentuali con due cifre decimali.

## Cosa otterrai

* Generare programmaticamente un file `.docx` vuoto.  
* Aggiungere un grafico a linee di dimensioni 400 × 300 punti.  
* Accedere alla prima serie di dati del grafico.  
* Applicare il codice di formato `#,##0.00%` in modo che i valori Y appaiano come percentuali.  

Non sono necessari strumenti esterni oltre al pacchetto NuGet di Aspose.Words.

## Prerequisiti

* SDK .NET 6.0 o successivo.  
* Visual Studio 2022 (o qualsiasi IDE C#).  
* Aspose.Words per .NET 23.10 o più recente – installa tramite `dotnet add package Aspose.Words`.  

Il codice funziona su Windows, Linux e macOS perché Aspose.Words è indipendente dalla piattaforma.

## Creare un documento Word con Aspose.Words

Il primo passo è istanziare un oggetto `Document`. Questo oggetto rappresenta l'intero file Word in memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document.
        Document doc = new Document();

        // The document currently has no content.
        // We will add a chart in the next step.
```

*Perché è importante*: `Document` è il punto di ingresso per tutte le operazioni di elaborazione Word. Senza di esso non è possibile aggiungere paragrafi, tabelle o grafici.

## Inserire un grafico a linee nel documento

Un `DocumentBuilder` scrive contenuto nel `Document`. Chiamare `InsertChart` crea una forma di grafico nella pagina corrente.

```csharp
        // Step 2: Initialize a DocumentBuilder to construct the document content.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a line chart with the desired size (400 × 300 points).
        Chart chart = builder.InsertChart(ChartType.Line, 400, 300);
```

*Perché è importante*: `InsertChart` restituisce un oggetto `Chart` che ti dà il pieno controllo su serie, assi e formattazione. I parametri di dimensione sono espressi in punti (1 punto = 1/72 pollice).

## Accedere alla prima serie di dati

Ogni grafico contiene una o più `ChartSeries`. La prima serie è all'indice 0.

```csharp
        // Step 4: Access the first data series of the chart.
        ChartSeries series = chart.Series[0];
```

*Perché è importante*: L'oggetto `ChartSeries` contiene i valori Y, i valori X e le opzioni di formattazione per una singola linea in un grafico a linee. Modificando questo oggetto si cambia la rappresentazione visiva dei dati.

## Applicare un formato numerico personalizzato alla serie

La proprietà `FormatCode` controlla come vengono visualizzati i valori numerici. Impostandola su `#,##0.00%` si indica a Word di trattare i valori come percentuali con due cifre decimali.

```csharp
        // Step 5: Apply a custom number format to the Y‑values.
        // This displays the numbers as percentages with two decimals.
        series.YValues.FormatCode = "#,##0.00%";

        // Optional: Populate the series with sample data.
        series.YValues.Add(0.15);
        series.YValues.Add(0.30);
        series.YValues.Add(0.45);
        series.YValues.Add(0.60);
```

*Perché è importante*: Senza un formato personalizzato, Word mostra numeri decimali grezzi (ad esempio `0.15`). Il codice di formato li converte in `15.00%`, che è spesso ciò che richiedono i report aziendali.

## Salvare il documento e verificare il risultato

```csharp
        // Save the document to the file system.
        string outputPath = "FormattedSeriesLineChart.docx";
        doc.Save(outputPath);
        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Quando apri `FormattedSeriesLineChart.docx` in Microsoft Word, vedrai un grafico a linee in cui le etichette dell'asse Y mostrano `15.00%`, `30.00%`, `45.00%` e `60.00%`. Le dimensioni del grafico corrispondono a quelle fornite in `InsertChart`.

### Screenshot dell'output previsto

> *Immagine: Una pagina di documento Word che mostra un grafico a linee con valori dell'asse Y formattati in percentuale.*  
> *(Testo alternativo: Screenshot di un documento Word che mostra un grafico a linee con valori dell'asse Y formattati in percentuale)*

## Variazioni comuni e casi limite

| Situazione | Regolazione |
|-----------|------------|
| **Serie multiple** | Itera su `chart.Series` e imposta `FormatCode` per ogni serie. |
| **Tipo di grafico diverso** | Sostituisci `ChartType.Line` con `ChartType.Column`, `ChartType.Pie`, ecc. |
| **Separatori specifici per locale** | Usa stringhe di formato consapevoli di `CultureInfo`, ad esempio `"# ##0,00 %"` per le impostazioni locali francesi. |
| **Fonte dati dinamica** | Popola `series.YValues` da un database o file CSV prima di applicare il formato. |

**Consiglio professionale:** Applica sempre il formato **dopo** aver aggiunto i valori Y. Cambiare il formato prima e poi aggiungere i valori funziona comunque, ma applicarlo più tardi garantisce che il formato sia applicato al set di dati finale.

## Riepilogo

Ora sai **come formattare le serie** in un grafico a linee Word usando C#. Il tutorial ha coperto:

* Creare un documento Word (`create word document`).  
* Inserire un grafico a linee (`insert line chart`, `add chart to word`).  
* Accedere alla prima serie del grafico.  
* Applicare un formato numerico personalizzato (`apply custom number format`) per visualizzare le percentuali.

## Prossimi passi

* Sperimenta con diversi valori di `ChartType` per vedere come si comportano altre visualizzazioni.  
* Aggiungi titoli, etichette degli assi e legende usando `chart.Title`, `chart.AxisX.Title` e `chart.AxisY.Title`.  
* Esporta il grafico come immagine (`chart.Save` con `SaveFormat.Png`) per l'uso nei report web.

Sentiti libero di adattare questo modello per generare dashboard, report finanziari o qualsiasi documento che richieda la creazione di grafici in modo programmatico. Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea un grafico a linee in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Inserisci un grafico a colonne in un documento Word](/words/english/net/programming-with-charts/insert-column-chart/)
- [Inserisci un grafico ad area in un documento Word | Aspose.Words per .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}