---
category: general
date: 2026-11-25
description: Wie man Formen in Word mit Java gruppiert und wie man Formabmessungen
  in einer DOCX-Datei mit Aspose.Words festlegt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes in word
- how to set shape dimensions
- set shape size word
language: de
lastmod: 2026-11-25
og_description: Wie man Formen in Word mit der Aspose.Words Java API gruppiert und
  die Größe von Formen in Word schnell festlegt. Folgen Sie der vollständigen Schritt‑für‑Schritt‑Lösung.
og_image_alt: Screenshot of a Word document showing grouped rectangle and ellipse
  shapes created with Java
og_title: Wie man Formen in Word gruppiert und ihre Abmessungen festlegt – Java‑Leitfaden
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  headline: How to group shapes in Word and set their dimensions programmatically
  type: TechArticle
- description: How to group shapes in Word using Java and how to set shape dimensions
    in a DOCX file with Aspose.Words.
  name: How to group shapes in Word and set their dimensions programmatically
  steps:
  - name: Expected output
    text: '* A Word document (`GroupShape.docx`) with one page. * A `GroupShape` containing
      a 100 × 50 pt rectangle and an 80 × 80 pt ellipse. * Selecting either shape
      selects the whole group.'
  - name: How to change the position of the grouped shapes?
    text: 'After creating the `GroupShape`, you can set its `left` and `top` properties:'
  - name: What if I need to add more than two shapes?
    text: '`GroupShape` works like any other container node. Call `groupShape.appendChild(yourShape)`
      for each additional shape. The API does not limit the number of children.'
  - name: Can I apply style (fill color, line weight) to individual shapes?
    text: 'Yes. Each `Shape` object exposes formatting properties:'
  - name: Does the code work with older Aspose.Words versions?
    text: The `insertGroupShape` method was introduced in version 24.9. If you are
      on an earlier version, you’ll need to create a `GroupShape` manually via the
      node tree, which is more involved. Upgrading is the recommended path.
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
- shapes
title: Wie man Formen in Word gruppiert und ihre Abmessungen programmgesteuert festlegt
url: /de/java/images-shapes/how-to-group-shapes-in-word-and-set-their-dimensions-program/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in Word gruppiert und ihre Abmessungen programmgesteuert festlegt

Wenn Sie **wie man Formen in Word gruppiert** und deren genaue Größe steuern möchten, zeigt Ihnen diese Anleitung eine vollständige, ausführbare Lösung. Mit Aspose.Words für Java können Sie ein Rechteck, eine Ellipse erstellen, sie zu einer `GroupShape` hinzufügen und dann **wie man Formabmessungen festlegt**, etwa Breite und Höhe, in einer einzigen DOCX‑Datei.

Sie lernen, wie man:

* Ein neues Word‑Dokument von Grund auf erstellt.  
* Eine `GroupShape` einfügt (neue API in Version 24.9).  
* Ein Rechteck und eine Ellipse zur Gruppe hinzufügt.  
* **Formgröße in Word** präzise mit `setWidth` und `setHeight` festlegt.  
* Das Dokument auf die Festplatte speichert.

Keine externen Werkzeuge sind nötig – nur Java 17+, Maven und die Aspose.Words für Java‑Bibliothek.

## Voraussetzungen

* Java Development Kit 17 oder neuer.  
* Maven (oder Gradle) für das Abhängigkeitsmanagement.  
* Aspose.Words für Java 24.9 oder später (die `GroupShape`‑API wurde in 24.9 eingeführt).  
* Grundlegende Kenntnisse der Java‑Syntax und objektorientierter Konzepte.

Falls Sie Aspose.Words noch nicht zu Ihrem Projekt hinzugefügt haben, fügen Sie die folgende Maven‑Abhängigkeit ein:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version>
</dependency>
```

## Schritt 1: Ein neues Dokument und einen DocumentBuilder erstellen

Die Klasse `Document` repräsentiert die gesamte Word‑Datei, während `DocumentBuilder` einen bequemen Weg bietet, Inhalte hinzuzufügen.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a DocumentBuilder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Warum dieser Schritt?*  
Ein frisches `Document` gibt Ihnen eine leere Leinwand. `DocumentBuilder` ist der hochrangige Helfer, mit dem Sie Absätze, Tabellen und in diesem Fall Formen einfügen können.

## Schritt 2: Eine GroupShape einfügen (neue API in Version 24.9)

Eine `GroupShape` wirkt wie ein Container; jede Form, die Sie hinzufügen, wird Teil derselben visuellen Gruppe.

```java
        // Step 2: Insert a GroupShape (new API in version 24.9)
        GroupShape groupShape = builder.insertGroupShape();
```

*Warum `GroupShape` verwenden?*  
Das Gruppieren von Formen vereinfacht das Verschieben, Drehen oder Anwenden von Formatierungen auf mehrere Objekte gleichzeitig. Die API wurde in 24.9 hinzugefügt, ältere Versionen können diese Zeile nicht kompilieren.

## Schritt 3: Ein Rechteck erstellen, seine Größe festlegen und zur Gruppe hinzufügen

Hier demonstrieren wir **wie man Formabmessungen festlegt** für ein Rechteck.

```java
        // Step 3: Create a rectangle, set its size, and add it to the group
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points (1 point = 1/72 inch)
        rectangle.setHeight(50.0);   // height in points
        groupShape.appendChild(rectangle);
