---
category: general
date: 2026-11-22
description: Crea un pulsante macro in un documento Word usando Java. Impara a inserire
  un pulsante di comando, impostare il testo del pulsante e collegare la macro al
  pulsante per documenti interattivi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create macro button
- insert command button
- set button text
- link macro to button
- add interactive button
language: it
lastmod: 2026-11-22
og_description: Crea un pulsante macro in un documento Word usando Java. Questo tutorial
  mostra come inserire un pulsante di comando, impostare il testo del pulsante e collegare
  la macro al pulsante per un'interattività completa.
og_image_alt: Screenshot of a Word document showing a macro button created with Java
  code
og_title: Crea un pulsante macro in un documento Word con Java – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  headline: How to create macro button in a Word document with Aspose.Words for Java
  type: TechArticle
- description: Create macro button in a Word document using Java. Learn to insert
    command button, set button text, and link macro to button for interactive documents.
  name: How to create macro button in a Word document with Aspose.Words for Java
  steps:
  - name: Insert command button into the document
    text: '`DocumentBuilder.insertForms2OleControl` creates an OLE control of the
      specified type. The `Forms2OleControlType.COMMAND_BUTTON` constant tells Aspose.Words
      to generate a command button that can host a macro.'
  - name: Set button text (caption)
    text: The caption is the visible label on the button. Use `setCaption` to define
      what the user sees.
  - name: Link macro to button
    text: A macro is identified by its name, for example `MyMacro`. The `setOnClick`
      method stores this name in the button’s `OnClick` event handler.
  - name: Add interactive button to a Word document
    text: After configuring the OLE control, you may want to position it, resize it,
      or add surrounding text. The `DocumentBuilder` continues to operate on the document,
      so you can insert paragraphs before or after the button.
  - name: Expected output
    text: 'Running the program generates `MacroButtonDemo.docm`. Opening the file
      in Microsoft Word shows:'
  type: HowTo
tags:
- Aspose.Words
- Java
- OLE controls
- Automation
title: Come creare un pulsante macro in un documento Word con Aspose.Words per Java
url: /it/java/using-document-elements/how-to-create-macro-button-in-a-word-document-with-aspose-wo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un pulsante macro in un documento Word con Aspose.Words per Java

Se hai bisogno di **creare un pulsante macro** in un file Word, questa guida ti accompagna passo passo attraverso le operazioni necessarie. Imparerai come **inserire un pulsante di comando**, **impostare il testo del pulsante** e **collegare la macro al pulsante** affinché il documento diventi completamente interattivo.

Gli sviluppatori spesso incorporano controlli OLE per attivare macro VBA all'interno di un documento. Questo tutorial copre l'intero flusso di lavoro, dalla configurazione del progetto a un esempio Java eseguibile che aggiunge un **pulsante interattivo** a un file .docx. Non sono necessari script esterni—tutto viene eseguito all'interno del processo Java.

## Prerequisiti

* JDK 17 o versioni successive installato.
* Maven 3.8+ (o Gradle) per la gestione delle dipendenze.
* Aspose.Words per Java 23.9 o più recente – la libreria fornisce le API `DocumentBuilder` e OLE control.
* Familiarità di base con Java e macro VBA.

Se uno di questi elementi manca, installalo prima; il resto del tutorial presuppone che siano disponibili.

## Come creare un pulsante macro con Aspose.Words per Java

Il nucleo della soluzione consiste in quattro azioni:

1. **Inserire un pulsante di comando** OLE control nel documento.
2. **Impostare il testo del pulsante** (didascalia) che l'utente vede.
3. **Collegare la macro al pulsante** in modo che il click esegua la routine VBA desiderata.
4. **Salvare il documento** con la macro incorporata.

Ogni azione è spiegata nella propria sezione di seguito.

### Passo 1: Inserire un pulsante di comando nel documento

```java
import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load a blank document or create a new one
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);
```

**Perché è importante:** Il controllo OLE funge da contenitore per la macro. Senza inserirlo, non c'è alcun elemento visivo su cui l'utente possa fare clic.

### Passo 2: Impostare il testo del pulsante (didascalia)

```java
        // Set the button's caption – this is the text displayed on the button
        commandButton.setCaption("Run Report");
```

**Perché è importante:** Un testo chiaro del pulsante migliora l'usabilità. Il metodo `setCaption` aggiorna la proprietà `Caption` del controllo OLE, che Word visualizza come etichetta del pulsante.

### Passo 3: Collegare la macro al pulsante

```java
        // Assign a macro to run when the button is clicked
        commandButton.setOnClick("MyMacro");
```

**Perché è importante:** Collegare una macro crea il comportamento interattivo. Quando l'utente fa clic sul pulsante in Word, viene eseguita la routine VBA associata.

### Passo 4: Aggiungere un pulsante interattivo a un documento Word

Dopo aver configurato il controllo OLE, potresti volerlo posizionare, ridimensionare o aggiungere testo circostante. Il `DocumentBuilder` continua a operare sul documento, così puoi inserire paragrafi prima o dopo il pulsante.

