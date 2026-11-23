---
category: general
date: 2026-11-22
description: Scopri come aggiungere una forma a Word usando Aspose.Words per Java
  – inserisci un rettangolo e nascondilo programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shape to word
- how to insert shape
- how to hide shape
- hide shape in word
language: it
lastmod: 2026-11-22
og_description: Aggiungi una forma a Word usando Aspose.Words per Java. Questo tutorial
  mostra come inserire un rettangolo, nascondere la forma e salvare il documento.
og_image_alt: Screenshot of Java code that adds and hides a shape in a Word document
og_title: Aggiungi forma a Word con Aspose.Words – Guida Java
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  headline: How to add shape to Word documents with Aspose.Words for Java
  type: TechArticle
- description: Learn how to add shape to Word using Aspose.Words for Java – insert
    a rectangle and hide it programmatically.
  name: How to add shape to Word documents with Aspose.Words for Java
  steps:
  - name: Expected output
    text: '* The file `output.docx` opens without any visible shapes. * If you inspect
      the document with Aspose.Words (e.g., `doc.getChildNodes(NodeType.SHAPE, true).size()`),
      the shape count will be **1**, confirming that the shape exists but is hidden.'
  - name: 1. Creating a shape in a fresh document
    text: 'If you start from scratch, replace the load line with:'
  - name: 2. Positioning the shape precisely
    text: 'By default, `insertShape` places the shape at the current cursor location.
      To position it absolutely:'
  - name: 3. Controlling visibility per output format
    text: 'If you need the shape visible in the Word UI but hidden when exporting
      to PDF, use `Shape.setWrapType(WrapType.NONE)` together with `Hidden`:'
  - name: 4. Adding text inside the shape
    text: 'A rectangle can contain a text frame:'
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- Shape handling
title: Come aggiungere forme ai documenti Word con Aspose.Words per Java
url: /it/java/images-shapes/how-to-add-shape-to-word-documents-with-aspose-words-for-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere forme ai documenti Word con Aspose.Words per Java

Se hai bisogno di **aggiungere forme a Word** documenti programmaticamente, Aspose.Words per Java lo rende semplice. In questa guida imparerai **come inserire una forma**, controllarne la visibilità e **come nascondere una forma** in modo che il file finale appaia esattamente come ti aspetti.

Seguirai un esempio completo e eseguibile che carica un file `.docx` esistente, inserisce un rettangolo, lo nasconde e salva il risultato. Non sono necessari script esterni né passaggi manuali, e il tutorial copre variazioni comuni come la creazione di un nuovo documento da zero o la nasconditura di una forma solo durante la stampa.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 (o successiva) installata – le versioni precedenti funzionano, ma l'ultima LTS offre migliori prestazioni.  
* Maven 3.8+ per la gestione delle dipendenze.  
* Una licenza valida di Aspose.Words per Java (la valutazione gratuita è sufficiente per l'apprendimento).  
* Un IDE o editor di testo a tua scelta (ad es., IntelliJ IDEA, VS Code).

## Passo 1: Aggiungere Aspose.Words al tuo progetto Maven

Aggiungi la seguente dipendenza al tuo `pom.xml`. Questo recupera l'ultima versione stabile (a novembre 2026).

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

> **Suggerimento:** Usa una clausola `<scope>provided</scope>` se prevedi di distribuire il JAR con la tua logica di licenza.

## Aggiungere forma a Word – inizializzare il documento

Il primo passo funzionale è ottenere un oggetto `Document`. Puoi caricare un file esistente o crearne uno nuovo.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document (or create a new one)
        Document doc = new Document("input.docx");   // <-- replace with your path
        // If you prefer a blank document, use:
        // Document doc = new Document();
```

*Perché è importante*: la classe `Document` è il punto di ingresso per tutte le manipolazioni di Word. Caricare un file esistente preserva stili, intestazioni e piè di pagina, mentre un nuovo documento ti offre una tela pulita.

## Come inserire una forma in un documento Word

Successivamente, crea un `DocumentBuilder` per modificare il contenuto del documento. Il builder fornisce metodi per inserire testo, tabelle e **forme**.

```java
        // Create a builder attached to the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a rectangle shape with a width of 100 points and height of 50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
```

La chiamata `insertShape` restituisce un oggetto `Shape` che puoi configurare ulteriormente (colore, bordo, testo, ecc.). Le dimensioni sono espresse in punti (1 pt = 1/72 in).

*Perché potresti usare un rettangolo*: i rettangoli sono il contenitore più comune per annotazioni, filigrane o segnaposti. Puoi sostituire `ShapeType.RECTANGLE` con `ShapeType.ELLIPSE`, `ShapeType.LINE`, ecc., per soddisfare diverse esigenze visive.

## Come nascondere una forma in Word

A volte è necessario che una forma esista per i calcoli di layout ma non appaia nella resa finale. Aspose.Words fornisce il metodo `setHidden(true)` per ottenere questo risultato.

```java
        // Hide the shape so it does not appear when the document is opened
        rectangle.setHidden(true);
```

Il flag hidden funziona come l'opzione di formattazione **Hidden** in Microsoft Word: la forma è omessa dal layout visivo ma partecipa comunque al modello a oggetti del documento. Questo è utile per:

* Memorizzare metadati o marcatori che la tua applicazione leggerà in seguito.  
* Creare segnaposti che vengono rimossi subito prima della pubblicazione.  
* Controllare la visibilità per diversi formati di output (ad es., nascondere in HTML ma mantenere in PDF).

> **Nota:** le forme nascoste vengono comunque esportate in PDF per impostazione predefinita. Se desideri escluderle anche dal PDF, imposta `rectangle.getWrapType( ) = WrapType.NONE` e regola di conseguenza la proprietà `Hidden`.

## Passo 4: Salvare il documento modificato

Infine, persisti le modifiche in un nuovo file.

```java
        // Save the document with the hidden rectangle
        doc.save("output.docx");   // <-- replace with your desired output path
    }
}
```

Quando apri `output.docx` in Microsoft Word, il rettangolo non sarà visibile, ma rimarrà parte dell'albero del documento. Puoi verificarne la presenza programmaticamente ricaricando il file e controllando `Shape.isHidden()`.

### Output previsto

* Il file `output.docx` si apre senza forme visibili.  
* Se ispezioni il documento con Aspose.Words (ad es., `doc.getChildNodes(NodeType.SHAPE, true).size()`), il conteggio delle forme sarà **1**, confermando che la forma esiste ma è nascosta.

## Varianti avanzate e casi limite

### 1. Creare una forma in un documento nuovo

Se parti da zero, sostituisci la riga di caricamento con:

```java
Document doc = new Document();          // creates an empty Word file
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Report Title");        // add a title before the shape
```

### 2. Posizionare la forma con precisione

Per impostazione predefinita, `insertShape` posiziona la forma nella posizione corrente del cursore. Per posizionarla in modo assoluto:

```java
rectangle.setLeft(72);   // 1 inch from the left margin
rectangle.setTop(144);   // 2 inches from the top of the page
rectangle.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangle.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
```

### 3. Controllare la visibilità per formato di output

Se vuoi che la forma sia visibile nell'interfaccia di Word ma nascosta durante l'esportazione in PDF, usa `Shape.setWrapType(WrapType.NONE)` insieme a `Hidden`:

```java
rectangle.setHidden(false);                 // visible in Word
rectangle.getParagraph().getParagraphFormat()
        .setPageBreakBefore(true);          // ensure it stays on its own line
