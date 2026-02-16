---
date: 2026-02-16
description: Scopri come aggiungere più serie ai grafici in Aspose.Words per Java,
  modificare i segni di graduazione degli assi, applicare un formato numerico personalizzato
  e generare documenti Word con grafici a linee e a colonne.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Aggiungi più serie ai grafici in Aspose.Words per Java
url: /it/java/document-conversion-and-export/using-charts/
weight: 12
---

 Asked Questions => "Domande frequenti"

Then each Q/A translate.

**Q: How can I add multiple series to a chart?** => "D: Come posso aggiungere più serie a un grafico?" (but keep **Q:** maybe keep as is? Keep **Q:** and **A:** but translate text after.

We'll keep **Q:** and **A:** as is, but translate content.

Now final metadata lines: "Last Updated:", "Tested With:", "Author:" translate.

Now produce final content with same shortcodes.

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungere più serie ai grafici in Aspose.Words per Java

## Introduzione all'uso dei grafici in Aspose.Words per Java

In questo tutorial imparerai **come aggiungere più serie** a un grafico usando Aspose.Words per Java, perché la personalizzazione dei segni di graduazione degli assi e l'applicazione di un formato numerico personalizzato sono importanti, e come generare un documento Word ricco di grafici. Che tu abbia bisogno di un grafico a linee per dati finanziari o di un grafico a colonne per le vendite, i passaggi seguenti ti guideranno nella creazione, nello styling e nella messa a punto dei grafici in modo programmatico.

## Risposte rapide
- **Come aggiungo più serie?** Usa `chart.getSeries().add(...)` per ogni serie che desideri visualizzare.  
- **Posso modificare i segni di graduazione degli assi?** Sì – usa `setMajorTickMark()` e `setMinorTickMark()` sugli oggetti asse.  
- **Quale formato posso applicare alle etichette dei dati?** Qualsiasi formato numerico compatibile con Excel, ad es. `"$"#,##0.00` o `0.00%`.  
- **Quali tipi di grafico sono supportati?** Line, column, area, bubble, scatter e molti altri tramite `ChartType`.  
- **È necessaria una licenza per la produzione?** È necessaria una licenza valida di Aspose.Words per Java per la piena funzionalità.

## Che cosa significa “add multiple series” in un grafico?
Aggiungere più serie significa inserire più di un set di dati nella stessa area del grafico, consentendo di confrontare diverse categorie o periodi temporali fianco a fianco. Ogni serie appare come una propria linea, colonna o insieme di marcatori, offrendo ai lettori una narrazione visiva più ricca.

## Perché usare Aspose.Words per Java per generare documenti Word con grafici?
- **Controllo totale** sul tipo di grafico, layout e stile senza aprire Word manualmente.  
- **Generazione programmatica** che si integra nei flussi di lavoro di reporting automatizzato.  
- **Cross‑platform** – funziona in qualsiasi ambiente compatibile con Java.  
- **API ricca** per personalizzare assi, etichette dati e formati numerici.

## Prerequisiti
- Java Development Kit (JDK) 8 o superiore.  
- Libreria Aspose.Words per Java aggiunta al progetto (Maven/Gradle o JAR).  
- Una licenza valida di Aspose per la produzione (opzionale per la valutazione).

## Guida passo‑passo

### Passo 1: Creare un grafico a linee e **aggiungere più serie**
Di seguito trovi il codice principale che crea un grafico a linee, cancella le serie predefinite e aggiunge tre serie distinte con etichette dati personalizzate.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.LINE, 432.0, 252.0);
Chart chart = shape.getChart();
chart.getTitle().setText("Data Labels With Different Number Format");

// Delete default generated series.
chart.getSeries().clear();

// Adding a series with data and data labels.
ChartSeries series1 = chart.getSeries().add("Aspose Series 1", 
    new String[] { "Category 1", "Category 2", "Category 3" }, 
    new double[] { 2.5, 1.5, 3.5 });

series1.hasDataLabels(true);
series1.getDataLabels().setShowValue(true);
series1.getDataLabels().get(0).getNumberFormat().setFormatCode("\"$\"#,##0.00");
series1.getDataLabels().get(1).getNumberFormat().setFormatCode("dd/mm/yyyy");
series1.getDataLabels().get(2).getNumberFormat().setFormatCode("0.00%");

// Or link format code to a source cell.
series1.getDataLabels().get(2).getNumberFormat().isLinkedToSource(true);

