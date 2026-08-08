---
category: general
date: 2026-08-07
description: Wie man Formen in Word mit Aspose.Words gruppiert und Formen zu einem
  Word‑Dokument mit C# hinzufügt. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung
  für sauberen, wiederverwendbaren Code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- add shapes to word document
language: de
lastmod: 2026-08-07
og_description: Wie man Formen in Word mit Aspose.Words für .NET gruppiert. Dieses
  Tutorial zeigt, wie man Formen zu einem Word‑Dokument hinzufügt, sie gruppiert und
  die Datei mit klarem C#‑Code speichert.
og_image_alt: Screenshot of a rectangle and ellipse grouped in a Word document created
  with Aspose.Words
og_title: Wie man Formen in Word gruppiert – kurzer C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  headline: How to group shapes in Word and add shapes to Word document
  type: TechArticle
- description: How to group shapes in Word with Aspose.Words and add shapes to Word
    document using C#. Follow this step‑by‑step guide for clean, reusable code.
  name: How to group shapes in Word and add shapes to Word document
  steps:
  - name: Create a document and a builder
    text: A `Document` object represents the entire DOCX file. `DocumentBuilder` provides
      a convenient API for editing the document.
  - name: Add the rectangle shape
    text: A rectangle is created by specifying `ShapeType.Rectangle`. Width, height,
      and location are set in points (1 pt ≈ 1/72 in).
  - name: Add the ellipse shape
    text: The ellipse uses `ShapeType.Ellipse`. Its size and position are independent
      of the rectangle, which allows you to control the final layout of the group.
  - name: Group the two shapes
    text: '`GroupShape` acts as a container that treats its children as a single object.
      This is the essential operation for **how to group shapes in Word**.'
  - name: Insert the grouped shape into the document
    text: '`DocumentBuilder.InsertNode` places the `GroupShape` at the current cursor
      location. Because we have not moved the builder, the group appears at the start
      of the first page.'
  - name: Save the document
    text: Finally, write the DOCX file to disk. Use a full path that your application
      can write to.
  - name: Expected output
    text: Open `GroupShape.docx`. You will see a single visual object that contains
      a blue rectangle on the left and a green ellipse on the right. Selecting the
      object in Word highlights both shapes simultaneously—proof that **how to group
      shapes in Word** succeeded.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Wie man Formen in Word gruppiert und Formen zu einem Word‑Dokument hinzufügt
url: /de/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in Word gruppiert und Formen zu einem Word-Dokument hinzufügt

Wenn Sie **wie man Formen in Word gruppiert** benötigen, führt Sie diese Anleitung durch den gesamten Prozess mit Aspose.Words für .NET. Sie lernen außerdem **wie man Formen zu einem Word-Dokument hinzufügt** mit wenigen Zeilen C#‑Code, sodass das Ergebnis für jedes Reporting‑ oder Templating‑Szenario bereit ist.

Das Tutorial deckt alles ab, was Sie benötigen: erforderliche NuGet‑Pakete, eine vollständige Quelldatei und eine Erklärung, warum jeder Schritt wichtig ist. Am Ende können Sie ein DOCX erzeugen, das ein Rechteck und eine Ellipse enthält, die zu einer einzigen Gruppierung kombiniert sind.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 SDK oder neuer installiert  
* Visual Studio 2022 (oder jede IDE, die .NET unterstützt)  
* Aspose.Words für .NET NuGet‑Paket (`Aspose.Words`) – die kostenlose Testversion funktioniert zum Testen, aber eine Lizenz entfernt Evaluationswasserzeichen  

Diese Elemente sind die einzigen externen Abhängigkeiten für **add shapes to Word document**.

## Wie man Formen in Word gruppiert

Der Kern der Lösung besteht darin, einzelne Formen zu erstellen, sie auf der Seite zu platzieren und sie anschließend in ein `GroupShape` zu verpacken. Die folgenden Schritte spiegeln die logische Reihenfolge des Codes wider.

### Schritt 1: Erstellen eines Dokuments und eines Builders

Ein `Document`‑Objekt repräsentiert die gesamte DOCX‑Datei. `DocumentBuilder` bietet eine bequeme API zum Bearbeiten des Dokuments.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create an empty Word document
Document doc = new Document();

// DocumentBuilder lets you insert nodes, text, and shapes
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist*: Das `Document` ist der Container für alle Word‑Elemente. Der `DocumentBuilder` verfolgt die aktuelle Cursor‑Position, was erforderlich ist, wenn Sie später die gruppierte Form einfügen.

### Schritt 2: Rechteckform hinzufügen

Ein Rechteck wird erstellt, indem `ShapeType.Rectangle` angegeben wird. Breite, Höhe und Position werden in Punkten gesetzt (1 pt ≈ 1/72 in).

```csharp
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;               // 100 pt wide
rectangleShape.Height = 50;               // 50 pt tall
rectangleShape.Left = 0;                  // X‑coordinate
rectangleShape.Top = 0;                   // Y‑coordinate
rectangleShape.StrokeColor = Color.Blue; // Outline color
```

*Warum das wichtig ist*: Das Setzen von `StrokeColor` macht die Form sichtbar, wenn das Dokument geöffnet wird. Sie könnten die Form auch mit `FillColor` füllen, falls ein durchgängiger Innenbereich gewünscht ist.

### Schritt 3: Ellipsenform hinzufügen

Die Ellipse verwendet `ShapeType.Ellipse`. Größe und Position sind unabhängig vom Rechteck, sodass Sie das endgültige Layout der Gruppe steuern können.

