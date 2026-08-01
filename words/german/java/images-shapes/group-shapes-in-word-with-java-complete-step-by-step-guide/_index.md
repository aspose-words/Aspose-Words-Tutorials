---
category: general
date: 2026-08-01
description: Gruppieren von Formen in Word mit Java unter Verwendung von Aspose.Words.
  Erfahren Sie, wie Sie Formen gruppieren und schnell ein Rechteck einfügen können,
  mit einem vollständigen Codebeispiel.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- insert rectangle shape
- Aspose.Words Java
- shape grouping tutorial
- Word document automation
language: de
lastmod: 2026-08-01
og_description: Formen in Word mit Java gruppieren. Dieser Leitfaden zeigt, wie man
  Formen gruppiert, ein Rechteck einfügt und ein DOCX mit Aspose.Words speichert.
og_image_alt: Screenshot of grouped shapes in a Word document created with Java
og_title: Formen in Word mit Java gruppieren – Vollständige Schritt‑für‑Schritt‑Programmieranleitung
schemas:
- author: Aspose
  dateModified: '2026-08-01'
  description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  headline: Group Shapes in Word with Java – Complete Step-by-Step Guide
  type: TechArticle
- description: Group shapes in Word with Java using Aspose.Words. Learn how to group
    shapes and insert rectangle shape quickly with a full code example.
  name: Group Shapes in Word with Java – Complete Step-by-Step Guide
  steps:
  - name: 1. Can I group more than two shapes?
    text: 'Absolutely. Just pass a larger array to `insertGroupShape`:'
  - name: 2. What if I need to change the group’s position after creation?
    text: 'Use the group’s `setLeft` and `setTop` methods, just like any other shape:'
  - name: 3. How do I apply a border or fill to the whole group?
    text: The group itself can have formatting, but it doesn’t affect the children
      directly. If you want a common border, wrap the shapes in a rectangle shape
      first, then group everything. Alternatively, iterate over each child shape and
      set the same `fillColor` or `strokeWeight`.
  - name: 4. Does `setHidden(true)` affect printing?
    text: Hidden shapes are **not** printed by default in Word, which can be useful
      for watermarks or template markers. If you need the shape to print but stay
      invisible on screen, you’ll have to use a different approach (e.g., set its
      opacity to 0%).
  type: HowTo
tags:
- Aspose.Words
- Java
- Word Automation
title: Gruppieren von Formen in Word mit Java – Vollständiger Schritt‑für‑Schritt‑Leitfaden
url: /de/java/images-shapes/group-shapes-in-word-with-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formen in Word mit Java gruppieren – Vollständige Schritt‑für‑Schritt‑Anleitung

Wenn Sie **Formen in Word** mit Java **gruppieren** müssen, deckt dieser Leitfaden alles ab. Egal, ob Sie einen Berichtsgenerator oder eine dynamische Vorlagen‑Engine bauen – das Gruppieren von Formen lässt Ihre Dokumente professionell aussehen und hält zusammengehörige Grafiken gemeinsam.

In den nächsten Minuten sehen Sie genau **wie man Formen gruppiert** und **Rechteck‑Form‑Objekte** mit Aspose.Words einfügt, plus eine Handvoll praktischer Tipps, die Sie vor häufigen Fallstricken bewahren. Bereit, lose Rechtecke und Ellipsen in eine ordentliche Gruppe zu verwandeln? Dann legen wir los.

## Was dieses Tutorial behandelt

* Die minimalen Voraussetzungen (Java 17+, Aspose.Words 24.10 oder neuer).  
* Ein vollständiges, ausführbares Java‑Programm, das ein Word‑Dokument erstellt, ein Rechteck und eine Ellipse einfügt, sie gruppiert, die Gruppe bei Bedarf ausblendet und die Datei speichert.  
* Warum jeder API‑Aufruf wichtig ist, nicht nur was er tut.  
* Edge‑Case‑Behandlung für ältere Aspose.Words‑Versionen und für das Gruppieren von mehr als zwei Formen.  
* Erwartete Ausgabe und ein schneller Weg, das Ergebnis zu überprüfen.

Am Ende können Sie diesen Code‑Snippet in jedes Java‑Projekt einbinden und sofort Formen in Word gruppieren, ohne durch verstreute Dokumentation zu wühlen.

---

## Voraussetzungen

| Anforderung | Warum das wichtig ist |
|-------------|-----------------------|
| **Java 17+** | Moderne Sprachfeatures und bessere Performance. |
| **Aspose.Words für Java 24.10+** | Die später verwendete `setHidden`‑Methode existiert erst ab dieser Version. |
| **Ein Maven‑ oder Gradle‑Build** | Macht das Verwalten von Abhängigkeiten unkompliziert. |
| **Eine IDE (IntelliJ, Eclipse, VS Code)** | Praktisch für schnelles Testen, aber jeder Text‑Editor reicht aus. |

