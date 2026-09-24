---
category: general
date: 2026-09-24
description: Scopri come creare un grafico in Word usando Java, inserire un grafico
  radiale e salvare il documento come docx con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create chart in word
- save document as docx
- add chart to word
- create word document java
- insert radial chart
language: it
lastmod: 2026-09-24
og_description: Crea un grafico in Word con Java e Aspose.Words. Questo tutorial ti
  mostra come aggiungere un grafico radiale, personalizzare i dati e salvare il documento
  come docx.
og_image_alt: Radial chart inserted in a Word document using Java code
og_title: Crea un grafico in Word con Java – guida passo‑passo
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  headline: How to create chart in Word with Java and Aspose.Words
  type: TechArticle
- description: Learn how to create chart in Word using Java, insert a radial chart,
    and save document as docx with Aspose.Words.
  name: How to create chart in Word with Java and Aspose.Words
  steps:
  - name: You should see a single page with a centered radial chart.
    text: You should see a single page with a centered radial chart.
  - name: If you added series data, the chart displays four slices labeled Q1‑Q4.
    text: If you added series data, the chart displays four slices labeled Q1‑Q4.
  - name: Right‑click the chart → **Edit Data** to confirm the underlying data table.
    text: Right‑click the chart → **Edit Data** to confirm the underlying data table.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Chart
- DOCX
title: Come creare un grafico in Word con Java e Aspose.Words
url: /it/java/using-document-elements/how-to-create-chart-in-word-with-java-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un grafico in Word con Java e Aspose.Words

Se hai bisogno di **creare un grafico in Word** da un'applicazione Java, questa guida ti accompagna attraverso l'intero processo. Vedrai come aggiungere un grafico radiale, opzionalmente popolare le sue serie e infine **salvare il documento come docx** usando la libreria Aspose.Words per Java.

Generare dati visivi all'interno di un file Word è una necessità comune per report, fatturazione o generazione automatica di documenti. Alla fine di questo tutorial sarai in grado di creare progetti **create word document java** che **add chart to Word** file senza alcuna modifica manuale.

## Prerequisiti

* Java Development Kit (JDK) 8 o più recente.
* Maven o Gradle per la gestione delle dipendenze.
* Un IDE come IntelliJ IDEA, Eclipse o VS Code.
* Una licenza valida di Aspose.Words per Java (la versione di prova gratuita funziona per lo sviluppo).

Questi strumenti forniscono la base per gli esempi di codice che seguono.

## Passo 1: Configurare il progetto Maven

Crea un nuovo progetto Maven (o aggiorna uno esistente) e aggiungi la dipendenza Aspose.Words al tuo `pom.xml`:

```xml
<project>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>word‑chart‑demo</artifactId>
    <version>1.0.0</version>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- use the latest stable version -->
        </dependency>
    </dependencies>
</project>
```

Eseguendo `mvn clean install` si scarica la libreria e rende disponibili le classi come `Document`, `DocumentBuilder` e `ChartType` nel classpath.

> **Suggerimento:** Mantieni la versione della libreria aggiornata. Le nuove versioni aggiungono tipi di grafico e migliorano le prestazioni di rendering.

## Passo 2: Creare un nuovo documento Word

Il primo passo programmatico per **create chart in Word** è istanziare un `Document` vuoto. Questo oggetto rappresenta l'intero pacchetto `.docx`.

```java
import com.aspose.words.*;

public class RadialChartDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a blank Word document
        Document doc = new Document();

        // Step 2.2: Obtain a DocumentBuilder to insert content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funziona come un cursore; conosce il punto di inserimento corrente e fornisce metodi per testo, tabelle e grafici. A questo punto hai **created word document java** style – una tela pulita pronta per i contenuti.

## Passo 3: Inserire un grafico radiale

Aspose.Words supporta molti tipi di grafico. Per **insert radial chart**, chiama `insertChart` con `ChartType.RADIAL`. Il metodo richiede anche larghezza e altezza in punti (1 point ≈ 1/72 inch).

```java
        // Step 3: Insert a radial chart (400 × 300 points)
        Shape chart = builder.insertChart(ChartType.RADIAL, 400, 300);
