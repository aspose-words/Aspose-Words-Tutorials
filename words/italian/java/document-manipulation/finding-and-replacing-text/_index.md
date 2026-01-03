---
date: 2026-01-03
description: Scopri come sostituire il testo con HTML nei documenti Word usando Aspose.Words
  per Java. Guida passo‑passo con esempi di codice, consigli su regex per la sostituzione
  del testo in Java e molto altro.
linktitle: Finding and Replacing Text
second_title: Aspose.Words Java Document Processing API
title: sostituire il testo con HTML usando Aspose.Words per Java
url: /it/java/document-manipulation/finding-and-replacing-text/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# sostituire testo con html in Aspose.Words per Java

## Introduzione alla ricerca e sostituzione di testo in Aspose.Words per Java

Aspose.Words per Java è una potente API Java che consente di manipolare documenti Word in modo programmatico. Uno dei compiti più comuni è **sostituire testo con html**, sia che tu stia aggiornando segnaposti in un modello, inserendo contenuti formattati o eseguendo trasformazioni di testo su larga scala. In questa guida vedremo come sostituire testo, come usare regex replace text java e persino come sostituire testo nelle intestazioni, mantenendo il codice pulito ed efficiente.

## Risposte rapide
- **Qual è il metodo principale per sostituire testo con html?** Usa `FindReplaceOptions` con un callback personalizzato come `ReplaceWithHtmlEvaluator`.  
- **Posso ignorare i campi durante la sostituzione?** Sì – imposta `options.setIgnoreFields(true)`.  
- **È necessaria una licenza per l'uso in produzione?** È richiesta una licenza valida di Aspose.Words per le distribuzioni commerciali.  
- **Quale versione di Java è supportata?** Aspose.Words per Java funziona con Java 8 e versioni successive.  
- **Il regex replace text java è supportato?** Assolutamente – passa un oggetto `Pattern` al metodo `replace`.

## Che cosa significa “sostituire testo con html”?

Sostituire testo con HTML indica lo scambio di un segnaposto di testo semplice con markup HTML ricco (tabelle, elenchi, stili) mantenendo intatta la struttura del documento Word circostante. Aspose.Words analizza l'HTML e inserisce gli oggetti Word corrispondenti, offrendoti il pieno controllo sul layout finale.

## Perché usare Aspose.Words per questo compito?

- **Fedele riproduzione di Word** – la libreria conserva tutta la formattazione, intestazioni, piè di pagina e modifiche tracciate.  
- **Supporto regex integrato** – perfetto per pattern di ricerca complessi (`regex replace text java`).  
- **Controllo fine‑grained** – opzioni come `IgnoreFields`, `IgnoreDeleted` e `UseLegacyOrder` ti permettono di personalizzare l'operazione secondo le tue esigenze.  
- **Cross‑platform** – funziona su qualsiasi OS che esegue Java.

## Prerequisiti

