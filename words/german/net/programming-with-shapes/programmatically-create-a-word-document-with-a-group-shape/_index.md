---
category: general
date: 2026-09-27
description: Programmgesteuert ein Word‑Dokument mit einer Gruppierung von Formen
  mithilfe von Aspose.Words in C# erstellen. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung,
  um die Datei zu erzeugen und nützliche Tipps zu erhalten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: de
lastmod: 2026-09-27
og_description: Erstellen Sie programmgesteuert ein Word‑Dokument mit einer Gruppierung
  von Formen mithilfe von Aspose.Words. Dieses Tutorial führt Sie durch den vollständigen
  C#‑Code, erklärt jeden Schritt und zeigt das Endergebnis.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Programmatisch ein Word‑Dokument mit einer Gruppierung erstellen – C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Programmgesteuert ein Word‑Dokument mit einer Gruppierung erstellen
url: /de/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Programmatisch ein Word-Dokument mit einer Gruppierungsform erstellen

Wenn Sie **programmatisch ein Word-Dokument** erstellen müssen, das eine gruppierte Zeichnung enthält, zeigt Ihnen dieser Leitfaden genau, wie Sie dies mit Aspose.Words für .NET tun können. Egal, ob Sie einen Vertragsgenerator, einen Berichtsgenerator oder ein Formular‑Ausfüll‑Tool erstellen, Sie lernen den vollständigen C#‑Code, warum jeder API‑Aufruf wichtig ist und wie Sie gängige Randfälle behandeln.

Das Erstellen einer Gruppierungsform in Word kann knifflig sein, weil das Word-Objektmodell Gruppierungsformen als Container für andere Zeichenobjekte behandelt. Dieses Tutorial beantwortet nicht nur **wie man Word‑Dokumente mit Gruppierungsformen erstellt**, sondern zeigt auch, wie man ein Klartext‑StructuredDocumentTag (SDT) in die Gruppe einbettet, sodass die Form bearbeitbaren Inhalt enthalten kann.

## Was Sie erreichen werden

- Ein neues leeres Word-Dokument mit `Document` und `DocumentBuilder` initialisieren.
- Ein `GroupShape` an der aktuellen Cursorposition einfügen.
- Ein Klartext-`StructuredDocumentTag` (SDT) zur Gruppierungsform hinzufügen.
- Die Datei als `.docx` speichern, das in Microsoft Word geöffnet werden kann.
- Die wichtigsten Eigenschaften von `GroupShape` und `StructuredDocumentTag` für zukünftige Erweiterungen verstehen.

### Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+).
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`).
- Eine C#‑IDE wie Visual Studio 2022 oder VS Code mit der C#‑Erweiterung.

---

## Programmatisch ein Word-Dokument erstellen – Projekt einrichten

1. **Ein neues Konsolenprojekt erstellen**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Öffnen Sie das Projekt in Ihrer IDE** und ersetzen Sie den Inhalt von `Program.cs` durch den im nächsten Abschnitt gezeigten Code.

> **Profi‑Tipp:** Halten Sie Ihren Projektordner sauber; Aspose.Words schreibt die Ausgabedatei in das Arbeitsverzeichnis, sofern Sie keinen absoluten Pfad angeben.

## Schritt 1: Dokument und Builder initialisieren

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Warum das wichtig ist:**  
`Document` repräsentiert die gesamte Word-Datei, während `DocumentBuilder` es Ihnen ermöglicht, neue Elemente zu positionieren, ohne manuell durch den Knotebaum zu navigieren. Das frühzeitige Festlegen der Seitenabmessungen stellt sicher, dass die Gruppierungsform nicht über die Seite hinausläuft.

## Schritt 2: Ein GroupShape an der aktuellen Cursorposition einfügen

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Erklärung:**  
Ein `GroupShape` ist ein Zeichenobjekt, das andere Formen, Bilder oder Textfelder enthalten kann. Durch das Festlegen von `Width`, `Height`, `Left` und `Top` steuern Sie die genaue Platzierung auf der Seite. Die Methode `InsertNode` fügt die Form in den Hauptdokumentfluss ein und verhält sich wie ein schwebendes Objekt.

## Schritt 3: Ein Klartext‑StructuredDocumentTag (SDT) innerhalb der Gruppe hinzufügen

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Warum ein SDT verwenden?**  
StructuredDocumentTags sind die nativen Inhaltssteuerelemente von Word. Sie ermöglichen es Benutzern, den Text direkt im gespeicherten Dokument zu bearbeiten, und können später programmgesteuert für die Datenerfassung abgerufen werden. Das Platzieren eines SDT innerhalb einer Gruppierungsform erlaubt es, visuelle Gruppierung mit bearbeitbarem Inhalt zu kombinieren.

## Schritt 4: Dokument speichern

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Ergebnis:**  
Beim Öffnen von `GroupShapeDemo.docx` in Microsoft Word wird ein schwebendes Rechteck (die Gruppierungsform) angezeigt, das einen Textplatzhalter mit dem Text „Text hier eingeben“ enthält. Benutzer können in die Form klicken und direkt tippen.

### Erwarteter Ausgabescreenshot (konzeptionell)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Der äußere Kasten ist das `GroupShape`; der innere graue Bereich ist das `StructuredDocumentTag`.

---

## Wie man ein GroupShape‑Word erstellt – zusätzliche Überlegungen

### Weitere Kindformen hinzufügen

Sie können die Gruppe erweitern, indem Sie zusätzliche Zeichenobjekte wie Bilder oder Textfelder anhängen:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Steuerung des Umbruchstils

Wenn Sie möchten, dass die Gruppierungsform hinter dem Text bleibt oder einen engen Umbruch hat, setzen Sie die Eigenschaft `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Randfall: Leere Gruppierungsform

Ein `GroupShape` ohne Kinder wird als unsichtbarer Platzhalter dargestellt. Vergewissern Sie sich stets, dass mindestens ein Kind (z. B. ein SDT oder ein Bild) hinzugefügt wird; andernfalls könnte Word die Gruppe beim Speichern entfernen.

### Hinweis zur Kompatibilität

Aspose.Words 23.10+ unterstützt `GroupShape` und `StructuredDocumentTag` vollständig. Wenn Sie ältere Versionen anvisieren, kann die Methode `AppendChild` sich anders verhalten, und Sie müssen möglicherweise nach dem Speichern `UpdatePageLayout` aufrufen.

---

## Vollständiges ausführbares Beispiel

Kopieren Sie das gesamte Snippet unten in `Program.cs` und führen Sie das Projekt aus. Der Code enthält alle oben genannten Schritte in einem einzigen, eigenständigen Programm.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierungsform in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Rechteckform in Word mit C# erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Leeres Word-Dokument mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}