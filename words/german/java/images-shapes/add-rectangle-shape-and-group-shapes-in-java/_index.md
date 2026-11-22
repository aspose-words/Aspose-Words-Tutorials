---
category: general
date: 2026-11-22
description: Füge in einem Word-Dokument mit Java ein Rechteck ein, setze die Größe
  der Form, gruppiere mehrere Formen und füge die Form effizient zur Gruppe hinzu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: de
lastmod: 2026-11-22
og_description: Fügen Sie in einem Word-Dokument mit Java ein Rechteck ein, setzen
  Sie anschließend die Größe der Form, gruppieren Sie mehrere Formen und fügen Sie
  die Form einer Gruppe in einem einzigen Arbeitsablauf hinzu.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Rechteck hinzufügen und Formen gruppieren in Java – vollständige Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Rechteckform hinzufügen und Formen gruppieren in Java
url: /de/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform hinzufügen und Formen gruppieren in Java

Wenn Sie **eine Rechteckform** zu einem Word‑Dokument mit Java hinzufügen möchten, führt Sie diese Anleitung Schritt für Schritt durch den Vorgang. Sie erfahren außerdem, wie Sie **die Formgröße festlegen**, **mehrere Formen gruppieren** und **eine Form zur Gruppe hinzufügen** können, ohne die IDE zu verlassen.

Die Arbeit mit Vektorgrafiken in einer DOCX‑Datei fühlt sich oft an, als müsste man verschiedene APIs jonglieren. Am Ende dieses Tutorials besitzen Sie ein einzelnes, eigenständiges Programm, das ein Rechteck, eine Ellipse und beliebige weitere Formen erstellt, diese dann gruppiert, sodass sie sich wie ein Objekt bewegen. Keine externen Werkzeuge sind nötig, außer Aspose.Words für Java.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java 17 oder höher installiert.
* Maven 3.8+ (oder Gradle) zur Verwaltung der Abhängigkeiten.
* Eine gültige Aspose.Words‑für‑Java‑Lizenz (die Evaluation funktioniert zum Testen).
* Eine IDE wie IntelliJ IDEA oder VS Code, wobei jeder Texteditor ausreicht.

Diese Voraussetzungen ermöglichen das Kompilieren und Ausführen des Codes in jeder modernen Entwicklungsumgebung.

## Schritt 1: Maven‑Projekt einrichten

Erstellen Sie ein neues Maven‑Projekt oder fügen Sie die Aspose.Words‑Abhängigkeit zu einer bestehenden `pom.xml` hinzu:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

Die Abhängigkeit zieht alle Klassen, die für die Dokumentenbearbeitung benötigt werden, einschließlich `Document`, `DocumentBuilder`, `Shape` und `GroupShape`. Maven lädt die JAR‑Dateien automatisch herunter, wenn Sie `mvn compile` ausführen.

## Schritt 2: Dokument laden und einen DocumentBuilder erstellen

Ein `DocumentBuilder` stellt die Fluent‑API zum Einfügen von Inhalten bereit. Laden Sie ein vorhandenes DOCX oder beginnen Sie mit einem leeren Dokument:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Das frühe Erzeugen des Builders gibt Ihnen einen Cursor, der am Anfang des Dokuments positioniert ist und bereit für das Einfügen von Formen ist.

## Rechteckform zu einem Word‑Dokument hinzufügen

### Schritt 3: Das Rechteck einfügen

Das Rechteck ist das erste visuelle Element, das wir im Dokument platzieren wollen. Durch die Verwendung des `Shape`‑Konstruktors mit `ShapeType.RECTANGLE` erhalten Sie ein vollständig editierbares Objekt.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Das Hinzufügen des Rechtecks zu diesem Zeitpunkt beeinflusst das Layout nicht, bis seine Größe definiert und es einem Container hinzugefügt wird.

### Formgröße und Abmessungen festlegen

#### Schritt 4: Breite und Höhe definieren

