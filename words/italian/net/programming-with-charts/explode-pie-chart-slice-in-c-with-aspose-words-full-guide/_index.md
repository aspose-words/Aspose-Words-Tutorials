---
category: general
date: 2026-07-19
description: Esplodi una fetta di grafico a torta usando Aspose.Words per C#. Scopri
  come esplodere una fetta di torta, regolare le dimensioni del foro della ciambella
  e modificare rapidamente i punti dati del grafico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- explode pie chart slice
- how to explode pie slice
- adjust doughnut hole size
- change chart data points
language: it
lastmod: 2026-07-19
og_description: Esplodi la fetta di un grafico a torta con Aspose.Words per C#. Questa
  guida ti mostra come esplodere la fetta di torta, regolare la dimensione del foro
  della ciambella e modificare i punti dati del grafico in modo efficiente.
og_image_alt: Screenshot showing an exploded pie chart slice created with Aspose.Words
  in C#
og_title: Esplodi la fetta del grafico a torta in C# – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  headline: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  type: TechArticle
- description: Explode pie chart slice using Aspose.Words for C#. Learn how to explode
    pie slice, adjust doughnut hole size, and change chart data points quickly.
  name: Explode Pie Chart Slice in C# with Aspose.Words – Full Guide
  steps:
  - name: Install and Reference Aspose.Words
    text: 'First things first, add the Aspose.Words package to your project. In the
      Package Manager Console:'
  - name: Load the Word Document Containing the Chart
    text: We need a `Document` object that points at the `.docx` with the chart you
      want to modify.
  - name: Retrieve the First Chart Node
    text: Most examples assume a single chart, so we’ll grab the first one. If you
      have multiple charts, adjust the index accordingly.
  - name: Explode the First Slice of a Pie Chart
    text: Now the star of the show—**how to explode pie slice**. We’ll set the `Exploded`
      property of the first data point.
  - name: Adjust Doughnut Hole Size (If It’s a Doughnut Chart)
    text: If your chart happens to be a doughnut, you might want to **adjust doughnut
      hole size**. The hole size is a percentage of the chart’s radius.
  - name: Change Chart Data Points (Optional)
    text: Sometimes you need to **change chart data points**—maybe you’ve updated
      the underlying numbers and want the visual to reflect that.
  - name: Save the Modified Document
    text: Finally, write the changes back to disk. You can overwrite the original
      or create a new file—up to you.
  - name: What’s Next?
    text: '- **Style the exploded slice** (change fill color, border, or add a data
      label). Search for “Aspose.Words chart formatting”. - **Automate batch processing**
      of multiple documents—loop through a folder, explode slices, and save new versions.
      - **Combine with Aspose.Slides** if you need the same chart'
  type: HowTo
tags:
- Aspose.Words
- C#
- Chart Manipulation
title: Esplodere la fetta del grafico a torta in C# con Aspose.Words – Guida completa
url: /it/net/programming-with-charts/explode-pie-chart-slice-in-c-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Esplodere una fetta di grafico a torta in C# con Aspose.Words – Guida completa

Ti sei mai chiesto come **esplodere una fetta di grafico a torta** in un documento Word usando C#? Non sei l’unico. Che tu stia preparando una presentazione di vendita o visualizzando i risultati di un sondaggio, una fetta esplosa attira l’attenzione esattamente dove desideri. In questo tutorial percorreremo l’intero processo—caricare un documento, estrarre il grafico, esplodere la prima fetta, regolare il foro del donut e persino modificare i punti dati del grafico.

Inseriremo anche i concetti secondari che potresti cercare: **come esplodere una fetta di torta**, **regolare la dimensione del foro del donut**, e **modificare i punti dati del grafico**. Nessun superfluo, solo una soluzione completa pronta da copiare‑incollare.

---

## Cosa ti servirà

Prima di iniziare, assicurati di avere:

