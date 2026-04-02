---
category: general
date: 2026-04-02
description: Come rilevare i font nei documenti C# utilizzando Aspose.Words. Scopri
  come configurare le impostazioni dei font e gestire efficacemente i font mancanti.
draft: false
keywords:
- how to detect fonts
- configure font settings
- handle missing fonts
- font substitution warning
- Aspose.Words font handling
language: it
og_description: Come rilevare i font nei documenti C# usando Aspose.Words. Questa
  guida ti mostra come configurare le impostazioni dei font e gestire i font mancanti.
og_title: Come rilevare i font in C# – Guida completa
tags:
- C#
- Aspose.Words
- Document Processing
title: Come rilevare i font in C# – Guida completa
url: /it/net/working-with-fonts/how-to-detect-fonts-in-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come rilevare i font in C# – Guida completa

Ti sei mai chiesto **come rilevare i font** mancanti o sostituiti quando carichi un documento Word in .NET? Non sei l'unico: gli sviluppatori si scontrano spesso con il problema di un documento che fa riferimento a un font non installato sul server. La buona notizia è che Aspose.Words ti offre un modo pulito e programmatico per individuare queste lacune.

In questo tutorial percorreremo un esempio pratico che non solo mostra **come rilevare i font**, ma dimostra anche come **configurare le impostazioni dei font** e **gestire i font mancanti** in modo elegante. Alla fine avrai a disposizione uno snippet pronto all'uso che stampa ogni avviso di sostituzione del font, così potrai registrarlo, generare allarmi o sostituire i font secondo necessità.

---

## Cosa ti serve

- **Aspose.Words for .NET** (l'ultima versione è la migliore; il codice qui sotto è destinato a .NET 6+)
- Un ambiente di sviluppo .NET (Visual Studio, Rider o VS Code)
- Un file `.docx` di esempio che faccia riferimento a un font che non hai installato (ideale per i test)

Non sono necessari altri pacchetti NuGet oltre ad Aspose.Words, e la soluzione funziona su Windows, Linux e macOS.

---

## Passo 1: Installa e riferisci Aspose.Words

Per prima cosa, aggiungi la libreria al tuo progetto. Il comando NuGet è semplice:

```bash
dotnet add package Aspose.Words
```

> **Suggerimento:** Se lavori su un server CI, fissa la versione del pacchetto per evitare cambiamenti inattesi.

---

## Passo 2: Configura le impostazioni dei font (e prepara le opzioni di caricamento)

Prima di aprire un documento, puoi indicare ad Aspose.Words dove cercare i font di fallback. Questa è la parte di **configurazione delle impostazioni dei font** che impedisce al motore di sostituire silenziosamente i font che potresti non volere.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 2: Create a FontSettings object and point it to a folder with fallback fonts
var fontSettings = new FontSettings();

// Example: add a custom folder that contains common Windows fonts
fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);

// You can also embed a default font to use when nothing matches
fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

