---
category: general
date: 2026-07-03
description: Registra una callback di avviso in Java per rilevare i font mancanti
  durante l'elaborazione dei documenti Word. Scopri la gestione degli avvisi di Aspose.Words
  e la rilevazione della sostituzione dei font.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: it
og_description: Registra il callback di avviso in Java per rilevare i caratteri mancanti.
  Questa guida mostra come catturare gli avvisi di sostituzione dei caratteri con
  Aspose.Words.
og_title: Registra callback di avviso in Java – Rileva i font mancanti
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Registra il callback di avviso in Java – Rileva facilmente i font mancanti
url: /it/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registra una callback di avviso in Java – Rileva facilmente i font mancanti

Ti sei mai chiesto come **registrare una callback di avviso** per **rilevare i font mancanti** durante la conversione o la modifica di documenti Word? Non sei l'unico. I font mancanti possono corrompere silenziosamente i layout, trasformare un report elegante in un caos confuso, e la maggior parte degli sviluppatori non se ne accorge fino a quando il PDF finale appare sbagliato.  

In questo tutorial percorreremo un esempio completo, pronto‑da‑eseguire, che mostra esattamente come agganciarsi al sistema di avvisi di Aspose.Words per Java, catturare quegli irritanti avvisi di sostituzione dei font e registrarli o reagire come necessario. Nessun vago “vedi la documentazione” – solo codice puro, pronto da copiare‑incollare, e la motivazione dietro ogni riga.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* **Java 17** (o qualsiasi JDK recente) installato e la variabile `JAVA_HOME` impostata.  
* **Aspose.Words for Java** JAR (scaricalo dal sito ufficiale o includilo via Maven).  
* Un file `.docx` di esempio che faccia riferimento a un font **non** installato sulla tua macchina—questo genererà l’avviso.  
* Il tuo IDE preferito o un semplice editor di testo e gli strumenti di build da riga di comando.

Tutto qui. Nessun framework aggiuntivo, nessun servizio esterno. Pronto? Iniziamo.

## Passo 1: Configura il progetto e aggiungi Aspose.Words

Se usi Maven, aggiungi la seguente dipendenza al tuo `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Per Gradle, inserisci questo in `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Se preferisci il percorso manuale, posiziona semplicemente `aspose-words-24.10.jar` sul classpath.  
**Consiglio:** tieni il JAR accanto alla cartella `src`; semplifica il comando `javac` successivo.

## Passo 2: Carica il documento che potrebbe contenere font mancanti

La prima cosa da fare è creare un oggetto `Document` che punti al file sorgente. Questo passaggio è semplice, ma è anche il punto in cui la libreria analizza il file e *potenzialmente* scopre i font mancanti.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Qui, `Document` è il punto di ingresso per tutte le operazioni di Aspose.Words. Quando il costruttore viene eseguito, la libreria analizza l’XML del documento, risolve i font e, se qualche font non è disponibile, *accoda* un avviso che potremo catturare in seguito.

## Passo 3: Registra una callback di avviso per catturare gli avvisi di sostituzione dei font

Ora arriva la star dello spettacolo: **registrare una callback di avviso**. Aspose.Words ti permette di collegare un’implementazione dell’interfaccia `IWarningCallback`. Ogni volta che il motore incontra una situazione da segnalare—come un font mancante—invoca il tuo metodo `warning`.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Perché è importante

* **Visibilità:** Senza una callback, la sostituzione avviene silenziosamente e potresti distribuire un documento con un aspetto errato.  
* **Automazione:** Nei pipeline batch puoi registrare ogni incidente di font mancante e poi alimentare l’elenco a uno script di installazione dei font.  
* **Conformità:** Alcuni settori (ad es. legale) richiedono la prova che i font originali siano stati usati o sostituiti correttamente.

Nota che filtriamo su `WarningType.FONT_SUBSTITUTION`. Aspose.Words emette molti tipi di avviso—overflow di layout, funzionalità deprecate, ecc.—ma noi ci interessiamo solo a quelli che indicano un font mancante. Questo mantiene la console pulita e focalizzata sull’obiettivo di **rilevare i font mancanti**.

## Passo 4: Salva il documento e lascia che la callback venga attivata

Quando chiami finalmente `save`, il motore completa eventuali caricamenti pigri e attiva la callback di avviso per ogni font mancante scoperto durante l’operazione di salvataggio.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Output console previsto

Supponendo che `input.docx` faccia riferimento al font *“Comic Sans MS”* che non è installato, vedrai qualcosa del genere:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Se il documento sorgente contiene solo font installati, la riga di avviso semplicemente non appare—significando che **rilevare i font mancanti** è avvenuto silenziosamente.

![Output della console che mostra la registrazione della callback di avviso e il rilevamento dei font mancanti](register-warning-callback-output.png)

*Testo alternativo immagine: output della callback di avviso che mostra il rilevamento dei font mancanti*

## Passo 5: Gestione dei casi limite e consigli di best‑practice

### Font mancanti multipli

Se un documento fa riferimento a diversi font non disponibili, la callback verrà attivata una volta per ogni font. Puoi aggregare i messaggi in una lista se ti serve un report riepilogativo più tardi.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Controllo del comportamento di sostituzione

A volte *vuoi* forzare un font di fallback specifico. Usa `FontSettings` prima di caricare il documento:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Ora la callback verrà comunque attivata, ma saprai esattamente quale font verrà usato.

### Considerazioni sulle prestazioni

Registrare una callback di avviso introduce un piccolo overhead—solo pochi nanosecondi per avviso. In servizi ad alto volume (ad es. conversione di migliaia di documenti all’ora) l’impatto è trascurabile. Tuttavia, se elabori milioni di file, considera di disabilitare gli avvisi dopo aver verificato che il set di font sia completo:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Note cross‑platform

La callback funziona allo stesso modo su Windows, macOS e Linux. L’unica differenza è il set di font disponibili su ciascun OS. Se esegui lo stesso job su più agenti, potresti vedere messaggi di sostituzione diversi. Per mantenere i risultati deterministici, distribuisci una **cartella di font personalizzata** e punta Aspose.Words a essa tramite `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Esempio completo, eseguibile

Di seguito trovi l’intera classe Java che puoi copiare‑incollare in `src/main/java/FontWarningDemo.java`. Include tutti gli import, la gestione degli errori e i commenti necessari per eseguirla subito.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Compila ed esegui:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Dovresti vedere le righe di avviso (se presenti) seguite dal messaggio di successo.

## Conclusione

Hai appena imparato **come registrare una callback di avviso** in Java per **rilevare i font mancanti** quando lavori con Aspose.Words. Collegandoti al sistema di avvisi della libreria ottieni piena visibilità sugli eventi di sostituzione dei font, puoi registrarli per conformità e persino sostituire i font programmaticamente se necessario.  

Da qui potresti approfondire:

* **Rilevare i font mancanti** su un batch di file usando un ciclo o stream paralleli.  
* Integrare la callback con un framework di logging (SLF4J, Log4j) per report di livello produzione.  
* Usare `FontSettings` per imporre una palette di font aziendale ed evitare fallback indesiderati.

Provalo—sostituisci il documento di input, sperimenta diversi scenari di font mancanti e osserva il comportamento della callback. Se incontri difficoltà, lascia un commento qui sotto; buona programmazione!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Custom Savings](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}