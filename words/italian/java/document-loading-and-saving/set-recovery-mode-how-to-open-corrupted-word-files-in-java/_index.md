---
category: general
date: 2025-12-23
description: Imposta la modalità di recupero per ripristinare i documenti Word danneggiati.
  Scopri come aprire i file DOCX, utilizzare la modalità di recupero e gestire i file
  corrotti in Java.
draft: false
keywords:
- set recovery mode
- recover damaged word
- how to open docx
- open corrupted word file
- use recovery mode
language: it
og_description: Imposta la modalità di recupero per ripristinare i documenti Word
  danneggiati. Questa guida mostra come aprire i file DOCX, utilizzare la modalità
  di recupero e gestire i file corrotti in Java.
og_title: Imposta la modalità di recupero – Apri file Word corrotti con Java
tags:
- Java
- Aspose.Words
- Document Recovery
title: Imposta la modalità di recupero – Come aprire file Word corrotti in Java
url: /it/java/document-loading-and-saving/set-recovery-mode-how-to-open-corrupted-word-files-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta la modalità di recupero – Come aprire file Word corrotti in Java

Mai provato a **impostare la modalità di recupero** su un documento Word che si rifiuta di aprirsi? Non sei solo. Molti sviluppatori si trovano in difficoltà quando un DOCX è leggermente corrotto e il consueto `new Document("file.docx")` genera un'eccezione. La buona notizia? Aspose.Words per Java ti offre un modo integrato per **usare la modalità di recupero** e effettivamente **recuperare file Word danneggiati**.

In questo tutorial ti guideremo attraverso tutto ciò che devi sapere per **aprire in modo sicuro file Word corrotti**, dalla configurazione di `LoadOptions` alla gestione dei casi limite che di solito creano problemi. Nessun superfluo—solo una soluzione pratica, passo‑per‑passo, da incollare subito nel tuo progetto.

> **Suggerimento:** Se stai gestendo solo piccoli difetti (come un piè di pagina mancante), la modalità di recupero **Tolerant** è di solito sufficiente. Riserva **Strict** per situazioni in cui è necessario che il documento sia al 100 % pulito prima dell'elaborazione.

## Di cosa avrai bisogno

