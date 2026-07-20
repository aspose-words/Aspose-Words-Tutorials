---
category: general
date: 2026-07-19
description: Gruppieren Sie Formen in Word mit Aspose.Words. Erfahren Sie, wie Sie
  ein Rechteck hinzufügen, eine Ellipse definieren und Formen in Word‑Dokumente einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: de
lastmod: 2026-07-19
og_description: Formen in Word mit Aspose.Words gruppieren. Master fügt Rechteckform
  hinzu, definiert Ellipsenform und fügt die Form in Word‑Dokumente ein.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Formen gruppieren in Word – Schritt‑für‑Schritt C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Formen in Word mit Aspose.Words gruppieren – Vollständiger C#‑Leitfaden
url: /de/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formen in Word gruppieren – Vollständige C#‑Anleitung

Haben Sie sich jemals gefragt, wie man **group shapes in Word** ohne Herumfummeln an der UI? Sie sind nicht allein. Egal, ob Sie Verträge, Flyer oder Diagramme programmgesteuert erzeugen, die Möglichkeit, **add rectangle shape**, **define ellipse shape** und dann **group shapes in Word** zu verwenden, kann Ihnen Stunden manueller Arbeit ersparen.

In diesem Tutorial führen wir Sie durch ein praxisnahes Beispiel mit **Aspose.Words for .NET**. Am Ende wissen Sie genau, wie man **insert shape into Word** einfügt, sie kombiniert und ein professionelles Dokument erstellt, das Sie an Kunden oder Teammitglieder senden können.

---

## Was Sie benötigen

