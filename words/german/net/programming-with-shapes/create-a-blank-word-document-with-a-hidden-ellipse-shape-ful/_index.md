---
category: general
date: 2026-07-29
description: Erstellen Sie ein leeres Word‑Dokument und lernen Sie, wie Sie eine Form
  ausblenden, ein verstecktes Objekt erstellen und eine Ellipsenform mit Aspose.Words
  in C# erzeugen. Schritt‑für‑Schritt‑Code ist enthalten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: de
lastmod: 2026-07-29
og_description: Erstellen Sie ein leeres Word‑Dokument und verbergen Sie die Form
  sofort. Lernen Sie, ein verstecktes Objekt zu erstellen und eine Ellipsenform mit
  Aspose.Words in C# zu zeichnen.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Erstelle ein leeres Word‑Dokument mit einer versteckten Ellipse – C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Ein leeres Word‑Dokument mit einer versteckten Ellipsenform erstellen – Vollständige
  C#‑Anleitung
url: /de/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines leeren Word-Dokuments mit einer versteckten Ellipsenform – Vollständige C#‑Anleitung

Haben Sie jemals ein **leeres Word‑Dokument** erstellen und darin eine Form verstecken müssen? Vielleicht generieren Sie eine Vorlage, bei der bestimmte Marker erst später sichtbar werden sollen. In diesem Tutorial zeigen wir Ihnen genau **wie man eine Form versteckt**, wie man ein **verstecktes Objekt erstellt** und sogar wie man eine **Ellipsenform erstellt** mit Aspose.Words für .NET. Am Ende haben Sie ein sofort ausführbares C#‑Snippet, das eine DOCX‑Datei mit einer unsichtbaren Ellipse erzeugt.

## Was Sie lernen werden

- Ein frisches leeres Word‑Dokument mit Aspose.Words initialisieren.  
- Eine Ellipsenform erstellen, ihre Abmessungen festlegen und sie auf der Seite positionieren.  
- Die Form als versteckt markieren, sodass sie weder auf dem Bildschirm noch beim Drucken erscheint.  
- Das Ergebnis auf die Festplatte speichern und überprüfen, dass das versteckte Objekt wirklich unsichtbar ist.  

Keine externen Bibliotheken außer Aspose.Words sind erforderlich, und der Code funktioniert mit Version 24.10 oder neuer (die `Hidden`‑Eigenschaft wurde in diesem Release eingeführt). Lassen Sie uns beginnen.

