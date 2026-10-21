---
category: general
date: 2026-10-04
description: Modifica il separatore delle note a piè di pagina in Java con Aspose.Words
  – scopri come cambiare il separatore delle note a piè di pagina e aggiungere una
  parola separatore personalizzata ai documenti Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit footnote separator
- change footnote separator
- custom separator word
language: it
lastmod: 2026-10-04
og_description: Modifica il separatore delle note a piè di pagina in Java con Aspose.Words.
  Questo tutorial mostra come cambiare il separatore delle note a piè di pagina e
  inserire una parola separatore personalizzata.
og_image_alt: Screenshot of a Java IDE showing code that edits a footnote separator
  in a Word document
og_title: Modifica il separatore delle note a piè di pagina in Java – guida completa
  di Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  headline: How to edit footnote separator in Java with Aspose.Words
  type: TechArticle
- description: Edit footnote separator in Java using Aspose.Words – learn how to change
    footnote separator and add a custom separator word to Word documents.
  name: How to edit footnote separator in Java with Aspose.Words
  steps:
  - name: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
    text: '**`clearChildren()`** removes any existing runs, ensuring the separator
      contains only the text you provide.'
  - name: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
    text: '**`new Run(document, "—")`** creates a text node with the desired separator.
      The `Run` object respects the document’s style, so the separator inherits the
      formatting of the original footnote separator.'
  - name: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
    text: '**`appendChild(customRun)`** inserts the new run into the separator paragraph.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
- Word processing
title: Come modificare il separatore delle note a piè di pagina in Java con Aspose.Words
url: /it/java/document-styling/how-to-edit-footnote-separator-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come modificare il separatore delle note a piè di pagina in Java con Aspose.Words

Se hai bisogno di **modificare il separatore delle note a piè di pagina** in un documento Word, questa guida ti mostra esattamente come farlo in Java. Che tu voglia **cambiare il separatore delle note a piè di pagina** in un trattino, una stella o qualsiasi **parola separatore personalizzata**, i passaggi seguenti coprono tutto ciò di cui hai bisogno.

Imparerai come caricare un file `.docx`, recuperare la sezione speciale del separatore, modificarne il contenuto e salvare il risultato. Nessuno script esterno o modifica manuale è necessario – tutto viene eseguito programmaticamente con la libreria Aspose.Words per Java.

## Prerequisiti

- Java 17 o versioni successive installate.
- Maven o Gradle per gestire le dipendenze (l'esempio utilizza Maven).
- Una licenza valida di Aspose.Words per Java (o una chiave di valutazione gratuita).
- Un documento Word che contiene già note a piè di pagina (il separatore esiste solo quando sono presenti note a piè di pagina).

## Aggiungi Aspose.Words al tuo progetto

Se usi Maven, aggiungi la seguente dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.11</version> <!-- Use the latest version -->
</dependency>
```

Per Gradle, aggiungi:

```gradle
implementation 'com.aspose:aspose-words:24.11'
```

## Passo 1: Carica il documento che contiene note a piè di pagina

Il primo passo è aprire il file Word che desideri modificare. Aspose.Words legge il file in un oggetto `Document`, che ti dà pieno accesso a tutte le parti del documento, inclusi i separatori delle note a piè di pagina.

```java
import com.aspose.words.*;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // Path to the source document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";

        // Load the document
        Document document = new Document(inputPath);
        
        // Continue with separator editing...
    }
}
```

**Perché è importante:** Caricare il documento crea una rappresentazione in memoria, così puoi modificare in sicurezza qualsiasi nodo senza toccare il file originale finché non lo salvi esplicitamente.

## Passo 2: Recupera la sezione del separatore delle note a piè di pagina

Word memorizza il separatore delle note a piè di pagina come un nodo speciale `Separator`. Aspose.Words fornisce il metodo `getFootnoteSeparator()` per ottenerlo direttamente.

```java
// Get the footnote separator (the line that appears between footnotes and the main text)
Separator footnoteSeparator = document.getFootnoteSeparator();

if (footnoteSeparator == null) {
    System.out.println("The document does not contain a footnote separator.");
    return;
}
```

**Consiglio:** Il nodo separatore esiste solo se il documento ha già almeno una nota a piè di pagina. Se provi a modificare un documento senza note a piè di pagina, `getFootnoteSeparator()` restituisce `null`, quindi verifica sempre questa condizione.

## Passo 3: Inserisci una parola separatore personalizzata

Ora puoi cambiare l'aspetto del separatore. In questo esempio sostituiamo la linea predefinita con un trattino lungo (`—`). Potresti invece inserire qualsiasi **parola separatore personalizzata**, come `"NOTE:"` o `"***"`.

```java
// Access the first paragraph of the separator (there is usually only one)
Paragraph separatorParagraph = footnoteSeparator.getParagraphs().get(0);

// Clear any existing runs (text fragments) to avoid mixing old and new content
separatorParagraph.clearChildren();

