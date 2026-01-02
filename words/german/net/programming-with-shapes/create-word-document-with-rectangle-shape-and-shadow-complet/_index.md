---
category: general
date: 2026-01-02
description: Erstellen Sie ein Word‑Dokument mit einer Rechteckform, setzen Sie die
  Füllfarbe der Form und speichern Sie die DOCX‑Datei mit Aspose.Words. Erfahren Sie,
  wie Sie in wenigen Minuten ein Rechteck mit Schatten erstellen.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: de
og_description: Erstelle ein Word‑Dokument mit einem benutzerdefinierten Rechteck,
  setze seine Füllfarbe, füge einen Schatten hinzu und speichere es als DOCX. Vollständiger
  Code und Erklärungen.
og_title: Word-Dokument mit Rechteckform erstellen – Schritt für Schritt
tags:
- Aspose.Words
- C#
- Document Generation
title: Word-Dokument mit Rechteckform und Schatten erstellen – Komplettanleitung
url: /de/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word‑Dokument mit Rechteckform und Schatten erstellen – Komplettanleitung

Haben Sie sich schon einmal gefragt, wie man ein **word document** erstellt, das ein schön gestaltetes Rechteck enthält? Vielleicht benötigen Sie einen Platzhalter für ein Logo, ein farbiges Banner oder einfach einen visuellen Hinweis in einem Bericht. In diesem Tutorial fügen wir eine **rectangle shape** hinzu, geben ihr eine Füllfarbe, wenden einen dezenten Schatten an und speichern schließlich die **docx file** – alles mit Aspose.Words für .NET.

Am Ende haben Sie ein sofort ausführbares C#‑Snippet, eine klare Erklärung jeder Zeile und ein paar Tipps, die Sie in Ihren eigenen Projekten wiederverwenden können. Kein Schnickschnack, nur eine praktische Lösung zum Kopieren‑Einfügen.

## Was Sie benötigen

- .NET 6 oder höher (der Code funktioniert auch mit .NET Framework)  
- Visual Studio 2022 (oder ein beliebiger anderer Editor)  
- **Aspose.Words** NuGet‑Paket (`Install-Package Aspose.Words`)  

Wenn Sie das bereits haben, super – los geht's.

## Schritt 1 – Neues Dokument initialisieren (How to create word document)

Das Erste, was Sie tun müssen, ist ein **word document** im Speicher zu **create**. Stellen Sie sich das vor wie das Öffnen einer leeren Leinwand, auf der Sie später Ihr Rechteck zeichnen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Warum das wichtig ist:** `Document` repräsentiert die gesamte DOCX‑Datei, während `DocumentBuilder` ein praktischer Helfer ist, mit dem Sie Text, Tabellen, Bilder und Formen einfügen können, ohne den zugrunde liegenden Knotebaum manuell zu bearbeiten.

## Schritt 2 – Rechteckform einfügen (Add rectangle shape)

Jetzt **add rectangle shape** zum Dokument. Die Methode `InsertShape` nimmt den Formtyp und deren Abmessungen in Punkten (1 Punkt = 1/72 Zoll).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Pro‑Tipp:** Wenn Sie einmal eine andere Geometrie benötigen (Ellipse, Dreieck usw.), ändern Sie einfach `ShapeType.Rectangle` in den gewünschten Enum‑Wert.

## Schritt 3 – Schatten konfigurieren (Set shape fill color & shadow)

Ein Schatten kann einer flachen Form mehr Dreidimensionalität verleihen. Hier aktivieren wir den Schatten und passen sein Aussehen an.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Warum diese Werte?** Ein moderater Unschärferadius und ein Abstand von 5 Punkten verhindern, dass der Schatten die Form überlagert, während 45° eine Lichtquelle von oben‑links simulieren – eine gängige UI‑Konvention.

## Schritt 4 – Dokument speichern (Save docx file)

Zum Schluss **save docx file** auf die Festplatte. Passen Sie den Pfad an Ihre Umgebung an.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Wenn Sie `ShadowDemo.docx` in Word öffnen, sollten Sie ein hellblaues Rechteck mit einem weichen grauen Schatten sehen, genau wie im Screenshot unten.

