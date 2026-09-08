---
category: general
date: 2026-09-08
description: Erstelle ein Rechteck in einem Word‑Dokument mit C#. Lerne, die Größe
  der Form festzulegen, mehrere Formen zu gruppieren und ein leeres Word‑Dokument
  programmgesteuert zu erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- set shape size
- group multiple shapes
- create blank word document
language: de
lastmod: 2026-09-08
og_description: Erstelle ein Rechteck in einem Word-Dokument mit C#. Dieser Leitfaden
  zeigt, wie man die Größe der Form festlegt, mehrere Formen gruppiert und programmgesteuert
  ein leeres Word-Dokument erstellt.
og_image_alt: Screenshot showing how to create rectangle shape in a Word document
  using C#
og_title: Rechteckform erstellen und Formen in Word mit C# gruppieren
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Create rectangle shape in a Word document with C#. Learn to set shape
    size, group multiple shapes, and create blank Word document programmatically.
  headline: Create rectangle shape and group shapes in Word using C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Rechteckform erstellen und Formen in Word mit C# gruppieren
url: /de/net/programming-with-shapes/create-rectangle-shape-and-group-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform erstellen und Formen in Word gruppieren mit C#

Wenn Sie **eine Rechteckform** in einer Word‑Datei **erstellen** möchten, bietet Ihnen dieses Tutorial eine vollständige, sofort ausführbare Lösung. Sie sehen, wie Sie die Formgröße festlegen, mehrere Formen gruppieren und ein leeres Word‑Dokument von Grund auf erstellen – alles mit der Aspose.Words for .NET‑Bibliothek.

Die programmgesteuerte Arbeit mit Word‑Dokumenten fühlt sich oft an, als müsste man viele kleine Details jonglieren. Am Ende dieses Leitfadens besitzen Sie eine einzelne Methode, die eine `.docx`‑Datei erzeugt, die ein Rechteck und eine Ellipse gruppiert enthält, bereit für weitere Bearbeitung oder den Druck.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
* Eine lizenzierte Kopie von **Aspose.Words for .NET** (Sie können einen kostenlosen Evaluierungsschlüssel verwenden)
* Eine IDE wie Visual Studio 2022 oder Visual Studio Code
* Grundlegende Kenntnisse der C#‑Syntax

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Schritt 1: Leeres Word‑Dokument erstellen

Der erste Schritt besteht darin, ein leeres Dokument zu erzeugen, das die Formen aufnehmen wird. Damit wird die Anforderung *leeres Word‑Dokument erstellen* erfüllt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty Word document
Document doc = new Document();

// The document already contains one section and one empty paragraph
// You can add additional sections later if needed
```

Ein leeres Dokument liefert Ihnen eine saubere Arbeitsfläche. Das `Document`‑Objekt repräsentiert die gesamte `.docx`‑Datei, und `FirstSection.Body.FirstParagraph` ist der Standard‑Einfügepunkt für neue Knoten.

## Schritt 2: Rechteckform erstellen

Jetzt können Sie das Rechteck hinzufügen. Hier findet die **create rectangle shape**‑Operation statt.

```csharp
// Initialize a DocumentBuilder to simplify node insertion
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape instance
Shape rectangle = new Shape(doc, ShapeType.Rectangle);

// Set the rectangle's size (width and height) and position
rectangle.Width  = 100;   // points; 1 point = 1/72 inch
rectangle.Height = 50;
rectangle.Left   = 10;    // distance from the left edge of the container
rectangle.Top    = 20;    // distance from the top edge of the container

// Optional: give the rectangle a visible border
rectangle.StrokeColor = Color.Blue;
rectangle.FillColor   = Color.LightGray;
```

Durch das direkte Setzen der Abmessungen wird das Schlüsselwort **set shape size** beantwortet. Alle Größenwerte werden in Punkten angegeben, was eine präzise Kontrolle über das Aussehen der Form im endgültigen Dokument ermöglicht.

## Schritt 3: Eine zusätzliche Form (Ellipse) erstellen

Ein typischer Anwendungsfall ist das Kombinieren mehrerer Formen. Hier fügen wir eine Ellipse hinzu, die später denselben Container teilen wird.

```csharp
// Create an ellipse shape instance
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width  = 80;
ellipse.Height = 80;
ellipse.Left   = 120;   // Position it to the right of the rectangle
ellipse.Top    = 30;

// Give the ellipse a distinct border and fill
ellipse.StrokeColor = Color.DarkGreen;
ellipse.FillColor   = Color.LightYellow;
```

Beide Formen sind zu diesem Zeitpunkt noch unabhängig. Der nächste Schritt zeigt, wie man **multiple shapes gruppiert**.

## Schritt 4: Formen in Word gruppieren

Das Gruppieren von Formen ermöglicht es Ihnen, sie als eine Einheit zu verschieben, zu skalieren oder zu formatieren. Damit werden die Anforderungen **group shapes in word** und **group multiple shapes** erfüllt.

```csharp
// Create a GroupShape container that will hold the rectangle and ellipse
GroupShape group = new GroupShape(doc);

