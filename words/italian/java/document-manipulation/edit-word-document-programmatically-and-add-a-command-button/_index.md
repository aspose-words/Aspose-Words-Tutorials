---
category: general
date: 2026-11-15
description: Modifica programmaticamente un documento Word per inserire un pulsante
  di comando. Scopri come aggiungere il pulsante, impostare il nome del pulsante di
  comando e creare un pulsante modulo in Word in pochi minuti.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit word document programmatically
- how to add button
- insert command button word
- create form button word
- set command button name
language: it
lastmod: 2026-11-15
og_description: Modifica un documento Word programmaticamente e inserisci un pulsante
  di comando. Questa guida mostra come aggiungere il pulsante, impostare il nome del
  pulsante di comando e creare rapidamente un pulsante modulo in Word.
og_image_alt: Screenshot of a Word document edited programmatically with a command
  button
og_title: Modifica documento Word programmaticamente – aggiungi un pulsante di comando
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  headline: Edit Word document programmatically and add a command button
  type: TechArticle
- description: Edit Word document programmatically to insert a command button. Learn
    how to add button, set command button name, and create form button Word in minutes.
  name: Edit Word document programmatically and add a command button
  steps:
  - name: Expected output
    text: 'When you open the saved file:'
  - name: How to add button to a specific paragraph?
    text: '```java builder.moveToParagraph(2, true); // moves to third paragraph (0‑based
      index) Forms2OleControl btn = builder.insertForms2OleControl(); btn.setName("btnThirdParagraph");
      btn.setCaption("Click Me"); ```'
  - name: How to insert a button inside a table cell?
    text: '```java Table table = builder.startTable(); builder.insertCell(); builder.insertCell();
      builder.endTable();'
  - name: What if I need a larger button?
    text: '```java cmdBtn.setWidth(100); // width in points cmdBtn.setHeight(30);
      // height in points ```'
  - name: How to **insert command button word** using a different language (e.g.,
      C#)?
    text: 'The same logic applies; replace Java syntax with C# equivalents:'
  type: HowTo
tags:
- Word automation
- Aspose.Words
- Java
title: Modifica un documento Word in modo programmatico e aggiungi un pulsante di
  comando
url: /it/java/document-manipulation/edit-word-document-programmatically-and-add-a-command-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modifica programmaticamente un documento Word e aggiungi un pulsante di comando

Se hai bisogno di **modificare un documento Word programmaticamente**, il modo più veloce è utilizzare l'API Aspose.Words. Questo tutorial ti mostra esattamente **come aggiungere pulsanti** di controllo, configurare la loro didascalia e **impostare il nome del pulsante di comando** in modo che il documento possa fungere da semplice modulo. Alla fine avrai un *.docx* completamente modificabile che contiene un pulsante di comando funzionante pronto per l'elaborazione successiva.

Imparerai come **inserire la parola pulsante di comando**, **creare la parola pulsante di modulo**, e gestire le proprietà del pulsante senza aprire Word manualmente. L'unico prerequisito è un ambiente di sviluppo Java di base e la libreria Aspose.Words per Java.

## Prerequisites

- Java 17 o versioni successive (il codice funziona anche con Java 8+)
- Aspose.Words per Java (scarica da [Aspose.Words for Java](https://products.aspose.com/words/java/))
- Un documento Word esistente (`input.docx`) che desideri modificare
- Familiarità con Maven o Gradle per aggiungere la dipendenza Aspose.Words

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Passo 1: Carica il documento Word

La prima operazione quando **modifichi un documento Word programmaticamente** è caricare il file sorgente in un oggetto `Document`. Questo oggetto rappresenta l'intero file Word in memoria, consentendoti di manipolarne il contenuto.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // Load the existing Word file
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Perché è importante:** Caricare il documento crea una struttura simile a un DOM che Aspose.Words può attraversare e modificare. Saltare questo passaggio ti lascerebbe senza un bersaglio per l'inserimento del pulsante.

## Passo 2: Crea un `DocumentBuilder` per modificare il documento

Un `DocumentBuilder` agisce come un cursore all'interno del file Word. Ti consente di inserire testo, immagini e controlli di modulo nella posizione corrente.

```java
        // Initialize a builder positioned at the start of the document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Suggerimento:** Se hai bisogno del pulsante in un paragrafo specifico, sposta prima il builder con `builder.moveToParagraph(index, true);`.

## Passo 3: Inserisci un Forms2OleControl (pulsante di comando)

Ora rispondiamo alla domanda centrale **come aggiungere un pulsante** in un file Word. Il metodo `insertForms2OleControl()` crea un pulsante di comando legacy *Forms2.0*, che è il controllo più compatibile tra le versioni di Word.

```java
        // Insert the command button at the builder's current cursor location
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();
```

> **Caso limite:** Il controllo Forms2.0 è visibile solo nella *Modalità Progettazione* di Word. Se ti serve un pulsante ActiveX più recente, considera `insertOleControl()` invece, ma il controllo legacy funziona per la maggior parte degli scenari di automazione.

## Passo 4: Configura le proprietà del pulsante

Dopo aver inserito il controllo, puoi **impostare il nome del pulsante di comando** e **inserire la parola pulsante di comando** (didascalia) per renderlo più user‑friendly.

```java
        // Set the internal name used by automation scripts
        cmdBtn.setName("cmdSubmit");

        // Set the text that appears on the button
        cmdBtn.setCaption("Submit");
```

> **Perché queste proprietà?**  
> - `setName` assegna al pulsante un identificatore che VBA o strumenti esterni possono referenziare.  
> - `setCaption` è l'etichetta visibile, creando effettivamente **la parola pulsante di modulo** su cui gli utenti finali fanno clic.

Puoi anche regolare dimensione, posizione o aggiungere una macro accedendo all'oggetto OLE sottostante, ma questi argomenti sono al di fuori dello scopo di questa breve guida.

## Passo 5: Salva il documento modificato

Infine, salva le modifiche in un nuovo file. Questo passaggio **crea la parola pulsante di modulo** nel documento di output.

```java
        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

> **Risultato:** Aprendo `output.docx` in Microsoft Word, vedrai un pulsante etichettato “Submit”. Quando passi Word alla *Modalità Progettazione* (Sviluppatore → Modalità Progettazione), puoi fare doppio clic sul pulsante per allegare una macro o semplicemente usarlo come segnaposto in un modulo.

### Output previsto

Quando apri il file salvato:

- Il punto di inserimento del cursore è sostituito da un pulsante.
- Il pulsante mostra la didascalia **Submit**.
- Il nome interno del pulsante è **cmdSubmit**, che puoi referenziare in VBA o in script di automazione esterni.

## Domande comuni e variazioni

### Come aggiungere un pulsante a un paragrafo specifico?

```java
builder.moveToParagraph(2, true); // moves to third paragraph (0‑based index)
Forms2OleControl btn = builder.insertForms2OleControl();
btn.setName("btnThirdParagraph");
btn.setCaption("Click Me");
```

### Come inserire un pulsante all'interno di una cella di tabella?

```java
Table table = builder.startTable();
builder.insertCell();
builder.insertCell();
builder.endTable();

builder.moveToCell(0, 0, 0, 0, true); // first row, first cell
Forms2OleControl cellBtn = builder.insertForms2OleControl();
cellBtn.setCaption("Cell Button");
```

### Cosa fare se ho bisogno di un pulsante più grande?

```java
cmdBtn.setWidth(100);   // width in points
cmdBtn.setHeight(30);   // height in points
```

### Come **inserire la parola pulsante di comando** usando un linguaggio diverso (ad es., C#)?

La stessa logica si applica; sostituisci la sintassi Java con le equivalenti C#:

```csharp
Document doc = new Document("input.docx");
DocumentBuilder builder = new DocumentBuilder(doc);
Forms2OleControl btn = builder.InsertForms2OleControl();
btn.Name = "cmdSubmit";
btn.Caption = "Submit";
doc.Save("output.docx");
```

## Consigli professionali e insidie

- **Consiglio professionale:** Chiama sempre `builder.moveToDocumentEnd()` prima di inserire un pulsante se lo vuoi alla fine del documento.  
- **Attenzione a:** Salvare nello stesso file che hai aperto può corrompere il documento se si verifica un'eccezione. Usa un percorso di output separato come mostrato.  
- **Compatibilità:** Il pulsante legacy Forms2.0 funziona in Word 2007‑2021. Per Word sul web, considera l'uso di controlli di contenuto.  
- **Prestazioni:** Caricare documenti molto grandi (>100 MB) può consumare molta memoria. Usa `Document.load(InputStream, LoadOptions)` con `LoadOptions.setLoadFormat(LoadFormat.DOCX)` per limitare l'uso delle risorse.

## Esempio completo funzionante

Di seguito trovi il programma Java completo, pronto per l'esecuzione. Copialo in una classe chiamata `WordButtonDemo.java`, regola i percorsi dei file e esegui `mvn compile exec:java`.

```java
import com.aspose.words.*;

public class WordButtonDemo {
    public static void main(String[] args) throws Exception {
        // 1. Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Create a builder positioned at the start
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a command button (Forms2OleControl)
        Forms2OleControl cmdBtn = builder.insertForms2OleControl();

        // 4. Set button properties – this is where we **set command button name**
        cmdBtn.setName("cmdSubmit");   // internal identifier
        cmdBtn.setCaption("Submit");   // visible text (creates form button word)

        // 5. Save the edited document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Esegui il programma e apri `output.docx` per verificare che il pulsante appaia come previsto.

## Conclusione

Ora sai come **modificare un documento Word programmaticamente** per **inserire la parola pulsante di comando**, **creare la parola pulsante di modulo**, e **impostare il nome del pulsante di comando** usando Aspose.Words per Java. Questo approccio elimina la modifica manuale, consente l'elaborazione batch dei moduli e si integra perfettamente con i flussi di lavoro automatizzati.

Successivamente, potresti esplorare:

- Aggiungere macro VBA al pulsante (`cmdBtn.getOleFormat().setMacroName("MyMacro")`)  
- Utilizzare **controlli di contenuto** per esperienze di modulo più ricche (`builder.insertCheckBox()` ecc.)  
- Automatizzare l'inserimento massivo su più documenti con un ciclo  

Sentiti libero di sperimentare con dimensioni, posizione e gestione degli eventi del pulsante per adattarlo al tuo scenario specifico. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come aggiungere un pulsante di comando programmaticamente in un documento Word](/words/english/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/)
- [Crea documento Word programmaticamente e aggiungi un pulsante ActiveX](/words/english/net/working-with-oleobjects-and-activex/create-word-document-programmatically-and-add-activex-button/)
- [Aggiungi pulsante di comando a un documento Word con Aspose.Words – Guida completa](/words/english/net/working-with-oleobjects-and-activex/add-command-button-to-word-document-with-aspose-words-comple/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}