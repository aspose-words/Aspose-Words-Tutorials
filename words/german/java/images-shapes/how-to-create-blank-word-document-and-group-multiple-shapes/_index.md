---
category: general
date: 2026-10-26
description: Erstellen Sie ein leeres Word‑Dokument in C# und lernen Sie, wie Sie
  eine Gruppierung von Formen einfügen und anschließend ein Rechteck zur Gruppe hinzufügen.
  Dieser Leitfaden behandelt das Gruppieren mehrerer Formen Schritt für Schritt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group multiple shapes
- insert rectangle shape
- how to insert group
- how to add rectangle
language: de
lastmod: 2026-10-26
og_description: Erstellen Sie ein leeres Word‑Dokument in C# und sehen Sie, wie Sie
  eine Gruppe einfügen, dann ein Rechteck hinzufügen. Beherrschen Sie das Gruppieren
  mehrerer Formen mit einem vollständigen Codebeispiel.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle shape
og_title: Leeres Word‑Dokument erstellen und mehrere Formen gruppieren – C#‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Create a blank Word document in C# and learn how to insert a group
    shape, then add a rectangle shape to the group. This guide covers group multiple
    shapes step‑by‑step.
  headline: How to create blank Word document and group multiple shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Wie man ein leeres Word‑Dokument erstellt und mehrere Formen gruppiert
url: /de/java/images-shapes/how-to-create-blank-word-document-and-group-multiple-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word‑Dokument erstellt und mehrere Formen gruppiert

Wenn Sie **ein leeres Word‑Dokument** programmgesteuert erstellen müssen, zeigt Ihnen dieses Tutorial genau, wie es geht. Sie sehen, wie Sie eine Gruppenform einfügen und dann **ein Rechteck** zu dieser Gruppe hinzufügen – der komplette Workflow von einem leeren Dokument bis zu einer gruppierten Zeichnung.

Die Arbeit mit Word‑Dateien bedeutet oft, mehrere Zeichnungen zusammen zu arrangieren – denken Sie an ein Diagramm, das aus mehreren Formen besteht. Am Ende dieses Leitfadens können Sie **mehrere Formen gruppieren**, ein **Rechteck einfügen** und verstehen **wie man eine Gruppe einfügt** und **wie man ein Rechteck hinzufügt** auf eine saubere, wiederverwendbare Weise.

## Was Sie benötigen

* .NET 6.0 oder höher (der Code funktioniert auch mit .NET Framework 4.6+)
* **Aspose.Words for .NET** NuGet‑Paket (`Install-Package Aspose.Words`)
* Grundlegende Kenntnisse in C# und der Visual‑Studio‑IDE (jede IDE funktioniert)

> **Pro‑Tipp:** Aspose.Words läuft vollständig offline; Sie benötigen nach der Installation des Pakets keine Internetverbindung mehr.

## Schritt 1: Ein leeres Word‑Dokument erstellen

Der erste Vorgang besteht darin, ein leeres `Document`‑Objekt zu instanziieren. Dieses Objekt stellt das **leere Word‑Dokument** dar, das Sie später mit Formen anreichern werden.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1 – create a new blank Word document
        Document doc = new Document();               // <-- blank document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum das wichtig ist:* Ein `Document` ohne Abschnitte oder Absätze ist trotzdem eine gültige .docx‑Datei. Der Start mit einer sauberen Basis stellt sicher, dass keine versteckten Formatierungen die später hinzuzufügenden Formen beeinträchtigen.

## Schritt 2: Eine Gruppenform einfügen (how to insert group)

Eine **Gruppenform** fungiert wie ein Container, der andere Zeichenobjekte aufnehmen kann. In Aspose.Words erstellen Sie sie mit `InsertGroupShape`.

```csharp
        // Step 2 – insert a group shape that will hold other shapes
        GroupShape group = builder.InsertGroupShape();   // <-- container for shapes
```

*Warum eine Gruppe verwenden?* Durch Gruppieren können Sie mehrere Formen gleichzeitig verschieben, drehen oder skalieren. Das ist für Diagramme unerlässlich, bei denen Elemente ausgerichtet bleiben müssen.

## Schritt 3: Ein Rechteck einfügen (insert rectangle shape)

Fügen Sie nun ein Rechteck zum Dokument hinzu. Die Methode `InsertShape` liefert ein `Shape`‑Objekt, das Sie später an die Gruppe anhängen können.

```csharp
        // Step 3 – create a rectangle shape with specific dimensions
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

*Warum ein Rechteck?* Rechtecke sind das am häufigsten genutzte Bauelement für Flussdiagramme, UI‑Mock‑Ups und Platzhalter‑Grafiken. Die Maße werden in Punkten angegeben (1 pt ≈ 1/72 Zoll).

## Schritt 4: Das Rechteck zur Gruppe hinzufügen (how to add rectangle)

Eine mit `InsertShape` erstellte Form befindet sich direkt im Dokumentkörper. Um sie Teil der Gruppe zu machen, rufen Sie `AppendChild` auf dem `GroupShape` auf.

```csharp
        // Step 4 – add the rectangle to the previously created group
        group.AppendChild(rectangle);   // <-- rectangle now belongs to the group
