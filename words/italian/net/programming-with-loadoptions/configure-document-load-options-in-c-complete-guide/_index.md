---
category: general
date: 2026-06-05
description: Configura le opzioni di caricamento del documento in C# per gestire gli
  avvisi di sostituzione dei caratteri e personalizzare il comportamento di caricamento
  utilizzando una callback di avviso.
draft: false
keywords:
- configure document load options
- warning callback
- font substitution warning
- LoadOptions usage
- Aspose.Words document loading
- C# document loading options
language: it
og_description: Configura le opzioni di caricamento del documento in C# per gestire
  gli avvisi di sostituzione dei font e perfeziona il caricamento del documento con
  una callback di avviso.
og_title: Configura le opzioni di caricamento del documento in C# – Guida completa
schemas:
- author: Aspose
  dateModified: '2026-06-05'
  description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  headline: Configure document load options in C# – Complete Guide
  type: TechArticle
- description: Configure document load options in C# to handle font substitution warnings
    and customize loading behavior using a warning callback.
  name: Configure document load options in C# – Complete Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Framework 4.6+ as well).
      - Aspose.Words for .NET installed (`dotnet add package Aspose.Words`). - Basic
      familiarity with C# syntax.'
  - name: Implement a Warning Callback for Font Substitution
    text: First things first—what’s a **warning callback**? In Aspose.Words it’s a
      delegate that gets invoked whenever the library encounters something worth flagging,
      like a missing font. By catching `WarningType.FontSubstitution` we can log the
      exact font the engine swapped out.
  - name: Set Up LoadOptions with the Callback
    text: Now that we have a callback, we need to **configure document load options**
      to actually use it. `LoadOptions` is a lightweight container that tells Aspose.Words
      how to behave during the `Document` constructor call.
  - name: Load the Document Using the Configured Options
    text: With the callback wired up, the final act is to actually **load the document**.
      The `Document` constructor accepts a file path and the `LoadOptions` we just
      prepared.
  - name: Optional – Verify Loaded Fonts (Edge Case Handling)
    text: Sometimes you might want to *pre‑validate* the document before loading it
      fully, especially in batch processing scenarios. Aspose.Words offers the `FontSettings`
      class that can enumerate required fonts.
  - name: What if the warning callback throws an exception?
    text: The callback runs on the same thread that loads the document. Throwing inside
      the delegate will abort the load and propagate the exception. Wrap your logic
      in a `try/catch` if you need resilience.
  - name: Can I suppress *all* warnings instead of handling them?
    text: Yes—set `loadOptions.WarningCallback = null;` or provide a callback that
      does nothing. Be aware you’ll lose visibility into potential problems.
  - name: Does this work with encrypted DOCX files?
    text: Absolutely. Just add `Password = "yourPassword"` to `LoadOptions` before
      creating the `Document`. The warning callback will still fire for font issues.
  - name: How does this differ from using `DocumentBuilder`?
    text: '`DocumentBuilder` is for *creating* or *modifying* a document after it’s
      loaded. **Configure document load options** influences the *initial* parsing
      stage, which is where font substitution decisions are made.'
  type: HowTo
tags:
- C#
- Aspose.Words
- LoadOptions
- DocumentProcessing
title: Configura le opzioni di caricamento del documento in C# – Guida completa
url: /it/net/programming-with-loadoptions/configure-document-load-options-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configurare le opzioni di caricamento del documento in C# – Guida completa

Ti è mai capitato di dover **configurare le opzioni di caricamento del documento** in C# perché il comportamento di caricamento predefinito non era sufficiente? Forse osservi sostituzioni di caratteri inattese o vuoi registrare ogni avviso che compare durante l’importazione di un file. In questo tutorial percorreremo una soluzione pratica, end‑to‑end, che non solo imposta tali opzioni ma dimostra anche un **callback di avviso** per gli avvisi di sostituzione dei font.

Copriremo tutto, dal piccolo frammento di codice che crea il callback al momento in cui apri finalmente il documento con le impostazioni personalizzate. Alla fine avrai un modello riutilizzabile da inserire in qualsiasi progetto Aspose.Words, sia che tu stia elaborando fatture, contratti legali o semplici report.

## Cosa imparerai