Fügen Sie die Aspose.Words‑Maven‑Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version>
</dependency>
```

Wenn Sie Gradle bevorzugen, lautet das Äquivalent:

```gradle
implementation 'com.aspose:aspose-words:24.10'
```

---

## Schritt 1: Neues Dokument und Builder erstellen

Zuerst erzeugen wir ein leeres `Document` und einen `DocumentBuilder`. Der Builder ist das Arbeitspferd, das das Einfügen von Formen, Text und mehr ermöglicht.

```java
// Step 1: Create a new empty document and a builder to work with it.
Document doc = new Document();                     // The container for all Word content.
DocumentBuilder builder = new DocumentBuilder(doc); // Fluent API to add elements.
```

*Warum dieser Schritt?*  
`Document` repräsentiert die gesamte DOCX‑Datei, während `DocumentBuilder` eine bequeme cursor‑basierte API bereitstellt. Ohne Builder müssten Sie low‑level‑Node‑Sammlungen manuell manipulieren – etwas, das leicht falsch gehen kann.

---

## Schritt 2: Ein Rechteck‑Shape (und eine Ellipse) einfügen

Jetzt fügen wir die beiden Grundformen hinzu, die wir gruppieren wollen. Beachten Sie den **insert rectangle shape**‑Aufruf – genau das sekundäre Stichwort, nach dem Sie suchen.

```java
// Step 2: Insert two simple shapes – a rectangle and an ellipse.
Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);
```

Ein paar Dinge, die Sie beachten sollten:

* Die Breite (`100`) und Höhe (`50`) werden in Punkten gemessen (1 pt ≈ 1/72 in). Passen Sie sie an Ihr Layout an.  
* Das Rechteck wird zuerst gezeichnet, sodass es standardmäßig hinter der Ellipse liegt. Wenn Sie die umgekehrte Reihenfolge benötigen, fügen Sie zuerst die Ellipse ein.  
* Beide Shapes erben die aktuelle Formatierung des Builders (Farbe, Linienstil). Sie können sie vor dem Gruppieren bei Bedarf anpassen.

---

## Schritt 3: Wie man Formen mit Aspose.Words gruppiert

Hier kommt der Kern des Tutorials – **wie man Formen gruppiert**. Die `insertGroupShape`‑API nimmt ein Array bestehender Shapes und gibt ein neues `Shape` zurück, das die Gruppe repräsentiert.

```java
// Step 3: Group the two shapes together using the InsertGroupShape API.
Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });
```

Warum eine Gruppe verwenden?

* Eine Gruppe bewegt sich als Einheit und bewahrt relative Positionen.  
* Sie können Transformationen (Drehung, Skalierung) auf das gesamte Set mit einem Aufruf anwenden.  
* Das Gruppieren vereinfacht spätere Bearbeitungen – bei Bedarf später entgruppieren, um einzelne Elemente zu ändern.

---

## Schritt 4 (optional): Die Gruppe aus der Dokumentenansicht ausblenden

Wenn die Gruppe nicht angezeigt werden soll, wenn der Benutzer das Dokument in Word öffnet, können Sie sie ausblenden. Dieser Schritt ist optional, aber praktisch für Hintergrundgrafiken oder Wasserzeichen.

```java
// Step 4: (Optional) Hide the group so it does not appear in the document view.
groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later
```

**Was, wenn Sie eine ältere Aspose.Words‑Version verwenden?**  
Die `setHidden`‑Methode lässt sich nicht kompilieren. In diesem Fall können Sie einen ähnlichen Effekt erzielen, indem Sie den `WrapType` des Shapes auf `NONE` setzen und es hinter die Textebene verschieben:

```java
groupShape.setWrapType(WrapType.NONE);
groupShape.getParagraph().getParagraphFormat().setStyleIdentifier(StyleIdentifier.BACKGROUND);
```

Das ist etwas ausführlicher, hält die Gruppe aber trotzdem aus dem Blickfeld des Lesers.

---

## Schritt 5: Dokument speichern

Zum Schluss schreiben wir das Dokument auf die Festplatte. Ändern Sie den Pfad nach Belieben, wo die Datei abgelegt werden soll.

```java
// Step 5: Save the document with the grouped shapes.
doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
```

Wenn Sie `GroupShapeResult.docx` in Microsoft Word öffnen, sehen Sie ein Rechteck und eine Ellipse, die sauber zusammengefasst sind. Wenn Sie `setHidden(true)` gesetzt haben, ist die Gruppe im Editor unsichtbar, bleibt aber in der Datei erhalten (nützlich für nachträgliche programmgesteuerte Verarbeitung).

---

## Vollständiges funktionierendes Beispiel

Alles zusammengeführt, hier die komplette, eigenständige Java‑Klasse, die Sie in Ihr Projekt kopieren‑und‑einfügen können:

```java
import com.aspose.words.*;

