---
category: general
date: 2026-08-07
description: Erstellen Sie ein leeres Word‑Dokument mit gruppierten Formen in Java
  mithilfe von Aspose.Words. Erfahren Sie, wie Sie Formen gruppieren, die Größe von
  Formen festlegen und Formen zu Word hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to group shape
- group shapes word
- set shape size
- add shapes to word
language: de
lastmod: 2026-08-07
og_description: Erstellen Sie ein leeres Word‑Dokument mit gruppierten Formen in Java.
  Folgen Sie dieser Anleitung, um die Formgröße festzulegen, Formen zu Word hinzuzufügen
  und zu lernen, wie man Formen gruppiert.
og_image_alt: Create blank Word document with grouped shapes using Aspose.Words for
  Java
og_title: Erstelle ein leeres Word-Dokument mit gruppierten Formen – Java‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Create blank Word document with grouped shapes in Java using Aspose.Words.
    Learn how to group shape, set shape size, and add shapes to Word.
  headline: Create blank Word document with grouped shapes in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word Automation
- Shapes
title: Erstelle ein leeres Word‑Dokument mit gruppierten Formen in Java
url: /de/java/images-shapes/create-blank-word-document-with-grouped-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Leeres Word-Dokument mit gruppierten Formen in Java erstellen

Wenn Sie ein **blank Word document** erstellen müssen, das mehrere Formen enthält, die als eine Einheit angeordnet sind, zeigt Ihnen dieses Tutorial genau, wie es geht. Sie sehen ein vollständiges, ausführbares Beispiel, das **how to group shape** Objekte demonstriert, deren Abmessungen anpasst und **add shapes to Word** mit Aspose.Words für Java verwendet.

Der Leitfaden führt Sie durch jeden Schritt – von der Projektkonfiguration bis zum Speichern der finalen .docx‑Datei – sodass Sie den Code direkt in Ihre eigene Anwendung kopieren können. Es werden keine externen Referenzen benötigt, und die Lösung funktioniert mit Aspose.Words 23.9 oder höher.

## Voraussetzungen

* Java 17 (oder ein unterstütztes JDK)
* Maven oder Gradle für die Abhängigkeitsverwaltung
* Eine Aspose.Words für Java Lizenz (oder ein temporärer Evaluierungsschlüssel)
* Eine Beispiel‑Bilddatei (z. B. `sample.jpg`) in einem bekannten Verzeichnis abgelegt

Falls eines dieser Elemente fehlt, installieren Sie es zuerst; der Rest des Tutorials geht davon aus, dass die Umgebung bereit ist.

## Schritt 1: Aspose.Words zu Ihrem Projekt hinzufügen

Fügen Sie die Aspose.Words‑Abhängigkeit zu Ihrer `pom.xml` (Maven) oder `build.gradle` (Gradle) hinzu. Diese Bibliothek stellt die Klassen `Document`, `DocumentBuilder`, `GroupShape` und `Shape` bereit, die später verwendet werden.

```xml
<!-- Maven -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

```gradle
// Gradle
implementation 'com.aspose:aspose-words:23.9'
```

**Warum das wichtig ist:** Ohne die Bibliothek stehen keine Word‑Processing‑APIs zur Verfügung, und Sie können kein **blank Word document** programmgesteuert erstellen.

## Schritt 2: Ein leeres Word-Dokument erstellen

Die erste konkrete Aktion besteht darin, ein `Document`‑Objekt zu instanziieren, das ein **blank Word document** im Speicher repräsentiert.

```java
import com.aspose.words.*;

public class GroupShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new, empty document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*`Document()`* erstellt ein **blank Word document** mit Standardeinstellungen (A4‑Seite, Standardränder). Der zugehörige `DocumentBuilder` ermöglicht das Einfügen von Inhalt an der aktuellen Cursor‑Position.

## Schritt 3: Eine Gruppierungsform einfügen (how to group shape)

Eine *group shape* fungiert als Container für andere Formen. In diesem Schritt lernen Sie, **how to group shape** Objekte zu gruppieren, sodass sie gemeinsam bewegt werden.

```java
        // Insert a group shape with a width of 300 points and height of 200 points
        GroupShape group = builder.insertGroupShape(300.0, 200.0);
```

Die Methode `insertGroupShape` platziert den Container an der Cursor‑Position des Builders. Gruppierung ist essenziell, wenn Sie mehrere Zeichnungen als eine Einheit behandeln möchten – das ist das Kernstück der **group shapes word**‑Funktionalität.

## Schritt 4: Ein Rechteck erstellen und seine Größe festlegen

Fügen Sie nun ein Rechteck zur Gruppe hinzu. Dies demonstriert **set shape size**, was für ein präzises Layout erforderlich ist.

```java
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        rectangle.setWidth(100.0);   // set shape width
        rectangle.setHeight(50.0);   // set shape height
        rectangle.setLeft(20.0);     // horizontal offset inside the group
        rectangle.setTop(20.0);      // vertical offset inside the group

        // Append rectangle to the group
        group.appendChild(rectangle);
```

