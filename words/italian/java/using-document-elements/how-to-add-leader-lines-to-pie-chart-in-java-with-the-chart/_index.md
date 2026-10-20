---
category: general
date: 2026-08-20
description: Aggiungi linee di collegamento al grafico a torta in Java rapidamente.
  Impara a inserire, esplodere, cambiare colore e etichettare le fette usando l'API
  Chart.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add leader lines to pie chart
- pie chart explosion Java
- set sector color Chart API
- builder.insertChart usage
- ChartType.PIE example
language: it
lastmod: 2026-08-20
og_description: Aggiungi linee di collegamento al grafico a torta in Java con un esempio
  conciso. Segui questa guida per inserire, esplodere, ricolorare e etichettare le
  fette usando l'API Chart.
og_image_alt: Screenshot showing a pie chart with an exploded slice and leader lines
  – add leader lines to pie chart
og_title: Aggiungi linee di collegamento al grafico a torta in Java – guida passo‑passo
  all'API Chart
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Add leader lines to pie chart in Java quickly. Learn to insert, explode,
    recolor, and label slices using the Chart API.
  headline: How to add leader lines to pie chart in Java with the Chart API
  type: TechArticle
tags:
- pie chart
- Java
- Chart API
- data visualization
title: Come aggiungere linee di collegamento al grafico a torta in Java con l'API
  Chart
url: /it/java/using-document-elements/how-to-add-leader-lines-to-pie-chart-in-java-with-the-chart/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere linee guida a un grafico a torta in Java con l'API Chart

Se hai bisogno di **aggiungere linee guida a un grafico a torta** in Java, questa guida ti accompagna passo passo nel processo completo. Vedrai come inserire un grafico a torta, far esplodere una fetta per enfatizzarla, cambiarne il colore e, infine, abilitare le linee guida che etichettano il segmento esploso.

L'esempio utilizza l'API Chart standard presente in molte librerie di reporting Java. Non sono necessari strumenti esterni e il codice funziona su qualsiasi ambiente JDK 8+.

## Cosa otterrai

* Crea un `Chart` di tipo `ChartType.PIE` con una dimensione personalizzata.  
* Fai esplodere la prima fetta per attirare l'attenzione.  
* Imposta il colore del settore della fetta esplosa su blu.  
* **Aggiungi linee guida a un grafico a torta** in modo che l'etichetta della fetta sia chiaramente collegata.

Dovresti già avere un progetto Java con la libreria Chart nel classpath. Se usi Maven, aggiungi la dipendenza mostrata nella sezione dei prerequisiti.

## Prerequisiti

* JDK 8 o versioni successive installate.  
* La libreria Chart (ad es., `com.example.chart:chart-api:2.5.0`).  
* Familiarità di base con le classi Java e le chiamate ai metodi.

---

## Come aggiungere linee guida a un grafico a torta

Di seguito trovi un programma completo e eseguibile che dimostra ogni passaggio. Il codice è deliberatamente autonomo così puoi copiarlo, incollarlo ed eseguirlo senza modifiche.

```java
// File: AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Demonstrates adding leader lines to a pie chart in Java.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // 1️⃣ Insert a pie chart with the desired size
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // 2️⃣ Pull out the first slice for emphasis (explosion)
        chart.getSeries().get(0).setExplosion(20);

        // 3️⃣ Change the color of the first slice to blue
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // 4️⃣ Show leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional: Save the chart as an image file
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart saved to pie-with-leader-lines.png");
    }
}
```

### Spiegazione di ogni passaggio

| Passo | Cosa fa il codice | Perché è importante |
|------|-------------------|----------------------|
| **1️⃣ Inserisci un grafico a torta** | `builder.insertChart(ChartType.PIE, 400, 300)` crea un grafico a torta di 400 × 300 pixel. | Stabilisce il contenitore del grafico e definisce le sue dimensioni, che influenzano il posizionamento delle etichette e la lunghezza delle linee guida. |
| **2️⃣ Fai esplodere la prima fetta** | `setExplosion(20)` sposta la fetta del 20 % del raggio. | Una fetta esplosa attira l'attenzione dell'osservatore e rende visibile la linea guida. |
| **3️⃣ Imposta il colore del settore** | `setSectorColor(Color.BLUE)` cambia il riempimento della fetta in blu. | Il contrasto di colore migliora la leggibilità, soprattutto quando la fetta è evidenziata. |
| **4️⃣ Abilita le linee guida** | `setLeaderLines(true)` attiva le linee di collegamento che uniscono la fetta alla sua etichetta. | Le linee guida garantiscono che l'etichetta rimanga leggibile anche quando la fetta è spostata verso l'esterno. |

La chiamata `saveAsPng` è opzionale ma utile per verificare il risultato visivo. Dopo aver eseguito il programma, dovresti vedere un'immagine simile a quella mostrata di seguito.

