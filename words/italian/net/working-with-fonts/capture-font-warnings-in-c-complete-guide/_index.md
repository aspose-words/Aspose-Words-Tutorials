---
category: general
date: 2026-03-06
description: Cattura gli avvisi di font durante il caricamento di un documento Word
  in C#. Impara a rilevare i font mancanti, controllare i font del documento e gestire
  i font mancanti in modo efficiente.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- load word document
- check document fonts
- handle missing fonts
language: it
og_description: Cattura gli avvisi di font durante il caricamento di un documento
  Word in C#. Questo tutorial mostra come rilevare i font mancanti, verificare i font
  del documento e gestire i font mancanti.
og_title: Cattura gli avvisi dei font in C# – Guida completa
tags:
- Aspose.Words
- C#
- Font Management
title: Cattura gli avvisi di font in C# – Guida completa
url: /it/net/working-with-fonts/capture-font-warnings-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Catturare gli avvisi di font in C# – Guida completa

Hai mai avuto bisogno di **catturare gli avvisi di font** durante l'elaborazione di un documento Word? Catturare gli avvisi di font è essenziale per **rilevare i font mancanti** e assicurarsi che il risultato finale abbia esattamente l'aspetto desiderato.  

In questo tutorial percorreremo un esempio pratico, end‑to‑end, che carica un file `.docx`, monitora il processo di caricamento e segnala eventuali sostituzioni di font. Alla fine saprai come **caricare un documento Word** in modo sicuro, **controllare i font del documento** e **gestire i font mancanti** senza sorprese a runtime.

## Cosa imparerai

- Come collegare un raccoglitore di avvisi a un `Document` di Aspose.Words.  
- Quali tipi di avviso indicano un font mancante o sostituito.  
- Modi per registrare o reagire a quegli avvisi in un'app di livello produzione.  
- Suggerimenti per configurare font personalizzati se devi **gestire i font mancanti** in modo elegante.

> **Prerequisito:** Hai una licenza valida di Aspose.Words per .NET (oppure stai usando la versione di prova) e un ambiente di sviluppo .NET (Visual Studio, Rider o VS Code). Non sono richieste altre librerie.

---

## Catturare gli avvisi di font – Passo‑per‑passo

Di seguito trovi il codice completo, eseguibile. Ogni sezione è suddivisa in un proprio passo così da poter copiare‑incollare, sperimentare e ampliare la logica.

![Diagramma di raccolta avvisi di font](image.png "Diagramma che mostra la raccolta degli avvisi"){: alt="diagramma di raccolta avvisi di font"}

### Passo 1: Caricare il documento Word

