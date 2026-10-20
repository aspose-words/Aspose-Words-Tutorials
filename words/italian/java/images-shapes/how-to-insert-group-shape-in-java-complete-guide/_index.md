---
category: general
date: 2026-07-16
description: come inserire una forma di gruppo in Java usando Aspose.Words – aggiungere
  una forma rettangolare, impostare le dimensioni della forma e creare un rettangolo
  e un cerchio colorati.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: it
lastmod: 2026-07-16
og_description: 'come inserire un gruppo di forme in Java: una guida pratica per aggiungere
  una forma rettangolare, impostare le dimensioni della forma e creare rettangolo
  e cerchio colorati con Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Inserisci forma di gruppo in Java – tutorial completo di Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: come inserire una forma di gruppo in Java – Guida completa
url: /it/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# come inserire una forma di gruppo in Java – Guida completa

Ti sei mai chiesto **come inserire una forma di gruppo** in un documento Word usando Java? Non sei l'unico. Che tu stia creando un generatore di report o un creatore di volantini dinamici, raggruppare le forme mantiene il layout ordinato e il tuo codice gestibile.

In questo tutorial percorreremo passo passo le operazioni per **aggiungere una forma rettangolare**, **impostare le dimensioni della forma**, e **creare un rettangolo colorato** e **creare un cerchio colorato** usando la libreria Aspose.Words. Alla fine avrai un programma eseguibile che produce un file .docx con un rettangolo blu e un cerchio rosso ordinatamente racchiusi in un gruppo.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- Java 17 (o qualsiasi JDK recente) installato e configurato.
- Maven o Gradle per gestire le dipendenze.
- Aspose.Words for Java 23.9 o più recente – puoi scaricarlo da Maven Central.
- Una conoscenza di base della sintassi Java – nulla di complicato è richiesto.

Se ti manca qualcuno di questi, scarica il JDK dal sito di Oracle e aggiungi la dipendenza Aspose.Words al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Ora che le basi sono pronte, mettiamoci al lavoro.

## come inserire una forma di gruppo – Panoramica

L'idea principale è semplice: creare un `Document`, aprire un `DocumentBuilder`, inserire una **forma di gruppo**, quindi inserire le singole forme (un rettangolo e un cerchio) all'interno di quel gruppo. Il gruppo funge da contenitore, quindi spostarlo in seguito sposterà tutto ciò che contiene – ideale per layout complessi.

Di seguito il codice completo, pronto per l'esecuzione. Sentiti libero di copiarlo e incollarlo in una nuova classe Java chiamata `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Suggerimento:** I valori di `setLeft` e `setTop` sono relativi all'origine del gruppo, non alla pagina. Questo rende il riposizionamento dell'intero gruppo un gioco da ragazzi in seguito.

### Cosa è appena successo?

1. **Document & Builder** – Creiamo un file Word vuoto e un `DocumentBuilder` che ci permette di inserire contenuti.
2. **Group Shape** – `builder.insertGroupShape()` crea un contenitore. Pensalo come una cartella per gli oggetti di disegno.
3. **Blue Rectangle** – Istanziano una `Shape` di tipo `RECTANGLE`, ne impostiamo le dimensioni, la posizione e la riempiamo di blu – questo è il passaggio **create colored rectangle**.
4. **Red Circle** – Stesso schema, ma usando `ELLIPSE` per un cerchio perfetto, poi lo riempiamo di rosso – questo è il passaggio **create colored circle**.
5. **Saving** – Infine salviamo tutto in `GroupShapeDemo.docx`.

Esegui il programma (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) e apri il file risultante. Dovresti vedere un rettangolo blu a sinistra e un cerchio rosso a destra, entrambi bloccati all'interno di un unico riquadro di gruppo.

## Aggiungere una forma rettangolare

Se ti serve solo un rettangolo senza raggruppamento, puoi saltare la chiamata a `insertGroupShape()` e aggiungere il rettangolo direttamente al corpo del documento. Tuttavia, il raggruppamento ti offre la flessibilità di spostare, ruotare o eliminare più forme in un unico passaggio.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Nota come abbiamo usato la logica **add rectangle shape** qui. Il rettangolo appare nella pagina come un oggetto indipendente. Nella maggior parte degli scenari reali vorrai comunque il gruppo, perché preserva il posizionamento relativo.

## Impostare le dimensioni della forma

Quando vedi metodi come `setWidth` e `setHeight`, ricorda che accettano **punti** (1/72 pollice). Se preferisci i millimetri, converti prima:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Questo frammento dimostra **set shape dimensions** con una conversione di unità – utile quando le specifiche di design provengono da un mockup UI che utilizza unità metriche.

## Creare un rettangolo colorato

Colorare una forma è semplice come chiamare `getFill().setForeColor()`. Puoi passare qualsiasi `java.awt.Color`. Vuoi una sfumatura? Usa `setForeColor` per il colore iniziale e `setBackColor` per quello finale.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Questo è un modo rapido per **create colored rectangle** con riempimento a gradiente invece di un colore solido.

## Creare un cerchio colorato

I cerchi sono semplicemente ellissi con larghezza e altezza uguali. La stessa logica di colore si applica:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Se ti serve un riempimento trasparente, imposta il canale alfa:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Ora hai padroneggiato la tecnica **create colored circle**.

## Salvare il documento

Aspose.Words ti consente di esportare in molti formati: DOCX, PDF, HTML, PNG, come preferisci. Per questa demo rimaniamo su DOCX perché preserva perfettamente le forme vettoriali.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Cambiare il `SaveFormat` è tutto ciò che serve per generare una versione PDF della stessa opera d'arte raggruppata.

## Errori comuni e come evitarli

- **Hai dimenticato di aggiungere la forma al gruppo?** La forma apparirà sulla pagina ma non si muoverà con il gruppo. Ricorda sempre di chiamare `group.appendChild(yourShape)`.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crea forma rettangolare in Word con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}