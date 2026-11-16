---
category: general
date: 2026-11-15
description: Erfahren Sie, wie Sie eine Form in ein Word‑Dokument einfügen und mehrere
  Formen mit Aspose.Words DocumentBuilder gruppieren. Enthält Beispiele zum Einfügen
  einer Rechteckform und zum Einfügen mehrerer Formen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: de
lastmod: 2026-11-15
og_description: Wie man eine Form in eine Word-Datei mit Aspose.Words einfügt. Dieser
  Leitfaden behandelt das Gruppieren mehrerer Formen, das Einfügen einer Rechteckform
  und das effiziente Hinzufügen mehrerer Formen.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Wie man eine Form einfügt und mehrere Formen mit DocumentBuilder gruppiert
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Wie man eine Form einfügt und mehrere Formen mit DocumentBuilder in C# gruppiert
url: /de/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen einfügt und mehrere Formen mit DocumentBuilder in C# gruppiert

Wenn Sie wissen möchten, **wie man Formen einfügt** in ein Word-Dokument mit Aspose.Words, zeigt Ihnen dieser Leitfaden die genauen Schritte. Sie lernen außerdem, **mehrere Formen zu gruppieren**, sodass sie sich wie ein einzelnes Objekt verhalten, und **wie man ein Rechteck einfügt** neben anderen Grafiken.

Die Dokumentenautomatisierung erfordert häufig das Hinzufügen mehrerer Grafiken – Diagramme, Logos, Call‑outs – und gleichzeitig eine übersichtliche Anordnung. Am Ende dieses Tutorials können Sie **mehrere Formen einfügen**, sie in einer Gruppe platzieren und ein sauberes, wiederverwendbares Layout speichern.

## Voraussetzungen

