---
category: general
date: 2026-08-10
description: Crea un documento Word con grafico a torta usando Aspose.Words. Scopri
  come inserire un grafico, personalizzare i colori del grafico a torta e modificare
  il colore di una fetta di torta in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- customize pie chart colors
- how to style pie
- how to insert chart
- change pie slice color
language: it
lastmod: 2026-08-10
og_description: Crea un documento Word con grafico a torta usando Aspose.Words. Questa
  guida spiega come inserire un grafico, personalizzare i colori del grafico a torta
  e modificare il colore di una fetta di torta in un'applicazione C#.
og_image_alt: Screenshot of a Word document containing a styled pie chart generated
  by Aspose.Words
og_title: Crea un documento Word con grafico a torta – Guida Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create pie chart Word document using Aspose.Words. Learn how to insert
    chart, customize pie chart colors, and change pie slice color in C#.
  headline: Create pie chart Word document with Aspose.Words
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, .NET
      6, and later. Just reference the same NuGet package.
    question: Does this work with .NET Core?
  - answer: Replace `ChartType.Pie` with `ChartType.Doughnut`. The same styling APIs
      (`Explosion`, `ForeColor`) apply.
    question: What if I need a donut chart instead of a pie?
  - answer: Open the existing file with `new Document("Existing.docx")`, create a
      `DocumentBuilder` for that document, and call `InsertChart` at the desired cursor
      position.
    question: Can I insert the chart into an existing document?
  - answer: 'Pie charts are best for a limited number of categories (typically < 10).
      For many categories, consider a bar or column chart instead. ## Full source
      code recap Below is the complete program in one block for easy copy‑paste: ```csharp
      using System; using System.Drawing; using Aspose.Words; using Aspo'
    question: How do I handle large datasets?
  type: FAQPage
tags:
- Aspose.Words
- C#
- pie chart
title: Crea un documento Word con grafico a torta usando Aspose.Words
url: /it/net/programming-with-charts/create-pie-chart-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word con grafico a torta usando Aspose.Words

Se hai bisogno di **creare un documento Word con grafico a torta** in modo programmatico, questo tutorial ti mostra esattamente come fare. Vedremo come inserire un grafico, **personalizzare i colori del grafico a torta** e **modificare il colore di una fetta** usando Aspose.Words per .NET.

Vedrai un esempio completo e eseguibile che potrai copiare in Visual Studio, eseguire e aprire immediatamente il *.docx* generato per verificare il grafico a torta stilizzato. Non è necessaria alcuna documentazione esterna: tutto ciò che ti serve è in questa guida.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o versioni successive installate  
* Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione temporanea)  
* Visual Studio 2022 (o qualsiasi IDE C#)  

Il codice utilizza solo gli spazi dei nomi `Aspose.Words` e `Aspose.Words.Drawing.Charts`, quindi non sono richiesti pacchetti NuGet aggiuntivi oltre alla libreria Aspose.Words.

## Crea documento Word con grafico a torta – esempio completo

Il seguente programma C# crea un nuovo documento Word, inserisce un grafico a torta, stilizza le prime due fette e salva il file. Ogni passaggio è spiegato in dettaglio.

```csharp
using System;
using System.Drawing;                // For Color
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Initialize a blank document and a DocumentBuilder.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a pie chart of size 400x300 points.
            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            // Step 3: Populate the chart with sample data (optional but makes the chart visible).
            // Aspose.Words creates an empty series by default; we add a series with three values.
            chart.Series.Clear(); // Remove the default empty series.
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30); // Slice 1
            series.DataPoints.Add(45); // Slice 2
            series.DataPoints.Add(25); // Slice 3

            // Step 4: Explode the first slice to emphasize it.
            series.Points[0].Explosion = 20; // 20% explosion makes the slice pop out.

            // Step 5: **Customize pie chart colors** – set the first two slices.
            series.Points[0].Format.Fill.ForeColor = Color.Orange; // Slice 1 color
            series.Points[1].Format.Fill.ForeColor = Color.Green;  // Slice 2 color

            // Step 6: **Change pie slice color** for any additional slices if needed.
            // Example: set the third slice to a custom blue.
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            // Step 7: Save the document containing the styled pie chart.
            string outputPath = @"PieChartStyled.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Spiegazione di ogni passaggio

