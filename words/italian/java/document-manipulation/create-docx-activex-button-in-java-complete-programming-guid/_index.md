---
category: general
date: 2026-08-14
description: Crea un pulsante ActiveX in un file docx in Java con Aspose.Words. Scopri
  come aggiungere un pulsante modulo in Word programmaticamente e salvare il documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create docx ActiveX button
- add form button word
language: it
lastmod: 2026-08-14
og_description: Crea un pulsante ActiveX in un file docx in Java usando Aspose.Words.
  Questa guida ti mostra come aggiungere un pulsante modulo in Word, configurarlo
  e salvare il file.
og_image_alt: Screenshot of a Word document containing an ActiveX CommandButton created
  with Java
og_title: Crea pulsante ActiveX per docx in Java – tutorial passo‑passo
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  headline: Create docx ActiveX button in Java – complete programming guide
  type: TechArticle
- description: Create docx ActiveX button in Java with Aspose.Words. Learn how to
    add a form button in Word programmatically and save the document.
  name: Create docx ActiveX button in Java – complete programming guide
  steps:
  - name: Set up the project and import Aspose.Words
    text: 'Add the Aspose.Words dependency to your `pom.xml` if you use Maven:'
  - name: Create a new blank document
    text: Instantiate a `Document` object, which represents an empty Word file ready
      to receive content.
  - name: Initialize a DocumentBuilder
    text: '`DocumentBuilder` provides a fluent interface for inserting text, images,
      and controls. Attach it to the document you just created.'
  - name: Insert an ActiveX CommandButton control
    text: Use the `insertForms2OleControl` method to embed an ActiveX `CommandButton`.
      This method returns a `Forms2OleControl` instance that you can further configure.
  - name: Configure the button’s properties
    text: Set the control’s name, caption, and layout attributes. These values determine
      how the button appears in Word and how you can reference it later via VBA or
      automation scripts.
  - name: Save the document
    text: Finally, write the document to disk. Use the `.docx` extension to keep the
      file in the modern Office Open XML format.
  type: HowTo
tags:
- ActiveX
- Java
- Aspose.Words
- Word automation
title: Crea un pulsante ActiveX per docx in Java – guida completa alla programmazione
url: /it/java/document-manipulation/create-docx-activex-button-in-java-complete-programming-guid/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un docx ActiveX button in Java – guida completa di programmazione

Se hai bisogno di **create docx ActiveX button** in Java, questa guida ti accompagna passo passo attraverso l'intero processo. Vedrai come aggiungere un pulsante di modulo in Word, configurarne le proprietà e produrre un file .docx pronto all'uso.

Lavorare con i controlli ActiveX è una necessità comune quando si automatizzano i moduli Word legacy. In questo tutorial imparerai a **add form button word** documents usando la libreria Aspose.Words for Java, così potrai incorporare controlli interattivi senza modifiche manuali.

## Di cosa avrai bisogno

* Java 17 o versioni successive (il codice si compila con versioni precedenti, ma Java 17 è consigliato).
* Aspose.Words for Java 23.10 o più recente – scarica il JAR dal sito Aspose o aggiungi la dipendenza Maven.
* Un IDE (IntelliJ IDEA, Eclipse o VS Code) o un semplice editor di testo e strumenti di compilazione da riga di comando.
* Conoscenze di base della sintassi Java e della programmazione orientata agli oggetti.

## Come creare un docx ActiveX button con Aspose.Words

I passaggi seguenti mostrano la sequenza esatta necessaria per **create docx ActiveX button** objects e inserirli in un documento Word.

### Passo 1: Configura il progetto e importa Aspose.Words

Aggiungi la dipendenza Aspose.Words al tuo `pom.xml` se usi Maven:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Oppure, se preferisci Gradle:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

