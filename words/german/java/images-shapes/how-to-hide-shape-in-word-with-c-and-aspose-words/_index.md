---
category: general
date: 2026-09-11
description: Erfahren Sie, wie Sie Formen in Word mit C# ausblenden. Dieser Leitfaden
  zeigt außerdem, wie Sie ein Rechteck einfügen und Formen in ein Word‑Dokument mit
  Aspose.Words einfügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: de
lastmod: 2026-09-11
og_description: Wie man eine Form in Word mit C# und Aspose.Words ausblendet. Folgen
  Sie der Schritt‑für‑Schritt‑Anleitung, um ein Rechteck einzufügen und Formen in
  einem Word‑Dokument zu verwalten.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Wie man eine Form in Word ausblendet – vollständiger C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man eine Form in Word mit C# und Aspose.Words ausblendet
url: /de/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in Word mit C# und Aspose.Words ausblendet

Wenn Sie eine Form in Word ausblenden müssen, dabei aber die Form in der Dokumentstruktur erhalten wollen, zeigt Ihnen dieses Tutorial genau, wie das geht. Mit Aspose.Words für .NET können Sie eine Rechteck‑Form einfügen, ausblenden und dennoch ihre Position für die spätere Verarbeitung beibehalten.

Die Word‑Automatisierung erfordert häufig eine feinkörnige Kontrolle über Formen – egal, ob Sie Vorlagen generieren, Berichte erstellen oder einen Dokument‑Bearbeitungs‑Service aufbauen. Am Ende dieses Leitfadens können Sie:

* Ein Rechteck in ein Word‑Dokument einfügen (`insert rectangle shape`).
* Jede Form ausblenden, ohne sie zu löschen (`how to hide shape in word`).
* Das Ergebnis speichern und überprüfen, dass die ausgeblendete Form in der gerenderten Ansicht nicht erscheint (`insert shape into word document`).

Das Beispiel funktioniert mit Aspose.Words 24.10 oder neuer und zielt auf .NET 6.0+ ab, die Konzepte gelten jedoch auch für frühere Versionen.

## Voraussetzungen

* **Aspose.Words für .NET** ≥ 24.10. Sie können eine kostenlose temporäre Lizenz von der Aspose‑Website erhalten.
* **.NET SDK** 6.0 oder neuer, installiert auf Ihrem Rechner.
* Eine Entwicklungsumgebung wie Visual Studio 2022, VS Code oder Rider.
* Grundlegende Kenntnisse in C# und dem Word‑Open‑XML‑Konzept (optional, aber hilfreich).

## Wie man Formen in Word mit Aspose.Words ausblendet

Unten finden Sie ein vollständiges, ausführbares Programm, das den gesamten Workflow demonstriert – vom Erstellen eines Dokuments über das Einfügen einer Rechteck‑Form bis hin zum Ausblenden derselben.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Erklärung der einzelnen Schritte

1. **Ein neues Dokument erstellen** – `Document` repräsentiert die Word‑Datei im Speicher. `DocumentBuilder` bietet eine fluente API zum Einfügen von Inhalten.
2. **Rechteck‑Form einfügen** – `InsertShape` erzeugt ein Zeichenobjekt vom Typ `Rectangle`. Die Abmessungen werden in Punkten angegeben (1 pt ≈ 1/72 in). Damit wird die Anforderung `insert rectangle shape` erfüllt.
3. **Form ausblenden** – Durch Setzen von `Shape.Hidden = true` wird die Form im Word‑Markup als ausgeblendet markiert (`<w:hidden/>`). Die Form bleibt Teil des Dokumentbaums, sodass Sie sie später wieder einblenden oder programmgesteuert referenzieren können. Das ist der Kern von `how to hide shape in word`.
4. **Datei speichern** – Das Dokument wird nach `output.docx` geschrieben. Beim Öffnen in Microsoft Word ist das Rechteck nicht sichtbar, existiert aber weiterhin im XML und kann mit einem ZIP‑Viewer oder dem Open‑XML‑SDK inspiziert werden.

### Erwartetes Ergebnis

Öffnen Sie `output.docx` in Microsoft Word:

* Das Dokument erscheint leer – keine sichtbare Form.
* Wenn Sie das zugrunde liegende XML (`word/document.xml`) untersuchen, finden Sie ein `<w:pict>`‑Element mit einem `<w:hidden/>`‑Attribut, das bestätigt, dass die Form vorhanden, aber ausgeblendet ist.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

Die ausgeblendete Form kann wieder sichtbar gemacht werden, indem Sie `Hidden = false` setzen und das Dokument erneut speichern.

## Rechteck‑Form in ein Word‑Dokument einfügen

Obwohl das Hauptziel das Ausblenden einer Form ist, beginnen viele Szenarien zunächst mit dem Einfügen einer Form. Die Methode `InsertShape` unterstützt zahlreiche `ShapeType`‑Werte, darunter `Rectangle`, `Ellipse`, `Line` und benutzerdefinierte Bilder.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Warum ein Rechteck verwenden?**  
Ein Rechteck bietet einen sauberen, achsen‑ausgerichteten Container, der Text, Bilder oder andere verschachtelte Formen aufnehmen kann. Es wird häufig als Platzhalter für dynamische Inhalte wie Tabellen oder Diagramme verwendet. Durch das vorherige Einfügen des Rechtecks erhalten Sie Layout‑Konsistenz, selbst wenn Sie es später ausblenden.

