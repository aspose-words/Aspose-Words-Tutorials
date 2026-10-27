---
category: general
date: 2026-10-23
description: Erstellen Sie ein leeres Word‑Dokument, fügen Sie eine Rechteckform hinzu
  und blenden Sie die Form in Word mit Aspose.Words aus. Schritt‑für‑Schritt‑Code
  für .NET‑Entwickler.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: de
lastmod: 2026-10-23
og_description: Erstellen Sie ein leeres Word‑Dokument, fügen Sie eine Rechteckform
  hinzu und blenden Sie die Form in Word mit Aspose.Words aus. Folgen Sie dem vollständigen
  C#‑Beispiel.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Erstelle ein leeres Word‑Dokument und füge eine versteckte Rechteckform
  hinzu
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Ein leeres Word‑Dokument erstellen und eine Rechteckform hinzufügen
url: /de/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen Sie ein leeres Word-Dokument und fügen Sie eine Rechteckform hinzu

Wenn Sie **ein leeres Word-Dokument erstellen** müssen, zeigt Ihnen dieses Handbuch, wie Sie dies mit Aspose.Words für .NET tun. Sie lernen außerdem **wie man eine Form einfügt** – speziell ein Rechteck – und **wie man die Form im Word ausblendet**, sodass sie das Layout nicht beeinflusst.

Das Tutorial führt Sie durch jede Codezeile, erklärt, warum jeder Schritt wichtig ist, und behandelt häufige Fallstricke wie die Sichtbarkeit versteckter Formen in verschiedenen Word‑Ansichtsmodi. Am Ende haben Sie eine voll funktionsfähige `.docx`‑Datei, die eine versteckte Rechteckform enthält, die Sie später programmgesteuert einblenden oder manipulieren können.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
- Aspose.Words für .NET NuGet-Paket (`Install-Package Aspose.Words`)
- Eine Entwicklungsumgebung wie Visual Studio 2022 oder VS Code mit C#‑Erweiterungen
- Grundlegende Kenntnisse der C#‑Syntax und von Word‑Dokumentkonzepten

Eine zusätzliche Office-Installation ist nicht erforderlich, da Aspose.Words vollständig im Speicher arbeitet.

## Erstellen Sie ein leeres Word-Dokument

Der erste Schritt besteht darin, ein leeres `Document`‑Objekt zu instanziieren. Dieses Objekt stellt eine Word‑Datei dar, die noch keine Abschnitte, Absätze oder Inhalte enthält.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Warum das wichtig ist:**  
Ein leeres `Document` bietet Ihnen eine saubere Leinwand. Wenn Sie von einer vorhandenen Vorlage ausgehen, könnten versteckte Formen unerwünschte Formatierungen übernehmen. Ein Neubeginn stellt sicher, dass die Rechteckform, die Sie später hinzufügen, der einzige von Ihnen gesteuerte Inhalt ist.

## Fügen Sie dem Dokument eine Rechteckform hinzu

Als Nächstes benötigen wir einen `DocumentBuilder`, um Inhalte in das Dokument einzufügen. Die Methode `InsertShape` des Builders ist der Standardweg, **Formen einzufügen**, wie Rechtecke, Kreise oder benutzerdefinierte Zeichnungen.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Warum das wichtig ist:**  
`InsertShape` gibt ein `Shape`‑Objekt zurück, das Sie weiter konfigurieren können (Farbe, Linienstil usw.). Die Abmessungen werden in Punkten angegeben (1 Punkt = 1/72 Zoll), was dem internen Messsystem von Word entspricht.

### Optional: Rechteck formatieren (optional)

Wenn Sie möchten, dass das Rechteck beim späteren Einblenden einen sichtbaren Rand hat, können Sie dessen Linienstärke und Farbe festlegen:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Diese Zeilen sind optional, da die Form im nächsten Schritt ausgeblendet wird.

## Form in Word ausblenden

Word ermöglicht es, Formen aus dem Layout zu verbergen, während sie weiterhin Teil des Objektmodells des Dokuments bleiben. Das Setzen der Eigenschaft `Hidden` auf `true` macht die Form in der normalen Ansicht unsichtbar, lässt sie aber über die API auswählbar.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Warum das wichtig ist:**  
Eine versteckte Form ist nützlich, um Metadaten, Platzhalter für die spätere Verarbeitung oder bedingte Inhalte zu speichern, die Sie nur unter bestimmten Umständen einblenden (z. B. beim Erstellen eines Abschlussberichts). Die Form bleibt in der Datei, sodass Sie sie programmgesteuert später mit `rectangleShape.Hidden = false;` wieder einblenden können.