```

*Was im Hintergrund passiert:* `AppendChild` verschiebt den Rechteck‑Knoten aus der Haupt‑Story des Dokuments in die interne Sammlung der Gruppe und behält dabei Größe und Position relativ zum Ursprung der Gruppe bei.

## Schritt 5: Das Dokument speichern

Zum Schluss schreiben Sie die Datei auf die Festplatte. Sie können die resultierende `.docx` in Microsoft Word öffnen, um das gruppierte Rechteck zu sehen.

```csharp
        // Step 5 – save the document to a file
        doc.Save("GroupedShapeExample.docx");
    }
}
```

> **Randfall:** Wenn Sie weitere Formen (z. B. Kreise, Linien) zur gleichen Gruppe hinzufügen möchten, wiederholen Sie **Schritt 3** und **Schritt 4** für jede neue Form, bevor Sie speichern. Die Gruppe passt automatisch ihre Begrenzungsbox an, um alle Kinder zu umfassen.

## Wie man mehrere Formen gruppiert – Erweiterung des Beispiels

Unten finden Sie ein kurzes Snippet, das eine zweite Form (eine Ellipse) zur gleichen Gruppe hinzufügt und damit **mehrere Formen gruppieren** in einem einzigen Dokument demonstriert.

```csharp
        // Additional shape: an ellipse
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
        group.AppendChild(ellipse);   // now the group contains rectangle + ellipse
```

Wenn Sie `GroupedShapeExample.docx` öffnen, sehen Sie, dass sich Rechteck und Ellipse gemeinsam bewegen, wenn Sie die Gruppe in Word auswählen.

## Häufige Fragen und Fehlersuche

| Frage | Antwort |
|----------|--------|
| **Benötige ich eine Lizenz für Aspose.Words?** | Eine kostenlose Evaluation funktioniert ohne Lizenz, fügt jedoch ein Wasserzeichen ein. Für den Produktionseinsatz eine Lizenz anwenden, um das Wasserzeichen zu entfernen und die volle Leistung freizuschalten. |
| **Kann ich Formen präzise positionieren?** | Ja. Nach dem Einfügen einer Form können Sie die Eigenschaften `Shape.Left`, `Shape.Top`, `Shape.Width` und `Shape.Height` setzen. |
| **Was passiert, wenn das Rechteck nach dem Speichern verschwindet?** | Stellen Sie sicher, dass Sie `group.AppendChild(rectangle)` *nach* dem Einfügen des Rechtecks aufrufen. Die Form muss zuerst im Dokumentkörper liegen und dann in die Gruppe verschoben werden. |
| **Ist es möglich, Formen über verschiedene Abschnitte hinweg zu gruppieren?** | Nein. Alle Formen einer Gruppe müssen zur selben Story (Abschnitt) gehören. Erstellen Sie bei Bedarf separate Gruppen pro Abschnitt. |

## Zusammenfassung

Sie wissen jetzt, wie man **ein leeres Word‑Dokument erstellt**, **eine Gruppe einfügt**, **ein Rechteck hinzufügt** und **mehrere Formen gruppiert** mit Aspose.Words für .NET. Das vollständige, ausführbare Beispiel oben kann in eine Konsolen‑App kopiert und sofort ausgeführt werden.

## Nächste Schritte

* Experimentieren Sie mit **insert rectangle shape**‑Größen und -Farben (`rectangle.FillColor = Color.LightBlue;`).  
* Erkunden Sie weitere Formtypen (`ShapeType.Polygon`, `ShapeType.Line`), um Ihre Diagramme zu erweitern.  
* Lernen Sie, wie Sie das finale `.docx` in PDF konvertieren (`doc.Save("output.pdf");`) für die Verteilung.  
* Tauchen Sie ein in **how to add rectangle** zu bereits bestehenden Dokumenten, die bereits Text enthalten – nutzen Sie `DocumentBuilder.MoveTo`, um die Gruppe dort zu positionieren, wo Sie sie benötigen.

Passen Sie den Code gern an Ihre eigenen Reporting‑ oder Diagrammgenerierungs‑Bedürfnisse an. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create blank Word document and group shapes in C#](/words/english/net/programming-with-shapes/how-to-create-blank-word-document-and-group-shapes-in-c/)
- [How to group shapes in Word and add shapes to Word document](/words/english/net/programming-with-shapes/how-to-group-shapes-in-word-and-add-shapes-to-word-document/)
- [How to create rectangle shape and group shapes in Word with Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}