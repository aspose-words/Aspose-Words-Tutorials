---
category: general
date: 2026-08-14
description: Wie man Formen in einem Word-Dokument mit C# gruppiert. Lernen Sie, ein
  Word-Dokument zu erstellen, ein Rechteck einzufügen, Formen in Word zu gruppieren
  und das Dokument als docx zu speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: de
lastmod: 2026-08-14
og_description: Wie man Formen in einem Word-Dokument mit C# gruppiert. Folgen Sie
  diesem vollständigen Tutorial, um eine Word-Datei zu erstellen, ein Rechteck einzufügen,
  Formen in Word zu gruppieren und das Ergebnis als docx zu speichern.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Wie man Formen in einem Word‑Dokument mit C# gruppiert – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Wie man Formen in einem Word‑Dokument mit C# gruppiert
url: /de/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in einem Word-Dokument mit C# gruppiert

Wenn Sie **wie man Formen gruppiert** in einem Word-Dokument benötigen, zeigt Ihnen dieser Leitfaden die genauen Schritte mit C# und der Aspose.Words-Bibliothek. Sie sehen, wie man ein Word-Dokument erstellt, ein Rechteck einfügt, Formen in Word gruppiert und schließlich **das Dokument als docx speichert** – alles in einem einzigen, ausführbaren Programm.

Das Erstellen und Manipulieren von Formen ist ein häufiges Bedürfnis, wenn Berichte, Verträge oder Marketingbroschüren programmgesteuert erzeugt werden. Am Ende dieses Tutorials haben Sie ein wiederverwendbares Code‑Snippet, das Sie in jedes .NET‑Projekt einbinden können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- .NET 6.0 oder höher installiert  
- Visual Studio 2022 (oder jede IDE, die .NET unterstützt)  
- Eine Aspose.Words für .NET Lizenz (oder eine kostenlose Testversion)  
- Grundlegende Kenntnisse der C#‑Syntax  

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Wie man Formen in einem Word-Dokument gruppiert

Der Kern der Lösung ist ein fünf‑stufiger Prozess. Jeder Schritt wird detailliert erklärt, und der vollständige Quellcode wird am Ende des Artikels bereitgestellt.

### Schritt 1: Erstelle ein neues leeres Dokument

