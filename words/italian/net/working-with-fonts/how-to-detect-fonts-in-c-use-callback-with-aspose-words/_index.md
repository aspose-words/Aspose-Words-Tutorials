---
category: general
date: 2026-03-17
description: Come rilevare i font in C# usando Aspose.Words e una callback di avviso.
  Scopri come utilizzare la callback per catturare le sostituzioni di font mancanti
  durante il caricamento dei documenti.
draft: false
keywords:
- how to detect fonts
- how to use callback
- Aspose.Words font detection
- C# missing font warning
- warning callback example
language: it
og_description: Come rilevare i font in C# usando Aspose.Words. Questa guida mostra
  come utilizzare un callback per catturare gli avvisi di font mancanti durante il
  caricamento di un documento.
og_title: Come rilevare i font in C# – Usa il callback con Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Come rilevare i font in C# – Usa il callback con Aspose.Words
url: /it/net/working-with-fonts/how-to-detect-fonts-in-c-use-callback-with-aspose-words/
---

"# How to Detect Fonts in C# – Use Callback with Aspose.Words" -> Italian: "# Come rilevare i font in C# – Utilizzare il callback con Aspere.Words". Keep Aspose.Words unchanged.

Paragraphs.

Let's translate.

Will produce final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come rilevare i font in C# – Utilizzare il callback con Aspose.Words

Hai mai avuto bisogno di **come rilevare i font** in un documento Word in modo programmatico e ti sei chiesto perché alcuni caratteri appaiono strani dopo la conversione? Non sei solo. In molti progetti reali—generatori di fatture, esportatori di report o pipeline di elaborazione batch—i font mancanti causano anomalie di layout silenziose difficili da debugare.  

La buona notizia? Aspose.Words ti offre un modo pulito per evidenziare questi problemi con un callback di avviso. In questo tutorial vedrai **come usare il callback** per catturare ogni sostituzione di font che Aspose esegue durante il caricamento di un documento, e otterrai un esempio pronto all'uso che stampa un report chiaro dei font mancanti.

Tratteremo:

* I prerequisiti minimi (un progetto .NET e il pacchetto NuGet Aspose.Words).  
* Come implementare `IWarningCallback` per ascoltare `WarningType.FontSubstitution`.  
* Come collegare il callback a `LoadOptions` e caricare un documento.  
* Come appare l'output, più alcuni consigli pratici per il codice di produzione.

Alla fine, sarai in grado di **rilevare automaticamente i font** in qualsiasi file DOCX, DOC o RTF e agire sulle informazioni dei font mancanti—che si tratti di registrare un log, avvisare l'utente o sostituire un font di fallback.

---

![Come rilevare i font in un documento Word usando il callback di avviso di Aspose.Words](https://example.com/images/detect-fonts.png "come rilevare i font in un documento Word")

## Cosa ti serve

* **.NET 6.0** o versioni successive (l'esempio compila anche con .NET Framework 4.6+).  
* **Aspose.Words for .NET** – installa via NuGet: `Install-Package Aspose.Words`.  
* Un file Word di esempio che faccia riferimento deliberatamente a un font non installato (ad es., `MissingFont.docx`).  

Non sono necessarie librerie aggiuntive; tutto risiede nello spazio dei nomi Aspose.

---

## Come rilevare i font con un callback di avviso

### Passo 1: Creare una classe di callback di avviso

Il callback implementa `IWarningCallback`. Quando Aspose.Words incontra un font che non riesce a trovare, genera un `WarningInfo` con `WarningType.FontSubstitution`. La nostra classe scrive semplicemente una riga amichevole sulla console.

```csharp
using System;
using Aspose.Words.Warnings;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about missing‑font warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Example output: [Font substitution] Missing: "Comic Sans MS"
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
        }
    }
}
```

**Perché è importante:** Filtrando su `WarningType.FontSubstitution` evitiamo avvisi rumorosi (come funzionalità deprecate) e manteniamo il log concentrato sul problema specifico che stai cercando di risolvere—**rilevare i font** che non sono presenti sulla macchina.

---

### Passo 2: Collegare il callback a `LoadOptions`

`LoadOptions` consente di personalizzare il modo in cui un documento viene analizzato. Assegnando il nostro `FontWarningCollector` alla proprietà `WarningCallback`, diciamo ad Aspose di invocarlo ogni volta che viene incontrato un font mancante.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

// Configure load options with our custom warning handler.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCollector()
};
```

**Suggerimento:** Puoi anche impostare `LoadOptions.FontSettings` qui se vuoi fornire programmaticamente un font di fallback. È uno scenario avanzato che menzioneremo più avanti.

---

### Passo 3: Caricare il documento e osservare l'output

Ora carichiamo effettivamente il file. Non appena Aspose analizza il documento, qualsiasi font che non riesce a localizzare attiva il nostro callback.

```csharp
// Replace the path with the location of your test document.
string docPath = @"C:\Docs\MissingFont.docx";

try
{
    Document doc = new Document(docPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
}
```

**Output previsto sulla console** (supponendo che il documento faccia riferimento a *Comic Sans MS* non installato):

```
[Font substitution] Missing: "Comic Sans MS"
Document loaded successfully.
```

Se il documento contiene più font mancanti, vedrai una riga per ogni font—esattamente le informazioni di **come rilevare i font** di cui hai bisogno.

---

## Come usare il callback per scenari più complessi

### Registrare su file anziché sulla console

In produzione probabilmente vuoi un log persistente. Sostituisci `Console.WriteLine` con uno `StreamWriter`:

```csharp
class FontWarningCollector : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            File.AppendAllText(_logPath,
                $"[Font substitution] Missing: {info.Description}{Environment.NewLine}");
        }
    }
}
```

### Raccogliere gli avvisi per analisi successive

A volte è necessario l'elenco dei font mancanti dopo il caricamento del documento, magari per mostrare una finestra di dialogo UI. Memorizza gli avvisi in una `List<string>` ed esponila:

```csharp
class FontWarningCollector : IWarningCallback
{
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            MissingFonts.Add(info.Description);
        }
    }
}

