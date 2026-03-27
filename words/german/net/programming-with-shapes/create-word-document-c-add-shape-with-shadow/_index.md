---
category: general
date: 2026-03-27
description: Erstellen Sie ein Word‑Dokument in C# und lernen Sie, wie Sie eine Form
  hinzufügen, einen Schatten auf die Form anwenden und den Schattenabstand festlegen.
  Schritt‑für‑Schritt‑Anleitung für Aspose.Words.
draft: false
keywords:
- create word document c#
- how to add shape
- apply shadow to shape
- how to create rectangle
- set shadow distance
language: de
og_description: Erstelle ein Word‑Dokument in C# mit einer Rechteckform und einem
  benutzerdefinierten Schatten. Folge diesem umfassenden Tutorial, um den Schattenabstand
  und -stil festzulegen.
og_title: Word-Dokument in C# erstellen – Form mit Schatten hinzufügen
tags:
- Aspose.Words
- C#
- Document Automation
title: Word-Dokument erstellen C# – Form mit Schatten hinzufügen
url: /de/net/programming-with-shapes/create-word-document-c-add-shape-with-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument mit C# erstellen – Form mit Schatten hinzufügen

Haben Sie schon einmal ein **Word-Dokument mit C# erstellen** müssen, das ein hübsch gestaltetes Rechteck enthält? Vielleicht bauen Sie eine Berichtsvorlage und möchten einen dezenten Drop‑Shadow, um das Layout hervorzuheben. In diesem Tutorial zeigen wir genau das – wie man eine Form hinzufügt, ihr einen Schatten zuweist und sogar den Schattenabstand mit Aspose.Words anpasst.

Wir beginnen mit einem leeren Dokument, fügen ein Rechteck ein, geben ihm einen voreingestellten Schatten und speichern schließlich die Datei. Am Ende haben Sie ein einsatzbereites .docx, das Sie in Word öffnen und den Effekt sofort sehen können. Keine externen Tools, nur reiner C#‑Code.

## Voraussetzungen

- .NET 6 (oder ein aktuelles .NET Framework) installiert.
- Visual Studio 2022 oder VS Code mit C#‑Erweiterung.
- Aspose.Words für .NET NuGet‑Paket (`Aspose.Words` Version 23.12 oder neuer).  
  Sie können es über die Package Manager Console hinzufügen:

  ```powershell
  Install-Package Aspose.Words
  ```

Das war’s – keine zusätzlichen DLLs oder COM‑Interop erforderlich.

## Schritt 1: Neues Dokument und Builder initialisieren – Grundlagen zum **Word-Dokument mit C# erstellen**

Zuerst benötigen wir ein `Document`‑Objekt, das die Word‑Datei repräsentiert, und einen `DocumentBuilder`, um sie zu bearbeiten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a blank Word document
Document document = new Document();

// DocumentBuilder lets us add content programmatically
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Warum dieser Schritt wichtig ist:** Die `Document`‑Klasse ist der Container für alle Word‑Teile (Seiten, Stile, Bilder). Der Builder ist die High‑Level‑API, die die low‑level Node‑Manipulation abstrahiert und es einfach macht, **Word-Dokument mit C# zu erstellen**, ohne sich direkt mit XML zu befassen.

## Schritt 2: Rechteck‑Form einfügen – **wie man ein Rechteck erstellt**  

