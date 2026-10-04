---
category: general
date: 2026-10-04
description: Erfahren Sie, wie Sie Formen in Word mit C# gruppieren. Dieser Leitfaden
  zeigt, wie man ein Rechteck einfügt, mehrere Formen gruppiert und programmgesteuert
  eine leere Word‑Datei erstellt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: de
lastmod: 2026-10-04
og_description: Formen in Word mit C# gruppieren. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung,
  um ein Rechteck einzufügen, mehrere Formen zu gruppieren und eine leere Word‑Datei
  mit DocumentBuilder zu erstellen.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Formen in Word mit C# gruppieren – vollständiges DocumentBuilder‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Wie man Formen in Word mit C# und DocumentBuilder gruppiert
url: /de/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in Word mit C# und DocumentBuilder gruppiert

Wenn Sie **Formen in Word** aus einer C#‑Anwendung gruppieren müssen, zeigt Ihnen dieses Tutorial genau, wie das geht. Sie sehen, wie man *ein Rechteck einfügt*, mehrere Zeichnungen zu einer einzigen Gruppe kombiniert und schließlich **eine leere Word‑Datei erstellt**, die die gruppierten Objekte enthält.

Die Arbeit mit Formen ist ein häufiges Erfordernis beim programmgesteuerten Erstellen von Berichten, Rechnungen oder benutzerdefinierten Vorlagen. Am Ende dieses Leitfadens haben Sie ein wiederverwendbares Code‑Snippet, das Sie in jedes .NET‑Projekt einbinden können, das Aspose.Words referenziert.

## Was Sie lernen werden

- Erstellen Sie ein leeres Word‑Dokument von Grund auf.  
- Fügen Sie ein Rechteck und eine Ellipse mit `DocumentBuilder` ein.  
- **Gruppieren Sie mehrere Formen** in ein `GroupShape`.  
- Verwenden Sie **append child to group**, um die Hierarchie aufzubauen.  
- Speichern Sie die Datei auf dem Datenträger und überprüfen Sie das Ergebnis.

Vorkenntnisse mit Aspose.Words sind nicht erforderlich, aber Sie sollten ein grundlegendes Verständnis von C#‑ und .NET‑Entwicklung besitzen.

## Voraussetzungen

| Anforderung | Grund |
|-------------|-------|
| .NET 6.0 or later | Stellt die Laufzeit für den C#‑Code bereit. |
| Aspose.Words for .NET (latest version) | Stellt `Document`, `DocumentBuilder` und Shape‑Klassen bereit. |
| An IDE such as Visual Studio 2022 (or VS Code) | Ermöglicht das einfache Kompilieren und Ausführen des Beispiels. |
| Write permission to a folder on your machine | Wird für den Aufruf `doc.save` benötigt. |

Install Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Formen in Word gruppieren – Schritt‑für‑Schritt‑Anleitung

Unten finden Sie das vollständige, ausführbare Programm. Jeder Abschnitt wird im Detail erklärt, damit Sie verstehen, **warum** der Code auf diese Weise geschrieben ist, und nicht nur, **was** er tut.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Warum jeder Schritt wichtig ist

1. **Erstellen Sie eine leere Word‑Datei** – Der Start mit einem leeren Dokument stellt sicher, dass keine versteckte Formatierung die Positionierung der Formen beeinträchtigt.  
2. **Initialisieren Sie DocumentBuilder** – `DocumentBuilder` abstrahiert die Low‑Level‑Knotenmanipulation, sodass Sie sich auf das Layout konzentrieren können.  
3. **Einzelne Formen einfügen** – Sie benötigen zunächst separate Objekte (`insert rectangle shape` und eine Ellipse), bevor Sie sie gruppieren können. Das Anpassen von `Left` und `Top` sorgt dafür, dass sie nebeneinander erscheinen.  
4. **Mehrere Formen gruppieren** – Durch das Erstellen eines `GroupShape` und die Verwendung von **append child to group** verwandeln Sie zwei unabhängige Zeichnungen in eine logische Einheit. Das Verschieben oder Ändern der Größe der Gruppe wirkt sich gleichzeitig auf beide Kinder aus.  
5. **Speichern Sie das Dokument** – Die endgültige Datei `GroupedShapes.docx` kann in Microsoft Word geöffnet werden, um zu überprüfen, dass das Rechteck und die Ellipse tatsächlich gruppiert sind (ein Objekt auswählen, und beide bewegen sich zusammen).

