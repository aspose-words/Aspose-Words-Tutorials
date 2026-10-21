---
category: general
date: 2026-07-29
description: Zeichnen Sie ein Rechteck in Word mit Aspose.Words. Erfahren Sie, wie
  Sie ein Rechteck‑Shape hinzufügen, ein Linien‑Shape hinzufügen und mehrere Shapes
  in einem einzigen Dokument verwalten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: de
lastmod: 2026-07-29
og_description: Rechteck in Word mit Aspose.Words zeichnen. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung,
  um ein Rechteck‑Shape, ein Linien‑Shape hinzuzufügen und mühelos mit mehreren Shapes
  in Word zu arbeiten.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Rechteck in Word zeichnen – Formen hinzufügen meistern
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Rechteck in Word zeichnen – Formen in Word mit Aspose hinzufügen
url: /de/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Kompletter Leitfaden zum Hinzufügen von Formen in Word

Haben Sie sich schon einmal gefragt, wie man **draw rectangle word** Dokumente erzeugt, ohne jedes Mal die Benutzeroberfläche zu öffnen? Sie sind nicht allein. Viele Entwickler müssen Word‑Dateien on‑the‑fly generieren, und der einfachste Weg ist, einer Bibliothek die schwere Arbeit zu überlassen. In diesem Tutorial zeigen wir Ihnen genau **wie man Formen hinzufügt** – insbesondere ein Rechteck und eine Linie – mit Aspose.Words für .NET, und wir konzentrieren uns dabei auf den Ausdruck *draw rectangle word*, damit Sie nie den Überblick verlieren.

Stellen Sie sich das vor wie ein Mini‑Art‑Studio, das in Ihrem Code lebt. Am Ende können Sie **Rechteck‑Form hinzufügen**, **Linien‑Form hinzufügen** und sie sogar zu **multiple shapes word**‑Gruppen kombinieren. Keine UI, kein manuelles Herumfummeln, nur sauberer, wiederholbarer C#‑Code.

## Was Sie lernen werden

- Ein neues Word‑Dokument mit Aspose.Words einrichten.  
- Einen **GroupShape** erstellen, der mehrere Objekte aufnehmen kann.  
- **add rectangle shape** und **add line shape** innerhalb dieser Gruppe **hinzufügen**.  
- Die gruppierten Formen in den Dokumentenkörper einfügen.  
- Die Datei speichern und das Ergebnis sofort sehen.  

Wenn Sie mit grundlegenden C#‑Kenntnissen vertraut sind und eine Kopie von Aspose.Words besitzen, sind Sie startklar. Keine zusätzlichen NuGet‑Pakete über die Kernbibliothek hinaus werden benötigt.

> **Profi‑Tipp:** Aspose.Words funktioniert mit .NET 6, .NET 7 und .NET Framework 4.6+. Wählen Sie die Runtime, die zu Ihrem Projekt passt.

