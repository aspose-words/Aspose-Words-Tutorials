---
category: general
date: 2026-06-30
description: Configura LoadOptions per gli avvisi in Aspose.Words Java. Impara a impostare
  un callback di avviso per la sostituzione dei font e altri avvisi delle opzioni
  di caricamento.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: it
og_description: Configura LoadOptions per gli avvisi in Aspose.Words Java. Questa
  guida mostra come catturare gli avvisi di sostituzione dei caratteri con una callback
  di avviso.
og_title: Configura LoadOptions per gli avvisi – Tutorial Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Configura LoadOptions per gli avvisi – Guida completa a Java
url: /it/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configura LoadOptions per gli Avvisi – Guida Completa Java

Ti è mai capitato di dover **configurare LoadOptions per gli avvisi** quando apri un documento Word con Aspose.Words per Java? Non sei il solo. Molti sviluppatori incontrano un problema quando un font mancante viene sostituito silenziosamente, facendo apparire il PDF finale fuori dal brand. La buona notizia? Collegando un **callback di avviso Java** al tuo `LoadOptions`, puoi catturare ogni avviso di sostituzione del font nel momento in cui si verifica.

In questo tutorial percorreremo un esempio pratico che non solo mostra come configurare il callback, ma spiega anche *perché* ogni elemento è importante. Alla fine sarai in grado di **gestire gli avvisi sui font**, registrarli o persino sostituire i font al volo—senza ipotesi.

## Cosa Imparerai

- Un programma Java completamente eseguibile che stampa ogni avviso di sostituzione del font.
- Una comprensione del funzionamento della **sostituzione dei font in Aspose.Words**.
- Suggerimenti per personalizzare la gestione degli avvisi in progetti più grandi.
- Approfondimento sulle **opzioni di caricamento del documento** e quando modificarle.

> **Prerequisito:** Java 8+ e la libreria Aspose.Words per Java (versione 23.9 o successiva). Non sono necessarie altre dipendenze esterne.

---

## Passo 1: Configura LoadOptions per gli Avvisi

La prima cosa di cui hai bisogno è un'istanza di `LoadOptions` che sappia che deve segnalare gli avvisi. Pensa a `LoadOptions` come alla cassetta degli attrezzi che consegni ad Aspose.Words prima che apra il file.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Perché è importante:**  
`LoadOptions` controlla come la libreria legge il documento. Assegnando un `IWarningCallback`, indichi ad Aspose.Words di invocare il tuo codice ogni volta che incontra qualcosa di rilevante—come un font mancante. Senza questo, la libreria sostituirebbe silenziosamente il font e non lo sapresti.

> **Consiglio professionale:** Se vuoi catturare *tutti* gli avvisi, rimuovi il controllo `if`. Per ora ci concentriamo sui problemi di font perché sono la fonte più comune di sorprese di layout.

## Passo 2: Carica il Documento Utilizzando le Opzioni Configurate

Ora che il callback è pronto, carica il tuo `.docx` (o qualsiasi formato supportato) con le stesse `LoadOptions`. È qui che le **opzioni di caricamento del documento** entrano effettivamente in gioco.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Dietro le quinte:**  
Quando Aspose.Words analizza `input.docx`, scansiona le tabelle dei font. Se un font referenziato nel documento non è installato sulla macchina host, il motore genera un avviso `FONT_SUBSTITUTION`, che attiva immediatamente il callback definito in precedenza.

## Passo 3: Salva il Documento – Gli Avvisi Sono Già Stati Stampati

Salvare il documento è semplice, ma è il momento in cui puoi verificare che il callback sia stato attivato correttamente. Tutti gli avvisi vengono stampati durante il passo di caricamento, quindi l'operazione di salvataggio è solo una pulizia.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Output console previsto:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Se non vedi nulla, o il documento ha usato solo font installati, o il callback non è stato collegato correttamente—ricontrolla il Passo 1.

## Passo 4: Estendi il Callback per **Gestire gli Avvisi sui Font** in Modo Elegante

