---
category: general
date: 2026-10-13
description: Come formattare un grafico in Word con C# applicando un formato numerico
  personalizzato, ad esempio valuta, agli assi del grafico. Esempio di codice passo‑passo
  incluso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: it
lastmod: 2026-10-13
og_description: Come formattare un grafico in Word con C# ti consente di applicare
  un formato numerico personalizzato agli assi del grafico, garantendo che i valori
  compaiano come valuta, percentuali o qualsiasi modello tu desideri. Segui la guida
  passo‑passo.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Come formattare un grafico in Word con C# – formati numerici personalizzati
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Come formattare un grafico in Word con C# e formati numerici personalizzati
url: /it/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come formattare un grafico in Word con C# e formati numerici personalizzati

Formattare un grafico in Word con C# è una necessità comune quando è necessario presentare dati in modo professionale. Questa guida mostra come applicare un formato numerico personalizzato all'asse di un grafico utilizzando **Aspose.Words for .NET**, in modo che i valori appaiano esattamente come previsto.

Imparerai a caricare un file DOCX, individuare il primo grafico, leggere il formato corrente e poi impostare un nuovo modello, ad esempio una valuta con due decimali. Il tutorial copre anche come modificare il formato dell'asse del grafico per serie aggiuntive e come ripristinare il formato se necessario.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o versioni successive installate  
* Un progetto Visual Studio 2022 (o qualsiasi IDE che supporti .NET)  
* Il pacchetto NuGet **Aspose.Words for .NET** (`Aspose.Words`)  
* Un documento Word (`input.docx`) che contiene almeno un grafico

Puoi aggiungere il pacchetto con il seguente comando:

```bash
dotnet add package Aspose.Words
```

## Come formattare un grafico in Word usando Aspose.Words

Il programma completo seguente dimostra ogni passaggio necessario per **formattare** i valori dell'asse del grafico. Salva il file come `Program.cs` ed eseguilo dalla riga di comando o dal tuo IDE.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Spiegazione di ogni passaggio

| Passo | Perché è importante | Codice chiave |
|------|---------------------|---------------|
| **Carica il documento** | È necessario un oggetto `Document` per lavorare con il file Word. | `new Document("input.docx")` |
| **Recupera il grafico** | Gli oggetti `Chart` sono memorizzati come nodi `Shape`; il cast consente di utilizzare le API specifiche per i grafici. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **Accedi ai valori X** | La formattazione dell'asse viene applicata alla collezione di valori di una serie di dati. | `chart.ChartData.Series[0].XValues` |
| **Leggi il formato corrente** | Conoscere il `FormatCode` esistente ti aiuta a decidere se sostituirlo o integrarlo. | `xValues.FormatCode` |
| **Imposta formato personalizzato** | La proprietà `FormatCode` accetta qualsiasi modello compatibile con Excel, consentendo valute, percentuali, date, ecc. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **Salva il documento** | Il salvataggio delle modifiche scrive il nuovo formato dell'asse nel file DOCX. | `doc.Save("output_formatted.docx")` |

L'esecuzione del programma produce `output_formatted.docx`. Aprilo in Word e vedrai i valori dell'asse X del grafico visualizzati come **$1,234.00**, **$2,345.00**, … invece di numeri semplici.

## Applica un formato numerico personalizzato all'asse del grafico

Se devi **applicare un formato numerico personalizzato** all'asse Y o a serie aggiuntive, il processo è identico—basta puntare a una collezione diversa:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Consiglio professionale:** Usa le virgolette doppie all'interno della stringa di formato per incorporare caratteri letterali (ad esempio, `"$"` per la valuta). Escapa le virgolette come mostrato sopra.

## Formato numerico personalizzato – gestione della locale di Word

Word rispetta la locale del documento quando interpreta i formati numerici. Se il documento utilizza una locale non statunitense, potresti dover regolare la stringa di formato:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

Testare il formato su un documento con impostazioni di lingua tedesca conferma che i valori appaiono come **€ 1.234,00**.

## Come impostare le proprietà del grafico programmaticamente

Oltre alla formattazione dell'asse, spesso si desidera **impostare** titoli, legende o etichette dati del grafico. Ecco un breve snippet che dimostra come impostare il titolo del grafico dopo aver formattato l'asse:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Combinando questo con il formato numerico personalizzato ottieni un grafico completamente rifinito, pronto per la reportistica.

## Cambia dinamicamente il formato dell'asse del grafico in base all'input dell'utente

In applicazioni reali potresti consentire agli utenti di scegliere un formato a runtime. Il metodo seguente incapsula la logica di formattazione:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

Puoi chiamare `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` per la valuta o `SetAxisFormat(chart, 0, "0%")` per le percentuali. Questo approccio mantiene il codice principale pulito e supporta future estensioni.

## Casi limite e problemi comuni

| Situazione | Cosa controllare | Correzione suggerita |
|-----------|-------------------|----------------------|
| Il documento contiene **nessun grafico** | `GetChild` restituisce `null`, provocando un'eccezione di cast. | Verifica `null` prima del cast (vedi esempio). |
| Più grafici nello stesso documento | Il codice prende sempre il primo grafico (`indice 0`). | Itera su `doc.GetChildNodes(NodeType.Shape, true)` e filtra per `ShapeType.Chart`. |
| Serie **senza valori X** (ad esempio, grafici a torta) | L'accesso a `XValues` può generare `ArgumentOutOfRangeException`. | Verifica che `Series[i].XValues` non sia vuoto prima della formattazione. |
| Mancata corrispondenza della locale | Il simbolo della valuta potrebbe apparire in modo errato. | Imposta esplicitamente `xValues.FormatCode` con i simboli della locale appropriata. |

## Output previsto

Dopo aver eseguito il programma di esempio, apri **output_formatted.docx**. L'asse X del grafico dovrebbe visualizzare i numeri nel formato personalizzato scelto. Per l'esempio di valuta, le etichette dell'asse appaiono così:

```
$1,000.00
$2,000.00
$3,000.00
```

Se hai applicato il formato percentuale ai valori Y, le etichette dell'asse Y appaiono così:

```
10%
20%
30%
```

## Conclusione

Questo tutorial ti ha mostrato **come formattare un grafico** in Word con C# **applicando un formato numerico personalizzato** ai valori dell'asse. Ora disponi di un modello riutilizzabile per impostare valute, percentuali o qualsiasi altro modello numerico, oltre a indicazioni per gestire le locale, più serie e input dinamico dell'utente.

Successivamente, potresti esplorare **come impostare** titoli, etichette dati o persino esportare il grafico come immagine usando `ChartRenderer`. Quei argomenti si basano direttamente sui concetti trattati qui e ti aiuteranno a creare soluzioni di reporting completamente automatizzate.

---


## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Formato numerico per l'asse in un grafico](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Formato del numero dell'etichetta dati in un grafico](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Formato dell'asse X secondario e impostazione delle unità di visualizzazione a migliaia nei grafici a linee Word usando Aspose.Words per .NET](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}