---
category: general
date: 2026-10-04
description: Impara come esplodere una sezione in un grafico Word, esplodere una fetta
  di grafico a torta e modificare le dimensioni del grafico a ciambella con un esempio
  Java passo‑passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to explode slice
- modify chart in word
- explode pie chart slice
- change doughnut chart size
- customize pie chart word
language: it
lastmod: 2026-10-04
og_description: Come far esplodere una fetta in un grafico Word e personalizzare i
  grafici a torta o a ciambella con Java. Segui l'esempio completo per modificare
  il grafico in Word.
og_image_alt: Screenshot showing an exploded pie chart slice inside a Word document
og_title: Come far esplodere una fetta in un grafico Word – guida completa Java
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to explode slice in a Word chart, explode pie chart slice
    and change doughnut chart size with a step‑by‑step Java example.
  headline: How to explode slice in a Word chart and customize its appearance
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Come esplodere una fetta in un grafico Word e personalizzarne l'aspetto
url: /it/java/document-styling/how-to-explode-slice-in-a-word-chart-and-customize-its-appea/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come esplodere una sezione in un grafico Word e personalizzarne l'aspetto

Se hai bisogno di **come esplodere una sezione** in un grafico Word, questa guida ti mostra esattamente come fare. Che tu stia preparando una presentazione di vendita o un rapporto finanziario, esplodere una fetta di un grafico a torta o regolare il foro di un grafico a ciambella può far risaltare i dati più importanti. Nelle sezioni seguenti imparerai anche a **modificare il grafico in Word**, **esplodere la fetta del grafico a torta**, **cambiare la dimensione del grafico a ciambella** e **personalizzare i documenti Word con grafici a torta** usando Aspose.Words for Java.

Concluderai questo tutorial con un programma Java completo, pronto all'esecuzione, che carica un file `.docx`, esplode la prima fetta di un grafico a torta, modifica la dimensione del foro della ciambella e salva il risultato. Non sono necessari script esterni né modifiche manuali.

## Prerequisiti

- Java 17 o versioni successive installate sulla tua macchina di sviluppo.  
- Maven 3.6+ (o Gradle) per gestire le dipendenze.  
- Libreria Aspose.Words for Java (la versione di prova gratuita è sufficiente per lo sviluppo).  
- Un documento Word (`input.docx`) che contenga almeno un grafico (a torta o a ciambella).

## Passo 1: Aggiungere Aspose.Words al progetto

Se usi Maven, aggiungi la seguente dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Per Gradle, inserisci questo in `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.9'
```

> **Suggerimento professionale:** Mantieni la versione della libreria aggiornata; le versioni più recenti aggiungono il supporto per nuovi tipi di grafico e migliorano le prestazioni.

## Passo 2: Caricare il documento Word che contiene un grafico

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // Path to the source .docx file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – this step is required before any chart manipulation.
        Document doc = new Document(inputPath);
```

**Perché è importante:** Il caricamento del documento crea una rappresentazione in memoria che Aspose.Words può attraversare. Senza questo oggetto non è possibile accedere ai nodi del grafico.

## Passo 3: Recuperare il primo grafico nel documento

```java
        // Locate the first Shape node that contains a chart.
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);

        // Cast the Shape to a Chart object.
        Chart chart = chartShape.getChart();
```

> **Spiegazione:** `NodeType.SHAPE` copre tutti gli oggetti di disegno, inclusi i grafici. L'argomento `true` indica ad Aspose di cercare in modo ricorsivo, garantendo che il primo grafico venga trovato anche se è annidato all'interno di una tabella.

## Passo 4: Esplodere la prima fetta di un grafico a torta

```java
        // Verify the chart type before exploding.
        if (chart.getChartType() == ChartType.PIE) {
            // Explode the first series (slice) by 20 points.
            chart.getSeries().get(0).setExplosion(20);
        } else {
            System.out.println("The first chart is not a pie chart; explosion skipped.");
        }
```

**Come funziona:** Il metodo `setExplosion` accetta un valore numerico che determina quanto la fetta si sposti dal centro. Un valore di `20` è visivamente evidente senza rompere il layout del grafico.

## Passo 5: Regolare la dimensione del foro della ciambella per un grafico a ciambella

```java
        // If the chart is a doughnut, change the hole size.
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            // Set the doughnut hole size to 40% of the chart radius.
            chart.setDoughnutHoleSize(40);
        } else {
            System.out.println("The first chart is not a doughnut chart; hole size unchanged.");
        }