Dopo che la dipendenza è risolta, importa le classi necessarie nel tuo file sorgente Java:

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;
```

Queste importazioni ti danno accesso a `Document`, `DocumentBuilder` e all'API `Forms2OleControl` utilizzata per inserire controlli ActiveX.

### Passo 2: Crea un nuovo documento vuoto

Istanzia un oggetto `Document`, che rappresenta un file Word vuoto pronto a ricevere contenuti.

```java
// Step 2: Create a new blank document
Document document = new Document();
```

Creare prima il documento garantisce che il builder successivo operi su una tela pulita.

### Passo 3: Inizializza un DocumentBuilder

`DocumentBuilder` fornisce un'interfaccia fluida per inserire testo, immagini e controlli. Collegalo al documento appena creato.

```java
// Step 3: Initialize a DocumentBuilder to construct the document content
DocumentBuilder builder = new DocumentBuilder(document);
```

Il builder tiene traccia della posizione corrente del cursore all'interno del documento, così la prossima inserzione avviene esattamente dove ti serve.

### Passo 4: Inserisci un controllo ActiveX CommandButton

Usa il metodo `insertForms2OleControl` per incorporare un ActiveX `CommandButton`. Questo metodo restituisce un'istanza `Forms2OleControl` che puoi configurare ulteriormente.

```java
// Step 4: Insert an ActiveX CommandButton control into the document
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMAND_BUTTON);
```

A questo punto il file .docx contiene un segnaposto per un pulsante, ma non ha ancora alcuna didascalia o dimensione visiva.

### Passo 5: Configura le proprietà del pulsante

Imposta il nome del controllo, la didascalia e gli attributi di layout. Questi valori determinano come il pulsante appare in Word e come potrai riferirti ad esso in seguito tramite VBA o script di automazione.

```java
// Step 5: Configure the button's properties (name, caption, size, and position)
commandButton.setName("btnSubmit");          // internal name used by VBA
commandButton.setCaption("Submit");          // text shown on the button
commandButton.setTop(100);                  // distance from the top of the page (points)
commandButton.setLeft(150);                 // distance from the left margin (points)
commandButton.setWidth(80);                 // button width (points)
commandButton.setHeight(30);                // button height (points)
```

> **Consiglio professionale:** Word misura le posizioni in punti (1 pt ≈ 1/72 in). Regola `setTop` e `setLeft` per allineare il pulsante al contenuto circostante.

### Passo 6: Salva il documento

Infine, scrivi il documento su disco. Usa l'estensione `.docx` per mantenere il file nel moderno formato Office Open XML.

```java
// Step 6: Save the document containing the ActiveX button
String outputPath = "C:/temp/ActiveXButton.docx";
document.save(outputPath);
System.out.println("Document saved to " + outputPath);
```

Quando apri il file risultante in Microsoft Word, vedrai un pulsante **Submit** posizionato alle coordinate specificate. Cliccare il pulsante in Word non attiverà alcuna azione a meno che non alleghi del codice VBA, ma il controllo è pienamente funzionale per flussi di lavoro basati su moduli.

## Domande comuni e casi particolari

| Domanda | Risposta |
|----------|--------|
| **Ho bisogno di una versione speciale di Word?** | I controlli ActiveX sono supportati nella versione desktop di Microsoft Word su Windows. Non sono disponibili in Word per Mac o Word Online. |
| **Posso usarlo con file `.doc`?** | Sì. Salva il documento con estensione `.doc` (`document.save("ActiveXButton.doc")`). La stessa API funziona per il formato binario più vecchio. |
| **Cosa succede se il pulsante non appare?** | Assicurati che **File → Opzioni → Centro protezione → Impostazioni Centro protezione → Impostazioni ActiveX** consentano i controlli ActiveX. Verifica anche che il documento non sia aperto in “Visualizzazione protetta”. |
| **Posso aggiungere altri controlli ActiveX?** | Assolutamente. Sostituisci `Forms2OleControlType.COMMAND_BUTTON` con `Forms2OleControlType.CHECK_BOX`, `RADIO_BUTTON`, ecc. |
| **Esiste un limite di dimensioni?** | Le dimensioni del controllo sono limitate solo dal layout della pagina. Dimensioni molto grandi possono causare overflow del layout. |

## Esempio completo e eseguibile

Di seguito trovi una classe Java completa che puoi copiare, compilare ed eseguire. Include tutte le importazioni, il metodo `main` e commenti in linea per chiarezza.

```java
package com.example.wordactive;

import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.Forms2OleControlType;

public class ActiveXButtonDemo {
    public static void main(String[] args) {
        try {
            // Create a new blank document
            Document document = new Document();

            // Initialize DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(document);

            // Insert an ActiveX CommandButton control
            Forms2OleControl commandButton = builder.insertForms2OleControl(
                    Forms2OleControlType.COMMAND_BUTTON);

            // Configure button properties
            commandButton.setName("btnSubmit");
            commandButton.setCaption("Submit");
            commandButton.setTop(100);   // points from top
            commandButton.setLeft(150);  // points from left
            commandButton.setWidth(80);  // width in points
            commandButton.setHeight(30); // height in points

            // Save the document
            String outputPath = "ActiveXButton.docx";
            document.save(outputPath);
            System.out.println("Document saved successfully to " + outputPath);
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Risultato atteso:** Dopo aver eseguito il programma, `ActiveXButton.docx` appare nella directory di lavoro. Aprendolo in Microsoft Word verrà mostrato un pulsante **Submit** cliccabile posizionato vicino all'angolo in alto a sinistra della prima pagina.

## Conclusione

Ora sai come **create docx ActiveX button** objects in Java usando Aspose.Words, e hai visto come **add form button word** documents in modo programmatico. I passaggi — configurazione del progetto, creazione del documento, inserimento del controllo, configurazione delle proprietà e salvataggio — coprono l'intero flusso di lavoro dall'inizio alla fine.

Successivamente, potresti esplorare:

* Aggiungere macro VBA che rispondono al click del pulsante.
* Incorporare altri controlli ActiveX come caselle di controllo o caselle di riepilogo.
* Automatizzare la generazione di moduli multi‑pagina con diversi elementi interattivi.

Sentiti libero di sperimentare con dimensioni, posizioni e didascalie per soddisfare i requisiti specifici del tuo design di modulo. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [How to Load HTML and Save as DOCX using Aspose.Words for Java](/words/english/java/document-loading-and-saving/loading-and-saving-html-documents/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}