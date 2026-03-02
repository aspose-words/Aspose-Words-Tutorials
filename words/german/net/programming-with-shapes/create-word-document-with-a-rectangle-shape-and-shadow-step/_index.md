---
category: general
date: 2026-03-01
description: Erstellen Sie ein Word-Dokument mit Aspose.Words und lernen Sie, wie
  man ein Rechteck hinzufügt, wie man einen Schatten hinzufügt, wie man die Transparenz
  einstellt und wie man eine Form erstellt – alles in C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: de
og_description: Erstellen Sie ein Word-Dokument mit Aspose.Words in C#. Erfahren Sie,
  wie Sie eine Rechteckform hinzufügen, einen äußeren Schatten anwenden und die Transparenz
  in nur wenigen Schritten einstellen.
og_title: Word-Dokument mit Rechteckform und Schatten erstellen – Anleitung
tags:
- Aspose.Words
- C#
- Document Generation
title: Word-Dokument mit einer Rechteckform und Schatten erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines Word-Dokuments mit einer Rechteckform und Schatten – Schritt‑für‑Schritt‑Anleitung

Haben Sie jemals **Word-Dokument erstellen** benötigt, das ein individuell gestaltetes Rechteck enthält? Vielleicht erstellen Sie eine Berichtsvorlage und möchten einen dezenten Drop‑Shadow, um das Layout hervorzuheben. Sie sind nicht allein – Entwickler fragen ständig: „Wie füge ich programmatisch eine Rechteckform und einen Schatten hinzu?“ Die gute Nachricht: Mit Aspose.Words können Sie das in wenigen Zeilen erledigen.

In diesem Tutorial führen wir Sie durch den gesamten Prozess: vom Erzeugen einer leeren Word‑Datei über das Hinzufügen einer Rechteckform bis hin zur Konfiguration eines äußeren Schattens mit Transparenz. Am Ende haben Sie ein einsatzbereites `Shadow.docx`, das Sie in Word öffnen und den Effekt sofort sehen können. Keine externen Tools, kein umständliches XML – nur sauberer C#‑Code und klare Erklärungen.

## Was Sie lernen werden

- **How to create shape** Objekte in einem Word-Dokument mit Aspose.Words erstellen.
- **How to add rectangle shape** zu einem Absatz hinzufügen, ohne den vorhandenen Inhalt zu stören.
- **How to add shadow** (outer shadow) und seine Farbe, Versatz, Unschärfe und Transparenz steuern.
- **How to set transparency** für den Schatten festlegen, damit er professionell aussieht.
- Tipps, Fallstricke und Varianten, die Sie in realen Projekten benötigen könnten.

### Voraussetzungen

- .NET 6.0 oder höher (die API funktioniert auch mit .NET Framework 4.6+).
- Aspose.Words für .NET über NuGet installiert (`Install-Package Aspose.Words`).
- Grundlegendes Verständnis der C#‑Syntax – nichts Besonderes, nur die üblichen `using`‑Anweisungen und Objekterstellung.

> **Pro tip:** Wenn Sie Visual Studio verwenden, aktivieren Sie „nullable reference types“, um potenzielle Null‑Referenz‑Fehler frühzeitig zu erkennen.

## Schritt 1 – Erstellen eines leeren Word-Dokuments

Um **Word-Dokument erstellen** zu können, beginnen wir mit der Klasse `Document`. Betrachten Sie sie als leere Leinwand; später können Sie Abschnitte, Absätze, Tabellen oder Formen hinzufügen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Warum benötigen wir eine frische `Document`‑Instanz? Weil jede Form, jeder Absatz oder Stil im Document Object Model (DOM) lebt. Ein sauberes Dokument stellt sicher, dass das Rechteck, das Sie hinzufügen, den vorhandenen Inhalt nicht beeinträchtigt.

## Schritt 2 – Definieren der Rechteckform

