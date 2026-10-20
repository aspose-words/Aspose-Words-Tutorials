---
category: general
date: 2026-09-21
description: Scopri come creare un documento Word in C# e inserire un grafico a colonne,
  impostare la posizione delle etichette e visualizzare i valori utilizzando Aspose.Words
  in una guida passo‑passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- how to insert chart
- how to set label
- how to display values
- insert column chart word
language: it
lastmod: 2026-09-21
og_description: Crea documento Word in C# con Aspose.Words. Questo tutorial mostra
  come inserire un grafico a colonne, impostare la posizione dell'etichetta e visualizzare
  i valori.
og_image_alt: Screenshot of a Word document created with C# that contains a column
  chart and data labels
og_title: Crea documento Word in C# – inserisci grafico a colonne, imposta etichetta,
  mostra valori
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  headline: How to create Word document C# with a column chart and formatted labels
  type: TechArticle
- description: Learn how to create Word document C# and insert a column chart, set
    label position, and display values using Aspose.Words in a step‑by‑step guide.
  name: How to create Word document C# with a column chart and formatted labels
  steps:
  - name: Expected result
    text: When you open `output.docx`, you should see a single column chart similar
      to the image below. Each column has a numeric label at its top, inside the column,
      displaying the series value.
  - name: Adding custom data to the chart
    text: 'If you need to replace the placeholder data, you can modify the chart’s
      `Series` collection:'
  - name: Changing label font and color
    text: 'You can further customize the label appearance:'
  - name: Inserting multiple charts
    text: The `DocumentBuilder` can insert as many charts as you need. Just call `InsertChart`
      again after moving the cursor with `builder.Writeln()` or `builder.InsertParagraph()`.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Charts
title: Come creare un documento Word in C# con un grafico a colonne e etichette formattate
url: /it/net/programming-with-charts/how-to-create-word-document-c-with-a-column-chart-and-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word C# con un grafico a colonne e etichette formattate

Se hai bisogno di **create Word document C#** che includa un grafico, questa guida ti mostra esattamente come farlo. Imparerai come inserire un **column chart**, posizionare la sua etichetta dati e visualizzare i valori dell’etichetta—tutto con Aspose.Words per .NET.

Generare un file Word con grafico richiedeva in passato lavoro manuale in Microsoft Word. Con i passaggi **how to insert chart** descritti qui, puoi automatizzare l’intero processo dal codice, rendendo la generazione dei report veloce e ripetibile. Il tutorial copre anche le proprietà **how to set label** e **how to display values** così il grafico è pronto per gli utenti finali.

Alla fine di questo articolo avrai un programma C# completo e eseguibile che crea un file `.docx` contenente un grafico a colonne le cui etichette dati appaiono all’interno di ogni colonna e mostrano i loro valori numerici.

## Prerequisiti

* .NET 6.0 SDK o versioni successive installate  
* Una copia con licenza di **Aspose.Words for .NET** (la versione di prova gratuita funziona per i test)  
* Un IDE come Visual Studio 2022 o Visual Studio Code  

Non sono richiesti pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Passo 1: Configura il progetto e aggiungi Aspose.Words

Crea un nuovo progetto console e aggiungi il pacchetto Aspose.Words:

```bash
dotnet new console -n WordChartDemo
cd WordChartDemo
dotnet add package Aspose.Words
```

Il comando `dotnet add package` scarica l'ultima versione stabile di **Aspose.Words**, che include l'API dei grafici utilizzata nell'esempio **insert column chart word**.

## Passo 2: Crea un nuovo documento Word vuoto

La prima porzione di codice crea un documento vuoto e un `DocumentBuilder` che ti permette di inserire contenuti. Questa è la base per **create word document C#**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 2: Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` rappresenta l'intero file `.docx`, mentre `DocumentBuilder` fornisce metodi come `InsertParagraph`, `InsertImage` e, soprattutto per questo tutorial, `InsertChart`.

## Passo 3: Inserisci un grafico a colonne (how to insert chart)

Ora inseriamo un **column chart**. Il metodo `InsertChart` accetta il tipo di grafico, la larghezza e l'altezza in punti.

```csharp
        // Step 3: Insert a column chart with a width of 400 pt and height of 300 pt.
        Chart chart = builder.InsertChart(ChartType.Column, 400, 300);
```

