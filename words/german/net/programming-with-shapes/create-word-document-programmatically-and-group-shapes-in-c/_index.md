---
category: general
date: 2026-08-10
description: Erstellen Sie ein Word‑Dokument programmgesteuert mit Aspose.Words, lernen
  Sie, wie Sie mehrere Formen in Word gruppieren, ein Rechteck zu Word hinzufügen
  und eine Gruppierung von Formen in C# erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- group multiple shapes word
- add rectangle to word
- how to create group shape
language: de
lastmod: 2026-08-10
og_description: Erstellen Sie ein Word‑Dokument programmgesteuert mit Aspose.Words.
  Dieser Leitfaden zeigt Ihnen, wie Sie mehrere Formen in Word gruppieren, ein Rechteck
  in Word hinzufügen und ein Nur‑Text‑Inhaltssteuerelement einbetten, alles in C#.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and ellipse with
  a plain‑text content control
og_title: Word-Dokument programmgesteuert erstellen – Formen in C# gruppieren
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  headline: Create word document programmatically and group shapes in C#
  type: TechArticle
- description: Create word document programmatically using Aspose.Words, learn how
    to group multiple shapes word, add rectangle to word, and create a group shape
    in C#.
  name: Create word document programmatically and group shapes in C#
  steps:
  - name: – Initialize the document and builder
    text: The `Document` object represents the entire DOCX file, while `DocumentBuilder`
      provides a convenient API to add content. Initializing them is the first requirement
      whenever you **create word document programmatically**.
  - name: – Create a group shape container
    text: A `Shape` with `ShapeType.Group` acts as a canvas that can hold other shapes.
      Setting `Width` and `Height` defines the bounding box for the group. This is
      the core of **how to create group shape** in Aspose.Words.
  - name: – Add a rectangle to word
    text: A rectangle is created with `ShapeType.Rectangle`. Its `Left` and `Top`
      properties position it relative to the group’s origin. This step demonstrates
      **add rectangle to word** and shows how you can control exact placement.
  - name: – Add an ellipse (circle) to the group
    text: An ellipse is added the same way as the rectangle, but with `ShapeType.Ellipse`.
      The `Left = 210` moves it to the right of the rectangle, creating a visually
      distinct pair of shapes inside the same group.
  - name: – Insert the completed group shape into the document
    text: '`builder.InsertNode(groupShape)` places the whole group at the current
      cursor location. Because the group already contains its children, you do not
      need additional insert calls for the rectangle or ellipse.'
  - name: – Create a plain‑text StructuredDocumentTag (SDT)
    text: A StructuredDocumentTag is a content control that end users can fill in
      when the document is opened in Word. Setting `Title = "CustomerName"` gives
      the control a meaningful identifier, which is useful for later data extraction.
  - name: – Save the document
    text: '`doc.Save("GroupAndSDT.docx")` writes the file to disk. The resulting DOCX
      contains the grouped shapes and the SDT. Opening the file in Microsoft Word
      will show a rectangle next to a circle, both selectable as a single object,
      followed by a placeholder “Enter name here …”.'
  - name: Using different shape types
    text: You can replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other
      `ShapeType` (e.g., `ShapeType.Polygon`, `ShapeType.Line`). The grouping logic
      remains identical.
  - name: Setting fill color and borders
    text: '```csharp rectangleShape.FillColor = System.Drawing.Color.LightBlue; rectangleShape.StrokeColor
      = System.Drawing.Color.DarkBlue; ellipseShape.FillColor = System.Drawing.Color.LightCoral;
      ``` Adding fill and stroke improves visual distinction, especially when the
      document is shared with non‑technical'
  - name: Rotating the entire group
    text: '```csharp groupShape.Rotation = 45; // rotates both shapes together ```
      Rotating the group is more efficient than rotating each child individually.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Word‑Dokument programmgesteuert erstellen und Formen in C# gruppieren
url: /de/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument programmgesteuert erstellen und Formen gruppieren in C#

Wenn Sie **ein Word-Dokument programmgesteuert erstellen** möchten, zeigt Ihnen dieses Tutorial, wie Sie eine DOCX‑Datei mit Aspose.Words bauen und **mehrere Formen in Word gruppieren**. Wir behandeln außerdem **ein Rechteck zu Word hinzufügen** und **wie man eine Gruppenform erstellt**, die sowohl ein Rechteck als auch eine Ellipse enthält, plus ein einfaches StructuredDocumentTag für Benutzereingaben.

