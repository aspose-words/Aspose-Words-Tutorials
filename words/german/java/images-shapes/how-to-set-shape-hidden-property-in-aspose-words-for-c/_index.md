---
category: general
date: 2026-08-20
description: Erfahren Sie, wie Sie die Eigenschaft „Hidden“ für Formen in Aspose.Words
  für C# festlegen. Diese Anleitung zeigt das Einfügen eines Bildes und das Ausblenden
  der Form, sodass sie weder in der Benutzeroberfläche noch im Druckausgabe erscheint.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: de
lastmod: 2026-08-20
og_description: Setzen Sie die versteckte Eigenschaft einer Form in Aspose.Words mit
  C#. Fügen Sie ein Bild ein, verbergen Sie die Form und stellen Sie sicher, dass
  sie weder in der Benutzeroberfläche noch im Druckausgabe angezeigt wird.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Setze die versteckte Eigenschaft von Shape in Aspose.Words – vollständige
  C#‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Wie man die versteckte Eigenschaft einer Form in Aspose.Words für C# festlegt
url: /de/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man die Eigenschaft „shape hidden“ in Aspose.Words für C# setzt

Wenn Sie die **shape hidden‑Eigenschaft** in einem Word‑Dokument festlegen müssen, zeigt Ihnen dieses Tutorial die genauen Schritte mit Aspose.Words für .NET. Egal, ob Sie eine Template‑Engine bauen, Berichte generieren oder ein Logo einbetten, das unsichtbar bleiben muss – Sie lernen, wie Sie ein Bild einfügen und die Form verbergen, sodass sie weder in der Benutzeroberfläche noch im Druck erscheint.

In diesem Leitfaden behandeln wir außerdem das **Einfügen von Bildern in ein Dokument**, erklären, warum das Verbergen einer Form für den Druck wichtig ist, und gehen den vollständigen, ausführbaren Code durch. Keine externen Referenzen nötig – einfach kopieren, einfügen und ausführen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 oder höher (die neueste Aspose.Words‑Version richtet sich an .NET 6+)
* Eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder den kostenlosen Evaluierungsmodus)
* Visual Studio 2022 oder eine beliebige C#‑IDE Ihrer Wahl
* Eine Bilddatei (z. B. `logo.png`) in einem Ordner, den Sie im Code referenzieren können

## Schritt 1: Erstellen eines neuen Document und DocumentBuilder

Die Klasse `DocumentBuilder` ist der Einstiegspunkt zum programmatischen Erstellen von Word‑Inhalten. Sie ermöglicht das Einfügen von Absätzen, Tabellen und Formen wie Bildern.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum dieser Schritt?*  
Durch das Erstellen eines `Document` erhalten Sie eine In‑Memory‑Repräsentation einer .docx‑Datei, während `DocumentBuilder` die Fluent‑API bereitstellt, die Objekte einfügt. Ohne diese Objekte können Sie keine Form im Dokument platzieren.

## Schritt 2: Das Bild als Form einfügen

Aspose.Words behandelt jedes Bild als `Shape`. Die Methode `InsertImage` gibt diese `Shape`‑Instanz zurück, die Sie anschließend manipulieren können.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Warum dieser Schritt?*  
`InsertImage` fügt das Bild nicht nur in den Textfluss ein, sondern liefert Ihnen auch eine Referenz (`picture`), die Sie konfigurieren können. Das ist entscheidend für die **C#‑shape‑hidden‑Eigenschaft**, die wir als Nächstes setzen.

## Schritt 3: Die shape hidden‑Eigenschaft setzen

Die Eigenschaft `Hidden` steuert, ob die Form in der UI und beim Drucken berücksichtigt wird. Wird sie auf `true` gesetzt, ist die Form in der Word‑UI unsichtbar und wird nicht gedruckt.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Warum dieser Schritt?*  
Wenn eine Form als hidden markiert ist, behandelt Word sie wie einen Kommentar – sie ist im Dokumenten‑Baum vorhanden, wird jedoch nie gerendert. Das ist das Kernstück des **set shape hidden property**.

## Schritt 4: Das Dokument speichern

