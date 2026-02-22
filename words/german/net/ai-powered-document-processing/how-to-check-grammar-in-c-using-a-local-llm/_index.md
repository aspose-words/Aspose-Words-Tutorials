---
category: general
date: 2026-02-21
description: Wie man Grammatik in C# prüft, indem man ein DOCX lädt, dessen Text an
  ein lokales LLM sendet und die korrigierte Version zurückschreibt. Enthält Anweisungen
  zur Nutzung des LLM und zum Auslesen des Word‑Dokumenttexts.
draft: false
keywords:
- how to check grammar
- how to use llm
- read word document text
- load docx in c#
language: de
og_description: Wie man Grammatik in C# prüft, indem man ein DOCX lädt, den Text an
  ein lokales LLM sendet und die korrigierte Version zurückschreibt. Lernen Sie, wie
  man LLM verwendet und den Text eines Word‑Dokuments liest.
og_title: Wie man Grammatik in C# mit einem lokalen LLM prüft
tags:
- C#
- LLM
- Aspose.Words
title: Wie man Grammatik in C# mit einem lokalen LLM prüft
url: /de/net/ai-powered-document-processing/how-to-check-grammar-in-c-using-a-local-llm/
---

Let's craft translation.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Grammatikprüfung in C# mit einem lokalen LLM

Haben Sie sich schon einmal gefragt, **wie man Grammatik** in einem Word‑Dokument prüft, ohne Ihr C#‑Projekt zu verlassen? Sie sind nicht allein – Entwickler fragen ständig: „Kann ich das Korrekturlesen automatisieren mit demselben Code, der Chatbots antreibt?“ Die kurze Antwort lautet ja. Indem Sie ein DOCX laden, den Text extrahieren und ihn an ein lokal gehostetes Large Language Model (LLM) übergeben, erhalten Sie sofort Grammatik‑Korrekturen und schreiben das überarbeitete Ergebnis direkt zurück in die Datei.

In diesem Tutorial gehen wir den gesamten Prozess durch: ein `.docx` mit **load docx in c#** lesen, **how to use llm** für Grammatik‑Korrektur aufrufen und schließlich das bereinigte Dokument speichern. Am Ende haben Sie eine einsatzbereite Konsolen‑App, die genau das tut – kein manuelles Kopieren/Einfügen, keine externen APIs, nur reines C# und ein lokaler LLM‑Endpunkt.

