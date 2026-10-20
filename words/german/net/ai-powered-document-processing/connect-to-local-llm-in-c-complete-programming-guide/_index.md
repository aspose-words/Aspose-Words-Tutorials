---
category: general
date: 2026-04-28
description: Verbinde dich von C# mit einem lokalen LLM und fordere das große Sprachmodell
  auf, ein Word‑Dokument zu laden, rufe das lokale LLM auf und schreibe den Text automatisch
  um. Schritt‑für‑Schritt‑Code enthalten.
draft: false
keywords:
- connect to local llm
- prompt large language model
- load word document
- call local llm
- rewrite text automatically
language: de
og_description: Verbinde dich von C# aus mit einem lokalen LLM und sieh, wie du ein
  großes Sprachmodell anweisen, ein Word‑Dokument laden, das lokale LLM aufrufen und
  den Text in wenigen Minuten automatisch umschreiben kannst.
og_title: Verbinden mit lokalem LLM in C# – Vollständiger Programmierleitfaden
tags:
- Aspose.Words
- C#
- LLM
- AI Automation
title: Verbinden mit lokalem LLM in C# – Vollständiger Programmierleitfaden
url: /de/net/ai-powered-document-processing/connect-to-local-llm-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verbindung zu lokalem LLM in C# – Vollständiger Programmierleitfaden

Haben Sie jemals **connect to local llm** von einer .NET‑App aus benötigt und sich gefragt, wie man es mit einer Word‑Datei kommunizieren lässt? Sie sind nicht allein. In diesem Leitfaden gehen wir den gesamten Prozess durch – connect to local llm, **prompt large language model**, ein Word‑Dokument laden, **call local llm** und schließlich **rewrite text automatically**. Am Ende haben Sie ein ausführbares Beispiel, das jeden Absatz in einen formellen Ton umwandelt, ohne externe API‑Schlüssel.

## Was dieses Tutorial abdeckt

Wir beginnen mit der Installation der erforderlichen NuGet‑Pakete, dann starten wir einen einfachen lokalen LLM‑Endpunkt (denken Sie an Ollama auf Port 11434). Anschließend laden wir eine `.docx`‑Datei mit Aspose.Words, senden einen Absatz an das LLM, erhalten eine überarbeitete Version und schreiben sie zurück in dasselbe Dokument. Sie sehen außerdem, wie man gängige Fallstricke behandelt – leere Absätze, async‑Entsorgung und Kodierungs‑Eigenheiten – sodass der Code in der Produktion funktioniert und nicht nur als Demo.

### Voraussetzungen

- .NET 6.0 SDK oder neuer (Sie können auch .NET 8 verwenden, wenn Sie möchten)
- Visual Studio 2022 oder VS Code mit C#‑Erweiterung
- **Aspose.Words for .NET** (Kostenlose Testversion funktioniert einwandfrei)
- Ein lokal gehostetes LLM, das den `/api/generate`‑Vertrag unterstützt (z. B. Ollama, LMStudio)
- Grundlegende Vertrautheit mit async/await in C#

> **Pro Tipp:** Wenn Sie Ollama noch nicht installiert haben, führen Sie `ollama serve` aus und holen Sie ein Modell mit `ollama pull llama3`. Der Standard‑HTTP‑Endpunkt wird `http://localhost:11434/api/generate` sein.

---

## Schritt 1: Erforderliche Pakete installieren

Fügen Sie zunächst die NuGet‑Pakete Aspose.Words und Aspose.Words.AI zu Ihrem Projekt hinzu.

```bash
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

Diese Bibliotheken bieten uns die **load word document**‑Funktionalität und einen dünnen Wrapper, um **call local llm** auszuführen, ohne HTTP‑Anfragen von Hand zu erstellen.

---

## Schritt 2: Verbindung zum lokalen LLM‑Endpunkt herstellen

Die Verbindung zu einem lokal gehosteten Modell ist so einfach wie das Instanziieren von `LocalLargeLanguageModel`. Der Konstruktor erwartet die vollständige URL des Generierungs‑Endpunkts.

```csharp
using Aspose.Words.AI;
using Aspose.Words;
using System.Threading.Tasks;

