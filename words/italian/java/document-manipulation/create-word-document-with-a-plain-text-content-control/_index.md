---
category: general
date: 2026-10-04
description: Crea un documento Word usando Java che includa un controllo di contenuto
  di testo semplice e un segnaposto. Scopri come aggiungere il segnaposto al tag e
  come inserire sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: it
lastmod: 2026-10-04
og_description: Crea un documento Word con un controllo di contenuto di testo semplice
  e un segnaposto. Questo tutorial mostra come aggiungere un segnaposto al tag e come
  inserire un sdt utilizzando Aspose.Words per Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Crea documento Word con controllo dei contenuti – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Crea documento Word con un controllo di contenuto di testo semplice
url: /it/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word con un controllo di contenuto di testo semplice

Se hai bisogno di **creare documento Word** che contenga una regione modificabile dall'utente, un controllo di contenuto di testo semplice è l'approccio più affidabile. Questo tutorial mostra esattamente come inserire un Structured Document Tag (SDT), impostare un segnaposto e salvare il risultato come **docx con segnaposto**. Vedrai un esempio Java completo e eseguibile che funziona con Aspose.Words for Java 23.8.

La guida copre tutti i prerequisiti, spiega perché ogni chiamata API è importante e fornisce suggerimenti per gestire casi limite come segnaposti multilingue o tag nidificati. Alla fine potrai generare un file Word che invita gli utenti a “Enter text…” direttamente nel documento.

## Prerequisiti

* Java 17 (o successivo) installato e configurato nel tuo PATH.  
* Maven 3.8+ per gestire le dipendenze.  
* Una licenza Aspose.Words per Java (la versione di valutazione funziona per i test).  
* Un IDE di sviluppo (IntelliJ IDEA, Eclipse o VS Code).

Aggiungi Aspose.Words al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Crea documento Word con un controllo di contenuto di testo semplice

Il flusso di lavoro principale consiste in quattro passaggi logici. Ogni passaggio è racchiuso in un metodo con un nome chiaro, così puoi riutilizzare la logica in progetti più grandi.

### Passo 1: Inizializza il documento e il builder

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Perché è importante:** `Document` rappresenta il file Word in memoria. `DocumentBuilder` è l'API fluente che ti consente di inserire paragrafi, tabelle e SDT. Iniziare con un documento vuoto garantisce che il segnaposto appaia all'inizio, il che è utile per i modelli.

### Passo 2: Inserisci un Structured Document Tag (SDT) di testo semplice

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Perché è importante:** `StructuredDocumentTagType.PLAIN_TEXT` crea un controllo di contenuto che accetta solo caratteri semplici, evitando formattazioni accidentali. La chiamata `setPlaceholderName` popola il testo di suggerimento grigio che gli utenti vedono prima di digitare — questa è l'operazione **add placeholder to tag** che fa sembrare il documento come un modulo.

### Passo 3: Aggiungi contenuto regolare dopo l'SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Perché è importante:** Aggiungere contenuto dopo il controllo verifica che l'SDT non consumi l'intero flusso del documento. Dimostra anche come mescolare tag strutturati con paragrafi ordinari, una esigenza comune nella creazione di modelli.

### Passo 4: Salva il file risultante

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Perché è importante:** Il metodo `save` scrive il modello in memoria in un file fisico **docx con segnaposto**. Il file generato può essere aperto in Microsoft Word, LibreOffice o in qualsiasi libreria che supporti il formato OpenXML.

## Codice sorgente completo

Mettere insieme i pezzi ti fornisce un programma autonomo che puoi compilare ed eseguire:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Output previsto

Eseguendo il programma viene creato `SdtDemo.docx`. Aprendo il file in Word si vede:

* Un segnaposto grigio “Enter text…” all'interno di un controllo di contenuto di testo semplice etichettato **MyTag**.  
* La riga **After SDT** subito sotto il controllo.

Il segnaposto scompare non appena l'utente digita, preservando la formattazione originale.

## Varianti comuni e casi limite

| Scenario | Modifica consigliata |
|----------|----------------------|
| **Multilingual placeholder** | Usa caratteri Unicode in `setPlaceholderName`, ad esempio `sdt.setPlaceholderName("Введите текст…");`. |
| **Nested content controls** | Inserisci un secondo SDT all'interno del primo chiamando `builder.moveTo(sdt.getParagraph());` prima del secondo `insertStructuredDocumentTag`. |
| **Read‑only control** | Chiama `sdt.setLockContentControl(true);` per impedire agli utenti di eliminare il tag. |
| **Rich‑text instead of plain text** | Sostituisci `StructuredDocumentTagType.PLAIN_TEXT` con `StructuredDocumentTagType.RICH_TEXT`. |
| **Saving to a stream** | Usa `doc.save(OutputStream, SaveFormat.DOCX);` quando devi inviare il file via HTTP. |

## Consigli professionali

* **Reuse tag IDs** – Se generi molti documenti dallo stesso modello, mantieni il nome del tag (`"MyTag"`) coerente così l'elaborazione a valle (ad es., mail‑merge) può individuarlo in modo affidabile.  
* **Performance** – Per modelli di grandi dimensioni, crea il `DocumentBuilder` una sola volta e riutilizzalo; inserire molti SDT in un ciclo è più veloce che ricreare il builder ad ogni iterazione.  
* **Testing** – Dopo aver generato il DOCX, verifica programmaticamente che il segnaposto esista con `doc.getRange().getStructuredDocumentTags().getCount()`.

## Conclusione

Ora sai come **creare documento Word** che contenga un **controllo di contenuto di testo semplice** con un segnaposto personalizzato, producendo efficacemente un **docx con segnaposto** pronto per l'input dell'utente. L'esempio dimostra l'intero ciclo, dall'inizializzazione del documento, **how to insert sdt**, **add placeholder to tag**, aggiunta di contenuto regolare e infine il salvataggio del file.

### Passi successivi

* Esplora **how to insert sdt** all'interno di tabelle per layout simili a moduli.  
* Combina questa tecnica con l'unione di **docx con segnaposto** per creare generatori di report automatizzati.  
* Sperimenta con altri tipi di controllo (`RICH_TEXT`, `CHECKBOX`) per creare moduli Word più ricchi.

Sentiti libero di adattare il codice al tuo motore di template e condividi i tuoi risultati nei commenti!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crea documento Word Java – Aggiungi forma rettangolare con effetto ombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Come creare documenti PDF con Aspose.Words per Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}