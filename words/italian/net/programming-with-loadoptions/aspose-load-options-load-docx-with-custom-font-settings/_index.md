---
category: general
date: 2025-12-29
description: Le Opzioni di Caricamento di Aspose consentono di caricare file DOCX
  personalizzando le impostazioni dei font e rilevando i font mancanti. Scopri come
  caricare i docx con il pieno controllo.
draft: false
keywords:
- aspose load options
- how to load docx
- custom font settings
- load word document
- detect missing fonts
language: it
og_description: Le Opzioni di Caricamento di Aspose ti consentono di caricare file
  DOCX personalizzando le impostazioni dei caratteri e rilevando i caratteri mancanti.
  Scopri come caricare i DOCX con il pieno controllo.
og_title: Opzioni di caricamento Aspose – Carica DOCX con impostazioni di carattere
  personalizzate
tags:
- Aspose.Words
- C#
- Document Processing
title: Opzioni di caricamento Aspose – Carica DOCX con impostazioni di font personalizzate
url: /it/net/programming-with-loadoptions/aspose-load-options-load-docx-with-custom-font-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Opzioni di Caricamento Aspose – Carica DOCX con Impostazioni Font Personalizzate

Ti sei mai chiesto come caricare un file DOCX in C# senza incappare in font mancanti? Non sei l'unico. **Le Opzioni di Caricamento Aspose** ti danno il controllo totale su come un documento Word viene aperto, consentendoti di impostare impostazioni font personalizzate e persino di rilevare i font mancanti prima che diventino un problema.

In questo tutorial percorreremo l'intero processo di caricamento di un DOCX usando Aspose.Words, configurando **impostazioni font personalizzate**, e collegando una callback di avviso che ti indica quali font sono mancanti. Alla fine sarai in grado di **caricare documenti Word** con fiducia, indipendentemente dai font usati dall'autore originale.

> **Prerequisito** – Hai bisogno di Aspose.Words per .NET (ultima versione) referenziato nel tuo progetto e una conoscenza di base di C#. Non sono richieste altre librerie.

## Cosa Imparerai

- Come creare un oggetto `LoadOptions` e collegare una callback di avviso.  
- Come impostare `FontSettings` per **impostazioni font personalizzate**.  
- Come effettivamente **caricare docx** e verificare che i font mancanti vengano segnalati.  
- Suggerimenti per gestire casi limite come font incorporati o cartelle di font basate su rete.

## Passo 1: Installa Aspose.Words e Prepara il Progetto

Prima di tutto, assicurati che Aspose.Words sia installato. Il modo più semplice è tramite NuGet:

```bash
dotnet add package Aspose.Words
```

Una volta aggiunto il pacchetto, crea un nuovo progetto console C# (o inserisci il codice in qualsiasi app esistente). Il codice che scriveremo funziona con .NET 6+ e .NET Framework 4.7.2+, quindi sei coperto in entrambi i casi.

> **Consiglio professionale:** Se stai puntando a .NET Core, aggiungi `using System;` all'inizio del file; l'IDE di solito lo inserisce automaticamente.

## Passo 2: Configura le Opzioni di Caricamento Aspose con una Callback di Avviso

Ora arriviamo al cuore della questione—**le opzioni di caricamento Aspose**. La classe `LoadOptions` ti permette di regolare come un documento viene analizzato. La useremo per:

1. Collegare una callback che si attiva ogni volta che il loader non riesce a trovare un font richiesto.  
2. Assegnare un'istanza `FontSettings` che potrà essere successivamente modificata per **impostazioni font personalizzate**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Step 2.1 – Create LoadOptions and a FontSettings object
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();

        // FontSettings is where you control where Aspose looks for fonts.
        // You could point it at a folder, a collection, or even a stream.
        FontSettings fontSettings = new FontSettings();

        // --------------------------------------------------------------
        // Step 2.2 – Register a warning callback to detect missing fonts
        // --------------------------------------------------------------
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            // This will be called for each missing font.
            // args.FontInfo can be null, so we guard against it.
            string missingFont = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missingFont}");
        };

        // Attach the FontSettings to the LoadOptions.
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Step 2.3 – (Optional) Add a custom font folder
        // --------------------------------------------------------------
        // If you have a folder with corporate fonts, tell Aspose to use it.
        // Replace "C:\\MyFonts" with the actual path on your machine.
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);
```

**Perché è importante:** Senza una callback di avviso, Aspose sostituisce silenziosamente i font mancanti, il che può provocare sorprese di layout in seguito. Collegandoti alla callback, **rilevi i font mancanti** in anticipo e puoi decidere se incorporare un fallback o chiedere all'utente di installare il tipo di carattere mancante.

## Passo 3: Carica il DOCX Usando le Opzioni Configurate

Con le `LoadOptions` pronte, caricare un DOCX è una riga di codice. Il costruttore `Document` accetta il percorso del file e le opzioni che abbiamo appena creato.

```csharp
        // --------------------------------------------------------------
        // Step 3 – Load the DOCX file while respecting our custom settings
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";

        // The Document constructor will invoke the warning callback
        // for any font it cannot resolve.
        Document doc = new Document(inputPath, loadOptions);

        Console.WriteLine("Document loaded successfully.");
```

Se il file di origine fa riferimento a un font che non è presente sul sistema o nella cartella personalizzata, vedrai un output simile a:

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
```

Quell'immediato feedback è inestimabile quando costruisci una pipeline di elaborazione batch che deve garantire fedeltà visiva.

