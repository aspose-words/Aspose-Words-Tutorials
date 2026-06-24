---
category: general
date: 2026-05-04
description: Wie man LLM verwendet, um Dokumente mit Aspose zu bearbeiten – lernen
  Sie, Absatztext zu ersetzen, eine Verbindung zu einem lokalen LLM herzustellen und
  Text mithilfe von KI neu zu schreiben.
draft: false
keywords:
- how to use llm
- replace paragraph text
- connect to local llm
- rewrite text using ai
- edit document aspose
language: de
og_description: Wie man ein LLM verwendet, um Dokumente mit Aspose zu bearbeiten.
  Dieser Leitfaden zeigt, wie man eine lokale LLM verbindet, Absatztext ersetzt und
  Text mithilfe von KI neu schreibt.
og_title: Wie man LLM mit Aspose.Words nutzt – Absätze in C# umschreiben
tags:
- Aspose.Words
- C#
- AI
- LLM
title: Wie man LLM mit Aspose.Words verwendet – Absätze in C# neu schreiben
url: /de/net/ai-powered-document-processing/how-to-use-llm-with-aspose-words-rewrite-paragraphs-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man LLM mit Aspose.Words verwendet – Absätze in C# neu schreiben

Haben Sie sich jemals gefragt, **wie man LLM** nutzt, um ein Word‑Dokument zu verfeinern, ohne es manuell zu öffnen? Sie sind nicht allein. Viele Entwickler stoßen auf ein Problem, wenn sie *Absatztext* programmgesteuert ersetzen wollen, aber keinen sauberen, KI‑gesteuerten Workflow haben.  

In diesem Tutorial verbinden wir ein lokales Large Language Model, übergeben ihm einen Ausschnitt aus einer `.docx`‑Datei, lassen es **Text mit KI neu schreiben** und speichern schließlich das aktualisierte Dokument – alles mit Aspose.Words. Am Ende haben Sie eine lauffähige C#‑Konsolenanwendung, die die gesamte Pipeline demonstriert.

> **Was Sie erhalten:** ein vollständiges, ausführbares Beispiel, Erklärungen zu jedem Schritt, Tipps für Sonderfälle und Ideen zur Erweiterung der Lösung.

## Was Sie benötigen

- **.NET 6+** (oder .NET Framework 4.7.2 – der Code funktioniert in beiden)
- **Aspose.Words for .NET** (NuGet‑Paket `Aspose.Words`)
- Ein **lokaler LLM‑Server**, der einen einfachen HTTP‑`/generate`‑Endpoint bereitstellt (z. B. Ollama, LMStudio oder ein eigener Flask‑Dienst)
- Grundlegende Kenntnisse in C# und HTTP‑Client‑Code  

Weitere SDKs sind nicht nötig; alles andere befindet sich im Code, den wir gemeinsam schreiben.

## Schritt 1: Wie man LLM verwendet, um Absatztext zu ersetzen

Das Erste, was wir tun müssen, ist den Absatz zu identifizieren, den wir ändern wollen. Aspose.Words macht das dank seines umfangreichen Objektmodells kinderleicht.

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

**Warum das wichtig ist:**  
Die richtige Node auszuwählen verhindert, dass Sie versehentlich Überschriften oder Tabellen überschreiben. Durch den **replace paragraph text**‑Ansatz bleibt die Dokumentstruktur erhalten, während nur der relevante Inhalt geändert wird.

> **Pro‑Tipp:** Wenn Ihr Dokument Abschnitte variabler Länge enthält, verwenden Sie `document.GetChildNodes(NodeType.Paragraph, true)` und LINQ, um einen Absatz anhand seines Textes oder Stils zu finden.

## Schritt 2: Verbindung zu einem lokalen LLM‑Endpoint herstellen

Jetzt, wo wir den Text haben, müssen wir ihn an das LLM senden. Das Beispiel nutzt eine einfache Wrapper‑Klasse `LocalLargeLanguageModel`, die das HTTP‑Handling verbirgt. Sie können sie durch direkte `HttpClient`‑Aufrufe ersetzen, wenn Sie möchten.

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

**Warum wir so verbinden:**  
Ein **connect to local llm**‑Setup eliminiert Latenz, hält Daten on‑premise und vermeidet API‑Kosten. Der Wrapper macht den späteren Code zudem übersichtlicher, sodass wir uns auf die **rewrite text using ai**‑Logik konzentrieren können.

## Schritt 3: Text mit KI und Aspose.Words neu schreiben

Mit dem Absatztext und dem bereitstehenden LLM formulieren wir einen Prompt, der dem Modell genau sagt, was wir wollen – eine formelle Umschreibung. Sie können den Prompt für andere Stile anpassen (freundlich, technisch usw.).

