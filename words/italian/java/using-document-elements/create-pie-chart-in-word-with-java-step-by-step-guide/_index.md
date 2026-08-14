---
category: general
date: 2026-08-14
description: Crea un grafico a torta in Word con Java usando Aspose.Words. Scopri
  come aggiungere i dati della serie al grafico e ruotare la fetta del grafico a torta
  in poche righe.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart in word
- how to add series data to chart
- rotate pie chart slice
- Aspose.Words chart API
- Java document automation
language: it
lastmod: 2026-08-14
og_description: Crea un grafico a torta in Word con Java usando Aspose.Words. Questo
  tutorial mostra come aggiungere i dati della serie al grafico e ruotare rapidamente
  una fetta del grafico a torta.
og_image_alt: Screenshot of a Word document containing a colorful pie chart generated
  by Java code
og_title: Crea un grafico a torta in Word con Java – guida completa alla programmazione
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  headline: Create pie chart in Word with Java – step-by-step guide
  type: TechArticle
- description: Create pie chart in Word with Java using Aspose.Words. Learn how to
    add series data to chart and rotate pie chart slice in just a few lines.
  name: Create pie chart in Word with Java – step-by-step guide
  steps:
  - name: Why use Aspose.Words?
    text: '* **No Microsoft Office required** – the library works on any server or
      CI environment. * **Full .docx fidelity** – the generated chart looks identical
      to one created manually in Word. * **Single‑file dependency** – just add the
      JAR and you’re ready to go.'
  - name: Expected output
    text: '* A file named **PieChart.docx** appears in the `output` folder. * Opening
      the file in Microsoft Word shows a colorful pie chart with three slices (40
      %, 30 %, 30 %). * The chart is rotated 45° clockwise, so the first slice starts
      slightly to the right of the vertical axis.'
  - name: Tips for production use
    text: '* **Reuse the `DocumentBuilder`** – you can insert multiple charts in the
      same document by calling `insertChart` repeatedly. * **Styling** – use `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);`
      to display percentages directly on the chart. * **Performance** – generate the
      chart on'
  - name: What’s next?
    text: '* Explore other chart types (`ChartType.BAR`, `ChartType.LINE`) to broaden
      your automation toolkit. * Combine chart generation with **mail merge** to produce
      personalized reports for each recipient. * Dive into the **Styling API** (`ChartFormat`,
      `DataLabel`, `ChartTitle`) to match your corporate br'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Crea un grafico a torta in Word con Java – guida passo passo
url: /it/java/using-document-elements/create-pie-chart-in-word-with-java-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un grafico a torta in Word con Java – guida passo‑passo

Se hai bisogno di **creare un grafico a torta in Word** programmaticamente, questa guida ti mostra esattamente come farlo con Java e Aspose.Words. Imparerai l'intero flusso di lavoro, dall'inserimento del grafico all'aggiunta dei punti dati e alla rotazione della prima fetta.

Generare un grafico direttamente in un file `.docx` elimina il passaggio manuale di copia‑incolla e ti consente di automatizzare report, fatture o dashboard. Durante il percorso tratteremo anche **come aggiungere dati di serie al grafico** e come **ruotare una fetta del grafico a torta** per una migliore enfasi visiva.

## Creare un grafico a torta in Word – panoramica

Aspose.Words for Java fornisce un'API fluida `DocumentBuilder` che può inserire un oggetto grafico in un documento Word. Il tipo di grafico che scegli determina il layout predefinito, e puoi personalizzare le serie, i colori, gli angoli e persino passare a una forma a ciambella con una singola chiamata di metodo.

### Perché usare Aspose.Words?

* **Nessun Microsoft Office richiesto** – la libreria funziona su qualsiasi server o ambiente CI.  
* **Fidelità completa .docx** – il grafico generato appare identico a quello creato manualmente in Word.  
* **Dipendenza a file singolo** – basta aggiungere il JAR e sei pronto.

## Come aggiungere dati di serie al grafico

Un grafico senza dati è solo un segnaposto. L'oggetto `Chart` espone una collezione `Series`; ogni serie contiene un elenco di valori numerici che corrispondono a fette (per una torta) o punti (per una linea). Aggiungere dati è semplice:

```java
// Add three values to the first (and only) series of the pie chart
chart.getSeries().get(0).add(40); // 40 % of the whole
chart.getSeries().get(0).add(30); // 30 %
chart.getSeries().get(0).add(30); // remaining 30 %
```

**Cosa fa il codice:**  
* `chart.getSeries()` restituisce una `List<ChartSeries>`.  
* `get(0)` seleziona la prima serie perché un grafico a torta contiene per definizione una sola serie.  
* `add(double)` aggiunge un punto dati. I valori sono convertiti automaticamente in percentuali che sommano al 100 % quando il grafico viene renderizzato.

> **Consiglio professionale:** Se la tua fonte dati contiene più di tre categorie, continua ad aggiungere valori nello stesso modo. Aspose.Words creerà automaticamente fette aggiuntive.

## Ruotare una fetta del grafico a torta

A volte vuoi che una specifica fetta inizi a un angolo particolare in modo che il segmento più importante sia rivolto allo spettatore. Il metodo `setFirstSliceAngle(double)` ruota l'intero grafico, spostando effettivamente l'inizio della prima fetta:

