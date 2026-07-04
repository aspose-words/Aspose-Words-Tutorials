---
category: general
date: 2026-04-10
description: Wie man in C# einem Shape einen Schatten hinzufügt – lernen Sie, wie
  Sie einen Schattenwurf anwenden, die Transparenz ändern, die Unschärfe anpassen
  und einen Formschatten mit Aspose.Words hinzufügen.
draft: false
keywords:
- how to set shadow
- apply drop shadow
- how to change transparency
- how to adjust blur
- add shape shadow
language: de
og_description: Wie man einem Shape in C# einen Schatten hinzufügt – dieses Tutorial
  zeigt, wie man einen Drop‑Shadow anwendet, die Transparenz ändert, die Unschärfe
  anpasst und einen Shape‑Schatten mit klaren Codebeispielen hinzufügt.
og_title: Wie man in C# einen Schatten auf eine Form setzt – Komplettanleitung
tags:
- Aspose.Words
- C#
- Document Automation
title: Wie man in C# einen Schatten auf eine Form setzt – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/how-to-set-shadow-on-a-shape-in-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man einen Schatten auf einer Form in C# setzt – Vollständige Anleitung

Haben Sie sich jemals gefragt, **wie man einen Schatten** auf einer Form setzt, wenn Sie programmgesteuert ein Word‑Dokument erstellen? Sie sind nicht allein. Viele Entwickler stoßen auf ein Problem, wenn sie einen dezenten Drop‑Shadow für ein Textfeld, ein Logo oder ein Call‑Out‑Box benötigen, und die API‑Dokumentation ist etwas dürftig.  

In diesem Tutorial führen wir Sie durch den gesamten Prozess: vom Laden einer `.docx`, dem Abrufen der ersten `Shape`, über das Anwenden eines Drop‑Shadows, das Anpassen seiner Transparenz, das Einstellen des Blur‑Radius und schließlich das korrekte Positionieren. Am Ende haben Sie ein wiederverwendbares Snippet, das mit Aspose.Words .NET 2023 oder neuer funktioniert, und Sie verstehen *warum* jede Eigenschaft wichtig ist.

## Was Sie benötigen

- **Aspose.Words for .NET** (NuGet‑Paket `Aspose.Words`) – die Bibliothek, die uns die Klassen `Document`, `Shape` und `ShadowFormat` bereitstellt.  
- **.NET 6+** (oder .NET Framework 4.7.2) – jede aktuelle Runtime reicht.  
- Eine einfache Word‑Datei (`input.docx`), die bereits mindestens eine Form enthält, z. B. ein Textfeld.  
- Visual Studio, VS Code oder Ihre bevorzugte IDE.

Das war's. Keine zusätzlichen Drittanbieter‑Tools, kein COM‑Interop, nur reines C#.

![how to set shadow example](image-placeholder.png){:alt="Schatten auf einer Form in einem Word-Dokument setzen"}

## Wie man einen Schatten setzt – Übersicht

Die Kernidee hinter **wie man einen Schatten setzt** besteht darin, das `ShadowFormat`‑Objekt zu manipulieren, das einer `Shape` zugeordnet ist. Betrachten Sie `ShadowFormat` als ein Mini‑„Stylesheet“ für den Schatten selbst: Es teilt dem Renderer mit, ob der Schatten sichtbar ist, welche Farbe er haben soll, wie transparent er ist, wie unscharf und wo er relativ zur Form positioniert ist.  

Unten finden Sie das *komplette* ausführbare Programm. Sie können es gerne in eine Konsolen‑App kopieren, **F5** drücken und beobachten, wie der Schatten in der gespeicherten `output.docx` erscheint.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;                 // Core document classes
using Aspose.Words.Drawing;         // Shape & ShadowFormat

class ShadowDemo
{
    static void Main()
    {
        // -------------------------------------------------
        // Step 1: Load the Word document that contains the shape.
        // -------------------------------------------------
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // -------------------------------------------------
        // Step 2: Retrieve the first shape (e.g., a textbox) from the document.
        // -------------------------------------------------
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found – make sure input.docx has a textbox.");
            return;
        }

