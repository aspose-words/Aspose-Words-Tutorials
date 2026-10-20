---
category: general
date: 2026-09-21
description: Erstellen Sie ein leeres Word‑Dokument mit Aspose.Words, legen Sie die
  Größe, Position und Farbe einer Form fest und speichern Sie die DOCX‑Datei in einem
  einzigen Durchlauf.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: de
lastmod: 2026-09-21
og_description: Erstellen Sie ein leeres Word‑Dokument, legen Sie die Größe der Form
  fest, setzen Sie die Position der Form, bestimmen Sie die Farbe der Form und speichern
  Sie die DOCX‑Datei mit Aspose.Words in wenigen Minuten.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Erstellen Sie ein leeres Word‑Dokument und fügen Sie farbige Formen hinzu
  – Aspose.Words‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Erstellen Sie ein leeres Word‑Dokument und fügen Sie farbige Formen mit Aspose.Words
  hinzu
url: /de/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein leeres Word-Dokument und fügen Sie farbige Formen mit Aspose.Words hinzu

Wenn Sie programmgesteuert **ein leeres Word-Dokument erstellen** müssen, zeigt Ihnen dieser Leitfaden, wie das mit Aspose.Words funktioniert. Sie lernen, wie Sie **Formgröße festlegen**, **Formposition festlegen**, **Formfarbe festlegen** und schließlich **die docx-Datei speichern**, ohne Ihre IDE zu verlassen.

Die Arbeit mit Word-Dateien in C# bedeutet oft das Jonglieren mit Low‑Level‑OpenXML‑Aufrufen, aber Aspose.Words abstrahiert die Komplexität. Am Ende dieses Tutorials verfügen Sie über ein voll funktionsfähiges `.docx`, das eine gruppierte Form aus zwei farbigen Rechtecken enthält – ideal für Berichte, Zertifikate oder benutzerdefinierte Vorlagen.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
- Aspose.Words für .NET 23.9 oder neuer (Installation über NuGet: `Install-Package Aspose.Words`)
- Grundlegende Kenntnisse in C# und Visual Studio (oder jedem C#‑Editor)

Keine vorhandene Word-Datei ist erforderlich; das Tutorial beginnt mit dem **Erstellen eines leeren Word-Dokuments** von Grund auf.

## Erstellen Sie ein leeres Word-Dokument mit Aspose.Words

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt stellt eine leere Word‑Datei im Speicher dar.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` ist zunächst leer, was genau das ist, was Sie benötigen, wenn Sie **ein leeres Word-Dokument erstellen**. Der `builder` wird später verwendet, um die Formgruppe an der aktuellen Cursorposition einzufügen.

## Formgröße festlegen und ein GroupShape erstellen

Ein `GroupShape` funktioniert wie ein Container, der mehrere einzelne Formen aufnehmen kann. Definieren Sie zunächst die Gesamtabmessungen des Containers.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Hier **setzen wir die Formgröße** für die Gruppe selbst (300 × 200). Die gleichen Eigenschaftsnamen (`Width`, `Height`) werden für jede Unterform verwendet, was Ihnen eine feinkörnige Kontrolle über jedes Element ermöglicht.

## Das erste Rechteck hinzufügen und die Formfarbe festlegen

Fügen Sie nun ein Rechteck zur Gruppe hinzu und geben ihm eine Hintergrundfarbe.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

Die Eigenschaft `FillColor` **legt die Formfarbe fest**. Mit `System.Drawing.Color` können Sie jeden vordefinierten oder benutzerdefinierten ARGB‑Wert auswählen.

## Ein zweites Rechteck hinzufügen, Größe, Position und Farbe festlegen

Ein zweites Rechteck zeigt, wie Sie **die Formposition** relativ zur Gruppe festlegen und wie Sie deren Farbe ändern.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Da die Breite der Gruppe 300 Punkte beträgt, passen die beiden 120‑Punkt‑Rechtecke bequem mit einer Lücke von 30 Punkten dazwischen. Passen Sie `Left` und `Top` an, wenn Sie ein anderes Layout benötigen.

## Das GroupShape in das Dokument einfügen

Nachdem die Gruppe vollständig konfiguriert ist, platzieren Sie sie an der aktuellen Cursorposition.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` schreibt die Form direkt in den Dokumentenkörper und bewahrt die exakt **festgelegte Formposition** aus früheren Schritten.

