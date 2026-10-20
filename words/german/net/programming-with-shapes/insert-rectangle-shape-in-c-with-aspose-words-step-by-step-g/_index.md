---
category: general
date: 2026-08-07
description: Fügen Sie in C# mit Aspose.Words ein Rechteck ein und lernen Sie, wie
  Sie die Form ausblenden, die Füllfarbe festlegen und das Rechteck effizient zu einem
  Word‑Dokument hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: de
lastmod: 2026-08-07
og_description: Rechteckform in ein Word‑Dokument mit C# einfügen. Erfahren Sie, wie
  Sie die Form ausblenden, die Füllfarbe festlegen und eine Rechteckform mit Aspose.Words
  hinzufügen.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Rechteckform in C# einfügen – vollständiges Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Rechteckform in C# mit Aspose.Words einfügen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in C# mit Aspose.Words – Schritt‑für‑Schritt‑Anleitung

Wenn Sie **eine Rechteckform** in ein Word‑Dokument aus C# einfügen müssen, zeigt Ihnen dieses Handbuch genau, wie das geht. Sie sehen, wie Sie die Füllfarbe festlegen, die Form ausblenden, sodass sie im endgültigen Layout nicht erscheint, und die Datei speichern – alles mit nur wenigen Code‑Zeilen.

In den folgenden Abschnitten behandeln wir alles, was Sie wissen müssen: Voraussetzungen, die vollständige Code‑Auflistung, Erklärungen zu jedem Schritt und Tipps für gängige Variationen, wie das erneute Sichtbarmachen der Form oder die Verwendung einer anderen Farbe. Am Ende können Sie **eine Rechteckform** zu jeder .docx‑Datei programmgesteuert **hinzufügen**.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* **Aspose.Words for .NET** (Version 23.10 oder neuer). Sie können es über NuGet installieren:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK oder neuer, auf Ihrem Rechner installiert.
* Grundlegendes Verständnis von C# und Visual Studio (oder einer anderen IDE Ihrer Wahl).

Es sind keine zusätzlichen Bibliotheken erforderlich – die formbezogenen APIs sind Teil des Kern‑Aspose.Words‑Pakets.

## Rechteckform mit Aspose.Words einfügen

Der Kern der Lösung ist ein kurzes, eigenständiges Programm, das ein leeres Dokument erstellt, ein Rechteck einfügt, es färbt, ausblendet und anschließend die Datei speichert. Unten finden Sie den vollständigen Quellcode mit Inline‑Kommentaren, die das *Warum* hinter jeder Zeile erklären.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Was jeder Schritt bewirkt

| Schritt | Grund |
|---------|-------|
| **Create a new document** | Stellt eine saubere Leinwand bereit; Sie können auch ein vorhandenes .docx laden, indem Sie einen Dateipfad an `new Document(path)` übergeben. |
| **Initialize DocumentBuilder** | `DocumentBuilder` ist der hoch‑level Helfer, der Ihnen das Einfügen von Text, Tabellen und Formen ermöglicht, ohne sich mit low‑level Knotenbäumen befassen zu müssen. |
| **Insert rectangle shape** | Die Methode `InsertShape` gibt ein `Shape`‑Objekt zurück, das Sie weiter anpassen können (Größe, Position, Rahmen usw.). |
| **Set fill color** | Die Eigenschaft `FillColor` steuert die Innenfarbe; Sie können jeden `Color`‑Wert verwenden (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)` usw.). |
| **Hide the shape** | `Hidden = true` weist Word an, die Form während des Layouts zu ignorieren, während sie weiterhin im XML‑Dokument bleibt. Das ist der Standardweg, unsichtbare Objekte zu speichern. |
| **Save the document** | Persistiert die Änderungen in einer .docx‑Datei. Die gespeicherte Datei enthält die ausgeblendete Rechteckform. |

## Wie man die Füllfarbe für eine Form festlegt

Das Ändern der Füllfarbe ist so einfach wie das Zuweisen eines `System.Drawing.Color` zur Eigenschaft `FillColor`. Wenn Sie einen benutzerdefinierten Farbton benötigen, verwenden Sie `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Why this matters*: Die Füllfarbe wird im XML der Form gespeichert (`<w:fill>`‑Attribut). Wenn die Form ausgeblendet ist, existiert die Farbe weiterhin, was für nachgelagerte Verarbeitung nützlich sein kann (z. B. das Extrahieren von Metadaten anhand von Farbcodes).

## Wie man eine Form im endgültigen Dokument ausblendet

