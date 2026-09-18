---
category: general
date: 2026-09-18
description: Crea un documento vuoto e inserisci forme in Word con Aspose.Words –
  scopri come aggiungere una forma triangolare e altro.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: it
lastmod: 2026-09-18
og_description: Crea un documento vuoto in Word usando Aspose.Words e impara come
  inserire una forma a triangolo, raggruppare forme e altre grafiche. Segui questa
  guida completa.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Crea un documento vuoto e aggiungi forme a Word – guida passo‑passo
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Come creare un documento vuoto e aggiungere forme a Word
url: /it/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento vuoto e aggiungere forme a Word

Se hai bisogno di **creare un documento vuoto** e poi arricchirlo con grafica, questa guida ti mostra esattamente come fare. Cammineremo passo passo nella creazione di un file Word da zero e **aggiungeremo forme a Word**, incluso **come inserire una forma triangolo**, usando Aspose.Words per Java.

Concluderai il tutorial con un file *.docx* pronto all'uso che contiene una forma raggruppata con all'interno un triangolo. I passaggi coprono tutto, dall'impostazione del progetto al salvataggio del **create word document** finale. Non sono necessari strumenti esterni oltre a Aspose.Words.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versioni successive installate  
* Maven o Gradle per la gestione delle dipendenze  
* Una licenza Aspose.Words per Java (la valutazione gratuita è sufficiente per questa demo)  

Se preferisci un sistema di build diverso, adatta di conseguenza la sintassi della dipendenza. Il codice funziona su qualsiasi piattaforma che supporti Java.

## Creare un documento vuoto con Aspose.Words

La prima operazione è **creare un documento vuoto** in memoria. Aspose.Words fornisce la classe `Document` che rappresenta un file Word senza alcun contenuto.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

Il costruttore `new Document()` crea una struttura *.docx* vuota, che potrai poi popolare con paragrafi, tabelle o grafica. Poiché il documento è vuoto, hai il pieno controllo su ogni elemento che aggiungi.

## Aggiungere forme a Word – inserire una forma di gruppo

Una forma di gruppo ti permette di trattare più grafiche come un'unica unità. Questo è utile quando vuoi spostare o ridimensionare più forme insieme.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` è l'API principale per aggiungere contenuti. La chiamata `insertGroupShape` crea un contenitore di 300 × 300 punti (circa 4 × 4 pollici). Dopo questa chiamata il cursore è posizionato *all'interno* del gruppo, pronto per ulteriori forme.

### Perché usare una forma di gruppo?

Raggruppare mantiene le grafiche correlate allineate e semplifica l'applicazione di formattazioni uniformi. Se in seguito decidi di spostare il triangolo, l'intero gruppo si muove insieme, preservando il layout.

## Come inserire una forma triangolo all'interno del gruppo

Ora affrontiamo **come inserire una forma triangolo**. Il triangolo è uno dei valori predefiniti di `ShapeType`.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

La chiamata `moveTo` assicura che il punto di inserimento del builder sia il primo paragrafo del gruppo. `insertShape` aggiunge quindi un triangolo di 60 × 60 punti. Poiché il cursore è dentro il gruppo, il triangolo diventa un figlio della forma di gruppo.

Suggerimenti per **add triangle shape**:

* La dimensione è misurata in punti; 72 punti corrispondono a un pollice. Regola le dimensioni in base al tuo layout.  
* Se ti serve un'orientazione diversa, usa `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` per allineare la forma all'interno del gruppo.  
* Il triangolo eredita i colori di riempimento e di linea del gruppo, a meno che non li sovrascrivi con `shape.getFillColor()` o `shape.getStrokeColor()`.

## Salvare il documento – create word document

Dopo aver costruito la grafica, salvi il file. Questo passaggio finalizza l'operazione di **create word document**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` scrive la rappresentazione in memoria su disco come documento Word standard. Puoi aprire `ExtendedGroup.docx` in Microsoft Word, LibreOffice o qualsiasi visualizzatore che supporti il formato OOXML. Il file mostrerà una forma raggruppata contenente un triangolo, esattamente come costruito dal codice.

## Esempio completo eseguibile

Unendo tutti i pezzi, ecco il programma completo che puoi copiare, compilare ed eseguire:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Risultato atteso

Quando apri `ExtendedGroup.docx`, vedrai una singola forma di gruppo al centro della pagina. All'interno di quel gruppo, appare un piccolo triangolo nella posizione predefinita. Il triangolo può essere selezionato e spostato come parte del gruppo, confermando che **add shapes to word** ha funzionato correttamente.

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|--------|
| *Posso aggiungere più di una forma all'interno del gruppo?* | Sì. Dopo aver inserito il triangolo, mantieni il cursore dentro il gruppo e chiama nuovamente `builder.insertShape` con un diverso `ShapeType`. |
| *E se volessi che il triangolo fosse rosso?* | Recupera lo `Shape` restituito da `insertShape` e chiama `shape.getFillColor().setColor(Color.RED)`. |
| *Funziona con file .doc più vecchi?* | Aspose.Words salva nel formato che specifichi. Usa `doc.save("file.doc", SaveFormat.DOC)` per creare un documento Word legacy. |
| *Come modifico il bordo del gruppo?* | Usa `group.getStrokeColor().setColor(Color.BLUE)` e `group.setLineWeight(2.0)` per personalizzare il contorno. |
| *C'è un modo per ruotare il triangolo?* | Chiama `shape.getRotation()` per impostare un angolo in gradi. |

## Pro tip

* **Riutilizza il builder** – creare un nuovo `DocumentBuilder` per ogni forma aggiunge overhead. Mantieni un unico builder per documento.  
* **Conversione unità** – se lavori con millimetri, convertili in punti (`points = mm * 2.83465`).  
* **Prestazioni** – per documenti di grandi dimensioni, chiama `doc.updatePageLayout()` una sola volta dopo aver aggiunto tutte le forme.

## Conclusione

Ora sai come **creare un documento vuoto**, **aggiungere forme a Word**, e in particolare **come inserire una forma triangolo** usando Aspose.Words per Java. L'esempio completo dimostra l'intero flusso di lavoro, da un file vuoto a un **create word document** salvato che contiene un triangolo raggruppato.

Da qui puoi esplorare altri valori di `ShapeType`, applicare stili personalizzati o combinare più gruppi per costruire diagrammi complessi. Sperimenta con diverse dimensioni, colori e posizioni per padroneggiare l'automazione di Word in Java.

--- 

*Pronto a automatizzare il tuo prossimo report? Clona l'esempio, modifica le dimensioni e integra il codice nella tua applicazione oggi stesso.*


## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}