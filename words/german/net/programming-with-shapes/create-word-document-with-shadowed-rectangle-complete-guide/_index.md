---
category: general
date: 2026-04-21
description: Erstelle ein Word-Dokument mit einem gestalteten Rechteck und Schatten.
  Erfahre, wie man Schatten hinzufügt, ein Rechteck einfügt, die Schattenfarbe festlegt
  und mehr in C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: de
og_description: Erstelle ein Word‑Dokument und füge in C# ein rechteckiges Shape mit
  Schatten hinzu. Befolge diese Anleitung, um Schattenfarbe, Unschärfe und Versatzwerte
  einfach einzustellen.
og_title: Word‑Dokument mit schattiertem Rechteck erstellen – Schritt für Schritt
tags:
- Aspose.Words
- C#
- Document Automation
title: Word-Dokument mit schattiertem Rechteck erstellen – Komplettanleitung
url: /de/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines Word-Dokuments mit schattiertem Rechteck – Komplettanleitung

Haben Sie jemals ein **Word-Dokument erstellen** müssen, das etwas professioneller aussieht als eine einfache Textseite? Vielleicht erstellen Sie eine Berichtsvorlage oder einen Flyer und ein einfaches Rechteck mit einem dezenten Schatten würde ausreichen. In diesem Tutorial führen wir Sie Schritt für Schritt durch genau das – wie man eine Rechteckform einfügt, den Schatten aktiviert und dessen Farbe, Weichzeichnung und Versätze anpasst – alles mit C# und Aspose.Words.

Wir behandeln außerdem **wie man Schatten hinzufügt** in einer Weise, die sowohl für Word 2016, 2019 als auch für die neueste Office 365‑Version funktioniert. Am Ende haben Sie eine speicherbereite *.docx*-Datei, die ein schön schattiertes Rechteck zeigt, und Sie verstehen das „Warum“ hinter jeder eingestellten Eigenschaft.

## Voraussetzungen

- .NET 6 (oder eine aktuelle .NET Framework‑Version)  
- Aspose.Words für .NET NuGet‑Paket (`Install-Package Aspose.Words`)  
- Grundlegende Kenntnisse der C#‑Syntax  
- Eine IDE wie Visual Studio (jedoch funktioniert jeder Editor)

Keine zusätzlichen Bibliotheken sind erforderlich; alles andere ist in Aspose.Words enthalten.

## Schritt 1 – Dokument und Builder initialisieren (Word-Dokument erstellen)

Um programmgesteuert ein **Word-Dokument zu erstellen**, beginnen Sie mit der Klasse `Document`. Der `DocumentBuilder` ist Ihr Pinsel; er ermöglicht das Hinzufügen von Text, Formen und anderen Elementen.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Warum das wichtig ist:* Das `Document`‑Objekt repräsentiert die gesamte .docx‑Datei. Ohne es haben Sie keinen Ort, an dem Sie das Rechteck oder dessen Schatten anbringen können.

## Schritt 2 – Rechteckform einfügen (Insert Rectangle Shape)

Jetzt fügen wir tatsächlich **eine Rechteckform ein**. Die Methode `InsertShape` erwartet ein `ShapeType`‑Enum sowie Breite und Höhe in Punkten.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Profi‑Tipp:* 1 Punkt ≈ 1/72 Zoll, also sind 200 pts etwa 2,78 Zoll breit. Passen Sie diese Werte an Ihr Layout an.

## Schritt 3 – Schatten aktivieren (How to Add Shadow)

Schatten sind standardmäßig deaktiviert. Setzen Sie das `Visible`‑Flag, um sie zu aktivieren.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Was passiert?* Wenn `Visible` true ist, rendert Word einen Drop‑Shadow basierend auf den nächsten eingestellten Eigenschaften.

## Schritt 4 – Aussehen des Schattens anpassen (Set Shadow Color, Blur, Offsets)

Hier **setzen Sie die Schattenfarbe**, den Weichzeichnungsradius und die X/Y‑Versätze. Experimentieren Sie gern – unterschiedliche Werte erzeugen ein sanftes Leuchten, einen tiefen Schatten oder sogar einen „schwebenden“ Effekt.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Warum diese Zahlen?* Eine Weichzeichnung von 5 pts erzeugt einen sanften, federartigen Rand, während ein Versatz von 4 pts den Schatten nach unten‑rechts verschiebt und eine Lichtquelle oben‑links simuliert. Ändern Sie `Color` zu `Color.Black` für stärkeren Kontrast oder verwenden Sie `Color.FromArgb(128, 0, 0, 0)` für ein halbtransparentes Schwarz.

### Randfälle & Variationen