- Come **configurare le opzioni di caricamento del documento** con `LoadOptions`.
- Come implementare un **callback di avviso** che intercetta gli avvisi `FontSubstitution`.
- Perché gestire in anticipo un **avviso di sostituzione del font** può salvarti da sorprese di layout.
- Gestione dei casi limite per font mancanti e come ricorrere a un fallback in modo elegante.
- Un esempio di codice completo, pronto per il copia‑incolla, che puoi eseguire subito.

### Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+).
- Aspose.Words per .NET installato (`dotnet add package Aspose.Words`).
- Familiarità di base con la sintassi C#.

Se hai tutto questo, tuffiamoci.

## Configurare le opzioni di caricamento del documento – Passo‑per‑passo

Di seguito è riportato l’intero flusso di lavoro suddiviso in quattro passaggi chiari. Ogni passaggio è spiegato, seguito da un conciso blocco di codice che puoi incollare direttamente in Visual Studio.

### Passo 1: Implementare un callback di avviso per la sostituzione dei font

Prima di tutto—cos’è un **callback di avviso**? In Aspose.Words è un delegato che viene invocato ogni volta che la libreria incontra qualcosa di degno di segnalazione, come un font mancante. Catturando `WarningType.FontSubstitution` possiamo registrare il font esatto che il motore ha sostituito.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Step 1: Define a warning callback that reports font substitution warnings
var fontWarningCallback = new IWarningCallback(
    warningInfo =>
    {
        // Check if the warning is about font substitution
        if (warningInfo.WarningType == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or telemetry system
            Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
        }
    });
```

**Perché è importante:** Senza un callback, la libreria sostituisce silenziosamente i font mancanti, il che può portare a testo illeggibile nel PDF o DOCX finale. Rendendo visibile l’avviso ottieni trasparenza e puoi decidere se incorporare il font mancante, passare a un fallback o avvisare l’utente.

> **Consiglio esperto:** Se devi catturare *tutti* gli avvisi, rimuovi il controllo `if`. Basta registrare `warningInfo.Description` per ogni evento.

### Passo 2: Configurare LoadOptions con il callback

Ora che abbiamo un callback, dobbiamo **configurare le opzioni di caricamento del documento** per usarlo realmente. `LoadOptions` è un contenitore leggero che indica ad Aspose.Words come comportarsi durante la chiamata al costruttore `Document`.

```csharp
// Step 2: Attach the callback to the LoadOptions object
var loadOptions = new LoadOptions
{
    WarningCallback = fontWarningCallback,
    // Optional: enforce strict loading mode (throws on any warning)
    // LoadFormat = LoadFormat.Docx,
    // LoadOptions.LoadFormat can be left null to auto-detect based on file extension
};
```

**Perché è importante:** Assegnando `WarningCallback`, ogni avviso emesso durante la fase di caricamento passa attraverso il nostro delegato. Qui puoi anche modificare altre proprietà di `LoadOptions`, come `LoadFormat` se conosci il tipo di file esatto, o `Password` per documenti criptati.

### Passo 3: Caricare il documento usando le opzioni configurate

Con il callback collegato, l’ultimo atto è **caricare effettivamente il documento**. Il costruttore `Document` accetta un percorso file e le `LoadOptions` appena preparate.

```csharp
// Step 3: Load the document with our custom options
string inputPath = @"C:\Docs\input.docx";   // Adjust to your environment
Document doc = new Document(inputPath, loadOptions);
```

Se il file di origine fa riferimento a un font non installato sulla macchina, vedrai una riga simile a:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

nella console. Questo feedback immediato ti consente di decidere se distribuire il font mancante insieme all’app o sostituirlo programmaticamente.

### Passo 4: Facoltativo – Verificare i font caricati (gestione dei casi limite)

A volte potresti voler *pre‑validare* il documento prima di caricarlo completamente, specialmente in scenari di elaborazione batch. Aspose.Words offre la classe `FontSettings` che può enumerare i font richiesti.

```csharp
// Optional: Check required fonts before full load
var fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
loadOptions.FontSettings = fontSettings;

