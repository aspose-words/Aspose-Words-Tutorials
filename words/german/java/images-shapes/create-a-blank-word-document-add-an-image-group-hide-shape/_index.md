---
category: general
date: 2026-10-10
description: Erstellen Sie ein leeres Word‑Dokument, fügen Sie ein Bild in Word ein,
  fügen Sie eine Bildgruppe hinzu und blenden Sie die Form in der gespeicherten Datei
  aus. Befolgen Sie diese Schritt‑für‑Schritt‑Anleitung.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert image into word
- add image group
- hide shape word document
language: de
lastmod: 2026-10-10
og_description: Erstellen Sie ein leeres Word‑Dokument, fügen Sie ein Bild in Word
  ein, erstellen Sie eine Bildgruppe und blenden Sie die Form aus. Dieser Leitfaden
  zeigt den vollständigen C#‑Code.
og_image_alt: Screenshot of a blank Word document with a hidden image group
og_title: Erstelle ein leeres Word‑Dokument, füge eine Bildgruppe hinzu, blende die
  Form aus.
schemas:
- author: Aspose
  dateModified: '2026-10-10'
  description: Create a blank Word document, insert image into Word, add an image
    group, and hide shape in the saved file. Follow this step‑by‑step guide.
  headline: Create a blank Word document, add an image group, hide shape
  type: TechArticle
tags:
- Word automation
- Aspose.Words
- C#
- Document processing
title: Erstelle ein leeres Word‑Dokument, füge eine Bildgruppe hinzu, verstecke die
  Form
url: /de/java/images-shapes/create-a-blank-word-document-add-an-image-group-hide-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines leeren Word‑Dokuments, Hinzufügen einer Bildgruppe, Ausblenden einer Form

Wenn Sie ein **leeres Word‑Dokument erstellen** und später visuelle Elemente ausblenden möchten, zeigt Ihnen dieses Tutorial genau, wie das geht. Sie lernen, ein Bild in Word einzufügen, eine Bildgruppe hinzuzufügen und eine Form im Word‑Dokument auszublenden – alles in einer einzigen wiederverwendbaren C#‑Routine.

Wir verwenden die Aspose.Words for .NET‑Bibliothek, mit der Sie .docx‑Dateien manipulieren können, ohne dass Microsoft Word installiert sein muss. Am Ende dieser Anleitung besitzen Sie ein ausführbares Programm, das eine Word‑Datei mit einer versteckten Bildgruppe erzeugt, bereit für nachgelagerte Verarbeitung oder bedingte Anzeige.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
- Aspose.Words for .NET NuGet‑Paket (`Install-Package Aspose.Words`)
- Ein Ordner auf der Festplatte, in dem Sie eine Bilddatei lesen und das Ausgabedokument schreiben können
- Grundlegende Kenntnisse in C# und Visual Studio (oder einer anderen IDE Ihrer Wahl)

## Erstellen eines leeren Word‑Dokuments mit Aspose.Words

Der erste Schritt ist, ein **leeres Word‑Dokument zu erstellen**. Aspose.Words stellt die Klasse `Document` bereit, die eine Word‑Datei im Speicher repräsentiert. Wird sie ohne Argumente instanziiert, erhalten Sie ein leeres Dokument, das bereit für Inhalte ist.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document doc = new Document();                 // blank .docx container
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist:* Der Start mit einem leeren Dokument stellt sicher, dass keine versteckten Formatierungen oder Restabschnitte das später hinzuzufügende Shape beeinträchtigen.

## Bild in Word einfügen mit DocumentBuilder

Als Nächstes **fügen wir ein Bild in Word ein**, indem wir zuerst ein Group‑Shape erstellen, das das Bild aufnehmen soll. Group‑Shapes ermöglichen es, mehrere Zeichenobjekte als eine Einheit zu behandeln – praktisch, wenn Sie sie später gemeinsam ausblenden oder verschieben möchten.

```csharp
        // Step 2: Insert a group shape with the desired size (width: 300, height: 200)
        GroupShape group = builder.InsertGroupShape(300, 200);
```

Die Methode `InsertGroupShape` erzeugt einen leeren Container. Die Abmessungen werden in Punkten angegeben (1 Punkt = 1/72 Zoll). Passen Sie die Größe an die Auflösung des Bildes an, das Sie einbetten wollen.

## Bildgruppe zum Dokument hinzufügen

Jetzt **fügen wir die Bildgruppe hinzu**, indem wir den Cursor des Builders in die neu erstellte Gruppe bewegen und das Bild einfügen. Alle nachfolgenden Einfügungen werden Teil der Gruppe sein.

```csharp
        // Step 3: Position the builder inside the group so subsequent inserts go into it
        builder.MoveTo(group);

        // Step 4: Add an image to the group shape
        // Replace the path with the actual location of your PNG/JPEG file
        builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");
```

