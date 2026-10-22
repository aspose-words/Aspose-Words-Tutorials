---
category: general
date: 2026-09-05
description: Erstellen Sie ein Rechteck in einem Word-Dokument mit Aspose.Words und
  lernen Sie, wie Sie eine Ellipse einfügen und Formen in Word gruppieren, um reichhaltigere
  Layouts zu erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: de
lastmod: 2026-09-05
og_description: Erstellen Sie ein Rechteck in einem Word‑Dokument mit Aspose.Words
  und sehen Sie dann, wie Sie eine Ellipse einfügen und Formen in Word für komplexe
  Layouts gruppieren.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Rechteckform erstellen und Formen in Word gruppieren – Aspose.Words‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man eine Rechteckform erstellt und Formen in Word mit Aspose.Words gruppiert
url: /de/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Rechteck erstellt und Formen in Word mit Aspose.Words gruppiert

Wenn Sie ein **Rechteck** in einem Word‑Dokument **erstellen** möchten, zeigt Ihnen diese Anleitung die genauen Schritte mit Aspose.Words für .NET. Sie sehen außerdem, wie Sie ein Ellipsen‑Word einfügen, Formen in Word gruppieren und das Ergebnis als DOCX‑Datei speichern. Die Lösung funktioniert in jedem .NET 6+‑Projekt und erfordert keine Installation von Microsoft Office auf dem Server.

Das Tutorial deckt alles von der Projekt‑Einrichtung bis zum Umgang mit gängigen Layout‑Fallstricken ab, sodass Sie den Code kopieren und sofort ausführen können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6 SDK oder später installiert  
* Eine NuGet‑kompatible IDE (Visual Studio, Rider oder VS Code)  
* Eine Aspose.Words für .NET‑Lizenz (oder einen temporären Evaluierungsschlüssel)  
* Grundkenntnisse in C# und der Word‑Dokumentstruktur  

Diese Voraussetzungen ermöglichen das Kompilieren des Codes und das korrekte Rendern der Formen.

## Schritt 1: Projekt einrichten und Aspose.Words hinzufügen

Erstellen Sie ein neues Konsolen‑Projekt und fügen Sie das Aspose.Words‑Paket hinzu:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Das Paket stellt die Klassen `Document`, `DocumentBuilder`, `Shape` und `GroupShape` bereit, die im gesamten Tutorial verwendet werden.

## Schritt 2: Leeres Dokument und Builder initialisieren

Das Objekt `Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` das programmgesteuerte Einfügen von Inhalten ermöglicht.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Durch das Erstellen des Dokuments zuerst wird sichergestellt, dass alle nachfolgenden Form‑Operationen einen gültigen Container haben.

## Schritt 3: **Rechteck erstellen** und Abmessungen festlegen

Ein Rechteck ist der häufigste Container für Text oder Bilder. Sie definieren seine Größe in Punkten (1 pt ≈ 1/72 Zoll).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Warum dieser Schritt wichtig ist: Die Klasse `Shape` kapselt Geometrie‑, Füll‑ und Linien‑Eigenschaften. Das Setzen von `Width` und `Height` vor dem Einfügen garantiert, dass die Form mit der erwarteten Größe erscheint.

## Schritt 4: **Wie man ein Ellipsen‑Word einfügt** – Ellipsen‑Form hinzufügen

Eine Ellipse kann für Icons, Marker oder dekorative Elemente verwendet werden. Der Code spiegelt die Rechteck‑Erstellung wider, nur der `ShapeType` ändert sich.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Die Eigenschaften `FillColor` und `Line.Color` zeigen, wie Sie das Aussehen ohne externe Bilder anpassen können.

## Schritt 5: **Formen in Word gruppieren** – Rechteck und Ellipse kombinieren

Durch Gruppieren können Sie mehrere Formen als eine Einheit verschieben, skalieren oder drehen. Das ist essenziell, wenn Sie eine zusammengesetzte Grafik benötigen (z. B. ein beschriftetes Icon).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Wenn Sie `AppendChild` aufrufen, werden die ursprünglichen Formen aus dem Haupt‑Dokumentfluss entfernt und zu Kindern des `GroupShape`. Die Gruppe verhält sich wie eine einzelne Form, was spätere Layout‑Anpassungen vereinfacht.

