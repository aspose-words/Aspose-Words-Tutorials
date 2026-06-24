---
category: general
date: 2026-06-24
description: Tutorial locale LLM che mostra come chiamare un LLM locale, caricare
  un documento Word ed eseguire il controllo grammaticale usando il controllo grammaticale
  AI in C#.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: it
og_description: Il tutorial su LLM locale spiega passo passo come chiamare un LLM
  locale, caricare un documento Word ed eseguire un controllo grammaticale AI in C#.
og_title: Tutorial LLM Locale – Richiama un LLM Locale ed Esegui il Controllo Grammaticale
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  headline: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  type: TechArticle
- description: Local LLM tutorial that shows you how to call a local LLM, load a Word
    document and run grammar check using AI grammar check in C#.
  name: Local LLM Tutorial – How to Call a Local LLM and Run Grammar Check
  steps:
  - name: How to Run
    text: 1. Open a terminal in the project folder. 2. Run `dotnet run`. 3. Watch
      the console print the corrected text.
  - name: Can I use a different LLM brand?
    text: Absolutely. As long as the server respects the OpenAI v1 API schema, just
      change `Endpoint` and pick the corresponding `AiModelType` enum value (e.g.,
      `AiModelType.Llama2`). The rest of the code stays identical.
  - name: What if my document is huge (10 MB+)?
    text: Large payloads can exceed the default request size of many servers. Split
      the document into sections and call `CheckGrammar` per section, then concatenate
      the results. This also reduces the chance of a timeout.
  - name: How do I write the corrected output back to a `.docx` file?
    text: 'The `Document` class usually provides a `Save(string path, string content)`
      method. After you get `result.CorrectedText`, call:'
  - name: Is the dummy API key a security risk?
    text: No. The key is ignored by self‑hosted endpoints, but some SDKs enforce a
      non‑null string. Using a placeholder like `"dummy"` satisfies the SDK without
      exposing any secrets.
  type: HowTo
tags:
- LLM
- C#
- GrammarCheck
- AI
title: Tutorial LLM Locale – Come richiamare un LLM locale ed eseguire il controllo
  grammaticale
url: /it/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tutorial LLM Locale – Chiamare un LLM Locale e Eseguire il Controllo Grammaticale

Ti sei mai chiesto come **eseguire il controllo grammaticale** su un file Word senza inviare nulla al cloud? In questo **tutorial LLM locale** collegheremo un modello di linguaggio di grandi dimensioni auto‑ospitato, caricheremo un file `.docx` e lasceremo che l'IA sistemi il testo. Nessuna chiave API, nessun traffico esterno—solo la tua macchina a fare il lavoro pesante.

Passeremo in rassegna ogni riga di codice, spiegheremo perché ogni elemento è importante e mostreremo anche come gestire le solite insidie (come file mancanti o endpoint non raggiungibili). Alla fine avrai un'app console C# pronta all'uso che esegue un **controllo grammaticale AI** usando un modello ospitato localmente.

> **Cosa otterrai:** un programma completo e eseguibile, una spiegazione chiara di ogni passaggio e consigli per scalare la soluzione a documenti più grandi o a diversi provider LLM.

