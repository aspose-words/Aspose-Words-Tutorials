---
category: general
date: 2026-07-20
description: Inserisci un grafico a torta in Java con una guida passo‑passo. Impara
  come far esplodere una fetta, come ruotare il grafico a torta, evidenziare una fetta
  del grafico a torta e personalizzare la fetta del grafico a torta.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- how to explode slice
- how to rotate pie chart
- highlight pie chart slice
- customize pie chart slice
language: it
lastmod: 2026-07-20
og_description: Inserisci un grafico a torta in Java e impara a far esplodere una
  fetta, a ruotare il grafico a torta, a evidenziare una fetta del grafico a torta
  e a personalizzare la fetta del grafico a torta per report visivi raffinati.
og_image_alt: Screenshot showing an inserted pie chart with an exploded and rotated
  slice
og_title: Inserisci un grafico a torta in Java – Esplodi, ruota e evidenzia
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Insert pie chart in Java with a step‑by‑step guide. Learn how to explode
    slice, how to rotate pie chart, highlight pie chart slice and customize pie chart
    slice.
  headline: Insert Pie Chart in Java – Explode, Rotate & Highlight Slices
  type: TechArticle
tags:
- Java
- charting
- visualization
title: Inserire un grafico a torta in Java – Esplodere, ruotare e evidenziare le fette
url: /it/java/images-shapes/insert-pie-chart-in-java-explode-rotate-highlight-slices/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserire pie chart in Java – Esplodere, Ruotare e Evidenziare le Fette

Hai mai avuto bisogno di **inserire pie chart** in un report Java ma non eri sicuro di come far sporgere una singola fetta? Non sei l’unico. Che tu stia costruendo un cruscotto, generando una fattura, o semplicemente visualizzando i risultati di un sondaggio, un pie chart ben stilizzato può trasformare numeri grezzi in intuizioni immediatamente comprensibili.

In questo tutorial vedrai un esempio completo, pronto‑all’uso, che mostra come **inserire un pie chart**, **come esplodere una fetta**, **come ruotare un pie chart**, e persino **evidenziare una fetta di pie chart** con colori personalizzati. Alla fine avrai uno snippet riutilizzabile da inserire in qualsiasi progetto Java che utilizza la popolare libreria *JFreeChart* (o qualsiasi API simile).

## Prerequisiti

- Java 17 o versioni successive (il codice si compila con versioni precedenti, ma useremo la sintassi moderna `var` per brevità).  
- Maven o Gradle per includere la dipendenza `org.jfree:jfreechart`.  
- Una comprensione di base delle classi Java e del concetto di chart builder.  

Se non hai mai aggiunto una libreria a un progetto Maven, inserisci semplicemente questo nel tuo `pom.xml`:

```xml
<dependency>
    <groupId>org.jfree</groupId>
    <artifactId>jfreechart</artifactId>
    <version>1.5.4</version>
</dependency>
```

Fatto—nessuna configurazione aggiuntiva necessaria.

## Passo 1: Inserire pie chart – Creare il Builder e l’Oggetto Chart

Prima di tutto: ci serve un *builder* (pensalo come una fabbrica) che sappia produrre grafici. In JFreeChart il `ChartFactory` fa il lavoro pesante.

```java
import org.jfree.chart.ChartFactory;
import org.jfree.chart.JFreeChart;
import org.jfree.data.general.DefaultPieDataset;

public class PieChartDemo {

    public static JFreeChart createPieChart() {
        // Prepare the data set
        var dataset = new DefaultPieDataset();
        dataset.setValue("Apples", 40);
        dataset.setValue("Bananas", 30);
        dataset.setValue("Cherries", 20);
        dataset.setValue("Dates", 10);

        // Insert pie chart with a width of 400 and height of 300
        JFreeChart chart = ChartFactory.createPieChart(
                "Fruit Distribution", // chart title
                dataset,              // data
                true,                 // include legend
                true,                 // tooltips
                false                 // URLs
        );
        return chart;
    }
}
```

Perché iniziamo con il dataset? Perché il grafico è solo un involucro visivo attorno ai numeri. **Inserendo pie chart** qui abbiamo già una tela di 400 × 300 (la dimensione verrà applicata più tardi quando lo renderizzeremo in un’immagine).

## Passo 2: Come esplodere una fetta – Evidenziare il primo segmento

Ora che il grafico esiste, facciamo spiccare la prima fetta. Esplodere una fetta la sposta leggermente dal cerchio, attirando l’occhio del lettore.