// Define the container's bounding box – it must be large enough for all children
group.Bounds = new RectangleF(0, 0, 300, 200);

// Append the group to the document's first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(group);

// Add the rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

Die Eigenschaft `GroupShape.Bounds` bestimmt das Koordinatensystem für die Kindformen. Indem Sie das Rechteck und die Ellipse in dieselbe `GroupShape` einfügen, können Sie sie später gemeinsam mit einem einzigen Aufruf verschieben oder drehen.

## Schritt 5: Dokument speichern

Abschließend schreiben Sie das Dokument auf die Festplatte. Die Datei enthält die gerade erstellten gruppierten Formen.

```csharp
// Choose an output path – ensure the directory exists and you have write permission
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");

// Save the document in DOCX format
doc.Save(outputPath);
```

Nach dem Ausführen des Programms öffnen Sie `GroupedShapes.docx` in Microsoft Word. Sie sollten ein Rechteck und eine Ellipse sehen, die zusammen gruppiert sind; das Auswählen einer Form wählt automatisch die andere aus, was den Erfolg der Gruppierung bestätigt.

## Vollständiger Quellcode

Kopieren Sie das folgende komplette Programm in ein neues Konsolen‑App‑Projekt und führen Sie es aus. Weiterer Code ist nicht nötig.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System;
using System.Drawing;
using System.IO;

class Program
{
    static void Main()
    {
        // Step 1: create a blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: create rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width  = 100,
            Height = 50,
            Left   = 10,
            Top    = 20,
            StrokeColor = Color.Blue,
            FillColor   = Color.LightGray
        };

        // Step 3: create ellipse shape
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width  = 80,
            Height = 80,
            Left   = 120,
            Top    = 30,
            StrokeColor = Color.DarkGreen,
            FillColor   = Color.LightYellow
        };

        // Step 4: group the shapes
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new RectangleF(0, 0, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);
        group.AppendChild(rectangle);
        group.AppendChild(ellipse);

        // Step 5: save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupedShapes.docx");
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Erwartete Ausgabe

Das Ausführen des Programms erzeugt `GroupedShapes.docx`. Beim Öffnen der Datei in Word sehen Sie:

* Ein **Rechteck** (100 pt × 50 pt) mit blauem Rand und hellgrauer Füllung.
* Eine **Ellipse** (80 pt × 80 pt) mit dunkelgrünem Rand und hellgelber Füllung.
* Beide Formen befinden sich in einer einzigen Gruppe, sodass das Verschieben einer Form die andere mitbewegt.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich mehr als zwei Formen zur Gruppe hinzufügen?** | Ja. Erstellen Sie weitere `Shape`‑Objekte und rufen Sie für jedes `group.AppendChild(yourShape)` auf. |
| **Wie kann ich die Gruppe rotieren?** | Setzen Sie `group.RotationAngle = 45;` (Grad). Alle Kindformen rotieren gemeinsam. |
| **Ist es möglich, Formen nach dem Speichern des Dokuments zu gruppieren?** | Sie müssen die Dokumentstruktur vor dem Speichern ändern; andernfalls müssten Sie die Datei laden, die Formen finden und die Gruppe neu erstellen. |
| **Muss ich irgendwelche Objekte freigeben?** | Aspose.Words verwaltet seine eigenen Ressourcen, aber Sie sollten `FileStream`‑Objekte freigeben, wenn Sie Streams manuell öffnen. |
| **Funktioniert der Code auch mit dem .doc (binären) Format?** | Ja, ändern Sie zu `doc.Save("output.doc")`. Das Gruppierungsverhalten ist identisch. |

## Fazit

Sie wissen jetzt, wie Sie **eine Rechteckform erstellen**, **die Formgröße festlegen** und **mehrere Formen gruppieren** können, und das alles in einer Word‑Datei mit C#. Dieser Ansatz ermöglicht es Ihnen, programmgesteuert komplexe Diagramme, Wasserzeichen oder vorlagenbasierte Berichte zu erstellen, ohne manuelle Nachbearbeitung.

### Nächste Schritte

* Erkunden Sie **group shapes in word** weiter, indem Sie Textfelder oder Bilder zur selben Gruppe hinzufügen.
* Verwenden Sie das `SetShapeSize`‑Muster, um Dimensionen dynamisch basierend auf dem Seitenlayout zu berechnen.
* Kombinieren Sie diese Technik mit Seriendruckfeldern, um personalisierte Dokumente in großem Umfang zu erzeugen.

Experimentieren Sie gern mit verschiedenen Formtypen, Farben und Gruppentransformationen. Viel Spaß beim Coden!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Erstellen einer Gruppierungsform in einem Word‑Dokument mit Aspose.Words für .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Leeres Word‑Dokument mit schattierter Rechteckform erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Word‑Dokument mit einer schattierten Rechteckform erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}