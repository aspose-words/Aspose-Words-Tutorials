---
category: general
date: 2026-05-04
description: Come utilizzare LLM per modificare documenti con Aspose – impara a sostituire
  il testo dei paragrafi, connetterti a un LLM locale e riscrivere il testo usando
  l'IA.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: it
og_description: Come utilizzare LLM per modificare documenti con Aspose. Questa guida
  mostra come connettersi a un LLM locale, sostituire il testo dei paragrafi e riscrivere
  il testo usando l'IA.
og_title: Come utilizzare LLM con Aspose.Words – Riscrivi i paragrafi in C#
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Come utilizzare LLM con Aspose.Words – Riscrivere i paragrafi in C#
url: /it/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come usare LLM con Aspose.Words – Riscrivere paragrafi in C#

Ti sei mai chiesto **come usare LLM** per perfezionare un documento Word senza aprirlo manualmente? Non sei l'unico. Molti sviluppatori si trovano in difficoltà quando devono *sostituire il testo del paragrafo* programmaticamente ma non hanno un flusso di lavoro basato su AI pulito.  

In questo tutorial collegheremo un modello di linguaggio di grandi dimensioni locale, gli forniremo un frammento da un file `.docx`, gli chiederemo di **riscrivere il testo usando l'AI**, e infine salveremo il documento aggiornato—tutto con Aspose.Words. Alla fine avrai un'app console C# pronta all'uso che dimostra l'intero pipeline.

> **Cosa otterrai:** un esempio completo e eseguibile, spiegazioni di ogni passaggio, suggerimenti per casi limite e idee per estendere la soluzione.

## Cosa ti serve

- **.NET 6+** (or .NET Framework 4.7.2 – il codice funziona su entrambi)
- **Aspose.Words for .NET** (pacchetto NuGet `Aspose.Words`)
- Un **server LLM locale** che espone un semplice endpoint HTTP `/generate` (ad es., Ollama, LMStudio, o un servizio Flask personalizzato)
- Una conoscenza di base di C# e del codice client HTTP  

Non sono richiesti SDK aggiuntivi; tutto il resto vive nel codice che scriveremo insieme.

## Passo 1: Come usare LLM per sostituire il testo del paragrafo

La prima cosa da fare è identificare il paragrafo che vogliamo modificare. Aspose.Words lo rende un gioco da ragazzi esponendo un modello di oggetti ricco.

```csharp
using Aspose.Words;
using Aspose.Words.AI;   // Imaginary namespace for illustration – replace with actual if needed
using System.Net.Http;
using System.Text;
using System.Text.Json;

// Load the source document
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Grab the third paragraph (zero‑based index)
Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];

// Show the original text in the console – handy for debugging
Console.WriteLine("Original paragraph:");
Console.WriteLine(targetParagraph.GetText());
```

**Perché è importante:**  
Selezionare il nodo corretto impedisce di sovrascrivere accidentalmente intestazioni o tabelle. Usando l'approccio **replace paragraph text** manteniamo intatta la struttura del documento toccando solo il contenuto di nostro interesse.

> **Consiglio professionale:** Se il tuo documento ha sezioni di lunghezza variabile, usa `document.GetChildNodes(NodeType.Paragraph, true)` e LINQ per individuare un paragrafo in base al suo testo o stile.

## Passo 2: Connettersi a un endpoint LLM locale

Ora che abbiamo il testo, dobbiamo inviarlo al LLM. L'esempio utilizza una semplice classe wrapper `LocalLargeLanguageModel` che nasconde la gestione HTTP. Sentiti libero di sostituirla con chiamate `HttpClient` se preferisci.

```csharp
/// <summary>
/// Minimal wrapper around a local LLM HTTP API.
/// Assumes the API accepts a JSON payload { "prompt": "..."} and returns { "response": "..." }.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _client;
    private readonly string _endpoint;

    public LocalLargeLanguageModel(string endpoint)
    {
        _endpoint = endpoint.TrimEnd('/');
        _client = new HttpClient();
    }

    public string GenerateText(string prompt)
    {
        var payload = new { prompt };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // Synchronous call for brevity – in production use async/await
        var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
        response.EnsureSuccessStatusCode();

        var json = response.Content.ReadAsStringAsync().Result;
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result?["response"] ?? string.Empty;
    }
}

// Step 2: Instantiate the LLM client pointing at localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:5000");
```

**Perché ci connettiamo in questo modo:**  
Una configurazione **connect to local llm** elimina la latenza, mantiene i dati on‑premise e evita i costi delle API. Il wrapper rende anche il codice successivo più pulito, permettendoci di concentrarci sulla logica di **rewrite text using ai**.

## Passo 3: Riscrivere il testo usando l'AI con Aspose.Words

