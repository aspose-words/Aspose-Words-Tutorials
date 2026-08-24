---
category: general
date: 2026-08-23
description: Erfahren Sie, wie Sie Formen in C# mit Aspose.Words gruppieren. Der Leitfaden
  behandelt außerdem, wie man ein Rechteck einfügt und Formen zu Word für komplexe
  Dokumente hinzufügt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: de
lastmod: 2026-08-23
og_description: Wie man Formen in C# mit Aspose.Words gruppiert. Folgen Sie diesem
  vollständigen Tutorial, um ein Rechteck-Shape einzufügen, Shapes zu Word hinzuzufügen
  und mehrere Shapes effizient zu gruppieren.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Wie man Formen in C# gruppiert – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Wie man Formen in C# mit Aspose.Words gruppiert
url: /de/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in C# mit Aspose.Words gruppiert

Wenn Sie **how to group shapes** in einem Word-Dokument programmgesteuert benötigen, zeigt Ihnen dieses Tutorial die genauen Schritte mit Aspose.Words für .NET. Egal, ob Sie einen Berichtsgenerator, eine Vorlagen‑Engine oder ein Diagramm‑Tool erstellen, Sie lernen, wie Sie eine Gruppe starten, ein Rechteck einfügen und **add shapes word**‑Inhalte hinzufügen, ohne Ihren Code zu verlassen.

Sie sehen außerdem, wie Sie **group multiple shapes** zusammenfassen, was wichtig ist, wenn Sie eine Sammlung von Objekten als einzelne Einheit verschieben, drehen oder formatieren möchten. Das untenstehende Beispiel funktioniert mit der neuesten Aspose.Words‑Version 24.x und erfordert nur .NET 6 oder höher.

## Voraussetzungen

