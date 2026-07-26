---
category: general
date: 2026-07-26
description: Inserisci un grafico a torta in un documento Word usando Aspose.Words.
  Scopri come aggiungere il grafico, far esplodere una fetta e mostrare le percentuali
  in pochi passaggi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to add chart
- how to explode slice
- add chart to word
- how to show percentages
language: it
lastmod: 2026-07-26
og_description: Inserisci un grafico a torta in un file Word con Aspose.Words. Segui
  questa guida per imparare come aggiungere il grafico, far esplodere una fetta e
  mostrare rapidamente le percentuali.
og_image_alt: Screenshot illustrating insert pie chart in a Word document
og_title: Inserisci un grafico a torta in Word – Tutorial passo passo di Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert pie chart into a Word document using Aspose.Words. Learn how
    to add chart, explode slice, and show percentages in just a few steps.
  headline: Insert Pie Chart in Word with Aspose.Words – Complete Guide
  type: TechArticle
- questions:
  - answer: Just add additional `ChartSeries` objects to `chart.Series`. Each series
      can have its own data set, colors, and explode settings.
    question: What if I need more than one series?
  - answer: Yes. Each `ChartPoint` has a `Format.Fill.ForeColor` property you can
      set to any `System.Drawing.Color`.
    question: Can I change the chart’s colors?
  - answer: The `ChartType` enum includes bar, line, doughnut, and many more. Swap
      `ChartType.Pie` for whichever visual you need.
    question: What about different chart types?
  - answer: Absolutely. Word treats the chart as a native Office chart, so users can
      double‑click it to open the built‑in chart editor.
    question: Is the chart editable in Word after insertion?
  type: FAQPage
tags:
- Aspose.Words
- Chart Automation
- .NET Development
title: Inserire un grafico a torta in Word con Aspose.Words – Guida completa
url: /it/java/using-document-elements/insert-pie-chart-in-word-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserire un grafico a torta in Word con Aspose.Words – Guida completa

Ti è mai capitato di dover **inserire un grafico a torta** in un report Word ma non sapevi da dove cominciare? Non sei l’unico. In molte applicazioni aziendali l’impatto visivo di un grafico a torta rende i dati immediatamente digeribili, e Aspose.Words lo rende possibile con poche righe di codice.

In questo tutorial percorreremo passo passo le operazioni per **aggiungere un grafico a Word**, far “esplodere” una fetta per enfatizzarla e mostrare le percentuali sulle etichette dei dati. Alla fine avrai un esempio pronto da eseguire che potrai inserire in qualsiasi progetto .NET.

---

## Prerequisiti

Prima di iniziare, assicurati di avere:

- .NET 6.0 o versioni successive (il codice funziona sia con .NET Core che con .NET Framework)
- Il pacchetto NuGet Aspose.Words for .NET installato  
  ```bash
  dotnet add package Aspose.Words
  ```
- Una conoscenza di base della sintassi C# — nulla di complesso
- Un IDE a tua scelta (Visual Studio, Rider o VS Code)

Tutto qui. Mettiamoci al lavoro.

---

## Inserire un grafico a torta in un documento Word

La prima cosa di cui abbiamo bisogno è un nuovo oggetto `Document` e un `DocumentBuilder`. Pensa al builder come a una penna che scrive direttamente sulla tela di Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
using Aspose.Words.Charts;

// Step 1: Create a new document and a builder to work with it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Perché è importante:** Il `Document` rappresenta l’intero file .docx, mentre il `DocumentBuilder` fornisce un’API comoda per inserire elementi come grafici, tabelle e testo. Questa è la base per ogni operazione **how to add chart**.

---

## Come aggiungere un grafico a Word

Ora che abbiamo un builder, possiamo davvero **inserire un grafico a torta**. Il metodo `insertChart` accetta il tipo di grafico e le dimensioni desiderate in punti (1 punto = 1/72 di pollice).

```csharp
// Step 2: Insert a pie chart of size 400x300 points
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

> **Suggerimento:** Se ti serve una dimensione diversa, modifica semplicemente i valori di larghezza e altezza. Il grafico verrà ridimensionato automaticamente per adattarsi ai margini della pagina.

---

## Come far “esplodere” una fetta per enfatizzare

Una modifica visiva comune è “esplodere” una fetta così che spunti fuori dal cerchio. Questo attira l’occhio del lettore verso la sezione più importante.

```csharp
// Step 3: Access the first series (the data set)
ChartSeries series = chart.Series[0];

