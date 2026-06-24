---
category: general
date: 2026-06-20
description: Abilita gli avvisi di sostituzione dei caratteri in C# usando Aspose.Words.
  Scopri come configurare LoadOptions, catturare gli avvisi e gestire efficientemente
  i caratteri mancanti.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: it
og_description: Abilita gli avvisi di sostituzione dei font in C# con Aspose.Words.
  Questa guida ti mostra come configurare LoadOptions, leggere WarningInfo e visualizzare
  i messaggi dei font mancanti.
og_title: Abilita gli avvisi di sostituzione dei font in C# – Guida completa
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Abilita gli avvisi di sostituzione dei caratteri in C# con Aspose.Words
url: /it/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Abilita gli avvisi di sostituzione dei font in C# con Aspose.Words

Ti sei mai chiesto come **abilitare gli avvisi di sostituzione dei font** quando un documento Word fa riferimento a un font che non è installato sul server? Non sei l'unico. I font mancanti possono corrompere silenziosamente il layout di PDF o immagini generate, e l'unico modo per intercettarli in anticipo è ascoltare gli avvisi emessi da Aspose.Words.

In questo tutorial percorreremo un esempio pratico che ti mostra esattamente come attivare quegli avvisi, estrarli dalla collezione `WarningInfo` e stampare messaggi significativi sulla console. Alla fine saprai come configurare **Aspose.Words LoadOptions**, gestire **avvisi di sostituzione dei font in C#** e mantenere la tua pipeline di elaborazione documenti a prova di errore.

Tratteremo anche alcuni casi limite—cosa succede se sopprimi gli avvisi o se devi registrarli invece di stamparli—e ti forniremo un esempio di codice completo, pronto per il copia‑incolla, che funziona con l'ultima versione di Aspose.Words per .NET (a partire dalla versione 24.10).

## Cosa ti serve

- .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.7+)
- Un riferimento NuGet a `Aspose.Words` (installalo tramite `dotnet add package Aspose.Words`)
- Un file Word che fa riferimento a un font che **non** hai installato (ad es., `DocumentWithMissingFont.docx`)
- Un IDE decente (Visual Studio, Rider o VS Code)

È tutto—nessun servizio aggiuntivo, nessuno strumento proprietario. Pronto? Immergiamoci.

## Passo 1: Abilita gli avvisi di sostituzione dei font

La prima cosa da fare è dire ad Aspose.Words che vuoi essere avvisato quando sostituisce un font mancante. Questo avviene tramite la proprietà `FontSettings` di un oggetto `LoadOptions`. Per impostazione predefinita, gli avvisi sono **disabilitati** per mantenere l'API silenziosa, quindi dobbiamo attivarli noi stessi.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Perché funziona:** Quando `FontSettings` non è `null`, la libreria popola automaticamente `Document.WarningInfo` con tutte le voci `WarningType.FontSubstitution` che incontra durante il caricamento di un documento. Pensalo come l'attivazione di una “modalità debug” per i font.

## Passo 2: Carica il documento con le opzioni configurate

Ora che la collezione di avvisi è attiva, carica il tuo documento usando il `LoadOptions` che abbiamo appena preparato. Se il documento contiene un font mancante, Aspose.Words sostituirà un font di fallback e inserirà un avviso nella lista `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Consiglio professionale:** Se stai elaborando molti file in un ciclo, riutilizza la stessa istanza di `LoadOptions`—creandola una sola volta risparmi qualche millisecondo per iterazione.

## Passo 3: Itera su WarningInfo e visualizza i messaggi di sostituzione dei font

Una volta caricato il documento, la collezione `WarningInfo` contiene tutti gli avvisi generati durante il caricamento. Siamo interessati solo a `WarningType.FontSubstitution`, quindi filtriamo di conseguenza.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Eseguendo lo snippet sopra su un documento che fa riferimento al font mancante “Papyrus” potrebbe produrre un output simile a:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Questi sono i **messaggi di sostituzione dei font** che stavi cercando—chiari, azionabili e pronti per essere registrati o inviati a un sistema di allerta.

## Esempio completo funzionante

Di seguito trovi un programma console autonomo che mette tutto insieme. Copialo e incollalo in un nuovo `.csproj` e premi **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Output previsto

Se il documento fa riferimento a font che non sono installati, vedrai qualcosa di simile a:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Se tutti i font sono presenti sulla macchina, il programma stamperà semplicemente:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Problemi comuni e consigli professionali

| Problema | Perché succede | Come risolvere / evitare |
|----------|----------------|--------------------------|
| **Gli avvisi scompaiono** | Hai cancellato `FontSettings` o usato un `LoadOptions` senza di esso. | Instanzia sempre `FontSettings` anche se non modifichi alcuna proprietà. |
| **Troppi avvisi** | Il documento utilizza molti font esotici. | Considera di aggiungere una cartella di font personalizzata a `FontSettings` tramite `SetFontsFolder` per ridurre le sostituzioni. |
| **Impatto sulle prestazioni in un ciclo stretto** | Ricreare `LoadOptions` ad ogni iterazione aggiunge overhead. | Riutilizza una singola istanza di `LoadOptions` per tutti i documenti. |
| **Output della console mancante** | Esecuzione all'interno di un'app GUI dove `Console.WriteLine` è ignorato. | Reindirizza gli avvisi a un logger (`ILogger`) o scrivili su un file. |

### Gestione degli avvisi in un servizio reale

In una web API probabilmente non vuoi scrivere sulla console. Invece, indirizza gli avvisi verso un log strutturato:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

In questo modo mantieni la **gestione degli avvisi del documento** mantenendo il tuo servizio pulito.

## Estendere l'esempio

- **Cattura altri tipi di avviso** (ad es., `WarningType.UnknownFileFormat`) rimuovendo il filtro `if`.
- **Salva un report** di tutti gli avvisi in JSON per analisi successive.
- **Forza un font di fallback specifico** impostando `FontSettings.SubstitutionSettings.DefaultFontName`.

Tutte queste sono estensioni naturali una volta che hai padroneggiato **l'abilitazione degli avvisi di sostituzione dei font**.

## Conclusione

Ti abbiamo mostrato come **abilitare gli avvisi di sostituzione dei font** in C# usando Aspose.Words, dalla configurazione di `LoadOptions` all'iterazione su `WarningInfo` e alla stampa di messaggi chiari. Seguendo i passaggi sopra potrai proteggere le tue pipeline di elaborazione documenti da modifiche silenziose del layout causate da font mancanti.

Successivamente, prova ad aggiungere una cartella di font personalizzata, registrare gli avvisi su un file, o anche inviarli a una dashboard di monitoraggio. Lo stesso schema funziona per qualsiasi scenario di **gestione degli avvisi del documento**, sia che tu stia convertendo in PDF, rendendo immagini o eseguendo mail‑merge.

Hai domande sugli **avvisi di sostituzione dei font in C#** o vuoi condividere un trucco intelligente? Lascia un commento qui sotto—buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Abilita gli avvisi di sostituzione dei font in Aspose.Words – Guida completa](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Come rilevare i font in Aspose.Words – Gestire avvisi e impostazioni](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Cattura gli avvisi di sostituzione dei font in Java con Aspose.Words – Guida completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}