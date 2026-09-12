---
category: general
date: 2026-09-11
description: Erfahren Sie, wie Sie ein Word‑Dokument erstellen, ein Rechteck hinzufügen
  und die Formabmessungen mit Aspose.Words festlegen. Schritt‑für‑Schritt C#‑Anleitung
  für präzise Formgrößen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: de
lastmod: 2026-09-11
og_description: Erstellen Sie ein Word-Dokument mit Aspose.Words in C#. Dieser Leitfaden
  zeigt, wie man ein Rechteck‑Shape hinzufügt, die Größe des Shapes festlegt und die
  Abmessungen des Shapes programmgesteuert verwaltet.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Word-Dokument mit Formen erstellen – Aspose.Words C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Wie man ein Word‑Dokument mit Formen mithilfe von Aspose.Words in C# erstellt
url: /de/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Word-Dokument mit Formen mit Aspose.Words in C# erstellt

Wenn Sie ein **Word-Dokument erstellen** müssen, das benutzerdefinierte Grafiken enthält, können Sie dies vollständig im Code erledigen. Dieses Tutorial führt Sie durch das Erstellen einer Word-Datei, das Hinzufügen einer Rechteckform und die Steuerung jeder Dimension der Form. Am Ende haben Sie ein wiederverwendbares Snippet, das Sie in jedes .NET-Projekt einbinden können.

Sie lernen, wie man **Rechteckform hinzufügen**, **Formgröße festlegen** und **Formabmessungen festlegen** innerhalb eines gruppierten Containers. Das Beispiel verwendet Aspose.Words 13.9, aber die Konzepte gelten auch für spätere Versionen. Vorkenntnisse mit der Aspose‑Zeichnungs‑API sind nicht erforderlich – nur Grundkenntnisse in C#.

## Voraussetzungen

