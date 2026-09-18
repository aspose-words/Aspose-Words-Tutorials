---
category: general
date: 2026-09-18
description: Erstellen Sie ein leeres Word‑Dokument und blenden Sie eine Ellipsen‑Form
  mit Aspose.Words aus. Erfahren Sie, wie Sie Formen in Word ausblenden, wie Sie eine
  Ellipse einfügen und wie Sie schnell eine versteckte Form erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: de
lastmod: 2026-09-18
og_description: Erstellen Sie ein leeres Word‑Dokument und verbergen Sie eine Ellipsen‑Form
  in Word. Diese Anleitung zeigt Ihnen Schritt für Schritt, wie Sie eine Ellipse einfügen,
  die Form in Word ausblenden und eine versteckte Form mit Aspose.Words erstellen.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Erstelle ein leeres Word‑Dokument mit einer versteckten Ellipsenform
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Erstelle ein leeres Word‑Dokument mit einer versteckten Ellipsenform
url: /de/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein leeres Word‑Dokument mit einer versteckten Ellipsenform

Wenn Sie ein **leeres Word‑Dokument** erstellen müssen, das eine Form enthält, die nicht im Layout erscheinen soll, zeigt Ihnen dieser Leitfaden genau, wie Sie das tun. Durch die Verwendung von Aspose.Words für .NET können Sie programmgesteuert eine Ellipse einfügen und dann die Form ausblenden, sodass das Dokument visuell leer bleibt, während die Formdaten erhalten bleiben.

In diesem Tutorial lernen Sie:

* wie man **leeres Word‑Dokument**‑Objekte erstellt,
* wie man **Ellipse einfügt** mit `DocumentBuilder`,
* wie man **Form in Word ausblendet**, sodass sie die Seite nicht beeinflusst,
* wie man **versteckte Form**‑Objekte für die spätere Verarbeitung erstellt.

Die Schritte funktionieren mit .NET 6+ und der neuesten Aspose.Words‑Version (23.9 zum Zeitpunkt der Erstellung). Es ist keine zusätzliche Office‑Installation erforderlich.

## Voraussetzungen

