---
category: general
date: 2026-10-07
description: Erstelle ein leeres Word‑Dokument in C# und lerne, ein Rechteck‑Shape
  hinzuzufügen, ein Bild‑Shape einzufügen und mehrere Shapes für dynamische Berichte
  zu gruppieren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- insert image shape
- group multiple shapes
- add image to word
language: de
lastmod: 2026-10-07
og_description: Erstellen Sie ein leeres Word‑Dokument in C# mit Aspose.Words. Erfahren
  Sie, wie Sie ein Rechteck hinzufügen, ein Bild einfügen und mehrere Formen gruppieren,
  um professionelle Dokumente zu erstellen.
og_image_alt: Screenshot of a Word file showing a grouped rectangle and logo created
  with C#
og_title: Leeres Word‑Dokument erstellen und Formen in C# gruppieren – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Create blank Word document in C# and learn to add rectangle shape,
    insert image shape, and group multiple shapes for dynamic reports.
  headline: How to create blank Word document and group shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man ein leeres Word‑Dokument erstellt und Formen in C# gruppiert
url: /de/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word-Dokument erstellt und Formen in C# gruppiert

Wenn Sie programmgesteuert ein **create blank Word document** erstellen müssen, zeigt Ihnen diese Anleitung genau, wie es geht. Sie sehen, wie Sie **add rectangle shape**, **insert image shape** und **group multiple shapes** hinzufügen, sodass sie sich wie ein einzelnes Objekt verhalten, wenn Sie später **add image to Word**.

Die Arbeit mit Word-Dateien aus dem Code kann einschüchternd wirken, aber Aspose.Words macht den Prozess unkompliziert. Am Ende dieses Tutorials verfügen Sie über ein wiederverwendbares C#‑Snippet, das eine saubere, leere Word‑Datei erzeugt, die ein gruppiertes Rechteck und ein Logo enthält. Sie können das Ergebnis in Rechnungen, Berichten oder jedem automatisierten Dokumenten‑Workflow einbetten.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+).  
* Eine gültige Aspose.Words for .NET Lizenz oder ein kostenloser Evaluierungsschlüssel.  
* Eine Bilddatei (z. B. `logo.png`), die in einem Ordner liegt, den Sie aus dem Code referenzieren können.  
* Visual Studio 2022 oder eine beliebige C#‑kompatible IDE.

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Wie man ein leeres Word-Dokument mit Aspose.Words erstellt

Der erste Schritt besteht immer darin, ein **create blank Word document** zu erstellen. Dieses Objekt wird alle nachfolgenden Formen beherbergen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// 1️⃣ Initialize a new empty document.
Document doc = new Document();

// 2️⃣ Prepare a DocumentBuilder – it simplifies adding content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` repräsentiert die gesamte `.docx`‑Datei. Zu diesem Zeitpunkt ist die Datei leer, was die Anforderung *create blank Word document* erfüllt.

## Erstellen eines Containers zum Gruppieren mehrerer Formen

Das Gruppieren von Formen ermöglicht es, sie gemeinsam zu verschieben, zu drehen oder zu skalieren. Aspose.Words stellt dafür die Klasse `GroupShape` bereit.

```csharp
// 3️⃣ Create a GroupShape that will hold our drawing objects.
GroupShape group = new GroupShape(doc)
{
    // Define the container’s position and size on the page.
    Bounds = new Rectangle(50, 50, 300, 200)
};

// Append the group to the first paragraph of the first section.
doc.FirstSection.Body.FirstParagraph.AppendChild(group);
```

Das Rechteck `Bounds` bestimmt, wo die Gruppe auf der Seite erscheint. Indem Sie die Gruppe im ersten Absatz platzieren, stellen Sie sicher, dass das **create blank Word document** sofort einen visuellen Container enthält.

## Wie man ein Rechteck innerhalb der Gruppe hinzufügt

Eine häufige Anforderung ist das **add rectangle shape** als Hintergrund oder Rahmen. Der folgende Code erstellt ein Rechteck und fügt es der zuvor definierten Gruppe hinzu.

```csharp
// 4️⃣ Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 100,
    Height = 80,
    Left = 20,
    Top = 20,
    // Optional: give the rectangle a light gray fill.
    FillColor = Color.LightGray
};

// Add the rectangle to the group.
group.AppendChild(rectangle);
```

Da das Rechteck innerhalb des `GroupShape` liegt, wird es zusammen mit allen anderen Formen, die Sie später hinzufügen, bewegt. Dies ist das Kernstück der **group multiple shapes**‑Funktionalität.

## Wie man ein Bild innerhalb der Gruppe einfügt

Als Nächstes **insert image shape** (das Logo) und platzieren es neben dem Rechteck. Dies demonstriert den **add image to Word**‑Workflow.

