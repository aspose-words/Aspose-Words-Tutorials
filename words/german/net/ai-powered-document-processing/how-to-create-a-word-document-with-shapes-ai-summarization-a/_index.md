---
category: general
date: 2026-11-25
description: Erfahren Sie, wie Sie ein Word‑Dokument erstellen, ein Rechteck hinzufügen,
  das Dokument mit KI zusammenfassen, Text mit KI übersetzen und das Dokument mit
  Aspose.Words als DOCX speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: de
lastmod: 2026-11-25
og_description: Erstelle ein Word‑Dokument, füge eine Rechteckform hinzu, fasse das
  Dokument mit KI zusammen, übersetze den Text mit KI und speichere das Dokument als
  DOCX – alles in einem einzigen C#‑Tutorial.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Erstelle ein Word‑Dokument mit Formen, KI‑Zusammenfassung und Übersetzung
  in C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Wie man ein Word‑Dokument mit Formen, KI‑Zusammenfassung und Übersetzung in
  C# erstellt
url: /de/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Word‑Dokument mit Formen, KI‑Zusammenfassung und Übersetzung in C# erstellt

Wenn Sie **programmgesteuert ein Word‑Dokument erstellen** müssen, zeigt Ihnen diese Anleitung genau, wie es geht. Mit Aspose.Words für .NET lernen Sie, **ein Rechteck‑Shape hinzuzufügen**, einen KI‑Dienst aufzurufen, um das **Dokument mit KI zusammenzufassen**, einen Absatz mit **Text mithilfe von KI zu übersetzen** und schließlich das **Dokument als DOCX zu speichern**.