Das `Hidden`‑Flag ist eine boolesche Eigenschaft der Klasse `Shape`. Wird es auf `true` gesetzt, wird die Form vom Word‑Layout‑Engine ignoriert.

```csharp
rectangleShape.Hidden = true;
```

**Common pitfalls**

* **Hidden vs. Visible** – Wenn Sie die Form später wieder anzeigen müssen, setzen Sie einfach `Hidden = false`.
* **Compatibility** – Ältere Word‑Versionen (vor 2007) können ausgeblendete Zeichenobjekte anders behandeln. Aspose.Words bewahrt die Kompatibilität, indem das Flag im entsprechenden OOXML‑Element gespeichert wird.

## Wie man Formen programmgesteuert einfügt

Obwohl das Beispiel ein Rechteck verwendet, funktioniert die gleiche `InsertShape`‑Methode für viele andere Formen (Ellipse, Dreieck, Linie usw.). Das erste Argument ist ein `ShapeType`‑Enum‑Wert:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Tip**: Wenn Sie die Form an einer bestimmten Stelle auf der Seite platzieren müssen, verwenden Sie `builder.MoveTo`, um den Einfügepunkt vor dem Aufruf von `InsertShape` zu setzen.

## Rechteckform zu einem bestehenden Dokument hinzufügen

Oft werden Sie eine Vorlage erweitern, anstatt von Grund auf neu zu beginnen. Ersetzen Sie Schritt 1 durch:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Alle nachfolgenden Schritte bleiben identisch, und das Rechteck wird dort eingefügt, wo der Cursor des Builders positioniert ist (standardmäßig am Ende des Dokuments).

## Umgang mit Randfällen und Variationen

### 1. Die Form wieder sichtbar machen

Wenn ein späterer Teil Ihres Workflows das ausgeblendete Rechteck sichtbar machen muss, können Sie das Flag umschalten:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Einen Rand (Strich) hinzufügen

Eine ausgeblendete Form kann dennoch einen sichtbaren Rand besitzen, wenn Sie sie anzeigen. Setzen Sie die Eigenschaften `LineColor` und `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Das Rechteck absolut positionieren

Für präzise Layout‑Kontrolle wechseln Sie den `WrapType` der Form zu `WrapType.Inline` (Standard) oder `WrapType.TopBottom` und passen die Eigenschaften `Left`/`Top` an:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Eine andere Maßeinheit verwenden

Aspose.Words arbeitet in Punkten (1 pt = 1/72 inch). Wenn Sie Zentimeter bevorzugen, konvertieren Sie zuerst:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Vollständiges ausführbares Beispiel

Unten finden Sie das *vollständige* Programm, das Sie kopieren, einfügen und ausführen können. Es enthält alle notwendigen `using`‑Direktiven und verwendet absolute Pfade, die Sie an Ihre Umgebung anpassen sollten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Expected result**: Die Datei `HiddenRectangleShape.docx` öffnet sich in Microsoft Word ohne sichtbare Form, aber das ausgeblendete Rechteck ist im Dokument‑XML vorhanden. Sie können seine Existenz prüfen, indem Sie die .docx‑Datei als ZIP‑Archiv öffnen und `word/document.xml` nach einem `<w:shape>`‑Element mit den Attributen `w:fill="yellow"` und `w:hidden="true"` durchsuchen.

## Fazit

Sie wissen jetzt, wie Sie **eine Rechteckform** in ein Word‑Dokument mit C# und Aspose.Words **einfügen**, **die Füllfarbe setzen** und **die Form ausblenden** können, sodass sie im endgültigen Layout unsichtbar bleibt. Das gleiche Muster funktioniert für andere Formtypen, benutzerdefinierte Farben und bestehende Vorlagen. Experimentieren Sie mit Rändern, absoluter Positionierung und verschiedenen Maßeinheiten, um die Form exakt an Ihre Anforderungen anzupassen.

### Nächste Schritte

* Erkunden Sie **wie man Formen** innerhalb von Tabellen oder Kopf‑/Fußzeilen für Wasserzeichen einfügt.
* Kombinieren Sie **Rechteckform hinzufügen** mit Inhaltssteuerelementen, um dynamische Platzhalter zu erstellen.
* Prüfen Sie Aspose.Words’ **shape manipulation**‑API für erweiterte Funktionen wie Drehung, Farbverläufe und SVG‑Import.

Passen Sie den Code gerne an Ihr eigenes Projekt an und teilen Sie uns in den Kommentaren mit, welche formbezogene Herausforderung Sie als Nächstes gelöst haben!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Handbuch gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Schatten zu Word‑Form in C# hinzufügen](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}