> **Was Sie benötigen**
> - .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework, aber .NET 6 ist der Sweet Spot)
> - Die [Aspose.Words for .NET](https://products.aspose.com/words/net/) Bibliothek (eine kostenlose Testversion reicht für Tests)
> - Einen laufenden LLM‑Server, der einen einfachen `CheckGrammar(string)`‑Endpunkt bereitstellt (z. B. Ollama, LM Studio oder ein benutzerdefinierter FastAPI‑Wrapper)
> - Grundlegende Kenntnisse von async/await (optional, aber empfohlen)

Wenn Sie sich fragen, **warum das wichtig ist**, denken Sie an die Zeit, die Sie damit verbringen, Tippfehler in generierten Berichten manuell zu korrigieren. Die Automatisierung dieses Schrittes beschleunigt nicht nur Pipelines, sondern garantiert auch Konsistenz über Dutzende von Dokumenten hinweg. Lassen Sie uns loslegen.

---

## Wie die Grammatikprüfung funktioniert – Überblick

Bevor wir loslegen, ein kurzer Fahrplan:

1. **Erstellen Sie einen Client**, der mit dem lokalen LLM‑Endpunkt kommuniziert.  
2. **Lesen Sie das Word‑Dokument** mit Aspose.Words – das ist der klassische Weg, um **read word document text** in C# zu erhalten.  
3. **Senden Sie den Rohtext** an das LLM und erhalten Sie eine korrigierte Version.  
4. **Ersetzen Sie den Originalinhalt** im Dokument durch den korrigierten Text.  
5. **Speichern** Sie die aktualisierte Datei (optional, aber meist erforderlich).

Jeder Schritt ist in einer eigenen Methode gekapselt, sodass Sie Teile später wiederverwenden oder austauschen können. Der vollständige Quellcode steht am Ende des Artikels.

---

## Schritt 1: LLM‑Client einrichten (How to Use LLM)

Um alles übersichtlich zu halten, kapseln wir den HTTP‑Aufruf in einer kleinen Wrapper‑Klasse. Diese Klasse geht davon aus, dass der LLM‑Dienst eine POST‑Anfrage mit einem JSON‑Payload `{ "prompt": "..." }` akzeptiert und `{ "response": "..." }` zurückgibt. Passen Sie die Serialisierung an, falls Ihr Service abweicht.

```csharp
using System.Net.Http;
using System.Text;
using System.Text.Json;
using System.Threading.Tasks;

/// <summary>
/// Minimal client for a local LLM that offers a grammar‑checking endpoint.
/// </summary>
public class LocalLargeLanguageModel
{
    private readonly HttpClient _http;
    private readonly string _baseUrl;

    public LocalLargeLanguageModel(string baseUrl)
    {
        _baseUrl = baseUrl.TrimEnd('/');
        _http = new HttpClient();
    }

    /// <summary>
    /// Sends the input text to the LLM and returns the corrected version.
    /// </summary>
    public async Task<string> CheckGrammarAsync(string input)
    {
        var payload = new { prompt = $"Correct the grammar and punctuation:\n\n{input}" };
        var content = new StringContent(JsonSerializer.Serialize(payload), Encoding.UTF8, "application/json");

        // The endpoint is assumed to be /grammar
        var response = await _http.PostAsync($"{_baseUrl}/grammar", content);
        response.EnsureSuccessStatusCode();

        var json = await response.Content.ReadAsStringAsync();
        var result = JsonSerializer.Deserialize<Dictionary<string, string>>(json);
        return result != null && result.TryGetValue("response", out var corrected) ? corrected : input;
    }
}
```

**Warum das wichtig ist:**  
- **Entkopplung** – Wenn Sie später von Ollama zu LM Studio wechseln, müssen Sie nur die URL oder das Payload‑Format ändern.  
- **Async‑freundlich** – Netzwerk‑I/O blockiert nicht Ihre UI oder Ihren Hintergrund‑Worker.  
- **Fehlerbehandlung** – `EnsureSuccessStatusCode` wirft eine klare Ausnahme, wenn das LLM nicht erreichbar ist, die wir später abfangen.

> **Pro‑Tipp:** Wenn Ihr LLM auf GPU läuft, halten Sie die Anforderungsgröße unter ~4 KB, um Latenzspitzen zu vermeiden.

---

## Schritt 2: DOCX laden und Text extrahieren (Read Word Document Text)

Aspose.Words macht das Lesen von Word‑Dateien zum Kinderspiel. Die Methode `Document.GetText()` liefert den gesamten sichtbaren Text inklusive Zeilenumbrüchen. Wenn Sie reichhaltigere Formatierungen (Tabellen, Fußnoten) benötigen, müssten Sie den Node‑Baum traversieren, aber für reine Grammatik‑Checks reicht der Klartext aus.

```csharp
using Aspose.Words;

/// <summary>
/// Loads a .docx file and returns its raw textual content.
/// </summary>
public static string ReadDocumentText(string filePath)
{
    if (!File.Exists(filePath))
        throw new FileNotFoundException($"Document not found: {filePath}");

    var doc = new Document(filePath);
    return doc.GetText(); // Returns text with line breaks
}
```

**Hinweis zu Randfällen:**  
Enthält das Dokument nicht‑englische Zeichen oder Sonderzeichen, stellen Sie sicher, dass das von Ihnen genutzte LLM‑Modell Unicode unterstützt. Die meisten modernen Modelle tun das, ältere könnten jedoch abschneiden oder falsch interpretieren.

---

## Schritt 3: Inhalt mit korrigiertem Text ersetzen

Aspose.Words bietet keine Einzeiler‑Methode „gesamten Body ersetzen“, aber das Leeren des Node‑Baums und das Einfügen eines einzelnen Paragraphen funktioniert gut. Das garantiert außerdem, dass versteckte Markups (wie nachverfolgte Änderungen) entfernt werden.

```csharp
/// <summary>
/// Overwrites the document with the supplied corrected text.
/// </summary>
public static void WriteCorrectedText(string filePath, string correctedText)
{
    var doc = new Document(filePath);
    doc.RemoveAllChildren(); // Clears sections, paragraphs, tables, etc.

    var builder = new DocumentBuilder(doc);
    builder.Writeln(correctedText); // Writes as a single paragraph; you can split by "\n" if you want multiple paragraphs.

    doc.Save(filePath); // Overwrites the original file
}
```

**Warum wir alle Kinder entfernen:**  
- Garantiert ein sauberes Fundament, sodass verbliebene Formatierungen den neuen Inhalt nicht beeinträchtigen.  
- Vereinfacht den Code – es muss nicht nach spezifischen Nodes gesucht werden, die ersetzt werden sollen.

Wenn Sie die ursprünglichen Überschriften erhalten wollen, könnten Sie den ursprünglichen Node‑Baum parsen und nur `Run`‑Nodes ersetzen, was jedoch über den Rahmen dieses Tutorials hinausgeht.

---

## Schritt 4: Alles zusammenführen – Vollständiges Beispiel

Unten finden Sie das komplette Konsolen‑Programm. Es demonstriert **how to check grammar** von Anfang bis Ende, inklusive einfacher Fehlerbehandlung und optionaler Befehlszeilen‑Argumente.

```csharp
using System;
using System.IO;
using System.Threading.Tasks;
using Aspose.Words;

// Ensure you have a license or are okay with the evaluation watermark.
class Program
{
    // Adjust these paths to match your environment.
    private const string InputPath = @"YOUR_DIRECTORY\input.docx";
    private const string OutputPath = @"YOUR_DIRECTORY\output.docx";
    private const string LlmEndpoint = "http://localhost:5000";

    static async Task Main(string[] args)
    {
        try
        {
            // 1️⃣ Create the LLM client.
            var llm = new LocalLargeLanguageModel(LlmEndpoint);

            // 2️⃣ Load the DOCX and read its text.
            Console.WriteLine("Reading document...");
            string originalText = ReadDocumentText(InputPath);

            // 3️⃣ Send text to the LLM for grammar correction.
            Console.WriteLine("Sending text to LLM for grammar check...");
            string correctedText = await llm.CheckGrammarAsync(originalText);

            // 4️⃣ Write the corrected text back into a new file.
            Console.WriteLine("Writing corrected text to new document...");
            // We copy the original file first so the original remains untouched.
            File.Copy(InputPath, OutputPath, overwrite: true);
            WriteCorrectedText(OutputPath, correctedText);

            Console.WriteLine($"✅ Grammar check complete! Updated file saved to: {OutputPath}");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"❌ An error occurred: {ex.Message}");
            // For real‑world apps, consider logging the stack trace.
        }
    }

    // --- Helper methods from earlier steps ---
    public static string ReadDocumentText(string filePath)
    {
        if (!File.Exists(filePath))
            throw new FileNotFoundException($"Document not found: {filePath}");

        var doc = new Document(filePath);
        return doc.GetText();
    }

    public static void WriteCorrectedText(string filePath, string correctedText)
    {
        var doc = new Document(filePath);
        doc.RemoveAllChildren();

        var builder = new DocumentBuilder(doc);
        // Preserve line breaks by splitting and writing each line.
        foreach (var line in correctedText.Split(new[] { "\r\n", "\n" }, StringSplitOptions.None))
        {
            builder.Writeln(line);
        }

        doc.Save(filePath);
    }
}
```

### Erwartete Ausgabe

Wenn Sie das Programm ausführen (`dotnet run`), erscheint in der Konsole etwa Folgendes:

```
Reading document...
Sending text to LLM for grammar check...
Writing corrected text to new document...
✅ Grammar check complete! Updated file saved to: YOUR_DIRECTORY\output.docx
```

Öffnen Sie `output.docx` in Word – Sie sehen denselben Inhalt, jedoch mit korrigierter Interpunktion, Subjekt‑Verb‑Übereinstimmung und allen offensichtlichen Tippfehlern, die das LLM behoben hat.

---

## Häufige Fragen & Randfälle

### Was, wenn das LLM `null` oder einen leeren String zurückgibt?

Die Methode `CheckGrammarAsync` greift auf den Original‑Input zurück, falls das Antwort‑Payload das Feld `response` nicht enthält. So wird verhindert, dass das Dokument versehentlich geleert wird.

### Wie groß darf ein Dokument sein, bevor die Anfrage timeoutet?

Die meisten lokalen LLM‑Server verarbeiten ein paar tausend Zeichen problemlos. Bei größeren Dateien (z. B. > 100 KB) sollten Sie den Text in Absätze aufteilen, jedes Chunk separat senden und anschließend die korrigierten Stücke wieder zusammensetzen. Eine Chunk‑Größe von ~2 KB ist ein guter Ausgangspunkt.

### Werden Bilder, Tabellen oder Fußnoten erhalten?

Nein. Durch das Leeren aller Kinder gehen nicht‑textuelle Elemente verloren. Wenn Sie diese behalten müssen, müssten Sie den Node‑Baum iterieren, nur `Run`‑Nodes ersetzen und andere Nodes unangetastet lassen. Das ist ein fortgeschritteneres Szenario – erkunden Sie gern die Aspose.Words‑API für die Manipulation von `NodeCollection`.

### Kann ich ein Cloud‑LLM statt eines lokalen verwenden?

Absolut. Ersetzen Sie einfach die Endpunkt‑URL und das Payload‑Format in `LocalLargeLanguageModel`. Beachten Sie, dass Cloud‑Dienste häufig Rate‑Limits und Kosten haben, während ein lokales Modell offline läuft und nach der initialen GPU/CPU‑Einrichtung kostenlos ist.

---

## Pro‑Tipps & Best Practices

- **Client cachen**: Das Wiederverwenden derselben `HttpClient`‑Instanz verhindert

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}