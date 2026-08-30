---
category: general
date: 2026-06-17
description: Registra gli avvisi di sostituzione dei font in Java con Aspose.Words
  – rileva i font mancanti durante il caricamento del documento e mantieni coerente
  l'output.
draft: false
keywords:
- log font substitution warnings
- Aspose.Words Java
- font substitution
- warning callback
- LoadOptions
- document loading
language: it
og_description: Registra gli avvisi di sostituzione dei font in Java con Aspose.Words.
  Impara a catturare gli avvisi di font mancanti durante il caricamento del documento
  e mantieni i tuoi PDF impeccabili.
og_title: Registrare gli avvisi di sostituzione dei font in Java – Guida completa
schemas:
- author: Aspose
  dateModified: '2026-06-17'
  description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  headline: Log Font Substitution Warnings in Java with Aspose.Words
  type: TechArticle
- description: Log font substitution warnings in Java using Aspose.Words – capture
    missing fonts during document load and keep your output consistent.
  name: Log Font Substitution Warnings in Java with Aspose.Words
  steps:
  - name: Prerequisites
    text: '- Java 8 or newer (the code works with Java 11+ as well). - Aspose.Words
      for Java library (version 23.10 or later is recommended). - A sample `.docx`
      that references a font not installed on your machine (e.g., `MissingFont.docx`).'
  - name: Logging to a File Instead of the Console
    text: 'If you prefer a persistent log, replace the `System.out.println` call with
      a `FileWriter`:'
  - name: Capturing Multiple Documents in a Loop
    text: 'When processing a folder of documents, you can reuse the same callback:'
  - name: Dealing with Embedded Fonts
    text: 'Aspose.Words can embed missing fonts if you enable it:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Processing
title: Registra avvisi di sostituzione dei font in Java con Aspose.Words
url: /it/java/document-loading-and-saving/log-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrare avvisi di sostituzione dei font in Java – Guida completa

Ti sei mai chiesto come **registrare gli avvisi di sostituzione dei font** quando un documento Word utilizza un font che non è presente sul server? Non sei l’unico a grattarsi la testa per i font mancanti che vengono sostituiti silenziosamente. La buona notizia? Aspose.Words per Java ti offre un modo semplice per intercettare quelle sostituzioni nel momento in cui il documento viene caricato.

In questo tutorial percorreremo un esempio pratico che mostra esattamente come registrare una callback per gli avvisi, filtrare gli avvisi di **sostituzione del font** e scriverli sulla console (o su qualsiasi logger tu preferisca). Alla fine avrai uno snippet riutilizzabile da inserire in qualsiasi progetto Java che utilizza **Aspose.Words Java**.

## Cosa imparerai

- Come configurare **LoadOptions** per catturare gli avvisi.
- Come implementare un **IWarningCallback** che reagisce solo agli eventi di **sostituzione del font**.
- Come caricare un documento in modo sicuro mantenendo una chiara traccia dei font mancanti.
- Suggerimenti per estendere la soluzione a log basati su file o sistemi di monitoraggio.

### Prerequisiti

- Java 8 o superiore (il codice funziona anche con Java 11+).
- Libreria Aspose.Words per Java (si consiglia la versione 23.10 o successiva).
- Un file `.docx` di esempio che faccia riferimento a un font non installato sulla tua macchina (ad es., `MissingFont.docx`).

Non sono richiesti framework aggiuntivi—solo Java puro e i JAR di Aspose.

---

## Passo 1: Configurare LoadOptions per Aspose.Words Java

Prima di poter intercettare gli avvisi, ti serve un'istanza di **LoadOptions**. Questo oggetto indica ad Aspose.Words come comportarsi durante l'analisi del file in ingresso.

```java
// Step 1: Create LoadOptions to enable warning capture
LoadOptions loadOptions = new LoadOptions();
```

Perché questo passo è fondamentale? Senza un oggetto `LoadOptions`, la libreria sostituisce silenziosamente i font mancanti e non vedi alcuna traccia. Creandone esplicitamente uno, apri la porta a una **callback di avviso** personalizzata che può registrare esattamente ciò che ti interessa.

> **Consiglio professionale:** Se carichi molti documenti in batch, riutilizza una singola istanza di `LoadOptions` per evitare creazioni inutili di oggetti.

---

## Passo 2: Implementare una Callback di Avviso per la Sostituzione del Font

Aspose.Words fornisce l'interfaccia `IWarningCallback`. Implementarla ti consente di decidere cosa fare quando il motore genera un `WarningInfo`. Nel nostro caso, vogliamo reagire solo a `WarningType.FONT_SUBSTITUTION`.

```java
// Step 2: Register a warning callback that logs only font‑substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Filter for font‑substitution warnings only
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Simple console output – replace with a logger if you prefer
            System.out.println("Font substitution: " + info.getMessage());
        }
    }
});
```

Alcune note importanti:

1. **Filtraggio** – L'istruzione `if` assicura che vengano ignorati gli avvisi non correlati (come problemi di layout) mantenendo il log pulito.
2. **Sicurezza dei thread** – La callback viene eseguita nello stesso thread che carica il documento, quindi per una semplice stampa su console non serve sincronizzazione aggiuntiva. Se scrivi su un logger condiviso, verifica che sia thread‑safe.
3. **Estensibilità** – Vuoi scrivere su un file? Sostituisci `System.out.println` con `java.util.logging.Logger` o con un framework di logging di terze parti.