Viele Entwickler haben Schwierigkeiten, Dokumenten‑Automatisierung und moderne KI‑Funktionen zu kombinieren. Am Ende dieses Tutorials besitzen Sie ein einzelnes, eigenständiges C#‑Projekt, das eine vollständig formatierte *.docx*-Datei erzeugt, inklusive einer visuellen Form, KI‑generierter Zusammenfassung und mehrsprachigem Inhalt.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- .NET 6.0 SDK oder neuer installiert  
- Visual Studio 2022 (oder eine beliebige C#‑IDE)  
- Eine Aspose.Words für .NET‑Lizenz (oder einen kostenlosen Evaluierungsschlüssel)  
- Internetzugang für die KI‑Zusammenfassungs‑ und Übersetzungs‑Aufrufe  

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` und `Aspose.Words.AI` hinaus erforderlich.

## Schritt 1: Projekt einrichten und erforderliche Pakete hinzufügen

Erstellen Sie ein neues Konsolen‑Projekt und binden Sie die Aspose.Words‑Bibliotheken ein.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Pro‑Tipp:** Wenn Sie den Evaluierungs‑Modus verwenden, rufen Sie `Aspose.Words.License.SetLicense("Aspose.Words.lic");` früh im `Main`‑Methoden‑Body auf, um Wasserzeichen zu vermeiden.

## Schritt 2: Dokument initialisieren – das Kernstück von **create word document**

Die erste ausführbare Code‑Zeile erzeugt ein frisches **Word‑Document**‑Objekt. Dieses Objekt ist die Leinwand für alle nachfolgenden Operationen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

Der `DocumentBuilder` vereinfacht das Einfügen von Text, Formen und Steuerelementen, ohne dass Sie manuell mit Low‑Level‑Node‑Bäumen arbeiten müssen.

## Schritt 3: **Add rectangle shape** zum Dokument hinzufügen

Ein Rechteck‑Shape kann als visueller Platzhalter, Hintergrund für ein Label oder einfache Grafik verwendet werden. Wir erstellen zuerst ein `GroupShape` und fügen anschließend ein `Rectangle` darin ein.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

Das Rechteck ist 100 Punkte breit und 50 Punkte hoch. Da es sich innerhalb eines `GroupShape` befindet, können Sie später weitere Elemente (z. B. Textfelder) hinzufügen, ohne Layout‑Kollisionen befürchten zu müssen.

## Schritt 4: Einen plain‑text StructuredDocumentTag (SDT) einfügen

StructuredDocumentTag‑Objekte sind nützlich für Inhaltssteuerelemente, die später an Datenquellen gebunden werden können.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

Das Flag `true` markiert das Tag als **repeating**‑Steuerelement, was für Vorlagen praktisch ist.

## Schritt 5: Ein ActiveX‑CommandButton‑Steuerelement hinzufügen (optionale UI)

Falls das erzeugte Dokument in einer Umgebung verwendet wird, die ActiveX unterstützt, können Sie einen Button einbetten.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Dieser Schritt ist optional; Sie können ihn entfernen, wenn Ihre Zielgruppe das Dokument niemals in einer Windows‑Umgebung verwendet.

## Schritt 6: **Summarize document with AI**

Aspose.Words.AI bietet einen praktischen Wrapper um Large‑Language‑Model‑Dienste. Hier rufen wir `DocumentSummarizer.Summarize` mit dem OpenAI‑Backend auf.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

Die Methode analysiert den aktuellen Node‑Baum, extrahiert die relevantesten Sätze und gibt einen knappen Absatz zurück. Das ist das Kernstück der **summarize document with AI**‑Funktionalität.

## Schritt 7: **Translate text using AI**

Als nächstes demonstrieren wir, wie ein Beispiel‑String von Englisch nach Französisch übersetzt wird. Die Methode `Translator.Translate` ruft intern ein Google‑AI‑Modell auf.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Sie können `Language.French` durch jeden unterstützten Sprach‑Enum‑Wert ersetzen, um die mehrsprachige Dokumentenerstellung on‑the‑fly zu ermöglichen.

## Schritt 8: **Save document as DOCX**

Abschließend speichern wir das bearbeitete Dokument auf dem Datenträger. Die `Save`‑Methode schreibt automatisch eine *.docx*-Datei, wenn Sie die `.docx`‑Erweiterung angeben.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

Die Datei `Result.docx` enthält nun:

- Ein Rechteck‑Shape innerhalb eines GroupShape  
- Ein plain‑text Inhaltssteuerelement (SDT)  
- Einen ActiveX‑CommandButton (falls Sie Schritt 5 beibehalten haben)  
- Einen KI‑generierten Zusammenfassungs‑Absatz  
- Eine französische Übersetzung von „Hello world“

Sie können die Datei in Microsoft Word öffnen, um jedes Element zu prüfen.

## Vollständiger Quellcode

Unten finden Sie das komplette, sofort ausführbare Programm. Kopieren Sie es in `Program.cs` und führen Sie `dotnet run` aus.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Erwartete Ausgabe

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Wenn Sie `Result.docx` öffnen, sehen Sie das Rechteck‑Shape oben, den SDT‑Platzhalter, den Button, den Zusammenfassungs‑Absatz und die französische Übersetzung als Klartext.

## Fazit

Sie wissen jetzt, wie man **ein Word‑Dokument** von Grund auf **erstellt**, **ein Rechteck‑Shape hinzufügt**, **das Dokument mit KI zusammenfasst**, **Text mit KI übersetzt** und **das Dokument als DOCX speichert** – alles mit wenigen prägnanten C#‑Zeilen. Dieses Muster skaliert: Sie können die fest codierten Strings durch dynamische Daten ersetzen, weitere Formen oder Diagramme hinzufügen und den KI‑Anbieter ändern, indem Sie die Parameter von `SummarizerOptions` oder `Translator` anpassen.

### Was kommt als Nächstes?

- Erkunden Sie Varianten von **add rectangle shape**: Füllfarbe, Linienstil ändern oder Text innerhalb der Form hinzufügen.  
- Nutzen Sie **summarize document with AI** für größere Dokumente, um automatisch Executive Summaries zu erzeugen.  
- Erweitern Sie **translate text using AI**, um ganze Absätze oder Tabellen stapelweise für mehrsprachige Berichte zu übersetzen.  
- Kombinieren Sie Aspose.Words‑Chart‑APIs, um Datenvisualisierungen neben KI‑generierten Insights einzubetten.  

Viel Spaß beim Experimentieren und teilen Sie Ihre Ergebnisse in den Kommentaren oder auf GitHub. Happy coding!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungs‑Ansätze in Ihren eigenen Projekten zu erkunden.

- [Create a blank word document and add a rectangle shape](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Add Text Watermark in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}