---
category: general
date: 2026-08-04
description: Rechteckform in ein Word-Dokument mit C# einfügen. Erfahren Sie, wie
  Sie Formen in Word gruppieren, das Dokument als docx speichern und DocumentBuilder
  für erweiterte Layouts verwenden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to group shapes
- group shapes in word
- save document as docx
- how to use builder
language: de
lastmod: 2026-08-04
og_description: Fügen Sie in einer Word-Datei mit C# ein Rechteck ein und gruppieren
  Sie anschließend die Formen für erweiterte Layouts. Dieses Tutorial behandelt außerdem
  das Speichern des Dokuments als DOCX und die effiziente Nutzung von DocumentBuilder.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with C# DocumentBuilder
og_title: Rechteckform in Word einfügen – Schritt‑für‑Schritt‑Anleitung für C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Insert rectangle shape in a Word document with C#. Learn how to group
    shapes in Word, save document as docx, and use DocumentBuilder for advanced layouts.
  headline: Insert rectangle shape in Word using C# – complete guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Rechteckform in Word mit C# einfügen – vollständiger Leitfaden
url: /de/java/images-shapes/insert-rectangle-shape-in-word-using-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Word mit C# einfügen – vollständige Anleitung

Wenn Sie **eine Rechteckform** in ein Word‑Dokument mit C# einfügen müssen, zeigt Ihnen dieses Tutorial genau, wie es geht. Sie lernen außerdem **wie man Formen gruppiert** in Word, **ein Dokument als docx speichert** und **wie man Builder verwendet** für sauberen, wartbaren Code.

