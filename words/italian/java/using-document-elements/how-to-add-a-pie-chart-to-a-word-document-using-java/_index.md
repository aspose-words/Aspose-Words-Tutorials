---
category: general
date: 2026-11-15
description: Scopri come aggiungere un grafico a torta a un documento Word con Aspose.Words
  per Java. Include la conversione in ciambella, la fetta esplosa e un esempio di
  codice completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add pie chart to word document
- Aspose.Words chart example
- Java pie chart tutorial
- create doughnut chart in Word
- explode pie slice Java
language: it
lastmod: 2026-11-15
og_description: Aggiungi un grafico a torta a un documento Word utilizzando Aspose.Words
  per Java. Questo tutorial mostra come far esplodere una fetta e trasformare il grafico
  in una ciambella.
og_image_alt: Screenshot of a Word document containing an exploded pie chart transformed
  into a doughnut
og_title: Aggiungi un grafico a torta a un documento Word con Java – guida passo‑passo
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  headline: How to add a pie chart to a Word document using Java
  type: TechArticle
- description: Learn how to add a pie chart to a Word document with Aspose.Words for
    Java. Includes doughnut conversion, exploded slice, and full code sample.
  name: How to add a pie chart to a Word document using Java
  steps:
  - name: Expected output
    text: 'Open `final-pie-doughnut.docx` in Microsoft Word:'
  - name: Adding multiple series
    text: 'If you need several series (e.g., stacked doughnut), add them sequentially:'
  - name: Custom colors
    text: 'You can assign a color to each slice via `ChartDataPoint.setFillFormat().setSolidFillColor()`:'
  - name: Working with an existing chart
    text: 'If the document already contains a chart and you only want to modify it,
      locate the chart shape:'
  - name: License handling
    text: 'Aspose.Words requires a license for production use. Place your `Aspose.Words.lic`
      file in the classpath and load it at application start:'
  - name: What to explore next
    text: '* **add bar chart to Word document** – similar steps but use `ChartType.BAR`.
      * **customize chart legends and titles** – use `pieChart.getTitle().setText("...")`
      and `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`. * **export the
      Word document as PDF** – change the `SaveFormat` to `PDF` for'
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Come aggiungere un grafico a torta a un documento Word usando Java
url: /it/java/using-document-elements/how-to-add-a-pie-chart-to-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi un grafico a torta a un documento Word – guida completa Java

Se hai bisogno di **aggiungere un grafico a torta a un documento Word** in modo programmatico, questo tutorial ti mostra esattamente come farlo con Aspose.Words for Java. Vedrai l'intero flusso di lavoro: caricamento di un DOCX, creazione di un grafico a torta, esplosione della prima fetta e conversione del grafico in una ciambella impostando la dimensione del foro.

La guida copre anche variazioni comuni — come aggiungere più serie, personalizzare i colori e gestire documenti che contengono già dei grafici — così potrai adattare il codice a progetti reali come report automatici o presentazioni dinamiche.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versioni successive (il codice si compila anche con JDK 11+)
* Maven 3.6+ o Gradle per la gestione delle dipendenze
* Una licenza Aspose.Words for Java (la versione di prova gratuita è sufficiente per i test)
* Una conoscenza di base della sintassi Java e della struttura di un progetto Maven

## Passo 1: Configura il progetto Maven e importa Aspose.Words

Crea un nuovo progetto Maven (o aggiungilo a uno esistente) e includi la dipendenza Aspose.Words:

```xml
<!-- pom.xml -->
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word-chart-demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- latest stable at time of writing -->
        </dependency>
    </dependencies>
</project>
```

> **Suggerimento:** Se usi Gradle, la voce equivalente è `implementation 'com.aspose:aspose-words:24.9'`.

La dipendenza fornisce le classi `Document`, `Chart` e `ChartType` necessarie per manipolare i grafici.

## Passo 2: Carica il documento di destinazione

