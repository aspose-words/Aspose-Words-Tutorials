---
category: general
date: 2026-09-05
description: Lernen Sie, wie Sie ein leeres Word‑Dokument erstellen und mit Aspose.Words
  in C# ein Rechteck hinzufügen, das ausgeblendet werden kann.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- add rectangle shape
- how to hide shape
- hide shape word
- create hidden shape
language: de
lastmod: 2026-09-05
og_description: Erstellung eines leeren Word‑Dokuments und Einfügen einer versteckten
  Rechteckform mit Aspose.Words – Schritt‑für‑Schritt‑Anleitung für C#‑Entwickler.
og_image_alt: Screenshot of a blank Word document with a hidden rectangle shape created
  by Aspose.Words in C#
og_title: Erstelle ein leeres Word‑Dokument mit einer versteckten Rechteckform
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  headline: Create a blank word document and add a rectangle shape
  type: TechArticle
- description: Learn how to create a blank word document and add a rectangle shape
    that can be hidden using Aspose.Words in C#.
  name: Create a blank word document and add a rectangle shape
  steps:
  - name: Expected result
    text: 'Open `HiddenRectangle.docx` in Word:'
  - name: Can I hide multiple shapes at once?
    text: Yes. Create each shape, set `Hidden = true`, and insert them sequentially.
      The hidden flag works per node, so mixing hidden and visible shapes in the same
      document is supported.
  - name: What if I need the shape to be hidden only in the print view?
    text: 'Word distinguishes between **display** and **print** visibility through
      the `DisplayWhen` property. Aspose.Words does not expose a direct API for that
      flag, but you can modify the underlying XML:'
  - name: Does the hidden shape affect file size?
    text: A hidden shape adds the same XML payload as a visible one, so the file size
      increase is identical. However, because the shape
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Erstelle ein leeres Word‑Dokument und füge eine Rechteckform hinzu
url: /de/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein leeres Word-Dokument und fügen Sie eine Rechteckform hinzu

Wenn Sie eine **blank word document**-Erstellung benötigen, die außerdem eine Form enthält, die nicht im Layout erscheinen soll, zeigt Ihnen dieser Leitfaden genau, wie Sie dies mit Aspose.Words für .NET umsetzen. Sie sehen ein vollständiges, ausführbares Beispiel, das ein neues Dokument erstellt, eine Rechteckform hinzufügt, diese Form ausblendet und die Datei speichert – ohne zusätzliche Werkzeuge.

Das Tutorial behandelt alles von der Projektkonfiguration bis zur Fehlersuche bei häufigen Fallstricken. Am Ende können Sie eine Word-Datei erzeugen, die für den Leser leer aussieht, aber dennoch versteckte Metadaten enthält, was nützlich ist für Wasserzeichen, benutzerdefinierte XML-Speicherung oder Layout-Anker.

## Voraussetzungen