// When converting to PDF, hide it programmatically:
if (exportingToPdf) {
    rectangle.setHidden(true);
}
```

### 4. Aggiungere testo all'interno della forma

Un rettangolo può contenere un frame di testo:

```java
Shape textBox = builder.insertShape(ShapeType.TEXT_BOX, 200, 50);
textBox.getTextBox().setInternalMarginLeft(5);
textBox.getTextBox().setInternalMarginTop(5);
builder.moveTo(textBox.getFirstParagraph());
builder.write("Confidential");
```

Puoi quindi nascondere la casella di testo con la stessa chiamata `setHidden(true)`.

## Problemi comuni e come evitarli

| Sintomo | Causa | Soluzione |
|---------|-------|-----------|
| La forma appare anche dopo `setHidden(true)` | Il documento è stato salvato prima che il flag hidden fosse impostato. | Assicurati di chiamare `setHidden(true)` **prima** di `doc.save()`. |
| Le dimensioni della forma appaiono distorte | Confusione tra punti e pixel su schermi ad alta DPI. | Usa i punti (72 pt = 1 in) per dimensioni coerenti su tutte le piattaforme. |
| La forma nascosta stampa comunque | Alcune stampanti ignorano il flag hidden. | Imposta `Shape.setWrapType(WrapType.NONE)` e inoltre rimuovi `Shape.getParagraph().getParagraphFormat().setPageBreakBefore(false)`. |

## Conclusione

Ora sai come **aggiungere forme a documenti Word** usando Aspose.Words per Java, **come inserire una forma** e **come nascondere una forma** in modo che rimanga invisibile agli utenti finali ma faccia comunque parte della struttura del documento. L'esempio completo sopra carica un file, inserisce un rettangolo, lo nasconde e salva il risultato, coprendo sia i casi d'uso tipici sia diversi scenari limite.

Da qui puoi approfondire argomenti correlati come **come inserire forme** con colori di riempimento personalizzati, **come nascondere forme in Word** per la stampa condizionale, o l'automazione di elaborazioni di massa di documenti con Aspose.Words. Sperimenta con valori diversi di `ShapeType`, opzioni di posizionamento e flag di visibilità per adattarli al tuo flusso di lavoro specifico.

Buona programmazione e goditi la flessibilità che la manipolazione programmatica di Word porta alle tue applicazioni Java!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Create a Word document programmatically, add and hide a shape in Java using Aspose.Words](/words/english/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/)
- [How to hide shape in a Word document using Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Create a blank .docx Word document and add a hidden rectangle shape with Aspose.Words](/words/english/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}