---
category: general
date: 2026-02-15
description: Scopri come ottenere i caratteri mancanti durante il caricamento di un
  documento Word in Java usando Aspose.Words. Include callback di avviso e gestione
  della sostituzione dei caratteri.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: it
og_description: Come ottenere i font mancanti in Java con Aspose.Words. Scopri le
  callback di avviso, la gestione della sostituzione dei font e le migliori pratiche
  per l'elaborazione dei documenti.
og_title: Come ottenere i font mancanti in Java – Guida Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Come ottenere i font mancanti in Java – Guida Aspose.Words
url: /it/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come ottenere i caratteri mancanti in Java – Guida Aspose.Words

Hai mai aperto un documento Word in Java solo per vedere strane sostituzioni di caratteri e chiederti **come ottenere i caratteri mancanti**? Non sei il primo a incontrare questa sorpresa. In molte applicazioni aziendali, gli avvisi di caratteri mancanti possono compromettere la fedeltà visiva di report, contratti o materiale di marketing.

La buona notizia? Aspose.Words ti offre un modo semplice per catturare quegli avvisi tramite un callback, così puoi registrare, sostituire o persino avvisare gli utenti prima che il documento venga renderizzato. In questo tutorial percorreremo un esempio completo e eseguibile che mostra **come ottenere i caratteri mancanti**, spiega perché il callback è importante e copre alcuni trucchi per casi limite che potresti incontrare in progetti reali.

> **Consiglio professionale:** Se stai già usando Aspose.Words 22.12 o versioni successive, l'API mostrata di seguito funziona subito senza configurazioni aggiuntive.

---

![Diagramma che illustra come ottenere i caratteri mancanti usando il callback di avviso di Aspose.Words](how-to-get-missing-fonts-diagram.png "diagramma di come ottenere i caratteri mancanti")

## Cosa copre questo tutorial

- Configurare un **callback di avviso Java LoadOptions** per catturare gli avvisi di sostituzione dei caratteri.  
- Filtrare gli avvisi in modo da vedere solo quelli relativi ai caratteri mancanti.  
- Stampare un rapporto chiaro e leggibile che indica quali caratteri sono stati sostituiti e con cosa sono stati sostituiti.  
- Suggerimenti per gestire documenti di grandi dimensioni, personalizzare il livello di avviso e integrare la soluzione in una pipeline di elaborazione più ampia.

Al termine di questa guida sarai in grado di rispondere alla domanda “**come ottenere i caratteri mancanti**?” con uno snippet di codice pronto all'uso e una solida comprensione dei meccanismi sottostanti.

### Prerequisiti

- Java 8 o versione più recente installata.  
- Libreria Aspose.Words per Java (scaricabile dal sito ufficiale o aggiungibile via Maven/Gradle).  
- Un documento Word che faccia riferimento a un carattere non installato sulla tua macchina (ad es., `MissingFont.docx`).  

Se ti manca qualcuno di questi, procurati subito la libreria—aggiungerla a Maven è semplice come:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Passo 1: Preparare una collezione per gli avvisi di sostituzione dei caratteri

Prima di caricare il documento abbiamo bisogno di un posto dove memorizzare gli avvisi che Aspose.Words genera. Un `ArrayList<WarningInfo>` funziona bene perché preserva l'ordine e ci permette di iterare in seguito.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Perché è importante:* il callback di avviso può attivarsi decine di volte per un singolo file—pensa a ogni glifo mancante, a ogni problema di immagine incorporata, ecc. Raccogliendoli prima, mantieni veloce la fase di caricamento e posticipi l'elaborazione a un ciclo controllato.

---

## Passo 2: Configurare LoadOptions con un callback di avviso

Aspose.Words ti consente di collegare un `IWarningCallback`. All'interno del callback aggiungeremo ogni `WarningInfo` alla nostra lista del Passo 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Spiegazione:* il metodo `warning` viene invocato **sincronamente** durante il caricamento del documento. Inserendo semplicemente il `WarningInfo` in `fontWarnings`, eviti operazioni I/O pesanti (come la scrittura su file) che potrebbero rallentare il caricamento. Questo schema—raccogli‑poi‑elabora—è il modo consigliato per gestire grandi quantità di avvisi.