```java
        // Add a descriptive paragraph before the button
        builder.moveToDocumentStart();
        builder.writeln("Click the button below to generate the report:");

        // Move the cursor back to the button location (optional)
        builder.moveTo(commandButton.getNode());

        // Optionally, resize the button (width and height in points)
        commandButton.setWidth(120);
        commandButton.setHeight(30);

        // Save the document with the macro-enabled format
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

**Perché è importante:** Salvare come `.docm` preserva il codice della macro. Se salvi come `.docx`, il riferimento alla macro viene perso.

## Esempio completo eseguibile

Di seguito è riportato il programma Java completo, inclusi import, gestione delle eccezioni e commenti che spiegano ogni passaggio. Copia il codice in un progetto Maven con la dipendenza Aspose.Words e eseguilo.

```java
// Maven dependency (add to pom.xml):
// <dependency>
//   <groupId>com.aspose</groupId>
//   <artifactId>aspose-words</artifactId>
//   <version>23.9</version>
// </dependency>

import com.aspose.words.*;

public class MacroButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new empty document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder to edit the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Write an introductory paragraph
        builder.writeln("Press the button to execute the macro:");

        // 4. Insert the command button OLE control
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMAND_BUTTON);

        // 5. Set the visual caption of the button
        commandButton.setCaption("Run Report");

        // 6. Link the button to a VBA macro named MyMacro
        commandButton.setOnClick("MyMacro");

        // 7. Resize the button for better appearance
        commandButton.setWidth(120);   // points
        commandButton.setHeight(30);   // points

        // 8. Save the document as a macro‑enabled file
        doc.save("MacroButtonDemo.docm", SaveFormat.DOCM);
    }
}
```

### Output previsto

Eseguendo il programma si genera `MacroButtonDemo.docm`. Aprendo il file in Microsoft Word si vede:

* Un paragrafo che recita *“Premi il pulsante per eseguire la macro:”*.
* Un pulsante con etichetta **Run Report** direttamente sotto il paragrafo.
* Quando fai clic sul pulsante, Word tenta di eseguire la macro `MyMacro`. (Devi aggiungere il codice VBA reale al documento manualmente o tramite un altro passaggio di automazione.)

Se la macro non esiste, Word visualizza un avviso di sicurezza, comportamento standard per i documenti abilitati alle macro.

## Variazioni comuni e casi limite

| Scenario | Come adattare il codice |
|----------|------------------------|
| **Didascalia del pulsante diversa** | Cambia la stringa passata a `setCaption`. |
| **Pulsanti multipli** | Chiama `insertForms2OleControl` ripetutamente, ognuno con il proprio `setCaption` e `setOnClick`. |
| **Nomi macro personalizzati** | Sostituisci `"MyMacro"` con qualsiasi nome di procedura VBA valido, ad esempio `"ExportToExcel"`. |
| **Vincoli di dimensione del pulsante** | Regola i valori di `setWidth` e `setHeight`; Word rispetta i punti forniti. |
| **Incorporare la macro programmaticamente** | Usa `Document.getBuiltInDocumentProperties().add("Macros", …)` o un passaggio separato di iniezione VBA; Aspose.Words non scrive codice VBA direttamente. |

**Suggerimento professionale:** Testa sempre il `.docm` generato su una macchina con la sicurezza delle macro impostata su *Abilita tutte le macro* per lo sviluppo. In produzione, firma la macro con un certificato attendibile per evitare richieste di sicurezza.

## Checklist di risoluzione dei problemi

* **Il pulsante non appare** – Verifica che il documento sia salvato come `.docm` e aperto in una versione di Word che supporta i controlli OLE.
* **La macro non viene eseguita** – Assicurati che il nome della macro corrisponda esattamente, inclusa la maiuscola/minuscola, e che la macro esista nel progetto VBA del documento.
* **La didascalia del pulsante è troncata** – Aumenta la larghezza del pulsante usando `setWidth` per ospitare testo più lungo.
* **Spostamento inatteso del layout** – Usa `builder.moveTo` per posizionare il cursore con precisione prima di inserire il controllo.

## Conclusione

Ora sai come **creare un pulsante macro** in un documento Word usando Java, **inserire un pulsante di comando**, **impostare il testo del pulsante** e **collegare la macro al pulsante** per una piena interattività. L'esempio completo dimostra ogni chiamata API necessaria, spiega perché ogni passaggio è importante e fornisce indicazioni per le variazioni comuni.

Successivamente, potresti esplorare:

* **Aggiungere un pulsante interattivo** a template esistenti invece di un nuovo documento.
* **Iniettare codice VBA programmaticamente** usando l'Open XML SDK o uno strumento di automazione secondario.
* **Combinare più controlli OLE** (caselle di controllo, caselle di riepilogo) per creare moduli avanzati.

Sperimenta con didascalie diverse, nomi di macro e dimensioni del pulsante per adattarli al tuo caso d'uso specifico. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche illustrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come inserire un pulsante di comando in un documento Word usando Java](/words/english/java/using-document-elements/how-to-insert-command-button-in-a-word-document-using-java/)
- [Come impostare la posizione del pulsante in un documento Word con Java](/words/english/java/using-document-elements/how-to-set-button-position-in-a-word-document-with-java/)
- [Come inserire un pulsante ActiveX in Word – Impostare la didascalia del pulsante](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}