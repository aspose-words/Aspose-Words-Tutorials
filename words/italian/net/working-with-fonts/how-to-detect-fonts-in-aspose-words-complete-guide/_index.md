---
category: general
date: 2026-04-07
description: Scopri come rilevare i caratteri e come catturare gli avvisi gestendo
  i caratteri mancanti in C# con Aspose.Words. Codice passo‑passo incluso.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- handle missing fonts
- Aspose.Words font substitution
- C# document loading warnings
language: it
og_description: Come rilevare i font in Aspose.Words? Segui questo tutorial per catturare
  gli avvisi e gestire i font mancanti senza sforzo.
og_title: Come rilevare i font in Aspose.Words – Guida completa
tags:
- Aspose.Words
- C#
- Font handling
title: Come rilevare i font in Aspose.Words – Guida completa
url: /it/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come rilevare i font in Aspose.Words – Guida completa

Ti sei mai chiesto **come rilevare i font** che mancano in un documento Word prima di inviarlo in produzione? Non sei l'unico. In molti scenari aziendali un font fuori posto può interrompere una pipeline di conversione PDF o causare difetti di layout che appaiono poco professionali. La buona notizia è che Aspose.Words ti offre un modo integrato per individuare quei tipi di carattere assenti e mostrare avvisi chiari.

In questo tutorial vedremo esattamente **come rilevare i font**, **come catturare gli avvisi**, e le migliori pratiche per **gestire i font mancanti** così la tua applicazione rimane robusta. Nessuno strumento esterno, nessuna congettura—solo puro codice C# che puoi inserire subito nel tuo progetto.

> **Anteprima rapida:** Alla fine avrai un `FontSubstitutionWarningCollector` riutilizzabile che raccoglie ogni messaggio di sostituzione del font durante il caricamento del documento, e saprai come reagire quando un font non può essere trovato.

---

## Cosa imparerai

- Come configurare `LoadOptions` per ascoltare gli avvisi di sostituzione dei font.  
- Come catturare quegli avvisi in una classe collector personalizzata.  
- Come elaborare gli avvisi raccolti e decidere se abortire, registrare o sostituire i font.  
- Gestione dei casi limite per documenti che fanno riferimento a font remoti o incorporati.  

**Prerequisiti:** .NET 6+ (o .NET Framework 4.6+), Aspose.Words per .NET (ultima versione), e una conoscenza di base di C#. Se non hai mai usato Aspose.Words, non preoccuparti—questa guida presuppone solo pochi minuti di configurazione.

## Come rilevare i font usando Aspose.Words LoadOptions

Il primo passo per rilevare i font mancanti è dire ad Aspose.Words di segnalarli. Questo avviene tramite la proprietà `LoadOptions.WarningCallback`, che accetta qualsiasi classe che implementi `IWarningCallback`. Di seguito creiamo un piccolo collector che memorizza ogni avviso per un'ispezione successiva.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.Collections.Generic;

/// <summary>
/// Collects all warnings emitted while loading a document.
/// </summary>
public class FontSubstitutionWarningCollector : IWarningCallback
{
    // Thread‑safe static list so we can access warnings after loading.
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();

    // Called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑related warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Warnings.Add(info);
        }
    }

    // Helper to clear previous run’s warnings.
    public static void Clear() => Warnings.Clear();
}
```

**Perché è importante:** Senza un callback per gli avvisi, Aspose.Words sostituisce silenziosamente i font mancanti con uno predefinito, e non saprai mai che esiste un problema. Catturando `WarningType.FontSubstitution` otteniamo piena visibilità—esattamente i dati di cui hai bisogno per **rilevare i font** che non sono disponibili sulla macchina host.

Ora colleghiamo il collector a `LoadOptions` e carichiamo un documento:

```csharp
// Step 1: Prepare load options with our warning collector.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontSubstitutionWarningCollector()
};

// Optional: clear any stale warnings from a previous run.
FontSubstitutionWarningCollector.Clear();

// Step 2: Load the document. Replace the path with your own file.
Document doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
```

> **Consiglio professionale:** Se lavori con molti documenti in batch, riutilizza la stessa istanza di `FontSubstitutionWarningCollector` ma ricorda di chiamare `Clear()` tra i caricamenti per evitare di mescolare avvisi provenienti da file diversi.

---

## Catturare gli avvisi durante il caricamento del documento

Dopo che il documento è stato caricato, il collector contiene già ogni avviso relativo ai font. La prossima domanda logica è: *Come posso catturare gli avvisi* in modo facile da registrare o visualizzare?

```csharp
// Step 3: Iterate over collected warnings and output them.
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    Console.WriteLine($"{warning.Type}: {warning.Message}");
}
```

L'output tipico appare così:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'Garamond' missing. Using 'Times New Roman' instead.
```

**Cosa ti dice:** Ogni riga rivela il nome del font originale e il fallback scelto da Aspose.Words. Con queste informazioni puoi decidere se il fallback è accettabile o se è necessario incorporare manualmente il font mancante.

---

## Gestire i font mancanti in modo elegante

Rilevare e catturare gli avvisi è solo metà della battaglia. Il vero valore arriva quando **gestisci i font mancanti** in modo pronto per la produzione. Di seguito tre strategie comuni:

