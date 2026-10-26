---
category: general
date: 2026-10-26
description: Scopri come specificare la codifica in Java usando LoadOptions. Questa
  guida copre la codifica dei caratteri, il metodo setEncoding e le opzioni di caricamento
  del documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to specify encoding
- character encoding in Java
- LoadOptions encoding
- setEncoding method
- document loading options
- Aspose.Words for Java
language: it
lastmod: 2026-10-26
og_description: Come specificare la codifica in Java usando Aspose.Words. Segui questo
  tutorial completo per caricare i documenti con il set di caratteri corretto.
og_image_alt: Screenshot showing how to specify encoding in Java LoadOptions
og_title: Come specificare la codifica in Java con Aspose.Words – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  headline: How to specify encoding when loading a document with Aspose.Words for
    Java
  type: TechArticle
- description: Learn how to specify encoding in Java using LoadOptions. This guide
    covers character encoding, setEncoding method, and document loading options.
  name: How to specify encoding when loading a document with Aspose.Words for Java
  steps:
  - name: 5.1 Loading from an `InputStream`
    text: 'Sometimes you receive a document as a stream (e.g., from a web service).
      You can still control the encoding by passing the stream together with `LoadOptions`:'
  - name: 5.2 Fallback when the encoding is unknown
    text: If you cannot determine the source file’s charset, you can attempt a detection
      library (such as ICU4J) before setting the encoding. Once you have a guess,
      invoke `setEncoding` with that value. This approach reduces the risk of mis‑decoded
      text.
  - name: 5.3 Dealing with unsupported encodings
    text: Java supports a wide range of code pages, but a few legacy encodings may
      be missing. In that case, consider converting the file to UTF‑8 externally (e.g.,
      using `iconv`) before loading it with Aspose.Words. After conversion, you can
      omit the `setEncoding` call because UTF‑8 is the default for most m
  type: HowTo
tags:
- Java
- Encoding
- Aspose.Words
title: Come specificare la codifica durante il caricamento di un documento con Aspose.Words
  per Java
url: /it/java/document-loading-and-saving/how-to-specify-encoding-when-loading-a-document-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come specificare la codifica quando si carica un documento con Aspose.Words per Java

Se hai bisogno di **come specificare la codifica** per un file sorgente in Java, questo tutorial ti mostra i passaggi esatti. Che il documento utilizzi Big5, UTF‑8 o un altro set di caratteri, puoi controllare il processo di lettura con `LoadOptions`. Alla fine della guida comprenderai perché la codifica dei caratteri è importante, come applicare il metodo `setEncoding` e come verificare che il documento venga caricato correttamente.

Caricare un documento con la corretta codifica dei caratteri evita testo illeggibile e garantisce che i contenuti multilingue vengano visualizzati come previsto. Questo tutorial copre:

* Il ruolo della **codifica dei caratteri in Java** durante la lettura dei file.
* Come configurare la **codifica di LoadOptions** per Aspose.Words.
* Codice pratico che puoi copiare nel tuo progetto.
* Problemi comuni come codifiche non corrispondenti e come risolverli.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* Java Development Kit (JDK) 8 o superiore.
* Maven o Gradle per gestire le dipendenze.
* Aspose.Words per Java 23.10 o successivo (la versione usata in questa guida).
* Un documento di testo di esempio (`input.doc`) salvato con la codifica desiderata (ad es., Big5).

Non hai bisogno di librerie aggiuntive; l'esempio utilizza solo l'API core di Aspose.Words.

## Passo 1: Aggiungi Aspose.Words al tuo progetto

Se usi Maven, aggiungi la seguente dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.10</version>
    <classifier>jdk17</classifier>
