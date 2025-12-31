---
category: general
date: 2025-12-31
description: Cattura gli avvisi di font in Aspose.Words per rilevare i font mancanti
  e elencarli nella tua app .NET. Scopri una soluzione C# passo passo.
draft: false
keywords:
- capture font warnings
- detect missing fonts
- list missing fonts
- Aspose.Words font warnings
- C# document loading
language: it
og_description: Cattura gli avvisi dei font in Aspose.Words per rilevare i font mancanti
  e elencarli. Guida completa in C# con codice e consigli.
og_title: Cattura avvisi di font – Rileva e elenca i font mancanti
tags:
- Aspose.Words
- C#
- .NET
- Font Substitution
title: Cattura avvisi di font – Rileva e elenca i font mancanti
url: /it/net/working-with-fonts/capture-font-warnings-detect-list-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Catturare gli avvisi di font – Rilevare e elencare i font mancanti

Ti è mai capitato di **catturare gli avvisi di font** durante il caricamento di un documento Word ma non sapevi come visualizzare i dettagli dei font mancanti? Non sei il solo. In molti progetti reali, i font mancanti causano problemi di layout e, senza avvisi adeguati, finisci a inseguire bug fantasma.  

In questo tutorial ti mostreremo come **rilevare i font mancanti** e **elencare i font mancanti** usando Aspose.Words per .NET. Alla fine avrai uno snippet C# pronto all'uso che stampa ogni avviso di sostituzione, così potrai registrare, avvisare o persino sostituire i font automaticamente.

---

## Perché è importante catturare gli avvisi di font

Quando Aspose.Words apre un DOCX che fa riferimento a un font non installato sul server, lo sostituisce silenziosamente con un fallback. Il documento sembra a posto, ma la fedeltà visiva è compromessa — pensa a un logo aziendale visualizzato con il tipo di carattere sbagliato.  

Catturare quegli avvisi ti consente di:

* **Mantenere la coerenza del brand** – sai esattamente quali font mancano.
* **Automatizzare la correzione** – sostituire i font mancanti programmaticamente.
* **Audit di conformità** – generare report per revisioni legali o di design.

In breve, **catturare gli avvisi di font** è la prima linea di difesa contro la sostituzione silenziosa dei font.

## Configurare LoadOptions per rilevare i font mancanti

La chiave per visualizzare gli avvisi è la proprietà `LoadOptions.FontSubstitutionWarning`. Per impostazione predefinita è impostata su `None`, il che significa che Aspose.Words ignora i messaggi. Passarla a `All` indica alla libreria di registrare ogni evento di sostituzione.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Configure LoadOptions so every font‑substitution warning is stored
LoadOptions loadOptions = new LoadOptions
{
    // Provide a fresh FontSettings instance – you can also pre‑load custom fonts here
    FontSettings = new FontSettings(),

    // This flag tells Aspose.Words to capture *all* font‑related warnings
    FontSubstitutionWarning = FontSubstitutionWarning.All
};
```

> **Suggerimento professionale:** Se hai già una cartella di font personalizzata, assegnala a `FontSettings.SetFontsFolder("path")` prima di caricare il documento. In questo modo puoi **rilevare i font mancanti** che non sono nella directory di sistema.

## Caricare il documento e elencare i font mancanti

Ora che i `LoadOptions` sono pronti, il passo successivo è caricare il file Word. Il costruttore accetta l'oggetto delle opzioni, e qualsiasi sostituzione verrà registrata nella `WarningInfoCollection` del documento.

```csharp
// Path to the DOCX that may contain unknown fonts
string docPath = @"C:\Docs\UnknownFonts.docx";

// Load the document with the warning‑capture options
Document document = new Document(docPath, loadOptions);
```

Se il file fa riferimento a font non disponibili, ogni font mancante genera una voce `WarningInfo`. Puoi **elencare i font mancanti** iterando su quella collezione.

```csharp
// Iterate through the warnings and output them to the console
foreach (WarningInfo warning in document.WarningInfoCollection)
{
    // The warning.Type will be FontSubstitution, and Description contains details
    Console.WriteLine($"{warning.Type}: {warning.Description}");
}
```

L'output tipico appare così:

```
FontSubstitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
FontSubstitution: Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Ogni riga ti indica esattamente quale font mancava, soddisfacendo il requisito di **elencare i font mancanti**.

## Leggere e interpretare la WarningInfoCollection

La `WarningInfoCollection` può contenere diversi tipi di avviso (ad es., `DocumentStructure`, `ImageLoading`). Per concentrarsi esclusivamente sui problemi di font, filtrare per `WarningType.FontSubstitution`.

```csharp
var fontWarnings = document.WarningInfoCollection
                           .Where(w => w.Type == WarningType.FontSubstitution);

foreach (var fw in fontWarnings)
{
    Console.WriteLine($"Missing font detected: {fw.Description}");
}
```

