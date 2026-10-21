---
category: general
date: 2026-03-30
description: Erfahren Sie, wie Sie in Word einer Form mit C# einen Schatten hinzufügen.
  Dieser Leitfaden zeigt außerdem, wie man einen Formschatten hinzufügt, die Transparenz
  der Form anpasst und einen Rechteckschatten hinzufügt.
draft: false
keywords:
- how to set shadow
- adjust shape transparency
- add shape shadow
- how to add shadow
- add rectangle shadow
language: de
og_description: Wie man in C# einem Word‑Shape einen Schatten hinzufügt? Folgen Sie
  dieser Schritt‑für‑Schritt‑Anleitung, um einem Shape einen Schatten zu geben, die
  Transparenz des Shapes anzupassen und einen Rechteckschatten hinzuzufügen.
og_title: Wie man Schatten zu einer Word-Form hinzufügt – C#‑Tutorial
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Wie man einem Word‑Shape einen Schatten hinzufügt – C#‑Tutorial
url: /de/net/programming-with-shapes/how-to-set-shadow-on-a-word-shape-c-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# So setzen Sie einen Schatten auf eine Word‑Form – C#‑Tutorial

Haben Sie sich jemals gefragt, **wie man einen Schatten** auf einer Form in einem Word‑Dokument setzt, ohne die Benutzeroberfläche zu benutzen? Sie sind nicht allein. In vielen Berichten oder Marketing‑Präsentationen lässt ein dezenter Drop‑Shadow ein Rechteck hervorstechen, und das programmgesteuerte Vorgehen spart Stunden.

In diesem Leitfaden gehen wir Schritt für Schritt durch ein vollständiges, sofort ausführbares Beispiel, das nicht nur **zeigt, wie man einen Schatten setzt**, sondern auch **Form‑Schatten hinzufügen**, **Form‑Transparenz anpassen** und sogar **Rechteck‑Schatten hinzufügen** für klassische Call‑Out‑Boxen behandelt. Am Ende haben Sie eine Word‑Datei (`output.docx`), die professionell wirkt, und Sie verstehen, warum jede Eigenschaft wichtig ist.

## Voraussetzungen

- .NET 6+ (oder .NET Framework 4.7.2) mit einem C#‑Compiler  
- Aspose.Words for .NET NuGet‑Paket (`Install-Package Aspose.Words`)  
- Grundlegende Kenntnisse in C# und dem Word‑Objektmodell  

Weitere Bibliotheken sind nicht nötig – alles steckt in Aspose.Words.

---

## Wie man in C# einen Schatten auf eine Word‑Form setzt

Unten finden Sie die komplette Quellcodedatei. Speichern Sie sie als `Program.cs` und führen Sie sie in Ihrer IDE oder mit `dotnet run` aus. Der Code lädt ein vorhandenes `.docx`, findet die erste Form (standardmäßig ein Rechteck), aktiviert deren Schatten, passt einige visuelle Parameter an und speichert das Ergebnis.

```csharp
// Program.cs
using System;
using System.Drawing;               // For Color
using Aspose.Words;                // Core document API
using Aspose.Words.Drawing;        // Shape and shadow classes

class ShadowDemo
{
    static void Main()
    {
        // 1️⃣ Load the Word document that contains the shape.
        // Replace YOUR_DIRECTORY with the folder where your files live.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath);

        // 2️⃣ Retrieve the first shape in the document.
        // If you have multiple shapes, you can loop or use GetChild with a different index.
        Shape rectangleShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (rectangleShape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx contains at least one shape.");
            return;
        }

        // 3️⃣ Enable the shape's shadow and choose a base color.
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Black;   // You can pick any System.Drawing.Color

        // 4️⃣ Fine‑tune the shadow appearance.
        rectangleShape.ShadowFormat.Transparency = 0.3;     // 30 % transparent (adjust shape transparency)
        rectangleShape.ShadowFormat.OffsetX = 5;           // Horizontal offset in points
        rectangleShape.ShadowFormat.OffsetY = 5;           // Vertical offset in points
        rectangleShape.ShadowFormat.BlurRadius = 4;       // Soft edge radius

        // 5️⃣ Save the updated document.
        string outputPath = @"YOUR_DIRECTORY\output.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Shadow applied! Check {outputPath}");
    }
}
```

> **Was Sie sehen werden** – Das Rechteck besitzt jetzt einen schwarzen Drop‑Shadow, der zu 30 % transparent ist, 5 pt nach rechts und unten verschoben und leicht verschwommen ist. Öffnen Sie `output.docx` in Word, um das Ergebnis zu prüfen.

## Form‑Transparenz anpassen – Warum das wichtig ist

Transparenz ist nicht nur ein ästhetischer Regler; sie beeinflusst die Lesbarkeit. Ein Wert von 0,0 macht den Schatten vollständig undurchsichtig, während 1,0 ihn komplett ausblendet. Im obigen Snippet haben wir `0.3` verwendet, um einen dezenten Effekt zu erzielen, der sowohl auf hellen als auch dunklen Hintergründen funktioniert. Experimentieren Sie gern:

```csharp
rectangleShape.ShadowFormat.Transparency = 0.1; // Almost solid shadow
rectangleShape.ShadowFormat.Transparency = 0.6; // Very faint
```

Denken Sie daran, dass **Form‑Transparenz anpassen** auch auf die Füllfarbe der Form angewendet werden kann, wenn Sie ein halbtransparentes Rechteck benötigen.

## Form‑Schatten zu verschiedenen Objekten hinzufügen

