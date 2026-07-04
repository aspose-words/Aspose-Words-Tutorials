---
category: general
date: 2026-05-29
description: Scopri come impostare FontSettings in Aspose.Words e gestire i caratteri
  mancanti in modo elegante. Guida passo passo con codice completo e migliori pratiche.
draft: false
keywords:
- how to set fontsettings
- handle missing fonts
language: it
og_description: Come impostare FontSettings in Aspose.Words e gestire rapidamente
  i font mancanti. Segui questa guida per una soluzione completa e eseguibile.
og_title: Come impostare FontSettings – Gestire i caratteri mancanti
schemas:
- author: Aspose
  dateModified: '2026-05-29'
  description: Learn how to set FontSettings in Aspose.Words and handle missing fonts
    gracefully. Step-by-step guide with complete code and best practices.
  headline: How to Set FontSettings – Handle Missing Fonts
  type: TechArticle
tags:
- Aspose.Words
- FontSettings
- C#
- Document Processing
title: Come impostare FontSettings – Gestire i caratteri mancanti
url: /it/net/working-with-fonts/how-to-set-fontsettings-handle-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare FontSettings – Gestire i font mancanti

Ti sei mai chiesto **come impostare FontSettings** quando lavori con Aspose.Words e improvvisamente ti imbatti in un documento che fa riferimento a un font che non hai installato? È un inconveniente comune, soprattutto quando si elaborano file forniti dai clienti su un server che dispone solo di un set minimo di font. La buona notizia? Puoi intercettare queste lacune e **gestire i font mancanti** senza che la tua app vada in crash o produca PDF brutti.

In questo tutorial percorreremo uno scenario reale: caricare un DOCX che richiede “Calibri” mentre il tuo container Linux fornisce solo “DejaVu Sans”. Vedrai esattamente come configurare FontSettings, sottoscrivere gli avvisi di sostituzione e fornire font di fallback in modo che il documento venga renderizzato esattamente come previsto dall’autore. Niente superfluo—solo il codice che puoi inserire nel tuo progetto subito.

## Prerequisiti