Perché filtrare? Perché un documento grande può anche generare avvisi su immagini corrotte o funzionalità non supportate. Restringendo la collezione eviti rumore e mantieni pulito l'output di **catturare gli avvisi di font**.

## Esempio completo funzionante – Catturare gli avvisi di font in azione

Di seguito trovi il programma completo e autonomo che puoi inserire in qualsiasi progetto console .NET. Dimostra ogni passaggio, dalla configurazione di `LoadOptions` alla stampa di un elenco ordinato di font mancanti.

```csharp
// ------------------------------------------------------------
// Complete C# example: Capture Font Warnings, Detect & List Missing Fonts
// ------------------------------------------------------------
using System;
using System.Linq;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare LoadOptions to capture all font‑substitution warnings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings(),
            FontSubstitutionWarning = FontSubstitutionWarning.All
        };

        // OPTIONAL: If you have a custom font folder, point Aspose.Words to it
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyFonts", true);

        // 2️⃣ Load the document with the configured options
        string docPath = @"C:\Docs\UnknownFonts.docx";
        Document doc = new Document(docPath, loadOptions);

        // 3️⃣ Filter only font‑substitution warnings
        var fontWarnings = doc.WarningInfoCollection
                               .Where(w => w.Type == WarningType.FontSubstitution);

        // 4️⃣ Output the missing‑font details
        Console.WriteLine("=== Missing Font Report ===");
        foreach (var warning in fontWarnings)
        {
            Console.WriteLine(warning.Description);
        }

        // 5️⃣ If no warnings were found, let the user know
        if (!fontWarnings.Any())
            Console.WriteLine("All referenced fonts are available – no warnings captured.");
    }
}
```

**Output della console previsto**

```
=== Missing Font Report ===
Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Font 'MyCustomFont' was not found. Substituted with 'Times New Roman'.
```

Se il documento non contiene font mancanti vedrai:

```
All referenced fonts are available – no warnings captured.
```

## Casi limite comuni e come gestirli

| Situation | Why It Happens | Recommended Fix |
|-----------|----------------|-----------------|
| **Il documento utilizza un font OpenType incorporato** | Aspose.Words può leggere i font incorporati, ma solo se il file non è corrotto. | Verifica prima il DOCX in Word; reinserisci il font se necessario. |
| **Un gran numero di avvisi** (ad es., più di 200 font mancanti) | Le importazioni massive da sistemi legacy spesso fanno riferimento a un'ampia palette di font. | Elabora gli avvisi in batch: salvali in un database, poi esegui uno script di installazione dei font. |
| **La WarningInfoCollection è vuota** | Il documento ha tutti i font, oppure `FontSubstitutionWarning` è rimasto impostato su `None`. | Ricontrolla la configurazione dei `LoadOptions` e assicurati di caricare il percorso file corretto. |
| **Font personalizzati situati su una condivisione di rete** | La latenza di rete può causare timeout durante la ricerca dei font. | Precarica i font in `FontSettings` usando `SetFontsFolder` e imposta `CacheFontData = true`. |

Questi consigli ti aiutano a **rilevare i font mancanti** in modo affidabile, anche in ambienti complessi.

## Illustrazione immagine

![esempio di cattura avvisi di font](https://example.com/images/capture-font-warnings.png "esempio di cattura avvisi di font")

*Lo screenshot mostra un'esecuzione della console in cui vengono segnalati due font mancanti.*

## Prossimi passi – Oltre la semplice segnalazione

Ora che puoi **catturare gli avvisi di font**, considera l'automazione della correzione:

1. **Sostituzione automatica dei font** – Sostituisci i font mancanti con un fallback approvato dall'azienda modificando `FontSettings.SubstitutionSettings`.
2. **Registrazione su un sistema di monitoraggio** – Invia i messaggi di avviso a Serilog, ELK o Azure Application Insights.
3. **Report per gli utenti** – Genera un riepilogo HTML o PDF per i designer per rivedere quali font devono essere installati.

Tutte queste estensioni si basano sulla stessa fondazione che abbiamo trattato: configurare `LoadOptions`, caricare il documento e leggere `WarningInfoCollection`.

## Conclusione

Hai appena imparato come **catturare gli avvisi di font** in Aspose.Words, **rilevare i font mancanti** e **elencare i font mancanti** con un output pulito e adatto alla console. L'approccio è semplice, richiede solo poche righe di C# e funziona con qualsiasi versione .NET che supporta Aspose.Words 23.x o successive.

Provalo su un DOCX di esempio che fa riferimento a un font che hai disinstallato deliberatamente – vedrai gli avvisi apparire immediatamente. Da lì, potrai decidere se installare i caratteri mancanti, sostituirli programmaticamente o semplicemente registrare il problema per una revisione successiva.

Buon coding, e che i tuoi documenti vengano sempre visualizzati con i font corretti!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}