```csharp
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;
ellipseShape.Height = 80;
ellipseShape.Left = 120;                  // Placed to the right of the rectangle
ellipseShape.Top = 0;
ellipseShape.StrokeColor = Color.Green;
```

*Warum das wichtig ist*: Durch die Positionierung der Ellipse bei `Left = 120` überschneidet sie das Rechteck nicht, wodurch die Gruppe visuell unterscheidbar wird.

### Schritt 4: Die beiden Formen gruppieren

`GroupShape` fungiert als Container, der seine Kinder als ein einziges Objekt behandelt. Dies ist die wesentliche Operation für **how to group shapes in Word**.

```csharp
GroupShape groupShape = new GroupShape(doc);
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);
```

*Warum das wichtig ist*: Durch das Gruppieren können Sie beide Formen gemeinsam verschieben, skalieren oder drehen. Jede Transformation, die auf `groupShape` angewendet wird, wird auf die Kind‑Elemente übertragen.

### Schritt 5: Die gruppierte Form in das Dokument einfügen

`DocumentBuilder.InsertNode` platziert das `GroupShape` an der aktuellen Cursor‑Position. Da wir den Builder nicht verschoben haben, erscheint die Gruppe am Anfang der ersten Seite.

```csharp
builder.InsertNode(groupShape);
```

*Warum das wichtig ist*: Das direkte Einfügen des Knotens vermeidet die Notwendigkeit eines separaten Absatzes oder einer Tabellenzelle. Die Gruppe wird Teil des Dokumenten‑Flows.

### Schritt 6: Dokument speichern

Abschließend schreiben Sie die DOCX‑Datei auf die Festplatte. Verwenden Sie einen vollständigen Pfad, in den Ihre Anwendung schreiben darf.

```csharp
doc.Save(@"C:\Temp\GroupShape.docx");
```

*Warum das wichtig ist*: `doc.Save` finalisiert alle Änderungen. Die resultierende Datei kann in Microsoft Word, LibreOffice oder jedem Viewer, der DOCX unterstützt, geöffnet werden.

## Vollständige Quelldatei

Kopieren Sie den Code unten in ein neues Konsolenprojekt (`dotnet new console`) und führen Sie es aus. Das Programm erstellt eine Datei namens `GroupShape.docx`, die ein gruppiertes Rechteck und eine Ellipse enthält.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeGrouping
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Define a rectangle shape
            Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
            rectangleShape.Width = 100;
            rectangleShape.Height = 50;
            rectangleShape.Left = 0;
            rectangleShape.Top = 0;
            rectangleShape.StrokeColor = Color.Blue;

            // Step 3: Define an ellipse shape
            Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
            ellipseShape.Width = 80;
            ellipseShape.Height = 80;
            ellipseShape.Left = 120;
            ellipseShape.Top = 0;
            ellipseShape.StrokeColor = Color.Green;

            // Step 4: Group the two shapes together
            GroupShape groupShape = new GroupShape(doc);
            groupShape.AppendChild(rectangleShape);
            groupShape.AppendChild(ellipseShape);

            // Step 5: Insert the grouped shape into the document
            builder.InsertNode(groupShape);

            // Step 6: Save the document
            doc.Save(@"C:\Temp\GroupShape.docx");
        }
    }
}
```

### Erwartete Ausgabe

Öffnen Sie `GroupShape.docx`. Sie sehen ein einzelnes visuelles Objekt, das ein blaues Rechteck links und eine grüne Ellipse rechts enthält. Wenn Sie das Objekt in Word auswählen, werden beide Formen gleichzeitig hervorgehoben — ein Beweis dafür, dass **how to group shapes in Word** erfolgreich war.

## Häufige Fragen und Randfälle

* **Kann ich mehr als zwei Formen hinzufügen?**  
  Ja. Rufen Sie `groupShape.AppendChild` für jede zusätzliche `Shape` auf, bevor Sie die Gruppe einfügen.

* **Was, wenn ich die Gruppe drehen muss?**  
  Setzen Sie `groupShape.RotationAngle = 45;` (Winkel in Grad) nach dem Aufbau der Gruppe.

* **Muss ich `doc.UpdatePageLayout()` aufrufen?**  
  Nicht für dieses Szenario. Das Layout wird automatisch aktualisiert, wenn das Dokument gespeichert wird.

* **Wie wirkt sich die Lizenzierung auf den Code aus?**  
  Mit einer gültigen Aspose.Words‑Lizenz (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) enthält das erzeugte Dokument kein Evaluations‑Wasserzeichen.

## Fazit

Sie wissen jetzt **wie man Formen in Word gruppiert** und **wie man Formen zu einem Word‑Dokument hinzufügt** mithilfe von Aspose.Words für .NET. Das Tutorial behandelte das Erstellen eines Dokuments, das Definieren einzelner Formen, das Gruppieren, das Einfügen der Gruppe und das Speichern der Datei.  

Ab hier können Sie experimentieren mit:

* Hinzufügen von Textfeldern oder Bildern zur Gruppe  
* Ändern von Füllfarben, Linienstilen oder Schatteneffekten  
* Gruppieren von Formen innerhalb von Tabellen oder Kopf‑/Fußzeilen  

Diese Erweiterungen ermöglichen es Ihnen, anspruchsvolle Word‑Templates programmgesteuert zu erstellen, während der Code sauber und wartbar bleibt. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Formen in Word‑Dokumenten mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Word‑Dokument mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}