* .NET 6.0 oder höher installiert  
* Visual Studio 2022 (oder jede C#‑IDE)  
* Eine Aspose.Words für .NET‑Lizenz oder einen kostenlosen Evaluierungsschlüssel  
* Grundlegende Kenntnisse in C# und der Aspose.Words `DocumentBuilder`‑Klasse  

Sie benötigen **keine** anderen Drittanbieter‑Bibliotheken; alles, was Sie brauchen, ist Teil von Aspose.Words.

## Schritt 1: Aspose.Words über NuGet installieren

Öffnen Sie Ihr Projekt in Visual Studio und führen Sie den folgenden Befehl in der Package Manager Console aus:

```powershell
Install-Package Aspose.Words
```

Das Paket enthält die Klassen `DocumentBuilder`, `Shape` und `GroupShape`, die im gesamten Tutorial verwendet werden.

## Schritt 2: Eine DocumentBuilder‑Instanz erstellen – die Grundlage für **wie man Formen einfügt**

Die erste ausführbare Codezeile besteht darin, einen `DocumentBuilder` zu erstellen. Dieses Objekt gibt Ihnen direkten Zugriff auf den Dokumentenbaum und ermöglicht es Ihnen, Formen genau dort zu platzieren, wo Sie sie benötigen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Warum das wichtig ist*: `DocumentBuilder` hält einen Cursor (den „Einfügepunkt“). Jeder nachfolgende `Insert...`‑Aufruf verwendet diesen Cursor, weshalb wir ihn später in ein `GroupShape` verschieben, um alle Formen zusammenzuhalten.

## Schritt 3: **Rechteck einfügen** – die erste Grafik, die Sie hinzufügen

Ein Rechteck ist ein gängiger Platzhalter für Tabellen, Bilder oder Call‑outs. Verwenden Sie `InsertShape` mit `ShapeType.Rectangle` und geben Sie Breite und Höhe in Punkten an (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Das Rechteck erscheint an der aktuellen Cursorposition. Sie können bei Bedarf später die Füllung, den Linienstil oder den Text anpassen.

## Schritt 4: Eine weitere Form einfügen – eine Ellipse für visuelle Abwechslung

Das Hinzufügen von mehr als einer Form demonstriert **mehrere Formen einfügen**. Die Ellipse wird nach dem Rechteck im Dokumentenfluss platziert.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

Zu diesem Zeitpunkt enthält das Dokument zwei unabhängige Formen. Wenn Sie den Cursor verschieben oder Text hinzufügen, bleiben die Formen an ihrer Einfügeposition.

## Schritt 5: **Mehrere Formen gruppieren**, damit sie als Einheit agieren

Das Gruppieren ist unerlässlich, wenn Sie mehrere Grafiken gemeinsam verschieben, drehen oder formatieren müssen. Der folgende Code erstellt ein `GroupShape`, verschiebt den Cursor des Builders hinein und fügt dann dieselben Formen erneut ein – dieses Mal werden sie zu Kind‑Elementen der Gruppe.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Warum eine Gruppe verwenden?

* **Einzelpunkt‑Transformation** – die gesamte Gruppe mit einem Aufruf drehen oder skalieren.  
* **Logische Organisation** – der Word‑Dokumentbaum spiegelt die Gruppierung wider, was spätere Bearbeitungen erleichtert.  
* **Konsistentes Layout** – das Verschieben der Gruppe bewahrt die relativen Positionen ihrer Kind‑Elemente.

### Weitere Formen hinzufügen – **mehrere Formen einfügen** innerhalb der Gruppe erweitern

Sie können `InsertShape` weiterhin aufrufen, solange der Cursor innerhalb des `GroupShape` bleibt. Zum Beispiel, um ein Dreieck hinzuzufügen:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Jeder Aufruf respektiert den Gruppenkontext, sodass das Dreieck automatisch Teil desselben Gruppensatzes wird.

## Schritt 6: Dokument speichern und Ergebnis überprüfen

Nachdem alle Formen platziert wurden, speichern Sie das Dokument in einer `.docx`‑Datei. Das Öffnen der Datei in Microsoft Word (oder einem kompatiblen Viewer) sollte zwei separate Formen zeigen, gefolgt von einem gruppierten Satz, der dasselbe Rechteck, dieselbe Ellipse und dasselbe Dreieck enthält.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Erwartete Ausgabe

* **Erste zwei Formen** – ein Rechteck und eine Ellipse, die unabhängig auf der Seite platziert sind.  
* **Gruppierter Block** – ein Rechteck, eine Ellipse und ein Dreieck, die zusammen verschoben werden, wenn Sie in Word auf eine von ihnen klicken.

Sie können die Gruppierung testen, indem Sie eine beliebige Form innerhalb der Gruppe auswählen; Word hebt die gesamte Sammlung hervor und bestätigt, dass die **Mehrere Formen gruppieren**‑Operation erfolgreich war.

## Häufige Stolperfallen und Profi‑Tipps

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| Formen erscheinen außerhalb der vorgesehenen Seite | Der Cursor des Builders wurde vor dem Einfügen nicht in das `GroupShape` verschoben. | Rufen Sie stets `builder.MoveTo(group)` **vor** allen `InsertShape`‑Aufrufen auf, die zur Gruppe gehören. |
| Gruppe verschwindet nach dem Speichern | Die Gruppe wurde eingefügt, ohne zur Knotensammlung des Dokuments hinzugefügt zu werden. | Verwenden Sie `builder.InsertNode(group)` unmittelbar nach dem Erstellen des `GroupShape`. |
| Unerwartete Größe wegen Dokument‑DPI | Aspose.Words verwendet Punkte; wenn Sie in Pixeln denken, können die Abmessungen nicht übereinstimmen. | Konvertieren Sie Pixel in Punkte (`points = pixels * 72 / 96`) oder arbeiten Sie direkt mit Punkten. |
| Formen überlappen unbeabsichtigt | Es wurde keine explizite Positionierung festgelegt; Word platziert sie sequenziell. | Setzen Sie `Shape.Left` und `Shape.Top` nach dem Einfügen, um die genaue Platzierung zu steuern. |

**Profi‑Tipp:** Nach dem Gruppieren können Sie die `Shapes`‑Sammlung der Gruppe (`group.Shapes`) abrufen, um zu iterieren, umzubenennen oder eine Massenformatierung anzuwenden.

## Schritt 7: Beispiel erweitern – was kommt als Nächstes?

Jetzt, da Sie **wie man Formen einfügt**, **Rechteck einfügt** und **mehrere Formen gruppiert**, können Sie Folgendes erkunden:

* **Animieren gruppierter Formen** – Rotations‑ oder Spiegelungseigenschaften für die Gruppe festlegen.  
* **Stile anwenden** – `Shape.FillColor`, `Shape.LineFormat` oder `Shape.TextBox` verwenden, um Beschriftungen hinzuzufügen.  
* **Exportieren nach PDF** – das gleiche gruppierte Layout wird korrekt gerendert, wenn Sie `doc.Save("output.pdf")` aufrufen.

All diese Erweiterungen nutzen denselben `DocumentBuilder`‑Workflow und halten Ihren Code sauber und wartbar.

## Fazit

Dieses Tutorial zeigte **wie man Formen einfügt** in ein Word‑Dokument mit Aspose.Words, wie man **ein Rechteck einfügt** und wie man **mehrere Formen gruppiert**, sodass sie sich wie ein einzelnes Objekt verhalten. Durch das Befolgen des Schritt‑für‑Schritt‑Codes können Sie zuverlässig **mehrere Formen einfügen**, sie in Gruppen organisieren und programmatisch Dokumente professioneller Qualität erzeugen.

Experimentieren Sie gern mit verschiedenen Formtypen, Farben und Gruppentransformationen. Wenn Sie bereit sind, integrieren Sie das Muster in größere Reporting‑ oder Templating‑Lösungen, um komplexe Dokumentenlayouts zu automatisieren. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Formen in Word‑Dokumenten mit Aspose.Words für .NET einfügen](/words/english/net/working-with-shapes/insert-shape/)
- [Wie man Ellipsen‑ und Rechteckformen innerhalb einer Gruppierung in einem Word‑Dokument mit Aspose.Words erstellt und einfügt](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Wie man Formen in einem Word‑Dokument mit Aspose.Words gruppiert](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}