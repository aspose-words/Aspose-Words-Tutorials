---
category: general
date: 2026-08-07
description: Crea rapidamente un grafico a torta in C#. Impara come inserire un grafico
  a torta, aggiungere le etichette dei dati alla torta, mostrare le percentuali nel
  grafico e personalizzare le etichette dei dati del grafico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart word
- show percentage chart
- add data labels pie
- insert pie chart
- customize chart data labels
language: it
lastmod: 2026-08-07
og_description: Crea un grafico a torta in Word con C# usando Aspose.Words. Questo
  tutorial mostra come inserire un grafico a torta, aggiungere le etichette dei dati
  al grafico a torta e visualizzare le percentuali, personalizzando le etichette dei
  dati del grafico.
og_image_alt: Word document displaying a pie chart with percentage labels outside
  each slice
og_title: Crea un grafico a torta in C# – tutorial completo
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  headline: Create pie chart word in C# – step‑by‑step guide
  type: TechArticle
- description: Create pie chart word in C# quickly. Learn how to insert pie chart,
    add data labels pie, show percentage chart, and customize chart data labels.
  name: Create pie chart word in C# – step‑by‑step guide
  steps:
  - name: Call `chart.Series.Add()` for each additional series.
    text: Call `chart.Series.Add()` for each additional series.
  - name: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
    text: Ensure each series uses the same categories; otherwise, Aspose.Words will
      throw an `ArgumentException`.
  - name: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
    text: Optionally, set `labels.ShowSeriesName = true` to differentiate slices.
  type: HowTo
tags:
- pie chart
- C#
- Aspose.Words
- chart customization
title: Crea un grafico a torta in C# – guida passo passo
url: /it/net/programming-with-charts/create-pie-chart-word-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un grafico a torta in Word con C# – guida passo‑passo

Se hai bisogno di **create pie chart word** documenti in C#, questa guida fornisce una soluzione completa, pronta‑da‑eseguire. Vedrai come **insert pie chart**, **add data labels pie** e **show percentage chart** mentre **customize chart data labels** per un aspetto curato.

Generare grafici programmaticamente ti salva dalla modifica manuale, soprattutto quando report o dashboard devono essere prodotti automaticamente. Nelle sezioni seguenti imparerai tutto il necessario per incorporare un grafico a torta completamente etichettato in un file Word usando Aspose.Words per .NET.

## Prerequisiti e configurazione