        // -------------------------------------------------
        // Step 3: Make the shadow visible.
        // -------------------------------------------------
        shape.ShadowFormat.Visible = true;

        // -------------------------------------------------
        // Step 4: Set the shadow colour to a dark gray.
        // -------------------------------------------------
        shape.ShadowFormat.Color = Color.DarkGray;

        // -------------------------------------------------
        // Step 5: Define the shadow's transparency (30 % transparent).
        // -------------------------------------------------
        shape.ShadowFormat.Transparency = 0.3;   // 0 = opaque, 1 = fully transparent

        // -------------------------------------------------
        // Step 6: Configure the blur radius (size) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Size = 6;            // Larger value = softer edges

        // -------------------------------------------------
        // Step 7: Set the offset distance and direction (angle) of the shadow.
        // -------------------------------------------------
        shape.ShadowFormat.Distance = 2;        // How far the shadow is from the shape
        shape.ShadowFormat.Angle = 45;          // Angle in degrees (0 = right, 90 = down)

        // -------------------------------------------------
        // Save the modified document.
        // -------------------------------------------------
        doc.Save("YOUR_DIRECTORY/output.docx");
        Console.WriteLine("Shadow applied successfully! Check output.docx.");
    }
}
```

### Warum diese Einstellungen wichtig sind

- **Visible** – Ohne Aktivierung dieses Flags werden alle anderen Eigenschaften ignoriert.  
- **Color** – Ein dunkles Grau ahmt einen typischen UI‑Drop‑Shadow nach; Sie können jede `Color` einsetzen.  
- **Transparency** – 0,3 erzeugt ein *weiches* Aussehen, während die Form lesbar bleibt.  
- **Size** – Steuert das Blur; ein Wert von 6 reicht meist für ein professionelles Gefühl.  
- **Distance & Angle** – Gemeinsam definieren sie den *Offset*; 2 pt bei 45° ergeben einen dezenten diagonalen Schatten.

Das ist das Wesentliche von **wie man einen Schatten setzt**. Als Nächstes zerlegen wir jedes Teil, sodass Sie **Drop‑Shadow anwenden**, **Transparenz ändern**, **Blur anpassen** und **Form‑Schatten hinzufügen** isoliert durchführen können.

---

## Drop‑Shadow auf eine Form anwenden

Wenn Leute fragen, „wie **apply drop shadow** in C#?“ (wie setze ich Drop‑Shadow in C#?), benötigen sie oft nur den Sichtbarkeits‑Schalter und eine Farbe. Das folgende Snippet isoliert diese beiden Zeilen:

```csharp
shape.ShadowFormat.Visible = true;          // Turns the shadow on
shape.ShadowFormat.Color   = Color.Black;   // Classic black drop shadow
```

> **Pro‑Tipp:** Wenn Sie ältere Word‑Versionen (2003‑2007) anvisieren, bleiben Sie bei Standardfarben. Einige exotische ARGB‑Werte können vom alten Renderer ignoriert werden.

---

## Wie man die Transparenz des Schattens ändert

Transparenz wird als **Float zwischen 0 und 1** angegeben. Ein Wert von **0** bedeutet einen vollständig undurchsichtigen Schatten; **1** macht ihn unsichtbar. Die meisten Designer setzen sich bei **0,2‑0,4** für ein natürliches Aussehen fest.

```csharp
shape.ShadowFormat.Transparency = 0.35; // 35 % transparent
```

### Randfälle

- **Negative values** – Aspose.Words wird sie auf 0 begrenzen, aber es ist besser, die Eingabe zu validieren.  
- **Values > 1** – Auf 1 begrenzt, wodurch der Schatten effektiv ausgeblendet wird.

Wenn Sie Benutzern erlauben möchten, einen Prozentsatz auszuwählen, konvertieren Sie ihn zuerst:

```csharp
float percent = 30;                     // User enters 30 %
shape.ShadowFormat.Transparency = percent / 100f;
```

---

## Wie man das Blur (Size) des Schattens anpasst

Die Eigenschaft **Size** steuert den Blur‑Radius. Größere Zahlen erzeugen einen weicheren, stärker diffundierten Schatten. Sie wird in Punkten (pt) und nicht in Pixeln gemessen.

```csharp
shape.ShadowFormat.Size = 10;  // A generous blur for a “soft” effect
```

#### Wann ein kleiner vs. großer Blur verwendet wird

- **Small blur (2‑4 pt)** – Gut für UI‑Style‑Callouts, bei denen Sie eine scharfe Kante wünschen.  
- **Large blur (8‑12 pt)** – Geeignet für gedruckte Berichte oder wenn die Form weit vom Hintergrund entfernt ist.

## Form‑Schatten hinzufügen – Positionierung und Richtung

Das letzte Element von **add shape shadow** ist der Offset. Zwei Eigenschaften arbeiten zusammen:

| Property | Meaning |
|----------|---------|
| **Distance** | Wie weit der Schatten von der Form entfernt liegt (in Punkten). |
| **Angle**    | Richtung des Offsets (0° = rechts, 90° = unten, 180° = links, 270° = oben). |

Beispiel, das einen dezenten Schatten unten‑rechts erzeugt:

```csharp
shape.ShadowFormat.Distance = 1.5; // Slight lift
shape.ShadowFormat.Angle    = 135; // Down‑left direction (135°)
```

Sie können mit Winkeln experimentieren, um Licht aus verschiedenen Richtungen zu simulieren. Ein gängiger Trick ist, dem Benutzer zu erlauben, eine „Lichtquelle“ aus einem Dropdown auszuwählen und sie einem Winkelwert zuzuordnen.

## Vollständiges funktionierendes Beispiel (Alle Schritte kombiniert)

Unten finden Sie dasselbe Programm wie zuvor, jedoch mit **extra Kommentaren**, die die Logik kristallklar machen. Kopieren Sie dies in `Program.cs` und führen Sie es aus; die Ausgabedatei enthält ein Textfeld mit einem perfekt abgestimmten Schatten.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeShadowDemo
{
    class Program
    {
        static void Main()
        {
            // Load the source document (must contain at least one shape)
            Document doc = new Document("YOUR_DIRECTORY/input.docx");

            // Grab the first shape we encounter – usually a textbox or picture
            Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
            if (shape == null)
            {
                Console.WriteLine("No shape found in the document.");
                return;
            }

            // ---------- Apply Drop Shadow ----------
            shape.ShadowFormat.Visible = true;          // Turn it on
            shape.ShadowFormat.Color   = Color.DarkGray; // Soft dark colour

            // ---------- How to Change Transparency ----------
            shape.ShadowFormat.Transparency = 0.3; // 30 % transparent – looks natural

            // ---------- How to Adjust Blur ----------
            shape.ShadowFormat.Size = 6; // Moderate blur for a professional feel

            // ---------- Add Shape Shadow (position) ----------
            shape.ShadowFormat.Distance = 2; // Slight offset
            shape.ShadowFormat.Angle    = 45; // Diagonal down‑right

            // Save the result
            doc.Save("YOUR_DIRECTORY/output.docx");
            Console.WriteLine("Document saved with shadow. Open output.docx to verify.");
        }
    }
}
```

**Erwartetes Ergebnis:** Öffnen Sie `output.docx`. Das erste Textfeld zeigt einen dunkelgrauen, zu 30 % transparenten Schatten, der leicht unscharf ist (size = 6) und um 2 pt bei einem Winkel von 45° versetzt ist. Der Effekt ist dezent, aber bemerkbar – genau das, was die meisten UI‑Designer anstreben.

## Häufige Fragen & Stolperfallen

- **„Funktioniert das auch mit Bildern?“**  
  Ja. Jede `Shape` – ob Textfeld, Bild oder Auto‑Shape – stellt `ShadowFormat` bereit. Ersetzen Sie einfach die Logik zum Abrufen der Form durch den entsprechenden Index oder Namen.

- **„Was, wenn das Dokument mehrere Formen enthält?“**  
  Durchlaufen Sie `doc.GetChildNodes(NodeType.Shape, true)` und wenden Sie dieselben Einstellungen auf jede an. Sie können auch nach `shape.Name` oder `shape

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}