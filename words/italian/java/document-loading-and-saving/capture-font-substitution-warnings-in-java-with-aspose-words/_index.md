---
category: general
date: 2026-06-27
description: Scopri come catturare gli avvisi di sostituzione dei font in Java usando
  Aspose.Words. Questo tutorial passo‑passo copre anche i callback di avviso e l'uso
  di LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: it
og_description: Cattura gli avvisi di sostituzione dei font in Java con Aspose.Words.
  Segui questa guida per impostare i callback di avviso, utilizzare LoadOptions e
  gestire i font mancanti.
og_title: Cattura gli avvisi di sostituzione dei font in Java – Tutorial Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Cattura gli avvisi di sostituzione dei font in Java con Aspose.Words – Guida
  completa
url: /it/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Catturare gli avvisi di sostituzione dei font in Java con Aspose.Words – Guida completa

Ti è mai capitato di dover **catturare gli avvisi di sostituzione dei font** durante il caricamento di un DOCX che utilizza caratteri esotici? Non sei il solo. In molti progetti reali—pensa a generatori di report automatici o convertitori di documenti batch—i font mancanti attivano sostituzioni silenziose che possono compromettere la fedeltà del layout.  

Fortunatamente, Aspose.Words offre un modo semplice per ascoltare questi avvisi. In questo tutorial vedremo come configurare **LoadOptions**, collegare un **callback di avviso di Aspose.Words** e stampare ogni notifica di *sostituzione del font* sulla console. Alla fine saprai esattamente quando un font è stato sostituito e come reagire programmaticamente.

> **Cosa otterrai:** uno snippet Java completamente eseguibile, una spiegazione del *perché* ogni elemento è importante e consigli per gestire casi particolari come directory di font personalizzate.

## Prerequisiti e ciò di cui avrai bisogno

- Java 8 o versioni successive installate (il codice funziona anche con Java 11+).
- L'ultimo JAR di Aspose.Words per Java (scaricabile dal sito ufficiale o da Maven Central).
- Un file DOCX che fa riferimento a font non installati sulla tua macchina (ad esempio un *font‑rich.docx* disponibile nel set demo di Aspose).
- Un IDE decente (IntelliJ IDEA, Eclipse o anche VS Code con estensioni Java).

No sono richieste librerie esterne oltre a Aspose.Words, e l'esempio funziona in un semplice metodo `main`.

## Passo 1: Configura LoadOptions – Il punto di ingresso per il caricamento personalizzato

`LoadOptions` è il contenitore di configurazione di Aspose.Words che indica alla libreria *come* leggere un documento. Per impostazione predefinita sostituisce silenziosamente i font mancanti, ma è possibile modificare questo comportamento con un callback di avviso.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Perché è importante:** senza `LoadOptions` il documento viene caricato silenziosamente e perdi la visibilità sui font mancanti. Creando un'istanza ottieni un hook per il sistema di avvisi.

## Passo 2: Definisci un Callback di Avviso per *Catturare gli Avvisi di Sostituzione dei Font*

Aspose.Words invia gli eventi di avviso tramite l'interfaccia `IWarningCallback`. Implementala inline (o come classe separata) e filtra per `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Spiegazione:**  
- `info.getWarningType()` indica la categoria dell'avviso.  
- `WarningType.FONT_SUBSTITUTION` è il valore enum di nostro interesse.  
- `info.getDescription()` contiene un messaggio leggibile, ad esempio *“Font 'Comic Sans MS' non trovato, sostituito con 'Arial'.”*  

Stampando la descrizione, **catturi gli avvisi di sostituzione dei font** in tempo reale.

## Passo 3: Carica il Documento Utilizzando le LoadOptions Configurate

Ora che il callback è impostato, carica il tuo DOCX. Il callback di avviso si attiva automaticamente durante il parsing.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Sostituisci `YOUR_DIRECTORY` con il percorso reale del tuo file di test. Quando viene eseguito il costruttore `Document`, qualsiasi font mancante attiva il callback definito in precedenza e vedrai i messaggi di sostituzione sulla console.

## Passo 4: Verifica il Documento Caricato (Opzionale ma Utile)

Dopo il caricamento, potresti voler confermare l'integrità del documento—conteggio pagine, estrazione testo, ecc. Questo passo non è necessario per catturare gli avvisi, ma ti aiuta a vedere l'impatto delle sostituzioni.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Se un font è stato sostituito, il layout potrebbe spostarsi leggermente; controllare il conteggio delle pagine può rivelare tali cambiamenti.

