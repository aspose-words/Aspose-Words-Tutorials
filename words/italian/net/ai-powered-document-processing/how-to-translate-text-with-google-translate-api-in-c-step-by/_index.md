---
category: general
date: 2026-11-15
description: Impara a tradurre il testo con Google in C#. Questo tutorial mostra un
  esempio di Google Translate, gestendo più lingue e le migliori pratiche.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: it
lastmod: 2026-11-15
og_description: Come tradurre testo con Google in C# usando un esempio completo di
  Google Translate. Segui questo tutorial per tradurre più lingue in modo sicuro.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Come tradurre il testo con l'API di Google Translate in C# – tutorial rapido
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  headline: How to translate text with Google Translate API in C# – step‑by‑step guide
  type: TechArticle
- description: Learn how to translate text with Google in C#. This tutorial shows
    a Google Translate example, handling multiple languages and best practices.
  name: How to translate text with Google Translate API in C# – step‑by‑step guide
  steps:
  - name: Prerequisites
    text: '* .NET 6.0 SDK or later (the code compiles with .NET Core and .NET Framework).
      * A Google Cloud account with the **Cloud Translation API** enabled. * Basic
      familiarity with C# and console applications.'
  - name: Handling language detection
    text: 'If you need to know the source language, the response object contains `DetectedSourceLanguage`:'
  - name: Translating large documents
    text: The API supports up to 30 KB per request. For larger texts, split the content
      into chunks, translate each chunk, and then concatenate the results. Keep sentence
      boundaries intact to avoid awkward phrasing.
  - name: Rate‑limiting and quotas
    text: Google enforces per‑minute request limits. Implement a retry policy with
      exponential back‑off to respect quota limits and avoid `429 Too Many Requests`
      errors.
  type: HowTo
- questions:
  - answer: Yes. Use the `Format` parameter (`"text"` or `"html"`) when calling `TranslateText`.
      The SDK exposes this via the `TranslateText` overload that accepts a `TranslateTextRequest`.
    question: Can I translate a whole HTML page?
  - answer: The API returns an error. Validate language codes against the list returned
      by `client.ListSupportedLanguages()` before making a request.
    question: What if a language isn’t supported?
  - answer: 'Google bills per character translated. Estimate costs using the pricing
      page and consider caching frequent translations. --- ## Conclusion You now know
      **how to translate text** in C# using the official Google Translate API. The
      tutorial covered a **Google translate example**, demonstrated **transla'
    question: Does the API charge per character?
  type: FAQPage
tags:
- Google Cloud
- C#
- Translation API
title: Come tradurre testo con l'API di Google Translate in C# – guida passo passo
url: /it/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come tradurre testo con l'API Google Translate in C# – guida passo‑passo

Se hai bisogno di **come tradurre testo** in un'applicazione .NET, l'API Google Cloud Translation offre una soluzione affidabile e indipendente dalla lingua. In questo tutorial vedrai un **esempio di Google Translate** che traduce una stringa semplice, si espande per **tradurre più lingue**, e segue le migliori pratiche per le chiavi API e la gestione degli errori.

Avrai a disposizione un programma console C# pronto all'uso, una chiara comprensione di **tradurre testo con Google**, e la fiducia per adattare il codice a progetti più grandi.

## Cosa copre questo tutorial

* Impostare un progetto Google Cloud e ottenere una chiave API.  
* Installare il pacchetto NuGet `Google.Cloud.Translation.V2`.  
* Scrivere codice pulito e riutilizzabile che **come tradurre testo** usando l'SDK ufficiale.  
* Estendere la soluzione per **tradurre più lingue** in una singola chiamata.  
* Problemi comuni e consigli per implementazioni di livello produzione.

### Prerequisiti

* .NET 6.0 SDK o successivo (il codice si compila con .NET Core e .NET Framework).  
* Un account Google Cloud con l'**API Cloud Translation** abilitata.  
* Familiarità di base con C# e le applicazioni console.  

