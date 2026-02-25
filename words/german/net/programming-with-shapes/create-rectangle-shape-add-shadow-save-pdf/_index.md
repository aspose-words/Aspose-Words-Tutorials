---
category: general
date: 2026-02-24
description: Erstellen Sie ein Rechteck-Shape in C# mit Aspose.Words, fügen Sie dem
  Shape einen Schatten hinzu und speichern Sie das Dokument als PDF. Lernen Sie, wie
  Sie in wenigen Minuten einen Schatten hinzufügen und das PDF speichern.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: de
og_description: Erstellen Sie eine Rechteckform in C# mit Aspose.Words, fügen Sie
  der Form einen Schatten hinzu und speichern Sie das Dokument als PDF – ein vollständiger,
  Schritt‑für‑Schritt‑Leitfaden.
og_title: Rechteck erstellen, Schatten hinzufügen & PDF speichern
tags:
- Aspose.Words
- C#
- PDF generation
title: Rechteckform erstellen, Schatten hinzufügen & PDF speichern
url: /de/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

keep the image URL unchanged.

Now produce the entire content with translations.

Let's start.

First three shortcodes unchanged.

Then heading "# Create rectangle shape, add shadow & save PDF" translate to German: "# Rechteckform erstellen, Schatten hinzufügen & PDF speichern". Keep same heading level.

Paragraphs translate.

Need to keep **bold** formatting.

Let's translate step by step.

Will produce final answer.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform erstellen, Schatten hinzufügen & PDF speichern

Haben Sie schon einmal **eine Rechteckform** in einem Word‑Dokument erstellen wollen, dabei aber auch einen schönen Drop‑Shadow und eine PDF‑Ausgabe benötigen? Sie sind nicht allein. In vielen Reporting‑ oder Rechnungserstellungs‑Projekten macht die visuelle Feinabstimmung — wie ein dezenter Schatten — den Unterschied zwischen „nur einer weiteren Datei“ und „professionell‑grade Dokument“ aus.

In diesem Tutorial gehen wir genau darauf ein: Wir verwenden **Aspose.Words for .NET**, um eine Rechteckform zu erstellen, ihr einen Schatten hinzuzufügen und schließlich **das Dokument als PDF zu speichern**. Am Ende haben Sie eine sofort lauffähige C#‑Konsolen‑App, die ein PDF mit einem schattierten Rechteck erzeugt, und Sie wissen, wie Sie den Schatten anpassen oder die Export‑Optionen ändern können.

## Was Sie benötigen

- .NET 6 SDK (oder jede aktuelle .NET‑Version) — die API funktioniert genauso unter .NET Framework 4.x.  
- Aspose.Words for .NET NuGet‑Paket (`Aspose.Words`) — installieren Sie es mit `dotnet add package Aspose.Words`.  
- Ein Code‑Editor — Visual Studio, VS Code oder Rider reichen aus.  

Keine zusätzlichen Lizenzschritte für dieses Beispiel; der kostenlose Evaluierungsmodus reicht aus, um die PDF‑Ausgabe zu sehen.

## Schritt 1: Projekt einrichten und Namespaces importieren

Zuerst erstellen wir ein Konsolen‑Projekt und binden die Klassen ein, die wir benötigen.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Warum das wichtig ist:* `Document` und `DocumentBuilder` liefern die Leinwand, während `Shape` und `ShadowFormat` das Rechteck zeichnen und formatieren. Das Vorab‑Importieren hält den späteren Code übersichtlich.

## Schritt 2: **Rechteckform erstellen** mit den gewünschten Abmessungen

Jetzt erzeugen wir ein leeres Dokument und fügen ein Rechteck ein. Beachten Sie, dass die Methode `InsertShape` ein `Shape`‑Objekt zurückgibt, das wir sofort formatieren können.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Erklärung*: Die Größe wird in Punkten angegeben (1 pt = 1/72 in). Passen Sie die Zahlen an Ihr Layout an. Wir geben der Form außerdem eine hellblaue Füllung, damit der Schatten besser zur Geltung kommt.

## Schritt 3: **Schatten zur Form hinzufügen** — Feinabstimmung des Effekts

Ein Schatten ist nicht nur „ein/aus“. Sie können Farbe, Unschärfe, Abstand, Richtung und sogar Transparenz steuern. Hier eine praktische Konfiguration, die für die meisten Berichte gut funktioniert.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Warum Sie diese Werte ändern könnten:*  
- **BlurRadius** — erhöhen für einen verträumten Effekt, verringern für eine scharfe Kante.  
- **Direction** — 0° zeigt nach rechts, 90° nach unten, 180° nach links usw. Drehen Sie den Schatten passend zu Ihrem Seitenlayout.  
- **Transparency** — auf `0` setzen für einen festen Schatten, `0.5` für halbtransparent usw.

### Wie man Schatten hinzufügt — alternative Ansätze

