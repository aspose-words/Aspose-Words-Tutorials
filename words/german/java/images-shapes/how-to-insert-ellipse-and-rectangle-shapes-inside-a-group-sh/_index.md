---
category: general
date: 2026-10-23
description: Erfahren Sie, wie Sie in Word mit Aspose.Words eine Ellipse einfügen
  und ein Rechteck hinzufügen. Enthält das Verschieben des Cursors zur Form und das
  Erstellen einer Gruppierung von Formen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert ellipse
- how to add rectangle
- move cursor to shape
- insert rectangle shape word
- how to create group shape
language: de
lastmod: 2026-10-23
og_description: Wie man eine Ellipse einfügt und ein Rechteck in Word mit Aspose.Words
  hinzufügt. Folgen Sie der Schritt‑für‑Schritt‑Anleitung, um den Cursor zur Form
  zu bewegen und eine Gruppierung von Formen zu erstellen.
og_image_alt: Screenshot of a Word document showing a group shape containing a rectangle
  and an ellipse
og_title: Wie man Ellipsen‑ und Rechteckformen in einer Word‑Gruppierung einfügt
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Learn how to insert ellipse and how to add rectangle shape in Word
    using Aspose.Words. Includes move cursor to shape and how to create group shape.
  headline: How to insert ellipse and rectangle shapes inside a group shape with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man Ellipsen‑ und Rechteckformen in eine Gruppierungsform mit Aspose.Words
  einfügt
url: /de/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Ellipsen- und Rechteckformen in einer Gruppierungsform mit Aspose.Words einfügt

Wenn Sie wissen möchten, **wie man eine Ellipse** in ein Word‑Dokument programmgesteuert einfügt, zeigt Ihnen diese Anleitung den kompletten Prozess. Sie werden außerdem sehen, **wie man ein Rechteck** einfügt, lernen, **den Cursor zur Form zu bewegen**, und entdecken, **wie man eine Gruppierungsform** erstellt, die mehrere Zeichenobjekte enthält.

Word‑Automatisierung erfordert häufig eine präzise Positionierung von Zeichenobjekten. Am Ende dieses Tutorials können Sie eine `.docx`‑Datei erzeugen, die ein gruppiertes Rechteck und eine Ellipse enthält, bereit für weitere Formatierung oder den Export. Es werden keine externen Werkzeuge benötigt, außer der Aspose.Words‑für‑.NET‑Bibliothek und einer .NET‑Entwicklungsumgebung.

## Voraussetzungen

* .NET 6.0 oder höher installiert.
* Aspose.Words für .NET (NuGet‑Paket `Aspose.Words`) zu Ihrem Projekt hinzugefügt.
* Grundlegende Kenntnisse der C#‑Syntax und von Visual Studio (oder einer beliebigen IDE).

Diese Voraussetzungen stellen sicher, dass der Code ohne zusätzliche Konfiguration kompiliert.

## Wie man eine Gruppierungsform in Word erstellt

Eine Gruppierungsform fungiert als Container, der es ermöglicht, mehrere Formen als eine Einheit zu verschieben, zu drehen oder zu formatieren. Der folgende Code erstellt eine Gruppe mit einer bestimmten Größe (300 × 200 Punkte) und bereitet das Dokument für weitere Zeichenoperationen vor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class GroupShapeDemo
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a group shape that will act as a container for other shapes.
        GroupShape group = builder.InsertGroupShape(300, 200);
        
        // The group shape is now part of the document.
        // Subsequent shape insertions will be placed inside this group.
```

*Warum dieser Schritt wichtig ist*: Die Gruppierungsform definiert ein lokales Koordinatensystem. Alle Formen, die nach dem Verschieben des Cursors in die Gruppe hinzugefügt werden, werden relativ zum Ursprung der Gruppe positioniert, wodurch Layout‑Berechnungen einfach werden.

## Wie man ein Rechteck in Word hinzufügt

Jetzt, da die Gruppe existiert, können Sie **ein Rechteck** darin einfügen. Das Rechteck dient als Hintergrund oder als visueller Platzhalter für andere Inhalte.

```csharp
        // Move the cursor into the group so that the next shape is added to it.
        builder.MoveTo(group);
        
        // Insert a rectangle of width 100 points and height 50 points.
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

*Erklärung*: `MoveTo(group)` teilt dem Builder mit, dass der aktive Einfügepunkt die Gruppierungsform ist. Ohne das Verschieben des Cursors würde `InsertShape` das Rechteck zum Hauptdokumentkörper hinzufügen statt zur Gruppe.

## Wie man eine Ellipse einfügt

Mit dem Rechteck an Ort und Stelle können Sie nun **zeigen, wie man eine Ellipse einfügt**. Die Ellipse wird innerhalb derselben Gruppe zentriert und überlappt das Rechteck, falls gewünscht.

