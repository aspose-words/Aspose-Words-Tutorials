---
category: general
date: 2026-09-21
description: Erfahren Sie, wie Sie Formen in Word mit Aspose.Words für C# gruppieren.
  Diese Schritt‑für‑Schritt‑Anleitung behandelt das Erstellen, Positionieren und Speichern
  von gruppierten Formen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: de
lastmod: 2026-09-21
og_description: Gruppieren Sie Formen in Word mit Aspose.Words für C#. Folgen Sie
  diesem kurzen Tutorial, um gruppierte Formen programmgesteuert zu erstellen, zu
  positionieren und zu speichern.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Formen in Word gruppieren mit Aspose.Words – vollständiger C#‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man Formen in Word mit Aspose.Words für C# gruppiert
url: /de/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in Word mit Aspose.Words für C# gruppiert

Wenn Sie **Formen in Word** programmgesteuert **gruppieren** müssen, macht Aspose.Words das ganz einfach. Dieses Tutorial zeigt Ihnen, wie Sie zwei Rechteck‑Formen erstellen, nebeneinander platzieren, sie zu einer `GroupShape`‑Instanz kombinieren und das Ergebnis als DOCX‑Datei speichern.

Sie erhalten ein vollständiges, ausführbares Beispiel, Erklärungen, warum jeder Schritt wichtig ist, und Tipps zum Umgang mit gängigen Sonderfällen wie überlappenden Formen oder dynamischer Größe. Am Ende dieses Leitfadens können Sie die Form‑Gruppierung in jedes Word‑Automatisierungsprojekt integrieren.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* .NET 6.0 (oder neuer) installiert – Aspose.Words unterstützt .NET Standard 2.0+, .NET Core und .NET Framework.
* Eine gültige Aspose.Words‑für‑.NET‑Lizenz (oder einen temporären Evaluierungsschlüssel) – die Bibliothek funktioniert ohne Lizenz, fügt jedoch ein Wasserzeichen hinzu.
* Visual Studio 2022 (oder eine beliebige C#‑IDE), um das Beispiel zu kompilieren und auszuführen.

Keine zusätzlichen NuGet‑Pakete sind über `Aspose.Words` hinaus erforderlich.

## Wie man Formen in Word mit Aspose.Words gruppiert

Der Kern der Lösung ist ein **`GroupShape`**‑Objekt, das als Container für einzelne Formen dient. Im Folgenden zerlegen wir den Prozess in klare Schritte.

### Schritt 1: Erstellen eines leeren Dokuments und eines `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum dieser Schritt?*  
`Document` repräsentiert die gesamte DOCX‑Datei, während `DocumentBuilder` fluente Methoden (z. B. `InsertShape`) bereitstellt, die neue Elemente automatisch an der aktuellen Cursor‑Position einfügen.

### Schritt 2: Einfügen der ersten Rechteck‑Form

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Der Aufruf von `InsertShape` fügt die Form dem Dokument hinzu und gibt ein `Shape`‑Objekt zurück, das Sie weiter konfigurieren können (Farbe, Rahmen usw.). Die Größe wird in Punkten angegeben (1 pt ≈ 1/72 in).

### Schritt 3: Einfügen des zweiten Rechtecks und Versetzen

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Durch Setzen von `Left` wird die Form relativ zum Seitenrand positioniert. Der Versatz muss größer sein als die Breite der ersten Form (100 pt), um Überlappungen zu vermeiden; wir verwenden 120 pt, um einen kleinen Abstand zu lassen.

### Schritt 4: Erstellen einer `GroupShape`, die groß genug für beide Rechtecke ist

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` erhält das zugehörige `Document` und die Container‑Abmessungen. Die Breite des Containers sollte die rechte Kante der am weitesten entfernten Form überschreiten; andernfalls würde die zweite Form abgeschnitten werden.

### Schritt 5: Anhängen der einzelnen Formen an die Gruppe

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

Durch Anhängen werden die Formen in die interne Sammlung der Gruppe verschoben. Nach diesem Aufruf sind die Formen keine eigenständigen Objekte mehr im Dokumenten‑Baum – sie gehören zur Gruppe.

### Schritt 6: Einfügen der gruppierten Form zurück in das Dokument

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` platziert die gesamte `GroupShape` an der Stelle, an der sich der Cursor gerade befindet. Wenn Sie die Gruppe in einem bestimmten Absatz benötigen, bewegen Sie den Builder zuerst zu diesem Absatz.

### Schritt 7: Speichern des Dokuments

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Die resultierende Datei enthält zwei Rechtecke, die sich wie ein einziges Objekt verhalten – Sie können sie in Microsoft Word gemeinsam verschieben, skalieren oder löschen.

## Vollständiger Quellcode

Alle Schritte zusammen ergeben ein eigenständiges Programm:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Erwartete Ausgabe:** Öffnet man *GroupedShapes.docx* in Microsoft Word, sieht man zwei nebeneinander stehende Rechtecke, die als ein einziges auswählbares Objekt behandelt werden. Das Ziehen der Gruppe bewegt beide Rechtecke zusammen.

## Übliche Variationen und Randfälle

| Situation | Empfohlene Anpassung |
|-----------|----------------------|
| **Mehr als zwei Formen** | Erstellen Sie zusätzliche `Shape`‑Objekte, positionieren Sie sie entsprechend und hängen Sie jedes an dieselbe `GroupShape` an. |
| **Dynamische Größe** | Berechnen Sie die Gruppen‑Breite/Höhe basierend auf den maximalen `Right`‑ und `Bottom`‑Werten der Kind‑Formen. |
| **Unterschiedliche Formtypen** | `ShapeType.Ellipse`, `ShapeType.Triangle` usw. können auf dieselbe Weise eingefügt werden; der Gruppen‑Container ist vom Typ unabhängig. |
| **Gedrehte Formen** | Setzen Sie `shape.Rotation = 45;` vor dem Anhängen; die Drehung bleibt innerhalb der Gruppe erhalten. |
| **Speichern als PDF** | Rufen Sie `doc.Save("GroupedShapes.pdf");` auf – die Gruppe bleibt in der PDF‑Darstellung erhalten. |

**Profi‑Tipp:** Nach dem Gruppieren können Sie einzelne Formen weiterhin ändern, indem Sie `group.GetChildNodes(NodeType.Shape, true)` aufrufen. Das ist nützlich, wenn Sie die Füllfarbe eines Rechtecks ändern möchten, ohne die Gruppe zu zerstören.

## Wie man die Gruppierung programmgesteuert überprüft

Falls Sie bestätigen müssen, dass die Formen korrekt gruppiert wurden (z. B. in Unit‑Tests), untersuchen Sie die Dokument‑Knoten‑Hierarchie:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

Die Ausgabe sollte sein:

```
Number of groups: 1
Children in first group: 2
```

Damit wird bestätigt, dass **Formen in Word** wie erwartet gruppiert wurden.

## Fazit

Sie wissen jetzt, wie Sie **Formen in Word** mit Aspose.Words für C# **gruppieren**. Der Vorgang besteht darin, einzelne Formen zu erstellen, sie zu positionieren, sie in einer `GroupShape` zu verpacken und die Gruppe wieder in das Dokument einzufügen. Mit dem obigen vollständigen Beispiel können Sie die Technik auf beliebig viele Formen, verschiedene Typen oder sogar die Kombination mit Textfeldern und Bildern ausweiten.

Als Nächstes erkunden Sie verwandte Themen wie **Aspose.Words Shape Grouping**, **C# Word Shape Manipulation** und **DocumentBuilder Insert Shape**, um fortgeschrittene Dokument‑Automatisierungsszenarien zu meistern. Experimentieren Sie mit dynamischer Größe, bedingter Gruppierung und dem Export nach PDF, um das volle Potenzial von Aspose.Words auszuschöpfen.


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}