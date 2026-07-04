---
category: general
date: 2026-04-28
description: Connetti al LLM locale da C# e chiedi al modello di linguaggio di caricare
  un documento Word, chiama l'LLM locale e riscrivi il testo automaticamente. Codice
  passo‑passo incluso.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: it
og_description: Connettiti a un LLM locale da C#, scopri come interagire con un modello
  di linguaggio di grandi dimensioni, caricare un documento Word, chiamare l'LLM locale
  e riscrivere il testo automaticamente in pochi minuti.
og_title: Connetti al LLM locale in C# – Guida completa di programmazione
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Connettersi a LLM locale in C# – Guida completa alla programmazione
url: /it/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Connettersi a LLM locale in C# – Guida completa di programmazione

Hai mai avuto bisogno di **connect to local llm** da un'app .NET e ti sei chiesto come farla parlare con un file Word? Non sei solo. In questa guida percorreremo l'intero processo—connect to local llm, **prompt large language model**, caricare un documento Word, **call local llm**, e infine **rewrite text automatically**. Alla fine avrai un esempio eseguibile che trasforma qualsiasi paragrafo in un tono formale senza chiavi API esterne.

## Cosa copre questo tutorial

Inizieremo installando i pacchetti NuGet necessari, poi avvieremo un semplice endpoint LLM locale (pensa a Ollama sulla porta 11434). Successivamente caricheremo un file `.docx` usando Aspose.Words, invieremo un paragrafo al LLM, riceveremo una versione riscritta e la scriveremo nuovamente nello stesso documento. Vedrai anche come gestire le problematiche comuni—paragrafi null, disposal asincrono e stranezze di codifica—così il codice funziona in produzione, non solo in una demo.

### Prerequisiti

- .NET 6.0 SDK o versioni successive (puoi anche usare .NET 8 se preferisci)
- Visual Studio 2022 o VS Code con estensione C#
- **Aspose.Words for .NET** (la versione di prova gratuita funziona bene)
- Un LLM ospitato localmente che supporta il contratto `/api/generate` (ad es., Ollama, LMStudio)
- Familiarità di base con async/await in C#

> **Consiglio professionale:** Se non hai ancora installato Ollama, esegui `ollama serve` e scarica un modello con `ollama pull llama3`. L'endpoint HTTP predefinito sarà `http://localhost:11434/api/generate`.

---

## Passo 1: Installa i pacchetti richiesti

Per prima cosa, aggiungi i pacchetti NuGet Aspose.Words e Aspose.Words.AI al tuo progetto.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Queste librerie ci forniscono la funzionalità di **load word document** e un wrapper leggero per **call local llm** senza dover creare manualmente richieste HTTP.

---

## Passo 2: Connettersi all'endpoint LLM locale

Connettersi a un modello ospitato localmente è semplice come istanziare `LocalLargeLanguageModel`. Il costruttore si aspetta l'URL completo dell'endpoint di generazione.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Perché avvolgiamo l'endpoint in una classe? `LocalLargeLanguageModel` gestisce la serializzazione JSON, i retry e le risposte in streaming per te—così puoi concentrarti sulla logica del prompt invece di armeggiare con `HttpClient`.

---

## Passo 3: Caricare il documento Word sorgente

Successivamente, carichiamo il documento in memoria. Aspose.Words supporta praticamente tutti i formati Word, quindi `Document` analizzerà `input.docx` senza necessità di avere Office installato.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Se devi lavorare con uno stream (ad es., un file caricato tramite ASP.NET), basta sostituire il percorso del file con un `MemoryStream` e passarlo al costruttore `Document`.

---

## Passo 4: Estrarre il testo del paragrafo corrente

Useremo `DocumentBuilder` per navigare nel documento. In questo esempio riscriviamo **il primo paragrafo**, ma puoi iterare su `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` per elaborarne molti.

```csharp
// Builder gives us a cursor inside the document
DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);

// Grab the text of the paragraph where the builder is currently positioned
string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

// Safety check – avoid sending empty strings to the LLM
if (string.IsNullOrWhiteSpace(originalParagraph))
{
    Console.WriteLine("No paragraph found at the current cursor position.");
    return;
}
```

L'operatore `?.` previene una `NullReferenceException` se il documento dovesse essere vuoto. Questo è uno di quegli **edge cases** che confondono i principianti.

---

## Passo 5: Promptare il LLM per riscrivere il paragrafo

Ora effettivamente **prompt large language model**. Il prompt è in inglese semplice; il wrapper lo invierà come JSON all'endpoint locale.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Perché formulare la richiesta in questo modo? I LLM rispondono meglio a istruzioni chiare e a compito unico. Aggiungere una nuova riga dopo i due punti separa l'istruzione dal contenuto, riducendo la probabilità che il modello ripeta il prompt.

**Output atteso** – Se `originalParagraph` era `"Hey, what's up?"`, il LLM potrebbe restituire:

> “Good day, how may I assist you?”

Puoi verificare il risultato stampandolo:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Passo 6: Inserire il testo riscritto nuovamente nel documento

