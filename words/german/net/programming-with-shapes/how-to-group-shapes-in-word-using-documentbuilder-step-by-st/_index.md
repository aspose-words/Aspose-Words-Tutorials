---
category: general
date: 2026-09-08
description: Erfahren Sie, wie Sie Formen in Word mit einem DocumentBuilder gruppieren,
  ein leeres Word‑Dokument erstellen und mit nur wenigen Zeilen C#‑Code ein Rechteck
  einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create blank word doc
- insert rectangle shape word
- how to use documentbuilder
language: de
lastmod: 2026-09-08
og_description: Formen in Word mit DocumentBuilder gruppieren. Dieses Tutorial zeigt,
  wie man ein leeres Word‑Dokument erstellt, eine Rechteckform einfügt und Formen
  zu einer GroupShape kombiniert.
og_image_alt: Screenshot of a Word document showing grouped shapes – group shapes
  in Word example
og_title: Formen in Word mit DocumentBuilder gruppieren – vollständiges C#‑Beispiel
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to group shapes in Word with a DocumentBuilder, create a
    blank Word doc, and insert a rectangle shape in just a few lines of C# code.
  headline: How to group shapes in Word using DocumentBuilder – step‑by‑step guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man Formen in Word mit DocumentBuilder gruppiert – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/how-to-group-shapes-in-word-using-documentbuilder-step-by-st/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in Word mit DocumentBuilder gruppiert – Schritt‑für‑Schritt‑Anleitung

Wenn Sie **Formen in Word** programmgesteuert **gruppieren** müssen, zeigt dieses Tutorial eine vollständige Lösung in C#. Sie sehen, wie Sie ein **leeres Word‑Dokument erstellen**, **DocumentBuilder** verwenden und **eine Rechteckform einfügen**, bevor Sie sie mit einer Ellipse gruppieren. Das Ergebnis ist ein einzelnes `GroupShape`, das Sie als ein Objekt verschieben, skalieren oder formatieren können.

Dieser Leitfaden deckt alles ab, was Sie wissen müssen, um ein Word‑Dokument mit gruppierten Grafiken mithilfe der Aspose.Words für .NET‑Bibliothek zu erzeugen. Am Ende des Artikels haben Sie ein ausführbares Projekt, das `GroupedShapes.docx` erzeugt, das ein Rechteck und eine Ellipse zu einer einzigen Form kombiniert.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7.2+)
- Aspose.Words für .NET NuGet‑Paket (`Aspose.Words`) – Version 23.12 oder neuer
- Eine C#‑IDE wie Visual Studio 2022 oder Visual Studio Code
- Grundlegende Kenntnisse der C#‑Syntax und objektorientierten Programmierung

> **Pro Tipp:** Installieren Sie das NuGet‑Paket über die Befehlszeile, um Ihr Projekt übersichtlich zu halten:  
> `dotnet add package Aspose.Words --version 23.12.0`

## Schritt 1: Ein leeres Word‑Dokument erstellen

Der erste Vorgang besteht darin, ein `Document`‑Objekt zu instanziieren, das eine leere Word‑Datei darstellt, und einen `DocumentBuilder`, mit dem Sie Inhalte hinzufügen können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Step 1: Create a blank Word document and a DocumentBuilder
        Document document = new Document();               // creates an empty .docx structure
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Warum das wichtig ist:** `Document` stellt den Dateicontainer bereit, während `DocumentBuilder` eine fluente API zum Einfügen von Text, Bildern und Formen bietet. Ohne einen `DocumentBuilder` müssten Sie den Knotbaum des Dokuments manuell manipulieren, was fehleranfällig ist.

## Schritt 2: Ein Rechteck einfügen

Ein Rechteck ist ein häufiges Bauelement für Diagramme. Verwenden Sie `InsertShape` mit `ShapeType.Rectangle` und geben Sie Breite und Höhe in Punkten an (1 pt ≈ 1/72 in).

```csharp
        // Step 2: Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;   // distance from the left margin (points)
        rectangleShape.Top = 50;    // distance from the top margin (points)
```

**Warum das wichtig ist:** Das Festlegen von `Left` und `Top` positioniert das Rechteck exakt auf der Seite, was entscheidend ist, wenn Sie es später mit anderen Formen gruppieren. Die Methode `InsertShape` fügt die Form automatisch dem aktuellen Absatz hinzu.

## Schritt 3: Eine Ellipse einfügen

Fügen Sie als Nächstes eine Ellipse hinzu, die neben dem Rechteck platziert wird.

```csharp
        // Step 3: Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;
```

