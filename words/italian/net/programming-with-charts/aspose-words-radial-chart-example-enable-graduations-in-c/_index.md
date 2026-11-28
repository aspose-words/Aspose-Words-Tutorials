---
category: general
date: 2026-10-13
description: Esempio di grafico radiale Aspose.Words che mostra come abilitare le
  graduazioni su un grafico radiale usando C# e Aspose.Words 24.9+.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: it
lastmod: 2026-10-13
og_description: Esempio di grafico radiale Aspose.Words che dimostra come abilitare
  le graduazioni su un grafico radiale con C# e la più recente libreria 24.9+.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Esempio di grafico radiale Aspose.Words – abilita le graduazioni in C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Esempio di grafico radiale Aspose.Words: abilitare le graduazioni in C#'
url: /it/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Esempio di grafico radiale Aspose.Words: abilitare le graduazioni in C#

Se stai cercando un **aspose.words radial chart example**, sei nel posto giusto. Questo tutorial ti guida passo passo per attivare le graduazioni per un grafico radiale usando l'API Aspose.Words per .NET.

I grafici radiali sono utili per visualizzare dati ciclici come metriche di orario o tendenze stagionali. Per impostazione predefinita le graduazioni (i segni di spunta attorno all'asse circolare) sono nascoste, il che può rendere il grafico più difficile da leggere. Abilitarle è una modifica a una singola riga, ma è necessario conoscere il modello di oggetti corretto e la versione che supporta la funzionalità.

In questa guida imparerai a:

* Caricare un documento Word che contiene già un grafico radiale.  
* Accedere alla forma del grafico tramite l'API Aspose.Words chart.  
* Attivare la **graduations visibility** (disponibile da **Aspose.Words version 24.9**).  
* Salvare il documento modificato e verificare il risultato.

Il codice completo, eseguibile, è incluso, così puoi copiarlo e incollarlo in un nuovo progetto console e vedere subito l'effetto.

![Esempio di grafico radiale Aspose.Words con graduazioni](https://example.com/images/radial-chart-graduations.png "Esempio di grafico radiale Aspose.Words che mostra le graduazioni abilitate")

## Prerequisiti

| Requisito | Perché è importante |
|-------------|----------------|
| .NET 6.0 o versioni successive | Aspose.Words per .NET 24.9+ mira a .NET Standard 2.0 e funziona su .NET 6+. |
| Aspose.Words per .NET **24.9** o versioni più recenti | La proprietà `IsGraduationsVisible` è stata introdotta nella versione 24.9. Le versioni precedenti genereranno una `MissingMemberException`. |
| Un documento Word (`RadialChart.docx`) che contiene un grafico radiale | L'esempio manipola un grafico esistente; crearne uno da zero è un argomento separato. |
| Un IDE C# (Visual Studio, Rider, VS Code) | Qualsiasi IDE in grado di compilare progetti .NET funzionerà. |
| Pacchetto NuGet `Aspose.Words` | Installa tramite `dotnet add package Aspose.Words --version 24.9.0` (o versioni successive). |

> **Consiglio professionale:** Se non puoi aggiornare alla 24.9, puoi comunque modificare altre proprietà del grafico, ma le graduazioni rimarranno nascoste perché l'API non esponeva quel flag.

## Esempio di grafico radiale Aspose.Words – guida passo‑passo

Le sezioni seguenti suddividono il processo in passaggi discreti e facili da seguire. Ogni passo include il codice esatto di cui hai bisogno e una breve spiegazione del *perché* del passo.

### Passo 1: Carica il documento che contiene un grafico radiale

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Perché è importante:**  
`Document` è il punto di ingresso dell'**Aspose.Words chart API**. Carica il file DOCX in memoria, dandoti accesso a ogni nodo—paragrafi, tabelle e forme di grafico. Se il file non viene trovato, `Document` genera una `FileNotFoundException`, che dovresti gestire nel codice di produzione.

### Passo 2: Recupera la prima forma di grafico dal documento

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Perché è importante:**  
I grafici sono memorizzati come nodi `Shape`. Il metodo `GetChild` con `NodeType.Shape` attraversa il DOM e restituisce la prima forma corrispondente. Il cast a `Chart` ti dà accesso alle proprietà specifiche del grafico come `RadialChart`. Il controllo null garantisce un errore chiaro se il documento non contiene un grafico, caso comune quando si riutilizzano template.

### Passo 3: Abilita le graduazioni sul grafico radiale

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Perché è importante:**  
`IsGraduationsVisible` controlla i segni di spunta attorno all'asse circolare. Quando impostato su `true`, il grafico rende visibili le graduazioni, migliorando la leggibilità per chi deve valutare i valori con precisione. La proprietà si trova sotto `RadialChart`, che è un sotto‑tipo di `Chart`. Se provi a usarla su un grafico non radiale (ad esempio un grafico a barre), la proprietà `RadialChart` sarà `null`, quindi dovresti verificare il tipo di grafico prima in scenari più complessi.

#### Gestione di grafici non radiali (opzionale)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Questa guardia rende il codice più robusto quando il documento di origine può contenere diversi tipi di grafico.

### Passo 4: Salva il documento modificato

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Perché è importante:**  
Chiamare `Save` scrive il DOM in memoria su un file .docx, persiste la modifica apportata al grafico. Il file di output può essere aperto in Microsoft Word, LibreOffice o qualsiasi visualizzatore che supporti DOCX. Vedrai il grafico radiale con le graduazioni visibili.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi incollare in `Program.cs` di un progetto console .NET.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Output previsto

Quando apri `RadialChart_Graduations.docx` in Word, il grafico radiale mostrerà i segni di spunta (graduazioni) attorno all'asse circolare, simile allo screenshot mostrato in precedenza. Il resto del grafico (serie di dati, legenda, titolo) rimane invariato.

## Varianti comuni e casi limite

| Situazione | Soluzione |
|-----------|----------|
| **Versione Aspose.Words più vecchia (< 24.9)** | Aggiorna all'ultimo pacchetto NuGet. La proprietà `IsGraduationsVisible` non esiste nelle versioni precedenti. |
| **Più grafici nello stesso documento** | Usa `doc.GetChild(NodeType.Shape, index, true)` con l'`index` appropriato o itera su `doc.GetChildNodes(NodeType.Shape, true)` e filtra per `ChartType.Radial`. |
| **Grafico creato programmaticamente** | Usa `DocumentBuilder` per inserire un grafico, quindi imposta `RadialChart.IsGraduationsVisible` sul |

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aggiorna i dati della serie del grafico in un documento Word usando Aspose.Words per .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Rimuovi una serie di grafico da un documento Word usando Aspose.Words per .NET](/words/english/net/programming-with-charts/remove-chart-series/)
- [Nascondi il bordo dell'area di tracciamento in un grafico a colonne con Aspose.Words per .NET](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}