## Dokument speichern

Abschließend schreiben Sie das Dokument auf die Festplatte. Die Dateierweiterung bestimmt das Word‑Format; `.docx` ist das moderne Open‑XML‑Format.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Ergebnis:**  
Wenn Sie `HiddenShape.docx` in Microsoft Word öffnen, wird eine ansonsten leere Seite angezeigt. Das Rechteck ist nicht sichtbar, aber wenn Sie zu **Start → Auswählen → Auswahlbereich** gehen, sehen Sie die aufgeführte Form und können deren Sichtbarkeit umschalten.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette Programm, das Sie kopieren, einfügen und ausführen können. Es enthält alle erforderlichen `using`‑Anweisungen und Kommentare.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Erwartete Ausgabe:**  

- Die Konsole gibt den Speicherort aus.  
- `HiddenShape.docx` öffnet sich als leere Seite in Word.  
- Die Rechteckform existiert, ist jedoch ausgeblendet; Sie können sie über den *Auswahlbereich* überprüfen oder indem Sie programmgesteuert `Hidden = false` setzen und die Datei erneut öffnen.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich andere Formtypen ausblenden?** | Ja. Jede `Shape` (z. B. `ShapeType.Ellipse`, `ShapeType.Picture`) unterstützt die Eigenschaft `Hidden`. |
| **Vergrößert die versteckte Form die Dateigröße?** | Der Anstieg ist vernachlässigbar (einige Kilobytes), da die Formdaten als XML im `.docx`‑Paket gespeichert werden. |
| **Was, wenn die Form nur in der Druckansicht erscheinen soll?** | Verwenden Sie die Eigenschaft `Shape.IsPrint` anstelle von `Hidden`. Das Setzen von `IsPrint = false` blendet die Form aus dem Druckausgang aus, lässt sie jedoch auf dem Bildschirm sichtbar. |
| **Wie kann man die Form später wieder einblenden?** | Laden Sie das Dokument, finden Sie die Form (z. B. über `Shape.Name`), setzen Sie dann `shape.Hidden = false;` und speichern Sie. |
| **Funktioniert das mit dem .doc (binären) Format?** | Ja, Aspose.Words kann mit `document.Save("file.doc");` im `.doc`‑Format speichern. Das versteckte Flag wird beibehalten. |

## Profi‑Tipps

- **Benennen Sie Ihre Formen**: `rectangleShape.Name = "PlaceholderRectangle";` erleichtert das spätere Auffinden über `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Batch‑Verarbeitung**: Wenn Sie vielen Dokumenten versteckte Formen hinzufügen müssen, verpacken Sie den Code in einer Methode und verwenden Sie die `DocumentBuilder`‑Instanz erneut.
- **Performance**: Das Erstellen einer Form ist kostengünstig, aber das häufige Speichern großer Dokumente kann I/O‑gebunden sein. Erwägen Sie die Verwendung von `MemoryStream` für die Zwischenspeicherung.

## Fazit

Sie wissen jetzt, wie Sie mit Aspose.Words für .NET **ein leeres Word-Dokument erstellen**, **eine Rechteckform hinzufügen** und **die Form im Word ausblenden**. Diese Technik ermöglicht es Ihnen, unsichtbare Platzhalter einzubetten, die Sie später einblenden oder manipulieren können – ein Muster, das für die dynamische Berichtserstellung, bedingte Inhalte und Dokumentvorlagen nützlich ist.

Nächste Schritte, die Sie erkunden könnten:

- Ersetzen Sie das Rechteck durch ein Bild oder Diagramm mit `ShapeType.Picture`.
- Verwenden Sie **how to insert shape** in Kopf‑/Fußzeilen für Wasserzeichen‑artige Platzhalter.
- Kombinieren Sie versteckte Formen mit **add rectangle shape**‑basierter Datenvalidierung (z. B. JSON im `AlternativeText`‑Eigenschaft einer Form speichern).

Viel Spaß beim Programmieren und fühlen Sie sich frei, mit anderen Formtypen und Sichtbarkeitsoptionen zu experimentieren, um Ihre Dokumenten‑Automatisierungsanforderungen zu erfüllen!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Handbuch gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word-Dokument erstellen – Wie man eine Rechteckform und einen Schatten hinzufügt](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Gruppenform in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Ein leeres Word-Dokument mit einer versteckten Ellipsenform erstellen – Vollständiger C#‑Leitfaden](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}