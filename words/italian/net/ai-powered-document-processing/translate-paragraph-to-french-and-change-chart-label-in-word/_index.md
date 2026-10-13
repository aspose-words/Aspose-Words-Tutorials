---
category: general
date: 2026-10-10
description: Traduci il paragrafo in francese e impara come modificare l'etichetta
  dei dati del grafico, personalizzare l'etichetta dei dati del grafico e salvare
  il file docx modificato usando Aspose.Words AI.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate paragraph to french
- how to change chart data label
- how to translate word document with ai
- customize chart data label
- how to save edited docx file
language: it
lastmod: 2026-10-10
og_description: Traduci il paragrafo in francese e impara come modificare l’etichetta
  dei dati del grafico, personalizzare l’etichetta dei dati del grafico e salvare
  il file docx modificato usando Aspose.Words AI.
og_image_alt: Screenshot of a Word document showing a French paragraph and a chart
  with a customized data label
og_title: Traduci il paragrafo in francese e modifica l'etichetta del grafico in Word
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Translate paragraph to French and learn how to change chart data label,
    customize chart data label, and save edited docx file using Aspose.Words AI.
  headline: Translate paragraph to French and change chart label in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- AI translation
- chart customization
title: Traduci il paragrafo in francese e modifica l'etichetta del grafico in Word
url: /it/net/ai-powered-document-processing/translate-paragraph-to-french-and-change-chart-label-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Traduci il paragrafo in francese e modifica l'etichetta del grafico in Word

Se hai bisogno di **tradurre il paragrafo in francese** e allo stesso tempo aggiornare un grafico nello stesso documento Word, questa guida ti mostra esattamente come fare. Utilizzando Aspose.Words AI puoi tradurre automaticamente il testo, poi modificare l'etichetta dei dati di un grafico e infine salvare il file `.docx` modificato—tutto in pochi passaggi semplici.

Il tutorial copre tutto, dal caricamento del file sorgente al salvataggio delle modifiche. Alla fine sarai in grado di tradurre qualsiasi paragrafo, personalizzare l'etichetta dei dati di un grafico e generare un nuovo file Word pronto per la distribuzione. Non sono necessari script esterni; l'intero flusso di lavoro è contenuto in un unico programma C#.

## Prerequisiti

- .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.7+)
- Una licenza Aspose.Words per .NET (o una chiave di valutazione gratuita)
- Accesso a Internet per il traduttore Google AI (la classe `Translator` utilizza l'API di Google in background)
- Un documento Word (`input.docx`) che contiene almeno un paragrafo e un grafico

## Passo 1: Configura il progetto e importa i namespace

Crea una nuova applicazione console e aggiungi il pacchetto NuGet Aspose.Words:

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Ora includi i namespace richiesti all'inizio di `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.AI;          // AI translation helpers
using Aspose.Words.Drawing;    // Chart manipulation classes
using Aspose.Words.Tables;     // For accessing chart series and labels
```

Queste importazioni ti danno accesso al caricamento dei documenti, alla traduzione AI e alla funzionalità di modifica dei grafici.

## Passo 2: Carica il documento Word sorgente

```csharp
// Path to the original file – adjust as needed
string inputPath = @"YOUR_DIRECTORY/input.docx";

// Load the document into memory
Document document = new Document(inputPath);
Console.WriteLine("Document loaded successfully.");
```

Il caricamento del file crea una rappresentazione in memoria che puoi interrogare e modificare senza toccare il file originale su disco.

## Passo 3: Traduci il primo paragrafo in francese

Il primo paragrafo è spesso un titolo o una frase introduttiva, il che lo rende un buon candidato per la traduzione. La classe `Translator` astrae la chiamata al modello AI di Google.

```csharp
// Retrieve the first paragraph in the first section
Paragraph paragraph = document.FirstSection.Body.FirstParagraph;

// Extract the raw text (including trailing paragraph mark)
string originalText = paragraph.GetText();

// Translate the text to French
string translatedText = Translator.Translate(originalText, Language.French);
Console.WriteLine($"Original: {originalText.Trim()}");
Console.WriteLine($"Translated: {translatedText.Trim()}");

// Replace the paragraph's runs with the translated text
paragraph.Runs.Clear();                     // Remove existing runs
paragraph.AppendChild(new Run(document, translatedText)); // Insert new run
```

**Perché funziona:**  
`paragraph.Runs.Clear()` rimuove tutte le esecuzioni di testo esistenti, garantendo che la nuova traduzione non si concatenzi con il contenuto precedente. `new Run(document, translatedText)` crea una nuova esecuzione che eredita la formattazione del paragrafo.

## Passo 4: Individua il primo grafico e personalizza la sua etichetta dei dati

I grafici sono memorizzati come nodi `Shape` di tipo `NodeType.Shape`. Il primo grafico può essere recuperato con `GetChild`.

```csharp
// Find the first chart in the document (deep search)
Chart chart = (Chart)document.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    Console.WriteLine("No chart found in the document.");
    return;
}

// Access the first series and its first data label
ChartSeries series = chart.Series[0];
ChartDataLabel dataLabel = series.DataLabels[0];

// Change the label's position and text
dataLabel.Position = ChartDataLabelPosition.OutsideEnd; // Move label outside the bar
dataLabel.Text = "Ventes T1"; // French for "Sales Q1"
Console.WriteLine("Chart data label customized.");
```

**Spiegazione dei passaggi chiave:**

- `GetChild(NodeType.Shape, 0, true)` esegue una ricerca in profondità e restituisce la prima forma, che nel nostro caso è un grafico.
- `ChartSeries` rappresenta una raccolta di punti dati; la prima serie (`Series[0]`) corrisponde tipicamente al set di dati principale.
- `ChartDataLabelPosition.OutsideEnd` sposta l'etichetta fuori dalla fine della barra, migliorando la leggibilità.
- Impostare `dataLabel.Text` a una stringa in francese allinea l'etichetta con il paragrafo tradotto.

## Passo 5: Salva il documento con il paragrafo tradotto

```csharp
string translatedDocPath = @"YOUR_DIRECTORY/translated.docx";
document.Save(translatedDocPath);
Console.WriteLine($"Translated document saved to {translatedDocPath}");
```

A questo punto il documento contiene il paragrafo in francese ma mantiene ancora la configurazione originale del grafico.

## Passo 6: Salva il documento con il grafico aggiornato

Puoi riutilizzare la stessa istanza `Document`—non è necessario ricaricarla—poiché le modifiche al grafico sono già in memoria.

```csharp
string chartUpdatedPath = @"YOUR_DIRECTORY/chart-updated.docx";
document.Save(chartUpdatedPath);
Console.WriteLine($"Chart‑updated document saved to {chartUpdatedPath}");
```

Entrambi i file sono ora pronti per la distribuzione:

- **`translated.docx`** – contiene il paragrafo in francese.
- **`chart-updated.docx`** – contiene il paragrafo in francese *e* l'etichetta del grafico personalizzata.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in `Program.cs`. Compila ed esegue così com'è, a condizione di aver sostituito `YOUR_DIRECTORY` con un percorso di cartella reale.



## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche illustrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Personalizza l'etichetta dei dati del grafico](/words/english/net/programming-with-charts/chart-data-label/)
- [Formatta il numero di etichette dei dati in un grafico](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Etichetta dati del grafico](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}