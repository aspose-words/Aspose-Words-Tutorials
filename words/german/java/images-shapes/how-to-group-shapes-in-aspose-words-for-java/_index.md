---
category: general
date: 2026-10-20
description: Wie man Formen in Aspose.Words für Java gruppiert – lernen Sie, wie man
  ein Rechteck einfügt, sie gruppiert und das Dokument speichert, in einer einzigen
  Anleitung.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: de
lastmod: 2026-10-20
og_description: Wie man Formen in Aspose.Words für Java gruppiert. Dieses Tutorial
  zeigt, wie man ein Rechteck einfügt, sie gruppiert und das Ergebnis exportiert.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: Wie man Formen in Aspose.Words für Java gruppiert – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Wie man Formen in Aspose.Words für Java gruppiert
url: /de/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man Formen in Aspose.Words für Java gruppiert

Wenn Sie **wie man Formen gruppiert** in einem Word‑Dokument mit Aspose.Words für Java benötigen, zeigt Ihnen diese Anleitung den kompletten Arbeitsablauf. Sie lernen, wie man **Rechteckform einfügt**, ein zweites Rechteck hinzufügt, die beiden Formen gruppiert und schließlich die Datei speichert – alles mit klarem, ausführbarem Code.

Das Gruppieren von Formen ist nützlich, wenn Sie mehrere Zeichnungen als eine Einheit verschieben, drehen oder formatieren möchten. Egal, ob Sie eine Berichtsvorlage, ein Diagramm oder einen individuellen Flyer erstellen, das Beherrschen der Form‑Gruppierung spart Zeit und sorgt für ein konsistentes Layout.

In diesem Tutorial werden Sie:

* Ein neues `Document` und einen `DocumentBuilder` erstellen.
* **Wie man Rechtecke einfügt** mit genauen Abmessungen.
* Die Rechtecke in ein `GroupShape` gruppieren.
* Das Dokument speichern und das Ergebnis überprüfen.

> **Voraussetzung** – Sie müssen Aspose.Words für Java (v23.12 oder neuer) zu Ihrem Projekt hinzugefügt haben. Maven‑Benutzer können die unten gezeigte Abhängigkeit einbinden.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Was Sie benötigen

| Element | Grund |
|---------|-------|
| Java 17+ | Moderne Sprachfeatures und bessere Performance |
| Aspose.Words for Java | Stellt die APIs `DocumentBuilder`, `Shape` und `GroupShape` bereit |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Zum Kompilieren und Ausführen des Beispiels |
| Schreibberechtigung für einen Ordner | Das Dokument wird auf die Festplatte gespeichert |

---

## Wie man eine Rechteckform einfügt

Der erste Schritt besteht darin, ein `Document` und einen `DocumentBuilder` zu erstellen. Der Builder stellt Methoden wie `insertShape` bereit, um Zeichenobjekte zu platzieren.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Warum das wichtig ist** – Die Verwendung von `insertShape` ist der Standardweg **wie man Rechtecke** in Aspose.Words einzufügen. Sie fügt die Form automatisch dem aktuellen Absatz des Dokuments hinzu, sodass Sie sich nicht um Low‑Level‑OpenXML kümmern müssen.

---

## Anpassen der Rechteckpositionen (optional)

Falls das zweite Rechteck eine benutzerdefinierte Position relativ zum ersten benötigt, können Sie dessen Eigenschaften `left` und `top` ändern. Dieser Schritt ist optional, wird aber häufig für ein präzises Diagrammlayout benötigt.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro‑Tipp:** Alle Maße sind in Punkten (1 pt ≈ 1/72 in). Verwenden Sie `convertPointsToPixels`, wenn Sie Pixelwerte für UI‑basierte Berechnungen benötigen.

---

## Wie man Formen gruppiert