Das Festlegen der Abmessungen der Form bestimmt, wie sie auf der Seite erscheint. Breite‑ und Höhenwerte werden in Punkten gemessen (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Sie können diese Zahlen an Ihre Design‑Anforderungen anpassen. Die gleichen Methoden gelten für jede `Shape`‑Instanz, sodass Sie sie für Kreise, Pfeile oder benutzerdefinierte Zeichnungen wiederverwenden können.

#### Schritt 5: Das Rechteck in das Dokument einfügen

Jetzt, wo das Rechteck eine Größe hat, platzieren Sie es auf der Seite. Die Methode `insertShape` von `DocumentBuilder` fügt die Form an der aktuellen Cursor‑Position ein.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

In diesem Stadium erscheint das Rechteck allein auf der Seite. Die nächsten Schritte zeigen, wie Sie es mit anderen Formen kombinieren.

## Mehrere Formen zusammen gruppieren

Das Gruppieren von Formen ermöglicht es Ihnen, sie als eine Einheit zu verschieben, zu drehen oder zu skalieren. Das ist besonders nützlich für komplexe Diagramme.

### Schritt 6: Einen Gruppen‑Shape‑Container erstellen

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

Der Aufruf `insertGroupShape` fügt dem Dokument einen leeren Container hinzu. Alle Formen, die diesem Container angehängt werden, werden Teil der Gruppe.

### Form zur Gruppe hinzufügen

#### Schritt 7: Das Rechteck zur Gruppe hinzufügen

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Durch das Anhängen wird das Rechteck vom Dokumentkörper in die interne Sammlung der Gruppe verschoben. Das Rechteck respektiert nun die Transformationen der Gruppe.

#### Schritt 8: Eine Ellipse zur Demonstration hinzufügen

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

Die Ellipse teilt denselben Koordinatenraum wie das Rechteck, sodass Sie sie visuell ausrichten können, indem Sie bei Bedarf die Eigenschaften `setLeft` und `setTop` anpassen.

### Schritt 9: Das Dokument speichern

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Das Ausführen des Programms erzeugt `output.docx`. Öffnen Sie die Datei in Microsoft Word oder LibreOffice; Sie sehen ein Rechteck und eine Ellipse, die zusammen gruppiert sind. Wenn Sie eine der Formen auswählen, wird die gesamte Gruppe hervorgehoben, was bestätigt, dass **Form zur Gruppe hinzufügen** erfolgreich war.

![Add rectangle shape example in Java](image.png){alt="Beispiel für das Hinzufügen einer Rechteckform in Java"}

*Der Screenshot zeigt das Rechteck und die Ellipse innerhalb einer einzigen Gruppe, bereit für die gemeinsame Manipulation.*

## Warum dieser Ansatz wichtig ist

* **Single source of truth** – Alle Form‑Eigenschaften werden festgelegt, bevor die Gruppe erstellt wird, wodurch Layout‑Fehler vermieden werden.
* **Wiederverwendbarkeit** – Die gleichen `setWidth`/`setHeight`‑Methoden funktionieren für jede Form, sodass Sie das Beispiel auf Pfeile, Sterne oder benutzerdefinierte SVGs ausweiten können.
* **Performance** – Das Gruppieren reduziert die Anzahl der Zeichenobjekte, die der Word‑Renderer verarbeiten muss, was die Öffnungsgeschwindigkeit großer Dokumente verbessert.
* **Wartbarkeit** – Durch das Zusammenhalten von Form‑Erstellung und Gruppierungslogik können zukünftige Entwickler Dimensionen ändern oder neue Formen hinzufügen, ohne in unverwandtem Code zu suchen.

## Häufige Varianten und Sonderfälle

| Szenario | Anpassung |
|----------|------------|
| **Andere Einheiten** | Verwenden Sie die Umrechnung `PointsToPixels` oder setzen Sie `Shape.setWrapType(WrapType.INLINE)` für Inline‑Platzierung. |
| **Gruppe rotieren** | Rufen Sie `groupShape.setRotation(45);` auf, um alle Kindformen um 45° zu drehen. |
| **Text zu einer Form hinzufügen** | Verwenden Sie `Shape.setText("Label");` nach dem Festlegen der Größe. |
| **Dynamische Größen** | Ermitteln Sie die Seitengröße über `doc.getFirstSection().getPageSetup().getPageWidth()` und berechnen Sie die Formgrößen proportional. |

Diese Varianten zeigen, wie das Kernmuster – **Rechteckform hinzufügen**, **Formgröße festlegen**, **mehrere Formen gruppieren**, **Form zur Gruppe hinzufügen** – an viele reale Anforderungen angepasst werden kann.

## Fazit

Sie wissen jetzt, wie Sie **eine Rechteckform** zu einem Word‑Dokument mit Java **hinzufügen**, **die Formgröße festlegen**, **mehrere Formen gruppieren** und **eine Form zur Gruppe hinzufügen** – und das auf saubere, wartbare Weise. Das vollständige Beispiel kompiliert zu einer einzigen ausführbaren Klasse, und die resultierende DOCX‑Datei demonstriert das erwartete Ergebnis.

Ab hier können Sie:

* Textbeschriftungen oder Hyperlinks zu jeder Form hinzufügen.
* Gruppen verschachteln, um hierarchische Diagramme zu erstellen.
* Das Dokument als PDF exportieren, wobei die Form‑Gruppen erhalten bleiben.

Experimentieren Sie gern mit unterschiedlichen Abmessungen, Farben und zusätzlichen Formtypen. Das Beherrschen der Form‑Manipulation öffnet die Tür zu automatisierter Berichtserstellung, dynamischen Diagrammen und reichhaltigen Dokumentenerlebnissen – alles direkt aus Java‑Code.

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Insert Rectangle Shape in Java – Group and Position Shapes](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [How to create and insert ellipse and rectangle shapes inside a group shape in a Word document using Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Create rectangle shape in a Word document using Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}