---
category: general
date: 2026-07-29
description: 'Tutorial Java per impostare la dimensione del pulsante: impara come
  inserire un pulsante di comando ActiveX in un documento Word usando Java e Aspose.Words,
  oltre al dimensionamento e alla creazione di un documento vuoto.'
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set button size java
- how to insert activex
- how to set button
- java create blank word
- insert command button word
language: it
lastmod: 2026-07-29
og_description: La guida su come impostare la dimensione del pulsante in Java mostra
  come inserire un pulsante di comando ActiveX in un file Word usando Java, regolarne
  le dimensioni e salvare il documento programmaticamente.
og_image_alt: set button size java example showing a Word document with an ActiveX
  command button
og_title: Imposta dimensione pulsante Java – Aggiungi pulsante di comando ActiveX
  a Word con Java
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  headline: set button size java – Insert ActiveX Command Button in Word
  type: TechArticle
- description: 'set button size java tutorial: learn how to insert ActiveX command
    button in a Word document using Java and Aspose.Words, plus sizing and blank document
    creation.'
  name: set button size java – Insert ActiveX Command Button in Word
  steps:
  - name: 1. Set Up the Project and Import Aspose.Words
    text: 'First, create a new Maven (or Gradle) project and add the Aspose.Words
      dependency shown above. Then, import the required classes in your Java source
      file:'
  - name: 2. java create blank word Document
    text: Now we actually **java create blank word** document. This is the foundation
      on which we’ll later **insert command button word**.
  - name: 3. Initialize DocumentBuilder and Insert the ActiveX Control
    text: 'The `DocumentBuilder` is a helper that lets us add content, paragraphs,
      tables, and, yes, ActiveX controls. Here’s where we answer **how to insert activex**:'
  - name: 4. How to Set Button Size Java – Adjust Width and Height
    text: 'Now comes the heart of the tutorial: **how to set button size java**. The
      control exposes several layout properties—`Left`, `Top`, `Width`, and `Height`.
      Setting them directly controls the button’s appearance on the page.'
  - name: 5. Save the Document
    text: 'Finally, persist the document to disk:'
  - name: What if the button doesn’t appear in Word?
    text: '- **Check the Word version.** ActiveX controls require the desktop version
      of Word; Word Online strips them out. - **Make sure the Aspose.Words license
      is applied** (if you’re using a paid edition). An unlicensed evaluation version
      may embed a watermark but still shows the control.'
  - name: Can I change the button’s font or color?
    text: Yes. After inserting the control, you can access its underlying OLE object
      and manipulate the VBA properties. That’s a more advanced topic—look into `commandButton.getOleObject().setProperty("ForeColor",
      0xFF0000)` for a red caption, for example.
  - name: How do I handle the button’s click event?
    text: ActiveX command buttons fire a VBA `Click` event. To make the button functional,
      you’ll need to embed a macro in the same document. Aspose.Words can add a macro
      module via the `Document.getMacros()` API, but the macro code itself must be
      written in VBA.
  - name: What about different button types?
    text: 'Aspose.Words supports many `Forms2OleControlType` values: `CHECKBOX`, `OPTIONBUTTON`,
      `LISTBOX`, etc. Swap the enum constant in the `insertForms2OleControl` call
      to experiment.'
  type: HowTo
tags:
- Java
- Aspose.Words
- ActiveX
- Word Automation
title: Imposta dimensione pulsante Java – Inserisci pulsante di comando ActiveX in
  Word
url: /it/java/using-document-elements/set-button-size-java-insert-activex-command-button-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set button size java – Inserire un pulsante di comando ActiveX in Word

Ti sei mai chiesto **how to set button size java** quando automatizzi i documenti Word? Forse stai creando uno strumento di reporting che necessita di un pulsante “Submit” cliccabile direttamente nel file .docx. In questo tutorial percorreremo l'intero processo—creare un documento Word vuoto, inserire un pulsante di comando ActiveX e impostare esplicitamente la sua larghezza e altezza—tutto con Java e Aspose.Words.