*Warum Abmessungen festlegen?* Durch das explizite Aufrufen von `setWidth` und `setHeight` wird sichergestellt, dass das Rechteck exakt wie beabsichtigt erscheint, unabhängig von den Standard‑Form‑Stilen des Dokuments.

## Schritt 5: Ein Bild einfügen und zur Gruppe hinzufügen

Das Hinzufügen eines Bildes zeigt einen weiteren häufigen Anwendungsfall für **add shapes to word**. Das Bild wird Teil derselben Gruppe und bewegt sich zusammen mit dem Rechteck.

```java
        // Insert an image at the current cursor position
        Shape picture = builder.insertImage("YOUR_DIRECTORY/sample.jpg");
        picture.setLeft(150.0);   // position inside the group
        picture.setTop(30.0);     // position inside the group

        // Append picture to the group
        group.appendChild(picture);
```

Falls die Bilddatei fehlt, wirft Aspose.Words eine Ausnahme. Ein praktischer Hinweis ist, den Pfad vorher zu überprüfen:

```java
        File imgFile = new File("YOUR_DIRECTORY/sample.jpg");
        if (!imgFile.exists()) {
            throw new IllegalArgumentException("Image file not found: " + imgFile.getAbsolutePath());
        }
```

## Schritt 6: Das Dokument mit den gruppierten Formen speichern

Abschließend speichern Sie das **blank Word document** (jetzt mit einer gruppierten Form gefüllt) auf dem Datenträger.

```java
        // Save the document as a .docx file
        doc.save("YOUR_DIRECTORY/GroupShapeDemo.docx");
    }
}
```

Wenn Sie `GroupShapeDemo.docx` in Microsoft Word öffnen, sehen Sie ein einzelnes gruppiertes Objekt, das ein Rechteck und ein Bild enthält. Das Auswählen eines beliebigen Teils der Gruppe bewegt den gesamten Container, was bestätigt, dass die Formen korrekt **grouped** wurden.

### Erwartete Ausgabe

* Eine Datei namens `GroupShapeDemo.docx` im angegebenen Verzeichnis.
* Beim Öffnen der Datei wird ein 300 × 200‑Punkt‑Container angezeigt mit:
  * Ein 100 × 50‑Punkt‑Rechteck bei (20, 20).
  * Ein Bild bei (150, 30) innerhalb desselben Containers.

## Randfälle und Variationen

| Situation | Wie man damit umgeht |
|-----------|----------------------|
| **Andere Seitengröße** | Rufen Sie `doc.getFirstSection().getPageSetup().setPaperSize(PaperSize.A5);` auf, bevor Sie die Gruppe einfügen. |
| **Mehrere Gruppen** | Wiederholen Sie die Schritte 3‑5 mit einer neuen `GroupShape`‑Instanz; jede Gruppe kann unabhängig positioniert werden. |
| **Drehen von Formen** | Verwenden Sie `shape.setRotationAngle(45.0);`, um ein Rechteck oder Bild zu drehen, bevor Sie es zur Gruppe hinzufügen. |
| **Nicht‑Bild‑Formen** | Erstellen Sie `Shape`‑Objekte vom Typ `ShapeType.ELLIPSE`, `ShapeType.LINE` usw. und fügen Sie sie genauso wie das Rechteck hinzu. |
| **Große Bilder** | Skalieren Sie das Bild mit `picture.setWidth(80.0); picture.setHeight(60.0);`, um die Gruppe innerhalb ihrer ursprünglichen Grenzen zu halten. |

## Praktische Tipps aus der Erfahrung

* **Pro‑Tipp:** Setzen Sie die `RelativeHorizontalPosition` und `RelativeVerticalPosition` der Gruppe auf `RelativeHorizontalPosition.PAGE` bzw. `RelativeVerticalPosition.PAGE`, wenn die Gruppe an der Seite und nicht am Cursor verankert bleiben soll.
* **Achten Sie auf:** Das Hinzufügen einer Form, die die Abmessungen der Gruppe überschreitet; die Form wird in Word abgeschnitten. Passen Sie die Gruppengröße mit `group.setWidth()` und `group.setHeight()` entsprechend an.
* **Leistungshinweis:** Wenn Sie viele Dokumente in einer Schleife erzeugen, verwenden Sie eine einzelne `DocumentBuilder`‑Instanz erneut und rufen Sie `doc.clone()` auf, um den Overhead bei der Objekterstellung zu reduzieren.

## Fazit

Sie wissen jetzt, wie man ein **blank Word document** erstellt, das eine gruppierte Sammlung von Formen mit Aspose.Words für Java enthält. Das Tutorial behandelte den gesamten Arbeitsablauf: Einrichtung der Bibliothek, Erstellen des Dokuments, Einfügen einer Gruppe, **set shape size**, **add shapes to word** und das Speichern des Ergebnisses.

Ab hier können Sie weiterführende Funktionen erkunden, wie das Gruppieren von Diagrammen, das Anwenden von Stilen auf einzelne Formen oder das Exportieren des Dokuments nach PDF. Jeder dieser Themen baut auf den im Leitfaden gezeigten Prinzipien auf.

---

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}