---
category: general
date: 2026-08-23
description: Erstellen Sie ein leeres Word‑Dokument mit Aspose.Words für Java, lernen
  Sie, wie Sie Formen gruppieren, ein Rechteck einfärben und das Dokument in wenigen
  Minuten als DOCX speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- save document as docx
- how to group shapes
- color rectangle shape
language: de
lastmod: 2026-08-23
og_description: Erstellen Sie ein leeres Word‑Dokument mit Aspose.Words für Java,
  sehen Sie dann, wie Sie Formen gruppieren, ein Rechteck einfärben und das Dokument
  effizient als DOCX speichern.
og_image_alt: Screenshot of a blank Word document containing grouped colored rectangle
  shapes
og_title: Leeres Word‑Dokument erstellen und Formen in Java gruppieren – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create blank Word document with Aspose.Words for Java, learn how to
    group shapes, color rectangle shape, and save document as docx in minutes.
  headline: Create blank Word document and group shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Leeres Word‑Dokument erstellen und Formen in Java gruppieren
url: /de/java/images-shapes/create-blank-word-document-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines leeren Word-Dokuments und Gruppieren von Formen in Java

Wenn Sie ein **create blank Word document** programmgesteuert benötigen, macht Aspose.Words for Java das unkompliziert. Dieses Tutorial zeigt Ihnen genau, wie Sie ein **create blank Word document** erstellen, ein **group shapes in Word** einfügen, **color rectangle shape** anwenden und schließlich **save document as docx**. Am Ende haben Sie ein wiederverwendbares Code‑Snippet, das Sie in jedes Java‑Projekt einbinden können.

Sie werden lernen:

* Die erforderliche Maven/Gradle‑Abhängigkeit für Aspose.Words.
* Wie man ein leeres Dokument und einen `DocumentBuilder` instanziiert.
* Die genauen Schritte, um **how to group shapes** innerhalb eines `GroupShape` auszuführen.
* Wie man Füllfarben für Rechteckformen festlegt.
* Die bewährte Vorgehensweise für **save document as docx** und wo die Ausgabedatei zu finden ist.

Vorkenntnisse mit Aspose.Words werden nicht vorausgesetzt, aber Sie sollten mit grundlegender Java‑Entwicklung vertraut sein und ein JDK 8 oder neuer installiert haben.

---

## Voraussetzungen

| Anforderung | Version / Details |
|-------------|-------------------|
| Java Development Kit | 8 or higher |
| Build tool | Maven 3+ or Gradle 6+ |
| Aspose.Words for Java | 23.12 or later (the latest version at the time of writing) |
| IDE (optional) | IntelliJ IDEA, Eclipse, VS Code, or any Java‑compatible editor |

---

## Schritt 1: Aspose.Words zu Ihrem Projekt hinzufügen

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

### Gradle

```gradle
implementation 'com.aspose:aspose-words:23.12'
```

> **Pro Tipp:** Wenn Sie einen Unternehmens‑Proxy verwenden, konfigurieren Sie Maven/Gradle so, dass das Paket aus dem Aspose‑Repository gezogen wird, wie in der offiziellen Dokumentation beschrieben.

---

## Schritt 2: **Create blank Word document** mit einem Builder

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 2.1: Create a new blank document
        Document doc = new Document();               // <-- create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Der `Document`‑Konstruktor erzeugt einen leeren `.docx`‑Container im Speicher. Der `DocumentBuilder` bietet Ihnen eine fluente API zum Hinzufügen von Inhalten, einschließlich Formen.

---

## Schritt 3: Einen **group shapes in Word**‑Container einfügen

```java
        // Step 3.1: Insert a GroupShape that will hold individual shapes
        // Width = 300 points, Height = 200 points
        GroupShape groupShape = builder.insertGroupShape(300, 200);
```

Ein `GroupShape` funktioniert wie ein Mini‑Canvas. Alle zu ihm hinzugefügten Formen bewegen sich gemeinsam, was genau **how to group shapes** für Layout‑Konsistenz bedeutet.

---

## Schritt 4: Die erste **color rectangle shape** (rot) hinzufügen

```java
        // Step 4.1: Create the first rectangle and set its fill color to red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        // Append the rectangle to the group
        groupShape.appendChild(redRectangle);
```

Die Konstante `ShapeType.RECTANGLE` erzeugt ein einfaches Rechteck. Durch Aufruf von `getFill().setForeColor(...)` steuern Sie die **color rectangle shape**. Sie können `java.awt.Color.RED` durch jede `java.awt.Color`‑Konstante oder einen benutzerdefinierten RGB‑Wert ersetzen.

---

## Schritt 5: Die zweite **color rectangle shape** (grün) hinzufügen und positionieren

```java
        // Step 5.1: Create a second rectangle, color it green, and offset it inside the group
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // Horizontal offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);
```

Durch Setzen von `setLeft` (oder `setTop`) wird die Form relativ zur oberen linken Ecke des **group shapes in Word**‑Containers verschoben. Dies demonstriert **how to group shapes** mit präziser Positionierung.

---

## Schritt 6: **Save document as docx** und das Ergebnis überprüfen

