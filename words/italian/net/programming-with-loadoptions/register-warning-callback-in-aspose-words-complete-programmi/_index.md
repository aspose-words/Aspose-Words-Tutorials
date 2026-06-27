---
category: general
date: 2026-06-27
description: Registra il callback di avviso in Aspose.Words per rilevare le sostituzioni
  di caratteri e i problemi di caricamento. Impara l'uso passo‑passo di LoadOptions
  con Aspose.Words.
draft: false
keywords:
- register warning callback aspose.words
- aspose.words warning callback
- loadoptions font substitution warning
- document loading warning handling
- aspose.words loadoptions example
language: it
og_description: Registra il callback di avviso in Aspose.Words per monitorare le sostituzioni
  di font e altri avvisi di caricamento. Segui questo tutorial completo per un'implementazione
  robusta.
og_title: Registrare il callback di avviso in Aspose.Words – Guida completa
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  headline: Register Warning Callback in Aspose.Words – Complete Programming Guide
  type: TechArticle
- description: Register warning callback in Aspose.Words to catch font substitutions
    and loading issues. Learn step‑by‑step usage of LoadOptions with Aspose.Words.
  name: Register Warning Callback in Aspose.Words – Complete Programming Guide
  steps:
  - name: 4.1 Logging to a File Instead of Console
    text: 'In production you rarely want console spam. Swap `Console.WriteLine` for
      a logger (e.g., `Serilog`, `NLog`) or write to a text file:'
  - name: 4.2 Providing a Custom Font Directory
    text: 'If your environment uses corporate fonts, tell Aspose.Words where to look
      before it falls back to substitution:'
  - name: 4.3 Handling Non‑Font Warnings
    text: 'You can broaden the scope to capture any loading warning:'
  - name: 5.1 Verify with a Document That Has Missing Fonts
    text: Create a small DOCX that references a font not installed on your machine
      (e.g., “Comic Sans MS” on a Linux server). Run the loader; you should see a
      substitution message.
  - name: 5.2 Benchmark Overhead
    text: The callback adds negligible overhead—roughly a few microseconds per warning.
      If you’re loading thousands of documents, you might batch log entries or disable
      the callback for non‑critical runs.
  - name: 5.3 Edge Cases
    text: '- **Multiple Substitutions for the Same Font:** Aspose.Words may fire the
      callback multiple times if the same missing font appears on different pages.
      Deduplicate in your logger if needed. - **Encrypted Documents:** If the DOCX
      is password‑protected, you must also set `loadOptions.Password`. The cal'
  type: HowTo
tags:
- aspose-words
- warning-callback
- csharp
- document-processing
title: Registrare il callback di avviso in Aspose.Words – Guida completa alla programmazione
url: /it/net/programming-with-loadoptions/register-warning-callback-in-aspose-words-complete-programmi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registra il Callback di Avviso in Aspose.Words – Guida Completa alla Programmazione

Ti sei mai chiesto come **registrare un callback di avviso in Aspose.Words** per vedere esattamente quali caratteri vengono sostituiti quando un documento viene caricato? Non sei l'unico. Molti sviluppatori si trovano di fronte a una sostituzione silenziosa dei font che rovina il layout di un PDF o di un file Word generato.  

In questo tutorial percorreremo una soluzione pratica che non solo registra un callback di avviso in Aspose.Words, ma spiega anche *perché* dovresti farlo, come funziona il callback dietro le quinte e quali casi limite potresti incontrare. Alla fine sarai in grado di registrare ogni sostituzione di font, catturare altri avvisi di caricamento e mantenere trasparente la tua pipeline di elaborazione documenti.

## Cosa Imparerai

- Configurare **LoadOptions** per controllare il comportamento di caricamento del documento.  
- Registrare un **callback di avviso** che si attiva per la sostituzione dei font e altri tipi di avviso.  
- Caricare un DOCX con le opzioni configurate e interpretare l'output del callback.  
- Insidie comuni (font mancanti, cartelle di font personalizzate e considerazioni sulle prestazioni).  