Puoi partire da un file `.docx` esistente o creare un nuovo documento vuoto. L'esempio qui sotto carica un modello chiamato `input.docx` situato nella cartella `src/main/resources`.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load the Word document that will receive the chart
        Document doc = new Document("src/main/resources/input.docx");
        // Continue with chart creation...
    }
}
```

Se il file non esiste, Aspose.Words creerà automaticamente un nuovo documento vuoto quando chiami `new Document()` senza specificare un nome file.

## Passo 3: Crea un grafico a torta e inseriscilo nel documento

Aspose.Words tratta un grafico come una forma che può essere posizionata ovunque un paragrafo possa apparire. Il codice seguente crea un **grafico a torta**, aggiunge una singola serie di dati e inserisce il grafico dopo il primo paragrafo.

```java
import com.aspose.words.*;
import java.util.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        Document doc = new Document("src/main/resources/input.docx");

        // Create a new chart of type PIE
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // Prepare data for the series: categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // Add a new series to the chart
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // Insert the chart into the document after the first paragraph
        Paragraph firstParagraph = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);
        firstParagraph.appendChild(pieChart);
        
        // Save the document to verify the result
        doc.save("output/add-pie-chart.docx", SaveFormat.DOCX);
    }
}
```

**Perché questo passo è importante:**  
* `ChartType.PIE` indica ad Aspose.Words di renderizzare un tradizionale grafico a torta.  
* Aggiungere una serie con etichette di categoria e valori numerici popola automaticamente le fette.  
* Inserire il grafico come figlio di un `Paragraph` mantiene intatto il flusso del documento.

## Passo 4: Esplodi la prima fetta per evidenziarla

Una *fetta esplosa* attira l'attenzione su un punto dati specifico. L'API espone `setExplode(boolean)` su un oggetto `ChartSeries`. Impostandolo sulla prima serie (indice 0) la prima fetta verrà spostata verso l'esterno.

```java
// Explode the first slice (index 0) of the first series
pieChart.getSeries().get(0).setExplode(true);
```

> **Domanda comune:** *E se ho più serie?*  
> Puoi puntare a una serie specifica tramite il suo indice, ad esempio `pieChart.getSeries().get(1).setExplode(true)` per la seconda serie.

## Passo 5: Converti il grafico a torta in una ciambella impostando la dimensione del foro

Un grafico a ciambella è essenzialmente un grafico a torta con un centro vuoto. Aspose.Words ti permette di definire la dimensione del foro come percentuale del raggio del grafico.

```java
// Turn the pie chart into a doughnut with a 30% hole size
pieChart.setHoleSize(30);
```

Il metodo `setHoleSize` accetta valori da **0** (torta normale) a **100** (completamente vuoto). Un valore intorno a **30‑40** produce una ciambella visivamente equilibrata.

## Passo 6: Salva e verifica il risultato

Dopo tutte le modifiche, salva il documento. La riga seguente scrive il file nella cartella `output`.

```java
doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);
```

### Output previsto

Apri `final-pie-doughnut.docx` in Microsoft Word:

* Apparirà un grafico a ciambella dove si trovava il primo paragrafo.
* La fetta “Apples” è esplosa (leggermente separata dalle altre).
* Il grafico mostra quattro fette etichettate *Apples*, *Bananas*, *Cherries*, *Dates* con le percentuali fornite.

Se preferisci un output PDF, cambia il `SaveFormat` in `SaveFormat.PDF`.

## Gestione di casi limite e variazioni

### Aggiunta di più serie

Se ti servono diverse serie (ad esempio ciambella impilata), aggiungile in sequenza:

```java
double[] values2022 = {20, 30, 25, 25};
double[] values2023 = {25, 20, 30, 25};