Der Code, den wir verwendet haben, richtet sich an ein `Shape`‑Objekt, aber dieselben `ShadowFormat`‑Eigenschaften existieren auch bei **Image**, **Chart** und sogar **TextBox**‑Objekten. Hier ein kurzes Muster, das Sie kopieren‑und‑einfügen können:

```csharp
// Assuming 'image' is an Aspose.Words.Drawing.Image object
image.ShadowFormat.Visible = true;
image.ShadowFormat.Color = Color.Gray;
image.ShadowFormat.OffsetX = 3;
image.ShadowFormat.OffsetY = 3;
image.ShadowFormat.BlurRadius = 2;
```

Egal, ob Sie **Form‑Schatten hinzufügen** zu einem Logo oder einem dekorativen Icon, das Vorgehen bleibt identisch.

## Wie man jedem Objekt einen Schatten hinzufügt – Sonderfälle

1. **Form ohne Begrenzungsrahmen** – Einige Word‑Formen (wie Freihand‑Skizzen) unterstützen keinen Schatten. Der Versuch, `ShadowFormat.Visible` zu setzen, schlägt stillschweigend fehl. Prüfen Sie `shape.IsShadowSupported`, wenn Sie Sicherheit benötigen.  
2. **Ältere Word‑Versionen** – Die Schatten‑Eigenschaften entsprechen Funktionen ab Word 2007. Wenn Sie Word 2003 unterstützen müssen, wird der Schatten beim Öffnen der Datei ignoriert.  
3. **Mehrere Schatten** – Aspose.Words unterstützt derzeit nur einen Schatten pro Form. Wenn Sie einen doppelten Effekt benötigen, duplizieren Sie die Form, versetzen sie leicht und wenden unterschiedliche Schatten‑Einstellungen an.

## Rechteck‑Schatten hinzufügen – Ein Praxisbeispiel

Stellen Sie sich vor, Sie erzeugen einen Quartalsbericht, bei dem jede Abschnitts‑Überschrift ein farbiges Rechteck ist. Das Hinzufügen eines **Rechteck‑Schatten** verleiht der Seite ein „Karten‑ähnliches“ Aussehen. Die Schritte sind identisch zum Basis‑Beispiel; stellen Sie nur sicher, dass die Ziel‑Form tatsächlich ein Rechteck ist (`shape.ShapeType == ShapeType.Rectangle`). Wenn Sie das Rechteck von Grund auf neu erstellen wollen, siehe das Snippet unten:

```csharp
// Create a new rectangle shape programmatically
Shape newRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,
    Height = 50,
    WrapType = WrapType.Inline
};
newRect.FillColor = Color.LightBlue;

// Apply shadow (same settings as before)
newRect.ShadowFormat.Visible = true;
newRect.ShadowFormat.Color = Color.Black;
newRect.ShadowFormat.Transparency = 0.25;
newRect.ShadowFormat.OffsetX = 4;
newRect.ShadowFormat.OffsetY = 4;
newRect.ShadowFormat.BlurRadius = 3;

// Insert into the first paragraph
doc.FirstSection.Body.FirstParagraph.AppendChild(newRect);
```

Wenn Sie das komplette Programm mit dieser Ergänzung ausführen, erhalten Sie ein frisches Rechteck, das bereits den gewünschten **Rechteck‑Schatten**‑Effekt besitzt.

---

![Word shape with shadow](placeholder-image.png){alt="wie man in Word einen Schatten auf eine Form setzt"}

*Abbildung: Das Rechteck nach Anwendung der Schatten‑Einstellungen.*

## Kurze Zusammenfassung (Stichpunkt‑Spickzettel)

- **Laden** Sie das Dokument mit `new Document(path)`.  
- **Suchen** Sie die Form über `doc.GetChild(NodeType.Shape, index, true)`.  
- **Aktivieren** Sie den Schatten: `shape.ShadowFormat.Visible = true;`.  
- **Farbe setzen** mit jeder `System.Drawing.Color`.  
- **Transparenz anpassen** (`0.0–1.0`), um die Undurchsichtigkeit zu steuern.  
- **OffsetX / OffsetY** verschieben den Schatten horizontal/vertikal (Punkte).  
- **BlurRadius** macht die Kante weicher – höhere Werte = unschärferer Schatten.  
- **Speichern** Sie die Datei und öffnen Sie sie in Word, um das Ergebnis zu sehen.

## Was können Sie als Nächstes ausprobieren?

- **Dynamische Farben** – Schattenfarbe aus einem Theme oder einer Benutzereingabe übernehmen.  
- **Bedingte Schatten** – Einen Schatten nur dann anwenden, wenn die Breite der Form einen Schwellenwert überschreitet.  
- **Batch‑Verarbeitung** – Durch alle Formen in einem Dokument iterieren und **Form‑Schatten hinzufügen** automatisch.  

Wenn Sie dem Tutorial gefolgt sind, wissen Sie jetzt, **wie man einen Schatten setzt**, wie man **Form‑Transparenz anpasst** und wie man **Rechteck‑Schatten** für einen professionellen Look hinzufügt. Experimentieren Sie, brechen Sie Dinge und reparieren Sie sie anschließend – Programmieren ist der beste Lehrer.

---

*Viel Spaß beim Coden! Wenn Ihnen dieses Tutorial geholfen hat, hinterlassen Sie einen Kommentar oder teilen Sie Ihre eigenen Schatten‑Tricks. Je mehr wir voneinander lernen, desto schöner werden unsere Word‑Dokumente.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}