```

L'oggetto `Shape` restituito contiene l'oggetto grafico sottostante. Il grafico rende automaticamente le graduazioni per un layout di 24,9°, che è il valore predefinito per i grafici radiali in Word.

### Perché usare un grafico radiale?

Un grafico radiale visualizza dati che avvolgono un cerchio, rendendolo ideale per mostrare pattern ciclici (ad esempio vendite mensili, metriche a quadrante). La stessa API può inserire grafici a barre, a torta o a linee, ma il tipo radiale aggiunge un aspetto distintivo senza codice di styling aggiuntivo.

## Passo 4: (Opzionale) Popolare i dati delle serie del grafico

Se vuoi che il grafico mostri valori reali, devi aggiungere serie e punti. Il frammento seguente aggiunge una singola serie con tre punti dati:

```java
        // Optional: add data to the chart
        Chart chartObj = chart.getChart();
        chartObj.getSeries().clear(); // remove any default series

        // Create a new series
        ChartSeries series = chartObj.getSeries().add("Quarterly Revenue");

        // Add data points (value, category)
        series.getDataPoints().add(15000, "Q1");
        series.getDataPoints().add(21000, "Q2");
        series.getDataPoints().add(18000, "Q3");
        series.getDataPoints().add(24000, "Q4");
```

Puoi ripetere le chiamate `add` per tutti i punti necessari. Aspose.Words aggiorna automaticamente la rappresentazione visiva, così vedi le fette radiali adattarsi ai nuovi valori.

> **Domanda comune:** *E se devo collegare i dati da un database?*  
> Recupera le righe, itera su di esse e chiama `series.getDataPoints().add(value, label)` all'interno del ciclo. L'API è thread‑safe e funziona con qualsiasi `ResultSet` tu fornisca.

## Passo 5: Salvare il documento come DOCX

Quando il grafico è pronto, l'ultimo passo è **save document as docx**. Il metodo `save` determina il formato di output dall'estensione del file.

```java
        // Step 5: Persist the document
        String outputPath = "output/RadialChartDemo.docx";
        doc.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Il file generato contiene un grafico radiale completamente funzionale che può essere aperto in Microsoft Word, LibreOffice o qualsiasi visualizzatore che supporti il formato DOCX. Poiché abbiamo usato l'estensione `.docx`, Word salva il file nel formato Open XML, che è lo standard moderno per i documenti Word.

### Verifica del risultato

Apri `RadialChartDemo.docx` in Word:

1. Dovresti vedere una singola pagina con un grafico radiale centrato.
2. Se hai aggiunto dati di serie, il grafico mostra quattro fette etichettate Q1‑Q4.
3. Fai clic destro sul grafico → **Edit Data** per confermare la tabella dati sottostante.

Se il grafico appare vuoto, verifica di aver chiamato `chart.getChart()` prima di aggiungere le serie e assicurati che il cursore del document builder sia posizionato dove desideri il grafico.

## Passo 6: Suggerimenti avanzati per lavorare con i grafici

| Suggerimento | Perché è importante |
|-----|----------------|
| **Imposta lo stile del grafico** – `chart.getChart().setStyle(ChartStyle.STYLE_PRESET_5);` | Migliora la coerenza visiva senza formattare manualmente ogni elemento. |
| **Ridimensiona dopo l'inserimento** – `chart.setWidth(500); chart.setHeight(350);` | Ti consente di regolare finemente le dimensioni del grafico in base al layout della pagina. |
| **Aggiungi un titolo** – `chart.getChart().getTitle().setText("Revenue Overview");` | Fornisce contesto ai lettori che visualizzano il documento senza il testo circostante. |
| **Esporta in PDF** – `doc.save("RadialChartDemo.pdf");` | Utile quando hai bisogno di una versione non modificabile per la distribuzione. |
| **Gestione della licenza** – `License lic = new License(); lic.setLicense("Aspose.Words.lic");` | Previene il watermark di valutazione nelle build di produzione. |

Questi miglioramenti sono opzionali ma dimostrano come puoi personalizzare ulteriormente il grafico dopo aver imparato a **add chart to Word**.

## Conclusione

Ora hai un esempio completo e autonomo che mostra come **create chart in Word** usando Java, **insert radial chart**, opzionalmente riempirlo con dati, e **save document as docx**. Lo stesso schema funziona per altri tipi di grafico, così puoi estendere questo tutorial a grafici a barre, a linee o a torta secondo necessità.

Next you might explore:

* Progetti **create word document java** che combinano tabelle, immagini e più grafici.
* Usare **save document as docx** insieme a **save document as pdf** per report multi‑formato.
* Aggiungere dati dinamici da REST API o database ai tuoi grafici.

Sentiti libero di sperimentare con le opzioni di stile, le dimensioni del grafico e le fonti di dati. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to create column chart using Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}