---
category: general
date: 2026-08-14
description: Raggruppa forme in Word con Java usando Aspose.Words. Scopri come creare
  una forma rettangolare, impostare le dimensioni della forma e raggruppare più forme
  in un documento Word vuoto.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: it
lastmod: 2026-08-14
og_description: Raggruppa forme in Word usando Aspose.Words per Java. Crea un documento
  Word vuoto, crea una forma rettangolare, imposta le dimensioni della forma e raggruppa
  più forme in pochi minuti.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Raggruppa forme in Word – esempio Java per sviluppatori
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Raggruppare le forme in Word – guida completa alla programmazione
url: /it/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Raggruppare forme in Word – guida completa di programmazione

Se hai bisogno di **raggruppare forme in Word**, questo tutorial ti guida attraverso l’intero processo con Java e Aspose.Words. Imparerai come **creare un documento Word vuoto**, **creare una forma rettangolare**, **impostare le dimensioni della forma** e infine **raggruppare più forme** affinché si comportino come un unico oggetto.

Lavorare con le forme in un file Word spesso sembra disegnare su una tela senza pennello. Alla fine di questa guida avrai uno snippet di codice riutilizzabile da inserire in qualsiasi progetto Java, sia che tu stia generando report, fatture o template personalizzati.

## Cosa ti serve

- Java 8 o versioni successive
- Aspose.Words per Java (l’ultima versione, ad es. 24.9)
- Un IDE come IntelliJ IDEA o Eclipse
- Familiarità di base con la programmazione orientata agli oggetti

Tutti questi prerequisiti sono gratuiti da installare, e il codice qui sotto si compila con una singola dipendenza Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Passo 1: Creare un documento Word vuoto e inizializzare il builder

La prima cosa da fare è **creare un documento Word vuoto**. Questo ti fornisce una tela pulita su cui potrai inserire le forme in seguito.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` rappresenta l’intero file *.docx*, mentre `DocumentBuilder` è l’aiutante che inserisce paragrafi, tabelle e forme. Inizializzare entrambi gli oggetti è la base per qualsiasi attività di automazione di Word.

## Passo 2: Inserire un contenitore di forma di gruppo

Una **forma di gruppo** funziona come una cartella che può contenere altre forme. Prima creiamo il contenitore con una dimensione fissa di 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

Il metodo `insertGroupShape` restituisce un oggetto `GroupShape`. Tutte le forme successive che desideri trattare come un’unica unità devono essere aggiunte a questo oggetto.

## Passo 3: Creare forme rettangolari e impostare le dimensioni delle forme

Ora **creiamo oggetti forma rettangolare**, configuriamo la loro dimensione e li posizioniamo all’interno del gruppo. Questo passaggio dimostra anche come **impostare con precisione le dimensioni della forma**.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Entrambi i rettangoli condividono le stesse dimensioni, ma le loro proprietà `left` differiscono, quindi appaiono affiancati. Puoi modificare `setTop` e `setLeft` per disporre qualsiasi layout ti serva.

## Passo 4: Salvare il documento contenente i rettangoli raggruppati

Dopo che le forme sono all’interno del gruppo, basta salvare il `Document`. Il file risultante mostrerà due rettangoli che si muovono insieme quando selezionati.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Eseguendo il programma si crea `GroupShape.docx` nella directory di lavoro. Aprilo in Microsoft Word, seleziona un rettangolo e noterai che l’intero gruppo si sposta come un’unica unità—esattamente ciò che **raggruppare forme in Word** dovrebbe fare.

![Group shapes in Word example](group-shapes.png){alt="Esempio di forme raggruppate in Word"}

*Figura: Due forme rettangolari raggruppate in un documento Word.*

## Consiglio esperto: Riutilizzare lo stesso gruppo di forme

Se devi aggiungere altre forme in seguito (ad es. cerchi, caselle di testo), conserva un riferimento a `groupShape` e continua a chiamare `appendChild`. Questo evita di ricreare il contenitore e garantisce che tutti i membri rimangano sincronizzati.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Casi limite e domande frequenti

- **Cosa succede se le forme si sovrappongono?** La sovrapposizione è consentita; Word le renderizza nell’ordine in cui sono state aggiunte. Usa `setZOrder` se hai bisogno di un ordine di impilamento esplicito.
- **Posso raggruppare forme su pagine diverse?** No. Un `GroupShape` è confinato a una singola pagina perché il suo sistema di coordinate è relativo alla pagina.
- **Le forme raggruppate ereditano la formattazione?** Ogni figlio mantiene la propria formattazione (colore di riempimento, stile della linea). Per applicare uno stile uniforme, itera su `groupShape.getChildNodes()` e imposta le proprietà programmaticamente.

## Codice sorgente completo per riferimento

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Eseguendo il programma si ottiene un file DOCX in cui i due rettangoli sono **raggruppati**. Selezionando uno qualsiasi dei rettangoli, entrambi si muovono, confermando che hai **raggruppato correttamente più forme**.

## Conclusione

Ora sai come **raggruppare forme in Word** usando Java, dalla **creazione di un documento Word vuoto** alla **creazione di una forma rettangolare**, **impostazione delle dimensioni della forma** e infine **raggruppare più forme** in un unico oggetto mobile. Questo modello scala a qualsiasi numero di forme e può essere combinato con testo, immagini o grafici per costruire documenti ricchi e programmabili.

### Qual è il prossimo passo?

- Esplora **raggruppare più forme** di tipo diverso (ellissi, frecce, caselle di testo).
- Applica colori di riempimento o bordi chiamando `shape.getFillColor()` e `shape.getLine().setColor()`.
- Inserisci la forma raggruppata in una cella di tabella per report strutturati.
- Combina questo approccio con la stampa unione per generare contratti personalizzati che includono grafiche brandizzate.

Sentiti libero di sperimentare, adattare le dimensioni o incorporare contenuti aggiuntivi. Quando padroneggerai il raggruppamento, i tuoi script di automazione Word diventeranno molto più flessibili e manutenibili. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}