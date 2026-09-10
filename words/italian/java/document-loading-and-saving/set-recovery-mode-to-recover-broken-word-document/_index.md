---
category: general
date: 2026-02-15
description: Impostare la modalità di recupero consente di caricare il documento con
  il recupero, facilitando il recupero di documenti Word danneggiati e la correzione
  degli errori di recupero del documento Word.
draft: false
keywords:
- set recovery mode
- recover broken word document
- load document with recovery
- recover word document errors
language: it
og_description: Impostare la modalità di recupero è la chiave per caricare un documento
  con il recupero, consentendo di recuperare gli errori di documenti Word danneggiati
  in Java.
og_title: Imposta modalità di recupero – Recupera rapidamente un documento Word danneggiato
tags:
- Aspose.Words
- Java
- Document Recovery
title: Imposta la modalità di recupero per ripristinare un documento Word danneggiato.
url: /it/java/document-loading-and-saving/set-recovery-mode-to-recover-broken-word-document/
---

markdown formatting.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set recovery mode – Come recuperare un documento Word danneggiato con Aspose.Words

Hai mai provato ad aprire un file Word che improvvisamente si rifiuta di caricarsi? Potresti trovarti davanti a un *.docx* corrotto e chiederti se devi ricominciare da capo. La buona notizia? **set recovery mode** in Aspose.Words ti offre un modo elegante per *load document with recovery* e mantenere intatta la maggior parte del contenuto.  

In questo tutorial imparerai esattamente come **set recovery mode**, perché l'opzione *RELAXED* è solitamente la scelta migliore per file danneggiati, e come gestire gli occasionali *recover word document errors* che sfuggono comunque. Nessuno strumento esterno, solo Java puro e qualche riga di codice.

> **Cosa otterrai:** un esempio completo e eseguibile che carica un file Word corrotto, salta le parti illeggibili e ti lascia con un oggetto `Document` utilizzabile pronto per ulteriori elaborazioni.

---

## Prerequisiti

- **Aspose.Words for Java** (v24.9 o più recente) aggiunto al tuo progetto tramite Maven o un JAR manuale.
- Un file **corrupted .docx** che vuoi testare (lo chiameremo `Corrupted.docx`).
- Conoscenze di base di Java – non è necessario essere un mago dell'elaborazione di Word, basta sentirsi a proprio agio con un metodo `main`.

Se ti manca qualcuno di questi, scarica l'ultimo JAR di Aspose.Words dal [sito ufficiale](https://products.aspose.com/words/java) e aggiungilo al tuo classpath. Tutto qui—nessuna dipendenza aggiuntiva.

---

## Passo 1: Comprendere le modalità di recupero

| Mode | Behavior | When to use |
|------|----------|------------|
| **RELAXED** | Salta le parti illeggibili, mantiene il resto. | La maggior parte dei file corrotti – vuoi **recover broken word document** senza eccezione. |
| **STRICT** | Lancia un'eccezione su qualsiasi errore. | Quando è necessario garantire un caricamento perfetto e privo di errori (raro per sorgenti corrotti). |

> **Consiglio professionale:** *RELAXED* è il valore predefinito per scenari “ottieni qualcosa indietro”, mentre *STRICT* è utile in pipeline automatizzate dove un fallimento deve interrompere il processo.

---

## Passo 2: Creare un oggetto `LoadOptions` e **set recovery mode**

