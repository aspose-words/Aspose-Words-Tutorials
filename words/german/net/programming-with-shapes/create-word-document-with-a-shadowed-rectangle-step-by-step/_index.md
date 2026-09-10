---
category: general
date: 2026-01-13
description: Erstellen Sie ein Word-Dokument mit Aspose.Words und lernen Sie, wie
  man ein Rechteck einfügt, wie man einen Schatten hinzufügt und den Formschatten
  in C# anwendet. Vollständiges Beispiel enthalten.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: de
og_description: Erstellen Sie ein Word‑Dokument mit Aspose.Words, sehen Sie, wie man
  ein Rechteck einfügt und wie man einen Schatten hinzufügt. Folgen Sie dem vollständigen
  C#‑Beispiel.
og_title: Word-Dokument mit schattiertem Rechteck erstellen – Vollständige Anleitung
tags:
- Aspose.Words
- C#
- Document Automation
title: Word‑Dokument mit schattiertem Rechteck erstellen – Schritt‑für‑Schritt‑Anleitung
url: /de/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines Word-Dokuments mit einem schattierten Rechteck – Schritt‑für‑Schritt‑Anleitung

Haben Sie jemals ein **Word-Dokument erstellen** müssen, das ein schön schattiertes Rechteck enthält, waren sich aber nicht sicher, wo Sie anfangen sollen? Sie sind nicht allein – viele Entwickler stoßen beim ersten Arbeiten mit Aspose.Words auf dieselbe Hürde.  

In diesem Tutorial führen wir Sie durch alles, was Sie benötigen, um **Word-Dokumente** programmgesteuert **ein Rechteck einfügen** zu können und zeigen **wie man einen Schatten hinzufügt**, damit die Form wirklich hervorsticht. Am Ende haben Sie ein einsatzbereites C#‑Snippet, das Sie in jedes .NET‑Projekt einbinden können.

## Was Sie lernen werden

- Den genauen Code, um **wie man eine Form einfügt** (ein Rechteck) in eine Word‑Datei.
- Die Eigenschaften, die Sie anpassen müssen, um **Formschatten hinzuzufügen** und ihr Aussehen zu steuern.
- Wie Sie das Ergebnis speichern und überprüfen, dass der Schatten sichtbar ist.
- Einige praktische Tipps und Hinweise zu Randfällen, die Ihnen später Kopfschmerzen ersparen.

Keine externe Dokumentation erforderlich – alles ist hier zu finden.

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes haben:

1. **.NET 6.0** (oder eine aktuelle .NET‑Version) installiert.  
2. Eine **Lizenz** für Aspose.Words für .NET, oder Sie können den kostenlosen Evaluierungsmodus zum Testen verwenden.  
3. Eine Entwicklungsumgebung – Visual Studio 2022 funktioniert hervorragend, aber jeder Editor, der C# kompilieren kann, reicht aus.

Das war’s. Keine zusätzlichen NuGet‑Pakete über `Aspose.Words` hinaus werden benötigt.

## Schritt 1 – Projekt einrichten und Aspose.Words referenzieren

Zuerst erstellen Sie eine neue Konsolenanwendung und fügen das Aspose.Words‑Paket hinzu:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Pro‑Tipp:** Wenn Sie die kostenlose Testversion verwenden, denken Sie daran, `License.SetLicense` mit Ihrer Lizenzdatei aufzurufen; andernfalls fügt die Bibliothek ein Wasserzeichen hinzu.

## Schritt 2 – DocumentBuilder initialisieren

Jetzt beginnen wir mit dem eigentlichen **Word-Dokument erstellen** Prozess. Die Klasse `Document` liefert uns eine leere Leinwand, und `DocumentBuilder` ermöglicht es uns, darauf zu zeichnen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Warum benötigen wir einen Builder? Er abstrahiert die Low‑Level‑OpenXML‑Details, sodass Sie sich auf *was* Sie wollen konzentrieren können, anstatt auf *wie* die Datei strukturiert ist. Das ist das Kernstück, um **wie man eine Form einfügt** schnell zu erledigen.

## Schritt 3 – Rechteck‑Form einfügen

Hier fügen wir tatsächlich **Rechteck‑Form ein**. Das Rechteck wird 150 × 100 Punkte groß sein (ungefähr 2 in × 1,3 in).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Die Methode `InsertShape` gibt ein `Shape`‑Objekt zurück, das wir weiter anpassen können. An diesem Punkt ist das Rechteck nur ein einfarbiger weißer Kasten – noch kein Schatten.

## Schritt 4 – Wie man einen Schatten hinzufügt (Formschatten hinzufügen)

