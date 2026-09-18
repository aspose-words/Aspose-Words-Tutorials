---
category: general
date: 2026-09-18
description: Erstellen Sie ein Rechteck in einem Word‑Dokument mit C#. Erfahren Sie,
  wie Sie mehrere Formen hinzufügen, Formen zu einer Gruppe zusammenfassen und die
  Gruppierung mit Aspose.Words einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: de
lastmod: 2026-09-18
og_description: Erstellen Sie ein Rechteck in einer Word-Datei mit C#. Dieser Leitfaden
  zeigt, wie man mehrere Formen hinzufügt, Formen zu einer Gruppe hinzufügt und eine
  Gruppenform mit Aspose.Words einfügt.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Rechteckform erstellen und Formen gruppieren in C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Rechteckform erstellen und mehrere Formen in C# gruppieren
url: /de/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform erstellen und mehrere Formen in C# gruppieren

Wenn Sie in einem Word‑Dokument **eine Rechteckform erstellen** müssen, zeigt dieses Tutorial eine vollständige Lösung. Sie sehen, wie man **mehrere Formen hinzufügt**, **Formen zu einer Gruppe hinzufügt** und **eine Gruppenform einfügt** mithilfe der Aspose.Words‑API für .NET.

Das Arbeiten mit Formen ist ein häufiges Erfordernis beim programmgesteuerten Erstellen von Berichten, Verträgen oder Marketing‑Materialien. Am Ende dieses Leitfadens verfügen Sie über eine ausführbare C#‑Konsolenanwendung, die eine `.docx`‑Datei erzeugt, die ein Rechteck, eine Ellipse und eine Gruppe enthält, die beide Formen hält.

Die einzigen Voraussetzungen sind ein aktuelles .NET‑SDK (6.0 oder neuer) und eine lizenzierte Kopie von Aspose.Words für .NET. Weitere Werkzeuge werden nicht benötigt.

## Voraussetzungen

- .NET 6.0 SDK oder neuer  
- Aspose.Words für .NET (NuGet‑Paket `Aspose.Words`)  
- Grundlegende Kenntnisse der C#‑Syntax  

Sie können das Paket mit dem folgenden Befehl installieren:

```bash
dotnet add package Aspose.Words
```

## Schritt 1: Rechteckform mit Aspose.Words erstellen

Der erste Schritt besteht darin, ein `Shape`‑Objekt vom Typ `Rectangle` zu erstellen. Dieses Objekt stellt das visuelle Rechteck dar, das im Dokument erscheint.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Warum das wichtig ist:** `ShapeType.Rectangle` weist Aspose.Words an, ein geometrisches Rechteck zu rendern. Das Festlegen von `Width` und `Height` definiert seine Größe in Punkten (1 Punkt = 1/72 Zoll). Das Hinzufügen von Füll‑ und Kontur‑Farben macht die Form sichtbar, ohne dass zusätzliche Formatierungen erforderlich sind.

## Schritt 2: Mehrere Formen zum Dokument hinzufügen

Nach dem Rechteck können Sie beliebig viele weitere Formen erstellen. In diesem Beispiel fügen wir eine Ellipse hinzu, um zu demonstrieren, wie **mehrere Formen hinzufügen** funktioniert.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Warum das wichtig ist:** Jeder Aufruf von `new Shape` erzeugt ein unabhängiges Zeichenobjekt. Durch das sequentielle Einfügen bauen Sie eine Sammlung von Formen auf, die später gruppiert oder einzeln positioniert werden können.

## Schritt 3: Formen zu einer Gruppe hinzufügen

Das Gruppieren von Formen vereinfacht die Layout‑Verwaltung, da die Gruppe wie ein einzelner Knoten wirkt. Dieser Schritt zeigt, wie man **Formen zu einer Gruppe hinzufügt** mithilfe von `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Warum das wichtig ist:** `GroupShape` fungiert als Container. Wenn Sie die Gruppe verschieben, drehen oder skalieren, folgen alle untergeordneten Formen automatisch. Das Begrenzungs‑Rechteck (200 × 200 Punkte) definiert den Koordinatenraum für die Kindformen.

## Schritt 4: Gruppenform in das Dokument einfügen

Da die Gruppe nun das Rechteck und die Ellipse enthält, müssen Sie **die Gruppenform** an der gewünschten Stelle **einfügen**. Der Builder hat die leere Gruppe bereits platziert, aber Sie können sie bei Bedarf auch an anderer Stelle einfügen.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Warum das wichtig ist:** Das Anpassen von `Left` und `Top` verschiebt die gesamte Gruppe innerhalb der Seite. Das Speichern des Dokuments schreibt die Form‑Hierarchie in eine `.docx`‑Datei, die in Microsoft Word, LibreOffice oder jedem kompatiblen Viewer geöffnet werden kann.

## Vollständiges ausführbares Beispiel

Unten finden Sie das vollständige Programm, das alle Schritte kombiniert. Kopieren Sie den Code in ein neues Konsolenprojekt und führen Sie ihn aus, um `GroupShapeExample.docx` zu erzeugen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Erwartete Ausgabe:**  
Beim Öffnen von `GroupShapeExample.docx` wird eine einzelne Gruppe angezeigt, die ein hellblaues Rechteck und eine hellkorallenfarbene Ellipse enthält, beide innerhalb eines 200 × 200 Punkte‑Containers positioniert. Die Gruppe kann in Word als ein Objekt ausgewählt werden, was bestätigt, dass **Formen zu einer Gruppe hinzufügen** erfolgreich war.

## Häufige Variationen und Sonderfälle

| Situation | Empfohlene Anpassung |
|-----------|----------------------|
| Verschiedene Formtypen (z. B. `ShapeType.Line`) | Erstellen Sie die Form mit dem gewünschten `ShapeType` und setzen Sie deren Geometrie entsprechend. |
| Erforderlich, eine Form zu drehen | Verwenden Sie `shape.Rotation = 45;` (Grad) bevor Sie sie zur Gruppe hinzufügen. |
| Größere Dokumente mit vielen Gruppen | Verwenden Sie eine einzelne `DocumentBuilder`‑Instanz wieder; vermeiden Sie das Erstellen eines neuen Builders für jede Gruppe, um den Speicherverbrauch zu reduzieren. |
| Speichern als PDF statt DOCX | Rufen Sie `doc.Save("output.pdf", SaveFormat.Pdf);` nach dem Einfügen der Gruppe auf. |

**Pro‑Tipp:** Setzen Sie immer explizite `Left`‑ und `Top`‑Werte für die Gruppe, wenn Sie eine präzise Platzierung benötigen. Wenn Sie diese weglassen, erbt die Gruppe die aktuelle Cursor‑Position des Builders, was zu unerwarteten Layout‑Ergebnissen führen kann.

## Fazit

Sie wissen jetzt, wie man **eine Rechteckform erstellt**, **mehrere Formen hinzufügt**, **Formen zu einer Gruppe hinzufügt** und **eine Gruppenform** in ein Word‑Dokument mit C# einfügt. Das vollständige Beispiel demonstriert den gesamten Arbeitsablauf von der Dokumenterstellung bis zum Speichern der finalen Datei.  

Als Nächstes können Sie verwandte Themen wie **Positionierung von Formen relativ zu Text**, **Anwenden von Textumbruch** und **Exportieren von gruppierten Formen nach PDF** erkunden. Diese Erweiterungen ermöglichen Ihnen, anspruchsvolle, programmgesteuerte Dokumentlayouts mit Aspose.Words zu erstellen.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Leeres Word‑Dokument mit schattierter Rechteckform erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}