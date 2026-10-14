---
category: general
date: 2026-10-13
description: 'Salva il documento modificato dopo aver personalizzato un grafico a
  torta: far esplodere le fette, modificare l''angolo della prima fetta e mostrare
  le etichette percentuali in C#.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save modified document
- show percentage labels
- explode pie chart slices
- display percentages pie
- change first slice
language: it
lastmod: 2026-10-13
og_description: Salva il documento modificato dopo aver personalizzato un grafico
  a torta in C#. Scopri come separare le fette del grafico, cambiare l'angolo della
  prima fetta e mostrare le etichette percentuali.
og_image_alt: Screenshot of a Word document where the pie chart slices are exploded
  and percentage labels are displayed after saving the modified document
og_title: Salva documento modificato con fette di grafico a torta esplose – Guida
  C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: 'Save modified document after customizing a pie chart: explode slices,
    change first slice angle, and show percentage labels in C#.'
  headline: Save modified document with exploded pie chart slices in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word chart
- pie chart
- document manipulation
title: Salva il documento modificato con le fette di grafico a torta esplose in C#
url: /it/net/programming-with-charts/save-modified-document-with-exploded-pie-chart-slices-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salva documento modificato con fette di grafico a torta esplose in C#

Se hai bisogno di **salvare documento modificato** dopo aver modificato un grafico a torta di Word, questa guida ti mostra esattamente come fare. Imparerai a esplodere le fette del grafico a torta, a cambiare l'angolo della prima fetta e a mostrare le etichette percentuali—tutto con poche righe di codice C#.

Personalizzare i grafici è una necessità comune quando si generano report, fatture o dashboard in modo programmatico. Alla fine di questo tutorial sarai in grado di caricare un file DOCX, modificare l'aspetto del grafico e **salvare documento modificato** pronto per la distribuzione.

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+)
- Aspose.Words per .NET 23.10 o più recente (versione di prova gratuita o copia con licenza)
- Un file Word (`input.docx`) che contiene un singolo grafico a torta
- Visual Studio 2022 o qualsiasi IDE C#

> **Suggerimento:** Il pacchetto NuGet Aspose.Words viene aggiunto con `dotnet add package Aspose.Words`.

## Passo 1: Carica il documento Word che contiene il grafico

Il primo passo è aprire il file DOCX di origine. La classe `Document` rappresenta l'intero file Word in memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Load the Word document that contains the chart
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
```

Caricare il documento ti dà pieno accesso a ogni nodo, incluse le forme che ospitano i grafici.

## Passo 2: Recupera la prima forma di grafico dal documento

I grafici sono memorizzati all'interno dei nodi `Shape`. Puoi individuare il primo grafico con `GetChild`.

```csharp
        // Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
```

Se il documento contiene più grafici, regola l'indice (`0`) o itera attraverso la collezione. Questa riga garantisce di avere un riferimento all'oggetto `Chart` che modificherai.

## Passo 3: Esplodere le fette del grafico a torta

Esplodere una fetta la separa dal resto della torta, rendendo il grafico più leggibile. La proprietà `Explode` funziona per l'intera serie.

```csharp
        // Enable slice explosion so each slice is separated from the pie
        chart.PieChart.Explode = true;
```

Impostare `Explode` su `true` **esplode le fette del grafico a torta** per l'intera serie, utile quando vuoi che ogni fetta risalti.

## Passo 4: Cambia l'angolo della prima fetta

A volte è necessario che la prima fetta inizi a un angolo personalizzato, ad esempio per allinearsi a una linea guida di design.

```csharp
        // Set a custom start angle for the first slice (30 degrees)
        chart.PieChart.FirstSliceAngle = 30;
```

La proprietà `FirstSliceAngle` **cambia l'orientamento della prima fetta**, ruotando l'intera torta in modo che la prima fetta inizi a 30 gradi.

## Passo 5: Mostra le etichette percentuali sulle fette della torta

Mostrare il contributo numerico di ogni fetta è spesso richiesto nei report. Il flag `DataLabel.ShowPercentage` attiva i valori percentuali.

```csharp
        // Display percentage values on the data labels of the pie slices
        chart.PieChart.DataLabel.ShowPercentage = true;