Einen Schatten hinzuzufügen ist überraschend einfach, sobald Sie wissen, welche Eigenschaften Sie anpassen müssen. Das Objekt `ShadowFormat` steuert Sichtbarkeit, Farbe, Unschärfe, Versatz und Größe.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Dieser Block beantwortet **wie man einen Schatten hinzufügt** in einfachem Englisch: Schalten Sie ihn ein, wählen Sie eine Farbe, passen Sie Transparenz, Versatz, Unschärfe und Größe an. Sie können mit diesen Zahlen experimentieren, um einen starken Drop‑Shadow oder einen hauchdünnen zu erhalten.

### Häufige Variationen

- **Verschiedene Farben:** Verwenden Sie `Color.Black` für einen klassischen Drop‑Shadow oder `Color.BlueViolet` für einen stilisierten Effekt.  
- **Keine Unschärfe:** Setzen Sie `BlurRadius = 0` für eine klare, scharfe Kante.  
- **Größere Versätze:** Erhöhen Sie `OffsetX`/`OffsetY`, um den Schatten weiter von der Form zu entfernen.

## Schritt 5 – Dokument speichern und überprüfen

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Die Datei wird ein standardmäßiges `.docx` sein, das jeder moderne Textverarbeitungsprogramm öffnen kann.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Öffnen Sie das resultierende *ShadowRectangle.docx* in Microsoft Word. Sie sollten ein Rechteck mit einem weichen grauen Schatten sehen, der nach unten rechts versetzt ist – genau das, was der Code angegeben hat.

> **Erwartete Ausgabe:** Eine einseitige Word‑Datei, die ein 150 × 100‑Punkte‑Rechteck mit einem 30 % transparenten grauen Schatten enthält, versetzt um 5 pt, unscharf um 4 pt und mit einer Größe von 75 % der Form.

## Vollständiges funktionierendes Beispiel

Wenn wir alles zusammenfügen, hier das vollständige, sofort ausführbare Programm:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Führen Sie das Programm (`dotnet run`) aus und Sie erhalten eine neue Word‑Datei mit einem schön schattierten Rechteck – perfekt für Berichte, Zertifikate oder jede visuelle Markierung, die Sie benötigen.

## Häufig gestellte Fragen (FAQs)

**F: Kann ich andere Formen (Ellipse, Stern) einfügen und dennoch denselben Schatten‑Code verwenden?**  
A: Absolut. Die Methode `InsertShape` akzeptiert jeden `ShapeType`‑Enum‑Wert. Sobald Sie eine `Shape`‑Instanz haben, funktionieren die `ShadowFormat`‑Eigenschaften identisch, sodass **wie man einen Schatten hinzufügt** formunabhängig ist.

**F: Was ist, wenn ich den Schatten auf beiden Seiten der Form brauche?**  
A: Aspose.Words unterstützt nur einen einzelnen Drop‑Shadow pro Form. Um einen doppelseitigen Effekt zu simulieren, duplizieren Sie die Form, versetzen jede Kopie unterschiedlich und setzen `ShadowFormat.Visible` einer Kopie auf `false`, während Sie den Schatten der anderen sichtbar lassen.

**F: Funktioniert das auf .NET Framework 4.8?**  
A: Ja. Die API ist versionsunabhängig; referenzieren Sie einfach die passende Aspose.Words‑DLL für Ihr Ziel‑Framework.

## Tipps & Fallstricke

- **Vergessen Sie nicht, `Visible = true` zu setzen** – sonst werden die Schatten‑Eigenschaften ignoriert.  
- **Transparenzwerte liegen zwischen 0.0 (undurchsichtig) und 1.0 (vollständig transparent).** Ein häufiger Fehler ist die Verwendung von `30` anstelle von `0.3`.  
- **Das Speichern in einen schreibgeschützten Ordner wirft eine Ausnahme aus.** Stellen Sie sicher, dass das Ausgabeverzeichnis beschreibbar ist.

## Nächste Schritte

Jetzt, da Sie **wie man eine Form einfügt**, **Formschatten hinzufügt** und **Word-Dokumente** mit Aspose.Words erstellen, möchten Sie vielleicht Folgendes erkunden:

- **Text innerhalb des Rechtecks hinzufügen** mit `builder.InsertParagraph()` bevor die Form eingefügt wird.  
- **Verlaufsfüllungen** oder **gemusterte Rahmen** anwenden für ein reichhaltigeres visuelles Styling.  
- Die automatische Erstellung mehrerer Seiten, jede mit einer anderen schattierten Form, um dynamische Berichte zu erstellen.

Fühlen Sie sich frei zu experimentieren – das Ändern der Farbe, Unschärfe oder Größe des Schattens kann das Aussehen Ihres Dokuments dramatisch verändern.

---

*Bereit, dies in die Produktion zu übernehmen? Holen Sie sich den Code, passen Sie die Parameter an und sehen Sie, wie Ihre Word‑Dateien in Sekunden einen professionellen Glanz erhalten.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}