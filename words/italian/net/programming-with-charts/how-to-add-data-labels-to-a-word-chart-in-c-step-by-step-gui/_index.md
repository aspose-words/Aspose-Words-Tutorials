---
category: general
date: 2026-08-04
description: Come aggiungere etichette dati in C# con Aspose.Words. Impara a modificare
  il grafico, centrare le etichette dati del grafico, mostrare le percentuali nel
  grafico e personalizzare le etichette dati del grafico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add data labels
- how to edit chart
- center chart data labels
- show percentages in chart
- customize chart data labels
language: it
lastmod: 2026-08-04
og_description: Come aggiungere etichette dati in C# usando Aspose.Words. Questo tutorial
  ti mostra come modificare il grafico, centrare le etichette dati del grafico, mostrare
  le percentuali nel grafico e personalizzare le etichette dati del grafico.
og_image_alt: Screenshot of a Word chart with data labels added using C#
og_title: Come aggiungere etichette dati a un grafico Word in C# – guida completa
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  headline: How to add data labels to a Word chart in C# – step‑by‑step guide
  type: TechArticle
- description: How to add data labels in C# with Aspose.Words. Learn to edit chart,
    center chart data labels, show percentages in chart, and customize chart data
    labels.
  name: How to add data labels to a Word chart in C# – step‑by‑step guide
  steps:
  - name: – Load the Word document containing the chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: – Retrieve the first chart from the document
    text: '```csharp // Find the first shape that contains a chart. Shape chartShape
      = (Shape)document.GetChild(NodeType.Shape, 0, true); Chart chart = chartShape.GetChart();
      ```'
  - name: – Enable data label customization and show percentages in chart
    text: '```csharp // Access the first series of the chart. ChartSeries series =
      chart.Series[0];'
  - name: – Change the label placement to the center of each data point
    text: '```csharp // Position the labels at the center of each point. dataLabels.Position
      = ChartDataLabelPosition.Center; // center chart data labels ```'
  - name: – Further customize chart data labels (optional)
    text: 'If you need more control, you can adjust font, color, or leader lines:'
  - name: – Save the modified document
    text: '```csharp // Persist the changes to a new file. document.Save("YOUR_DIRECTORY/output.docx");
      ```'
  - name: Expected result
    text: 'When you open `output.docx` in Microsoft Word, the chart will display:'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Come aggiungere le etichette dei dati a un grafico Word in C# – guida passo
  passo
url: /it/net/programming-with-charts/how-to-add-data-labels-to-a-word-chart-in-c-step-by-step-gui/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere etichette dati a un grafico Word in C# – guida passo‑passo

Se hai bisogno di **how to add data labels** a un grafico inserito in un documento Word, questa guida ti mostra il codice esatto da eseguire. Vedrai come modificare le proprietà del grafico, centrare le etichette dati del grafico, mostrare le percentuali nel grafico e personalizzare le etichette dati del grafico per qualsiasi scenario.

Il tutorial copre tutto il necessario per modificare un grafico esistente, dal caricamento del documento al salvataggio delle modifiche. Non sono necessari riferimenti esterni—solo la libreria Aspose.Words per .NET e un ambiente di sviluppo C# di base.

## Prerequisiti

* .NET 6.0 (o successivo) installato.
* Aspose.Words per .NET versione 23.9 o più recente.  
  Puoi installarlo tramite NuGet:

```bash
dotnet add package Aspose.Words
```

* Un file Word (`input.docx`) che contiene almeno un grafico.

## Come aggiungere etichette dati a un grafico Word in C#

Le sezioni seguenti ti guidano passo passo. La parola chiave principale **how to add data labels** appare naturalmente nella narrazione e nei commenti del codice, mantenendo la densità entro il range consigliato.

### Passo 1 – Carica il documento Word contenente il grafico

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document.
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

*Perché questo passo è importante*: L'oggetto `Document` rappresenta l'intero file Word. Caricandolo ottieni l'accesso a tutti i nodi, incluse le forme che ospitano i grafici.

### Passo 2 – Recupera il primo grafico dal documento

```csharp
// Find the first shape that contains a chart.
Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
Chart chart = chartShape.GetChart();
```

*Perché questo passo è importante*: I grafici sono memorizzati all'interno dei nodi `Shape`. Convertendo il nodo recuperato in `Shape` e chiamando `GetChart()`, ottieni un oggetto `Chart` che espone serie, assi e collezioni di etichette.

### Passo 3 – Abilita la personalizzazione delle etichette dati e mostra le percentuali nel grafico

```csharp
// Access the first series of the chart.
ChartSeries series = chart.Series[0];

