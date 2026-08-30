---
category: general
date: 2026-08-07
description: Come far esplodere una fetta di torta in Java usando Aspose.Words. Scopri
  come aggiungere linee guida alla torta, creare un grafico Word e personalizzare
  le fette del grafico a torta.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode pie slice
- add leader lines to pie
- java create word chart
- customize pie chart slices
language: it
lastmod: 2026-08-07
og_description: Come far esplodere una fetta di torta in Java con Aspose.Words. Questa
  guida ti mostra come aggiungere linee guida alla torta, creare grafici Word e personalizzare
  le fette del grafico a torta per un impatto visivo chiaro.
og_image_alt: Screenshot of a Word document with an exploded pie chart created using
  Java Aspose.Words
og_title: Come esplodere una fetta di torta in Java – Guida Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to explode pie slice in Java using Aspose.Words. Learn to add leader
    lines to pie, create Word chart, and customize pie chart slices.
  headline: How to explode pie slice in Java – Aspose.Words chart tutorial
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Pie Chart
title: Come far esplodere una fetta di torta in Java – tutorial sul grafico Aspose.Words
url: /it/java/using-document-elements/how-to-explode-pie-slice-in-java-aspose-words-chart-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come far esplodere una fetta di torta in Java – tutorial sui grafici Aspose.Words

Se hai bisogno di sapere **come far esplodere una fetta di torta** in un documento Word usando Java, questo tutorial ti copre. Ti mostreremo anche **come aggiungere linee guida alle torte** nei grafici, **java create word chart** objects, e **customize pie chart slices** per un risultato rifinito. Alla fine di questa guida avrai un esempio completo e eseguibile che potrai inserire in qualsiasi progetto Java.

![How to explode pie slice in Java – Aspose.Words chart](/images/pie-chart-exploded.png)

## Prerequisiti

* Java Development Kit (JDK) 8 o superiore.  
* Maven o Gradle per la gestione delle dipendenze.  
* Una licenza Aspose.Words per Java (la valutazione gratuita è sufficiente per scopi di apprendimento).  
* Familiarità di base con la sintassi Java e i concetti orientati agli oggetti.

> **Consiglio professionale:** Anche se Aspose.Words offre una prova gratuita, l'acquisto di una licenza rimuove il watermark di valutazione dai documenti generati.

## Cosa copre questo tutorial

* Creazione di un nuovo documento Word da zero.  
* Inserimento di un **grafico a torta** usando il `DocumentBuilder`.  
* **Esplodere una fetta di torta** per evidenziare un punto dati.  
* **Aggiungere linee guida alla torta** per una etichettatura più chiara.  
* Personalizzare l'aspetto della fetta, come colori e bordi.  
* Salvataggio del documento su disco e verifica del risultato.

---

## Come far esplodere una fetta di torta con Aspose.Words in Java

Il primo passo è configurare l'oggetto grafico e far esplodere la fetta desiderata. Aspose.Words espone il grafico tramite la classe `Shape`, e ogni fetta è un `ChartPoint`. Impostando la proprietà `Explosion` controlli quanto la fetta si sposta verso l'esterno.

```java
// Step 1: Create a blank document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a pie chart (400x300 points)
Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
Chart chart = pieChart.getChart();

// Step 3: Explode the first slice (index 0) by 20 points
chart.getSeries().get(0).getPoints().get(0).setExplosion(20);
```

**Perché funziona:**  
`setExplosion(20)` indica al motore del grafico di spostare la fetta di 20 punti dal centro del grafico. Il valore è relativo; numeri più grandi creano un effetto più drammatico. Puoi far esplodere qualsiasi fetta cambiando l'indice (`get(1)`, `get(2)`, …).

## Aggiungere linee guida alla torta per etichette più chiare

Le linee guida collegano l'etichetta di una fetta al suo bordo, il che è particolarmente utile quando le fette sono esplose o quando il grafico contiene molte piccole sezioni. La chiamata `setLeaderLines(true)` abilita questa funzionalità per l'intera serie.

```java
// Step 4: Enable leader lines for the series
chart.getSeries().get(0).setLeaderLines(true);
```

**Perché ti servono le linee guida:**  
Quando una fetta è esplosa, l'etichetta predefinita può sovrapporsi ad altri elementi. Le linee guida mantengono l'etichetta leggibile disegnando una breve linea dalla fetta alla casella di testo.

## Java create Word chart – inserimento della serie di dati

Un grafico senza dati non è molto utile. Devi popolare la serie con categorie e valori. Di seguito aggiungiamo tre categorie che rappresentano la quota di mercato.