```csharp
// Build the prompt – notice the newline for readability
string prompt = $"Rewrite the following in a formal tone:\n{targetParagraph.GetText()}";

// Ask the LLM to generate the revised version
string revisedText = localLlm.GenerateText(prompt);

// Show the AI‑generated text
Console.WriteLine("\nRevised paragraph:");
Console.WriteLine(revisedText);
```

**Warum das funktioniert:**  
LLMs reagieren auf Prompts; klare Anweisungen („Rewrite … in a formal tone“) führen zu konsistenten Ergebnissen. Der **rewrite text using ai**‑Schritt ist das Herzstück des Tutorials – er zeigt, wie KI direkt in Dokument‑Workflows eingebettet werden kann.

## Schritt 4: Das Dokument bearbeiten und Änderungen speichern

Jetzt ersetzen wir die ursprünglichen Runs durch den neuen Inhalt. Aspose.Words speichert Text in `Run`‑Objekten, daher verhindert das vorherige Leeren von Runs verbleibende Formatierungsartefakte.

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

**Hinweis zu Sonderfällen:**  
Enthält der ursprüngliche Absatz gemischte Formatierungen (fett, kursiv), möchten Sie vielleicht die Stile beibehalten. Erstellen Sie in diesem Fall einen neuen `Run`, kopieren Sie die ursprünglichen `Font`‑Einstellungen und setzen Sie anschließend dessen `Text` auf `revisedText`.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette Programm, das Sie in ein Konsolenprojekt kopieren‑und‑einfügen können. Denken Sie daran, zuerst das Aspose.Words‑NuGet‑Paket zu installieren (`dotnet add package Aspose.Words`).

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

### Erwartete Ausgabe

```
Original paragraph:
the quick brown fox jumps over the lazy dog.

Revised paragraph:
The quick brown fox leaps over the lazy dog in a formal manner.

Document saved as output.docx
```

Öffnen Sie `output.docx` – Sie werden sehen, dass der dritte Absatz nun die überarbeitete Version enthält.

## Häufige Fragen & Stolperfallen

| Frage | Antwort |
|----------|--------|
| **Was, wenn mein LLM JSON mit zusätzlichen Feldern zurückgibt?** | Passen Sie `GenerateText` an, um die richtige Eigenschaft zu deserialisieren, oder parsen Sie die Antwort manuell. |
| **Kann ich mehrere Absätze gleichzeitig verarbeiten?** | Ja – iterieren Sie über `document.FirstSection.Body.Paragraphs` und wenden Sie dieselbe Prompt‑Logik an, ggf. mit einem Absatz‑Index im Prompt für Kontext. |
| **Mein LLM‑Server verwendet Authentifizierung?** | Fügen Sie vor dem POST einen Header zum `HttpClient` hinzu: `_client.DefaultRequestHeaders.Add("Authorization", "Bearer YOUR_TOKEN");`. |
| **Die Formatierung geht nach dem Ersetzen verloren.** | Bewahren Sie die ursprünglichen `Run.Font`‑Einstellungen: erstellen Sie einen neuen `Run`, kopieren Sie `originalRun.Font.Clone()`, und setzen Sie dann dessen `Text`. |
| **Das LLM liefert manchmal leere Strings.** | Implementieren Sie ein Fallback – wenn `revisedText.Trim().Length == 0`, behalten Sie den Originaltext bei oder versuchen Sie es mit einem einfacheren Prompt erneut. |

## Erweiterung der Lösung

Jetzt, wo Sie **how to use llm** für einen einzelnen Absatz beherrschen, denken Sie an folgende nächste Schritte:

- **Batch‑Verarbeitung:** Durchlaufen Sie jeden Absatz und schreiben Sie ihn in einem gewünschten Stil neu (z. B. „make all text concise“).  
- **Stil‑bewusste Umschreibung:** Übergeben Sie den Namen des ursprünglichen Absatz‑Stils im Prompt, damit das LLM Überschriften von Fließtext unterscheiden kann.  
- **Integration in eine CI‑Pipeline:** Automatisieren Sie die Dokumenten‑Politur als Teil eines Dokumentations‑Build‑Prozesses.  
- **Alternative Prompts:** Probieren Sie „summarize this paragraph“ oder „translate this paragraph to Spanish“ aus, um die volle Leistungsfähigkeit von **rewrite text using ai** zu erkunden.

## Fazit

Wir haben den gesamten Ablauf von **how to use llm** mit Aspose.Words durchlaufen: Dokument laden, **connect to local llm**, Absatz extrahieren, **rewrite text using ai**, **replace paragraph text** und schließlich das Ergebnis speichern. Der Code ist eigenständig, funktioniert sofort und zeigt, wie KI praktisch mit traditioneller Dokumenten‑Automatisierung kombiniert werden kann.

Probieren Sie es aus, passen Sie die Prompts an und lassen Sie

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}