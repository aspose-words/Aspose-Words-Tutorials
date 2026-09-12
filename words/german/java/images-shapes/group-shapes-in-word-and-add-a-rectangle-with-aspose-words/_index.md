---
category: general
date: 2026-09-11
description: Gruppieren Sie Formen in Word und fügen Sie eine Rechteckform mit Aspose.Words
  für Java hinzu. Erfahren Sie, wie Sie die Formgröße festlegen, Objekte gruppieren
  und das Dokument speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- set shape size
- how to group shapes
- how to add rectangle
language: de
lastmod: 2026-09-11
og_description: Formen in Word gruppieren und ein Rechteck mit Aspose.Words für Java
  hinzufügen. Dieses Tutorial zeigt, wie man die Formgröße festlegt, Formen gruppiert
  und das Dokument exportiert.
og_image_alt: Screenshot showing grouped shapes in a Word document
og_title: Formen in Word gruppieren – Rechteck mit Aspose.Words hinzufügen
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  headline: Group shapes in Word and add a rectangle with Aspose.Words
  type: TechArticle
- description: Group shapes in Word and add a rectangle shape using Aspose.Words for
    Java. Learn how to set shape size, group objects, and save the document.
  name: Group shapes in Word and add a rectangle with Aspose.Words
  steps:
  - name: Prerequisites
    text: '* Java 17 or later installed. * Maven or Gradle to manage dependencies.
      * A valid Aspose.Words for Java license (or a free evaluation key). * An image
      file (`sample.png`) placed in a known directory (replace `YOUR_DIRECTORY` with
      your actual path).'
  - name: Add a group shape
    text: A group shape is a container that can hold other shapes. Think of it as
      a folder for drawing objects.
  - name: How to add rectangle
    text: The code above demonstrates **how to add rectangle** by creating a `Shape`
      instance with `ShapeType.RECTANGLE` and then appending it to the `GroupShape`.
      This pattern works for any other shape type (e.g., `ELLIPSE`, `POLYLINE`).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word automation
title: Formen in Word gruppieren und ein Rechteck mit Aspose.Words hinzufügen
url: /de/java/images-shapes/group-shapes-in-word-and-add-a-rectangle-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Gruppieren von Formen in Word und Hinzufügen eines Rechtecks mit Aspose.Words

Wenn Sie **Formen in Word gruppieren** müssen, während Sie programmgesteuert ein Rechteck hinzufügen, bietet Ihnen dieser Leitfaden eine vollständige, sofort ausführbare Lösung. Sie sehen genau, wie man ein Gruppen‑Shape einfügt, ein Rechteck‑Shape hinzufügt, die Größe des Shapes festlegt und schließlich das Dokument speichert, damit Sie das Ergebnis sofort ansehen können.

Die Arbeit mit Word‑Dokumenten bedeutet oft, mehrere Objekte – Bilder, Diagramme oder einfache geometrische Formen – zu einer einzigen logischen Einheit zu arrangieren. Das Gruppieren dieser Objekte erleichtert das Verschieben, Drehen oder Stylen zusammen. In diesem Tutorial behandeln wir außerdem **wie man Rechtecke** hinzufügt und **die Größe von Shapes** für eine perfekte Layout‑Kontrolle festlegt.

## Was Sie lernen werden

* Wie man ein neues Word‑Dokument mit Aspose.Words für Java erstellt.  
* **Wie man Formen gruppiert**, sodass sie sich wie ein einzelnes Objekt verhalten.  
* **Rechteck‑Shape hinzufügen** zu einer Gruppe und ein Bild in dieselbe Gruppe einfügen.  
* **Shape‑Größe festlegen** für sowohl das Rechteck als auch das Bild.  
* Das Dokument speichern und in Microsoft Word öffnen, um das Ergebnis zu überprüfen.

### Voraussetzungen

* Java 17 oder höher installiert.  
* Maven oder Gradle zur Verwaltung von Abhängigkeiten.  
* Eine gültige Aspose.Words‑Lizenz für Java (oder ein kostenloser Evaluierungsschlüssel).  
* Eine Bilddatei (`sample.png`) in einem bekannten Verzeichnis abgelegt (ersetzen Sie `YOUR_DIRECTORY` durch Ihren tatsächlichen Pfad).

---

## Wie man Formen in Word mit Aspose.Words gruppiert

Der erste Schritt besteht darin, ein `Document` und einen `DocumentBuilder` zu erstellen. Der Builder bietet Ihnen eine bequeme API zum Einfügen von Shapes, Text und anderen Elementen.

```java
import com.aspose.words.*;

public class GroupShapesExample {
    public static void main(String[] args) throws Exception {
        // Initialize the document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Warum das wichtig ist:** `DocumentBuilder` arbeitet direkt mit dem zugrunde liegenden `Document`‑Objekt und ermöglicht das Einfügen von Shapes, ohne manuell low‑level‑Knoten‑Sammlungen zu handhaben.

### Eine Gruppen‑Shape hinzufügen

Eine Gruppen‑Shape ist ein Container, der andere Shapes aufnehmen kann. Denken Sie daran wie an einen Ordner für Zeichenobjekte.

```java
        // Insert an empty group shape – this will hold the rectangle and the picture
        GroupShape group = builder.insertGroupShape();
```

Die Methode `insertGroupShape()` erstellt einen `GroupShape`‑Knoten und gibt ihn zurück, sodass Sie später Kind‑Shapes anhängen können.  

## Ein Rechteck‑Shape zur Gruppe hinzufügen

Jetzt **fügen wir ein Rechteck‑Shape** zur zuvor erstellten Gruppe hinzu. Das Rechteck dient als Hintergrund oder Rahmen für das Bild.

```java
        // Create a rectangle shape with a specific size
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // width in points
        rectangle.setHeight(50.0);   // height in points
        rectangle.setFillColor(java.awt.Color.LIGHT_GRAY);
        rectangle.setStrokeColor(java.awt.Color.DARK_GRAY);
        rectangle.setStrokeWeight(1.0);
        // Append the rectangle to the group
        group.appendChild(rectangle);
