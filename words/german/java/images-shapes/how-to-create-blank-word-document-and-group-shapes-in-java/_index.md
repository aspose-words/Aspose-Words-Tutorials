---
category: general
date: 2026-09-27
description: Erstellen Sie ein leeres Word‑Dokument in Java und gruppieren Sie Formen
  mit Aspose.Words. Erfahren Sie, wie Sie die Formgröße festlegen, die Füllfarbe der
  Form setzen und ein Kind zur Gruppe hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- set shape size
- set shape fill color
- append child to group
language: de
lastmod: 2026-09-27
og_description: Erstellen Sie ein leeres Word-Dokument in Java mit Aspose.Words. Dieses
  Tutorial zeigt, wie man Formen in Word gruppiert, die Größe einer Form festlegt,
  die Füllfarbe einer Form setzt und ein Kind zur Gruppe hinzufügt.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Ein leeres Word‑Dokument erstellen und Formen in Java gruppieren – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Create a blank Word document in Java and group shapes using Aspose.Words.
    Learn to set shape size, set shape fill color, and append child to group.
  headline: How to create blank word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Wie man ein leeres Word‑Dokument erstellt und Formen in Java gruppiert
url: /de/java/images-shapes/how-to-create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word-Dokument erstellt und Formen in Java gruppiert

Wenn Sie programmgesteuert ein **leeres Word-Dokument erstellen** müssen, zeigt Ihnen dieser Leitfaden genau, wie das mit Aspose.Words for Java funktioniert. Sie lernen außerdem, **Formen in Word zu gruppieren**, die Größe jeder Form festzulegen, eine Füllfarbe anzuwenden und **ein Kind zur Gruppe hinzuzufügen**, sodass die Objekte als eine Einheit agieren.

Die Arbeit mit Word-Dateien aus dem Code erspart Ihnen manuelle Formatierung und ermöglicht es, Berichte, Verträge oder Marketingbroschüren automatisch zu erzeugen. Am Ende dieses Tutorials haben Sie ein ausführbares Java‑Programm, das eine `.docx`‑Datei erzeugt, die ein blaues Rechteck und ein Bild enthält, die beide zusammen gruppiert sind.

## Voraussetzungen

- Java 17 (oder ein aktuelles JDK) installiert.
- Maven oder Gradle zur Verwaltung der Abhängigkeiten.
- Eine Aspose.Words for Java Lizenz (die kostenlose Evaluierung funktioniert zum Testen).
- Eine Beispiel‑Bilddatei (z. B. `sample.jpg`) in einem Ordner, den Sie im Code referenzieren können, abgelegt.

> **Profi‑Tipp:** Bewahren Sie Ihre Bilddateien in einem `resources`‑Verzeichnis auf und laden Sie sie mit `ClassLoader.getResourceAsStream`, um hartkodierte absolute Pfade zu vermeiden.

## Schritt 1: Ein leeres Word-Dokument erstellen und ein GroupShape hinzufügen

Der erste Schritt besteht darin, ein neues `Document`‑Objekt zu instanziieren, das eine leere Word‑Datei repräsentiert, und anschließend ein `GroupShape` einzufügen. Die Gruppe dient als Container für alle Formen, die Sie später hinzufügen.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();                     // create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape();     // group shapes in word
```

*Warum das wichtig ist:* Ein `GroupShape` ermöglicht es, mehrere Formen gemeinsam zu verschieben, zu drehen oder zu formatieren, was für komplexe Layouts wie Diagramme oder Wasserzeichen unerlässlich ist.

## Schritt 2: Ein Rechteck einfügen und **Formgröße festlegen**

Als Nächstes erstellen Sie ein Rechteck, definieren seine Abmessungen und fügen es der Gruppe hinzu. Dies demonstriert die **Formgröße festlegen**‑Operation.

```java
        // Step 2: Create a rectangle shape, configure its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);                         // set shape size – width 100 points
        rectangle.setHeight(50.0);                         // set shape size – height 50 points
        rectangle.setFillColor(java.awt.Color.BLUE);      // set shape fill color to blue
        group.appendChild(rectangle);                     // append child to group
