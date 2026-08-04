---
category: general
date: 2026-08-04
description: Il posizionamento personalizzato delle etichette dei dati per i grafici
  in C# consente di centrare le etichette sulle fette del grafico. Segui questa guida
  passo passo usando l'API dei grafici di Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Custom Data‑Label Placement for Charts
- chart data label positioning
- Aspose.Words chart API
- C# chart manipulation
- Word document chart automation
language: it
lastmod: 2026-08-04
og_description: Il posizionamento personalizzato delle etichette dati per i grafici
  in C# ti mostra come centrare tutte le etichette dati su ogni sezione di un grafico
  Word. Padroneggia il posizionamento delle etichette dei grafici con Aspose.Words.
og_image_alt: Screenshot of a Word chart with centered data labels after applying
  C# code
og_title: Posizionamento personalizzato delle etichette dati per i grafici in C# –
  guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Custom Data‑Label Placement for Charts in C# lets you center labels
    on chart slices. Follow this step‑by‑step guide using Aspose.Words chart API.
  headline: Custom Data‑Label Placement for Charts in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart
- Data Labels
title: Posizionamento personalizzato delle etichette dei dati per i grafici in C#
url: /it/net/programming-with-charts/custom-data-label-placement-for-charts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Posizionamento Personalizzato delle Etichette Dati per i Grafici in C#

**Custom Data‑Label Placement for Charts** ti consente di controllare esattamente dove appare ogni etichetta su un grafico all'interno di un documento Word. In questo tutorial imparerai a centrare tutte le etichette dati su ogni fetta usando C# e l'API dei grafici di Aspose.Words.

Otterrai un esempio completo e eseguibile che carica un file `.docx`, accede alla prima forma del grafico, cambia la `Position` di ogni etichetta in `Center` e salva il documento aggiornato. Non sono necessari riferimenti esterni—solo la libreria Aspose.Words per .NET e un ambiente di sviluppo C# di base.

**What you’ll learn**

* Come caricare un documento Word che contiene un grafico.  
* Come individuare la forma del grafico con l'API dei grafici di Aspose.Words.  
* Come applicare **chart data label positioning** a ogni serie nel grafico.  
* Come salvare il documento in modo che le etichette centrate compaiano in Word.  

**Prerequisites**

