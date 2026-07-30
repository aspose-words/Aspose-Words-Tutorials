---
category: general
date: 2025-12-29
description: Erstellen Sie eine Rechteckform in einem Word‑Dokument mit Aspose.Words
  C#. Erfahren Sie, wie Sie die Transparenz der Form festlegen, die Schattenfarbe
  einstellen und das Word‑Dokument mühelos speichern.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: de
og_description: Erstellen Sie ein Rechteck in einem Word-Dokument mit Aspose.Words
  C#. Dieser Leitfaden zeigt, wie Sie die Transparenz der Form festlegen, die Schattenfarbe
  einstellen und das Word-Dokument speichern.
og_title: Rechteckform in Word erstellen – Vollständiges Aspose.Words‑Tutorial
tags:
- Aspose.Words
- C#
- Word Automation
title: Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Word erstellen – Vollständiges Aspose.Words Tutorial

Haben Sie jemals **Rechteckform erstellen** in einem Word-Dokument benötigen, aber wussten nicht, wo Sie anfangen sollen? Sie sind nicht allein; viele Entwickler stoßen auf dieses Problem, wenn sie Berichte oder Rechnungen automatisieren. In diesem Leitfaden gehen wir die genauen Schritte durch, um eine Rechteckform zu erstellen, die Transparenz der Form festzulegen, die Schattenfarbe zu setzen und schließlich **Word-Dokument speichern** mit Aspose.Words für .NET.

Wir behandeln alles vom initialen Dokumentobjekt bis zur finalen `.docx`-Datei auf der Festplatte, sodass Sie am Ende **Word-Dokument programmatisch erstellen** können, ohne zu raten. Keine externen Referenzen, nur eine eigenständige Lösung, die Sie in Ihr Projekt kopieren‑einfügen können.

## Voraussetzungen