Risponderemo anche alla persistente domanda “how to insert activex” che molti sviluppatori si pongono. Alla fine avrai un programma eseguibile che produce un file Word contenente un pulsante di comando perfettamente dimensionato, pronto per ulteriori personalizzazioni.

---

## Cosa ti serve

- **Java Development Kit (JDK) 8 o più recente** – il codice si compila con qualsiasi JDK recente.
- **Aspose.Words for Java** (l'ultima versione a partire da luglio 2026). Scarica il JAR dal [sito Aspose](https://products.aspose.com/words/java) o tramite Maven:
  ```xml
  <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.10</version>
  </dependency>
  ```
- Un IDE o un semplice editor di testo—IntelliJ IDEA, Eclipse o VS Code vanno bene.
- Una cartella dove desideri che il file **CommandButton.docx** generato venga salvato.

È tutto. Nessuna libreria Office interop aggiuntiva, nessun trucco COM, solo puro Java.

---

## Implementazione passo‑passo

Divideremo la soluzione in cinque passaggi logici. Ogni passaggio ha un'intestazione H2 dedicata; uno di essi contiene la nostra **primary keyword** per soddisfare la SEO.

### 1. Configurare il progetto e importare Aspose.Words

Per prima cosa, crea un nuovo progetto Maven (o Gradle) e aggiungi la dipendenza Aspose.Words mostrata sopra. Poi, importa le classi necessarie nel tuo file sorgente Java:

```java
import com.aspose.words.*;
```

> **Suggerimento:** Se usi un IDE, lascia che importi automaticamente le classi. Risparmia molto tempo di digitazione e previene errori di battitura.

### 2. java create blank word Document

Ora creiamo effettivamente il documento **java create blank word**. Questa è la base su cui più tardi **insert command button word**.

```java
// Step 2: Create a new blank document
Document document = new Document();          // Starts with a clean, empty .docx
```

L'oggetto `Document` rappresenta l'intero file Word in memoria. A questo punto il file non ha pagine, né testo—solo una tela pulita.

### 3. Inizializzare DocumentBuilder e inserire il controllo ActiveX

Il `DocumentBuilder` è un helper che ci permette di aggiungere contenuti, paragrafi, tabelle e, sì, controlli ActiveX. Qui rispondiamo a **how to insert activex**:

```java
// Step 3: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert an ActiveX command button (COMMANDBUTTON is a built‑in type)
Forms2OleControl commandButton = builder.insertForms2OleControl(
        Forms2OleControlType.COMMANDBUTTON);
```

`Forms2OleControl` è il wrapper di Aspose attorno a un oggetto OLE. Specificando `COMMANDBUTTON` indichiamo a Word di incorporare un classico pulsante di comando ActiveX.

### 4. How to Set Button Size Java – Regolare larghezza e altezza

Ora arriva il cuore del tutorial: **how to set button size java**. Il controllo espone diverse proprietà di layout—`Left`, `Top`, `Width` e `Height`. Impostandole direttamente si controlla l'aspetto del pulsante nella pagina.

```java
// Step 4: Set button properties, including size
commandButton.setCaption("Click Me"); // Text shown on the button
commandButton.setLeft(100);           // Distance from the left margin (points)
commandButton.setTop(200);            // Distance from the top margin (points)
commandButton.setWidth(120);          // Width in points (≈1.67 inches)
commandButton.setHeight(30);          // Height in points (≈0.42 inches)
```

Perché questi numeri? In Word, un punto corrisponde a 1/72 di pollice. Quindi una larghezza di `120` punti si traduce in circa 1,67 pollici—sufficiente per un'etichetta leggibile, ma non eccessiva. Regola i valori per adattarli al tuo layout; le stesse proprietà rispondono anche alla domanda **how to set button** che potresti avere.

> **Nota:** Se ti serve un tipo di pulsante diverso (ad esempio, una casella di controllo), sostituisci `Forms2OleControlType.COMMANDBUTTON` con il valore enum appropriato.

### 5. Salvare il documento

Infine, salva il documento su disco:

```java
// Step 5: Save the document with the embedded ActiveX control
document.save("YOUR_DIRECTORY/CommandButton.docx");
```

Sostituisci `YOUR_DIRECTORY` con un percorso assoluto o relativo sulla tua macchina. Dopo aver eseguito il programma, apri il file generato in Microsoft Word. Vedrai un pulsante etichettato “Click Me” posizionato a 100 pts dalla sinistra e 200 pts dall'alto, dimensionato esattamente come impostato.

---

## Esempio completo funzionante

Di seguito la classe Java completa, pronta per l'esecuzione. Copiala e incollala in `CommandButtonActiveX.java`, regola il percorso di output e premi **Run**.

```java
import com.aspose.words.*;

public class CommandButtonActiveX {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document (java create blank word)
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to work with the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert an ActiveX command button (how to insert activex)
        Forms2OleControl commandButton = builder.insertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON);

        // Step 4: Set button properties – this is how to set button size java
        commandButton.setCaption("Click Me"); // Button text
        commandButton.setLeft(100);           // Left position (points)
        commandButton.setTop(200);            // Top position (points)
        commandButton.setWidth(120);          // Width (points)
        commandButton.setHeight(30);          // Height (points)

        // Step 5: Save the document (insert command button word)
        document.save("YOUR_DIRECTORY/CommandButton.docx");
    }
}
```

**Output previsto:** Aprendo `CommandButton.docx` in Word si visualizza una singola pagina con un pulsante cliccabile “Click Me” posizionato più o meno al centro della pagina. Le dimensioni del pulsante corrispondono ai valori impostati, confermando che **set button size java** funziona come previsto.

---

## Domande comuni e casi particolari

### E se il pulsante non appare in Word?

- **Verifica la versione di Word.** I controlli ActiveX richiedono la versione desktop di Word; Word Online li rimuove.
- **Assicurati che la licenza Aspose.Words sia applicata** (se utilizzi un'edizione a pagamento). Una versione di valutazione non licenziata può inserire una filigrana ma mostra comunque il controllo.

### Posso cambiare il font o il colore del pulsante?

Sì. Dopo aver inserito il controllo, puoi accedere al suo oggetto OLE sottostante e manipolare le proprietà VBA. È un argomento più avanzato—ad esempio, guarda `commandButton.getOleObject().setProperty("ForeColor", 0xFF0000)` per una didascalia rossa.

### Come gestire l'evento click del pulsante?

I pulsanti di comando ActiveX generano un evento VBA `Click`. Per rendere il pulsante funzionale, dovrai incorporare una macro nello stesso documento. Aspose.Words può aggiungere un modulo macro tramite l'API `Document.getMacros()`, ma il codice della macro deve essere scritto in VBA.

### E per i diversi tipi di pulsante?

Aspose.Words supporta molti valori `Forms2OleControlType`: `CHECKBOX`, `OPTIONBUTTON`, `LISTBOX`, ecc. Sostituisci la costante enum nella chiamata `insertForms2OleControl` per sperimentare.

---

## Suggerimenti professionali per codice pronto alla produzione

- **Usa costanti per i valori di layout** – rende più facili le future modifiche.
- **Avvolgi il percorso di salvataggio in un oggetto `Path`** per evitare separatori specifici della piattaforma.
- **Rilascia il Document** (o usa try‑with‑resources) se stai elaborando molti file in un ciclo.
- **Convalida la cartella di output** prima di chiamare `save` per evitare `FileNotFoundException`.

---

## Conclusione

Hai appena imparato **set button size java** creando un file Word vuoto, inserendo un pulsante di comando ActiveX e configurando con precisione le sue dimensioni—tutto con poche righe di codice Java. Questo copre il nucleo di **how to insert activex**, **how to set button**, **java create blank word** e **insert command button word** in un unico esempio autonomo.

Prossimi passi? Prova a personalizzare la didascalia del pulsante, aggiungere una macro per rispondere ai click, o incorporare più controlli nella stessa pagina. Potresti anche esplorare la conversione del .docx risultante in PDF con Aspose.Words, preservando il pulsante come immagine statica.

Sentiti libero di sperimentare, e se incontri un problema, lascia un commento qui sotto. Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completo e funzionante con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuti usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Come caricare documenti Word con Aspose.Words Java: Guida completa](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Come salvare un documento come PDF con Aspose.Words per Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}