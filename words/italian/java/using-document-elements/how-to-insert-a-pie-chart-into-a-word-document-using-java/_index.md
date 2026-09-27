---
category: general
date: 2026-09-27
description: Impara come inserire un grafico a torta in un documento Word con Java,
  creare un grafico a torta in Word e mostrare le percentuali sul grafico a torta
  per una chiara comprensione dei dati.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- create pie chart in word
- show percentages on pie chart
- add chart to word document
- how to add leader lines
language: it
lastmod: 2026-09-27
og_description: Come inserire un grafico a torta in un documento Word con Java. Questa
  guida ti mostra come creare un grafico a torta in Word, visualizzare le percentuali
  sul grafico a torta e aggiungere linee guida.
og_image_alt: Screenshot of a formatted pie chart inserted into a Word document
og_title: Come inserire un grafico a torta in un documento Word usando Java
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  headline: How to insert a pie chart into a Word document using Java
  type: TechArticle
- description: Learn how to insert pie chart into a Word document with Java, create
    pie chart in Word, and show percentages on pie chart for clear data insight.
  name: How to insert a pie chart into a Word document using Java
  steps:
  - name: Expected output
    text: '![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image
      alt="Formatted pie chart inserted into a Word document"}'
  - name: Changing slice values
    text: 'If you need custom data, replace the default series values:'
  - name: Multiple series (donut chart)
    text: While a simple pie chart has one series, Aspose.Words also supports donut
      charts with multiple series. Switch `ChartType.PIE` to `ChartType.DONUT` and
      repeat the series‑configuration steps.
  - name: Exporting to PDF
    text: If your downstream workflow requires PDF, call `doc.save("output/PieFormatted.pdf");`
      after the chart is built. The visual layout remains identical.
  type: HowTo
tags:
- Java
- Aspose.Words
- Word automation
- Chart
title: Come inserire un grafico a torta in un documento Word usando Java
url: /it/java/using-document-elements/how-to-insert-a-pie-chart-into-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire un grafico a torta in un documento Word usando Java

Se hai bisogno di **how to insert pie chart** in un file Word, questa guida ti accompagna attraverso l’intero processo. Vedrai come **create pie chart in Word**, visualizzare le percentuali su ogni fetta e aggiungere linee guida per un aspetto curato.

L’automazione di Word spesso sembra ingombrante, ma con Aspose.Words for Java puoi generare documenti completamente formattati in modo programmatico. Alla fine di questo tutorial avrai uno snippet Java eseguibile che produce un documento Word contenente un grafico a torta stilizzato.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- Java 17 o versioni successive installate
- Maven o Gradle per gestire le dipendenze
- Aspose.Words for Java (versione 23.11 o più recente) aggiunto al tuo progetto
- Familiarità di base con la sintassi Java

Non è necessaria alcuna esperienza pregressa con le API dei grafici; i passaggi seguenti coprono tutto, dalla configurazione del progetto al risultato finale.

## Passo 1: Configurare la dipendenza Maven

Aggiungi la libreria Aspose.Words al tuo `pom.xml`. Questa singola dipendenza ti dà accesso a `Document`, `DocumentBuilder` e alle classi dei grafici.

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.11</version>
</dependency>
```

Se usi Gradle, l’equivalente è:

```groovy
implementation 'com.aspose:aspose-words:23.11'
```

> **Suggerimento:** Usa l’ultima versione stabile per beneficiare di correzioni di bug e nuove funzionalità dei grafici.

## Passo 2: Creare un nuovo documento e un builder

L’oggetto `Document` rappresenta il file Word, mentre `DocumentBuilder` ti consente di inserire contenuti. Questa è la base per **add chart to word document**.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Il builder è ora pronto a posizionare oggetti ovunque nel documento.

## Passo 3: Inserire un grafico a torta

Aspose.Words supporta diversi tipi di grafico; scegliamo `ChartType.PIE`. La dimensione è espressa in punti (1 punto = 1/72 di pollice).

```java
        // Step 3: Insert a pie chart with a size of 400x300 points
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);
```

A questo punto il grafico contiene una serie di dati predefinita con valori segnaposto. Potrai sostituire tali valori in seguito, se necessario.

## Passo 4: Accedere alla serie del grafico

Un grafico a torta ha una singola serie che contiene i valori delle fette. Recuperala per applicare la formattazione.

```java
        // Step 4: Get the first (and only) series
        ChartSeries series = chart.getSeries().get(0);
