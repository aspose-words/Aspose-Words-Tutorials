---
category: general
date: 2026-09-05
description: Crea un grafico radar in Word usando C#. Impara a generare un documento
  Word vuoto, aggiungere un grafico radar, impostare le dimensioni del grafico e abilitare
  rapidamente le tacche.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radar chart
- add chart to word
- add radar chart
- generate blank word document
- set chart size word
language: it
lastmod: 2026-09-05
og_description: Crea un grafico radar in Word usando C#. Questa guida ti mostra come
  generare un documento Word vuoto, aggiungere un grafico radar, impostare le dimensioni
  del grafico e abilitare le tacche—tutto in pochi minuti.
og_image_alt: Screenshot of a Word document with a created radar chart
og_title: Crea un grafico radar in Word – guida passo passo C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create radar chart in Word using C#. Learn to generate a blank Word
    document, add a radar chart, set chart size, and enable tick marks quickly.
  headline: How to create radar chart and add chart to Word with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Chart
- Word automation
title: Come creare un grafico radar e aggiungere il grafico a Word con C#
url: /it/net/programming-with-charts/how-to-create-radar-chart-and-add-chart-to-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico radar e aggiungere il grafico a Word con C#

Se hai bisogno di **creare un grafico radar** all'interno di un file Word, questa guida ti accompagna passo passo attraverso l'intero processo. Imparerai a **generare un documento Word vuoto**, inserire un grafico radar, **impostare le dimensioni del grafico in Word**, e abilitare le graduazioni dell'asse—tutto con poche righe di codice C#.

