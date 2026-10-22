---
category: general
date: 2026-09-24
description: Inserisci un grafico a torta in un DOCX usando Aspose.Words per Java.
  Impara a impostare la dimensione del foro, a far esplodere una fetta di torta, a
  evidenziare una fetta del grafico a torta e a creare un grafico DOCX senza sforzo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart word
- set hole size
- explode pie slice
- highlight pie chart slice
- create docx chart
language: it
lastmod: 2026-09-24
og_description: Inserisci un grafico a torta in un DOCX con Aspose.Words per Java.
  Impara a impostare la dimensione del foro, far esplodere una fetta di torta, evidenziare
  una fetta del grafico a torta e creare un grafico DOCX in pochi minuti.
og_image_alt: Screenshot of a Word document displaying a formatted pie chart created
  with Java
og_title: Inserisci la parola diagramma a torta in Java – tutorial passo‑passo
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  headline: Insert pie chart word in Java – complete guide
  type: TechArticle
- description: Insert pie chart word in a DOCX using Aspose.Words for Java. Learn
    to set hole size, explode pie slice, highlight pie chart slice, and create docx
    chart effortlessly.
  name: Insert pie chart word in Java – complete guide
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well) * Aspose.Words
      for Java library (version 23.9 or newer) * An IDE or build tool (Maven/Gradle)
      that can resolve the Aspose.Words dependency'
  - name: Why this matters
    text: '`Document` represents the whole Word file, while `DocumentBuilder` is the
      high‑level API that lets you insert paragraphs, tables, and charts without dealing
      with low‑level XML. Starting with a clean document ensures that the chart you
      add is the only content, which is perfect for learning or for gen'
  - name: Practical tip
    text: If you later decide to switch to a doughnut chart, simply change the `holeSize`
      value to a percentage (e.g., `30`). The same API works for both chart types.
  - name: Why explode?
    text: An exploded slice draws the reader’s eye to the most important data point—perfect
      for dashboards or executive summaries. The value `20` means 20 % of the radius;
      you can adjust it between `0` (no explosion) and `100` (fully detached).
  - name: Expert note
    text: Changing the fill color of a specific slice requires accessing the `DataPoint`
      object. If you have multiple series, iterate through `series.getDataPoints()`
      and apply styles conditionally.
  - name: Pro tip
    text: Always call `setHoleSize(0)` **after** `insertChart`. If you set it before
      insertion, Aspose.Words will revert to the default doughnut size once the chart
      is created.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart formatting
title: Inserire il grafico a torta in Java – guida completa
url: /it/java/using-document-elements/insert-pie-chart-word-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserire un grafico a torta in Java – guida completa

Se hai bisogno di **inserire un grafico a torta** in un file DOCX, questo tutorial ti mostra esattamente come farlo con Aspose.Words per Java. Vedrai l'intero flusso di lavoro, dalla creazione del documento alla personalizzazione del grafico in modo che la fetta sia esplosa, la dimensione del foro sia impostata a zero e la fetta sia evidenziata.

Lavorare con i grafici nei documenti Word spesso sembra un'attività separata dall'elaborazione del testo, ma Aspose.Words unifica entrambi. Nei passaggi seguenti imparerai anche come **creare un grafico docx** pronto per essere aperto in Microsoft Word, Google Docs o qualsiasi altro visualizzatore compatibile con DOCX.

## Cosa otterrai

* **Inserire un grafico a torta** in un documento vuoto  
* **Impostare la dimensione del foro** per trasformare il grafico in una torta completa (senza ciambella)  
* **Esplodere una fetta di torta** per attirare l'attenzione su un segmento specifico  
* **Evidenziare una fetta di grafico a torta** con formattazione personalizzata  
* **Creare un grafico docx** che può essere condiviso o ulteriormente modificato  

### Prerequisiti

* Java 17 o successiva (il codice si compila anche con Java 8)  
* Libreria Aspose.Words per Java (versione 23.9 o successiva)  
* Un IDE o uno strumento di build (Maven/Gradle) in grado di risolvere la dipendenza Aspose.Words  

```xml
<!-- Example Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

---

## Come inserire un grafico a torta in un DOCX usando Aspose.Words

Il primo passo è creare un nuovo documento vuoto e ottenere un `DocumentBuilder`. Il builder ti dà accesso diretto al flusso di contenuto del documento, rendendo banale **inserire un grafico a torta**.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

### Perché è importante
`Document` rappresenta l'intero file Word, mentre `DocumentBuilder` è l'API di alto livello che ti permette di inserire paragrafi, tabelle e grafici senza dover gestire XML a basso livello. Iniziare con un documento pulito garantisce che il grafico aggiunto sia l'unico contenuto, il che è perfetto per l'apprendimento o per generare report basati su template.

## Impostare la dimensione del foro per creare una torta completa

Per impostazione predefinita, Aspose.Words crea un grafico a ciambella quando richiedi un grafico a torta. Per rendere il grafico un vero cerchio, devi **impostare la dimensione del foro** a `0`. Questo rimuove il foro interno e produce un aspetto classico di torta.

```java
        // Step 2: Insert a pie chart with a specific size
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);

        // Step 4: Ensure the chart is a full pie (no doughnut hole)
        pieChart.getChart().setHoleSize(0);   // set hole size to zero
