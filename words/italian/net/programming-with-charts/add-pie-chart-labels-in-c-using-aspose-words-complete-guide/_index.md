---
category: general
date: 2026-07-20
description: Aggiungi etichette al grafico a torta con Aspose.Words per .NET. Scopri
  come modificare le etichette del grafico a torta, visualizzare le etichette percentuali
  e aggiornare rapidamente le etichette delle serie del grafico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart labels
- change pie chart labels
- update chart series labels
- show percentage labels
- display pie chart percentages
language: it
lastmod: 2026-07-20
og_description: Aggiungi etichette al grafico a torta in C# con Aspose.Words. Impara
  a modificare le etichette del grafico a torta, visualizzare le etichette percentuali
  e aggiornare le etichette delle serie del grafico in pochi passaggi.
og_image_alt: Word document screenshot displaying a pie chart with custom percentage
  labels
og_title: Aggiungi etichette al grafico a torta in C# – Tutorial completo di Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Add pie chart labels with Aspose.Words for .NET. Learn how to change
    pie chart labels, show percentage labels, and update chart series labels quickly.
  headline: Add pie chart labels in C# using Aspose.Words – Complete Guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Aggiungi etichette al grafico a torta in C# con Aspose.Words – Guida completa
url: /it/net/programming-with-charts/add-pie-chart-labels-in-c-using-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungere etichette al grafico a torta in C# usando Aspose.Words – Guida completa

Hai bisogno di **aggiungere etichette al grafico a torta** a un documento Word usando C#? Con Aspose.Words puoi modificare facilmente **le etichette del grafico a torta** e **visualizzare le percentuali del grafico a torta** direttamente nel file—senza dover intervenire manualmente in Word.  

In questo tutorial vedremo passo passo come **mostrare le etichette di percentuale**, riposizionarle e persino **aggiornare le etichette delle serie del grafico** per dati dinamici. Alla fine avrai uno snippet riutilizzabile da inserire in qualsiasi progetto .NET.

> **Anteprima rapida:** Dopo aver seguito la guida, aprendo il file `.docx` salvato vedrai un grafico a torta in cui ogni fetta è etichettata con la sua percentuale, posizionata all'esterno della fetta per la massima leggibilità.

---

## Cosa ti servirà

