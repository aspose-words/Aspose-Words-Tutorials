---
category: general
date: 2026-04-04
description: Cattura gli avvisi di sostituzione dei caratteri durante il caricamento
  dei documenti Word con Aspose.Words per Java e rileva automaticamente i caratteri
  mancanti. Segui questa guida passo‑passo.
draft: false
keywords:
- capture font substitution warnings
- detect missing fonts
language: it
og_description: Cattura gli avvisi di sostituzione dei caratteri durante il caricamento
  dei documenti Word con Aspose.Words per Java e rileva i caratteri mancanti in pochi
  semplici passaggi.
og_title: Cattura avvisi di sostituzione dei font – Rileva i font mancanti
tags:
- Aspose.Words
- Java
- Document Processing
title: Cattura avvisi di sostituzione dei font – Rileva i font mancanti
url: /it/java/document-loading-and-saving/capture-font-substitution-warnings-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cattura avvisi di sostituzione dei font – Rileva i font mancanti

Ti è mai capitato di **catturare gli avvisi di sostituzione dei font** quando apri un file Word, solo per scoprire che un carattere cruciale è mancante? Non sei solo. In molti flussi di lavoro aziendali un font mancante può trasformare un report perfettamente formattato in un caos incomprensibile, e l'unico indizio che ottieni è un avviso silenzioso che la maggior parte degli sviluppatori non vede mai.

La buona notizia è che Aspose.Words per Java ti permette di agganciarti al processo di caricamento e **rilevare i font mancanti** prima che ti creino problemi. In questo tutorial percorreremo un esempio completo e eseguibile che stampa ogni avviso di sostituzione direttamente sulla console, così potrai decidere se incorporare il font corretto, sostituirlo o avvisare l'utente.

Entro la fine di questa guida saprai come:

* Configurare un oggetto `LoadOptions` con un callback di avviso personalizzato.
* Filtrare il callback in modo che reagisca solo agli eventi di sostituzione dei font.
* Caricare qualsiasi file `.docx` e vedere gli avvisi istantaneamente.
* Estendere la soluzione per registrare gli avvisi, lanciare eccezioni o persino installare automaticamente i font mancanti.

Nessuna documentazione esterna necessaria—solo poche righe di Java e il JAR di Aspose.Words.

## Prerequisiti

Prima di immergerci, assicurati di avere:

* Java 8 o versioni successive installate (la versione LTS più recente funziona meglio).
* Aspose.Words per Java 23.11 o successivo – puoi scaricare l'artifact Maven o il JAR semplice dal sito Aspose.
* Un documento Word che faccia riferimento a un font che non hai sulla tua macchina di sviluppo (ad esempio, “MyFancyFont”).  
* Un IDE o un editor di testo a tua scelta – io uso IntelliJ IDEA, ma Eclipse o VS Code vanno benissimo.

Se qualcuno di questi ti è sconosciuto, fermati e installalo prima; il resto del tutorial presuppone che siano pronti.

---

## Cattura avvisi di sostituzione dei font usando Aspose.Words

Il cuore della soluzione risiede in un'istanza di `LoadOptions`. Assegnando un `IWarningCallback` possiamo intercettare ogni avviso che la libreria emette durante la fase di caricamento.

```java
import com.aspose.words.*;

public class FontDiagnosticsTutorial {
    public static void main(String[] args) throws Exception {

        // Step 1️⃣: Create LoadOptions and set a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Capture only font substitution warnings.
                if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
                    System.out.println("Font substitution: " + info.getDescription());
                }
            }
        });

        // Step 2️⃣: Load the document. The callback runs automatically.
        Document doc = new Document("YOUR_DIRECTORY/document-with-missing-font.docx", loadOptions);

        // Step 3️⃣: If you reach this line, the document is loaded.
        // Any missing‑font warnings have already been printed to the console.
        System.out.println("Document loaded successfully.");
    }
}
```

**Perché funziona:**  
`LoadOptions` indica ad Aspose.Words come trattare il file in ingresso. L'interfaccia `IWarningCallback` è un hook che riceve un oggetto `WarningInfo` per *ogni* avviso. Controllando `info.getWarningType()` filtriamo tutto tranne `SUBSTITUTED_FONT`. La proprietà `description` contiene un messaggio leggibile dall'uomo come “Font 'MyFancyFont' was substituted with 'Arial'”.

### Output console previsto

If il documento sorgente fa riferimento a un font non installato, vedrai qualcosa di simile:

```
Font substitution: Font 'MyFancyFont' was substituted with 'Arial'.
Document loaded successfully.
```

Se il documento utilizza solo font presenti sulla macchina, il callback rimane silenzioso e otterrai solo la riga finale “Document loaded successfully.”.

---

## Rileva i font mancanti nel tuo documento