- .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.7+)
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`)
- Grundlegende Vertrautheit mit C#‑Syntax
- Eine IDE Ihrer Wahl (Visual Studio, Rider, VS Code usw.)

> **Pro Tipp:** Wenn Sie eine kostenlose Testversion von Aspose.Words verwenden, fügt die Bibliothek dem Ausgabedokument ein Wasserzeichen hinzu. Für die Produktion benötigen Sie eine gültige Lizenz.

## Schritt 1: Dokument und Builder initialisieren

Das erste, was wir tun, ist ein neues, leeres Word-Dokument und einen `DocumentBuilder` zu erstellen, der es uns ermöglicht, Inhalte einzuf. Denken Sie an den Builder wie an einen virtuellen Stift, der auf der Seite zeichnet.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Warum das wichtig ist:** Ohne einen `DocumentBuilder` müssten Sie den Low‑Level‑Knotenbaum direkt manipulieren, was fehleranfällig und schwerer zu lesen ist.

## Schritt 2: Rechteckform erstellen

Jetzt erstellen wir tatsächlich **eine Rechteckform**. Die Methode `InsertShape` nimmt ein `ShapeType`‑Enum, Breite und Höhe (in Punkten) entgegen. Das zurückgegebene `Shape`‑Objekt ermöglicht es uns, später visuelle Eigenschaften anzupassen.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Zu diesem Zeitpunkt ist das Rechteck ein durchgehend schwarzer Kasten, der am aktuellen Absatz verankert ist. Sie können es verschieben, die Größe ändern oder bei Bedarf später sogar drehen.

![Rechteckform mit Schatten in einem Word-Dokument](/images/rectangle-shadow.png "Ein Word-Dokument, das eine Rechteckform mit einem grauen Schatten zeigt")

*Bild‑Alt‑Text: Rechteckform mit Schatten in einem Word-Dokument*

## Schritt 3: Transparenz der Form festlegen

Transparenz ist der „Durchsichtigkeit“-Grad der Füllung der Form. Aspose.Words verwendet eine `Transparency`‑Eigenschaft, die von `0.0` (undurchsichtig) bis `1.0` (vollständig transparent) reicht. Hier **setzen wir die Transparenz der Form** auf 40 %, damit der darunterliegende Text lesbar bleibt.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Randfall:** Wenn Sie eine völlig unsichtbare Form benötigen, aber dennoch den Schatten anzeigen möchten, setzen Sie `Transparency` auf `1.0` und geben der Form eine nicht‑null Konturbreite.

## Schritt 4: Schatten konfigurieren

Ein dezenter Drop‑Shadow verleiht Tiefe. Wir werden **die Schattenfarbe** auf ein mittleres Grau setzen, den Unschärferadius anpassen und ihn sowohl horizontal als auch vertikal um einige Punkte versetzen.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Warum das wichtig ist:** Ein zu scharfer oder zu dunkler Schatten kann wie ein Druckfehler aussehen. Passen Sie `Blur` und `Transparency` an, bis es natürlich wirkt.

## Schritt 5: Word-Dokument speichern

Schließlich **speichern wir das Word-Dokument** auf der Festplatte. Die Methode `Save` ermittelt das Dateiformat automatisch anhand der Erweiterung; `.docx` ist das moderne OpenXML‑Format.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Falls der Ordner nicht existiert, wirft Aspose.Words eine `ArgumentException`. Stellen Sie sicher, dass der Pfad gültig ist, oder erstellen Sie das Verzeichnis vorher.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort ausführbare Programm, das alle Schritte zusammenführt. Kopieren Sie dies in ein neues Konsolenprojekt und drücken Sie **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Erwartetes Ergebnis

Öffnen Sie `ShadowRectangle.docx` in Microsoft Word. Sie sollten ein hellgraues Rechteck mit einem weichen, leicht versetzten Schatten sehen, beide mit 40 % Transparenz gerendert. Die Form befindet sich auf einer leeren Seite, bereit für zusätzlichen Inhalt.

## Häufige Fragen & Variationen

**Was, wenn ich eine andere Form benötige?**  
Ersetzen Sie `ShapeType.Rectangle` durch einen anderen Enum‑Wert (`Ellipse`, `Triangle`, `Star` usw.). Der Rest des Codes bleibt unverändert.

**Kann ich die Konturfarbe ändern?**  
Ja – verwenden Sie `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` und setzen Sie optional `rectangleShape.StrokeWeight = 1.5;`.

**Wie platziere ich die Form an einer bestimmten Position auf der Seite?**  
Setzen Sie `rectangleShape.WrapType = WrapType.None;` und passen Sie dann die Eigenschaften `rectangleShape.Left` und `rectangleShape.Top` an (Werte in Punkten).

**Ist es möglich, Text in das Rechteck einzufügen?**  
Absolut. Nach dem Erstellen der Form können Sie `rectangleShape.AppendChild(new Paragraph(document))` aufrufen und anschließend einen `Run` mit Ihrem Text hinzufügen. Denken Sie daran, die `rectangleShape.TextBox`‑Eigenschaften zu setzen, wenn Sie eine umfangreichere Formatierung wünschen.

## Pro‑Tipps & Fallstricke

- **Lizenz frühzeitig:** Wenn Sie vergessen, eine Lizenz anzuwenden, fügt Aspose.Words ein Wasserzeichen auf der ersten Seite ein, was beim Testen verwirrend sein kann.
- **Performance‑Tipp:** Beim Erzeugen vieler Dokumente in einer Schleife verwenden Sie eine einzelne `Document`‑Instanz und rufen nach jedem Speichern `document.RemoveAllChildren();` auf, um übermäßigen GC‑Druck zu vermeiden.
- **Schatten‑Sichtbarkeit:** Auf Bildschirmen mit niedriger Auflösung kann ein dezenter Schatten unsichtbar erscheinen. Erhöhen Sie `Blur` oder `OffsetX/Y` zum Debuggen und reduzieren Sie es anschließend für die Produktion.

## Nächste Schritte

Jetzt, da Sie wissen, wie man **eine Rechteckform erstellt**, **die Transparenz der Form festlegt**, **die Schattenfarbe setzt** und **das Word-Dokument speichert**, sollten Sie das Tutorial erweitern:

- Mehrere Formen hinzufügen und gruppieren.
- Das Rechteck in eine Tabellenzelle einfügen für ein Berichtslayout.
- Die Form mit `DocumentBuilder.InsertHtml` kombinieren, um HTML‑gestylten Inhalt zu überlagern.
- Andere visuelle Effekte wie `Glow` oder `Reflection` erkunden für reichhaltigere UI‑ähnliche Dokumente.

Experimentieren Sie, brechen Sie Dinge und verfeinern Sie anschließend – die programmgesteuerte Dokumentenerstellung ist ein Spielplatz, an dem visuelles Design auf Code trifft.

---

*Viel Spaß beim Coden! Wenn Sie auf Probleme stoßen, hinterlassen Sie unten einen Kommentar und wir helfen Ihnen gemeinsam weiter.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}