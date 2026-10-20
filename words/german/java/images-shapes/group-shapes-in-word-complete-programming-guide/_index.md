---
category: general
date: 2026-08-14
description: Formen in Word mit Java und Aspose.Words gruppieren. Erfahren Sie, wie
  Sie ein Rechteck erstellen, die Formabmessungen festlegen und mehrere Formen in
  einem leeren Word‑Dokument gruppieren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- create rectangle shape
- set shape dimensions
- group multiple shapes
- build blank word document
language: de
lastmod: 2026-08-14
og_description: Formen in Word mit Aspose.Words für Java gruppieren. Erstellen Sie
  ein leeres Word‑Dokument, fügen Sie ein Rechteck‑Shape hinzu, legen Sie die Formabmessungen
  fest und gruppieren Sie mehrere Shapes in wenigen Minuten.
og_image_alt: Screenshot showing grouped rectangle shapes in a Word document created
  with Java
og_title: Formen in Word gruppieren – Java‑Beispiel für Entwickler
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to create
    rectangle shape, set shape dimensions, and group multiple shapes in a blank Word
    document.
  headline: Group shapes in Word – complete programming guide
  type: TechArticle
- questions:
  - answer: Overlap is allowed; Word will render them in the order they were added.
      Use `setZOrder` if you need explicit stacking.
    question: What if the shapes overlap?
  - answer: No. A `GroupShape` is confined to a single page because its coordinate
      system is page‑relative.
    question: Can I group shapes across different pages?
  - answer: Each child keeps its own formatting (fill color, line style). To apply
      a uniform style, iterate over `groupShape.getChildNodes()` and set properties
      programmatically.
    question: Do grouped shapes inherit formatting?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Gruppieren von Formen in Word – vollständiger Programmierleitfaden
url: /de/java/images-shapes/group-shapes-in-word-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gruppenformen in Word – vollständiger Programmierleitfaden

Wenn Sie **Formen in Word gruppieren** müssen, führt Sie dieses Tutorial durch den gesamten Prozess mit Java und Aspose.Words. Sie lernen, wie man ein **leeres Word‑Dokument erstellt**, **ein Rechteck‑Shape erzeugt**, **die Shape‑Abmessungen festlegt** und schließlich **mehrere Shapes gruppiert**, sodass sie sich wie ein einzelnes Objekt verhalten.

Die Arbeit mit Shapes in einer Word‑Datei fühlt sich oft an wie das Zeichnen auf einer Leinwand ohne Pinsel. Am Ende dieses Leitfadens besitzen Sie ein wiederverwendbares Code‑Snippet, das Sie in jedes Java‑Projekt einbinden können, egal ob Sie Berichte, Rechnungen oder benutzerdefinierte Vorlagen erzeugen.

## Was Sie benötigen

- Java 8 oder neuer
- Aspose.Words für Java (die neueste Version, z. B. 24.9)
- Eine IDE wie IntelliJ IDEA oder Eclipse
- Grundlegende Kenntnisse der objektorientierten Programmierung

All diese Voraussetzungen sind kostenlos zu installieren, und der untenstehende Code kompiliert mit einer einzigen Maven‑Abhängigkeit:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
    <classifier>jdk17</classifier>
</dependency>
```

## Schritt 1: Leeres Word‑Dokument erstellen und den Builder initialisieren

Das Erste, was Sie tun müssen, ist ein **leeres Word‑Dokument zu erstellen**. Das gibt Ihnen eine saubere Leinwand, in die Sie später Shapes einfügen können.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new empty document
        Document doc = new Document();

        // DocumentBuilder lets you add content programmatically
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` repräsentiert die gesamte *.docx*-Datei, während `DocumentBuilder` der Helfer ist, der Absätze, Tabellen und Shapes einfügt. Das Initialisieren beider Objekte ist die Grundlage für jede Word‑Automatisierungsaufgabe.

## Schritt 2: Einen Group‑Shape‑Container einfügen

Ein **Group‑Shape** wirkt wie ein Ordner, der andere Shapes enthalten kann. Zuerst erstellen wir den Container mit einer festen Größe von 400 pt × 200 pt.

```java
        // Insert a group shape that will hold other shapes (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);
```

Die Methode `insertGroupShape` gibt ein `GroupShape`‑Objekt zurück. Alle nachfolgenden Shapes, die Sie als eine Einheit behandeln möchten, müssen an dieses Objekt angehängt werden.

## Schritt 3: Rechteck‑Shapes erstellen und Shape‑Abmessungen festlegen

Jetzt **erstellen wir Rechteck‑Shape‑Objekte**, konfigurieren deren Größe und positionieren sie innerhalb der Gruppe. Dieser Schritt zeigt zudem, wie man **Shape‑Abmessungen** exakt festlegt.

```java
        // ---- First rectangle -------------------------------------------------
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);   // set shape dimensions: width = 150 pt
        rectangle1.setHeight(100);  // set shape dimensions: height = 100 pt
        rectangle1.setTop(20);      // vertical offset inside the group
        rectangle1.setLeft(20);     // horizontal offset inside the group
        groupShape.appendChild(rectangle1); // add to the group

        // ---- Second rectangle ------------------------------------------------
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);    // place it beside the first rectangle
        groupShape.appendChild(rectangle2);
```

