---
category: general
date: 2026-03-25
description: Crea un callback di avviso per caricare il documento Word e rilevare
  i caratteri mancanti. Scopri come configurare le impostazioni dei font in Aspose.Words
  per .NET.
draft: false
keywords:
- create warning callback
- load word document
- detect missing fonts
- configure font settings
language: it
og_description: Crea una callback di avviso per caricare il documento Word rilevando
  i font mancanti. Questa guida mostra come configurare le impostazioni dei font in
  Aspose.Words.
og_title: Crea callback di avviso – Carica documento Word e rileva i font mancanti
tags:
- Aspose.Words
- C#
- Font handling
title: Crea callback di avviso per il caricamento di documenti Word – Guida completa
url: /it/net/working-with-fonts/create-warning-callback-for-loading-word-documents-complete/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea callback di avviso – Carica documento Word e rileva i font mancanti

Ti è mai capitato di dover **creare un callback di avviso** durante il caricamento di un documento Word e di chiederti perché alcuni font scompaiono? Non sei l'unico. In molte applicazioni aziendali, i font mancanti causano disastri di layout e, senza un callback adeguato, potresti non accorgerti nemmeno del problema.  

La buona notizia? Con Aspose.Words per .NET puoi **caricare un documento Word**, **rilevare i font mancanti**, e **configurare le impostazioni dei font** in poche linee di codice ordinate. In questo tutorial passeremo in rassegna un esempio completo e eseguibile, spiegheremo perché ogni parte è importante e ti mostreremo come verificare che il callback di avviso stia facendo il suo lavoro.

> **Cosa otterrai**  
> * Un programma C# completo che carica un DOCX, segnala eventuali sostituzioni di font e ti consente di personalizzare i percorsi di ricerca dei font.  
> * Comprensione delle classi `FontSettings`, `LoadOptions` e `IWarningCallback`.  
> * Suggerimenti per gestire casi limite come font incorporati o cartelle di font a livello di sistema.

---

## Prerequisiti

- .NET 6+ (o .NET Framework 4.7.2+) con un compilatore C#.  
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`).  
- Un file Word di esempio (`input.docx`) che utilizza almeno un font non installato sulla macchina (ad esempio *Calibri Light* su un contenitore Windows minimale).  
- Familiarità di base con le app console C#.

Nessuna libreria aggiuntiva è necessaria; tutto vive all'interno di Aspose.Words.

---

## Passo 1: Crea callback di avviso per rilevare i font mancanti

Il componente **principale** di questo puzzle è una classe che implementa `IWarningCallback`. Aspose.Words invocherà questo callback ogni volta che incontra una situazione che richiede un avviso – la sostituzione dei font è la più comune.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

/// <summary>
/// Handles warning events raised by Aspose.Words during document loading.
/// Specifically looks for FontSubstitution warnings and writes them to the console.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Perché è importante** – Senza un callback dovresti setacciare i log a posteriori. Gestendo gli avvisi in tempo reale puoi decidere se abortire il caricamento, sostituire il font mancante con un fallback, o semplicemente registrare il problema per una revisione successiva.

---

## Passo 2: Configura FontSettings per la gestione personalizzata dei font

Prima di caricare effettivamente il documento, potremmo voler indicare ad Aspose.Words dove cercare i font che non sono presenti sul sistema. È qui che entra in gioco `FontSettings`.

```csharp
// Create a FontSettings instance.
FontSettings fontSettings = new FontSettings();

// Add a custom folder (e.g., a shared network location) where your application stores its fonts.
fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);

// Optional: If you have a specific font to use as a universal fallback, set it here.
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

**Perché è importante** – Indicando ad Aspose.Words una cartella che contiene i font mancanti, spesso eviti del tutto la sostituzione. Quando ciò non è possibile, un valore predefinito sensato (come *Arial*) mantiene il documento leggibile.

---

## Passo 3: Carica documento Word con il callback di avviso configurato

Ora uniamo tutto: creiamo `LoadOptions`, colleghiamo i nostri `FontSettings` e `FontWarningHandler`, e infine carichiamo il documento.

```csharp
// Prepare LoadOptions with both FontSettings and our warning handler.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontWarningHandler()
};

// Load the Word document. Replace the path with your actual file location.
Document document = new Document(@"C:\Docs\input.docx", loadOptions);

// At this point the warning handler has already printed any font‑substitution messages.
Console.WriteLine("✅ Document loaded successfully.");
```

**Perché è importante** – `LoadOptions` è l'unico punto in cui configuri *come* viene letto un documento. Fornendo sia la configurazione dei font sia il callback di avviso, garantiamo che qualsiasi font mancante sia cercato nei posti giusti **e** segnalato immediatamente.

---