Jetzt platzieren wir ein Rechteck auf der Seite. Die Größe wird in Punkten angegeben (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle 200 pt wide and 100 pt tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue fill so we can see it clearly
rectangleShape.FillColor = Color.LightBlue;
```

> **Pro‑Tipp:** Wenn Sie eine andere Form benötigen, ersetzen Sie einfach `ShapeType.Rectangle` durch `ShapeType.Ellipse`, `ShapeType.Triangle` usw. Der gleiche Code funktioniert für **wie man eine Form hinzufügt** jeder Art.

## Schritt 3: Voreingestellten Schatten anwenden und feinjustieren – **Schatten auf Form anwenden**  

Aspose.Words liefert mehrere voreingestellte Schattenformate. Wir verwenden `Preset1` und passen anschließend Abstand, Weichzeichnung, Transparenz und Farbe an.

```csharp
// Choose a predefined shadow style
rectangleShape.Shadow.Format = ShadowFormat.Preset1;

// Adjust the shadow distance – this is the offset from the shape
rectangleShape.Shadow.Distance = 5; // measured in points

// Make the edge of the shadow a little fuzzy
rectangleShape.Shadow.BlurRadius = 3;

// Set the shadow to be 40 % transparent (0 = opaque, 1 = fully transparent)
rectangleShape.Shadow.Transparency = 0.4;

// Pick a gray tone for the shadow color
rectangleShape.Shadow.Color = Color.Gray;
```

> **Warum den Schatten anpassen?** Die Eigenschaft `Distance` steuert, wie weit der Schatten vom Rechteck entfernt liegt – denken Sie an das „Anheben“, das Sie in einer 3‑D‑Darstellung sehen würden. Das Ändern von `BlurRadius` macht die Kanten weicher, während `Transparency` Ihnen ein dezentes, professionelles Aussehen ermöglicht. Damit wird die Anforderung **Schattenabstand festlegen** erfüllt und gezeigt, wie man **Schatten auf Form anwenden** flexibel umsetzt.

## Schritt 4: Dokument speichern – **Word-Dokument mit C# erstellen** abschließen

Zum Schluss schreiben wir das Dokument auf die Festplatte. Passen Sie den Pfad an einen Ordner an, in den Sie Schreibrechte haben.

```csharp
// Save the document as a .docx file
string outputPath = @"C:\Temp\ShadowShape.docx";
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Öffnen Sie die resultierende Datei in Microsoft Word, und Sie sehen ein hellblaues Rechteck mit einem weichen grauen Schatten, der um 5 pt versetzt ist. Das ist der visuelle Beweis, dass Sie erfolgreich **Word-Dokument mit C# erstellt** haben, inklusive einer gestalteten Form.

![Create Word Document C# with Shadowed Shape](shadow-example.png){: .img alt="Beispiel für Word-Dokument mit C# – Rechteck mit Schatten"}

## Optionale Varianten & Sonderfälle

| Szenario | Was zu ändern ist | Warum es wichtig ist |
|----------|-------------------|----------------------|
| **Anderer Schattenstil** | `rectangleShape.Shadow.Format = ShadowFormat.Preset3;` | Verleiht ein dramatischeres Aussehen ohne zusätzlichen Code. |
| **Kein Preset – benutzerdefinierter Schatten** | `Format` weglassen und `OffsetX`, `OffsetY` manuell setzen. | Vollständige Kontrolle über Richtung und Tiefe. |
| **Mehrere Formen** | `builder.InsertShape` erneut aufrufen, bevor gespeichert wird. | Nützlich für komplexe Vorlagen mit Icons, Logos usw. |
| **Kompatibilität mit älteren Aspose‑Versionen** | `ShadowEffect`‑Klasse verwenden (verfügbar in v20.x). | Stellt sicher, dass Ihr Code in Legacy‑Projekten läuft. |
| **Als PDF speichern** | `document.Save("ShadowShape.pdf");` | Der gleiche Schatten wird im PDF‑Export dargestellt. |

> **Häufige Frage:** *Was tun, wenn der Schatten in Word nicht erscheint?*  
> Stellen Sie sicher, dass Sie eine aktuelle Version von Aspose.Words (≥ 22.9) verwenden. Ältere Releases hatten nur eingeschränkte Schattenunterstützung. Prüfen Sie außerdem, dass das Dokument in einer aktuellen Word‑Version (2016 +) geöffnet wird.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort einsetzbare Programm. Es enthält alle `using`‑Direktiven, Kommentare und Fehlerbehandlung für ein reibungsloses Erlebnis.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShadowShapeDemo
{
    class Program
    {
        static void Main()
        {
            try
            {
                // 1️⃣ Create a new blank document and a builder
                Document doc = new Document();
                DocumentBuilder builder = new DocumentBuilder(doc);

                // 2️⃣ Insert a rectangle (200 pt × 100 pt) and fill it
                Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
                rect.FillColor = Color.LightBlue;

                // 3️⃣ Apply a preset shadow and tweak its properties
                rect.Shadow.Format = ShadowFormat.Preset1;   // predefined style
                rect.Shadow.Distance = 5;                    // set shadow distance
                rect.Shadow.BlurRadius = 3;                  // soften edges
                rect.Shadow.Transparency = 0.4;              // semi‑transparent
                rect.Shadow.Color = Color.Gray;              // shadow color

                // 4️⃣ Save the document
                string outPath = @"C:\Temp\ShadowShape.docx";
                doc.Save(outPath);

                Console.WriteLine($"✅ Document created successfully at {outPath}");
            }
            catch (Exception ex)
            {
                Console.Error.WriteLine($"❌ Error: {ex.Message}");
            }
        }
    }
}
```

Führen Sie das Programm aus, navigieren Sie zu `C:\Temp\ShadowShape.docx`, und Sie sehen das Rechteck mit dem exakt konfigurierten Schatten.

## Zusammenfassung & nächste Schritte

- Sie wissen jetzt, wie man **Word-Dokument mit C# erstellt**, ein Rechteck einfügt und **Schatten auf Form anwendet** mit einem benutzerdefinierten **Schattenabstand festlegt**.  
- Das Beispiel nutzt Aspose.Words, das die OpenXML‑Komplexität abstrahiert und ein konsistentes Rendering über verschiedene Word‑Versionen hinweg garantiert.  
- Möchten Sie weitergehen? Kombinieren Sie mehrere Formen, fügen Sie Text in das Rechteck ein oder exportieren Sie dasselbe Dokument als PDF, um zu sehen, wie der Schatten übertragen wird.

### Verwandte Themen, die Sie erkunden könnten

- **Wie man eine Form** in Kopf‑/Fußzeilen für Branding hinzufügt.  
- Verwendung von **Aspose.Words**, um Diagramme und Tabellen programmgesteuert einzufügen.  
- Anpassung von **Schatteneinstellungen** bei Bildern statt Vektorformen.  
- Automatisierung der Massenerstellung von Dokumenten für Rechnungen oder Zertifikate.

Experimentieren Sie, brechen Sie den Code und bauen Sie ihn dann wieder zusammen – das ist der schnellste Weg, die Konzepte zu verinnerlichen. Wenn Sie auf ein Problem stoßen, hinterlassen Sie einen Kommentar unten oder schauen Sie in die offizielle Aspose.Words‑Dokumentation für tiefere API‑Einblicke.

Viel Spaß beim Coden und beim Veredeln Ihrer Word‑Dateien!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}