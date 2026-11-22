---
category: general
date: 2026-11-22
description: Crea un grafico a torta in Java e impara a impostare la dimensione del
  grafico, aggiungere le etichette dei dati, mostrare le percentuali e ruotare la
  prima fetta per un impatto visivo chiaro.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- set chart size
- show percentages pie chart
- add data labels pie chart
- rotate pie chart slice
language: it
lastmod: 2026-11-22
og_description: Crea un grafico a torta in Java, imposta la dimensione del grafico,
  mostra le percentuali sulle etichette dei dati e ruota la prima fetta—tutto in un
  unico esempio eseguibile.
og_image_alt: Screenshot of a created pie chart showing custom size, percentage labels,
  and a rotated first slice
og_title: Crea un grafico a torta con dimensioni personalizzate, etichette e rotazione
  in Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  headline: Create pie chart with custom size, data labels, and rotation in Java
  type: TechArticle
- description: Create pie chart in Java and learn how to set chart size, add data
    labels, show percentages, and rotate the first slice for clear visual impact.
  name: Create pie chart with custom size, data labels, and rotation in Java
  steps:
  - name: Why each step matters
    text: '| Step | Purpose | How it relates to the keywords | |------|---------|--------------------------------|
      | **Insert chart** | **Create pie chart** – the core object that will render
      the visual. | Directly satisfies the *create pie chart* requirement. | | **Set
      dimensions** | The `addChart(..., 400, 3'
  - name: 1. Insert a pie chart and set chart size
    text: '```java IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50,
      400, 300); ```'
  - name: 2. Populate the chart with data
    text: The demo adds three categories and a single series. Replace the hard‑coded
      numbers with data from a database, CSV, or user input as needed.
  - name: 3. Show percentages on each slice
    text: '```java series.getDataLabelFormat().setShowPercentage(true); ```'
  - name: 4. Add detailed data labels
    text: '```java series.getDataLabelFormat().setShowCategoryName(false); series.getDataLabelFormat().setShowLeaderLines(false);
      ```'
  - name: 5. Rotate the first slice
    text: '```java chart.setFirstSliceAngle(45); ```'
  - name: 6. Save and view the result
    text: 'Running the program produces `output/PieChartDemo.pptx`. Open it in PowerPoint
      or any compatible viewer to see the final pie chart:'
  - name: What’s next?
    text: '* Explore other chart types (Bar, Line, Area) using the same `ChartType`
      enum. * Combine multiple charts on a single slide for dashboards. * Export charts
      to PNG or SVG for use in web applications.'
  type: HowTo
tags:
- Java
- charts
- Aspose.Slides
- data‑visualization
title: Crea un grafico a torta con dimensioni personalizzate, etichette dei dati e
  rotazione in Java
url: /it/java/getting-started/create-pie-chart-with-custom-size-data-labels-and-rotation-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un grafico a torta con dimensioni personalizzate, etichette dati e rotazione in Java

Se hai bisogno di **create pie chart** in Java, questa guida ti accompagna passo passo attraverso l'intero processo. Imparerai come **set chart size**, abilitare **show percentages pie chart**, aggiungere **data labels pie chart** e **rotate pie chart slice** in modo che la prima fetta inizi con un angolo di 45 gradi.

L'esempio utilizza **Aspose.Slides for Java**, una libreria ampiamente usata per manipolare file PowerPoint. Gli stessi concetti si applicano ad altre librerie di grafici; basta sostituire le chiamate API con le equivalenti nel tuo toolkit.

## Prerequisiti

* Java 17 o versioni successive installate  
* Maven 3.8+ (o Gradle) per la gestione delle dipendenze  
* Una conoscenza di base della sintassi Java  
* Accesso al binario di Aspose.Slides for Java (puoi ottenere una prova gratuita dal sito ufficiale)

Aggiungi la dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-slides</artifactId>
    <version>24.9</version> <!-- latest version as of November 2026 -->
</dependency>
```

## Crea un grafico a torta – esempio completo

Il programma seguente crea una diapositiva PowerPoint che contiene un grafico a torta con dimensioni personalizzate, etichette dati percentuali e una prima fetta ruotata.

```java
package com.example.piechart;

import com.aspose.slides.*;
import com.aspose.slides.charts.*;

public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a presentation
        Presentation pres = new Presentation();

        // 2️⃣ Add a blank slide
        ISlide slide = pres.getSlides().addEmptySlide(pres.getLayoutSlides().get_Item(0));

        // 3️⃣ Insert a pie chart (create pie chart)
        IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
        // The dimensions above also demonstrate set chart size

        // 4️⃣ Populate the chart with sample data
        IChartDataWorkbook workbook = chart.getChartData().getChartDataWorkbook();

        // Clear the default series & categories
        chart.getChartData().getSeries().clear();
        chart.getChartData().getCategories().clear();

        // Add categories (slices)
        chart.getChartData().getCategories().add(workbook.getCell(0, "A1", "Category A"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A2", "Category B"));
        chart.getChartData().getCategories().add(workbook.getCell(0, "A3", "Category C"));

        // Add a series and assign values
        IChartSeries series = chart.getChartData().getSeries().add(
                workbook.getCell(0, "B1", "Series 1"),
                chart.getType());

        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B1", 30));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B2", 45));
        series.getDataPoints().addDataPointForPieSeries(workbook.getCell(0, "B3", 25));

        // 5️⃣ Enable percentage display on data labels (show percentages pie chart)
        series.getDataLabelFormat().setShowPercentage(true);
        series.getDataLabelFormat().setShowCategoryName(false);
        series.getDataLabelFormat().setShowLegendKey(false);
        series.getDataLabelFormat().setShowSeriesName(false);
        series.getDataLabelFormat().setShowValue(false);
        series.getDataLabelFormat().setShowLeaderLines(false);

        // 6️⃣ Rotate the chart so the first slice starts at 45 degrees (rotate pie chart slice)
        chart.setFirstSliceAngle(45);

        // 7️⃣ Save the presentation
        String outPath = "output/PieChartDemo.pptx";
        pres.save(outPath, SaveFormat.Pptx);
        System.out.println("Presentation saved to " + outPath);
    }
}
```