```

## Passo 5: Esplodere la prima fetta

Esplodere una fetta attira l’attenzione su un punto dati specifico. È un indizio visivo comune quando vuoi evidenziare una metrica chiave.

```java
        // Step 5: Explode the first slice
        series.setExploded(true);
```

## Passo 6: Mostrare le percentuali su ogni fetta

Visualizzare le percentuali direttamente sul grafico migliora la comprensione dei dati. Questo soddisfa il requisito **show percentages on pie chart**.

```java
        // Step 6: Show percentages on each slice
        series.setShowPercentage(true);
```

## Passo 7: Aggiungere linee guida per etichette più chiare

Le linee guida collegano le etichette delle fette alle rispettive sezioni, eliminando ambiguità. Questo realizza **how to add leader lines**.

```java
        // Step 7: Add leader lines so labels are clearly connected
        series.setShowLeaderLines(true);
```

## Passo 8: Salvare il documento

Infine, scrivi il documento su disco. Puoi scegliere qualsiasi cartella a cui hai accesso in scrittura.

```java
        // Step 8: Save the document with the formatted pie chart
        doc.save("output/PieFormatted.docx");
    }
}
```

Eseguendo il programma viene creato `output/PieFormatted.docx`. Apri il file in Microsoft Word e vedrai un grafico a torta dove:

- La prima fetta è esplosa.
- Ogni fetta mostra il valore percentuale.
- Le linee guida puntano dalle percentuali alle fette corrispondenti.

### Output previsto

![Formatted pie chart in Word](/images/pie-formatted.png){: .center-image alt="Grafico a torta formattato inserito in un documento Word"}

Lo screenshot (il testo alternativo utilizza la keyword principale) illustra l’aspetto finale: un grafico a torta pulito e basato sui dati, pronto per report, proposte o dashboard.

## Varianti comuni e casi limite

### Modifica dei valori delle fette

Se ti servono dati personalizzati, sostituisci i valori della serie predefinita:

```java
double[] values = {30, 45, 25};
String[] categories = {"Apples", "Bananas", "Cherries"};
series.getDataLabelCollection().clear(); // remove placeholder labels

for (int i = 0; i < values.length; i++) {
    series.getData().add(values[i]);
    series.getCategory().add(categories[i]);
}
```

### Serie multiple (grafico a ciambella)

Mentre un semplice grafico a torta ha una sola serie, Aspose.Words supporta anche i grafici a ciambella con serie multiple. Cambia `ChartType.PIE` in `ChartType.DONUT` e ripeti i passaggi di configurazione della serie.

### Esportazione in PDF

Se il tuo flusso di lavoro richiede un PDF, chiama `doc.save("output/PieFormatted.pdf");` dopo aver costruito il grafico. Il layout visivo rimane identico.

## Elenco completo del codice sorgente

Di seguito trovi il file Java completo e autonomo che puoi copiare‑incollare nel tuo IDE.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Initialize a blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 400x300‑point pie chart
        Chart chart = builder.insertChart(ChartType.PIE, 400, 300);

        // Access the single series in the pie chart
        ChartSeries series = chart.getSeries().get(0);

        // Explode the first slice for emphasis
        series.setExploded(true);

        // Show percentages on each slice
        series.setShowPercentage(true);

        // Add leader lines for clear label connections
        series.setShowLeaderLines(true);

        // Save the document
        doc.save("output/PieFormatted.docx");
    }
}
```

Compila ed esegui il programma con `mvn compile exec:java -Dexec.mainClass=PieChartExample` (o il comando equivalente di Gradle). Il file Word generato conterrà il grafico a torta completamente formattato.

## Conclusione

Ora sai **how to insert pie chart** in un documento Word usando Java, come **create pie chart in Word**, come **show percentages on pie chart** e come **add chart to word document** con linee guida. L’esempio completo dimostra ogni passaggio, spiega perché il codice è scritto in quel modo e fornisce suggerimenti per la personalizzazione.

Prossimamente potresti esplorare:

- Aggiungere etichette dati con caratteri personalizzati (**show percentages on pie chart** varianti)
- Combinare più grafici in un unico documento (**add chart to word document** caso d’uso)
- Automatizzare la generazione di report con tabelle e grafici insieme

Sentiti libero di sperimentare con colori, ordine delle fette o esportazione in PDF. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API ed esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Nascondere l’asse del grafico in un documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Creare un grafico a linee in Word usando Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}