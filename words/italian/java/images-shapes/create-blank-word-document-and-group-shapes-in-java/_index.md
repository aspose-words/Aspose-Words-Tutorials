---
category: general
date: 2026-08-23
description: Crea un documento Word vuoto con Aspose.Words per Java, impara a raggruppare
  le forme, colorare una forma rettangolare e salvare il documento come docx in pochi
  minuti.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: it
lastmod: 2026-08-23
og_description: Crea un documento Word vuoto con Aspose.Words per Java, quindi scopri
  come raggruppare le forme, colorare una forma rettangolare e salvare il documento
  come docx in modo efficiente.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Crea un documento Word vuoto e raggruppa le forme in Java – guida passo
  passo
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Crea un documento Word vuoto e raggruppa le forme in Java
url: /it/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word vuoto e raggruppa forme in Java

Se hai bisogno di **creare documento Word vuoto** programmaticamente, Aspose.Words per Java lo rende semplice. Questo tutorial ti mostra esattamente come **creare documento Word vuoto**, inserire un **group shapes in Word**, applicare **color rectangle shape**, e infine **save document as docx**. Alla fine avrai uno snippet di codice riutilizzabile da inserire in qualsiasi progetto Java.

Imparerai:

* La dipendenza Maven/Gradle necessaria per Aspose.Words.
* Come istanziare un documento vuoto e un `DocumentBuilder`.
* I passaggi esatti per **how to group shapes** all'interno di un `GroupShape`.
* Come impostare i colori di riempimento sulle forme rettangolari.
* La migliore pratica per **save document as docx** e dove trovare il file di output.

Non è richiesto alcun precedente esperienza con Aspose.Words, ma dovresti sentirti a tuo agio con lo sviluppo Java di base e avere installato un JDK 8 o successivo.

---

## Prerequisiti

| Requisito | Versione / Dettaglio |
|-----------|----------------------|
| Java Development Kit | 8 or higher |
| Strumento di build | Maven 3+ or Gradle 6+ |
| Aspose.Words for Java | 23.12 or later (the latest version at the time of writing) |
| IDE (opzionale) | IntelliJ IDEA, Eclipse, VS Code, or any Java‑compatible editor |

---

## Passo 1: Aggiungi Aspose.Words al tuo progetto

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Consiglio professionale:** Se utilizzi un proxy aziendale, configura Maven/Gradle per scaricare il pacchetto dal repository Aspose come descritto nella documentazione ufficiale.

---

## Passo 2: **Create blank Word document** con un builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Il costruttore `Document` crea un contenitore `.docx` vuoto in memoria. Il `DocumentBuilder` ti offre un'API fluida per aggiungere contenuti, incluse le forme.

---

## Passo 3: Inserisci un contenitore **group shapes in Word**

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

Un `GroupShape` funziona come un mini‑canvas. Tutte le forme aggiunte ad esso si muovono insieme, il che è esattamente **how to group shapes** per la coerenza del layout.

---

## Passo 4: Aggiungi la prima **color rectangle shape** (red)

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

La costante `ShapeType.RECTANGLE` crea un rettangolo semplice. Chiamando `getFill().setForeColor(...)` controlli la **color rectangle shape**. Puoi sostituire `java.awt.Color.RED` con qualsiasi costante `java.awt.Color` o valore RGB personalizzato.

---

## Passo 5: Aggiungi la seconda **color rectangle shape** (green) e posizionala

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Impostare `setLeft` (o `setTop`) sposta la forma rispetto all'angolo in alto a sinistra del contenitore **group shapes in Word**. Questo dimostra **how to group shapes** con posizionamento preciso.

---

## Passo 6: **Save document as docx** e verifica il risultato

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Il metodo `save` scrive automaticamente un file `.docx` perché l'estensione del file è `.docx`. Se ti serve un formato diverso (ad esempio PDF), passa l'enum `SaveFormat` appropriato.

> **Suggerimento:** Assicurati che la directory di destinazione (`output/` in questo esempio) esista o creala programmaticamente con `new File("output").mkdirs();`.

---

## Codice sorgente completo per copia‑incolla veloce

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Output previsto:** Aprendo `GroupShapeDemo.docx` in Microsoft Word si vede una singola pagina contenente due rettangoli colorati (rosso a sinistra, verde a destra) che si muovono insieme quando selezioni il gruppo.

---

## Domande comuni e gestione dei casi limite

| Domanda | Risposta |
|----------|----------|
| *Posso aggiungere più di due forme allo stesso gruppo?* | Sì. Chiama `groupShape.appendChild(yourShape)` per ogni forma aggiuntiva. Il gruppo ridimensionerà automaticamente per adattarsi alle estremità più lontane, oppure puoi regolare manualmente la sua larghezza/altezza. |
| *E se ho bisogno di un tipo di forma diverso (ad esempio ellisse)?* | Sostituisci `ShapeType.RECTANGLE` con `ShapeType.ELLIPSE`. Si applica la stessa logica di colore di riempimento. |
| *Devo rilasciare l'oggetto `Document`?* | Aspose.Words gestisce internamente le risorse native. Quando la JVM termina, le risorse vengono rilasciate. Per applicazioni a lungo termine, chiama `doc.dispose();` se utilizzi la versione **Aspose.Words for Java (Native)**. |
| *Come cambio l'ordine Z in modo che un rettangolo appaia sopra?* | Usa `groupShape.insertAfter(shape, referenceShape);` o `groupShape.insertBefore(shape, referenceShape);` per riordinare i figli all'interno del gruppo. |
| *Posso raggruppare forme tra sezioni diverse?* | No. Un `GroupShape` deve trovarsi all'interno di un singolo paragrafo o contenitore di forme. Per raggruppare tra sezioni, crea gruppi separati in ogni sezione. |

---

## Conclusione

Ora sai come **create blank Word document** con Aspose.Words per Java, **group shapes in Word**, applicare lo stile **color rectangle shape**, e **save document as docx**. Questo modello si scala a layout più complessi—basta aggiungere forme aggiuntive, regolare gli offset e, facoltativamente, impostare testo, immagini o collegamenti ipertestuali all'interno del gruppo.

**Passi successivi** che potresti esplorare:

* Usa **group shapes in Word** per creare diagrammi di flusso o mock‑up UI.
* Sperimenta con **save document as docx** combinato con la conversione PDF (`doc.save("out.pdf")`).
* Applica gradienti o motivi alla **color rectangle shape** per un design visivo più ricco.
* Combina forme raggruppate con tabelle o grafici per documenti di reporting avanzati.

Sentiti libero di modificare le dimensioni, i colori o i tipi di forma per adattarli al branding del tuo progetto. Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Come salvare documento come pdf con Aspose.Words per Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Utilizzare forme del documento in Aspose.Words per Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}