```

*Erklärung:* `setWidth` und `setHeight` bestimmen die genaue Größe der Form in Punkten (1 Punkt = 1/72 Zoll). Passen Sie diese Werte an Ihre Layout‑Anforderungen an.

## Schritt 3: **Füllfarbe der Form** für das Rechteck festlegen

Der Hintergrund des Rechtecks wird mit `setFillColor` auf Blau gesetzt. Sie können jede `java.awt.Color`‑Konstante verwenden oder eine benutzerdefinierte RGB‑Farbe erstellen.

```java
        // The fill color was already applied in the previous step.
        // If you need a different color later, just call setFillColor again:
        // rectangle.setFillColor(new java.awt.Color(255, 165, 0)); // orange
```

*Warum das nützlich ist:* Füllfarben helfen, Objekte visuell zu unterscheiden, insbesondere wenn Sie das Dokument später als PDF exportieren oder ausdrucken.

## Schritt 4: Ein Bild einfügen und **Kind zur Gruppe hinzufügen**

Fügen Sie nun ein Bild zum selben `GroupShape` hinzu. Das Bild wird über `DocumentBuilder.insertImage` eingefügt und anschließend zur Gruppe hinzugefügt, sodass es zusammen mit dem Rechteck bewegt wird.

```java
        // Step 4: Insert an image and add it to the same group
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        group.appendChild(picture);                       // append child to group
```

*Randfall:* Wenn der Bildpfad falsch ist, wirft Aspose.Words eine `FileNotFoundException`. Verwenden Sie einen relativen Pfad oder laden Sie das Bild aus den Ressourcen, um dieses Problem zu vermeiden.

## Schritt 5: **Das Dokument mit den gruppierten Formen speichern**

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Die resultierende Datei enthält das Rechteck und das Bild, die zusammen gruppiert sind.

```java
        // Step 5: Save the document with the grouped shapes
        doc.save("YOUR_DIRECTORY/GroupShape.docx");       // creates the blank word document with grouped shapes
    }
}
```

### Erwartete Ausgabe

- Eine Datei namens `GroupShape.docx` erscheint im angegebenen Verzeichnis.
- Öffnet man die Datei in Microsoft Word, wird eine leere Seite mit einem blauen Rechteck und dem ausgewählten Bild angezeigt, die beide als ein einzelnes Objekt ausgewählt sind (Sie können sie gemeinsam verschieben oder die Größe ändern).

![leeres Word-Dokument mit gruppierten Formen erstellen](/images/grouped-shapes.png "leeres Word-Dokument mit gruppierten Formen erstellen")

*Der obige Screenshot zeigt die endgültig gruppierten Formen im neu erstellten Word-Dokument.*

## Häufige Variationen und zusätzliche Tipps

| Situation | Vorgehensweise |
|-----------|----------------|
| **Multiple images** | Fügen Sie jedes Bild mit `builder.insertImage` ein und rufen Sie für jedes `group.appendChild(picture)` auf. |
| **Different shape types** | Verwenden Sie `ShapeType.OVAL`, `ShapeType.LINE` usw., beim Erzeugen des `Shape`‑Objekts. |
| **Changing group position** | Nachdem Sie alle Kinder hinzugefügt haben, setzen Sie `group.setLeft(x)` und `group.setTop(y)`, um die gesamte Gruppe zu verschieben. |
| **Export to PDF** | Rufen Sie nach dem Gruppieren `doc.save("output.pdf")` auf; das PDF erhält die Gruppierung. |
| **License enforcement** | Wenn Sie die Evaluierungs‑Version ausführen, erscheint ein Wasserzeichen. Installieren Sie eine gültige Lizenz, um es zu entfernen. |

## Fazit

Sie wissen jetzt, wie man ein **leeres Word-Dokument erstellt**, ein **GroupShape** einfügt, **die Formgröße festlegt**, **die Füllfarbe der Form setzt** und **ein Kind zur Gruppe hinzufügt** mit Aspose.Words for Java. Dieses Muster ermöglicht es Ihnen, komplexe, programmatische Layouts zu erstellen, die später in Word bearbeitet oder in andere Formate exportiert werden können.

Als Nächstes erkunden Sie, wie man **Formen in Word gruppiert** mit Textfeldern, Hyperlinks zu Formen hinzufügt oder die Erstellung von mehrseitigen Berichten automatisiert. Die gleichen Prinzipien gelten – erstellen Sie einfach weitere Formen, konfigurieren Sie deren Eigenschaften und fügen Sie sie derselben Gruppe hinzu.

Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform in Word mit Java erstellen – Vollständige Anleitung](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Word-Dokument mit Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Gruppenform in Word-Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}