Am Ende haben Sie eine einsatzbereite Word‑Datei, die eine gruppierte Rechteck‑Ellipse‑Form und ein Inhaltssteuerelement enthält, in das ein Benutzer einen Namen eingeben kann. Nach dem Ausführen des Codes ist keine manuelle Bearbeitung in Word mehr nötig.

## Was Sie benötigen

- .NET 6.0 oder höher (das Beispiel zielt auf .NET 6 ab, aber jede aktuelle .NET‑Version funktioniert)
- Eine Aspose.Words for .NET‑Lizenz (die kostenlose Testversion reicht für Tests)
- Visual Studio 2022 oder eine beliebige C#‑IDE Ihrer Wahl
- Grundlegende Kenntnisse der C#‑Syntax

## Word-Dokument programmgesteuert erstellen – Gesamtablauf

Der Prozess besteht aus drei logischen Phasen:

1. **Initialisieren** eines `Document` und eines `DocumentBuilder` – die Grundlage für jede Word‑Datei, die Sie erzeugen.
2. **Eine Gruppenform erstellen**, die ein Rechteck und eine Ellipse enthält – demonstriert **mehrere Formen in Word gruppieren** und **wie man eine Gruppenform erstellt**.
3. **Ein StructuredDocumentTag (SDT) einfügen** – ein einfaches Text‑Inhaltssteuerelement, das Endbenutzern das Ausfüllen von Daten ermöglicht und **ein Rechteck zu Word hinzufügen** als Teil des Gesamtlayouts illustriert.

Unten finden Sie den vollständigen, ausführbaren Code sowie eine Schritt‑für‑Schritt‑Erklärung.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1 – Initialize the document and builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2 – Create a group shape container
            Shape groupShape = new Shape(doc, ShapeType.Group)
            {
                Width = 400,
                Height = 200
            };

            // Step 3 – Add a rectangle to the group
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100,
                Left = 0,
                Top = 0
            };
            groupShape.GroupShape.AddChild(rectangleShape);

            // Step 4 – Add an ellipse (circle) to the group
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse)
            {
                Width = 100,
                Height = 100,
                Left = 210, // Position next to the rectangle
                Top = 0
            };
            groupShape.GroupShape.AddChild(ellipseShape);

            // Step 5 – Insert the completed group shape into the document
            builder.InsertNode(groupShape);

            // Step 6 – Create a plain‑text StructuredDocumentTag for user input
            StructuredDocumentTag sdtTag = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Block)
            {
                Title = "CustomerName"
            };
            builder.InsertNode(sdtTag);
            builder.Writeln("Enter name here …");

            // Step 7 – Save the document
            doc.Save("GroupAndSDT.docx");
            Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Schritt 1 – Dokument und Builder initialisieren
Das `Document`‑Objekt repräsentiert die gesamte DOCX‑Datei, während `DocumentBuilder` eine bequeme API zum Hinzufügen von Inhalten bereitstellt. Die Initialisierung ist die erste Voraussetzung, wann immer Sie **ein Word-Dokument programmgesteuert erstellen**.

> **Pro‑Tipp:** Wenn Sie dasselbe Dokument über mehrere Vorgänge hinweg wiederverwenden wollen, behalten Sie eine einzige `DocumentBuilder`‑Instanz, um unnötige Objektinstanziierungen zu vermeiden.

### Schritt 2 – Einen Gruppenform‑Container erstellen
Ein `Shape` mit `ShapeType.Group` fungiert als Leinwand, die andere Formen aufnehmen kann. Durch Setzen von `Width` und `Height` wird das Begrenzungsrechteck der Gruppe definiert. Dies ist der Kern von **wie man eine Gruppenform erstellt** in Aspose.Words.

> **Randfall:** Ist die Breite der Gruppe kleiner als die kombinierte Breite ihrer Kind‑Shapes, werden die Kinder abgeschnitten. Stellen Sie sicher, dass die Gruppe groß genug ist, um jedes Kind‑Shape zu enthalten.