public class GroupShapeTutorial {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a builder to work with it.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert two simple shapes – a rectangle and an ellipse.
        Shape rectangleShape = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        Shape ellipseShape   = builder.insertShape(ShapeType.ELLIPSE, 100, 50);

        // Step 3: Group the two shapes together using the InsertGroupShape API.
        Shape groupShape = builder.insertGroupShape(new Shape[] { rectangleShape, ellipseShape });

        // Step 4: (Optional) Hide the group so it does not appear in the document view.
        groupShape.setHidden(true);   // Requires Aspose.Words 24.10 or later

        // Step 5: Save the document with the grouped shapes.
        doc.save("YOUR_DIRECTORY/GroupShapeResult.docx");
    }
}
```

**Erwartete Ausgabe:** Eine Datei namens `GroupShapeResult.docx`, die eine einzige Gruppe enthält, die ein blau gefülltes Rechteck und eine rot umrandete Ellipse (Standardfarben) hält. Öffnen Sie das Dokument, wählen Sie die Gruppe aus und klicken Sie mit der rechten Maustaste → **Group → Ungroup**, dann erscheinen die beiden ursprünglichen Formen wieder.

---

## Häufige Fragen & Edge Cases

### 1. Kann ich mehr als zwei Formen gruppieren?

Absolut. Übergeben Sie einfach ein größeres Array an `insertGroupShape`:

```java
Shape triangle = builder.insertShape(ShapeType.TRIANGLE, 80, 80);
Shape[] manyShapes = new Shape[] { rectangleShape, ellipseShape, triangle };
Shape bigGroup = builder.insertGroupShape(manyShapes);
```

Die API skaliert linear; die einzige Einschränkung ist der Speicherbedarf bei extrem großen Gruppen.

### 2. Was, wenn ich die Position der Gruppe nach der Erstellung ändern muss?

Verwenden Sie die Methoden `setLeft` und `setTop` der Gruppe, genau wie bei jedem anderen Shape:

```java
groupShape.setLeft(150);
groupShape.setTop(200);
```

Da sich die Gruppe wie ein einzelnes Shape verhält, bewegen sich alle Kind‑Shapes gemeinsam.

### 3. Wie wende ich einen Rahmen oder eine Füllung auf die gesamte Gruppe an?

Die Gruppe selbst kann formatiert werden, beeinflusst jedoch die Kinder nicht direkt. Wenn Sie einen gemeinsamen Rahmen wollen, packen Sie die Shapes zuerst in ein Rechteck‑Shape und gruppieren dann alles. Alternativ iterieren Sie über jedes Kind‑Shape und setzen dieselbe `fillColor` bzw. `strokeWeight`.

### 4. Wirkt `setHidden(true)` auf den Druck?

Versteckte Shapes werden standardmäßig **nicht** von Word gedruckt, was für Wasserzeichen oder Vorlagen‑Marker nützlich sein kann. Wenn das Shape gedruckt, aber auf dem Bildschirm unsichtbar sein soll, müssen Sie einen anderen Ansatz wählen (z. B. die Deckkraft auf 0 % setzen).

---

## Profi‑Tipps aus der Praxis

* **Benennen Sie Ihre Shapes** – `groupShape.setName("HeaderGraphics");` erleichtert das Debuggen, wenn Sie später Shapes per Name abrufen.  
* **Builder wiederverwenden** – Nach dem Einfügen einer Gruppe bleibt der Cursor des Builders an der Stelle der Gruppe, sodass Sie direkt danach weitere Absätze hinzufügen können, ohne die Position zurückzusetzen.  
* **Versions‑Guard** – Wenn Sie eine Bibliothek ausliefern, die auf älteren Aspose.Words‑Versionen laufen könnte, wickeln Sie den `setHidden`‑Aufruf in ein `try‑catch` für `NoSuchMethodError` und greifen Sie auf den oben gezeigten `WrapType.NONE`‑Trick zurück.  
* **Performance‑Hinweis** – Beim Generieren von Tausenden  

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Features zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Rendering Shapes in Aspose.Words for Java](/words/english/java/rendering-documents/rendering-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}