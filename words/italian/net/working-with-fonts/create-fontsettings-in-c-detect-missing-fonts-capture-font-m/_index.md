---
category: general
date: 2026-03-01
description: Crea FontSettings in C# per rilevare i font mancanti, catturare i messaggi
  dei font e gestire i font mancanti con Aspose.Words. Guida passo‑passo per gli sviluppatori.
draft: false
keywords:
- create fontsettings
- detect missing fonts
- capture font messages
- handle missing fonts
- Aspose.Words font handling
- C# document processing
language: it
og_description: Crea FontSettings in C# per rilevare i font mancanti, catturare i
  messaggi dei font e gestire i font mancanti usando Aspose.Words. Tutorial completo
  con codice.
og_title: Crea FontSettings in C# – Rileva i font mancanti e cattura i messaggi dei
  font
tags:
- Aspose.Words
- C#
- Font Management
title: Crea FontSettings in C# – Rileva i font mancanti e cattura i messaggi dei font
url: /it/net/working-with-fonts/create-fontsettings-in-c-detect-missing-fonts-capture-font-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea FontSettings in C# – Rileva Font Mancanti e Cattura Messaggi di Font

Hai mai dovuto **creare FontSettings** in un progetto .NET ma non sapevi come individuare i font che non sono installati sulla macchina di destinazione? Non sei l'unico. In molte applicazioni reali — pensa a generatori di report automatizzati o convertitori di documenti — i font mancanti possono rompere silenziosamente il layout, e non lo scopri finché il PDF non appare strano.  

E se potessi **rilevare i font mancanti**, **catturare i messaggi di font**, e **gestire i font mancanti** prima che rovinino il risultato? La buona notizia è che Aspose.Words rende tutto questo un gioco da ragazzi. In questo tutorial percorreremo l’intero processo, dalla configurazione dell’oggetto `FontSettings` all’attivazione di un callback di avviso che ti indica esattamente quali glifi sono stati sostituiti.

> **TL;DR:** Alla fine avrai un’app console C# pronta all’uso che registra ogni sostituzione di font, permettendoti di decidere se incorporare un sostituto o avvisare l’utente.

---

## Prerequisiti

- .NET 6 SDK (o qualsiasi versione recente di .NET)  
- Visual Studio 2022 o VS Code con estensioni C#  
- Una licenza Aspose.Words per .NET (la versione di prova gratuita è sufficiente per questa demo)  
- Un file DOCX di esempio che faccia riferimento a un font non installato (ad es., *Comic Sans MS* su una macchina Linux)  

Non sono necessari pacchetti NuGet speciali oltre a `Aspose.Words`.

---

## Passo 1 – Installa Aspose.Words e Configura il Progetto

Prima di tutto, crea un nuovo progetto console e aggiungi la libreria Aspose.Words.

```bash
dotnet new console -n FontSettingsDemo
cd FontSettingsDemo
dotnet add package Aspose.Words
```

> **Suggerimento:** Se hai già una soluzione, aggiungi semplicemente il pacchetto tramite l’interfaccia di NuGet Package Manager — così è più facile tenere traccia delle versioni.

---

## Passo 2 – Crea FontSettings (Parola Chiave Principale Appare Qui)

Il passo **create FontSettings** è la pietra angolare di qualsiasi flusso di lavoro legato ai font. `FontSettings` indica ad Aspose.Words dove cercare i font, se usare le cartelle di sistema e come fare fallback quando qualcosa manca.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// 1️⃣ Create a FontSettings object – this is where we’ll configure search paths.
FontSettings fontSettings = new FontSettings();

// Optional: add a custom folder that contains fallback fonts.
fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

Perché è importante? Senza un `FontSettings` configurato correttamente, il motore sostituisce silenziosamente i glifi mancanti con il font di sistema predefinito, e non vedrai mai un avviso.

---

## Passo 3 – Collega LoadOptions con FontSettings

`LoadOptions` ti permette di passare il `FontSettings` al caricatore di documenti. Questo è il ponte che consente al motore di **rilevare i font mancanti** durante la fase di costruzione del `Document`.

```csharp
// 2️⃣ Configure LoadOptions to use the FontSettings we just created.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

Ora, ogni volta che carichi un DOCX con `loadOptions`, Aspose.Words consulterà il `FontSettings` impostato in precedenza.

---

## Passo 4 – Attacca un Callback di Avviso per **Catturare Messaggi di Font**

Aspose.Words emette avvisi per varie condizioni — la sostituzione di font è una delle più comuni. Fornendo un’implementazione di `IWarningCallback`, puoi **catturare i messaggi di font** in tempo reale.

```csharp
// 3️⃣ Attach a warning handler that will print font‑substitution warnings.
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

### La Classe del Gestore di Avvisi

```csharp
/// <summary>
/// Handles font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Source == WarningSource.FontSubstitution)
        {
            Console.WriteLine($"[FontSubstitution] {info.Description}");
        }
    }
}
```

Il campo `info.Description` contiene un messaggio leggibile dall’uomo, ad esempio *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”* Questo è esattamente il tipo di output di cui hai bisogno per **gestire i font mancanti** in modo elegante.

---

