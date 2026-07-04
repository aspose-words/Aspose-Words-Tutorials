---
category: general
date: 2026-06-24
description: Lokales LLM‑Tutorial, das zeigt, wie man ein lokales LLM aufruft, ein
  Word‑Dokument lädt und eine Grammatikprüfung mit KI‑Grammatikprüfung in C# durchführt.
draft: false
keywords:
- local llm tutorial
- run grammar check
- ai grammar check
- call local llm
- load word document
language: de
og_description: Das lokale LLM‑Tutorial erklärt Schritt für Schritt, wie man ein lokales
  LLM aufruft, ein Word‑Dokument lädt und in C# eine KI‑Grammatikprüfung durchführt.
og_title: Lokales LLM‑Tutorial – Lokales LLM aufrufen und Grammatik prüfen
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
title: Lokales LLM‑Tutorial – Wie man ein lokales LLM aufruft und eine Grammatikprüfung
  durchführt
url: /de/net/ai-powered-document-processing/local-llm-tutorial-how-to-call-a-local-llm-and-run-grammar-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lokales LLM‑Tutorial – Lokales LLM aufrufen und Grammatikprüfung durchführen

Haben Sie sich jemals gefragt, wie man **Grammatikprüfung** auf einer Word‑Datei durchführt, ohne etwas in die Cloud zu senden? In diesem **lokalen LLM‑Tutorial** verbinden wir ein selbstgehostetes Large Language Model, laden eine `.docx`‑Datei und lassen die KI den Text aufräumen. Keine API‑Schlüssel, kein externer Datenverkehr – nur Ihr eigener Rechner, der die schwere Arbeit übernimmt.

Wir gehen jede Codezeile durch, erklären, warum jedes Teil wichtig ist, und zeigen Ihnen sogar, wie Sie die üblichen Fallstricke (wie fehlende Dateien oder einen nicht erreichbaren Endpunkt) handhaben können. Am Ende haben Sie eine sofort ausführbare C#‑Konsolenanwendung, die eine **ai grammar check** mithilfe eines lokal gehosteten Modells durchführt.

> **Was Sie erhalten:** ein vollständiges, ausführbares Programm, eine klare Erklärung jedes Schrittes und Tipps zum Skalieren der Lösung für größere Dokumente oder verschiedene LLM‑Anbieter.

