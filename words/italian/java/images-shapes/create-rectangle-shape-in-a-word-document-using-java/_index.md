---
category: general
date: 2026-11-15
description: Crea una forma rettangolare in Word con Java e impara come aggiungere
  forme a Word, impostare le dimensioni delle forme e salvare il documento Word in
  modo efficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add shapes to word
- save word document
- set shape dimensions
- define shape size
language: it
lastmod: 2026-11-15
og_description: Crea una forma rettangolare in un documento Word usando Java. Impara
  ad aggiungere forme a Word, impostare le dimensioni della forma e salvare il documento
  Word in pochi minuti.
og_image_alt: Screenshot showing a rectangle shape inside a group shape in a Word
  document
og_title: Crea una forma rettangolare in Word con Java – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  headline: Create rectangle shape in a Word document using Java
  type: TechArticle
- description: Create rectangle shape in Word with Java and learn how to add shapes
    to Word, set shape dimensions, and save Word document efficiently.
  name: Create rectangle shape in a Word document using Java
  steps:
  - name: Prerequisites
    text: '* Java 17 or later (the code compiles with Java 8 as well). * Aspose.Words
      for Java 23.10 or newer – you can obtain it from Maven Central. * A basic understanding
      of Java syntax and object‑oriented concepts.'
  - name: Expected output
    text: '* A Word file named `RectangleShapeDemo.docx`. * Inside the first paragraph,
      a group shape containing a 100 pt × 50 pt rectangle. * No text is added, so
      the rectangle appears on a blank page.'
  - name: What’s next?
    text: '* Explore **add shapes to Word** by inserting circles, arrows, or text
      boxes. * Combine multiple shapes into a single `GroupShape` and apply transformations
      (rotate, flip). * Generate reports that embed charts as shapes, then **save
      Word document** as PDF for sharing.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Crea una forma rettangolare in un documento Word usando Java
url: /it/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea una forma rettangolare in un documento Word usando Java

Se hai bisogno di **creare una forma rettangolare** all'interno di un file Word, questa guida ti mostra esattamente come farlo con Java. Vedrai come **aggiungere forme a Word**, controllare le **impostazioni delle dimensioni della forma**, e infine **salvare il documento Word** senza lasciare il tuo IDE.

Nelle sezioni successive otterrai un esempio completo e eseguibile, una spiegazione di ogni riga e consigli per le difficoltà comuni, come problemi di dimensionamento e compatibilità del documento. Non sono necessari riferimenti esterni—solo la libreria Aspose.Words for Java.

## Cosa imparerai

* Come inizializzare un `Document` e un `DocumentBuilder`.
* Come inserire una **group shape** e posizionare un rettangolo al suo interno.
* Come **definire la dimensione della forma** usando `setWidth` e `setHeight`.
* Come **salvare il documento Word** in formato `.docx`.
* Gestione dei casi limite per diverse dimensioni di pagina e impostazioni DPI.

### Prerequisiti

* Java 17 o successiva (il codice si compila anche con Java 8).
* Aspose.Words for Java 23.10 o più recente – è possibile ottenerla da Maven Central.
* Una comprensione di base della sintassi Java e dei concetti di programmazione orientata agli oggetti.

> **Pro tip:** Se prevedi di aggiungere altre forme in seguito (ad es., cerchi o caselle di testo), tienile all'interno della stessa `GroupShape`. Questo rende più semplice spostare, ruotare o formattare l'intera collezione.

## Passo 1: Inizializzare il documento e il builder

Il primo passo è creare un file Word vuoto e un `DocumentBuilder` che ti permette di scrivere contenuti.  

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Perché è importante:* Un `Document` rappresenta l'intero file, mentre `DocumentBuilder` fornisce metodi di alto livello per inserire testo, tabelle e **forme**. Senza il builder dovresti manipolare manualmente i nodi di basso livello.

## Passo 2: Inserire una group shape per contenere più forme

Una **group shape** funziona come un contenitore; puoi aggiungere diverse forme e trattarle come un unico oggetto in seguito (ad es., spostarle o ruotarle insieme).

```java
        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();
```

*Perché usare una group shape?* Se in seguito decidi di aggiungere frecce, cerchi o etichette attorno al rettangolo, il gruppo mantiene tutto allineato. Inoltre semplifica il flusso di lavoro **add shapes to Word** perché è necessario un solo chiamata a `appendChild` per ogni nuova forma.

## Passo 3: Creare la forma rettangolare

Ora creiamo il rettangolo effettivo che vivrà all'interno del gruppo. Il costruttore `Shape` richiede il `Document` proprietario e il tipo di forma desiderato.

```java
        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
```

*Perché un rettangolo?* `ShapeType.RECTANGLE` è la primitiva più comune per evidenziare sezioni, creare segnaposti o disegnare semplici mock‑up UI direttamente in Word.

## Passo 4: Definire le dimensioni del rettangolo

Impostare le dimensioni è il punto in cui **set shape dimensions** diventa importante. Puoi usare qualsiasi unità di misura supportata da Aspose.Words; il valore predefinito è punti (1 pt = 1/72 pollice).