* .NET 6.0 (o successivo) installato.  
* Visual Studio 2022 (o qualsiasi IDE C#).  
* Un riferimento al pacchetto NuGet `Aspose.Words`.  
* Un file Word (`Chart.docx`) che contiene almeno un grafico.

---

## Posizionamento Personalizzato delle Etichette Dati per i Grafici – passo 1: caricare il documento

La prima azione è aprire il file Word che contiene il grafico. `Document` è il punto di ingresso per qualsiasi manipolazione con Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Load the source Word document.
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

// Verify that the document actually contains a chart.
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
if (shapes.Count == 0)
{
    throw new InvalidOperationException("The document does not contain any shapes.");
}
```

*Why this step matters*: Senza caricare il documento non è possibile accedere all'oggetto grafico. La convalida garantisce di ricevere un errore chiaro se il file non contiene un grafico, evitando un riferimento nullo in seguito.

---

## Utilizzare l'API dei grafici di Aspose.Words per accedere alle forme dei grafici

Aspose.Words tratta un grafico come un oggetto `Chart` annidato all'interno di una `Shape`. Lo si recupera effettuando il cast del nodo figlio appropriato.

```csharp
// Get the first shape that is a chart.
Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (!chartShape.HasChart)
{
    throw new InvalidOperationException("The first shape is not a chart.");
}

// Extract the Chart instance.
Chart chart = chartShape.GetChart();
```

*Why this step matters*: Accedere direttamente a `Chart` ti dà il pieno controllo su serie, punti dati e proprietà delle etichette. Se la forma non è un grafico, il codice si interrompe subito con un messaggio informativo.

---

## Impostare il posizionamento delle etichette dati del grafico in C#

Ora itera su ogni serie e su ogni etichetta dati, impostando la `Position` su `Center`. Questo è il fulcro di **Custom Data‑Label Placement for Charts**.

```csharp
// Center all data labels on each slice of the chart.
foreach (Series series in chart.Series)
{
    foreach (ChartDataLabel label in series.DataLabels)
    {
        // Position enum values: Center, InsideEnd, OutsideEnd, etc.
        label.Position = ChartDataLabelPosition.Center;
    }
}
```

**Pro tip**: Se ti serve un posizionamento diverso (ad es., `InsideEnd` per un grafico a colonne), modifica il valore dell'enumerazione di conseguenza. L'enumerazione `ChartDataLabelPosition` copre tutte le posizioni standard supportate da Word.

*Why this step matters*: Modificando `label.Position` si aggiorna la rappresentazione OOXML sottostante, così l'etichetta appare centrata quando il documento viene aperto in Microsoft Word.

---

## Salvare il documento Word con le etichette aggiornate

Dopo aver modificato il grafico, persisti le modifiche su un file. Puoi sovrascrivere l'originale o creare una nuova copia.

```csharp
// Save the modified document with centered labels.
doc.Save(@"YOUR_DIRECTORY\ChartLabelsCentered.docx");
```

*Why this step matters*: Il salvataggio scrive l'OOXML aggiornato su disco. Aprendo `ChartLabelsCentered.docx` in Word verranno mostrate tutte le etichette delle fette centrate, confermando che **Custom Data‑Label Placement for Charts** ha avuto successo.

---

## Casi limite e variazioni

| Situation | How to handle |
|-----------|---------------|
| **Multiple charts** in the same document | Loop over `doc.GetChildNodes(NodeType.Shape, true)` and check `shape.HasChart` for each shape. |
| **Different chart types** (pie, doughnut, bar) | The same `ChartDataLabelPosition.Center` works for pie‑type charts. For bar/column charts you may prefer `InsideEnd` or `OutsideEnd`. |
| **Label text needs formatting** | Access `label.TextProperties` to set font size, color, or boldness. |
| **Running on .NET Core** | Ensure you reference the .NET Standard version of Aspose.Words; the API is identical. |

---

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare‑incollare in un'applicazione console. Include tutte le direttive `using` necessarie e la gestione degli errori.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Path to the source and destination files.
        const string sourcePath = @"YOUR_DIRECTORY\Chart.docx";
        const string destPath   = @"YOUR_DIRECTORY\ChartLabelsCentered.docx";

        // Load the document.
        Document doc = new Document(sourcePath);

        // Find the first chart shape.
        Shape chartShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (chartShape == null || !chartShape.HasChart)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Get the Chart object.
        Chart chart = chartShape.GetChart();

        // Center all data labels.
        foreach (Series series in chart.Series)
        {
            foreach (ChartDataLabel label in series.DataLabels)
            {
                label.Position = ChartDataLabelPosition.Center;
            }
        }

        // Save the updated document.
        doc.Save(destPath);
        Console.WriteLine($"Document saved with centered labels to: {destPath}");
    }
}
```

**Expected result**: Apri `ChartLabelsCentered.docx` in Microsoft Word. Ogni fetta del grafico ora mostra la sua etichetta dati direttamente al centro della fetta, fornendo un aspetto visivo più pulito.

---

## Conclusione

Ora disponi di una soluzione completa per **Custom Data‑Label Placement for Charts** in C#. Caricando il documento, accedendo al grafico tramite l'API dei grafici di Aspose.Words, impostando `ChartDataLabelPosition.Center` per ogni etichetta e salvando il file, puoi automatizzare il posizionamento delle etichette per qualsiasi grafico basato su Word.

Successivamente, esplora altre opzioni di **chart data label positioning** come `InsideEnd` o `OutsideEnd`, oppure sperimenta con **C# chart manipulation** per cambiare colori, aggiungere legende o generare grafici da zero. Queste estensioni si basano direttamente sulle tecniche illustrate qui e ampliano le tue competenze nell'automazione dei grafici nei documenti Word. Buon coding!

## Cosa Dovresti Imparare Dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Personalizza l'Etichetta del Grafico](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatta il Numero dell'Etichetta del Grafico](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Etichetta del Grafico](/words/german/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}