// Step 4: Explode the first slice to emphasize it
series.Points[0].Exploded = true;
```

> **Perché far esplodere una fetta?** Quando vuoi evidenziare una categoria particolare — ad esempio, “Ricavi Q1” in un report finanziario — far esplodere la fetta la rende immediatamente visibile senza aggiungere testo extra.

---

## Come mostrare le percentuali sulle etichette dei dati

La maggior parte dei grafici a torta appare migliore quando ogni fetta visualizza la sua percentuale. Aspose.Words consente di attivare questa opzione con una singola proprietà.

```csharp
// Step 5: Show percentages on the data labels of the first series
series.DataLabelFormat.ShowPercentage = true;
```

> **Nota veloce:** Il flag `ShowPercentage` funziona per tutti i punti della serie, quindi non è necessario impostarlo per ogni fetta.

---

## Salvare il documento contenente il grafico

Infine, scriviamo il documento su disco. Scegli qualsiasi cartella ti piaccia; assicurati solo che il percorso esista.

```csharp
// Step 6: Save the document containing the chart
doc.Save(@"C:\Temp\PieChart.docx");
```

Quando apri `PieChart.docx` in Microsoft Word vedrai un grafico a torta perfettamente renderizzato con la prima fetta esplosa e le percentuali visualizzate — esattamente ciò che ti aspetti da un report aziendale curato.

---

## Esempio completo funzionante

Di seguito trovi il programma completo, pronto per il copia‑incolla. Eseguilo come applicazione console e verifica il file di output.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Create a new document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a pie chart (400x300 points)
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data
            ChartSeries series = chart.Series[0];
            series.Name = "Sales Q1";
            series.Add(30); // Product A
            series.Add(45); // Product B
            series.Add(25); // Product C

            // Explode the first slice (Product A)
            series.Points[0].Exploded = true;

            // Show percentages on data labels
            series.DataLabelFormat.ShowPercentage = true;

            // Save the document
            string outputPath = @"C:\Temp\PieChart.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Risultato atteso:** Apri il `PieChart.docx` generato. Vedrai un grafico a torta a tre fette intitolato “Sales Q1”, con la prima fetta estratta e ogni fetta etichettata “30 %”, “45 %” e “25 %”. L’aspetto visivo corrisponde ai dati inseriti.

---

## Domande frequenti e casi particolari

- **E se avessi bisogno di più di una serie?**  
  Aggiungi semplicemente oggetti `ChartSeries` aggiuntivi a `chart.Series`. Ogni serie può avere il proprio set di dati, colori e impostazioni di esplosione.

- **Posso cambiare i colori del grafico?**  
  Sì. Ogni `ChartPoint` dispone della proprietà `Format.Fill.ForeColor` che puoi impostare su qualsiasi `System.Drawing.Color`.

- **E per altri tipi di grafico?**  
  L’enumerazione `ChartType` include barre, linee, ciambelle e molti altri. Sostituisci `ChartType.Pie` con il tipo di visualizzazione che ti serve.

- **Il grafico è modificabile in Word dopo l’inserimento?**  
  Assolutamente. Word tratta il grafico come un grafico Office nativo, quindi gli utenti possono fare doppio clic per aprire l’editor di grafico integrato.

---

## Conclusione

Ora sai esattamente come **inserire un grafico a torta** in un documento Word usando Aspose.Words, **come aggiungere un grafico a Word**, **come far esplodere una fetta** e **come mostrare le percentuali** sulle etichette dei dati. L’esempio completo sopra è pronto per l’esecuzione e puoi estenderlo con dati personalizzati, stili o serie aggiuntive.

Pronto per il passo successivo? Prova a sostituire il grafico a torta con una ciambella, o genera un batch di report con set di dati diversi in modo automatico. Se sei curioso di altre visualizzazioni, consulta le nostre guide su **how to add chart** per grafici a barre e linee, o esplora il riferimento API **add chart to word** per personalizzazioni più approfondite.

Buona programmazione, e che i tuoi documenti siano sempre chiari come una torta perfettamente tagliata!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}