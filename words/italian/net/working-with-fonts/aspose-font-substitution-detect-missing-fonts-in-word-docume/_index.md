---
category: general
date: 2026-04-05
description: Guida alla sostituzione dei font Aspose per rilevare i font mancanti
  durante il caricamento di un documento Word. Scopri come configurare le impostazioni
  dei font e gestire efficacemente i font mancanti.
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- configure font settings
- handle missing fonts
language: it
og_description: Guida alla sostituzione dei font di Aspose per rilevare i font mancanti
  durante il caricamento di un documento Word. Scopri come configurare le impostazioni
  dei font e gestire i font mancanti in modo efficiente.
og_title: Sostituzione dei Font Aspose – Rileva i Font Mancanti nei Documenti Word
tags:
- Aspose.Words
- C#
- Font Management
title: Sostituzione dei Font Aspose – Rileva i Font Mancanti nei Documenti Word
url: /it/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docume/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sostituzione dei Font Aspose – Rilevare i Font Mancanti nei Documenti Word

Ti è mai capitato di avere un file Word che appare perfetto su un computer ma mostra strani cambiamenti di font su un altro? Questo è il classico **aspose font substitution** problem, e di solito significa che alcuni font mancano sul sistema di destinazione. In questo tutorial ti mostreremo, passo dopo passo, come **detect missing fonts** quando **load a Word document**, come **configure font settings**, e cosa fare per **handle missing fonts** in modo elegante.

Ti guideremo attraverso un esempio completo e eseguibile in C#, spiegheremo perché ogni riga è importante e ti mostreremo anche l'output della console che dovresti vedere. Alla fine sarai in grado di individuare le sostituzioni di font nel momento in cui un documento viene caricato—senza congetture.

## Cosa Imparerai

- Come abilitare il diagnostic collector di Aspose.Words per gli avvisi sui font.  
- Il codice esatto necessario per **load a Word document** con **font settings** personalizzate.  
- Come iterare sugli oggetti `WarningInfo` per elencare ogni font sostituito.  
- Suggerimenti per sopprimere gli avvisi indesiderati o fornire font di fallback.  
- Un esempio pronto all'uso che puoi copiare‑incollare in Visual Studio.

### Prerequisiti

- .NET 6.0 o successivo (l'API funziona allo stesso modo su .NET Framework).  
- Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`).  
- Un file Word che faccia riferimento a un font che non hai installato (ad es., `MissingFont.docx`).  

Se hai tutto questo, immergiamoci.

## Passo 1 – Abilitare il Diagnostic Collector (Configurare le Impostazioni dei Font)

Prima di tutto: Aspose.Words registra gli avvisi di sostituzione dei font solo se glielo chiedi. Questo si fa creando un oggetto `FontSettings` e assegnandolo a un'istanza di `LoadOptions`. Pensalo come accendere le “lucette di debug” per la gestione dei font.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Prepare load options with a fresh FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    // The FontSettings object is the hub for all font‑related configuration.
    FontSettings = new FontSettings()
};
```

**Perché?**  
Senza un oggetto `FontSettings` il collector degli avvisi rimane silenzioso, e non saprai mai quali font sono stati sostituiti. Inizializzandolo vuoto lasciamo che Aspose usi i font di sistema predefiniti *e* tenga traccia di eventuali sostituzioni.

> **Pro tip:** Se sai che una cartella specifica contiene i font aziendali, punta `FontSettings` lì con `SetFontsFolder("path")`. Questo può ridurre il numero di avvisi di font mancanti.

## Passo 2 – Caricare il Documento con le Opzioni Configurate (Caricare Documento Word)

Ora che il collector è attivo, carica il tuo file `.docx` usando le stesse `LoadOptions`. Questo è il momento in cui Aspose analizza il documento, cerca ogni riferimento a un font e decide se è necessaria una sostituzione.

```csharp
// Step 2: Load the Word file while applying the previously defined load options.
Document document = new Document(@"C:\Docs\MissingFont.docx", loadOptions);
```

**Perché è importante?**  
Se ti limitassi a chiamare `new Document("MissingFont.docx")`, verrebbero applicate le impostazioni predefinite *e* la lista degli avvisi rimarrebbe vuota. Passare `loadOptions` garantisce che il diagnostic collector sia collegato al processo di caricamento.

## Passo 3 – Recuperare e Visualizzare gli Avvisi di Sostituzione dei Font (Rilevare i Font Mancanti)

Dopo che il documento è in memoria, Aspose conserva gli avvisi in `document.WarningCallback.Warnings`. Scorri quella collezione, filtra per `WarningType.FontSubstitution` e stampa la descrizione. Ogni descrizione ti indica quale font era mancante e quale è stato usato al suo posto.

```csharp
// Step 3: Examine the warning list for any font substitution entries.
foreach (WarningInfo warningInfo in document.WarningCallback.Warnings)
{
    if (warningInfo.Type == WarningType.FontSubstitution)
    {
        // The Description contains a human‑readable message, e.g.,
        // "Font 'Comic Sans MS' was not found. Substituted with 'Arial'."
        Console.WriteLine($"Substituted font: {warningInfo.Description}");
    }
}
```

**Output console previsto**

```
Substituted font: Font 'MyCustomFont' was not found. Substituted with 'Arial'.
Substituted font: Font 'Times New Roman' was not found. Substituted with 'Calibri'.
```

Quell'output ti indica esattamente quali font mancano sulla macchina che esegue il codice. Ora puoi decidere se installare i font mancanti, incorporarli nel documento, o mantenere la sostituzione.

![Output della console che mostra gli avvisi di sostituzione dei font Aspose](/images/aspose-font-substitution-console.png)

*Testo alternativo dell'immagine:* sostituzione dei font Aspose – output della console che elenca i font sostituiti

## Passo 4 – Opzionale: Personalizzare il Comportamento di Sostituzione (Gestire i Font Mancanti)

A volte non ti basta sapere *che* è avvenuta una sostituzione—vuoi controllare *come* avviene. Aspose.Words ti permette di registrare una regola personalizzata `IFontSubstitutionRule`. Di seguito un esempio rapido che forza qualsiasi font mancante a ricadere su `Tahoma`.

```csharp
// Optional Step 4 – Define a custom substitution rule.
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        // Always return Tahoma regardless of the missing font.
        return new FontInfo("Tahoma");
    }
}

// Apply the rule to the FontSettings we created earlier.
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(new TahomaFallbackRule());
```

**Quando useresti questo?**  
Se generi PDF per un servizio web e sai che tutti i client possono renderizzare `Tahoma`, forzare il fallback garantisce coerenza visiva senza dover distribuire decine di file di font.

## Esempio Completo Funzionante (Tutti i Passi Combinati)

Ecco l'intero programma che puoi incollare in un nuovo progetto console. Compila così com'è, a patto che tu abbia installato il pacchetto NuGet Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1 – Enable diagnostic collector (configure font settings)
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // Optional: Force all missing fonts to Tahoma
        // -------------------------------------------------
        loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRules.Add(
            new TahomaFallbackRule());

        // -------------------------------------------------
        // Step 2 – Load the document (load word document)
        // -------------------------------------------------
        Document doc = new Document(@"C:\Docs\MissingFont.docx", loadOptions);

        // -------------------------------------------------
        // Step 3 – List any font substitutions (detect missing fonts)
        // -------------------------------------------------
        foreach (WarningInfo warning in doc.WarningCallback.Warnings)
        {
            if (warning.Type == WarningType.FontSubstitution)
                Console.WriteLine($"Substituted font: {warning.Description}");
        }
    }
}