```csharp
// 5️⃣ Create an image shape.
Shape picture = new Shape(doc, ShapeType.Image)
{
    Width = 80,
    Height = 80,
    Left = 150,
    Top = 30
};

// Load the image from disk. Replace the path with your actual image location.
picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));

// Add the image shape to the same group.
group.AppendChild(picture);
```

Die Methode `SetImage` liest die Datei und bettet sie direkt in das Word‑Dokument ein, sodass das Bild erhalten bleibt, selbst wenn die Quelldatei verschoben wird. Damit ist der Schritt **insert image shape** abgeschlossen und die Anforderung **add image to Word** finalisiert.

## Dokument speichern

Zum Schluss speichern Sie die Datei auf dem Datenträger. Die gespeicherte Datei enthält das leere Dokument, das gruppierte Rechteck und das eingebettete Logo.

```csharp
// 6️⃣ Save the document with the grouped shapes.
doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
```

Wenn Sie `GroupShape.docx` in Microsoft Word öffnen, sehen Sie eine einzelne Gruppe, die ein hellgraues Rechteck und das nebeneinander positionierte Logo enthält. Das Auswählen eines beliebigen Teils der Gruppe ermöglicht das Verschieben oder Skalieren der gesamten Sammlung und beweist, dass die Formen tatsächlich **group multiple shapes** sind.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie kopieren, einfügen und ausführen können. Ersetzen Sie `YOUR_DIRECTORY` durch einen absoluten oder relativen Pfad, der auf Ihrem Rechner existiert.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a blank Word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Create a GroupShape to hold the rectangle and image.
        GroupShape group = new GroupShape(doc)
        {
            Bounds = new Rectangle(50, 50, 300, 200)
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(group);

        // Step 3: Add a rectangle shape inside the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 100,
            Height = 80,
            Left = 20,
            Top = 20,
            FillColor = Color.LightGray
        };
        group.AppendChild(rectangle);

        // Step 4: Insert an image shape inside the group.
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            Width = 80,
            Height = 80,
            Left = 150,
            Top = 30
        };
        picture.ImageData.SetImage(Image.FromFile(@"YOUR_DIRECTORY/logo.png"));
        group.AppendChild(picture);

        // Step 5: Save the document.
        doc.Save(@"YOUR_DIRECTORY/GroupShape.docx");
    }
}
```

### Erwartete Ausgabe

* Eine Datei namens `GroupShape.docx` im Verzeichnis `YOUR_DIRECTORY`.  
* Beim Öffnen der Datei in Word wird eine einzelne visuelle Gruppe angezeigt, die ein graues Rechteck links und das `logo.png` rechts enthält.  
* Das Auswählen eines beliebigen Teils der visuellen Gruppe ermöglicht das Verschieben oder Skalieren der gesamten Sammlung und bestätigt, dass die Formen korrekt **group multiple shapes** sind.

## Häufige Fragen und Sonderfall‑Behandlung

| Frage | Antwort |
|---|---|
| **Kann ich mehr als zwei Formen zur selben Gruppe hinzufügen?** | Ja. Rufen Sie `group.AppendChild(yourShape)` für jede zusätzliche `Shape` auf. Die Gruppe kann beliebig viele Zeichenobjekte enthalten. |
| **Was passiert, wenn die Bilddatei fehlt?** | `SetImage` wirft eine `FileNotFoundException`. Wickeln Sie den Aufruf in einen try‑catch‑Block und stellen Sie eine Alternative bereit (z. B. eine Platzhalterform). |
| **Muss ich `WrapType` für die Formen setzen?** | Standardmäßig sind Formen inline. Wenn Sie ein schwebendes Verhalten benötigen, setzen Sie `picture.WrapType = WrapType.Inline;` oder einen anderen Wrap‑Modus, bevor Sie sie zur Gruppe hinzufügen. |
| **Wie beeinflusst die Dokumentgröße die Grenzen der Gruppe?** | Das Rechteck `Bounds` ist in Punkten definiert (1 pt ≈ 1/72 in). Passen Sie die Größe an, wenn Sie die Gruppe in einem anderen Seitenlayout platzieren (z. B. A4 vs. Letter). |
| **Kann ich dieselbe Gruppe in einem anderen Dokument wiederverwenden?** | Ja. Klonen Sie die Gruppe mit `GroupShape cloned = (GroupShape)group.Clone(true);` und fügen Sie sie in ein anderes `Document` ein. |

## Pro‑Tipps

* **Wiederverwenden des `DocumentBuilder`** zum Hinzufügen von Text vor oder nach der Gruppe. Er berücksichtigt automatisch die aktuelle Cursorposition.  
* **Setzen Sie `Shape.StrokeColor`**, wenn Sie einen sichtbaren Rand um das Rechteck benötigen.  
* **Verwenden Sie hochauflösende PNGs** für das Logo, um Pixelbildung zu vermeiden, wenn

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Inline‑Bild in Word-Dokument mit Aspose.Words einfügen](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}