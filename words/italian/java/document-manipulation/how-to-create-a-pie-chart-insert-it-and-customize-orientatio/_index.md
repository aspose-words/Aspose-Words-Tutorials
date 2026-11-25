---
category: general
date: 2026-11-25
description: Impara a creare un grafico a torta in Java, inserire il grafico a torta
  in un documento Word, far esplodere una fetta e cambiare l'orientamento del grafico
  con chiari esempi di codice.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- change chart orientation
- explode pie slice
- insert pie chart
- rotate pie chart
language: it
lastmod: 2026-11-25
og_description: Crea un grafico a torta in Java, inserisci il grafico a torta in un
  documento, esplodi una fetta del grafico e cambia l'orientamento del grafico con
  codice passo‑passo.
og_image_alt: Screenshot of a created pie chart with an exploded slice and rotated
  orientation
og_title: Crea un grafico a torta in Java – inserisci, esplodi la fetta e ruota
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a pie chart in Java, insert pie chart into a Word
    document, explode pie slice and change chart orientation with clear code examples.
  headline: How to create a pie chart, insert it, and customize orientation in Java
  type: TechArticle
tags:
- Java
- Aspose.Words
- Charting
title: Come creare un grafico a torta, inserirlo e personalizzare l'orientamento in
  Java
url: /it/java/document-manipulation/how-to-create-a-pie-chart-insert-it-and-customize-orientatio/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico a torta, inserirlo e personalizzare l'orientamento in Java

Se hai bisogno di **creare un grafico a torta** all'interno di un documento Word, questa guida ti mostra esattamente come farlo. Vedrai come **inserire un grafico a torta**, far esplodere una fetta per enfatizzarla e **cambiare l'orientamento del grafico** con una semplice rotazione.

Il tutorial copre tutto ciò di cui hai bisogno — dall'impostazione della libreria Aspose.Words per Java alla produzione di un file `.docx` finale che visualizza un grafico a torta ruotato ed esploso. Non è necessaria alcuna documentazione esterna; basta seguire i passaggi e eseguire il codice.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versioni successive installate.  
* Maven o Gradle per gestire le dipendenze.  
* Una licenza valida di Aspose.Words per Java (oppure usa la modalità di valutazione gratuita).

Aggiungi la dipendenza Aspose.Words al tuo `pom.xml` (Maven) o `build.gradle` (Gradle). Esempio per Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

> **Consiglio:** Mantieni la versione della libreria aggiornata; l'ultima release (24.10 al momento della stesura) include correzioni di bug per il rendering dei grafici.

## Passo 1: Creare un grafico a torta e inserirlo nel documento

