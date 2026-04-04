---
category: general
date: 2026-04-04
description: Erstellen Sie eine Rechteckform in C# mit Aspose.Words und lernen Sie,
  wie Sie einen Schatten hinzufügen, den Schatten verwischen und den Schatten transparent
  machen – Schritt‑für‑Schritt‑Anleitung.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: de
og_description: Erstellen Sie ein Rechteck-Shape in C# mit Aspose.Words. Erfahren
  Sie, wie Sie einen Schatten hinzufügen, den Schatten verwischen und den Schatten
  transparent machen – in einem prägnanten Tutorial.
og_title: Rechteckform erstellen und Schatten in C# hinzufügen
tags:
- Aspose.Words
- C#
- Document Automation
title: Rechteckform erstellen und wie man Schatten in C# hinzufügt
url: /de/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform erstellen und Schatten in C# hinzufügen

Haben Sie schon einmal **eine Rechteckform** in einem Word‑Dokument erstellen wollen, waren sich aber nicht sicher, wie Sie ihr einen dezenten Drop‑Shadow geben? Sie sind nicht allein. In vielen Reporting‑ oder Branding‑Szenarien kann ein einfaches Rechteck mit einem weichen, halbtransparenten Schatten das Layout aufwerten, ohne viel Aufwand.

In diesem Tutorial gehen wir Schritt für Schritt durch **wie man ein Dokument erstellt** mit Aspose.Words, zeigen dann **wie man einen Schatten hinzufügt**, **wie man den Schatten verwischt** und sogar **wie man den Schatten transparent macht**. Am Ende haben Sie ein sofort ausführbares C#‑Snippet, das eine *.docx*-Datei mit einem schön schattierten Rechteck erzeugt – in wenigen Minuten.

## Was Sie benötigen

- .NET 6 oder höher (die API funktioniert auch mit .NET Framework 4.6+)
- Aspose.Words für .NET (die kostenlose Testversion reicht für dieses Beispiel)
- Ein Code‑Editor – Visual Studio, VS Code, Rider oder was Sie bevorzugen
- Grundkenntnisse in C# – nichts Aufwändiges, nur die Fähigkeit, eine Konsolen‑App zu starten

Wenn Sie das haben, können wir direkt zur Lösung springen.

## Schritt 1 – Wie man ein Dokument erstellt und die Zeichenfläche initialisiert

Zuerst benötigen Sie ein leeres `Document`‑Objekt. Denken Sie daran wie an ein leeres Blatt Papier, das Aspose.Words später in eine Word‑Datei verwandelt.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Warum instanziieren wir `Document` anstatt eine Vorlage zu laden? Von Grund auf neu zu beginnen stellt sicher, dass keine versteckten Stile oder Abschnitte unser Rechteck beeinflussen. Außerdem bleibt die Dateigröße klein – eine gute Gewohnheit, wenn Sie viele Dokumente in einer Schleife erzeugen.

## Schritt 2 – Rechteckform erstellen (der Kern unseres Hauptkeywords)

Jetzt **erstellen wir die Rechteckform**. Die Klasse `Shape` ist flexibel; Sie geben den Typ (Rectangle), die Größe und wie sie mit umgebendem Text umfließen soll, an.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Beachten Sie die Verwendung der Objekt‑Initialisierer‑Syntax – sie ist kompakt und reduziert die Gefahr, später eine Eigenschaft zu vergessen. Das Rechteck wird im ersten Absatz platziert, den wir im nächsten Schritt hinzufügen.

## Schritt 3 – Wie man einen Schatten hinzufügt und sein Aussehen anpasst

Einen Schatten hinzuzufügen ist nicht nur eine einzelne Zeile; Sie haben mehrere Eigenschaften, die Sie anpassen können. Hier kommen die sekundären Keywords **apply blur to shadow** und **make shadow transparent** ins Spiel.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Ein kurzer Hinweis zu den Zahlen: Ein `BlurRadius` von 5 erzeugt ein sanftes Verwischen; erhöhen Sie ihn auf 10 für einen weicheren Look oder reduzieren Sie ihn auf 2 für eine schärfere Kante. Der Wert `Transparency` liegt zwischen 0 (undurchsichtig) und 1 (unsichtbar). Passen Sie ihn an die Kontrastanforderungen Ihrer Marke an.

