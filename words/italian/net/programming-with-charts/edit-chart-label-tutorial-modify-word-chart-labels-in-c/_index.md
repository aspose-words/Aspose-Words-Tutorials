---
category: general
date: 2026-09-11
description: Tutorial per modificare le etichette del grafico che mostra come cambiare
  la posizione dell'etichetta del grafico, personalizzare l'etichetta dei dati del
  grafico, nascondere il nome della categoria del grafico e visualizzare il valore
  dell'etichetta del grafico con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: it
lastmod: 2026-09-11
og_description: Il tutorial su come modificare le etichette del grafico ti guida a
  cambiare la posizione dell'etichetta del grafico, a personalizzare l'etichetta dei
  dati del grafico, a nascondere il nome della categoria del grafico e a mostrare
  il valore dell'etichetta del grafico utilizzando Aspose.Words per .NET.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Tutorial per modificare le etichette del grafico – personalizza le etichette
  dei grafici di Word in C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Tutorial per modificare le etichette del grafico – modifica le etichette dei
  grafici di Word in C#
url: /it/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modifica tutorial etichette grafico – modifica le etichette dei grafici Word in C#

Se hai bisogno di **edit chart label tutorial** per un documento Word, questa guida ti mostra esattamente come cambiare la posizione dell’etichetta del grafico, personalizzare l’etichetta dei dati del grafico, nascondere il nome della categoria del grafico e visualizzare il valore dell’etichetta del grafico utilizzando Aspose.Words per .NET. Vedrai un esempio completo e eseguibile che puoi inserire in qualsiasi progetto C#.

Lavorare con le etichette dei grafici è una necessità comune quando si generano report, fatture o dashboard in modo programmatico. Questo tutorial copre ogni passaggio—dal caricamento del documento al salvataggio delle modifiche—così potrai produrre grafici curati senza interventi manuali.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o versioni successive installate  
* Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione temporanea)  
* Visual Studio 2022 o qualsiasi IDE compatibile con C#  
* Un file Word (`Chart.docx`) che contenga almeno un grafico  

Non sono necessari pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Passo 1: Configura il progetto e importa gli spazi dei nomi

Crea una nuova applicazione console e aggiungi il pacchetto NuGet Aspose.Words:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

Apri `Program.cs` e importa gli spazi dei nomi richiesti:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Questi spazi dei nomi ti danno accesso alla classe `Document` per gestire i file Word e alle classi `Chart` per manipolare gli elementi del grafico.

## Passo 2: Carica il documento Word che contiene un grafico

La prima riga operativa carica il documento sorgente. Sostituisci `YOUR_DIRECTORY` con il percorso reale dove si trova `Chart.docx`.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

Il caricamento del documento crea una rappresentazione in memoria che puoi attraversare e modificare.

## Passo 3: Recupera il primo grafico nel documento

I grafici sono memorizzati come nodi figlio di tipo `NodeType.Chart`. Il metodo `GetChild` ricerca nell’albero del documento e restituisce il grafico che desideri modificare.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Se il documento contiene più grafici, puoi cambiare l’indice per puntare a uno diverso.

## Passo 4: Accedi e personalizza l’etichetta dei dati della prima serie

Ogni serie di un grafico ha un oggetto `DataLabel` che controlla come appare l’etichetta. Il codice qui sotto dimostra le quattro personalizzazioni chiave richieste dalle parole chiave secondarie del tutorial.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Perché queste impostazioni sono importanti**

* `DataLabelPosition.Center` sposta l’etichetta dalla posizione predefinita esterna al punto al centro del punto dati, rendendo il grafico più leggibile quando i punti sono molto ravvicinati.  
* Impostare un `Separator` personalizzato ti consente di controllare come il nome della serie, il valore e le altre parti vengono concatenati.  
* Nascondere il nome della categoria (`ShowCategoryName = false`) riduce il disordine visivo quando la categoria è già evidente sull’asse.  
* Abilitare `ShowValue` garantisce che il valore reale dei dati sia visibile, cosa spesso richiesta per report finanziari o statistici.

## Passo 5: Salva il documento modificato

Dopo aver regolato le proprietà dell’etichetta, persisti le modifiche in un nuovo file:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Il nuovo file (`CustomLabelChart.docx`) contiene lo stesso layout del grafico ma con l’aspetto dell’etichetta definito da te.

## Codice sorgente completo

Di seguito trovi il programma completo, pronto per l’esecuzione. Copialo in `Program.cs`, adatta i percorsi dei file e avvia il progetto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Risultato atteso

Apri `CustomLabelChart.docx` in Microsoft Word. Dovresti vedere l’etichetta della prima serie del grafico centrata su ogni punto dati, visualizzando solo il valore numerico e usando “; ” come separatore. I nomi delle categorie non appariranno più accanto ai valori.

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|--------|
| **E se il documento non contiene alcun grafico?** | L’esempio verifica la presenza di un grafico `null` e termina in modo pulito con un messaggio sulla console. |
| **Posso modificare le etichette per più serie?** | Sì. Itera su `chart.Series` e applica le stesse impostazioni di `DataLabel` a ciascuna `Series[i].DataLabel`. |
| **Come cambio lo stile del carattere dell’etichetta?** | Usa `label.Font` (ad esempio `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **`DataLabelPosition.Center` è supportato per tutti i tipi di grafico?** | La maggior parte dei grafici 2‑D lo supporta. Per i grafici 3‑D, alcune posizioni potrebbero essere ignorate da Word. |
| **È necessaria una licenza per Aspose.Words?** | La modalità di valutazione funziona ma aggiunge una filigrana. Una licenza rimuove la filigrana e sblocca tutte le funzionalità. |

## Consigli professionali

* **Elaborazione batch:** Incapsula la logica di caricamento e salvataggio in un metodo che accetta percorsi di input e output. Questo rende semplice processare decine di documenti in un ciclo.  
* **Prestazioni:** Riutilizza un’unica istanza di `Document` quando modifichi più grafici nello stesso file per evitare I/O ripetuti.  
* **Test:** Verifica le modifiche alle etichette automatizzando un confronto visivo (ad es., usando un visualizzatore Word senza interfaccia) se devi convalidare l’output nelle pipeline CI.

## Prossimi passi

Ora che conosci le basi del **edit chart label tutorial**, considera di approfondire:

* **Change chart label position** per altre serie o diversi tipi di grafico  
* **Customize chart data label** formattando numeri, colori dei caratteri o riempimenti di sfondo  
* **Hide chart category name** mantenendo comunque il nome della serie per grafici a più serie  
* **Show chart label value** insieme ai valori percentuali per i grafici a torta  

Questi argomenti ampliano il tuo controllo sull’estetica dei grafici Word e ti preparano a scenari di reporting avanzati.

---

*Buona programmazione! Se questo tutorial ti è stato utile, condividilo con i colleghi o contribuisci con miglioramenti su GitHub.*

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Customize Chart Data Label](/words/english/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/german/net/programming-with-charts/chart-data-label/)
- [Chart Data Label](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}