Beide Rechtecke teilen sich dieselben Abmessungen, aber ihre `left`‑Eigenschaften unterscheiden sich, sodass sie nebeneinander erscheinen. Sie können `setTop` und `setLeft` ändern, um jedes gewünschte Layout zu erzeugen.

## Schritt 4: Das Dokument mit den gruppierten Rechtecken speichern

Nachdem die Shapes in der Gruppe sind, speichern Sie einfach das `Document`. Die resultierende Datei zeigt zwei Rechtecke, die zusammen bewegt werden, wenn sie ausgewählt werden.

```java
        // Save the document to disk
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Das Ausführen des Programms erzeugt `GroupShape.docx` im Arbeitsverzeichnis. Öffnen Sie die Datei in Microsoft Word, wählen Sie ein Rechteck aus, und Sie werden feststellen, dass die gesamte Gruppe als Einheit bewegt wird – genau das, wofür **Gruppieren von Shapes in Word** gedacht ist.

![Group shapes in Word example](group-shapes.png){alt="Beispiel für gruppierte Shapes in Word"}

*Abbildung: Zwei Rechteck‑Shapes, die in einem Word‑Dokument zusammengefasst sind.*

## Pro‑Tipp: Wiederverwendung desselben Group‑Shapes

Wenn Sie später weitere Shapes hinzufügen möchten (z. B. Kreise, Textfelder), behalten Sie eine Referenz auf `groupShape` und rufen weiterhin `appendChild` auf. Das verhindert das Neuerstellen des Containers und stellt sicher, dass alle Mitglieder synchron bleiben.

```java
        // Example: add a third shape later
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(120);
        ellipse.setHeight(80);
        ellipse.setTop(130);
        ellipse.setLeft(140);
        groupShape.appendChild(ellipse);
```

## Sonderfälle und häufige Fragen

- **Was passiert, wenn sich die Shapes überlappen?** Überlappungen sind erlaubt; Word rendert sie in der Reihenfolge, in der sie hinzugefügt wurden. Verwenden Sie `setZOrder`, wenn Sie eine explizite Stapelreihenfolge benötigen.
- **Kann ich Shapes über verschiedene Seiten hinweg gruppieren?** Nein. Ein `GroupShape` ist auf eine einzelne Seite beschränkt, da sein Koordinatensystem seitenbezogen ist.
- **Erben gruppierte Shapes Formatierungen?** Jedes Kind behält seine eigene Formatierung (Füllfarbe, Linienstil). Um einen einheitlichen Stil anzuwenden, iterieren Sie über `groupShape.getChildNodes()` und setzen die Eigenschaften programmgesteuert.

## Vollständiger Quellcode zum Nachschlagen

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // 1. Build blank Word document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert group shape container (400 pt × 200 pt)
        GroupShape groupShape = builder.insertGroupShape(400, 200);

        // 3. Create first rectangle and set shape dimensions
        Shape rectangle1 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle1.setWidth(150);
        rectangle1.setHeight(100);
        rectangle1.setTop(20);
        rectangle1.setLeft(20);
        groupShape.appendChild(rectangle1);

        // 4. Create second rectangle and set shape dimensions
        Shape rectangle2 = new Shape(doc, ShapeType.RECTANGLE);
        rectangle2.setWidth(150);
        rectangle2.setHeight(100);
        rectangle2.setTop(20);
        rectangle2.setLeft(200);
        groupShape.appendChild(rectangle2);

        // 5. Save the document containing the grouped rectangles
        String outputPath = "GroupShape.docx";
        doc.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

Das Ausführen des Programms erzeugt eine DOCX‑Datei, in der die beiden Rechtecke **gruppiert** sind. Durch Auswahl eines Rechtecks werden beide bewegt, was bestätigt, dass Sie **mehrere Shapes erfolgreich gruppiert** haben.

## Fazit

Sie wissen jetzt, wie man **Shapes in Word gruppiert** mit Java, von **Erstellung eines leeren Word‑Dokuments** über **Erzeugung eines Rechteck‑Shapes**, **Festlegung der Shape‑Abmessungen** bis hin zum **Gruppieren mehrerer Shapes** zu einem einzigen, beweglichen Objekt. Dieses Muster skaliert auf beliebig viele Shapes und lässt sich mit Text, Bildern oder Diagrammen kombinieren, um reichhaltige, programmatisch erzeugte Dokumente zu erstellen.

### Was kommt als Nächstes?

- Erkunden Sie **das Gruppieren mehrerer Shapes** mit verschiedenen Typen (Ellipsen, Pfeile, Textfelder).
- Wenden Sie Füllfarben oder Rahmen an, indem Sie `shape.getFillColor()` und `shape.getLine().setColor()` aufrufen.
- Fügen Sie das gruppierte Shape in eine Tabellenzelle ein, um strukturierte Berichte zu erstellen.
- Kombinieren Sie diesen Ansatz mit Seriendruck, um personalisierte Verträge zu generieren, die Marken‑Grafiken enthalten.

Experimentieren Sie gern, passen Sie die Abmessungen an oder betten Sie zusätzlichen Inhalt ein. Sobald Sie das Gruppieren beherrschen, werden Ihre Word‑Automatisierungsskripte deutlich flexibler und wartbarer. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}