### Schritt 3 – Ein Rechteck zu Word hinzufügen
Ein Rechteck wird mit `ShapeType.Rectangle` erstellt. Die Eigenschaften `Left` und `Top` positionieren es relativ zum Ursprung der Gruppe. Dieser Schritt demonstriert **ein Rechteck zu Word hinzufügen** und zeigt, wie Sie die genaue Platzierung steuern können.

> **Häufiger Fehler:** Vergessen Sie, `Left`/`Top` zu setzen, erscheint das Rechteck am Standardursprung der Gruppe (0,0) und kann andere Kinder überlappen.

### Schritt 4 – Eine Ellipse (Kreis) zur Gruppe hinzufügen
Eine Ellipse wird auf dieselbe Weise wie das Rechteck hinzugefügt, jedoch mit `ShapeType.Ellipse`. `Left = 210` verschiebt sie nach rechts vom Rechteck, sodass ein visuell unterscheidbares Paar von Formen innerhalb derselben Gruppe entsteht.

> **Warum eine Gruppe verwenden?** Durch Gruppieren können Sie beide Formen später mit einer einzigen Operation verschieben, drehen oder skalieren und behalten dabei ihr relatives Layout bei.

### Schritt 5 – Die fertiggestellte Gruppenform in das Dokument einfügen
`builder.InsertNode(groupShape)` platziert die gesamte Gruppe an der aktuellen Cursor‑Position. Da die Gruppe bereits ihre Kinder enthält, sind keine zusätzlichen Einfüge‑Aufrufe für das Rechteck oder die Ellipse nötig.

### Schritt 6 – Ein einfaches StructuredDocumentTag (SDT) erstellen
Ein StructuredDocumentTag ist ein Inhaltssteuerelement, das Endbenutzer beim Öffnen des Dokuments in Word ausfüllen können. Durch `Title = "CustomerName"` erhält das Steuerelement einen aussagekräftigen Bezeichner, was für spätere Datenauszüge nützlich ist.

> **Warum ein einfaches Text‑SDT?** Es beschränkt die Eingabe auf reinen Text und verhindert versehentliche Formatierungen, die nachgelagerte Verarbeitung stören könnten.

### Schritt 7 – Das Dokument speichern
`doc.Save("GroupAndSDT.docx")` schreibt die Datei auf die Festplatte. Die resultierende DOCX‑Datei enthält die gruppierten Formen und das SDT. Öffnen Sie die Datei in Microsoft Word, sehen Sie ein Rechteck neben einem Kreis, beide als ein einzelnes Objekt auswählbar, gefolgt von einem Platzhalter „Enter name here …“.

#### Erwartete Ausgabe
- Eine Datei namens **GroupAndSDT.docx** im Ausführungsordner.
- In Word: eine gruppierte Form (Rechteck + Ellipse), die Sie als Einheit bewegen können.
- Direkt unter der Gruppe ein grau schattiertes Inhaltssteuerelement, das den Benutzer auffordert, einen Namen einzugeben.

## Zusätzliche Varianten und bewährte Vorgehensweisen

### Verwendung verschiedener Formtypen
Sie können `ShapeType.Rectangle` oder `ShapeType.Ellipse` durch jeden anderen `ShapeType` ersetzen (z. B. `ShapeType.Polygon`, `ShapeType.Line`). Die Gruppierungslogik bleibt identisch.

### Füllfarbe und Rahmen setzen
```csharp
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```
Das Hinzufügen von Füllung und Kontur verbessert die visuelle Unterscheidung, besonders wenn das Dokument mit nicht‑technischen Stakeholdern geteilt wird.

### Die gesamte Gruppe drehen
```csharp
groupShape.Rotation = 45; // rotates both shapes together
```
Das Drehen der Gruppe ist effizienter als das Drehen jedes einzelnen Kindes.

### Export nach PDF
Falls Sie eine PDF‑Version benötigen, rufen Sie einfach auf:
```csharp
doc.Save("GroupAndSDT.pdf", SaveFormat.Pdf);
```
Alle gruppierten Formen und das SDT (als Textfeld gerendert) erscheinen im PDF.

## Häufige Stolperfallen und wie man sie vermeidet

| Symptom | Ursache | Lösung |
|---------|---------|--------|
|         |         |        |
|         |         |        |

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}