Aggiungere dati visuali ai report è una necessità comune, e l'uso di Aspose.Words lo rende semplice. Nei passaggi seguenti copriamo anche come **aggiungere un grafico a Word** programmaticamente, così potrai automatizzare dashboard, riepiloghi finanziari o qualsiasi contenuto basato su dati.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o versioni successive installate  
* Una licenza Aspose.Words per .NET (o una prova gratuita) – la libreria fornisce le API `Document`, `DocumentBuilder` e chart utilizzate in questo tutorial  
* Visual Studio 2022 (o qualsiasi IDE C#)  

> **Suggerimento:** Se stai testando, posiziona il DLL di Aspose.Words nella cartella `bin` del tuo progetto e riferiscilo tramite NuGet (`Install-Package Aspose.Words`).

## Come creare un grafico radar in un documento Word

Il primo passo è **generare un documento Word vuoto** che ospiterà il grafico. Questo ti fornisce una tela pulita e ti permette di controllare i metadati del documento prima di aggiungere qualsiasi contenuto.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// 1️⃣ Create an empty Word document
Document document = new Document();   // this is a blank .docx file
```

*Perché è importante:* Un oggetto `Document` vuoto garantisce che non vi siano stili o sezioni nascosti che interferiscano con il layout del grafico. Ti consente inoltre di impostare in seguito le proprietà del documento (autore, titolo) se necessario.

## Come aggiungere un grafico a Word usando Aspose.Words

Successivamente, crea un `DocumentBuilder`. Il builder è lo strumento principale che ti permette di inserire testo, immagini e grafici nel documento.

```csharp
// 2️⃣ Initialize a DocumentBuilder for the empty document
DocumentBuilder builder = new DocumentBuilder(document);
```

Ora puoi **aggiungere un grafico radar** direttamente dove è posizionato il cursore. Il metodo `InsertChart` accetta un enum `ChartType`, larghezza e altezza in punti.

```csharp
// 3️⃣ Insert a radar (radial) chart with a specific size
Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);
```

*Perché 400 × 300?* Queste dimensioni forniscono un grafico chiaro e leggibile su una pagina A4 standard. Puoi regolare la dimensione in seguito con il passaggio **imposta le dimensioni del grafico in Word** se il tuo layout richiede un rapporto d'aspetto diverso.

## Impostare le dimensioni del grafico in Word

Se devi perfezionare la dimensione dopo l'inserimento, puoi modificare le proprietà `Width` e `Height` del grafico. Questo è utile quando il testo circostante o i margini della pagina richiedono un equilibrio visivo differente.

```csharp
// 4️⃣ Adjust chart dimensions (optional)
// radarChart.Width = 500;   // width in points
// radarChart.Height = 350;  // height in points
```

> **Nota:** La sovraccarico di `InsertChart` imposta già la dimensione, quindi il codice sopra è opzionale e mostrato per completezza.

## Abilitare i segni di graduazione sull'asse radiale

Un grafico radar è più utile quando l'asse radiale mostra chiare graduazioni. Le impostazioni seguenti attivano i segni di graduazione e impostano l'intervallo a 30 gradi, allineandosi con le tipiche visualizzazioni radar in stile bussola.

```csharp
// 5️⃣ Turn on graduations (tick marks) and set interval
radarChart.AxisX.HasGraduations = true;      // show tick marks
radarChart.AxisX.GraduationInterval = 30;   // every 30 degrees
```

*Perché è importante:* Le graduazioni aiutano i lettori a valutare i valori a ciascun angolo, migliorando la leggibilità per gli stakeholder non familiari con i dati.

## Salvare il documento contenente il grafico

Infine, scrivi il documento su disco. Puoi scegliere qualsiasi cartella ti piaccia; assicurati solo che il percorso esista.

```csharp
// 6️⃣ Save the Word file
document.Save(@"C:\Temp\RadialChart.docx");
```

Quando apri `RadialChart.docx` in Microsoft Word, vedrai un grafico radar completamente renderizzato al centro della pagina, con le dimensioni specificate e i segni di graduazione ogni 30 gradi.

### Output previsto

* Un file `.docx` chiamato **RadialChart.docx**  
* La prima pagina contiene un grafico radar di dimensioni 400 × 300 punti  
* L'asse X (asse radiale) visualizza i segni di graduazione a 0°, 30°, 60°, …, 330°  

Ora puoi sostituire la serie di dati segnaposto con i tuoi valori accedendo a `radarChart.Series` – ma questo va oltre lo scopo di questo tutorial base su **aggiungere un grafico radar**.

## Varianti comuni e casi limite

| Scenario | Adeguamento |
|----------|------------|
| **Tipo di grafico diverso** | Sostituisci `ChartType.Radar` con `ChartType.Column`, `ChartType.Pie`, ecc. |
| **Grafici multipli** | Chiama `InsertChart` più volte; ogni chiamata posiziona il nuovo grafico dopo quello precedente. |
| **Set di dati grandi** | Usa `radarChart.Series[0].DataPoints.AddDataPointForBarSeries(value)` per popolare molti punti. |
| **Salvataggio come PDF** | Chiama `document.Save("RadialChart.pdf", SaveFormat.Pdf);` dopo aver aggiunto il grafico. |
| **Esecuzione su .NET Core** | Assicurati di riferire il pacchetto `Aspose.Words.NETCore`; l'uso dell'API è identico. |

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in un'applicazione console. Include tutti i passaggi, le eventuali regolazioni di dimensione e commenti per chiarezza.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace RadarChartDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Generate a blank Word document
            Document document = new Document();

            // 2️⃣ Create a builder to work with the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3️⃣ Insert a radar chart (400 × 300 points)
            Chart radarChart = builder.InsertChart(ChartType.Radar, 400, 300);

            // 4️⃣ (Optional) Change chart size if needed
            // radarChart.Width = 500;
            // radarChart.Height = 350;

            // 5️⃣ Enable tick marks on the radial axis
            radarChart.AxisX.HasGraduations = true;          // show tick marks
            radarChart.AxisX.GraduationInterval = 30;       // every 30 degrees

            // 6️⃣ Populate the chart with sample data (optional)
            radarChart.Series[0].DataPoints.Clear();
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(10);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(20);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(30);
            radarChart.Series[0].DataPoints.AddDataPointForBarSeries(40);

            // 7️⃣ Save the document
            string outputPath = @"C:\Temp\RadialChart.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Esegui il programma, apri il file risultante e vedrai il grafico radar esattamente come descritto.

## Conclusione

Ora sai come **creare un grafico radar** e **aggiungere un grafico a Word** usando C#. Il tutorial ha coperto la generazione di un **documento Word vuoto**, l'inserimento di un grafico radar, **impostare le dimensioni del grafico in Word**, e l'abilitazione delle graduazioni dell'asse. Con questa base potrai estendere la soluzione a più grafici, serie di dati personalizzate o esportazione in PDF.

### Prossimi passi

* Esplora altri tipi di grafico con `ChartType` (ad esempio `Bar`, `Line`) – vedi la parola chiave **add radar chart** per esempi correlati.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e spiegazioni passo passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci alternativi nei tuoi progetti.

- [Insert Scatter Chart in Word Document](/words/english/net/programming-with-charts/insert-scatter-chart/)
- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}