---
category: general
date: 2026-11-15
description: Erfahren Sie, wie Sie Text mit Google in C# übersetzen. Dieses Tutorial
  zeigt ein Google‑Translate‑Beispiel, behandelt mehrere Sprachen und bewährte Verfahren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to translate text
- translate text with google
- google translate example
- google translate tutorial
- translate multiple languages
language: de
lastmod: 2026-11-15
og_description: Wie man Text mit Google in C# übersetzt, anhand eines vollständigen
  Google‑Translate‑Beispiels. Folgen Sie diesem Tutorial, um mehrere Sprachen sicher
  zu übersetzen.
og_image_alt: Console output showing translated text from English to French using
  Google Translate API
og_title: Wie man Text mit der Google Translate API in C# übersetzt – Schnellkurs
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
title: Wie man Text mit der Google‑Translate‑API in C# übersetzt – Schritt‑für‑Schritt‑Anleitung
url: /de/net/ai-powered-document-processing/how-to-translate-text-with-google-translate-api-in-c-step-by/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Text mit der Google Translate API in C# übersetzt – Schritt‑für‑Schritt‑Anleitung

Wenn Sie in einer .NET‑Anwendung **Text übersetzen** müssen, bietet die Google Cloud Translation API eine zuverlässige, sprachunabhängige Lösung. In diesem Tutorial sehen Sie ein **Google Translate Beispiel**, das einen einfachen String übersetzt, zu **mehreren Sprachen übersetzen** erweitert und bewährte Methoden für API‑Schlüssel und Fehlerbehandlung befolgt.

Sie erhalten ein sofort ausführbares C#‑Konsolenprogramm, ein klares Verständnis von **Textübersetzung mit Google**, und das Vertrauen, den Code für größere Projekte anzupassen.

## Was dieses Tutorial abdeckt

* Einrichten eines Google‑Cloud‑Projekts und Beschaffung eines API‑Schlüssels.  
* Installation des NuGet‑Pakets `Google.Cloud.Translation.V2`.  
* Schreiben von sauberem, wiederverwendbarem Code, der **Text übersetzt** mithilfe des offiziellen SDK.  
* Erweiterung der Lösung, um **mehrere Sprachen** in einem Aufruf zu übersetzen.  
* Häufige Fallstricke und Tipps für produktionsreife Implementierungen.

### Voraussetzungen

* .NET 6.0 SDK oder neuer (der Code kompiliert mit .NET Core und .NET Framework).  
* Ein Google‑Cloud‑Konto mit aktivierter **Cloud Translation API**.  
* Grundlegende Kenntnisse in C# und Konsolenanwendungen.  

---

## Schritt 1: Installieren der Google Cloud Translation Client‑Bibliothek

Die offizielle Client‑Bibliothek abstrahiert HTTP‑Aufrufe und übernimmt die Authentifizierung für Sie.

```bash
dotnet add package Google.Cloud.Translation.V2
```

Durch Ausführen des Befehls wird das Paket `Google.Cloud.Translation.V2` zu Ihrem Projekt hinzugefügt, wodurch Sie Zugriff auf die im gesamten Leitfaden verwendete Klasse `TranslationClient` erhalten.

> **Warum dieser Schritt wichtig ist** – Die Verwendung des SDK vermeidet manuelle Anfragekonstruktion, reduziert Fehler und stellt sicher, dass Sie mit der neuesten API‑Version von Google kompatibel sind.

## Schritt 2: Erstellen eines wiederverwendbaren Übersetzungshilfs

Das Kapseln der Übersetzungslogik in einer statischen Klasse macht den Code wiederverwendbar und isoliert die Handhabung des API‑Schlüssels.

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

> **Warum wir ein Dictionary zurückgeben** – Wenn Sie **mehrere Sprachen übersetzen** müssen, erleichtert die Organisation der Ergebnisse nach Sprachcode die nachfolgende Verarbeitung.

## Schritt 3: Erstellen der Konsolenanwendung, die den Helfer verwendet

Unten finden Sie ein vollständiges `Program.cs`, das sowohl eine Einzeltext‑Übersetzung als auch eine Batch‑Übersetzung demonstriert.

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

**Erwartete Konsolenausgabe**

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

> **Warum die try/catch‑Blöcke?** – Netzwerkfehler, Kontingentgrenzen oder ein ungültiger API‑Schlüssel werfen Ausnahmen. Durch eine elegante Behandlung wird die Benutzererfahrung verbessert und Ihre Anwendung bleibt stabil.