```java
import org.jfree.chart.plot.PiePlot;
import org.jfree.chart.plot.PiePlotState;

public static void explodeFirstSlice(JFreeChart chart) {
    // Grab the plot from the chart – this is where we tweak appearance
    PiePlot plot = (PiePlot) chart.getPlot();

    // Explode the first slice (index 0) to highlight it
    // The key "Apples" corresponds to the first entry we added
    plot.setExplodePercent("Apples", 0.15); // 15% outward
}
```

Nota che usiamo la frase **come esplodere una fetta** nel nome del metodo; questo rende l’intento cristallino. Il metodo `setExplodePercent` accetta una chiave (l’etichetta della fetta) e una percentuale, così puoi regolare la distanza di “sporgenza” secondo necessità.

## Passo 3: Come ruotare un pie chart – Cambiare l’angolo di partenza

Un pie chart predefinito inizia dalla posizione delle 12. A volte vuoi che la prima fetta inizi altrove—magari per allinearla a un mock‑up di design o per corrispondere a un altro grafico.

```java
public static void rotateChart(JFreeChart chart, double startAngle) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Rotate the chart so the first slice starts at the given angle (degrees)
    plot.setStartAngle(startAngle);
}
```

Chiamare `rotateChart(chart, 45)` ruota l’intero pie chart in modo che la fetta “Apples” inizi a 45 gradi, esattamente ciò che richiede **come ruotare un pie chart**.

## Passo 4: Evidenziare una fetta di pie chart – Colori e etichette personalizzati

Oltre a esplodere, potresti voler assegnare a una fetta un colore unico o un’etichetta in grassetto per davvero **evidenziare una fetta di pie chart**.

```java
import java.awt.Color;
import org.jfree.chart.labels.StandardPieSectionLabelGenerator;

public static void customizeSlice(JFreeChart chart) {
    PiePlot plot = (PiePlot) chart.getPlot();

    // Set a vivid color for the "Apples" slice
    plot.setSectionPaint("Apples", new Color(0xFF5722)); // deep orange

    // Make the label display both key and value in bold
    plot.setLabelGenerator(new StandardPieSectionLabelGenerator(
            "{0}: {1} ({2})")); // key: value (percent)
    plot.setLabelFont(plot.getLabelFont().deriveFont(java.awt.Font.BOLD));
}
```

Qui abbiamo **personalizzato una fetta di pie chart** modificando il suo colore e lo stile dell’etichetta. Sentiti libero di cambiare colore o font per adattarli alla palette del tuo brand.

## Passo 5: Renderizzare il grafico in un’immagine (Opzionale ma utile)

La maggior parte delle app reali ha bisogno del grafico come PNG, JPEG o anche PDF. Di seguito un modo rapido per scrivere il grafico su un file.

```java
import java.io.File;
import org.jfree.chart.ChartUtils;

public static void saveChart(JFreeChart chart, String filename) throws Exception {
    int width = 400;
    int height = 300;
    File outFile = new File(filename);
    ChartUtils.saveChartAsPNG(outFile, chart, width, height);
}
```

Eseguendo l’intero flusso otterrai un PNG 400 × 300 che appare più o meno così:

![Esempio di inserimento pie chart](image.png){: alt="Esempio di inserimento pie chart che mostra una fetta esplosa e ruotata"}

## Esempio completo funzionante

Mettendo tutto insieme, ecco un metodo `main` che puoi copiare‑incollare in una nuova classe Java ed eseguire:

```java
public class PieChartDemo {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Insert the pie chart
        JFreeChart chart = createPieChart();

        // 2️⃣ Explode the first slice
        explodeFirstSlice(chart);

        // 3️⃣ Rotate the chart 45° so the first slice starts at 45 degrees
        rotateChart(chart, 45);

        // 4️⃣ Highlight and customize the exploded slice
        customizeSlice(chart);

        // 5️⃣ Save to disk (optional)
        saveChart(chart, "fruit-pie.png");

        System.out.println("Pie chart generated: fruit-pie.png");
    }

    // ... (include the helper methods from steps 1‑4 here) ...
}
```

### Output previsto

Eseguendo il programma viene creato un file chiamato **fruit-pie.png**. Aprilo e vedrai:

- Un pie chart 400 × 300 intitolato “Fruit Distribution”.  
- La fetta “Apples” esplosa verso l’esterno del 15 %.  
- L’intero grafico ruotato in modo che “Apples” inizi alla posizione di 45 gradi.  
- L'esplosione

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Inserire grafico a dispersione](/words/hindi/net/programming-with-charts/insert-scatter-chart/)
- [Inserire grafico ad area](/words/hindi/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}