---
category: general
date: 2026-04-21
description: Scopri come rilevare i font, catturare gli avvisi, configurare la callback
  e elencare gli avvisi con Aspose.Words in C#. Guida passo‑passo per una gestione
  affidabile dei font.
draft: false
keywords:
- how to detect fonts
- how to capture warnings
- how to configure callback
- how to enumerate warnings
- Aspose.Words font handling
language: it
og_description: Come rilevare i font in Aspose.Words? Questo tutorial ti mostra come
  catturare gli avvisi, configurare un callback e enumerare gli avvisi in C#.
og_title: Come rilevare i font in Aspose.Words – Guida completa
tags:
- Aspose.Words
- C#
- Document Processing
title: Come rilevare i font in Aspose.Words – Guida completa
url: /it/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come rilevare i font in Aspose.Words – Guida completa

Ti sei mai chiesto **come rilevare i font** mancanti quando carichi un documento Word? È uno scenario che compare più spesso di quanto vorresti, soprattutto quando si lavora con file legacy o distribuzioni cross‑platform. In questo tutorial percorreremo un esempio completo e funzionante che **cattura gli avvisi**, **configura un callback** e **elenca gli avvisi** così saprai sempre quali font sono stati sostituiti.

Useremo Aspose.Words per .NET (v24.9 al momento della stesura) e C# puro. Nessun servizio esterno, nessuna magia—solo l'API e qualche riga di codice. Alla fine sarai in grado di individuare ogni sostituzione di font, registrarla e persino decidere se interrompere il caricamento se un font critico è mancante.  

### Cosa ti serve
- **Aspose.Words per .NET** (installalo via NuGet: `Install-Package Aspose.Words`)
- .NET 6.0 o successivo (il codice funziona anche su .NET Framework)
- Un file DOCX di esempio che faccia riferimento a un font non presente sulla macchina (ad es. “MyCustomFont.ttf”)
- Visual Studio, Rider o qualsiasi editor C# tu preferisca

> **Consiglio esperto:** Se non hai un documento con font mancanti, rinomina semplicemente un file di font sul tuo sistema o modifica l'XML del DOCX per fare riferimento a una famiglia di font inesistente.

---

## Come rilevare i font con Aspose.Words

L'idea di base è agganciarsi al sistema di avvisi di Aspose.Words. Quando la libreria non riesce a trovare un font richiesto, emette un avviso `WarningType.FontSubstitution`. Fornendo un'implementazione personalizzata di `IWarningCallback`, puoi **rilevare i font** che sono stati sostituiti durante il processo di caricamento.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a collector that implements IWarningCallback
public class FontWarningCollector : IWarningCallback
{
    public List<WarningInfo> Warnings { get; } = new();

    public void Warning(WarningInfo info)
    {
        // Store every warning – we’ll filter later
        Warnings.Add(info);
    }
}
```

> **Perché funziona:** Aspose.Words chiama il metodo `Warning` per ogni problema non critico. Memorizzando gli oggetti `WarningInfo` ottieni pieno accesso al tipo, al messaggio e al contesto, che è esattamente ciò di cui hai bisogno per **rilevare i font** sostituiti.

---

## Come catturare gli avvisi durante il caricamento di un documento

Ora che abbiamo un raccoglitore, dobbiamo dire a `LoadOptions` di usarlo. Questa è la parte **come catturare gli avvisi** del puzzle.

```csharp
// 2️⃣ Prepare LoadOptions with our warning collector
var warningCollector = new FontWarningCollector();
var loadOptions = new LoadOptions
{
    // Assign the callback – this is where warnings are captured
    WarningCallback = warningCollector
};