| Passo | Cosa fa | Perché è importante |
|------|--------------|----------------|
| **1** | Crea un nuovo `Document` e un `DocumentBuilder`. | Il `DocumentBuilder` fornisce metodi fluent per inserire contenuti, come i grafici, nel file Word. |
| **2** | Chiama `InsertChart` con `ChartType.Pie` e una dimensione fissa. | `InsertChart` è il **metodo per inserire un grafico**; specificare larghezza/altezza garantisce che il grafico si adatti bene alla pagina. |
| **3** | Aggiunge una serie di dati con tre categorie e valori numerici. | Un grafico a torta senza dati è invisibile; popolarlo dimostra i passaggi di stilizzazione. |
| **4** | Imposta `Explosion` sul primo punto. | Esplodere una fetta attira l'attenzione su un segmento particolare—utile per evidenziare dati chiave. |
| **5** | Imposta `ForeColor` per i primi due punti. | Questo è il fulcro della **personalizzazione dei colori del grafico a torta**; puoi usare qualsiasi `System.Drawing.Color`. |
| **6** | Mostra come **modificare il colore di una fetta** per fette aggiuntive. | Dimostra che la stilizzazione non è limitata alle prime due fette; puoi colorare ogni fetta individualmente. |
| **7** | Salva il documento come `PieChartStyled.docx`. | L'output finale può essere aperto in Microsoft Word, Google Docs o qualsiasi visualizzatore compatibile. |

#### Output previsto

Aprendo `PieChartStyled.docx` si visualizza una singola pagina con un grafico a torta di 400 × 300 pt:

* La fetta 1 (arancione) è esplosa verso l'esterno.  
* La fetta 2 (verde) appare accanto alla fetta esplosa.  
* La fetta 3 (blu acciaio) riempie il segmento rimanente.

Il grafico riflette i valori dei dati (30, 45, 25) e i colori personalizzati che hai definito.

## Come stilizzare la torta – consigli aggiuntivi

* **Usa i colori del tema** – invece di codificare `Color.Orange`, puoi prelevare i colori dal tema del documento:  
  ```csharp
  chart.Series[0].Points[0].Format.Fill.ForeColor = doc.Theme.ColorScheme.Accent1;
  ```
* **Aggiungi etichette dati** – se vuoi visualizzare le percentuali sul grafico:  
  ```csharp
  chart.HasDataLabel = true;
  chart.DataLabel.NumberFormat = "#%";
  ```
* **Ridimensiona dinamicamente** – calcola la dimensione del grafico in base ai margini della pagina:  
  ```csharp
  double width = doc.PageSetup.PageWidth - doc.PageSetup.LeftMargin - doc.PageSetup.RightMargin;
  double height = width * 0.75; // 4:3 aspect ratio
  builder.InsertChart(ChartType.Pie, width, height);
  ```

Queste varianti dimostrano la flessibilità del **come stilizzare la torta** oltre l'esempio base.

## Domande frequenti

**D: Funziona con .NET Core?**  
R: Sì. Aspose.Words per .NET è compatibile con .NET Core, .NET 5, .NET 6 e versioni successive. Basta fare riferimento allo stesso pacchetto NuGet.

**D: E se avessi bisogno di un grafico a ciambella invece di una torta?**  
R: Sostituisci `ChartType.Pie` con `ChartType.Doughnut`. Le stesse API di stilizzazione (`Explosion`, `ForeColor`) si applicano.

**D: Posso inserire il grafico in un documento esistente?**  
R: Apri il file esistente con `new Document("Existing.docx")`, crea un `DocumentBuilder` per quel documento e chiama `InsertChart` nella posizione desiderata del cursore.

**D: Come gestire dataset di grandi dimensioni?**  
R: I grafici a torta sono migliori per un numero limitato di categorie (tipicamente < 10). Per molte categorie, considera un grafico a barre o a colonne.

## Riepilogo del codice sorgente completo

Di seguito trovi il programma completo in un unico blocco per un facile copia‑incolla:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartWordDemo
{
    class Program
    {
        static void Main()
        {
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            Chart chart = builder.InsertChart(ChartType.Pie, 400, 300).Chart;

            chart.Series.Clear();
            ChartSeries series = chart.Series.Add("Sales", new[] { "Product A", "Product B", "Product C" });
            series.DataPoints.Add(30);
            series.DataPoints.Add(45);
            series.DataPoints.Add(25);

            series.Points[0].Explosion = 20;
            series.Points[0].Format.Fill.ForeColor = Color.Orange;
            series.Points[1].Format.Fill.ForeColor = Color.Green;
            series.Points[2].Format.Fill.ForeColor = Color.SteelBlue;

            doc.Save("PieChartStyled.docx");
            Console.WriteLine("Document saved as PieChartStyled.docx");
        }
    }
}
```

Eseguendo questo codice otterrai il documento Word con il grafico a torta stilizzato descritto in precedenza.

## Conclusione

Ora sai come **creare documenti Word con grafico a torta** usando Aspose.Words, **personalizzare i colori del grafico a torta** e **modificare il colore di una fetta** in modo programmatico. La guida ha coperto l'inserimento del grafico, il popolamento dei dati, l'esplosione di una fetta, l'applicazione di colori personalizzati e il salvataggio del risultato.  

Da qui puoi esplorare argomenti correlati come **come inserire altri tipi di grafico**, aggiungere legende o generare report multi‑pagina con più grafici. Sperimenta con diverse combinazioni di colori e set di dati per adattare i report alle tue esigenze.

Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}