- Ambiente di sviluppo Java (JDK 8+)  
- Libreria Aspose.Words per Java – scaricala da [qui](https://releases.aspose.com/words/java/).  
- Un documento Word di esempio (`.docx`) su cui sperimentare.

## Ricerca e sostituzione di testo semplice

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Find and replace text
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Questo esempio base mostra **come sostituire testo** usando il metodo `replace`. È la base per scenari più avanzati.

## Uso delle espressioni regolari (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Use regular expressions for finding and replacing text
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Le espressioni regolari offrono un potente matching di pattern, ideale per segnaposti dinamici o confini di parola complessi.

## Ignorare il testo all'interno dei campi (aspose words replace text)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreFields to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Imposta `IgnoreFields` per mantenere intatti campi di unione, numeri di pagina o altri codici di campo mentre sostituisci il contenuto circostante.

## Ignorare il testo all'interno delle revisioni di eliminazione

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreDeleted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Questo impedisce che il testo contrassegnato per l'eliminazione (modifiche tracciate) venga modificato.

## Ignorare il testo all'interno delle revisioni di inserimento

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set IgnoreInserted to true
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

Utile quando vuoi mantenere intatto il testo appena inserito durante una sostituzione massiva.

## Sostituire testo con HTML

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Use options when replacing text
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Save the modified document
doc.save("modified-document.docx");
```

Qui **sostituiamo testo con html** fornendo un valutatore personalizzato che analizza la stringa HTML e inserisce i nodi Word appropriati.

## Sostituire testo in intestazioni e piè di pagina (replace text in headers)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the collection of headers and footers
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Choose the header or footer type you want to replace text in (e.g., HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Create a FindReplaceOptions instance and apply it to the footer's range
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Save the modified document
doc.save("modified-document.docx");
```

La sostituzione mirata all'interno di intestazioni o piè di pagina garantisce che il branding del documento rimanga coerente.

## Visualizzare le modifiche per l'ordine di intestazioni e piè di pagina

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get the first section
Section firstPageSection = doc.getFirstSection();

// Create a FindReplaceOptions instance and apply it to the document's range
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Replace text that affects header and footer orders
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

Questo esempio registra le modifiche, aiutandoti a verificare le variazioni nell'ordinamento di intestazioni/π piè di pagina.

## Sostituire testo con campi

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback for fields
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Use options when replacing text
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

L'inserimento di campi (ad es., campi di unione) consente di creare documenti dinamici che possono essere popolati in seguito.

## Sostituire con un valutatore

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set a custom replacing callback
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Use options when replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

I valutatori personalizzati ti danno il pieno controllo programmatico sul testo di sostituzione.

## Sostituire con regex (regex replace text java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Use regular expressions for finding and replacing text
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Un modo conciso per eseguire sostituzioni basate su pattern in tutto il documento.

## Riconoscimento e sostituzioni all'interno dei pattern di sostituzione

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance with UseSubstitutions set to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Use options when replacing text with a pattern
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Save the modified document
doc.save("modified-document.docx");
```

Abilita `UseSubstitutions` per fare riferimento ai gruppi di cattura direttamente nella stringa di sostituzione.

## Sostituire con una stringa (replace text word java)

```java
// Load the document
Document doc = new Document("your-document.docx");

// Replace text with a string
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

La forma più semplice di sostituzione—perfetta per segnaposti statici.

## Uso dell'ordine legacy

```java
// Load the document
Document doc = new Document("your-document.docx");

// Create a FindReplaceOptions instance and set UseLegacyOrder to true
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Use options when replacing text
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Save the modified document
doc.save("modified-document.docx");
```

L'ordine legacy può essere necessario quando si lavora con documenti più vecchi che dipendono dalla sequenza di attraversamento originale.

## Sostituire testo in una tabella

```java
// Load the document
Document doc = new Document("your-document.docx");

// Get a specific table (e.g., the first table)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

// Use FindReplaceOptions for replacing text in the table
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Save the modified document
doc.save("modified-document.docx");
```

Le sostituzioni mirate all'interno delle tabelle evitano modifiche indesiderate altrove nel documento.

## Problemi comuni e soluzioni

- **HTML non visualizzato correttamente** – Assicurati che il tuo HTML sia ben formato e includa i tag richiesti (es. `<p>`, `<table>`).  
- **Regex non corrisponde** – Ricorda di eseguire l'escape dei caratteri speciali e usa `Pattern.CASE_INSENSITIVE` se necessario.  
- **Campi sostituiti involontariamente** – Imposta `options.setIgnoreFields(true)` per proteggerli.  
- **Prestazioni su documenti di grandi dimensioni** – Usa `UseLegacyOrder` o elabora le sezioni singolarmente per ridurre l'impronta di memoria.

## Domande frequenti

**D: Come scarico Aspose.Words per Java?**  
R: Puoi scaricare Aspose.Words per Java dal sito web visitando [questo link](https://releases.aspose.com/words/java/).

**D: Posso usare le espressioni regolari per la sostituzione del testo?**  
R: Sì, puoi utilizzare le espressioni regolari per la sostituzione del testo in Aspose.Words per Java. Questo ti consente di eseguire operazioni di ricerca e sostituzione più avanzate e flessibili.

**D: Come posso ignorare il testo all'interno dei campi durante la sostituzione?**  
R: Imposta la proprietà `IgnoreFields` di `FindReplaceOptions` su `true`. Questo esclude il contenuto dei campi, come i campi di unione, dalla sostituzione.

**D: È possibile sostituire testo all'interno di intestazioni e piè di pagina?**  
R: Assolutamente. Accedi all'intestazione o al piè di pagina desiderato tramite `HeaderFooterCollection` e applica il metodo `replace` con le opzioni appropriate.

**D: Cosa fa l'opzione `UseLegacyOrder`?**  
R: `UseLegacyOrder` forza il motore di ricerca/sostituzione a attraversare i nodi nell'ordine originale usato dalle versioni precedenti di Aspose.Words, utile per la compatibilità con documenti legacy.

---

**Ultimo aggiornamento:** 2026-01-03  
**Testato con:** Aspose.Words per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}