Per prima cosa, dobbiamo **caricare il documento Word** che potrebbe contenere font non installati sulla macchina corrente. Il costruttore `Document` fa il lavoro pesante, ma manterremo la chiamata isolata così potrai sostituirla con uno stream o un array di byte in seguito, se necessario.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        // 👉 Replace the path with the location of your .docx file.
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Step 1: Load the Word document.
        Document doc = LoadDocument(inputPath);

        // Step 2 and 3 are performed inside LoadDocument – see below.
    }

    /// <summary>
    /// Loads a document while attaching a warning collector.
    /// Returns the Document instance ready for further processing.
    /// </summary>
    private static Document LoadDocument(string path)
    {
        // Create the warning collector before the load.
        var warningCollector = new WarningInfoCollector();

        // Attach the collector to the document’s warning callback.
        // This ensures that any font‑related warnings are captured.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // Load the file – this is where Aspose.Words may discover missing fonts.
        tempDoc = new Document(path);

        // After loading, iterate over warnings and report them.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }
```

**Perché è importante:** Caricare un documento senza un gestore di avvisi significa che qualsiasi sostituzione di font viene ignorata silenziosamente. Impostando `WarningCallback` *prima* del caricamento garantiamo di vedere ogni avviso `FontSubstitution` che si verifica.

### Passo 2: Collegare un raccoglitore di avvisi

La classe `WarningInfoCollector` è un'implementazione integrata di `IWarningCallback`. Essa memorizza semplicemente ogni avviso in una lista che potremo ispezionare in seguito.

```csharp
    /// <summary>
    /// Scans the collected warnings and prints information about missing fonts.
    /// </summary>
    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            // We’re only interested in font‑related warnings.
            if (warning.Type == WarningType.FontSubstitution)
            {
                // warning.Description contains the original font name.
                // warning.Subtype holds the name of the font that was actually used.
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Consiglio professionale:** Se devi **gestire i font mancanti** in modo più aggressivo (ad esempio, interrompere il caricamento o sostituire con un fallback specifico), puoi sostituire il `Console.WriteLine` con una logica personalizzata—lanciare un'eccezione, scrivere su un file di log o aggiungere una fonte di font personalizzata.

### Passo 3: Verificare l'output

Esegui il programma da console. Se il tuo `input.docx` utilizza un font non installato, vedrai righe simili a:

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
```

Se non compare alcun output, il documento ha usato solo font già disponibili **oppure** Aspose.Words ha trovato un font corrispondente nella sua collezione di fallback integrata. In entrambi i casi, hai **controllato i font del documento** con successo.

---

## Rilevare i font mancanti senza licenza (Versione di prova)

Anche con la versione di prova di 30 giorni, il meccanismo di avviso funziona esattamente allo stesso modo. L'unica differenza è che la versione di prova aggiunge una filigrana all'output generato, che **non** influisce sulla raccolta degli avvisi. Quindi puoi **rilevare i font mancanti** in tutta sicurezza prima di decidere se acquistare una licenza completa.

---

## Gestire i font mancanti – Opzioni avanzate

A volte vuoi fornire i tuoi file di font (ad esempio i font del brand aziendale) così che la sostituzione non avvenga mai. Aspose.Words ti permette di registrare cartelle di font personalizzate:

```csharp
// Register a folder that contains all your custom .ttf/.otf files.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
doc.FontSettings = fontSettings;
```

Inserisci il codice sopra **prima** di caricare il documento se vuoi che il loader consideri quei font durante la fase di parsing iniziale. Questo è il modo più affidabile per **gestire i font mancanti** senza dipendere dai font di sistema predefiniti.

---

## Errori comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Raccoglitore di avvisi collegato dopo il caricamento** | Il documento è già stato analizzato, quindi nessun avviso viene registrato. | Collega `WarningCallback` **prima** di chiamare `new Document(path)`. |
| **Compaiono solo avvisi generici** | Hai filtrato il tipo di avviso sbagliato. | Usa `WarningType.FontSubstitution` per concentrarti sui problemi di font. |
| **Nessun output nonostante font mancanti** | Aspose.Words ha trovato un fallback integrato (es. Arial). | Disattiva i fallback integrati con `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` |
| **Rallentamento durante la scansione di documenti grandi** | Raccogliere ogni avviso può essere costoso. | Limita la raccolta a `FontSubstitution` oppure elabora gli avvisi in batch. |

---

## Esempio completo funzionante (pronto per il copia‑incolla)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class FontWarningDemo
{
    static void Main()
    {
        string inputPath = @"YOUR_DIRECTORY\input.docx";

        // Load the document and capture any font warnings.
        Document doc = LoadDocument(inputPath);

        // At this point you can continue processing the document,
        // knowing that you’ve already reported any missing fonts.
        Console.WriteLine("Document loaded successfully.");
    }

    private static Document LoadDocument(string path)
    {
        var warningCollector = new WarningInfoCollector();

        // IMPORTANT: set the callback BEFORE the load.
        Document tempDoc = new Document();
        tempDoc.WarningCallback = warningCollector;

        // OPTIONAL: register custom font folder to reduce substitutions.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", recursive: true);
        tempDoc.FontSettings = fontSettings;

        // Load the document – this triggers warning collection.
        tempDoc = new Document(path);

        // Report any font substitutions.
        ReportFontWarnings(warningCollector);

        return tempDoc;
    }

    private static void ReportFontWarnings(WarningInfoCollector collector)
    {
        foreach (WarningInfo warning in collector.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine(
                    $"Font '{warning.Description}' was substituted with '{warning.Subtype}'.");
            }
        }
    }
}
```

**Output console previsto** (supponendo due font mancanti):

```
Font 'Comic Sans MS' was substituted with 'Arial'.
Font 'MyCustomFont' was substituted with 'Times New Roman'.
Document loaded successfully.
```

Se la console rimane silenziosa tranne che per “Document loaded successfully”, hai **controllato i font del documento** e non sono stati trovati font mancanti.

---

## Conclusione

Ti abbiamo mostrato come **catturare gli avvisi di font** in C# usando Aspose.Words, un metodo affidabile per **rilevare i font mancanti**, **caricare un documento Word** in sicurezza, **controllare i font del documento** e **gestire i font mancanti** tramite font personalizzati.  

Con questo modello puoi integrare la validazione dei font in qualsiasi pipeline di automazione—sia che tu stia generando PDF, convertendo in HTML o semplicemente archiviando file Word.

### Cosa fare dopo?

- Esplora l'API **FontSettings.SubstitutionSettings** per definire le tue regole di fallback.  
- Combina la raccolta degli avvisi con un framework di logging (Serilog, NLog) per il monitoraggio in produzione.  
- Usa lo stesso approccio per catturare altri tipi di avviso, come la risoluzione delle immagini o le funzionalità non supportate.

Hai altre domande sulla gestione dei font o su Aspose.Words in generale? Lascia un commento o visita i forum della community di Aspose. Buona programmazione, e che i tuoi documenti vengano sempre visualizzati con i font che ti aspetti!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}