---
category: general
date: 2026-09-24
description: Erfahren Sie, wie Sie in Java ein leeres Word‑Dokument erstellen und
  Formen wie Rechtecke und Linien mit Aspose.Words gruppieren. Enthält Schritt‑für‑Schritt‑Code.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shapes
- add rectangle shape
- group shapes in word
- set shape size
language: de
lastmod: 2026-09-24
og_description: Erstellen Sie ein leeres Word‑Dokument in Java und lernen Sie, wie
  Sie Formen gruppieren, eine Rechteckform hinzufügen und die Größe von Formen mit
  Aspose.Words festlegen.
og_image_alt: Screenshot of a blank Word document with grouped shapes created using
  Java
og_title: Erstelle ein leeres Word‑Dokument und gruppiere Formen in Java – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-24'
  description: Learn how to create a blank Word document in Java and group shapes
    like rectangles and lines using Aspose.Words. Includes step‑by‑step code.
  headline: How to create a blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Wie man ein leeres Word‑Dokument erstellt und Formen in Java gruppiert
url: /de/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Word-Dokument erstellt und Formen in Java gruppiert

Wenn Sie ein **leeres Word-Dokument erstellen** und anschließend mehrere Zeichenobjekte organisieren müssen, zeigt Ihnen dieses Handbuch genau, wie es geht. Mit Aspose.Words for Java können Sie eine Gruppenform einfügen, eine Rechteckform hinzufügen, eine Linie zeichnen und die Größe sowie Position jeder Form steuern – alles in einem einzigen, ausführbaren Programm.

Sie gehen jeden Schritt durch, von der Initialisierung des Dokuments bis zum Speichern der finalen `.docx`. Am Ende verstehen Sie **wie man Formen gruppiert**, **ein Rechteck hinzufügt** und **die Formgröße festlegt**, sodass Ihre Word-Dateien genau wie gewünscht aussehen.

## Voraussetzungen