- **Aspose.Words for .NET** (neueste Version, z. B. 24.9). Sie können es über NuGet mit `Install-Package Aspose.Words` beziehen.
- Eine .NET‑Entwicklungsumgebung (Visual Studio 2022 oder VS Code mit der C#‑Erweiterung funktioniert einwandfrei).
- Grundlegende Kenntnisse der C#‑Syntax – nichts Besonderes, nur die üblichen `using`‑Anweisungen und Objektinstanziierungen.

Das war’s. Keine zusätzlichen Bibliotheken, kein COM‑Interop, nur reiner Managed‑Code.

## Formen in Word gruppieren mit Aspose.Words

Im Folgenden finden Sie eine Schritt‑für‑Schritt‑Aufschlüsselung, die den bereits vorhandenen Code widerspiegelt. Jeder Schritt erklärt **why** wir es tun, nicht nur **what** die Zeile bewirkt, sodass Sie das Muster an jede gewünschte Form anpassen können.

### Schritt 1: Dokument und Builder einrichten

Wir beginnen mit der Erstellung eines leeren `Document` und eines `DocumentBuilder`. Der Builder ist unser „Stift“, mit dem wir Inhalte dort einfügen können, wo wir sie benötigen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Why?** Das `Document`‑Objekt repräsentiert die gesamte .docx‑Datei, während `DocumentBuilder` eine bequeme API zum Einfügen von Knoten (wie Formen) bietet, ohne sich mit dem zugrunde liegenden Knotbaum auseinandersetzen zu müssen.

### Schritt 2: Rechteckform hinzufügen (add rectangle shape)

Jetzt **add rectangle shape** wir dem Dokument. Wir setzen Größe, Position und Füllfarbe, damit es hervorsticht.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Tip:** Sie können `FillColor` zu jeder gewünschten `System.Drawing.Color` ändern. Das ist nützlich, wenn Sie farbcodierte Abschnitte in einem Bericht benötigen.

### Schritt 3: Ellipsenform definieren (define ellipse shape)

Als Nächstes **define ellipse shape** wir. Beachten Sie den anderen `ShapeType` und den Versatz (`Left = 120`), sodass die Ellipse neben dem Rechteck liegt.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Why this matters:** Durch die explizite Positionierung der Formen steuern Sie, wie sie vor dem Gruppieren erscheinen. Wenn Sie sich auf das automatische Layout verlassen, könnte die Gruppierung nicht zentriert aussehen.

### Schritt 4: (Optional) Einzelne Formen zur Vorschau einfügen

Wenn Sie jede Form vor dem Gruppieren sehen möchten, können Sie **insert shape into Word** einzeln einfügen. Dieser Schritt ist optional, aber praktisch zum Debuggen.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Pro tip:** Kommentieren Sie diese beiden Zeilen aus, sobald Sie sicher sind, dass die Formen korrekt aussehen; andernfalls erhalten Sie nach dem Gruppieren doppelte Darstellungen.

### Schritt 5: Formen gruppieren – GroupShape erstellen

Hier ist der Kern des Tutorials: **how to group shapes**. Wir erstellen ein `GroupShape`, fügen unser Rechteck und die Ellipse hinzu und bestimmen, wie sich die Gruppe im Zusammenhang mit umgebendem Text verhält.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Explanation:** `GroupShape` ist im Wesentlichen eine Mini‑Canvas, die andere Formen enthält. Durch das Setzen von `WrapType` auf `Inline` bewegt sich die gesamte Gruppe als Einheit, wenn Sie Text hinzufügen oder löschen.

### Schritt 6: Gruppierte Form in das Dokument einfügen (insert shape into word)

Jetzt **insert shape into Word** wir – diesmal ist es der gruppierte Container, nicht die einzelnen Teile.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **What happens under the hood?** Der Aufruf `InsertNode` fügt das `GroupShape` zur Knotensammlung des Dokuments hinzu. Da die Gruppe bereits das Rechteck und die Ellipse enthält, erscheinen sie zusammen als ein Objekt.

### Schritt 7: Dokument speichern

Abschließend schreiben Sie die Datei auf die Festplatte. Sie können den Pfad an das Layout Ihres Projekts anpassen.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Result:** Öffnen Sie `GroupShape.docx` in Microsoft Word und Sie sehen ein hellblaues Rechteck und eine korallenfarbene Ellipse, die zusammengefasst sind. Wenn Sie eines ziehen, bewegt sich das andere – genau das, was „group shapes in word“ verspricht.

## Visuelle Bestätigung

Unten sehen Sie ein Mock‑up, wie die gruppierten Formen im Word‑Dokument aussehen.  

![Screenshot of grouped shapes in a Word document created with Aspose.Words](grouped_shapes_placeholder.png "group shapes in word")

*Der Alt‑Text des Bildes enthält das Hauptkeyword für Barrierefreiheit und SEO.*

## Häufige Fragen & Sonderfälle

### Was, wenn ich mehr als zwei Formen benötige?

Rufen Sie einfach weiter `groupShape.AppendChild(yourNewShape);` auf, bevor Sie die Gruppe einfügen. Die API setzt keine Grenze für die Anzahl der Kindformen.

### Kann ich die gesamte Gruppe drehen oder skalieren?

Absolut. `GroupShape` erbt von `Shape`, sodass Sie Eigenschaften wie `RotationAngle`, `Width` oder `Height` an der Gruppe selbst setzen können und alle Kindformen folgen.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Wie ändere ich die Hintergrundfarbe der Gruppe?

Verwenden Sie `groupShape.FillColor`. Damit füllen Sie das unsichtbare Begrenzungsfeld; das kann zum Hervorheben nützlich sein.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Funktioniert das mit älteren Word‑Formaten (.doc)?

`Aspose.Words` kann auch im `.doc`‑Format speichern – ersetzen Sie einfach die Dateierweiterung in `Save`. Allerdings werden einige erweiterte Form‑Funktionen (wie Gruppierung) nur im OOXML‑`.docx`‑Format vollständig unterstützt.

## Vollständiges funktionierendes Beispiel

Kopieren Sie den folgenden Block in eine neue Konsolen‑App, um den gesamten Prozess in Aktion zu sehen. Es fehlen keine Teile; dies ist ein **komplettes, ausführbares Beispiel**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Erwartete Ausgabe:** Wenn Sie `GroupShape.docx` öffnen, sehen Sie ein einzelnes gruppiertes Objekt, das aus einem hellblauen Rechteck und einer hellkorallenfarbenen Ellipse besteht, perfekt nebeneinander ausgerichtet.

## Zusammenfassung

Wir haben gerade alles behandelt, was Sie benötigen, um **group shapes in Word** mit Aspose.Words zu **gruppen**:

1. Erstellen Sie ein Dokument und einen Builder.  
2. **Add rectangle shape** und **define ellipse shape** mit expliziten Abmessungen.  
3. (Optional) **insert shape into Word** für eine schnelle Vorschau.  
4. Verwenden Sie `GroupShape`, um **how to group shapes** – fügen Sie jedes Kind hinzu, setzen Sie das Wrapping und fügen Sie es ein.  
5. Speichern Sie die Datei und überprüfen Sie das

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}