// -------------------------------------------------
// Optional custom rule class (handle missing fonts)
// -------------------------------------------------
class TahomaFallbackRule : IFontSubstitutionRule
{
    public FontInfo Substitute(FontInfo fontInfo, FontSubstitutionInfo substitutionInfo)
    {
        return new FontInfo("Tahoma");
    }
}
```

Esegui il programma, osserva la console, e vedrai stampato ogni evento di font mancante. Da lì potrai decidere se installare i font mancanti, incorporarli, o mantenere il fallback.

## Domande Frequenti

**Q: Questo funziona con la conversione PDF?**  
Sì. Quando successivamente chiami `doc.Save("output.pdf")`, i font che sono stati sostituiti durante il caricamento saranno quelli incorporati nel PDF. Quindi intercettare gli avvisi in anticipo ti aiuta a evitare sorprese di cambiamenti di font nel PDF finale.

**Q: E se devo elaborare molti documenti?**  
Avvolgi la logica di caricamento in un blocco try‑catch e riutilizza una singola istanza di `FontSettings` per tutti i documenti. Questo riduce l'overhead e mantiene attivo il collector degli avvisi per ogni file.

**Q: Posso sopprimere completamente gli avvisi?**  
Puoi impostare `loadOptions.WarningCallback = null;` prima del caricamento, ma perderai la possibilità di **detect missing fonts**—cosa che di solito non è desiderata.

## Conclusione

Abbiamo coperto tutto ciò che ti serve per padroneggiare **aspose font substitution**: abilitare il diagnostic collector, caricare un file Word con **font settings** personalizzate, estrarre l'elenco dei font mancanti e persino sovrascrivere la regola di sostituzione predefinita per **handle missing fonts** a modo tuo. Con poche righe di C# ottieni piena visibilità sui problemi di font che altrimenti si nasconderebbero dietro sottili cambiamenti di layout.

Passi successivi? Prova a incorporare i font originali nel documento con `FontSettings.SetFontsFolder` o esplora `FontSourceBase` per caricare i font da un database. Potresti anche sperimentare con la collezione `Document.BuiltInStyle` per vedere come le modifiche a livello di stile propagano i cambiamenti di font.

Hai altre domande su Aspose.Words o sulla gestione dei font? Lascia un commento, consulta la documentazione ufficiale di Aspose, o avvia un nuovo progetto e gioca con il codice sopra. Buona programmazione, e che i tuoi documenti vengano sempre renderizzati esattamente come previsto!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}