![Diagramm zum lokalen LLM‑Tutorial](https://example.com/local-llm-tutorial-diagram.png "Diagramm, das den Ablauf des lokalen LLM‑Tutorials veranschaulicht")

## Voraussetzungen

- .NET 6.0 SDK oder neuer (Sie können es von der Microsoft‑Website herunterladen)
- Ein lokal laufender LLM‑Server, der einen OpenAI‑kompatiblen Endpunkt bereitstellt (z. B. Ollama, LM Studio oder ein benutzerdefinierter FastAPI‑Wrapper)
- Das NuGet‑Paket `AiGrammar` (oder jede Bibliothek, die die Klassen `LocalLargeLanguageModel`, `Document` und `AiModelType` bereitstellt)
- Ein Beispiel‑Word‑Dokument (`input.docx`) in einem Ordner, den Sie später referenzieren

Das war’s – keine zusätzlichen Cloud‑Anmeldeinformationen erforderlich.

## Schritt 1: Lokales LLM‑Tutorial – Einrichten des Endpunkts

Das erste, was wir benötigen, ist ein **call local llm**‑Objekt, das weiß, wohin es seine Anfragen senden soll. Denken Sie daran wie an die Telefonnummer, die Sie wählen, bevor Sie sprechen können.

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

**Warum das wichtig ist:**  
Die meisten LLM‑SDKs erwarten einen HTTP‑Endpunkt, der dem OpenAI‑API‑Vertrag entspricht. Indem wir `Endpoint` auf `http://localhost:8000/v1` setzen, teilen wir der Bibliothek mit, **call local llm** zu verwenden, anstatt die Server von OpenAI zu kontaktieren. Der Dummy‑API‑Schlüssel ist nur ein Platzhalter – einige Clients akzeptieren keinen Nullwert, daher geben wir ihm etwas Harmloses.

> **Pro‑Tipp:** Wenn Sie das LLM hinter einem Reverse‑Proxy betreiben, setzen Sie `Endpoint` auf die Proxy‑URL und lassen Sie den Proxy die TLS‑Beendigung übernehmen. Das hält Ihre Konsolen‑App einfach und sicher.

## Schritt 2: Word‑Dokument für Grammatikprüfung laden

Jetzt, wo das Modell erreichbar ist, müssen wir den Inhalt des **load word document** in den Speicher laden. Die Klasse `Document` abstrahiert das Parsen von `.docx` für uns.

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

**Warum das wichtig ist:**  
Ein binäres `.docx`‑File direkt an ein LLM zu übergeben, würde es verwirren. Der `Document`‑Helper extrahiert den Rohtext und erhält dabei Absatzumbrüche, was dem **ai grammar check** eine saubere Eingabe liefert. Die Existenzprüfung verhindert eine unangenehme `FileNotFoundException`, die sonst die Anwendung zum Absturz bringen würde.

## Schritt 3: Grammatikprüfung mit dem LLM ausführen

Hier ist das Herzstück des Tutorials: Wir bitten das lokale Modell, den Text Korrektur zu lesen. Die Methode `CheckGrammar` verbirgt die HTTP‑Logik und gibt ein Ergebnisobjekt zurück.

```csharp
// Step 3: Run the grammar‑check operation using the LLM
var result = doc.CheckGrammar(
    llm,
    AiModelType.Gpt4   // You can swap this for any model supported by AiModelType
);
```

**Warum das wichtig ist:**  
`AiModelType.Gpt4` ist lediglich ein Label, das dem entfernten Dienst mitteilt, welche Prompt‑Vorlage zu verwenden ist. Wenn Sie ein kleineres Modell haben (z. B. `Llama2`), ersetzen Sie es entsprechend. Die Bibliothek serialisiert den Dokumententext, sendet ihn an `http://localhost:8000/v1/completions` und parsed die korrigierte Ausgabe.

> **Randfall:** Wenn das LLM ein Timeout hat, wirft `CheckGrammar` eine `TimeoutException`. Umgeben Sie den Aufruf mit einem `try/catch`‑Block, wenn Sie große Dokumente oder einen stark ausgelasteten Server erwarten.

## Schritt 4: Korrigierten Text ausgeben

Schließlich zeigen wir die bereinigte Version an. In einer echten Anwendung könnten Sie sie in eine neue `.docx`‑Datei zurückschreiben, aber für dieses Tutorial reicht ein Konsolenausdruck aus.

```csharp
// Step 4: Output the corrected text
Console.WriteLine("=== Corrected Text ===");
Console.WriteLine(result.CorrectedText);
```

**Erwartete Ausgabe** (unter der Annahme, dass die Originaldatei einige absichtliche Fehler enthielt):

```
=== Corrected Text ===
The quick brown fox jumps over the lazy dog. 
She doesn't like apples, but she loves oranges.
```

Wenn das LLM keine Fehler gefunden hat, ist die Ausgabe identisch mit der Eingabe, was dennoch ein nützliches Signal ist.

## Voll funktionsfähiges Beispiel

Wenn wir alles zusammenfügen, hier das komplette Programm, das Sie in ein neues Konsolenprojekt kopieren‑und‑einfügen können:

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

### So führen Sie es aus

1. Öffnen Sie ein Terminal im Projektordner.  
2. Führen Sie `dotnet run` aus.  
3. Beobachten Sie, wie die Konsole den korrigierten Text ausgibt.

Das ist das gesamte **local llm tutorial** in weniger als 100 Zeilen Code.

## Häufig gestellte Fragen (FAQ)

### Kann ich eine andere LLM‑Marke verwenden?

Absolut. Solange der Server das OpenAI‑v1‑API‑Schema einhält, ändern Sie einfach `Endpoint` und wählen den entsprechenden `AiModelType`‑Enum‑Wert (z. B. `AiModelType.Llama2`). Der Rest des Codes bleibt unverändert.

### Was, wenn mein Dokument riesig ist (10 MB+)?

Große Payloads können die Standard‑Request‑Größe vieler Server überschreiten. Teilen Sie das Dokument in Abschnitte und rufen Sie `CheckGrammar` pro Abschnitt auf, dann fügen Sie die Ergebnisse zusammen. Das reduziert auch die Wahrscheinlichkeit eines Timeouts.

### Wie schreibe ich die korrigierte Ausgabe zurück in eine `.docx`‑Datei?

Die Klasse `Document` bietet in der Regel eine Methode `Save(string path, string content)`. Nachdem Sie `result.CorrectedText` erhalten haben, rufen Sie auf:

```csharp
doc.Save(@"C:\Projects\GrammarDemo\output_corrected.docx", result.CorrectedText);
```

Prüfen Sie die Dokumentation der Bibliothek für die genaue Signatur.

### Ist der Dummy‑API‑Schlüssel ein Sicherheitsrisiko?

Nein. Der Schlüssel wird von selbstgehosteten Endpunkten ignoriert, aber einige SDKs verlangen einen nicht‑null‑String. Die Verwendung eines Platzhalters wie `"dummy"` erfüllt das SDK, ohne irgendwelche Geheimnisse preiszugeben.

## Nächste Schritte und verwandte Themen

- **Fine‑tune your local LLM** für domänenspezifische Grammatik (z. B. juristisches oder medizinisches Schreiben).  
- **Run a batch job**, das einen gesamten Ordner mit Word‑Dateien verarbeitet – ideal für Publishing‑Pipelines.  
- Erkunden Sie **streaming responses**, wenn Sie Echtzeit‑Vorschläge erhalten möchten, während der Benutzer tippt.  
- Kombinieren Sie dies mit **spell‑checking libraries** für ein zweischichtiges Qualitätsgate.

Jede dieser Ideen baut auf den Kernkonzepten dieses **local llm tutorial** auf, sodass Sie dieselben Muster – **call local llm**, **load word document**, **run grammar check** und **handle results** – immer wieder finden werden.

---

*Viel Spaß beim Coden! Wenn Sie auf ein Problem stoßen, hinterlassen Sie unten einen Kommentar und wir helfen Ihnen weiter.*

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Laden mit Kodierung in Word‑Dokument](/words/english/net/programming-with-loadoptions/load-with-encoding/)
- [Laden verschlüsselter Word‑Dokumente](/words/english/net/programming-with-loadoptions/load-encrypted-document/)
- [Beschädigtes DOCX wiederherstellen – Öffnen & Laden von Word‑Dokumenten](/words/english/python-net/document-operations/recover-corrupted-docx-open-load-word-document/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}