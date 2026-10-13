---
category: general
date: 2026-03-14
description: Gestisci rapidamente i caratteri mancanti con Aspose.Words. Scopri come
  catturare gli avvisi di sostituzione dei caratteri, configurare LoadOptions e evitare
  problemi di rendering.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: it
og_description: Gestisci i caratteri mancanti in Aspose.Words usando un raccoglitore
  di avvisi. Questo tutorial mostra passo passo come rilevare e registrare le sostituzioni
  dei caratteri.
og_title: Gestire i Font Mancanti in Aspose.Words – Guida Completa C#
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Gestire i font mancanti in Aspose.Words – Guida completa C#
url: /it/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gestire i Font Mancanti in Aspose.Words – Guida Completa C#

Ti è mai capitato di **gestire i font mancanti** durante il caricamento di un documento Word e di chiederti perché il tuo PDF o l'output immagine appaia sbagliato? Non sei il solo. I file dei font mancanti sono un fastidio silenzioso che può trasformare un report perfettamente progettato in un caos incomprensibile.  

La buona notizia? Aspose.Words ti offre un modo semplice per intercettare quegli eventi di sostituzione dei font, registrarli e persino sostituirli con un font di fallback se lo desideri. In questo tutorial percorreremo un esempio completo, pronto all'uso, che mostra esattamente come configurare un raccoglitore di avvisi, collegarlo a `LoadOptions` e caricare un documento che potrebbe contenere font mancanti.

Alla fine di questa guida sarai in grado di:

* Rilevare ogni sostituzione di font che avviene durante il caricamento del documento.  
* Stampare un messaggio console amichevole (o indirizzarlo a un logger) per ogni font mancante.  
* Estendere la soluzione per sostituire i font, se necessario.  

**Prerequisiti** – avrai bisogno di:

* .NET 6.0 o successivo (il codice funziona anche con .NET Core e .NET Framework).  
* Il pacchetto NuGet Aspose.Words per .NET (versione corrente 23.11).  
* Un file Word che fa riferimento intenzionalmente a un font non installato – lo chiameremo `doc-with-missing-font.docx`.  

Se sei già a tuo agio con C# e hai un progetto configurato, puoi passare direttamente al codice. Altrimenti, continua a leggere; copriremo prima i piccoli passaggi di configurazione.

---

## Perché Gestire i Font Mancanti è Importante

Quando Aspose.Words carica un documento, tenta di associare ogni glifo a un font installato sulla macchina. Se non riesce a trovare il font esatto, lo sostituisce silenziosamente con quello più vicino. Questa sostituzione può modificare l'altezza delle linee, il kerning e persino far scomparire dei caratteri. Catturando l'evento `WarningType.FontSubstitution` ottieni una visione trasparente di **cosa** è stato sostituito e **perché**, il che è fondamentale per:

* Mantenere la coerenza del brand (il tuo font aziendale deve apparire esattamente come progettato).  
* Debuggare problemi di conversione PDF—spesso il colpevole è un font mancante.  
* Costruire pipeline di documenti automatizzate dove è necessario segnalare file problematici per una revisione manuale.  

Ora che il “perché” è chiaro, immergiamoci nel **come**.

---

## Passo 1 – Configurare il Raccoglitore di Avvisi

La prima cosa di cui abbiamo bisogno è un oggetto che possa ascoltare gli avvisi di Aspose.Words. `DocumentWarnings` implementa `IWarningCallback`, permettendoci di reagire ogni volta che la libreria genera un avviso.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**Cosa sta succedendo?**  
* `DocumentWarnings` è un leggero wrapper intorno all'interfaccia di callback.  
* La lambda controlla `e.WarningType` così ignoriamo gli avvisi non correlati (come le funzionalità deprecate).  
* `e.WarningInfo` contiene il nome del font mancante, che stampiamo sulla console.  

*Consiglio Pro*: Sostituisci `Console.WriteLine` con un logger strutturato (Serilog, NLog) in produzione—così ottieni timestamp e livelli di log gratuitamente.

---

## Passo 2 – Collegare il Raccoglitore a LoadOptions