Il primo passo è **creare oggetti grafico a torta** e incorporarli in un file Word. Il codice qui sotto costruisce un documento semplice, aggiunge un segnaposto per il grafico e inserisce un grafico a torta di dimensioni 400 × 300 pixel.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new Document and DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a pie chart of size 400x300
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Populate the chart with sample data
        chart.getSeries().clear(); // remove default series
        ChartSeries series = chart.getSeries().add("Sales", new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Save the document so far (optional)
        doc.save("Step1_InsertPieChart.docx");
    }
}
```

**Perché è importante:** `builder.insertChart` crea un segnaposto per il grafico che Aspose.Words converte automaticamente in un grafico OOXML quando il documento viene salvato. L'argomento `ChartType.PIE` indica alla libreria di renderizzare un grafico a torta, soddisfacendo il requisito di **inserire un grafico a torta**.

## Passo 2: Far esplodere una fetta per evidenziare un segmento

Far esplodere una fetta attira l'attenzione su un punto dati specifico. La riga seguente fa esplodere la prima fetta (indice 0) di 10 punti:

```java
// 4️⃣ Explode the first slice (index 0) by 10 points
chart.getSeries().get(0).setExplode(0, 10);
```

Puoi cambiare l'indice per puntare a una fetta diversa, o regolare la distanza di esplosione per un effetto più delicato. Far esplodere una fetta è il modo standard per **far esplodere una fetta di torta** in Aspose.Words.

## Passo 3: Cambiare l'orientamento del grafico ruotandolo

Ruotare il grafico offre una nuova prospettiva visiva. Usa `setRotationAngle` per ruotare l'intero grafico in senso orario (l'angolo è misurato in gradi).

```java
// 5️⃣ Rotate the entire chart by 45 degrees
chart.setRotationAngle(45);
```

La chiamata sopra soddisfa i requisiti di **ruotare il grafico a torta** e **cambiare l'orientamento del grafico**. È accettato qualsiasi angolo compreso tra 0 e 360 gradi.

## Esempio completo eseguibile

Mettendo tutto insieme, ecco un programma completo e autonomo che crea un grafico a torta, fa esplodere una fetta e ruota il grafico. Eseguilo dal tuo IDE o dalla riga di comando con `java -cp <classpath> PieChartDemo`.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300 pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Prepare data series (Sales per quarter)
        chart.getSeries().clear(); // remove default placeholder
        ChartSeries series = chart.getSeries().add(
                "Quarterly Sales",
                new String[] { "Q1", "Q2", "Q3", "Q4" },
                new double[] { 15000, 23000, 18000, 27000 });

        // Explode the first slice (Q1) by 10 points
        chart.getSeries().get(0).setExplode(0, 10);

        // Rotate the chart 45 degrees clockwise
        chart.setRotationAngle(45);

        // Save the final document
        doc.save("CreatePieChartDemo.docx");
        System.out.println("Document created successfully: CreatePieChartDemo.docx");
    }
}
```

### Output previsto

* Un file chiamato **CreatePieChartDemo.docx** appare nella directory di lavoro.  
* Aprendo il file in Microsoft Word si visualizza un grafico a torta di 400 × 300 pixel.  
* La prima fetta (Q1) è spostata verso l'esterno di 10 punti, creando un effetto di **esplosione della fetta di torta**.  
* L'intero grafico è inclinato di 45 gradi, dimostrando **cambio di orientamento del grafico** e **rotazione del grafico a torta**.

## Varianti comuni e casi limite

| Situazione | Come adattare il codice |
|------------|--------------------------|
| **Dimensione del grafico diversa** | Modifica gli argomenti `400, 300` in `insertChart`. |
| **Serie multiple** | Aggiungi altri oggetti `ChartSeries` a `chart.getSeries()`. |
| **Esplodere una fetta diversa** | Usa `setExplode(sliceIndex, distance)` con l'`sliceIndex` desiderato. |
| **Nessuna rotazione necessaria** | Ometti la chiamata a `setRotationAngle` o imposta l'angolo a `0`. |
| **Esportare in PDF invece di DOCX** | Dopo aver costruito il documento, chiama `doc.save("output.pdf")` con il formato PDF. |

> **Attenzione a:** L'uso di una distanza di esplosione negativa genera `IllegalArgumentException`. Fornisci sempre un valore non negativo.

## Suggerimento sulle prestazioni

Se generi molti grafici in un ciclo, riutilizza un unico `DocumentBuilder` e chiama `insertChart` solo per ogni iterazione. Questo riduce il consumo di memoria e velocizza l'elaborazione.

## Conclusione

Ora sai come **creare un grafico a torta**, **inserire un grafico a torta**, **far esplodere una fetta di torta** e **ruotare un grafico a torta** usando Aspose.Words per Java. L'esempio completo dimostra l'intero flusso di lavoro — dall'inizializzazione del documento al salvataggio di un file che visualizza un grafico a torta ruotato ed esploso.

Successivamente, potresti approfondire **il cambio di orientamento del grafico** applicando effetti 3‑D, oppure sperimentare con altri tipi di grafico come **Bar** o **Line**. Gli stessi pattern API si applicano, quindi estendere questo tutorial è semplice.

Sentiti libero di modificare i dati, l'indice della fetta o l'angolo di rotazione per adattarli alle tue esigenze di reporting, e condividi i tuoi risultati con la community!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to insert a pie chart into a Word document using Java](/words/english/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/)
- [How to explode pie slice in Java – Aspose.Words chart tutorial](/words/english/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}