![Aggiungi linee guida a un grafico a torta](https://example.com/assets/pie-leader-lines.png "Aggiungi linee guida a un grafico a torta – fetta esplosa con colore blu e linee guida")

*Figura: Un grafico a torta in cui la prima fetta è esplosa, colorata di blu e collegata alla sua etichetta da una linea guida.*

## Personalizzare le linee guida (avanzato)

La chiamata base `setLeaderLines(true)` utilizza lo stile predefinito della libreria. Puoi controllare ulteriormente l'aspetto:

```java
// Change leader line color to dark gray
chart.setLeaderLineColor(Color.DARK_GRAY);

// Increase line thickness for better visibility
chart.setLeaderLineWidth(2);

// Position labels outside the chart area
chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);
```

Queste opzioni sono utili quando è necessario allineare il branding aziendale o migliorare l'accessibilità.

### Gestione di più serie

Se il tuo grafico a torta contiene più di una serie, potresti voler linee guida solo per una specifica fetta. Usa l'indice della serie per mirare all'elemento corretto:

```java
// Enable leader lines only for the second series, third slice
chart.getSeries().get(1).get(2).setExplosion(15);
chart.getSeries().get(1).get(2).setLeaderLineEnabled(true);
```

Quando una fetta non è esplosa, la linea guida è tipicamente nascosta automaticamente, ma puoi forzarla con `setLeaderLineEnabled(true)`.

## Problemi comuni e come evitarli

| Problema | Sintomo | Soluzione |
|----------|---------|-----------|
| **Linee guida non visibili** | Il grafico viene renderizzato senza connettori. | Assicurati che la fetta sia esplosa (`setExplosion` > 0) o abilita esplicitamente le linee guida sulla fetta. |
| **Sovrapposizione delle etichette** | Le etichette si sovrappongono. | Aumenta le dimensioni del grafico o imposta `setLabelPlacement(Chart.LabelPlacement.OUTSIDE)`. |
| **Colore non applicato** | La fetta mantiene il colore predefinito. | Verifica di stare puntando all'indice di serie corretto (`getSeries().get(0)`). |
| **Immagine non salvata** | `saveAsPng` genera un'eccezione. | Controlla i permessi di scrittura per la directory di output e che la libreria supporti l'esportazione PNG. |

Affrontare questi problemi in anticipo evita sorprese a runtime e produce un grafico rifinito.

## Elenco completo del codice sorgente

Per comodità, ecco nuovamente il file sorgente completo, inclusi import e commenti:

```java
// AddLeaderLinesDemo.java
import com.example.chart.Chart;
import com.example.chart.ChartBuilder;
import com.example.chart.ChartType;
import com.example.chart.Color;

/**
 * Complete example that adds leader lines to a pie chart.
 */
public class AddLeaderLinesDemo {

    public static void main(String[] args) {
        // Create a builder and insert a 400×300 pie chart
        ChartBuilder builder = new ChartBuilder();
        Chart chart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);

        // Explode the first slice (20% offset) and color it blue
        chart.getSeries().get(0).setExplosion(20);
        chart.getSeries().get(0).setSectorColor(Color.BLUE);

        // Turn on leader lines for the exploded slice
        chart.setLeaderLines(true);

        // Optional styling
        chart.setLeaderLineColor(Color.DARK_GRAY);
        chart.setLeaderLineWidth(2);
        chart.setLabelPlacement(Chart.LabelPlacement.OUTSIDE);

        // Export the chart as a PNG image
        chart.saveAsPng("pie-with-leader-lines.png");
        System.out.println("Chart generated successfully.");
    }
}
```

Eseguendo questo programma viene generato `pie-with-leader-lines.png`, che mostra un grafico a torta con una fetta blu esplosa e linee guida chiare che puntano all'etichetta della fetta.

## Conclusione

Ora sai come **aggiungere linee guida a un grafico a torta** in Java usando l'API Chart. Il processo consiste nell'inserire un `ChartType.PIE`, far esplodere la fetta desiderata, personalizzarne il colore e abilitare le linee guida. Con le opzioni di stile opzionali puoi regolare finemente il colore della linea, lo spessore e il posizionamento delle etichette per soddisfare qualsiasi requisito visivo.

Successivamente, considera di esplorare argomenti correlati come **pie chart explosion Java**, **set sector color Chart API**, e **builder.insertChart usage** per creare visualizzazioni più sofisticate come grafici a ciambella, torte impilate o dashboard interattive.

Sentiti libero di sperimentare con diversi indici di fetta, colori e stili di linee guida—i tuoi grafici diventeranno più informativi e visivamente accattivanti ad ogni modifica. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Aggiungere valori data/ora all'asse di un grafico](/words/english/net/programming-with-charts/date-time-values-to-axis/)
- [Inserire un grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}