```java
// Step 5: Populate the chart with data
ChartSeries series = chart.getSeries().get(0);
series.getDataLabel().setShowCategoryName(true); // show labels
series.getDataLabel().setShowPercentage(true);   // show percentages

// Add categories and values
series.getCategories().add("Product A");
series.getCategories().add("Product B");
series.getCategories().add("Product C");

series.getValues().add(45); // Product A = 45%
series.getValues().add(30); // Product B = 30%
series.getValues().add(25); // Product C = 25%
```

**Spiegazione:**  
`ChartSeries` contiene sia le categorie (i nomi delle fette) sia i valori numerici. Abilitare `ShowCategoryName` e `ShowPercentage` rende il grafico auto‑esplicativo, il che si abbina bene alle linee guida aggiunte in precedenza.

## Personalizzare le fette del grafico a torta oltre l'esplosione

Oltre a far esplodere una fetta, spesso si desidera regolare colori, bordi o persino nascondere completamente una fetta. Il frammento seguente dimostra tre personalizzazioni comuni:

```java
// Step 6: Change slice colors and borders
ChartPoint pointA = series.getPoints().get(0); // Product A
ChartPoint pointB = series.getPoints().get(1); // Product B
ChartPoint pointC = series.getPoints().get(2); // Product C

// Set custom fill colors
pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50")); // green
pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3")); // blue
pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800")); // orange

// Add a thin border to each slice
for (ChartPoint pt : series.getPoints()) {
    pt.getFormat().getLine().setWeight(0.5);
    pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
}

// Optional: hide a slice (e.g., Product C) without removing data
pointC.setIsHidden(true);
```

**Perché personalizzare le fette:**  
I colori personalizzati fanno sì che il grafico si allinei al branding aziendale, mentre i bordi migliorano la leggibilità su pagine stampate. Nascondere una fetta è utile quando vuoi mantenere intatto il modello di dati ma omettere temporaneamente una categoria dall'output visivo.

## Salva il documento e verifica il risultato

Infine, scrivi il documento su disco. Puoi aprire il `.docx` generato in Microsoft Word, LibreOffice o qualsiasi visualizzatore che supporti il formato.

```java
// Step 7: Save the document
String outputPath = "output/PieChartDemo.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

**Output previsto:**  
Quando apri `PieChartDemo.docx`, vedrai un grafico a torta in cui la prima fetta (Product A) è esplosa verso l'esterno, le linee guida puntano da ogni fetta alla sua etichetta e le fette appaiono nei colori verde, blu e arancione personalizzati. La fetta nascosta (Product C) non sarà visibile, ma le percentuali continueranno a sommare 100 % perché i dati rimangono nella serie del grafico.

---

## Esempio completo e eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire dopo aver aggiunto la dipendenza Aspose.Words al tuo progetto.

```java
import com.aspose.words.*;
import com.aspose.words.drawing.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a pie chart (400x300 points)
        Shape pieChart = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = pieChart.getChart();

        // Explode the first slice to highlight it
        chart.getSeries().get(0).getPoints().get(0).setExplosion(20);

        // Enable leader lines for clearer labeling
        chart.getSeries().get(0).setLeaderLines(true);

        // Populate the chart with data
        ChartSeries series = chart.getSeries().get(0);
        series.getDataLabel().setShowCategoryName(true);
        series.getDataLabel().setShowPercentage(true);

        series.getCategories().add("Product A");
        series.getCategories().add("Product B");
        series.getCategories().add("Product C");

        series.getValues().add(45);
        series.getValues().add(30);
        series.getValues().add(25);

        // Customize slice colors and borders
        ChartPoint pointA = series.getPoints().get(0);
        ChartPoint pointB = series.getPoints().get(1);
        ChartPoint pointC = series.getPoints().get(2);

        pointA.getFormat().getFill().setForeColor(java.awt.Color.decode("#4CAF50"));
        pointB.getFormat().getFill().setForeColor(java.awt.Color.decode("#2196F3"));
        pointC.getFormat().getFill().setForeColor(java.awt.Color.decode("#FF9800"));

        for (ChartPoint pt : series.getPoints()) {
            pt.getFormat().getLine().setWeight(0.5);
            pt.getFormat().getLine().setForeColor(java.awt.Color.BLACK);
        }

        // Hide the third slice (optional)
        pointC.setIsHidden(true);

        // Save the document
        document.save("output/PieChartDemo.docx");
        System.out.println("Pie chart Word document created successfully.");
    }
}
```

**Dipendenza (Maven)**  

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- Use the latest stable version -->
</dependency>
```

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Come caricare documenti Word con Aspose.Words Java: Guida completa](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}