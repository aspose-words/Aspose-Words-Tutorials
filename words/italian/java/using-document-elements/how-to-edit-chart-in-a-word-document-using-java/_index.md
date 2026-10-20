---
category: general
date: 2026-09-11
description: Come modificare un grafico in un documento Word con Java – impara ad
  aggiornare le impostazioni del grafico, abilitare le linee della griglia, modificare
  le opzioni del grafico e salvare il documento aggiornato.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit chart
- update chart settings
- save updated document
- change chart options
- enable chart gridlines
language: it
lastmod: 2026-09-11
og_description: Come modificare un grafico in un documento Word con Java. Segui questa
  guida per aggiornare le impostazioni del grafico, abilitare le linee della griglia,
  modificare le opzioni del grafico e salvare il documento aggiornato.
og_image_alt: Screenshot of a Word document showing a chart with gridlines enabled
og_title: Come modificare un grafico in un documento Word usando Java – guida completa
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  headline: How to edit chart in a Word document using Java
  type: TechArticle
- description: How to edit chart in a Word document with Java – learn to update chart
    settings, enable chart gridlines, change chart options, and save the updated document.
  name: How to edit chart in a Word document using Java
  steps:
  - name: Expected result
    text: 'When you open `output.docx`:'
  - name: What if the document has no chart?
    text: 'Attempting to cast a non‑chart shape will throw a `ClassCastException`.
      Guard against this by checking the shape type:'
  - name: How to edit a specific chart instead of the first one?
    text: 'Iterate through `shapes` and match a known title or an alternative identifier:'
  - name: Can I disable gridlines again later?
    text: 'Yes, simply set the property to `false`:'
  - name: Does this work with `.doc` (binary) files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. However, some newer chart features (like graduations) are only
      stored in the OOXML format, so you’ll see the effect only when saving as `.docx`.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart manipulation
title: Come modificare un grafico in un documento Word usando Java
url: /it/java/using-document-elements/how-to-edit-chart-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come modificare un grafico in un documento Word usando Java

Se hai bisogno di **modificare un grafico** in un file Word, questa guida ti mostra i passaggi esatti. Imparerai come aggiornare le impostazioni del grafico, abilitare le linee della griglia del grafico, modificare le opzioni del grafico e, infine, **salvare il documento aggiornato** senza perdere alcuna formattazione.

Lavorare con i grafici in modo programmatico spesso sembra un'operazione a scatola nera, soprattutto quando si desidera regolare dettagli visivi come le graduazioni o le linee della griglia. Questo tutorial copre tutto ciò che devi sapere, dal caricamento del documento al salvataggio delle modifiche. Non sono necessari strumenti esterni: basta la libreria Aspose.Words for Java (versione 24.9 o successiva).

Al termine di questo articolo sarai in grado di:

* Caricare un file `.docx` che contiene un grafico.
* Individuare la forma del grafico e modificarne le proprietà.
* Abilitare le linee della griglia del grafico (graduazioni) e regolare altre opzioni.
* **Salvare il documento aggiornato** in un nuovo file.

## Prerequisiti

* Java 17 o versione successiva installata sulla tua macchina.  
* Maven o Gradle per gestire le dipendenze.  
* Aspose.Words for Java 24.9+ (la versione che ha introdotto `setShowGraduations`).  
* Un documento Word (`input.docx`) che contiene già almeno un grafico.

Se non conosci Aspose.Words, pensalo come un'API completa che ti consente di leggere, modificare e scrivere documenti Word in modo programmatico—simile a come manipoleresti un DOM in un browser web.

## Passo 1: Configurare il progetto e importare la libreria

Crea un nuovo progetto Maven o aggiungi la dipendenza a uno esistente:

```xml
<!-- pom.xml -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

> **Pro tip:** Usa l'ultima versione stabile per assicurarti di avere il metodo `setShowGraduations`. Le versioni più vecchie non compileranno.

## Passo 2: Caricare il documento Word che contiene un grafico

La prima azione in qualsiasi flusso **come modificare un grafico** è caricare il file sorgente. Aspose.Words rappresenta l'intero documento con la classe `Document`.

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // Replace with the actual path to your input file
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document into memory
        Document doc = new Document(inputPath);
```

L'oggetto `Document` ti dà accesso a ogni nodo all'interno del file, incluse forme, tabelle e paragrafi.  

## Passo 3: Individuare la prima forma di grafico nel documento

I grafici sono memorizzati come nodi `Shape` il cui renderer è un `Chart`. Per modificare un grafico devi prima recuperare quel nodo.

```java
        // Find all shape nodes (including charts)
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);

        // Assume the first shape is a chart; adjust the index if needed
        Shape chartShape = (Shape) shapes.get(0);

        // Cast the shape renderer to Chart
        Chart chart = (Chart) chartShape.getChart();
```

Se il documento contiene più grafici, itera su `shapes` e verifica `chartShape.getChart() != null` prima del cast. Questo evita `ClassCastException` e garantisce che **modifichi le opzioni del grafico** solo su oggetti grafico validi.

## Passo 4: Abilitare le linee della griglia del grafico (graduazioni) – una nuova proprietà nella versione 24.9

La proprietà `setShowGraduations` attiva o disattiva la visibilità delle linee di griglia minori sull'asse dei valori. Abilitarle spesso migliora la leggibilità per insiemi di dati densi.

