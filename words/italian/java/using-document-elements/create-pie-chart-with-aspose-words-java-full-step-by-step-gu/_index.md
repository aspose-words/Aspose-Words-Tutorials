---
category: general
date: 2026-07-16
description: Crea un grafico a torta in Java usando Aspose.Words. Scopri come aggiungere
  linee di collegamento, mostrare la legenda del grafico ed esplodere una fetta in
  un unico tutorial.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create pie chart
- add leader lines
- show chart legend
- how to explode slice
- how to add legend
language: it
lastmod: 2026-07-16
og_description: Crea un grafico a torta in Java usando Aspose.Words. Questa guida
  mostra come aggiungere linee guida, visualizzare la legenda del grafico e separare
  una fetta, offrendoti un risultato visivo curato in pochi minuti.
og_image_alt: Screenshot of a Java‑generated pie chart with an exploded slice and
  visible legend
og_title: Crea un grafico a torta con Aspose.Words Java – Tutorial completo di formattazione
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  headline: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  type: TechArticle
- description: Create pie chart in Java using Aspose.Words. Learn how to add leader
    lines, show chart legend, and explode a slice in a single tutorial.
  name: Create Pie Chart with Aspose.Words Java – Full Step‑by‑Step Guide
  steps:
  - name: Java 17 (or later) installed.
    text: Java 17 (or later) installed.
  - name: Aspose.Words for Java JAR on your classpath.
    text: Aspose.Words for Java JAR on your classpath.
  - name: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
    text: A basic IDE or text editor—IntelliJ IDEA, Eclipse, VS Code, whatever you
      prefer.
  type: HowTo
tags:
- Aspose.Words
- Java
- Chart Formatting
- Data Visualization
title: Crea un grafico a torta con Aspose.Words Java – Guida completa passo passo
url: /it/java/using-document-elements/create-pie-chart-with-aspose-words-java-full-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un grafico a torta con Aspose.Words Java – Guida completa passo‑passo

Ti sei mai chiesto come **creare un grafico a torta** programmaticamente in Java senza lottare con API di disegno a basso livello? Non sei l'unico. Molti sviluppatori hanno bisogno di una visualizzazione rapida per report, dashboard o documenti automatizzati, e ricorrono ad Aspose.Words perché gestisce il lavoro pesante.  

In questo tutorial percorreremo un esempio completo, pronto all'uso, che non solo **crea un grafico a torta** ma ti mostra anche come **aggiungere leader lines**, **mostrare la legenda del grafico** e persino **esplodere una fetta** per enfatizzare. Alla fine avrai un file `.docx` dall'aspetto così curato da impressionare un cliente.

> **Quick win:** Lo snippet di codice qui sotto funziona subito con Aspose.Words for Java 23.9 (o qualsiasi versione più recente). Nessuna dipendenza aggiuntiva, solo il JAR.

## Cosa imparerai

- Impostare un documento Word vuoto con `DocumentBuilder`.
- Inserire un **grafico a torta** di dimensioni personalizzate.
- Utilizzare la funzione **explode slice** per evidenziare un punto dati.
- Abilitare le **leader lines** affinché la fetta esplosa rimanga collegata all'etichetta.
- Attivare la **legenda del grafico** così i lettori possono identificare immediatamente ogni fetta.
- Salvare il risultato in un file `.docx` che puoi aprire con Microsoft Word o LibreOffice.

**Prerequisiti** – Avrai bisogno di:

1. Java 17 (o successiva) installato.
2. JAR di Aspose.Words per Java nel tuo classpath.
3. Un IDE o editor di testo di base—IntelliJ IDEA, Eclipse, VS Code, o quello che preferisci.

Ora, immergiamoci.

## Passo 1: Inizializzare il Documento e il Builder – Prepararsi a **creare un grafico a torta**

Per prima cosa, ci serve una tela pulita. `Document` rappresenta l'intero file Word, mentre `DocumentBuilder` è l'assistente che ci permette di aggiungere contenuti.

```java
import com.aspose.words.*;

public class PieChartFormattingDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a DocumentBuilder to work with it
        Document doc = new Document();               // the container for our Word file
        DocumentBuilder builder = new DocumentBuilder(doc); // convenient API for adding elements
```

> **Why this matters:** Iniziare con un `Document` nuovo garantisce l'assenza di stili nascosti o oggetti residui che potrebbero interferire con il rendering del grafico.

## Passo 2: Inserire il **grafico a torta** – Le dimensioni contano

Aspose.Words rende l'inserimento del grafico una singola riga di codice. Qui richiediamo un grafico a torta di 400 × 300 punti—circa 5,5 × 4,2 pollici su uno schermo tipico.

```java
        // Step 2: Insert a pie chart of size 400x300 points
        Shape chartShape = builder.insertChart(ChartType.PIE, 400, 300);
        Chart chart = chartShape.getChart(); // the underlying chart object we will format
```

> **Pro tip:** Se ti serve una dimensione diversa, basta modificare i due argomenti numerici. L'API lavora in punti, dove 72 punti = 1 pollice.

## Passo 3: **Come esplodere una fetta** – Evidenziare un punto dati chiave

Esplodere una fetta la estrae dal resto della torta, attirando l'occhio del lettore. Il metodo `setExplosion` accetta un intero che rappresenta la distanza in punti.

