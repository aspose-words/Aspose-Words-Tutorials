---
category: general
date: 2026-02-18
description: Scopri come catturare gli avvisi sui font e rilevare i font mancanti
  in C# usando Aspose.Words. Segui questa guida passo passo per gestire i font mancanti
  in modo efficiente.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- handle missing fonts
- list missing fonts
language: it
og_description: Cattura gli avvisi di font in C# e impara a rilevare i font mancanti,
  gestire i font mancanti e elencare i font mancanti con un esempio di codice completo.
og_title: Cattura gli avvisi di font in C# – Guida completa
tags:
- Aspose.Words
- C#
- Font Management
title: Cattura gli avvisi sui font in C# – Guida completa alla programmazione
url: /it/net/working-with-fonts/capture-font-warnings-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Catturare gli avvisi di font in C# – Guida completa alla programmazione

Ti sei mai chiesto come **catturare gli avvisi di font** quando un documento fa riferimento a un font che non è installato sul server? Non sei il solo. In molte applicazioni aziendali, i font mancanti causano anomalie di layout, e l'unico modo affidabile per individuarli è ascoltare gli avvisi che la libreria genera.  

In questo tutorial ti mostreremo una soluzione pronta all'uso che non solo **cattura gli avvisi di font**, ma anche **rileva i font mancanti**, **gestisce i font mancanti**, e persino **elenca i font mancanti**, così potrai decidere se sostituirli, incorporarli o avvisare l'utente. Nessuna documentazione esterna necessaria—basta copiare, incollare ed eseguire.

## Cosa imparerai

- Come configurare `LoadOptions` per attivare gli avvisi di sostituzione dei font.  
- Il codice esatto necessario per caricare un DOCX e estrarre ogni avviso.  
- Perché ogni passaggio è importante, incluse le considerazioni sulle prestazioni.  
- Gestione di casi limite, come documenti con font a script misti o cartelle di font personalizzate.  

**Prerequisiti**: .NET 6+ (o .NET Framework 4.6+), un riferimento al pacchetto NuGet **Aspose.Words**, e una conoscenza di base di C#. Se non hai mai usato Aspose.Words, non preoccuparti—questa guida ti accompagna passo passo.

![Diagram showing capture font warnings flow](image.png){alt="diagramma di cattura avvisi di font"}

## Catturare gli avvisi di font – Perché è importante

Quando Aspose.Words carica un documento, sostituisce silenziosamente qualsiasi font non disponibile con un fallback. Questo fallback mantiene viva l'operazione di caricamento, ma il risultato visivo può risultare completamente fuori centro. Attivando il flag **SubstitutionWarningLevel.All**, la libreria aggiunge una voce `WarningInfo` per ogni font mancante, consentendoti di **rilevare i font mancanti** prima che il documento venga renderizzato o salvato.

> **Consiglio professionale:** Se stai elaborando centinaia di file in un processo batch, registrare questi avvisi in un archivio centrale può farti risparmiare ore di QA manuale in seguito.

## Passo 1: Configura il tuo progetto

1. Apri il tuo IDE preferito (Visual Studio, Rider, VS Code).  
2. Crea un nuovo progetto console:

```bash
dotnet new console -n FontWarningDemo
cd FontWarningDemo
```

3. Aggiungi il pacchetto Aspose.Words:

```bash
dotnet add package Aspose.Words
```

È tutto—nessun DLL aggiuntivo, nessun COM interop. La libreria fornisce tutto il necessario per **gestire i font mancanti**.

## Passo 2: Prepara le Load Options per catturare tutti gli avvisi di sostituzione dei font

Per far sì che il motore **catturi gli avvisi di font**, devi indicargli di registrare ogni sostituzione. Il frammento seguente crea un'istanza di `LoadOptions`, abilita il livello di avviso e (facoltativamente) indica al motore una cartella che contiene font personalizzati che potresti voler usare.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -----------------------------------------------------------------
            // Step 2.1 – Create LoadOptions and turn on font‑substitution warnings
            // -----------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions();

            // Initialise FontSettings if you need to add a custom font folder
            loadOptions.FontSettings = new FontSettings();

            // Capture *all* font substitution events (this is the key for capture font warnings)
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // Optional: add a folder that contains corporate fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);
```

**Perché è importante:**  
- `SubstitutionWarningLevel.All` garantisce che **ogni** evento di font mancante venga registrato, non solo il primo.  
- Senza questo flag, Aspose.Words sostituisce silenziosamente il font e non saprai mai che esiste un problema.

## Passo 3: Carica il documento usando le opzioni configurate

Ora apriamo effettivamente il file. Sostituisci `DocumentWithMissingFonts.docx` con il percorso del tuo documento di test.

```csharp
            // -----------------------------------------------------------------
            // Step 2.2 – Load the document with the warning‑enabled options
            // -----------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";

            Document document = new Document(docPath, loadOptions);