![Diagramm einer versteckten Ellipse in einem leeren Word‑Dokument](https://example.com/hidden-ellipse.png "Versteckte Ellipsenform in ein leeres Word‑Dokument eingefügt")

## Leeres Word‑Dokument erstellen und eine versteckte Ellipsenform einfügen

Der erste Schritt besteht darin, ein brandneues Dokument zu erzeugen. Denken Sie an `Document` als leere Leinwand; `DocumentBuilder` ist Ihr Pinsel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Warum mit einem leeren Dokument beginnen?**  
> Ein sauberer Anfang stellt sicher, dass kein bereits vorhandener Inhalt die versteckte Form, die Sie hinzufügen möchten, beeinträchtigt. Außerdem ist das Beispiel so einfacher in jedes Projekt zu kopieren und einzufügen.

## Wie man eine Form versteckt: Setzen der Hidden‑Eigenschaft

Aspose.Words 24.10 hat das `Hidden`‑Flag bei `Shape` eingeführt. Wenn es auf `true` gesetzt wird, behandelt Word die Form wie einen Kommentar — vollständig unsichtbar in der Benutzeroberfläche und beim Drucken.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Pro‑Tipp:** Wenn Sie die Form später programmgesteuert sichtbar machen wollen, setzen Sie einfach `ellipseShape.Hidden = false;` und speichern das Dokument erneut.

## Verstecktes Objekt erstellen: Die Form in das Dokument einfügen

Jetzt, wo die Ellipse vorbereitet und versteckt ist, fügen wir sie an der aktuellen Cursorposition des Builders ein. Die Position des Builders ist standardmäßig am Anfang des ersten Absatzes, was für ein leeres Dokument ideal ist.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **Was, wenn die Form auf einer bestimmten Seite liegen soll?**  
> Bewegen Sie den Builder zuerst zur gewünschten Seite (`builder.MoveToDocumentEnd();` oder `builder.MoveToPage(pageNumber);`), bevor Sie `InsertNode` aufrufen.

## Das Dokument mit der versteckten Form speichern

Zum Schluss schreiben wir die Datei auf die Festplatte. Das Ergebnis ist ein normales DOCX, das jeder Textverarbeiter öffnen kann — außer dass die Ellipse unsichtbar bleibt.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Erwartete Ausgabe:** Öffnen Sie `HiddenShape.docx` in Microsoft Word. Sie sehen keine Grafiken, aber die Dateigröße ist etwas größer als bei einem wirklich leeren Dokument, weil die versteckte Ellipse im XML gespeichert ist.

## Versteckte Ellipse programmgesteuert überprüfen (optional)

Wenn Sie sicher gehen wollen, dass die Form tatsächlich versteckt ist, können Sie die gespeicherte Datei laden und die `Hidden`‑Eigenschaft der Form prüfen:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Das Ausführen dieses Snippets gibt `True` aus und bestätigt, dass das versteckte Objekt den Speicher‑Lade‑Zyklus überstanden hat.

## Randfälle und häufige Fragen

### Was, wenn die Ziel‑Word‑Version versteckte Formen nicht unterstützt?

Das `Hidden`‑Flag ist Teil der Office Open XML‑Spezifikation und wird von Word 2007+ sowie LibreOffice respektiert. Ältere Formate (z. B. `.doc`) ignorieren das Flag, daher sollten Sie immer als `.docx` speichern, wenn Sie ein zuverlässiges Verstecken benötigen.

### Kann ich andere Objekttypen (Bilder, Tabellen) verstecken?

Ja. Jeder Knoten, der von `Shape` abgeleitet ist — einschließlich Bilder, Textfelder und sogar SmartArt — bietet die `Hidden`‑Eigenschaft. Setzen Sie sie einfach vor dem Einfügen auf `true`.

### Beeinträchtigt das Verstecken einer Form die Dokumentleistung?

Nur unwesentlich. Die Form wird als XML‑Markup gespeichert, und Word überspringt das Rendern versteckter Objekte während des Layouts. Wenn Sie viele versteckte Objekte einbetten, wächst die Dateigröße, aber das Rendern bleibt schnell.

### Wie unterscheidet sich das von einem Lesezeichen oder Kommentar als Marker?

Lesezeichen sind per Definition unsichtbar, dienen jedoch der Navigation, nicht als visuelle Platzhalter. Kommentare erscheinen im Rand. Eine versteckte Form liefert Ihnen ein visuelles Objekt (Größe, Position), das Sie später enthüllen oder manipulieren können – praktisch für Vorlagen‑Szenarien.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort kopier‑und‑einfüg‑bereite Programm. Es enthält alle using‑Direktiven, die Erstellung der versteckten Ellipse und einen Verifizierungsschritt.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Das Ausführen des Programms erzeugt `HiddenEllipse.docx` im Ausführungsordner. Öffnen Sie die Datei — Sie sehen eine völlig normale leere Seite, doch die versteckte Ellipse befindet sich still im Dokument.

## Zusammenfassung

Wir haben behandelt, wie man **ein leeres Word‑Dokument erstellt**, **eine Form versteckt**, **ein verstecktes Objekt erstellt** und **eine Ellipsenform erstellt**, alles mit wenigen C#‑Zeilen. Die zentrale Erkenntnis ist die `Hidden`‑Eigenschaft von `Shape`, die jedes visuelle Element zu einem unsichtbaren Marker macht, ohne die Word‑Kompatibilität zu brechen.

## Was kommt als Nächstes?

- **Die versteckte Form formatieren** (Füllfarbe, Linienstil), sodass sie beim späteren Enthüllen exakt wie gewünscht aussieht.  
- **Versteckte Formen mit Lesezeichen kombinieren**, um dynamische Vorlagen zu bauen, die ein‑ oder ausgeschaltet werden können.  
- **Weitere Formtypen erkunden** — Rechtecke, Pfeile oder sogar benutzerdefinierte SVG‑Pfade — indem Sie `ShapeType.Ellipse` austauschen.  

Probieren Sie es aus: Ändern Sie die Größe, verschieben Sie die Position oder fügen Sie mehrere versteckte Ellipsen ein. Das gleiche Muster funktioniert für jede Aspose.Words‑Form, die Sie aus dem Blickfeld halten möchten.

Wenn Sie auf ein Problem stoßen oder Ideen haben, dieses Muster zu erweitern, hinterlassen Sie einen Kommentar unten. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}