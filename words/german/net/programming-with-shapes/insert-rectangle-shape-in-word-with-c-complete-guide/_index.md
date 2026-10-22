---
category: general
date: 2026-08-10
description: Rechteckform in Word mit C# einfügen. Erfahren Sie, wie Sie die Form
  ausblenden, die Form in Word ausblenden und eine versteckte Form mit Aspose.Words
  erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- hide shape in word
- create hidden shape
language: de
lastmod: 2026-08-10
og_description: Rechteckform in Word mit C# einfügen. Dieses Tutorial erklärt, wie
  man eine Form ausblendet, eine Form in Word ausblendet und eine versteckte Form
  mit vollständigen Codebeispielen erstellt.
og_image_alt: Screenshot showing a hidden rectangle shape inserted into a Word document
  using C#
og_title: Rechteckform in Word mit C# einfügen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  headline: Insert rectangle shape in Word with C# – complete guide
  type: TechArticle
- description: Insert rectangle shape in Word using C#. Learn how to hide shape, hide
    shape in Word, and create hidden shape with Aspose.Words.
  name: Insert rectangle shape in Word with C# – complete guide
  steps:
  - name: Can I hide only the outline but keep the fill visible?
    text: Yes. Instead of setting `Hidden = true`, you can set `rectangle.LineFormat.Visible
      = false` to hide the border while keeping the fill color. This is a variation
      of **how to hide shape** that preserves part of the visual appearance.
  - name: Does the hidden flag work in older Word versions (2003, 2007)?
    text: The hidden attribute is part of the Open XML specification introduced with
      Word 2007. Documents saved in the older binary `.doc` format will not preserve
      the flag. To support legacy formats, save the document as `.docx` and, if needed,
      convert it later using Aspose.Words’ `SaveFormat.Doc`.
  - name: What if I need to hide multiple shapes at once?
    text: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` on each shape that meets your criteria (e.g., a specific
      `ShapeType` or a custom `AlternativeText` value).
  - name: Is there a performance impact when hiding shapes?
    text: The hidden flag adds a tiny XML attribute; it does not affect rendering
      speed. However, a very large number of hidden objects can increase file size
      marginally. Remove shapes you never need to keep the document lean.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Rechteckform in Word mit C# einfügen – vollständige Anleitung
url: /de/net/programming-with-shapes/insert-rectangle-shape-in-word-with-c-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Word mit C# einfügen – vollständige Anleitung

Wenn Sie **eine Rechteckform** in ein Word‑Dokument mit C# einfügen möchten, zeigt Ihnen diese Anleitung die genauen Schritte. Sie erfahren außerdem **wie man eine Form ausblendet**, sodass sie in der finalen Datei nicht erscheint – das beantwortet die häufige Frage **hide shape in Word** und demonstriert, wie man **create hidden shape** programmgesteuert erzeugt.

Das Tutorial behandelt alles von der Einrichtung des Aspose.Words SDK bis zur Überprüfung, dass die Form ausgeblendet ist. Am Ende des Artikels besitzen Sie einen wiederverwendbaren Code‑Snippet, den Sie in jedes .NET‑Projekt einbinden können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- .NET 6.0 oder höher installiert (der Code funktioniert auch mit .NET Framework 4.6+)
- Eine gültige Aspose.Words for .NET‑Lizenz oder einen temporären Evaluierungsschlüssel
- Visual Studio 2022 (oder eine beliebige IDE, die C# unterstützt)
- Grundkenntnisse in C#‑Syntax und dem Document Object Model (DOM) von Word‑Dateien

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Schritt 1: Neues leeres Dokument und einen DocumentBuilder erstellen

Der erste Vorgang besteht darin, ein `Document`‑Objekt zu instanziieren. Der `DocumentBuilder` bietet eine bequeme API zum Einfügen von Inhalten wie Formen, Absätzen und Tabellen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document document = new Document();

// DocumentBuilder lets you add elements to the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

**Warum das wichtig ist:** `Document` repräsentiert die gesamte .docx‑Datei, während `DocumentBuilder` einen Cursor verwaltet, der verfolgt, wo das nächste Element platziert wird. Das Initialisieren beider Objekte ist die Grundlage für jede Word‑Automatisierungsaufgabe.

## Schritt 2: Rechteckform einfügen

Jetzt fügen Sie das Rechteck ein. Die Methode `InsertShape` benötigt den Formtyp und ihre Abmessungen in Punkten (1 Punkt ≈ 1/72 Zoll). Eine Größe von **200 × 100 Punkten** ergibt ein Rechteck von etwa 2,78 × 1,39 Zoll.

```csharp
// Insert a rectangle of 200x100 points.
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Warum das wichtig ist:** Das erhaltene `Shape`‑Objekt ist vollständig konfigurierbar – Farbe, Rahmen, Text und Sichtbarkeit können alle geändert werden, bevor das Dokument gespeichert wird.