- .NET 6 SDK (oder jede von Aspose.Words unterstützte .NET‑Version)
- Visual Studio 2022 oder VS Code
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`)
- Grundlegende Kenntnisse in C# und dem Aspose.Words‑Objektmodell

> **Pro‑Tipp:** Verwenden Sie die kostenlose Evaluierungslizenz von Aspose, um Wasserzeichen‑Beschränkungen während des Tests zu vermeiden.

## So gruppieren Sie Formen mit Aspose.Words

Unten finden Sie ein vollständiges, ausführbares Programm, das **how to start group**, das Hinzufügen eines Rechtecks und das Abschließen der Gruppe demonstriert. Der Code folgt dem gleichen logischen Ablauf wie das von Ihnen bereitgestellte Snippet, fügt jedoch Kontext, Fehlerbehandlung und Kommentare zur Klarheit hinzu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Warum jeder Schritt wichtig ist

| Schritt | Zweck | Wie es zu den Schlüsselwörtern passt |
|------|---------|--------------------------------|
| **Create a new blank document** | Stellt eine leere Leinwand für Form‑Operationen bereit. | Legt die Grundlage für **add shapes word** später. |
| **Initialize DocumentBuilder** | Der Builder ist die primäre API zum Einfügen von Objekten. | Wird benötigt, bevor Sie **how to start group** ausführen können. |
| **StartGroupShape** | Beginnt einen logischen Container; alle nachfolgenden Formen werden Mitglieder dieser Gruppe. | Antwortet direkt auf **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Platziert einzelne Formen innerhalb der Gruppe. Der Aufruf für das Rechteck erfüllt **insert rectangle shape**; die Textform erfüllt **add shapes word**. | Demonstriert **group multiple shapes**. |
| **EndGroupShape** | Schließt die Gruppe ab, sodass Sie sie als Einheit verschieben oder formatieren können. | Vollendet den **how to group shapes**‑Ablauf. |

## Einfügen einer Rechteckform – tieferer Einblick

Die Methode `InsertShape` akzeptiert ein `ShapeType`‑Enum, Breite und Höhe. Um **insert rectangle shape** mit benutzerdefiniertem Styling einzufügen, können Sie das Beispiel erweitern:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Warum stilisieren?** Styling sorgt dafür, dass das Rechteck beim späteren Verschieben der Gruppe hervorsticht. Es zeigt zudem, dass Form‑Eigenschaften *vor* dem Schließen der Gruppe gesetzt werden können.

## Hinzufügen von Word‑Ebene‑Formen (add shapes word)

Wenn Sie Text direkt in eine Form einbetten müssen – häufig „WordArt“ oder „Textfeld“ genannt – verwenden Sie `ShapeType.TextPlainText`. Nach dem Einfügen können Sie Text in die Form schreiben mit `DocumentBuilder.Writeln` oder indem Sie auf die `TextBox`‑Eigenschaft der Form zugreifen:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Damit wird das Schlüsselwort **add shapes word** erfüllt und gezeigt, wie Text mit der Gruppe mitreisen kann.

## Gruppieren mehrerer Formen – praktische Szenarien

Wenn Sie **group multiple shapes**, können Sie sie wie ein einzelnes Objekt für Positionierung, Drehung oder Skalierung behandeln. Zum Beispiel können Sie nach dem Schließen der Gruppe die gesamte Gruppe verschieben:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Oder die Gruppe drehen:

```csharp
group.Rotation = 45; // degrees
```

Diese Vorgänge sind nur möglich, weil die Formen dieselbe übergeordnete Gruppe teilen.

## Umgang mit Randfällen

1. **Verschachtelte Gruppen** – Aspose.Words ermöglicht Gruppen innerhalb von Gruppen. Um eine verschachtelte Gruppe zu erstellen, rufen Sie `StartGroupShape` erneut auf, bevor Sie `EndGroupShape` für die innere Gruppe aufrufen.
2. **Leere Gruppen** – Wenn Sie eine Gruppe starten, aber nie eine Form einfügen, erstellt `EndGroupShape` trotzdem einen leeren Container. Das ist harmlos, kann jedoch die Dateigröße leicht erhöhen.
3. **Kompatibilität** – Das erzeugte DOCX funktioniert mit Word 2010 und neuer. Ältere Versionen können Gruppierungs‑Metadaten ignorieren, daher sollten Sie stets mit der Ziel‑Word‑Version testen.

## Vollständige Quelldatei zur Referenz

Speichern Sie das Folgende als `Program.cs` in einem .NET‑Konsolenprojekt. Der Code kompiliert und läuft ohne Änderungen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Erwartete Ausgabe

Wenn Sie `GroupedShapes.docx` in Microsoft Word öffnen, sehen Sie:

- Ein hellkorallenfarbenes Rechteck, eine Ellipse und ein Textfeld – alle visuell miteinander verbunden.
- Das Auswählen eines beliebigen Teils der Gruppe wählt auch die gesamte Gruppe aus (ein einzelner Begrenzungsrahmen erscheint).
- Das Verschieben oder Drehen der Gruppe bewegt alle drei Formen zusammen.

## Häufig gestellte Fragen

**F: Kann ich Formen gruppieren, die bereits im Dokument existieren?**  
A: Ja. Rufen Sie die vorhandenen `Shape`‑Objekte ab, rufen Sie `builder.StartGroupShape()` auf, fügen Sie sie mit `builder.InsertShape(existingShape)` erneut ein und rufen Sie anschließend `EndGroupShape()` auf.

**F: Wirkt sich das Gruppieren auf das zugrunde liegende XML aus?**  
A: Aspose.Words fügt ein `<w:grpSp>`‑Element hinzu, das den `<w:sp>`‑Knoten jeder Form enthält. Dies entspricht vollständig der Office Open XML‑Spezifikation.

**F: Was, wenn ich später entgruppieren muss?**  
A: Es gibt keine direkte „ungroup“‑API, aber Sie können über die Kindformen der Gruppe (`group.GroupShape.Children`) iterieren und sie in den Dokumentkörper kopieren.

## Nächste Schritte

Jetzt, da Sie **how to group shapes** kennen, sollten Sie diese verwandten Themen erkunden:

- **Komplexe Formatierung auf gruppierte Formen anwenden** – lernen Sie, wie Sie Farbverläufe, Schatteneffekte und Linienstile festlegen.
- **Gruppierte Formen als Bilder exportieren** – verwenden Sie `Shape.GetShapeRenderer().Save(...)`, um eine Gruppe zu rasterisieren.
- **Dynamische Diagramme erstellen** – kombinieren Sie datenbasierte Positionierung mit Gruppierung, um automatisch Flussdiagramme zu erzeugen.

Jedes dieser Themen baut auf der hier behandelten Grundlage auf und hilft Ihnen, reichhaltigere, interaktivere Word‑Dokumente zu erstellen.

---

*Viel Spaß beim Coden! Wenn Ihnen diese Anleitung nützlich war, teilen Sie sie mit Kollegen oder geben Sie dem Repository, das das Beispielprojekt enthält, einen Stern.*

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Formen in Word‑Dokumenten mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}