---
category: general
date: 2026-09-30
description: Erstellen Sie ein leeres Dokument und fügen Sie ein Rechteck, eine Ellipse
  und mehrere Formen als Gruppe in C# mit Aspose.Words ein. Erfahren Sie, wie Sie
  Formen einfügen und wie Sie eine Gruppe erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: de
lastmod: 2026-09-30
og_description: Erstellen Sie ein leeres Dokument in C# und lernen Sie, wie Sie Formen
  einfügen und mehrere Formen mit Aspose.Words gruppieren. Folgen Sie der Schritt‑für‑Schritt‑Anleitung.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Erstellen Sie ein leeres Dokument und gruppieren Sie Formen in C# – Aspose.Words‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Wie man ein leeres Dokument erstellt und Formen mit Aspose.Words in C# hinzufügt
url: /de/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Dokument erstellt und Formen mit Aspose.Words in C# hinzufügt

Wenn Sie ein **leeres Dokument erstellen** und es mit Grafiken füllen müssen, zeigt Ihnen diese Anleitung genau, wie das geht. Sie sehen, wie Sie eine **Rechteckform einfügen**, weitere Zeichenobjekte hinzufügen und dann **mehrere Formen gruppieren** können, sodass sie sich wie eine Einheit verhalten.

Die Arbeit mit Formen ist ein häufiges Bedürfnis beim Erzeugen von Verträgen, Zertifikaten oder benutzerdefinierten Berichten. In diesem Tutorial lernen Sie den kompletten Workflow, von der Initialisierung des Dokuments bis zum Speichern der finalen Datei, unter Verwendung der Aspose.Words API für .NET.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 (oder höher) SDK installiert  
* Eine gültige Aspose.Words for .NET Lizenz (die kostenlose Testversion reicht für dieses Beispiel)  
* Eine IDE wie Visual Studio 2022 oder Visual Studio Code  

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Wie man ein leeres Dokument erstellt und mit Formen arbeitet

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert die Word‑Datei im Speicher und gibt Ihnen Zugriff auf den `DocumentBuilder`, das primäre Werkzeug zum Einfügen von Inhalten.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Warum das wichtig ist:** Ein leeres Dokument bietet Ihnen eine saubere Leinwand. Der `DocumentBuilder` hält den aktuellen Einfügepunkt, sodass jede Form, die Sie hinzufügen, automatisch an der richtigen Seite platziert wird.

## Rechteckform und weitere Formen einfügen

Als Nächstes fügen wir ein Rechteck und eine Ellipse hinzu. Beide Aufrufe verwenden dieselbe `InsertShape`‑Methode, die empfohlene Vorgehensweise **wie man Formen einfügt** in Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Die `InsertShape`‑Methode positioniert die Form automatisch an der aktuellen Cursor‑Position.* Wenn Sie eine präzise Platzierung benötigen, können Sie `Shape.Left` und `Shape.Top` nach dem Einfügen anpassen.

## Mehrere Formen zu einem einzigen Objekt gruppieren

Jetzt kombinieren wir das Rechteck und die Ellipse zu einer logischen Einheit. Das Gruppieren ist nützlich, wenn Sie mehrere Formen zusammen verschieben oder skalieren möchten.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Wie das funktioniert:** `InsertGroupShape` erstellt einen Container, der sich wie jede andere `Shape` verhält. Durch Aufruf von `AppendChild` verschieben Sie die bestehenden Formen in den Container, der automatisch deren relative Koordinaten aktualisiert.

### Praktischer Tipp

Wenn Sie später **wie man eine Gruppe** programmgesteuert für mehr als zwei Formen erstellt, wiederholen Sie einfach `AppendChild` für jede weitere `Shape`‑Instanz. Die Gruppe kann beliebig viele Zeichenobjekte enthalten, einschließlich Bilder, Textfelder oder sogar andere Gruppen.

## Vollständiges Beispiel – wie man Formen einfügt und das Dokument speichert

Unten finden Sie das komplette, ausführbare Programm, das jeden bisher besprochenen Schritt demonstriert. Das Ausführen des Codes erzeugt eine Datei `ShapesDemo.docx`, die ein Rechteck, eine Ellipse und eine gruppierte Form enthält.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Erwartete Ausgabe:** Das Öffnen von `ShapesDemo.docx` in Microsoft Word zeigt eine einzelne Seite mit einem blauen Rechteck, einer grünen Ellipse und einem umgebenden grauen Rand, der die Gruppe darstellt. Das Verschieben der Gruppe bewegt beide Formen zusammen, was bestätigt, dass die **mehrere Formen gruppieren**‑Operation erfolgreich war.

## Häufige Fragen und Edge‑Case‑Behandlung

| Frage | Antwort |
|----------|--------|
| *Was, wenn ich die Formen auf einer bestimmten Seite haben möchte?* | Rufen Sie `builder.MoveToDocumentEnd();` vor dem Einfügen der Formen auf, oder verwenden Sie `builder.MoveToSection(sectionIndex);`, um ein bestimmtes Kapitel anzusteuern. |
| *Kann ich Text in einer gruppierten Form hinzufügen?* | Ja. Erstellen Sie eine `Shape` vom Typ `ShapeType.TextBox`, konfigurieren Sie deren Text und `AppendChild` sie dann zum `GroupShape`. |
| *Verwenden die Formabmessungen Punkte oder Pixel?* | Aspose.Words verwendet **Punkte** (1 pt = 1/72 Zoll). Das sorgt für konsistente Größenangaben auf Druckern und Bildschirmen. |
| *Wie ändert man die Rotation der Gruppe?* | Setzen Sie `groupShape.RotationAngle = 45;` (Grad). Alle Kindformen rotieren um den Ursprung der Gruppe. |

## Fazit

Sie wissen jetzt, wie man **ein leeres Dokument erstellt**, **ein Rechteck einfügt**, **wie man Formen einfügt** wie Ellipsen, und **mehrere Formen gruppiert** zu einem einzigen Objekt mithilfe von Aspose.Words für .NET. Das vollständige Codebeispiel demonstriert den empfohlenen Ansatz, und die obigen Tipps helfen Ihnen, die Lösung an komplexere Szenarien anzupassen, etwa das Hinzufügen von Textfeldern oder das Rotieren von Gruppen.

Bereit, weiter zu erkunden? Versuchen Sie, eine Bildform zur Gruppe hinzuzufügen, experimentieren Sie mit unterschiedlichen Füllfarben oder erzeugen Sie einen mehrseitigen Bericht, bei dem jede Seite ihr eigenes gruppiertes Diagramm enthält. Die gleichen Prinzipien gelten, sodass Sie dieses Muster auf jedes Dokument‑Automatisierungsprojekt skalieren können.


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}