- **Aspose.Words for .NET** (l’ultima versione al 2026‑07‑19). Puoi ottenerlo da NuGet con `Install-Package Aspose.Words`.
- Un progetto **.NET 6+** (o .NET Framework 4.7.2+ se sei ancora su legacy).
- Un file Word (`Chart.docx`) che contenga già un grafico a torta o a ciambella. Se non ne hai uno, crea rapidamente un grafico in Word e salvalo.

Tutto qui—nessuna libreria aggiuntiva, nessun interop COM, solo codice gestito puro.

---

## Esplodere una fetta di grafico a torta – Implementazione passo‑passo

Di seguito suddividiamo il compito in passaggi di dimensioni gestibili. Ogni sezione ha un chiaro titolo, uno snippet di codice e una breve spiegazione del *perché* facciamo quello che facciamo.

### Passo 1: Installare e fare riferimento ad Aspose.Words

Prima di tutto, aggiungi il pacchetto Aspose.Words al tuo progetto. Nella Console di Gestione Pacchetti:

```powershell
Install-Package Aspose.Words
```

> **Consiglio:** Se usi l’interfaccia NuGet integrata in Visual Studio, cerca “Aspose.Words” e premi Installa. Questo garantisce di avere le ultime correzioni di bug e la possibilità di lavorare con i grafici subito pronto all’uso.

### Passo 2: Caricare il documento Word contenente il grafico

Ci serve un oggetto `Document` che punti al file `.docx` con il grafico da modificare.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Load the source document
Document doc = new Document(@"C:\Charts\Chart.docx");

// Verify that the document actually contains a chart
if (doc.GetChildNodes(NodeType.Chart, true).Count == 0)
{
    throw new InvalidOperationException("No chart found in the specified document.");
}
```

> **Perché è importante:** `Document` è il punto di ingresso per ogni operazione in Aspose.Words. Controllando la presenza di grafici fin da subito, evitiamo riferimenti nulli più tardi quando proveremo a esplodere una fetta.

### Passo 3: Recuperare il primo nodo grafico

La maggior parte degli esempi assume un unico grafico, quindi prenderemo il primo. Se ne hai più di uno, regola l’indice di conseguenza.

```csharp
// Grab the first chart in the document (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

> **Nota:** Il cast a `Chart` è sicuro dopo aver confermato che esiste un grafico. Questo oggetto ci dà accesso a serie, punti dati e impostazioni specifiche del tipo di grafico.

### Passo 4: Esplodere la prima fetta di un grafico a torta

Ora la parte centrale—**come esplodere una fetta di torta**. Imposteremo la proprietà `Exploded` del primo punto dati.

```csharp
// Ensure the chart is a Pie (or Pie3D) before exploding
if (chart.ChartType == ChartType.Pie || chart.ChartType == ChartType.Pie3D)
{
    // Explode the first slice (index 0)
    chart.PieChartData.Series[0].DataPoints[0].Exploded = true;
}
else
{
    Console.WriteLine("The chart is not a pie chart; skipping explode operation.");
}
```

> **Perché funziona:** `Exploded` indica a Word di spostare quella fetta dal centro, creando l’effetto classico di “torta esplosa”. La proprietà è booleana, quindi impostarla a `true` è sufficiente.

### Passo 5: Regolare la dimensione del foro del donut (se è un grafico a ciambella)

Se il tuo grafico è una ciambella, potresti voler **regolare la dimensione del foro del donut**. La dimensione del foro è una percentuale del raggio del grafico.

```csharp
// Check for Doughnut chart type and modify the hole size
if (chart.ChartType == ChartType.Doughnut)
{
    // Set the hole size to 30% (range: 0–100)
    chart.DoughnutChartData.HoleSize = 30;
}
```

> **Cosa indica il numero:** Un valore di `30` significa che il cerchio interno occuperà il 30 % del raggio totale, lasciando una corona esterna più spessa.

### Passo 6: Modificare i punti dati del grafico (opzionale)

A volte è necessario **modificare i punti dati del grafico**—magari hai aggiornato i numeri sottostanti e vuoi che il visuale li rifletta.

