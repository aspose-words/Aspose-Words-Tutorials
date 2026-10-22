---
category: general
date: 2026-09-08
description: Erfahren Sie, wie Sie ein leeres Word‑Dokument erstellen, ein Rechteck
  einfügen und mehrere Formen mit C# gruppieren. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: de
lastmod: 2026-09-08
og_description: Erstelle ein leeres Word-Dokument, füge eine Rechteckform ein und
  gruppiere mehrere Formen in C#. Dieses Tutorial führt dich durch den gesamten Prozess.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Leeres Word‑Dokument mit gruppierten Formen in C# erstellen
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Wie man ein leeres Word‑Dokument mit gruppierten Formen erstellt
url: /de/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word-Dokument mit gruppierten Formen erstellt

Wenn Sie ein **leeres Word-Dokument** erstellen müssen, das benutzerdefinierte Grafiken enthält, zeigt Ihnen diese Anleitung genau, wie das geht. Sie lernen, **ein Rechteck einfügen**, **mehrere Formen gruppieren** und **Formen zur Gruppe hinzufügen** mit Aspose.Words für .NET.

Ein leeres Dokument bietet Ihnen eine saubere Leinwand, und das Gruppieren von Formen ermöglicht es Ihnen, sie als Einheit zu verschieben, zu skalieren oder zu drehen. Dieses Tutorial deckt jeden Schritt ab – von der Initialisierung des Dokuments bis zum Speichern der finalen Datei – sodass Sie den Code in Ihr eigenes Projekt kopieren und sofortige Ergebnisse sehen können.

## Was Sie benötigen

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
* Eine gültige Aspose.Words für .NET Lizenz (die kostenlose Evaluierung funktioniert für Tests)
* Eine IDE wie Visual Studio 2022 oder Visual Studio Code
* Grundlegende Kenntnisse der C#‑Syntax

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Wie man ein leeres Word-Dokument erstellt

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt stellt eine leere `.docx`‑Datei dar, die Sie mit einem `DocumentBuilder` bearbeiten können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Der `Document`‑Konstruktor erstellt ein **leeres Word-Dokument** im Speicher. Der `DocumentBuilder` bietet eine fluente API zum Einfügen von Text, Bildern und Zeichenobjekten.

## Rechteckform in das Dokument einfügen

Als Nächstes fügen Sie eine Rechteckform hinzu. Das Rechteck wird das erste Kind der Gruppe sein, die wir später erstellen.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Der Aufruf von `InsertShape` mit `ShapeType.Rectangle` **fügt eine Rechteckform** an der aktuellen Cursorposition ein. Breite und Höhe werden in Punkten angegeben (1 pt ≈ 1/72 in).

## Mehrere Formen zusammen gruppieren

Ein `GroupShape` fungiert als Container. Alle Kindformen innerhalb der Gruppe bewegen und transformieren sich gemeinsam. Zuerst erstellen Sie die Gruppe, dann fügen Sie das gerade erstellte Rechteck hinzu.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Die Methode `InsertGroupShape` platziert eine leere Gruppe am Cursor des Builders. Durch das Anhängen des Rechtecks **gruppieren wir mehrere Formen** – das Rechteck wird Teil der internen Knotensammlung der Gruppe.

## Formen zur Gruppe hinzufügen und die Datei speichern

Fügen Sie nun eine zweite Form – eine Ellipse – hinzu, um zu demonstrieren, wie mehrere Objekte denselben Container teilen. Anschließend speichern Sie das Dokument.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Der Aufruf von `InsertShape` **fügt Formen zur Gruppe hinzu**, wenn Sie das zurückgegebene `Shape` an das `GroupShape` anhängen. Das Speichern des `Document` schreibt eine `.docx`‑Datei, die Sie in Microsoft Word, LibreOffice oder einem anderen kompatiblen Viewer öffnen können.

### Erwartetes Ergebnis

Wenn Sie *GroupShapeDemo.docx* öffnen, sehen Sie eine leere Seite mit einem gruppierten Objekt, das ein hellblaues Rechteck und eine rosa Ellipse enthält. Durch Auswählen der Gruppe können Sie beide Formen gemeinsam verschieben, was bestätigt, dass das **Gruppieren mehrerer Formen** wie beabsichtigt funktioniert hat.

## Warum ein GroupShape verwenden?

* **Atomare Transformationen** – Skalieren, Drehen oder Verschieben der Gruppe wirkt sich einheitlich auf alle Kinder aus.
* **Logische Organisation** – Hält zusammengehörige Grafiken zusammen, wodurch die Dokumentenstruktur leichter zu pflegen ist.
* **Performance** – Das Rendern eines einzelnen Containers ist oft schneller als das Verarbeiten vieler unabhängiger Formen.

Falls Sie später ein einzelnes Kind ändern müssen, können Sie es über `group.ChildNodes` nach Index oder nach seiner `Name`‑Eigenschaft abrufen.

## Häufige Variationen und Sonderfälle

| Szenario                                 | Wie man den Code anpasst                                                            |
|------------------------------------------|--------------------------------------------------------------------------------------|
| **Verschiedene Formtypen**                | Ersetzen Sie `ShapeType.Rectangle` oder `ShapeType.Ellipse` durch einen anderen `ShapeType` |
| **Text in einer Form hinzufügen**           | Verwenden Sie `Shape.TextPath.Text = "Hello"` nach dem Einfügen der Form                    |
| **Drehwinkel festlegen**             | `group.Rotation = 45;` (Grad)                                                 |
| **Als PDF statt DOCX speichern**        | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Rand auf die Gruppe anwenden**       | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Pro‑Tipps

* **Benennen Sie Ihre Formen** – `rectangle.Name = "MyRect";` erleichtert das spätere Auffinden.
* **Verwenden Sie relative Positionierung** – Setzen Sie `group.RelativeHorizontalPosition` auf `RelativeHorizontalPosition.Page`, wenn die Gruppe an den Seitenrändern verankert bleiben soll.
* **Ressourcen freigeben** – Umhüllen Sie das `Document` in einem `using`‑Block, wenn Sie in größeren Anwendungen arbeiten, um nicht verwalteten Speicher zeitnah freizugeben.

## Vollständiger Quellcode für schnelles Kopieren‑Einfügen

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Kopieren Sie den Code in ein neues Konsolenprojekt, stellen Sie das `Aspose.Words`‑NuGet‑Paket wieder her und führen Sie es aus. Die Ausgabedatei erscheint im `bin/Debug/net6.0`‑Ordner des Projekts (oder dem entsprechenden Ordner).

## Nächste Schritte

Jetzt, da Sie **ein leeres Word-Dokument erstellen**, **ein Rechteck einfügen** und **mehrere Formen gruppieren** können, könnten Sie folgendes erkunden:

* **Textfelder** innerhalb einer Gruppe hinzufügen, um beschriftete Diagramme zu erstellen.
* Die gruppierte Grafik in ein Bild exportieren mit `doc.Save("image.png", SaveFormat.Png)`.
* Gruppen mit Tabellen kombinieren für reich formatierte Berichte.

Experimentieren Sie mit verschiedenen Formeigenschaften, Gruppenhierarchien und Exportformaten, um die Zeichenfähigkeiten von Aspose.Words voll auszuschöpfen.

--- 

*Denken Sie daran*: Das Gruppieren von Formen ist ein leistungsstarkes Mittel, um Ihre Word-Dokumente übersichtlich und Ihren Code wartbar zu halten. Viel Spaß beim Coden!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}