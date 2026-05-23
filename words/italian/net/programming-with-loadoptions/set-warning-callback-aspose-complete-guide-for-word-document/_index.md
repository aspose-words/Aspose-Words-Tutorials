---
category: general
date: 2026-05-23
description: Imposta il callback di avviso di Aspose per catturare gli avvisi di sostituzione
  dei font in Aspose.Words. Scopri LoadOptions, FontSettings e l'implementazione di
  IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: it
og_description: Imposta il callback di avviso di Aspose per monitorare la sostituzione
  dei caratteri in Aspose.Words. Questo tutorial mostra LoadOptions, FontSettings
  e l'implementazione del gestore di avvisi.
og_title: Imposta callback di avviso Aspose – Guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Imposta callback di avviso Aspose – Guida completa al caricamento di documenti
  Word
url: /it/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Guida completa per il caricamento di documenti Word

Ti sei mai chiesto come **set warning callback aspose** per non perdere mai più un avviso di sostituzione dei font? Non sei solo. Quando un DOCX fa riferimento a un font che non è installato, Aspose.Words lo sostituisce silenziosamente, e senza un callback adeguato potresti non accorgerti che qualcosa è cambiato.

In questo tutorial percorreremo un esempio completo e funzionante che mostra esattamente come catturare questi avvisi. Alla fine comprenderai **Aspose.Words LoadOptions**, come configurare **FontSettings** e perché implementare **IWarningCallback** è il modo più pulito per rimanere informato. Niente superflui—solo il codice che puoi inserire subito in un progetto .NET.

## Cosa imparerai

- Come **set warning callback aspose** su un'istanza `LoadOptions`.  
- Il ruolo di **Aspose.Words LoadOptions** durante l'apertura di un documento.  
- Configurare la gestione della **Aspose fonts substitution** con `FontSettings`.  
- Scrivere una **IWarningCallback implementation** personalizzata per registrare i problemi dei font.  
- Caricare un documento in modo sicuro con le migliori pratiche di **Aspose document loading**.

### Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.5+).  
- Una licenza valida di Aspose.Words per .NET o una chiave di prova.  
- Visual Studio, Rider o qualsiasi editor C# tu preferisca.  
- Un file DOCX di esempio (`fontTest.docx`) che faccia riferimento a un font mancante (opzionale ma utile).

> **Pro tip:** Se non hai un DOCX con font mancante, rinomina semplicemente un font nello stile del documento e osserva l'avviso generato.

---

## Come impostare il warning callback aspose per il caricamento dei documenti

Di seguito trovi il programma completo e autonomo. Salvalo come `Program.cs`, ripristina i pacchetti NuGet e avvialo. La console stamperà ogni avviso di sostituzione dei font generato da Aspose.Words durante il caricamento del file.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Output console previsto

Se `fontTest.docx` fa riferimento a un font che non è installato, vedrai qualcosa di simile:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Se tutti i font sono presenti, l'unica riga stampata sarà *Document loaded successfully*—nessun avviso, nessun rumore.

![esempio di set warning callback aspose](image.png "esempio di set warning callback aspose")

---

## Comprendere LoadOptions in Aspose.Words

`LoadOptions` è il punto di accesso a ogni impostazione che puoi modificare per **aspose document loading**. Ti permette di:

1. **Specify a custom `FontSettings`** – utile quando la tua app fornisce i propri font.  
2. **Attach a warning callback** – esattamente quello che abbiamo fatto per intercettare le sostituzioni dei font.  
3. Controllare il rilevamento del formato del documento, la gestione delle password e altro ancora.

Poiché `LoadOptions` viene passato al costruttore `Document`, le impostazioni vengono applicate **una sola volta**, proprio nel momento in cui il file viene analizzato. Per questo possiamo garantire che il nostro gestore di avvisi vedrà ogni sostituzione prima che il documento sia costruito in memoria.