</dependency>
```

Per Gradle, inserisci questa riga nel tuo `build.gradle`:

```gradle
implementation 'com.aspose:aspose-words:23.10:jdk17'
```

L'inclusione della libreria rende disponibili le classi `LoadOptions`, `Document` e `Encoding`.

## Passo 2: Crea un'istanza di `LoadOptions`

`LoadOptions` ti consente di personalizzare come Aspose.Words apre un file. Creare l'oggetto è la prima parte di **come specificare la codifica**.

```java
// Step 2: Create load options to customize how the document is opened
LoadOptions loadOptions = new LoadOptions();
```

L'oggetto `LoadOptions` inizia con le impostazioni predefinite. Regolerai le sue proprietà nel passaggio successivo.

## Passo 3: Imposta la codifica dei caratteri desiderata

Il metodo `setEncoding` definisce la **codifica dei caratteri in Java** che il loader deve utilizzare. In questo esempio scegliamo la pagina di codice Big5, comune per i file di testo in cinese tradizionale.

```java
// Step 3: Specify the character encoding (Big5) for the source file
loadOptions.setEncoding(Encoding.getEncoding("Big5"));
```

*Perché è importante*: Se i byte del file vengono interpretati con la pagina di codice errata, i caratteri appaiono come punti interrogativi o spazzatura. Chiamando esplicitamente `setEncoding`, indichi ad Aspose.Words di decodificare il flusso di byte usando la tabella di mappatura Big5.

Puoi sostituire `"Big5"` con qualsiasi nome di charset riconosciuto da Java, come `"UTF-8"`, `"ISO-8859-1"` o `"Windows-1252"`. Il metodo lancia `UnsupportedEncodingException` se il nome non è valido, quindi potresti voler gestire quell'eccezione nel codice di produzione.

## Passo 4: Carica il documento con le opzioni configurate

Ora che la **codifica di LoadOptions** è impostata, passa le opzioni al costruttore `Document`. Questo passaggio completa il flusso principale di **come specificare la codifica**.

```java
// Step 4: Load the document using the configured options
Document doc = new Document("YOUR_DIRECTORY/input.doc", loadOptions);
```

Sostituisci `YOUR_DIRECTORY` con il percorso assoluto o relativo al tuo file. L'istanza `Document` ora contiene il contenuto completamente analizzato, rispettando la codifica fornita.

## Passo 5: Verifica che il testo venga caricato correttamente

Una rapida verifica ti aiuta a garantire che la codifica sia stata applicata come previsto. Puoi estrarre il testo del documento e stamparlo sulla console:

```java
// Step 5: Output the document text to verify correct decoding
System.out.println(doc.getText());
```

Se la console mostra caratteri cinesi leggibili (o la lingua che ti aspetti), la codifica è avvenuta con successo. Se vedi ancora output illeggibile, ricontrolla la codifica del file originale e conferma che il nome del charset corrisponda esattamente.

## Gestione dei casi limite comuni

### 5.1 Caricamento da un `InputStream`

A volte ricevi un documento come stream (ad es., da un servizio web). Puoi comunque controllare la codifica passando lo stream insieme a `LoadOptions`:

```java
try (InputStream stream = new FileInputStream("YOUR_DIRECTORY/input.doc")) {
    Document docFromStream = new Document(stream, loadOptions);
    System.out.println(docFromStream.getText());
}
```

Le stesse **opzioni di caricamento del documento** si applicano, e la chiamata a `setEncoding` rimane invariata.

### 5.2 Fallback quando la codifica è sconosciuta

Se non riesci a determinare il charset del file sorgente, puoi provare una libreria di rilevamento (come ICU4J) prima di impostare la codifica. Una volta ottenuta una ipotesi, invoca `setEncoding` con quel valore. Questo approccio riduce il rischio di testo decodificato in modo errato.

### 5.3 Gestione delle codifiche non supportate

Java supporta un'ampia gamma di pagine di codice, ma alcune codifiche legacy potrebbero mancare. In tal caso, considera di convertire il file in UTF‑8 esternamente (ad es., usando `iconv`) prima di caricarlo con Aspose.Words. Dopo la conversione, puoi omettere la chiamata a `setEncoding` perché UTF‑8 è il valore predefinito per la maggior parte delle API moderne.

## Consiglio professionale: Riutilizza `LoadOptions` per l'elaborazione batch

Se devi caricare molti documenti che condividono lo stesso charset, crea una singola istanza di `LoadOptions` e riutilizzala:

```java
LoadOptions sharedOptions = new LoadOptions();
sharedOptions.setEncoding(Encoding.getEncoding("Big5"));

