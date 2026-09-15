---
category: general
date: 2026-09-14
description: Erfahren Sie, wie Sie ein Tag einfügen, Formen hinzufügen, eine Gruppe
  erstellen und das Dokument mit Aspose.Words in C# als DOCX speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert tag
- save document as docx
- how to create group
- how to add shapes
- how to save docx
language: de
lastmod: 2026-09-14
og_description: Wie man ein Tag einfügt, Formen hinzufügt, eine Gruppe erstellt und
  das Dokument als DOCX mit Aspose.Words speichert. Folgen Sie der Schritt‑für‑Schritt‑Anleitung.
og_image_alt: Diagram showing how to insert tag inside a grouped shape before saving
  as DOCX
og_title: Wie man ein Tag einfügt und eine gruppierte Form in einem DOCX mit C# erstellt
schemas:
- author: Aspose
  dateModified: '2026-09-14'
  description: Learn how to insert tag, add shapes, create a group, and save document
    as DOCX using Aspose.Words in C#.
  headline: How to insert tag and create a group shape in a DOCX
  type: TechArticle
tags:
- Aspose.Words
- C#
- DOCX manipulation
title: Wie man ein Tag einfügt und eine Gruppenform in einer DOCX erstellt
url: /de/net/programming-with-shapes/how-to-insert-tag-and-create-a-group-shape-in-a-docx/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Tag einfügt und eine Gruppenform in einem DOCX erstellt

Wenn Sie wissen müssen **wie man ein Tag einfügt** beim Erstellen eines komplexen Layouts, zeigt Ihnen dieser Leitfaden eine vollständige, ausführbare Lösung. Sie sehen, wie man Formen hinzufügt, eine Gruppe erstellt und schließlich **das Dokument als DOCX speichert** mit Aspose.Words für .NET.

Die Dokumentenerstellung erfordert häufig das Mischen von Text‑Tags mit grafischen Elementen. In diesem Tutorial lernen Sie genau **wie man ein Tag einfügt**, wie man **Formen hinzufügt**, wie man **eine Gruppe erstellt** und den korrekten Weg, **docx zu speichern**, sodass die Datei in Word ohne Qualitätsverlust geöffnet werden kann.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`)
- Grundlegende Kenntnisse der C#‑Syntax
- Eine IDE wie Visual Studio oder VS Code

Es werden keine zusätzlichen Bibliotheken benötigt; das gesamte Beispiel läuft mit einem einzigen NuGet‑Verweis.

## Wie man eine Gruppe erstellt und Formen hinzufügt

Der erste logische Schritt besteht darin, eine **Gruppe** zu erstellen, die mehrere Formen enthält. Das Gruppieren hält die Formen zusammen, wenn Sie sie später verschieben oder drehen.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

// 1️⃣ Create an empty document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// 2️⃣ Build a GroupShape (200 × 200 points) and set its bounds
GroupShape groupShape = new GroupShape(document, 200, 200);
groupShape.Bounds = new RectangleF(50, 50, 200, 200);

// 3️⃣ Add a rectangle shape
groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
{
    Width = 80,
    Height = 80,
    Left = 0,
    Top = 0
});

// 4️⃣ Add an ellipse shape next to the rectangle
groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
{
    Width = 80,
    Height = 80,
    Left = 100,
    Top = 0
});
```

**Warum das wichtig ist:**  
`GroupShape` wirkt wie ein Container. Wenn Sie später die Gruppe verschieben, reisen sowohl das Rechteck als auch die Ellipse zusammen und behalten ihre relativen Positionen bei. Dies ist der empfohlene Weg, mehrere Grafiken zu verwalten, die zum selben logischen Block gehören.

## Wie man ein Tag im Dokument einfügt

Jetzt, da die Gruppe fertig ist, können Sie **ein Tag einfügen** (ein StructuredDocumentTag, auch als SDT bekannt) direkt nach der Gruppe. Das Tag kann Klartext, Rich‑Text oder sogar wiederholende Inhalte enthalten.

```csharp
// 5️⃣ Insert the group at the current builder position
builder.InsertNode(groupShape);

// 6️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and write content
builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
builder.Writeln("Content inside the SDT");
```

**Warum Sie ein StructuredDocumentTag verwenden sollten:**  
Ein SDT liefert einen semantischen Marker, den Word für Inhaltssteuerelemente, Datenbindung oder Formular‑Ausfüll‑Szenarien erkennen kann. Durch die Verwendung von `InsertStructuredDocumentTag` geben Sie explizit **wie man ein Tag einfügt** an, sodass es nachfolgende Bearbeitungen in Microsoft Word übersteht.

## Wie man docx speichert und das Ergebnis überprüft

Der letzte Schritt besteht darin, das Dokument zu persistieren. Der untenstehende Code demonstriert den korrekten Weg, **das Dokument als docx zu speichern** und wo die Ausgabedatei zu finden ist.