Das Erste, was Sie tun, wenn Sie **Word-Dokument erstellen** programmgesteuert möchten, ist ein `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert die gesamte .docx‑Datei im Speicher.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:** `DocumentBuilder` ist ein hoch‑level Helfer, der es Ihnen ermöglicht, Text, Tabellen und Formen einzufügen, ohne den zugrunde liegenden Knotebaum manuell zu bearbeiten.

### Schritt 2: Rechteckform einfügen

Um **Rechteckform einfügen** zu demonstrieren, verwenden wir die Methode `InsertShape`. Das Rechteck wird das erste Mitglied der Gruppe sein.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Warum das wichtig ist:** Formen werden relativ zum Einfügepunkt positioniert. Das Festlegen einer Füllfarbe hilft Ihnen, die Form zu sehen, wenn Sie das resultierende Dokument öffnen.

### Schritt 3: Ellipsenform einfügen

Als Nächstes **Ellipsenform einfügen** (die API nennt sie `Ellipse`). Dies wird das zweite Mitglied der Gruppe sein.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Warum das wichtig ist:** Durch das sofortige Einfügen der Ellipse nach dem Rechteck landen beide Formen im selben Absatz, was das spätere Gruppieren vereinfacht.

### Schritt 4: Rechteck und Ellipse gruppieren

Jetzt beantworten wir die zentrale Frage **wie man Formen gruppiert** in einem Word-Dokument. Aspose.Words stellt `AppendGroupShape` bereit, um einen Gruppen‑Container zu erstellen, und anschließend rufen Sie `Group()` auf diesem Container auf.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Warum das wichtig ist:** Sobald die Formen gruppiert sind, wirkt sich jede Transformation (Verschieben, Größenänderung, Drehen), die auf `groupedShape` angewendet wird, automatisch auf sowohl das Rechteck als auch die Ellipse aus. Das ist entscheidend, um die Layout‑Konsistenz in generierten Dokumenten zu wahren.

### Schritt 5: Das Dokument als DOCX-Datei speichern

Der letzte Schritt ist, **das Dokument als docx zu speichern**. Sie können jeden gewünschten Pfad wählen; das Beispiel verwendet den Platzhalter `"YOUR_DIRECTORY"`, den Sie durch einen echten Ordner ersetzen sollten.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Warum das wichtig ist:** Das Speichern als DOCX bewahrt die Gruppierungs‑Metadaten, sodass Sie beim Öffnen der Datei in Microsoft Word das Rechteck und die Ellipse als ein einzelnes Objekt sehen.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das alle fünf Schritte kombiniert. Kopieren Sie es in ein neues Konsolen‑Projekt, stellen Sie das Aspose.Words‑NuGet‑Paket wieder her und führen Sie es aus.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Erwartete Ausgabe

Wenn Sie `groupedShapes.docx` in Microsoft Word öffnen, sehen Sie ein hellblaues Rechteck und eine hellkorallenfarbene Ellipse, die zusammengefasst sind. Das Anklicken einer der Formen wählt beide aus, sodass Sie sie als Einheit verschieben oder skalieren können.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich mehr als zwei Formen gruppieren?** | Ja. Übergeben Sie beliebig viele `Shape`‑Objekte an `AppendGroupShape`. Die Methode akzeptiert ein Array, sodass Sie die Sammlung dynamisch aufbauen können. |
| **Was, wenn die Gruppe an einer Tabellenzelle verankert sein soll?** | Fügen Sie die Formen in den Absatz der Zelle ein und rufen Sie dann `AppendGroupShape` für diesen Absatz auf. Die Gruppe erbt die Verankerung der Zelle. |
| **Beeinflusst das Gruppieren das zugrunde liegende XML?** | Aspose.Words schreibt ein `<w:grpSp>`‑Element, das die Kindformen enthält. Word erkennt dies als Gruppe und bewahrt die relative Positionierung. |
| **Wie kann ich später entgruppieren?** | Rufen Sie `groupedShape.Ungroup()` auf; die Methode gibt die einzelnen Formen zurück, sodass Sie sie separat bearbeiten können. |
| **Gibt es Performance‑Einbußen beim Gruppieren vieler Formen?** | Das Gruppieren selbst ist wenig kostenintensiv, aber das Rendern sehr großer Gruppen (Hunderte von Formen) kann die Dateigröße erhöhen. Erwägen Sie das Flatten von Bildern, falls die Größe ein Problem darstellt. |

## Pro‑Tipps

- **Explizite Positionen festlegen** (`Left`, `Top`), wenn Sie vor dem Gruppieren eine präzise Ausrichtung benötigen.  
- **Verwenden Sie `Shape.WrapType = WrapType.Inline`**, wenn die Gruppe sich wie ein Absatzelement verhalten soll und nicht als schwebendes Objekt.  
- **Wenden Sie einen Linienstil** auf die Gruppe (`groupedShape.LineFormat`) an, um der gesamten Sammlung einen Rahmen zu geben.  
- **Gruppe wiederverwenden**: Nach dem Aufruf von `Group()` können Sie `groupedShape` klonen und die Kopie an anderer Stelle im Dokument einfügen.

## Nächste Schritte

Jetzt, wo Sie **wie man Formen gruppiert** in einem Word‑Dokument kennen, können Sie verwandte Themen erkunden, wie zum Beispiel:

- **Rechteckform einfügen** mit benutzerdefiniertem Text oder Bildern innerhalb der Form.  
- **Komplexe Diagramme erstellen** durch Verschachteln von Gruppen (eine Gruppe in einer Gruppe).  
- **Das Dokument als PDF exportieren** und dabei die Formengruppierung beibehalten (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Jeder dieser Punkte baut auf den hier behandelten Grundlagen auf, sodass Sie Ihr Word‑Automatisierungs‑Toolkit weiter ausbauen können.

## Fazit

Dieses Tutorial zeigte **wie man Formen gruppiert** in einem Word‑Dokument mit C#. Sie haben gelernt, **Word‑Dokument zu erstellen**, **Rechteckform einzufügen**, **Formen in Word zu gruppieren** und schließlich **das Dokument als docx zu speichern**. Mit dem vollständigen, ausführbaren Beispiel und den praktischen Tipps können Sie die Formengruppierung in jeden Dokument‑Generierungs‑Workflow integrieren. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden demonstrierten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Formen in Word-Dokumente mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}