ChartSeries s2022 = pieChart.getSeries().add("2022", categories, values2022);
ChartSeries s2023 = pieChart.getSeries().add("2023", categories, values2023);
```

### Colori personalizzati

Puoi assegnare un colore a ogni fetta tramite `ChartDataPoint.setFillFormat().setSolidFillColor()`:

```java
ChartDataPoint point = series.getDataPoints().get(0); // first slice
point.getFillFormat().setSolidFillColor(java.awt.Color.RED);
```

### Lavorare con un grafico esistente

Se il documento contiene già un grafico e vuoi solo modificarlo, individua la forma del grafico:

```java
NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
for (Node shapeNode : (Iterable<Node>) shapes) {
    Shape shape = (Shape) shapeNode;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart existingChart = shape.getChart();
        // Apply explode/holeSize changes here
    }
}
```

### Gestione della licenza

Aspose.Words richiede una licenza per l'uso in produzione. Posiziona il file `Aspose.Words.lic` nel classpath e caricalo all'avvio dell'applicazione:

```java
License license = new License();
license.setLicense("Aspose.Words.lic");
```

Non impostare una licenza aggiungerà una filigrana al documento generato.

## Esempio completo, eseguibile

Di seguito trovi la classe Java completa che incorpora tutti i passaggi discussi. Copiala in `src/main/java/com/example/AddPieChart.java` ed esegui `mvn compile exec:java`.

```java
package com.example;

import com.aspose.words.*;

public class AddPieChart {
    public static void main(String[] args) throws Exception {
        // Load license (optional for trial)
        // new License().setLicense("Aspose.Words.lic");

        // 1️⃣ Load the base document
        Document doc = new Document("src/main/resources/input.docx");

        // 2️⃣ Create a pie chart
        Chart pieChart = new Chart(doc, ChartType.PIE);

        // 3️⃣ Define categories and values
        String[] categories = {"Apples", "Bananas", "Cherries", "Dates"};
        double[] values = {30, 20, 25, 25};

        // 4️⃣ Add a series with the data
        ChartSeries series = pieChart.getSeries().add("Fruit Distribution", categories, values);

        // 5️⃣ Explode the first slice
        pieChart.getSeries().get(0).setExplode(true);

        // 6️⃣ Convert to doughnut (30% hole)
        pieChart.setHoleSize(30);

        // 7️⃣ Insert the chart after the first paragraph
        Paragraph firstPara = (Paragraph) doc.getFirstSection()
                .getBody()
                .getChild(NodeType.PARAGRAPH, 0, true);
        firstPara.appendChild(pieChart);

        // 8️⃣ Save the final document
        doc.save("output/final-pie-doughnut.docx", SaveFormat.DOCX);

        System.out.println("Chart added successfully. Check output/final-pie-doughnut.docx");
    }
}
```

L'esecuzione del programma produce il grafico a ciambella descritto in precedenza. Modifica `categories`, `values` o `holeSize` per adattarli ai tuoi dati.

## Conclusione

Ora sai come **aggiungere un grafico a torta a un documento Word** usando Java e Aspose.Words. Il tutorial ha coperto il caricamento di un documento, la creazione di un grafico a torta, l'esplosione di una fetta, la trasformazione del grafico in una ciambella e la gestione di variazioni comuni come più serie, colori personalizzati e grafici esistenti. Con queste basi potrai costruire strumenti di reporting automatici, generare presentazioni dinamiche o incorporare visualizzazioni ricche direttamente nei file Word.

### Cosa esplorare dopo

* **add bar chart to Word document** – passaggi simili ma usando `ChartType.BAR`.  
* **customize chart legends and titles** – usa `pieChart.getTitle().setText("...")` e `pieChart.getLegend().setPosition(LegendPosition.RIGHT)`.  
* **export the Word document as PDF** – cambia il `SaveFormat` in `PDF` per file pronti alla distribuzione.  
* **populate chart data from a database** – sostituisci gli array statici con i risultati di una query JDBC.

Sentiti libero di sperimentare con diversi tipi di grafico, fonti di dati e opzioni di stile. Buon coding!

## What Should You Learn Next?

The following tutorials cover closely related topics that build on the techniques demonstrated in this guide. Each resource includes complete working code examples with step-by-step explanations to help you master additional API features and explore alternative implementation approaches in your own projects.

- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)
- [Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide](/words/english/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}