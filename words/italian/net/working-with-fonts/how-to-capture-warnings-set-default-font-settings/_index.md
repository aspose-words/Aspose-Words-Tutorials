---
category: general
date: 2026-03-19
description: Scopri come catturare gli avvisi in Aspose.Words, impostare le impostazioni
  predefinite dei font e rilevare i font mancanti durante il caricamento di un documento
  Word.
draft: false
keywords:
- how to capture warnings
- set default font settings
- load word document
- detect missing fonts
- Aspose.Words warning callback
- font substitution handling
language: it
og_description: Come catturare gli avvisi in Aspose.Words, impostare le impostazioni
  predefinite dei caratteri e rilevare i caratteri mancanti durante il caricamento
  di un documento Word.
og_title: Come catturare gli avvisi – Imposta le impostazioni predefinite del carattere
tags:
- Aspose.Words
- C#
- Document Processing
title: Come catturare gli avvisi – Impostare le impostazioni predefinite del carattere
url: /it/net/working-with-fonts/how-to-capture-warnings-set-default-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come catturare gli avvisi – Impostare le impostazioni predefinite dei font

**Come catturare gli avvisi** è una necessità comune quando si lavora con Aspose.Words, specialmente se i documenti dipendono da font specifici che potrebbero non essere presenti sulla macchina di destinazione. Hai mai aperto un DOCX e ti sei chiesto perché il layout sembrava sbagliato? La risposta è spesso nascosta in un avviso riguardo a un font mancante.  

In questa guida vedremo **come catturare gli avvisi** mentre **carichi un documento Word**, configuri **impostazioni predefinite dei font**, e infine **rilevi i font mancanti** così da poter reagire programmaticamente. Nessun superfluo—solo un esempio completo, eseguibile, e la motivazione dietro ogni riga.

> *Consiglio esperto:* Catturare gli avvisi in anticipo ti salva dal dover fare debug di misteriosi problemi di layout in seguito.

---

## Di cosa avrai bisogno

- **Aspose.Words for .NET** (ultima versione al 2026).  
- Un ambiente di sviluppo .NET (Visual Studio, Rider o VS Code).  
- Un file DOCX di esempio che faccia riferimento a un font che *non* hai installato (ad esempio *Comic Sans MS* su una macchina Linux).  

Questo è tutto. Non sono necessari pacchetti NuGet aggiuntivi oltre a Aspose.Words.

---

## Passo 1 – Comprendere perché è necessario catturare gli avvisi

Quando Aspose.Words analizza un documento, può incontrare font non disponibili sull'host. Per impostazione predefinita la libreria sostituisce silenziosamente con un font di riserva, il che può modificare interruzioni di riga, spaziature e persino far scomparire del testo.  

Utilizzando **WarningCallback** insieme a un oggetto **FontSettings** ottieni due cose:

1. **Visibilità** – ricevi una voce `WarningInfo` per ogni sostituzione.  
2. **Controllo** – puoi pre‑configurare un font predefinito per ridurre le sorprese visive.

Pensalo come l'installazione di un “cane da guardia” che grida ogni volta che il motore scambia un pezzo sotto il cofano.

---

## Passo 2 – Impostare le impostazioni predefinite dei font

La prima keyword secondaria, **set default font settings**, appare proprio qui. Crei un'istanza `FontSettings` e, facoltativamente, la indirizzi a una cartella che contiene i tuoi font di riserva.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a FontSettings object and point it to a folder with fallback fonts (optional)
var fontSettings = new FontSettings();
// Example: fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);
```

> **Perché?**  
> Se non specifichi un font di riserva, Aspose.Words sceglie il primo font di sistema che corrisponde allo stile, il che può essere drasticamente diverso. Impostando un valore predefinito noto, garantisci un rendering coerente su tutte le macchine.

---

## Passo 3 – Preparare un Warning Callback per catturare gli avvisi

Ora vedremo **come catturare gli avvisi** collegando una `WarningInfoCollection` alle opzioni di caricamento. Questa collezione memorizzerà ogni avviso emesso durante il processo di caricamento.

```csharp
// Step 3: Prepare a list that will collect warning information
var warningInfos = new List<WarningInfo>();

// Create a WarningInfoCollection that forwards warnings to our list
var warningCallback = new WarningInfoCollection(warningInfos);
```

La `WarningInfoCollection` implementa `IWarningCallback`, quindi Aspose.Words inserisce automaticamente ogni avviso in `warningInfos`. Nessun polling necessario.

---

## Passo 4 – Caricare il documento Word con le opzioni configurate

Ecco dove brilla la seconda keyword secondaria, **load word document**. Passiamo sia le `FontSettings` sia il `WarningCallback` tramite un'istanza `LoadOptions`.

```csharp
// Step 4: Build LoadOptions with our font settings and warning callback
var loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = warningCallback
};

// Load the DOCX – this is the moment we actually **load word document**
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Se il documento fa riferimento a un font non installato, il callback degli avvisi catturerà una voce `WarningType.FontSubstitution`.

---

## Passo 5 – Rilevare i font mancanti dagli avvisi raccolti

Infine, rispondiamo alla terza keyword secondaria, **detect missing fonts**, iterando sugli avvisi raccolti.

```csharp
// Step 5: Examine the collected warnings for any font substitution events
foreach (var warning in warningInfos)
{
    if (warning.WarningType == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substitution detected: {warning.Description}");
    }
}
```

Un output tipico appare così:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Quella riga ti indica esattamente quale font è mancante e quale sostituto è stato usato—informazioni che puoi registrare, mostrare all'utente, o persino attivare una routine personalizzata di installazione del font.

---

## Esempio completo eseguibile

Di seguito trovi il programma completo da copiare‑incollare in un'applicazione console. Dimostra **come catturare gli avvisi**, **impostare le impostazioni predefinite dei font**, **caricare un documento Word**, e **rilevare i font mancanti** in un unico flusso.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace CaptureWarningsDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Prepare a list to collect warning information during loading
            var warningInfos = new List<WarningInfo>();

            // 2️⃣ Configure load options – this is where we **set default font settings**
            var fontSettings = new FontSettings();
            // Uncomment and adjust the line below if you have a fallback folder:
            // fontSettings.SetFontsFolder(@"C:\MyFallbackFonts", true);

            var loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new WarningInfoCollection(warningInfos)
            };

            // 3️⃣ **Load word document** with the configured options
            string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
            Document document = new Document(docPath, loadOptions);

            // 4️⃣ **Detect missing fonts** by scanning the collected warnings
            Console.WriteLine("Scanning for font substitution warnings...");
            foreach (var warning in warningInfos)
            {
                if (warning.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Description}");
                }
            }

            // Optional: keep console window open
            Console.WriteLine("Done. Press any key to exit.");
            Console.ReadKey();
        }
    }
}
```

**Risultato atteso:** Quando il DOCX specificato fa riferimento a un font non installato, la console stampa un avviso per ogni sostituzione. Se tutti i font sono presenti, il ciclo non produce alcun output.

---

## Problemi comuni e casi limite

| Situazione | Perché accade | Come gestirlo |
|------------|----------------|---------------|
| **Nessun avviso appare** anche se il layout sembra errato | Il documento potrebbe utilizzare font *incorporati*, che Aspose.Words rende senza sostituzione. | Controlla `Document.HasEmbeddedFonts` e considera l'estrazione dei font incorporati se ti servono su un'altra macchina. |
| **Avvisi multipli per il |  |  |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}