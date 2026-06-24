---
category: general
date: 2026-05-04
description: Scopri come utilizzare la sostituzione dei caratteri Aspose per rilevare
  i font mancanti quando carichi un documento Word e recuperare i dettagli dei font
  mancanti—guida passo‑passo.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: it
og_description: Padroneggia la sostituzione dei font Aspose per rilevare i font mancanti
  durante il caricamento di un documento Word e recuperare le informazioni sui font
  mancanti con codice C# completo.
og_title: Sostituzione dei Font Aspose – Rileva i Font Mancanti nei Documenti Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Sostituzione dei font Aspose: rileva i font mancanti nei documenti Word'
url: /it/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Rileva i Font Mancanti nei Documenti Word

Ti sei mai chiesto perché un documento Word appare sbagliato su un altro computer? Spesso il colpevole è un font mancante, e **Aspose font substitution** è lo strumento che ti permette di individuare queste lacune prima che diventino un disastro visivo. In questo tutorial vedremo come **rilevare i font mancanti** nel momento in cui **carichi un documento Word**, e poi **recuperare i dettagli dei font mancanti** così da poterli correggere o sostituire.

Copriremo tutto, dalla configurazione del callback di avviso all’estrazione di un elenco pulito dei font mancanti. Alla fine avrai a disposizione uno snippet C# pronto all’uso che ti indica esattamente quali font non sono stati trovati, e comprenderai perché questo è importante per la fedeltà del documento.

---

## Prerequisiti – Cosa Serve Prima di Iniziare

- **Aspose.Words for .NET** (v23.12 o successiva consigliata).  
- Un ambiente di sviluppo .NET (Visual Studio, Rider o la CLI `dotnet`).  
- Un file DOCX di esempio che utilizzi intenzionalmente un font non installato—chiamiamolo `DocumentWithMissingFont.docx`.  
- Conoscenze di base di C#—nulla di complesso, solo la capacità di eseguire un’app console.

Se qualcosa di quanto sopra ti è sconosciuto, fermati e installa il pacchetto NuGet:

```bash
dotnet add package Aspose.Words
```

Tutto qui. Nessun font aggiuntivo, nessun servizio esterno.

---

## Passo 1: Carica il Documento Word (e Attiva i Controlli dei Font)

La prima cosa da fare è **caricare un documento Word**. Aspose.Words analizza il file e, se non riesce a trovare un font di riferimento, genera un avviso *FontSubstitution*. Ecco il codice che esegue il caricamento:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Perché è importante:** Caricare il documento subito dà ad Aspose la possibilità di analizzare ogni run di testo, stile e oggetto incorporato. Se un font non è presente sul sistema o nella cartella dei font personalizzati, otterrai un avviso in seguito.

---

## Passo 2: Collega un Callback di Avviso per Catturare gli Eventi di Sostituzione

Aspose.Words utilizza un meccanismo di callback per informarti di problemi come i font mancanti. Assegnando un’implementazione di `IWarningCallback` a `doc.WarningCallback`, puoi intercettare ogni avviso al momento in cui si verifica.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Consiglio pratico:** Puoi collegare più callback (ad esempio per il logging o per aggiornamenti UI) avvolgendoli in un pattern composito, ma per questo tutorial un singolo callback mantiene le cose chiare.

---

## Passo 3: Implementa il Callback di Avviso per la Sostituzione dei Font

Ora definiamo la classe che esegue effettivamente il lavoro. Il callback riceve un oggetto `WarningInfo`; filtriamo per `WarningType.FontSubstitution` e memorizziamo la descrizione per un uso successivo.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Cosa succede:** Quando Aspose incontra un font mancante, crea un avviso del tipo “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Il nostro callback stampa quella riga e la salva.

---

## Passo 4: Elabora il Documento (Opzionale) e Raccogli i Font Mancanti

