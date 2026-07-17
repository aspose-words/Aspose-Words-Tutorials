---
category: general
date: 2026-07-16
description: Wie man in Java mit Aspose.Words eine Gruppenform einfügt – ein Rechteck
  hinzufügen, die Formabmessungen festlegen und ein farbiges Rechteck sowie einen
  Kreis erstellen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert group
- add rectangle shape
- set shape dimensions
- create colored rectangle
- create colored circle
language: de
lastmod: 2026-07-16
og_description: 'Wie man eine Gruppenform in Java einfügt: ein praxisnaher Leitfaden
  zum Hinzufügen einer Rechteckform, Festlegen der Formabmessungen und Erstellen von
  farbigen Rechtecken und Kreisen mit Aspose.Words.'
og_image_alt: Screenshot showing a grouped blue rectangle and red circle in a Java‑generated
  Word document
og_title: Gruppenform in Java einfügen – Vollständiges Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-16'
  description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  headline: how to insert group shape in Java – Complete Guide
  type: TechArticle
- description: how to insert group shape in Java using Aspose.Words – add rectangle
    shape, set shape dimensions, and create colored rectangle and circle.
  name: how to insert group shape in Java – Complete Guide
  steps:
  - name: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
    text: '**Document & Builder** – We spin up an empty Word file and a `DocumentBuilder`
      that lets us insert content.'
  - name: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
    text: '**Group Shape** – `builder.insertGroupShape()` creates a container. Think
      of it as a folder for drawing objects.'
  - name: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
    text: '**Blue Rectangle** – We instantiate a `Shape` of type `RECTANGLE`, size
      it, position it, and fill it with blue – that’s the **create colored rectangle**
      step.'
  - name: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
    text: '**Red Circle** – Same pattern, but using `ELLIPSE` for a perfect circle,
      then filling it red – that’s the **create colored circle** part.'
  - name: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
    text: '**Saving** – Finally we persist everything to `GroupShapeDemo.docx`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shapes
- Document Automation
- Group Shapes
title: Wie man eine Gruppenform in Java einfügt – Komplettanleitung
url: /de/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Gruppenkörper in Java einfügt – Vollständige Anleitung

Haben Sie sich schon einmal gefragt, **wie man einen Gruppenkörper** in ein Word‑Dokument mit Java einfügt? Sie sind nicht allein. Egal, ob Sie einen Berichtsgenerator oder einen dynamischen Flyer‑Ersteller bauen – das Gruppieren von Formen hält Ihr Layout übersichtlich und Ihren Code handhabbar.

In diesem Tutorial gehen wir die genauen Schritte durch, um **ein Rechteck einzufügen**, **die Formabmessungen festzulegen** und **ein farbiges Rechteck** sowie **einen farbigen Kreis** mit der Aspose.Words‑Bibliothek zu erstellen. Am Ende haben Sie ein lauffähiges Programm, das eine .docx‑Datei mit einem blauen Rechteck und einem roten Kreis erzeugt, die sauber in einer Gruppe verpackt sind.

## Voraussetzungen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

- Java 17 (oder ein aktuelles JDK) installiert und konfiguriert.
- Maven oder Gradle zur Verwaltung von Abhängigkeiten.
- Aspose.Words for Java 23.9 oder neuer – Sie können es von Maven Central beziehen.
- Grundlegendes Verständnis der Java‑Syntax – nichts Besonderes erforderlich.

Falls Ihnen etwas fehlt, holen Sie sich das JDK von der Oracle‑Website und fügen Sie die Aspose.Words‑Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Jetzt, wo die Grundlagen gelegt sind, legen wir los.

## how to insert group shape – Überblick

Die Kernidee ist einfach: ein `Document` erstellen, einen `DocumentBuilder` öffnen, eine **Gruppe** einfügen und dann einzelne Formen (ein Rechteck und einen Kreis) in diese Gruppe legen. Die Gruppe wirkt wie ein Container, sodass ein späteres Verschieben alles darin gleichzeitig bewegt – ideal für komplexe Layouts.

Unten finden Sie den vollständigen, sofort ausführbaren Code. Kopieren Sie ihn gern in eine neue Java‑Klasse namens `InsertGroupShapeDemo`.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to insert a group shape, add a rectangle and a circle,
 * set their dimensions, and apply colors using Aspose.Words for Java.
 */
