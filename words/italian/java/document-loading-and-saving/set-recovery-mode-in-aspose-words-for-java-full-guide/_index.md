---
category: general
date: 2026-07-03
description: Imposta la modalità di recupero per ripristinare i file Word corrotti
  in Java e visualizza il conteggio delle pagine dopo il caricamento. Impara passo
  passo con Aspose.Words.
draft: false
keywords:
- set recovery mode
- display page count
- recover corrupted word
- Aspose.Words Java
- document loading options
language: it
og_description: Imposta la modalità di recupero in Aspose.Words per Java per recuperare
  file Word corrotti e visualizzare il conteggio delle pagine. Segui l'esempio completo
  ora.
og_title: Imposta la modalità di recupero in Aspose.Words per Java – Tutorial completo
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  headline: Set Recovery Mode in Aspose.Words for Java – Full Guide
  type: TechArticle
- description: Set recovery mode to recover corrupted Word files in Java and display
    page count after loading. Learn step‑by‑step with Aspose.Words.
  name: Set Recovery Mode in Aspose.Words for Java – Full Guide
  steps:
  - name: Why `RecoveryMode.PARSE`?
    text: '- **PARSE** – Aspose.Words parses whatever fragments it can understand,
      stitching together a partially functional document. Ideal when you need *any*
      content out of a broken file. - **SKIP** – The library skips over corrupted
      sections entirely, which can be faster but may discard more data.'
  - name: 1️⃣ Corrupted Header/Footer Sections
    text: Sometimes only the main body parses while headers and footers are lost.
      If you rely on those for branding, you may need to re‑inject them after recovery.
  - name: 2️⃣ Images That Won’t Load
    text: Embedded images often get stripped out when the zip container (the underlying
      `.docx` format) is damaged. You can catch this by iterating over `doc.getSections()`
      and checking `Section.getBody().getParagraphs()` for `Shape` objects.
  - name: 3️⃣ Large Documents and Memory
    text: Recovering a 200‑page corrupted file can be memory‑intensive. Consider increasing
      the JVM heap size (`-Xmx2g`) when you anticipate huge documents.
  - name: 4️⃣ License Restrictions
    text: The evaluation version caps certain features, but **recovery** is fully
      functional. However, the printed page count may be limited to a few pages in
      the trial. Always test with a licensed build for production.
  - name: Maven `pom.xml` snippet
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> </dependency> ```'
  - name: Java source file `RecoveryModeDemo.java`
    text: '```java import com.aspose.words.*;'
  type: HowTo
- questions:
  - answer: That usually means the file is beyond salvage—perhaps the zip container
      is completely broken. In such cases, you might need a third‑party repair tool
      before handing it to Aspose.Words.
    question: What if `RecoveryMode.PARSE` still throws an exception?
  - answer: 'Absolutely. Implement `IWarningCallback` to capture any warnings Aspose.Words
      emits during the parsing process. This gives you insight into which parts were
      skipped. ```java loadOptions.setWarningCallback(new IWarningCallback() { public
      void warning(WarningInfo info) { System.out.println("Warning: "'
    question: Can I combine `RecoveryMode.PARSE` with custom document loading callbacks?
  - answer: 'No. Aspose.Words works on a copy in memory; the source file remains untouched
      unless you explicitly call `doc.save()`. --- ## ## Wrap‑Up We’ve covered how
      to **set recovery mode** in Aspose.Words for Java, why `PARSE` is generally
      the best choice for salvaging a broken document, and how to **display'
    question: Does changing the recovery mode affect the original file?
  type: FAQPage
tags:
- Java
- Aspose.Words
- Word recovery
title: Imposta la modalità di ripristino in Aspose.Words per Java – Guida completa
url: /it/java/document-loading-and-saving/set-recovery-mode-in-aspose-words-for-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Impostare la modalità di recupero in Aspose.Words per Java – Guida completa

Ti sei mai chiesto come **impostare la modalità di recupero** quando carichi un file `.docx` danneggiato con Aspose.Words? Non sei l’unico a grattarsi la testa davanti a documenti Word corrotti che rifiutano di aprirsi. In questo tutorial vedremo esattamente come configurare la libreria per **recuperare file Word corrotti** e poi **visualizzare il conteggio delle pagine** del contenuto caricato con successo.

Copriamo tutto, dal piccolo aggiustamento di `LoadOptions` fino all’ultimo `System.out.println` che ti dice quante pagine sono sopravvissute alla missione di salvataggio. Nessun superfluo, solo una soluzione pratica pronta al copia‑incolla che funziona con l’ultima release Aspose.Words 23.12.

## Cosa imparerai

- Perché la modalità di recupero è importante e quali opzioni offre Aspose.Words.  
- Come **impostare la modalità di recupero** programmaticamente usando Java.  
- Modi per **visualizzare il conteggio delle pagine** dopo il caricamento del documento, confermando che il recupero è riuscito.  
- Trappole comuni nella gestione di file Word corrotti e come evitarle.  

Prima di immergerci, assicurati di avere:

1. Una licenza valida di Aspose.Words per Java (o una chiave di valutazione temporanea).  
2. Java 17 o superiore installato sulla tua macchina.  
3. Il file `Corrupted.docx` corrotto che vuoi testare.  

Li hai? Ottimo—mettiamoci al lavoro.

> **Consiglio professionale:** Anche se usi una versione di prova, le funzionalità di recupero funzionano esattamente allo stesso modo di una build con licenza.

---

## ## Come impostare la modalità di recupero con Aspose.Words per Java

Il cuore della soluzione vive nella classe `LoadOptions`. Per impostazione predefinita Aspose.Words fa del suo meglio per caricare un documento, ma quando il file è gravemente danneggiato devi indicargli *come* comportarsi. È qui che entra in gioco **impostare la modalità di recupero**.

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a LoadOptions instance – this object holds all the loading preferences.
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose the recovery mode. PARSE attempts to salvage as much as possible,
        //    while SKIP simply skips unreadable parts.
        loadOptions.setRecoveryMode(RecoveryMode.PARSE);

        // 3️⃣ Load the document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 4️⃣ Finally, display the number of pages that were successfully recovered.
        System.out.println("Document loaded, page count = " + doc.getPageCount());
    }
}
```