**Warum das wichtig ist:** Die Verwendung eines anderen `ShapeType` zeigt, wie dieselbe `DocumentBuilder`‑API unterschiedliche Grafiken erzeugen kann. Das Positionieren der Ellipse so, dass sie das Rechteck überlappt, macht den Gruppierungseffekt deutlich.

## Schritt 4: Die beiden Formen gruppieren

Ein `GroupShape` fungiert als Container. Durch das Anhängen des Rechtecks und der Ellipse als Kind‑Elemente verhalten sie sich wie ein einzelnes Objekt.

```csharp
        // Step 4: Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        // Define the bounding rectangle that encloses all child shapes
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);

        // Insert the group into the document body
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);
```

**Warum das wichtig ist:** Die Eigenschaft `Bounds` gibt Word an, wo die Gruppe auf der Seite liegt. Durch das Anhängen der Kind‑Formen erhalten Sie deren individuelle Formatierung, während Sie kollektive Transformationen (Verschieben, Drehen, Skalieren) ermöglichen.

## Schritt 5: Das Dokument speichern

Schließlich schreiben Sie das Dokument auf die Festplatte. Sie können den Pfad zu einem beliebigen Ordner ändern.

```csharp
        // Step 5: Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wenn Sie `GroupedShapes.docx` in Microsoft Word öffnen, sehen Sie ein Rechteck und eine Ellipse, die zusammen gruppiert sind. Das Auswählen der Gruppe hebt beide Formen hervor, sodass Sie sie als eine Einheit ziehen oder skalieren können.

### Erwartete Ausgabe

- Eine Word‑Datei mit dem Namen **GroupedShapes.docx**
- Die erste Seite enthält ein **Rechteck** (100 pt × 50 pt) an Position (50, 50)
- Eine **Ellipse** (80 pt × 80 pt) an Position (200, 70)
- Beide Formen sind Teil eines **GroupShape** mit einer Begrenzungsbox von 300 pt × 200 pt

## Häufige Variationen und Sonderfälle

| Szenario | Anpassung |
|----------|------------|
| **Andere Seitengröße** | Setzen Sie `document.Sections[0].PageSetup.PageWidth` und `PageHeight`, bevor Sie Formen einfügen. |
| **Mehr als zwei Formen** | Erstellen Sie zusätzliche `Shape`‑Objekte und rufen Sie für jedes `groupShape.AppendChild(newShape)` auf. |
| **Füllfarbe anwenden** | `rectangleShape.FillColor = System.Drawing.Color.LightBlue;` |
| **Gruppe drehen** | `groupShape.Rotation = 45;` (degrees) |
| **Exportieren nach PDF** | Nach dem Speichern des DOCX rufen Sie `document.Save("GroupedShapes.pdf");` auf. |

## Vollständiger Quellcode (bereit zum Ausführen)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapesDemo
{
    static void Main()
    {
        // Create a blank Word document and a DocumentBuilder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape and position it
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangleShape.Left = 50;
        rectangleShape.Top = 50;

        // Insert an ellipse shape and position it
        Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipseShape.Left = 200;
        ellipseShape.Top = 70;

        // Group the two shapes into a single GroupShape
        GroupShape groupShape = new GroupShape(document);
        groupShape.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        document.FirstSection.Body.FirstParagraph.AppendChild(groupShape);

        // Save the document with the grouped shapes
        string outputPath = @"GroupedShapes.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Kopieren Sie den Code in ein neues Konsolenprojekt, stellen Sie das Aspose.Words‑NuGet‑Paket wieder her und führen Sie es aus. Die Konsole bestätigt den Dateipfad, und das Öffnen der Datei zeigt die gruppierten Grafiken.

## Fazit

Sie wissen jetzt **wie man Formen in Word** mit dem Aspose.Words `DocumentBuilder` gruppiert. Das Tutorial führte Sie durch das Erstellen eines **leeren Word‑Dokuments**, das **Einfügen einer Rechteckform**, das Hinzufügen einer Ellipse und das Kombinieren zu einem `GroupShape`. Mit dieser Grundlage können Sie direkt aus C# umfangreichere Diagramme, Flussdiagramme oder benutzerdefinierte Grafiken erstellen.

### Was kommt als Nächstes?

- Erkunden Sie **wie man DocumentBuilder** für Tabellen, Kopf‑ und Fußzeilen verwendet.
- Kombinieren Sie **Insert rectangle shape Word**‑Techniken mit Textfeldern für kommentierte Diagramme.
- Verwenden Sie **create blank word doc** als Vorlage für die automatisierte Berichtserstellung.

Experimentieren Sie gern mit Farben, Verläufen und zusätzlichen Formen. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Formen in Word‑Dokumenten mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}