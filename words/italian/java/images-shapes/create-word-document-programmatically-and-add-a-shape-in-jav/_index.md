---
category: general
date: 2026-10-26
description: Scopri come creare un documento Word programmaticamente, aggiungere una
  forma e nascondere un oggetto in Word usando Aspose.Words per Java – guida passo‑passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: it
lastmod: 2026-10-26
og_description: Crea un documento Word programmaticamente, impara come aggiungere
  forme e nascondere oggetti in Word con Aspose.Words per Java. Esempio completo e
  eseguibile.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Crea un documento Word programmaticamente – aggiungi e nascondi forme in
  Java
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Creare un documento Word programmaticamente e aggiungere una forma in Java
url: /it/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creare un documento Word programmaticamente e aggiungere una forma in Java

Se hai bisogno di **creare un documento Word programmaticamente**, questo tutorial ti mostra esattamente come farlo, aggiungere una forma e poi nascondere l'oggetto in Word. Che tu stia costruendo un generatore di report o un sistema di contratti automatizzato, otterrai una soluzione completa, pronta‑all'uso in pochi minuti.

Imparerai a:

* Inizializzare un documento Word con Aspose.Words per Java.  
* Inserire un'ellisse (o qualsiasi altra forma) usando la tecnica **how to add shape**.  
* Nascondere quella forma in modo che non appaia mai quando il file viene aperto, rispondendo alla domanda **how to hide shape**.  

Non sono necessari strumenti esterni oltre alla libreria Aspose.Words, e il codice funziona con Java 17 e versioni successive.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java Development Kit (JDK) 17 o più recente installato.  
* Maven o Gradle per gestire le dipendenze (l'esempio utilizza Maven).  
* Una licenza valida di Aspose.Words per Java (la valutazione gratuita è sufficiente per i test).  

Se sei nuovo a Aspose.Words, consulta la guida ufficiale Getting Started, ma non sarà necessario leggerla per seguire questo tutorial.

## Dipendenza Maven

Aggiungi la seguente dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Consiglio:** Mantieni il numero di versione aggiornato; le versioni più recenti contengono correzioni di bug per la gestione delle forme.

## Passo 1: Creare un documento Word programmaticamente – inizializzare il documento

La prima cosa da fare quando **crei un documento Word programmaticamente** è istanziare un oggetto `Document`. Questo oggetto rappresenta l'intero file .docx in memoria.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché questo passo è importante*: La classe `Document` è il punto di ingresso per tutte le operazioni di elaborazione Word. Senza di essa non è possibile aggiungere pagine, paragrafi o forme.

## Passo 2: How to add shape – inserimento di un'ellisse

Ora affrontiamo la parte **how to add shape** del tutorial. Aspose.Words supporta molti tipi di forme (Ellipse, Rectangle, TextBox, ecc.). Di seguito inseriamo un'ellisse con larghezza e altezza di 50 punti.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

Il metodo `insertShape` restituisce un oggetto `Shape` che puoi personalizzare ulteriormente — colore, stile della linea, rotazione e altro. Le coordinate sono misurate in punti (1/72 di pollice).

*Perché potresti voler aggiungere una forma*: Le forme sono utili per filigrane, elementi decorativi o segnaposti che in seguito nascondi o sostituisci.

## Passo 3: How to hide shape – rendere l'oggetto invisibile in Word

Per rispondere alla domanda **how to hide shape**, imposta semplicemente la proprietà `Hidden` della forma su `true`. Questo indica a Word di trattare la forma come un oggetto nascosto, così non verrà mai visualizzata nella vista del documento o nella stampa.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Se hai bisogno di **nascondere l'oggetto in Word** per un utente o una condizione specifica, puoi attivare/disattivare questa proprietà a runtime in base alla tua logica di business.

> **Nota:** Le forme nascoste fanno ancora parte della struttura XML del documento. Possono essere rivelate in seguito impostando `setHidden(false)`.

## Passo 4: Salvare il documento

Dopo aver aggiunto e nascosto la forma, scrivi il documento su disco.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Quando apri `HiddenShapeDemo.docx` in Microsoft Word, vedrai una pagina vuota perché l'ellisse è nascosta. Il documento si comporta altrimenti come qualsiasi normale file Word.

## Esempio completo funzionante

Mettendo insieme tutti i pezzi, ecco il programma completo e eseguibile:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Output previsto**

```
Document created successfully.
```

Aprendo `HiddenShapeDemo.docx` si vede una pagina vuota; l'ellisse nascosta non viene renderizzata, confermando che l'operazione **hide object in Word** è riuscita.

## Casi limite e variazioni

| Situazione | Cosa cambiare | Perché |
|-----------|----------------|-----|
| Nascondere un rettangolo invece di un'ellisse | Usa `ShapeType.RECTANGLE` in `insertShape` | Segnaposto visivo diverso |
| Nascondere più forme contemporaneamente | Loop attraverso `doc.getChildNodes(NodeType.SHAPE, true)` e imposta `setHidden(true)` | Utile per l'elaborazione in blocco |
| Mostrare la forma solo nella visualizzazione di stampa | Imposta `shape.setVisible(false)` e `shape.setPrint(true)` | Word distingue tra visibilità su schermo e stampa |
| Usare un'unità di misura diversa | Chiama `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` | Allinea ai requisiti del tuo layout |

## Errori comuni

* **Dimenticare di chiamare `setHidden(true)`** – la forma apparirà normalmente.  
* **Salvare il documento prima di nascondere la forma** – l'ordine è importante; nascondi prima, poi salva.  
* **Usare una versione obsoleta di Aspose.Words** – le versioni più vecchie potrebbero non includere l'API `setHidden`.  

Testa sempre il file generato nella versione target di Microsoft Word per assicurarti che lo stato nascosto si comporti come previsto.

## Conclusione

In questa guida hai imparato come **creare un documento Word programmaticamente**, **aggiungere una forma**, e **nascondere l'oggetto in Word** usando Aspose.Words per Java. L'esempio completo dimostra i passaggi esatti, dall'inizializzazione del documento al salvataggio di un file in cui la forma non appare mai.  

Da qui puoi:

* Sperimentare con altri tipi di forme (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Combinare forme nascoste con segnalibri per creare template dinamici.  
* Esplorare le proprietà `setVisible` e `setPrint` per un controllo più granulare sulla visibilità degli oggetti.

Buon coding e divertiti ad automatizzare i tuoi documenti Word!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare un documento Word vuoto con Aspose.Words per Java](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Come nascondere una forma in un documento Word usando Java](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Creare documento Word Java – Aggiungere forma rettangolo con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}