```java
        // Turn on gridlines (graduations) for the value axis
        chart.setShowGraduations(true);
```

> **Perché è importante:** Le linee di griglia forniscono allo spettatore un riferimento visivo per ogni punto dati, rendendo più facili da individuare le tendenze. Il valore predefinito è `false`, quindi devi abilitarle esplicitamente quando necessario.

Puoi anche personalizzare altri aspetti, come le linee di griglia principali, i titoli degli assi o la posizione della legenda. Di seguito un esempio di modifica del titolo del grafico e della posizione della legenda—entrambi parte di **modifica delle opzioni del grafico**.

```java
        // Change the chart title
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);

        // Move the legend to the bottom
        chart.getLegend().setPosition(LegendPosition.BOTTOM);
```

## Passo 5: Salvare il documento con le impostazioni del grafico aggiornate

Dopo aver modificato il grafico, persisti le modifiche. Questo passo completa la fase di **salvataggio del documento aggiornato**.

```java
        // Replace with the desired output path
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // Save the modified document
        doc.save(outputPath);
        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

Eseguendo il programma otterrai `output.docx` in cui il grafico ora mostra le linee di griglia, un nuovo titolo e una legenda spostata. Apri il file in Microsoft Word per verificare le modifiche visive.

## Codice sorgente completo (eseguibile)

```java
import com.aspose.words.*;

public class ChartEditor {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the Word document that contains a chart
        String inputPath = "YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Locate the first chart shape in the document
        NodeCollection shapes = doc.getChildNodes(NodeType.SHAPE, true);
        Shape chartShape = (Shape) shapes.get(0);
        Chart chart = (Chart) chartShape.getChart();

        // 3️⃣ Enable chart gridlines (graduations)
        chart.setShowGraduations(true);

        // 4️⃣ Change chart options (title and legend)
        chart.getTitle().setText("Sales Overview 2026");
        chart.getTitle().setOverlay(false);
        chart.getLegend().setPosition(LegendPosition.BOTTOM);

        // 5️⃣ Save the document with the updated chart settings
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("Chart edited and document saved to: " + outputPath);
    }
}
```

### Risultato atteso

Quando apri `output.docx`:

* Il grafico mostra le linee di griglia minori sull'asse dei valori.  
* Il titolo è **“Sales Overview 2026”**.  
* La legenda appare nella parte inferiore del grafico.

Se il grafico originale aveva già le linee di griglia, l'aspetto visivo rimane invariato, confermando che il codice è **idempotente**.

## Domande comuni e gestione dei casi limite

### E se il documento non contiene alcun grafico?

Tentare di effettuare il cast di una forma non grafico genererà una `ClassCastException`. Previeni questo controllo il tipo di forma:

```java
if (chartShape.getShapeType() == ShapeType.CHART) {
    Chart chart = (Chart) chartShape.getChart();
    // proceed with modifications
}
```

### Come modificare un grafico specifico invece del primo?

Itera su `shapes` e confronta un titolo noto o un identificatore alternativo:

```java
for (Node node : shapes) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.CHART) {
        Chart c = (Chart) shape.getChart();
        if ("Revenue Q1".equals(c.getTitle().getText())) {
            // modify this chart
        }
    }
}
```

### Posso disabilitare le linee di griglia in un secondo momento?

Sì, imposta semplicemente la proprietà su `false`:

```java
chart.setShowGraduations(false);
```

### Funziona con file `.doc` (binari)?

Aspose.Words astrae il formato del file, quindi lo stesso codice funziona per `.doc` e `.docx`. Tuttavia, alcune funzionalità più recenti dei grafici (come le graduazioni) sono memorizzate solo nel formato OOXML, quindi vedrai l'effetto solo salvando come `.docx`.

## Consigli per un codice pronto per la produzione

* **Convalida i percorsi di input** – usa `Files.exists(Paths.get(inputPath))` prima del caricamento.  
* **Avvolgi le chiamate API** in blocchi try‑catch per esporre i dettagli delle `Exception`, soprattutto quando si trattano documenti corrotti.  
* **Rilascia le risorse** – sebbene Aspose.Words gestisca la memoria, chiamare `doc.close()` (o usare try‑with‑resources se disponibile) può liberare le handle native più rapidamente.  
* **Controllo versione** – assicurati che la versione della libreria a runtime sia ≥ 24.9 prima di chiamare `setShowGraduations`. Puoi interrogare `License.getVersion()` se ti serve una verifica programmatica.

## Conclusione

Ora sai **come modificare gli oggetti grafico** in un documento Word usando Java. Il processo—caricare il documento, individuare il grafico, abilitare le linee di griglia, modificare le opzioni del grafico e **salvare il documento aggiornato**—copre gli scenari più comuni per la manipolazione programmatica dei grafici.  

Da qui puoi esplorare personalizzazioni aggiuntive come cambiare i colori delle serie dati, applicare stili al grafico o esportare il grafico come immagine. Ognuna di queste attività segue lo stesso schema: recuperare l'istanza `Chart`, regolare le sue proprietà e **salvare il documento aggiornato**.

Buona programmazione, e sentiti libero di sperimentare con altre impostazioni del grafico per adattarle alle tue esigenze di reporting!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Set Default Options For Data Labels In A Chart](/words/english/net/programming-with-charts/default-options-for-data-labels/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}