### Pro‑Tipp

Wenn Sie jemals einen farbigen Schatten benötigen (z. B. ein Unternehmens‑Blau), ersetzen Sie einfach `Color.DarkGray` durch `Color.FromArgb(80, 0, 120, 215)`. Das erste Argument ist der Alpha‑Kanal – halten Sie ihn niedrig für Subtilität.

## Schritt 4 – Die Form in das Dokument einfügen

Nachdem Rechteck und Schatten fertig sind, platzieren wir sie im ersten Absatz des Dokuments. Dieser Schritt sorgt dafür, dass die Form ganz oben im Dokument erscheint.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Warum der erste Absatz? Er ist ein sicherer Standard, der selbst funktioniert, wenn das Dokument komplett leer ist. Wenn Sie eine bestimmte Position haben (z. B. nach einer Überschrift), würden Sie diesen Knoten finden und die Form dort einfügen.

## Schritt 5 – Datei speichern und Ergebnis prüfen

Zum Schluss speichern wir das Dokument auf dem Datenträger. Sie können jeden gewünschten Pfad wählen; stellen Sie nur sicher, dass der Ordner existiert.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Wenn Sie *ShadowRectangle.docx* in Microsoft Word öffnen, sollten Sie ein 200 × 100‑Punkte‑Rechteck mit einem dunkelgrauen, leicht verwischten, zu 30 % transparenten Schatten sehen, der um drei Punkte nach rechts und unten versetzt ist. Der Effekt ist dezent, verleiht aber flachen Layouts Tiefe.

![Rechteckform mit Schatten in Aspose.Words](https://example.com/placeholder-image.png "Rechteckform mit Schatten in Aspose.Words")

*Bild‑Alt‑Text:* **Rechteckform mit Schatten in Aspose.Words** – das Bild zeigt das fertige Dokument mit dem schattierten Rechteck.

## Häufige Varianten und Sonderfälle

### Die Schattenfarbe dynamisch ändern

Wenn Ihre Anwendung Themes unterstützt, können Sie die Schattenfarbe aus einer Konfigurationsdatei holen:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Die Form nicht inline platzieren

Manchmal soll das Rechteck über dem Text schweben. Wechseln Sie `WrapType` zu `WrapType.Square` und setzen Sie `RelativeHorizontalPosition` auf `RelativeHorizontalPosition.Margin` für mehr Kontrolle.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Mehrere Seiten behandeln

Wenn Sie ein Rechteck auf jeder Seite benötigen, iterieren Sie über `doc.Sections` und hängen ein geklontes Shape an den ersten Absatz jeder Section an. Denken Sie daran, `rect.Clone(true)` aufzurufen, um auch die Schatteneinstellungen zu duplizieren.

## Zusammenfassung – Was wir erreicht haben

- **Rechteckform erstellt** mit Aspose.Words
- **Wie man einen Schatten hinzufügt** mit Farbe, Versatz, Verwischung und Transparenz
- Demonstriert **apply blur to shadow** und **make shadow transparent**
- Eine Word‑Datei gespeichert, die Sie sofort öffnen können

All das wurde mit nur wenigen Zeilen Code erreicht, was beweist, dass anspruchsvolle visuelle Anpassungen nicht immer schwere Grafik‑Bibliotheken erfordern.

## Was kommt als Nächstes?

- Experimentieren Sie mit anderen `ShapeType`s (Ellipse, Cloud usw.) und beobachten Sie, wie sich Schatten verhalten.
- Kombinieren Sie das Rechteck mit Textfeldern, um beschriftete Call‑outs zu erstellen.
- Tauchen Sie ein in **wie man ein Dokument erstellt** Vorlagen, die bereits Platzhalter für Shapes enthalten, und füllen Sie diese programmgesteuert.

Passen Sie den Blur‑Radius, die Farbe oder die Transparenz an, bis der Schatten genau zu Ihrer Designsprache passt. Die API ist nachsichtig, und Änderungen sind sofort sichtbar, wenn Sie die Konsolen‑App erneut ausführen.

Viel Spaß beim Coden und mögen Ihre Dokumente stets diese zusätzliche Tiefenwirkung besitzen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}