## Passo 4: Verifica l'output – cosa dovresti vedere?

Esegui il programma da una console. Se `input.docx` utilizza un font che non è installato e non si trova nemmeno in `C:\SharedFonts`, vedrai qualcosa del genere:

```
⚠️ Font substitution detected: Font 'Roboto' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
```

Se tutti i font sono disponibili, la riga di avviso semplicemente non appare mai. Questo ciclo di feedback immediato è inestimabile durante le pipeline di elaborazione automatica dei documenti, dove le sostituzioni silenziose dei font potrebbero violare le linee guida del brand.

---

## Passo 5: Trappole comuni e consigli di best‑practice

| Problema | Come evitarlo |
|----------|---------------|
| **Dimenticato di fare riferimento a `Aspose.Words.Fonts`** | Assicurati di avere `using Aspose.Words.Fonts;` in cima; altrimenti il compilatore segnalerà tipi mancanti. |
| **Il percorso della cartella dei font è errato** | Controlla attentamente il percorso e imposta `recursive: true` se hai sottocartelle. Usa `Path.GetFullPath` per il debug. |
| **Callback di avviso multipli** | Aspose.Words rispetta solo l'ultimo `WarningCallback` assegnato. Mantieni un unico handler che delega se hai bisogno di una logica più complessa. |
| **Esecuzione su un server senza UI** | Le scritture su console vanno bene, ma per le app web potresti voler registrare su un file o su un sistema di monitoraggio invece di `Console.WriteLine`. |
| **Documenti grandi causano rallentamenti** | Riutilizza una singola istanza di `FontSettings` per più caricamenti; crearla ripetutamente può essere costoso. |

**Suggerimento professionale:** Se devi *raccogliere* gli avvisi per un'analisi successiva, memorizzali in una `List<string>` all'interno dell'handler invece di stamparli direttamente.

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Puoi quindi ispezionare `handler.Messages` dopo il caricamento del documento.

---

## Passo 6: Estendere la soluzione – e se devo incorporare un font di fallback?

A volte vuoi che il font mancante sia *incorporato* nel PDF di output così che i visualizzatori a valle vedano l'aspetto esatto. Dopo aver caricato il documento, puoi forzare l'incorporamento:

```csharp
// Ensure the fallback font is embedded when saving to PDF.
PdfSaveOptions pdfOptions = new PdfSaveOptions
{
    EmbedStandardPdfFonts = false,
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};

document.Save(@"C:\Docs\output.pdf", pdfOptions);
Console.WriteLine("✅ PDF saved with embedded fonts.");
```

Questo snippet mostra come lo stesso **configure font settings** approach può essere esteso oltre il semplice caricamento.

---

## Esempio completo eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in un nuovo progetto Console App. Include tutti i componenti discussi sopra.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    // Step 1 – Warning handler
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 2 – Configure FontSettings
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\SharedFonts", recursive: true);
            fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";

            // Step 3 – LoadOptions with warning callback
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontWarningHandler()
            };

            // Step 4 – Load the document
            string docPath = @"C:\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");

            // Optional: Save as PDF with embedded fonts
            var pdfOptions = new PdfSaveOptions
            {
                EmbedStandardPdfFonts = false,
                FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
            };
            doc.Save(@"C:\Docs\output.pdf", pdfOptions);
            Console.WriteLine("✅ PDF saved with embedded fonts.");
        }
    }
}
```

**Output previsto** (quando è presente un font mancante):

```
⚠️ Font substitution: Font 'Times New Roman' was not found. Substituted with 'Arial'.
✅ Document loaded successfully.
✅ PDF saved with embedded fonts.
```

Se non avviene alcuna sostituzione, compaiono solo i messaggi di successo.

---

## Conclusione

Abbiamo appena **creato un callback di avviso** che rileva in modo affidabile i **font mancanti** durante il **caricamento di un documento Word** con Aspose.Words, e abbiamo mostrato come **configurare le impostazioni dei font** per controllare dove la libreria cerca i font e quale fallback utilizzare. Collegando `FontSettings` e `LoadOptions`, ottieni piena visibilità sui problemi legati ai font—niente più glitch di layout silenziosi.

Prossimi passi? Prova a sostituire `FontWarningHandler` con un logger che scrive su un database, o sperimenta con **regole di sostituzione dei font** per mappare font mancanti specifici a alternative approvate dal brand. Potresti anche esplorare **il caricamento dinamico dei font** da storage cloud se la tua app gira in un ambiente containerizzato.

Hai domande su un caso limite particolare—come gestire le funzionalità OpenType o i file DOCX criptati? Lascia un commento qui sotto, e buona programmazione!  

---

![Create warning callback diagram](https://example.com/images/create-warning-callback.png "Create warning callback diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}