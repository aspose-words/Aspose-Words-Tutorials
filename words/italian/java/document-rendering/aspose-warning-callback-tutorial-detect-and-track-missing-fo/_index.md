---
category: general
date: 2026-03-17
description: Impara il tutorial sul callback di avviso di Aspose per rilevare i font
  mancanti e monitorare i font mancanti nei documenti Java con un esempio completo
  e eseguibile.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: it
og_description: Padroneggia il tutorial sul callback di avviso di Aspose per rilevare
  i font mancanti e monitorarli nel tuo flusso di lavoro di elaborazione Word in Java.
og_title: Tutorial di callback di avviso Aspose – Rileva i font mancanti
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Tutorial sul callback di avviso di Aspose – Rilevare e tracciare i font mancanti
url: /it/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Rilevare e Tracciare i Font Mancanti

Ti sei mai chiesto come **rilevare i font mancanti** quando converti o modifichi file Word con Aspose.Words? Non sei solo. In molti progetti reali, un font fuori posto può causare problemi di layout, e hai bisogno di un modo affidabile per **tracciare i font mancanti** prima che ti creino problemi in seguito.  

La buona notizia? Il **aspose warning callback tutorial** ti offre un hook programmatico pulito che stampa esattamente gli avvisi di sostituzione dei font man mano che si verificano. In questa guida vedremo come impostare il callback, caricare un documento e vedere gli avvisi in azione—tutto in Java.

Alla fine di questo articolo sarai in grado di individuare automaticamente i font mancanti, registrarli e decidere se incorporare un sostituto o modificare i file sorgente. Nessuno strumento esterno richiesto.

## Prerequisiti

- **Java 8+** (il codice si compila con qualsiasi JDK recente)
- **Aspose.Words for Java** versione 23.10 o successiva – scarica dal portale Aspose o aggiungi la dipendenza Maven.
- Un file DOCX di esempio che fa riferimento intenzionalmente a un font non installato (ad es., “Comic Sans MS” su una macchina Linux).

Questo è tutto—nessuna libreria extra, nessuna procedura di build complessa.

## Passo 1: Registrare un Callback di Avviso – Il Cuore del aspose warning callback tutorial

La prima cosa che il tutorial ti insegna è come collegare un listener di avviso. Aspose.Words genera un oggetto `WarningInfo` per ogni problema riscontrato, e il flag `WarningSource.FONT_SUBSTITUTION` ci indica esattamente quando un font viene sostituito.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Perché è importante:** Senza il callback, Aspose sostituisce silenziosamente i font mancanti, e non sai mai quali glifi potrebbero apparire errati. Registrando l'avviso, puoi **rilevare i font mancanti** in anticipo e decidere se incorporare quello corretto.

> **Consiglio pro:** Se hai bisogno di raccogliere gli avvisi per un report successivo, memorizzali in una `List<WarningInfo>` invece di stamparli direttamente.

## Passo 2: Caricare il Documento – Dove i font mancanti potrebbero nascondersi

Ora carichiamo il DOCX che potrebbe fare riferimento a font non presenti sulla macchina. L'operazione di caricamento attiva il callback di avviso se mancano dei font.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**Cosa succede dietro le quinte?** Aspose analizza le definizioni di stile del documento, scansiona ogni run di testo e controlla il repository di font del sistema. Quando non trova una corrispondenza esatta, ricorre a un sostituto e genera l'avviso che abbiamo appena collegato.

## Passo 3: Salvare il Documento – Emissione degli avvisi

Infine, salviamo il documento. L'operazione di salvataggio ricalcola anche i font, così eventuali avvisi non emessi durante il caricamento appariranno ora.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Quando esegui il programma, vedrai un output della console simile a:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Quell'output dimostra che il **aspose warning callback tutorial** funziona, e hai **rilevato con successo i font mancanti** e ora li **stai tracciando** attraverso il log.

## Come Rilevare i Font Mancanti in un Documento Word – Oltre le Basi

L'approccio con il callback è ottimo per esecuzioni singole, ma a volte serve un'utilità riutilizzabile. Ecco un wrapper veloce che puoi inserire in qualsiasi progetto:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Usalo così:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Ora hai un metodo riutilizzabile **detect missing fonts** che restituisce una lista che puoi inserire in una pipeline CI o in una UI.

## Tracciare i Font Mancanti con Aspose.Words – Reporting per i Team

In un team più grande, potresti voler generare un report CSV di tutti i font mancanti su molti documenti. Combina l'utilità precedente con una semplice iterazione dei file:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Eseguendo questo script otterrai un CSV **track missing fonts** che ogni sviluppatore può consultare prima di commettere un documento in produzione.

## Problemi Comuni & Come Evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Callback not firing** | Hai dimenticato di impostare il callback **prima** di caricare il documento. | Posiziona `Document.setWarningCallback` all'inizio di `main`. |
| **Only first warning appears** | Aspose memorizza nella cache gli avvisi per ogni istanza di `Document`. | Usa un nuovo oggetto `Document` per ogni file, oppure resetta il callback tra le esecuzioni. |
| **Wrong font name in log** | La descrizione contiene testo extra (“Font … non trovato”). | Rimuovi usando regex come mostrato nell'esempio CSV. |
| **Performance hit on large batches** | Il callback viene eseguito su ogni run di testo, il che può risultare costoso. | Limita il controllo a una fase pre‑flight; salta il salvataggio se ti serve solo la rilevazione. |

## Risultati Attesi & Verifica

1. **Output della console** – Dovresti vedere almeno una riga “Font substitution warning” per ogni font mancante.  
2. **Report CSV** – Dopo che lo script di massa termina, apri `missing-fonts-report.csv` e verifica che ogni riga elenchi il nome del documento e il font mancante esatto.  
3. **Documento salvato** – Il DOCX di output verrà renderizzato usando i font di fallback, ma il layout visivo potrebbe differire dall'originale.

Se qualche passaggio non si comporta come descritto, verifica nuovamente che il JAR di Aspose.Words sia nel tuo classpath e che `input.docx` faccia davvero riferimento a un font assente dal tuo OS.

## Conclusione

Hai appena completato un **aspose warning callback tutorial** che mostra come **rilevare i font mancanti** e **tracciare i font mancanti** nelle applicazioni Java. Registrando un listener di avviso, caricando il documento e opzionalmente esportando i risultati, ottieni piena visibilità sui problemi legati ai font prima che emergano in produzione.

Successivamente, potresti esplorare:

- Incorporare direttamente il font mancante con `LoadOptions.setFontSubstitution`.
- Utilizzare la classe `FontSettings` per mappare i font mancanti a sostituti specifici.
- Integrare il report CSV in una pipeline CI/CD per far fallire le build quando compaiono font non documentati.

Provalo, adatta i callback al tuo framework di logging e osserva il tuo flusso di lavoro dei documenti diventare molto più robusto. Buon coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}