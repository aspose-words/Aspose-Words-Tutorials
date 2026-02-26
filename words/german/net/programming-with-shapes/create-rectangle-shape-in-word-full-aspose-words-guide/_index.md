---
category: general
date: 2026-02-26
description: Erstellen Sie ein Rechteck in Word mit Aspose.Words und lernen Sie, wie
  Sie eine Form zu Word hinzufügen, ihr einen Schatten zuweisen und die Transparenz
  der Form in wenigen Minuten einstellen.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: de
og_description: Erstellen Sie ein Rechteck in Word mit Aspose.Words. Lernen Sie, wie
  Sie eine Form zu Word hinzufügen, einen Schatten auf die Form anwenden und die Transparenz
  der Form schnell einstellen.
og_title: Rechteckform in Word erstellen – Vollständige Aspose.Words-Anleitung
tags:
- Aspose.Words
- C#
- Word Automation
title: Rechteckform in Word erstellen – Vollständiger Aspose.Words-Leitfaden
url: /de/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

unchanged.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Word erstellen – Vollständige Aspose.Words-Anleitung

Haben Sie jemals **eine Rechteckform** in einem Word‑Dokument erstellen müssen, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein – viele Entwickler stoßen dabei auf Schwierigkeiten, wenn sie Berichte oder Rechnungen automatisieren. In diesem Tutorial führen wir Sie durch ein komplettes, sofort ausführbares Beispiel, das zeigt, wie Sie **eine Form zu Word hinzufügen**, einen dezenten Schatten anwenden und die Transparenz der Form steuern, alles mit Aspose.Words für .NET.

Am Ende der Anleitung haben Sie eine `.docx`‑Datei, die ein sauberes Rechteck mit einem eleganten Schatten enthält – perfekt für Branding, Hervorhebungen oder einfach, um Ihr Dokument etwas professioneller wirken zu lassen. Keine externen Werkzeuge nötig, nur ein paar Zeilen C#.

## Was Sie benötigen

