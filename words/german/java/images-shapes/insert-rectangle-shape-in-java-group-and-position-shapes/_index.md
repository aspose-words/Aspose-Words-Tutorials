---
category: general
date: 2026-07-26
description: Rechteckform in Java mit Aspose.Words einfügen. Erfahren Sie, wie Sie
  die Größe der Form festlegen, die Form positionieren und Formen in einer DOCX-Datei
  gruppieren.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: de
lastmod: 2026-07-26
og_description: Fügen Sie in Java ein Rechteck ein, um reichhaltige DOCX‑Grafiken
  zu erstellen. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung, um die Größe der
  Form festzulegen, die Form zu positionieren und Formen mühelos zu gruppieren.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Rechteckform in Java einfügen – Gruppierung und Positionierung meistern
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Rechteckform in Java einfügen – Formen gruppieren und positionieren
url: /de/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Java einfügen – Formen gruppieren und positionieren

Haben Sie schon einmal **eine Rechteckform** in ein Word‑Dokument einfügen müssen, während Sie Java‑Code schreiben? Sie sind nicht allein – Entwickler, die Berichte, Rechnungen oder benutzerdefinierte Vorlagen erstellen, stoßen ständig auf dieses Problem. Die gute Nachricht: Mit nur wenigen Zeilen Aspose.Words für Java können Sie **eine Rechteckform einfügen**, **die Formgröße festlegen**, **die Form positionieren** und sogar **Formen gruppieren**, sodass sie sich als Einheit bewegen.

In diesem Leitfaden gehen wir den gesamten Prozess von der Erstellung eines leeren Dokuments bis zum Speichern einer `.docx`‑Datei durch, die zwei Rechtecke sauber gruppiert enthält. Am Ende wissen Sie **wie man Rechtecke** hinzufügt, ihre Abmessungen steuert, sie exakt dort platziert, wo Sie sie benötigen, und sie zu einer wiederverwendbaren Gruppe bündelt. Keine externen Bibliotheken außer Aspose.Words sind erforderlich, und der Code funktioniert mit Java 8 plus.

## Voraussetzungen

- Java 8 oder neuer installiert (ich verwende JDK 17, aber alles, was Maven unterstützt, reicht)
- Aspose.Words für Java 23.9 oder später – fügen Sie die Abhängigkeit zu Ihrer `pom.xml` hinzu oder laden Sie das JAR herunter
- Grundlegendes Verständnis der Java‑Syntax (wenn Sie eine `main`‑Methode schreiben können, sind Sie startklar)
- Eine IDE oder ein Texteditor Ihrer Wahl (IntelliJ IDEA, Eclipse, VS Code …)

> **Pro‑Tipp:** Wenn Sie Maven verwenden, sieht die Abhängigkeit so aus:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Jetzt, wo die Grundlagen stehen, tauchen wir in den Code ein.

## Rechteckform einfügen und Größe festlegen

Als Erstes erstellen Sie ein frisches `Document` und einen `DocumentBuilder`. Der Builder ist Ihr „Stift“, der Formen auf die Seite zeichnet. Unten **fügen wir eine Rechteckform ein** und setzen sofort **die Formgröße** auf 100 × 80 Punkte.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Beachten Sie, dass die Aufrufe `setWidth`/`setHeight` **die Formgröße** in Punkten festlegen (1 pt ≈ 1/72 Zoll). Sie könnten auch `setSize` verwenden, wenn Ihnen eine einzelne Methode lieber ist, aber die expliziten Aufrufe machen die Absicht kristallklar.

## Form auf der Seite positionieren

Nachdem wir das erste Rechteck haben, müssen wir **die Form** des zweiten Rechtecks so **positionieren**, dass sie das erste nicht überlappt. Das Positionieren funktioniert auf dieselbe Weise: Sie setzen die Eigenschaften `Left` und `Top` relativ zum Ursprung der Gruppe.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Falls Sie sich fragen, warum wir `setLeft` anstelle von `setX` verwenden, liegt das daran, dass Aspose.Words das klassische Windows‑GDI‑Koordinatensystem übernimmt – `Left` ist der horizontale Versatz, `Top` der vertikale Versatz. Durch Ändern dieser Werte können Sie das Layout feinjustieren, ohne mit Tabellen oder Absätzen zu hantieren.

## Wie man Formen gruppiert