Stampare sulla console va bene per le demo, ma il codice di produzione spesso richiede una gestione più ricca: registrare su file, inviare avvisi o persino sostituire i font programmaticamente.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Perché lo faresti:**  
Un file di log ti fornisce informazioni post‑mortem, specialmente quando elabori lotti di documenti. Il blocco di sostituzione opzionale mostra come **configurare LoadOptions per gli avvisi** *e* intervenire per far rispettare una politica di font aziendale.

## Avanzato: Controllare Altri Scenari di **Sostituzione dei Font in Aspose.Words**

Il warning callback non è limitato ai font mancanti. Puoi anche catturare:

- **Caratteri Unicode non supportati** (`WarningType.UNSUPPORTED_CHAR`).
- **Problemi di script complessi** (`WarningType.COMPLEX_SCRIPT`).

Basta espandere l'istruzione `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Questo rende la tua soluzione robusta per documenti multilingue, un caso limite comune nelle applicazioni globali.

## Esempio Completo Funzionante

Di seguito trovi il programma completo, pronto per l'esecuzione. Incollalo in qualsiasi IDE Java, sostituisci i segnaposto `YOUR_DIRECTORY` e premi *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Risultato Atteso

- La console stampa eventuali avvisi di sostituzione del font.
- `font-warnings.log` contiene un elenco con timestamp (se hai mantenuto la registrazione opzionale).
- `output.docx` viene salvato con i font sostituiti, corrispondenti al fallback definito.

## Problemi Comuni & Come Evitarli

| Problema | Perché Accade | Soluzione |
|----------|----------------|-----------|
| **Nessun avviso appare** | Il callback non è stato collegato, o il documento utilizza solo font installati. | Verifica che `loadOptions.setWarningCallback(...)` sia chiamato *prima* di caricare il documento. |
| **FileNotFoundException** su `input.docx` | Il percorso è errato o il file non è incluso nel progetto. | Usa un percorso assoluto o posiziona il file nella cartella delle risorse del progetto. |
| **Rallentamento delle prestazioni** durante l'elaborazione di migliaia di documenti | Registrazione eccessiva su disco per ogni avviso. | Bufferizza i log e scrivi in batch, o limita la registrazione solo agli avvisi critici. |
| **Sostituzione del font inattesa** nonostante il fallback | La tabella di sostituzione non è stata applicata in tempo. | Imposta le impostazioni di sostituzione **prima** di caricare il documento, o usa `FontSettings.setSubstitutionSettings` a livello globale. |

## Prossimi Passi

Ora che hai padroneggiato **configurare LoadOptions per gli avvisi**, considera questi argomenti di approfondimento:

- **Elaborazione batch**: Scorri una directory di documenti, aggregando tutti gli avvisi sui font in un unico report.
- **Provider di font personalizzati**: Carica i font da una condivisione di rete o da risorse incorporate invece del sistema operativo locale.
- **Integrare con framework di logging** come Log4j per tracciabilità a livello enterprise.
- Esplora altre **opzioni di caricamento del documento** come il rilevamento `LoadFormat` o la gestione della `Password` per file protetti.

Ognuno di questi si basa sullo stesso schema—crea un oggetto `LoadOptions`, collega i callback appropriati e lascia che Aspose.Words faccia il lavoro pesante.

## Conclusione

Abbiamo approfondito come **configurare LoadOptions per gli avvisi** in Aspose.Words per Java, impostare un **callback di avviso Java** e utilizzare queste informazioni per **gestire gli avvisi sui font** in modo intelligente. Il codice è compatto, i concetti sono chiari, e ora disponi di una solida base per estendere la gestione degli avvisi ad altri scenari come caratteri non supportati o script complessi.

Provalo, modifica la tabella di sostituzione per farla corrispondere ai font del tuo brand, e guarda quegli scambi silenziosi di font scomparire. Buon coding!

--- 

![Diagram showing the flow of configuring LoadOptions for warnings, loading a document, capturing font substitution events, and saving the output](configure-loadoptions-for-warnings-diagram.png "Configure LoadOptions for warnings flow")


## Cosa Dovresti Imparare Dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Cattura gli Avvisi di Sostituzione dei Font in Java con Aspose.Words – Guida Completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Come Impostare LoadOptions in Aspose.Words per Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Come Caricare Documenti RTF Configurando le Opzioni di Caricamento RTF in Aspose.Words per Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}