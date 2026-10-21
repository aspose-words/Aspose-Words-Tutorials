---
category: general
date: 2026-07-29
description: Come modificare un grafico in un documento Word—impara a cambiare la
  posizione dell'etichetta del grafico, regolare le etichette del grafico a barre,
  modificare le etichette dei dati del grafico e cambiare il carattere dell'etichetta
  del grafico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- change chart label position
- adjust bar chart labels
- modify chart data labels
- change chart label font
language: it
lastmod: 2026-07-29
og_description: Come modificare rapidamente un grafico in Word. Impara a cambiare
  la posizione delle etichette del grafico, a regolare le etichette dei grafici a
  barre, a modificare le etichette dei dati del grafico e a cambiare il carattere
  delle etichette del grafico.
og_image_alt: Screenshot of a Word bar chart with custom label positions and larger
  font size
og_title: Come modificare il grafico in Word – Cambiare etichette e carattere
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  headline: 'How to Edit Chart in Word: Change Label Position, Font & More'
  type: TechArticle
- description: How to edit chart in a Word document—learn to change chart label position,
    adjust bar chart labels, modify chart data labels, and change chart label font.
  name: 'How to Edit Chart in Word: Change Label Position, Font & More'
  steps:
  - name: What if the document contains multiple charts?
    text: 'The code above grabs the *first* chart (`GetChild(NodeType.Shape, 0, true)`).
      To edit all charts, replace the single retrieval with a loop:'
  - name: How to **change chart label font** for a specific series only?
    text: 'Each `ChartSeries` has its own `DataLabelCollection`. Target a series by
      index:'
  - name: Does this work with pie or line charts?
    text: Yes—`ChartDataLabelPosition` supports values like `InsideEnd`, `OutsideEnd`,
      and `BestFit`. For a pie chart you might prefer `OutsideEnd` to keep labels
      readable.
  - name: What about localization (e.g., different decimal separators)?
    text: Aspose.Words respects the document’s locale settings. If you need to enforce
      a specific format, adjust `label.NumberFormat` before saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: 'Come modificare un grafico in Word: modifica la posizione delle etichette,
  il carattere e altro'
url: /it/net/working-with-charts/how-to-edit-chart-in-word-change-label-position-font-more/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come modificare un grafico in Word: cambiare la posizione dell'etichetta, il carattere e altro

Modificare un grafico in un documento Word è una necessità comune quando vuoi che i tuoi report abbiano un aspetto curato. Hai mai faticato a **cambiare la posizione dell'etichetta del grafico** o a rendere le etichette leggibili senza dover setacciare menu infiniti? Non sei solo: la maggior parte degli sviluppatori si imbatte in questo ostacolo quando automatizza la generazione di report. In questa guida percorreremo un esempio completo e funzionante che mostra esattamente come **regolare le etichette di un grafico a barre**, **modificare le etichette dei dati del grafico** e **cambiare il carattere delle etichette del grafico** usando C# e la libreria Aspose.Words.

## Cosa imparerai

- Caricare un file .docx che contiene già un grafico a barre.  
- Recuperare la prima forma grafico e accedere alla sua collezione di etichette dati.  
- **Cambiare la posizione dell'etichetta del grafico** per rendere le barre più pulite.  
- **Regolare la dimensione del carattere delle etichette del grafico a barre** per una migliore leggibilità.  
- Salvare il documento modificato su disco.  

Nessuno strumento esterno, nessun passaggio manuale nell'interfaccia—solo puro codice che puoi inserire in qualsiasi progetto .NET. Alla fine avrai una soluzione autonoma riutilizzabile in decine di documenti.

> **Prerequisiti**  
> - .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.7+).  
> - Aspose.Words for .NET (disponibile via NuGet).  
> - Un file Word (`BarChart.docx`) che contiene già un grafico a barre.  

Se ti manca qualcuno di questi, scarica subito l'ultimo pacchetto Aspose.Words:

```bash
dotnet add package Aspose.Words
```

---

## Come modificare un grafico: recuperare il grafico dal documento Word

Il primo passo in **come modificare un grafico** è caricare il documento e individuare la forma grafico. Aspose.Words tratta i grafici come nodi `Shape`, quindi possiamo usare `GetChild` con `NodeType.Shape` per ottenere il primo grafico che troviamo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the Word document that contains a chart
Document document = new Document(@"C:\Temp\BarChart.docx");

