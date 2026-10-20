---
category: general
date: 2026-10-20
description: Crea un grafico a torta in un documento Word utilizzando Aspose.Words
  – guida passo‑passo che mostra come impostare il colore, separare una fetta e salvare
  il documento Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- save word document
- how to create chart
- how to explode slice
- how to set color
language: it
lastmod: 2026-10-20
og_description: Crea un grafico a torta in un documento Word con Aspose.Words. Scopri
  come impostare il colore, separare una fetta e salvare il documento Word in un unico
  esempio eseguibile.
og_image_alt: Screenshot of a Word document containing a customized pie chart with
  an exploded red slice
og_title: Crea un grafico a torta in un documento Word – guida completa C#
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create pie chart in a Word document using Aspose.Words – step‑by‑step
    guide that shows how to set color, explode slice, and save Word document.
  headline: How to create pie chart in a Word document with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart automation
title: Come creare un grafico a torta in un documento Word con Aspose.Words
url: /it/java/images-shapes/how-to-create-pie-chart-in-a-word-document-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico a torta in un documento Word con Aspose.Words

Se hai bisogno di **creare un grafico a torta** all'interno di un file Word, questa guida ti mostra esattamente come farlo. Vedrai come impostare un colore personalizzato, far esplodere una fetta per enfatizzarla e, infine, **salvare il documento Word** con il grafico incorporato.

Generare grafici programmaticamente elimina i passaggi manuali di apertura di Word, inserimento di un grafico e regolazione della sua apparizione. Alla fine di questo tutorial avrai un'applicazione console C# completa e funzionante che crea un grafico a torta, lo personalizza e scrive il risultato su disco.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o versioni successive installate  
* Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione gratuita)  
* Un IDE come Visual Studio 2022 o VS Code  

Non sono richiesti pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Come creare un grafico a torta in un documento Word

Il primo passo è istanziare un `Document` e un `DocumentBuilder`. Il builder ti dà accesso alle funzionalità di alto livello di Word, inclusa l'inserzione di grafici.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a blank document and a builder.
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Step 2: Insert a 400x300‑point pie chart.
            Chart pieChart = builder.InsertChart(ChartType.Pie, 400, 300);

            // Populate the chart with sample data.
            // Series 0, Category 0‑2 correspond to three slices.
            pieChart.Series[0].DataPoints.Clear();
            pieChart.Series[0].DataPoints.Add(30); // Slice A
            pieChart.Series[0].DataPoints.Add(45); // Slice B
            pieChart.Series[0].DataPoints.Add(25); // Slice C

            // The chart is now part of the document; further customization follows.
```

A questo punto il documento contiene già un grafico a torta di base. Le sezioni successive spiegano **come far esplodere una fetta**, **come impostare il colore** e **come salvare il documento Word**.

## Come far esplodere una fetta per enfatizzare

Far esplodere una fetta la separa dal resto della torta, attirando l'occhio del lettore. L'API Aspose.Words ti consente di specificare una distanza di esplosione in punti.

```csharp
            // Step 3: Explode the first slice (index 0) by 20 points.
            // This moves the slice outward while keeping the rest of the chart intact.
            pieChart.Series[0].SetExplosion(0, 20);
```

Perché far esplodere la fetta? Nei report che evidenziano una categoria particolare — ad esempio “Prodotto più venduto” — la separazione visiva rende il punto dati immediatamente riconoscibile.

## Come impostare il colore su una fetta del grafico

I colori personalizzati migliorano la coerenza del brand e la leggibilità. Puoi assegnare qualsiasi `System.Drawing.Color` a un punto dati specifico.

```csharp
            // Step 4: Apply a red fill to the same slice we just exploded.
            // The Fill property controls the interior color of the slice.
            pieChart.Series[0].DataPoints[0].Fill.ForeColor = Color.Red;
```

Non sei limitato ai colori predefiniti; puoi creare un valore `Color.FromArgb` per tonalità precise.

## Come salvare il documento Word con il grafico

Una volta che il grafico ha l'aspetto desiderato, persistere il file è semplice. Il metodo `Document.Save` scrive il documento nel formato che specifichi — qui usiamo il default `.docx`.

```csharp
            // Step 5: Save the document to the desired location.
            string outputPath = @"C:\Temp\PieChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Eseguendo il programma viene creato `PieChart.docx`. Aprendo il file in Microsoft Word si vede un grafico a torta in cui la prima fetta è esplosa e colorata di rosso, esattamente come specificato nel codice.

