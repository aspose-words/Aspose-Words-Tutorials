---
category: general
date: 2026-07-29
description: Inserisci un grafico a torta con Aspose.Words per Java e scopri come
  generare un grafico a ciambella, formattare il grafico a torta, formattare il grafico
  in Word e personalizzare le dimensioni del grafico.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert pie chart
- generate doughnut chart
- format pie chart
- format chart word
- customize chart size
language: it
lastmod: 2026-07-29
og_description: Inserisci un grafico a torta con Aspose.Words per Java e impara rapidamente
  a generare un grafico a ciambella, formattare il grafico a torta, formattare il
  grafico in Word e personalizzare le dimensioni del grafico per documenti professionali.
og_image_alt: Screenshot showing a Word document with an inserted pie chart created
  by Aspose.Words Java API
og_title: Inserisci un grafico a torta in Java – Tutorial completo di Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Insert pie chart using Aspose.Words for Java and learn how to generate
    doughnut chart, format pie chart, format chart Word, and customize chart size.
  headline: Insert pie chart in Java with Aspose.Words – Full Guide
  type: TechArticle
- questions:
  - answer: The evaluation version works fine for testing, but it adds a watermark.
      Drop your `aspose.words.lic` file in the classpath for a clean output.
    question: Do I need a license?
  - answer: 'Absolutely. Add the following dependency to your `pom.xml`:'
    question: Can I use this with Maven?
  - answer: Loop over `pieChart.getSeries()` and apply `setExplosion`, `setFillColor`,
      or other formatting per series. That’s the way to **format pie chart** for multi‑dimensional
      data.
    question: What if I have more than one series?
  - answer: Yes—once saved, you can open the document and manually adjust colors,
      fonts, or even convert the pie to a bar chart if you need to.
    question: Is the chart editable in Word after generation?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Chart
- Document Generation
- Word Automation
title: Inserire un grafico a torta in Java con Aspose.Words – Guida completa
url: /it/java/using-document-elements/insert-pie-chart-in-java-with-aspose-words-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insert pie chart in Java with Aspose.Words – Guida completa

Ti sei mai chiesto come **insert pie chart** in un documento Word dal codice Java? Non sei l'unico—molti sviluppatori incontrano questo ostacolo quando hanno bisogno di un modo rapido e programmatico per visualizzare i dati. La buona notizia? Con Aspose.Words for Java puoi farlo in poche righe, e nel frattempo puoi anche **generate doughnut chart**, **format pie chart**, **format chart Word** e **customize chart size** per adattarlo al tuo brand.

In questo tutorial percorreremo un esempio reale che inizia creando un documento vuoto, inserendo un grafico a torta, modificando alcune proprietà visive e infine salvando il file. Alla fine avrai uno snippet riutilizzabile da incollare in qualsiasi progetto Java che necessiti di automazione dei grafici. Nessuna libreria aggiuntiva, nessuna manipolazione manuale con l'interoperabilità di Office—solo Java pulito e compilato.

## Cosa ti serve

