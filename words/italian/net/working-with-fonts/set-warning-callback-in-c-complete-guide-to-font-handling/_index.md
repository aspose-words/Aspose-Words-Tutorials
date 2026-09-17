---
category: general
date: 2026-02-10
description: Imposta il callback di avviso per monitorare le modifiche dei font mentre
  configuri il font predefinito e imposti il font di importazione predefinito in Aspose.Words.
  Scopri la soluzione completa passo‑passo.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: it
og_description: Imposta la callback di avviso per monitorare le modifiche dei font
  durante la configurazione del font predefinito e l'impostazione del font di importazione
  predefinito. Segui il tutorial completo per Aspose.Words.
og_title: Imposta callback di avviso in C# – Guida completa
tags:
- Aspose.Words
- C#
- Document Import
title: Imposta callback di avviso in C# – Guida completa alla gestione dei font
url: /it/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta callback di avviso in C# – Guida completa alla gestione dei font

Ti è mai capitato di dover **impostare un callback di avviso** durante il caricamento di un documento Word e di chiederti come *configurare il font predefinito* allo stesso tempo? Non sei l'unico. In molti progetti reali—come generatori di report automatici o pipeline di conversione documenti—i font mancanti possono rompere silenziosamente il layout, e l'unico modo per intercettare questi problemi è **monitorare le modifiche dei font** tramite un callback di avviso.

In questo tutorial percorreremo un esempio pratico che ti mostra come **impostare il callback di avviso**, **configurare il font predefinito**, e persino **impostare il font di importazione predefinito** usando Aspose.Words per .NET. Alla fine avrai uno snippet pronto all'uso, comprenderai perché ogni parte è importante e saprai come adattarlo a casi limite come cartelle di font personalizzate o sostituzioni silenziose.

---

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.6+)  
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`)  
- Una cartella che contiene il font di fallback che desideri utilizzare (ad es., `fonts/Arial.ttf`)  
- Familiarità di base con le app console C#  

Non sono richieste librerie aggiuntive.

---

## Passo 1: Crea LoadOptions e **configura il font predefinito**

La prima cosa da fare quando vuoi controllare la gestione dei font è creare un'istanza di `LoadOptions`. Questo oggetto indica ad Aspose.Words come gestire i font mancanti durante l'importazione.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Perché è importante:**  
Se il documento di origine fa riferimento a un font che non è installato sul server, Aspose.Words cercherà nella cartella fornita. Questo è il fulcro di **set default import font**—stai indicando esplicitamente alla libreria dove trovare una sostituzione prima che vengano sollevati avvisi.

---

## Passo 2: **Imposta callback di avviso** per **monitorare le modifiche dei font**

Aspose.Words genera una `WarningInfoCollection` ogni volta che deve sostituire un font, tra le altre cose. Collegando un gestore, puoi registrare o reagire a ogni sostituzione.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Perché è importante:**  
Semplicemente **configure default font** non è sufficiente se devi verificare quali font sono stati effettivamente sostituiti. Il callback ti fornisce un registro in tempo reale, soddisfacendo il requisito di **monitor font changes** e aiutandoti a intercettare fallback inaspettati precocemente in una pipeline CI.

---

## Passo 3: Carica il documento con le opzioni preparate

Ora che le opzioni di caricamento sono completamente preparate, puoi caricare in sicurezza qualsiasi file `.docx`. Il callback si attiva automaticamente se avviene una sostituzione.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Cosa vedrai:**  
Se l'origine utilizza un font che non è presente, la console stamperà qualcosa del genere:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Quell'output conferma che hai impostato correttamente **set warning callback** e che il **default import font** ha avuto effetto.

---

## Passo 4: (Opzionale) Affina il comportamento di sostituzione dei font

A volte potresti voler sostituire *tutti* i font mancanti con una singola famiglia, indipendentemente dalla richiesta originale. Aspose.Words ti permette di impostare un *fallback font* a livello globale.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Quando usarlo:**  
Se generi PDF per un brand che consente solo un insieme limitato di font, questo garantisce coerenza in tutti i documenti, anche se l'origine tenta di utilizzare qualcosa di esotico.

---

## Passo 5: Salva o elabora ulteriormente il documento

Dopo il caricamento, puoi continuare con qualsiasi elaborazione necessaria—modifica, conversione in PDF, estrazione di testo, ecc. Ecco un rapido esempio di salvataggio del documento come PDF mantenendo i font sostituiti.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

Il PDF risultante mostrerà il fallback font ovunque sia avvenuta una sostituzione, fornendoti una conferma visiva che il **set warning callback** ha funzionato come previsto.

---

## Problemi comuni & consigli esperti

| Problema | Perché succede | Soluzione |
|----------|----------------|-----------|
| **Il callback non si attiva mai** | `LoadOptions.WarningCallback` non è stato assegnato *prima* del caricamento del documento. | Allega sempre il callback **prima** di chiamare `new Document(...)`. |
| **Cartella dei font errata** | Errore di battitura nel percorso o permessi di lettura mancanti. | Verifica che la cartella esista e che l'app abbia accesso `Read`. Usa percorsi assoluti per affidabilità. |
| **Sostituzioni multiple, output rumoroso** | Documenti grandi con molti font mancanti. | Filtra gli avvisi per `WarningType.FontSubstitution` (come mostrato) o scrivili in un file di log invece della console. |
| **Il fallback font non è stato applicato** | Il fallback font non è installato sulla macchina. | Posiziona il file `.ttf`/`.otf` nella cartella passata a `SetFontsFolder`. Aspose.Words lo carica direttamente, senza necessità di installazione a livello di OS. |

**Consiglio esperto:** Quando esegui questo in una pipeline CI/CD, reindirizza l'output della console a un artefatto di build. In questo modo avrai una traccia di audit di ogni sostituzione di font avvenuta durante la build.

---

## Esempio completo funzionante (pronto per copia‑incolla)

Di seguito trovi il programma completo che puoi inserire in un nuovo progetto Console App. Include tutti i passaggi, le istruzioni `using` e i commenti necessari.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Output console previsto** (supponendo che `Times New Roman` fosse mancante):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Esegui il programma, apri `output.pdf` e vedrai il documento renderizzato con il fallback font ovunque necessario.

---

## Conclusione

Ora disponi di un modello solido e pronto per la produzione su come **set warning callback** in C#, **configure default font**, **monitor font changes** e **set default import font** quando lavori con Aspose.Words. Collegando un raccoglitore di avvisi prima del caricamento, puntando `FontSettings` a una cartella di font affidabile e, opzionalmente, forzando un fallback globale, ottieni piena visibilità e controllo sulla sostituzione dei font—esattamente ciò di cui ha bisogno qualsiasi pipeline di elaborazione documenti robusta.

Pronto per il livello successivo? Prova a combinare questo approccio con:

- **Caricamento dinamico dei font** da un database (usa `FontSettings.SetFontsFolder` a runtime).  
- **Gestori di avviso personalizzati** che scrivono in un log strutturato (JSON o CSV) per analisi.  
- **Elaborazione parallela dei documenti** dove ogni thread ottiene il proprio `LoadOptions` per evitare interferenze.  

Sentiti libero di sperimentare, adattare il codice alla tua architettura e condividere eventuali scoperte nei commenti. Buon coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}