Jetzt, wo die Rechtecke existieren, können Sie sie in ein `GroupShape` einfügen. Das Gruppieren lässt die beiden Rechtecke wie ein einzelnes Objekt verhalten – Verschieben, Drehen oder Formatieren der Gruppe wirkt sich auf beide Formen aus.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Warum das Gruppieren funktioniert** – `GroupShape` erbt von `Shape`, sodass Sie die Gruppe genauso behandeln können wie jedes andere Zeichenobjekt. Wenn Sie `appendChild` aufrufen, werden die Formen aus ihrer ursprünglichen Position entfernt und zu Kindern der Gruppe.

---

## Speichern des Dokuments mit den gruppierten Formen

Zum Schluss schreiben Sie das Dokument auf die Festplatte. Die Datei enthält ein einzelnes `GroupShape` mit zwei Rechtecken darin.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Erwartetes Ergebnis

Öffnen Sie `GroupShape.docx` in Microsoft Word:

* Sie sehen zwei Rechtecke (blau und grün), die nebeneinander positioniert sind.
* Das Auswählen eines Rechtecks wählt die gesamte Gruppe aus – das Ziehen bewegt beide gleichzeitig.
* Die Gruppe hat einen dünnen roten Rand, der bestätigt, dass die `GroupShape`‑Eigenschaften angewendet wurden.

Wenn Sie mit der rechten Maustaste auf die Gruppe klicken und **Group → Ungroup** wählen, kehren die Rechtecke zu unabhängigen Formen zurück, was zeigt, dass die Gruppierungsoperation umkehrbar ist.

---

## Häufige Variationen und Sonderfälle

| Situation | Wie man damit umgeht |
|-----------|----------------------|
| **Mehr als zwei Formen** | Jede Form einfügen und dann alle zum selben `GroupShape` hinzufügen. |
| **Unterschiedliche Formtypen** (z. B. Ellipse, Bild) | Verwenden Sie `builder.insertShape(ShapeType.ELLIPSE, …)` oder `builder.insertImage(...)`, bevor Sie sie anhängen. |
| **Skalieren der Gruppe** | Rufen Sie `group.setWidth(newWidth)` oder `group.setHeight(newHeight)` auf; Kinder skalieren proportional. |
| **Drehen der Gruppe** | `group.setRotationAngle(45);` dreht die gesamte Sammlung um ihr Zentrum. |
| **Ursprüngliche Positionen beibehalten** | Speichern Sie `left`/`top` jeder Form vor dem Gruppieren und stellen Sie sie nach dem Aufheben der Gruppierung wieder her, falls nötig. |

---

## Vollständiges, ausführbares Beispiel

Unten finden Sie die komplette Java‑Klasse, die Sie in Ihre IDE kopieren‑und‑einfügen können. Sie enthält alle Importe, Fehlerbehandlung und Kommentare zur Klarheit.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Führen Sie das Programm aus, öffnen Sie das resultierende `GroupShape.docx` und Sie sehen die gruppierten Rechtecke exakt wie beschrieben.

---

## Fazit

Sie wissen jetzt **wie man Formen gruppiert** in Aspose.Words für Java, vom Erstellen eines Dokuments über das Einfügen von Rechteckformen, das Anpassen ihrer Positionen bis hin zum Gruppieren mit `GroupShape`. Diese Technik ermöglicht es, mehrere Zeichnungen als eine Einheit zu behandeln, was Layout‑Anpassungen und visuelle Konsistenz vereinfacht.

**Nächste Schritte**

* Erkunden Sie **wie man Rechtecke einfügt** mit unterschiedlichen Füllmustern oder Rändern.  
* Kombinieren Sie **Rechteckform einfügen** mit Textfeldern, um beschriftete Diagramme zu erstellen.  
* Experimentieren Sie mit dem Drehen oder Skalieren der Gruppe, um komplexere Grafiken zu erzeugen.

Passen Sie den Code gern für andere Formtypen, größere Gruppen oder dynamische Dokumentengenerierungsszenarien an. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform in Java einfügen – Formen gruppieren und positionieren](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [wie man Gruppierungsform in Java einfügt – Komplett‑Leitfaden](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Wie man einem Shape in Aspose.Words einen Schatten hinzufügt – Komplett‑Leitfaden](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}