- **Aspose.Words für .NET** (die neueste Version ab Anfang 2026). Sie können es von NuGet holen (`Install-Package Aspose.Words`).
- Eine .NET‑Entwicklungsumgebung (Visual Studio, Rider oder VS Code mit der C#‑Erweiterung).
- Grundlegende Kenntnisse der C#‑Syntax – nichts Besonderes, nur die üblichen `using`‑Anweisungen und Objektinstanziierungen.

Wenn Sie das bereits haben, großartig – lassen Sie uns loslegen.

## Rechteckform erstellen – Kernschritte

Unten finden Sie den vollständigen Quellcode. Kopieren Sie ihn in ein neues Konsolenprojekt, drücken Sie **F5**, und Sie sehen `ShadowDemo.docx` im von Ihnen angegebenen Ordner erscheinen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Warum das funktioniert

- **`Document`** ist der Einstiegspunkt; es repräsentiert die gesamte Word‑Datei.
- **`Shape`** mit `ShapeType.Rectangle` teilt Aspose mit, dass wir ein rechteckiges Zeichenobjekt wollen.
- Durch das Setzen von **`Width`** und **`Height`** erhält die Form eine feste Größe; andernfalls wird ein winziger Platzhalter verwendet.
- Das **`Shadow`**‑Objekt ermöglicht es uns, jeden visuellen Aspekt fein abzustimmen: Unschärfe, Abstand, Richtung, Farbe, Transparenz und Ausdehnung. Das ist das Herzstück von *apply shadow to shape*.
- Schließlich fügt **`AppendChild`** die Form in den ersten Absatz des Dokuments ein, was die einfachste Methode ist, *add shape to Word* zu realisieren, ohne Tabellen oder Kopf‑/Fußzeilen zu verwenden.

Wenn Sie `ShadowDemo.docx` öffnen, sehen Sie ein graues Rechteck, das bequem im Dokument sitzt, sein Schatten schräg nach unten‑rechts in einem 45°‑Winkel. Der Schatten ist kein fester Block; der Unschärferadius mildert die Kanten, und die Transparenz lässt ihn wie einen natürlichen Fall‑Schatten wirken, statt einer harten Überlagerung.

![Beispiel für das Erstellen einer Rechteckform](image.png "Rechteckform mit Schatten in Word erstellen mit Aspose.Words")

*(Das obige Bild zeigt das Endergebnis des Code‑Snippets.)*

## Form zu Word‑Dokument hinzufügen – Platzierungsoptionen

Das Beispiel verwendet den **ersten Absatz**, weil es der schnellste Weg ist, etwas auf dem Bildschirm zu sehen. In realen Szenarien möchten Sie vielleicht:

- Die Form in einen bestimmten **Abschnitt** oder **Kopf‑/Fußzeile** einfügen.
- Sie in einer **Tabellenzelle** platzieren, um sie mit tabellarischen Daten auszurichten.
- Sie mit **Textumbruch**‑Optionen (z. B. `WrapType.Square`) umwickeln, sodass umliegender Text um das Rechteck fließt.

Hier ist eine schnelle Variante, die die Form in einen neuen Absatz mit einem benutzerdefinierten Stil einfügt:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Pro‑Tipp:* Fügen Sie die Form immer **nach** der Konfiguration ihrer Eigenschaften hinzu; andernfalls müssen Sie möglicherweise `UpdateLayout` aufrufen, um das visuelle Erscheinungsbild zu aktualisieren.

## Schatten auf Form anwenden – Feineinstellung des Aussehens

Schatten können das Aussehen eines Dokuments dramatisch verändern. Die Klasse `Shadow` stellt mehrere Eigenschaften bereit:

| Eigenschaft   | Was es steuert                                      | Typische Werte |
|---------------|-----------------------------------------------------|----------------|
| `BlurRadius`  | Weichheit der Schattenkanten                        | 2.0 – 10.0      |
| `Distance`    | Wie weit der Schatten von der Form versetzt ist     | 1.0 – 8.0       |
| `Direction`   | Winkel in Grad (0 = links, 90 = oben)               | 0 – 360         |
| `Color`       | Schattenfarbe (beliebiges `System.Drawing.Color`)  | Gray, Black, Custom |
| `Transparency`| Deckkraft (0 = vollständig undurchsichtig, 1 = unsichtbar) | 0.0 – 0.5       |
| `Spread`      | Ausdehnung des Schattens, bevor die Unschärfe angewendet wird | 0.0 – 1.0       |

Wenn Sie ein **subtiles, professionelles Aussehen** wünschen, halten Sie `BlurRadius` bei etwa 4‑6 und `Transparency` bei etwa 0,2, genau wie im obigen Code. Für einen **dramatischen Effekt** erhöhen Sie `Distance` auf 6, setzen `Direction` auf 135° und reduzieren `Transparency` auf 0,05.

## Form‑Transparenz und Schatten‑Ausdehnung festlegen

Transparenz betrifft nicht nur den Schatten; Sie können das Rechteck selbst ebenfalls teilweise durchsichtig machen:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Die Kombination einer halbtransparenten Füllung mit einem weichen Schatten erzeugt häufig ein modernes UI‑Gefühl – ideal für Dashboards oder Design‑Mock‑Ups, die in Berichten eingebettet sind.

### Sonderfälle, die beachtet werden sollten

1. Ältere Word‑Versionen (vor 2007) unterstützen einige Schatten‑Eigenschaften nicht. Wenn Sie `.doc`‑Dateien anvisieren, sollten Sie den Schatten vereinfachen (z. B. `BlurRadius` auf 0 setzen).
2. High‑DPI‑Displays können den Schatten leicht anders rendern. Testen Sie in der Zielumgebung, wenn die visuelle Treue kritisch ist.
3. Überlappende Formen – Aspose rendert Schatten in der Reihenfolge, in der sie hinzugefügt werden. Fügen Sie Formen von hinten nach vorne ein, um unerwünschte Überdeckungen zu vermeiden.

## Ergebnis speichern und überprüfen

Die Methode `Document.Save` erkennt das Ausgabeformat automatisch anhand der Dateierweiterung. Für eine **`.docx`**‑Datei erhalten Sie das Open‑XML‑Format, das die meisten modernen Textverarbeitungsprogramme verstehen. Wenn Sie eine **PDF**‑Version mit derselben visuellen Gestaltung benötigen, ändern Sie einfach die Erweiterung:

```csharp
document.Save("ShadowDemo.pdf");
```

Das Öffnen des erzeugten `ShadowDemo.docx` (oder `ShadowDemo.pdf`) sollte ein sauberes **Rechteck mit Schatten** zeigen und bestätigen, dass Sie erfolgreich *create rectangle shape* und *apply shadow to shape* mit Aspose.Words umgesetzt haben.

## Häufig gestellte Fragen

**Q: Kann ich eine andere Form verwenden, z. B. eine Ellipse?**  
A: Absolut. Ersetzen Sie `ShapeType.Rectangle` durch `ShapeType.Ellipse` (oder irgendeinen anderen `ShapeType`‑Enum). Die Schatten‑Eigenschaften bleiben gleich.

**Q: Was, wenn das Rechteck anklickbar sein soll?**  
A: Sie können der Form einen Hyperlink zuweisen:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: Funktioniert das unter .NET 6+?**  
A: Ja. Aspose.Words 23.11 und höher unterstützen .NET 6, .NET 7 und .NET 8 vollständig. Verweisen Sie einfach auf das passende NuGet‑Paket.

**Q: Wie ändere ich die Schattenfarbe, um sie an meine Marke anzupassen?**  
A: Verwenden Sie beliebige `System.Drawing.Color`, die Ihnen gefällt:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Fazit

Wir haben alles behandelt, was Sie benötigen, um **eine Rechteckform** in einem Word‑Dokument zu **erstellen**, **eine Form zu Word hinzuzufügen**, **einen Schatten auf die Form anzuwenden** und **die Transparenz der Form festzulegen**. Der vollständige, ausführbare Code befindet sich oben auf dieser Seite, und die Erklärungen sollten Ihnen genug Sicherheit geben, um Größen, Farben und Schattenparameter für jedes Projekt anzupassen.

Bereit für den nächsten Schritt? Probieren Sie Folgendes aus:

- Mehrere Formen übereinander stapeln für einen Abzeichen‑Effekt.
- Dynamische Größenbestimmung basierend auf dem Dokumentinhalt (z. B. Breite aus einer Tabellenspalte berechnen).
- Export des Dokuments nach PDF oder HTML, wobei der Schatten erhalten bleibt.

Hinterlassen Sie gerne einen Kommentar, wenn Sie auf Probleme stoßen, oder teilen Sie Ihre eigenen Varianten zum Thema „Rechteck mit Schatten“.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}