// Create a client that talks to the LLM running on localhost
var localLlm = new LocalLargeLanguageModel("http://localhost:11434/api/generate");
```

Warum verpacken wir den Endpunkt in einer Klasse? `LocalLargeLanguageModel` übernimmt die JSON‑Serialisierung, Wiederholungsversuche und Streaming‑Antworten für Sie – sodass Sie sich auf die Prompt‑Logik konzentrieren können, anstatt mit `HttpClient` zu fiddeln.

---

## Schritt 3: Quell‑Word‑Dokument laden

Als Nächstes laden wir das Dokument in den Speicher. Aspose.Words unterstützt praktisch jedes Word‑Format, sodass `Document` `input.docx` ohne installierte Office‑Software parsen kann.

```csharp
// Path to the source file – adjust as needed
string inputPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document; throws if the file is missing or corrupted
Document sourceDocument = new Document(inputPath);
```

Wenn Sie mit einem Stream arbeiten müssen (z. B. eine über ASP.NET hochgeladene Datei), ersetzen Sie einfach den Dateipfad durch einen `MemoryStream` und übergeben ihn dem `Document`‑Konstruktor.

---

## Schritt 4: Aktuellen Absatztext extrahieren

Wir verwenden `DocumentBuilder`, um im Dokument zu navigieren. In diesem Beispiel überarbeiten wir **the first paragraph**, Sie können jedoch über `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` iterieren, um viele zu verarbeiten.

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

Der `?.`‑Operator verhindert eine `NullReferenceException`, falls das Dokument leer sein sollte. Das ist einer dieser **edge cases**, die Anfängern Probleme bereiten.

---

## Schritt 5: Das LLM auffordern, den Absatz umzuschreiben

Jetzt **prompt large language model** wir tatsächlich. Der Prompt ist einfaches Englisch; der Wrapper sendet ihn als JSON an den lokalen Endpunkt.

```csharp
// Build a friendly instruction for the model
string prompt = $"Rewrite the following sentence in a more formal tone:\n{originalParagraph}";

// Await the model's response – this is an async call
string rewrittenParagraph = await localLlm.PromptAsync(prompt);
```

Warum die Anfrage so formulieren? LLMs reagieren am besten auf klare, einzelne Aufgaben‑Anweisungen. Ein Zeilenumbruch nach dem Doppelpunkt trennt die Anweisung vom Inhalt und verringert die Wahrscheinlichkeit, dass das Modell den Prompt zurückgibt.

**Erwartete Ausgabe** – Wenn `originalParagraph` `"Hey, what's up?"` war, könnte das LLM zurückgeben:

> “Good day, how may I assist you?”

Sie können das Ergebnis überprüfen, indem Sie es ausgeben:

```csharp
Console.WriteLine("Original:  " + originalParagraph);
Console.WriteLine("Rewritten: " + rewrittenParagraph);
```

---

## Schritt 6: Den überarbeiteten Text zurück in das Dokument einfügen

Mit dem neuen Text in der Hand ersetzen wir den alten Absatz. `DocumentBuilder.Writeln` schreibt eine neue Zeile und bewegt den Cursor nach vorne, was ideal zum Anhängen ist. Wenn Sie den exakt gleichen Absatz *ersetzen* müssen, können Sie vor dem Schreiben `docBuilder.CurrentParagraph.RemoveAllChildren()` verwenden.

```csharp
// Option A – Append a new paragraph (keeps the original)
docBuilder.Writeln(rewrittenParagraph);