---

## Passo 1: Installa la libreria client Google Cloud Translation

La libreria client ufficiale astrae le chiamate HTTP e gestisce l'autenticazione per te.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Eseguendo il comando si aggiunge il pacchetto `Google.Cloud.Translation.V2` al tuo progetto, fornendoti l'accesso alla classe `TranslationClient` usata in tutta questa guida.

> **Perché questo passo è importante** – Usare l'SDK evita la costruzione manuale delle richieste, riduce i bug e garantisce che tu sia allineato con l'ultima versione dell'API di Google.

## Passo 2: Crea un helper di traduzione riutilizzabile

Incapsulare la logica di traduzione in una classe statica rende il codice riutilizzabile e isola la gestione della chiave API.

```csharp
using Google.Cloud.Translation.V2;
using System;

namespace GoogleTranslateDemo
{
    /// <summary>
    /// Provides simple methods to translate text using the Google Cloud Translation API.
    /// </summary>
    public static class Translator
    {
        /// <summary>
        /// Translates a single string into the specified target language.
        /// </summary>
        /// <param name="sourceText">The text you want to translate.</param>
        /// <param name="targetLanguage">ISO‑639‑1 language code (e.g., "fr" for French).</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>The translated text.</returns>
        public static string Translate(string sourceText, string targetLanguage, string apiKey)
        {
            // Initialise the client with the provided API key.
            var client = TranslationClient.CreateFromApiKey(apiKey);

            // Perform the translation. The API automatically detects the source language.
            var response = client.TranslateText(sourceText, targetLanguage);
            return response.TranslatedText;
        }

        /// <summary>
        /// Translates a collection of texts into several languages at once.
        /// </summary>
        /// <param name="sourceTexts">Array of strings to translate.</param>
        /// <param name="targetLanguages">Array of ISO‑639‑1 codes (e.g., "es", "de").</param>
        /// <param name="apiKey">Your Google Cloud API key.</param>
        /// <returns>A dictionary keyed by language code containing the translated results.</returns>
        public static Dictionary<string, string[]> TranslateMultiple(string[] sourceTexts,
                                                                    string[] targetLanguages,
                                                                    string apiKey)
        {
            var client = TranslationClient.CreateFromApiKey(apiKey);
            var result = new Dictionary<string, string[]>();

            foreach (var lang in targetLanguages)
            {
                var translations = client.TranslateTexts(sourceTexts, lang);
                result[lang] = translations.Select(t => t.TranslatedText).ToArray();
            }

            return result;
        }
    }
}
```

> **Perché restituiamo un dizionario** – Quando hai bisogno di **tradurre più lingue**, organizzare i risultati per codice lingua rende il processamento successivo più semplice.

## Passo 3: Costruisci l'applicazione console che utilizza l'helper

Di seguito è presente un completo `Program.cs` che dimostra sia la traduzione di un singolo testo sia una traduzione batch.

```csharp
using System;
using GoogleTranslateDemo; // Namespace from the helper class

class Program
{
    static void Main()
    {
        // ---- Single translation (Google Translate example) ----
        string sourceText = "Hello, world!";
        string targetLanguage = "fr"; // French
        string apiKey = "YOUR_GOOGLE_API_KEY"; // Replace with your actual key

        try
        {
            string translated = Translator.Translate(sourceText, targetLanguage, apiKey);
            Console.WriteLine($"[Single] English → French: {translated}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Translation failed: {ex.Message}");
        }

        // ---- Translate multiple languages (translate multiple languages) ----
        string[] texts = { "Good morning", "How are you?" };
        string[] languages = { "es", "de", "ja" }; // Spanish, German, Japanese

        try
        {
            var batchResult = Translator.TranslateMultiple(texts, languages, apiKey);
            foreach (var kvp in batchResult)
            {
                Console.WriteLine($"\n[Batch] Language: {kvp.Key}");
                for (int i = 0; i < texts.Length; i++)
                {
                    Console.WriteLine($"  {texts[i]} → {kvp.Value[i]}");
                }
            }
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Batch translation failed: {ex.Message}");
        }
    }
}
```