String[] files = {"doc1.doc", "doc2.doc", "doc3.doc"};
for (String file : files) {
    Document d = new Document("YOUR_DIRECTORY/" + file, sharedOptions);
    // Process each document...
}
```

Riutilizzare l'oggetto riduce l'overhead di creazione degli oggetti e garantisce una codifica coerente per tutto il batch.

## Esempio completo eseguibile

Di seguito è riportato il programma completo che incorpora tutti i passaggi, include gli import necessari e gestisce le potenziali eccezioni.

```java
import com.aspose.words.Document;
import com.aspose.words.LoadOptions;
import com.aspose.words.Encoding;

import java.io.FileInputStream;
import java.io.InputStream;
import java.io.UnsupportedEncodingException;

public class LoadDocumentWithEncoding {
    public static void main(String[] args) {
        // Path to the input document
        String inputPath = "YOUR_DIRECTORY/input.doc";

        try {
            // Create LoadOptions and set the desired charset (Big5 in this case)
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setEncoding(Encoding.getEncoding("Big5"));

            // Load the document using the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Output the document text to verify correct decoding
            System.out.println("Document text:");
            System.out.println(doc.getText());

            // Optional: load from InputStream using the same options
            try (InputStream stream = new FileInputStream(inputPath)) {
                Document docFromStream = new Document(stream, loadOptions);
                System.out.println("Text from stream:");
                System.out.println(docFromStream.getText());
            }

        } catch (UnsupportedEncodingException e) {
            System.err.println("The specified encoding is not supported: " + e.getMessage());
        } catch (Exception e) {
            System.err.println("Error loading document: " + e.getMessage());
        }
    }
}
```

**Output previsto** (supponendo che il file sorgente contenga testo cinese codificato in Big5):

```
Document text:
【此處顯示正確的中文內容】...
Text from stream:
【此處顯示正確的中文內容】...
```

Se l'output mostra simboli illeggibili, rivedi il nome del charset o verifica la codifica originale del file.

## Domande frequenti

**Funziona con altri formati di documento (DOCX, RTF, HTML)?**  
Sì. Lo stesso oggetto `LoadOptions` si applica a qualsiasi formato supportato da Aspose.Words. L'unico requisito è che il file sottostante utilizzi effettivamente il charset specificato.

**Cosa succede se devo cambiare la codifica dopo che il documento è stato caricato?**  
La codifica influisce solo sulla fase di lettura. Una volta che l'oggetto `Document` esiste, la sua rappresentazione Unicode interna è indipendente dal charset originale. Per cambiare la codifica di output, regola le `SaveOptions` quando scrivi il file.

**Posso usare questo approccio con altre librerie (ad es., Apache POI)?**  
Apache POI gestisce la propria rilevazione del charset per i formati binari più vecchi, ma il concetto di fornire un charset a un loader è simile. Per Aspose.Words, `LoadOptions` è il modo ufficiale per controllare **come specificare la codifica**.

## Conclusione

Ora sai **come specificare la codifica** quando carichi un documento con Aspose.Words per Java. Creando un oggetto `LoadOptions`, chiamando il metodo `setEncoding` e passando le opzioni al costruttore `Document`, garantisci che i byte del file vengano interpretati correttamente. Questa pratica elimina il testo illeggibile, supporta contenuti multilingue e si integra senza problemi con l'elaborazione batch o i flussi di lavoro basati su stream.

Esplora argomenti correlati come **opzioni di caricamento del documento**, **salvataggio con codifiche specifiche** e **gestione di Unicode in Java** per approfondire la tua padronanza dell'elaborazione del testo. Sperimenta con diversi nomi di charset, combina l'approccio con la conversione PDF o integralo in un servizio web che accetta upload in varie codifiche.

Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to Convert RTF Text with UTF-8 Encoding in Java Using Aspose.Words](/words/english/java/document-operations/load-rtf-with-utf8-java-asposewords/)
- [How to set options in Aspose.Words for Java – complete guide](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Recover Corrupted DOCX Word Document Using Aspose.Words LoadOptions – Java Guide](/words/english/java/document-loading-and-saving/recover-corrupted-word-document-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}