## Schritt 3: Die Form ausblenden

Um zu verhindern, dass das Rechteck angezeigt oder gedruckt wird, setzen Sie die Eigenschaft `Hidden` auf `true`. Diese Eigenschaft entspricht direkt dem Word‑Attribut „Hidden“, das Word sowohl in der Ansicht als auch im Druckmodus respektiert.

```csharp
// Hide the shape so it never appears.
rectangle.Hidden = true;
```

**Warum das wichtig ist:** Das Setzen von `Hidden` ist der Standardweg, um **hide shape in Word** zu erreichen, ohne die Form aus der Dokumentstruktur zu entfernen. Die Form bleibt für Code zugänglich, sodass spätere Manipulationen wie bedingte Formatierungen oder datenbasierte Sichtbarkeitsumschaltungen möglich sind.

## Schritt 4: Dokument speichern

Abschließend speichern Sie das Dokument auf dem Datenträger. Wählen Sie beliebig einen Ordner; das Beispiel verwendet einen Platzhalter‑Pfad, den Sie durch einen echten Pfad ersetzen sollten.

```csharp
// Save the document with the hidden rectangle.
document.Save(@"C:\Temp\HiddenShape.docx");
```

**Warum das wichtig ist:** Das Speichern finalisiert die Datei und schreibt das Hidden‑Flag in das zugrunde liegende Open XML. Wenn Sie das Dokument in Microsoft Word öffnen, ist das Rechteck unsichtbar, was bestätigt, dass Sie erfolgreich **created hidden shape** haben.

## Schritt 5: Die ausgeblendete Form überprüfen

Öffnen Sie das erzeugte `HiddenShape.docx` in Microsoft Word:

1. Gehen Sie zu **Datei → Optionen → Anzeige** und stellen Sie sicher, dass *„Ausgeblendeten Text anzeigen“* **nicht aktiviert** ist.  
2. Das Rechteck sollte auf keiner Seite sichtbar sein.  
3. Um sicherzugehen, aktivieren Sie *„Ausgeblendeten Text anzeigen“*; das Rechteck erscheint mit einer schwachen, gepunkteten Kontur, was beweist, dass die Form existiert, aber ausgeblendet ist.

Falls das Rechteck noch sichtbar ist, prüfen Sie, ob Sie die Datei nach dem Setzen von `Hidden = true` gespeichert haben und ob Sie die richtige Datei öffnen.

## Vollständiges, ausführbares Beispiel