*Tipp:* Verwenden Sie einen absoluten Pfad oder einen korrekt escaped relativen Pfad; andernfalls wirft `InsertImage` eine `FileNotFoundException`.

## Form in einem Word‑Dokument ausblenden

Schließlich **blenden wir die Form im Word‑Dokument aus**, indem wir die Eigenschaft `Hidden` der Gruppe auf `true` setzen. Versteckte Shapes werden beim Öffnen des Dokuments in Word nicht angezeigt, bleiben aber in der Datei erhalten und können später programmgesteuert wieder sichtbar gemacht werden.

```csharp
        // Step 5: Hide the entire group (the image will not be visible in the saved document)
        group.Hidden = true;

        // Step 6: Save the document with the hidden group
        doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");
    }
}
```

Wenn Sie *GroupHidden.docx* in Microsoft Word öffnen, sehen Sie eine komplett leere Seite, weil die Bildgruppe ausgeblendet ist. Die Datei enthält weiterhin die Bilddaten, die Sie später mit `group.Hidden = false` wieder einblenden können, falls nötig.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in ein neues Konsolen‑Projekt kopieren‑und‑einfügen können:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a group shape (300 pt × 200 pt)
            GroupShape group = builder.InsertGroupShape(300, 200);

            // 3️⃣ Move inside the group so inserts become part of it
            builder.MoveTo(group);

            // 4️⃣ Insert the image (replace with your own file)
            builder.InsertImage(@"YOUR_DIRECTORY\photo1.png");

            // 5️⃣ Hide the group so the image is not shown
            group.Hidden = true;

            // 6️⃣ Save the result
            doc.Save(@"YOUR_DIRECTORY\GroupHidden.docx");

            Console.WriteLine("Document created successfully.");
        }
    }
}
```

**Erwartete Ausgabe**

- Eine Datei namens `GroupHidden.docx` erscheint in `YOUR_DIRECTORY`.
- Beim Öffnen der Datei in Word wird eine leere Seite angezeigt.
- Das versteckte Bild kann durch Ändern von `group.Hidden = false` und erneutem Speichern wieder sichtbar gemacht werden.

## Häufige Varianten und Sonderfälle

| Situation | Wie der Code anzupassen ist |
|-----------|-----------------------------|
| **Mehrere Bilder** | Fügen Sie zusätzliche `InsertImage`‑Aufrufe nach `builder.MoveTo(group)` ein. Alle Bilder bleiben innerhalb derselben Gruppe und teilen das Hidden‑Flag. |
| **Verschiedene Bildformate** | Aspose.Words unterstützt PNG, JPEG, BMP, GIF, TIFF. Ändern Sie einfach die Dateierweiterung; ein Code‑Änderung ist nicht nötig. |
| **Bedingte Sichtbarkeit** | Speichern Sie eine benutzerdefinierte Dokumentvariable (`doc.Variables.Add("ShowImages", "true")`) und schalten Sie `group.Hidden` zur Laufzeit basierend auf deren Wert um. |
| **Große Dokumente** | Erzeugen Sie die Gruppe auf einer bestimmten Seite (`builder.InsertBreak(BreakType.PageBreak)`) bevor Sie die Gruppe einfügen, um Layout‑Verschiebungen zu vermeiden. |
| **Kompatibilität mit älteren Word‑Versionen** | Speichern Sie als `doc.Save("output.doc", SaveFormat.Doc)`, wenn Sie das Legacy‑`.doc`‑Format benötigen; versteckte Shapes verhalten sich identisch. |

**Pro‑Tipp:** Setzen Sie `group.Hidden = true` immer **nach** dem Einfügen aller Kind‑Elemente. Das Setzen des Flags vor dem Hinzufügen von Inhalten kann dazu führen, dass einige Elemente in älteren Word‑Versionen unerwartet gerendert werden.

## Fazit

Sie wissen nun, wie Sie **ein leeres Word‑Dokument erstellen**, **ein Bild in Word einfügen**, **eine Bildgruppe hinzufügen** und **eine Form im Word‑Dokument ausblenden** mit Aspose.Words for .NET. Das vollständige Beispiel demonstriert jeden Schritt von der Initialisierung des Dokuments bis zum Speichern einer Datei, die eine versteckte Bildgruppe enthält.

Als Nächstes könnten Sie:

- Textfelder oder Diagramme zur gleichen Gruppe hinzufügen
- `DocumentBuilder.StartBookmark` / `EndBookmark` verwenden, um versteckte Abschnitte zu markieren
- Die Sichtbarkeit programmgesteuert basierend auf Benutzereingaben oder Dokumentvariablen umschalten

Experimentieren Sie gern mit verschiedenen Shapes, Größen und Sichtbarkeitsregeln, um Ihr Automatisierungsszenario optimal zu unterstützen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with Floating Image in .NET](/words/english/net/add-content-using-documentbuilder/insert-floating-image/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}