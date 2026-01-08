---
date: 2025-12-13
description: Scopri come creare un grafico a colonne e formattare le etichette dei
  dati del grafico con Aspose.Words per Java. Esplora l'aggiunta di più serie, la
  modifica del tipo di asse e la possibilità di nascondere l'asse del grafico.
linktitle: Using Charts
second_title: Aspose.Words Java Document Processing API
title: Come creare un grafico a colonne usando Aspose.Words per Java
url: /it/java/document-conversion-and-export/using-charts/
weight: 12
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico a colonne usando Aspose.Words per Java

In questo tutorial **creerai visualizzazioni di grafici a colonne** direttamente all'interno di documenti Word usando Aspose.Words per Java. Vedremo come creare diversi tipi di grafico, aggiungere più serie, formattare le etichette dei dati del grafico, cambiare il tipo di asse e persino nascondere un asse del grafico quando è necessario un aspetto più pulito. Alla fine avrai un approccio solido, pronto per la produzione, per incorporare grafici ricchi nei tuoi documenti.

## Risposte rapide
- **Qual è la classe principale per costruire un grafico?** `DocumentBuilder` con `insertChart`.
- **Quale metodo aggiunge una nuova serie?** `chart.getSeries().add(...)`.
- **Come formattare le etichette dei dati del grafico?** Usa `getDataLabels().get(...).getNumberFormat().setFormatCode(...)`.
- **Posso nascondere un asse?** Sì, chiama `setHidden(true)` sull'oggetto asse.
- **È necessaria una licenza per Aspose.Words?** È richiesta una licenza per l'uso in produzione; è disponibile una versione di prova gratuita.

## Che cos'è un grafico a colonne e perché usarlo?

Un grafico a colonne visualizza dati categorici come barre verticali, rendendolo ideale per confrontare valori tra gruppi (vendite per regione, spese mensili, ecc.). Nelle applicazioni Java, generare un grafico a colonne con Aspose.Words ti consente di incorporare queste visualizzazioni direttamente nei file Word / DOCX senza dover ricorrere a Excel o strumenti esterni.

## Come creare un grafico a colonne

Di seguito trovi un esempio semplice che crea un grafico a colonne. Il codice è identico allo snippet originale – abbiamo aggiunto solo commenti esplicativi per renderlo più facile da seguire.

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

### Aggiungere più serie

Puoi **aggiungere più serie** a un grafico a colonne chiamando ripetutamente `chart.getSeries().add(...)`, come mostrato sopra. Ogni serie può avere il proprio insieme di categorie e valori, consentendoti di confrontare diversi set di dati fianco a fianco.

## Come creare un grafico a linee con etichette dati personalizzate

Se ti serve un grafico a linee invece di un grafico a colonne, lo stesso schema si applica. Questo esempio dimostra anche come **formattare le etichette dei dati del grafico** con formati numerici diversi.

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

### Aggiungere etichette dati

La chiamata `series1.hasDataLabels(true)` **aggiunge etichette dati** alla serie, mentre `setShowValue(true)` rende visibili i valori effettivi sul grafico.

## Come cambiare il tipo di asse e personalizzare le proprietà dell'asse

Cambiare il tipo di asse (ad esempio da data a categoria) ti permette di controllare come i punti dati vengono tracciati. Questo snippet mostra anche come **nascondere l'asse del grafico** se preferisci un design minimalista.

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

// Example of hiding the Y axis.
yAxis.setHidden(true);

yAxis.setTickLabelPosition(AxisTickLabelPosition.HIGH);
yAxis.setMajorUnit(100.0);
yAxis.setMinorUnit(50.0);
yAxis.getDisplayUnit().setUnit(AxisBuiltInUnit.HUNDREDS);
yAxis.getScaling().setMinimum(new AxisBound(100.0));
yAxis.getScaling().setMaximum(new AxisBound(700.0));

doc.save("Your Directory Path" + "WorkingWithCharts.DefineXYAxisProperties.docx");
```

### Cambiare il tipo di asse

`xAxis.setCategoryType(AxisCategoryType.CATEGORY)` **cambia il tipo di asse** da un asse basato su data a uno categorico, offrendoti il pieno controllo sul posizionamento delle etichette.

## Come formattare le etichette dei dati del grafico (formati numerici)

Puoi applicare la formattazione numerica direttamente all'asse o alle etichette dei dati. Questo esempio formatta i numeri dell'asse Y con un separatore delle migliaia.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
Shape shape = builder.insertChart(ChartType.COLUMN, 432.0, 252.0);
Chart chart = shape.getChart();

// Clear default series and add your data.

chart.getAxisY().getNumberFormat().setFormatCode("#,##0");

doc.save("Your Directory Path" + "WorkingWithCharts.NumberFormatForAxis.docx");
```

## Personalizzazioni aggiuntive del grafico

Oltre alle basi, puoi regolare i limiti, impostare unità di intervallo tra le etichette, nascondere assi specifici e molto altro. Consulta la documentazione dell'API Aspose.Words per Java per l'elenco completo delle proprietà.

## Domande frequenti

**D: Come posso aggiungere più serie a un grafico?**  
R: Usa `chart.getSeries().add()` per ogni serie che desideri visualizzare. Ogni chiamata può fornire un nome unico, un array di categorie e un array di valori.

**D: Come formattare le etichette dei dati del grafico con formati numerici personalizzati?**  
R: Accedi all'oggetto `DataLabels` di una serie e chiama `getNumberFormat().setFormatCode("il tuo formato")`. Puoi anche collegare il formato a una cella di origine con `isLinkedToSource(true)`.

**D: Come posso nascondere un asse del grafico?**  
R: Chiama `setHidden(true)` sul `ChartAxis` che desideri nascondere (ad esempio `chart.getAxisY().setHidden(true)`).

**D: Qual è il modo migliore per cambiare il tipo di asse?**  
R: Usa `setCategoryType(AxisCategoryType.CATEGORY)` per assi categorici o `AxisCategoryType.DATE` per assi basati su data.

**D: Come aggiungere etichette dati a una serie?**  
R: Abilita le etichette con `series.hasDataLabels(true)` e poi configura la visibilità usando `series.getDataLabels().setShowValue(true)`.

## Conclusione

Abbiamo coperto tutto ciò che ti serve per **creare visualizzazioni di grafici a colonne** con Aspose.Words per Java—dall'inserimento di grafici di base e l'aggiunta di più serie, alla formattazione delle etichette dei dati, al cambiamento del tipo di asse e al nascondere gli assi per un aspetto pulito. Integra queste tecniche nei tuoi flussi di reporting o di generazione di documenti per fornire documenti Word professionali e basati sui dati.

---

**Ultimo aggiornamento:** 2025-12-13  
**Testato con:** Aspose.Words per Java 24.12 (ultima versione)  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}