## Passo 4: Verifica il Documento Caricato (Facoltativo ma Utile)

Dopo il caricamento, potresti voler confermare che il contenuto del documento sia accessibile. Per un rapido controllo di sanità, stampiamo il testo del primo paragrafo.

```csharp
        // --------------------------------------------------------------
        // Step 4 – Quick sanity check: print the first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");
    }
}
```

Eseguendo il programma ora otterrai:

```
[Warning] Missing font: Times New Roman
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

## Passo 5: Casi Limite & Suggerimenti Avanzati

### 5.1 Gestione dei Font Incorporati

Alcuni file DOCX incorporano direttamente i font richiesti. Aspose.Words li utilizza automaticamente, quindi non vedrai avvisi per questi. Tuttavia, se deliberatamente **carichi documenti Word** che rimuovono i font incorporati (ad esempio, dopo una conversione), potresti dover fornire i font mancanti tramite `SetFontsFolder` come mostrato in precedenza.

### 5.2 Utilizzare uno Stream di Memoria Invece di un Percorso File

Se il tuo DOCX risiede in un database o proviene da una richiesta HTTP, puoi caricarlo da un `MemoryStream`:

```csharp
using (var stream = new MemoryStream(byteArrayFromDb))
{
    Document docFromStream = new Document(stream, loadOptions);
    // Continue processing...
}
```

Le stesse **opzioni di caricamento Aspose** si applicano, e la callback di avviso funziona comunque.

### 5.3 Sovrascrivere Globalmente la Sostituzione dei Font

Se preferisci sostituire i font mancanti con un fallback specifico (ad esempio, Arial), puoi aggiungere una regola di sostituzione:

```csharp
fontSettings.SubstitutionSettings.FontSubstitution.AddSubstitutes("MissingFontName", new[] { "Arial" });
```

Combina questo con la callback di avviso per registrare l'evento di sostituzione e mantenere l'output coerente.

## Passo 6: Esempio Completo Funzionante

Di seguito trovi il programma completo, pronto per il copia‑incolla, che incorpora tutti i passaggi descritti. Salvalo come `Program.cs`, ripristina i pacchetti NuGet e avvialo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // --------------------------------------------------------------
        // Create LoadOptions with custom font settings and warning callback
        // --------------------------------------------------------------
        LoadOptions loadOptions = new LoadOptions();
        FontSettings fontSettings = new FontSettings();

        // Warn about missing fonts
        fontSettings.SubstitutionSettings.WarningCallback = (sender, args) =>
        {
            string missing = args.FontInfo?.FullFontName ?? "Unknown Font";
            Console.WriteLine($"[Warning] Missing font: {missing}");
        };

        // Optional: point to a folder with corporate fonts
        fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

        // Attach settings to load options
        loadOptions.FontSettings = fontSettings;

        // --------------------------------------------------------------
        // Load the DOCX file
        // --------------------------------------------------------------
        string inputPath = @"C:\Documents\input.docx";
        Document doc = new Document(inputPath, loadOptions);
        Console.WriteLine("Document loaded successfully.");

        // --------------------------------------------------------------
        // Quick sanity check – print first paragraph
        // --------------------------------------------------------------
        string firstParagraph = doc.FirstSection.Body.Paragraphs[0].GetText();
        Console.WriteLine($"First paragraph text: {firstParagraph}");

        // --------------------------------------------------------------
        // (Optional) Demonstrate loading from a stream
        // --------------------------------------------------------------
        // byte[] bytes = File.ReadAllBytes(inputPath);
        // using var ms = new MemoryStream(bytes);
        // Document docFromStream = new Document(ms, loadOptions);
        // Console.WriteLine("Loaded from stream.");
    }
}
```

### Output Atteso

```
[Warning] Missing font: Times New Roman
[Warning] Missing font: Calibri
Document loaded successfully.
First paragraph text: This is the first line of my DOCX file.
```

Se non mancano font, le righe di avviso semplicemente non appariranno.

## Panoramica Visiva

![esempio opzioni di caricamento aspose](/images/aspose-load-options.png "Diagramma che mostra il flusso di lavoro delle Opzioni di Caricamento Aspose")

*Il diagramma illustra come le **Opzioni di Caricamento Aspose** si collocano tra la tua fonte file e l'oggetto `Document`, gestendo la risoluzione dei font e il rilevamento dei font mancanti.*

## Conclusione

Abbiamo percorso una soluzione completa per **le opzioni di caricamento Aspose**, mostrandoti esattamente **come caricare docx** applicando **impostazioni font personalizzate** e **rilevando i font mancanti**. Configurando una callback di avviso e, facoltativamente, puntando Aspose a una cartella di font personalizzata, ottieni piena visibilità sui problemi di font prima che influenzino il rendering.  

Da qui puoi esplorare argomenti correlati come la conversione **carica documento Word** in PDF, l'aggiunta di filigrane, o l'elaborazione batch di decine di file in una cartella. Lo stesso schema—creare `LoadOptions`, collegare le callback e chiamare `new Document(...)`—funziona su tutta l'API di Aspose.Words.

Hai domande su un caso limite specifico, come la gestione di lingue da destra a sinistra o di file DOCX criptati? Lascia un commento o consulta la documentazione di Aspose.Words per approfondimenti. Buona programmazione, e che i tuoi documenti vengano sempre renderizzati esattamente come previsto!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}