**Prerequisiti:** Visual Studio 2022 (o qualsiasi IDE C#), runtime .NET 6+ e una licenza attiva di Aspose.Words (la versione di prova gratuita è sufficiente per sperimentare). Non sono necessari pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

---

![Diagramma che illustra il flusso di registrazione di un callback di avviso in Aspose.Words e la gestione degli avvisi di sostituzione dei font](register-warning-callback-aspose-words.png "diagramma di registrazione del callback di avviso aspose.words")

## Passo 1: Crea LoadOptions – Il Punto di Ingresso per la Gestione degli Avvisi  

Prima che il callback possa attivarsi, è necessaria un'istanza di **LoadOptions**. Pensala come il pannello di controllo che consegni ad Aspose.Words quando dici “carica questo file, ma avvisami se qualcosa non va”.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

// Initialize LoadOptions – this object will carry our warning callback.
var loadOptions = new LoadOptions();
```

> **Perché è importante:** `LoadOptions` ti consente di regolare tutto, dalle password di crittografia alle directory dei font. Collegando un callback di avviso a questo oggetto, trasformi un processo silenzioso in uno osservabile.

## Passo 2: Registra il Callback di Avviso – Cattura le Sostituzioni di Font  

Ora arriva la star dello spettacolo: il **callback di avviso**. Registreremo un metodo anonimo (una lambda) che Aspose.Words invocherà per ogni avviso di caricamento. All'interno del callback filtriamo `WarningType.FontSubstitution` e stampiamo un messaggio amichevole.

```csharp
// Register a warning callback to be notified of font substitutions.
loadOptions.WarningCallback = (sender, args) =>
{
    // The callback runs for each loading warning; we care about font substitution warnings.
    if (args.WarningType == WarningType.FontSubstitution)
    {
        // Cast to the more specific warning info type.
        var fontWarning = (FontSubstitutionWarningInfo)args;
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
    // Optional: handle other warning types here (e.g., MissingResource, UnsupportedFeature).
};
```

> **Consiglio professionale:** Se vuoi anche registrare immagini mancanti o funzionalità non supportate, aggiungi ulteriori rami `if` che controllano `args.WarningType`. Questo rende la tua **register warning callback in Aspose.Words** una soluzione unica per tutti i diagnostici di caricamento.

## Passo 3: Carica il Documento Utilizzando le LoadOptions Configurate  

Con il callback collegato, il passo successivo è semplicemente caricare il documento. Passa l'istanza `loadOptions` al costruttore `Document`. Ogni volta che Aspose.Words incontra un font che non riesce a trovare, il tuo callback si attiverà e scriverà sulla console.

```csharp
// Load the DOCX while the warning callback is active.
var doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Esegui il programma e vedrai un output simile a:

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
```

Questo è il nocciolo di **register warning callback aspose.words**—un pattern a tre passi che puoi riutilizzare in qualsiasi progetto.

## Passo 4: Estendere il Callback per Scenari Reali  

### 4.1 Registrare su File Invece che su Console  

In produzione raramente vuoi spam sulla console. Sostituisci `Console.WriteLine` con un logger (ad es., `Serilog`, `NLog`) o scrivi su un file di testo:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    if (args.WarningType == WarningType.FontSubstitution)
    {
        var info = (FontSubstitutionWarningInfo)args;
        File.AppendAllText("font-warnings.log",
            $"[WARN] {DateTime.Now}: Font '{info.FontName}' → '{info.SubstitutedFontName}'{Environment.NewLine}");
    }
};
```

### 4.2 Fornire una Cartella di Font Personalizzata  

Se il tuo ambiente utilizza font aziendali, indica ad Aspose.Words dove cercare prima che ricorra alla sostituzione:

```csharp
loadOptions.FontSettings = new FontSettings();
loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
```

Ora il callback potrebbe attivarsi *meno* spesso, perché il motore trova i font corretti.

### 4.3 Gestire Avvisi Non Relativi ai Font  

Puoi ampliare lo scopo per catturare qualsiasi avviso di caricamento:

```csharp
loadOptions.WarningCallback = (sender, args) =>
{
    switch (args.WarningType)
    {
        case WarningType.FontSubstitution:
            var f = (FontSubstitutionWarningInfo)args;
            Log($"Font '{f.FontName}' → '{f.SubstitutedFontName}'");
            break;
        case WarningType.MissingResource:
            var m = (MissingResourceWarningInfo)args;
            Log($"Missing resource: {m.ResourceType} - {m.ResourceName}");
            break;
        // Add more cases as needed.
    }
};
```

## Passo 5: Testare la Tua Implementazione – Cosa Aspettarsi  

### 5.1 Verifica con un Documento che Ha Font Mancanti  

Crea un piccolo DOCX che faccia riferimento a un font non installato sulla tua macchina (ad es., “Comic Sans MS” su un server Linux). Esegui il loader; dovresti vedere un messaggio di sostituzione.  

### 5.2 Benchmark dell'Overhead  

Il callback aggiunge un overhead trascurabile—circa pochi microsecondi per avviso. Se carichi migliaia di documenti, potresti raggruppare le voci di log o disabilitare il callback per esecuzioni non critiche.

### 5.3 Casi Limite  

- **Sostituzioni Multiple per lo Stesso Font:** Aspose.Words può attivare il callback più volte se lo stesso font mancante appare su pagine diverse. De‑duplica nel tuo logger se necessario.  
- **Documenti Cifrati:** Se il DOCX è protetto da password, devi anche impostare `loadOptions.Password`. Il callback si attiverà comunque dopo la decrittazione.  
- **Caricamento Asincrono:** L'API è sincrona, ma puoi avvolgere la chiamata di caricamento in `Task.Run` per l'elaborazione in background; il callback rimane thread‑safe.

## Insidie Comuni & Come Evitarle  

| Insidia | Perché Accade | Soluzione |
|---------|----------------|-----|
| **Nessun output** | Callback non assegnato *o* `WarningCallback` sovrascritto successivamente. | Assicurati di assegnare il callback **una sola volta** prima del caricamento e di non riassegnare `loadOptions` dopo l'assegnazione. |
| **Eccezione di cast errato** | Tentativo di cast di un avviso che non è `FontSubstitutionWarningInfo`. | Controlla sempre `args.WarningType` prima di effettuare il cast. |
| **Rallentamento delle prestazioni** | Log sincrono verso una destinazione I/O lenta. | Usa framework di logging asincroni o bufferizza le scritture. |
| **Font personalizzati mancanti** | Cartella dei font non aggiunta a `FontSettings`. | Aggiungi `SetFontsFolder` come mostrato nel Passo 4.2. |

## Esempio Completo Funzionante – Copia‑e‑Incolla  

Di seguito trovi un programma autonomo che puoi copiare in un nuovo progetto Console App. Dimostra l'intero flusso dall'inizio alla fine.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Loading.Warning;

class Program
{
    static void Main()
    {
        // 1️⃣ Create LoadOptions.
        var loadOptions = new LoadOptions();

        // 2️⃣ Register the warning callback (register warning callback Aspose.Words).
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
            {
                var fontInfo = (FontSubstitutionWarningInfo)args;
                Console.WriteLine(
                    $"Font '{fontInfo.FontName}' was substituted with '{fontInfo.SubstitutedFontName}'.");
            }
            // Optional: handle other warnings here.
        };

        // Optional: tell Aspose where to find corporate fonts.
        // loadOptions.FontSettings = new FontSettings();
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", true);

        // 3️⃣ Load the document using the configured options.
        string filePath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        var doc = new Document(filePath, loadOptions);

        // At this point the document is loaded, and any font substitutions have been printed.
        Console.WriteLine("Document loaded successfully.");
    }
}
```

**Output console previsto** (supponendo font mancanti):

```
Font 'Calibri' was substituted with 'Arial'.
Font 'Times New Roman' was substituted with 'Liberation Serif'.
Document loaded successfully.
```

Esegui il programma e vedrai esattamente quali font Aspose.Words ha sostituito, offrendoti piena visibilità sul processo di caricamento.

---

## Conclusione  

Abbiamo appena coperto **come registrare un callback di avviso in Aspose.Words**, perché è una best‑practice per qualsiasi flusso di lavoro di elaborazione documenti, e come estendere il pattern per logging, font personalizzati e gestione più ampia degli avvisi. Con sole tre righe di codice trasformi un'operazione di caricamento “black‑box” in un passaggio auditabile e debug‑abile—niente più misteriosi cambiamenti di layout.

Cosa fare dopo? Prova a combinare questo callback con **Aspose.Words SaveOptions** per registrare avvisi sia durante il caricamento *che* il salvataggio, oppure collega il callback a un'API web che processa upload in tempo reale. Puoi anche esplorare le altre parole chiave secondarie introdotte—come *loadoptions font substitution warning*—per ottimizzare le prestazioni o integrarle in una dashboard di monitoraggio.

Hai domande o uno scenario difficile? Lascia un commento e risolviamo insieme. Buona programmazione, e che i tuoi PDF vengano sempre renderizzati con i font corretti!

## Cosa Dovresti Imparare Dopo?


I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aspose Words Java Callback Custom Savings](/words/german/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/french/java/images-shapes/aspose-words-java-callback-custom-savings/)
- [Aspose Words Java Callback Custom Savings](/words/spanish/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}