// Option B – Replace the existing paragraph (uncomment to use)
// docBuilder.CurrentParagraph.RemoveAllChildren();
// docBuilder.CurrentParagraph.AppendChild(new Run(docBuilder.Document, rewrittenParagraph));
```

Beide Ansätze werden gezeigt, damit Sie denjenigen auswählen können, der zu Ihrem Workflow passt.

---

## Schritt 7: Das aktualisierte Dokument speichern

Abschließend speichern wir die Änderungen in einer neuen Datei. Aspose.Words wählt das Format automatisch anhand der Dateierweiterung.

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
sourceDocument.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Öffnen Sie `output.docx` in Word, und Sie werden sehen, dass der Absatz nun in einem formellen Ton geschrieben ist.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie das **complete, self‑contained program**. Kopieren Sie es in ein Konsolenprojekt, stellen Sie die NuGet‑Pakete wieder her und führen Sie es aus – keine zusätzliche Konfiguration ist nötig, außer einem laufenden lokalen LLM.

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

### Was Sie erwarten können, wenn Sie es ausführen

1. Die Konsole gibt die ursprünglichen und überarbeiteten Absätze aus.  
2. `output.docx` erscheint neben `input.docx`.  
3. Beim Öffnen der Datei wird der neue formelle Absatz nach dem Original eingefügt (oder ersetzt, wenn Sie zum alternativen Code gewechselt haben).

---

## Umgang mit gängigen Edge Cases

| Situation | Lösung |
|-----------|--------|
| **Leerer oder nur aus Leerzeichen bestehender Absatz** | Prüfen Sie `string.IsNullOrWhiteSpace` vor dem Prompten (siehe Schritt 3). |
| **LLM gibt einen Fehler oder leere Zeichenkette zurück** | `PromptAsync` in ein `try/catch` einbetten und auf den Originaltext zurückgreifen. |
| **Mehrere Absätze müssen umgeschrieben werden** | Durchlaufen Sie `sourceDocument.GetChildNodes(NodeType.Paragraph, true)` und wenden Sie dieselbe Prompt‑Logik an. |
| **Große Dokumente verursachen Latenz** | Absätze stapeln und in einer einzigen Anfrage senden (Prompt bis zu 4 KB pro Aufruf). |
| **Nicht‑ASCII‑Zeichen werden verzerrt** | Stellen Sie sicher, dass der LLM‑Endpunkt UTF‑8 verwendet (die meisten modernen Modelle tun dies). |

---

## Nächste Schritte & verwandte Themen

- **Prompt large language model** mit umfangreicheren Anweisungen (z. B. Stilrichtlinien, Längenbegrenzungen).  
- Verwenden Sie **call local llm** in einer Web‑API, um Dokument‑Automatisierung als Service bereitzustellen.  
- Untersuchen Sie **load word document** in parallelen Streams für Hochdurchsatz‑Szenarien.  
- Kombinieren Sie diesen Ansatz mit **rewrite text automatically** für die Massen‑E‑Mail‑Erstellung oder Bericht‑Standardisierung.  

Wenn Sie tiefer einsteigen möchten, sehen Sie sich die Aspose‑Dokumentation zu **document merging** und die Ollama‑API‑Referenz für benutzerdefinierte Sampling‑Parameter an.

---

## Fazit

Wir haben Ihnen gerade gezeigt, wie Sie **connect to local llm** aus C# heraus, **prompt large language model**, **load word document**, **call local llm** und **rewrite text automatically** – alles in einer einzigen ausführbaren Konsolen‑App – verwenden können. Das Muster skaliert: Tauschen Sie den Prompt aus, iterieren Sie über Absätze oder stellen Sie die Logik über einen ASP.NET‑Endpunkt bereit. Die zentrale Erkenntnis ist, dass lokale KI‑Modelle eng mit klassischen Dokument‑Verarbeitungs‑Bibliotheken integriert werden können, was Ihnen leistungsstarke Automatisierung ermöglicht, ohne Ihre vertrauenswürdige On‑Prem‑Umgebung zu verlassen.

Haben Sie Fragen zu Threading,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}