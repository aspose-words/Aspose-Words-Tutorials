---
category: general
date: 2026-07-20
description: come inserire un grafico a torta in Word con Aspose.Words. Impara ad
  aggiungere la percentuale dell'etichetta dei dati e a visualizzare le percentuali
  sul grafico per documenti professionali.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert pie chart
- add data label percent
- display percentages on chart
- add pie chart to word
- show percent on pie chart
language: it
lastmod: 2026-07-20
og_description: come inserire un grafico a torta in Word usando Aspose.Words. Questa
  guida mostra come aggiungere la percentuale dell’etichetta dei dati e visualizzare
  le percentuali sul grafico in poche righe.
og_image_alt: Screenshot showing how to insert pie chart in Word with percentage labels
og_title: come inserire un grafico a torta in Word – guida rapida
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: how to insert pie chart in Word with Aspose.Words. Learn to add data
    label percent and display percentages on chart for professional documents.
  headline: how to insert pie chart in Word – add data label percent
  type: TechArticle
tags:
- Aspose.Words
- Java
- Chart
- Word Automation
title: come inserire un grafico a torta in Word – aggiungere la percentuale dell’etichetta
  dati
url: /it/java/using-document-elements/how-to-insert-pie-chart-in-word-add-data-label-percent/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# come inserire un grafico a torta in Word – aggiungere la percentuale dell’etichetta dati

Ti sei mai chiesto **come inserire un grafico a torta** in un documento Word senza impazzire con l’interfaccia? Non sei solo. In molti scenari di reporting è necessario *aggiungere un grafico a torta a Word* e, cosa più importante, **mostrare la percentuale sul grafico a torta** affinché i lettori comprendano immediatamente la distribuzione dei dati.

In questo tutorial percorreremo l’intero processo usando Aspose.Words per Java. Alla fine saprai esattamente come **aggiungere la percentuale dell’etichetta dati**, **visualizzare le percentuali sul grafico**, e ottenere un grafico a torta rifinito che appare corretto al primo colpo. Nessun plugin extra, nessuna modifica manuale—solo codice pulito da inserire in qualsiasi progetto.

---

## Prerequisiti

- Java 17 (o successiva) – la versione LTS corrente supportata da Aspose.Words.  
- Aspose.Words per Java 24.x (l’ultima al momento della scrittura, luglio 2026).  
- Un setup Maven o Gradle di base per importare la libreria.  
- Un IDE a tua scelta (IntelliJ IDEA, Eclipse, VS Code… qualsiasi vada bene).

Se hai già tutto questo, ottimo—iniziamo.

---

## Passo 1: Configurare il progetto e importare la libreria

Per prima cosa, aggiungi la dipendenza Aspose.Words al tuo `pom.xml` (Maven) o `build.gradle` (Gradle). Questo ti darà accesso alle classi `Document`, `DocumentBuilder` e ai tipi di grafico.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:24.9'
```

> **Pro tip:** Mantieni il numero di versione aggiornato; le versioni più recenti spesso includono correzioni relative ai grafici che rendono **visualizzare le percentuali sul grafico** più affidabile.

---

## Passo 2: Creare un nuovo documento Word e un builder

Il builder è il tuo coltellino svizzero per inserire contenuti. Qui creiamo un documento nuovo e vi colleghiamo un `DocumentBuilder`.

```java
import com.aspose.words.*;