- **Kein Blur:** Setzen Sie `Blur = 0` für einen scharfen, kantigen Schatten.  
- **Negative Versätze:** Verwenden Sie `OffsetX = -4`, um den Schatten nach links zu verschieben.  
- **Verschiedene Formen:** Die gleichen Schatten‑Eigenschaften funktionieren für Kreise, Dreiecke oder sogar frei gezeichnete Formen – ändern Sie einfach `ShapeType` in Schritt 2.  
- **Kompatibilität:** Aspose.Words schreibt die Schatten‑Daten im Office Open XML‑Format, das mit Word 2010‑2021 und Office 365 funktioniert.

## Schritt 5 – Dokument speichern (Word-Dokument erstellen)

Abschließend speichern Sie die Datei auf dem Datenträger. Sie können jedes unterstützte Format wählen (`.docx`, `.pdf`, `.odt`, …), aber für diese Anleitung bleiben wir beim klassischen Word‑Format.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Wenn Sie **ShadowRectangle.docx** in Microsoft Word öffnen, sehen Sie ein graues Rechteck mit einem dezenten, unscharfen Schatten, der nach unten‑rechts versetzt ist – genau das, was wir programmiert haben.

### Erwartete Ausgabe

- Eine einseitige *.docx*-Datei.  
- Ein 200 pt × 100 pt großes Rechteck, zentriert dort, wo der Cursor beim Aufruf von `InsertShape` stand.  
- Ein grauer Schatten, der 4 pts nach rechts und 4 pts nach unten erscheint, mit einer Weichzeichnung von 5 pt.

Falls die Form nicht zentriert erscheint, können Sie den Cursor mit `builder.MoveTo` vor dem Einfügen verschieben oder nach dem Einfügen die Eigenschaften `Left` und `Top` der Form anpassen.

## Häufige Fragen & Fehlersuche

**Q: Der Schatten wird in Word nicht angezeigt.**  
A: Stellen Sie sicher, dass `ShadowFormat.Visible` `true` ist. Vergewissern Sie sich außerdem, dass Sie eine aktuelle Version von Aspose.Words verwenden (die Schatten‑Funktion wurde in Version 20.3 hinzugefügt).  

**Q: Kann ich einen Farbverlauf auf den Schatten anwenden?**  
A: Nicht direkt über `ShadowFormat`. Die Word‑Benutzeroberfläche unterstützt Verlaufsschatten, aber das Open‑XML‑Schema (nach dem Aspose.Words arbeitet) stellt nur einfarbige Schatten bereit. Sie müssten das zugrunde liegende XML manuell bearbeiten – ein fortgeschritteneres Szenario.  

**Q: Was, wenn ich ein transparentes Rechteck nur mit einem Schatten benötige?**  
A: Setzen Sie nach dem Einfügen `rectangle.FillColor = Color.Transparent;`. Der Schatten wird weiterhin gerendert, da er unabhängig von der Füllung ist.

## Profi‑Tipps für Produktionscode

- **Builder wiederverwenden:** Wenn Sie mehrere Formen hinzufügen, behalten Sie dieselbe `DocumentBuilder`‑Instanz – das Erstellen einer neuen Instanz für jede Form verursacht unnötigen Overhead.  
- **Batch‑Speicherungen:** Speichern Sie einmal nach allen Änderungen; häufige I/O verlangsamt die Generierung großer Dokumente.  
- **Fehlerbehandlung:** Umwickeln Sie den gesamten Block mit einem `try / catch` und protokollieren Sie `Aspose.Words`‑Ausnahmen; diese enthalten oft hilfreiche Zeilennummern, wenn die Dokumentvorlage beschädigt ist.

## Nächste Schritte (Verwandte Themen)

- **Wie man Schatten** zu Bildern oder Textfeldern hinzufügt (ähnliche `ShadowFormat`‑Verwendung).  
- **Rechteckform einfügen** in einer Tabellenzelle für benutzerdefiniertes Zellenstyling.  
- **Rechteck in Word erstellen** mittels Word‑eigenem XML (für diejenigen, die rohes Open XML bevorzugen).  
- **Schattenfarbe setzen** dynamisch basierend auf Benutzereingaben oder Designfarben.

Experimentieren Sie mit verschiedenen Farben, Weichzeichnungsradien und Versätzen – vielleicht ein sanftes blaues Leuchten für einen Geschäftsbericht oder ein tiefschwarzer Schatten für einen dramatischen Flyer. Die Möglichkeiten sind endlos, und die Code‑Änderungen sind minimal.

---

### Kurze Zusammenfassung

- Wir **haben ein Word-Dokument** von Grund auf erstellt.  
- Wir **haben eine Rechteckform eingefügt** und deren Schatten aktiviert.  
- Wir **haben die Schattenfarbe**, Weichzeichnung und Versätze gesetzt, um ein professionelles Aussehen zu erzielen.  
- Wir haben die Datei gespeichert, bereit zur Verteilung.

Jetzt haben Sie eine solide Grundlage, um jedem Word‑Automatisierungsprojekt visuelle Akzente zu verleihen. Haben Sie weitere Ideen? Hinterlassen Sie einen Kommentar, und wir führen die Diskussion fort. Viel Spaß beim Programmieren!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}