// Usage
var collector = new FontWarningCollector();
LoadOptions opts = new LoadOptions { WarningCallback = collector };
Document doc = new Document(docPath, opts);

if (collector.MissingFonts.Any())
{
    Console.WriteLine("Missing fonts detected:");
    collector.MissingFonts.ForEach(f => Console.WriteLine($"- {f}"));
}
```

### Fornire un font di fallback programmaticamente

Se hai un font aziendale da imporre, puoi aggiungerlo a `FontSettings` prima del caricamento:

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial Unicode MS";

LoadOptions opts = new LoadOptions
{
    WarningCallback = new FontWarningCollector(),
    FontSettings = fontSettings
};

Document doc = new Document(docPath, opts);
```

Ora Aspose sostituisce i font mancanti con *Arial Unicode MS* continuando a segnalare la sostituzione tramite il callback. Questo è un modo intelligente per **come usare il callback** sia per la rilevazione sia per la rimessione automatica.

---

## Problemi comuni e consigli professionali

| Problema | Perché accade | Come evitarlo |
|----------|---------------|---------------|
| **Dimenticare di fare riferimento a `Aspose.Words.Warnings`** | L'interfaccia `IWarningCallback` si trova lì. | Aggiungi `using Aspose.Words.Warnings;` in cima al file. |
| **Caricare un documento senza `LoadOptions`** | Il loader predefinito sostituisce silenziosamente i font senza notifica. | Crea sempre un'istanza di `LoadOptions` e assegna il tuo callback. |
| **Eseguire su un server con permessi limitati** | Scrivere su un file di log può generare `UnauthorizedAccessException`. | Usa una cartella scrivibile (ad es., la directory dati dell'app) o rimani su collezioni in memoria. |
| **Thread multipli che condividono lo stesso collector** | `FontWarningCollector` non è thread‑safe di default. | Crea un collector separato per ogni thread o proteggi la lista con un lock. |
| **Supporre che il callback scatti per i font incorporati** | I font incorporati sono già presenti nel documento; non viene generato alcun avviso. | Se devi verificare l'integrità dei font incorporati, ispeziona `FontInfo` tramite `FontSettings`. |

---

## Esempio completo (pronto da copiare‑incollare)

```csharp
// ------------------------------------------------------------
// Detect missing fonts in a Word document using Aspose.Words
// ------------------------------------------------------------
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningCollector : IWarningCallback
{
    // Store warnings for later use (optional)
    public List<string> MissingFonts { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Print to console
            Console.WriteLine($"[Font substitution] Missing: {info.Description}");
            // Keep a copy in memory
            MissingFonts.Add(info.Description);
        }
    }
}

class Program
{
    static void Main()
    {
        // Path to the document you want to inspect
        string docPath = @"YOUR_DIRECTORY\MissingFont.docx";

        // 1️⃣ Create the callback collector
        var collector = new FontWarningCollector();

        // 2️⃣ Set up LoadOptions with the callback
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = collector
        };

        // 3️⃣ Load the document – warnings will fire automatically
        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");

            // Optional: act on the collected data
            if (collector.MissingFonts.Count > 0)
            {
                Console.WriteLine("\nSummary of missing fonts:");
                foreach (var font in collector.MissingFonts)
                    Console.WriteLine($"- {font}");
            }
            else
            {
                Console.WriteLine("\nNo missing fonts detected.");
            }
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Cosa dovresti vedere** (supponendo che il file faccia riferimento a due font assenti):

```
[Font substitution] Missing: "Comic Sans MS"
[Font substitution] Missing: "Papyrus"
Document loaded successfully.

Summary of missing fonts:
- Comic Sans MS
- Papyrus
```

Se il file utilizza solo font installati, la console stampa semplicemente:

```
Document loaded successfully.

No missing fonts detected.
```

---

## Conclusioni

Abbiamo esaminato **come rilevare i font** in un documento Word collegando un callback di avviso personalizzato a Aspose.Words. L'approccio è leggero, richiede

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}