- **Aspose.Words for .NET** (l'ultima versione disponibile al 2026). Puoi ottenerlo da NuGet: `Install-Package Aspose.Words`.
- Un **documento Word** che contiene già un grafico a torta o a ciambella (lo chiameremo `Chart.docx`).
- Familiarità di base con **C#** e Visual Studio (o il tuo IDE preferito).

Questo è tutto—nessuna libreria aggiuntiva, nessun interop COM, solo codice gestito puro.

---

## Aggiungere etichette al grafico a torta – Implementazione completa

Di seguito trovi un programma console C# **completo e eseguibile** che carica un documento, modifica il primo grafico a torta e salva il risultato. Ogni riga è commentata così capirai **perché** facciamo quello che facciamo, non solo **cosa**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace PieChartLabelDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the Word document that already contains a pie chart.
            //    Change the path to where your Chart.docx lives.
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart node in the document.
            //    The GetChild method walks the document tree and returns the first Node of type Chart.
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label collection of the first series.
            //    In a pie chart each series represents the whole pie; the collection holds the labels for each slice.
            ChartDataLabelCollection dataLabels = chart.Series[0].DataLabelCollection;

            // 4️⃣ Position the data labels **outside** the slices.
            //    This is the most readable layout for pie/doughnut charts.
            dataLabels.Position = ChartDataLabelPosition.OutsideEnd;

            // 5️⃣ Turn on the percentage display.
            //    ShowPercentage automatically calculates and shows each slice’s contribution.
            dataLabels.ShowPercentage = true;

            // 6️⃣ (Optional) If you also want the actual values, enable ShowValue.
            //    dataLabels.ShowValue = true; // uncomment to display raw numbers.

            // 7️⃣ Save the modified document.
            //    The new file will contain the pie chart with custom labels.
            doc.Save(@"YOUR_DIRECTORY\ChartWithCustomLabels.docx");

            Console.WriteLine("Pie chart labels added successfully!");
        }
    }
}
```

### Risultato atteso

Apri `ChartWithCustomLabels.docx` in Microsoft Word. Dovresti vedere il grafico a torta **con le etichette di percentuale posizionate all'esterno di ogni fetta**. Le etichette appaiono, ad esempio, come “35 %”, “20 %”, ecc., rendendo il grafico immediatamente comprensibile.

---

## Modificare le etichette del grafico a torta: posizionamento e formattazione

Se devi solo **modificare le etichette del grafico a torta** senza mostrare le percentuali, puoi impostare la proprietà `Position` su una delle seguenti:

| Enum Posizione | Effetto visivo |
|----------------|----------------|
| `InsideEnd`    | Le etichette sono all'interno della fetta, proprio al bordo. |
| `Center`       | Le etichette appaiono al centro della fetta (utile per torte piccole). |
| `OutsideEnd`   | Le etichette sono all'esterno della fetta, collegate da una linea guida (impostazione predefinita). |

```csharp
dataLabels.Position = ChartDataLabelPosition.Center; // example switch
```

**Consiglio professionale:** `OutsideEnd` funziona meglio quando il grafico ha molte fette; evita la sovrapposizione del testo.

---

## Mostrare le etichette di percentuale su un grafico a torta

La proprietà `ShowPercentage` è un **flag booleano**. Impostandola a `true` si indica ad Aspose.Words di calcolare il contributo di ogni fetta in base alla sorgente dati sottostante.

```csharp
dataLabels.ShowPercentage = true; // Turns on the % display
```

Puoi anche combinarla con `ShowValue` se ti servono sia i numeri grezzi **che** le percentuali:

```csharp
dataLabels.ShowValue = true; // Shows the actual cell value next to the %
```

Quando entrambi i flag sono attivi, l’etichetta appare così: “45 % (120)”.

---

## Aggiornare le etichette delle serie del grafico per dati dinamici

Spesso genererai grafici al volo—ad esempio vendite mensili o risultati di sondaggi. Per **aggiornare le etichette delle serie del grafico** in modo programmatico, modifica la collezione `Series` prima di intervenire sulle etichette dei dati:

```csharp
// Assume you have a second series you want to rename
chart.Series[1].Name = "Projected Growth";

// Refresh the data label collection after changes
ChartDataLabelCollection secondSeriesLabels = chart.Series[1].DataLabelCollection;
secondSeriesLabels.ShowPercentage = true;
secondSeriesLabels.Position = ChartDataLabelPosition.OutsideEnd;
```

Questo snippet dimostra come **aggiornare le etichette delle serie del grafico** per qualsiasi serie, non solo la prima. È utile quando costruisci report che combinano dati reali e previsioni.

---

## Casi limite e problemi comuni

| Situazione | Cosa controllare | Correzione |
|------------|------------------|------------|
| **Il grafico non è una torta/ciambella** | `Position` potrebbe non avere alcun effetto visivo. | Verifica che `chart.Type` sia `ChartType.Pie` o `ChartType.Doughnut`. |
| **Nessun grafico trovato** | `GetChild` restituisce `null`. | Aggiungi una clausola di guardia (vedi codice) e registra un messaggio utile. |
| **Versione Word più vecchia** | Alcune funzionalità delle etichette vengono ignorate. | Salva come `.docx` (formato moderno) per garantire il supporto completo. |
| **Numero elevato di fette** | Le etichette possono sovrapporsi anche con `OutsideEnd`. | Considera di ridurre il numero di fette o aumentare le dimensioni del grafico. |

---

## Esempio completo funzionante (copia‑incolla)

Di seguito trovi il **programma completo** che puoi copiare in un nuovo progetto console. Sostituisci `YOUR_DIRECTORY` con la cartella che contiene `Chart.docx`.



## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche illustrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Imposta le opzioni predefinite per le etichette dei dati in un grafico](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Personalizza una singola serie di grafico in un grafico](/words/english/net/programming-with-charts/single-chart-series/)
- [Inserisci un grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}