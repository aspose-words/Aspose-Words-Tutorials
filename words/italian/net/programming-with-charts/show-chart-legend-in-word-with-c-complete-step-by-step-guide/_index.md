---
category: general
date: 2026-06-02
description: Mostra la legenda del grafico in un documento Word usando C#. Scopri
  come aggiungere la legenda, applicare uno stile di grafico predefinito e personalizzare
  gli elementi visivi del grafico Word in pochi minuti.
draft: false
keywords:
- show chart legend
- how to add legend
- add legend word chart
- apply preset chart style
- apply chart style word
language: it
og_description: Mostra la legenda del grafico in un documento Word immediatamente.
  Questa guida ti accompagna nell’aggiungere una legenda, nell’applicare uno stile
  di grafico predefinito e nella gestione dei casi particolari.
og_title: Mostra la legenda del grafico in Word – Tutorial completo C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  headline: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Show chart legend in a Word document using C#. Learn how to add legend,
    apply preset chart style, and customize Word chart visuals in minutes.
  name: Show Chart Legend in Word with C# – Complete Step‑by‑Step Guide
  steps:
  - name: How to add legend to a specific chart (not the first one)?
    text: 'Replace the `0` index in `GetChild(NodeType.Chart, 0, true)` with the zero‑based
      position of your target chart, or loop through all chart nodes:'
  - name: Can I place the legend at the bottom instead of the right?
    text: 'Absolutely. Just change the `LegendPosition` enum:'
  - name: What if the chart already has a legend but I want to hide it?
    text: 'Set `HasLegend` to `false`:'
  - name: Does this work with Word 2010, 2016, and later?
    text: Yes. Aspose.Words abstracts the underlying Word version, so the same code
      works across all modern .docx files.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word chart
- Legend customization
title: Mostra la legenda del grafico in Word con C# – Guida completa passo passo
url: /it/net/programming-with-charts/show-chart-legend-in-word-with-c-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mostra la legenda del grafico in Word con C# – Guida completa passo‑passo

Ti sei mai chiesto **come aggiungere la legenda** a un grafico inserito in un documento Word? Non sei l'unico. In molti report, una legenda mancante rende i dati criptici, e correggerla non dovrebbe essere un problema.  

In questo tutorial mostreremo **la legenda del grafico** in un file Word usando Aspose.Words per .NET, applicheremo uno stile di grafico predefinito e ci assicureremo che la legenda appaia esattamente dove ti serve. Alla fine avrai un esempio pronto‑da‑eseguire che potrai inserire in qualsiasi progetto C#.

## Cosa copre questa guida

Percorreremo l’intero flusso di lavoro:

1. Caricare un *.docx* esistente che contiene già un grafico.  
2. Recuperare il primo grafico (o qualsiasi grafico di destinazione).  
3. **Applicare uno stile di grafico predefinito** per dare all’immagine un aspetto professionale.  
4. **Mostrare la legenda del grafico**, posizionarla a destra e gestire casi speciali come i grafici Waterfall.  
5. Salvare il documento modificato.

Nessuno strumento esterno, nessuna manipolazione manuale dell’interfaccia—solo puro codice. L’unico prerequisito è un riferimento al pacchetto NuGet Aspose.Words (versione 23.10 o successiva) e una conoscenza di base di C#.

---

## Prerequisiti

- .NET 6.0 o successivo (l’esempio funziona anche con .NET Framework 4.7.2).  
- Libreria Aspose.Words per .NET installata (`Install-Package Aspose.Words`).  
- Un file Word (`input.docx`) che contiene già almeno un grafico.  
- Visual Studio, Rider o qualsiasi IDE tu preferisca.

---

## Passo 1: Configurare il progetto e caricare il documento

Per prima cosa, crea un’app console (o integra il codice in un progetto esistente). Aggiungi le direttive `using` e carica il file `.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        
        // Continue with the next steps...
```

> **Perché è importante:** Caricare il documento è la base. Senza un’istanza `Document` non puoi accedere agli oggetti grafico esposti da Aspose.Words.

---

## Passo 2: Recuperare il grafico di destinazione

I grafici sono memorizzati come nodi all’interno dell’albero del documento. Il metodo `GetChild` esegue una ricerca profonda, consentendoci di ottenere il primo grafico indipendentemente da dove si trovi (intestazione, corpo, piè di pagina, ecc.).

```csharp
        // Retrieve the first chart in the document (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }
```

> **Suggerimento:** Se hai più grafici, cambia l’indice `0` in `1`, `2`, … oppure itera su `doc.GetChildNodes(NodeType.Chart, true)`.

---

## Passo 3: Applicare uno stile visivo predefinito

Un grafico dall’aspetto gradevole parte spesso da uno stile. Aspose.Words fornisce decine di stili integrati; `ChartStyle.Style12` è un’opzione pulita e moderna.

```csharp
        // Apply a preset visual style to the chart
        chart.Style = ChartStyle.Style12;
```

> **Come funziona:** La proprietà `Style` corrisponde agli stili di grafico Word integrati che vedi nell’interfaccia. Scegliere un preset ti salva dal dover impostare manualmente colori, caratteri e marcatori.

---

## Passo 4: Abilitare la legenda e posizionarla

Ora arriva la parte centrale—**mostrare la legenda del grafico**. Attiviamo la legenda, poi la agganciamo al lato destro del grafico.