```java
        // Step 3: Explode the first slice to emphasize it
        chart.getSeries().get(0).setExplosion(10); // 10 points outward
```

> **What if you have multiple series?** Puoi chiamare `setExplosion` su qualsiasi indice di serie (`get(1)`, `get(2)`, …) per esplodere fette diverse.

## Passo 4: **Aggiungere leader lines** e **mostrare la legenda del grafico** – Collegare i punti

Quando una fetta è esplosa, l'etichetta può allontanarsi. Le leader lines mantengono l'etichetta ancorata, preservando la leggibilità. Allo stesso tempo, una legenda offre una chiave rapida per tutte le fette.

```java
        // Step 4: Enable leader lines for the exploded slice and show the legend
        chart.getSeries().get(0).setLeaderLines(true); // draws a line from slice to its label
        chart.setShowLegend(true);                     // makes the legend visible below the chart
```

> **Why enable leader lines?** Senza di esse, l'etichetta potrebbe apparire sospesa, confondendo gli utenti su a quale fetta appartiene.  
> **Need a custom legend position?** Usa `chart.getLegend().setPosition(LegendPosition.TOP)` o qualsiasi altro valore enum.

## Passo 5: Salvare il Documento – L'ultimo passo per **creare un grafico a torta**

Infine, persisti il documento su disco. Regola il percorso verso una cartella in cui hai permessi di scrittura.

```java
        // Step 5: Save the document with the formatted pie chart
        doc.save("YOUR_DIRECTORY/PieChartDemo.docx");
    }
}
```

Esegui il programma, apri il file generato `PieChartDemo.docx` e dovresti vedere un grafico a torta ben formattato con la prima fetta esplosa, le leader lines e una legenda visibile.

![Esempio di grafico a torta che mostra una fetta esplosa e la legenda](pie-chart-example.png){: .center-image alt="Esempio di creazione di grafico a torta con fetta esplosa, linee guida e legenda"}

### Output previsto

Quando apri il file Word, il grafico appare più o meno così:

- Un grafico a torta di 400 × 300 pt.
- La prima fetta è spostata di 10 pt.
- Una sottile leader line collega la fetta esplosa alla sua etichetta.
- Una legenda sotto il grafico elenca il nome di ogni serie.

Se non vedi la leader line, verifica che `setLeaderLines(true)` sia chiamato *dopo* l'impostazione dell'esplosione—l'ordine è importante.

## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **No legend appears** | `setShowLegend(true)` è stato omesso o chiamato sull'oggetto grafico sbagliato. | Assicurati di chiamare `chart.setShowLegend(true)` **dopo** aver recuperato il `Chart` dalla forma. |
| **Leader line missing** | La fetta non è stata esplosa, o il tipo di grafico non supporta le leader lines. | Solo `ChartType.PIE` (o `PIE_3D`) supporta le leader lines. Chiama prima `setExplosion`, poi `setLeaderLines(true)`. |
| **Slice doesn’t move** | Valore di esplosione troppo basso (0‑2 pt). | Aumenta l'intero, ad esempio `setExplosion(10)` o un valore più alto per un effetto più marcato. |
| **Chart looks distorted** | Usare una dimensione non quadrata (larghezza ≠ altezza) può schiacciare la torta. | Mantieni larghezza e altezza uguali o quasi; 400 × 300 funziona ma 400 × 400 dà un cerchio perfetto. |

## Modifiche avanzate (Opzionale)

Se vuoi andare oltre le basi, considera:

- **Custom colors**: `chart.getSeries().get(0).getDataPoints().get(i).getFormat().getFill().setForeColor(Color.RED);`
- **Data labels**: `chart.getSeries().get(0).setDataLabelType(ChartDataLabelType.CATEGORY);`
- **3‑D effect**: Sostituisci `ChartType.PIE` con `ChartType.PIE_3D`.

Queste opzioni ti permettono di affinare l'aspetto per allinearlo alle linee guida del brand aziendale.

## Riepilogo – Cosa abbiamo realizzato

Abbiamo iniziato con un documento Word vuoto, **creato un grafico a torta**, **esploso la prima fetta**, **aggiunto le leader lines** e **mostrato la legenda del grafico**. L'intero flusso è contenuto in un conciso metodo `main`, rendendolo facile da integrare in pipeline di reporting più ampie.

## Prossimi passi

- **Add more series**: Popolare il grafico con dati reali da un database o CSV.  
- **Export to PDF**: Usa `doc.save("output.pdf", SaveFormat.PDF);` per generare una versione PDF.  
- **Combine with other shapes**: Inserire tabelle, immagini o grafici aggiuntivi per un report completo.

Se sei curioso di altri tipi di grafico—colonna, barra, linea—basta sostituire `ChartType.PIE` con l'enum appropriato e seguire gli stessi passaggi di formattazione.

*Happy charting!* Sentiti libero di lasciare un commento se qualcosa non ha funzionato come previsto, o condividi come hai personalizzato la posizione della legenda. Il tuo feedback aiuta tutti noi a costruire documenti automatizzati migliori.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Come creare documenti PDF con Aspose.Words per Java | Document Processing API](/words/english/java/)
- [Come aggiungere filigrana ai documenti usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-watermarks-to-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}