doc.save("Your Directory Path" + "WorkingWithCharts.FormatNumberOfDataLabel.docx");
```

> **Suggerimento:** Chiama `chart.getSeries().add(...)` quante volte è necessario per **aggiungere più serie** – ogni chiamata crea una nuova linea (o colonna, ecc.) sullo stesso grafico.

### Passo 2: **Creare un grafico a colonne** (create column chart java)
Il frammento successivo mostra come inserire un semplice grafico a colonne, utile per confrontare categorie fianco a fianco.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Delete default generated series.
chart.getSeries().clear();

// Creating categories and adding data.
String[] categories = new String[] { "Category 1", "Category 2" };
chart.getSeries().add("Aspose Series 1", categories, new double[] { 1.0, 2.0 });
chart.getSeries().add("Aspose Series 2", categories, new double[] { 3.0, 4.0 });

doc.save("Your Directory Path" + "WorkingWithCharts.InsertSimpleColumnChart.docx");
```

### Passo 3: **Modificare i segni di graduazione degli assi** (change axis tick marks)
Personalizzare gli assi X e Y migliora la leggibilità. Il codice seguente dimostra come cambiare i segni di graduazione, invertire l'ordine e impostare punti di intersezione personalizzati.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.AREA, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

ChartAxis xAxis = chart.getAxisX();
ChartAxis yAxis = chart.getAxisY();

// Change the X axis to be a category instead of date.
xAxis.setCategoryType(AxisCategoryType.CATEGORY);
xAxis.setCrosses(AxisCrosses.CUSTOM);
xAxis.setCrossesAt(3.0); // Measured in display units of the Y axis (hundreds).
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

### Passo 4: **Applicare un formato numerico personalizzato** (apply custom number format)
Puoi formattare i numeri degli assi o le etichette dati con qualsiasi modello supportato da Excel. Di seguito trovi un esempio conciso che formatta l'asse Y con un modello separatore di migliaia.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

### Passo 5: Generare il documento Word finale (generate chart word document)
Dopo aver configurato serie, assi e etichette, chiama semplicemente `doc.save(...)` come mostrato negli snippet precedenti. Il file `.docx` risultante contiene grafici pienamente funzionanti che possono essere aperti e modificati in Microsoft Word.

## Casi d'uso comuni
- **Dashboard finanziari** – grafici a linee con più serie per ricavi, spese e profitto.  
- **Report di vendita** – grafici a colonne che confrontano le vendite trimestrali per regione.  
- **Monitoraggio progetti** – grafici area o scatter che visualizzano l'avanzamento nel tempo.  

## Personalizzazioni aggiuntive del grafico
Oltre alle basi, puoi regolare i limiti, nascondere gli assi (`axis.setHidden(true)`), cambiare i colori, aggiungere legende e molto altro. Consulta il riferimento API di Aspose.Words per Java per l'elenco completo delle opzioni.

## Conclusione
In questa guida abbiamo illustrato come **aggiungere più serie** ai grafici, creare sia grafici a linee che a colonne, **modificare i segni di graduazione degli assi**, **applicare formati numerici personalizzati** e infine **generare un documento Word ricco di grafici**. Con Aspose.Words per Java disponi di un modo potente, code‑first, per inserire visualizzazioni dati professionali direttamente nei tuoi documenti.

## Domande frequenti

**Q: Come posso aggiungere più serie a un grafico?**  
**A:** Chiama `chart.getSeries().add()` per ogni serie che desideri visualizzare. Ogni chiamata crea un nuovo set di dati che appare come una propria linea, colonna o gruppo di marcatori.

**Q: Come formatto le etichette dati con un formato numerico personalizzato?**  
**A:** Accedi all'oggetto `DataLabels` della serie e usa `getNumberFormat().setFormatCode("tuo modello")`. Puoi anche collegare il formato a una cella di origine con `isLinkedToSource(true)`.

**Q: Come posso modificare i segni di graduazione degli assi?**  
**A:** Usa `setMajorTickMark()` e `setMinorTickMark()` su `ChartAxis`. Le opzioni includono `CROSS`, `INSIDE`, `OUTSIDE` e `NONE`.

**Q: Posso creare altri tipi di grafico come scatter o area?**  
**A:** Sì – specifica il `ChartType` desiderato (ad es. `ChartType.SCATTER`, `ChartType.AREA`) quando chiami `builder.insertChart(...)`.

**Q: Come nascondo un asse che non mi serve?**  
**A:** Chiama `axis.setHidden(true)` sull'oggetto `ChartAxis` che desideri nascondere.

---

**Ultimo aggiornamento:** 2026-02-16  
**Testato con:** Aspose.Words per Java 24.11  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}