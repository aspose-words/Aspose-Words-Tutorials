---
category: general
date: 2026-10-13
description: Scopri come regolare programmaticamente le etichette dei grafici in un
  documento Word usando C#. Questa guida copre la manipolazione dei grafici con Aspose.Words
  e l’allineamento delle etichette.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically adjust chart labels
- Aspose.Words chart manipulation
- C# chart data label
- Word document chart example
- modify chart label position
- set data label alignment
language: it
lastmod: 2026-10-13
og_description: Regola programmaticamente le etichette dei grafici in un documento
  Word usando C#. Segui questo tutorial completo per modificare la posizione delle
  etichette, l'allineamento e altro ancora.
og_image_alt: Screenshot showing programmatically adjust chart labels in a Word document
og_title: Regola programmaticamente le etichette dei grafici in Word – Guida passo‑passo
  in C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to programmatically adjust chart labels in a Word document
    using C#. This guide covers Aspose.Words chart manipulation and label alignment.
  headline: Programmatically adjust chart labels in a Word document with C#
  type: TechArticle
tags:
- chart labels
- C#
- Aspose.Words
title: Regolare programmaticamente le etichette del grafico in un documento Word con
  C#
url: /it/net/programming-with-charts/programmatically-adjust-chart-labels-in-a-word-document-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Regolare programmaticamente le etichette del grafico in un documento Word con C#

Se devi **regolare programmaticamente le etichette del grafico** in un documento Word, questa guida ti mostra esattamente come farlo con C#. Che tu stia generando report, automatizzando dashboard o personalizzando template, vedrai un esempio completo e funzionante che modifica la posizione e l’allineamento delle etichette di un grafico all’interno di un file .docx.