```csharp
        // Keep the cursor inside the same group.
        builder.MoveTo(group);
        
        // Insert an ellipse of width 80 points and height 80 points.
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

*Warum der Cursor verschoben werden muss*: Jeder Aufruf von `InsertShape` beachtet die aktuelle Cursorposition. Das erneute Aufrufen von `MoveTo(group)` stellt sicher, dass die Ellipse ebenfalls ein Kind der Gruppe ist und die beabsichtigte Hierarchie bewahrt bleibt.

## Cursor zur Form bewegen, bevor weitere Objekte eingefügt werden

Wenn Sie später weitere Formen hinzufügen müssen, bewegen Sie stets **den Cursor zur Form**, bevor Sie einfügen. Dieses Muster verhindert eine versehentliche Platzierung außerhalb der Gruppe.

```csharp
        // Example: add a third shape, such as a line.
        builder.MoveTo(group);
        builder.InsertShape(ShapeType.Line, 150, 0);
```

*Tipp*: Das wiederholte Verwenden von `MoveTo(group)` ist kostengünstig und verbessert die Lesbarkeit des Codes. Es erleichtert zudem die zukünftige Wartung, da der Einfüge‑Kontext explizit ist.

## Dokument speichern

Abschließend wird das Dokument auf dem Datenträger gespeichert. Das Beispiel speichert die Datei als `GroupShape.docx` in einem von Ihnen angegebenen Ordner.

```csharp
        // Save the document to the desired location.
        document.Save(@"C:\Temp\GroupShape.docx");
    }
}
```

Wenn Sie die gespeicherte Datei in Microsoft Word öffnen, sehen Sie eine einzelne Gruppe, die ein Rechteck und eine Ellipse enthält, beide korrekt positioniert.

### Erwartete Ausgabe

* Eine `.docx`‑Datei mit dem Namen `GroupShape.docx`.
* Im Dokument ein gruppiertes Zeichenobjekt mit der Größe 300 × 200 Punkte.
* Innerhalb der Gruppe:
  * Ein Rechteck (100 × 50 Punkte) am Ursprung der Gruppe.
  * Eine Ellipse (80 × 80 Punkte), die das Rechteck überlappt.
  * Alle zusätzlichen Formen, die Sie nach dem Verschieben des Cursors hinzugefügt haben.

## Häufige Variationen und Sonderfälle

| Situation | Empfohlener Ansatz |
|-----------|--------------------|
| **Different unit sizes** | Aspose.Words verwendet Punkte (1 pt = 1/72 in). Konvertieren Sie Zentimeter oder Zoll in Punkte, bevor Sie `InsertShape` aufrufen. |
| **Rotating shapes inside the group** | Nach dem Einfügen einer Form rufen Sie das `ShapeBase`‑Objekt ab und setzen `ShapeBase.RotationAngle`. |
| **Adding text inside a shape** | Verwenden Sie `ShapeBase.AppendChild(new Paragraph(document))` und fügen Sie anschließend einen `Run` mit dem gewünschten Text hinzu. |
| **Saving to PDF instead of DOCX** | Rufen Sie `document.Save("GroupShape.pdf", SaveFormat.Pdf);` auf – die Gruppen‑Hierarchie wird im PDF‑Ausgabe erhalten. |

Diese Variationen zeigen, dass dieselbe **how to insert ellipse**‑Logik für viele reale Szenarien angepasst werden kann.

## Pro‑Tipps

* **Verwenden Sie dieselbe `DocumentBuilder`‑Instanz erneut** – sie reduziert den Speicherverbrauch und hält den Dokumentzustand konsistent.
* **Validieren Sie die Formabmessungen** – extrem große Breiten oder Höhen können in älteren Word‑Versionen Darstellungsprobleme verursachen.
* **Gruppieren Sie vor dem Stylen** – das Anwenden von Füllfarben oder Linienstilen auf die Gruppe, nachdem alle Kinder hinzugefügt wurden, sorgt für ein einheitliches Erscheinungsbild.

## Fazit

Sie verstehen nun **how to insert ellipse** und **how to add rectangle** innerhalb eines gruppierten Containers in einem Word‑Dokument mit Aspose.Words. Indem Sie konsequent **move cursor to shape** vor jedem Einfügen ausführen, erhalten Sie eine saubere Hierarchie und vermeiden versehentliche Platzierungen. Das vollständige Beispiel kompiliert, läuft und erzeugt eine gruppierte Form, die weiter angepasst oder exportiert werden kann.

Bereit, mehr zu entdecken? Versuchen Sie, diese Technik mit **how to create group shape** für komplexe Diagramme zu kombinieren, oder experimentieren Sie mit **insert rectangle shape word** zusammen mit Textfeldern für die Erstellung umfangreicher Berichte. Viel Spaß beim Programmieren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man Rechteckformen und Gruppierungsformen in Word mit Aspose.Words erstellt](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Wie man ein leeres Word‑Dokument erstellt und eine versteckte Ellipse in C# hinzufügt](/words/english/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/)
- [Wie man eine Gruppierungsform‑docx erstellt und interaktive Steuerelemente in C# hinzufügt](/words/english/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}