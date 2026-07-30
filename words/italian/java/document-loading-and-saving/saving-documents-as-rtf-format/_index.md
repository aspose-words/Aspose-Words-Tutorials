---
date: 2025-12-24
description: Scopri come convertire Word in RTF usando Aspose.Words per Java. Questo
  tutorial passo‑passo mostra come caricare un DOCX, configurare le opzioni di salvataggio
  RTF e salvare come testo formattato.
linktitle: Saving Documents as RTF Format
second_title: Aspose.Words Java Document Processing API
title: Converti Word in RTF con il tutorial di Aspose.Words per Java
url: /it/java/document-loading-and-saving/saving-documents-as-rtf-format/
weight: 23
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Converti Word in RTF con Aspose.Words per Java

In questo tutorial imparerai **come convertire Word in RTF** in modo rapido e affidabile usando Aspose.Words per Java. Convertire un DOCX nel formato RTF rich text è una necessità comune quando serve una ampia compatibilità con editor di testo legacy, client di posta elettronica o sistemi di archiviazione documenti. Ti guideremo attraverso il caricamento di un documento Word in Java, la personalizzazione delle opzioni di salvataggio RTF (incluso il salvataggio delle immagini come WMF) e, infine, la scrittura del file di output.

## Risposte rapide
- **Cosa significa “convertire word in rtf”?** Trasforma un file DOCX/Word in Rich Text Format mantenendo testo, stili e, facoltativamente, le immagini.  
- **È necessaria una licenza?** Una versione di prova gratuita è sufficiente per lo sviluppo; per la produzione è richiesta una licenza commerciale.  
- **Quale versione di Java è supportata?** Aspose.Words per Java supporta Java 8 e versioni successive.  
- **Posso mantenere le immagini durante la conversione?** Sì – usa l’opzione `saveImagesAsWmf` per incorporare le immagini come WMF all’interno del RTF.  
- **Quanto tempo richiede la conversione?** Tipicamente meno di un secondo per documenti standard; file più grandi possono richiedere qualche secondo.

## Che cosa è “convertire word in rtf”?
Convertire un documento Word in RTF crea un file indipendente dalla piattaforma che memorizza testo, formattazione e, facoltativamente, immagini in un markup basato su testo semplice. Questo rende il documento visualizzabile in quasi tutti gli editor di testo senza perdere il layout.

## Perché usare Aspose.Words per Java per salvare come rich text?
- **Fedele al 100 %** – Tutte le funzionalità di Word (stili, tabelle, intestazioni/piè di pagina) vengono conservate.  
- **Nessun Microsoft Office richiesto** – Funziona su qualsiasi server o ambiente cloud.  
- **Controllo granulare** – Le opzioni di salvataggio ti permettono di decidere come vengono memorizzate le immagini, quale codifica usare e molto altro.

## Prerequisiti
1. **Libreria Aspose.Words per Java** – Scarica e aggiungi il JAR al tuo progetto da [qui](https://releases.aspose.com/words/java/).  
2. **Un file Word di origine** – Per esempio, `Document.docx` che desideri salvare come RTF.  
3. **Ambiente di sviluppo Java** – JDK 8+ e il tuo IDE preferito.

## Passo 1: Carica il documento Word (load word document java)
Per prima cosa, carica il DOCX esistente in un oggetto `Document`. Questa è la base per qualsiasi conversione.

```java
import com.aspose.words.Document;

// Load the source document (e.g., Document.docx)
Document doc = new Document("path/to/Document.docx");
```

> **Suggerimento:** Usa percorsi assoluti o risorse nel class‑path per evitare `FileNotFoundException`.

## Passo 2: Configura le opzioni di salvataggio RTF (save images as wmf)
Aspose.Words offre la classe `RtfSaveOptions` per affinare l’output. In questo esempio abilitiamo **salvataggio immagini come WMF**, il formato consigliato per i file RTF.

```java
import com.aspose.words.RtfSaveOptions;

// Create an instance of RtfSaveOptions
RtfSaveOptions saveOptions = new RtfSaveOptions();

// Set the option to save images as WMF
saveOptions.setSaveImagesAsWmf(true);
```

Puoi anche modificare altre impostazioni, come `saveOptions.setEncoding(Charset.forName("UTF-8"))` se ti serve una codifica dei caratteri specifica.

## Passo 3: Salva il documento come RTF (save docx as rtf)
Ora scrivi il documento usando le opzioni configurate. Questo passaggio **salva il DOCX come RTF**, producendo un file rich text pronto per la distribuzione.

```java
// Save the document in RTF format

doc.save("path/to/output.rtf", saveOptions);
```

## Codice completo per convertire Word in RTF
Di seguito trovi la versione compatta da copiare‑incollare in una classe Java. Dimostra **il salvataggio come rich text** con l’opzione immagine WMF in un unico blocco.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
RtfSaveOptions saveOptions = new RtfSaveOptions(); { saveOptions.setSaveImagesAsWmf(true); }
doc.save("Your Directory Path" + "WorkingWithRtfSaveOptions.SavingImagesAsWmf.rtf", saveOptions);
```

## Problemi comuni e risoluzione
| Problema | Motivo | Correzione |
|----------|--------|------------|
| RTF di output vuoto | File di origine non trovato o non caricato | Verifica il percorso in `new Document(...)` |
| Immagini mancanti | `saveImagesAsWmf` impostato su `false` | Abilita `saveOptions.setSaveImagesAsWmf(true)` |
| Caratteri illeggibili | Codifica errata | Imposta `saveOptions.setEncoding(Charset.forName("UTF-8"))` |

## Domande frequenti

**D: Come modifico altre opzioni di salvataggio RTF?**  
R: Usa la classe `RtfSaveOptions` – fornisce proprietà per compressione, font e altro. Consulta la documentazione API di Aspose.Words Java per l’elenco completo.

**D: Posso salvare il documento RTF con una codifica diversa?**  
R: Sì. Chiama `saveOptions.setEncoding(Charset.forName("UTF-8"))` (o qualsiasi charset supportato) prima del salvataggio.

**D: È possibile salvare il documento RTF senza immagini?**  
R: Assolutamente. Imposta `saveOptions.setSaveImagesAsWmf(false)` per escludere le immagini dall’output.

**D: Come gestire le eccezioni durante la conversione?**  
R: Avvolgi le chiamate di caricamento e salvataggio in un blocco try‑catch che cattura `Exception`. Registra l’errore e, se necessario, rilancia un’eccezione personalizzata per la tua applicazione.

**D: Funziona con file Word protetti da password?**  
R: Carica il documento con un oggetto `LoadOptions` che includa la password, quindi procedi con gli stessi passaggi di salvataggio.

## Conclusione
Ora disponi di un metodo completo e pronto per la produzione per **convertire Word in RTF** usando Aspose.Words per Java. Caricando il DOCX, configurando `RtfSaveOptions` (incluso **salvataggio immagini come WMF**) e chiamando `doc.save(...)`, puoi generare file rich text di alta qualità che funzionano ovunque. Sentiti libero di esplorare ulteriori opzioni di salvataggio per personalizzare l’output secondo le tue esigenze specifiche.

---

**Ultimo aggiornamento:** 2025-12-24  
**Testato con:** Aspose.Words per Java 24.12  
**Autore:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}