Sie fragen sich vielleicht: „Warum überhaupt eine Gruppe?“ Das Gruppieren ist sinnvoll, wenn Sie möchten, dass Formen zusammen verschoben, als Einheit rotiert oder einen gemeinsamen Stil teilen. Im obigen Snippet haben wir bereits ein `GroupShape` über `builder.insertGroupShape` erstellt. Dieses Objekt ist im Wesentlichen ein Container – denken Sie an einen Ordner, der andere Form‑Dateien enthält.

> **Warum das wichtig ist:** Wenn Sie später eine Beschriftung hinzufügen oder das gesamte Diagramm drehen möchten, müssen Sie nur die Gruppe ändern, nicht jedes Rechteck einzeln.

## Wie man ein Rechteck zu einer Gruppe hinzufügt

Der Vorgang **wie man ein Rechteck** zur Gruppe hinzufügt, besteht einfach darin, `group.appendChild(rectangle)` aufzurufen. Im Hintergrund aktualisiert Aspose.Words die interne Sammlung der Gruppe und berechnet die Begrenzungsbox automatisch neu, sodass die Gruppe weiterhin ihre deklarierte Breite und Höhe einhält.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Sie können mit anderen `ShapeType`s experimentieren – `ShapeType.ELLIPSE`, `ShapeType.TRIANGLE` usw. – und das gleiche `appendChild`‑Muster funktioniert.

## Dokument speichern

Abschließend schreiben wir das Dokument auf die Festplatte. Der Pfad kann absolut oder relativ sein; stellen Sie nur sicher, dass der Ordner existiert.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Wenn Sie `GroupShape.docx` in Microsoft Word öffnen, sehen Sie zwei Rechtecke nebeneinander, beide in einem hellgrauen Kasten eingeschlossen. Das Auswählen des grauen Kastens hebt beide Rechtecke gleichzeitig hervor – ein Beweis dafür, dass **wie man Formen gruppiert** wirklich funktioniert.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Beispiel für das Einfügen einer Rechteckform, das zwei gruppierte Rechtecke in einer Java‑generierten DOCX‑Datei zeigt"}

*Bild‑Alt‑Text (SEO):* **Beispiel für das Einfügen einer Rechteckform, das zwei gruppierte Rechtecke in einer Java‑generierten DOCX‑Datei zeigt**.

## Erwartete Ausgabe

- Eine `GroupShape.docx`‑Datei im Ordner `output`.
- Im Dokument: eine 400 × 200 pt‑Gruppe, die zwei Rechtecke (100 × 80 pt und 120 × 60 pt) enthält, positioniert bei (20, 30) bzw. (150, 50).
- Die Gruppe hat einen dünnen schwarzen Rand und eine hellgraue Füllung, sodass die Gruppierung optisch deutlich wird.

Öffnen Sie die Datei und versuchen Sie, den grauen Kasten zu ziehen – beide Rechtecke sollten sich gemeinsam bewegen. Wenn das nicht funktioniert, prüfen Sie, ob Sie `group.appendChild` für jede Form aufgerufen haben.

## Häufige Stolperfallen & Randfälle

| Problem | Warum es passiert | Lösung |
|-------|----------------|-----|
| **Rechtecke erscheinen außerhalb der Seite** | `Left`/`Top`‑Werte überschreiten die Gruppengröße | Gruppengröße erhöhen (`insertGroupShape(width, height)`) oder Versätze reduzieren |
| **Gruppe verschwindet nach dem Speichern** | Die `Width`/`Height` der Gruppe sind 0 | Nicht‑null‑Dimensionen beim Aufruf von `insertGroupShape` angeben |
| **Formfarben sehen falsch aus** | Standardfüllung ist transparent; Word rendert sie als weiß | Explizit `setFillColor` setzen oder `ShapeStyle` verwenden |
| **Ausnahme `ArgumentOutOfRangeException`** | Negative Koordinaten verwendet | `Left` und `Top` nicht‑negativ halten |

Das frühzeitige Behandeln dieser Punkte erspart Ihnen die „Warum verschwindet meine Form?“-Kopfschmerzen, die viele Einsteiger erleben.

## Zusammenfassung & nächste Schritte

Wir haben den gesamten Lebenszyklus von **Rechteckform einfügen** in Java behandelt: Dokument erstellen, **Formgröße festlegen**, **Form positionieren**, **wie man Formen gruppiert** und **wie man ein Rechteck** zu dieser Gruppe hinzufügt. Das vollständige, ausführbare Beispiel befindet sich im Code‑Block oben, und Sie können es direkt in ein Maven‑Projekt einfügen, um das Ergebnis zu sehen.

Was kommt als Nächstes? Experimentieren Sie mit:

- Text in jedes Rechteck einfügen via


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}