## Schritt 6: Dokument speichern

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Sie können jedes unterstützte Format wählen (`.docx`, `.pdf`, `.html` usw.). Für dieses Tutorial behalten wir das native Word‑Format bei.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Nach dem Ausführen des Programms öffnen Sie *GroupShape.docx* in Microsoft Word. Sie sehen ein Rechteck und eine Ellipse, die zusammen gruppiert und an den von Ihnen angegebenen Koordinaten positioniert sind.

## Häufige Varianten und Sonderfälle

| Situation | Was zu ändern ist | Grund |
|-----------|-------------------|-------|
| **Andere Größeneinheiten** | Verwenden Sie `ConvertUtil.InchToPoint(2.5)` für Zoll oder `ConvertUtil.MillimeterToPoint(30)` für Millimeter. | Macht den Code lesbarer, wenn Sie nicht‑Punkt‑Messungen nutzen. |
| **Text im Rechteck hinzufügen** | Erzeugen Sie einen `Paragraph`‑Knoten, setzen Sie dessen `Text`‑Eigenschaft und fügen Sie ihn via `AppendChild` zu `rectangleShape` hinzu. | Ermöglicht das Beschriften der Form ohne separate Textfelder. |
| **Gruppe rotieren** | Setzen Sie `groupShape.Rotation = 45;` (Grad). | Praktisch für diagonale Badges oder Wasserzeichen. |
| **Als PDF speichern** | Rufen Sie `doc.Save("GroupShape.pdf");` auf. | Aspose.Words rastert Vektorformen automatisch für die PDF‑Ausgabe. |
| **Mehrere Gruppen** | Erzeugen Sie weitere `GroupShape`‑Instanzen und wiederholen Sie die Append/Insert‑Schritte. | Ermöglicht komplexe Seitenlayouts mit mehreren unabhängigen Kompositen. |

### Profi‑Tipp

Fügen Sie Formen immer **vor** dem Gruppieren hinzu. Wenn Sie versuchen, eine Form zu gruppieren, die bereits Teil einer anderen Gruppe ist, wirft Aspose.Words eine `ArgumentException`. Das Erstellen der Gruppe in einer einzigen Methode verhindert diesen Laufzeitfehler.

### Achten Sie darauf

* **Koordinatensystem** – `Left` und `Top` werden vom linken bzw. oberen Rand der Seitenränder gemessen, nicht vom Dokumentrand. Ein Missverständnis kann dazu führen, dass Formen außerhalb der Seite platziert werden.
* **Lizenzierung** – Ohne gültige Lizenz enthält das gespeicherte Dokument ein Wasserzeichen mit dem Hinweis „Aspose.Words for .NET Evaluation“. Setzen Sie Ihre Lizenz früh im Code (`License license = new License(); license.SetLicense("Aspose.Words.lic");`), um das zu vermeiden.

## Vollständiger Quellcode (ausführbar)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Wenn Sie dieses Programm ausführen, entsteht *GroupShape.docx* mit den gruppierten Formen exakt wie beschrieben.

## Fazit

Sie wissen jetzt, wie man **ein Rechteck erstellt**, **ein Ellipsen‑Word einfügt** und **Formen in Word gruppiert** mit Aspose.Words. Das vollständige Beispiel demonstriert den gesamten Workflow – vom Initialisieren eines Dokuments bis zum Speichern der finalen Datei – sodass Sie die Form‑Verarbeitung in jede automatisierte Reporting‑ oder Dokument‑Generierungslösung integrieren können.

### Was kommt als Nächstes?

* Erkunden Sie **aspose.words create shapes** für komplexere Geometrien wie `Polygon` oder `Freeform`.  
* Kombinieren Sie gruppierte Formen mit **Content Controls**, um dynamische Vorlagen zu bauen.  
* Konvertieren Sie das DOCX zu PDF oder HTML, um zu sehen, wie Vektorformen in verschiedenen Formaten gerendert werden.  

Experimentieren Sie gern mit unterschiedlichen Größen, Farben und Rotationen. Sobald Sie das Gruppieren von Formen beherrschen, können Sie anspruchsvolle Diagramme, Badges und benutzerdefinierte UI‑Elemente direkt in Word‑Dokumenten erstellen.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}