- **Java 17** (o qualsiasi JDK recente; l'API è retrocompatibile)
- **Aspose.Words for Java** 22.12 o più recente – puoi scaricare l'artifact Maven o il .jar dal sito Aspose.
- Un IDE modesto (IntelliJ IDEA, Eclipse, VS Code…) – qualsiasi cosa ti permetta di eseguire un metodo `main`.
- Opzionale: un file di licenza se non vuoi la filigrana di valutazione.

Se li hai, possiamo passare direttamente al codice.

## Passo 1: Inserire un grafico a torta con Aspose.Words

La prima cosa che facciamo è **insert pie chart** in un documento nuovo. Questo passo prepara il terreno per tutto il resto, perché l'oggetto chart ci dà accesso a serie, punti dati e modifiche visive.

```java
import com.aspose.words.*;

public class PieChartFormatting {
    public static void main(String[] args) throws Exception {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with a specific size (500x400 points)
        Chart pieChart = builder.insertChart(ChartType.PIE, 500, 400);
```

> **Perché è importante:** `DocumentBuilder.insertChart` non solo crea il grafico ma restituisce anche un oggetto `Chart` che possiamo manipolare. Gli argomenti width e height ti permettono di **customize chart size** al momento della creazione, così non è necessario ridimensionare in seguito.

## Passo 2: Generare un grafico a ciambella (opzionale)

Se il tuo design richiede un buco al centro—pensa a un classico doughnut chart—Aspose lo rende con una sola riga. La stessa istanza `Chart` può essere trasformata da una torta normale a una ciambella regolando la dimensione del buco.

```java
        // Optional: Turn the pie into a doughnut by setting the hole size (0‑100%)
        pieChart.getChartData().setHoleSize(30); // 30% hole makes it a doughnut chart
```

> **Suggerimento:** La dimensione del buco ha effetto solo per `ChartType.DONUT`. Se mantieni il tipo `PIE`, la chiamata viene ignorata, quindi sentiti libero di sperimentare.

## Passo 3: Formattare le fette del grafico a torta

Una buona visualizzazione spesso mette in evidenza una fetta particolare. Qui **format pie chart** facendo esplodere la prima fetta di 20 punti verso l'esterno. Questo attira l'occhio del lettore al punto dati più importante.

```java
        // Explode the first slice to emphasize it
        pieChart.getSeries().get(0).setExplosion(20);
```

> **Consiglio professionale:** Puoi iterare su `pieChart.getSeries()` se hai più serie e impostare colori, bordi o etichette dati individuali. Questo è il modo per **format chart Word** documenti con uno stile ricco.

## Passo 4: Aggiungere dati al grafico

Un grafico senza dati è solo una forma decorativa. Forniamogli un semplice set di dati—ad esempio, i numeri di vendita trimestrali.

```java
        // Populate the chart with sample data
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataLabels().setShowCategoryName(true);
        series.getDataLabels().setShowValue(true);

        // Clear any default points and add our own
        series.getPoints().clear();
        series.getPoints().add(new ChartPoint(30)); // Q1
        series.getPoints().add(new ChartPoint(45)); // Q2
        series.getPoints().add(new ChartPoint(15)); // Q3
        series.getPoints().add(new ChartPoint(10)); // Q4
```

> **Perché lo facciamo:** Aggiungendo esplicitamente oggetti `ChartPoint` garantiamo che il grafico rifletta la nostra logica di business. Le chiamate `setShowCategoryName` e `setShowValue` fanno parte del **formatting the pie chart** per mostrare sia le etichette che i numeri.

## Passo 5: Rifinire l'aspetto (customize chart size & style)

Oltre alle dimensioni iniziali, potresti voler modificare la legenda del grafico, il titolo o anche il font usato per le etichette dati. Tutto ciò rientra in **customize chart size** e nella formattazione generale.

```java
        // Set a title for the chart
        ChartTitle title = pieChart.getTitle();
        title.setText("Quarterly Sales Distribution");
        title.getFont().setSize(14);
        title.getFont().setBold(true);

        // Move the legend to the right side
        ChartLegend legend = pieChart.getLegend();
        legend.setPosition(LegendPosition.RIGHT);
        legend.getFont().setSize(10);

        // Adjust the overall chart size again if needed
        pieChart.setWidth(600);   // width in points
        pieChart.setHeight(450);  // height in points
```

> **Caso limite:** Se in seguito decidi di esportare il documento in PDF, i dati vettoriali del grafico rimangono nitidi perché la dimensione è definita in punti, non in pixel. Questo è un vantaggio per **format chart Word** e i formati successivi.

## Passo 6: Salvare e visualizzare il documento

L'ultimo passo è semplice come chiamare `doc.save`. Questo scrive un file `.docx` che puoi aprire in Microsoft Word, LibreOffice o qualsiasi visualizzatore che supporti il formato OpenXML.

```java
        // Save the document containing the formatted chart
        doc.save("YOUR_DIRECTORY/PieChart.docx");
    }
}
```

> **Risultato:** Apri `PieChart.docx` e vedrai un grafico a torta (o ciambella) di dimensioni corrette con una fetta esplosa, un titolo e una legenda—tutto generato senza mai toccare l'interfaccia utente.

### Output previsto

| Elemento | Cosa vedrai |
|----------|--------------|
| Tipo di grafico | Pie chart (o doughnut se `holeSize` > 0) |
| Esplosione della fetta | Prima fetta spostata di 20 pts |
| Legenda | Posizionata a destra |
| Titolo | “Quarterly Sales Distribution” in grassetto 14 pt |
| Etichette dati | Nome categoria e valore mostrati su ogni fetta |
| Documento | Un file Word `.docx` standard pronto per la condivisione |

## Domande comuni e problemi

- **Ho bisogno di una licenza?**  
  La versione di valutazione funziona bene per i test, ma aggiunge una filigrana. Inserisci il tuo file `aspose.words.lic` nel classpath per un output pulito.

- **Posso usarlo con Maven?**  
  Assolutamente. Aggiungi la seguente dipendenza al tuo `pom.xml`:

  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>22.12</version>
  </dependency>
  ```

- **E se ho più di una serie?**  
  Itera su `pieChart.getSeries()` e applica `setExplosion`, `setFillColor` o altre formattazioni per serie. Questo è il modo per **format pie chart** per dati multidimensionali.

- **Il grafico è modificabile in Word dopo la generazione?**  
  Sì—una volta salvato, puoi aprire il documento e regolare manualmente colori, font o persino convertire la torta in un grafico a barre se necessario.

## Conclusione

Abbiamo appena **inserted pie chart** in un documento Word usando Aspose.Words per Java, mostrato come **generate doughnut chart**, dimostrato diversi modi per **format pie chart**, coperto le migliori pratiche di **format chart Word** e imparato a **customize chart size** per un aspetto curato. L'esempio completo e eseguibile sopra può essere inserito in qualsiasi progetto Java, fornendoti automazione dei grafici istantanea senza l'overhead dell'interoperabilità COM o delle installazioni di Office.

Cosa fare dopo? Prova a sostituire la fonte dati con un database live, aggiungi colori condizionali basati su soglie, o esporta lo stesso documento in PDF per un report pronto per la stampa. Ognuno di questi passi si basa sulla base che abbiamo creato, quindi troverai la transizione fluida.

Se incontri problemi o hai idee per ulteriori miglioramenti—magari un grafico a barre impilate o un grafico a linee—lascia un commento qui sotto. Buon lavoro con i grafici!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Format Number Of Data Label In A Chart](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Number Format For Axis In A Chart](/words/english/net/programming-with-charts/number-format-for-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}