`LoadOptions` è il guardiano per ogni documento che apri con Aspose.Words. Assegnando la nostra istanza `fontWarnings` alla proprietà `WarningCallback`, garantiamo che il raccoglitore sia attivo durante il processo di caricamento.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**Perché usare LoadOptions?**  
Oltre agli avvisi, `LoadOptions` ti permette di gestire password, codifiche e persino il caricamento di risorse personalizzate. Qui ci concentriamo sulla parte degli avvisi, ma lo stesso schema funziona per altri callback.

---

## Passo 3 – Caricare il Documento con le Opzioni Configurate

Ora finalmente carichiamo il documento in memoria. Se qualche font è mancante, il nostro raccoglitore si attiverà e vedrai una riga console per ogni sostituzione.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Se esegui questo snippet con un documento che fa riferimento, ad esempio, a *Calibri Light* mentre la tua macchina di test ha solo *Calibri*, otterrai un output simile a:

```
Font 'Calibri Light' was substituted.
```

Questo è l'intero ciclo di rilevamento—semplice, ma potente.

---

## Passo 4 – (Opzionale) Sostituire i Font Mancanti con un Sostituto Conosciuto

A volte non vuoi solo registrare il problema; vuoi imporre un font di fallback in modo che l'output renderizzato sia coerente. Aspose.Words ti permette di fornire un oggetto `FontSettings` personalizzato che mappa i font mancanti a un sostituto.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Spiegazione**  
* Il carattere jolly `"*"` indica ad Aspose.Words di trattare *qualsiasi* font mancante allo stesso modo.  
* Puoi anche mappare font specifici individualmente se hai bisogno di un controllo più fine.  
* Dopo aver impostato `document.FontSettings`, qualsiasi rendering successivo (PDF, immagine, HTML) rispetta la sostituzione.

---

## Esempio Completo Funzionante

Di seguito trovi il programma completo che puoi copiare‑incollare in un'app console. Include tutte le istruzioni `using` necessarie, la gestione degli errori e commenti per chiarezza.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Output previsto** (quando viene rilevato un font mancante):

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Se il documento sorgente contiene già tutti i font richiesti, la riga di avviso semplicemente non apparirà—nulla di cui preoccuparsi.

---

## Domande Frequenti & Casi Limite

| Domanda | Risposta |
|----------|--------|
| **E se voglio solo registrare, non sostituire i font?** | Salta completamente il blocco `FontSettings`; il raccoglitore di avvisi da solo è sufficiente. |
| **Posso reindirizzare gli avvisi a un file?** | Sì—sostituisci `Console.WriteLine` con `File.AppendAllText("font-warnings.log", …)`. |
| **Funziona per DOC, DOCX e ODT?** | Assolutamente. `LoadOptions` si applica a tutti i formati supportati da Aspose.Words. |
| **E i font personalizzati incorporati nel documento?** | I font incorporati aggirano il meccanismo di sostituzione; vengono usati così come sono. |
| **C'è un impatto sulle prestazioni?** | L'overhead è minimo—solo una callback per font mancante. Per grandi batch, considera di aggregare gli avvisi invece di scrivere per ogni evento. |

---

## Conclusione

Abbiamo mostrato **come gestire i font mancanti** in Aspose.Words collegando un raccoglitore `DocumentWarnings` a `LoadOptions`, opzionalmente sostituendo con un font di fallback e salvando il risultato. Questo modello ti offre piena visibilità sugli eventi di sostituzione dei font, aiutandoti a mantenere la fedeltà visiva nelle conversioni PDF, immagine o HTML.

Prossimi passi che potresti esplorare:

* Integrare il raccoglitore di avvisi con un framework di logging centralizzato.  
* Creare una dashboard UI che elenchi i documenti con font mancanti per l'elaborazione batch.  
* Combinare questo approccio con Aspose.PDF per verificare che i PDF generati utilizzino effettivamente il font di fallback.  

Sentiti libero di sperimentare—sostituisci `"Arial"` con `"Tahoma"` o carica un diverso set di documenti. L'idea di base rimane la stessa: cattura l'avviso, agisci di conseguenza e mantieni i tuoi documenti esattamente come previsto.

Buona programmazione! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}