## Schritt 4: Sichern Ihres API‑Schlüssels

Das Hard‑Coden des API‑Schlüssels, wie oben gezeigt, ist für eine schnelle Demo akzeptabel, jedoch nicht für die Produktion. Befolgen Sie diese Praktiken:

* Speichern Sie den Schlüssel in einer Umgebungsvariable (`GOOGLE_API_KEY`) und lesen Sie ihn zur Laufzeit aus:
  ```csharp
  string apiKey = Environment.GetEnvironmentVariable("GOOGLE_API_KEY");
  ```
* Verwenden Sie **Google Application Default Credentials** anstelle eines API‑Schlüssels, wenn Sie auf Google Cloud (App Engine, Cloud Run usw.) laufen.
* Beschränken Sie den Schlüssel in der Google‑Cloud‑Konsole auf die Translation API und limitieren Sie die Nutzung auf bestimmte IP‑Adressen oder Referrer.

## Schritt 5: Erweiterung der Lösung für reale Szenarien

### Erkennung der Ausgangssprache

Wenn Sie die Ausgangssprache kennen müssen, enthält das Antwortobjekt `DetectedSourceLanguage`:

```csharp
var response = client.TranslateText(sourceText, targetLanguage);
Console.WriteLine($"Detected source: {response.DetectedSourceLanguage}");
```

### Übersetzung großer Dokumente

Die API unterstützt bis zu 30 KB pro Anfrage. Für größere Texte teilen Sie den Inhalt in Abschnitte, übersetzen jeden Abschnitt und fügen dann die Ergebnisse zusammen. Bewahren Sie Satzgrenzen, um unbeholfene Formulierungen zu vermeiden.

### Rate‑Limiting und Kontingente

Google setzt pro‑Minute-Anfrage‑Limits durch. Implementieren Sie eine Wiederholungs‑Richtlinie mit exponentiellem Back‑off, um Kontingentgrenzen zu respektieren und `429 Too Many Requests`‑Fehler zu vermeiden.

```csharp
// Example using Polly (install Polly via NuGet)
var policy = Policy
    .Handle<Google.Api.Gax.Rpc.ResourceExhaustedException>()
    .WaitAndRetryAsync(3, attempt => TimeSpan.FromSeconds(Math.Pow(2, attempt)));

await policy.ExecuteAsync(() => client.TranslateTextAsync(...));
```

---

## Häufige Fragen und Randfälle

**F: Kann ich eine komplette HTML‑Seite übersetzen?**  
A: Ja. Verwenden Sie den Parameter `Format` (`"text"` oder `"html"`), wenn Sie `TranslateText` aufrufen. Das SDK stellt dies über die Überladung von `TranslateText` bereit, die ein `TranslateTextRequest` akzeptiert.

**F: Was ist, wenn eine Sprache nicht unterstützt wird?**  
A: Die API gibt einen Fehler zurück. Validieren Sie Sprachcodes anhand der Liste, die von `client.ListSupportedLanguages()` zurückgegeben wird, bevor Sie eine Anfrage stellen.

**F: Berechnet die API pro Zeichen?**  
A: Google berechnet pro übersetztem Zeichen. Schätzen Sie die Kosten mithilfe der Preisseite und erwägen Sie das Caching häufiger Übersetzungen.

---

## Fazit

Sie wissen jetzt, **wie man Text** in C# mit der offiziellen Google Translate API übersetzt. Das Tutorial behandelte ein **Google Translate Beispiel**, zeigte **mehrere Sprachen übersetzen** und hob produktionsreife Praktiken wie API‑Schlüssel‑Sicherheit und Fehlerbehandlung hervor. Durch die Wiederverwendung des `Translator`‑Helpers können Sie Übersetzungen in jeden .NET‑Dienst, Desktop‑App oder Microservice integrieren.

**Nächste Schritte**

* Entdecken Sie das **Google Translate Tutorial** für erweiterte Funktionen wie Glossare und benutzerdefinierte Modelle.  
* Kombinieren Sie diesen Code mit ASP.NET Core, um eine mehrsprachige Web‑API zu erstellen.  
* Experimentieren Sie mit Batch‑Übersetzung von CSV‑Dateien, um Lokalisierungspipelines zu automatisieren.

Viel Spaß beim Programmieren und beim Erstellen global zugänglicher Anwendungen!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein übersetztes Word‑Dokument in C# mit Google KI speichert](/words/english/net/ai-powered-document-processing/how-to-save-translated-word-document-in-c-with-google-ai/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}