### Erwartete Ausgabe

Open `GroupedShapes.docx` in Microsoft Word:

- Sie sehen ein Rechteck und eine Ellipse nebeneinander.  
- Wenn Sie eine der Formen auswählen, werden beide hervorgehoben, was bestätigt, dass sie zur selben Gruppe gehören.  
- Die Gruppe kann gezogen, in der Größe geändert oder als ein einzelnes Objekt formatiert werden.

![Diagram of grouped rectangle and ellipse inside a Word document](https://example.com/grouped-shapes.png){: .center-image alt="Diagramm einer gruppierten Rechtecks- und Ellipsenform in einem Word‑Dokument"}

*Der Screenshot veranschaulicht die endgültig gruppierten Formen.*

---

## Rechteckform einfügen – Größe und Stil anpassen

Wenn Sie ein Rechteck mit einer bestimmten Füllfarbe oder einem Rand benötigen, ändern Sie das `Shape`‑Objekt nach dem Einfügen:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Diese Eigenschaften gehören zur `Shape`‑Klasse und funktionieren für jeden Formtyp, nicht nur für Rechtecke. Das Anpassen des Stils, bevor Sie **append child to group** ausführen, stellt sicher, dass die Gruppe die von Ihnen festgelegten visuellen Eigenschaften erbt.

---

## Mehrere Formen gruppieren – mehr als zwei Objekte handhaben

Das Beispiel gruppiert ein Rechteck und eine Ellipse, aber Sie können beliebig viele Formen hinzufügen:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Profi‑Tipp:** Nachdem Sie eine komplexe Gruppe erstellt haben, können Sie ihr Layout sperren, um versehentliche Änderungen zu verhindern:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – Reihenfolge ist wichtig

Die Reihenfolge, in der Sie `AppendChild` aufrufen, definiert die Z‑Reihenfolge (welche Form oben liegt). Im Beispiel wird das Rechteck zuerst hinzugefügt, dann die Ellipse, sodass die Ellipse das Rechteck überlagert, falls sie sich überschneiden. Das Neuordnen ist so einfach wie das Aufrufen von `RemoveChild` und erneutes Hinzufügen:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Leere Word‑Datei erstellen – wiederverwendbare Hilfsmethode

Wenn Ihre Anwendung häufig ein neues Dokument benötigt, kapseln Sie die Erstellungslogik ein:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Sie können dann die Zeile `new Document()` im Hauptprogramm durch `CreateBlankWordFile()` ersetzen. Dies demonstriert das Konzept **create blank word file** auf wiederverwendbare Weise.

---

## Häufige Stolperfallen und wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| Formen erscheinen außerhalb der Seite | Standardwerte für `Left`/`Top` sind 0, wodurch die Form am Rand platziert wird. | Setzen Sie `Left` und `Top` nach dem Einfügen explizit. |
| Gruppe verliert Formatierung | Das Ändern einer Kindform, nachdem sie zu einer Gruppe hinzugefügt wurde, kann das Layout der Gruppe zerstören. | Wenden Sie alle visuellen Eigenschaften **vor** dem Aufruf von `AppendChild` an. |
| Gespeicherte Datei ist leer | `DocumentBuilder` wurde nie verwendet, um einen Knoten hinzuzufügen, oder `doc.Save` wurde auf einer anderen `Document`‑Instanz aufgerufen. | Stellen Sie sicher, dass Sie dasselbe `Document` speichern, das Sie erstellt haben. |
| Kompatibilitätswarnungen in Word | Verwendung neuerer Form‑Funktionen, die nicht unterstützt werden |  |

## Was Sie als Nächstes lernen sollten?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Formen in Word‑Dokumenten mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}