// Retrieve the first chart shape from the document
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
```

> **Perché è importante:**  
> Accedendo direttamente all'oggetto `Chart`, eviti l'overhead di aprire il file in Word e di regolare manualmente ogni etichetta. Questo è il fondamento di qualsiasi automazione di **modifica delle etichette dei dati del grafico**.

## Regolare le etichette del grafico a barre: cambiare la posizione dell'etichetta del grafico

Ora che abbiamo l'istanza `Chart`, iteriamo sulla sua `DataLabelCollection`. L'obiettivo è **cambiare la posizione dell'etichetta del grafico** in modo che ogni etichetta si trovi comodamente alla base della barra, anziché fluttuare sopra di essa.

```csharp
// Loop through each data label in the chart
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Place label inside the base of the bar
    dataLabel.Position = ChartDataLabelPosition.InsideBase;
}
```

> **Consiglio professionale:**  
> `InsideBase` funziona bene per i grafici a barre verticali. Se lavori con un grafico a barre orizzontali, prova `InsideEnd`. Sperimentare le posizioni è semplice—basta rieseguire il codice e aprire il documento salvato.

## Cambiare il carattere dell'etichetta del grafico: regolare la dimensione per leggibilità

Un carattere minuscolo è il killer silenzioso della chiarezza dei report. Per **cambiare il carattere dell'etichetta del grafico**, imposta semplicemente la proprietà `Font.Size` su ogni `ChartDataLabel`. Lo aumenteremo a 9 pt, che è un valore ottimale per la maggior parte dei report stampati.

```csharp
foreach (ChartDataLabel dataLabel in chart.DataLabelCollection)
{
    // Set a readable font size (9 points)
    dataLabel.Font.Size = 9;
}
```

> **Perché lo facciamo:**  
> Regolare la dimensione del carattere fa parte delle migliori pratiche di **modifica delle etichette dei dati del grafico**. Caratteri più grandi migliorano l'accessibilità e riducono la necessità di post‑processing manuale.

## Salvare il documento aggiornato

Dopo aver sistemato posizioni e caratteri, l'ultimo passo in **come modificare un grafico** è persistere le modifiche. Aspose.Words lo rende un'operazione a una riga.

```csharp
// Save the modified document with new label settings
document.Save(@"C:\Temp\BarChartCustomLabels.docx");
```

Apri `BarChartCustomLabels.docx` in Word e vedrai le etichette ben inserite all'interno delle barre, renderizzate con un chiaro carattere da 9 pt. Niente più sforzi per leggere numeri minuscoli.

---

## Esempio completo funzionante (tutti i passaggi in un unico file)

Di seguito trovi un programma console completo, pronto per l'esecuzione, che dimostra l'intero flusso—dal caricamento del documento al salvataggio della versione aggiornata. Copialo e incollalo in un nuovo progetto console .NET e premi **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source document (must contain a bar chart)
            string sourcePath = @"C:\Temp\BarChart.docx";

            // Path where the edited document will be saved
            string destPath = @"C:\Temp\BarChartCustomLabels.docx";

            // Load the Word document
            Document doc = new Document(sourcePath);

            // Retrieve the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Iterate over each data label
            foreach (ChartDataLabel label in chart.DataLabelCollection)
            {
                // Change chart label position
                label.Position = ChartDataLabelPosition.InsideBase;

                // Change chart label font size
                label.Font.Size = 9;
            }

            // Save the updated document
            doc.Save(destPath);
            Console.WriteLine($"Chart labels updated and saved to: {destPath}");
        }
    }
}
```

**Output previsto** quando esegui il programma:

```
Chart labels updated and saved to: C:\Temp\BarChartCustomLabels.docx
```

Apri il file risultante e vedrai le **etichette del grafico a barre regolate** posizionate all'interno delle barre con una dimensione del carattere confortevole.

---

## Domande frequenti e casi particolari

### E se il documento contiene più grafici?

Il codice sopra recupera il *primo* grafico (`GetChild(NodeType.Shape, 0, true)`). Per modificare tutti i grafici, sostituisci il singolo recupero con un ciclo:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape shape in shapes)
{
    if (shape.HasChart)
    {
        Chart chart = shape.GetChart();
        // Apply label changes as shown earlier
    }
}
```

### Come **cambiare il carattere dell'etichetta del grafico** solo per una serie specifica?

Ogni `ChartSeries` ha la propria `DataLabelCollection`. Individua una serie per indice:

```csharp
ChartSeries series = chart.Series[1]; // second series (zero‑based)
foreach (ChartDataLabel label in series.DataLabelCollection)
{
    label.Font.Size = 10; // larger for this series only
}
```

### Funziona con grafici a torta o a linee?

Sì—`ChartDataLabelPosition` supporta valori come `InsideEnd`, `OutsideEnd` e `BestFit`. Per un grafico a torta potresti preferire `OutsideEnd` per mantenere le etichette leggibili.

### E per la localizzazione (ad es., separatori decimali diversi)?

Aspose.Words rispetta le impostazioni di locale del documento. Se devi imporre un formato specifico, regola `label.NumberFormat` prima del salvataggio.

---

## Riepilogo e prossimi passi

Abbiamo coperto **come modificare un grafico** in un documento Word dall'inizio alla fine: caricamento del file, recupero del grafico, **cambio della posizione dell'etichetta del grafico**, **regolazione delle etichette del grafico a barre**, **modifica delle etichette dei dati del grafico** e infine **cambio del carattere dell'etichetta del grafico** prima di salvare. L'esempio completo è pronto per la produzione e può essere inserito in qualsiasi pipeline di automazione.

Pronto a fare il salto di livello? Considera queste idee successive:

- **Aggiungere colori alle etichette** (`dataLabel.Font.Color = Color.Blue;`).  
- **Mostrare i valori in percentuale** (`dataLabel.NumberFormat = "0%";`).  
- **Creare grafici programmaticamente** invece di caricare quelli esistenti.  

Tutte queste si basano sulla stessa superficie API che abbiamo usato oggi, quindi ti sentirai subito a casa.

Se hai incontrato problemi, lascia un commento qui sotto o consulta la documentazione di Aspose.Words per opzioni di personalizzazione più approfondite. Buon coding e goditi quei grafici splendidamente etichettati!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci alternativi nei tuoi progetti.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}