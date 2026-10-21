---
category: general
date: 2026-09-18
description: Impara a creare un documento Word e inserire un grafico a torta usando
  Aspose.Words per Java. Include la rotazione del grafico a torta e i passaggi per
  generare il file Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- insert pie chart
- rotate pie chart
- generate word file
- how to create pie chart
language: it
lastmod: 2026-09-18
og_description: Crea un documento Word e inserisci un grafico a torta usando Java.
  Segui questa guida per ruotare il grafico a torta, far esplodere le fette e generare
  un file Word.
og_image_alt: Screenshot showing a Word document containing a pie chart created with
  Java
og_title: Crea un documento Word con un grafico a torta – guida Java passo‑passo
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  headline: How to create a Word document with a pie chart in Java
  type: TechArticle
- description: Learn to create a Word document and insert pie chart using Aspose.Words
    for Java. Includes rotate pie chart and generate Word file steps.
  name: How to create a Word document with a pie chart in Java
  steps:
  - name: Expected output
    text: 'After running the program, open `output/PieChart.docx`. You should see:'
  - name: Inserting multiple charts
    text: 'If you need more than one chart, call `builder.insertChart` again after
      moving the cursor:'
  - name: Changing chart colors
    text: 'You can customize slice colors via the series'' `getPoints()` collection:'
  - name: Handling large datasets
    text: For datasets with more than 10 slices, consider using a doughnut chart (`ChartType.DOUGHNUT`)
      to keep the visual clear.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart
- Word automation
title: Come creare un documento Word con un grafico a torta in Java
url: /it/java/images-shapes/how-to-create-a-word-document-with-a-pie-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word con un grafico a torta in Java

Se hai bisogno di **creare un documento Word** che visualizzi dati, questa guida ti mostra come farlo con Aspose.Words per Java. Imparerai a inserire un grafico a torta, a far esplodere una fetta, a ruotare il grafico e, infine, a **generare un file Word** che potrai aprire con Microsoft Word.

Creare report che combinano testo e grafici non richiede uno strumento grafico separato. Alla fine di questo tutorial avrai un programma completo e funzionante che crea un file .docx contenente un grafico a torta completamente configurato.

## Prerequisiti

- Java 17 o versioni successive (il codice si compila anche con Java 8+)
- Maven o Gradle per la gestione delle dipendenze
- Licenza Aspose.Words per Java (la versione di prova gratuita funziona per questo esempio)
- Familiarità di base con la sintassi Java

## Passo 1: Configurare il progetto Maven

Crea un nuovo progetto Maven e aggiungi la dipendenza Aspose.Words al file `pom.xml`:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-pie-chart</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.12</version>
        </dependency>
    </dependencies>
</project>
```

> **Suggerimento:** Mantieni il numero di versione aggiornato; le versioni più recenti includono miglioramenti ai tipi di grafico e correzioni di bug.

## Passo 2: Creare un nuovo documento Word

La prima operazione quando **crei un documento Word** programmaticamente è istanziare un oggetto `Document`. Questo oggetto rappresenta l'intero file .docx in memoria.

```java
import com.aspose.words.*;

public class PieChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2: Create a blank document
        Document doc = new Document();

        // Continue with chart insertion...
```

La classe `Document` è il punto di ingresso per tutte le funzionalità di elaborazione testi. Nessun file viene scritto su disco a questo punto; tutto avviene in RAM fino a quando non chiami `save`.

## Passo 3: Come inserire un grafico a torta

Un `DocumentBuilder` ti consente di aggiungere contenuti al documento. Con `insertChart` puoi **inserire grafici a torta** direttamente.

```java
        // Step 3: Initialize DocumentBuilder
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a pie chart with width=400pt, height=300pt
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

`ChartType.PIE` indica ad Aspose.Words di creare un grafico a torta. Le dimensioni sono espresse in punti (1 pt ≈ 1/72 in). Dopo questa chiamata il grafico appare in un nuovo paragrafo.

## Passo 4: Popolare il grafico con i dati

Un grafico a torta necessita di una serie di valori. Qui aggiungiamo tre categorie: “Apples”, “Bananas” e “Cherries”.

```java
        // Create a data series
        chart.getSeries().add("Fruits", new String[]{"Apples", "Bananas", "Cherries"},
                new double[]{30, 45, 25});
```

Il metodo `add` costruisce la serie e crea automaticamente le voci della legenda. Puoi riutilizzare questo schema per qualsiasi insieme di dati numerico.

## Passo 5: Evidenziare la prima fetta

Far esplodere una fetta attira l'attenzione su un valore particolare. La prima fetta (indice 0) è esplosa di 20 punti.

```java
        // Step 5: Explode the first slice
        chart.getSeries().get(0).setExplode(20);
```

Impostare `explode` sulla serie influisce sull'intero grafico, quindi solo il primo punto dati è spostato.

## Passo 6: Come ruotare un grafico a torta

Ruotare il grafico migliora l'equilibrio visivo, soprattutto quando la fetta più grande non è in alto. Il metodo `setRotationAngle` accetta i gradi.

```java
        // Step 6: Rotate the chart 45 degrees
        chart.setRotationAngle(45);
```

Una rotazione di 45° sposta l'angolo di partenza in senso orario, rendendo il grafico più leggibile in molti layout.

## Passo 7: Salvare il documento e generare un file Word

Infine, scrivi il documento su disco. Questo passaggio **genera un file Word** che può essere aperto con Microsoft Word, LibreOffice o qualsiasi visualizzatore compatibile.

```java
        // Step 7: Save the document
        String outputPath = "output/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Il metodo `save` rileva automaticamente l'estensione .docx e scrive un pacchetto compatibile con Word. La cartella `output` deve esistere oppure puoi crearla programmaticamente.

### Output previsto

Dopo aver eseguito il programma, apri `output/PieChart.docx`. Dovresti vedere:

- Una singola pagina contenente un grafico a torta di 400 × 300 pt.
- La fetta “Apples” esplosa verso l'esterno di 20 pt.
- L'intero grafico ruotato di 45° in senso orario.
- Una legenda che corrisponde alle tre categorie di frutta.

## Variazioni comuni e casi limite

### Inserire più grafici

Se ti serve più di un grafico, chiama nuovamente `builder.insertChart` dopo aver spostato il cursore:

```java
builder.writeln();               // Add a line break
Chart secondChart = builder.insertChart(ChartType.PIE, 300, 200);
```

### Cambiare i colori del grafico

Puoi personalizzare i colori delle fette tramite la collezione `getPoints()` della serie:

```java
chart.getSeries().get(0).getPoints().get(0).getFormat().getFill().setForeColor(Color.RED);
```

### Gestire dataset di grandi dimensioni

Per dataset con più di 10 fette, considera l'uso di un grafico a ciambella (`ChartType.DOUGHNUT`) per mantenere la visuale chiara.

## Conclusione

Ora sai come **creare un documento Word**, **inserire un grafico a torta**, **ruotare il grafico a torta** e **generare un file Word** usando Aspose.Words per Java. La soluzione completa dimostra l'intero flusso di lavoro, dall'inizializzazione del documento alla generazione finale del file, coprendo sia il “come” sia il “perché” di ogni passaggio.

Successivamente, esplora argomenti correlati come **come creare dati per un grafico a torta** da un database, aggiungere etichette dati o esportare il grafico come immagine. Sperimenta con diversi tipi di grafico (bar, line, doughnut) per ampliare il tuo toolkit di automazione Word.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}