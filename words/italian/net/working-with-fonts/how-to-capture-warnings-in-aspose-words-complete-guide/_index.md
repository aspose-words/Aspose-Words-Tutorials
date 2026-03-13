---
category: general
date: 2026-03-13
description: Come catturare gli avvisi durante il caricamento dei documenti con Aspose.Words,
  oltre a suggerimenti per gestire i caratteri mancanti e impostare configurazioni
  di font personalizzate. Scopri una soluzione completa in C#.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: it
og_description: Come catturare gli avvisi durante il caricamento di file Word con
  Aspose.Words, oltre a modi pratici per gestire i font mancanti e impostare configurazioni
  di font personalizzate.
og_title: Come catturare gli avvisi in Aspose.Words – Guida completa
tags:
- Aspose.Words
- C#
- Document Processing
title: Come catturare gli avvisi in Aspose.Words – Guida completa
url: /it/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

Check for any URLs: none except image path. Keep unchanged.

Now produce final translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come catturare gli avvisi in Aspose.Words – Guida completa

Ti sei mai chiesto **come catturare gli avvisi** che compaiono quando Aspose.Words carica un documento? In molti progetti reali vedrai avvisi di sostituzione dei caratteri, note su funzionalità deprecate o persino messaggi relativi alla sicurezza. Ignorarli è come guidare con il parabrezza incrinato—potresti arrivare a destinazione, ma non saprai mai quando qualcosa sta per rompersi.

La buona notizia è che Aspose.Words ti offre un modo pulito, basato su callback, per intercettare questi messaggi. In questo tutorial percorreremo un **esempio completo in C#** che non solo cattura gli avvisi, ma ti mostra anche come **gestire i caratteri mancanti** e **impostare impostazioni di carattere personalizzate** affinché i tuoi documenti vengano renderizzati esattamente come ti aspetti.

---

## Cosa imparerai

- Configurare `LoadOptions` per inserire un oggetto `FontSettings` personalizzato.  
- Registrare una callback per gli avvisi che filtra gli eventi `FontSubstitution`.  
- Stampare i dettagli degli avvisi sulla console (o su qualsiasi logger tu preferisca).  
- Estendere la soluzione per gestire elegantemente i caratteri mancanti su diverse piattaforme.  

Al termine di questa guida avrai uno snippet pronto all'uso da inserire in qualsiasi progetto .NET, più una serie di consigli pratici per evitare le trappole più comuni.

---

## Prerequisiti

| Requisito | Perché è importante |
|-----------|----------------------|
| **Aspose.Words for .NET** (v23.12 o successiva) | L'API che utilizziamo (`LoadOptions`, `IWarningCallback`) si trova qui. |
| **.NET 6+** (o .NET Framework 4.7.2+) | Le funzionalità di linguaggio moderne rendono il codice più pulito. |
| **Un file DOCX di esempio** (chiamato `input.docx`) collocato in una cartella nota | Serve qualcosa da caricare e da far generare un avviso. |
| **Una console o un framework di logging** (opzionale) | Per vedere gli avvisi catturati in azione. |

Non sono necessari pacchetti NuGet aggiuntivi oltre a Aspose.Words stesso.

---

## Passo 1: Configurare le impostazioni di carattere personalizzate  

Prima di caricare un documento puoi indicare ad Aspose.Words dove cercare i caratteri. Questa è la parte **imposta impostazioni di carattere personalizzate** del puzzle.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Perché è importante:**  
Se un DOCX fa riferimento a un carattere che non è installato sulla macchina, Aspose.Words lo sostituirà silenziosamente con un carattere di fallback *a meno che* tu non abbia configurato una cartella contenente i caratteri richiesti. Impostando una cartella personalizzata riduci la probabilità di avvisi di “sostituzione del carattere” fin dall'inizio.

> **Suggerimento professionale:** Su Linux potresti dover aggiungere il pacchetto `fonts-dejavu-core` o qualsiasi collezione TrueType di cui i tuoi documenti dipendono.