// Append a new Run that contains the custom separator word
Run customRun = new Run(document, "—");   // Replace "—" with any text you need
separatorParagraph.appendChild(customRun);
```

### Cosa fa il codice

1. **`clearChildren()`** rimuove tutti i run esistenti, assicurando che il separatore contenga solo il testo fornito.
2. **`new Run(document, "—")`** crea un nodo di testo con il separatore desiderato. L'oggetto `Run` rispetta lo stile del documento, quindi il separatore eredita la formattazione del separatore originale della nota a piè di pagina.
3. **`appendChild(customRun)`** inserisce il nuovo run nel paragrafo del separatore.

Puoi anche applicare formattazione al run, ad esempio:

```java
customRun.getFont().setBold(true);
customRun.getFont().setSize(10);
customRun.getFont().setColor(Color.BLUE);
```

## Passo 4: Salva il documento modificato

Dopo aver modificato il separatore, scrivi il documento nuovamente su disco. Scegli un nuovo nome file per mantenere intatto il file originale.

```java
// Path to the output document
String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";

// Save the changes
document.save(outputPath);

System.out.println("Footnote separator edited successfully. Saved to " + outputPath);
```

**Verifica del risultato:** Apri `ModifiedNotes.docx` in Microsoft Word. Il separatore delle note a piè di pagina dovrebbe ora mostrare il trattino personalizzato (o qualsiasi parola tu abbia scelto) invece della linea predefinita.

## Gestione di più separatori delle note a piè di pagina

Word supporta tre tipi speciali di separatori:

| Tipo di separatore | Metodo |
|--------------------|--------|
| Separatore delle note a piè di pagina | `getFootnoteSeparator()` |
| Separatore di continuazione delle note a piè di pagina | `getFootnoteContinuationSeparator()` |
| Separatore delle note a piè di pagina per la prima pagina | `getFootnoteSeparatorForFirstPage()` |

Se devi modificare tutti, ripeti **Passo 2** e **Passo 3** per ciascun metodo. Esempio:

```java
Separator continuation = document.getFootnoteContinuationSeparator();
if (continuation != null) {
    // Apply the same custom run or a different one
    Paragraph p = continuation.getParagraphs().get(0);
    p.clearChildren();
    p.appendChild(new Run(document, "*"));
}
```

## Problemi comuni e come evitarli

| Problema | Causa | Soluzione |
|----------|-------|-----------|
| Nessun separatore appare dopo il salvataggio | Il documento non aveva note a piè di pagina → il nodo separatore è `null` | Aggiungi almeno una nota a piè di pagina prima di modificare, oppure crea una nota fittizia programmaticamente. |
| Il separatore mostra spazi extra | I run esistenti non sono stati cancellati | Chiama `clearChildren()` prima di aggiungere il nuovo run. |
| La formattazione appare diversa | Il run eredita lo stile dal separatore originale | Imposta esplicitamente le proprietà del carattere sul `Run` se ti serve un aspetto specifico. |

## Esempio completo funzionante

Mettendo insieme tutti i pezzi, ecco una classe Java autonoma che puoi copiare, compilare ed eseguire:

```java
import com.aspose.words.*;
import java.awt.Color;

public class EditFootnoteSeparator {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the document
        String inputPath = "YOUR_DIRECTORY/docWithNotes.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the footnote separator
        Separator footnoteSeparator = doc.getFootnoteSeparator();
        if (footnoteSeparator == null) {
            System.out.println("Document has no footnote separator.");
            return;
        }

        // 3️⃣ Replace the separator with a custom word (e.g., an em dash)
        Paragraph para = footnoteSeparator.getParagraphs().get(0);
        para.clearChildren();                       // Remove old runs
        Run customRun = new Run(doc, "—");          // Change "—" to any word you need
        customRun.getFont().setBold(true);         // Optional styling
        customRun.getFont().setSize(9);
        customRun.getFont().setColor(Color.DARK_GRAY);
        para.appendChild(customRun);

        // 4️⃣ Save the modified document
        String outputPath = "YOUR_DIRECTORY/ModifiedNotes.docx";
        doc.save(outputPath);

        System.out.println("Footnote separator edited successfully.");
    }
}
```

Esegui il programma, poi apri `ModifiedNotes.docx` per confermare che il separatore è stato aggiornato.

## Conclusione

Ora sai come **modificare il separatore delle note a piè di pagina** in un documento Word usando Java e Aspose.Words. Il tutorial ha coperto il caricamento di un documento, il recupero del nodo separatore speciale, l'inserimento di una **parola separatore personalizzata**, e il salvataggio del risultato. Seguendo questi passaggi puoi anche **cambiare il separatore delle note a piè di pagina** per le sezioni di continuazione o per le note a piè di pagina della prima pagina.

Successivamente, potresti esplorare:

- Aggiungere separatori diversi per le note a piè di pagina della prima pagina (`getFootnoteSeparatorForFirstPage()`).
- Creare programmaticamente note a piè di pagina quando non ne esistono.
- Usare Aspose.Words per formattare il testo delle note a piè di pagina (font, colori, rientri).

Sentiti libero di sperimentare con altri caratteri o parole per adattarle al branding del tuo documento. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Inserisci separatore di stile del documento in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)
- [Ottieni separatore di stile del paragrafo in documento Word](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Come caricare documenti Word con Aspose.Words Java: Guida completa](/words/english/java/document-operations/aspose-words-java-master-word-processing/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}