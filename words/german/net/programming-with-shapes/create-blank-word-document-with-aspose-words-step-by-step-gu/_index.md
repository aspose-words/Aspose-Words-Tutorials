---
category: general
date: 2026-02-23
description: Erstellen Sie ein leeres Word‑Dokument mit C# und Aspose.Words. Erfahren
  Sie, wie Sie eine Rechteckform hinzufügen, einen Schatten hinzufügen und das Word‑Dokument
  mit der Form in wenigen Minuten speichern.
draft: false
keywords:
- create blank word document
- add rectangle shape
- how to add shape
- add shadow word
- save word with shape
language: de
og_description: Erstellen Sie schnell ein leeres Word‑Dokument. Diese Anleitung zeigt,
  wie man eine Rechteckform hinzufügt, ein Wort mit Schatten hinzufügt und das Word‑Dokument
  mit der Form mithilfe von Aspose.Words speichert.
og_title: Leeres Word‑Dokument erstellen – Vollständiges C#‑Tutorial
tags:
- Aspose.Words
- C#
- Document Automation
title: Leeres Word‑Dokument mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/
---

-button >}}

All good.

Now ensure we didn't miss any markdown formatting. Keep code block placeholders unchanged.

Now produce final answer with only translated content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Leeres Word-Dokument erstellen – Vollständiges C#-Tutorial

Haben Sie sich jemals gefragt, wie man **create blank word document** programmgesteuert erstellt, ohne Microsoft Word zu öffnen? Sie sind nicht allein. In vielen Automatisierungsprojekten benötigen wir eine frische .docx‑Datei, legen eine Form darauf, geben dieser Form einen schönen Schatten und dann **save word with shape** für die spätere Verwendung.  

In diesem Leitfaden gehen wir genau das durch – beginnend mit einem leeren Dokument, **adding a rectangle shape**, Konfiguration eines **add shadow word**‑Effekts und schließlich das Persistieren der Datei. Am Ende haben Sie ein komplettes, ausführbares Snippet, das Sie in jede .NET‑Konsolenanwendung einfügen können. Kein Rätsel, keine fehlenden Teile.

## Was Sie benötigen

- **Aspose.Words for .NET** (jede aktuelle Version, z. B. 24.10).  
- .NET 6 oder höher (der Code funktioniert auch mit .NET Framework 4.7+).  
- Eine einfache C#‑IDE – Visual Studio, Rider oder sogar VS Code mit der C#‑Erweiterung.  

Das war's. Keine zusätzlichen NuGet‑Pakete außer Aspose.Words und keine Word‑Installation erforderlich.

---

## Schritt 1: Leeres Word-Dokument erstellen

Das Erste, was Sie tun, wenn Sie **create blank word document** möchten, ist die Instanziierung der Klasse `Document`. Betrachten Sie sie als eine saubere Leinwand, die Ihnen Aspose.Words zur Verfügung stellt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1 – initialize an empty document
Document document = new Document();   // this is a brand‑new, blank Word file
```

> **Warum das wichtig ist:** Das `Document`‑Objekt enthält alle Abschnitte, Absätze und Formen. Mit einer leeren Instanz zu starten, garantiert, dass Sie jedes später hinzugefügte Element kontrollieren.

---

## Schritt 2: Ein Rechteck‑Shape zum Dokument hinzufügen

Jetzt, wo wir ein sauberes Dokument haben, lassen Sie uns **add rectangle shape**. Ein Rechteck ist ein einfaches `Shape` mit `ShapeType.Rectangle`. Sie können natürlich andere Typen wählen, aber ein Rechteck eignet sich hervorragend für die Demonstration.

```csharp
// Step 2 – create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width = 200,   // width in points (≈2.78 inches)
    Height = 100   // height in points (≈1.39 inches)
};
```

> **Pro‑Tipp:** Wenn Sie sich jemals fragen, **how to add shape**, das kein Rechteck ist, ändern Sie einfach `ShapeType.Rectangle` zu einem anderen Enum‑Wert wie `ShapeType.Ellipse` oder `ShapeType.Polygon`. Der Rest des Codes bleibt unverändert.

---

## Schritt 3: Einen benutzerdefinierten Schatten für das Shape konfigurieren

Ein einfaches Rechteck wirkt etwas fade, also werden wir **add shadow word** hinzufügen, um es hervorzuheben. Aspose.Words stellt ein `ShadowFormat`‑Objekt mit vielen Eigenschaften bereit.

```csharp
// Step 3 – enable and style the shadow
rectangleShape.ShadowFormat.Enabled = true;                // turn on the shadow
rectangleShape.ShadowFormat.Color = Color.Gray;           // shadow color
rectangleShape.ShadowFormat.OffsetX = 5;                  // horizontal offset (points)
rectangleShape.ShadowFormat.OffsetY = 5;                  // vertical offset (points)
rectangleShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
rectangleShape.ShadowFormat.BlurRadius = 4;               // soft edge blur
```

> **Warum das wichtig ist:** Der Schatten verleiht einen subtilen Tiefeneindruck, besonders wenn das Dokument auf dem Bildschirm angezeigt wird. Passen Sie `OffsetX`, `OffsetY` und `BlurRadius` an, um Ihrem Design‑Stil zu entsprechen.

---

## Schritt 4: Das Shape in das Dokument einfügen

Mit dem fertigen Shape müssen wir es irgendwo platzieren. Der einfachste Ort ist der erste Absatz der ersten Sektion. Wenn das Dokument noch keinen Absatz hat, erstellt Aspose automatisch einen.

```csharp
// Step 4 – put the rectangle into the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Randfall:** Wenn Sie das Shape an einer bestimmten Stelle einfügen möchten (z. B. nach einer bestimmten Überschrift), finden Sie das Ziel‑`Paragraph` über `document.GetChildNodes(NodeType.Paragraph, true)` und verwenden Sie `InsertAfter` bzw. `InsertBefore` entsprechend.

