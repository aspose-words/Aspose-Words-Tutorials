---
date: 2026-01-01
description: Scopri come creare campi modulo e aggiungere testo, tabelle, immagini,
  collegamenti ipertestuali e molto altro utilizzando Aspose.Words per Java DocumentBuilder.
  Una guida passo‑passo per gli sviluppatori.
linktitle: Adding Content using DocumentBuilder
second_title: Aspose.Words Java Document Processing API
title: Come creare campi modulo e aggiungere contenuti usando DocumentBuilder in Aspose.Words
  per Java
url: /it/java/document-manipulation/adding-content-using-documentbuilder/
weight: 26
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java

## Introduzione all'aggiunta di contenuto usando DocumentBuilder in Aspose.Words per Java

In questa guida passo‑paso, **creerai campi modulo** e aggiungerai una varietà di contenuti—testo, tabelle, linee orizzontali, HTML, collegamenti ipertestuali, immagini e molto altro—in un documento Word con Aspose.Words per Java. Che tu stia creando un report, un modello di contratto o un modulo interattivo, la classe `DocumentBuilder` ti offre un controllo dettagliato su ogni elemento. Iniziamo!

## Risposte rapide
- **Come creo i campi modulo?** Usa `insertTextInput`, `insertCheckBox` o `insertComboBox` su un `DocumentBuilder`.
- **Quale metodo aggiunge testo semplice?** Chiama `builder.write("Your text")` o `builder.writeln("Your text")`.
- **Posso inserire una linea orizzontale?** Sì—`builder.insertHorizontalRule()` aggiunge un separatore di linea.
- **Come incorporare HTML?** Usa `builder.insertHtml("<p>HTML content</p>")`.
- **Come aggiungere un'immagine in linea?** `builder.insertImage("path/to/image.png")` inserisce l'immagine all'interno del flusso di testo.

## Che cos'è DocumentBuilder e perché usarlo per creare campi modulo?

`DocumentBuilder` è l'API fluente di Aspose.Words per costruire e modificare documenti Word programmaticamente. Astrae la struttura OpenXML a basso livello, permettendoti di concentrarti su *cosa* vuoi aggiungere—come **i campi modulo**—invece di *come* appare l'XML. Questo lo rende ideale per generare moduli dinamici, contratti o qualsiasi documento che richieda interazione dell'utente.

## Prerequisiti