![Word‑Dokument mit Rechteckform und Schatten erstellen](https://example.com/images/rectangle-shadow.png "Word‑Dokument mit Rechteckform und Schatten erstellen")

*Bild‑Alt‑Text:* **Word‑Dokument** mit einer Rechteckform und einem Schatten.

## Vollständiges, sofort ausführbares Beispiel (How to create rectangle and save)

Alles zusammengeführt, hier das komplette Programm, das Sie in eine Konsolen‑App kopieren können:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Erwartetes Ergebnis

- Eine Datei namens **ShadowDemo.docx** erscheint im Zielordner.  
- Beim Öffnen in Microsoft Word wird eine einzelne Seite mit dem Text „Shadow Demo“ gefolgt von einem hellblauen Rechteck angezeigt.  
- Das Rechteck wirft einen weichen grauen Schatten im Winkel von 45°, wodurch ein leichter 3‑D‑Effekt entsteht.

## Häufige Fragen & Sonderfälle

### Was tun, wenn ich eine andere Größe brauche?

Ändern Sie einfach die Argumente `200, 100` in `InsertShape`. Diese Zahlen stehen für Breite und Höhe in Punkten. Für ein Quadrat verwenden Sie identische Werte.

### Kann ich den Schatten stärker betonen?

Erhöhen Sie `BlurRadius` für eine weichere Kante, vergrößern Sie `Distance` für einen größeren Versatz oder senken Sie `Transparency` (z. B. `0.1`), um ihn dunkler zu machen.

### Wie füge ich dem Rechteck einen Rahmen hinzu?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### Ist das mit älteren Versionen von Aspose.Words kompatibel?

Ja. Die Klasse `ShadowFormat` gibt es bereits seit den frühen 2020‑Versionen. Bei einer sehr alten Version müssen Sie ggf. ein Upgrade durchführen, um alle Eigenschaften nutzen zu können.

## Tipps & Stolperfallen

- **Pro‑Tipp:** Größere Dokumente immer wieder freigeben (`doc.Dispose()`), besonders in Web‑Anwendungen, um native Ressourcen zu schonen.  
- **Achten Sie auf:** Die Verwendung eines relativen Pfads ohne passende Berechtigungen kann zu `UnauthorizedAccessException` führen. Nutzen Sie absolute Pfade oder stellen Sie sicher, dass der Anwendungspool Schreibrechte hat.  
- **Denken Sie daran:** Die Eigenschaft `FillColor` akzeptiert jedes `System.Drawing.Color`. Verwenden Sie z. B. `Color.FromArgb(255, 173, 216, 230)` für einen individuellen Pastellton.

## Nächste Schritte

Jetzt, wo Sie wissen, wie man ein **word document** erstellt, **rectangle shape** hinzufügt, **shape fill color** setzt und die **docx file** speichert, können Sie weiter experimentieren:

- Mehrere Formen einfügen und mit `RelativeHorizontalPosition` sowie `RelativeVerticalPosition` anordnen.  
- Das Rechteck mit Text über `Shape.TextBox` für Beschriftungen kombinieren.  
- Das gleiche Dokument nach PDF exportieren (`doc.Save("output.pdf")`) für die Verteilung.

Wenn Sie mehr über fortgeschrittene Grafiken erfahren möchten, schauen Sie sich die Unterstützung von Aspose.Words für **WordArt**, **Charts** und **Inline‑Images** an. Jede folgt demselben Muster: Knoten erstellen, Eigenschaften konfigurieren und speichern.

---

### TL;DR

- Verwenden Sie `Document` und `DocumentBuilder`, um ein **word document** zu **create**.  
- Rufen Sie `InsertShape(ShapeType.Rectangle, …)` auf, um **add rectangle shape** hinzuzufügen.  
- Setzen Sie `FillColor` für die gewünschte Hintergrundfarbe.  
- Aktivieren Sie `ShadowFormat` und passen Sie die Eigenschaften für ein professionelles Aussehen an.  
- Abschließend `document.Save("yourPath.docx")` ausführen, um die **docx file** zu **save**.

Viel Spaß beim Coden und beim Gestalten Ihrer Word‑Dateien!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}