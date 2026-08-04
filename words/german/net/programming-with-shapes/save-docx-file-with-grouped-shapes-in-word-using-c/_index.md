---
category: general
date: 2026-08-04
description: Speichere eine DOCX-Datei programmgesteuert, während du ein Rechteck‑Shape
  hinzufügst und Shapes in Word gruppierst. Lerne, Shape‑Abmessungen festzulegen und
  ein Textfeld programmgesteuert zu erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: de
lastmod: 2026-08-04
og_description: Speichern Sie eine docx-Datei mit C# durch Hinzufügen einer Rechteckform,
  Gruppieren von Formen in Word, Festlegen von Formabmessungen und programmatisches
  Erstellen eines Textfelds.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: DOCX-Datei mit gruppierten Formen in Word speichern – C# Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: DOCX-Datei mit gruppierten Formen in Word mit C# speichern
url: /de/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# DOCX-Datei mit gruppierten Formen in Word mit C# speichern

Wenn Sie eine **docx-Datei speichern** müssen, die mehrere zusammen angeordnete Formen enthält, zeigt Ihnen diese Anleitung, wie Sie dies mit C# tun können. Sie lernen, wie man **ein Rechteck form hinzufügt**, mehrere Formen in einem Word‑Dokument gruppiert, **Form‑Abmessungen festlegt** und **ein Textfeld programmgesteuert erstellt**. Die Lösung funktioniert mit der neuesten Aspose.Words für .NET und läuft auf .NET 6 oder höher.

Das Tutorial führt Sie durch jeden Schritt, von der Projekt‑Einrichtung bis zum abschließenden Aufruf `doc.Save`. Am Ende haben Sie ein wiederverwendbares Code‑Snippet, das Sie in jedes Konsolen‑ oder ASP.NET‑Projekt einfügen können. Keine externen Skripte oder manuelle Bearbeitung der DOCX‑Datei sind erforderlich.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie folgendes haben:

* .NET 6 SDK (oder neuer) installiert.
* Eine gültige Lizenz für **Aspose.Words for .NET** (die kostenlose Testversion funktioniert zum Testen).
* Visual Studio 2022, VS Code oder jede IDE, die .NET‑Projekte erstellen kann.

Der Code verwendet nur den Aspose.Words‑Namespace, sodass keine zusätzlichen NuGet‑Pakete erforderlich sind.

## DOCX-Datei mit gruppierten Formen in Word speichern

Der Kern der Lösung besteht darin, ein `GroupShape` zu erstellen, das ein Rechteck und ein Textfeld enthält, dann die Gruppe in das Dokument einzufügen und `doc.Save` aufzurufen. Die folgenden Abschnitte zerlegen den Prozess in handhabbare Teile.

### 1. Erstellen eines neuen Dokuments und eines Builders

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum dieser Schritt wichtig ist* – Ein frisches `Document`‑Objekt stellt eine leere *.docx*-Datei dar. `DocumentBuilder` liefert High‑Level‑Methoden wie `InsertNode`, die wir verwenden, um die Gruppenform zu platzieren.

### 2. Rechteckform zu einer Gruppe hinzufügen

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Warum dieser Schritt wichtig ist* – Der Vorgang **add rectangle shape** zeigt, wie man ein visuelles Element mit exakter Größe und Position definiert. Das Rechteck befindet sich innerhalb von `group`, sodass das Verschieben der Gruppe später das Rechteck automatisch bewegt.

### 3. Formen im Word‑Dokument gruppieren

Die Klasse `GroupShape` fasst mehrere Zeichenobjekte zusammen. Das Gruppieren ist nützlich, wenn Sie mehrere Objekte als eine Einheit behandeln möchten (z. B. sie gemeinsam verschieben, drehen oder kopieren).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Warum wir gruppieren* – Das Gruppieren reduziert die Layout‑Komplexität. Anstatt jede Form einzeln auf der Seite zu positionieren, passen Sie einmal die `Left`, `Top`, `Width` und `Height` der Gruppe an.

### 4. Form‑Abmessungen für präzises Layout festlegen

