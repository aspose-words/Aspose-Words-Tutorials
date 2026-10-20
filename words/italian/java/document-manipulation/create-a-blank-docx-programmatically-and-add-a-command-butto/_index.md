---
category: general
date: 2026-10-20
description: Crea un file DOCX vuoto programmaticamente e incorpora un pulsante di
  comando usando Java. Scopri il codice completo per creare un documento Word, salvarlo
  con il pulsante e impostare la didascalia del pulsante di comando.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank docx programmatically
- create word document code
- save word with button
- add command button word
- set command button caption
language: it
lastmod: 2026-10-20
og_description: Crea un documento DOCX vuoto programmaticamente e incorpora un pulsante
  di comando. Segui questa guida passo‑passo in Java per salvare Word con il pulsante
  e impostare la didascalia del pulsante di comando.
og_image_alt: Screenshot of a blank DOCX file with an inserted command button created
  programmatically
og_title: Crea un documento DOCX vuoto programmaticamente – aggiungi un pulsante di
  comando
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  headline: Create a blank DOCX programmatically and add a command button
  type: TechArticle
- description: Create a blank DOCX programmatically and embed a command button using
    Java. Learn the full create word document code to save Word with button and set
    command button caption.
  name: Create a blank DOCX programmatically and add a command button
  steps:
  - name: Initialize a new blank document
    text: A blank document is the canvas on which you’ll place the command button.
      Aspose.Words provides the `Document` class for this purpose.
  - name: Set up a `DocumentBuilder`
    text: '`DocumentBuilder` is a helper that lets you insert content, including OLE
      controls, without dealing with low‑level node manipulation.'
  - name: Insert an OLE command button
    text: Word treats interactive controls as OLE (Object Linking and Embedding) objects.
      Aspose.Words exposes `Forms2OleControl` for this.
  - name: Configure the button – type, caption, and location
    text: You must define the control’s type (`COMMANDBUTTON`), set a user‑visible
      caption, and place it on the page.
  - name: Save the document with the embedded button
    text: Finally, write the file to disk. The resulting file can be opened in Microsoft
      Word, where the button will be fully functional.
  - name: Expected result
    text: 'When you open `CommandButton.docx` in Microsoft Word:'
  type: HowTo
tags:
- Java
- DOCX
- Aspose.Words
- Command button
- Automation
title: Crea un file DOCX vuoto programmaticamente e aggiungi un pulsante di comando
url: /it/java/document-manipulation/create-a-blank-docx-programmatically-and-add-a-command-butto/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento DOCX vuoto programmaticamente e aggiungi un pulsante di comando

Se hai bisogno di **creare un documento DOCX vuoto programmaticamente**, questo tutorial ti mostra come incorporare un pulsante di comando direttamente nel file. Otterrai il completo *create word document code* che salva un documento Word con un pulsante, ti permette di **set command button caption**, e funziona con l'ultima libreria Aspose.Words for Java.

Incorporare controlli interattivi in un file DOCX è utile quando vuoi distribuire modelli che attivano macro, avviano programmi esterni, o semplicemente guidano gli utenti con un pulsante cliccabile “Click Me”. I passaggi seguenti coprono tutto, dall'inizializzazione di un documento vuoto alla persistenza del file finale su disco.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versione più recente installata.  
* Maven (o lo strumento di build preferito) per gestire le dipendenze.  
* Aspose.Words for Java 23.9 o successivo. Aggiungi la dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

* Un IDE come IntelliJ IDEA o VS Code (qualsiasi editor che supporti Java va bene).

## Crea un documento DOCX vuoto programmaticamente – passo‑per‑passo

Le sezioni seguenti suddividono il processo in passaggi chiari e numerati. Ogni passo spiega **perché** è necessario, non solo **cosa** digitare.

### Passo 1: Inizializza un nuovo documento vuoto

Un documento vuoto è la tela su cui inserirai il pulsante di comando. Aspose.Words fornisce la classe `Document` a questo scopo.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

*Why this matters*: Iniziare con un `Document` vuoto garantisce che nessuna formattazione nascosta o controllo esistente interferisca con il pulsante che aggiungerai in seguito.

### Passo 2: Configura un `DocumentBuilder`

`DocumentBuilder` è un helper che ti consente di inserire contenuti, inclusi controlli OLE, senza dover gestire la manipolazione a basso livello dei nodi.

```java
        // Step 2: Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Why this matters*: Il builder mantiene la posizione corrente del cursore, così il pulsante verrà posizionato esattamente dove lo specifichi.

### Passo 3: Inserisci un pulsante di comando OLE

Word tratta i controlli interattivi come oggetti OLE (Object Linking and Embedding). Aspose.Words espone `Forms2OleControl` per questo.

```java
        // Step 3: Insert an OLE command button into the document
        com.aspose.words.forms.Forms2OleControl commandButton = builder.insertForms2OleControl();