// Wrap the settings into LoadOptions so Aspose.Words uses them when loading
var loadOptions = new LoadOptions { FontSettings = fontSettings };
```

Perché farlo? Se il documento fa riferimento a *Comic Sans* ma il tuo server ha solo *Calibri*, Aspose.Words sostituirà *Calibri* e genererà un avviso. Configurando il percorso di ricerca, riduci le sorprese indesiderate.

---

## Passo 3: Carica il documento con le opzioni preparate

Ora apriamo effettivamente il file. Le `LoadOptions` create nel passo precedente vengono passate direttamente al costruttore `Document`.

```csharp
// Step 3: Load the Word file using the configured FontSettings
var docPath = @"C:\Docs\input.docx";
var document = new Document(docPath, loadOptions);
```

Se il file non viene trovato o è corrotto, viene sollevata un'eccezione—quindi potresti voler avvolgere questo codice in un try/catch in produzione.

---

## Passo 4: Scansiona gli avvisi del documento per le sostituzioni dei font

Aspose.Words raccoglie un elenco di avvisi durante il parsing. Tra questi, `FontSubstitutionWarning` ti indica esattamente quale font è stato sostituito.

```csharp
// Step 4: Iterate over warnings and look for FontSubstitutionWarning instances
foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fontWarning)
    {
        Console.WriteLine(
            $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
    }
}
```

La collezione `Warnings` può contenere anche altri elementi (ad esempio `DocumentStructureWarning`). Filtrare per `FontSubstitutionWarning` garantisce che vengano segnalati solo gli scenari di **gestione dei font mancanti** di nostro interesse.

---

## Passo 5: Metti tutto insieme – Un esempio completo e eseguibile

Di seguito trovi il programma completo. Copialo in una nuova console app e avvialo; vedrai ogni font mancante stampato sulla console.

```csharp
// Full example: Detect font substitutions in a Word document
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare font settings (configure font settings)
        var fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\Windows\Fonts", recursive: true);
        fontSettings.SubstitutionSettings.DefaultFontName = "Arial";

        // 2️⃣ Build load options with those settings
        var loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document (handle missing fonts gracefully)
        var docPath = @"C:\Docs\input.docx";
        Document document;
        try
        {
            document = new Document(docPath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Scan warnings for font substitution events
        bool anySubstitutions = false;
        foreach (WarningInfo warning in document.Warnings)
        {
            if (warning is FontSubstitutionWarning fontWarning)
            {
                anySubstitutions = true;
                Console.WriteLine(
                    $"Font '{fontWarning.FontName}' was substituted with '{fontWarning.SubstitutedFontName}'.");
            }
        }

        // 5️⃣ Inform the user if everything was fine
        if (!anySubstitutions)
        {
            Console.WriteLine("No font substitutions detected – all fonts were found.");
        }
    }
}
```

**Output previsto** (esempio):

```
Font 'Times New Roman' was substituted with 'Arial'.
Font 'Comic Sans MS' was substituted with 'Arial'.
```

Se il documento utilizza solo font presenti sulla macchina, vedrai invece la riga “No font substitutions detected”.

---

## Casi limite e domande frequenti

### E se il documento non contiene **avvisi**?

Significa semplicemente che tutti i font richiesti sono stati trovati nelle cartelle di ricerca configurate. Il flag `anySubstitutions` nell'esempio gestisce anche questo caso.

### Posso **registrare** gli avvisi su un file invece che sulla console?

Assolutamente sì. Sostituisci le chiamate a `Console.WriteLine` con un logger a tua scelta (Serilog, NLog, ecc.). L'oggetto `WarningInfo` espone anche `WarningType` e `WarningMessage` se ti servono più dettagli.

### Come **ignorare** certi font, ad esempio un font aziendale che non deve mai essere sostituito?

Puoi aggiungere una regola di sostituzione personalizzata:

```csharp
fontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("MyBrandFont", new[] { "Arial", "Helvetica" });
```

Ora Aspose.Words sostituirà solo *MyBrandFont* con le alternative elencate, e continuerai a ricevere un avviso su cui poter intervenire.

### Funziona su contenitori **Linux**?

Sì—basta assicurarsi di montare una cartella contenente i file `.ttf`/`.otf` necessari e puntare `SetFontsFolder` a quella directory. Aspose.Words non dipende dai font installati dal sistema operativo.

---

## Panoramica visiva

![how to detect fonts flowchart](detect-fonts.png "Diagram showing the steps to detect fonts in a document")

*Testo alternativo immagine:* **how to detect fonts** flowchart che illustra configurazione, caricamento e ispezione degli avvisi.

---

## Riepilogo – Cosa abbiamo imparato

- **Come rilevare i font** mancanti o sostituiti usando gli avvisi di Aspose.Words.  
- Come **configurare le impostazioni dei font** per puntare a cartelle di font personalizzate e impostare un fallback predefinito.  
- Strategie per **gestire i font mancanti**, dalla registrazione alle regole di sostituzione personalizzate.

Il tutto è racchiuso in una piccola console app autonoma che puoi inserire in qualsiasi soluzione .NET.

---

## Prossimi passi e argomenti correlati

- **Incorporare i font** direttamente nel documento di output per evitare future sostituzioni (`SaveOptions` con `EmbedFullFonts`).  
- **Sostituzione programmatica dei font** – sostituire i font mancanti con un’alternativa specifica prima del salvataggio.  
- **Ottimizzazione delle prestazioni** – memorizzare nella cache `FontSettings` quando si elaborano molti documenti in batch.  

Se ti interessano questi argomenti, cerca *configure font settings* e *handle missing fonts*—ti condurranno a approfondimenti sulla gestione dei font con Aspose.Words.

---

Buon coding! Hai un caso particolare di font? Lascia un commento e ti aiuteremo a risolverlo.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}