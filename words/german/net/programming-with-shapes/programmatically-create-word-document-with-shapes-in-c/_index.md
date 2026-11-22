---
category: general
date: 2026-11-22
description: Programmgesteuert ein Word‑Dokument in C# erstellen, ein Rechteck‑Shape
  einfügen, mehrere Shapes einfügen und die Shapes mit Aspose.Words in Word schreiben.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- insert rectangle shape
- insert multiple shapes
- write shapes to word
language: de
lastmod: 2026-11-22
og_description: Programmgesteuertes Erstellen eines Word‑Dokuments in C# durch Einfügen
  einer Rechteckform, Einfügen mehrerer Formen und Schreiben der Formen in Word mit
  Aspose.Words.
og_image_alt: Screenshot of a Word document showing a rectangle and an ellipse grouped
  together
og_title: Word‑Dokument programmgesteuert mit Formen in C# erstellen
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  headline: Programmatically create Word document with shapes in C#
  type: TechArticle
- description: Programmatically create Word document in C# and insert rectangle shape,
    insert multiple shapes, and write shapes to Word using Aspose.Words.
  name: Programmatically create Word document with shapes in C#
  steps:
  - name: '**Initialize** a new `Document` and a `DocumentBuilder`.'
    text: '**Initialize** a new `Document` and a `DocumentBuilder`.'
  - name: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
    text: '**Insert multiple shapes** (a rectangle and an ellipse) and place them
      inside a `GroupShape`.'
  - name: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
    text: '**Write shapes to Word** by saving the `Document` to a `.docx` file.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Word-Dokument programmgesteuert mit Formen in C# erstellen
url: /de/net/programming-with-shapes/programmatically-create-word-document-with-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programmatisch ein Word-Dokument mit Formen in C# erstellen

Wenn Sie **programmatisch ein Word-Dokument** erstellen müssen, das benutzerdefinierte Grafiken enthält, zeigt Ihnen dieser Leitfaden, wie Sie dies mit Aspose.Words für .NET tun können. Sie lernen, ein Rechteck‑Shape einzufügen, weitere Shapes hinzuzufügen, sie zu gruppieren und schließlich die Shapes nach Word zu schreiben – alles in wenigen Zeilen C#.

Das Erstellen einer Word‑Datei mit Grafiken erfordert nicht mehr manuelle Bearbeitung oder Makro‑Skripte. Am Ende dieses Tutorials verfügen Sie über eine wiederverwendbare Methode, die eine `.docx`‑Datei erzeugt, die ein Rechteck und eine Ellipse gruppiert enthält, bereit für nachgelagerte Verarbeitung oder Berichterstellung.

