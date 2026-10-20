---
category: general
date: 2026-02-28
description: Impara a gestire gli avvisi sui font e a rilevare i font mancanti in
  Aspose.Words usando C#. Guida completa passo passo con codice completo.
draft: false
keywords:
- handle font warnings
- detect missing fonts
language: it
og_description: Gestisci gli avvisi sui font in Aspose.Words e rileva i font mancanti
  con un esempio C# pronto all'uso. Segui i passaggi e visualizza il risultato.
og_title: Gestire gli avvisi di font in Aspose.Words – Guida completa
tags:
- Aspose.Words
- C#
- Document Loading
title: Gestire gli avvisi sui font in Aspose.Words – Rilevare i font mancanti
url: /it/net/working-with-fonts/handle-font-warnings-in-aspose-words-detect-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gestire gli avvisi di font in Aspose.Words – Rilevare i font mancanti

Ti è mai capitato di **gestire gli avvisi di font** durante il caricamento di un documento Word e ti sei chiesto perché alcuni testi appaiono strani? Non sei l'unico. I font mancanti generano avvisi di sostituzione che possono corrompere silenziosamente il layout visivo, e se non **rilevi i font mancanti** non saprai mai cosa è andato storto.

In questo tutorial ti mostreremo un modo pratico per **gestire gli avvisi di font** usando `IWarningCallback` di Aspose.Words. Alla fine della guida sarai in grado di individuare ogni evento di sostituzione del font, registrarlo e persino decidere se interrompere il caricamento. Nessuna documentazione esterna, solo un unico esempio pronto per il copia‑incolla.

## Cosa imparerai

- Configura un gestore di avvisi personalizzato che reagisce solo agli avvisi di sostituzione del font.  
- Associa il gestore a `LoadOptions` in modo che ogni caricamento di documento lo utilizzi.  
- Verifica l'output nella console e comprendi il significato di ciascun avviso.  

**Prerequisiti**

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+).  
- Aspose.Words per .NET installato tramite NuGet (`Install-Package Aspose.Words`).  
- Un file Word che fa riferimento a un font non installato sulla tua macchina (ad es., un font aziendale personalizzato).  

Se ti manca qualcuno di questi, procuratelo subito—altrimenti, iniziamo.

## Come gestire gli avvisi di font in Aspose.Words

Di seguito trovi il programma completo e eseguibile. Include tutto, dalle istruzioni `using` al metodo `Main`, così puoi inserirlo in un'app console e premere **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

/// <summary>
/// Custom warning handler that reacts only to font‑substitution warnings.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We’re only interested in font substitution events.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write a clear message to the console – this is how we **detect missing fonts**.
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 1: Create LoadOptions and attach the custom warning callback.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningHandler()
        };

        // Step 2: Load the document. Any missing font will trigger our handler.
        // Replace the path with the actual location of your test document.
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        // Keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

> **Output console previsto** (supponendo che il documento utilizzi un font non installato sulla tua macchina):
> ```
> ⚠️ Font substituted: Font 'MyCustomFont' was substituted with 'Arial'.
> ✅ Document loaded successfully.
> 
> Press any key to exit...
> ```

Se il documento non contiene **font mancanti**, la riga di avviso non appare mai—quindi hai effettivamente **rilevato i font mancanti** solo quando necessario.

### Perché funziona

Aspose.Words genera un `WarningInfo` per ogni problema non critico che incontra durante l'analisi di un file. Implementando `IWarningCallback` ottieni un punto di aggancio in quel flusso. Il flag `WarningType.FontSubstitution` indica esattamente quando la libreria ha dovuto sostituire un font richiesto con un fallback. Questo è il modo più affidabile per **gestire gli avvisi di font** perché viene eseguito *durante* il caricamento, prima ancora di toccare il modello a oggetti del documento.

## Rilevare i font mancanti senza interrompere l'applicazione

A volte potresti voler trattare un font mancante come un errore fatale—forse le linee guida del tuo brand vietano qualsiasi sostituzione. Puoi modificare il gestore per lanciare un'eccezione invece di limitarti a registrare:

```csharp
public void Warning(WarningInfo info)
{
    if (info.WarningType == WarningType.FontSubstitution)
    {
        // Throwing stops the load process; you can catch it higher up.
        throw new InvalidOperationException($"Missing font detected: {info.Description}");
    }
}
```

Ora il blocco `try…catch` attorno a `new Document(...)` catturerà il problema, permettendoti di decidere se interrompere, utilizzare un fallback o chiedere all'utente.

## Bonus: Visualizzare gli avvisi in un'applicazione UI

Se stai creando un'app WinForms o WPF, sostituisci `Console.WriteLine` con una chiamata adatta all'interfaccia utente:

```csharp
MessageBox.Show($"Font substituted: {info.Description}", "Font Warning",
                MessageBoxButtons.OK, MessageBoxIcon.Warning);
```

In questo modo, gli utenti finali vedranno l'avviso immediatamente, e tu continuerai a **gestire gli avvisi di font** in modo coerente su tutte le piattaforme.

## Errori comuni e consigli professionali

- **Problema:** Dimenticare di impostare `WarningCallback`. Il comportamento predefinito è ignorare gli avvisi di font, quindi non li vedrai mai.  
  **Consiglio professionale:** Crea sempre un'istanza di `LoadOptions` anche se ti serve solo il gestore degli avvisi. È poco costoso e esplicito.  

- **Problema:** Usare il separatore di percorso sbagliato su sistemi non Windows.  
  **Consiglio professionale:** Usa `Path.Combine` o una stringa letterale (`@"C:\Docs\MissingFont.docx"` funziona su Windows; su Linux usa `"/home/user/docs/MissingFont.docx"`).  

- **Problema:** Supporre che l'avviso venga generato per i font incorporati.  
  **Consiglio professionale:** I font incorporati sono considerati presenti, quindi non appare alcun avviso di sostituzione. Prova con font davvero *mancanti* per vedere il gestore in azione.  

- **Problema:** Registrare in eccesso tutti i tipi di avviso.  
  **Consiglio professionale:** Filtra per `WarningType.FontSubstitution` come mostrato—così la console rimane pulita e ti concentri sullo scenario di **rilevare i font mancanti**.  

## Riepilogo dell'esempio completo funzionante

Ecco di nuovo l'intero programma, questa volta senza commenti per chi preferisce una visualizzazione pulita:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            Console.WriteLine($"⚠️ Font substituted: {info.Description}");
    }
}

class Program
{
    static void Main()
    {
        var loadOptions = new LoadOptions { WarningCallback = new FontWarningHandler() };
        string docPath = @"C:\Docs\MissingFont.docx";

        try
        {
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("✅ Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"❌ Failed to load document: {ex.Message}");
        }

        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

Copia, incolla, esegui—la tua console ora **gestirà gli avvisi di font** e **rileverà i font mancanti** automaticamente.

## Prossimi passi

- **Registrare su file:** Sostituisci `Console.WriteLine` con un logger (ad es., NLog) per tracciamento di livello produzione.  
- **Elaborazione batch:** Scorri una cartella di documenti, raccogliendo tutti gli eventi di sostituzione del font in un report CSV.  
- **Installazione automatica dei font:** Collega il gestore degli avvisi per scaricare i font mancanti da un repository aziendale prima che il caricamento continui.  

Ciascuna di queste estensioni si basa sull'idea centrale di **gestire gli avvisi di font** in modo pulito e riutilizzabile.

---

*Buon coding! Se incontri qualche strano problema mentre provi a **rilevare i font mancanti**, lascia un commento qui sotto. Sarò felice di aiutarti a risolverlo.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}