Das Arbeiten mit Formen ist eine häufige Anforderung beim programmatischen Erstellen von Berichten, Zertifikaten oder benutzerdefinierten Layouts. Am Ende dieser Anleitung haben Sie ein vollständig ausführbares Beispiel, das ein Rechteck erstellt, eine Ellipse hinzufügt, sie gruppiert und das Ergebnis als DOCX‑Datei speichert.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher installiert  
* Visual Studio 2022 (oder jede IDE, die C# unterstützt)  
* Die **Aspose.Words for .NET**‑Bibliothek (verfügbar über NuGet)  

Sie können die Bibliothek mit dem folgenden Befehl hinzufügen:

```bash
dotnet add package Aspose.Words
```

## Rechteckform mit DocumentBuilder einfügen

Der erste Schritt besteht darin, ein neues `Document` und einen `DocumentBuilder` zu erstellen. Der Builder bietet Ihnen eine fluente API zum Einfügen von Inhalten, einschließlich Formen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document.
        Document document = new Document();

        // Initialize the builder that will edit the document.
        DocumentBuilder builder = new DocumentBuilder(document);
```

Die `DocumentBuilder`‑Instanz ist das Kernobjekt, das Sie verwenden, um **eine Rechteckform** und andere Elemente **einzufügen**. Sie verfolgt die aktuelle Cursor‑Position im Dokument, sodass jede Einfügung genau dort erfolgt, wo Sie sie benötigen.

## Wie man eine Rechteckform einfügt

Wenn der Builder bereit ist, rufen Sie `InsertShape` auf. Sie geben den `ShapeType`, die Breite und die Höhe in Punkten an (1 pt ≈ 1/72 in).

```csharp
        // Insert a rectangle of 100 pt width and 50 pt height.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;
```

*Warum das wichtig ist*: Das Festlegen von `FillColor` und `StrokeColor` macht das Rechteck optisch unterscheidbar, was hilft, wenn Sie es später mit anderen Formen gruppieren.

## Wie man Formen in Word gruppiert

Das Gruppieren von Formen ermöglicht es, mehrere Objekte als eine Einheit zu verschieben, zu drehen oder zu formatieren. Nachdem Sie das Rechteck eingefügt haben, fügen Sie eine weitere Form hinzu (in diesem Beispiel eine Ellipse) und erstellen dann ein `GroupShape`.

```csharp
        // Insert an ellipse of 80 pt diameter.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // Insert an empty group container.
        GroupShape groupShape = builder.InsertGroupShape();

        // Add the rectangle and ellipse to the group.
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
```

Der Aufruf `InsertGroupShape` erstellt einen Platzhalter, der beliebig viele Kindformen aufnehmen kann. Durch das Anhängen des Rechtecks und der Ellipse gruppieren Sie effektiv **Formen in Word**. Die Gruppe verhält sich wie eine einzelne Form – Sie können sie neu positionieren, einen Rahmen anwenden oder die Größe ändern, ohne das interne Layout jedes Kindes zu beeinflussen.

### Profi‑Tipp

Nach dem Gruppieren können Sie die Position der Gruppe relativ zur Seite ändern:

```csharp
        // Move the whole group 150 pt right and 100 pt down.
        groupShape.Left = 150;
        groupShape.Top = 100;
```

## Dokument als docx speichern

Sobald die Formen angeordnet sind, müssen Sie die Datei speichern. Die Methode `Document.Save` ermittelt das Format automatisch anhand der Dateierweiterung. Um **ein Dokument als docx zu speichern**, übergeben Sie einen Pfad, der mit `.docx` endet.

```csharp
        // Save the document to the output folder.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

Das Ausführen des Programms erzeugt `output.docx`. Öffnen Sie die Datei in Microsoft Word, und Sie sehen ein hellblaues Rechteck und eine hellkorallenfarbene Ellipse, die zusammen gruppiert sind. Sie können die Gruppe anklicken und sie als einzelnes Objekt verschieben.

## DocumentBuilder effektiv nutzen

`DocumentBuilder` ist mehr als ein Formeinfüger; er verarbeitet auch Text, Tabellen, Kopf‑ und Fußzeilen. Wenn Sie die Erstellung von Formen mit Text kombinieren, denken Sie daran, den Cursor zurückzusetzen, wenn Sie Inhalte an anderer Stelle einfügen müssen:

```csharp
        // Move the cursor to a new paragraph after the group.
        builder.Writeln(); // Inserts a line break.
        builder.Font.Size = 12;
        builder.Writeln("Shapes have been added and grouped successfully.");
```

Den Zustand des Builders explizit zu halten, verhindert versehentliche Überschreibungen und macht den Code leichter wartbar.

## Randfälle und Variationen

| Situation | Empfohlener Ansatz |
|-----------|--------------------|
| **Mehr als zwei Formen** | Jede Form einfügen, dann `AppendChild` für jede Form vor dem Speichern aufrufen. |
| **Verschachtelte Gruppen** | Eine Gruppe erstellen, Formen hinzufügen und dann diese Gruppe in ein weiteres `GroupShape` einfügen. |
| **Unterschiedliche Maßeinheiten** | `builder.ConvertPixelsToPoints` verwenden, wenn Sie Abmessungen in Pixeln haben. |
| **Kompatibilität mit älteren Word‑Versionen** | Als `.doc` speichern, indem Sie die Erweiterung ändern; die meisten Form‑Funktionen funktionieren weiterhin. |

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige Programm, das Sie in ein neues Konsolenprojekt kopieren‑und‑einfügen können. Weitere Code‑Snippets sind nicht erforderlich.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape.
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.FillColor = System.Drawing.Color.LightBlue;
        rectangleShape.StrokeColor = System.Drawing.Color.DarkBlue;

        // 3️⃣ Insert an ellipse shape.
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.FillColor = System.Drawing.Color.LightCoral;
        ellipseShape.StrokeColor = System.Drawing.Color.Maroon;

        // 4️⃣ Create a group shape and add both shapes.
        GroupShape groupShape = builder.InsertGroupShape();
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Optional: reposition the group.
        groupShape.Left = 150;
        groupShape.Top = 100;

        // 5️⃣ Add a caption below the group.
        builder.Writeln();
        builder.Font.Size = 12;
        builder.Writeln("Grouped rectangle and ellipse created with DocumentBuilder.");

        // 6️⃣ Save the document as DOCX.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        document.Save(outputPath);
    }
}
```

**Erwartetes Ergebnis**: Beim Öffnen von `output.docx` sehen Sie ein hellblaues Rechteck und eine hellkorallenfarbene Ellipse, die zusammen gruppiert sind, positioniert 150 pt vom linken Rand und 100 pt vom oberen Rand. Die Beschriftung erscheint unterhalb der Gruppe.

## Fazit

Sie wissen jetzt, wie man mit C# **eine Rechteckform** in eine Word‑Datei **einfügt**, **wie man Formen in Word gruppiert** und **wie man ein Dokument als docx** mit dem Aspose.Words `DocumentBuilder` **speichert**. Durch das Beherrschen dieser Schritte können Sie komplexe Layouts – Zertifikate, Berichte oder benutzerdefinierte Formulare – vollständig per Code erstellen.

Als Nächstes erkunden Sie verwandte Themen wie **Textfelder hinzufügen**, **mit Tabellen arbeiten** oder **in PDF exportieren**. Jeder dieser Punkte baut auf denselben `DocumentBuilder`‑Grundlagen auf, die Sie gerade geübt haben.

Bereit, Ihre Word‑Dokumente zu automatisieren? Versuchen Sie, das Beispiel mit mehr Formen zu erweitern, Verläufe anzuwenden oder über Daten zu iterieren, um in einem Durchlauf einen vollständigen Bericht zu erzeugen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Formen in Word‑Dokumenten mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}