Potresti chiederti, *“Un avviso di sostituzione è lo stesso di un font mancante?”* Nella maggior parte dei casi, sì—Aspose.Words sostituisce un font mancante con un fallback e lo segnala tramite `SUBSTITUTED_FONT`. Tuttavia, ci sono casi limite in cui un font è presente ma lo stile esatto (grassetto‑corsivo, caratteristiche OpenType specifiche) non lo è, portando a una sostituzione sottile.

Per essere assolutamente sicuri di aver catturato ogni lacuna, puoi combinare il callback di avviso con un'ispezione post‑caricamento:

```java
// After loading the document, iterate through all runs.
for (Paragraph para : (Iterable<Paragraph>) doc.getFirstSection().getBody().getChildNodes(NodeType.PARAGRAPH, true)) {
    for (Run run : (Iterable<Run>) para.getChildNodes(NodeType.RUN, true)) {
        Font font = run.getFont();
        if (font.getName().equalsIgnoreCase("MyFancyFont")) {
            System.out.println("Run still uses the missing font: " + font.getName());
        }
    }
}
```

**Consiglio professionale:** Se trovi delle run che ancora fanno riferimento al font mancante, puoi sostituirle al volo:

```java
font.setName("Arial"); // fallback
```

---

## Problemi comuni e come evitarli

| Problema | Perché succede | Soluzione |
|----------|----------------|-----------|
| **Dimenticare di impostare il callback** | `LoadOptions` usa per default un callback no‑op, quindi gli avvisi scompaiono. | Chiama sempre `loadOptions.setWarningCallback(...)` prima di caricare. |
| **Usare il tipo di avviso sbagliato** | `WarningType.SUBSTITUTED_FONT` è l'unico enum che segnala i font mancanti. | Filtra su `WarningType.SUBSTITUTED_FONT` *esattamente*; gli altri tipi (ad es., `UNKNOWN_FILE_FORMAT`) non sono correlati. |
| **Hard‑coding dei percorsi dei file** | Funziona localmente ma si rompe nelle pipeline CI/CD. | Usa un percorso relativo o passa la posizione del file come argomento da riga di comando. |
| **Ignorare i font Unicode** | Alcuni font mancanti sono un problema solo per determinati caratteri. | Testa con un documento contenente l'intero set di caratteri che ti aspetti di supportare. |
| **Eseguire su un server headless senza configurazione dei font** | Il server potrebbe non avere alcun font di fallback, causando sostituzioni inaspettate. | Installa un set minimo di font comuni (Arial, Times New Roman) sul server. |

---

## Estendere la soluzione

Adesso che puoi **catturare gli avvisi di sostituzione dei font**, potresti voler:

* **Registrare gli avvisi su un file** – sostituisci `System.out.println` con un logger come SLF4J.
* **Lanciare un'eccezione** – utile nelle pipeline automatizzate dove un font mancante dovrebbe far fallire la build:

```java
if (info.getWarningType() == WarningType.SUBSTITUTED_FONT) {
    throw new RuntimeException("Missing font detected: " + info.getDescription());
}
```

* **Auto‑installare i font mancanti** – scarica il TTF/OTF necessario a runtime e aggiungilo al `GraphicsEnvironment` di Java. È uno scenario più avanzato, ma completamente fattibile.

---

## Diagramma (opzionale)

![Diagramma del flusso di cattura degli avvisi di sostituzione dei font che mostra LoadOptions → WarningCallback → Output console](capture-font-substitution-warnings-diagram.png)

*Alt text:* “Diagramma del flusso di cattura degli avvisi di sostituzione dei font che illustra come Aspose.Words instrada gli avvisi di font mancanti verso un callback personalizzato.”

---

## Conclusione

Abbiamo appena coperto come **catturare gli avvisi di sostituzione dei font** e **rilevare i font mancanti** durante il caricamento di documenti Word con Aspose.Words per Java. Configurando un oggetto `LoadOptions` e implementando un piccolo `IWarningCallback`, ottieni piena visibilità sul processo di fallback dei font, permettendoti di registrare, sostituire o interrompere in caso di caratteri mancanti.

In sintesi: imposta il callback, filtra per `SUBSTITUTED_FONT`, carica il documento e gestisci l'output come necessita la tua applicazione. Da qui puoi espandere a framework di logging, controlli CI o persino provisioning automatizzato dei font.

Vuoi andare oltre? Prova:

* **Incorporare i font** direttamente nel documento salvato (`doc.save(..., SaveOptions.createSaveOptions(SaveFormat.DOCX))` con `FontEmbeddingMode.EMBED_ALL`).
* **Generare un PDF** dopo aver corretto i font, assicurando che l'output finale appaia esattamente come previsto.
* **Scansionare un'intera cartella** di documenti per font mancanti e produrre un report riepilogativo.

Questo è tutto per ora—buon coding, e che i tuoi documenti vengano sempre visualizzati con il font corretto!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}