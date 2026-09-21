---
category: general
date: 2026-09-21
description: Erstelle ein leeres Word‑Dokument mit einer versteckten Ellipse in C#.
  Erfahre, wie man eine Form in Word ausblendet und programmgesteuert eine versteckte
  Form erzeugt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: de
lastmod: 2026-09-21
og_description: Erstelle ein leeres Word‑Dokument mit einer versteckten Ellipse mithilfe
  von C#. Dieser Leitfaden zeigt, wie man Formen in Word ausblendet und versteckte
  Formen programmgesteuert erstellt.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Erstelle ein leeres Word‑Dokument mit einer versteckten Ellipsenform in
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man ein leeres Word‑Dokument erstellt und in C# eine versteckte Ellipse‑Form
  hinzufügt
url: /de/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word‑Dokument erstellt und eine versteckte Ellipsenform in C# hinzufügt

Wenn Sie ein **leeres Word‑Dokument** benötigen, das eine unsichtbare Grafik enthält, zeigt Ihnen diese Anleitung genau, wie das geht. Am Ende des Tutorials haben Sie eine .docx‑Datei, die leer aussieht, aber tatsächlich eine Ellipsenform enthält, die im Layout verborgen ist.

Wir verwenden Aspose.Words für .NET, um das Dokument zu erstellen, eine Ellipse einzufügen, sie zu verbergen und die Datei zu speichern. Die Schritte decken außerdem **wie man Ellipse‑Objekte erstellt**, den richtigen Weg, **eine Form in Word zu verbergen**, und **wie man versteckte Formen** programmiert, die in jedem .NET‑Projekt funktionieren, ab.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 SDK oder neuer installiert  
* Visual Studio 2022 (oder ein beliebiger C#‑Editor)  
* Eine Aspose.Words für .NET‑Lizenz oder eine kostenlose Evaluierungskopie  
* Grundlegende Kenntnisse der C#‑Syntax  

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Leeres Word‑Dokument mit Aspose.Words erstellen

Der erste Schritt besteht darin, eine leere Word‑Datei zu erzeugen. Das gibt uns eine saubere Leinwand, in die wir später versteckte Grafiken einfügen können.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Warum wir mit einem leeren Dokument beginnen** – Das Starten mit einer leeren Datei garantiert, dass kein unerwünschter Inhalt die versteckte Form beeinträchtigt. Außerdem bleibt die Dateigröße minimal, was nützlich ist, wenn das Dokument später als Vorlage verwendet wird.

## Wie man eine Ellipse im leeren Dokument erstellt

Als Nächstes benötigen wir einen `DocumentBuilder`, um Inhalte hinzuzufügen. Der Builder ermöglicht es uns, Formen genau dort zu platzieren, wo wir sie benötigen.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Erklärung** – `ShapeType.Ellipse` weist Aspose.Words an, eine kreis‑ähnliche Figur zu zeichnen. Breite und Höhe werden in Punkten gemessen (1 pt ≈ 1/72 Zoll). Sie können diese Werte an Ihre Design‑Bedürfnisse anpassen.

## Form in Word verbergen, sodass sie nicht im Layout erscheint

Eine versteckte Form befindet sich weiterhin im XML‑Dokument, was für Metadaten, bedingte Formatierung oder spätere programmgesteuerte Änderungen nützlich sein kann. Um sie zu verbergen, setzen wir die Eigenschaft `Hidden` auf `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Warum die Form verbergen** – Versteckte Formen werden vom Layout‑Engine ignoriert, sodass die Seite völlig leer wirkt. Die Form‑Daten bleiben jedoch erhalten, was nützlich sein kann, um Marker, Lesezeichen oder benutzerdefiniertes XML zu speichern, das nachgelagerte Prozesse auslesen können.

## Dokument mit der versteckten Form speichern

Abschließend schreiben wir die Datei auf die Festplatte. Die gespeicherte `.docx`‑Datei öffnet sich in Microsoft Word ohne sichtbaren Inhalt, während die versteckte Ellipse weiterhin vorhanden ist.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verifizierung** – Öffnen Sie die erzeugte Datei in Word, drücken Sie dann `Alt+F9`, um Feldfunktionen ein‑ bzw. auszublenden, und `Ctrl+A` → `Ctrl+Shift+F9`, um versteckte Objekte anzuzeigen. Sie sehen die Ellipse im XML des Dokuments (`word/document.xml`), aber nichts auf der Seite.

---

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in ein neues Konsolen‑Projekt kopieren‑und‑einfügen können. Es enthält alle `using`‑Direktiven und die `Main`‑Methode, sodass Sie es ohne weitere Boiler‑Plate ausführen können.

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
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Erwartete Ausgabe** – Beim Ausführen des Programms gibt die Konsole den Dateipfad aus, und die resultierende Word‑Datei enthält keine sichtbaren Objekte. Wenn Sie das Dokument mit einem Zip‑Tool untersuchen (`.docx` ist ein Zip‑Archiv), finden Sie das `<w:pict>`‑Element, das die Ellipse in `word/document.xml` beschreibt.

---

## Häufige Varianten und Sonderfälle

| Szenario | Was zu ändern ist | Warum es wichtig ist |
|----------|-------------------|----------------------|
| **Andere Form** | Ersetzen Sie `ShapeType.Ellipse` durch `ShapeType.Rectangle`, `ShapeType.Line` usw. | Ermöglicht das Verbergen anderer Grafiken bei gleichbleibendem Workflow. |
| **Mehrere versteckte Formen** | Rufen Sie `InsertShape` mehrmals auf und setzen Sie `Hidden = true` für jede. | Praktisch, um eine Sammlung von Markern oder Platzhaltern einzubetten. |
| **Bedingte Sichtbarkeit** | Verwenden Sie `shape.Visible = false` zusammen mit `shape.Hidden = true` für zusätzliche Sicherheit. | Ältere Word‑Versionen interpretieren `Visible` anders; beide Einstellungen decken alle Fälle ab. |
| **Speichern in einen Stream** | Ersetzen Sie `doc.Save(path)` durch `doc.Save(stream, SaveFormat.Docx)`. | Ermöglicht das direkte Senden des Dokuments über HTTP oder das Speichern in einer Datenbank. |
| **Stil anwenden** | Nach dem Einfügen `ellipse.FillColor`, `ellipse.LineWeight` usw. ändern, bevor Sie verbergen. | Das Styling der Form bleibt im XML erhalten und kann später wieder eingeblendet werden. |

**Pro‑Tipp:** Testen Sie die versteckte Form immer in der Ziel‑Word‑Version (z. B. Word 2019, Word 365), da gelegentlich Rendering‑Eigenheiten auftreten, wenn versteckte Objekte mit komplexen Seitenlayouts interagieren.

---

## Häufig gestellte Fragen

**F: Beeinflusst das Verbergen einer Form die Dateigröße?**  
A: Das XML der Form fügt ein paar hundert Bytes hinzu, was für die meisten Anwendungsfälle vernachlässigbar ist. Die Datei bleibt im Wesentlichen so groß wie ein wirklich leeres Dokument.

**F: Kann ich die Form später programmgesteuert wieder einblenden?**  
A: Ja. Laden Sie das Dokument, finden Sie die Form (`doc.GetChildNodes(NodeType.Shape, true)`) und setzen Sie `shape.Hidden = false`.

**F: Wird die versteckte Form beim Drucken angezeigt?**  
A: Nein. Versteckte Objekte werden aus dem Druck‑Layout ausgeschlossen, sodass die gedruckte Seite leer bleibt.

**F: Ist dieser Ansatz nur mit Office Open XML (OOXML) kompatibel?**  
A: Die `Hidden`‑Eigenschaft ist Teil der OOXML‑Spezifikation, sodass jeder Word‑Prozessor, der OOXML vollständig implementiert (Word, LibreOffice, Google Docs), das versteckte Flag respektiert.

---

## Fazit

Sie wissen jetzt, wie man **ein leeres Word‑Dokument erstellt**, **eine Ellipse erzeugt**, **eine Form in Word verbirgt** und **eine versteckte Form** mit Aspose.Words für .NET erstellt. Das Tutorial behandelte den gesamten Lebenszyklus – vom Initialisieren einer leeren Datei über das Einfügen, Verbergen und Speichern der Form – sowie Verifizierungsschritte und gängige Varianten.

Als Nächstes könnten Sie:

* Versteckte Textfelder für Metadaten hinzufügen (`hide shape in word`‑Technik auf Text angewendet)  
* Benutzerdefinierte XML‑Teile verwenden, um strukturierte Daten neben versteckten Formen zu speichern  
* Das Dokument mit versteckter Form in PDF konvertieren und dabei die versteckten Elemente erhalten  

Experimentieren Sie mit verschiedenen Formen und Sichtbarkeits‑Einstellungen, um zu sehen, wie versteckte Inhalte als leichter Datenspeicher in Word‑Dateien dienen können.

Viel Spaß beim Coden!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}