```

### Consiglio pratico
Se in seguito decidi di passare a un grafico a ciambella, basta cambiare il valore `holeSize` in una percentuale (ad esempio, `30`). La stessa API funziona per entrambi i tipi di grafico.

## Esplodere una fetta di torta per evidenziare un segmento

Esplodere una fetta la fa risaltare visivamente. L'operazione **esplodere una fetta di torta** sposta la fetta scelta verso l'esterno di una percentuale del raggio del grafico.

```java
        // Step 3: Explode the first slice to highlight it
        pieChart.getChart().getSeries().get(0).setExplosion(20); // explode pie slice
```

### Perché esplodere?
Una fetta esplosa attira l'attenzione del lettore al punto dati più importante—perfetto per dashboard o sintesi esecutive. Il valore `20` significa il 20 % del raggio; puoi regolarlo tra `0` (nessuna esplosione) e `100` (completamente separata).

## Evidenziare una fetta di grafico a torta con formattazione personalizzata

Oltre all'esplosione, potresti voler **evidenziare una fetta di grafico a torta** cambiandone il colore di riempimento o il bordo. Sebbene il codice dimostrativo si concentri sull'esplosione, puoi estenderlo come segue:

```java
        // Optional: Change fill color of the exploded slice
        ChartSeries series = pieChart.getChart().getSeries().get(0);
        series.getDataPoints().get(0).getFormat().setFillColor(java.awt.Color.RED);
```

### Nota dell'esperto
Cambiare il colore di riempimento di una fetta specifica richiede l'accesso all'oggetto `DataPoint`. Se hai più serie, itera attraverso `series.getDataPoints()` e applica gli stili in modo condizionale.

## Salvare e verificare il grafico docx creato

Infine, **crei un grafico docx** salvando il `Document`. Il file risultante può essere aperto in Microsoft Word per vedere il grafico a torta formattato.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartFormatted.docx");
    }
}
```

#### Output previsto
Aprendo `PieChartFormatted.docx` si visualizza un unico grafico a torta:

* Il grafico occupa un'area di 400 × 300 pt.  
* La dimensione del foro è `0`, quindi il grafico è una torta completa.  
* La prima fetta è esplosa del 20 % e colorata di rosso (se hai aggiunto la formattazione opzionale).  

Ora hai un **grafico docx** che può essere distribuito, incorporato nelle email o ulteriormente modificato programmaticamente.

---

## Varianti comuni e casi limite

| Scenario | Come adattare il codice |
|----------|----------------------|
| **Multiple series** | Itera su `pieChart.getChart().getSeries()` e imposta `Explosion` o `FillColor` per serie. |
| **Dynamic data** | Popola le serie con valori provenienti da un database o CSV prima di chiamare `setExplosion`. |
| **Different chart size** | Modifica gli argomenti width/height in `insertChart(ChartType.PIE, width, height)`. |
| **Export to PDF** | Dopo aver salvato il DOCX, chiama `doc.save("output.pdf")` per generare una versione PDF dello stesso grafico. |
| **Localization** | Usa `DocumentBuilder.insertChart` con un formato numerico specifico per la locale per le etichette. |

### Consiglio professionale
Chiama sempre `setHoleSize(0)` **dopo** `insertChart`. Se lo imposti prima dell'inserimento, Aspose.Words tornerà alla dimensione predefinita della ciambella una volta creato il grafico.

---

## Riepilogo

Ora sai come **inserire un grafico a torta** in un documento Word usando Java, come **impostare la dimensione del foro** per un aspetto a torta completa, come **esplodere una fetta di torta** per attirare l'attenzione e come **evidenziare una fetta di grafico a torta** con colori personalizzati. L'esempio completo dimostra anche come **creare un grafico docx** pronto per la distribuzione.

---

## Prossimi passi

* Esplora altri tipi di grafico (`BAR`, `LINE`, `SCATTER`) con `ChartType`.  
* Combina la generazione di grafici con la stampa unione per produrre report personalizzati.  
* Integra il DOCX generato in un servizio web che restituisce il file su richiesta.  

Se incontri problemi, ricorda di verificare di utilizzare una versione compatibile di Aspose.Words e che la directory di output esista e sia scrivibile.

Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Utilizzare l'API dei grafici Word](/words/english/net/programming-with-charts/)
- [Inserire un grafico a bolle in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}