* SDK .NET 6.0 o successivo installato.  
* Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione temporanea).  
* Visual Studio 2022 (o qualsiasi IDE che supporti C#).  

Add the Aspose.Words NuGet package to your project:

```bash
dotnet add package Aspose.Words
```

> **Consiglio professionale:** Se prevedi di generare molti grafici, abilita la modalità **Free‑Form Drawing** (`DocumentBuilder.UseFreeFormDrawing = true`) per migliori prestazioni.

## Crea un grafico a torta in Word con Aspose.Words

Il primo passo importante è creare un documento Word vuoto e un `DocumentBuilder`. Questo oggetto gestisce tutte le inserzioni successive.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new blank document and a DocumentBuilder
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché è importante*: `Document` rappresenta l'intero file `.docx`, mentre `DocumentBuilder` fornisce un'API fluida per aggiungere paragrafi, tabelle e grafici. Iniziare con un documento pulito garantisce che nessuna formattazione nascosta interferisca con il layout del grafico.

## Inserisci un grafico a torta nel documento

Ora inseriamo un grafico a torta della dimensione desiderata. Il metodo `InsertChart` restituisce un oggetto `Chart` che possiamo configurare ulteriormente.

```csharp
// Step 2: Insert a pie chart of the desired size
Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);
```

*Perché è importante*: Il flag `ChartType.Pie` indica ad Aspose.Words di generare un grafico circolare. La larghezza (`400`) e l'altezza (`300`) sono espresse in punti, offrendoti un controllo preciso sull'ingombro visivo.

## Popola il grafico con i dati

Un grafico a torta richiede almeno una serie di valori numerici. Qui aggiungiamo tre categorie: “Apples”, “Bananas” e “Cherries”.

```csharp
// Populate the first series with sample data
chart.Series[0].AddCategory("Apples", 40);
chart.Series[0].AddCategory("Bananas", 35);
chart.Series[0].AddCategory("Cherries", 25);
```

*Perché è importante*: Ogni chiamata a `AddCategory` crea una fetta. Il valore numerico determina la dimensione della fetta, mentre l'etichetta diventa il nome della categoria visualizzato quando le etichette dati sono attivate.

## Aggiungi etichette dati alla torta e mostra percentuale del grafico

Per rendere il grafico informativo, abilitiamo le etichette dati, le posizioniamo all'esterno delle fette e chiediamo ad Aspose.Words di mostrare sia il nome della categoria sia la percentuale.

```csharp
// Step 3: Access the first series' data label collection
ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;

// Step 4: Position labels outside the slices and show useful information
labels.Position = ChartDataLabelPosition.OutsideEnd; // places label outside each slice
labels.ShowCategoryName = true;                     // displays "Apples", "Bananas", …
labels.ShowPercentage = true;                       // displays "40%" etc.
```

*Perché è importante*: Impostare `Position` su `OutsideEnd` migliora la leggibilità, soprattutto quando le fette sono piccole. Abilitare `ShowCategoryName` e `ShowPercentage` soddisfa il requisito **show percentage chart** e realizza l'obiettivo **add data labels pie**.

## Personalizza ulteriormente le etichette dati del grafico (opzionale)

Potresti voler cambiare il carattere, aggiungere una linea guida o nascondere la legenda. Il frammento seguente dimostra le personalizzazioni più comuni:

```csharp
// Optional: customize label font and leader lines
labels.Font.Size = 10;
labels.Font.Color = System.Drawing.Color.DarkBlue;
labels.ShowLeaderLines = true;

// Optional: hide the default legend because labels already contain the needed info
chart.HasLegend = false;
```

*Perché è importante*: Personalizzare l'aspetto dell'etichetta garantisce che il grafico corrisponda alla guida di stile del tuo documento. Rimuovere la legenda riduce il disordine visivo quando le etichette dati trasmettono già le stesse informazioni.

## Salva il documento con il grafico personalizzato

Infine, scrivi il documento su disco. Scegli un percorso a cui hai accesso in scrittura.

```csharp
// Step 5: Save the document with the customized chart
doc.Save("YOUR_DIRECTORY/ChartWithCustomLabels.docx");
```

Quando apri `ChartWithCustomLabels.docx` in Microsoft Word, vedrai un grafico a torta in cui ogni fetta è etichettata con il nome della categoria e la percentuale, posizionata all'esterno della fetta e formattata con le impostazioni di carattere personalizzate.

### Output previsto

| Fetta   | Valore | Percentuale | Etichetta mostrata in Word |
|---------|--------|-------------|----------------------------|
| Apples  | 40     | 40 %        | Apples – 40 %              |
| Bananas | 35     | 35 %        | Bananas – 35 %             |
| Cherries| 25     | 25 %        | Cherries – 25 %            |

Il grafico dovrebbe apparire simile all'illustrazione seguente:

![Documento Word che mostra un grafico a torta con etichette percentuali all'esterno di ogni fetta](pie-chart-word.png "Esempio di creazione di un grafico a torta in Word")

*Il testo alternativo dell'immagine include la parola chiave principale per SEO.*

## Gestione di più serie e casi limite

L'esempio base utilizza una singola serie, tipica per un grafico a torta. Se devi visualizzare più serie (ad esempio confrontando due anni), devi:

1. Chiamare `chart.Series.Add()` per ogni serie aggiuntiva.  
2. Assicurarsi che ogni serie utilizzi le stesse categorie; altrimenti Aspose.Words genererà un `ArgumentException`.  
3. Facoltativamente, impostare `labels.ShowSeriesName = true` per differenziare le fette.

```csharp
// Adding a second series (e.g., sales in 2025)
chart.Series.Add("2025");
chart.Series[1].AddCategory("Apples", 45);
chart.Series[1].AddCategory("Bananas", 30);
chart.Series[1].AddCategory("Cherries", 25);
```

Quando esistono più serie, il grafico viene renderizzato automaticamente come una **pie raggruppata** (nota anche come “pie of pies”). Controlla l'output per verificare che le etichette rimangano leggibili.

## Problemi comuni e come evitarli

| Problema | Causa | Soluzione |
|----------|-------|-----------|
| Le etichette si sovrappongono alle fette | Area del grafico piccola o molte categorie | Aumentare le dimensioni del grafico (`InsertChart(width, height)`) o cambiare `Position` a `InsideEnd`. |
| Le percentuali non sommano a 100 % | Errori di arrotondamento nei dati | Usare `labels.ShowPercentage = true` (Aspose.Words normalizza automaticamente). |
| Il grafico appare vuoto in Word | Licenza mancante o timeout della valutazione | Assicurarsi che una licenza valida di Aspose.Words sia caricata prima di creare il documento. |
| I colori dei font differiscono dal tema di Word | Font personalizzato impostato nel codice | Rimuovere le impostazioni di font personalizzate o abbinare i colori del tema di Word (`System.Drawing.Color.Black`). |

## Codice sorgente completo (eseguibile)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Load license (optional for evaluation)
        // License license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert a pie chart
        Chart chart = builder.InsertChart(ChartType.Pie, 400, 300);

        // 3. Add data to the first series
        chart.Series[0].AddCategory("Apples", 40);
        chart.Series[0].AddCategory("Bananas", 35);
        chart.Series[0].AddCategory("Cherries", 25);

        // 4. Configure data labels
        ChartDataLabelCollection labels = chart.Series[0].DataLabelCollection;
        labels.Position = ChartDataLabelPosition.OutsideEnd;
        labels.ShowCategoryName = true;
        labels.ShowPercentage = true;

        // Optional: further customization
        labels.Font.Size = 10;
        labels.Font.Color = Color.DarkBlue;
        labels.ShowLeaderLines = true;
        chart.HasLegend = false;

        // 5. Save the document
        doc.Save("ChartWithCustomLabels.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Eseguendo il programma si genera `ChartWithCustomLabels.docx`, che contiene un esempio di **create pie chart word** che soddisfa tutti i requisiti elencati nel tutorial.

## Conclusione

Ora sai come **create pie chart word** documenti in C# usando Aspose.Words. La guida ha coperto l'inserimento di un grafico a torta, **add data labels pie**, **show percentage chart**, e **customize chart data labels** per ottenere un file Word professionale e basato sui dati.

Da qui puoi esplorare argomenti correlati come **insert pie chart** in paragrafi esistenti, generare grafici **bar** o **line**, o automatizzare la creazione batch di report con set di dati variabili. Sperimenta con diverse posizioni delle etichette, stili di carattere e configurazioni multi‑serie per adattare l'output alle tue specifiche esigenze di reporting.

Buon lavoro con i grafici!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Personalizza l'etichetta del grafico](/words/english/net/programming-with-charts/chart-data-label/)
- [Imposta opzioni predefinite per le etichette dati in un grafico](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Inserisci grafico a colonne in un documento Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}