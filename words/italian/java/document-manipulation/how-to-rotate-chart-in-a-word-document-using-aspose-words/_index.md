---
category: general
date: 2026-10-10
description: Impara come ruotare un grafico in un file Word e modificare il grafico
  in Word per cambiare le dimensioni del grafico a ciambella con un esempio Java completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to rotate chart
- modify chart in word
- change doughnut chart size
- Aspose.Words chart manipulation
- Java chart API
language: it
lastmod: 2026-10-10
og_description: Come ruotare un grafico in un file Word e modificare il grafico in
  Word per cambiare le dimensioni del grafico a ciambella usando Aspose.Words per
  Java.
og_image_alt: Screenshot showing a rotated doughnut chart after applying how to rotate
  chart steps
og_title: Come ruotare un grafico in un documento Word – guida Java passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Learn how to rotate chart in a Word file and modify chart in Word to
    change doughnut chart size with a complete Java example.
  headline: How to rotate chart in a Word document using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Come ruotare un grafico in un documento Word usando Aspose.Words
url: /it/java/document-manipulation/how-to-rotate-chart-in-a-word-document-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come ruotare un grafico in un documento Word usando Aspose.Words

Se hai bisogno di **how to rotate chart** all'interno di un file Microsoft Word, questa guida ti mostra i passaggi esatti. Imparerai anche come **modify chart in Word** per **change doughnut chart size** senza uscire dal tuo codice Java.

L'automazione di Word spesso sembra una serie di chiamate API scollegate, ma con Aspose.Words puoi trattare un grafico come qualsiasi altro nodo del documento. Alla fine di questo tutorial avrai un programma eseguibile che carica un `.docx` esistente, ruota un grafico a ciambella di 45°, riduce il foro al 50 % del raggio e salva il risultato in un nuovo file.

## Prerequisiti

* Java 17 o versioni successive installato.
* Maven (o Gradle) per gestire le dipendenze.
* Un documento Word di input (`input.docx`) che contiene già un grafico a ciambella.
* Una licenza valida di Aspose.Words per Java (o usa la modalità di valutazione).

## Passo 1: Configurare il progetto Maven

Crea un nuovo progetto Maven o aggiungi la seguente dipendenza al tuo `pom.xml` esistente:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest version available -->
</dependency>
```

Eseguendo `mvn clean install` verrà scaricata la libreria e le classi saranno disponibili nel tuo classpath.

## Passo 2: Caricare il documento Word che contiene un grafico

La prima operazione è aprire il documento esistente. La classe `Document` rappresenta l'intero file.

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Il caricamento del file **non** lo modifica; crea semplicemente una rappresentazione in‑memoria che puoi interrogare e modificare.

## Passo 3: Creare un DocumentBuilder per la navigazione

`DocumentBuilder` ti fornisce un'API simile a un cursore per percorrere l'albero del documento. Lo useremo per individuare la prima forma di grafico.

```java
        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Il builder inizia all'inizio del documento, ma puoi spostarlo su qualsiasi nodo in seguito, se necessario.

## Passo 4: Recuperare la prima forma di grafico

I grafici sono memorizzati come nodi `Shape`. Filtrando i nodi figlio di tipo `NodeType.SHAPE` possiamo estrarre l'oggetto grafico.

```java
        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();
```

Se il documento contiene più grafici, puoi iterare su `getChildNodes` e controllare ogni `Shape` con `hasChart()` prima di eseguire il cast.

## Passo 5: Ruotare il grafico (how to rotate chart)

Un grafico a ciambella è essenzialmente un grafico a torta con un foro. Ruotarlo cambia l'angolo di partenza della prima fetta.

```java
        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);
```

Il metodo `setStartAngle` si aspetta un double che rappresenta i gradi. I valori positivi ruotano in senso orario, mentre i valori negativi ruotano in senso antiorario.

## Passo 6: Modificare la dimensione del foro della ciambella (change doughnut chart size)

La dimensione del foro è espressa come frazione del raggio del grafico. Un valore di `0.5` significa che il foro occupa il 50 % del raggio totale.

```java
        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);
```

**Suggerimento:** L'intervallo valido è `0.0` (nessun foro, cioè una torta normale) fino a `0.9` (anello molto sottile). Valori al di fuori di questo intervallo genereranno un `IllegalArgumentException`.

## Passo 7: Salvare il documento modificato

Infine, scrivi le modifiche su disco.

```java
        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");
    }
}
```