---

## Passo 3: Caricare il documento usando le opzioni configurate

Ora leggiamo effettivamente il file Word. Se il documento contiene caratteri non installati, Aspose.Words li sostituirà automaticamente e attiverà il callback di avviso che abbiamo appena configurato.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*Cosa succede dietro le quinte?* Aspose.Words analizza la tabella dei caratteri del file, la confronta con i caratteri disponibili sul sistema operativo host e, per ogni voce mancante, crea un `WarningInfo` con `WarningSource.FontSubstitution`. Quella sorgente è la chiave che useremo per isolare gli avvisi di caratteri mancanti.

---

## Passo 4: Filtrare e visualizzare solo gli avvisi di sostituzione dei caratteri

Dopo il caricamento, `fontWarnings` può contenere un mix di messaggi (ad es., funzionalità deprecate, problemi di immagine). Ci interessano solo i caratteri mancanti, quindi attraversiamo la lista e stampiamo un rapporto conciso.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Esempio di output**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Perché è utile:* il campo `description` indica quale carattere il documento richiedeva, mentre `additionalInfo` mostra quale carattere Aspose.Words ha effettivamente usato. Con questi dati puoi:

- Richiedere all'utente di installare il carattere mancante.  
- Incorporare programmaticamente un carattere sostitutivo nel documento (`doc.getFontInfos().add(...)`).  
- Registrare l'evento per audit di conformità.

---

## Gestire casi limite e variazioni comuni

### 1. Sopprimere gli avvisi non relativi ai caratteri

Se vuoi solo i messaggi legati ai caratteri, puoi restringere il callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Questo riduce il consumo di memoria quando si elaborano batch molto grandi.

### 2. Regolare la gravità dell'avviso

Aspose.Words classifica gli avvisi con `WarningType`. Per i caratteri mancanti vedrai tipicamente `WarningType.FontSubstitution`. Se desideri trattarli come errori (ad es., interrompere il caricamento), lancia un'eccezione all'interno del callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Lavorare con stream invece di file

A volte i documenti provengono da un database o da una richiesta HTTP. Lo stesso approccio funziona con un `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Ricorda solo di chiudere lo stream dopo il caricamento.

### 4. Utilizzare una cartella di caratteri personalizzata

Se disponi di una collezione di caratteri aziendali su un'unità condivisa, indica ad Aspose.Words quella cartella:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Ora la libreria cercherà lì *prima* di ricorrere ai caratteri di sistema, riducendo drasticamente il numero di avvisi di caratteri mancanti.

---

## Esempio completo funzionante

Mettendo tutto insieme, ecco una classe autonoma che puoi inserire in qualsiasi progetto Java:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Esegui questo programma e vedrai un elenco ordinato di tutti i caratteri che Aspose.Words ha dovuto sostituire. Nessuna libreria aggiuntiva, nessuna magia nascosta—solo Java puro e la potenza dell'**API di caratteri mancanti di Aspose.Words**.

---

## Conclusione

Abbiamo risposto alla domanda fondamentale **come ottenere i caratteri mancanti** in un ambiente Java usando Aspose.Words. Collegando un callback di avviso a `LoadOptions`, raccogliendo gli oggetti `WarningInfo` e filtrando le sorgenti `FontSubstitution`, ottieni piena visibilità sui problemi legati ai caratteri prima di qualsiasi rendering. L'approccio scala da utility monofile a processori batch massivi ed è sufficientemente flessibile da gestire cartelle di caratteri personalizzate, gestione della gravità o input basati su stream.

Passi successivi? Prova a incorporare direttamente i caratteri sostituiti nel documento (`doc.getFontInfos().add(...)`) così il file finale sarà davvero autonomo, oppure integra il rapporto di avviso in una dashboard di monitoraggio. Potresti anche approfondire argomenti correlati come **document processing Java**, **Aspose.Words font substitution warning** e **Java LoadOptions warning callback** per ampliare le tue competenze.

Buona programmazione, e che i tuoi documenti vengano sempre renderizzati con i caratteri che ti aspetti!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}