- .NET 6.0 oder höher installiert  
- Aspose.Words für .NET NuGet-Paket (`Install-Package Aspose.Words`)  
- Eine IDE wie Visual Studio 2022 (jeder Editor, der C# unterstützt, funktioniert)  

Wenn Sie diese Werkzeuge bereit haben, können Sie den Code sofort ausführen, ohne zusätzliche Konfiguration.

## Schritt 1: Dokument und Builder initialisieren – Grundlagen zum Erstellen eines Word-Dokuments

Der erste Vorgang besteht darin, ein `Document`‑Objekt und einen `DocumentBuilder` zu instanziieren. Das `Document` repräsentiert die Datei selbst, während der `DocumentBuilder` eine fluente API zum Einfügen von Inhalten bereitstellt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Warum das wichtig ist:**  
Das vorherige Erstellen des Dokuments gibt Ihnen eine leere Leinwand. Der Cursor des Builders startet im ersten Absatz, wo wir später **Formen in Word erstellen** werden.

## Schritt 2: Einen GroupShape erstellen, um mehrere Grafiken zu halten

Ein `GroupShape` fungiert als Container; Sie können die gesamte Gruppe als Einheit verschieben, drehen oder skalieren. Hier definieren wir die Breite und Höhe des Containers in Punkten (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Warum das wichtig ist:**  
Das Gruppieren von Formen vereinfacht die Layoutverwaltung. Wenn Sie später weitere Formen hinzufügen müssen (z. B. Kreise oder Textfelder), erben sie die Position und Skalierung der Gruppe.

## Schritt 3: Eine Rechteckform erstellen und ihre Abmessungen konfigurieren

Jetzt fügen wir das eigentliche Rechteck hinzu. Der `Shape`‑Konstruktor benötigt die Dokumentreferenz und den Formtyp. Nach der Erstellung setzen wir explizit **Formgröße festlegen** und **Formabmessungen festlegen**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Warum das wichtig ist:**  
Die Angabe von Breite, Höhe, links und oben gibt Ihnen pixelgenaue Kontrolle über die Form. Das ist entscheidend, wenn das Dokument einer Designspezifikation oder einem gedruckten Formular entsprechen muss.

## Schritt 4: Die Gruppe durch Anhängen des Rechtecks zusammenstellen

Das Anhängen des Rechtecks an das `GroupShape` macht es zu einem Kindknoten. Sie können beliebig viele Kinder hinzufügen, bevor Sie die Gruppe in das Dokument einfügen.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Tipp:** Wenn Sie planen, eine zweite Form hinzuzufügen, erstellen Sie sie auf dieselbe Weise und rufen Sie `group.AppendChild(secondShape)` auf. Alle Kinder teilen das Koordinatensystem der Gruppe.

## Schritt 5: Die gruppierte Form in das Dokument einfügen und speichern

Nachdem die Gruppe vollständig gebaut ist, platzieren wir sie im aktuellen Absatz. Die `CurrentParagraph`‑Eigenschaft des Builders bietet direkten Zugriff auf den zugrunde liegenden Knotbaum.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Warum das wichtig ist:**  
Das Anhängen der Gruppe an einen Absatz stellt sicher, dass die Form inline mit dem Textfluss erscheint. Das Speichern des Dokuments finalisiert die **Word-Dokument erstellen**‑Operation.

## Häufige Variationen und Sonderfälle

| Szenario | Anpassung |
|----------|------------|
| **Andere Seitenorientierung** | Setzen Sie `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` bevor Sie die Gruppe erstellen. |
| **Mehrere Rechtecke** | Erstellen Sie zusätzliche `Shape`‑Objekte und rufen Sie für jedes `group.AppendChild(newRect)` auf. |
| **Dynamische Größe basierend auf Inhalt** | Berechnen Sie Breite/Höhe aus Bildabmessungen oder Textmetriken und weisen Sie sie dann `rectangle.Width` / `rectangle.Height` zu. |
| **Export nach PDF** | Nach `doc.Save` rufen Sie `doc.Save("GroupShape.pdf", SaveFormat.Pdf);` auf. |
| **Kompatibilität mit älteren Word-Versionen** | Speichern Sie mit `SaveFormat.Doc` anstelle von `Docx` für die Kompatibilität mit Word 97‑2003. |

## Vollständiges, ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie kopieren, einfügen und ausführen können. Es enthält alle `using`‑Direktiven, einen `Main`‑Einstiegspunkt und Kommentare, die jede Zeile erklären.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Erwartete Ausgabe:**  
Wenn Sie *GroupShape.docx* öffnen, zeigt die erste Seite ein grau umrandetes Rechteck, das 50 pt vom linken/oberen Rand entfernt ist, wobei das Rechteck selbst 10 pt innerhalb der Gruppe versetzt ist. Die Abmessungen entsprechen den im Code festgelegten Werten.

## Fazit

Sie wissen jetzt, wie man **Word-Dokument erstellt**, **Rechteckform hinzufügt** und mithilfe von Aspose.Words präzise **Formgröße festlegen** und **Formabmessungen festlegen**. Der gruppierte‑Form‑Ansatz hält Ihr Layout flexibel und bereit für zukünftige Erweiterungen wie zusätzliche Grafiken oder Textfelder.

Als Nächstes erkunden Sie verwandte Themen wie **Formen in Word erstellen** für Kreise, Pfeile oder benutzerdefinierte SVG‑Pfade und lernen, wie man **Formfüllfarbe festlegen** oder **Rotation anwenden**. Experimentieren Sie mit verschiedenen Messungen, um zu sehen, wie Word Punkte gegenüber Zentimetern rendert, und integrieren Sie den Code in größere Dokument‑Generierungs‑Pipelines.

Viel Spaß beim Programmieren, und fühlen Sie sich frei, dieses Muster an jedes automatisierte Reporting‑ oder Formularausfüll‑Szenario anzupassen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Leeres Word-Dokument mit schattierter Rechteckform erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape‑Schatten‑Tutorial – Schatten zu Word‑Form in C# hinzufügen](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}