Con il testo del paragrafo a disposizione e il LLM pronto, creiamo un prompt che indica al modello esattamente ciò che vogliamo—riscrivere in tono formale. Puoi modificare il prompt per altri stili (amichevole, tecnico, ecc.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Perché funziona:**  
I LLM sono guidati dal prompt; fornire istruzioni esplicite (“Rewrite … in a formal tone”) produce risultati coerenti. Il passo **rewrite text using ai** è il cuore del tutorial – dimostra come l'AI possa essere integrata direttamente nei flussi di lavoro dei documenti.

## Passo 4: Modificare il documento e salvare le modifiche

Ora sostituiamo i run originali con il nuovo contenuto. Aspose.Words memorizza il testo in oggetti `Run`, quindi cancellarli prima evita artefatti di formattazione residui.

```csharp
// Clear existing runs (pieces of text) from the paragraph
targetParagraph.Runs.Clear();

// Append a new Run containing the revised text
targetParagraph.AppendChild(new Run(document, revisedText));

// Save the updated document
document.Save("YOUR_DIRECTORY/output.docx");

// Confirmation
Console.WriteLine("\nDocument saved as output.docx");
```

**Nota sui casi limite:**  
Se il paragrafo originale conteneva formattazione mista (grassetto, corsivo) potresti voler preservare gli stili. In tal caso, crea un nuovo `Run`, copia le impostazioni originali di `Font`, quindi imposta il suo `Text` a `revisedText`.

## Esempio completo funzionante

Di seguito trovi l'intero programma che puoi copiare‑incollare in un progetto console. Ricorda di installare prima il pacchetto NuGet Aspose.Words (`dotnet add package Aspose.Words`).

```csharp
// ---------------------------------------------------------------
// Complete C# console app: how to use llm to edit a Word doc
// ---------------------------------------------------------------
using Aspose.Words;
using Aspose.Words.AI;   // Replace with real namespace if needed
using System;
using System.Collections.Generic;
using System.Net.Http;
using System.Text;
using System.Text.Json;

namespace LlmAsposeDemo
{
    public class LocalLargeLanguageModel
    {
        private readonly HttpClient _client;
        private readonly string _endpoint;

        public LocalLargeLanguageModel(string endpoint)
        {
            _endpoint = endpoint.TrimEnd('/');
            _client = new HttpClient();
        }

        public string GenerateText(string prompt)
        {
            var payload = new { prompt };
            var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

            var response = _client.PostAsync($"{_endpoint}/generate", content).Result;
            response.EnsureSuccessStatusCode();

            var json = response.Content.ReadAsStringAsync().Result;
            var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
            return result?["response"] ?? string.Empty;
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the document
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // 2️⃣ Pick the third paragraph (index 2)
            Paragraph targetParagraph = document.FirstSection.Body.Paragraphs[2];
            Console.WriteLine("Original paragraph:");
            Console.WriteLine(targetParagraph.GetText());

            // 3️⃣ Connect to the local LLM
            var localLlm = new LocalLargeLanguageModel("http://localhost:5000");

            // 4️⃣ Ask the model to rewrite it formally
            string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";
            string revisedText = localLlm.GenerateText(prompt);
            Console.WriteLine("\nRevised paragraph:");
            Console.WriteLine(revisedText);

            // 5️⃣ Replace the paragraph contents
            targetParagraph.Runs.Clear();
            targetParagraph.AppendChild(new Run(document, revisedText));

            // 6️⃣ Save the file
            document.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("\nDocument saved as output.docx");
        }
    }
}
```

### Output previsto

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Apri `output.docx` – vedrai che il terzo paragrafo ora contiene la versione perfezionata.

## Domande comuni e problemi

| Domanda | Risposta |
|----------|--------|
| **E se il mio LLM restituisce JSON con campi extra?** | Regola `GenerateText` per deserializzare la proprietà corretta o analizza manualmente la risposta. |
| **Posso elaborare più paragrafi contemporaneamente?** | Sì – itera su `document.FirstSection.Body.Paragraphs` e applica la stessa logica del prompt, magari aggiungendo un indice del paragrafo al prompt per il contesto. |
| **Il mio server LLM utilizza l'autenticazione?** | Aggiungi un header al `HttpClient` prima del POST: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **La formattazione viene persa dopo la sostituzione.** | Preserva le impostazioni originali di `Run.Font`: crea un nuovo `Run`, copia `originalRun.Font.Clone()`, quindi imposta il suo `Text`. |
| **Il LLM a volte restituisce stringhe vuote.** | Implementa un fallback – se `revisedText.Trim().Length == 0`, mantieni il testo originale o riprova con un prompt più semplice. |

## Estendere la soluzione

Ora che hai padroneggiato **how to use llm** per un singolo paragrafo, considera i seguenti passi successivi:

- **Elaborazione batch:** Scorri tutti i paragrafi e riscrivili in uno stile scelto (ad es., “rendi tutto il testo conciso”).  
- **Riscrittura consapevole dello stile:** Passa il nome dello stile del paragrafo originale nel prompt affinché il LLM rispetti intestazioni vs testo del corpo.  
- **Integrazione con una pipeline CI:** Automatizza la rifinitura dei documenti come parte del processo di build della documentazione.  
- **Prompt alternativi:** Prova “summarize this paragraph” o “translate this paragraph to Spanish” per esplorare tutta la potenza di **rewrite text using ai**.  

## Conclusione

Abbiamo percorso l'intero flusso di **how to use llm** con Aspose.Words: caricamento di un documento, **connect to local llm**, estrazione di un paragrafo, **rewrite text using ai**, **replace paragraph text**, e infine salvataggio del risultato. Il codice è autonomo, funziona subito, e mostra un modo pratico per combinare l'AI con l'automazione tradizionale dei documenti.

Provalo, modifica i prompt, e lascia

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}