## Die docx-Datei speichern

Der letzte Schritt besteht darin, das Dokument auf die Festplatte zu schreiben. Dies demonstriert die **save docx file**‑Operation.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Nach dem Ausführen des Programms öffnen Sie `GroupShape.docx` in Microsoft Word. Sie sollten eine leere Seite mit einer gruppierten Form sehen, die zwei farbige Rechtecke nebeneinander enthält.

### Erwartete Ausgabe

- Eine einseitige `.docx`‑Datei.
- Die Seite enthält eine Gruppenform, die 100 pts von den linken und oberen Rändern entfernt ist.
- Innerhalb der Gruppe befindet sich ein hellblaues Rechteck links und ein hellkorallenfarbenes Rechteck rechts, jeweils 120 × 80 pts.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie in eine Konsolenanwendung kopieren‑und‑einfügen können. Es werden keine zusätzlichen Dateien benötigt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Das Ausführen dieses Programms erzeugt das exakt beschriebene Dokument und erfüllt alle vier Ziele: **create blank word document**, **set shape size**, **set shape position**, **set shape color** und **save docx file**.

## Häufige Variationen und Sonderfälle

| Szenario | Was zu ändern ist | Warum es wichtig ist |
|----------|-------------------|----------------------|
| **Verschiedene Formtypen** | Ersetzen Sie `ShapeType.Rectangle` durch `ShapeType.Ellipse`, `ShapeType.Triangle` usw. | Ermöglicht das Erstellen komplexerer Grafiken ohne externe Bilder. |
| **Dynamische Abmessungen** | Berechnen Sie `Width` und `Height` aus Benutzereingaben oder Konfigurationsdateien. | Macht die Lösung wiederverwendbar für mehrere Dokumentvorlagen. |
| **Als PDF speichern** | Rufen Sie `document.Save("output.pdf", SaveFormat.Pdf);` auf | Wenn Empfänger ein nicht‑editierbares Format benötigen, ist PDF eine sichere Wahl. |
| **Text in einer Form hinzufügen** | Erstellen Sie eine `TextBox`‑Form und setzen Sie `TextBox.Text`. | Nützlich zum Erstellen beschrifteter Abzeichen oder Hinweisfelder. |
| **Mehrere Gruppen auf einer Seite** | Wiederholen Sie die Schritte 2‑5 mit unterschiedlichen `Left`/`Top`‑Werten. | Ermöglicht das Erstellen von Dashboards oder mehrteiligen Layouts. |

### Profi‑Tipp

Wenn Sie Formen präzise ausrichten müssen, verwenden Sie vor dem Einfügen der Gruppe die Eigenschaft `ShapeBase.WrapType = WrapType.Inline`. Dadurch wird die Gruppe wie ein Absatz behandelt und verhindert unerwarteten Textfluss darum herum.

## Fazit

Sie wissen jetzt, wie man mit Aspose.Words **ein leeres Word-Dokument erstellt**, **Formgröße festlegt**, **Formposition festlegt**, **Formfarbe festlegt** und **die docx-Datei speichert**. Das vollständige Beispiel zeigt ein sauberes, wiederverwendbares Muster zum Hinzufügen gruppierter Grafiken zu jedem Word‑Automatisierungsprojekt.

Ab hier können Sie folgendes erkunden:

- Weitere Formen oder Bilder zum selben `GroupShape` hinzufügen (**set shape size**, **set shape color**‑Variationen).
- `ShapeBase.Rotation` verwenden, um Rechtecke für dekorative Effekte zu drehen.
- Das gleiche Dokument als PDF oder HTML exportieren, um die Verbreitung zu erweitern (**save docx file**‑Alternative).

Fühlen Sie sich frei, mit verschiedenen Farben, Größen und Layout‑Logiken zu experimentieren, um Ihren spezifischen Berichts‑ oder Vorlagenanforderungen gerecht zu werden. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}