Quando apri `DoughnutFormatted.docx` in Microsoft Word, vedrai il grafico a ciambella ruotato di 45° e il foro ridotto a metà della sua dimensione originale.

## Esempio completo e eseguibile

Mettendo insieme tutti i pezzi, ecco il programma completo che puoi copiare‑incollare nel tuo IDE:

```java
import com.aspose.words.*;

public class RotateDoughnutChart {
    public static void main(String[] args) throws Exception {
        // Load a document that already contains a chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Create a DocumentBuilder for the loaded document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Retrieve the first chart shape from the document
        Shape chartShape = (Shape) builder.getCurrentParagraph()
                .getChildNodes(NodeType.SHAPE, true)
                .get(0);

        // Ensure the shape actually contains a chart
        if (!chartShape.hasChart()) {
            System.out.println("No chart found in the first shape.");
            return;
        }

        // Cast the shape's renderer to a Chart object
        Chart chart = chartShape.getChart();

        // Rotate the chart by setting its start angle to 45 degrees
        chart.setStartAngle(45.0);

        // Adjust the doughnut hole size to 50 %
        chart.setDoughnutHoleSize(0.5);

        // Save the modified document
        doc.save("YOUR_DIRECTORY/DoughnutFormatted.docx");

        System.out.println("Chart rotated and doughnut size changed successfully.");
    }
}
```

### Output previsto

Eseguendo il programma stampa:

```
Chart rotated and doughnut size changed successfully.
```

Aprendo `DoughnutFormatted.docx` si vede un grafico a ciambella la cui prima fetta inizia alla posizione di 45° e il cui raggio interno occupa metà del raggio esterno.

## Varianti comuni e casi limite

| Situazione | Cosa regolare | Perché è importante |
|-----------|----------------|----------------|
| **Multiple charts** | Itera su `getChildNodes(NodeType.SHAPE, true)` e controlla `shape.hasChart()` per ciascuno | Garantisce di modificare il grafico desiderato anziché il primo |
| **Bar or line chart** | `setStartAngle` non si applica; usa `chart.getSeries().get(0).setFillFormat(...)` per altre modifiche visive | Non tutti i tipi di grafico supportano la rotazione; solo i grafici a ciambella/torta hanno un angolo di partenza |
| **Chart without a doughnut hole** | Salta `setDoughnutHoleSize` o prima converti il tipo di grafico in ciambella tramite `chart.setChartType(ChartType.DONUT)` | Modificare la dimensione del foro su un grafico non a ciambella genera un'eccezione |
| **Large documents** | Usa `DocumentBuilder.moveToDocumentStart()` e `builder.moveToNode(chartShape)` per una navigazione mirata | Migliora le prestazioni evitando il percorso completo di nodi non correlati |

## Consigli professionali per una manipolazione affidabile dei grafici

* **Cache the chart reference** – Se prevedi di modificare diverse proprietà, mantieni una variabile locale `Chart` invece di chiamare ripetutamente `chartShape.getChart()`.
* **Validate input values** – Prima di chiamare `setStartAngle` o `setDoughnutHoleSize`, verifica l'intervallo per evitare errori a runtime.
* **Use a license** – La modalità di valutazione inserisce una filigrana nella prima pagina. Applicare una licenza (`License license = new License(); license.setLicense("Aspose.Words.lic");`) la rimuove.

## Prossimi passi

Ora che conosci **how to rotate chart** e **change doughnut chart size**, puoi esplorare altri scenari **modify chart in Word**:

* Cambia i colori delle fette con `chart.getSeries().get(0).getDataPoints().get(i).getFillFormat().setForeColor(Color.getRed())`.
* Aggiungi etichette dati chiamando `chart.getSeries().get(0).setHasDataLabel(true)`.
* Esporta il grafico come immagine usando `chart.toImage(300, 300, ImageType.PNG)`.

Ciascuna di queste estensioni segue lo stesso schema: ottieni l'oggetto `Chart`, chiama il setter appropriato e salva il documento.

---

**Hai appena imparato a ruotare e ridimensionare i grafici a ciambella in Word usando Java.** Sentiti libero di adattare il codice ad altri tipi di grafico, integrarlo in una pipeline più ampia di generazione di documenti, o combinarlo con Aspose.Slides per l'automazione di PowerPoint. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Nascondere l'asse del grafico in un documento Word](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Inserire un grafico a bolle in un documento Word](/words/english/net/programming-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}