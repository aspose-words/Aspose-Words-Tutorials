---
"description": "Scopri come creare e personalizzare grafici in Aspose.Words per Java. Esplora i tipi di grafico, la formattazione e le proprietà degli assi per la visualizzazione dei dati."
"linktitle": "Utilizzo dei grafici"
"second_title": "API di elaborazione dei documenti Java Aspose.Words"
"title": "Utilizzo di grafici in Aspose.Words per Java"
"url": "/it/java/document-conversion-and-export/using-charts/"
"weight": 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Utilizzo di grafici in Aspose.Words per Java


## Introduzione all'uso dei grafici in Aspose.Words per Java

In questo tutorial, esploreremo come lavorare con i grafici utilizzando Aspose.Words per Java. Imparerai a creare diversi tipi di grafici, personalizzare le proprietà degli assi, formattare le etichette dati e altro ancora. Iniziamo subito!

## Creazione di un grafico a linee

Per creare un grafico a linee, utilizzare il seguente codice:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Elimina le serie generate di default.
chart.getSeries().clear();

// Aggiungere una serie con dati ed etichette dati.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Oppure collega il codice di formato a una cella di origine.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

## Creazione di altri tipi di grafici

È possibile creare diversi tipi di grafici, come a colonne, ad area, a bolle, a dispersione e altri ancora, utilizzando tecniche simili. Ecco un esempio di inserimento di un semplice grafico a colonne:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Elimina le serie generate di default.
chart.getSeries().clear();

// Creazione di categorie e aggiunta di dati.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

## Personalizzazione delle proprietà degli assi

È possibile personalizzare le proprietà degli assi, ad esempio modificandone il tipo, impostando le tacche, formattando le etichette e altro ancora. Ecco un esempio di definizione delle proprietà degli assi XY:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Cancella le serie predefinite e aggiungi i tuoi dati.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Modificare l'asse X in modo che sia una categoria anziché una data.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Misurato in unità di visualizzazione dell'asse Y (centinaia).
xAxis.setReverseOrder(true);
xAxis.setMajorTickMark(AxisTickMark.CROSS);
xAxis.setMinorTickMark(AxisTickMark.OUTSIDE);
xAxis.setTickLabelOffset(200);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

## Formattazione delle etichette dati

È possibile formattare le etichette dati con diversi formati numerici. Ecco un esempio:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Cancella le serie predefinite e aggiungi i tuoi dati.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Ulteriori personalizzazioni del grafico

Puoi personalizzare ulteriormente i tuoi grafici modificando i limiti, le unità di intervallo tra le etichette, nascondendo gli assi del grafico e altro ancora. Esplora i frammenti di codice forniti per saperne di più su queste opzioni.

## Conclusione

In questo tutorial abbiamo esplorato come lavorare con i grafici utilizzando Aspose.Words per Java. Hai imparato a creare diversi tipi di grafici, personalizzare le proprietà degli assi, formattare le etichette dati e altro ancora. Aspose.Words per Java offre potenti strumenti per aggiungere rappresentazioni visive dei dati ai tuoi documenti, migliorando il modo in cui presenti le informazioni.

## Domande frequenti

### Come posso aggiungere più serie a un grafico?

È possibile aggiungere più serie a un grafico utilizzando `chart.getSeries().add()` metodo. Assicurati di specificare il nome della serie, le categorie e i valori dei dati.

### Come posso formattare le etichette dati con formati numerici personalizzati?

È possibile formattare le etichette dati accedendo a `DataLabels` proprietà di una serie e impostazione del codice di formato desiderato utilizzando `getNumberFormat().setFormatCode()`.

### Come posso personalizzare le proprietà degli assi in un grafico?

È possibile personalizzare le proprietà dell'asse come tipo, segni di spunta, etichette e altro ancora accedendo a `ChartAxis` proprietà come `setCategoryType()`, `setCrosses()`, E `setMajorTickMark()`.

### Come posso creare altri tipi di grafici, come grafici a dispersione o ad area?

È possibile creare vari tipi di grafici specificando l'appropriato `ChartType` quando si inserisce il grafico utilizzando `builder.insertChart(ChartType.TYPE, width, height)`.

### Come posso nascondere un asse di un grafico?

È possibile nascondere un asse del grafico impostando `setHidden(true)` proprietà dell'asse.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}