Wenn Sie einen **mehrschichtigen Schatten** benötigen (z. B. einen dunkleren äußeren Schatten plus einen helleren inneren), können Sie eine zweite Form erzeugen, sie versetzen und ein anderes `ShadowFormat` setzen. Oder für einen schnellen „keine Unschärfe“-Look setzen Sie `BlurRadius = 0`.

## Schritt 4: **Dokument als PDF speichern** — der finale Export

Nachdem Rechteck und Schatten fertig sind, schreiben wir die Datei als PDF. Aspose.Words übernimmt die Konvertierung intern; Sie rufen einfach `Save` mit dem gewünschten Format auf.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Tipp*: Wenn Sie die PDF‑Konformität (PDF/A, PDF/X) steuern oder Schriften einbetten möchten, verwenden Sie eine Überladung:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Damit ist der **Wie‑man‑PDF‑speichert**‑Teil zusammengefasst.

## Vollständiges, ausführbares Beispiel

Unten finden Sie das komplette Programm, das Sie in `Program.cs` einfügen können. Es kompiliert und läuft sofort (stellen Sie nur sicher, dass der Ausgabepfad existiert).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Erwartetes Ergebnis

Öffnen Sie die erzeugte `ShadowRectangle.pdf`. Sie sehen eine einzelne Seite mit einem hellblauen Rechteck, einem weichen grauen Schatten, der um 45° nach rechts‑unten versetzt ist, und klaren Kanten. Das PDF sollte in jedem modernen Reader (Adobe Acrobat, Edge, Chrome) angezeigt werden können.

![Rechteckform mit Schatten im PDF](/images/shadow-rectangle.png "Rechteckform mit Schatten im PDF")

*(Der Alt‑Text des Bildes enthält das Haupt‑Keyword für SEO.)*

## Häufige Fragen & Sonderfälle

**Was tun, wenn der Schatten im PDF verschwindet?**  
Stellen Sie sicher, dass Sie eine aktuelle Version von Aspose.Words (≥23.3) verwenden. Ältere Builds hatten einen Bug, bei dem bestimmte Schatten‑Eigenschaften bei der PDF‑Konvertierung ignoriert wurden.

**Kann ich die Schattenfarbe an meine Markenfarbe anpassen?**  
Natürlich — ersetzen Sie einfach `System.Drawing.Color.Gray` durch jede gewünschte `Color`, z. B. `Color.FromArgb(128, 0, 0, 255)` für ein halbtransparentes Blau.

**Wie füge ich einem anderen Shape (Ellipse, Stern usw.) einen Schatten hinzu?**  
Das gleiche `ShadowFormat` funktioniert für jedes `Shape`‑Objekt. Nachdem Sie das Shape erstellt haben, greifen Sie auf dessen `ShadowFormat` zu und setzen die Eigenschaften.

**Was ist mit DPI‑ oder Skalierungsproblemen?**  
Die PDF‑Darstellung respektiert die Punktgröße des Shapes. Wenn Sie eine höherauflösende Ausgabe (für den Druck) benötigen, passen Sie die Shape‑Abmessungen entsprechend an oder setzen Sie `PdfSaveOptions.ImageResolution`.

**Kann ich in andere Formate exportieren, z. B. PNG?**  
Ja — rufen Sie einfach `document.Save("output.png", SaveFormat.Png)` auf. Der Schatten wird dabei identisch gerendert.

## Profi‑Tipps & bewährte Vorgehensweisen

- **Builder wiederverwenden**: Wenn Sie mehrere Shapes hinzufügen, behalten Sie eine einzige `DocumentBuilder`‑Instanz; das ist günstiger als viele Instanzen zu erzeugen.  
- **Batch‑Speichern**: Beim Erzeugen vieler PDFs in einer Schleife das `PdfSaveOptions`‑Objekt wiederverwenden, um wiederholte Allokationen zu vermeiden.  
- **Testen**: Öffnen Sie das PDF nach dem Speichern immer, um zu prüfen, ob der Schatten wie erwartet erscheint. Einige PDF‑Viewer rendern Schatten leicht unterschiedlich; Adobe Acrobat ist die zuverlässigste Referenz.  
- **Performance**: Für sehr große Dokumente deaktivieren Sie die automatischen Seitenumbrüche von `DocumentBuilder.InsertShape`, indem Sie `builder.PageSetup.DifferentFirstPageHeaderFooter = false` setzen, falls Sie diese nicht benötigen.

## Fazit

Wir haben alles behandelt, was Sie benötigen, um **eine Rechteckform zu erstellen**, **einen Schatten zur Form hinzuzufügen** und **das Dokument als PDF zu speichern** — unter Verwendung von Aspose.Words for .NET. Der Code ist kompakt, die Konzepte sind erklärt, und Sie haben nun eine solide Basis, um mit anderen Shapes, Schatten‑Stilen und Export‑Optionen zu experimentieren.  

Nächste Schritte? Versuchen Sie, das Rechteck durch ein abgerundetes -

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}