## Passo 5: Avanzato – Gestire Programmaticamente i Font Sostituiti

A volte non basta registrare l'avviso—potresti dover incorporare un font di fallback o modificare lo stile. Di seguito trovi un modello rapido da adottare.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Indicando ad Aspose.Words una cartella che contiene i font originali, puoi *evitare* completamente la sostituzione. Se la cartella manca, il callback di avviso cattura comunque l'evento, fornendoti una strategia di fallback.

## Esempio Completo Funzionante

Mettendo tutto insieme, ecco il programma completo, pronto per l'esecuzione:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Output previsto sulla console** (quando si incontra un font mancante):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Se tutti i font sono presenti, il callback rimane silenzioso—non viene stampato nulla, esattamente come ci si aspetta.

## Problemi Comuni & Consigli Pro

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Il callback non si attiva mai** | Hai dimenticato di collegare il callback a `LoadOptions` **oppure** hai usato il costruttore predefinito di `Document` senza passare `loadOptions`. | Chiama sempre `loadOptions.setWarningCallback(...)` **e** utilizza il sovraccarico `new Document(path, loadOptions)`. |
| **Troppi avvisi ingombrano il log** | Documenti di grandi dimensioni con molti font mancanti generano un avviso per ogni sostituzione. | Filtra ulteriormente controllando `info.getDescription()` per nomi di font specifici, oppure aggrega gli avvisi in una lista per un'elaborazione successiva. |
| **I font sostituiti influenzano il layout** | Il font di fallback può avere metriche diverse (dimensione, spaziatura). | Fornisci una cartella di font personalizzata (vedi Passo 5) o regola lo stile del documento dopo il caricamento. |
| **Esecuzione su server headless** | Il fallback di default dei font potrebbe dipendere da font di sistema non installati sul server. | Distribuisci i font necessari con la tua applicazione e punta `FontSettings` a quella cartella. |

## Domande Frequenti

**D: Funziona con PDF o altri formati?**  
R: Sì. Il callback di avviso è indipendente dal formato; si attiva per qualsiasi tipo di documento caricato da Aspose.Words (DOC, DOCX, RTF, HTML, ecc.). L'unica differenza è l'insieme di avvisi che possono comparire.

**D: Posso catturare altri tipi di avviso, come gli avvisi di *risoluzione immagine*?**  
R: Assolutamente. All'interno del metodo `warning`, controlla `info.getWarningType()` per altri valori enum come `WarningType.IMAGE_RESOLUTION`. Quindi gestiscili di conseguenza.

**D: Cosa succede se ho bisogno dell'elenco dei font sostituiti dopo il caricamento del documento?**  
R: Salva ogni `info.getDescription()` in una `List<String>` all'interno del callback. Dopo il caricamento avrai una collezione che potrai registrare, inviare a un servizio di monitoraggio o usare per avviare una routine di download dei font.

## Conclusione

Ora sai **come catturare gli avvisi di sostituzione dei font** in Java usando Aspose.Words, perché ogni elemento del puzzle è importante e come estendere la soluzione per scenari reali. Sfruttando `LoadOptions`, un `callback di avviso di Aspose.Words` e, facoltativamente, `FontSettings`, ottieni piena visibilità sui font mancanti e puoi mantenere affidabili le tue pipeline di conversione dei documenti.

Pronto per il passo successivo? Prova a sostituire `System.out.println` con un logger come SLF4J, oppure integra l'elenco degli avvisi in un'interfaccia utente che avvisa gli utenti prima di finalizzare una conversione batch. Puoi anche esplorare il **callback di avviso di Aspose.Words** per altri tipi di avviso, come *funzionalità non supportate* o avvisi di *immagini ad alta risoluzione*.

Buona programmazione, e che i tuoi PDF non soffrano mai più di inaspettate sostituzioni di font!

![Screenshot che mostra l'output della console con gli avvisi di sostituzione dei font catturati](image-placeholder.png "cattura avvisi di sostituzione dei font")


## Cosa Dovresti Imparare Dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Abilita gli Avvisi di Sostituzione dei Font in Aspose.Words – Guida Completa](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Come Impostare LoadOptions in Aspose.Words per Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Come Creare Documenti PDF con Aspose.Words per Java | API di Elaborazione Documenti](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}