```java
        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

> **Nota:** Se preferisci i millimetri, chiama `rectangle.setWidth(ConversionUtil.inchesToPoints(1.39));` dove `1.39 in ≈ 35 mm`. Questo dimostra la flessibilità di **define shape size**.

## Passo 5: Aggiungere il rettangolo alla group shape

Aggiungere il rettangolo al gruppo creato in precedenza lo fa apparire nel documento.

```java
        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);
```

A questo punto il rettangolo è posizionato nell'angolo in alto a sinistra del gruppo. Puoi spostarlo in seguito con `rectangle.setLeft(...)` e `rectangle.setTop(...)` se hai bisogno di un posizionamento preciso.

## Passo 6: (Opzionale) Salvare il documento per vedere il risultato

Infine, scrivi il documento su disco. Questo è il passo **save Word document** che produce un file `.docx` che puoi aprire in Microsoft Word, LibreOffice o Google Docs.

```java
        // Step 6: Save the document (optional but recommended for verification)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

Eseguendo il programma si crea `RectangleShapeDemo.docx` contenente un unico rettangolo all'interno di una group shape. Aprendo il file si vede un rettangolo bianco semplice—esattamente della dimensione che hai definito.

### Output previsto

* Un file Word chiamato `RectangleShapeDemo.docx`.
* All'interno del primo paragrafo, una group shape contenente un rettangolo di 100 pt × 50 pt.
* Nessun testo è aggiunto, quindi il rettangolo appare su una pagina vuota.

## Varianti comuni e casi limite

| Situazione | Come adattare il codice |
|-----------|-----------------------|
| **Dimensione pagina diversa** (es., A4) | Chiama `document.getFirstSection().getPageSetup().setPaperSize(PaperSize.A4);` prima di inserire la forma. |
| **DPI più alto per la stampa** | Moltiplica larghezza/altezza per il fattore DPI desiderato, ad es., `rectangle.setWidth(200 * 2);` per doppia risoluzione. |
| **Aggiungere un'etichetta di testo all'interno del rettangolo** | Crea una `Shape` di tipo `TEXT_BOX`, imposta `setWidth`/`setHeight` per corrispondere al rettangolo, quindi aggiungila alla stessa `GroupShape`. |
| **Ruotare il rettangolo** | Usa `rectangle.setRotationAngle(45);` per ruotare di 45 gradi in senso orario. |
| **Salvare come PDF invece di DOCX** | Sostituisci `document.save("output.docx");` con `document.save("output.pdf");` – la stessa API funziona per PDF, preservando il rettangolo. |

## Consigli professionali per un'implementazione robusta

1. **Riutilizza il builder** – dopo aver inserito la group shape, puoi continuare ad aggiungere paragrafi o tabelle senza creare una nuova istanza di builder.
2. **Rilascia le risorse** – sebbene il garbage collector di Java gestisca la maggior parte degli oggetti, chiamare esplicitamente `document.close();` (se usi stream) previene perdite di handle di file.
3. **Convalida le dimensioni** – prima di chiamare `setWidth`/`setHeight`, assicurati che i valori siano positivi; valori negativi generano `IllegalArgumentException`.
4. **Compatibilità di versione** – il codice funziona con Aspose.Words 23.x e successive. Versioni precedenti potrebbero richiedere `Shape.setSize(width, height)` invece dei singoli setter.

## Esempio completo e eseguibile

```java
import com.aspose.words.*;

public class RectangleShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Initialise a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape into the document
        GroupShape groupShape = builder.insertGroupShape();

        // Step 3: Create a rectangle shape that will live inside the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Step 4: Define the rectangle's size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);

        // Optional: set a light gray fill to make it visible in Word
        rectangle.getFillColor() .setRGB(200, 200, 200);

        // Step 5: Add the rectangle to the group shape
        groupShape.appendChild(rectangle);

        // Step 6: Save the document (you can also save as PDF)
        document.save("output/RectangleShapeDemo.docx");
    }
}
```

> **Verifica del risultato:** Apri `output/RectangleShapeDemo.docx` in Microsoft Word. Dovresti vedere un rettangolo della dimensione specificata centrato nella parte superiore della prima pagina. Se il rettangolo appare troppo piccolo, regola i valori passati a `setWidth` e `setHeight`.

## Conclusione

Ora sai come **creare una forma rettangolare** in un file Word usando Java, come **aggiungere forme a Word** tramite una `GroupShape`, come **impostare le dimensioni della forma** e **definire la dimensione della forma**, e infine come **salvare il documento Word** per una distribuzione successiva. Lo stesso schema funziona per altri tipi di forma, consentendoti di creare diagrammi complessi programmaticamente.

### Cosa c'è dopo?

* Esplora **add shapes to Word** inserendo cerchi, frecce o caselle di testo.
* Combina più forme in una singola `GroupShape` e applica trasformazioni (ruota, capovolgi).
* Genera report che incorporano grafici come forme, quindi **save Word document** come PDF per la condivisione.

Sentiti libero di sperimentare con le dimensioni, i colori e il posizionamento per adattarli al tuo scenario specifico. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Rectangle Shape in Java Word Document – Full Step‑by‑Step Guide](/words/english/java/images-shapes/create-rectangle-shape-in-java-word-document-full-step-by-st/)
- [Create word document java – hide shape and set fill color](/words/english/java/images-shapes/create-word-document-java-hide-shape-and-set-fill-color/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}