public class InsertGroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a group shape that will contain other shapes.
        Shape group = builder.insertGroupShape();

        // Step 3: Create a blue rectangle, set its size and position, and add it to the group.
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);          // set shape dimensions – width
        rectangle.setHeight(50.0);          // set shape dimensions – height
        rectangle.setLeft(20.0);            // X‑coordinate inside the group
        rectangle.setTop(20.0);             // Y‑coordinate inside the group
        rectangle.getFill().setForeColor(Color.BLUE); // create colored rectangle
        group.appendChild(rectangle);       // add rectangle shape to the group

        // Step 4: Create a red circle, set its size and position, and add it to the same group.
        Shape circle = new Shape(doc, ShapeType.ELLIPSE);
        circle.setWidth(60.0);              // set shape dimensions – width (diameter)
        circle.setHeight(60.0);             // set shape dimensions – height (diameter)
        circle.setLeft(150.0);              // X‑coordinate inside the group
        circle.setTop(20.0);                // Y‑coordinate inside the group
        circle.getFill().setForeColor(Color.RED); // create colored circle
        group.appendChild(circle);          // add circle shape to the group

        // Step 5: Save the document with the grouped shapes.
        doc.save("GroupShapeDemo.docx");
        System.out.println("Document saved successfully.");
    }
}
```

> **Pro‑Tipp:** Die Werte von `setLeft` und `setTop` beziehen sich auf den Ursprung der Gruppe, nicht auf die Seite. Das macht das spätere Verschieben der gesamten Gruppe zum Kinderspiel.

### Was ist gerade passiert?

1. **Document & Builder** – Wir erzeugen eine leere Word‑Datei und einen `DocumentBuilder`, mit dem wir Inhalte einfügen können.
2. **Group Shape** – `builder.insertGroupShape()` erstellt einen Container. Denken Sie an einen Ordner für Zeichenobjekte.
3. **Blaues Rechteck** – Wir instanziieren ein `Shape` vom Typ `RECTANGLE`, setzen Größe und Position und füllen es blau – das ist der Schritt **create colored rectangle**.
4. **Roter Kreis** – Gleiches Muster, aber mit `ELLIPSE` für einen perfekten Kreis, dann rot gefüllt – das ist der Schritt **create colored circle**.
5. **Speichern** – Abschließend schreiben wir alles nach `GroupShapeDemo.docx`.

Führen Sie das Programm aus (`mvn compile exec:java -Dexec.mainClass=InsertGroupShapeDemo`) und öffnen Sie die erzeugte Datei. Sie sollten ein blaues Rechteck links und einen roten Kreis rechts sehen, beide fest in einer einzigen Gruppenbox eingeschlossen.

## Ein Rechteck einfügen

Wenn Sie nur ein Rechteck ohne Gruppierung benötigen, können Sie den Aufruf von `insertGroupShape()` weglassen und das Rechteck direkt an den Dokumentkörper anhängen. Gruppierung bietet jedoch die Flexibilität, mehrere Formen gleichzeitig zu verschieben, zu drehen oder zu löschen.

```java
Shape rect = new Shape(doc, ShapeType.RECTANGLE);
rect.setWidth(120);
rect.setHeight(70);
rect.getFill().setForeColor(Color.GREEN);
builder.insertNode(rect);
```

Beachten Sie, dass wir hier die Logik **add rectangle shape** verwendet haben. Das Rechteck erscheint als eigenständiges Objekt auf der Seite. In den meisten realen Szenarien möchten Sie jedoch die Gruppe verwenden, weil sie die relative Positionierung beibehält.

## Formabmessungen festlegen

Wenn Sie Methoden wie `setWidth` und `setHeight` sehen, denken Sie daran, dass sie **Punkte** (1/72 Zoll) erwarten. Wenn Sie Millimeter bevorzugen, konvertieren Sie zuerst:

```java
double mmToPoints = 72.0 / 25.4;
double widthInMm = 50; // 50 mm
rectangle.setWidth(widthInMm * mmToPoints);
rectangle.setHeight(30 * mmToPoints);
```

Dieses Snippet demonstriert **set shape dimensions** mit einer Einheitenumrechnung – praktisch, wenn Ihre Design‑Spezifikationen aus einem UI‑Mockup stammen, das metrische Einheiten verwendet.

## Ein farbiges Rechteck erstellen

Eine Form zu färben ist so einfach wie `getFill().setForeColor()` aufzurufen. Sie können jede `java.awt.Color` übergeben. Einen Farbverlauf wünschen? Verwenden Sie `setForeColor` für die Startfarbe und `setBackColor` für die Endfarbe.

```java
rectangle.getFill().setForeColor(Color.MAGENTA);
rectangle.getFill().setBackColor(Color.YELLOW);
rectangle.getFill().setFillType(FillType.GRADIENT);
```

Damit haben Sie schnell **create colored rectangle** mit einem Farbverlauf statt einer einfarbigen Füllung erzeugt.

## Einen farbigen Kreis erstellen

Kreise sind lediglich Ellipsen mit gleicher Breite und Höhe. Die gleiche Farb‑Logik gilt:

```java
circle.getFill().setForeColor(new Color(255, 165, 0)); // orange
```

Falls Sie eine transparente Füllung benötigen, setzen Sie den Alpha‑Kanal:

```java
circle.getFill().setForeColor(new Color(0, 0, 255, 128)); // semi‑transparent blue
```

Jetzt beherrschen Sie die Technik **create colored circle**.

## Das Dokument speichern

Aspose.Words ermöglicht die Ausgabe in viele Formate: DOCX, PDF, HTML, PNG und mehr. Für dieses Demo bleiben wir bei DOCX, weil es die Vektorgrafiken perfekt bewahrt.

```java
doc.save("GroupShapeDemo.pdf", SaveFormat.PDF);
```

Ein Wechsel des `SaveFormat` reicht aus, um eine PDF‑Version desselben gruppierten Kunstwerks zu erzeugen.

## Häufige Stolperfallen & wie man sie vermeidet

- **Haben Sie vergessen, die Form zur Gruppe hinzuzufügen?** Die Form erscheint auf der Seite, bewegt sich jedoch nicht mit der Gruppe. Rufen Sie immer `group.appendChild(yourShape)` auf.

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to create form fields and add content using DocumentBuilder in Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}