- **Java 17** (o qualsiasi JDK recente; l'API funziona allo stesso modo)
- **Aspose.Words for Java** 23.9 (o più recente) – la libreria che fornisce la classe `LoadOptions`.
- Un file **DOCX corrotto** per i test (puoi crearne uno troncando un file valido con un editor esadecimale).
- Il tuo IDE preferito (IntelliJ, Eclipse, VS Code—scegli quello che ti è più comodo).

È tutto. Nessun plugin Maven aggiuntivo, nessuna utility esterna. Solo la libreria principale e un po' di codice.

![Illustrazione dell'impostazione della modalità di recupero nell'API Java di Aspose.Words](/images/set-recovery-mode-java.png){.align-center alt="imposta modalità di recupero"}

## Passo 1 – Crea un'istanza di `LoadOptions`

La prima cosa da fare è istanziare un oggetto `LoadOptions`. Pensalo come una cassetta degli attrezzi che indica ad Aspose.Words **come trattare il file in ingresso**.

```java
import com.aspose.words.LoadOptions;

// Step 1: Create LoadOptions with default settings
LoadOptions loadOptions = new LoadOptions();
```

Perché non saltare questo passo? Perché senza un `LoadOptions` non puoi indicare alla libreria se desideri **usare la modalità di recupero** o meno. Il comportamento predefinito è strict, il che significa che qualsiasi corruzione interrompe il caricamento.

## Passo 2 – Scegli la modalità di recupero corretta

Aspose.Words offre due valori enum:

| Modalità | Cosa fa |
|------|--------------|
| `RecoveryMode.Tolerant` | Tenta di recuperare il più possibile. Ideale per scenari di *recupero di Word danneggiato* in cui l'unico problema è uno stile mancante o una relazione rotta. |
| `RecoveryMode.Strict`   | Interrompe rapidamente al primo problema. Usala quando hai bisogno della garanzia che il documento sia intatto prima di ulteriori elaborazioni. |

Imposta la modalità con una singola riga:

```java
import com.aspose.words.RecoveryMode;

// Step 2: Tell the loader to be forgiving
loadOptions.setRecoveryMode(RecoveryMode.Tolerant); // or RecoveryMode.Strict
```

**Perché è importante:** Quando **usi la modalità di recupero**, la libreria ripara internamente le parti rotte, ricostruisce i nodi XML mancanti e ti fornisce un oggetto `Document` utilizzabile. In modalità *strict* otterresti invece un `InvalidFormatException`.

## Passo 3 – Carica il documento con le tue opzioni

Ora consegni finalmente il file ad Aspose.Words, passando le `LoadOptions` appena configurate.

```java
import com.aspose.words.Document;

// Step 3: Load the (potentially corrupted) DOCX
String filePath = "C:/Documents/corrupted.docx";
Document doc = new Document(filePath, loadOptions);
```

Se il file è solo leggermente corrotto, `doc` sarà un oggetto `Document` pienamente funzionale. Ora puoi:

- Leggere il testo (`doc.getText()`),
- Salvare in un altro formato (`doc.save("repaired.pdf")`),
- O anche ispezionare l'elenco delle parti recuperate tramite l'API `Document`.

### Verifica del recupero

Un rapido controllo di coerenza ti aiuta a confermare che il recupero sia effettivamente riuscito:

```java
if (doc.getSections().getCount() > 0) {
    System.out.println("Document loaded successfully – recovery mode worked!");
} else {
    System.out.println("No sections found – the file might be beyond repair.");
}
```

## Passo 4 – Gestione dei casi limite

### 4.1 Quando Tolerant non è sufficiente

A volte un file è così danneggiato che anche la modalità **Tolerant** non riesce a ricomporlo (ad esempio, l'XML principale è mancante). In questi rari casi, puoi:

1. **Provare un secondo caricamento con `RecoveryMode.Strict`** per vedere se il messaggio di errore fornisce più dettagli.
2. **Ritirarsi a un'utilità zip** per estrarre manualmente le parti XML e ripararle.
3. **Registrare l'eccezione** e informare l'utente che il documento è irrecuperabile.

```java
try {
    loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
    Document doc = new Document(filePath, loadOptions);
    // proceed with doc
} catch (Exception e) {
    System.err.println("Tolerant mode failed: " + e.getMessage());
    // optional: retry with Strict or alert the user
}
```

### 4.2 Considerazioni sulla memoria

Caricare file DOCX di grandi dimensioni con il recupero abilitato può temporaneamente raddoppiare l'uso della memoria perché Aspose.Words mantiene sia le strutture originali sia quelle riparate in memoria. Se stai elaborando grandi lotti:

- **Riutilizza la stessa istanza di `LoadOptions`** invece di crearne una nuova ogni volta.
- **Rilascia il `Document`** (`doc.close()`) non appena hai finito.
- **Esegui su una JVM con heap sufficiente** (`-Xmx2g` o superiore per file multi‑gigabyte).

### 4.3 Salvataggio del file riparato

Dopo un caricamento riuscito, potresti voler **salvare la versione pulita** così da non dover più eseguire il recupero.

```java
String repairedPath = "C:/Documents/repaired.docx";
doc.save(repairedPath);
System.out.println("Repaired file saved to: " + repairedPath);
```

Ora, la prossima volta che apri `repaired.docx` potrai saltare completamente il passo **use recovery mode**.

## Domande frequenti

**D: Funziona anche per i vecchi file `.doc`?**  
R: Sì. Lo stesso approccio con `LoadOptions` si applica a `.doc` e `.rtf`. Basta cambiare l'estensione del file.

**D: Posso combinare `setRecoveryMode` con altre opzioni di caricamento (ad esempio, password)?**  
R: Assolutamente. `LoadOptions` ha proprietà come `setPassword` e `setLoadFormat`. Impostale prima di chiamare `setRecoveryMode`.

**D: C'è qualche penalità di prestazioni?**  
R: Leggermente—il recupero aggiunge un overhead di parsing. Nei benchmark, un file corrotto da 5 MB viene caricato circa il 30 % più lentamente in modalità **Tolerant** rispetto al caricamento strict di un file pulito. Restano comunque accettabili per la maggior parte dei lavori batch.

## Esempio completo funzionante

Di seguito trovi una classe Java completa, pronta per l'esecuzione, che dimostra **come aprire docx**, **usare la modalità di recupero** e **salvare una copia riparata**.

```java
package com.example.recovery;

import com.aspose.words.*;

public class RecoverCorruptedDocx {
    public static void main(String[] args) {
        // Path to the possibly corrupted DOCX
        String inputPath = "C:/Documents/corrupted.docx";
        // Where the repaired file will be saved
        String outputPath = "C:/Documents/repaired.docx";

        // 1️⃣ Create LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Choose recovery mode – Tolerant is usually enough
        loadOptions.setRecoveryMode(RecoveryMode.Tolerant);
        // If you need strict validation, switch to RecoveryMode.Strict

        try {
            // 3️⃣ Load the document with the configured options
            Document doc = new Document(inputPath, loadOptions);

            // Quick sanity check
            if (doc.getSections().getCount() > 0) {
                System.out.println("✅ Document loaded – recovery succeeded.");
            } else {
                System.out.println("⚠️ No sections found – the file may be beyond repair.");
            }

            // 4️⃣ (Optional) Save a clean copy for future use
            doc.save(outputPath);
            System.out.println("💾 Repaired file saved to: " + outputPath);
        } catch (Exception e) {
            // Handle cases where even tolerant mode fails
            System.err.println("❌ Failed to load document: " + e.getMessage());
            // You could retry with Strict or log for further analysis
        }
    }
}
```

Esegui questa classe dopo aver aggiunto il JAR di Aspose.Words per Java al classpath del tuo progetto. Se il file di input è solo leggermente danneggiato, vedrai il messaggio **✅** e un nuovo `repaired.docx` sul disco.

## Conclusione

Abbiamo coperto tutto ciò che ti serve per **impostare la modalità di recupero** e aprire con successo file **Word corrotti** in Java. Creando un oggetto `LoadOptions`, selezionando il `RecoveryMode` appropriato e gestendo i rari casi limite, puoi trasformare un frustrante “il file non si apre” in un flusso di lavoro di recupero fluido.

Ricorda:

- **Tolerant** è la tua scelta per la maggior parte degli scenari di *recupero di Word danneggiato*.  
- **Strict** ti fornisce un fallimento immediato quando hai bisogno di assoluta certezza.  
- Verifica sempre il documento caricato e, se possibile, salva una copia pulita per le esecuzioni future.

Ora puoi rispondere con sicurezza a “**come aprire docx** che rifiuta di caricarsi?” con uno snippet di codice concreto e una spiegazione chiara. Buona programmazione, e che i tuoi documenti rimangano sani!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}