Sowohl die Gruppe als auch ihre untergeordneten Formen benötigen explizite Abmessungen; andernfalls wendet Word Standardgrößen an, die möglicherweise nicht Ihrem Design entsprechen.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Warum wir Abmessungen festlegen* – Präzise Messungen stellen sicher, dass das Rechteck und das Textfeld nicht unbeabsichtigt überlappen und dass das endgültige **save docx file** dem beabsichtigten Layout entspricht.

### 5. Textfeld programmgesteuert innerhalb der Gruppe erstellen

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Warum dieser Schritt wichtig ist* – Der Abschnitt **create textbox programmatically** zeigt, wie man Rich‑Text in einer Form einbettet. Die Verwendung von `Paragraph` und `Run` gibt Ihnen später die volle Kontrolle über die Formatierung.

### 6. Gruppenform einfügen und **docx-Datei speichern**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Warum dieser letzte Schritt wichtig ist* – Der Aufruf `InsertNode` platziert die gruppierten Formen genau dort, wo sich der Cursor des Builders befindet. Die Methode `doc.Save` führt die **save docx file**‑Operation aus und schreibt ein vollwertiges Word‑Dokument auf die Festplatte.

> **Ergebnis:** Beim Öffnen von *GroupShape.docx* in Microsoft Word wird ein Rechteck links und ein Textfeld rechts angezeigt, beide zusammen in einer einzigen Gruppe gesperrt. Sie können die Gruppe als Einheit verschieben, ihre Größe ändern oder zusätzliche Formatierungen anwenden.

## Vollständiges, ausführbares Beispiel

Kopieren Sie den untenstehenden Code in ein neues Konsolenprojekt (`dotnet new console`) und führen Sie `dotnet run` aus. Das Programm erstellt `GroupShape.docx` im Ausgabeverzeichnis des Projekts.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Erwartete Ausgabe

* Eine Datei namens **GroupShape.docx** erscheint im Ausgabeverzeichnis.
* Beim Öffnen der Datei wird eine rechteckige Form links und ein Textfeld mit dem Text „Grouped text“ rechts angezeigt, beide zusammen gesperrt.
* Das Auswählen einer der Formen verschiebt die gesamte Gruppe, was bestätigt, dass die **group shapes word**‑Funktionalität wie beabsichtigt funktioniert.

## Häufige Variationen und Sonderfälle

| Situation | Empfehlung |
|-----------|------------|
| Mehr als zwei Formen benötigen | Fügen Sie zusätzliche `Shape`‑Objekte zu `group` hinzu, bevor Sie `builder.InsertNode` aufrufen. |
| Die Gruppe soll auf einer bestimmten Seite erscheinen | Bewegen Sie den Cursor des Builders mit `builder.MoveToDocumentEnd()` oder `builder.MoveToPage(pageNumber)`. |
| Andere Einheiten benötigen (z. B. Zentimeter) | Verwenden Sie `ConvertUtil.InchToPoint(1.0)`, um Zoll in Punkte umzuwandeln, die Einheit, die Word erwartet. |
| Das Textfeld soll Text umbrechen | Setzen Sie `textBox.TextBoxWrap = TextBoxWrapType.Square` nach dem Erstellen des Textfelds. |
| Arbeiten mit älteren .NET Framework‑Versionen | Die gleiche API funktioniert mit .NET Framework 4.7+, stellen Sie jedoch sicher, dass Sie die korrekte Aspose.Words‑Version referenzieren. |

**Pro‑Tipp:** Setzen Sie die `Width` und `Height` der Gruppe immer *nach* dem Hinzufügen aller untergeordneten Formen. Dadurch wird sichergestellt, dass die Gruppe ihren gesamten Inhalt vollständig umschließt und ein Abschneiden beim Öffnen des Dokuments in Word verhindert wird.

## Fazit

Sie wissen jetzt, wie Sie **docx-Datei speichern** können, während Sie **ein Rechteck form hinzufügen**, **group shapes word**, **Form‑Abmessungen festlegen** und **ein Textfeld programmgesteuert erstellen** mit Aspose.Words für .NET. Das vollständige Beispiel demonstriert ein sauberes, wiederholbares Muster, das Sie an komplexere Layouts anpassen können, wie Diagramme, Bilder,

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Aspose.Words Shape Shadow Tutorial – Schatten zu Word‑Form in C# hinzufügen](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}