## Was Sie benötigen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
- Aspose.Words für .NET (NuGet‑Paket `Aspose.Words`)
- Eine IDE wie Visual Studio 2022 (jeder Editor, der C# kompilieren kann, ist geeignet)

> **Pro‑Tipp:** Installieren Sie das Paket mit dem CLI‑Befehl `dotnet add package Aspose.Words`, bevor Sie mit dem Codieren beginnen.

## Programmatisch ein Word-Dokument erstellen – Überblick

Der gesamte Ablauf besteht aus drei logischen Phasen:

1. **Initialisieren** Sie ein neues `Document` und einen `DocumentBuilder`.  
2. **Mehrere Shapes einfügen** (ein Rechteck und eine Ellipse) und sie in einem `GroupShape` platzieren.  
3. **Shapes nach Word schreiben** indem Sie das `Document` in einer `.docx`‑Datei speichern.

Jede Phase ist im Folgenden in einem eigenen Schritt gekapselt, sodass Sie den Code direkt in Ihr Projekt kopieren‑und‑einfügen können.

![Programmatically create Word document with grouped shapes](grouped-shapes.png){: .align-center alt="Programmatisch ein Word-Dokument mit gruppierten Formen erstellen"}

## Schritt 1: Dokument und Builder initialisieren

Die Klasse `Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` eine fluente API zum Hinzufügen von Inhalten bereitstellt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document document = new Document();

// Initialize a DocumentBuilder for the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Warum das wichtig ist:* Das Erstellen des `Document` zuerst gibt Ihnen eine leere Leinwand. Der `DocumentBuilder` verfolgt den aktuellen Einfügepunkt, was entscheidend ist, wenn Sie später Shapes an eine Absatz‑Hierarchie anhängen.

## Schritt 2: Einen Group‑Shape‑Container einfügen

Ein `GroupShape` ermöglicht es, mehrere einzelne Shapes als eine Einheit zu behandeln. Das ist nützlich, wenn Sie sie gemeinsam verschieben oder skalieren möchten.

```csharp
// Insert a group shape container at the current cursor position
GroupShape groupShape = builder.InsertGroupShape();
```

*Erklärung:* `InsertGroupShape` fügt einen leeren Container ein und macht ihn automatisch zum aktuellen Shape. Alle nachfolgenden Shape‑Einfügungen werden zu diesem Container hinzugefügt, bis Sie die Gruppe schließen.

## Rechteck‑Shape einfügen

Jetzt fügen wir die erste Grafik hinzu – ein Rechteck. Damit wird die Anforderung **Rechteck‑Shape einfügen** erfüllt.

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Das Rechteck erbt den Formatierungskontext der Gruppe, sodass es innerhalb des `GroupShape` erscheint. Sie können später bei Bedarf auch Linienfarbe, Füllung oder Text festlegen.

## Mehrere Shapes einfügen

Um die Fähigkeit **mehrere Shapes einfügen** zu demonstrieren, fügen wir direkt nach dem Rechteck eine Ellipse hinzu. Sie können beliebig viele Shapes (z. B. Dreiecke, Sterne) hinzufügen, bevor Sie die Gruppe schließen.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Zu diesem Zeitpunkt enthält die Gruppe zwei unterschiedliche Shapes: ein Rechteck und eine Ellipse. Da sie denselben Eltern‑Container teilen, können Sie sie als Einheit verschieben.

## Schritt 3: Das Group‑Shape an die Absatz‑Hierarchie anhängen

Word‑Dokumente speichern Inhalte in einem Absatz‑Baum. Damit die Gruppe in der endgültigen Datei sichtbar wird, müssen wir sie an den aktuellen Absatz anhängen.

```csharp
// Append the group shape to the current paragraph so it becomes part of the document flow
groupShape.AppendChild(builder.CurrentParagraph);
```

*Warum dieser Schritt erforderlich ist:* Ohne das Anhängen der Gruppe an einen Absatz existieren die Shapes nur im Speicher und werden beim Speichern des Dokuments weggelassen.

## Schritt 4: Dokument speichern – Shapes nach Word schreiben

Abschließend speichern wir das im Speicher befindliche `Document` auf die Festplatte. Damit wird das Ziel **Shapes nach Word schreiben** erreicht.

```csharp
// Define the output path (adjust the folder as needed)
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");

// Save the document in DOCX format
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Wenn Sie `GroupShape.docx` in Microsoft Word öffnen, sehen Sie ein Rechteck und eine Ellipse, die zusammen gruppiert sind, genau wie vom Code eingefügt.

### Erwartete Ausgabe

- Eine Datei namens **GroupShape.docx** im Ausgabeverzeichnis des Projekts.
- In der Word‑Datei: ein einzelner Absatz, der ein gruppiertes Rechteck (100 pt × 50 pt) und eine Ellipse (80 pt × 40 pt) enthält. Das Auswählen eines der Shapes wählt die gesamte Gruppe aus.

## Umgang mit häufigen Sonderfällen

| Situation | Empfehlung |
|-----------|------------|
| **Andere DPI oder Seitengröße** | Setzen Sie `builder.PageSetup.PaperSize` explizit, bevor Sie Shapes einfügen, um unerwartete Skalierung zu vermeiden. |
| **Präzise Positionierung von Shapes erforderlich** | Verwenden Sie `builder.MoveTo`, um den Einfügepunkt zu verschieben, und setzen Sie dann die Eigenschaften `groupShape.Left` und `groupShape.Top` (Werte in Punkten). |

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word‑Dokument erstellen – Rechteck‑Shape & Schatten einfügen in C#](/words/english/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/)
- [Word‑Dokument programmatisch erstellen und Shapes gruppieren in C#](/words/english/net/programming-with-shapes/create-word-document-programmatically-and-group-shapes-in-c/)
- [Programmatisch ein Word‑Dokument mit einem Group‑Shape erstellen](/words/english/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}