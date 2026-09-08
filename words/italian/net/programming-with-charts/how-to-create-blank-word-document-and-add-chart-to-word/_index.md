---
category: general
date: 2026-09-08
description: Crea un documento Word vuoto e aggiungi un grafico a Word con Aspose.Words.
  Scopri come inserire un grafico radar, abilitare le graduazioni e salvare il file.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add chart to word
- insert radar chart
- Aspose.Words chart
- C# Word automation
language: it
lastmod: 2026-09-08
og_description: Crea un documento Word vuoto e aggiungi un grafico a Word usando Aspose.Words.
  Questo tutorial mostra come inserire un grafico radar, configurare gli assi e salvare
  il documento.
og_image_alt: Radar chart inserted into a blank Word document created with C#
og_title: Crea un documento Word vuoto e aggiungi un grafico radar – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: create blank Word document and add chart to Word with Aspose.Words.
    Learn how to insert radar chart, enable graduations, and save the file.
  headline: How to create blank Word document and add chart to Word
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- Chart
title: Come creare un documento Word vuoto e aggiungere un grafico.
url: /it/net/programming-with-charts/how-to-create-blank-word-document-and-add-chart-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto e aggiungere un grafico a Word

Se hai bisogno di **creare un documento Word vuoto** per un report, un modello o un'unione di stampa automatizzata, questa guida ti accompagna passo passo attraverso l'intero processo con C# e Aspose.Words. Imparerai anche come **aggiungere un grafico a Word**, in particolare come **inserire un grafico radar**, attivare le graduazioni e salvare il risultato come file .docx.

Questo tutorial copre tutto, dall'impostazione del progetto fino al passaggio finale di verifica. Alla fine avrai a disposizione uno snippet di codice riutilizzabile che può essere inserito in qualsiasi applicazione .NET. Non è necessaria alcuna esperienza pregressa con Aspose.Words, ma è consigliabile avere una conoscenza di base di C# e un SDK .NET recente installato.

## Prerequisiti

- .NET 6.0 SDK o successivo  
- Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`)  
- Un IDE come Visual Studio 2022 o VS Code  
- Permessi di scrittura sulla cartella in cui verrà salvato il documento  

Puoi installare la libreria con il comando seguente:

```bash
dotnet add package Aspose.Words
```

## Passo 1: Creare un documento Word vuoto

Il primo passo è **creare un documento Word vuoto** in memoria. La classe `Document` rappresenta l'intero file, mentre `DocumentBuilder` fornisce un'API fluida per aggiungere contenuti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

public class RadarChartDemo
{
    public static void Main()
    {
        // Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` inizia vuoto, quindi hai una tela pulita su cui posizionare il grafico. Mantenere il documento vuoto in questa fase rende più semplice riutilizzare lo stesso codice per diversi modelli.

## Passo 2: Aggiungere un grafico a Word

Successivamente, **aggiungiamo un grafico a Word** chiamando `InsertChart`. Il metodo richiede il tipo di grafico e le dimensioni desiderate in punti (1 punto = 1/72 di pollice).

```csharp
        // Insert a radar (radial) chart with a defined size
        Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

`ChartType.Radar` indica ad Aspose.Words di generare un grafico radiale, ideale per visualizzare dati multivariati in un layout circolare. I valori di dimensione (400 × 300) funzionano bene per la maggior parte delle pagine in orientamento verticale, ma puoi modificarli per adattarli al tuo layout.

## Passo 3: Inserire il grafico radar e configurare le graduazioni

Ora **inseriamo il grafico radar** e abilitiamo le graduazioni (ticchetti) sia sull'asse delle categorie (X) sia su quello dei valori (Y). Le graduazioni migliorano la leggibilità mostrando le posizioni esatte per ciascun punto dati.

```csharp
        // Turn on graduations for both axes
        radarChart.AxisX.HasGraduations = true;   // radial (category) axis
        radarChart.AxisY.HasGraduations = true;   // value axis

        // Optional: define a custom graduation step for the radial axis
        radarChart.AxisX.GraduationStep = 10;
```

Impostare `HasGraduations` a `true` disegna i segni di graduazione sugli assi. L'opzionale `GraduationStep` controlla la spaziatura tra i ticchetti sull'asse radiale; un passo di 10 significa un ticchetto ogni 10 gradi.

### Consiglio professionale
Se hai bisogno di visualizzare le etichette dei dati, chiama `radarChart.Series[0].HasDataLabel = true;`. Questo aggiunge il valore numerico accanto a ogni punto, utile per le presentazioni.

## Passo 4: Popolare il grafico con dati di esempio (opzionale)

Un grafico radar senza dati è invisibile. Di seguito trovi un modo rapido per aggiungere una serie di valori di esempio. Puoi sostituire questo blocco con la tua fonte dati.

```csharp
        // Add a series with sample data
        radarChart.Series.Clear(); // Remove any default series
        var series = radarChart.Series.Add("Performance", "Category");
        series.Add(30);
        series.Add(55);
        series.Add(70);
        series.Add(45);
        series.Add(90);
```

Ogni chiamata a `Add` inserisce un punto nella serie. L'ordine dei punti corrisponde alle posizioni angolari intorno al cerchio.

## Passo 5: Salvare il documento contenente il grafico

Infine, salva il documento su disco. Il metodo `Save` scrive automaticamente il file .docx, preservando il grafico e tutta la formattazione.

```csharp
        // Save the document to a file
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "RadarChart.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Eseguendo il programma si crea un **documento Word vuoto** che ora contiene un grafico radar pienamente funzionante. Apri il file in Microsoft Word per vedere il risultato.

![Radar chart in Word document](radar_chart.png){alt="Radar chart inserted into a blank Word document"}

## Varianti comuni e casi limite

| Situazione | Cosa modificare |
|-----------|----------------|
| **Dimensione del grafico diversa** | Regola i parametri di larghezza/altezza di `InsertChart`. |
| **Altri tipi di grafico** | Sostituisci `ChartType.Radar` con `ChartType.Column`, `ChartType.Pie`, ecc., mantenendo la stessa logica delle graduazioni. |
| **Salvataggio su stream** | Usa `document.Save(Stream, SaveFormat.Docx)` |

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Create Word Scatter Chart Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}