* Visual Studio 2022 (oder jede C#‑IDE)
* .NET 6 SDK oder neuer
* Aspose.Words für .NET NuGet‑Paket  
  ```bash
  dotnet add package Aspose.Words
  ```
* Grundkenntnisse in C# und Word‑Dokumentkonzepten

## Schritt 1: Erstellen Sie ein leeres Word‑Dokument

Das Erste, was Sie tun müssen, ist ein `Document`‑Objekt zu instanziieren. Dieses Objekt stellt eine leere `.docx`‑Datei dar und bildet die Grundlage für alle weiteren Vorgänge.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Das Erstellen eines **leeren Word‑Dokuments** gibt Ihnen eine saubere Leinwand – keine Absätze, keine Abschnitte, nur die zugrunde liegende Paketstruktur. Dies ist der ideale Ausgangspunkt, wenn Sie nur eine versteckte Form und sonst nichts benötigen.

## Schritt 2: Initialisieren Sie einen DocumentBuilder

`DocumentBuilder` stellt eine praktische API zum Hinzufügen von Inhalten zu einem `Document` bereit. Er funktioniert wie ein Cursor, den Sie durch das Dokument bewegen.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Der Builder erzeugt automatisch einen Standard‑Erste‑Abschnitt und -Absatz, sodass Sie Formen einfügen können, ohne manuell Abschnitte hinzuzufügen.

## Schritt 3: Eine Ellipsenform einfügen

Jetzt **fügen wir eine Ellipse** mit der Methode `InsertShape` ein. Die Methode erwartet einen `ShapeType`‑Enum‑Wert, die Breite und die Höhe (in Punkten).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Warum eine Ellipse? Eine Ellipse ist eine Vektorform, die ausgeblendet werden kann, ohne den umgebenden Textfluss zu beeinflussen. Die Breite von 100 pt und die Höhe von 50 pt sind willkürlich; Sie können sie an Ihre späteren Verarbeitungsanforderungen anpassen.

## Schritt 4: Die Form ausblenden, damit sie nicht im Layout erscheint

Um **die Form in Word auszublenden**, setzen Sie die Eigenschaft `Hidden` des `Shape`‑Objekts auf `true`. Wenn das Dokument in Microsoft Word geöffnet wird, ist die Form unsichtbar und nimmt keinen Platz im Layout ein.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

Das `Hidden`‑Flag wird im XML der Form gespeichert (`<w:hidden/>`). Word respektiert dieses Attribut beim Rendern, weshalb das Dokument völlig leer aussieht, obwohl die Form vorhanden ist.

### Profi‑Tipp

Wenn Sie die Form später wieder sichtbar machen müssen, setzen Sie einfach `ellipse.Hidden = false;` und speichern das Dokument.

## Schritt 5: Das Dokument mit der versteckten Form speichern

Zum Schluss speichern Sie das Dokument auf dem Datenträger. Die Datei ist ein reguläres `.docx`, das jeder Textverarbeitungs‑Editor öffnen kann.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Die gespeicherte Datei `HiddenEllipse.docx` ist ein **leeres Word‑Dokument**, das eine versteckte Ellipse enthält. Öffnet man sie in Microsoft Word, wird eine leere Seite angezeigt, aber die Form ist weiterhin in der Open‑XML‑Struktur vorhanden.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, eigenständige Programm, das Sie kopieren, einfügen und ausführen können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Erwartete Ausgabe**

* Eine Datei namens `HiddenEllipse.docx` erscheint in `C:\Temp`.
* Öffnet man die Datei in Microsoft Word, wird eine völlig leere Seite angezeigt.
* Untersucht man das Dokument mit dem Open XML‑SDK oder einem ZIP‑Viewer, findet man das `<w:shape>`‑Element mit `<w:hidden/>` im Dokumententeil.

## Häufige Fragen und Sonderfälle

### Was tun, wenn die Form trotzdem erscheint?

* Stellen Sie sicher, dass Sie Aspose.Words 23.9 oder neuer verwenden – ältere Versionen hatten einen Fehler, bei dem `Hidden` für einige Formtypen ignoriert wurde.
* Prüfen Sie, ob Sie keine zusätzliche Formatierung (z. B. `WrapType`) anwenden, die die Form zwingt, Layout‑Platz zu belegen.

### Kann ich andere Formtypen ausblenden?

Ja. Die gleiche `Hidden`‑Eigenschaft funktioniert für `ShapeType.Rectangle`, `ShapeType.Picture` usw. Ersetzen Sie einfach `ShapeType.Ellipse` durch den gewünschten Typ.

### Wie kann man versteckte Formen später auflisten?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Dieses Snippet iteriert über alle Formen und gibt diejenigen aus, die ausgeblendet sind – nützlich für **versteckte Form**‑Workflows, bei denen Sie die Formen später verarbeiten oder wieder einblenden müssen.

## Fazit

Sie wissen jetzt, wie Sie ein **leeres Word‑Dokument** erstellen, eine **Ellipse einfügen** und **die Form in Word ausblenden**, um eine **versteckte Form** zu erzeugen, die für den Leser unsichtbar bleibt. Diese Technik ist praktisch, um Metadaten, Lesezeichen oder benutzerdefiniertes XML in einem Dokument zu speichern, ohne das visuelle Erscheinungsbild zu verändern.

### Nächste Schritte

* Erkunden Sie **wie man Formen bedingt ausblendet** basierend auf dem Dokumentinhalt.
* Lernen Sie **wie man Formen wieder einblendet**, wenn Sie eine finale Version des Dokuments erzeugen.
* Kombinieren Sie versteckte Formen mit **benutzerdefinierten Dokumenteigenschaften**, um maschinenlesbare Daten einzubetten.

Probieren Sie verschiedene Formtypen, Größen und Ausblend‑Logiken aus, um sie an Ihr Automatisierungsszenario anzupassen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden vorgestellten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}