Prima di iniziare, assicurati di avere la libreria Aspose.Words per Java installata nel tuo progetto. Puoi scaricarla da [qui](https://releases.aspose.com/words/java/).

## Aggiungere testo (come aggiungere testo)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a simple text paragraph
builder.write("This is a simple text paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Aggiungere tabelle

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start a table
Table table = builder.startTable();

// Insert cells and content
builder.insertCell();
builder.write("Cell 1");

builder.insertCell();
builder.write("Cell 2");

// End the table
builder.endTable();

// Save the document
doc.save("path/to/your/document.docx");
```

## Aggiungere una linea orizzontale (aggiungere linea orizzontale)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a horizontal rule
builder.insertHorizontalRule();

// Save the document
doc.save("path/to/your/document.docx");
```

## Aggiungere campi modulo (creare campi modulo)

### Campo di input testo

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a text input form field
builder.insertTextInput("TextInput", TextFormFieldType.REGULAR, "", "Default text", 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Campo casella di controllo

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a check box form field
builder.insertCheckBox("CheckBox", true, true, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

### Campo casella combinata

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Define items for the combo box
String[] items = { "Option 1", "Option 2", "Option 3" };

// Insert a combo box form field
builder.insertComboBox("DropDown", items, 0);

// Save the document
doc.save("path/to/your/document.docx");
```

## Aggiungere HTML (inserire HTML)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert HTML content
builder.insertHtml("<p>This is an HTML paragraph.</p>");

// Save the document
doc.save("path/to/your/document.docx");
```

## Aggiungere collegamenti ipertestuali (come aggiungere collegamento ipertestuale)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a hyperlink
builder.write("Visit ");
builder.getFont().setColor(Color.BLUE);
builder.getFont().setUnderline(Underline.SINGLE);
builder.insertHyperlink("Aspose Website", "http://www.aspose.com", false);
builder.getFont().clearFormatting();
builder.write(" for more information.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Aggiungere un indice

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();

// Save the document
doc.save("path/to/your/document.docx");
```

## Aggiungere immagini

### Immagine in linea (inserire immagine in linea)

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");

// Save the document
doc.save("path/to/your/document.docx");
```

### Immagine flottante

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);

// Save the document
doc.save("path/to/your/document.docx");
```

## Aggiungere paragrafi

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a paragraph
builder.writeln("This is a formatted paragraph.");

// Save the document
doc.save("path/to/your/document.docx");
```

## Spostare il cursore (Passo 10)

Puoi controllare la posizione del cursore all'interno del documento usando metodi come `moveToParagraph`, `moveToCell`, ecc.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Queste sono alcune operazioni comuni che puoi eseguire usando `DocumentBuilder` di Aspose.Words per Java. Esplora la documentazione della libreria per funzionalità più avanzate e opzioni di personalizzazione. Buona creazione di documenti!

## Conclusione

In questa guida completa, abbiamo mostrato come **creare campi modulo** e aggiungere vari tipi di contenuto—testo, tabelle, linee orizzontali, HTML, collegamenti ipertestuali, un indice, immagini, paragrafi formattati e navigazione del cursore—usando `DocumentBuilder` di Aspose.Words per Java. Ora disponi di una solida base per generare documenti Word dinamici e interattivi in modo programmatico.

## FAQ

### Q: Che cos'è Aspose.Words per Java?

A: Aspose.Words per Java è una libreria Java che consente agli sviluppatori di creare, modificare e manipolare documenti Microsoft Word programmaticamente. Offre un'ampia gamma di funzionalità per la generazione di documenti, la formattazione e l'inserimento di contenuti.

### Q: Come posso aggiungere un indice al mio documento?

A: Per aggiungere un indice, usa `DocumentBuilder` per inserire un campo TOC e poi chiama `doc.updateFields()` dopo aver aggiunto il contenuto.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a table of contents field
builder.insertTableOfContents("\\o \"1-3\" \\h \\z \\u");

// Add document content
// ...

// Update the table of contents
doc.updateFields();
```

### Q: Come inserisco immagini in un documento usando Aspose.Words per Java?

A: Puoi inserire immagini, sia in linea che flottanti, usando `DocumentBuilder`.

#### Immagine in linea:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert an inline image
builder.insertImage("path/to/your/image.png");
```

#### Immagine flottante:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a floating image
builder.insertImage("path/to/your/image.png", RelativeHorizontalPosition.MARGIN, 100.0, RelativeVerticalPosition.MARGIN, 100.0, 200.0, 100.0, WrapType.SQUARE);
```

### Q: Posso formattare testo e paragrafi quando aggiungo contenuto?

A: Sì, puoi formattare testo e paragrafi usando `DocumentBuilder`. Imposta le proprietà del carattere, l'allineamento del paragrafo, l'indentazione e altro prima di scrivere il contenuto.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Set font and paragraph formatting
Font font = builder.getFont();
font.setSize(16.0);
font.setBold(true);
font.setColor(Color.BLUE);
font.setName("Arial");
font.setUnderline(Underline.DASH);

ParagraphFormat paragraphFormat = builder.getParagraphFormat();
paragraphFormat.setFirstLineIndent(8.0);
paragraphFormat.setAlignment(ParagraphAlignment.JUSTIFY);
paragraphFormat.setKeepTogether(true);

// Insert a formatted paragraph
builder.writeln("This is a formatted paragraph.");
```

### Q: Come posso spostare il cursore in una posizione specifica all'interno del documento?

A: Usa metodi come `moveToParagraph`, `moveToCell`, ecc., per posizionare il cursore prima di inserire nuovo contenuto.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Move the cursor to a specific paragraph
builder.moveToParagraph(2, 0);

// Add content at the new cursor position
builder.writeln("This is the 3rd paragraph.");
```

Queste risposte coprono gli scenari più comuni quando si lavora con `DocumentBuilder` di Aspose.Words per Java. Per dettagli più approfonditi, consulta la [documentazione della libreria](https://reference.aspose.com/words/java/) o unisciti alla community di Aspose.Words per supporto.

---

**Ultimo aggiornamento:** 2026-01-01  
**Testato con:** Aspose.Words per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}