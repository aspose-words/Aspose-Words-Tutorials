---
category: general
date: 2026-04-04
description: Scopri come catturare gli avvisi, rilevare i caratteri mancanti e registrare
  gli eventi di sostituzione utilizzando Aspose.Words LoadOptions in C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: it
og_description: Come catturare gli avvisi, rilevare i caratteri mancanti e registrare
  gli eventi di sostituzione utilizzando Aspose.Words LoadOptions in C#.
og_title: Come catturare gli avvisi in C# – Rilevare i font mancanti e registrare
  le sostituzioni
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Come catturare gli avvisi in C# – Rilevare i font mancanti e registrare le
  sostituzioni
url: /it/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come catturare gli avvisi in C# – Rilevare i font mancanti e registrare le sostituzioni

Ti sei mai chiesto **come catturare gli avvisi** che compaiono quando carichi un documento Word con font mancanti? Non sei l’unico. In molti progetti reali i font vanno persi durante la migrazione e il fallback silenzioso può rompere il layout. La buona notizia? Aspose.Words ti offre un modo pulito per ascoltare quegli avvisi, rilevare i font mancanti e persino registrare ogni sostituzione così da poter correggere la fonte in seguito.

In questo tutorial percorreremo una soluzione completa, pronta all’uso, che mostra **come catturare gli avvisi**, dimostra **come rilevare i font mancanti** e spiega **come registrare gli eventi di sostituzione**. Alla fine avrai un gestore di avvisi riutilizzabile, un oggetto `LoadOptions` completamente configurato e un esempio di output console che potrai verificare.

> **Prerequisito:** È necessario Aspose.Words per .NET (v24.x o successiva) installato tramite NuGet e un ambiente di sviluppo C# di base (Visual Studio 2022 o VS Code vanno bene).

---

## Come catturare gli avvisi durante il caricamento dei documenti

Il cuore della soluzione è una classe che implementa `IWarningCallback`. Aspose.Words chiama automaticamente questo callback per ogni avviso generato durante il caricamento del documento, inclusi gli avvisi di sostituzione dei font.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Perché questo passaggio?**  
> Filtrando su `WarningType.FontSubstitution` evitiamo il disordine causato da avvisi non correlati (come funzionalità deprecate). Questo rende il log focalizzato sul problema esatto che ti interessa—i font mancanti.

---

## Rilevare i font mancanti con Aspose.Words

Quando un documento fa riferimento a un font che non è installato sulla macchina, Aspose.Words sostituisce il più vicino disponibile e genera un avviso. Il nostro gestore sopra intercetterà ogni occorrenza, **rilevando così i font mancanti**.

Per vederlo in azione, dobbiamo configurare `LoadOptions` e collegare il gestore:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Suggerimento:** Se preferisci raccogliere gli avvisi per un'elaborazione successiva (ad esempio scriverli su un file), sostituisci `Console.WriteLine` con del codice che aggiunga il messaggio a una `List<string>`.

---

## Come registrare gli eventi di sostituzione

Registrare è semplice come indirizzare l’output dell’avviso verso una destinazione persistente. Di seguito un rapido esempio che scrive ogni avviso di sostituzione in un file di testo chiamato `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Perché registrare su file?**  
> I log persistenti ti consentono di verificare i problemi di font attraverso più esecuzioni, automatizzare avvisi o alimentare i dati in un controllo della pipeline di build.

---

## Esempio completo funzionante

Mettendo tutto insieme, ecco un’applicazione console autonoma che puoi copiare, incollare e far girare. Dimostra **come catturare gli avvisi**, **rilevare i font mancanti** e **come registrare le sostituzioni** in un unico passaggio.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Output console previsto

Se `input.docx` fa riferimento a un font non installato, vedrai qualcosa di simile:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Se hai sostituito il gestore con `FileLoggingWarningHandler`, le stesse righe appariranno dentro `font-warnings.log` con i timestamp.

![come catturare gli avvisi output console](image-placeholder.png)

---

## Domande frequenti e casi particolari

### E se avessi bisogno di catturare *tutti* gli avvisi, non solo le sostituzioni dei font?

Rimuovi semplicemente il controllo `if (info.Type == WarningType.FontSubstitution)`. Il callback riceverà ogni tipo di avviso (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, ecc.). Potrai quindi gestire ciascun caso in base a `info.Type`.

### Funziona con i PDF o solo con i documenti Word?

`LoadOptions` e `IWarningCallback` fanno parte di Aspose.Words, quindi si applicano ai formati compatibili con Word (`.docx`, `.doc`, `.rtf`, `.html`). Per i PDF dovresti usare i meccanismi di avviso propri di Aspose.PDF.

### Come posso sopprimere gli avvisi invece di registrarli?

Imposta `LoadOptions.WarningCallback = null` oppure implementa il callback ma lascia il corpo del metodo vuoto. La libreria effettuerà comunque la sostituzione in modo silenzioso.

### E per quanto riguarda la sicurezza dei thread?

L’istanza del callback viene invocata sullo stesso thread che carica il documento, quindi non è necessaria alcuna sincronizzazione aggiuntiva a meno che non condivida il gestore tra caricamenti paralleli. In tal caso, proteggi le risorse condivise (ad esempio il file di log) con un lock o utilizza collezioni concorrenti.

---

## Conclusione

Abbiamo coperto **come catturare gli avvisi** da Aspose.Words, mostrato come **rilevare i font mancanti** e spiegato **come registrare le sostituzioni** per analisi successive. Inserendo una semplice implementazione di `IWarningCallback` in `LoadOptions`, ottieni piena visibilità sui problemi legati ai font senza ingombrare il tuo codice.

Prossimi passi? Prova a estendere il logger per inviare email, integrarlo con Azure Monitor o installare automaticamente i font mancanti su un server di build. Potresti anche esplorare altri tipi di avviso—`WarningType.DegradedDocument` può avvisarti di funzionalità che non sono sopravvissute al processo di conversione.

Hai altre domande sulla gestione dei font o su Aspose.Words in generale? Lascia un commento o apri una nuova issue sui forum di Aspose. Buona programmazione, e che i tuoi documenti vengano sempre visualizzati con il carattere corretto!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}