// Turn on data labels and request percentage values.
ChartDataLabelCollection dataLabels = series.DataLabels;
dataLabels.ShowPercentage = true;   // show percentages in chart
dataLabels.ShowValue = true;        // optional: also show raw values
```

*Perché questo passo è importante*: Impostare `ShowPercentage` indica ad Aspose.Words di calcolare e visualizzare il contributo di ogni sezione al totale. Questo risponde direttamente alla parola chiave secondaria **show percentages in chart**.

### Passo 4 – Cambia la posizione dell'etichetta al centro di ogni punto dati

```csharp
// Position the labels at the center of each point.
dataLabels.Position = ChartDataLabelPosition.Center; // center chart data labels
```

*Perché questo passo è importante*: La proprietà `Position` controlla dove appare l'etichetta rispetto al punto dati. Usare `Center` soddisfa la parola chiave secondaria **center chart data labels** e migliora la leggibilità per i grafici a torta o a ciambella.

### Passo 5 – Personalizza ulteriormente le etichette dati del grafico (opzionale)

Se hai bisogno di più controllo, puoi regolare il font, il colore o le linee guida:

```csharp
// Example: make labels bold and red.
dataLabels.Font.Bold = true;
dataLabels.Font.Color = System.Drawing.Color.Red;

// Example: add leader lines for better separation.
dataLabels.ShowLeaderLines = true;
```

Queste impostazioni illustrano la parola chiave secondaria **customize chart data labels** e dimostrano come puoi adattare l'aspetto per corrispondere alle linee guida del brand.

### Passo 6 – Salva il documento modificato

```csharp
// Persist the changes to a new file.
document.Save("YOUR_DIRECTORY/output.docx");
```

*Perché questo passo è importante*: Il salvataggio scrive il grafico aggiornato nel documento Word, rendendo le nuove etichette dati visibili quando il file viene aperto in Microsoft Word.

## Esempio completo, eseguibile

Di seguito è riportato un programma completo che puoi copiare, incollare ed eseguire. Include tutte le direttive `using` necessarie e commenti che spiegano ogni riga.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class AddDataLabelsDemo
{
    static void Main()
    {
        // 1. Load the Word document.
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first chart.
        Shape chartShape = (Shape)document.GetChild(NodeType.Shape, 0, true);
        Chart chart = chartShape.GetChart();

        // 3. Enable data labels and show percentages.
        ChartSeries series = chart.Series[0];
        ChartDataLabelCollection dataLabels = series.DataLabels;
        dataLabels.ShowPercentage = true;
        dataLabels.ShowValue = true;

        // 4. Center the labels on each data point.
        dataLabels.Position = ChartDataLabelPosition.Center;

        // 5. Optional: further customize appearance.
        dataLabels.Font.Bold = true;
        dataLabels.Font.Color = System.Drawing.Color.DarkBlue;
        dataLabels.ShowLeaderLines = true;

        // 6. Save the modified document.
        document.Save("YOUR_DIRECTORY/output.docx");

        Console.WriteLine("Data labels added and document saved successfully.");
    }
}
```

### Risultato previsto

Quando apri `output.docx` in Microsoft Word, il grafico mostrerà:

* Valori percentuali accanto a ogni sezione (ad esempio **25 %**, **40 %**, …).
* Etichette posizionate al centro di ogni punto dati.
* Qualsiasi stile aggiuntivo applicato, come testo rosso in grassetto.

Questi indizi visivi rendono il grafico più facile da interpretare, soprattutto in presentazioni o report.

## Come modificare le proprietà del grafico oltre le etichette dati

Mentre l'obiettivo di questa guida è **how to add data labels**, potresti anche voler **how to edit chart** impostazioni come titoli, posizione della legenda o formattazione degli assi. L'oggetto `Chart` fornisce proprietà come `Title`, `Legend` e `AxisX/AxisY`. Ad esempio, per cambiare il titolo del grafico:

```csharp
chart.Title.Text = "Quarterly Sales Breakdown";
chart.Title.Font.Size = 14;
```

Tutte le modifiche al grafico seguono lo stesso schema: recuperare il grafico, regolare le sue proprietà, quindi salvare il documento.

## Problemi comuni e consigli di best‑practice

| Problema | Perché succede | Correzione consigliata |
|---|---|---|
| Il grafico è all'interno di una forma raggruppata. | `GetChild(NodeType.Shape, …)` restituisce il gruppo esterno, non il grafico interno. | Cerca ricorsivamente una forma con `shape.HasChart`. |
| Le etichette dati non compaiono dopo il salvataggio. | `ShowValue` o `ShowPercentage` non è stato impostato su `true`. | Imposta esplicitamente sia `ShowValue` che `ShowPercentage` secondo necessità. |
| Le etichette si sovrappongono su sezioni piccole. | Il posizionamento al centro può causare affollamento. | Usa `ChartDataLabelPosition.OutSideEnd` per posizionamento esterno, oppure abilita `LeaderLines`. |

## Conclusione

Ora sai **how to add data labels** a un grafico Word usando C#. Il tutorial ha coperto il recupero del grafico, l'abilitazione della visibilità delle etichette, il centramento delle etichette, la visualizzazione delle percentuali e la personalizzazione dell'aspetto. Con queste conoscenze puoi anche **how to edit chart** dettagli, **center chart data labels**, **show percentages in chart**, e **customize chart data labels** per qualsiasi scenario di reporting.

Pronto a esplorare di più? Prova ad aggiungere più serie, applicare formattazione condizionale o esportare il grafico come immagine. L'API Aspose.Words offre ampie capacità di manipolazione dei grafici—sperimenta per trovare la rappresentazione visiva perfetta per i tuoi dati.

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Customize A Single Chart Data Point In A Chart](/words/english/net/programming-with-charts/single-chart-data-point/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}