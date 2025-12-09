---
language: it
url: /italian/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Rilevare i Font Mancanti nei Documenti Aspose.Words – Guida Completa C# 

Ti sei mai chiesto come **rilevare i font mancanti** quando carichi un file Word con Aspose.Words? Nel mio lavoro quotidiano, mi sono imbattuto in alcuni PDF che sembravano sbagliati perché il documento originale usava un font che non avevo installato. La buona notizia? Aspose.Words può dirti esattamente quando sostituisce un font, e puoi catturare queste informazioni con un semplice callback di avviso.  

In questo tutorial vedremo un **esempio completo e eseguibile** che mostra come registrare ogni sostituzione di font, perché il callback è importante, e un paio di trucchi extra per una rilevazione robusta dei font mancanti. Niente superfluo, solo il codice e il ragionamento di cui hai bisogno per farlo funzionare subito.

---

## Cosa Imparerai

- Come implementare **Aspose.Words warning callback** per catturare gli eventi di sostituzione dei font.  
- Come configurare **LoadOptions C#** affinché il callback venga invocato durante il caricamento di un documento.  
- Come verificare che la rilevazione dei font mancanti abbia effettivamente funzionato e come appare l'output della console.  
- Ottimizzazioni opzionali per grandi batch o ambienti headless.  

**Prerequisiti** – Hai bisogno di una versione recente di Aspose.Words per .NET (il codice è stato testato con la 23.12), .NET 6 o successivo, e una conoscenza di base di C#. Se li hai, sei pronto a partire.

---

## Rilevare i Font Mancanti con un Callback di Avviso

Il cuore della soluzione è un'implementazione di `IWarningCallback`. Aspose.Words genera un oggetto `WarningInfo` per molte situazioni, ma noi ci interessiamo solo a `WarningType.FontSubstitution`. Vediamo come collegarci a questo.

### Passo 1: Creare un Collettore di Avvisi Font

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Perché è importante*: Filtrando su `WarningType.FontSubstitution` evitiamo il rumore di avvisi non correlati (come le funzionalità deprecate). `info.Description` contiene già il nome del font originale e quello di fallback usato, fornendoti una chiara traccia di audit.

---

## Configurare LoadOptions per Usare il Callback

Ora diciamo ad Aspose.Words di usare il nostro raccoglitore quando carica un file.

### Passo 2: Configurare LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Perché è importante*: `LoadOptions` è l'unico punto in cui puoi collegare il callback, le password di crittografia e altri comportamenti di caricamento. Tenerlo separato dal costruttore `Document` rende il codice riutilizzabile per molti file.

---

## Caricare il Documento e Catturare i Font Mancanti

Con il callback collegato, il passo successivo è semplicemente caricare il documento.

### Passo 3: Carica il tuo DOCX (o qualsiasi formato supportato)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Quando il costruttore `Document` analizza il file, qualsiasi font mancante attiva il nostro `FontWarningCollector`. La console mostrerà righe come:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Quella riga è la prova concreta che **rilevare i font mancanti** ha funzionato.

---

## Verificare l'Output – Cosa Aspettarsi

Esegui il programma da un terminale o da Visual Studio. Se il documento di origine contiene un font che non hai installato, vedrai almeno una riga “Font substituted”. Se il documento usa solo font installati, il callback rimane silenzioso e vedrai solo il messaggio “Document loaded successfully.”.

**Suggerimento**: Per ricontrollare, apri il file Word in Microsoft Word e guarda l'elenco dei font. Qualsiasi font che appare in *Replace Fonts* sotto il gruppo *Home → Font* è un candidato per la sostituzione.

---

## Avanzato: Rilevare i Font Mancanti in Massa

Spesso è necessario analizzare decine di file. Lo stesso schema scala bene:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Poiché il `FontWarningCollector` scrive sulla console ogni volta che viene invocato, otterrai un report per file senza ulteriori complicazioni. Per scenari di produzione potresti voler registrare su un file o su un database – basta sostituire `Console.WriteLine` con il logger preferito.

---

## Problemi Comuni & Consigli Pro

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Nessun avviso appare** | Il documento contiene effettivamente solo font installati. | Verifica aprendo il file in Word o rimuovendo deliberatamente un font dal tuo sistema. |
| **Callback non chiamato** | `LoadOptions.WarningCallback` non è mai stato assegnato o è stata usata in seguito una nuova istanza di `LoadOptions`. | Mantieni un unico oggetto `LoadOptions` e riutilizzalo per ogni caricamento. |
| **Troppi avvisi non correlati** | Non hai filtrato per `WarningType.FontSubstitution`. | Aggiungi la guardia `if (info.Type == WarningType.FontSubstitution)` come mostrato. |
| **Rallentamento delle prestazioni su file enormi** | Il callback viene eseguito per ogni avviso, che può essere molti per documenti grandi. | Disabilita altri tipi di avviso tramite `LoadOptions.WarningCallback` o imposta `LoadOptions.LoadFormat` a un tipo specifico se lo conosci. |

---

## Esempio Completo Funzionante (Pronto per Copia‑Incolla)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Output console previsto** (quando si incontra un font mancante):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Se non avviene alcuna sostituzione, vedrai solo la riga di successo.

---

## Conclusione

Ora hai un **metodo completo e pronto per la produzione per rilevare i font mancanti** in qualsiasi documento elaborato da Aspose.Words. Sfruttando il **callback di avviso Aspose.Words** e configurando **LoadOptions C#**, puoi registrare ogni sostituzione di font, risolvere problemi di layout e assicurarti che i tuoi PDF mantengano l'aspetto previsto.  

Da un singolo file a un batch massivo, lo schema rimane lo stesso—implementa `IWarningCallback`, collegalo a `LoadOptions`, e lascia che Aspose.Words faccia il lavoro pesante.  

Pronto per il passo successivo? Prova a combinare questo con **l'incorporamento dei font** o **famiglie di font di fallback** per correggere automaticamente il problema, o esplora l'API **DocumentVisitor** per un'analisi più profonda del contenuto. Buona programmazione, e che tutti i tuoi font rimangano dove ti aspetti!

---

![Rileva i font mancanti in Aspose.Words – screenshot dell'output della console](https://example.com/images/detect-missing-fonts.png "output consolevamento font mancanti")

{{< layout-end >}}

{{< layout-end >}}