```

*Warum Breite und Höhe explizit setzen?*  
Word speichert die Formgröße in Punkten. Durch Aufruf von `setWidth` und `setHeight` bestimmen Sie den genauen visuellen Platzbedarf, was bei präzisem Layout oder beim Export nach PDF unerlässlich ist.

## Schritt 4: Eine Ellipse erstellen, ihre Größe festlegen und zur selben Gruppe hinzufügen

Die gleiche **Formgröße‑Word**‑Technik funktioniert für jeden Formtyp.

```java
        // Step 4: Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(document, ShapeType.ELLIPSE);
        ellipse.setWidth(80.0);
        ellipse.setHeight(80.0);
        groupShape.appendChild(ellipse);
```

*Warum die Ellipse zur selben `GroupShape` hinzufügen?*  
Beide Formen bewegen sich zusammen als Einheit. Das ist nützlich für Icons, Logos oder komplexe Diagramme, die ausgerichtet bleiben müssen.

## Schritt 5: Das Dokument mit den gruppierten Formen speichern

Abschließend das DOCX‑File auf die Festplatte schreiben.

```java
        // Step 5: Save the document with the grouped shapes
        document.save("GroupShape.docx");
    }
}
```

Wenn Sie dieses Programm ausführen, entsteht eine Datei namens **GroupShape.docx**, die ein Rechteck und eine Ellipse enthält, die zusammen gruppiert sind. Öffnen Sie die Datei in Microsoft Word, sehen Sie, dass sich die beiden Formen wie ein einzelnes Objekt verhalten – Sie können sie gemeinsam ziehen, skalieren oder drehen.

### Erwartete Ausgabe

* Ein Word‑Dokument (`GroupShape.docx`) mit einer Seite.  
* Eine `GroupShape`, die ein 100 × 50 pt Rechteck und eine 80 × 80 pt Ellipse enthält.  
* Das Auswählen einer Form wählt die gesamte Gruppe aus.

## Häufige Fragen und Sonderfälle

### Wie ändert man die Position der gruppierten Formen?

Nachdem Sie die `GroupShape` erstellt haben, können Sie deren `left`‑ und `top`‑Eigenschaften setzen:

```java
groupShape.setLeft(150.0);
groupShape.setTop(200.0);
```

Diese Koordinaten werden ebenfalls in Punkten gemessen.

### Was, wenn ich mehr als zwei Formen hinzufügen muss?

`GroupShape` funktioniert wie jeder andere Container‑Knoten. Rufen Sie `groupShape.appendChild(yourShape)` für jede zusätzliche Form auf. Die API begrenzt die Anzahl der Kinder nicht.

### Kann ich Stil (Füllfarbe, Linienstärke) auf einzelne Formen anwenden?

Ja. Jedes `Shape`‑Objekt stellt Formatierungseigenschaften bereit:

```java
rectangle.getFillColor().setColor(Color.BLUE);
ellipse.getStroke().setWeight(2.0);
```

### Funktioniert der Code mit älteren Aspose.Words‑Versionen?

Die Methode `insertGroupShape` wurde in Version 24.9 eingeführt. Wenn Sie eine frühere Version verwenden, müssen Sie eine `GroupShape` manuell über den Knotebaum erstellen, was aufwändiger ist. Ein Upgrade wird empfohlen.

## Pro‑Tipps

* **Punkte für Konsistenz verwenden** – Word’s interne Einheit ist der Punkt (1/72 Zoll). Die Umrechnung von Pixeln oder Zentimetern kann zu unerwarteten Größen führen.  
* **Gruppieren, bevor Sie positionieren** – Positionieren Sie die `GroupShape` erst, nachdem Sie alle Kinder hinzugefügt haben; sonst müssen Sie ggf. Offsets neu berechnen.  
* **DocumentBuilder wiederverwenden** – Sie können mehrere Gruppen im selben Dokument einfügen, indem Sie den Cursor des Builders (`builder.moveTo`) vor jedem `insertGroupShape`‑Aufruf verschieben.

## Fazit

Sie haben nun ein vollständiges End‑zu‑Ende‑Beispiel, wie man **Formen in Word gruppiert** und **Formabmessungen festlegt** mit Aspose.Words für Java. Das Tutorial behandelte das Erstellen eines Dokuments, das Einfügen einer `GroupShape`, das Hinzufügen eines Rechtecks und einer Ellipse, das Festlegen ihrer genauen Größe und das Speichern des Ergebnisses.  

Ab hier können Sie:

* Textfelder oder Bilder zur selben Gruppe hinzufügen.  
* Gruppierte Formen mit Word‑Smart‑Art‑Funktionen animieren (über die API).  
* Die gruppierten Formen nach PDF oder SVG für die Web‑Nutzung exportieren.

Experimentieren Sie gern mit verschiedenen Formtypen, Größen und Positionen – das Gruppieren gibt Ihnen mächtige Kontrolle über komplexe Layouts in Word‑Dokumenten.

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create a blank Word document and group shapes in Java](/words/english/java/images-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-java/)
- [How to group shapes in Word with Java – complete guide](/words/english/java/images-shapes/how-to-group-shapes-in-word-with-java-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}