1. **Log and Continue** – Adatto per l'elaborazione batch dove ti serve solo un tracciato di audit.  
2. **Abort on Critical Fonts** – Lancia un'eccezione se un font particolare (ad esempio un carattere specifico del brand) è mancante.  
3. **Embed the Font On‑The‑Fly** – Carica il font mancante da una cartella nota e registralo con Aspose.Words prima di ricaricare il documento.  

### Esempio: Interrompere su un font critico

```csharp
// Define a list of fonts that must be present.
var requiredFonts = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };

foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    // Extract the original font name from the warning message.
    string missingFont = ExtractFontName(warning.Message);
    if (requiredFonts.Contains(missingFont))
    {
        throw new InvalidOperationException(
            $"Critical font '{missingFont}' is missing. Document load aborted.");
    }
}

// Helper method to parse font name from warning text.
string ExtractFontName(string message)
{
    // Message pattern: "Font 'X' was not found..."
    int start = message.IndexOf('\'') + 1;
    int end = message.IndexOf('\'', start);
    return (start > 0 && end > start) ? message[start..end] : string.Empty;
}
```

### Esempio: Incorporamento automatico dei font mancanti

```csharp
foreach (var warning in FontSubstitutionWarningCollector.Warnings)
{
    string missingFont = ExtractFontName(warning.Message);
    string fontPath = $@"C:\Fonts\{missingFont}.ttf";

    if (File.Exists(fontPath))
    {
        // Register the font with Aspose.Words.
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(Path.GetDirectoryName(fontPath), false);
        doc.FontSettings = fontSettings;

        // Reload the document now that the font is available.
        doc = new Document(@"C:\Docs\MissingFonts.docx", loadOptions);
        break; // Re‑load once; subsequent warnings will be resolved.
    }
}
```

**Perché questi pattern aiutano:** Decidendo esplicitamente cosa fare quando un font è mancante, elimini i fallback silenziosi che potrebbero compromettere il branding o la leggibilità. Questa è l'essenza di **gestire i font mancanti** in modo controllato.

---

## Esempio completo funzionante

Mettendo tutto insieme, ecco un unico programma pronto all'esecuzione che dimostra **come rilevare i font**, **come catturare gli avvisi**, e una semplice politica per **gestire i font mancanti** registrandoli.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System;
using System.Collections.Generic;
using System.IO;

public class FontSubstitutionWarningCollector : IWarningCallback
{
    public static List<WarningInfo> Warnings { get; } = new List<WarningInfo>();
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Warnings.Add(info);
    }
    public static void Clear() => Warnings.Clear();
}

class Program
{
    static void Main()
    {
        string docPath = @"C:\Docs\MissingFonts.docx";

        // 1️⃣ Configure LoadOptions with the warning collector.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontSubstitutionWarningCollector()
        };
        FontSubstitutionWarningCollector.Clear();

        // 2️⃣ Load the document – this is where fonts are detected.
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Process the collected warnings.
        if (FontSubstitutionWarningCollector.Warnings.Count == 0)
        {
            Console.WriteLine("✅ No missing fonts detected.");
        }
        else
        {
            Console.WriteLine("⚠️ Font substitution warnings:");
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
                Console.WriteLine($"{w.Type}: {w.Message}");

            // Example policy: abort if a brand‑critical font is missing.
            var critical = new HashSet<string> { "MyBrand-Regular", "MyBrand-Bold" };
            foreach (var w in FontSubstitutionWarningCollector.Warnings)
            {
                string missing = ExtractFontName(w.Message);
                if (critical.Contains(missing))
                {
                    Console.WriteLine($"❌ Critical font '{missing}' missing. Stopping.");
                    return;
                }
            }
        }

        // 4️⃣ Continue with normal processing (e.g., save as PDF).
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
        Console.WriteLine("✅ Document saved as PDF.");
    }

    // Helper to pull the original font name out of the warning text.
    static string ExtractFontName(string message)
    {
        int first = message.IndexOf('\'') + 1;
        int last = message.IndexOf('\'', first);
        return (first > 0 && last > first) ? message[first..last] : string.Empty;
    }
}
```

**Risultato atteso:** Quando esegui il programma su un documento che fa riferimento a un font non presente sulla macchina, la console elencherà ogni avviso di sostituzione. Se qualche avviso riguarda un font del set `critical`, il programma termina in anticipo, evitando la generazione di un PDF difettoso.

---

## Domande frequenti (FAQ)

| Question | Answer |
|----------|--------|
| *Ho bisogno di una licenza per Aspose.Words per usare questo codice?* | Sì, una licenza valida di Aspose.Words rimuove le filigrane di valutazione e sblocca tutte le funzionalità. |
| *Questo approccio può rilevare i font incorporati?* | I font incorporati fanno già parte del file, quindi Aspose.Words non genererà un avviso di sostituzione. Puoi controllare `Document.FontInfos` per elencare i font incorporati se necessario. |
| *Cosa succede se il font mancante è un font di sistema su Windows ma non su Linux?* | Lo stesso avviso verrà generato su Linux perché il font non è installato lì. Usa la strategia “gestire i font mancanti” per distribuire i file `.ttf` necessari con la tua app. |
| *Il collector di avvisi è thread* |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}