---

## Passo 2: Registrare una callback per gli avvisi  

Aspose.Words implementa `IWarningCallback`. Creeremo un piccolo handler che stampa solo gli avvisi che ci interessano: caratteri mancanti o sostituiti.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Perché è importante:**  
Lo scenario **gestisci caratteri mancanti** è ora visibile. Invece di indovinare quale carattere è stato sostituito, ottieni una descrizione chiara come “Font 'Calibri' was substituted with 'Arial'”. Questo è inestimabile quando si debugga la disposizione in PDF generati o report stampati.

---

## Passo 3: Caricare il documento con le opzioni configurate  

Ora finalmente portiamo il documento in memoria, usando le `LoadOptions` che abbiamo appena preparato.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Se il file di origine utilizza un carattere che non è presente in `C:\MyFonts`, vedrai un output simile a:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Quella riga è il risultato **come catturare gli avvisi** che stavi cercando.

---

## Passo 4: Esempio completo (pronto per il copia‑incolla)

Di seguito trovi l'intero programma, pronto per la compilazione. Incollalo in un nuovo progetto console e avvialo—assicurati solo che i percorsi puntino a posizioni reali sulla tua macchina.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Output previsto:**  

- Se tutti i caratteri sono disponibili:  
  `Document processed. Check console for any warning messages.`  

- Se un carattere è mancante:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Passo 5: Varianti comuni e casi limite  

| Situazione | Cosa modificare |
|------------|-----------------|
| **Più cartelle di caratteri** | Chiama `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` per ogni posizione aggiuntiva. |
| **Sopprimere tutti gli avvisi** | Implementa `Warn` ma lascia il corpo vuoto, oppure imposta `loadOptions.WarningCallback = null;`. |
| **Catturare altri tipi di avviso** | Controlla `info.WarningType` contro `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent`, ecc. |
| **Esecuzione su Linux/macOS** | Assicurati che la cartella dei caratteri contenga file `.ttf`/`.otf` compatibili con Linux; potresti dover installare `libfontconfig`. |
| **Documenti di grandi dimensioni** | Considera lo streaming del documento (`LoadOptions.LoadFormat = LoadFormat.Docx;`) per ridurre la pressione sulla memoria. |

Prevedendo questi scenari eviterai sorprese quando passerai da una workstation di sviluppo a una pipeline CI o a una VM cloud.

---

## Passo 6: Conferma visiva (opzionale)

Se preferisci un'indicazione visiva rapida, puoi esportare gli avvisi catturati in un piccolo report HTML. Ecco un frammento che scrive i messaggi in `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Dopo aver caricato il documento, chiama `handler.WriteReport(@"C:\Docs\warnings.html");` e aprilo in un browser. L'immagine sotto mostra come potrebbe apparire il report:

![screenshot di come catturare gli avvisi](/images/capture-warnings.png)

*Testo alternativo:* **come catturare gli avvisi** – screenshot dell'output della console e del report HTML.

---

## Conclusione  

Abbiamo coperto **come catturare gli avvisi** in Aspose.Words, dimostrato un modo affidabile per **gestire i caratteri mancanti** e mostrato come **impostare impostazioni di carattere personalizzate** per un rendering deterministico. L'esempio completo è pronto per essere inserito in qualsiasi soluzione .NET, e il modulo `FontWarningHandler` può essere esteso per adattarsi alla tua strategia di logging o telemetria.

Prossimi passi? Prova a sostituire le chiamate a `Console.WriteLine` con un logger strutturato come Serilog, oppure invia gli avvisi a Application Insights per un monitoraggio in tempo reale. Potresti anche esplorare il pattern `DocumentVisitor` se devi ispezionare il contenuto del documento dopo il caricamento.

Hai domande su altri tipi di avviso o su strategie di incorporamento dei caratteri? Lascia un commento qui sotto—buona programmazione!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}