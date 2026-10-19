---
category: general
date: 2026-05-30
description: Registra una callback di avviso in Java per monitorare i font mancanti
  e personalizzare il caricamento dei documenti con Aspose.Words. Scopri la soluzione
  completa passo‑passo.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: it
og_description: Registra una callback di avviso in Java per monitorare i font mancanti
  e personalizzare il caricamento del documento. Guida completa con codice e spiegazioni.
og_title: Registra callback di avviso in Java – Traccia i font mancanti
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Registra callback di avviso in Java – Traccia i font mancanti
url: /it/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registra callback di avviso in Java – Traccia i font mancanti

Ti sei mai chiesto come **tracciare i font mancanti** durante il caricamento di un documento Word con Aspose.Words per Java? Forse hai notato quelle sostituzioni silenziose dei font e ti sei chiesto: “Cosa è successo al mio layout?” La buona notizia è che non devi più indovinare. **Registrando un callback di avviso**, puoi catturare ogni evento di sostituzione del font nel momento in cui il documento viene letto, e puoi anche **personalizzare il caricamento del documento** per adattarlo al tuo flusso di lavoro.

> **Cosa otterrai:**  
> • Un programma Java completo che utilizza Aspose.Words  
> • Spiegazioni passo‑passo di ogni riga  
> • Suggerimenti per gestire casi particolari come file crittografati o grandi batch  
> • Un rapido controllo di coerenza che puoi eseguire su qualsiasi file `.docx`

## Prerequisiti

Prima di iniziare, assicurati di avere:

- **Java 17** (o qualsiasi JDK recente) installato e la variabile `JAVA_HOME` impostata.  
- **Aspose.Words for Java** JAR nel tuo classpath. Puoi scaricare l'ultima versione dal repository Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Un documento Word di esempio (`input.docx`) che sospetti contenga font non installati sulla tua macchina.  
- Un IDE o uno strumento di build da riga di comando (Maven/Gradle) con cui ti trovi a tuo agio.

È tutto. Nessun font aggiuntivo, nessun servizio esterno—solo Java puro e Aspose.Words.

## Perché registrare un callback di avviso?

Pensa al **callback di avviso** come a una telecamera di sicurezza per il processo di caricamento del documento. Quando Aspose.Words incontra un glifo mancante, non lancia un'eccezione; sostituisce silenziosamente con un font di fallback. Questa sostituzione silenziosa può rompere il layout, soprattutto in PDF o fatture dove il branding è critico. Registrando un callback puoi:

1. **Ottenere informazioni in tempo reale** – ogni avviso `FONT_SUBSTITUTION` viene consegnato immediatamente.  
2. **Loggare o reagire** – puoi scrivere su un file, generare un allarme, o persino sostituire il font programmaticamente.  
3. **Mantenere un output pulito** – sapere quali font mancano ti permette di correggere il documento sorgente prima della pubblicazione.

In sintesi, il callback trasforma un problema nascosto in uno visibile, rendendo il tuo pipeline di documenti molto più affidabile.

## Passo 1 – Crea `LoadOptions` per personalizzare il modo in cui il documento viene caricato

La prima cosa che facciamo è istanziare `LoadOptions`. Questo oggetto è il punto di ingresso per ogni modifica al momento del caricamento di cui potresti aver bisogno, dalla gestione delle password alla nostra funzionalità di **registrazione del callback di avviso**.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

Perché non chiamare semplicemente `new Document("file.docx")`? Perché senza `LoadOptions` perdi la possibilità di agganciarti agli eventi di caricamento. `LoadOptions` è l’unico posto in cui Aspose.Words ti permette di **personalizzare il caricamento del documento**.

## Passo 2 – Registra un callback di avviso per tracciare i font mancanti

Ora arriva la star dello spettacolo: **registriamo un callback di avviso** che implementa `IWarningCallback`. All’interno del metodo `warning` filtriamo per `WarningType.FONT_SUBSTITUTION` e stampiamo un messaggio utile.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Alcune cose da notare:

- **Perché `IWarningCallback`?** È l’interfaccia che Aspose.Words utilizza per tutti i tipi di avviso, offrendoti un unico punto di ingresso per molte possibili problematiche.  
- **Il filtraggio è fondamentale** – senza il controllo `if` vedresti avvisi su immagini mancanti, funzionalità deprecate, ecc., che ingombrarebbero i log.  
- **Thread‑safety** – il callback viene eseguito nello stesso thread che carica il documento, quindi puoi aggiornare in sicurezza strutture condivise se devi aggregare risultati in seguito.

