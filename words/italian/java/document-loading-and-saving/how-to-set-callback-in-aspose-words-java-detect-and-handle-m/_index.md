---
category: general
date: 2026-06-20
description: Come impostare il callback in Aspose.Words Java per rilevare i caratteri
  mancanti e personalizzare il caricamento del documento. Impara passo passo la gestione
  degli avvisi di sostituzione dei caratteri.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: it
og_description: come impostare il callback in Aspose.Words Java per rilevare i font
  mancanti, gestire le sostituzioni e personalizzare il caricamento del documento.
  Guida completa con codice.
og_title: come impostare il callback – Rilevare i font mancanti in Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: come impostare il callback in Aspose.Words Java – rilevare e gestire i font
  mancanti
url: /it/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# come impostare il callback in Aspose.Words Java – Rilevare e gestire i font mancanti

Ti sei mai chiesto **come impostare il callback** in Aspose.Words Java per individuare i font mancanti prima che rovinino il tuo PDF o DOCX? Non sei l’unico. Gli avvisi di font mancanti possono corrompere silenziosamente il layout e, senza un callback di avviso adeguato, potresti non accorgertene fino a quando il documento finale appare sbagliato.  

In questo tutorial percorreremo un esempio completo, pronto‑da‑eseguire, che **rileva i font mancanti**, **gestisce i font mancanti** in modo elegante e ti mostra come **personalizzare il caricamento del documento** con un callback di avviso. Alla fine avrai una classe Java autonoma da inserire in qualsiasi progetto—senza dover cercare documentazione aggiuntiva.

## Cosa ti servirà

- Java 8 o versioni successive (il codice funziona anche con Java 11+)  
- Libreria Aspose.Words per Java (versione 23.9 o successiva)  
- Un file DOCX che faccia riferimento a un font non installato sul tuo sistema (ad esempio un font aziendale personalizzato)  

Se non hai ancora aggiunto Aspose.Words al tuo progetto Maven, includi semplicemente:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

È tutto—nessun plugin extra, nessuna dipendenza nativa.

---

## Passo 1: Comprendere il meccanismo WarningCallback

Il **warning callback** è il modo in cui Aspose.Words ti avvisa quando qualcosa di inaspettato accade durante il caricamento o il salvataggio di un documento. Implementando `IWarningCallback` ottieni il pieno controllo su ciò che viene registrato, ignorato o persino trasformato in eccezione.

> **Perché è importante:**  
> Quando un font è mancante, Aspose sostituisce un font di fallback. Il risultato visivo può differire notevolmente, soprattutto per PDF con branding pesante. Catturando `WarningType.FONT_SUBSTITUTION`, puoi registrare il nome esatto del font, decidere se interrompere l’operazione o sostituire programmaticamente con un tuo font personalizzato.

---

## Passo 2: Creare un’istanza di LoadOptions

`LoadOptions` è il punto di ingresso per personalizzare il caricamento del documento. Collegherai il callback a questo oggetto prima di caricare effettivamente il file.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

A questo punto `loadOptions` è solo un contenitore vuoto—non succede ancora nulla. La vera magia inizia quando colleghiamo il callback.

---

## Passo 3: Implementare e collegare il Callback

Di seguito trovi una classe anonima compatta che implementa `IWarningCallback`. Stampa una riga amichevole sulla console ogni volta che avviene una sostituzione di font.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Consiglio esperto:** Se vuoi **gestire i font mancanti** fornendo una sostituzione, puoi anche impostare `FontSettings` su `LoadOptions` e mappare i font mancanti a un fallback noto.

---

## Passo 4: Caricare il documento con le tue opzioni personalizzate

Ora che il callback è configurato, carica il documento. Se il file fa riferimento a un font che non possiedi, vedrai l’avviso stampato.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Quando esegui il programma, la console potrebbe mostrare:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Quella riga dimostra che hai **rilevato con successo i font mancanti** e sei ora in grado di **gestire i font mancanti** come preferisci.

---

## Passo 5: Opzionale – Sostituire i font mancanti con un font noto

Se preferisci sostituire automaticamente qualsiasi font mancante con, ad esempio, `Times New Roman`, puoi aggiungere un oggetto `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Ora il documento viene caricato e ogni riferimento a `MyCustomFont` viene silenziosamente scambiato con `Times New Roman`. La console continuerà a indicare cosa è stato sostituito, mantenendoti informato.

---

## Esempio completo funzionante

Di seguito trovi una singola classe Java che incorpora tutti i passaggi descritti. Copiala nel tuo IDE, modifica `docPath` e avviala.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Output previsto**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Ora disponi di un metodo riproducibile per **rilevare i font mancanti**, **gestire i font mancanti** e **personalizzare il caricamento del documento**—tutto imparando **come impostare correttamente il callback**.

---

## Domande frequenti

### E se voglio che il programma interrompa il caricamento quando un font è mancante?

Lancia un'eccezione all’interno del metodo `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Il blocco `catch` alla fine catturerà l’eccezione e potrai decidere come registrarla o avvisare l’utente.

### Funziona anche per i PDF generati da DOCX?

Assolutamente sì. Il callback viene attivato durante la fase di **caricamento**, che è identica per tutti i formati di output (`save` in PDF, DOCX, HTML, ecc.). Finché carichi il documento sorgente con le stesse `LoadOptions`, intercetterai i font mancanti prima che influenzino il PDF finale.

### Posso catturare altri tipi di avviso (ad esempio conversione immagini)?

Sì—`WarningInfo.getWarningType()` può essere confrontato con altri enum come `WarningType.IMAGE_CONVERSION`. Basta aggiungere ulteriori rami `if` nel callback.

### C’è un impatto sulle prestazioni?

Trascurabile. Il callback viene eseguito in modo sincrono durante il caricamento e i controlli aggiuntivi sono leggeri. Se devi caricare migliaia di documenti, potresti voler disabilitare gli avvisi in produzione impostando `loadOptions.setWarningCallback(null);`.

---

## Panoramica visiva

![come impostare il callback esempio in Aspose.Words Java](https://example.com/images/callback-diagram.png "come impostare il callback")

*Il diagramma illustra il flusso: `LoadOptions` → `IWarningCallback` → Caricamento del documento → Gestione della sostituzione dei font.*

---

## Conclusione

Abbiamo coperto **come impostare il callback** in Aspose.Words Java, dimostrato **come rilevare i font mancanti**, mostrato modi pratici per **gestire i font mancanti** e spiegato come **personalizzare il caricamento del documento** con `LoadOptions`.  

Con queste conoscenze, ora puoi proteggere le tue pipeline di documenti da sostituzioni di font silenziose, mantenere intatto il branding e fornire agli utenti un feedback chiaro quando qualcosa va storto.

### Cosa fare dopo?

- Esplora le **tabelle di sostituzione dei font** per mappare in blocco molti font mancanti.  
- Combina questo callback con la **validazione del documento** per far rispettare le linee guida di stile.  
- Prova **callback di avviso personalizzati** che scrivono su un file di log o su un sistema di monitoraggio invece di `System.out`.  

Sentiti libero di sperimentare e facci sapere come hai personalizzato il callback per i tuoi progetti. Buon coding!

---

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi nella tua attività.

- [Come impostare LoadOptions in Aspose.Words per Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Come rilevare i font in Aspose.Words – Gestire avvisi e impostazioni](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Come catturare i font in Aspose.Words – Guida completa](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}