public class PieChartExample {
    public static void main(String[] args) throws Exception {
        // Step 2: Initialize a blank document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Perché ci serve un builder? Astrae le strutture OpenXML a basso livello, permettendoci di concentrarci su *cosa* vogliamo—come **aggiungere un grafico a torta a Word**—invece di *come* appare l’XML.

---

## Passo 3: Inserire il grafico a torta

Ora arriva il cuore di **come inserire un grafico a torta**. Chiediamo al builder di posizionare un grafico a torta di dimensioni specifiche. Le dimensioni sono in punti (1 pt ≈ 1/72 in).

```java
        // Step 3: Insert a pie chart – width 400pt, height 300pt
        Chart pieChart = (Chart) builder.insertChart(ChartType.PIE, 400, 300);
```

A questo punto il grafico è vuoto, ma il segnaposto è già nel documento. Hai appena **aggiunto un grafico a torta a Word** programmaticamente.

---

## Passo 4: Popolare il grafico con i dati

Un grafico a torta necessita di almeno una serie di valori. Forniamogli alcuni dati di esempio che rappresentano la quota di mercato.

```java
        // Step 4: Add a data series with sample values
        ChartSeries series = pieChart.getSeries().get(0);
        series.getDataPoints().add(30); // Product A
        series.getDataPoints().add(45); // Product B
        series.getDataPoints().add(25); // Product C
```

Se ti servono più serie (torte impilate, ciambelle, ecc.) puoi chiamare `pieChart.getSeries().add()` e ripetere i passaggi. La stessa logica vale quando vuoi **visualizzare le percentuali sul grafico** per ogni fetta.

---

## Passo 5: **aggiungere la percentuale dell’etichetta dati** – mostrare le percentuali sulle fette

Questa è la parte che la maggior parte degli sviluppatori dimentica: configurare le etichette dati per mostrare le percentuali. Senza di essa, il grafico mostra solo numeri grezzi, che possono risultare ambigui.

```java
        // Step 5: Enable percentage labels on the first series
        series.getDataLabel().setShowPercent(true);
```

La chiamata `setShowPercent(true)` indica ad Aspose.Words di renderizzare l’etichetta come “30 %”, “45 %”, ecc. È esattamente così che **mostri la percentuale sul grafico a torta** senza alcun lavoro di formattazione aggiuntivo.

---

## Passo 6: Salvare il documento

Infine, scrivi il documento su disco. Puoi scegliere `.docx`, `.pdf` o anche `.html`. Per questa guida ci limiteremo al moderno formato `.docx`.

```java
        // Step 6: Save the result
        doc.save("PieChartDemo.docx");
    }
}
```

Esegui il programma, apri `PieChartDemo.docx` e vedrai un grafico a torta ben renderizzato con le etichette percentuali su ogni fetta.

---

## Output previsto

Di seguito uno screenshot del file Word generato. Nota come ogni fetta mostra la sua quota in percentuale—esattamente ciò che volevamo impostando **aggiungere la percentuale dell’etichetta dati**.

![Screenshot che mostra come inserire un pie chart in Word con etichette percentuali](/images/pie-chart-percent.png){.center width=600px alt="Screenshot che mostra come inserire un pie chart in Word con etichette percentuali"}

*Il testo alternativo include la keyword principale, soddisfacendo sia SEO che accessibilità.*

---

## Domande frequenti & gestione dei casi limite

| Domanda | Risposta |
|----------|--------|
| **Posso cambiare il font delle etichette percentuali?** | Sì. Dopo aver abilitato `setShowPercent(true)`, recupera l’oggetto `DataLabel` e modifica la sua proprietà `Font` (`dataLabel.getFont().setSize(10);`). |
| **E se avessi bisogno di un grafico a ciambella invece di una torta?** | Sostituisci `ChartType.PIE` con `ChartType.DOUGHNUT` nella chiamata `insertChart`. La stessa logica di **aggiungere la percentuale dell’etichetta dati** funziona. |
| **Le versioni più vecchie di Word (2007‑2010) mostrano correttamente le percentuali?** | Aspose.Words scrive l’XML sottostante in modo indipendente dalla versione, quindi le percentuali appaiono in qualsiasi Word che supporti i grafici (2007+). |
| **Come aggiungere un titolo al grafico?** | Usa `pieChart.getTitle().setText("Market Share");` prima di salvare. |
| **Posso inserire il grafico in un paragrafo o cella di tabella specifici?** | Assolutamente. Sposta il `DocumentBuilder` nella posizione desiderata (`builder.moveToParagraph(index, true);` o `builder.moveToCell(table, row, column, true);`) prima di chiamare `insertChart`. |

---

## Consigli e trucchi dal campo

- **Pro tip:** Se prevedi di generare molti grafici in un ciclo, riutilizza un’unica istanza di `DocumentBuilder`; riduce il consumo di memoria.  
- **Attenzione a:** Fette molto piccole (< 2 %). Aspose.Words potrebbe omettere l’etichetta per evitare ingombri; puoi forzarla con `dataLabel.setShowLabel(true);`.  
- **Nota sulle performance:** Il rendering dei grafici è intensivo per la CPU. Per generare report in massa, considera il multithreading ma assicurati che ogni thread lavori su una propria istanza di `Document`.  
- **Controllo versione:** Il metodo `setShowPercent` è stato introdotto in Aspose.Words 22.8. Se usi una versione più vecchia, aggiorna o calcola manualmente le percentuali e impostale come etichette personalizzate.

---

## Riepilogo

Abbiamo coperto **come inserire un grafico a torta** in un documento Word usando Aspose.Words, ti abbiamo mostrato come **aggiungere la percentuale dell’etichetta dati**, e dimostrato il modo più semplice per **visualizzare le percentuali sul grafico**. Con poche righe di Java puoi **aggiungere un grafico a torta a Word** e **mostrare la percentuale sul grafico a torta**, trasformando numeri grezzi in visualizzazioni immediatamente comprensibili.

---

## Cosa fare dopo?

- Sperimenta con altri tipi di grafico (`BAR`, `LINE`, `AREA`) e osserva come la stessa logica di **aggiungere la percentuale dell’etichetta dati** si applichi.  
- Combina grafici e tabelle per report più ricchi—Aspose.Words rende banale posizionare un grafico accanto a una tabella di dati.  
- Esplora l’esportazione dello stesso documento in PDF o HTML per vedere come le percentuali vengano renderizzate su diversi formati.

Sentiti libero di modificare dimensioni, colori o sorgente dati (ad esempio una query al database) e guarda i tuoi report Word prendere vita. Se incontri difficoltà, lascia un commento qui sotto—buona creazione di grafici!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che ampliano le tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci alternativi nei tuoi progetti.

- [Insert Column Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Insert Area Chart in Word Document | Aspose.Words for .NET](/words/english/net/working-with-charts/insert-area-chart/)
- [Insert a Bubble Chart in Word Using Aspose.Words for .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}