### Perché ogni passaggio è importante

| Passo | Scopo | Come si relaziona alle parole chiave |
|------|---------|--------------------------------|
| **Insert chart** | **Create pie chart** – l'oggetto principale che renderà il grafico. | Soddisfa direttamente il requisito *create pie chart*. |
| **Set dimensions** | La chiamata `addChart(..., 400, 300)` dimostra **set chart size**. | Controlla la larghezza (400 px) e l'altezza (300 px). |
| **Show percentages** | `setShowPercentage(true)` fa sì che il grafico **show percentages pie chart** su ogni fetta. | Gli utenti spesso hanno bisogno di percentuali invece dei valori grezzi. |
| **Add data labels** | La configurazione `DataLabelFormat` aggiunge **data labels pie chart** con la visibilità desiderata. | Le etichette migliorano la leggibilità e sono personalizzabili. |
| **Rotate slice** | `setFirstSliceAngle(45)` ruota il grafico in modo che la prima fetta inizi con un angolo di 45 gradi, soddisfacendo **rotate pie chart slice**. | Migliora l'enfasi visiva per una fetta particolare. |

## Analisi passo‑passo

### 1. Inserisci un grafico a torta e imposta la dimensione del grafico

```java
IChart chart = slide.getShapes().addChart(ChartType.Pie, 50, 50, 400, 300);
```

*Il metodo `addChart` crea il grafico e contemporaneamente **set chart size** a 400 × 300 punti.*  
Se hai bisogno di una dimensione diversa, modifica gli ultimi due argomenti.

### 2. Popola il grafico con i dati

La demo aggiunge tre categorie e una singola serie. Sostituisci i numeri codificati con dati provenienti da un database, CSV o input dell'utente secondo necessità.

### 3. Mostra le percentuali su ogni fetta

```java
series.getDataLabelFormat().setShowPercentage(true);
```

*Abilitare `setShowPercentage(true)` garantisce che il grafico **show percentages pie chart** calcoli automaticamente la quota di ciascuna fetta sul totale.*

### 4. Aggiungi etichette dati dettagliate

```java
series.getDataLabelFormat().setShowCategoryName(false);
series.getDataLabelFormat().setShowLeaderLines(false);
```

Puoi attivare altre opzioni di etichetta (`setShowValue`, `setShowSeriesName`, ecc.) per personalizzare l'esperienza **add data labels pie chart**.

### 5. Ruota la prima fetta

```java
chart.setFirstSliceAngle(45);
```

*Chiamare `setFirstSliceAngle(45)` **rotate pie chart slice** così che il primo segmento inizi con un angolo di 45 gradi, facendolo risaltare.*

### 6. Salva e visualizza il risultato

Eseguendo il programma si genera `output/PieChartDemo.pptx`. Aprilo in PowerPoint o in qualsiasi visualizzatore compatibile per vedere il grafico a torta finale:

![Esempio di creazione di grafico a torta](images/pie_chart_example.png){.align-center alt="Screenshot di un grafico a torta creato con dimensioni personalizzate, etichette percentuali e una prima fetta ruotata"}

L'immagine sopra dimostra il risultato **create pie chart**, confermando che dimensioni, etichette, percentuali e rotazione sono state applicate correttamente.

## Variazioni comuni e casi limite

| Situazione | Adeguamento |
|-----------|------------|
| Dimensioni del grafico diverse | Cambia i parametri di larghezza/altezza in `addChart`. |
| Serie multiple | Aggiungi oggetti `IChartSeries` aggiuntivi; ogni serie può avere le proprie impostazioni di etichetta. |
| Formato etichetta personalizzato | Usa `series.getDataLabelFormat().setNumberFormat("0.0%")` per controllare le cifre decimali. |
| Rotazione a un altro angolo | Passa qualsiasi intero (0‑360) a `setFirstSliceAngle`. |
| Esportazione come immagine | Dopo il salvataggio, chiama `chart.writeAsSvg(outPath)` o `chart.writeAsPng(outPath)` per una versione raster. |

> **Consiglio professionale:** Se prevedi di generare molti grafici in un ciclo, riutilizza lo stesso oggetto `Presentation` e sostituisci solo i dati del grafico. Questo riduce il consumo di memoria e velocizza l'elaborazione.

## Conclusione

Ora sai come **create pie chart** in Java, **set chart size**, abilitare **show percentages pie chart**, **add data labels pie chart** e **rotate pie chart slice** per una migliore enfasi visiva. L'esempio completo e eseguibile dimostra ogni passaggio dall'inizializzazione al salvataggio del file PowerPoint finale.

### Cosa fare dopo?

* Esplora altri tipi di grafico (Bar, Line, Area) utilizzando lo stesso enum `ChartType`.  
* Combina più grafici in una singola diapositiva per cruscotti.  
* Esporta i grafici in PNG o SVG per l'uso in applicazioni web.  

Sentiti libero di sperimentare con colori, legende ed effetti di animazione—le tue visualizzazioni dei dati sono limitate solo dalla fantasia. Buon lavoro con i grafici!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [come inserire un grafico a torta in Word – aggiungere etichetta dati percentuale](/words/english/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/)
- [Come esplodere una fetta di torta in Java – tutorial grafico Aspose.Words](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Inserire un grafico a torta in Java – Esplodi, ruota e evidenzia le fette](/words/english/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}