Jetzt **how to create shape** ein Rechteck. Der `Shape`‑Konstruktor erhält das zugehörige Dokument und den Formtyp. Außerdem setzen wir Breite und Höhe in Punkten (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Vielleicht fragen Sie sich: „Kann ich Zentimeter statt Punkte verwenden?“ Die API akzeptiert nur Punkte, aber Sie können konvertieren: `points = centimeters * 28.35`. Diese kleine Umrechnung ist praktisch, wenn Sie Formen an Seitenrändern ausrichten.

## Schritt 3 – Hinzufügen eines äußeren Schattens und Festlegen der Transparenz

Hier passiert die Magie: **how to add shadow** und **how to set transparency** für diesen Schatten. Die Eigenschaft `ShadowFormat` gibt Ihnen die volle Kontrolle.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Warum diese Einstellungen?**  
- **Transparency** lässt die darunterliegende Seitenstruktur durchscheinen und verhindert, dass der Schatten zu schwer wirkt.  
- **OffsetX/Y** erzeugen die Illusion, dass die Form von der Seite abgehoben ist.  
- **BlurRadius** mildert die Kanten – ohne ihn wäre der Schatten ein harter Rechteck, was unnatürlich wirkt.  

Wenn Sie einen dramatischeren Effekt benötigen, erhöhen Sie `OffsetX/Y` auf 10 und `BlurRadius` auf 8. Für einen dezenten Hinweis lassen Sie beide bei 2.

## Schritt 4 – Einfügen der Form in das Dokument

Wir **add rectangle shape** jetzt in den ersten Absatz des Dokuments. Hat das Dokument keinen Inhalt, wird `FirstParagraph` automatisch für Sie erstellt.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Was, wenn Sie die Form in einer bestimmten Tabellenzelle oder einem späteren Absatz haben möchten? Suchen Sie einfach den Knoten (`doc.GetChild(NodeType.Paragraph, index, true)`) und rufen Sie `AppendChild` darauf auf. Das gleiche Form‑Objekt kann geklont werden, falls Sie mehrere Kopien benötigen.

## Schritt 5 – Dokument speichern

Schließlich **create word document** wir die Datei auf dem Datenträger. Verwenden Sie einen Pfad, der zu Ihrer Umgebung passt; das Beispiel nutzt einen Platzhalter.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Wenn Sie `Shadow.docx` in Microsoft Word öffnen, sehen Sie ein hellgraues Rechteck mit einem weichen äußeren Schatten, der nach unten rechts versetzt ist. Die 30 %‑Transparenz des Schattens sorgt dafür, dass er die Seite nicht dominiert.

---

![Word-Dokument mit einer schattierten Rechteckform erstellen](image.png "Word-Dokument mit einer schattierten Rechteckform")

*Bildbeschreibung: Word-Dokument mit einer schattierten Rechteckform erstellen*

## Vollständiger, sofort ausführbarer Code

Unten finden Sie das komplette Programm, das Sie in eine Konsolen‑App kopieren‑und‑einfügen können. Keine fehlenden Teile, kein „siehe Dokumentation für mehr“.

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

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Erwartetes Ergebnis

- Eine Datei namens **Shadow.docx** erscheint im Zielordner.
- Beim Öffnen in Word wird ein Rechteck (200 × 100 pt) mit einem dunkelgrauen äußeren Schatten angezeigt.
- Der Schatten ist um 5 pt horizontal und vertikal versetzt, unscharf und zu 30 % transparent.

## Häufige Fragen & Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich die Schattenfarbe an meine Marke anpassen?** | Absolut – ersetzen Sie einfach `System.Drawing.Color.DarkGray` durch jede gewünschte `Color`, z. B. `Color.FromArgb(255, 0, 120, 215)` für einen blauen Akzent. |
| **Was, wenn ich einen inneren Schatten statt eines äußeren möchte?** | Setzen Sie `ShadowFormat.Style = ShadowStyle.InnerShadow`. Die übrigen Eigenschaften funktionieren gleich. |
| **Wird Transparenz in älteren Word‑Versionen unterstützt?** | Ja. Aspose.Words schreibt das passende XML, das Word 2007+ versteht. Ältere Versionen ignorieren möglicherweise den Transparenzwert, zeigen aber trotzdem den Schatten. |
| **Kann ich mehrere Formen mit unterschiedlichen Schatten hinzufügen?** | Sicher – erstellen Sie einfach neue `Shape`‑Instanzen, konfigurieren Sie jeden Schatten separat und hängen Sie sie an die gewünschten Knoten an. |
| **Wie wirkt sich das bei Hunderten von Formen auf die Performance aus?** | Viele Formen können den Speicherverbrauch erhöhen. Verwenden Sie eine einzige `Document`‑Instanz und fügen Sie Formen in einer Schleife hinzu; entsorgen Sie temporäre Objekte, falls Sie an Grenzen stoßen. |

## Tipps für reale Projekte

- **Batch-Generierung:** Beim Erstellen von Berichten für viele Benutzer instanziieren Sie eine einzelne `Document`‑Vorlage und klonen sie für jede Iteration. Ersetzen Sie Platzhalter, bevor Sie Formen anhängen.
- **Dynamische Größenanpassung:** Verwenden Sie Seitenabmessungen (`document.FirstSection.PageSetup.PageWidth`), um die Formgröße relativ zur Seite zu berechnen und ein konsistentes Layout über verschiedene Papiergrößen hinweg sicherzustellen.
- **Testing:** Öffnen Sie die erzeugte `.docx` immer in Word, nachdem Sie die Schattenparameter geändert haben. Visuelles Feedback ist schneller als Zahlen zu raten.

## Nächste Schritte

Jetzt, wo Sie **how to add rectangle shape**, **how to add shadow** und **how to set transparency** kennen, können Sie Folgendes erkunden:

- Hinzufügen von **Verlaufsfüllungen** zu Formen (`Shape.FillFormat`).
- Einbetten von **Bildern** in Formen für Wasserzeichen‑Effekte.
- Verwendung von **Tabellen**, um mehrere schattierte Formen in einem Raster auszurichten.
- Exportieren desselben Dokuments nach PDF (`document.Save("output.pdf")`), wobei Schatten erhalten bleiben.

Jeder dieser Punkte baut auf denselben Kernkonzepten auf, sodass Sie sich beim Erweitern des Codes wohl fühlen werden.

### Zusammenfassung

Wir begannen mit **Word-Dokument erstellen** mittels Aspose.Words, dann **how to create shape** ein Rechteck, wendeten **how to add shadow** an, passten **how to set transparency** an und speicherten das Ergebnis. Der gesamte Prozess lässt sich in ein kompaktes, wiederverwendbares Muster fassen, das Sie an jede Automatisierungssituation anpassen können.

Experimentieren Sie gern – ändern Sie Farben, spielen Sie mit Versätzen oder stapeln Sie mehrere Formen übereinander. Wenn Sie auf ein Problem stoßen, schauen Sie noch einmal in die obigen Abschnitte; sie dienen als schnelle Referenz. Viel Spaß beim Coden und mögen Ihre Dokumente stets professionell aussehen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}