### Perché `RecoveryMode.PARSE`?

- **PARSE** – Aspose.Words analizza tutti i frammenti che riesce a comprendere, ricucendo un documento parzialmente funzionale. Ideale quando ti serve *qualsiasi* contenuto da un file rotto.  
- **SKIP** – La libreria salta completamente le sezioni corrotte, il che può essere più veloce ma potrebbe scartare più dati.  

Nella maggior parte degli scenari reali, **PARSE** è la scelta più sicura perché massimizza la quantità di testo, immagini e formattazione recuperabili.

---

## ## Visualizzare il conteggio delle pagine dopo il recupero

Una volta caricato il documento, il passo logico successivo è verificare il successo dell’operazione. La metrica più semplice, ma anche la più informativa, è il conteggio delle pagine. Il metodo `Document.getPageCount()` fa esattamente questo.

```java
int pages = doc.getPageCount();
System.out.println("Document loaded, page count = " + pages);
```

Se il file era completamente illeggibile, Aspose.Words lancerà un’eccezione *prima* di arrivare a questa riga. Quando vedi un conteggio di pagine pari a `0` o un numero molto basso, di solito significa che la modalità di recupero ha dovuto scartare grandi blocchi del file originale.

**Output previsto (esempio):**

```
Document loaded, page count = 12
```

Questo ti indica che la libreria è riuscita a ricostruire dodici pagine dalla sorgente corrotta—un risultato piuttosto solido per un `.docx` danneggiato.

---

## ## Casi limite e trappole comuni

### 1️⃣ Sezioni intestazione/piè di pagina corrotte
A volte solo il corpo principale viene analizzato mentre intestazioni e piè di pagina vanno persi. Se ti affidi a questi per il branding, potresti doverli reinserire dopo il recupero.

### 2️⃣ Immagini che non si caricano
Le immagini incorporate spesso vengono rimosse quando il contenitore zip (il formato `.docx` sottostante) è danneggiato. Puoi rilevare ciò iterando su `doc.getSections()` e controllando `Section.getBody().getParagraphs()` per oggetti `Shape`.

```java
for (Section sec : doc.getSections()) {
    for (Paragraph para : sec.getBody().getParagraphs()) {
        for (Node node : para.getChildNodes(NodeType.SHAPE, true)) {
            Shape shape = (Shape) node;
            System.out.println("Found image: " + shape.getName());
        }
    }
}
```

Se il ciclo non stampa nulla, probabilmente la modalità di recupero ha saltato le immagini.

### 3️⃣ Documenti di grandi dimensioni e memoria
Recuperare un file corrotto di 200 pagine può richiedere molta memoria. Considera di aumentare la dimensione dell'heap JVM (`-Xmx2g`) quando prevedi documenti di grandi dimensioni.