Nachfolgend das komplette Programm, das Sie kopieren, einfügen und direkt ausführen können.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a rectangle shape of 200x100 points.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Step 3: Hide the shape so it does not appear when viewed or printed.
        rectangle.Hidden = true;

        // Step 4: Save the document with the hidden shape.
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
        Console.WriteLine("Open the file in Word to verify that the rectangle is hidden.");
    }
}
```

**Erwartete Ausgabe:** Die Konsole gibt den Dateipfad und eine kurze Erinnerung aus. Wenn die Datei in Word geöffnet wird, ist das Rechteck unsichtbar, solange ausgeblendeter Text nicht aktiviert ist.

## Häufige Fragen und Sonderfälle

### Kann ich nur die Kontur ausblenden, aber die Füllung sichtbar lassen?

Ja. Anstatt `Hidden = true` zu setzen, können Sie `rectangle.LineFormat.Visible = false` verwenden, um den Rand zu verbergen und die Füllfarbe beizubehalten. Das ist eine Variante von **how to hide shape**, die einen Teil der visuellen Darstellung erhält.

### Funktioniert das Hidden‑Flag in älteren Word‑Versionen (2003, 2007)?

Das Hidden‑Attribut ist Teil der Open XML‑Spezifikation, die mit Word 2007 eingeführt wurde. Dokumente, die im älteren binären `.doc`‑Format gespeichert werden, bewahren das Flag nicht. Um Legacy‑Formate zu unterstützen, speichern Sie das Dokument als `.docx` und konvertieren Sie es bei Bedarf später mit Aspose.Words’ `SaveFormat.Doc`.

### Was, wenn ich mehrere Formen gleichzeitig ausblenden muss?

Iterieren Sie über die Sammlung `Document.GetChildNodes(NodeType.Shape, true)` und setzen Sie `Hidden = true` für jede Form, die Ihren Kriterien entspricht (z. B. ein bestimmter `ShapeType` oder ein benutzerdefinierter `AlternativeText`‑Wert).

```csharp
foreach (Shape shp in document.GetChildNodes(NodeType.Shape, true))
{
    if (shp.AlternativeText == "HideMe")
        shp.Hidden = true;
}
```

### Gibt es Performance‑Auswirkungen beim Ausblenden von Formen?

Das Hidden‑Flag fügt lediglich ein winziges XML‑Attribut hinzu; es beeinflusst die Rendergeschwindigkeit nicht. Allerdings kann eine sehr große Anzahl ausgeblendeter Objekte die Dateigröße geringfügig erhöhen. Entfernen Sie Formen, die Sie nie benötigen, um das Dokument schlank zu halten.

## Tipps und bewährte Vorgehensweisen

- **Geben Sie der Form einen aussagekräftigen Namen** mittels `rectangle.Name = "MyHiddenRectangle"`; das erleichtert das spätere Suchen der Form im DOM.  
- **Setzen Sie `AlternativeText`** auf ein benutzerdefiniertes Tag (z. B. `"HiddenShape"`). Damit können Sie die Form finden, ohne sich auf ihren Index zu verlassen.  
- **Umgeben Sie den Code mit einem try‑catch‑Block**, um Lizenz‑ oder I/O‑Ausnahmen elegant zu behandeln.  
- **Entsorgen Sie das Document** nach dem Speichern, wenn Sie viele Dateien in einer Schleife verarbeiten, um nicht verwaltete Ressourcen freizugeben: `document.Dispose();`.

## Fazit

Sie wissen jetzt, wie Sie **eine Rechteckform** in ein Word‑Dokument mit C# **einfügen**, **wie Sie shape in Word ausblenden** und **wie Sie eine hidden shape erstellen**, die Teil der Dokumentstruktur bleibt, aber für Endbenutzer unsichtbar ist. Das vollständige, ausführbare Beispiel demonstriert den gesamten Workflow von der Dokumenterstellung bis zur Verifizierung.

Als nächstes könnten Sie **how to hide shape** basierend auf Benutzereingaben erkunden oder ausgeblendete Formen mit Inhaltssteuerelementen für dynamische Dokumentengenerierung kombinieren. Die gleiche Technik lässt sich auch auf andere Formtypen wie Ellipsen, Pfeile oder benutzerdefinierte Zeichnungen anwenden.

Experimentieren Sie gern mit unterschiedlichen Abmessungen, Farben und Sichtbarkeitseinstellungen. Bei Problemen schauen Sie noch einmal die obigen Schritte durch oder konsultieren Sie die Aspose.Words‑Dokumentation für tiefere API‑Details. Viel Spaß beim Coden!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}