Questa porzione di codice **registra il callback di avviso**, e da questo momento in poi ogni evento di font mancante verrà stampato su `stdout`. Questo è il cuore del **tracciamento dei font mancanti**.

## Passo 3 – Carica il documento usando le `LoadOptions` configurate

Con il callback al suo posto, carichiamo finalmente il file. Se il documento fa riferimento a un font che non possiedi, il callback si attiva prima che l’oggetto `Document` sia completamente costruito.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Sostituisci `YOUR_DIRECTORY` con il percorso reale sulla tua macchina. Il costruttore `Document` legge il file, applica eventuali password (se ne hai impostata una in `loadOptions`) e attiva il callback di avviso per ogni font mancante. Vedrai un output simile a:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Quella riga dimostra che hai **tracciato con successo i font mancanti**.

## Passo 4 – Continua a elaborare il documento (opzionale)

A questo punto puoi manipolare il documento come preferisci—sostituire testo, inserire immagini, o persino scambiare programmaticamente i font sostituiti. Il callback ti ha già fornito l’elenco dei font problematici, quindi potresti, ad esempio, incorporare un font di fallback:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Sentiti libero di saltare questo blocco se ti serve solo **tracciare i font mancanti**. L’importante è che ora possiedi le informazioni necessarie per prendere una decisione informata.

## Passo 5 – Salva il documento elaborato

Infine, persisti il documento. Puoi sovrascrivere l’originale, salvare in una nuova posizione, o esportare in PDF—tutto senza perdere i dati di avviso catturati in precedenza.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Eseguendo l’intera classe otterrai un output sulla console per ogni font mancante e un nuovo file chiamato `processed.docx` nella stessa cartella.

## Esempio completo funzionante

Di seguito trovi la classe Java completa che puoi copiare‑incollare nel tuo IDE. Include tutto ciò di cui abbiamo parlato, più un piccolo wrapper `main`.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Output previsto

Quando esegui il programma su un documento che utilizza un font non installato sul tuo sistema, vedrai qualcosa di simile:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Se il documento **non contiene font mancanti**, la console rimane silenziosa fino alla riga finale “Document saved successfully.”—esattamente ciò che ti aspetti da una corretta implementazione di **registrazione del callback di avviso**.

## Pro Tips & Common Pitfalls

- **Callback multipli?** Aspose.Words consente solo un gestore di avviso. Se devi loggare sia su file che su console, implementa un callback composito che inoltri l’avviso a più destinazioni.  
- **Batch di grandi dimensioni** – quando elabori centinaia di file, considera di riutilizzare una singola istanza di `LoadOptions`; crearne una per file aggiunge overhead inutile.  
- **Documenti crittografati** – imposta la password su `LoadOptions` prima del caricamento, altrimenti otterrai un `IncorrectPasswordException` prima che il callback possa attivarsi.  
- **Performance** – il callback viene eseguito in modo sincrono. Se logghi su un servizio remoto, bufferizza i messaggi e flushali dopo il completamento del caricamento per evitare colli di bottiglia I/O.  
- **Fallback dei font** – puoi anche fornire una collezione personalizzata di `FontSource` se possiedi font proprietari che vuoi che Aspose.Words consideri prima di ricorrere ai font di sistema.

## Conclusione

Hai appena imparato come **registrare un callback di avviso** in Java, tracciare efficacemente i **font mancanti** e **personalizzare il caricamento del documento** con Aspose.Words. La soluzione è autonoma, funziona con un unico metodo `main` e ti fornisce visibilità immediata su qualsiasi sostituzione di font che altrimenti passerebbe inosservata.

Prossimi passi? Prova a estendere il callback per scrivere gli avvisi in un file CSV a fini di audit, o combinalo con un processore batch che incorpora automaticamente i font mancanti. Potresti anche esplorare altri tipi di avviso come `IMAGE_SUBSTITUTION` o `DEPRECATED_FEATURE`—il medesimo schema si applica.

Buon coding, e che i tuoi documenti vengano sempre renderizzati esattamente come previsto!

![Register warning callback diagram](register-warning-callback.png "Register warning callback flow")


## Cosa dovresti imparare dopo?

- [Callback di avviso in Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Personalizza colori tema e font in Aspose.Words Java: Guida completa](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Traccia le modifiche nei documenti Word usando Aspose.Words Java: Guida completa alle revisioni dei documenti](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}