// Re-load the document now that we have a custom font folder
Document docWithCustomFonts = new Document(inputPath, loadOptions);
```

**Quando usarla:** Se mantieni un repository privato di font (ad esempio i font del brand aziendale), puntare `FontSettings` a quella cartella garantisce che il motore trovi i caratteri corretti senza ricorrere a quelli generici.

## Esempio completo funzionante

Di seguito trovi l’intero programma—copia, incolla ed esegui. Dimostra tutto, dalla creazione del callback al caricamento finale del documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class Program
{
    static void Main()
    {
        // 1️⃣ Define the warning callback
        var fontWarningCallback = new IWarningCallback(
            warningInfo =>
            {
                if (warningInfo.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substitution detected: {warningInfo.Description}");
                }
            });

        // 2️⃣ Configure LoadOptions with the callback
        var loadOptions = new LoadOptions
        {
            WarningCallback = fontWarningCallback,
            // Uncomment the next line to point to a custom font folder
            // FontSettings = new FontSettings { SetFontsFolder(@"C:\MyFonts", true) }
        };

        // 3️⃣ Load the document using the custom options
        string inputFile = @"YOUR_DIRECTORY/input.docx";
        Document doc = new Document(inputFile, loadOptions);

        // 4️⃣ (Optional) Save as PDF to verify everything works
        string outputFile = @"YOUR_DIRECTORY/output.pdf";
        doc.Save(outputFile);
        Console.WriteLine($"Document loaded and saved to {outputFile}");
    }
}
```

**Output previsto**

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Document loaded and saved to C:\Your\Path\output.pdf
```

Se non esistono font mancanti, il callback rimane semplicemente silenzioso—nulla di cui preoccuparsi.

## Domande frequenti e casi limite

### Cosa succede se il callback di avviso genera un’eccezione?

Il callback viene eseguito sullo stesso thread che carica il documento. Lanciare un’eccezione all’interno del delegato interromperà il caricamento e propagherà l’eccezione. Avvolgi la tua logica in un `try/catch` se hai bisogno di resilienza.

### Posso sopprimere *tutti* gli avvisi invece di gestirli?

Sì—imposta `loadOptions.WarningCallback = null;` o fornisci un callback che non fa nulla. Tieni presente che perderai la visibilità su potenziali problemi.

### Funziona con file DOCX criptati?

Assolutamente. Basta aggiungere `Password = "yourPassword"` a `LoadOptions` prima di creare il `Document`. Il callback di avviso continuerà a scattare per problemi di font.

### In che modo questo differisce dall’uso di `DocumentBuilder`?

`DocumentBuilder` serve a *creare* o *modificare* un documento dopo che è stato caricato. **Configurare le opzioni di caricamento del documento** influisce sulla fase di parsing *iniziale*, dove vengono prese le decisioni di sostituzione dei font.

## Panoramica visiva

![Diagramma che mostra il flusso di configurazione delle opzioni di caricamento del documento](https://example.com/images/load-options-flow.png "Diagramma che mostra il flusso di configurazione delle opzioni di caricamento del documento")

*L’immagine illustra il flusso: callback → LoadOptions → costruttore Document → gestione degli avvisi.*

## Conclusione

Ora sai come **configurare le opzioni di caricamento del documento** in C# per catturare gli avvisi di sostituzione dei font, inserire cartelle di font personalizzate e mantenere il pieno controllo sul processo di caricamento. Questo modello ti dà la certezza che ogni font mancante verrà segnalato, permettendoti di preservare la fedeltà dei documenti in qualsiasi ambiente.

Prossimi passi? Prova a sostituire la registrazione su console con un sistema di telemetria più robusto, o combina questo approccio con `DocumentBuilder` per sostituire automaticamente i font mancanti con un default aziendale. Potresti anche esplorare altri valori di `WarningType` come `DocumentStructure` per ottenere approfondimenti ancora più dettagliati.

Buona programmazione, e che i tuoi documenti vengano sempre renderizzati esattamente come desideri!


## Cosa dovresti imparare dopo?


I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑paso per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Master Aspose.Words Markdown Load Options in Python for Enhanced Document Processing](/words/english/python-net/document-operations/aspose-words-markdown-load-options-python/)
- [Optimizing Document Loading with HTML, RTF, and TXT Options](/words/english/java/word-processing/optimizing-document-loading-options/)
- [Using Document Options and Settings in Aspose.Words for Java](/words/english/java/document-manipulation/using-document-options-and-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}