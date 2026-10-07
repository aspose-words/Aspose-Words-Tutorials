---
category: general
date: 2026-10-07
description: Scopri come creare un grafico a torta in Word, aggiungere serie di dati
  e salvare il grafico come PNG usando Java. Segui la guida passo‑passo per risultati
  rapidi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add data series
- save chart as png
- generate pie chart in word
- save word chart as image
language: it
lastmod: 2026-10-07
og_description: 'Crea rapidamente un grafico a torta in Word: questo tutorial mostra
  come aggiungere serie di dati, generare il grafico e salvare il grafico di Word
  come immagine (PNG). Segui l''esempio di codice completo.'
og_image_alt: Screenshot of a create pie chart result in a Word document
og_title: Crea un grafico a torta in Word ed esportalo come PNG – guida
schemas:
- author: GroupDocs
  dateModified: '2026-10-07'
  description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  headline: How to create a pie chart in Word and save it as PNG
  type: TechArticle
- description: Learn how to create a pie chart in Word, add data series, and save
    the chart as PNG using Java. Follow the step‑by‑step guide for quick results.
  name: How to create a pie chart in Word and save it as PNG
  steps:
  - name: Load the source document
    text: You must open the Word file that will host the chart. The `Document` class
      reads the `.docx` content into memory.
  - name: Add data series to the chart
    text: Creating a **pie chart** starts with a `Chart` instance. The constructor
      receives the parent `Document` and the chart type (`ChartType.PIE`). After the
      chart object exists, you populate it with numeric values and optional labels.
  - name: Save chart as PNG
    text: Once the chart is part of the document, you can export the visual representation.
      The `save` method on the underlying chart object writes a PNG file to the file
      system.
  type: HowTo
tags:
- Java
- Word automation
- Chart generation
title: Come creare un grafico a torta in Word e salvarlo come PNG
url: /it/java/document-conversion-and-export/how-to-create-a-pie-chart-in-word-and-save-it-as-png/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico a torta in Word e salvarlo come PNG

Se hai bisogno di **creare grafici a torta** all'interno di un file Microsoft Word, questa guida ti mostra esattamente come farlo con Java. Imparerai anche come **aggiungere serie di dati** al grafico e **salvare il grafico come PNG** così che l'immagine possa essere riutilizzata al di fuori di Word.

Generare un grafico direttamente in un documento ti evita di esportare i dati in uno strumento grafico separato. Alla fine di questo tutorial avrai un file Word completamente funzionante che contiene un grafico a torta e un'immagine PNG corrispondente sul disco.

## Prerequisiti

* Java 17 o versioni successive installato.
* Il **GroupDocs.Viewer for Java** (o una libreria compatibile che fornisce le classi `Document`, `Chart`, `ChartType` e `ImageSaveOptions`).
* Un progetto Maven o Gradle dove puoi aggiungere la dipendenza della libreria.
* Un documento Word di input (`input.docx`) situato in una cartella a cui puoi fare riferimento dal codice.

Se utilizzi Maven, aggiungi la dipendenza (sostituisci `VERSION` con l'ultima release):

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-viewer</artifactId>
    <version>VERSION</version>
</dependency>
```

## Come creare un grafico a torta in Word

Il nucleo della soluzione ruota attorno a tre azioni:

1. Caricare il file `.docx` sorgente.
2. **Aggiungere serie di dati** a un nuovo oggetto `Chart` di tipo `PIE`.
3. **Salvare il grafico come PNG** così ottieni un file immagine accanto al documento Word.

Di seguito ogni passaggio è spiegato in dettaglio, seguito dal codice Java esatto di cui hai bisogno.

### Passo 1: Caricare il documento sorgente

Devi aprire il file Word che conterrà il grafico. La classe `Document` legge il contenuto `.docx` in memoria.

```java
// Step 1: Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Perché è importante*: Caricare il documento crea un modello mutabile. Tutte le operazioni successive sul grafico modificano questa rappresentazione in memoria, che poi persisterai nuovamente su disco.

### Passo 2: Aggiungere serie di dati al grafico

Creare un **grafico a torta** inizia con un'istanza `Chart`. Il costruttore riceve il `Document` genitore e il tipo di grafico (`ChartType.PIE`). Dopo che l'oggetto chart esiste, lo popoli con valori numerici e etichette opzionali.

```java
// Step 2: Create a pie chart and configure its data series
Chart chart = new Chart(doc, ChartType.PIE);

// Example: add a data series (replace with your actual data)
double[] values = { 30, 20, 50 };
String[] categories = { "A", "B", "C" };
chart.getSeries().add(values, categories);
```

*Perché è importante*: Il metodo `add` **aggiunge serie di dati** al grafico. Ogni voce in `values` diventa una fetta della torta, mentre `categories` fornisce le etichette della legenda. Puoi fornire un numero qualsiasi di punti; la libreria calcolerà automaticamente gli angoli delle fette.

### Passo 3: Salvare il grafico come PNG

Una volta che il grafico fa parte del documento, puoi esportare la rappresentazione visiva. Il metodo `save` sull'oggetto chart sottostante scrive un file PNG nel file system.

```java
// Step 3: Save the chart as a PNG image (graduations are added automatically)
chart.getChartShape()
     .getChart()
     .save("YOUR_DIRECTORY/radial.png",
           ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

*Perché è importante*: Salvare il grafico come PNG ti fornisce un'immagine raster che può essere incorporata in pagine web, email o report senza richiedere il file Word originale. L'oggetto `ImageSaveOptions` ti consente di controllare il formato, la risoluzione e altre impostazioni di esportazione.

## Generare un grafico a torta in Word – personalizzare l'aspetto

Oltre ai passaggi base, potresti voler personalizzare colori, titoli o etichette dei dati. La maggior parte delle librerie espone un oggetto `ChartOptions` o simile. Ecco un rapido esempio che aggiunge un titolo e cambia i colori delle fette:

```java
chart.getChart().setTitle("Sales Distribution Q1");

// Set custom colors (RGB format)
chart.getSeries().get(0).setColors(new int[] {
    0xFF5733, // slice A – orange
    0x33FF57, // slice B – green
    0x3357FF  // slice C – blue
});
```

Queste personalizzazioni sono opzionali ma illustrano come puoi **generare un grafico a torta in Word** che corrisponde al tuo brand.

## Salvare il grafico Word come immagine – approcci alternativi

Se ti serve solo l'immagine e non il grafico all'interno del documento, puoi omettere l'inserimento della forma del grafico nel file Word e chiamare direttamente il metodo `save` dopo aver creato il grafico. Il codice rimane lo stesso; semplicemente ometti i passaggi che aggiungono il grafico al corpo del documento.

```java
// Directly save the chart without embedding it in the document
chart.getChart().save("YOUR_DIRECTORY/pie_only.png",
                      ImageSaveOptions.createSaveOptions(SaveFormat.PNG));
```

## Esempio completo eseguibile

Copia la classe seguente nel tuo progetto, regola i percorsi dei file e eseguila. Il programma:

1. Caricare `input.docx`.
2. **Creare un grafico a torta**, **aggiungere serie di dati**, e incorporarlo nel documento.
3. **Salvare il grafico come PNG** (`radial.png`).
4. Persistere il file Word modificato come `output.docx`.



## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Creare un grafico a dispersione Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-scatter-chart/)
- [Inserire un grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-column-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}