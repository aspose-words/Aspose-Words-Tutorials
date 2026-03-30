---
category: general
date: 2026-03-30
description: come catturare gli avvisi durante il caricamento di un file DOCX – impara
  a rilevare i font mancanti, configurare le impostazioni dei font e impostare le
  opzioni di caricamento in C#
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: it
og_description: come catturare gli avvisi durante il caricamento di un file DOCX –
  guida passo‑passo per rilevare i font mancanti e configurare le impostazioni dei
  font in C#
og_title: come catturare gli avvisi – configurare le opzioni di caricamento per i
  font mancanti
tags:
- Aspose.Words
- C#
- Font management
title: come catturare gli avvisi – configurare le opzioni di caricamento per i font
  mancanti
url: /it/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# come catturare gli avvisi – configurare le opzioni di caricamento per i font mancanti

Ti sei mai chiesto **come catturare gli avvisi** che compaiono quando un documento tenta di utilizzare un font che non hai installato? È uno scenario che mette in difficoltà molti sviluppatori che lavorano con librerie di elaborazione testi, soprattutto quando è necessario **rilevare i font mancanti** prima che interrompano la tua pipeline di esportazione PDF.  

In questo tutorial ti mostreremo una soluzione pratica, pronta‑all'uso, che **configura le impostazioni dei font**, **imposta le opzioni di caricamento** e stampa ogni avviso di sostituzione sulla console. Alla fine saprai esattamente come **gestire i font mancanti** in modo da mantenere la tua applicazione robusta e i tuoi utenti soddisfatti.

## Cosa imparerai

- Come **impostare le opzioni di caricamento** in modo che la libreria segnali i problemi di font invece di sostituirli silenziosamente.
- I passaggi esatti per **configurare le impostazioni dei font** per la cattura degli avvisi.
- Modi per **rilevare i font mancanti** programmaticamente e reagire di conseguenza.
- Un esempio completo, copy‑paste in C#, che funziona con l'ultima versione di Aspose.Words per .NET (v24.10 al momento della stesura).
- Suggerimenti per estendere la soluzione per registrare gli avvisi, ricorrere a font personalizzati o interrompere l'elaborazione quando i font critici sono assenti.

> **Prerequisito:** È necessario avere installato il pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`). Non sono richieste altre dipendenze esterne.

---

## Passo 1: Importare i namespace e preparare il progetto

Per prima cosa, aggiungi le direttive `using` essenziali. Non si tratta solo di boilerplate; indicano al compilatore dove si trovano `LoadOptions`, `FontSettings` e `Document`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Consiglio professionale:** Se stai usando .NET 6+ puoi abilitare le dichiarazioni *global using* per evitare di ripetere queste righe in ogni file.

---

## Passo 2: Impostare le opzioni di caricamento e abilitare gli avvisi di sostituzione dei font

Il cuore di **come catturare gli avvisi** risiede nell'oggetto `LoadOptions`. Creando una nuova istanza di `FontSettings` e collegando un gestore di eventi a `SubstitutionWarning`, fai sì che la libreria segnali ogni volta che non riesce a trovare un font richiesto.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Perché è importante:** Senza l'iscrizione all'evento, Aspose.Words ricorre silenziosamente a un font predefinito e non sai mai quali glifi sono stati sostituiti. Ascoltando `SubstitutionWarning`, ottieni un tracciamento completo—cruciale per ambienti con requisiti di conformità stringenti.

## Passo 3: Caricare il documento usando le opzioni configurate

Ora che gli avvisi sono collegati, carica il tuo DOCX (o qualsiasi formato supportato) con le `loadOptions` appena preparate. Il costruttore `Document` attiverà immediatamente la logica di verifica dei font.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Se il file fa riferimento, ad esempio, a *“Comic Sans MS”* su una macchina che ha solo *“Arial”*, vedrai qualcosa di simile:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Quella riga viene stampata direttamente sulla console grazie al gestore che abbiamo collegato in precedenza.

## Passo 4: Verificare e reagire agli avvisi catturati

Catturare gli avvisi è solo metà della battaglia; spesso è necessario decidere cosa fare dopo. Di seguito trovi un modello rapido che memorizza gli avvisi in una lista per un'analisi successiva—perfetto se vuoi registrarli su file o interrompere l'importazione quando un font critico è mancante.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Gestione dei casi limite:**  
- **Font mancanti multipli:** La lista conterrà una voce per ogni sostituzione, così potrai iterare e creare un report dettagliato.  
- **Font di fallback personalizzati:** Se disponi di file di font propri, aggiungili a `FontSettings` prima del caricamento: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. Gli avvisi mostreranno allora il fallback personalizzato invece del predefinito di sistema.  

## Passo 5: Esempio completo funzionante (pronto per il copy‑paste)

Mettendo tutto insieme, ecco un'app console autonoma che puoi compilare ed eseguire subito.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Output console previsto** (quando il DOCX fa riferimento a un font mancante):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Se un font *critico* come “Times New Roman” è mancante, vedrai invece il messaggio di interruzione.

## Domande frequenti e insidie

| Question | Answer |
|----------|--------|
| **Devo chiamare `SetFontsFolder` per catturare gli avvisi?** | No. L'evento di avviso funziona con i font di sistema predefiniti. Usa `SetFontsFolder` solo quando vuoi fornire font di fallback aggiuntivi. |
| **Funzionerà su .NET Core / .NET 5+?** | Assolutamente. Aspose.Words 24.10 supporta tutti i runtime .NET moderni. Basta assicurarsi che il pacchetto NuGet corrisponda al framework di destinazione. |
| **E se volessi registrare gli avvisi su un file invece che sulla console?** | Sostituisci `Console.WriteLine(msg);` con una chiamata a qualsiasi framework di logging, ad esempio `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Posso sopprimere gli avvisi per font specifici?** | Sì. All'interno del gestore dell'evento puoi filtrare: `if (e.FontName == "SomeFont") return;`. Questo offre un controllo fine. |
| **C'è un modo per trattare i font mancanti come errori?** | Lancia un'eccezione manualmente all'interno del gestore quando una condizione è soddisfatta, oppure imposta un flag e interrompi l'elaborazione dopo la costruzione di `Document`, come mostrato nell'esempio. |

## Conclusione

Ora disponi di un modello solido, pronto per la produzione, per **catturare gli avvisi** che si verificano quando si caricano documenti con font mancanti. **Rilevando i font mancanti**, **configurando le impostazioni dei font** e **impostando le opzioni di caricamento** in modo appropriato, ottieni piena visibilità sugli eventi di sostituzione dei font e puoi decidere se registrarli, usare un fallback o interrompere.

Fai il passo successivo integrando questa logica nella tua pipeline di conversione PDF, aggiungendo font di fallback personalizzati o inviando la lista degli avvisi a un sistema di monitoraggio. L'approccio scala da piccoli utility a servizi di elaborazione documenti di livello enterprise.

### Letture aggiuntive e prossimi passi

- **Esplora altre funzionalità di FontSettings** – incorporare font personalizzati, controllare l'ordine di fallback e considerazioni di licenza.  
- **Combina con la conversione PDF** – dopo aver catturato gli avvisi, chiama `doc.Save("output.pdf");` e verifica che il PDF utilizzi i font previsti.  
- **Automatizza i test** – scrivi test unitari che caricano documenti con font noti mancanti e verifica che la lista degli avvisi contenga i messaggi attesi.  

Se incontri problemi o hai idee per miglioramenti, sentiti libero di lasciare un commento. Buon coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}