---
category: general
date: 2026-08-07
description: Come modificare la nota a piè di pagina in Java con Aspose.Words – aggiungere
  un trattino personalizzato, modificare la linea della nota a piè di pagina e impostare
  l'allineamento del paragrafo per documenti rifiniti.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: it
lastmod: 2026-08-07
og_description: Come modificare la nota a piè di pagina in Java con Aspose.Words.
  Scopri come aggiungere un trattino personalizzato, modificare la linea della nota
  a piè di pagina e impostare l'allineamento del paragrafo in pochi passaggi.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: Come modificare la nota a piè di pagina in Java – aggiungere il trattino,
  cambiare riga, impostare l'allineamento
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Come modificare la nota a piè di pagina in Java con Aspose.Words
url: /it/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come modificare le note a piè di pagina in Java con Aspose.Words

Se hai bisogno di **come modificare le note a piè di pagina** in un documento Word usando Java, questa guida mostra l'intero flusso di lavoro. Imparerai ad aggiungere un trattino personalizzato, modificare la linea della nota a piè di pagina e impostare l'allineamento del paragrafo affinché il separatore della nota a piè di pagina abbia un aspetto professionale.

Modificare le note a piè di pagina è una necessità comune quando si preparano contratti legali, articoli accademici o brochure di marketing. I passaggi seguenti coprono tutto ciò di cui hai bisogno — dal caricamento del documento al salvataggio del file finale — senza richiedere strumenti aggiuntivi.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versioni successive installato.  
* Aspose.Words per Java (ultima versione) aggiunto al classpath del tuo progetto.  
* Un file DOCX (`input.docx`) che contiene almeno una nota a piè di pagina.

Questi elementi garantiscono che il codice venga eseguito senza errori di runtime.

## Come modificare il separatore e la linea della nota a piè di pagina

Il separatore della nota a piè di pagina è il paragrafo che appare tra il testo principale e l'elenco delle note a piè di pagina. Cambiarne l'aspetto migliora la leggibilità e corrisponde all'identità aziendale.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Perché ogni riga è importante

1. **Caricamento del documento** – `new Document(...)` legge il file DOCX in memoria, fornendoti l'accesso a tutti i suoi nodi.  
2. **Recupero del separatore** – `getFootnoteSeparator()` restituisce il paragrafo speciale che Aspose.Words tratta come la linea della nota a piè di pagina. Questo oggetto è l'unico punto in cui è possibile modificare in sicurezza il separatore.  
3. **Impostazione dell'allineamento del paragrafo** – `setAlignment(ParagraphAlignment.CENTER)` cambia l'allineamento della linea. La parola chiave *set paragraph alignment* viene applicata direttamente al separatore, garantendo un trattino centrato.  
4. **Aggiunta di un trattino personalizzato** – Cancellando le run esistenti e aggiungendo una nuova `Run` con il carattere em‑dash (`—`), ottieni l'effetto *add custom dash* e allo stesso tempo *change footnote line* nello stile desiderato.  
5. **Salvataggio del documento** – `doc.save(...)` scrive le modifiche su disco, producendo un file di output che riflette tutte le modifiche.

## Aggiungi un trattino personalizzato al separatore della nota a piè di pagina

Il codice nella **Fase 4** dimostra la tecnica *add custom dash*. Puoi sostituire l'em‑dash con qualsiasi stringa, ad esempio `"***"` o `"---"`, per adattarla al linguaggio visivo del tuo documento.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Usare un trattino personalizzato è particolarmente utile quando la linea sottile predefinita non soddisfa le linee guida del brand.

## Modifica lo stile della linea della nota a piè di pagina

Se preferisci una linea solida invece di un trattino, puoi inserire un carattere Unicode per il disegno di box o un trattino basso ripetuto.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

Il passaggio *change footnote line* funziona allo stesso modo indipendentemente dal carattere scelto, poiché il paragrafo separatore rende semplicemente il testo che contiene.

## Imposta l'allineamento del paragrafo per il separatore della nota a piè di pagina

L'operazione *set paragraph alignment* non è limitata all'allineamento centrato. Puoi allineare a sinistra, a destra o giustificare secondo le esigenze del layout.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Allineare il separatore a destra può essere utile per documenti che usano note a piè di pagina allineate a destra, come pubblicazioni bilingue.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che incorpora tutti i concetti — caricamento di un documento, modifica del separatore della nota a piè di pagina, aggiunta di un trattino personalizzato, modifica dello stile della linea e impostazione dell'allineamento.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Output previsto:** Il file `output.docx` contiene un em‑dash centrato dove una volta c'era la linea sottile originale. Tutte le note a piè di pagina rimangono intatte e il layout del documento riflette il nuovo stile del separatore.

## Problemi comuni e come evitarli

| Problema | Motivo | Soluzione |
|----------|--------|-----------|
| Separatore non trovato | Il documento non contiene note a piè di pagina o utilizza uno stile di nota personalizzato | Assicurati che il DOCX di origine contenga almeno una nota a piè di pagina prima di chiamare `getFootnoteSeparator()` |
| Trattino personalizzato non visibile | Il font non supporta il carattere scelto | Usa un carattere Unicode supportato dal font predefinito del documento, o incorpora un font compatibile |
| L'allineamento sembra invariato | Il formato del paragrafo viene sovrascritto più tardi nel codice | Applica l'allineamento **dopo** qualsiasi altra chiamata di formattazione che potrebbe reimpostarlo |

Affrontare questi punti previene errori di runtime e garantisce che il processo *how to edit footnote* funzioni in modo affidabile.

## Prossimi passi

Ora che conosci **come modificare le note a piè di pagina**, puoi esplorare attività correlate:

* **Aggiungi uno stile personalizzato per il riferimento della nota a piè di pagina** – modifica i nodi `FootnoteReference` per cambiare la numerazione o i simboli.  
* **Inserisci programmaticamente nuove note a piè di pagina** – usa `DocumentBuilder.insertFootnote()` per contenuti dinamici.  
* **Applica formattazione condizionale** – cambia l'aspetto della nota a piè di pagina in base allo stile del paragrafo o alla lunghezza del contenuto.  

Ognuna di queste estensioni si basa sulla stessa superficie API che hai usato per *add custom dash*, *change footnote line* e *set paragraph alignment*.

---

*Buon coding! Se il tutorial ti ha aiutato a padroneggiare la modifica delle note a piè di pagina, considera di condividerlo con il tuo team o di contribuire con una pull request per migliorare ulteriormente l'esempio.*

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Imposta la posizione di Note a piè di pagina e Note di chiusura](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Come creare campi modulo e aggiungere contenuti usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Come impostare LoadOptions in Aspose.Words per Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}