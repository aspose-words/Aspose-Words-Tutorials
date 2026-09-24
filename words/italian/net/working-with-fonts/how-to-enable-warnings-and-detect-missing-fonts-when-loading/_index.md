---
category: general
date: 2026-02-21
description: Scopri come abilitare gli avvisi, rilevare i caratteri mancanti e caricare
  in modo sicuro i file docx usando Aspose.Words in C#. Segui la guida passo passo.
draft: false
keywords:
- how to enable warnings
- detect missing fonts
- how to load docx
- font substitution handling
- Aspose.Words warnings
language: it
og_description: Come abilitare gli avvisi, rilevare i caratteri mancanti e caricare
  correttamente i file docx con Aspose.Words. Esempio di codice completo incluso.
og_title: Come abilitare gli avvisi e rilevare i font mancanti durante il caricamento
  di DOCX
tags:
- C#
- Aspose.Words
- Document processing
title: Come abilitare gli avvisi e rilevare i font mancanti durante il caricamento
  dei file DOCX
url: /it/net/working-with-fonts/how-to-enable-warnings-and-detect-missing-fonts-when-loading/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come abilitare gli avvisi e rilevare i caratteri mancanti durante il caricamento di file DOCX

Ti sei mai chiesto **come abilitare gli avvisi** per i caratteri mancanti prima che rovinino silenziosamente il rendering del tuo documento? Non sei solo—la maggior parte degli sviluppatori presume che la libreria faccia semplicemente “la cosa giusta”, solo per scoprire in seguito che un carattere è stato sostituito senza alcun indizio.  

In questo tutorial ti mostreremo esattamente **come abilitare gli avvisi**, come **rilevare i caratteri mancanti**, e il modo corretto **come caricare docx** usando Aspose.Words per .NET. Alla fine avrai un esempio pronto‑all'uso che stampa ogni avviso di sostituzione del carattere sulla console, così non dovrai più indovinare cosa è successo all'interno del file.

## Prerequisiti

- .NET 6.0 o versioni successive (il codice funziona anche su .NET Framework 4.7+)  
- Visual Studio 2022 o qualsiasi IDE C# tu preferisca  
- Il pacchetto NuGet **Aspose.Words** (`Install-Package Aspose.Words`)  
- Un file DOCX che potrebbe contenere caratteri non installati sulla tua macchina (lo chiameremo `input.docx`)

> **Suggerimento:** Se non hai un file di test, apri semplicemente un documento Word che utilizza un carattere aziendale personalizzato e salvalo come `input.docx`. Questo attiverà l'avviso che vogliamo catturare.

## Panoramica della soluzione

1. **Crea** un oggetto `LoadOptions` con `FontSubstitutionWarnings` attivato.  
2. **Carica** il file DOCX usando quelle opzioni.  
3. **Ispeziona** la collezione `WarningCallback` per eventuali voci `FontSubstitution`.  
4. **Reagisci** – potresti registrare, visualizzare o persino sostituire il carattere mancante programmaticamente.

Di seguito scomponiamo ogni passaggio, spieghiamo *perché* è importante e ti forniamo un frammento di codice completo e eseguibile.

---

## Passo 1: Installa Aspose.Words e configura il progetto

Prima di poter **come abilitare gli avvisi**, abbiamo bisogno della libreria che li supporta effettivamente.

```bash
# Using the .NET CLI
dotnet add package Aspose.Words
```

Oppure, nella Console di Gestione Pacchetti di Visual Studio:

```powershell
Install-Package Aspose.Words
```

> **Perché questo passaggio?**  
> Senza il pacchetto, le classi `LoadOptions`, `Document` e l'infrastruttura degli avvisi semplicemente non esistono. Aggiungere il riferimento NuGet garantisce di ottenere l'ultima versione stabile (al momento della stesura, 24.5).

---

## Passo 2: Crea le opzioni di caricamento che abilitano gli avvisi di sostituzione dei caratteri

