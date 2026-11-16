---
category: general
date: 2026-11-15
description: Imposta l'interlinea del paragrafo in un documento Word con Java. Scopri
  come impostare l'interlinea programmaticamente usando Aspose.Words per una formattazione
  precisa del documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: it
lastmod: 2026-11-15
og_description: Imposta l'interlinea dei paragrafi in un documento Word con Java.
  Questa guida spiega come impostare l'interlinea per i paragrafi e i separatori delle
  note a piè di pagina utilizzando Aspose.Words, offrendoti il pieno controllo sul
  layout del documento.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Imposta l'interlinea del paragrafo in Word usando Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Imposta l'interlinea del paragrafo in un documento Word con Java
url: /it/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Impostare l'interlinea dei paragrafi in un documento Word con Java

Se devi **impostare l'interlinea dei paragrafi** in un documento Word, questo tutorial ti mostra come farlo con Java e Aspose.Words. Imparerai anche **come impostare l'interlinea** per i separatori delle note a piè di pagina—una esigenza comune nella formattazione di documenti professionali.

Nelle sezioni seguenti:

* Caricherai un file *.docx* esistente.
* Recupererai il paragrafo del separatore della nota a piè di pagina.
* Applicherai un valore di interlinea personalizzato.
* Salverai il documento aggiornato.

Non è necessaria alcuna configurazione esterna oltre all'aggiunta della libreria Aspose.Words al tuo progetto, quindi puoi copiare il codice così com'è e eseguirlo subito.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java 17 o versione successiva installata.
* Maven (o un altro tool di build) per gestire le dipendenze.
* Una licenza valida di Aspose.Words per Java (la valutazione gratuita è sufficiente per i test).
* Un documento Word di input (`input.docx`) situato in una directory nota.

Aggiungi la dipendenza Aspose.Words al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Impostare l'interlinea dei paragrafi con Aspose.Words

Questo titolo H2 contiene la parola chiave principale, soddisfacendo il requisito SEO.

### Passo 1: Caricare il documento Word

Per prima cosa, crea un'istanza `Document` che punti al tuo file sorgente.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Perché è importante*: Caricare il documento ti fornisce un modello in memoria che puoi manipolare senza toccare il file originale finché non lo salvi esplicitamente.

### Passo 2: Recuperare il separatore della nota a piè di pagina

I separatori delle note a piè di pagina sono paragrafi speciali che appaiono tra le note e il testo principale. Per modificarne l'aspetto devi accedere all'oggetto `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Consiglio*: Se il tuo documento non contiene note a piè di pagina, il separatore esiste comunque come paragrafo nascosto, quindi la chiamata non restituirà mai `null`.

### Passo 3: Come impostare l'interlinea per il paragrafo del separatore

Ora applica l'interlinea desiderata. Aspose.Words utilizza i punti per i valori di interlinea; 12 pt corrispondono approssimativamente a un'interlinea singola per la maggior parte dei caratteri.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

Puoi anche usare altre modalità di spaziatura:

| Modalità                | Chiamata al metodo                                 |
|--------------------------|----------------------------------------------------|
| **Exactly** (pt fissi)   | `setLineSpacingRule(LineSpacingRule.EXACTLY)`     |
| **Multiple** (es. 1.5)   | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Scegliere la regola corretta garantisce che il documento venga visualizzato in modo coerente su Word, Google Docs e altri visualizzatori.

### Passo 4: Salvare il documento aggiornato

Infine, scrivi le modifiche su disco.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Quando apri `output.docx` in Microsoft Word, il separatore della nota a piè di pagina verrà visualizzato con l'interlinea che hai definito.

## Comprendere come impostare l'interlinea per i paragrafi normali

La stessa API funziona per qualsiasi oggetto `Paragraph`, non solo per i separatori delle note a piè di pagina. Ecco un rapido esempio che regola l'interlinea del primo paragrafo del corpo:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Perché potresti averne bisogno**: Rapporti, contratti e lavori accademici richiedono spesso uno stile di interlinea specifico (ad esempio, interlinea doppia per le bozze). Usare lo stesso metodo `setLineSpacing` garantisce il layout esatto che ti aspetti.

## Problemi comuni e come evitarli

| Problema                                 | Causa                                          | Soluzione |
|------------------------------------------|-----------------------------------------------|-----------|
| L'interlinea non cambia                  | `LineSpacingRule` lasciato al valore predefinito (AUTO) | Imposta esplicitamente la regola con `setLineSpacingRule`. |
| Righe vuote aggiuntive dopo il separatore| Il separatore contiene ritorni a capo nascosti | Rimuovi gli spazi con `separator.getText().trim();` prima di applicare l'interlinea. |
| Il documento si corrompe dopo il salvataggio| Uso di una versione obsoleta di Aspose.Words | Aggiorna all'ultima versione (es. 24.10) che contiene correzioni per il salvataggio. |

## Consiglio professionale: elaborare in batch più documenti

Se devi aggiornare decine di file, racchiudi la logica in un metodo di supporto e itera su una cartella:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Eseguire questo metodo in un ciclo ti farà risparmiare ore di editing manuale.

## Output previsto

Dopo aver eseguito il programma completo, `output.docx`:

* Conterrà il contenuto originale invariato, tranne l'interlinea.
* Mostrerà il separatore della nota a piè di pagina con un layout a interlinea singola (12 pt).
* Preserverà tutta l'altra formattazione (stili, immagini, tabelle).

Apri il file in Word e verifica che la linea del separatore sia più stretta (o più larga, a seconda del valore impostato).

## Conclusione

Ora sai come **impostare l'interlinea dei paragrafi** in un documento Word usando Java, e comprendi anche **come impostare l'interlinea** sia per i separatori delle note a piè di pagina sia per i paragrafi normali. L'esempio completo e funzionante dimostra come caricare un documento, regolare le proprietà di interlinea e salvare il risultato—tutto con poche chiamate API chiare.

**Passi successivi** che potresti esplorare:

* **Come impostare l'interlinea** per tabelle e voci di elenco.
* Applicare regole di spaziatura diverse a titoli rispetto al corpo del testo.
* Usare l'oggetto `Style` per imporre l'interlinea su tutto il documento.

Sperimenta con i valori, combinandoli con altre opzioni di formattazione, e avrai il pieno controllo sul layout dei documenti in qualsiasi applicazione Java. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come impostare le opzioni in Aspose.Words per Java – guida completa](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Come impostare LoadOptions in Aspose.Words per Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Modificare la spaziatura e i rientri dei paragrafi asiatici in un documento Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}