- Java 17 oder neuer (der Code kompiliert mit jedem aktuellen JDK)
- Aspose.Words for Java-Bibliothek (Download von der [Aspose-Website](https://products.aspose.com/words/java))
- Eine IDE oder ein Build‑Tool (Maven/Gradle), das die Aspose.Words‑JAR zum Klassenpfad hinzufügen kann
- Grundlegende Kenntnisse der Java‑Syntax

> **Profi‑Tipp:** Verwenden Sie Maven für das Abhängigkeitsmanagement; fügen Sie `com.aspose:aspose-words:23.12` (oder die neueste Version) zu Ihrer `pom.xml` hinzu.

## Schritt 1: Ein leeres Word-Dokument erstellen

Die erste Aufgabe besteht darin, ein **leeres Word-Dokument zu erstellen**. Dadurch erhalten Sie eine saubere Leinwand, in die Sie später Formen einfügen können.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document document = new Document();

        // DocumentBuilder provides convenient methods for inserting content
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Warum das wichtig ist:* Ein `Document`‑Objekt repräsentiert die gesamte `.docx`‑Datei. Das Beginnen mit einem leeren Dokument stellt sicher, dass keine versteckten Formatierungen die später hinzuzufügenden Formen beeinträchtigen.

## Schritt 2: Eine Gruppenform einfügen – der Container für mehrere Objekte

Eine **Gruppenform** fungiert als Container, der es Ihnen ermöglicht, mehrere Formen gemeinsam zu verschieben, zu skalieren oder zu drehen. Dies ist das Kernprinzip von **wie man Formen gruppiert** in Word.

```java
        // Insert a group shape of width 300 points and height 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

*Erläuterung:* Die Methode `insertGroupShape` erstellt ein `GroupShape`‑Objekt und platziert es an der aktuellen Cursorposition. Alle nachfolgenden Formen, die Sie mit `appendChild` zu dieser Gruppe hinzufügen, werden als eine Einheit behandelt.

## Schritt 3: Ein Rechteck hinzufügen und seine Größe festlegen

Jetzt **fügen wir ein Rechteck** zur Gruppe hinzu und **setzen die Formgröße** präzise.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);   // set shape width
        rectangle.setHeight(100.0);  // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Add the rectangle to the group
        group.appendChild(rectangle);
```

*Warum Sie die Formgröße festlegen müssen:* Breite und Höhe bestimmen, wie das Rechteck auf der Seite erscheint. Die Methoden `setLeft` und `setTop` positionieren das Rechteck relativ zum Ursprung der Gruppe und geben Ihnen pixelgenaue Layout‑Kontrolle.

## Schritt 4: Eine Linienform hinzufügen und ihre Abmessungen konfigurieren

Eine Linie ist ein weiteres gängiges Zeichenobjekt. Wir werden die Logik, die wir beim **Hinzufügen eines Rechtecks** verwendet haben, auf eine Linie anwenden und zeigen, dass dieselben Größenprinzipien gelten.

```java
        // Create a line shape
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);   // line length
        line.setHeight(0.0);    // height is zero for a horizontal line
        line.setLeft(20.0);
        line.setTop(130.0);

        // Add the line to the same group
        group.appendChild(line);
```

*Wichtiger Punkt:* Obwohl eine Linie keine Höhe hat, verwenden Sie weiterhin `setWidth`, um ihre Länge zu definieren. Die Positionierung (`setLeft`, `setTop`) folgt demselben Koordinatensystem wie bei anderen Formen.

## Schritt 5: Das Dokument mit gruppierten Formen speichern

Abschließend speichern Sie das Dokument, um die Änderungen zu übernehmen. Dadurch entsteht eine `.docx`‑Datei, die Sie in Microsoft Word öffnen können, um das Ergebnis zu überprüfen.

```java
        // Save the document to disk
        document.save("GroupShapeDemo.docx");
    }
}
```

**Erwartete Ausgabe:** Beim Öffnen von `GroupShapeDemo.docx` wird eine leere Seite angezeigt, die ein gruppiertes Rechteck und eine Linie enthält. Wenn Sie eine der Formen auswählen, wird die gesamte Gruppe ausgewählt, sodass Sie beide zusammen verschieben können.

## Häufige Fragen und Sonderfall‑Behandlung

| Frage | Antwort |
|----------|--------|
| *Kann ich mehr als zwei Formen zur Gruppe hinzufügen?* | Ja. Rufen Sie `group.appendChild(yourShape)` für jede zusätzliche Form auf. |
| *Was, wenn ich eine andere Einheit (z. B. Zentimeter) für die Größe benötige?* | Aspose.Words verwendet Punkte (1 Punkt = 1/72 Zoll). Konvertieren Sie mit `Points = centimeters * 28.3465`. |
| *Behält die Gruppe ihr Layout bei, wenn das Dokument auf einem anderen Rechner geöffnet wird?* | Absolut. Alle Größen‑ und Positionsdaten werden in der `.docx`‑Datei gespeichert, wodurch das Layout portabel ist. |
| *Wie kann ich Formen später wieder entgruppieren?* | Rufen Sie das `GroupShape`‑Objekt ab und iterieren Sie über `group.getChildNodes(NodeType.SHAPE, true)`, um jedes Kind aus der Gruppe zu verschieben. |
| *Was, wenn ich die gesamte Gruppe drehen muss?* | Verwenden Sie `group.setRotationAngle(double angleInDegrees)` vor dem Speichern. |

## Vollständiges, ausführbares Beispiel

Unten finden Sie das vollständige Programm, das Sie in Ihre IDE kopieren und einfügen können. Es enthält alle erforderlichen Importe und Kommentare.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 2: Insert a group shape (container)
        GroupShape group = builder.insertGroupShape(300.0, 200.0);

        // Step 3: Add a rectangle shape and set its size
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(150.0);
        rectangle.setHeight(100.0);
        rectangle.setLeft(20.0);
        rectangle.setTop(20.0);
        group.appendChild(rectangle);

        // Step 4: Add a line shape and configure its dimensions
        Shape line = new Shape(document, ShapeType.LINE);
        line.setWidth(200.0);
        line.setHeight(0.0);
        line.setLeft(20.0);
        line.setTop(130.0);
        group.appendChild(line);

        // Step 5: Save the document with the grouped shapes
        document.save("GroupShapeDemo.docx");
    }
}
```

Führen Sie das Programm aus, öffnen Sie `GroupShapeDemo.docx` in Microsoft Word, und Sie sehen die gruppierten Formen exakt wie beschrieben.

## Fazit

Sie wissen jetzt, wie man mit Aspose.Words for Java **ein leeres Word-Dokument erstellt**, **Formen in Word gruppiert**, **ein Rechteck hinzufügt** und **die Formgröße festlegt**. Durch das Platzieren von Formen in einem `GroupShape` erhalten Sie die vollständige Kontrolle über die gemeinsame Positionierung, Skalierung und Drehung – ideal für Diagramme, Flussdiagramme oder benutzerdefinierte Grafiken, die in automatisierten Berichten eingebettet sind.

**Nächste Schritte:**  
- Erkunden Sie **wie man Formen gruppiert** mit komplexeren Objekten wie Bildern oder Textfeldern.  
- Experimentieren Sie mit `setRotationAngle`, um die gesamte Gruppe zu drehen.  
- Kombinieren Sie diese Technik mit Seriendruck, um personalisierte Dokumente zu erzeugen, die Marken‑Grafiken enthalten.

Passen Sie den Code gerne für Ihre eigenen Projekte an und teilen Sie Ihre Ergebnisse in den Kommentaren!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Handbuch gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform in Word mit Java erstellen – Vollständige Anleitung](/words/english/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/)
- [Word‑Dokument mit Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Gruppenform in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}