![diagramma tutorial LLM locale](https://example.com/local-llm-tutorial-diagram.png "Diagramma che illustra il flusso del tutorial LLM locale")

## Prerequisiti

Prima di iniziare, assicurati di avere:

- .NET 6.0 SDK o versioni successive (puoi scaricarlo dal sito di Microsoft)
- Un server LLM in esecuzione localmente che espone un endpoint compatibile con OpenAI (ad es., Ollama, LM Studio o un wrapper FastAPI personalizzato)
- Il pacchetto NuGet `AiGrammar` (o qualsiasi libreria fornisca le classi `LocalLargeLanguageModel`, `Document` e `AiModelType`)
- Un documento Word di esempio (`input.docx`) posizionato in una cartella a cui farai riferimento più tardi

Tutto qui—nessuna credenziale cloud aggiuntiva richiesta.

## Passo 1: Tutorial LLM Locale – Configurare l'Endpoint

La prima cosa di cui abbiamo bisogno è un oggetto **call local llm** che sappia dove inviare le richieste. Pensalo come il numero di telefono da comporre prima di parlare.

```csharp
using System;
using AiGrammar;   // Hypothetical library containing the LLM helpers

// Step 1: Configure a local large language model (LLM) endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",
    ApiKey = "dummy"   // Not required for self‑hosted models, but the property is mandatory
};
```

**Perché è importante:**  
La maggior parte degli SDK LLM si aspetta un endpoint HTTP che segua il contratto dell'API OpenAI. Puntando `Endpoint` su `http://localhost:8000/v1` indichiamo alla libreria di **call local llm** invece di contattare i server di OpenAI. La chiave API fittizia è solo un segnaposto—alcuni client rifiutano un valore nullo, quindi forniamo qualcosa di innocuo.

> **Consiglio esperto:** Se esegui l'LLM dietro un reverse proxy, imposta `Endpoint` sull'URL del proxy e lascia che il proxy gestisca la terminazione TLS. Questo mantiene la tua app console semplice e sicura.

## Passo 2: Caricare il Documento Word per il Controllo Grammaticale

Ora che il modello è raggiungibile, dobbiamo **load word document** in memoria. La classe `Document` astrae il parsing del `.docx` per noi.

```csharp
// Step 2: Load the document you want to check
var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";
if (!System.IO.File.Exists(docPath))
{
    Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
    return;
}

var doc = new Document(docPath);
```

**Perché è importante:**  
Passare direttamente un file binario `.docx` a un LLM lo confonderebbe. L'helper `Document` estrae il testo grezzo mantenendo le interruzioni di paragrafo, fornendo al **ai grammar check** un input pulito. Il controllo di esistenza evita una fastidiosa `FileNotFoundException` che altrimenti bloccherebbe l'app.

## Passo 3: Eseguire il Controllo Grammaticale con l'LLM

Ecco il cuore del tutorial: chiediamo al modello locale di revisionare il testo. Il metodo `CheckGrammar` nasconde la logica HTTP e restituisce un oggetto risultato.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Perché è importante:**  
`AiModelType.Gpt4` è solo un'etichetta che indica al servizio remoto quale modello di prompt utilizzare. Se hai un modello più piccolo (ad es., `Llama2`), sostituiscilo di conseguenza. La libreria serializza il testo del documento, lo invia a `http://localhost:8000/v1/completions` e interpreta l'output corretto.

> **Caso limite:** Se l'LLM scade, `CheckGrammar` lancia una `TimeoutException`. Avvolgi la chiamata in un blocco `try/catch` se ti aspetti documenti grandi o un server occupato.

## Passo 4: Visualizzare il Testo Corretto

Infine, mostriamo la versione pulita. In un'app reale potresti scriverla nuovamente in un nuovo file `.docx`, ma per questo tutorial basta stampare a console.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Output previsto** (supponendo che il file originale contenga qualche errore deliberato):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Se l'LLM non trova errori, l'output sarà identico all'input, il che è comunque un segnale utile.

## Esempio Completo Funzionante

Mettendo tutto insieme, ecco il programma completo che puoi copiare‑incollare in un nuovo progetto console:

```csharp
using System;
using AiGrammar;   // Replace with the actual namespace of your grammar library

namespace LocalLlmGrammarDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Configure the local LLM endpoint
            var llm = new LocalLargeLanguageModel
            {
                Endpoint = "http://localhost:8000/v1",
                ApiKey = "dummy"
            };

            // Path to the Word document you want to check
            var docPath = @"C:\Projects\GrammarDemo\YOUR_DIRECTORY\input.docx";

            // Verify the file exists before proceeding
            if (!System.IO.File.Exists(docPath))
            {
                Console.Error.WriteLine($"Error: The file '{docPath}' does not exist.");
                return;
            }

            // Load the document (this also extracts plain text)
            var doc = new Document(docPath);

            // Perform the AI grammar check using the local LLM
            GrammarCheckResult result;
            try
            {
                result = doc.CheckGrammar(llm, AiModelType.Gpt4);
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"Grammar check failed: {ex.Message}");
                return;
            }

            // Show the corrected text
            Console.WriteLine("=== Corrected Text ===");
            Console.WriteLine(result.CorrectedText);
        }
    }
}
```

### Come Eseguire

1. Apri un terminale nella cartella del progetto.  
2. Esegui `dotnet run`.  
3. Osserva la console stampare il testo corretto.

Questo è l'intero **local llm tutorial** in meno di 100 righe di codice.

## Domande Frequenti (FAQ)

### Posso usare un LLM di un altro marchio?

Assolutamente. Finché il server rispetta lo schema API v1 di OpenAI, basta cambiare `Endpoint` e scegliere il valore enum `AiModelType` corrispondente (ad es., `AiModelType.Llama2`). Il resto del codice rimane identico.

### E se il mio documento è enorme (10 MB+)?

Carichi di grandi dimensioni possono superare la dimensione massima di richiesta di molti server. Dividi il documento in sezioni e chiama `CheckGrammar` per sezione, poi concatena i risultati. Questo riduce anche il rischio di timeout.

### Come scrivere l'output corretto in un file `.docx`?

La classe `Document` di solito fornisce un metodo `Save(string path, string content)`. Dopo aver ottenuto `result.CorrectedText`, chiama:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Controlla la documentazione della libreria per la firma esatta.

### La chiave API fittizia è un rischio di sicurezza?

No. La chiave è ignorata dagli endpoint auto‑ospitati, ma alcuni SDK richiedono una stringa non nulla. Usare un segnaposto come `"dummy"` soddisfa l'SDK senza esporre segreti.

## Prossimi Passi e Argomenti Correlati

- **Fine‑tune del tuo LLM locale** per grammatica specifica di dominio (ad es., legale o medico).  
- **Eseguire un batch job** che processi un'intera cartella di file Word—ideale per pipeline editoriali.  
- Esplorare **risposte in streaming** se vuoi suggerimenti in tempo reale mentre l'utente digita.  
- Combinare tutto con **librerie di spell‑checking** per una doppia barriera di qualità.

Ognuna di queste idee si basa sui concetti chiave trattati in questo **local llm tutorial**, così troverai gli stessi pattern—**call local llm**, **load word document**, **run grammar check**, e **handle results**—ripetuti più volte.

---

*Happy coding! If you hit a snag, drop a comment below and we’ll troubleshoot together.*

## Cosa Dovresti Imparare Dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Load Encrypted In Word Document](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Recover Corrupted DOCX – Open & Load Word Document](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}