![draw rectangle word Beispiel](https://example.com/placeholder-image.png "draw rectangle word – gruppierte Formen in einer Word-Datei")

## draw rectangle word – Dokument einrichten

Bevor wir **draw rectangle word** ausführen können, benötigen wir eine saubere Leinwand. Die `Document`‑Klasse ist diese Leinwand; der `DocumentBuilder` ist unser Pinsel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Die beiden Zeilen oben erzeugen ein frisches, im Speicher befindliches `.docx`. Noch nichts wird auf die Festplatte geschrieben, sodass Sie ohne Dateisystem‑Unordnung experimentieren können.

## Wie man Formen hinzufügt – Einen GroupShape‑Container erstellen

Wenn Sie **multiple shapes word** als eine Einheit verhalten lassen wollen – gemeinsam verschieben, gemeinsam rotieren – packen Sie sie in einen `GroupShape`. Denken Sie an eine Gruppe wie an einen Ordner, der andere Formen enthält.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Warum eine Gruppe? Weil Sie später **add rectangle shape** und **add line shape** hinzufügen und dann zusammen verschieben wollen. Ohne Gruppe müssten Sie jede Form einzeln neu positionieren.

## add rectangle shape – Ein Rechteck in die Gruppe einfügen

Jetzt, wo der Container existiert, **add rectangle shape** wir. Ein Rechteck ist ein `Shape`, dessen `ShapeType` auf `Rectangle` gesetzt ist.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Beachten Sie, dass die Werte für `Left` und `Top` relativ zum Ursprung der Gruppe und nicht zur Seite sind. Das erleichtert das präzise Ausrichten der Formen. Das Rechteck erscheint in der Nähe der oberen linken Ecke der Gruppe.

## add line shape – Eine Linie zur selben Gruppe hinzufügen

Eine Linie ist einfach ein weiteres `Shape`, aber ihr `ShapeType` ist `Line`. Wir positionieren sie unterhalb des Rechtecks.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Da die Höhe der Linie null ist, bestimmt die `Top`‑Eigenschaft, wo die Linie vertikal liegt. Die `Width` steuert, wie lang die Linie horizontal verläuft.

## multiple shapes word – Die Gruppe in den Dokumentenkörper einfügen

Wir haben nun eine Gruppe, die **add rectangle shape** und **add line shape** enthält. Der letzte Schritt ist, das Ganze in das Dokument zu legen.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` platziert die Gruppe exakt dort, wo der `DocumentBuilder` gerade positioniert ist. Wenn Sie sie an einem bestimmten Absatz benötigen, bewegen Sie den Builder zuerst mit `builder.MoveToParagraph(index)`.

## Ergebnis speichern – Die draw rectangle word‑Ausgabe sehen

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Öffnen Sie die erzeugte Datei in Microsoft Word und Sie sehen eine einzelne Gruppe, die ein Rechteck und eine Linie enthält. Sie können die Gruppe anklicken, verschieben oder sogar die Größe ändern – alle Formen bewegen sich gemeinsam. Das ist die Stärke von **multiple shapes word**.

### Erwartetes Ergebnis

- Eine `.docx`‑Datei namens `GroupShape.docx`.  
- Eine Seite mit einem gruppierten Rechteck (120 × 80 pt) nahe der oberen linken Ecke.  
- Eine horizontale Linie (150 pt lang) direkt unter dem Rechteck.  
- Beide Formen sind als ein einzelnes Objekt auswählbar.

Wenn Sie die Gruppe doppelklicken, lässt Word Sie jede Form einzeln bearbeiten – ideal für Feineinstellungen.

## Häufige Fragen & Sonderfälle

**Was, wenn ich mehr als zwei Formen brauche?**  
Rufen Sie einfach `group.AppendChild(yourShape)` für jedes weitere Objekt auf. Die Gruppe kann beliebig viele Formen aufnehmen und eignet sich daher für komplexe Diagramme.

**Kann ich die Füllfarbe des Rechtecks ändern?**  
Natürlich. Nach dem Erzeugen des Rechtecks setzen Sie `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Das funktioniert bei jeder Form, die Füllungen unterstützt.

**Muss ich `Height = 0` für eine Linie setzen?**  
Ja, für eine gerade horizontale Linie sollte die Höhe null sein. Für eine vertikale Linie setzen Sie `Width = 0` und geben `Height` einen positiven Wert.

**Funktioniert das mit .doc‑Dateien (Word 97‑2003)?**  
Aspose.Words kann in das ältere `.doc`‑Format speichern, aber einige moderne Form‑Features können eingeschränkt sein. Für volle Funktionsfähigkeit bleiben Sie bei `.docx`.

**Wie rotiere ich die gesamte Gruppe?**  
Setzen Sie `group.Rotation = 45;` (Grad) bevor Sie sie einfügen. Die Rotation wird auf jede Kind‑Form angewendet.

## Zusammenfassung – Formen programmgesteuert in Word hinzufügen

- **draw rectangle word** beginnt mit dem Erzeugen eines `Document` und `DocumentBuilder`.  
- Erstellen Sie einen **GroupShape**, um **multiple shapes word** zu halten.  
- **add rectangle shape** und **add line shape** werden der Gruppe hinzugefügt.  
- Fügen Sie die Gruppe mit `builder.InsertNode` in den Body ein.  
- Speichern Sie die Datei und öffnen Sie sie, um das visuelle Ergebnis zu prüfen.

Damit ist der gesamte Workflow in einem leicht lesbaren Code‑Listing zusammengefasst.

## Nächste Schritte & verwandte Themen

Jetzt, wo Sie **wie man Formen hinzufügt** kennen, können Sie Folgendes erkunden:

- **add rectangle shape** mit abgerundeten Ecken (`ShapeType.Rectangle` + `CornerRadius`).  
- Linien mit verschiedenen Strichmustern stylen (`line.LineFormat.DashStyle`).  
- Bilder neben Formen einbetten für reichhaltigere Berichte.  
- **multiple shapes word** nutzen, um Flussdiagramme oder einfache UML‑Diagramme zu bauen.  

Jedes dieser Themen baut natürlich auf dem hier gelegten Fundament auf und folgt dem gleichen Muster: Formen erstellen, konfigurieren und bei Bedarf gruppieren.

---

Viel Spaß beim Coden! Wenn Sie auf Eigenheiten stoßen oder einen coolen Anwendungsfall teilen möchten, hinterlassen Sie unten einen Kommentar. Ihr Feedback hilft uns allen, die Kunst von **draw rectangle word** und darüber hinaus zu meistern.


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}