```

Se il file contiene riferimenti a font che non sono presenti sulla macchina (o nella cartella opzionale che hai aggiunto), la `document.WarningInfoCollection` verrà popolata.

## Passo 4: Trova e visualizza gli avvisi di sostituzione dei font

Ecco il cuore del tutorial: iterare sulla `WarningInfoCollection` per **elencare i font mancanti**. Filtreremo per `WarningType.FontSubstitution` e stamperemo un messaggio amichevole.

```csharp
            // -----------------------------------------------------------------
            // Step 2.3 – Enumerate and output font substitution warnings
            // -----------------------------------------------------------------
            var fontWarnings = document.WarningInfoCollection
                                         .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    // The Description property already contains a readable message
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // Keep console window open when debugging
            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

### Output previsto

```
⚠️ Missing fonts detected:
- Missing font: "Comic Sans MS"
- Missing font: "Calibri Light"
```

Se il documento utilizza solo font installati, vedrai la riga “✅ No missing fonts detected”.

## Passo 5: Avanzato – Come **gestire i font mancanti** programmaticamente

Stampare semplicemente una lista può essere sufficiente per uno strumento diagnostico, ma molti sistemi di produzione hanno bisogno di **gestire i font mancanti** automaticamente. Di seguito due strategie comuni:

### 5.1 Sostituire con un fallback noto

```csharp
loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution
{
    // Replace any missing font with Arial, which is universally available
    SubstituteFont = "Arial"
};
```

### 5.2 Incorporare un font personalizzato al volo

Se disponi di un file di font aziendale (`MyBrand.ttf`), puoi incorporarlo quando viene rilevato un font mancante:

```csharp
foreach (WarningInfo warning in fontWarnings)
{
    string missingFontName = warning.Description.Split('"')[1]; // crude extraction
    // Load your custom font (ensure the path is correct)
    string customFontPath = $@"C:\MyCompany\Fonts\{missingFontName}.ttf";

    if (File.Exists(customFontPath))
    {
        loadOptions.FontSettings.SetFontsFolder(Path.GetDirectoryName(customFontPath), false);
        Console.WriteLine($"🔧 Embedded custom font for \"{missingFontName}\"");
    }
}
```

> **Nota:** L'incorporamento dei font può aumentare la dimensione del file di output, quindi valuta il compromesso tra fedeltà e larghezza di banda.

## Problemi comuni e come evitarli

| Sintomo | Probabile causa | Soluzione |
|---------|-----------------|----------|
| Nessun avviso appare anche se il documento sembra errato | `SubstitutionWarningLevel` non impostato su `All` | Assicurati che il passo 2 imposti il flag esattamente come mostrato |
| Gli avvisi elencano lo stesso font più volte | Il documento contiene il font in diversi stili | De‑duplica se ti serve solo un elenco unico: `fontWarnings.Select(w => w.Description).Distinct()` |
| L'applicazione si arresta con file DOCX di grandi dimensioni | Caricamento con impostazioni di memoria predefinite | Usa `LoadOptions.LoadFormat` o trasmetti il file in streaming per ridurre la pressione sulla memoria |

## Esempio completo funzionante (pronto per copia‑incolla)

```csharp
using System;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ---------------------------------------------------------------
            // Configure LoadOptions to capture font warnings
            // ---------------------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSettings.SubstitutionWarningLevel.All;

            // OPTIONAL: add a folder with custom fonts
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCompany\Fonts", false);

            // ---------------------------------------------------------------
            // Load the document
            // ---------------------------------------------------------------
            string docPath = @"YOUR_DIRECTORY\DocumentWithMissingFonts.docx";
            Document doc = new Document(docPath, loadOptions);

            // ---------------------------------------------------------------
            // Retrieve and display missing‑font warnings
            // ---------------------------------------------------------------
            var fontWarnings = doc.WarningInfoCollection
                                  .Where(w => w.WarningType == WarningType.FontSubstitution);

            if (!fontWarnings.Any())
            {
                Console.WriteLine("✅ No missing fonts detected – all good!");
            }
            else
            {
                Console.WriteLine("⚠️ Missing fonts detected:");
                foreach (WarningInfo warning in fontWarnings)
                {
                    Console.WriteLine($"- {warning.Description}");
                }
            }

            // ---------------------------------------------------------------
            // OPTIONAL: automatic handling (fallback or embedding)
            // ---------------------------------------------------------------
            // Example: substitute everything with Arial
            // loadOptions.FontSettings.DefaultFontSubstitution = new FontSettings.FontSubstitution { SubstituteFont = "Arial" };

            Console.WriteLine("\nPress any key to exit...");
            Console.ReadKey();
        }
    }
}
```

Esegui il programma con `dotnet run`. Dovresti vedere l'elenco dei font mancanti stampato sulla console, confermando che hai **catturato gli avvisi di font** con successo.

## Conclusione

Ora disponi di un modello completo, pronto per la produzione, per **catturare gli avvisi di font**, **rilevare i font mancanti**, **gestire i font mancanti** e **elencare i font mancanti** usando Aspose.Words in C#. L'approccio è leggero, richiede solo poche righe di codice e può essere inserito in qualsiasi pipeline esistente—che tu

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}