**Output console previsto**

```
[Single] English → French: Bonjour le monde!

[Batch] Language: es
  Good morning → Buenos días
  How are you? → ¿Cómo estás?

[Batch] Language: de
  Good morning → Guten Morgen
  How are you? → Wie geht es Ihnen?

[Batch] Language: ja
  Good morning → おはようございます
  How are you? → お元気ですか？
```

> **Perché i blocchi try/catch?** – Errori di rete, limiti di quota o una chiave API non valida generano eccezioni. Gestirli in modo appropriato migliora l'esperienza dell'utente e mantiene stabile l'applicazione.

## Passo 4: Metti al sicuro la tua chiave API

Inserire la chiave API nel codice, come mostrato sopra, è accettabile per una demo veloce ma non per la produzione. Segui queste pratiche:

* Memorizza la chiave in una variabile d'ambiente (`GOOGLE_API_KEY`) e leggila a runtime:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Usa le **Google Application Default Credentials** invece di una chiave API quando esegui su Google Cloud (App Engine, Cloud Run, ecc.).
* Limita la chiave all'API Translation nella console Google Cloud e restringi l'uso a indirizzi IP o referenti specifici.

## Passo 5: Estendi la soluzione per scenari reali

### Gestione del rilevamento della lingua

Se hai bisogno di conoscere la lingua di origine, l'oggetto risposta contiene `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Traduzione di documenti di grandi dimensioni

L'API supporta fino a 30 KB per richiesta. Per testi più lunghi, suddividi il contenuto in blocchi, traduci ogni blocco e poi concatena i risultati. Mantieni intatti i confini delle frasi per evitare formulazioni goffe.

### Limitazione della velocità e quote

Google applica limiti di richieste per minuto. Implementa una politica di retry con back‑off esponenziale per rispettare i limiti di quota ed evitare errori `429 Too Many Requests`.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Domande comuni e casi particolari

**Q: Posso tradurre un'intera pagina HTML?**  
A: Sì. Usa il parametro `Format` (`"text"` o `"html"`) quando chiami `TranslateText`. L'SDK espone questo tramite la sovraccarico di `TranslateText` che accetta un `TranslateTextRequest`.

**Q: Cosa succede se una lingua non è supportata?**  
A: L'API restituisce un errore. Convalida i codici lingua rispetto all'elenco restituito da `client.ListSupportedLanguages()` prima di effettuare una richiesta.

**Q: L'API addebita per carattere?**  
A: Google fattura per carattere tradotto. Stima i costi usando la pagina dei prezzi e considera di memorizzare nella cache le traduzioni frequenti.

---

## Conclusione

Ora sai **come tradurre testo** in C# usando l'API ufficiale di Google Translate. Il tutorial ha coperto un **esempio di Google Translate**, ha dimostrato **tradurre più lingue**, e ha evidenziato pratiche pronte per la produzione come la sicurezza della chiave API e la gestione degli errori. Riutilizzando l'helper `Translator`, puoi integrare la traduzione in qualsiasi servizio .NET, applicazione desktop o microservizio.

**Passi successivi**

* Esplora il **Google Translate tutorial** per funzionalità avanzate come glossari e modelli personalizzati.  
* Combina questo codice con ASP.NET Core per creare un'API web multilingue.  
* Sperimenta la traduzione batch di file CSV per automatizzare le pipeline di localizzazione.

Buon coding e divertiti a costruire applicazioni accessibili a livello globale!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [tradurre docx in francese con Aspose.Words e Google API](/words/english/net/ai-powered-document-processing/translate-docx-to-french-with-aspose-words-and-google-api/)
- [Come salvare un documento Word tradotto in C# con Google AI](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)
- [Tradurre stringa in spagnolo in C# con Aspose.Words AI](/words/english/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}