```java
// Rotate the chart so that the first slice starts at 45 degrees
chart.setFirstSliceAngle(45);
```

L'angolo è misurato in gradi in senso orario rispetto all'asse verticale. Impostandolo a `0` (il valore predefinito) la prima fetta si trova in alto. Regola il valore per evidenziare una fetta o per rispettare una linea guida di design.

> **Domanda comune:** *La rotazione influisce sull'ordine dei dati?*  
> No. L'ordine dei dati rimane lo stesso; solo la posizione di partenza visiva cambia.

## Esempio Java completo

Di seguito trovi un programma completo, pronto‑all'uso, che crea un documento Word con un grafico a torta, aggiunge dati di serie, ruota la fetta e salva il file. Tutti gli import necessari sono elencati, così puoi copiare il codice in qualsiasi IDE.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartInWord {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Initialize a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a PIE chart with a width of 400 points and a height of 300 points
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 3️⃣ Add data points to the first (and only) series
        chart.getSeries().get(0).add(40); // Slice 1
        chart.getSeries().get(0).add(30); // Slice 2
        chart.getSeries().get(0).add(30); // Slice 3

        // 4️⃣ Rotate the start angle so the first slice begins at 45°
        chart.setFirstSliceAngle(45);

        // 5️⃣ (Optional) If you prefer a doughnut chart, uncomment the next line
        // chart.setHoleSize(0.5); // hole size between 0.0 (pie) and 1.0 (empty)

        // 6️⃣ Save the document – adjust the path as needed
        String outPath = "output/PieChart.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Output previsto

* Un file chiamato **PieChart.docx** appare nella cartella `output`.  
* Aprendo il file in Microsoft Word si vede un grafico a torta colorato con tre fette (40 %, 30 %, 30 %).  
* Il grafico è ruotato di 45° in senso orario, quindi la prima fetta inizia leggermente a destra dell'asse verticale.

## Problemi comuni e migliori pratiche

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Il grafico appare vuoto** | Il documento è stato salvato prima che il grafico fosse completamente renderizzato. | Chiamare `doc.save()` **dopo** tutte le modifiche al grafico. |
| **I valori delle fette non sommano al 100 %** | L'aggiunta di numeri grezzi che non rappresentano percentuali può causare una scala inattesa. | Fornire valori che rappresentano logicamente porzioni di un intero, o lasciare che Aspose.Words calcoli automaticamente le percentuali. |
| **La rotazione non ha effetto** | L'uso di `ChartType.DOUGHNUT` senza impostare `holeSize` può nascondere l'effetto di rotazione. | Mantenere il grafico come `PIE` o regolare `holeSize` dopo aver impostato l'angolo. |
| **Errori di percorso file** | I percorsi relativi possono risolversi diversamente su Windows rispetto a Linux. | Utilizzare `Paths.get("output", "PieChart.docx").toString()` o un percorso assoluto per il codice di produzione. |

### Consigli per l'uso in produzione

* **Riutilizza il `DocumentBuilder`** – puoi inserire più grafici nello stesso documento chiamando `insertChart` ripetutamente.  
* **Stilizzazione** – usa `chart.getSeries().get(0).getDataLabels().setShowPercentage(true);` per mostrare le percentuali direttamente sul grafico.  
* **Prestazioni** – genera il grafico una volta e clonaloo (`chart.deepClone()`) se ti servono grafici identici in più punti.

## Ruotare una fetta del grafico a torta – scenari avanzati

* **Angolo dinamico** – calcola l'angolo in base ai dati (ad esempio, fai in modo che la fetta più grande inizi in alto).  
  ```java
  double maxValue = Collections.max(chart.getSeries().get(0).getDataPoints());
  double total = chart.getSeries().get(0).getDataPoints().stream().mapToDouble(Double::doubleValue).sum();
  double startAngle = 360 * (maxValue / total) / 2; // Center the largest slice
  chart.setFirstSliceAngle(startAngle);
  ```
* **Serie multiple** – sebbene un grafico a torta normalmente abbia una sola serie, Aspose.Words consente di aggiungerne altre per torte impilate. La rotazione si applica comunque solo alla prima serie.

## Conclusione

Ora sai come **creare un grafico a torta in Word** usando Java, come **aggiungere dati di serie al grafico**, e come **ruotare una fetta del grafico a torta** per un'enfasi visiva. L'esempio completo dimostra l'intero flusso di lavoro—dall'inizializzazione del documento al salvataggio del file `.docx` finale—così puoi integrare la generazione di grafici in qualsiasi pipeline di reporting automatizzato.

### Cosa fare dopo?

* Esplora altri tipi di grafico (`ChartType.BAR`, `ChartType.LINE`) per ampliare il tuo toolkit di automazione.  
* Combina la generazione di grafici con **mail merge** per produrre report personalizzati per ogni destinatario.  
* Approfondisci l'**API di stilizzazione** (`ChartFormat`, `DataLabel`, `ChartTitle`) per allineare il tuo branding aziendale.

Sentiti libero di sperimentare con diversi set di dati, angoli e stili di grafico. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Come creare campi modulo e aggiungere contenuti usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Come convertire Word in PDF usando Aspose.Words per Java](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}