## Form in Word‑Dokument einfügen – bewährte Vorgehensweisen

Wenn Sie `insert shape into word document` ausführen, beachten Sie Folgendes:

* **Explizite Abmessungen festlegen** – Vermeiden Sie die automatische Größenbestimmung; geben Sie Breite und Höhe in Punkten an, um ein konsistentes Layout über alle Plattformen hinweg zu gewährleisten.
* **Positionierung definieren** – Standardmäßig ist die Form an den aktuellen Absatz angeheftet. Verwenden Sie `builder.MoveTo` oder `builder.StartBookmark`, um sie exakt zu platzieren.
* **Styling frühzeitig anwenden** – Füllfarbe, Linienstil und Textumbruch beeinflussen das Endergebnis. Auch ausgeblendete Formen profitieren von korrektem Styling, da das Markup unverändert bleibt.
* **Versionskompatibilität** – Die Eigenschaft `Hidden` ist erst ab Aspose.Words 24.10 verfügbar. Zielten Sie auf eine ältere Version, können Sie das `<w:hidden/>`‑Attribut manuell über die `Node`‑API hinzufügen.

### Manuelles Hinzufügen des hidden‑Attributs (Fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Komplettes End‑to‑End‑Beispiel

Alles zusammengeführt, hier ein einzelnes Programm, das:

1. Ein Rechteck einfügt.
2. Die Form ausblendet.
3. Eine sichtbare Ellipse zum Kontrast hinzufügt.
4. Das Dokument speichert.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

Beim Ausführen des Programms entsteht `demo_output.docx`. Beim Öffnen sehen Sie nur die Korallen‑Ellipse; das grüne Rechteck ist im XML vorhanden, aber im Ansichtsmodus ausgeblendet.

## Häufige Fragen und Sonderfälle

**F: Beeinflusst das Ausblenden einer Form die Seitennummerierung?**  
A: Nein. Ausgeblendete Formen werden vom Layout‑Engine ignoriert und beanspruchen keinen Platz. Das ist nützlich für Platzhalter‑Inhalte, die keine Seitenumbrüche verursachen sollen.

**F: Kann ich eine Form ausblenden, die Teil einer Kopf‑ oder Fußzeile ist?**  
A: Ja. Die `Hidden`‑Eigenschaft funktioniert bei Formen, die überall im Dokumentbaum liegen, einschließlich Kopf‑ und Fußzeilen sowie innerhalb von Tabellen.

**F: Was, wenn ich mehrere Formen gleichzeitig ausblenden muss?**  
A: Durchlaufen Sie die Sammlung `Document.GetChildNodes(NodeType.Shape, true)` und setzen Sie für jede Ziel‑Form `Hidden = true`.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**F: Wird das hidden‑Attribut beim Konvertieren in PDF beibehalten?**  
A: Beim Konvertieren nach PDF werden ausgeblendete Formen standardmäßig weggelassen, was dem Rendering‑Verhalten von Word entspricht. Wenn Sie sie im PDF benötigen, müssen Sie sie vor der Konvertierung wieder einblenden.

## Tipps und Fallstricke

* **Pro‑Tipp:** Setzen Sie `shape.WrapType = WrapType.None`, bevor Sie die Form ausblenden, falls Sie sie später wieder einblenden möchten, ohne den umgebenden Text zu stören.
* **Achten Sie auf ältere Aspose.Words‑Versionen:** Die `Hidden`‑Eigenschaft wirft vor Version 24.10 eine `NotSupportedException`. Verwenden Sie in diesem Fall den manuellen XML‑Ansatz.
* **Testing:** Öffnen Sie die erzeugte `.docx` stets in Word und nutzen Sie „XML‑Markup anzeigen“ (Entwicklertools‑Registerkarte), um zu prüfen, dass das `<w:hidden/>`‑Attribut vorhanden ist.

## Fazit

Sie wissen jetzt, wie Sie Formen in Word mit C# und Aspose.Words ausblenden, sowie wie Sie Rechteck‑Formen einfügen und Formen in ein Word‑Dokument einfügen, wobei Sie die Sichtbarkeit vollständig steuern können. Durch die Nutzung der `Hidden`‑Eigenschaft können Sie Formen im Dokumentmodell für die spätere Verarbeitung behalten und gleichzeitig den Endbenutzern eine saubere Ansicht präsentieren.

Als Nächstes können Sie verwandte Themen erkunden, etwa **Aktualisieren von Form‑Eigenschaften zur Laufzeit**, **Konvertieren ausgeblendeter Formen in Bilder** oder **Verwendung des Open‑XML‑SDK zum direkten Manipulieren versteckter Elemente**. Diese Erweiterungen vertiefen Ihr Wissen.

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Formen in Word‑Dokumenten mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Rechteck‑Form in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}