* .NET 6.0 SDK oder neuer (der Code funktioniert auch mit .NET Framework 4.7+)
* Visual Studio 2022 (oder jede IDE, die C# unterstützt)
* Eine aktive **Aspose.Words** NuGet-Lizenz (die kostenlose Testversion funktioniert zum Testen)
* Grundlegende Kenntnisse in C# und dem Konzept von Dokumentknoten

Sie können die Bibliothek mit dem folgenden CLI-Befehl installieren:

```bash
dotnet add package Aspose.Words
```

> **Profi‑Tipp:** Halten Sie Ihre Aspose.Words-Version auf dem neuesten Stand; die in diesem Tutorial verwendete API ist ab Version 23.10 stabil.

## So erstellen Sie ein leeres Word-Dokument mit Aspose.Words

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Ein neues `Document` repräsentiert ein leeres **blank word document** – keine Absätze, keine Abschnitte, nur den Dateicontainer.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new, empty Word document
Document document = new Document();
```

> **Warum das wichtig ist:** Das Beginnen mit einem leeren Dokument stellt sicher, dass die versteckte Form, die Sie später hinzufügen, nicht mit vorhandenem Inhalt oder Stilvorlagen interferiert.

## Fügen Sie dem Dokument eine Rechteckform hinzu

Als Nächstes erstellen wir eine rechteckige Form. In Aspose.Words ist eine Form ein Knoten, der überall im Dokumentbaum platziert werden kann und der mit Größe, Füllung, Linienstil und Sichtbarkeit konfiguriert werden kann.

```csharp
// Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(document);

// Define a rectangle shape (the "add rectangle shape" step)
Shape rectangle = new Shape(document, ShapeType.Rectangle)
{
    Width = 150,   // Width in points (1 point = 1/72 inch)
    Height = 80,   // Height in points
    FillColor = System.Drawing.Color.LightGray,
    StrokeColor = System.Drawing.Color.DarkGray,
    StrokeWeight = 0.5
};
```

Der obige Code erstellt ein sichtbares Rechteck. An dieser Stelle könnten Sie es mit `builder.InsertNode(rectangle)` in das Dokument einfügen. Da wir jedoch möchten, dass die Form verborgen bleibt, passen wir vor dem Einfügen ihre `Hidden`‑Eigenschaft an.

## So blenden Sie eine Form in einem Word-Dokument aus

Word stellt ein `Hidden`‑Attribut für Form‑Knoten bereit. Wenn es auf `true` gesetzt ist, erscheint die Form nicht im Seitenlayout, bleibt aber Teil des XML‑Dokuments. Dies ist der Kern der **how to hide shape**‑Anforderung.

```csharp
// Hide the shape so it won't be displayed
rectangle.Hidden = true;
```

> **Erklärung:** Das Setzen von `Hidden = true` fügt dem XML der Form das Attribut `<w:hide>` hinzu. Word‑Programme ignorieren die Form beim Rendern, doch die Form kann weiterhin programmgesteuert oder über die XML‑Ansicht von Word abgerufen werden.

## Fügen Sie die versteckte Form in das leere Dokument ein

Jetzt platzieren wir das versteckte Rechteck im Dokumentbaum. Da das Dokument noch leer ist, wird die Form zum ersten Knoten in der Hauptstory.

```csharp
// Insert the hidden rectangle at the current cursor position
builder.InsertNode(rectangle);
```

Wenn Sie die resultierende Datei in Microsoft Word öffnen, sehen Sie eine scheinbar leere Seite. Die Form ist vorhanden, aber unsichtbar.

## Dokument speichern

Abschließend schreiben Sie das Dokument auf die Festplatte. Sie können jedes unterstützte Format wählen (`.docx`, `.pdf`, `.odt` usw.). Für dieses Tutorial verwenden wir das moderne DOCX‑Format.

```csharp
// Save the file – adjust the path as needed
string outputPath = Path.Combine(Environment.CurrentDirectory, "HiddenRectangle.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

### Erwartetes Ergebnis

Öffnen Sie `HiddenRectangle.docx` in Word:

* Das Dokument erscheint leer (keine sichtbaren Formen oder Texte).
* Wenn Sie die Datei mit einem Tool wie **Open XML SDK** oder dem **Word XML Viewer** untersuchen, sehen Sie das `<w:pict>`‑Element, das das Rechteck mit dem `hidden`‑Attribut enthält.

![leeres Word-Dokument mit versteckter Rechteckform](image.png){: .align-center alt="leeres Word-Dokument mit versteckter Rechteckform"}

## Vollständiges, ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie in eine Konsolenanwendung kopieren‑und‑einfügen können. Es enthält alle erforderlichen `using`‑Direktiven, Fehlerbehandlung und Kommentare.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document
        Document document = new Document();

        // 2️⃣ Prepare a DocumentBuilder to manipulate the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Define a rectangle shape (add rectangle shape)
        Shape rectangle = new Shape(document, ShapeType.Rectangle)
        {
            Width = 150,
            Height = 80,
            FillColor = System.Drawing.Color.LightGray,
            StrokeColor = System.Drawing.Color.DarkGray,
            StrokeWeight = 0.5,
            // 4️⃣ Hide the shape (how to hide shape)
            Hidden = true
        };

        // 5️⃣ Insert the hidden shape into the blank document
        builder.InsertNode(rectangle);

        // 6️⃣ Save the document (create hidden shape)
        string outputPath = Path.Combine(
            Environment.CurrentDirectory, "HiddenRectangle.docx");
        document.Save(outputPath);

        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

Führen Sie das Programm (`dotnet run`) aus und überprüfen Sie die Ausgabedatei. Die Konsole bestätigt den Speicherort.

## Häufige Fragen und Sonderfälle

### Kann ich mehrere Formen gleichzeitig ausblenden?

Ja. Erstellen Sie jede Form, setzen Sie `Hidden = true` und fügen Sie sie nacheinander ein. Das Hidden‑Flag wirkt pro Knoten, sodass das Mischen von versteckten und sichtbaren Formen im selben Dokument unterstützt wird.

### Was ist, wenn die Form nur in der Druckansicht ausgeblendet sein soll?

Word unterscheidet zwischen **Anzeige**‑ und **Druck**‑Sichtbarkeit über die `DisplayWhen`‑Eigenschaft. Aspose.Words stellt dafür keine direkte API bereit, aber Sie können das zugrunde liegende XML anpassen:

```csharp
rectangle.GetShapeRenderer().GetShapeXml()
    .SetAttribute("w:display", "print");
```

Verwenden Sie dies nur, wenn Sie ausschließlich Druck‑Sichtbarkeit benötigen.

### Beeinflusst die versteckte Form die Dateigröße?

Eine versteckte Form fügt dieselbe XML‑Payload wie eine sichtbare hinzu, sodass die Dateigrößen‑Erhöhung identisch ist. Allerdings, weil die Form

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Erstellen Sie ein leeres Word-Dokument mit schattierter Rechteckform – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Schatten zu Word‑Form in C# hinzufügen](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}