### Risultato atteso

* Un file Word chiamato **PieChart.docx** in `C:\Temp`.  
* Il documento contiene un unico grafico a torta, di dimensioni 400 × 300 punti.  
* La fetta 0 è spostata di 20 punti e riempita di rosso, mentre le altre fette mantengono il colore predefinito.  

Puoi verificare l'esplosione e il colore selezionando il grafico in Word e ispezionando le proprietà della fetta.

## Suggerimenti professionali e ostacoli comuni

* **Suggerimento pro:** Se devi modificare il titolo o la legenda del grafico, usa le proprietà `pieChart.Title.Text` e `pieChart.Legend` prima di salvare.  
* **Attenzione a:** Dimenticare di cancellare i punti dati predefiniti può generare fette extra e indesiderate. Chiama sempre `Series[0].DataPoints.Clear()` prima di aggiungere i tuoi dati.  
* **Consiglio sulle prestazioni:** Per documenti di grandi dimensioni, riutilizza una singola istanza di `DocumentBuilder` invece di crearne molte; questo riduce il consumo di memoria.

## Come creare un grafico usando Aspose.Words (contesto aggiuntivo)

Il metodo `InsertChart` supporta molti tipi di grafico oltre ai grafici a torta, come colonne, linee e aree. Per passare a un tipo diverso, sostituisci `ChartType.Pie` con il valore enum desiderato, ad esempio `ChartType.Column`. Il resto dei passaggi di personalizzazione (esplosione delle fette, impostazione dei colori) segue lo stesso schema, anche se non tutti i tipi di grafico espongono una proprietà “explosion”.

## Come far esplodere una fetta in altri tipi di grafico

Solo i grafici di tipo torta espongono il metodo `SetExplosion`. Se provi a chiamarlo su un grafico a barre, l'API genera un `ArgumentException`. In quei casi, considera l'uso di etichette dati o callout per evidenziare una barra particolare.

## Come impostare il colore su una serie invece che su una singola fetta

Se vuoi che tutte le fette di una serie condividano lo stesso colore, itera sui punti dati:

```csharp
foreach (ChartDataPoint point in pieChart.Series[0].DataPoints)
{
    point.Fill.ForeColor = Color.Blue;
}
```

Questo approccio è utile quando hai bisogno di uno schema di colore uniforme su più grafici.

## Come salvare il documento Word in altri formati

Aspose.Words può esportare in PDF, HTML e molti altri formati. Cambia l'estensione del file in `Save` e, facoltativamente, passa un oggetto `SaveOptions`:

```csharp
document.Save(@"C:\Temp\PieChart.pdf", SaveFormat.Pdf);
```

Il motore di rendering del grafico converte automaticamente il grafico nel formato di destinazione, preservando colori e impostazioni di esplosione.

## Conclusione

Ora sai come **creare un grafico a torta** in un documento Word, personalizzarne l'aspetto **esplodendo una fetta** e **impostando il colore**, e infine **salvare il documento Word** con il grafico incorporato. Questo esempio end‑to‑end ti fornisce una solida base per automatizzare la generazione di report, dashboard o qualsiasi scenario in cui sia necessario inserire dati visuali programmaticamente.

### Prossimi passi

* Esplora altri tipi di grafico (`ChartType.Column`, `ChartType.Line`) per ampliare il tuo toolkit di reporting.  
* Combina più grafici in un unico documento per costruire dashboard complete.  
* Sperimenta con `ChartDataLabel` per mostrare percentuali o valori direttamente sulle fette.  

Sentiti libero di adattare il codice alle tue fonti dati — che tu estragga valori da un database, da un'API o da un file CSV, lo stesso flusso di lavoro Aspose.Words si applica. Buon lavoro con i grafici!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Explode Pie Chart Slice in C# with Aspose.Words – Full Guide](/words/english/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/)
- [Insert Custom Column Chart in Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/insert-custom-chart/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}