```

*Why this matters*: L'inserimento del controllo crea un segnaposto che potrai configurare in seguito (tipo, didascalia, posizione).

### Passo 4: Configura il pulsante – tipo, didascalia e posizione

Devi definire il tipo del controllo (`COMMANDBUTTON`), impostare una didascalia visibile all'utente e posizionarlo nella pagina.

```java
        // Step 4: Configure the command button's type, caption, and position
        commandButton.setOleControlType(com.aspose.words.forms.OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");               // set command button caption
        commandButton.setLeft(100);                         // distance from the left margin (points)
        commandButton.setTop(200);                          // distance from the top margin (points)
```

*Why this matters*:  
* **Type** indica a Word che il controllo si comporta come un pulsante cliccabile.  
* **Caption** è il testo che l'utente vede; modificarla è il modo per **set command button caption**.  
* **Left** e **Top** controllano il posizionamento preciso, fondamentale quando **add command button word** documenti richiedono layout accurati.

### Passo 5: Salva il documento con il pulsante incorporato

Infine, scrivi il file su disco. Il file risultante può essere aperto in Microsoft Word, dove il pulsante sarà pienamente funzionale.

```java
        // Step 5: Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

*Why this matters*: Questo passo **saves Word with button** così il controllo persiste su tutte le macchine. Il file può essere distribuito come modello o usato in pipeline di generazione automatica di report.

## Esempio completo funzionante

Copia l'intera classe qui sotto in un file chiamato `CommandButtonDemo.java`, imposta `YOUR_DIRECTORY` su un percorso reale e eseguilo con `mvn compile exec:java`.

```java
import com.aspose.words.Document;
import com.aspose.words.DocumentBuilder;
import com.aspose.words.forms.Forms2OleControl;
import com.aspose.words.forms.OleControlType;

public class CommandButtonDemo {
    public static void main(String[] args) throws Exception {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert an OLE command button into the document
        Forms2OleControl commandButton = builder.insertForms2OleControl();

        // Configure the command button
        commandButton.setOleControlType(OleControlType.COMMANDBUTTON);
        commandButton.setCaption("Click Me");   // set command button caption
        commandButton.setLeft(100);             // points from left margin
        commandButton.setTop(200);              // points from top margin

        // Save the document with the embedded command button
        String outputPath = "YOUR_DIRECTORY/CommandButton.docx";
        document.save(outputPath);
        System.out.println("Document saved to: " + outputPath);
    }
}
```

### Risultato atteso

Quando apri `CommandButton.docx` in Microsoft Word:

* Il documento è completamente vuoto eccetto per un pulsante etichettato **Click Me**.  
* Cliccando il pulsante verrà visualizzato il comportamento predefinito di Word (non fa nulla a meno che non sia associata una macro), confermando che il controllo OLE è stato incorporato correttamente.

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|--------|
| **Posso cambiare la dimensione del pulsante?** | Sì. Usa `commandButton.setWidth(double)` e `commandButton.setHeight(double)` per regolare le dimensioni in punti. |
| **E se ho bisogno di una macro collegata al pulsante?** | Il pulsante è solo un controllo OLE. Devi aggiungere manualmente una macro VBA al documento o tramite le utility `addMacro` dell'API `Document` di Aspose.Words. |
| **Il pulsante funziona in LibreOffice?** | LibreOffice supporta controlli OLE limitati. Il pulsante appare, ma il suo comportamento al click può differire. |
| **Come aggiungere più pulsanti?** | Ripeti i Passi 3‑4 con una nuova istanza di `Forms2OleControl`. Regola `setLeft`/`setTop` per ogni pulsante per evitare sovrapposizioni. |
| **Il codice è compatibile con .NET?** | La stessa logica si applica, ma utilizzeresti le classi di `Aspose.Words` per .NET (`Document`, `DocumentBuilder`, `Forms2OleControl`). |

## Consigli pratici

* **Pro tip:** Usa `builder.moveToDocumentEnd()` prima di inserire il pulsante se vuoi posizionarlo alla fine del documento, indipendentemente dal contenuto precedente.  
* **Attenzione a:** Valori molto piccoli di `Left`/`Top` possono posizionare il pulsante fuori dall'area stampabile, rendendolo invisibile nella visualizzazione layout di Word.  
* **Nota sulle prestazioni:** Inserire molti controlli OLE può aumentare la dimensione del file. Se ti serve solo un'indicazione visiva, considera l'uso di una semplice `Shape` con un hyperlink.

## Conclusione

Ora sai come **create a blank DOCX programmatically** e incorporare un pulsante di comando pienamente funzionante usando Java. Il tutorial ha coperto l'intero flusso di lavoro *create word document code*, ha mostrato come **save Word with button**, ha illustrato il modo corretto per **add command button word** e ha spiegato come **set command button caption**.

Da qui puoi:

* Aggiungere altri controlli OLE (checkbox, combo box) per moduli più ricchi.  
* Collegare macro VBA per far eseguire al pulsante azioni personalizzate.  
* Combinare questa tecnica con la stampa unione per modelli dinamici e interattivi.

Sentiti libero di sperimentare con stili di pulsante, posizioni e controlli aggiuntivi per soddisfare le tue specifiche esigenze aziendali. Buon coding.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑per‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci alternativi nei tuoi progetti.

- [Crea un documento Word vuoto con un pulsante di comando – guida passo‑per‑passo](/words/english/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/)
- [Come inserire un pulsante ActiveX in Word – Imposta la didascalia del pulsante](/words/english/java/using-document-elements/how-to-insert-activex-button-in-word-set-button-caption/)
- [Crea un documento Word vuoto con Java – Guida completa Aspose.Words](/words/english/java/document-loading-and-saving/create-blank-word-document-with-java-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}