```csharp
        // Enable the legend and place it on the right side
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;
```

> **Perché a destra?** Posizionare la legenda a destra mantiene ampia l’area dati, il che è particolarmente utile per i grafici a barre o a colonne.

---

## Passo 5: Gestire i grafici Waterfall (caso speciale)

I grafici Waterfall si comportano in modo leggermente diverso; la legenda può essere nascosta per impostazione predefinita. La seguente clausola di guardia garantisce che la legenda sia visibile quando il tipo di grafico è Waterfall.

```csharp
        // For Waterfall charts, ensure the legend is visible
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }
```

> **Nota sul caso limite:** Alcune versioni più vecchie di Word ignorano `HasLegend` per i grafici Waterfall, quindi impostare esplicitamente `Legend.Show` garantisce la visibilità.

---

## Passo 6: Salvare il documento modificato

Infine, scrivi le modifiche su disco. Puoi sovrascrivere il file originale o crearne uno nuovo.

```csharp
        // Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

L’esecuzione del programma produrrà `output.docx` con una legenda visibile a destra, stilizzata con `Style12`. Apri il file in Word per verificare il risultato.

---

## Esempio completo (tutti i passaggi combinati)

Di seguito trovi il codice completo, pronto‑da‑eseguire. Copialo‑incollalo in `Program.cs` (o in qualsiasi file C#) e adatta i percorsi dei file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2️⃣ Retrieve the first chart (deep search)
        Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // 3️⃣ Apply a preset visual style (show chart legend with a nice look)
        chart.Style = ChartStyle.Style12;

        // 4️⃣ Enable the legend and dock it to the right
        chart.HasLegend = true;
        chart.Legend.Position = LegendPosition.Right;

        // 5️⃣ Special handling for Waterfall charts
        if (chart.Type == ChartType.Waterfall)
        {
            chart.Legend.Show = true;
        }

        // 6️⃣ Save the updated document
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Chart legend added and style applied successfully.");
    }
}
```

**Output previsto:** L’apertura di `output.docx` mostra il grafico originale con una legenda allineata a destra, stilizzata con il moderno `Style12`. Tutte le serie dati sono chiaramente etichettate, rendendo il grafico immediatamente comprensibile.

---

## Domande frequenti (FAQ)

### Come aggiungere la legenda a un grafico specifico (non al primo)?

Sostituisci l’indice `0` in `GetChild(NodeType.Chart, 0, true)` con la posizione zero‑based del grafico desiderato, oppure cicla tutti i nodi grafico:

```csharp
NodeCollection charts = doc.GetChildNodes(NodeType.Chart, true);
foreach (Chart c in charts)
{
    // Apply the same steps to each chart
}
```

### Posso posizionare la legenda in basso invece che a destra?

Assolutamente. Basta cambiare l’enum `LegendPosition`:

```csharp
chart.Legend.Position = LegendPosition.Bottom;
```

### E se il grafico ha già una legenda ma voglio nasconderla?

Imposta `HasLegend` a `false`:

```csharp
chart.HasLegend = false;
```

### Funziona con Word 2010, 2016 e versioni successive?

Sì. Aspose.Words astrae la versione sottostante di Word, quindi lo stesso codice funziona su tutti i file .docx moderni.

---

## Pro Tips & Errori comuni

- **Pro tip:** Dopo aver applicato uno stile, puoi ancora modificare elementi individuali (colori, etichette dati) tramite la collezione `Chart.Series`. Lo stile ti fornisce una solida base.
- **Attenzione a:** Se il grafico è dentro una cella di tabella, la legenda potrebbe risultare compressa. Considera di aumentare le dimensioni del grafico (`chart.Width`, `chart.Height`) prima di posizionare la legenda.
- **Nota sulle prestazioni:** Caricare documenti di grandi dimensioni (centinaia di MB) può richiedere molta memoria. Usa `LoadOptions` con `LoadFormat.Docx` per ridurre l’overhead se devi manipolare solo i grafici.

---

## Prossimi passi

Ora che sai **come aggiungere la legenda** e **applicare uno stile di grafico predefinito** in Word, potresti approfondire:

- **Colori personalizzati per il grafico** (`chart.Series[i].Format.Fill.ForeColor`).  
- **Formattazione delle etichette dati** (`chart.Series[i].HasDataLabel = true`).  
- **Esportare il grafico come immagine** (`chart.ToImage()`), utile per l’inserimento altrove.  

Ognuno di questi argomenti si basa sullo stesso modello di oggetti, quindi la curva di apprendimento rimane leggera.

---

## Conclusione

Abbiamo appena dimostrato una soluzione pulita, end‑to‑end, per **mostrare la legenda del grafico** in un documento Word usando C#. Caricando il documento, recuperando il grafico, applicando uno stile predefinito, abilitando la legenda e gestendo le particolarità dei Waterfall, ottieni un grafico rifinito pronto per qualsiasi report aziendale.  

Sentiti libero di sperimentare con altri valori di `ChartStyle` o posizioni della legenda—le tue visualizzazioni meritano la migliore presentazione. Se incontri difficoltà, lascia un commento qui sotto; buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Insert Column Chart In A Word Document](/words/english/net/programming-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Using Word Chart API](/words/english/net/programming-with-charts/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}