### Quando usare un LoadOptions personalizzato

- **Batch processing** di molti file in cui desideri una strategia di logging uniforme.  
- **Cloud services** che devono segnalare i font mancanti al chiamante.  
- **Testing pipelines** che verificano che i documenti rispettino una politica aziendale sui font.

---

## Configurare FontSettings per la sostituzione dei font Aspose

L'oggetto `FontSettings` controlla come Aspose.Words risolve i font. Per impostazione predefinita cerca nelle cartelle dei font di sistema, poi ricade sui sostituti integrati. Puoi affinare questo comportamento:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Queste righe sono opzionali per lo scenario base di “set warning callback aspose”, ma illustrano come puoi **ridurre** il numero di avvisi di sostituzione fornendo in anticipo i font corretti.

---

## Implementare IWarningCallback per gli avvisi di sostituzione dei font

L'interfaccia `IWarningCallback` è minuscola—solo un metodo `Warning`. Tuttavia ti offre **pieno controllo** su come gestire gli avvisi:

- **Log to a file** invece della console.  
- **Collect warnings** in una lista per analisi successive.  
- **Throw exceptions** per avvisi critici (ad esempio quando un font richiesto è mancante).

Ecco un esempio rapido che memorizza gli avvisi in una `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Puoi quindi ispezionare `handler.Messages` dopo aver caricato il documento per decidere se interrompere l'elaborazione.

---

## Caricare un documento con gestione personalizzata degli avvisi (flusso completo)

Mettendo tutto insieme, il modello finale che probabilmente riutilizzerai è il seguente:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Questo snippet dimostra il flusso di **aspose document loading** che utilizzerai in produzione: configurare, caricare, poi reagire. Il modello scala agevolmente sia che tu stia elaborando un singolo file sia che tu stia iterando su migliaia di documenti.

---

## Domande frequenti & casi limite

**E se il documento è protetto da password?**  
Aggiungi `Password = "secret"` all'inizializzatore `LoadOptions`. Il callback degli avvisi funziona comunque una volta che il file è stato decrittato.

**Il callback si attiva per altri tipi di avviso?**  
Sì—`WarningInfo.Type` può essere `DocumentStructure`, `UnsupportedFileFormat`, ecc. Nel nostro esempio filtriamo per `FontSubstitution`, ma puoi registrare tutto rimuovendo il controllo `if`.

**Questo influisce sulle prestazioni?**  
Trascurabilmente. Il callback viene invocato solo quando si verifica un avviso, molto meno frequentemente rispetto alle normali fasi di parsing.

**Posso disabilitare completamente la sostituzione dei font?**  
Puoi impostare `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;` ma allora Aspose.Words lancerà un'eccezione per i font mancanti invece di sostituirli.

---

## Conclusione

Ora sai esattamente come **set warning callback aspose** per monitorare gli eventi di sostituzione dei font durante l'elaborazione con **Aspose.Words LoadOptions**. Configurando `FontSettings`, implementando un leggero `IWarningCallback` e caricando il documento con queste opzioni, ottieni piena visibilità su qualsiasi modifica ai font effettuata da Aspose dietro le quinte.  

Da qui potresti:

- Estendere il gestore di avvisi per scrivere su un servizio di logging centrale.  
- Combinare il callback con una strategia personalizzata di fallback dei font.  
- Utilizzare il modello quando costruisci un'API cloud che valida i documenti caricati dai client.

Provalo con i tuoi file DOCX, modifica i `FontSettings` e osserva la console che ti indica esattamente quali font sono stati sostituiti. Buon coding, e che i tuoi documenti vengano sempre visualizzati come previsto!

## Tutorial correlati

- [Catturare gli avvisi di sostituzione dei font in Java con Aspose.Words – Guida completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Abilitare gli avvisi di sostituzione dei font in Aspose.Words – Guida completa](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Come impostare LoadOptions in Aspose.Words per Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}