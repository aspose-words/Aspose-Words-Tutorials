---
category: general
date: 2026-09-27
description: Crea un grafico radiale in Java e inserisci il grafico in Word. Scopri
  come impostare le dimensioni del grafico, aggiungere serie di dati e generare un
  documento Word vuoto.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create radial chart
- insert chart into word
- create blank word document
- how to set chart size
- add data series chart
language: it
lastmod: 2026-09-27
og_description: Crea un grafico radiale in Java, poi inserisci il grafico in Word.
  Questa guida mostra come impostare le dimensioni del grafico, aggiungere serie di
  dati e creare un documento Word vuoto.
og_image_alt: Screenshot showing a radial chart inserted into a Word document created
  with Java
og_title: Crea un grafico radiale e inseriscilo in Word con Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create radial chart in Java and insert chart into Word. Learn how to
    set chart size, add data series, and generate a blank Word document.
  headline: Create radial chart and insert chart into Word with Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart generation
title: Crea un grafico radiale e inseriscilo in Word con Java
url: /it/java/word-processing/create-radial-chart-and-insert-chart-into-word-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un grafico radiale e inseriscilo in Word con Java

Se hai bisogno di **creare un grafico radiale** in un file Word usando Java, questo tutorial ti mostra esattamente come fare. Vedrai come **inserire il grafico in Word**, impostare le dimensioni del grafico e costruire un **documento Word vuoto** da zero.

Percorreremo tutti i passaggi necessari, dall’inizializzazione del documento all’aggiunta di una serie di dati e al salvataggio del file `.docx` finale. Alla fine avrai un file Word completamente funzionale contenente un grafico radiale e comprenderai **come impostare le dimensioni del grafico** e **come aggiungere una serie di dati al grafico** per future personalizzazioni.

## Prerequisiti

* Java 17 o successiva (il codice si compila con qualsiasi JDK moderno)
* Aspose.Words per Java 24.9 o più recente – il metodo `setShowGraduations` è disponibile solo da questa versione
* Un IDE o uno strumento di build (Maven/Gradle) che possa includere il JAR di Aspose.Words
* Familiarità di base con la sintassi Java e la gestione delle dipendenze Maven/Gradle

> **Consiglio professionale:** Se usi Maven, aggiungi quanto segue al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Passo 1: Crea un documento Word vuoto

Un documento vuoto è la tela su cui verrà posizionato il grafico. La classe `Document` rappresenta l’intero file `.docx`.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank Word document
```

Creare un documento vuoto garantisce che nessun contenuto preesistente interferisca con il layout del grafico.

## Passo 2: Inizializza un DocumentBuilder

`DocumentBuilder` fornisce metodi comodi per inserire oggetti, testo e altri elementi nel documento.

```java
        // Step 2: Initialise a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Il builder sarà poi utilizzato per **inserire il grafico in Word**.

## Passo 3: Costruisci il grafico radiale

Aspose.Words supporta molti tipi di grafico; `ChartType.RADIAL` crea un grafico radiale (polare).

```java
        // Step 3: Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);
```

A questo punto il grafico esiste ma non ha dati, dimensioni né opzioni visive.

## Passo 4: Aggiungi una serie di dati al grafico

Un grafico senza una serie di dati è vuoto. Il metodo `add` accetta un nome della serie e un array di valori.

```java
        // Step 4: Add a data series to the chart
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});
```

Puoi aggiungere più serie chiamando `add` più volte. Questo soddisfa il requisito **add data series chart**.

## Passo 5: Abilita le graduazioni (opzionale)

Le graduazioni sono le linee della griglia radiale che migliorano la leggibilità. Sono disponibili solo dalla versione 24.9.

```java
        // Step 5: Enable graduations on the chart (available from version 24.9)
        chart.getChartObject().setShowGraduations(true);
```

Se utilizzi una versione più vecchia di Aspose.Words, questa riga genererà un’eccezione—verifica quindi prima la versione della libreria.

## Passo 6: Imposta le dimensioni del grafico

Controllare le dimensioni del grafico ti permette di adattarlo bene ai margini della pagina. Questo risponde a **how to set chart size**.

```java
        // Step 6: Define the chart's dimensions
        chart.setWidth(400);   // width in points (≈5.5 inches)
        chart.setHeight(300);  // height in points (≈4.2 inches)
```