```csharp
// 7️⃣ Save the document to the file system
string outputPath = Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.Desktop), "GroupAndSDT.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Wenn Sie *GroupAndSDT.docx* in Word öffnen, sollten Sie eine gruppierte Rechteck‑Ellipsen‑Grafik sehen, gefolgt von einem Klartext‑Inhaltssteuerelement mit dem Titel **MyTag**, das die Zeile „Content inside the SDT“ enthält.

### Erwartete Ausgabe

- Eine 200 × 200 Punkt‑Gruppe, positioniert bei (50, 50) auf der Seite.  
- Innerhalb der Gruppe: ein blaues Rechteck links und eine Ellipse rechts (Standardfarben).  
- Direkt unter der Gruppe: ein Inhaltssteuerelement mit der Beschriftung **MyTag** und dem Text „Content inside the SDT“.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in eine Konsolenanwendung kopieren‑und‑einfügen können. Es enthält alle notwendigen `using`‑Direktiven, Fehlerbehandlung und Kommentare, die jeden Schritt erklären.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeWordsGroupAndTag
{
    class Program
    {
        static void Main()
        {
            // Create a new empty document and a DocumentBuilder to work with it
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // Build a GroupShape (200x200) and define its bounds
            GroupShape groupShape = new GroupShape(document, 200, 200);
            groupShape.Bounds = new RectangleF(50, 50, 200, 200);

            // Add a rectangle to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Rectangle)
            {
                Width = 80,
                Height = 80,
                Left = 0,
                Top = 0
            });

            // Add an ellipse to the group
            groupShape.AppendChild(new Shape(document, ShapeType.Ellipse)
            {
                Width = 80,
                Height = 80,
                Left = 100,
                Top = 0
            });

            // Insert the group into the document at the current builder position
            builder.InsertNode(groupShape);

            // Insert a plain‑text StructuredDocumentTag (SDT) and write some content inside it
            builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");
            builder.Writeln("Content inside the SDT");

            // Save the resulting document
            string outputPath = Path.Combine(
                Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
                "GroupAndSDT.docx");

            document.Save(outputPath);
            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

Führen Sie das Programm aus, navigieren Sie zu Ihrem Desktop und doppelklicken Sie auf *GroupAndSDT.docx*, um zu überprüfen, dass die Gruppe und das Tag wie beschrieben erscheinen.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich mehr als zwei Formen zur Gruppe hinzufügen?** | Ja. Rufen Sie `groupShape.AppendChild(new Shape(...))` für jede zusätzliche Form auf, bevor Sie die Gruppe einfügen. |
| **Was, wenn ich ein Rich‑Text‑Tag anstelle von Klartext benötige?** | Verwenden Sie `StructuredDocumentTagType.RichText` in `InsertStructuredDocumentTag`. |
| **Wie ändere ich die Farbe des Rechtecks oder der Ellipse?** | Setzen Sie die Eigenschaft `FillColor` bei jeder `Shape`‑Instanz, z. B. `shape.FillColor = Color.LightBlue;`. |
| **Ist es möglich, die gesamte Gruppe zu drehen?** | Setzen Sie `groupShape.Rotation = 45;` (Grad) bevor Sie den Knoten einfügen. |
| **Muss ich `Dispose()` für irgendwelche Objekte aufrufen?** | Aspose.Words verwaltet die meisten Ressourcen intern; das Entsorgen des `Document` ist in einer kurzlebigen Konsolen‑App optional. |

## Best Practices für das Speichern von DOCX‑Dateien

- **Immer einen absoluten Pfad** (oder einen gut definierten relativen Pfad) verwenden, wenn Sie `document.Save` aufrufen. Das verhindert den „Datei nicht gefunden“-Fehler, der bei mehrdeutigen Arbeitsverzeichnissen auftreten kann.  
- **Bevorzugen Sie `Save`‑Überladungen, die einen Stream akzeptieren**, wenn Sie das Dokument über HTTP senden oder in einer Datenbank speichern müssen.  
- **Setzen Sie die `CompatibilityOptions**, falls Sie ältere Word‑Versionen (z. B. Word 2003) ansprechen müssen. Für die meisten modernen Szenarien funktionieren die Standardeinstellungen einwandfrei.

## Nächste Schritte

Jetzt, da Sie **wie man ein Tag einfügt**, **wie man Formen hinzufügt**, **wie man eine Gruppe erstellt** und **wie man docx speichert**, können Sie weiterführende Szenarien erkunden:

- Kombinieren Sie mehrere Gruppen, um komplexe Diagramme zu erstellen.  
- Verwenden Sie `StructuredDocumentTag` für Datenbindung in Word‑Vorlagen.  
- Exportieren Sie dasselbe Dokument nach PDF (`document.Save("output.pdf")`), während Sie die gruppierten Grafiken beibehalten.  
- Automatisieren Sie das Ausfüllen von Formularen, indem Sie programmgesteuert den Inhalt des SDT setzen (`builder.MoveToDocumentEnd(); builder.Write("New value");`).

Experimentieren Sie mit verschiedenen `ShapeType`‑Werten (z. B. `ShapeType.Polygon`, `ShapeType.Line`), um zu sehen, wie sie sich innerhalb einer `GroupShape` verhalten. Das gleiche Muster funktioniert für Tabellen, Bilder oder jedes andere Element, das Sie zusammenhalten möchten.

---

**Zusammenfassung:** Dieses Tutorial zeigte **wie man ein Tag einfügt** innerhalb einer gruppierten Form, **wie man Formen hinzufügt**, **wie man eine Gruppe erstellt** und die korrekte Methode, **das Dokument als docx zu speichern** mit Aspose.Words für .NET. Sie haben nun eine solide Grundlage, um programmgesteuert reichhaltige, interaktive DOCX‑Dateien zu erstellen.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to Save Markdown from DOCX – Step‑by‑Step Guide](/words/english/net/programming-with-markdownsaveoptions/how-to-save-markdown-from-docx-step-by-step-guide/)
- [How to Recover DOCX – Complete Guide Using Aspose.Words](/words/english/net/programming-with-loadoptions/how-to-recover-docx-complete-guide-using-aspose-words/)
- [How to Check Grammar in DOCX with Aspose.Words – use gpt-4 turbo](/words/english/net/ai-powered-document-processing/how-to-check-grammar-in-docx-with-aspose-words-use-gpt-4-tur/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}