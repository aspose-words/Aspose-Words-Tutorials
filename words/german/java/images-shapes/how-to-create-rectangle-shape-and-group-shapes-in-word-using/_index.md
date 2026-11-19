---
category: general
date: 2026-11-18
description: Erfahren Sie, wie Sie mit C# ein Rechteck in einem Word‑Dokument erstellen.
  Der Leitfaden behandelt außerdem das Festlegen der Formgröße, das Festlegen der
  Position der Form und das Gruppieren von Formen in Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: de
lastmod: 2026-11-18
og_description: Erstelle ein Rechteck in einer Word-Datei mit C# und lerne, die Formabmessungen
  festzulegen, die Position der Form zu setzen und Formen in Word zu gruppieren.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Rechteck erstellen und Formen in Word mit C# gruppieren
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man in Word mit C# ein Rechteck erstellt und Formen gruppiert
url: /de/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So erstellen Sie ein Rechteck‑Shape und gruppieren Shapes in Word mit C#

Wenn Sie ein **rectangle shape** in einem Word‑Dokument erstellen müssen, zeigt Ihnen dieses Tutorial eine komplette, sofort ausführbare Lösung. Sie sehen, wie Sie die Größe eines Shapes festlegen, die Position eines Shapes setzen und Shapes in Word gruppieren, sodass sie sich wie ein einzelnes Objekt verhalten.

Die Arbeit mit Shapes ist ein häufiges Anliegen beim programmatischen Erzeugen von Berichten, Rechnungen oder Diagrammen. Am Ende dieses Leitfadens können Sie eine `.docx`‑Datei erzeugen, die ein Rechteck, eine Ellipse und einen gruppierten Container enthält – alles erstellt mit Aspose.Words für .NET.

## Voraussetzungen

- .NET 6.0 SDK oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`)
- Ein Code‑Editor oder eine IDE (Visual Studio, VS Code, Rider usw.)

Keine zusätzlichen Bibliotheken sind erforderlich.

## So erstellen Sie ein rectangle shape und gruppieren Shapes in Word

Die Kernschritte sind:

1. **Ein leeres Dokument** und einen `DocumentBuilder` erstellen.
2. **Ein `GroupShape`** einfügen, das die einzelnen Shapes enthält.
3. **Ein Rechteck‑Shape** erstellen, seine Abmessungen festlegen und zur Gruppe hinzufügen.
4. **Ein Ellipse‑Shape** erstellen, Größe und Position festlegen und zur Gruppe hinzufügen.
5. **Das Dokument speichern**.

Jeder Schritt wird unten erklärt, und der komplette Quellcode folgt nach der Erklärung.

### Schritt 1: Dokument und Builder initialisieren

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` eine fluente API zum Einfügen von Inhalten bereitstellt. Die Initialisierung ist zwingend erforderlich, bevor Sie Shapes hinzufügen können.

### Schritt 2: Ein GroupShape einfügen

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

Ein `GroupShape` funktioniert wie ein Container; alle untergeordneten Shapes bewegen sich gemeinsam. Dies ist die empfohlene Methode, um **shapes in Word zu gruppieren**, wenn Sie kollektive Transformationen benötigen (z. B. Verschieben, Drehen oder Löschen).

### Schritt 3: Das Rechteck erstellen und seine Größe festlegen

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Hier **create rectangle shape** und **set shape size**, indem wir `Width` und `Height` zuweisen. In Aspose.Words werden Größen in Punkten angegeben (1 pt ≈ 1/72 in). Das explizite Festlegen der Abmessungen stellt sicher, dass das Rechteck exakt wie gewünscht erscheint.

### Schritt 4: Die Ellipse erstellen, Abmessungen festlegen und positionieren

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

Die **set shape dimensions** für die Ellipse sind für Breite und Höhe identisch, wodurch ein perfekter Kreis entsteht. Die `Left`‑Eigenschaft demonstriert **set shape position**: Die Ellipse beginnt 120 pt rechts vom Ursprung der Gruppe, sodass sie das Rechteck nicht überlappt.

### Schritt 5: Das Dokument speichern

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Beim Speichern wird die Word‑Datei auf die Festplatte geschrieben. Sie können `GroupShape.docx` in Microsoft Word öffnen, um zu prüfen, dass Rechteck und Ellipse gruppiert und korrekt positioniert sind.

## Größen und Abmessungen von Shapes – ein tieferer Blick