Imparerai anche come utilizzare le tecniche di **manipolazione dei grafici di Aspose.Words**, gestire più serie e evitare le insidie più comuni quando lavori con gli oggetti **C# chart data label**.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 (o successivo) installato  
* Visual Studio 2022 (o qualsiasi IDE C#)  
* Il pacchetto NuGet **Aspose.Words for .NET** (`Install-Package Aspose.Words`)  
* Un documento Word (`input.docx`) che contenga almeno un grafico  

Questi elementi sono necessari per l'**esempio di grafico in documento Word** che modificheremo.

## Passo 1: Configurare il progetto e importare i namespace

Crea un nuovo progetto console e aggiungi le direttive `using` necessarie. Questo prepara l’ambiente per **regolare programmaticamente le etichette del grafico**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the source and destination files
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the document that contains a chart
            Document doc = new Document(inputPath);
```

*Perché questo passo?*  
Il caricamento del documento ti dà accesso all’albero interno dell'**esempio di grafico in documento Word**, dove i grafici sono memorizzati come nodi shape.

## Passo 2: Individuare la prima shape del grafico

I grafici sono memorizzati come nodi `Shape`. Il codice seguente recupera il primo grafico nel documento, che è il bersaglio per le nostre modifiche alle etichette.

```csharp
            // Retrieve the first chart shape in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }
```

*Perché questo passo?*  
Il metodo `GetChild` ricerca ricorsivamente (`true`) e restituisce il primo nodo di tipo `Shape`. Il cast a `Chart` consente di lavorare con l’API specifica del grafico.

## Passo 3: Accedere all’etichetta dati da modificare

Ogni serie in un grafico ha una raccolta di etichette dati. Per un grafico semplice, la prima etichetta è spesso sufficiente. Il codice sotto mostra come raggiungerla.

```csharp
            // Access the first series' first data label
            ChartSeries series = chart.Series[0];
            ChartDataLabel dataLabel = series.DataLabelCollection[0];
```

*Perché questo passo?*  
`ChartSeries` rappresenta una serie di punti. `DataLabelCollection` contiene le etichette per quella serie, permettendo un controllo preciso su posizione e allineamento.

## Passo 4: Modificare la posizione e l’allineamento dell’etichetta

Ora **regoliamo programmaticamente le etichette del grafico** impostando la posizione, l’allineamento orizzontale e quello verticale. Queste proprietà corrispondono alle opzioni che vedi nell’interfaccia di Word.

```csharp
            // Set the label's position relative to the data point
            dataLabel.Position = DataLabelPosition.OutsideEnd; // Options: OutsideEnd, InsideEnd, etc.

            // Align the label horizontally and vertically
            dataLabel.HorizontalAlignment = HorizontalAlignment.Center;
            dataLabel.VerticalAlignment = VerticalAlignment.Top;
```

*Perché queste impostazioni?*  

* `OutsideEnd` posiziona l’etichetta appena fuori dalla fine di ogni barra o colonna, migliorando la leggibilità.  
* `HorizontalAlignment.Center` mantiene il testo centrato sopra il punto, mentre `VerticalAlignment.Top` allinea il bordo superiore dell’etichetta al punto dati, evitando sovrapposizioni con altri elementi.

### Suggerimento professionale
Se un grafico ha più serie, itera su `chart.Series` e applica le stesse impostazioni a ciascuna `DataLabelCollection`. In questo modo otterrai un aspetto coerente su tutto il grafico.

```csharp
            // Example: adjust all series in the chart
            foreach (ChartSeries s in chart.Series)
            {
                foreach (ChartDataLabel lbl in s.DataLabelCollection)
                {
                    lbl.Position = DataLabelPosition.OutsideEnd;
                    lbl.HorizontalAlignment = HorizontalAlignment.Center;
                    lbl.VerticalAlignment = VerticalAlignment.Top;
                }
            }
```

## Passo 5: Salvare il documento modificato

Dopo aver regolato le etichette, persisti le modifiche in un nuovo file. Questo completa il processo di **modifica della posizione dell’etichetta del grafico**.

```csharp
            // Save the updated document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Quando apri `output.docx`, vedrai che ogni etichetta del grafico è stata spostata alla fine esterna del suo punto dati, centrata orizzontalmente e allineata in alto verticalmente.

## Casi limite e varianti

| Situazione | Cosa controllare | Approccio consigliato |
|------------|------------------|-----------------------|
| **Grafici multipli** nello stesso documento | `GetChild` restituisce solo il primo grafico. | Usa `doc.GetChildNodes(NodeType.Shape, true)` per iterare su tutte le shape dei grafici. |
| **Serie senza etichette dati** | `DataLabelCollection` potrebbe essere vuota. | Verifica `series.HasDataLabels` prima di accedere alla collezione. |
| **Tipi di grafico diversi** (torta, linea, dispersione) | Non tutti i valori di `DataLabelPosition` sono validi. | Usa `DataLabelPosition.Auto` per i grafici che decidono automaticamente la migliore posizione. |
| **Localizzazione** | Le costanti di allineamento sono indipendenti dalla lingua, ma il testo renderizzato potrebbe richiedere supporto da destra a sinistra. | Imposta `dataLabel.TextDirection` se hai bisogno di lingue RTL. |

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Sostituisci `YOUR_DIRECTORY` con un percorso di cartella reale.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelAdjustment
{
    class Program
    {
        static void Main(string[] args)
        {
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            string outputPath = @"YOUR_DIRECTORY\output.docx";

            // Load the Word document that contains a chart
            Document doc = new Document(inputPath);

            // Retrieve the first chart shape from the document
            Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // Loop through all series and adjust each data label
            foreach (ChartSeries series in chart.Series)
            {
                foreach (ChartDataLabel label in series.DataLabelCollection)
                {
                    label.Position = DataLabelPosition.OutsideEnd;
                    label.HorizontalAlignment = HorizontalAlignment.Center;
                    label.VerticalAlignment = VerticalAlignment.Top;
                }
            }

            // Save the modified document
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Risultato atteso:** L’apertura di `output.docx` mostra ogni etichetta del grafico posizionata fuori dal punto dati, centrata orizzontalmente e allineata in alto—esattamente l’effetto di **regolare programmaticamente le etichette del grafico** che hai implementato.

## Conclusione

Ora sai come **regolare programmaticamente le etichette del grafico** in un documento Word usando C#. Il tutorial ha coperto:

* Caricamento di un documento con **manipolazione dei grafici di Aspose.Words**  
* Accesso a una **C# chart data label**  
* Modifica della **posizione dell’etichetta del grafico** e dell’allineamento  
* Salvataggio del file e gestione dei casi limite più comuni  

Da qui puoi esplorare scenari più avanzati, come personalizzare i caratteri delle etichette, aggiungere formattazione condizionale o aggiornare più grafici in un processo batch. Sperimenta con le diverse opzioni di `DataLabelPosition` per trovare lo stile più adatto ai tuoi report.

---

*Pronto a potenziare la tua pipeline di reporting automatizzato? Prova ad aggiungere formati numerici personalizzati alle etichette o a esportare il grafico come immagine per usarlo nei PDF.*

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Set Uniform Data Labels in a Column Chart Using Aspose.Words for .NET](/words/english/net/programming-with-charts/uniform-data-labels/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)
- [Update Chart Series Data in a Word Document Using Aspose.Words for .NET](/words/english/net/programming-with-charts/modify-chart-series/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}