Abschließend schreiben Sie das Dokument auf die Festplatte. Sie können jedes von Aspose.Words unterstützte Format wählen (`.docx`, `.pdf`, `.html` usw.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Warum dieser Schritt?*  
Das Speichern finalisiert die Änderungen im Speicher. Öffnet man die resultierende `.docx` in Microsoft Word, ist kein Bild sichtbar, und der PDF‑Export bestätigt, dass die Form im Druck nicht erscheint.

## Vollständiges, ausführbares Beispiel

Alles zusammengeführt, hier das komplette Programm, das Sie kompilieren und ausführen können:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Erwartete Ausgabe**

* Öffnet man `HiddenImageDocument.docx` in Microsoft Word, wird kein Bild angezeigt.
* Der Export oder das Drucken des Dokuments (bzw. das Öffnen der PDF) zeigt ebenfalls kein Bild.
* Die versteckte Form existiert weiterhin im XML des Dokuments, was Sie prüfen können, indem Sie die `.docx` als ZIP öffnen und `word/document.xml` inspizieren – Sie sehen ein `<w:pict>`‑Element mit `w:hidden="true"`.

## Häufige Variationen und Sonderfälle

| Situation | Was zu tun ist | Warum es wichtig ist |
|-----------|----------------|----------------------|
| **Bilddatei fehlt** | `InsertImage` in ein `try/catch` einbetten und `FileNotFoundException` behandeln. | Verhindert, dass die Anwendung abstürzt, und ermöglicht ein klares Fehlermeldungs‑Logging. |
| **Mehrere versteckte Formen** | Für jede eingefügte `Shape` `picture.Hidden = true` setzen oder über `doc.GetChildNodes(NodeType.Shape, true)` iterieren. | Stellt sicher, dass jedes unerwünschte visuelle Element unsichtbar bleibt. |
| **Form nur im Bearbeitungsmodus sichtbar** | Nach dem Bearbeiten `picture.Hidden = false` setzen und vor dem Speichern wieder zurückschalten. | Ermöglicht die Arbeit mit der Form in der UI, während das Endergebnis sauber bleibt. |
| **Drucken in älteren Word‑Versionen** | Das Dokument mit Word 2010 oder neuer prüfen; das hidden‑Flag wird von allen modernen Versionen unterstützt. | Gewährleistet Kompatibilität für Ihre Benutzerbasis. |
| **Anderes Dateiformat verwenden (z. B. direkt PDF)** | Das `Hidden`‑Flag funktioniert identisch; Aspose.Words respektiert es bei der PDF‑Konvertierung. | Bestätigt, dass **prevent shape from printing** für alle Exportziele funktioniert. |

## Profi‑Tipp: Das hidden‑Flag programmgesteuert prüfen

Falls Sie vor dem Speichern bestätigen möchten, dass eine Form versteckt ist, können Sie die Eigenschaft inspizieren:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Diese einfache Prüfung ist in automatisierten Pipelines hilfreich, in denen die Einhaltung von Dokument‑Generierungs‑Richtlinien garantiert werden muss.

## Fazit

Sie wissen jetzt, wie Sie die **shape hidden‑Eigenschaft** in Aspose.Words für C# setzen. Durch das Einfügen eines Bildes, das Anwenden von `picture.Hidden = true` und das Speichern des Dokuments bleibt die Form aus der UI und erscheint nie im Druck. Diese Technik ist unverzichtbar, wenn Sie Platzhalter, Wasserzeichen oder Branding‑Elemente benötigen, die für Endbenutzer unsichtbar bleiben sollen.

### Was kommt als Nächstes?

* Erkunden Sie weitere Form‑Eigenschaften wie `picture.WrapType`, `picture.Rotation` und `picture.RelativeHorizontalPosition`.
* Lernen Sie, wie Sie **shape in Aspose.Words** bedingt basierend auf Benutzereingaben oder Konfiguration verbergen.
* Kombinieren Sie versteckte Formen mit **insert image into document**‑Schleifen, um dynamische, unsichtbare Marker für die spätere Verarbeitung zu erzeugen (z. B. Mail‑Merge‑Felder).

Experimentieren Sie gern mit verschiedenen Bildformaten, Dokument‑Layouts und Exportzielen. Das Verbergen von Formen gibt Ihnen feinkörnige Kontrolle darüber, was Ihre Leser tatsächlich sehen – und was im Hintergrund bleibt. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungs‑Ansätze in Ihren Projekten erkunden können.

- [Rechteckige Form in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET hinzufügen](/words/english/net/working-with-shapes/add-group-shape/)
- [Inline‑Bild in Word‑Dokument mit Aspose.Words einfügen](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}