- **Punkte vs. Zoll**: 72 pt = 1 in. Wenn Sie Zoll bevorzugen, multiplizieren Sie mit 72 (z. B. `2.5 * 72` für 2,5 in).
- **Automatisches Skalieren**: Wenn Sie `Width` oder `Height` weglassen, verwendet das Shape seine Standardgröße. Setzen Sie **set shape size** explizit, um Layout‑Überraschungen zu vermeiden.
- **Seitenverhältnis**: Bei Shapes wie `Ellipse` sorgt das Gleiche von `Width` und `Height` für ein kreisförmiges Aussehen.

## Positionierung eines Shapes in Word

Die Eigenschaften `Left` und `Top` steuern den Versatz des Shapes innerhalb seines Containers (der Gruppe oder der Seite). Positive Werte verschieben das Shape nach rechts/unten; negative Werte nach links/oben. Beim Gruppieren sind die Positionen relativ zum Ursprung der Gruppe, was Layout‑Berechnungen vereinfacht.

## Shapes in Word mit Aspose.Words gruppieren

Das Gruppieren ist essenziell, wenn mehrere Shapes als eine Einheit agieren sollen. Das `GroupShape`‑Objekt:

- Unterstützt `AppendChild`, um jedes `Shape` (Rechteck, Ellipse, Bild usw.) hinzuzufügen.
- Ermöglicht das Verschieben, Drehen oder Löschen der gesamten Gruppe mit einem einzigen Aufruf.
- Behält die Positionen der Kind‑Shapes relativ zur Gruppe bei, wodurch komplexe Diagramme leichter zu handhaben sind.

**Pro‑Tipp:** Nachdem Sie alle Kind‑Shapes hinzugefügt haben, können Sie `Width`, `Height`, `Left` und `Top` der Gruppe anpassen, um die gesamte Sammlung in einem Schritt neu zu positionieren.

## Komplettes ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie kopieren, einfügen und ausführen können. Es enthält alle `using`‑Direktiven, eine `Main`‑Methode und Kommentare, die jede Zeile erläutern.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Erwartetes Ergebnis:** Nach dem Ausführen des Programms erscheint `GroupShape.docx` im Ausführungsordner. Öffnen Sie die Datei in Word, Sie sehen ein Rechteck (100 pt × 50 pt) links und eine Ellipse (80 pt × 80 pt) 120 pt rechts davon, beide innerhalb eines einzigen gruppierten Objekts.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Screenshot eines Word‑Dokuments, das ein gruppiertes Rechteck‑ und Ellipse‑Shape zeigt, erstellt mit C#" }

*Das obige Bild veranschaulicht das Endergebnis; das Rechteck und die Ellipse sind als eine Gruppe auswählbar.*

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich mehr als zwei Shapes hinzufügen?** | Ja. Rufen Sie `group.AppendChild(yourShape)` für jedes zusätzliche Shape auf. |
| **Wie kann ich die Gruppe drehen?** | Verwenden Sie `group.RotationAngle = 45;` (Grad) nach dem Hinzufügen aller Kinder. |
| **Wie ändere ich die Hintergrundfarbe der Gruppe?** | Setzen Sie `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Funktioniert das mit .doc‑Dateien?** | Aspose.Words unterstützt `.doc` und `.docx`. Der gleiche Code funktioniert; ändern Sie lediglich die Dateierweiterung im `Save`. |
| **Gibt es Auswirkungen auf den Speicher bei vielen gruppierten Shapes?** | Das Gruppieren selbst verursacht nur geringen Overhead. Hauptsächlich ist die Gesamtzahl der Shapes relevant; halten Sie sie für sehr große Dokumente im Rahmen. |

## Fazit

In diesem Tutorial haben Sie gelernt, wie Sie ein **rectangle shape** in einer Word‑Datei mit C# erstellen, **set shape size**, **set shape dimensions**, **set shape position** festlegen und schließlich **shapes in Word gruppieren** mit Aspose.Words. Das vollständige Beispiel demonstriert einen sauberen, wartbaren Ansatz, den Sie auf komplexere Diagramme, Charts oder benutzerdefinierte Grafiken erweitern können.

Als Nächstes könnten Sie:

- Text in Shapes einfügen (`Shape.TextPath.Text = "Hello"`).
- Bilder in ein `GroupShape` einfügen.
- Die gruppierten Shapes mit `doc.Save("output.pdf")` nach PDF exportieren.

Experimentieren Sie gern mit verschiedenen Größen, Positionen und zusätzlichen Shape‑Typen, um den Anforderungen Ihres Projekts gerecht zu werden. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}