Con il nuovo testo a disposizione, sostituiamo il vecchio paragrafo. `DocumentBuilder.Writeln` scrive una nuova riga e sposta il cursore in avanti, perfetto per aggiungere. Se devi *sostituire* esattamente lo stesso paragrafo, puoi usare `docBuilder.CurrentParagraph.RemoveAllChildren()` prima di scrivere.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Entrambi gli approcci sono mostrati così puoi scegliere quello che si adatta al tuo flusso di lavoro.

---

## Passo 7: Salvare il documento aggiornato

Infine, salviamo le modifiche in un nuovo file. Aspose.Words sceglie automaticamente il formato in base all'estensione del file.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Apri `output.docx` in Word e vedrai che il paragrafo ora è scritto in tono formale.

---

## Esempio completo funzionante

Di seguito trovi il **programma completo e autonomo**. Copialo e incollalo in un progetto console, ripristina i pacchetti NuGet ed eseguilo—non è necessaria alcuna configurazione aggiuntiva oltre a un LLM locale in esecuzione.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System;
using System.IO;
using System.Threading.Tasks;

class Program
{
    static async Task Main()
    {
        // -------------------------------------------------
        // Step 1: Connect to the locally hosted LLM endpoint
        // -------------------------------------------------
        var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");

        // -------------------------------------------------
        // Step 2: Load the source Word document
        // -------------------------------------------------
        string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");
        Document sourceDocument = new Document(inputPath);

        // -------------------------------------------------
        // Step 3: Retrieve the text of the current paragraph
        // -------------------------------------------------
        DocumentBuilder docBuilder = new DocumentBuilder(sourceDocument);
        string originalParagraph = docBuilder.CurrentParagraph?.GetText() ?? string.Empty;

        if (string.IsNullOrWhiteSpace(originalParagraph))
        {
            Console.WriteLine("No paragraph found at the current cursor position.");
            return;
        }

        // -------------------------------------------------
        // Step 4: Ask the LLM to rewrite the paragraph in a formal tone
        // -------------------------------------------------
        string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";
        string rewrittenParagraph = await localLlm.PromptAsync(prompt);

        // -------------------------------------------------
        // Step 5: Insert the rewritten text back into the document
        // -------------------------------------------------
        docBuilder.Writeln(rewrittenParagraph);

        // -------------------------------------------------
        // Step 6: Save the updated document
        // -------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
        sourceDocument.Save(outputPath);

        Console.WriteLine("Original paragraph:");
        Console.WriteLine(originalParagraph);
        Console.WriteLine("\nRewritten paragraph:");
        Console.WriteLine(rewrittenParagraph);
        Console.WriteLine($"\nDocument saved to {outputPath}");
    }
}
```

### Cosa aspettarsi quando lo esegui

1. La console stampa i paragrafi originali e riscritti.  
2. `output.docx` appare accanto a `input.docx`.  
3. Aprendo il file si vede il nuovo paragrafo formale inserito dopo l'originale (o sostituito, se hai usato il codice alternativo).

---

## Gestire i casi limite comuni

| Situation | Solution |
|-----------|----------|
| **Paragrafo vuoto o composto solo da spazi** | Verifica `string.IsNullOrWhiteSpace` prima di fare il prompt (vedi Passo 3). |
| **Il LLM restituisce un errore o una stringa vuota** | Avvolgi `PromptAsync` in un `try/catch` e ricorri al testo originale. |
| **Più paragrafi necessitano di riscrittura** | Itera su `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` e applica la stessa logica di prompt. |
| **Documenti grandi causano latenza** | Raggruppa i paragrafi e inviali in una singola richiesta (prompt fino a 4 KB per chiamata). |
| **Caratteri non ASCII vengono corrotti** | Assicurati che l'endpoint LLM utilizzi UTF-8 (la maggior parte dei modelli moderni lo fa). |

---

## Prossimi passi e argomenti correlati

- **Prompt large language model** con istruzioni più ricche (ad es., guide di stile, limiti di lunghezza).  
- Usa **call local llm** in una web API per esporre l'automazione dei documenti come servizio.  
- Esplora **load word document** in stream paralleli per scenari ad alta velocità.  
- Combina questo approccio con **rewrite text automatically** per generare email di massa o standardizzare report.  

Se vuoi approfondire, consulta la documentazione di Aspose su **document merging** e il riferimento API di Ollama per parametri di campionamento personalizzati.

---

## Conclusione

Ti abbiamo appena mostrato come **connect to local llm** da C#, **prompt large language model**, **load word document**, **call local llm**, e **rewrite text automatically**—tutto in una singola app console eseguibile. Il modello è scalabile: cambia il prompt, itera sui paragrafi o espone la logica tramite un endpoint ASP.NET. Il punto chiave è che i modelli AI locali possono essere strettamente integrati con le librerie classiche di elaborazione documenti, offrendoti un'automazione potente senza mai uscire dal tuo ambiente on‑prem di fiducia.

Hai domande sul threading,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}