Puoi modificare i valori di larghezza e altezza per adattarli alle tue esigenze di layout. Ricorda che 1 punto ≈ 1/72 pollice.

## Passo 7: Inserisci il grafico nel documento Word

Ora il grafico è pronto per essere posizionato. Il metodo `insertChart` di `DocumentBuilder` gestisce l’inserimento.

```java
        // Step 7: Insert the chart into the document
        builder.insertChart(chart);
```

Questo è il cuore dell’operazione **insert chart into word**.

## Passo 8: Salva il documento

Infine, scrivi il documento su disco. Il file conterrà il grafico radiale appena creato.

```java
        // Step 8: Save the document with the chart
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Eseguendo il programma otterrai `RadialChart.docx` nella directory di lavoro del progetto. Aprendo il file in Microsoft Word vedrai un grafico radiale con tre punti dati e graduazioni visibili.

### Output previsto

* Un file Word chiamato `RadialChart.docx`
* All’interno del file, una singola pagina contenente un grafico radiale dimensionato 400 × 300 punti
* Il grafico mostra una serie intitolata **Series 1** con valori **10, 20, 30**
* Le graduazioni (linee della griglia radiale) sono visibili attorno al grafico

## Varianti comuni e casi limite

| Situazione | Cosa cambiare | Motivo |
|------------|----------------|--------|
| **Serie multiple** | Chiama `chart.getSeries().add(...)` per ogni serie | Consente visualizzazioni comparative dei dati |
| **Tipo di grafico diverso** | Sostituisci `ChartType.RADIAL` con `ChartType.COLUMN` (o qualsiasi altro) | Usa il tipo di grafico più adatto ai tuoi dati |
| **Colori personalizzati** | Accedi a `chart.getSeries().get(i).getFormat().getFill().setForeColor(Color)` | Migliora l’identità visiva del brand |
| **Versione Aspose.Words più vecchia** | Ometti la riga `setShowGraduations` o aggiorna la libreria | Previene `NoSuchMethodError` |
| **Salvataggio in formato diverso** | Usa `doc.save("RadialChart.pdf", SaveFormat.PDF)` | Genera un PDF invece di un DOCX |

## Esempio completo eseguibile

Di seguito trovi il programma Java completo e autonomo. Copialo in un file chiamato `RadialChartExample.java`, aggiungi la dipendenza Aspose.Words e eseguilo.

```java
import com.aspose.words.*;

public class RadialChartExample {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank Word document
        Document doc = new Document();

        // 2. Initialise a DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Create a radial chart
        Chart chart = new Chart(doc, ChartType.RADIAL);

        // 4. Add a data series (add data series chart)
        chart.getSeries().add("Series 1", new double[] {10, 20, 30});

        // 5. Enable graduations (requires Aspose.Words 24.9+)
        chart.getChartObject().setShowGraduations(true);

        // 6. Set chart size (how to set chart size)
        chart.setWidth(400);
        chart.setHeight(300);

        // 7. Insert the chart into the document (insert chart into word)
        builder.insertChart(chart);

        // 8. Save the document (create blank word document with chart)
        String outputPath = "RadialChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

## Conclusione

Ora sai come **creare un grafico radiale** programmaticamente, **aggiungere una serie di dati al grafico**, controllare **come impostare le dimensioni del grafico** e **inserire il grafico in Word** partendo da un **documento Word vuoto**. L’esempio utilizza Aspose.Words per Java 24.9, ma gli stessi concetti valgono per altre librerie di grafici che espongono un’API simile.

### Prossimi passi

* Esplora altri tipi di grafico (`ChartType.PIE`, `ChartType.LINE`, ecc.) – questo ricollega alla keyword secondaria **insert chart into word**.
* Personalizza le etichette degli assi, le legende e i colori per allinearle alle linee guida del tuo brand.
* Genera grafici dinamicamente da query di database o file CSV.
* Converti il `.docx` risultante in PDF per la distribuzione (`doc.save("output.pdf", SaveFormat.PDF)`).

Sentiti libero di sperimentare con le dimensioni, i dati delle serie e le opzioni di stile per creare l’aspetto esatto di cui hai bisogno. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Area Chart Into A Word Document](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}