```

Questo passo **mostra le etichette percentuali** direttamente sul grafico, soddisfacendo anche il requisito **display percentages pie**.

## Passo 6: Salva il documento modificato

Dopo aver applicato tutte le personalizzazioni, persisti le modifiche in un nuovo file. Il metodo `Save` scrive il DOCX aggiornato su disco.

```csharp
        // Save the modified document
        doc.Save(@"YOUR_DIRECTORY\output.docx");
    }
}
```

Ora hai un **salvare documento modificato** che contiene un grafico a torta esploso, una prima fetta ruotata e etichette percentuali visibili.

![Salva documento modificato mostrando grafico a torta esploso](/images/pie-chart-exploded.png "Salva documento modificato con fette di grafico a torta esplose e etichette percentuali")

*Lo screenshot illustra il risultato finale dopo che il documento è stato salvato.*

## Esempio completo, eseguibile

Unendo i pezzi, ecco il programma completo che puoi copiare‑incollare in un progetto console:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

namespace PieChartCustomizer
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source DOCX
            Document doc = new Document(@"YOUR_DIRECTORY\input.docx");

            // 2️⃣ Get the first chart shape
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Explode all slices
            chart.PieChart.Explode = true;

            // 4️⃣ Rotate the first slice to 30°
            chart.PieChart.FirstSliceAngle = 30;

            // 5️⃣ Show percentages on each slice
            chart.PieChart.DataLabel.ShowPercentage = true;

            // 6️⃣ Persist the changes
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Risultato atteso

Aprendo `output.docx` verrà mostrato un grafico a torta dove:

- Ogni fetta è leggermente separata (**exploded pie chart slices**)
- La prima fetta inizia con uno scostamento di 30 gradi (**change first slice**)
- Ogni fetta mostra il suo contributo in percentuale (**show percentage labels**, **display percentages pie**)
- Il file è stato **salvare documento modificato** senza alterare l'originale.

## Domande comuni e casi particolari

| Question | Answer |
|----------|--------|
| **E se il documento non contiene grafici?** | Il codice verifica `null` dopo `GetChild`. Se non esiste alcun grafico, puoi aggiungerne uno programmaticamente o interrompere con un messaggio chiaro. |
| **Posso esplodere solo una singola fetta?** | Sì. Usa `chart.PieChart.Series[0].DataPoints[i].Explosion = true;` dove `i` è l'indice della fetta. |
| **Come modifico il formato dell'etichetta (es., mostra valore + %)?** | Imposta `chart.PieChart.DataLabel.ShowValue = true;` e opzionalmente `chart.PieChart.DataLabel.ShowPercentage = true;` per combinare entrambi. |
| **Lo stile del grafico viene preservato dopo il salvataggio?** | Aspose.Words conserva tutti gli stili, inclusi colori e caratteri, quando **salvi documento modificato**. |
| **Posso elaborare più grafici nello stesso file?** | Itera tutti i nodi `Shape` con `NodeType.Shape` e filtra con `shape.HasChart`. Applica gli stessi passaggi a ciascun grafico. |

## Conclusione

Ora sai come **salvare documento modificato** dopo aver personalizzato programmaticamente un grafico a torta in Word. La guida ha coperto l'esplosione delle fette del grafico a torta, la modifica dell'angolo della prima fetta e la visualizzazione delle etichette percentuali—soddisfacendo i requisiti **show percentage labels**, **explode pie chart slices**, **display percentages pie**, e **change first slice**.

Successivamente, considera di esplorare:

- Aggiungere serie di dati dinamicamente (`chart.Series.Add(...)`)  
- Personalizzare la posizione della legenda e i titoli del grafico  
- Convertire il DOCX in PDF mantenendo lo stile del grafico  

Sentiti libero di sperimentare con angoli diversi, impostazioni di esplosione o formati di etichetta per adattarli alle tue esigenze di reporting. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come salvare un documento modificato in C# con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-docsaveoptions/how-to-save-edited-document-in-c-with-aspose-words-step-by-s/)
- [Aggiorna i dati della serie del grafico in un documento Word usando Aspose.Words per .NET](/words/english/net/programming-with-charts/modify-chart-series/)
- [Inserisci un grafico a colonne in un documento Word](/words/english/net/programming-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}