## Passo 5 – Carica il Documento e Lascia che il Callback Faccia il Suo Lavoro

Con tutto collegato, il caricamento del documento è semplice. Se il file sorgente fa riferimento a un font assente dal sistema, il nostro gestore di avvisi verrà attivato.

```csharp
// 4️⃣ Load a document that may contain unknown fonts.
Document doc = new Document(@"C:\Docs\UnknownFont.docx", loadOptions);

// Optional: you can now save the document to PDF or any other format.
doc.Save(@"C:\Docs\Result.pdf");
```

Quando esegui il programma, vedrai un output sulla console simile a:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
[FontSubstitution] Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Quell’output è la parte **capture font messages** del nostro flusso di lavoro. Puoi estendere il gestore per scrivere su file, inviare telemetria, o persino abortire la conversione se mancano font critici.

---

## Passo 6 – Esempio Completo (Tutti i Pezzi Insieme)

Di seguito trovi un programma completo, pronto per il copia‑incolla. Incollalo in `Program.cs`, aggiusta i percorsi dei file e avvia `dotnet run`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSettingsDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // ----- Step 1: Create FontSettings -----
            FontSettings fontSettings = new FontSettings();
            // Add any custom folder with fallback fonts (optional)
            fontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);

            // ----- Step 2: Configure LoadOptions -----
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                WarningCallback = new FontSubstitutionWarningHandler()
            };

            // ----- Step 3: Load the document -----
            string inputPath = @"C:\Docs\UnknownFont.docx";
            Document doc = new Document(inputPath, loadOptions);

            // ----- Step 4: Save the result (optional) -----
            string outputPath = @"C:\Docs\Result.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any font substitution warnings.");
        }
    }

    // ----- Warning handler that captures font messages -----
    class FontSubstitutionWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Source == WarningSource.FontSubstitution)
            {
                Console.WriteLine($"[FontSubstitution] {info.Description}");
            }
        }
    }
}
```

### Output Atteso

Eseguendo il programma su una macchina che non ha *Comic Sans MS* verrà stampato qualcosa del genere:

```
[FontSubstitution] Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document processed. Check console for any font substitution warnings.
```

Otterrai anche `Result.pdf` che utilizza i font sostituiti, garantendo che la conversione non vada in crash.

---

## Domande Frequenti & Casi Limite

| Domanda | Risposta |
|----------|----------|
| **E se voglio che la conversione fallisca invece di sostituire?** | All’interno di `FontSubstitutionWarningHandler`, lancia un’eccezione quando `info.Description` contiene il nome di un font critico. |
| **Posso incorporare automaticamente un font di sostituzione?** | Sì. Dopo aver rilevato un font mancante, puoi caricare un `FontInfo` di fallback da un percorso noto e aggiungerlo a `fontSettings` tramite `fontSettings.SetFontsFolder`. |
| **Funziona su Linux/macOS?** | Assolutamente. `FontSettings` è cross‑platform; assicurati solo che la cartella di fallback contenga i file `.ttf` o `.otf` appropriati. |
| **Il callback di avviso è thread‑safe?** | Il callback viene eseguito nello stesso thread che carica il documento, quindi non serve sincronizzazione aggiuntiva per la scrittura su console. Per scenari multi‑thread, proteggi le risorse condivise. |
| **Come registro gli avvisi su un file?** | Sostituisci `Console.WriteLine` con `File.AppendAllText("font_warnings.log", ...)` oppure usa un framework di logging (Serilog, NLog). |

---

## Suggerimenti Pro per una Gestione dei Font Pronta per la Produzione

1. **Cache delle Ricerche di Font** – Riutilizzare la stessa istanza di `FontSettings` per più caricamenti di documenti evita scansioni ripetute del filesystem.  
2. **Whitelist di Font Critici** – Se il tuo brand richiede un font specifico, verifica la sua presenza subito e abortisci con un messaggio di errore chiaro.  
3. **Usa `SetFontFolder` Ricorsivamente** – Impostare `recursive: true` garantisce la scansione delle sottocartelle, utile quando distribuisci un’intera collezione di font.  
4. **Combina con `FontSubstitutionSettings`** – Puoi affinare le regole di sostituzione (ad es., preferire font con lo stesso nome di famiglia).  

---

## Conclusione

Abbiamo appena **creato FontSettings**, configurato `LoadOptions` per **rilevare i font mancanti**, collegato un callback che **cattura i messaggi di font**, e dimostrato come **gestire i font mancanti** in modo pulito e pronto per la produzione. L’intero flusso si inserisce in poche decine di righe di C#, ma ti offre piena visibilità sul panorama dei font di qualsiasi DOCX che elabori.

Prossimi passi, potresti esplorare:

- **Incorporare font di fallback** direttamente nel PDF di output (`PdfSaveOptions.FontEmbeddingMode`).  
- **Sostituire programmaticamente i font** in base a regole di branding aziendale.  
- **Integrare con una pipeline CI** per segnalare automaticamente i documenti che usano font non autorizzati.

Provalo, personalizza il gestore di avvisi secondo le tue esigenze, e lascia che le tue pipeline di documenti funzionino con sicurezza — niente più misteriosi glitch di layout causati da scambi di font invisibili.

Buon coding! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}