Il cuore di **come abilitare gli avvisi** si trova nella classe `LoadOptions`. Impostare `FontSubstitutionWarnings` a `true` indica al motore di registrare ogni volta che deve sostituire un carattere mancante.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Step 2: Build the options object
LoadOptions loadOptions = new LoadOptions
{
    // This flag makes the library emit warnings for any font it cannot find.
    FontSubstitutionWarnings = true
};
```

> **Perché abilitare questa opzione?**  
> Per impostazione predefinita Aspose.Words sostituisce silenziosamente i caratteri mancanti con un carattere di fallback (di solito Arial). Questo può causare spostamenti di layout, caratteri invisibili o violazioni del brand. Attivare l'opzione ti offre piena visibilità.

---

## Passo 3: Carica il file DOCX usando le opzioni configurate

Ora che sappiamo **come caricare docx** con gli avvisi attivati, eseguiamo effettivamente il caricamento.

```csharp
// Step 3: Load the document – replace the path with your own file location.
string docPath = @"YOUR_DIRECTORY\input.docx";
Document document = new Document(docPath, loadOptions);
```

> **Cosa succede dietro le quinte?**  
> Durante l'analisi del DOCX, Aspose.Words controlla ogni elemento `<w:rFonts>`. Se il carattere specificato non è installato, registra un avviso `FontSubstitution` e ricorre a un carattere predefinito. Poiché abbiamo abilitato gli avvisi, quelle voci finiscono in `document.WarningCallback.Warnings`.

---

## Passo 4: Recupera e visualizza gli avvisi di sostituzione dei caratteri

La proprietà `WarningCallback` contiene una `WarningInfoCollection`. Scorri la collezione, filtra per `WarningType.FontSubstitution` e stampa i messaggi.

```csharp
// Step 4: Iterate over warnings and print font‑substitution details.
foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"⚠️ Font substituted: {warning.Message}");
    }
}
```

**Output previsto** (esempio):

```
⚠️ Font substituted: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
⚠️ Font substituted: Font 'CorporateLogo' was not found. Substituted with 'Times New Roman'.
```

> **Cosa fare con questi messaggi?**  
> Potresti registrarli su un file, mostrarli in un'interfaccia utente, o persino attivare una routine di fallback personalizzata per i caratteri. L'importante è che ora *rilevi i caratteri mancanti* invece di indovinare in seguito.

---

## Passo 5: (Opzionale) Sostituisci i caratteri mancanti con un fallback specifico

Se disponi di un carattere aziendale che desideri imporre, puoi gestire gli avvisi e sostituirli al volo.

```csharp
// Optional: Custom fallback font
string fallbackFont = "Calibri";

foreach (WarningInfo warning in document.WarningCallback.Warnings)
{
    if (warning.Type == WarningType.FontSubstitution)
    {
        // Extract the missing font name from the warning message
        string missingFont = warning.Message.Split('\'')[1];
        Console.WriteLine($"Replacing missing font '{missingFont}' with '{fallbackFont}'");
        document.FontInfos[missingFont].SubstitutedFont = fallbackFont;
    }
}
```

> **Perché considerare questo?**  
> Garantisce coerenza visiva in tutti i documenti generati, il che è fondamentale per la conformità al brand.

---

## Esempio completo, eseguibile

Di seguito trovi un singolo file C# che puoi copiare‑incollare in un'app console. Copre tutto—dall'installazione del pacchetto alla stampa degli avvisi.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with warnings enabled
            LoadOptions loadOptions = new LoadOptions
            {
                FontSubstitutionWarnings = true
            };

            // 2️⃣ Load the DOCX (adjust the path as needed)
            string docPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Show all font‑substitution warnings
            Console.WriteLine("=== Font Substitution Warnings ===");
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ {warning.Message}");
                }
            }

            // 4️⃣ (Optional) Replace missing fonts with Calibri
            string fallback = "Calibri";
            foreach (WarningInfo warning in doc.WarningCallback.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    string missingFont = warning.Message.Split('\'')[1];
                    Console.WriteLine($"Replacing '{missingFont}' with '{fallback}'");
                    doc.FontInfos[missingFont].SubstitutedFont = fallback;
                }
            }

            // 5️⃣ Save the corrected document (optional)
            string outPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Eseguilo**: `dotnet run` dalla cartella del progetto. Se mancano dei caratteri, vedrai gli avvisi stampati e la sostituzione opzionale verrà applicata prima di salvare il file.

---

## Domande frequenti

### Funziona anche con la conversione PDF?

Sì. Dopo aver gestito gli avvisi, puoi chiamare `doc.Save("output.pdf")` e i caratteri sostituiti appariranno nel PDF come avviene nel DOCX.

### E se devo sopprimere gli avvisi per un carattere specifico?

Puoi filtrarli nel ciclo—basta saltare il `WarningInfo` il cui `Message` contiene il nome del carattere che desideri ignorare.

### `FontSubstitutionWarnings` è disponibile nelle versioni più vecchie di Aspose.Words?

È stata introdotta nella versione 20.5. Se sei bloccato su una versione più vecchia, aggiorna tramite NuGet; la modifica dell'API è retro‑compatibile.

---

## Conclusione

Abbiamo illustrato **come abilitare gli avvisi**, mostrato **come rilevare i caratteri mancanti**, e dimostrato il modo corretto **come caricare docx** con Aspose.Words mantenendo piena visibilità sulle sostituzioni dei caratteri. Ispezionando `document.WarningCallback.Warnings` ottieni una traccia di audit affidabile—niente più fallback silenziosi.

Passi successivi? Prova a collegare la logica degli avvisi a un framework di logging come Serilog, o costruisci un'interfaccia che evidenzi i caratteri mancanti prima di distribuire il documento agli utenti. Potresti anche esplorare la classe `FontSettings` per un controllo più granulare sulle politiche di sostituzione dei caratteri.

Buon coding, e che i tuoi documenti vengano sempre renderizzati esattamente come desideri! 

![Diagramma che illustra il flusso dal caricamento di un file DOCX alla cattura degli avvisi di sostituzione dei caratteri – come abilitare gli avvisi in Aspose.Words](/images/font-warning-flow.png)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}