In questo momento il grafico contiene una serie di dati predefinita con valori segnaposto. Puoi sostituire i dati della serie se ti servono numeri personalizzati, ma per dimostrare **how to set label** e **how to display values**, i dati predefiniti sono sufficienti.

## Passo 4: Posiziona l'etichetta dati all'interno di ogni colonna (how to set label)

Le etichette dati sono il testo che appare su ogni colonna. Per rendere il grafico più leggibile, spostiamo l'etichetta all'interno della colonna e abilitiamo il suo valore numerico.

```csharp
        // Step 4: Access the first data label of the first series.
        ChartDataLabel label = chart.DataLabels[0];

        // Position the label at the inside end of the column.
        label.Position = ChartDataLabelPosition.InsideEnd;

        // Show the numeric value of each data point.
        label.ShowValue = true;
```

`ChartDataLabelPosition.InsideEnd` posiziona l'etichetta in cima alla colonna ma ancora all'interno della forma della colonna, uno stile visivo comune per i report. Impostare `ShowValue` a `true` soddisfa il requisito **how to display values**.

## Passo 5: Salva il documento

Infine, scrivi il documento su disco. Il file può essere aperto con Microsoft Word, LibreOffice o qualsiasi visualizzatore che supporti il formato Open XML.

```csharp
        // Step 5: Save the document to the output folder.
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Eseguendo il programma si genera `output.docx` che contiene un grafico a colonne con le etichette dati posizionate all'interno di ogni colonna e che mostrano i loro valori.

### Risultato atteso

Quando apri `output.docx`, dovresti vedere un unico grafico a colonne simile all'immagine qui sotto. Ogni colonna ha un'etichetta numerica in cima, all'interno della colonna, che visualizza il valore della serie.

![Grafico in un documento Word creato con C#](/images/word-chart-example.png "Grafico in un documento Word creato con C# – create word document C#")

*Alt text:* *Grafico in un documento Word creato con C# che dimostra come inserire column chart word e visualizzare i valori.*

## Varianti comuni e casi limite

### Aggiungere dati personalizzati al grafico

Se devi sostituire i dati segnaposto, puoi modificare la collezione `Series` del grafico:

```csharp
// Replace the default series with custom values.
chart.Series.Clear();
ChartSeries series = chart.Series.Add(ChartType.Column);
series.Name = "Sales Q1";
series.AddCategory("Jan", 120);
series.AddCategory("Feb", 150);
series.AddCategory("Mar", 180);
```

### Modificare il carattere e il colore dell'etichetta

Puoi personalizzare ulteriormente l'aspetto dell'etichetta:

```csharp
label.Font.Name = "Arial";
label.Font.Size = 10;
label.Font.Color = System.Drawing.Color.DarkBlue;
```

### Inserire più grafici

`DocumentBuilder` può inserire quanti grafici desideri. Basta chiamare nuovamente `InsertChart` dopo aver spostato il cursore con `builder.Writeln()` o `builder.InsertParagraph()`.

## Consigli professionali

* **Consiglio:** Imposta `chart.HasTitle = true` e assegna `chart.Title.Text` per dare al grafico un titolo descrittivo. Questo migliora l'accessibilità per i lettori di schermo.
* **Attenzione:** Quando salvi su una condivisione di rete, assicurati che l'applicazione abbia i permessi di scrittura; altrimenti `doc.Save` genererà un `UnauthorizedAccessException`.
* **Suggerimento di performance:** Riutilizza una singola istanza di `DocumentBuilder` per più inserimenti; creare un nuovo builder per ogni operazione aggiunge un sovraccarico non necessario.

## Conclusione

Ora sai come **create Word document C#** che contiene un grafico a colonne, come **insert chart** elementi, **set label** posizioni e **display values** all'interno di ogni colonna. L'esempio di codice completo sopra è pronto per l'esecuzione e puoi estenderlo con dati personalizzati, stili o grafici aggiuntivi.

Successivamente, esplora argomenti correlati come **how to insert picture**, **how to generate tables** o **how to apply document themes** per rendere i tuoi report automatizzati ancora più ricchi. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Inserisci grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserisci un semplice grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Inserisci grafico ad area in documento Word | Aspose.Words per .NET](/words/english/net/working-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}