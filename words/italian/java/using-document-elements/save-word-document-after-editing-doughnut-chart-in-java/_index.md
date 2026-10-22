---
category: general
date: 2026-09-11
description: Salva il documento Word dopo aver modificato un grafico a ciambella con
  Aspose.Words per Java. Scopri come cambiare la dimensione del foro della ciambella,
  ruotare il grafico a ciambella e modificare le proprietà del grafico a ciambella.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save word document
- rotate doughnut chart
- edit doughnut chart
- change doughnut hole
- change chart hole size
language: it
lastmod: 2026-09-11
og_description: Salva il documento Word dopo aver modificato un grafico a ciambella
  usando Aspose.Words per Java. Questo tutorial mostra come cambiare la dimensione
  del foro della ciambella, ruotare il grafico a ciambella e personalizzare l'aspetto
  del grafico.
og_image_alt: Java code editing a doughnut chart before saving Word document
og_title: Salva documento Word dopo aver modificato il grafico a ciambella – Guida
  Java
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Save Word document after editing a doughnut chart with Aspose.Words
    for Java. Learn how to change doughnut hole size, rotate doughnut chart, and edit
    doughnut chart properties.
  headline: Save Word document after editing doughnut chart in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word
- Chart
- Doughnut
title: Salva documento Word dopo aver modificato il grafico a ciambella in Java
url: /it/java/using-document-elements/save-word-document-after-editing-doughnut-chart-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salva documento Word dopo aver modificato il grafico a ciambella in Java

Se hai bisogno di **salvare documento Word** che contiene un grafico a ciambella personalizzato, questa guida ti mostra esattamente come fare. In poche righe di Java puoi modificare il foro della ciambella, ruotare il grafico a ciambella e poi scrivere il risultato su disco.

Vedrai un esempio completo e eseguibile che utilizza Aspose.Words per Java, più suggerimenti per gestire più grafici, verificare i tipi di nodo e evitare errori comuni. Non sono necessari riferimenti esterni—tutto ciò di cui hai bisogno è incluso.

## Prerequisites

Prima di iniziare, assicurati di avere:

- Java 17 o versioni successive installate
- Maven o Gradle per gestire le dipendenze
- Aspose.Words per Java (versione 23.9 o successiva) aggiunto al tuo progetto  
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.9</version>
  </dependency>
  ```
- Un file Word (`input.docx`) che contiene un singolo grafico a ciambella

## Step 1: Load the Word document

Passo 1: Carica il documento Word

Il primo passo è aprire il file di origine. Questo passo è essenziale perché ogni operazione successiva lavora sull'oggetto `Document` in memoria.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // Load the Word document that contains a doughnut chart
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Perché?** Caricare il documento crea una rappresentazione DOM che ti permette di attraversare forme, tabelle e grafici. Se il file non può essere aperto, Aspose.Words lancia un'eccezione, così sai immediatamente che il percorso è errato.

## Step 2: Locate the doughnut chart shape

Passo 2: Individua la forma del grafico a ciambella

Un grafico è memorizzato all'interno di un nodo `Shape`. Recuperiamo la prima forma che contiene un grafico e convertiamo il suo renderer in `Chart`.

```java
        // Find the first shape that contains a chart
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        // Ensure the shape actually holds a chart
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        // Get the Chart object for further manipulation
        Chart chart = chartShape.getChart();
```

> **Perché?** Verificare `isChart()` previene un `ClassCastException` quando il documento contiene immagini o altre forme prima del grafico. Questo rende il codice robusto per documenti con contenuti misti.

## Step 3: Change doughnut hole size  

Passo 3: Modifica la dimensione del foro della ciambella  

Ora modifichiamo il foro della ciambella. Il metodo `setHoleSize` si aspetta una percentuale del raggio del grafico (10 – 90).

```java
        // Adjust the size of the doughnut hole (percentage of the chart radius)
        chart.setHoleSize(30);   // The hole occupies 30 % of the radius
```

> **Perché?** Modificare il foro della ciambella (`change doughnut hole` / `change chart hole size`) ti consente di enfatizzare o de‑enfatizzare l'area centrale. Valori al di fuori del 10‑90 % vengono ignorati dall'API.

## Step 4: Rotate the doughnut chart  

Passo 4: Ruota il grafico a ciambella  

Per controllare dove inizia la prima fetta, imposta l'angolo della prima fetta. Questo ruota effettivamente il **grafico a ciambella**.

```java
        // Rotate the chart so that the first slice starts at a custom angle
        chart.setFirstSliceAngle(45);   // Starts the first slice at 45 degrees
```

> **Perché?** Ruotare il grafico è utile quando vuoi che una specifica fetta appaia in alto o per corrispondere a una specifica di design.

## Step 5: Save the updated document  

Passo 5: Salva il documento aggiornato  

Infine, scrivi le modifiche in un nuovo file. Questo è il momento in cui **salvi documento Word** con il grafico modificato.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Risultato atteso:** `output.docx` contiene il contenuto originale, ma il grafico a ciambella ora ha un foro del 30 % e la sua prima fetta inizia a 45 °. Aprire il file in Microsoft Word mostrerà il grafico trasformato.

## Full working example

Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare‑incollare nel tuo IDE. Include tutti gli import e la gestione degli errori necessari per **modificare il grafico a ciambella** e **salvare documento Word** in modo sicuro.

```java
import com.aspose.words.*;

public class DoughnutChartEditor {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Locate the first chart shape
        Shape chartShape = (Shape) doc.getChildNodes(NodeType.SHAPE, true).get(0);
        if (!chartShape.isChart()) {
            throw new IllegalStateException("The first shape is not a chart.");
        }
        Chart chart = chartShape.getChart();

        // 3. Change the doughnut hole size
        chart.setHoleSize(30); // 30 % hole

        // 4. Rotate the doughnut chart
        chart.setFirstSliceAngle(45); // start at 45°

        // 5. Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Expected output

Output atteso

When you open `output.docx`:

- Il foro centrale del grafico a ciambella occupa circa un terzo del raggio del grafico.  
- La prima fetta inizia alla posizione di 45 gradi, spostando l'intero grafico in senso orario.  

Entrambi i cambiamenti visivi sono riflessi immediatamente in Word.

## Common variations and edge cases

Varianti comuni e casi limite

| Situazione | Come gestirlo |
|-----------|----------------|
| **Grafici multipli** | Itera su `doc.getChildNodes(NodeType.SHAPE, true)` e filtra `shape.isChart()`; applica `setHoleSize` / `setFirstSliceAngle` a ciascun `Chart`. |
| **Il grafico non è una ciambella** | Verifica `chart.getType()`; chiama `setHoleSize` solo quando `chart.getType() == ChartType.DOUGHNUT`. |
| **È necessario modificare dinamicamente la dimensione del foro** | Calcola la percentuale desiderata in base ai valori dei dati, poi chiama `setHoleSize(computedValue)`. |
| **Salvataggio su stream** | Usa |

## What Should You Learn Next?

Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un grafico a colonne usando Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-charts/)
- [Come salvare un documento come PDF con Aspose.Words per Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Salva Word con password usando Aspose.Words per Java](/words/english/java/document-loading-and-saving/advance-saving-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}