```java
        // Step 6.1: Persist the document to the file system
        String outputPath = "output/GroupShapeDemo.docx";
        doc.save(outputPath);          // <-- save document as docx
        System.out.println("Document saved to: " + outputPath);
    }
}
```

Die `save`‑Methode schreibt automatisch eine `.docx`‑Datei, da die Dateierweiterung `.docx` ist. Wenn Sie ein anderes Format benötigen (z. B. PDF), übergeben Sie das entsprechende `SaveFormat`‑Enum.

> **Tipp:** Stellen Sie sicher, dass das Zielverzeichnis (`output/` in diesem Beispiel) existiert oder erstellen Sie es programmgesteuert mit `new File("output").mkdirs();`.

---

## Vollständiger Quellcode für schnelles Kopieren‑Einfügen

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a new blank document
        Document doc = new Document();               // create blank Word document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape (the container for grouped shapes)
        GroupShape groupShape = builder.insertGroupShape(300, 200);

        // 3️⃣ First rectangle – red
        Shape redRectangle = new Shape(doc, ShapeType.RECTANGLE);
        redRectangle.setWidth(120);
        redRectangle.setHeight(80);
        redRectangle.getFill().setForeColor(java.awt.Color.RED);
        groupShape.appendChild(redRectangle);

        // 4️⃣ Second rectangle – green, positioned next to the red one
        Shape greenRectangle = new Shape(doc, ShapeType.RECTANGLE);
        greenRectangle.setWidth(120);
        greenRectangle.setHeight(80);
        greenRectangle.setLeft(130); // offset inside the group
        greenRectangle.getFill().setForeColor(java.awt.Color.GREEN);
        groupShape.appendChild(greenRectangle);

        // 5️⃣ Save the file as DOCX
        String outPath = "output/GroupShapeDemo.docx";
        doc.save(outPath);          // save document as docx
        System.out.println("Document saved to: " + outPath);
    }
}
```

**Erwartete Ausgabe:** Beim Öffnen von `GroupShapeDemo.docx` in Microsoft Word wird eine einzelne Seite angezeigt, die zwei farbige Rechtecke enthält (rot links, grün rechts), die sich gemeinsam bewegen, wenn Sie die Gruppe auswählen.

---

## Häufige Fragen und Sonderfall‑Behandlung

| Frage | Antwort |
|----------|--------|
| *Kann ich mehr als zwei Formen zur selben Gruppe hinzufügen?* | Ja. Rufen Sie `groupShape.appendChild(yourShape)` für jede zusätzliche Form auf. Die Gruppe passt ihre Größe automatisch an die äußersten Ausmaße an, oder Sie können Breite/Höhe manuell anpassen. |
| *Was, wenn ich einen anderen Formtyp benötige (z. B. Ellipse)?* | Ersetzen Sie `ShapeType.RECTANGLE` durch `ShapeType.ELLIPSE`. Die gleiche Füllfarben‑Logik gilt. |
| *Muss ich das `Document`‑Objekt freigeben?* | Aspose.Words verwaltet native Ressourcen intern. Beim Beenden der JVM werden Ressourcen freigegeben. Für langlaufende Anwendungen rufen Sie `doc.dispose();` auf, wenn Sie die **Aspose.Words for Java (Native)**‑Version verwenden. |
| *Wie ändere ich die Z‑Reihenfolge, sodass ein Rechteck oben erscheint?* | Verwenden Sie `groupShape.insertAfter(shape, referenceShape);` oder `groupShape.insertBefore(shape, referenceShape);`, um Kinder innerhalb der Gruppe neu zu ordnen. |
| *Kann ich Formen über verschiedene Abschnitte hinweg gruppieren?* | Nein. Ein `GroupShape` muss innerhalb eines einzelnen Absatzes oder Form‑Containers liegen. Um über Abschnitte hinweg zu gruppieren, erstellen Sie separate Gruppen in jedem Abschnitt. |

---

## Fazit

Sie wissen jetzt, wie man mit Aspose.Words for Java **create blank Word document**, **group shapes in Word**, **color rectangle shape**‑Stile anwendet und **save document as docx**. Dieses Muster lässt sich auf komplexere Layouts skalieren – fügen Sie einfach weitere Formen hinzu, passen Sie Versätze an und setzen Sie optional Text, Bilder oder Hyperlinks innerhalb der Gruppe.

**Nächste Schritte**, die Sie erkunden könnten:

- Verwenden Sie **group shapes in Word**, um Flussdiagramme oder UI‑Mock‑ups zu erstellen.
- Experimentieren Sie mit **save document as docx** kombiniert mit PDF‑Konvertierung (`doc.save("out.pdf")`).
- Wenden Sie Verläufe oder Muster auf die **color rectangle shape** an, um ein reichhaltigeres Design zu erzielen.
- Kombinieren Sie gruppierte Formen mit Tabellen oder Diagrammen für fortgeschrittene Berichtsdokumente.

Passen Sie die Abmessungen, Farben oder Formtypen gerne an das Branding Ihres Projekts an. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu beherrschen und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [How to save document as pdf with Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Using Document Shapes in Aspose.Words for Java](/words/english/java/document-conversion-and-export/using-document-shapes/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}