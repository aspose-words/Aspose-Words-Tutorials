---
category: general
date: 2026-09-18
description: Scopri come creare un grafico radiale in un documento Word usando Java,
  aggiungere le etichette dei dati del grafico e inserire i dati della serie con un
  esempio di codice completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- add chart data labels
- add series data
- create blank word
- how to insert chart
language: it
lastmod: 2026-09-18
og_description: Crea un grafico radiale in un documento Word usando Java, aggiungi
  le etichette dei dati del grafico e inserisci i dati della serie in un unico tutorial.
og_image_alt: Radial chart displayed inside a generated Word document
og_title: Crea un grafico radiale in Word con Java – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn how to create radial chart in a Word document using Java, add
    chart data labels, and insert series data with a complete code example.
  headline: How to create radial chart in a Word document with Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Chart
- Word automation
title: Come creare un grafico radiale in un documento Word con Java
url: /it/java/using-document-elements/how-to-create-radial-chart-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico radiale in un documento Word con Java

Se devi creare un grafico radiale in un documento Word, questa guida ti mostra i passaggi esatti. Imparerai anche come aggiungere le etichette dei dati del grafico e inserire i dati della serie in modo che il grafico sia pronto per la presentazione.

Generare un grafico in modo programmatico elimina il lavoro di formattazione manuale e garantisce coerenza nei report. Il tutorial presuppone che tu abbia conoscenze di base di Java e una versione recente della libreria Aspose.Words per Java installata.

## Di cosa avrai bisogno

* Java 17 o versioni successive  
* Aspose.Words per Java (versione 23.12 o successiva)  
* Un IDE o uno strumento di build che possa risolvere le dipendenze Maven/Gradle  

Avere questi prerequisiti installati ti consente di eseguire l'esempio senza configurazioni aggiuntive.

## Come creare un grafico radiale in un documento Word

Il primo passo è creare un file Word vuoto che ospiterà il grafico. Un documento vuoto fornisce una tela pulita ed evita stili indesiderati.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

/* Step 1: Create a new blank Word document */
Document doc = new Document();

/* Step 2: Open a builder to add content */
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` rappresenta l'intero file .docx, mentre `DocumentBuilder` fornisce metodi per inserire elementi come paragrafi, tabelle e grafici.

## Come inserire il grafico

Successivamente inserisci il grafico stesso. Il metodo `insertChart` crea un oggetto grafico e lo posiziona nella posizione corrente del cursore del builder.

```java
import com.aspose.words.Chart;
import com.aspose.words.ChartType;

/* Step 3: Insert a polar (radial) chart with a width of 400 pt and height of 300 pt */
Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);
```

Un grafico polare visualizza i punti dati attorno a un asse centrale, ideale per mostrare informazioni cicliche. Le dimensioni sono espresse in punti (1 pt ≈ 1/72 pollice).

## Aggiungere dati della serie al grafico

Un grafico senza dati di serie è vuoto. Puoi aggiungere una serie manualmente o collegarla a una fonte dati. L'esempio sotto aggiunge una singola serie con tre punti dati.

```java
import com.aspose.words.ChartSeries;
import java.util.Arrays;

/* Step 4: Add a series and populate it with values */
ChartSeries series = chart.getSeries().add("Sample Series",
        Arrays.asList("Jan", "Feb", "Mar"),
        Arrays.asList(30.0, 45.0, 25.0));
```

`add` riceve un nome della serie, un elenco di etichette di categoria e un elenco di valori numerici corrispondenti. Puoi ripetere questo blocco per aggiungere altre serie (`addSeriesData`).

## Aggiungere etichette dei dati del grafico alla prima serie

Le etichette dei dati rendono il grafico leggibile senza dover passare il mouse sui punti. La riga seguente attiva le etichette di valore per la prima serie.

```java
/* Step 5: Show the numeric values as data labels */
chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);
```

Impostare `showValue` su `true` visualizza il valore di ogni punto direttamente sul grafico. Puoi anche abilitare i nomi delle categorie, le percentuali o le linee guida tramite lo stesso oggetto `DataLabelFormat`.

## Salvare il file Word

Dopo aver configurato il grafico, scrivi il documento su disco. Scegli una posizione a cui la tua applicazione possa accedere.

```java
/* Step 6: Save the document containing the radial chart */
doc.save("output/RadialChart.docx");
```

Il file `RadialChart.docx` ora contiene un grafico radiale pienamente funzionante con le etichette dei dati.

## Esempio completo funzionante

Di seguito trovi un programma autonomo che puoi copiare, compilare ed eseguire. Dimostra l'intero flusso di lavoro, dalla creazione di un documento Word vuoto al salvataggio di un grafico radiale con etichette dei dati.

```java
import com.aspose.words.*;

import java.util.Arrays;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Create a new blank Word document
        Document doc = new Document();

        // Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a polar (radial) chart with the desired dimensions
        Chart chart = builder.insertChart(ChartType.POLAR, 400, 300);

        // Add a series and populate it with sample data
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                Arrays.asList("Q1", "Q2", "Q3", "Q4"),
                Arrays.asList(15000.0, 23000.0, 18000.0, 21000.0));

        // Show the numeric values as data labels for the first series
        chart.getSeries().get(0).getDataLabelFormat().setShowValue(true);

        // Save the document containing the chart
        doc.save("output/RadialChart.docx");
    }
}
```

**Risultato atteso**

Quando apri `output/RadialChart.docx` in Microsoft Word, vedrai un grafico radiale intitolato *Quarterly Sales*. Ogni punto visualizza il suo valore numerico (ad es., “15000”) accanto al marcatore.

## Varianti comuni e casi limite

| Situazione | Modifica consigliata |
|------------|----------------------|
| Hai bisogno di un tipo di grafico diverso | Sostituisci `ChartType.POLAR` con qualsiasi altro valore enum `ChartType` (ad esempio, `ChartType.COLUMN`). |
| Il grafico deve utilizzare un intervallo Excel esterno | Usa `chart.setDataRange("Sheet1!A1:B5")` dopo aver creato il grafico e caricato la cartella di lavoro. |
| Vuoi nascondere la legenda | `chart.getLegend().setVisible(false);` |
| Il documento deve essere salvato come PDF | Chiama `doc.save("RadialChart.pdf");` – Aspose.Words converte automaticamente il grafico. |

Queste regolazioni mantengono intatta la logica di base adattando l'output a requisiti specifici.

## Suggerimenti professionali

* **Riutilizza il builder** – Puoi inserire più grafici nello stesso documento chiamando `builder.insertChart` più volte.  
* **Prestazioni** – Quando generi molti grafici, crea un'unica istanza di `DocumentBuilder` e riutilizzala per ridurre l'overhead di allocazione degli oggetti.  
* **Stilizzazione** – L'aspetto del grafico (colori, spessore delle linee) è controllato tramite i metodi `getSeries().get(i).getFormat()` dell'oggetto `Chart`. Sperimenta con queste impostazioni per allinearle all'identità visiva aziendale.

## Conclusione

Ora sai come creare un grafico radiale in un documento Word con Java, aggiungere dati di serie e aggiungere etichette dei dati del grafico prima di salvare il file. L'esempio completo può essere esteso per gestire serie aggiuntive, stili personalizzati o formati di output alternativi.

Esplora argomenti correlati come **come inserire un grafico** da fonti dati esterne, **creare documenti Word vuoti** con modelli predefiniti e **aggiungere dati di serie** in modo dinamico da database. Sperimenta con diversi tipi di grafico per scoprire quale visualizzazione comunica al meglio i tuoi dati.

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Imposta opzioni predefinite per le etichette dei dati in un grafico](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}