```

**Perché è utile:** Un foro più grande può migliorare la leggibilità quando hai molti punti dati. Il metodo `setDoughnutHoleSize` accetta una percentuale (0‑100).

## Passo 6: Salvare il documento modificato

```java
        // Path for the output document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";

        // Save the changes – the file now contains the exploded slice and updated doughnut size.
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

### Output previsto

- La prima fetta del primo grafico a torta è spostata verso l'esterno, facendola risaltare.  
- Se il grafico è una ciambella, il foro centrale si espande al 40 % del raggio del grafico.  
- Il file risultante `PieChart.docx` può essere aperto in Microsoft Word, LibreOffice o qualsiasi visualizzatore compatibile, mostrando le modifiche visive applicate programmaticamente.

## Esempio completo, eseguibile

Di seguito trovi l'intero programma in un unico blocco. Copialo in `ChartExploder.java`, adatta i percorsi dei file e eseguilo con `mvn compile exec:java` (o la configurazione di esecuzione del tuo IDE).

```java
import com.aspose.words.*;

public class ChartExploder {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the source document
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Find the first chart shape
        Shape chartShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        if (chartShape == null) {
            System.out.println("No chart found in the document.");
            return;
        }

        // 3️⃣ Cast to Chart
        Chart chart = chartShape.getChart();

        // 4️⃣ Explode the first slice if it is a pie chart
        if (chart.getChartType() == ChartType.PIE) {
            chart.getSeries().get(0).setExplosion(20);
            System.out.println("Exploded first slice of the pie chart.");
        }

        // 5️⃣ Change doughnut hole size if it is a doughnut chart
        if (chart.getChartType() == ChartType.DOUGHNUT) {
            chart.setDoughnutHoleSize(40);
            System.out.println("Set doughnut hole size to 40%.");
        }

        // 6️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/PieChart.docx";
        doc.save(outputPath);
        System.out.println("Modified document saved as " + outputPath);
    }
}
```

L'esecuzione di questo codice **modificherà il grafico in Word**, **esploderà la fetta del grafico a torta** e **cambierà la dimensione del grafico a ciambella** automaticamente.

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|--------|
| *E se il documento contiene più grafici?* | L'esempio si rivolge al **primo** grafico (`NodeType.SHAPE, 0`). Per lavorare con altri grafici, cambia l'indice o itera su `doc.getChildNodes(NodeType.SHAPE, true)` filtrando con `shape.getChart() != null`. |
| *Posso esplodere una fetta diversa dalla prima?* | Sì. Accedi alla serie desiderata tramite `chart.getSeries().get(seriesIndex)` e chiama `setExplosion(value)`. Gli indici partono da zero. |
| *Funziona con file Word 2007‑2021?* | Aspose.Words supporta `.doc`, `.docx`, `.dot` e `.dotx`. Lo stesso codice funziona su tutte le versioni perché la libreria astrae il formato del file. |
| *E se il grafico è a barre o a linee?* | `setExplosion` e `setDoughnutHoleSize` sono applicabili solo ai grafici di tipo torta. Il codice salta in sicurezza queste operazioni quando il tipo di grafico è diverso. |
| *È necessaria una licenza per Aspose.Words?* | Una licenza di valutazione gratuita rimuove il limite di 30 giorni ma aggiunge una filigrana. Per la produzione, acquista una licenza per rimuovere la filigrana e sbloccare tutte le funzionalità. |

## Conclusione

Ora sai **come esplodere una sezione** in un grafico Word, come **modificare il grafico in Word** e come **cambiare la dimensione del grafico a ciambella** usando Aspose.Words for Java. L'esempio completo dimostra l'intero flusso di lavoro — dal caricamento del documento, alla localizzazione del grafico, all'applicazione delle modifiche visive, fino al salvataggio del risultato — così da poter integrare questi passaggi in qualsiasi pipeline di reporting o generazione di documenti.

**Passi successivi**

- Esplora altre personalizzazioni dei grafici, come cambiare i colori, aggiungere etichette dati o cambiare il tipo di grafico (`chart.setChartType(ChartType.BAR_CLUSTERED)`).  
- Combina questa logica con Aspose.PDF per generare una versione PDF dello stesso rapporto.  
- Automatizza il processo per un batch di documenti iterando sui file in una cartella.

Sentiti libero di sperimentare con valori di esplosione diversi o percentuali del foro della ciambella per adeguarli alle linee guida di design. Buona programmazione!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Insert Bubble Chart In Word Document](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}