---

## Passo 3: Caricare il Documento Utilizzando le Opzioni Configurate

Ora che la callback è pronta, carica il tuo file Word. Nel momento in cui Aspose.Words analizza il documento, qualsiasi font mancante attiverà la callback definita sopra.

```java
// Step 3: Load the document with the warning‑aware LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Se il file sorgente fa riferimento a un font non installato, vedrai un output simile a:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Quella riga è il **log degli avvisi di sostituzione dei font** che stavi cercando. Ora puoi agire di conseguenza—ad esempio avvisare un utente, passare a un foglio di stile di fallback o semplicemente tenere traccia per motivi di conformità.

---

## Passo 4: Proseguire con l'Elaborazione Normale

Dopo il caricamento, il documento si comporta come qualsiasi altro oggetto `Document`. Sentiti libero di ispezionare le sezioni, estrarre testo o convertire in PDF. La registrazione degli avvisi avviene automaticamente durante il passaggio di caricamento, quindi non serve codice aggiuntivo.

```java
// Example: Print the number of sections – just to prove the doc is usable
System.out.println("Document has " + doc.getSections().getCount() + " sections.");
```

La console mostrerà ora sia l’avviso di sostituzione del font (se presente) **che** il conteggio delle sezioni, confermando che il documento è pienamente funzionante.

---

## Suggerimenti Avanzati & Casi Limite

### Registrare su File anziché sulla Console

Se preferisci un log persistente, sostituisci la chiamata `System.out.println` con un `FileWriter`:

```java
private static final String LOG_PATH = "logs/font_substitutions.txt";

loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                fw.write("Font substitution: " + info.getMessage() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
});
```

Ricorda di gestire correttamente le `IOException` nel codice di produzione.

### Catturare più Documenti in un Loop

Quando elabori una cartella di documenti, puoi riutilizzare la stessa callback:

```java
File[] files = new File("input").listFiles((dir, name) -> name.endsWith(".docx"));
for (File f : files) {
    Document d = new Document(f.getAbsolutePath(), loadOptions);
    // Additional processing...
}
```

Poiché la callback è collegata a `loadOptions`, ogni iterazione registra automaticamente gli eventuali eventi di sostituzione del font.

### Gestire i Font Incorporati

Aspose.Words può incorporare i font mancanti se lo abiliti:

```java
loadOptions.setLoadFormat(LoadFormat.DOCX);
loadOptions.setEnableFontSubstitution(true); // default is true
```

Anche con l’incorporamento attivo, la callback di avviso viene comunque attivata, offrendoti visibilità su ciò che è stato sostituito.

---

## Esempio Completo Funzionante

Di seguito trovi il programma completo, pronto per l’esecuzione. Copialo in una classe chiamata `FontSubstitutionDiagnostics.java`, modifica il percorso del file e avvialo.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

/**
 * Demonstrates how to log font substitution warnings using Aspose.Words for Java.
 */
public class FontSubstitutionDiagnostics {

    // Optional: path to a persistent log file
    private static final String LOG_FILE = "font_substitution_log.txt";

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Register a warning callback that logs only font‑substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substitution: " + info.getMessage();
                    // Log to console
                    System.out.println(message);
                    // Also append to a file (optional)
                    try (FileWriter fw = new FileWriter(LOG_FILE, true)) {
                        fw.write(message + System.lineSeparator());
                    } catch (IOException e) {
                        // In a real app, use a proper logging framework
                        e.printStackTrace();
                    }
                }
            }
        });

        // 3️⃣ Load the document with the configured LoadOptions
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 4️⃣ Continue normal processing – e.g., print section count
        System.out.println("Document has " + doc.getSections().getCount() + " sections.");
    }
}
```

**Output previsto** (supponendo che il documento sorgente faccia riferimento a un font mancante):

```
Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
Document has 3 sections.
```

Sia la console sia il file `font_substitution_log.txt` conterranno l’avviso, fornendo una traccia affidabile.

---

## Conclusione

Ti abbiamo appena mostrato come **registrare gli avvisi di sostituzione dei font** in Java usando Aspose.Words. Configurando `LoadOptions`, collegando un `IWarningCallback` e caricando il documento, ottieni piena visibilità su tutti gli eventi di font mancanti che altrimenti passerebbero inosservati. Da qui puoi:

- Inviare gli avvisi a un servizio di logging centrale.
- Attivare allarmi per pipeline di controllo qualità.
- Combinare questa tecnica con altre strategie di **caricamento dei documenti**, come la conversione PDF o la fusione di mail.

Sentiti libero di sperimentare—sostituisci il logger della console con SLF4J, aggiungi timestamp o invia avvisi a una dashboard di monitoraggio. Il pattern di base rimane lo stesso, e ora disponi di una solida base per una gestione robusta dei font in qualsiasi flusso di lavoro documentale basato su Java.

Hai un’idea da condividere? Forse l’hai integrata con Spring Boot o con una funzione cloud. Lascia un commento qui sotto e continuiamo la discussione. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}