```csharp
// Example: Update the second data point's value to 75
if (chart.PieChartData?.Series?.Count > 0 && chart.PieChartData.Series[0].DataPoints.Count > 1)
{
    chart.PieChartData.Series[0].DataPoints[1].Value = 75;
}
```

> **Perché potresti farlo:** Cambiare il valore di un punto dati ricalcola automaticamente le percentuali delle fette, mantenendo il grafico accurato senza doverlo modificare manualmente in Word.

### Passo 7: Salvare il documento modificato

Infine, scrivi le modifiche su disco. Puoi sovrascrivere l’originale o creare un nuovo file—a te la scelta.

```csharp
// Save the document with the exploded slice and adjusted doughnut hole
doc.Save(@"C:\Charts\FormattedChart.docx");

// Quick confirmation
Console.WriteLine("Document saved successfully with exploded pie chart slice.");
```

> **Suggerimento:** Usa `SaveFormat.Docx` se vuoi essere esplicito, ma `Save(string)` rileva automaticamente il formato dall’estensione del file.

---

## Risultato atteso

Quando apri `FormattedChart.docx` in Microsoft Word, dovresti vedere:

- La prima fetta di un grafico a torta **esplosa** verso l’esterno.
- Se il grafico è una ciambella, il foro centrale ora occupa **30 %** del raggio.
- Qualsiasi punto dati modificato riflette i nuovi valori impostati.

Di seguito è mostrato un mock‑up di come appare la fetta esplosa (immagine solo a scopo illustrativo).

![Fetta di grafico a torta esplosa creata con Aspose.Words in C#](exploded-pie-slice.png)

*Alt text:* **fetta di grafico a torta esplosa** che mostra un segmento allontanato in un documento Word.

---

## Domande frequenti e casi particolari

**E se il grafico non è una torta o una ciambella?**  
Il codice verifica `ChartType` prima di applicare `Exploded` o `HoleSize`. Per grafici a barre, linee o area quelle proprietà semplicemente non esistono, quindi la logica le salta in sicurezza.

**Posso esplodere più fette?**  
Assolutamente. Scorri `chart.PieChartData.Series[0].DataPoints` e imposta `Exploded = true` su qualsiasi indice desideri.

**Devo preoccuparmi dei formati numerici specifici della cultura?**  
Aspose.Words memorizza i valori numerici come double, indipendentemente dalla locale, quindi sei al sicuro da problemi di virgole vs punti.

**Cosa succede con i grafici inseriti in intestazioni/piè di pagina?**  
Usa `doc.GetChildNodes(NodeType.Chart, true)` per recuperare tutti i grafici, poi ispeziona `ParentNode` di ciascun nodo per capire dove si trovano. La stessa logica di esplosione si applica.

---

## Conclusione

Ora disponi di una soluzione solida, pronta da copiare‑incollare, su **come esplodere una fetta di grafico a torta** usando Aspose.Words in C#. Abbiamo coperto l’intero flusso di lavoro—dal caricamento del documento, al recupero del grafico, all’esplosione della fetta, **regolando la dimensione del foro del donut**, fino a **modificare i punti dati del grafico** e infine salvare il file.

Sentiti libero di sperimentare: prova a esplodere una fetta diversa, modifica la dimensione del foro al 45 %, o aggiorna più punti dati contemporaneamente. L’API di Aspose.Words rende queste modifiche semplici, e le variazioni appaiono immediatamente aprendo il file Word.

---

### Cosa c’è dopo?

- **Stilizzare la fetta esplosa** (cambiare colore di riempimento, bordo o aggiungere un’etichetta dati). Cerca “Aspose.Words chart formatting”.
- **Automatizzare l’elaborazione batch** di più documenti—scorri una cartella, esplodi le fette e salva nuove versioni.
- **Combinare con Aspose.Slides** se ti serve lo stesso grafico in una presentazione PowerPoint.

Hai altre domande sulla manipolazione dei grafici, o vuoi approfondire altri tipi di grafico? Lascia un commento qui sotto, e buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Inserire un grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserire un semplice grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Inserire un grafico ad area in un documento Word | Aspose.Words per .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}