```

> **Tipp:** Das Festlegen von `FillColor` und `StrokeColor` macht das Rechteck im endgültigen Dokument sichtbar. Wenn Sie diese Eigenschaften weglassen, könnte das Shape transparent erscheinen.

### Wie man ein Rechteck hinzufügt

Der obige Code demonstriert **wie man ein Rechteck hinzufügt**, indem er eine `Shape`‑Instanz mit `ShapeType.RECTANGLE` erstellt und sie dann an die `GroupShape` anhängt. Dieses Muster funktioniert für jeden anderen Shape‑Typ (z. B. `ELLIPSE`, `POLYLINE`).

## Shape‑Größe für Rechteck und Bild festlegen

Eine korrekte Größenbestimmung stellt sicher, dass das Rechteck und das Bild korrekt ausgerichtet sind. Hier legen wir außerdem **die Shape‑Größe** für das Bild fest, das wir als Nächstes einfügen werden.

```java
        // Insert an image and set its size
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.png");
        picture.setWidth(100.0);   // match rectangle width
        picture.setHeight(50.0);   // match rectangle height
        // Append the picture to the same group
        group.appendChild(picture);
```

Sowohl das Rechteck als auch das Bild haben jetzt dieselben Abmessungen (100 × 50 Punkte). Da sie zur selben Gruppe gehören, wirkt sich das Verschieben oder Drehen der Gruppe auf beide Shapes gleichzeitig aus.

> **Warum Größen angleichen?** Das Ausrichten der Abmessungen garantiert, dass das Bild sauber innerhalb des Rechtecks sitzt und einen sauberen „gerahmten Bild“-Effekt erzeugt.

## Das Dokument speichern und das Ergebnis anzeigen

Abschließend schreiben wir das Dokument auf die Festplatte. Das Öffnen der Datei in Microsoft Word zeigt die gruppierten Shapes als ein einziges auswählbares Objekt.

```java
        // Save the document – the group will appear as one object in Word
        doc.save("YOUR_DIRECTORY/output.docx");
        System.out.println("Document saved successfully.");
    }
}
```

Wenn Sie `output.docx` öffnen, sehen Sie ein Rechteck mit dem Bild darin. Durch Klicken auf das Shape werden sowohl das Rechteck als auch das Bild ausgewählt, weil sie **gruppiert** sind.

![Gruppierte Formen in Word Beispiel](https://example.com/images/group-shapes-word.png "Gruppierte Formen in Word Beispiel")

*Bild‑Alt‑Text:* *Gruppierte Formen in Word Beispiel* – ein Word‑Dokument, das ein gruppiertes Rechteck und Bild zeigt.

## Häufige Fragen und Sonderfall‑Behandlung

| Frage | Antwort |
|----------|--------|
| **Was, wenn ich eine andere Größe für das Bild benötige?** | Passen Sie `picture.setWidth()` und `picture.setHeight()` nach dem Einfügen an. Das Rechteck kann seine ursprüngliche Größe behalten, oder Sie können es ebenfalls anpassen, um übereinzustimmen. |
| **Kann ich weitere Shapes zur selben Gruppe hinzufügen?** | Ja. Rufen Sie `group.appendChild(newShape)` für jedes zusätzliche `Shape`‑Objekt auf. |
| **Wie drehe ich die gesamte Gruppe?** | Verwenden Sie `group.setRotationAngle(double angleInRadians)`. Die Drehung wird auf jedes Kind‑Shape angewendet. |
| **Was, wenn die Bilddatei fehlt?** | `insertImage` wirft `FileNotFoundException`. Umschließen Sie den Aufruf in einem try‑catch‑Block und stellen Sie ein Ersatz‑Platzhalter‑Shape bereit. |
| **Ist es später möglich, die Gruppe aufzulösen?** | Rufen Sie `group.removeAllChildren()` auf, um die Kinder zu lösen, und fügen Sie sie anschließend einzeln wieder in das Dokument ein. |

## Fazit

Sie haben jetzt ein vollständiges, ausführbares Beispiel, das **zeigt, wie man Formen in Word gruppiert**, **ein Rechteck‑Shape hinzufügt**, **die Shape‑Größe festlegt** und das Dokument mit Aspose.Words für Java **speichert**. Durch das Gruppieren von Rechteck und Bild können Sie sie als Einheit verschieben, skalieren oder drehen – genau das, was viele Dokument‑Automatisierungsszenarien erfordern.

Ab hier könnten Sie folgendes erkunden:

* Textfelder zur selben Gruppe hinzufügen (`how to add rectangle`‑Style‑Text).  
* Unterschiedliche Füllmuster oder Verläufe anwenden (`set shape size` kombiniert mit Styling).  
* Die gleiche Technik verwenden, um Diagramme, Tabellen oder SmartArt zu gruppieren (`how to group shapes` über andere Objekttypen).  

Fühlen Sie sich frei, mit anderen Shape‑Typen, Farben und Layout‑Optionen zu experimentieren. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Word‑Dokument mit Java erstellen – Rechteck‑Shape mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Wie man Formularfelder erstellt und Inhalte mit DocumentBuilder in Aspose.Words für Java hinzufügt](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Wie man Word in PDF mit Aspose.Words für Java konvertiert](/words/english/java/document-converting/using-document-converting/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}