### 4️⃣ Restrizioni di licenza
La versione di valutazione limita alcune funzionalità, ma **il recupero** è pienamente operativo. Tuttavia, il conteggio delle pagine stampato potrebbe essere limitato a poche pagine nella versione di prova. Testa sempre con una build con licenza per la produzione.

---

## ## Esempio completo end‑to‑end (eseguibile)

Di seguito trovi un programma autonomo che puoi inserire in qualsiasi progetto Maven o Gradle. Include la dichiarazione della dipendenza necessaria per Aspose.Words 23.12.

### Snippet Maven `pom.xml`

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### File sorgente Java `RecoveryModeDemo.java`

```java
import com.aspose.words.*;

public class RecoveryModeDemo {
    public static void main(String[] args) {
        try {
            // Initialize load options
            LoadOptions loadOptions = new LoadOptions();

            // Set recovery mode to PARSE – this is the key step to recover corrupted Word files.
            loadOptions.setRecoveryMode(RecoveryMode.PARSE);

            // Load the possibly damaged document
            Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

            // Display the page count to confirm how much content was recovered.
            System.out.println("Document loaded, page count = " + doc.getPageCount());

            // (Optional) Save the recovered document for further inspection.
            doc.save("YOUR_DIRECTORY/Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Cosa fa questo codice:**

1. **Imposta la modalità di recupero** – il fulcro del nostro tutorial.  
2. Carica il file corrotto usando le `LoadOptions` configurate.  
3. **Visualizza il conteggio delle pagine**, fornendoti un feedback immediato.  
4. Salva una versione pulita (`Recovered.docx`) così da poterla aprire in Word in seguito.

Esegui il programma con:

```bash
javac -cp "path/to/aspose-words-23.12.jar" RecoveryModeDemo.java
java -cp ".:path/to/aspose-words-23.12.jar" RecoveryModeDemo
```

Dovresti vedere il conteggio delle pagine stampato sulla console, confermando che il recupero è riuscito.

---

## ## Panoramica visiva (Immagine)

![set recovery mode flow diagram](https://example.com/images/recovery-mode-flow.png "Diagram illustrating how set recovery mode works in Aspose.Words for Java")

*Il testo alternativo include la parola chiave principale **set recovery mode** per soddisfare la SEO.*

---

## ## Domande frequenti

**D: Cosa succede se `RecoveryMode.PARSE` lancia ancora un’eccezione?**  
R: Di solito significa che il file è oltre la possibilità di salvataggio—potrebbe essere il contenitore zip completamente rotto. In questi casi potresti aver bisogno di uno strumento di riparazione di terze parti prima di passarlo ad Aspose.Words.

**D: Posso combinare `RecoveryMode.PARSE` con callback personalizzati per il caricamento del documento?**  
R: Assolutamente sì. Implementa `IWarningCallback` per catturare gli avvisi che Aspose.Words emette durante il processo di parsing. Questo ti dà visibilità su quali parti sono state saltate.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    public void warning(WarningInfo info) {
        System.out.println("Warning: " + info.getDescription());
    }
});
```

**D: Cambiare la modalità di recupero influisce sul file originale?**  
R: No. Aspose.Words lavora su una copia in memoria; il file sorgente rimane intatto a meno che non chiami esplicitamente `doc.save()`.

---

## ## Conclusione

Abbiamo coperto come **impostare la modalità di recupero** in Aspose.Words per Java, perché `PARSE` è generalmente la scelta migliore per salvare un documento rotto, e come **visualizzare il conteggio delle pagine** per verificare il risultato. Seguendo l’esempio completo, ora disponi di una soluzione pronta all’uso che può **recuperare file Word corrotti** e darti un feedback immediato sul successo dell’operazione.

Passi successivi? Prova a sostituire `RecoveryMode.SKIP` per vedere la differenza, sperimenta con file multi‑sezione di grandi dimensioni, o integra la logica in un servizio web che ripara automaticamente i documenti caricati dagli utenti. Lo stesso schema funziona per PDF (usando Aspose.PDF) e anche per il recupero di testo semplice con altre librerie—ricorda sempre l’idea di base: configura il loader, tenta il recupero, quindi valida con una metrica semplice come il conteggio delle pagine.

Buon coding, e che i tuoi documenti rimangano integri!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Aspose.Words Java: Comprehensive Guide to Word Document Processing](/words/english/java/document-operations/aspose-words-java-master-word-processing/)
- [Combine Multiple Word Files with Aspose.Words for Java](/words/english/java/document-manipulation/cloning-and-combining-documents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}