Ecco dove la parola chiave principale appare nel codice. Impostiamo esplicitamente **set recovery mode** su un'istanza `LoadOptions` prima di caricare il file.

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions and choose a recovery mode.
        // RELAXED will skip unreadable parts, while STRICT throws an exception.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // <-- set recovery mode

        // 2️⃣ Load the potentially corrupted document using the configured options.
        Document doc = new Document("YOUR_DIRECTORY/Corrupted.docx", loadOptions);

        // 3️⃣ Verify that the document loaded and optionally save a cleaned copy.
        System.out.println("Document loaded successfully. Page count: " + doc.getPageCount());
        doc.save("Recovered.docx");
    }
}
```

**Perché è importante:** chiamando `setRecoveryMode`, indichi ad Aspose.Words quanto aggressivamente debba tentare di recuperare il file. Senza questa chiamata la libreria usa per impostazione predefinita *STRICT*, che interromperebbe al primo segno di problemi—vanificando lo scopo di un flusso di lavoro *recover broken word document*.

---

## Passo 3: Verificare il caricamento – Abbiamo davvero **recover broken word document**?

Dopo il caricamento, puoi ispezionare l'oggetto `Document`:

```java
// Check if any sections were dropped
int sections = doc.getSections().getCount();
System.out.println("Sections recovered: " + sections);
```

Se la console mostra un numero ragionevole di sezioni, hai caricato con successo *load document with recovery*. In pratica, noterai che la maggior parte del testo, delle tabelle e delle immagini sopravvive, mentre le parti corrotte semplicemente scompaiono.

---

## Passo 4: Gestire con eleganza i rimanenti **recover word document errors**

Anche con la modalità *RELAXED*, alcuni casi limite possono ancora generare avvisi. Avvolgi il caricamento in un try‑catch per mantenere viva la tua app:

```java
try {
    Document doc = new Document("Corrupted.docx", loadOptions);
    // Continue processing...
} catch (Exception ex) {
    System.err.println("Recovery failed: " + ex.getMessage());
    // Optionally fallback to a backup copy or notify the user.
}
```

**Quando potrebbe succedere?** Se il file è così danneggiato che anche un parser rilassato non riesce a identificare una struttura di documento valida, Aspose.Words lancerà comunque un'eccezione. In quei rari casi, potresti dover chiedere all'utente di fornire una copia diversa.

---

## Passo 5: Salvare il file recuperato (opzionale)

La maggior parte degli sviluppatori desidera una versione pulita da consegnare ai sistemi a valle. La chiamata `save` qui sotto scrive un nuovo `.docx` che non contiene più i frammenti corrotti.

```java
doc.save("Recovered.docx");
System.out.println("Recovered file saved as Recovered.docx");
```

Ora hai un **recover broken word document** che può essere aperto in Microsoft Word, Google Docs o qualsiasi altro visualizzatore—senza finestre di errore.

---

## Panoramica visiva (Immagine)

![Diagramma che mostra il flusso di set recovery mode – dal file corrotto al documento recuperato](https://example.com/images/recovery-flow.png "diagramma del flusso set recovery mode")

*Il testo alternativo contiene esplicitamente la parola chiave principale, aiutando sia i motori di ricerca che gli screen reader.*

---

## Domande comuni e casi limite

| Question | Answer |
|----------|--------|
| *E se avessi bisogno di conservare le parti corrotte per analisi forense?* | Usa `LoadOptions.setRecoverMode(LoadOptions.RecoveryMode.STRICT)` e cattura l'eccezione. Il messaggio dell'eccezione contiene i dettagli delle parti problematiche. |
| *Posso passare da RELAXED a STRICT a runtime?* | Assolutamente—basta creare una nuova istanza `LoadOptions` con la modalità desiderata prima di ogni caricamento. |
| *Funziona con i vecchi file .doc?* | Sì. Lo stesso `LoadOptions` si applica sia ai formati `.doc` che `.docx`. |
| *C'è un impatto sulle prestazioni?* | Minimo. L'overhead di parsing aggiuntivo è trascurabile rispetto al costo di un caricamento completo del documento. |

---

## Esempio completo funzionante (pronto per copia‑incolla)

```java
import com.aspose.words.*;

public class RecoverWordDocument {
    public static void main(String[] args) {
        try {
            // Step 1 – configure recovery mode
            LoadOptions loadOptions = new LoadOptions();
            loadOptions.setRecoveryMode(LoadOptions.RecoveryMode.RELAXED); // set recovery mode

            // Step 2 – load the corrupted file
            Document doc = new Document("Corrupted.docx", loadOptions);

            // Step 3 – optional verification
            System.out.println("Loaded! Pages: " + doc.getPageCount());

            // Step 4 – save a clean copy
            doc.save("Recovered.docx");
            System.out.println("Saved recovered document as Recovered.docx");
        } catch (Exception e) {
            System.err.println("Failed to recover document: " + e.getMessage());
        }
    }
}
```

Esegui il programma, puntalo al tuo file danneggiato e osserva l'output. Se tutto è andato liscio, vedrai stampato il conteggio delle pagine e apparirà un nuovo `Recovered.docx` accanto al tuo file sorgente.

---

## Conclusione

Abbiamo coperto tutto ciò di cui hai bisogno per **set recovery mode** in Aspose.Words, dalla scelta dell'enum `RecoveryMode` corretto alla gestione dei pochi *recover word document errors* che potrebbero ancora comparire. Seguendo i passaggi sopra, puoi affidabilmente **load document with recovery**, conservare le parti buone di un file corrotto e generare una versione pulita pronta per qualsiasi elaborazione a valle.

Pronto per la prossima sfida? Prova a combinare **set recovery mode** con le API di **document cleaning** di Aspose.Words—rimuovendo paragrafi nascosti, correggendo collegamenti ipertestuali rotti, o persino convertendo il file recuperato in PDF in un unico passaggio. Le possibilità sono infinite, e ora hai una solida base per affrontare i file Word corrotti a testa alta.

Buon coding, e che i tuoi documenti rimangano sani!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}