Se ti serve solo **rilevare i font mancanti**, il passaggio di caricamento è sufficiente—gli avvisi vengono generati automaticamente. Tuttavia, molti sviluppatori hanno anche bisogno di **recuperare le informazioni sui font mancanti** dopo aver eseguito alcune operazioni (ad esempio salvataggio, conversione). Di seguito forziamo una piccola operazione—salvare in PDF—per assicurarci che tutti gli avvisi vengano emessi, poi estraiamo i messaggi raccolti.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Output console previsto** (esempio):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Nota come ogni riga indica chiaramente il font originale e il fallback scelto da Aspose. Questo è il cuore della segnalazione **aspose font substitution**.

---

## Passo 5: Avanzato – Utilizzare Font Sources Personalizzati per Ridurre le Sostituzioni

A volte *hai* i font mancanti, ma non nella cartella di sistema predefinita. Aspose.Words ti consente di puntare a una directory personalizzata tramite `FontSettings`. Aggiungere questo passaggio può ridurre drasticamente il numero di avvisi di sostituzione.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **Perché aggiungerlo?** Se distribuisci documenti su più macchine, includere i font necessari in una cartella nota garantisce lo stesso aspetto visivo ovunque. Inoltre rende la tua routine di **detect missing fonts** più accurata perché Aspose controlla prima quella cartella prima di ricorrere al fallback.

---

## Esempio Completo Funzionante

Mettendo tutto insieme, ecco un programma console pronto per il copia‑incolla. Salvalo come `Program.cs` ed eseguilo con `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Cosa dovresti vedere:** Se il DOCX di origine fa riferimento a font che non possiedi, la console stampa ogni riga di sostituzione seguita da un riepilogo conciso. Se tutti i font sono presenti, otterrai il messaggio “No missing fonts were detected.”

---

## Problemi Comuni & Come Evitarli

| Problema | Perché accade | Soluzione |
|----------|---------------|-----------|
| **Nessun avviso appare** | Il documento utilizza solo font di sistema, o hai già aggiunto una cartella personalizzata contenente i font mancanti. | Verifica che il DOCX faccia davvero riferimento a un font non disponibile. Puoi aprirlo in Word e cambiare un paragrafo in un font raro (es. “Papyrus”). |
| **Messaggi duplicati** | Lo stesso font è usato in più run, generando più avvisi. | De‑duplica l’elenco con `Distinct()` se ti serve solo un set unico. |
| **Impatto sulle prestazioni su documenti grandi** | Ogni avviso viene elaborato sul thread UI. | Esegui il caricamento in un task in background o usa `Parallel.ForEach` per il post‑processing. |
| **Font di fallback errato** | Il fallback predefinito di Aspose potrebbe non corrispondere al tuo brand. | Imposta `FontSettings.SubstitutionSettings.DefaultFontName` su un fallback preferito (es. “Calibri”). |

---

## Estendere la Soluzione – Esportare i Font Mancanti in JSON

Se stai costruendo un servizio web che deve riportare i font mancanti al client, serializzare l’elenco è banale:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Ora la tua API può restituire un payload JSON pulito che un altro sistema può consumare.

---

## Conclusione

In questa guida abbiamo dimostrato **Aspose font substitution** dall’inizio alla fine: caricamento di un documento Word, collegamento di un callback di avviso, cattura di ogni evento *detect missing fonts* e infine **retrieve missing font** per la segnalazione o la correzione. Aggiungendo cartelle di font personalizzate puoi ridurre l’elenco delle sostituzioni, e con poche righe extra puoi persino esportare i risultati in JSON.

Ricorda, l’integrità visiva dei tuoi documenti dipende dai font che usano. Con la tecnica mostrata qui non sarai più sorpreso da un fallback inatteso.  

Pronto per il passo successivo? Prova a integrare questa logica in una pipeline di elaborazione documenti più ampia, o esplora le altre funzionalità di Aspose.Words come l’incorporamento dei font (`doc.FontSettings.EmbeddedFonts`). Le possibilità sono infinite, e i tuoi utenti ti ringrazieranno per l’output curato.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}