// 3️⃣ Load the document (replace the path with your own file)
Document doc = new Document("YOUR_DIRECTORY/DocumentWithMissingFont.docx", loadOptions);
```

> **Caso limite:** Se carichi un documento da uno stream (`new Document(stream, loadOptions)`), lo stesso callback funziona—basta passare lo stream invece del percorso file.

A questo punto il documento è completamente caricato, ma tutti gli avvisi di sostituzione dei font sono salvati in modo sicuro dentro `warningCollector.Warnings`.

---

## Come elencare gli avvisi e segnalare le sostituzioni di font

Infine, filtriamo gli avvisi raccolti e **elenchiamo gli avvisi** che riguardano specificamente la sostituzione dei font. Questo passaggio trasforma i dati grezzi in un report leggibile.

```csharp
// 4️⃣ Iterate over the collected warnings
foreach (var warning in warningCollector.Warnings)
{
    // We're only interested in font substitution warnings
    if (warning.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Substituted font: {warning.Message}");
    }
}
```

**Output previsto** (esempio):

```
Substituted font: Font 'Calibri' not found. Substituted with 'Arial'.
Substituted font: Font 'MyCustomFont' not found. Substituted with 'Times New Roman'.
```

Se il documento non contiene font mancanti, il ciclo non produce alcun output—nulla di cui preoccuparsi.

---

## Esempio completo funzionante (tutti i passaggi in un unico file)

Di seguito trovi il programma completo che puoi copiare‑incollare in un progetto console. Unisce **come rilevare i font**, **come catturare gli avvisi**, **come configurare il callback** e **come elencare gli avvisi** in un flusso unico e coerente.

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontDetectionDemo
{
    // Custom warning collector (captures all warnings)
    public class FontWarningCollector : IWarningCallback
    {
        public List<WarningInfo> Warnings { get; } = new();

        public void Warning(WarningInfo info)
        {
            Warnings.Add(info);
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Set up the warning collector (how to configure callback)
            var collector = new FontWarningCollector();
            var loadOptions = new LoadOptions
            {
                WarningCallback = collector
            };

            // -------------------------------------------------
            // Step 2: Load the document (how to detect fonts)
            string filePath = "YOUR_DIRECTORY/DocumentWithMissingFont.docx";
            Document doc;
            try
            {
                doc = new Document(filePath, loadOptions);
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to load document: {ex.Message}");
                return;
            }

            // -------------------------------------------------
            // Step 3: Enumerate warnings (how to enumerate warnings)
            bool anySubstitutions = false;
            foreach (var warning in collector.Warnings)
            {
                if (warning.Type == WarningType.FontSubstitution)
                {
                    anySubstitutions = true;
                    Console.WriteLine($"Substituted font: {warning.Message}");
                }
            }

            if (!anySubstitutions)
            {
                Console.WriteLine("No font substitutions detected – all fonts are available.");
            }

            // Optional: Continue processing the document...
        }
    }
}
```

**Eseguendo questo programma** verrà stampato ogni font che Aspose.Words ha dovuto sostituire. Puoi reindirizzare l'output a un file di log, generare un avviso, o addirittura interrompere il caricamento se un font critico è mancante.

---

## Domande frequenti e insidie

### E se devo interrompere il caricamento quando un font richiesto è mancante?
Puoi ispezionare gli oggetti `WarningInfo` all'interno del callback e lanciare un'eccezione quando appare un nome di font specifico. L'eccezione interromperà il caricamento, dandoti il pieno controllo.

```csharp
public void Warning(WarningInfo info)
{
    if (info.Type == WarningType.FontSubstitution &&
        info.Message.Contains("MyCriticalFont"))
    {
        throw new InvalidOperationException("Critical font missing – aborting load.");
    }
    Warnings.Add(info);
}
```

### Funziona con PDF o altri formati?
Sì. Aspose.Words utilizza la stessa infrastruttura di avvisi per PDF, RTF e HTML. Basta cambiare l'estensione del file e il resto del codice rimane identico.

### Come posso registrare gli avvisi su un file invece che sulla console?
Sostituisci `Console.WriteLine` con qualsiasi framework di logging tu preferisca (`Serilog`, `NLog`, ecc.). La classe `WarningInfo` espone `Message`, `Source` e `Exception` per log dettagliati.

### Questo influisce sulle prestazioni?
Il sovraccarico è trascurabile—Aspose.Words genera già gli avvisi internamente. Aggiungere un callback semplicemente li memorizza in una lista, operazione O(n) rispetto al numero di avvisi. Per documenti tipici, l'impatto è ben al di sotto dell'1 % del tempo totale di caricamento.

---

## Riepilogo visivo

![Come rilevare i font in Aspose.Words – diagramma del flusso di avviso](https://example.com/images/font-detection-diagram.png "come rilevare i font")

*Testo alternativo:* **come rilevare i font** – diagramma che mostra il callback di avviso, la raccolta e i passaggi di enumerazione.

---

## Conclusione

Abbiamo coperto **come rilevare i font** in Aspose.Words mediante **cattura degli avvisi**, **configurazione di un callback** e **enumerazione degli avvisi**. Il campione di codice completo mostra un pattern pronto per la produzione che puoi inserire in qualsiasi applicazione .NET.  

Successivamente, potresti voler approfondire:

- **Come catturare gli avvisi** per altri problemi (ad es. errori di conversione immagine)
- **Come configurare il callback** per framework di logging personalizzati
- **Come enumerare gli avvisi** su più documenti in un batch
- L'uso di **Aspose.Words.Fonts.FontSettings** per fornire cartelle di font di fallback, riducendo così il numero di sostituzioni fin dall'inizio.

Provalo, adatta il raccoglitore al tuo stile di logging, e non sarai più sorpreso da una sostituzione di font inattesa. Se incontri difficoltà, lascia un commento qui sotto—buona programmazione!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}