---

## Schritt 5: Das Word‑Dokument mit dem Shape speichern

Abschließend **save word with shape** wir auf die Festplatte. Die `Save`‑Methode ermittelt das Format automatisch aus der Dateierweiterung.

```csharp
// Step 5 – persist the document
string outputPath = @"C:\Temp\shadowedRectangle.docx";
document.Save(outputPath);
```

> **Was Sie sehen werden:** Öffnen Sie `shadowedRectangle.docx` in Word (oder einem anderen kompatiblen Viewer) und Sie sehen ein graues Rechteck mit einem weichen Schatten, das oben auf der ersten Seite sitzt.

---

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette Programm, das Sie in eine Konsolen‑App kopieren‑und‑einfügen können. Es enthält alle using‑Direktiven, Kommentare und die genauen Schritte, die wir besprochen haben.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeWordShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank word document
            Document document = new Document();

            // 2️⃣ Add a rectangle shape
            Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
            {
                Width = 200,
                Height = 100
            };

            // 3️⃣ Configure a custom shadow (add shadow word)
            rectangleShape.ShadowFormat.Enabled = true;
            rectangleShape.ShadowFormat.Color = Color.Gray;
            rectangleShape.ShadowFormat.OffsetX = 5;
            rectangleShape.ShadowFormat.OffsetY = 5;
            rectangleShape.ShadowFormat.Transparency = 0.3;
            rectangleShape.ShadowFormat.BlurRadius = 4;

            // 4️⃣ Insert the shape into the first paragraph
            document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

            // 5️⃣ Save the document (save word with shape)
            string outputFile = @"YOUR_DIRECTORY\shadow.docx";
            document.Save(outputFile);

            // Confirmation
            System.Console.WriteLine($"Document saved to {outputFile}");
        }
    }
}
```

Führen Sie das Programm aus, navigieren Sie zu `YOUR_DIRECTORY` und öffnen Sie das erzeugte `shadow.docx`. Sie sollten das Rechteck mit einem dezenten grauen Schatten sehen – genau das, was wir erreichen wollten.

---

## Häufig gestellte Fragen & Tipps

### Wie ändere ich die Farbe des Shapes?
```csharp
rectangleShape.FillColor = Color.LightBlue;
```
Setzen Sie einfach `FillColor`, bevor Sie das Shape anhängen.

### Was tun, wenn ich mehrere Shapes auf derselben Seite benötige?
Erstellen Sie zusätzliche `Shape`‑Objekte und hängen Sie jedes an denselben Absatz oder an verschiedene Absätze an. Sie können das Layout auch mit `WrapType` und `RelativeHorizontalPosition` steuern.

### Kann ich zu PDF exportieren und dabei den Schatten beibehalten?
Absolut. Verwenden Sie `document.Save("output.pdf")` – Aspose.Words bewahrt den Schatteneffekt bei der PDF‑Konvertierung.

### Funktioniert das auf .NET Core?
Ja. Aspose.Words ist plattformübergreifend; derselbe Code läuft auf .NET Core, .NET 5+ und .NET Framework.

### Wie füge ich ein Shape ohne Absatz hinzu?
Sie können das Shape direkt zu einem `Run` oder zu einer `Story` hinzufügen. Für eine genauere Positionierung setzen Sie `rectangleShape.RelativeHorizontalPosition = RelativeHorizontalPosition.Page` und passen die Eigenschaften `Left`/`Top` an.

---

## Visuelles Ergebnis

![Rechteck-Shape mit grauem Schatten in einem Word-Dokument – add shadow word Beispiel](https://example.com/placeholder-image.png "add shadow word example")

*Der Alt‑Text des Bildes enthält das sekundäre Schlüsselwort **add shadow word**, um SEO‑Anforderungen zu erfüllen.*

---

## Fazit

Wir haben gerade gezeigt, wie man **create blank word document**, **add rectangle shape**, einen **add shadow word**‑Effekt anwendet und schließlich **save word with shape** mit Aspose.Words für .NET durchführt. Der Prozess ist einfach: Instanziieren Sie ein `Document`, erstellen Sie ein `Shape`, passen Sie dessen `ShadowFormat` an, fügen Sie es ein und rufen `Save` auf.  

Ab hier können Sie experimentieren – probieren Sie verschiedene Shape‑Typen aus, spielen Sie mit Farben oder schichten Sie mehrere Shapes. Wenn Sie dieses Dokument mit bestehendem Inhalt zusammenführen müssen, laden Sie einfach die vorhandene Datei via `new Document("existing.docx")` und folgen Sie denselben Schritten.  

Haben Sie weitere Fragen? Hinterlassen Sie einen Kommentar, und happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}