- .NET 6.0 o versioni successive (l'API funziona allo stesso modo su .NET Framework 4.7+)
- Aspose.Words per .NET 23.10 o versioni successive (il nome del pacchetto NuGet è `Aspose.Words`)
- Un ambiente di sviluppo C# di base (Visual Studio, Rider o VS Code)

Se li hai, immergiamoci.

## Passo 1: Creare FontSettings e ascoltare gli eventi di sostituzione

Il cuore della soluzione è l'oggetto `FontSettings`. Collegando un gestore al suo evento `FontSubstitutionWarning` otterrai un report in tempo reale ogni volta che Aspose.Words deve sostituire un tipo di carattere mancante.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1 – initialize FontSettings
FontSettings fontSettings = new FontSettings();

// Subscribe to the warning event so we can log substitutions
fontSettings.FontSubstitutionWarning += (sender, e) =>
{
    // e.FontFamilyName – the name requested in the source document
    // e.SubstitutedFontFamilyName – the font actually used by the engine
    Console.WriteLine(
        $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
};
```

**Perché è importante:**  
Quando il motore non riesce a trovare *Calibri*, potrebbe passare silenziosamente a *Arial*. Ascoltando l'avviso, mantieni una traccia di audit trasparente—perfetta per il debugging o per la reportistica di conformità.

> **Consiglio professionale:** Se esegui questo su un server CI, reindirizza l'output a un file di log così potrai rivedere quali font erano mancanti dopo un'esecuzione batch.

## Passo 2: Collegare FontSettings a LoadOptions

`LoadOptions` è il punto di accesso per controllare come viene analizzato un documento. Assegnando il `FontSettings` appena configurato, ogni successivo caricamento di `Document` rispetterà la nostra logica di sostituzione.

```csharp
// Step 2 – wire FontSettings into LoadOptions
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Cosa succede dietro le quinte?**  
Durante il costruttore `Document` Aspose.Words legge l'XML del DOCX, risolve i riferimenti ai font e—se un font non viene trovato—attiva l'avviso che abbiamo impostato in precedenza. Senza questo hook, non sapresti mai che è avvenuta una sostituzione.

## Passo 3: Caricare il documento e (facoltativamente) definire i font di fallback

Ora finalmente carichiamo il file in memoria. Se hai già una cartella di font di fallback (ad esempio, una directory di font OpenType fornita con la tua app), indica a `FontSettings` dove cercare. Questo passaggio è facoltativo ma spesso è il modo più pulito per *gestire i font mancanti*.

```csharp
// Optional: add a folder that contains fallback fonts
fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

// Step 3 – load the document using the prepared LoadOptions
Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);
```

**Avviso caso limite:**  
Se il documento contiene un font personalizzato incorporato come flusso binario, Aspose.Words lo utilizzerà automaticamente—nessuna sostituzione necessaria. L'avviso si attiva solo per i font di sistema *mancanti*.

### Verifica del risultato

Dopo il caricamento, potresti voler salvare il documento in PDF o Word per confermare che tutto sia corretto.

```csharp
// Save as PDF to see the final rendering
doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);
```

Quando esegui il programma, la console stamperà righe simili a:

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
```

Se vedi questi messaggi, hai gestito con successo i **font mancanti** e sai esattamente quali sostituzioni sono avvenute.

## Passo 4: Avanzato – Regole personalizzate di sostituzione dei font (Facoltativo)

A volte è necessario un mapping deterministico, ad esempio, sostituire sempre *Times New Roman* con *Liberation Serif*. Puoi ottenere ciò con `FontSettings.SubstitutionTable`.

```csharp
// Define explicit substitution pairs
fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });
```

**Perché farlo?**  
Regole esplicite ti danno controllo sulla tipografia, garantendo coerenza del brand nei PDF generati, specialmente quando produci materiale di marketing.

## Problemi comuni e come evitarli

| Problema | Sintomo | Soluzione |
|----------|----------|-----------|
| **Nessun avviso di output** | Pensate che i font siano a posto ma il documento appare sbagliato. | Assicurati che `FontSubstitutionWarning` sia collegato **prima** del caricamento del documento. |
| **Cartella di fallback non scansionata** | Le sostituzioni ricadono ancora sui font di sistema predefiniti. | Chiama `SetFontsFolder(path, true)` con il secondo argomento `true` per scorrere le sottocartelle. |
| **Impatto sulle prestazioni con grandi batch** | Il caricamento di 10k documenti diventa lento. | Metti in cache una singola istanza di `FontSettings` e riutilizzala tra i caricamenti; evita di ricrearla ogni volta. |
| **Font incorporati ignorati** | Ti aspettavi che fosse usato un font incorporato personalizzato, ma avviene una sostituzione. | Verifica che il DOCX di origine incorpori effettivamente il font (controlla con Word → File → Info → Fonts). |

## Esempio completo funzionante

Di seguito trovi il programma completo, pronto per il copia‑incolla. Dimostra tutto, dalla gestione degli eventi al salvataggio del PDF finale.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Set up FontSettings with a warning handler
        FontSettings fontSettings = new FontSettings();
        fontSettings.FontSubstitutionWarning += (sender, e) =>
        {
            Console.WriteLine(
                $"Font '{e.FontFamilyName}' substituted with '{e.SubstitutedFontFamilyName}'.");
        };

        // Optional: point to a folder that contains fallback fonts
        fontSettings.SetFontsFolder(@"C:\MyApp\FallbackFonts", true);

        // 2️⃣ Attach FontSettings to LoadOptions
        LoadOptions loadOptions = new LoadOptions { FontSettings = fontSettings };

        // 3️⃣ Load the document that may have missing fonts
        Document doc = new Document(@"C:\Docs\DocWithMissingFonts.docx", loadOptions);

        // 4️⃣ (Optional) Define explicit substitution rules
        fontSettings.SubstitutionTable.AddSubstitutes("Times New Roman", new[] { "Liberation Serif" });
        fontSettings.SubstitutionTable.AddSubstitutes("Calibri", new[] { "DejaVu Sans", "Arial" });

        // 5️⃣ Save the result – PDF is a common target format
        doc.Save(@"C:\Docs\Output.pdf", SaveFormat.Pdf);

        Console.WriteLine("Document processed and saved successfully.");
    }
}
```

**Output console previsto** (esempio):

```
Font 'Calibri' substituted with 'DejaVu Sans'.
Font 'Cambria Math' substituted with 'Arial Unicode MS'.
Document processed and saved successfully.
```

Esegui il programma, apri `Output.pdf` e vedrai il testo renderizzato con i font di fallback—nessun quadrato di glifi mancanti, nessun crash.

## Conclusione

Ora hai a disposizione un modello solido e pronto per la produzione su **come impostare FontSettings** in Aspose.Words e **gestire i font mancanti** in modo elegante. Collegando l'evento `FontSubstitutionWarning`, indicando una directory di font di fallback e (se necessario) definendo regole esplicite di sostituzione, ottieni piena visibilità e controllo sulla tipografia nei flussi di lavoro automatizzati di documenti.

Cosa fare dopo? Prova ad aggiungere una collezione di font personalizzati per tipografie specifiche del brand, o esplora l'API `FontSourceBase` per caricare i font da un database o da un archivio cloud. Gli stessi principi si applicano—basta collegare una fonte diversa a `FontSettings`.

Hai domande su casi limite, come la gestione di script da destra a sinistra o font emoji? Lascia un commento qui sotto, e buona programmazione!

## Cosa dovresti imparare dopo?

- [Come acquisire i font in Aspose.Words – Guida completa](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)
- [Come rilevare i font in Aspose.Words – Gestire avvisi e impostazioni](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Come caricare DOCX e rilevare i font mancanti – Guida completa C#](/words/english/net/working-with-fonts/how-to-load-docx-and-detect-missing-fonts-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}