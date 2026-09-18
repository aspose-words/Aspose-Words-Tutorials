---
category: general
date: 2026-09-18
description: Erstellen Sie ein leeres Dokument und fügen Sie Formen in Word mit Aspose.Words
  ein – erfahren Sie, wie Sie eine Dreiecksform und mehr hinzufügen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: de
lastmod: 2026-09-18
og_description: Erstellen Sie ein leeres Dokument in Word mit Aspose.Words und lernen
  Sie, wie Sie eine Dreiecksform, Gruppierungen von Formen und weitere Grafiken einfügen.
  Folgen Sie diesem umfassenden Leitfaden.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Leeres Dokument erstellen und Formen zu Word hinzufügen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Wie man ein leeres Dokument erstellt und Formen zu Word hinzufügt
url: /de/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein leeres Dokument erstellt und Formen zu Word hinzufügt

Wenn Sie ein **leeres Dokument erstellen** und es anschließend mit Grafiken anreichern möchten, zeigt Ihnen dieser Leitfaden genau, wie das geht. Wir führen Sie durch das Erstellen einer Word‑Datei von Grund auf und **fügen Formen zu Word hinzu**, einschließlich **wie man eine Dreiecksform einfügt**, mit Aspose.Words für Java.

Am Ende des Tutorials haben Sie eine einsatzbereite *.docx*-Datei, die eine gruppierte Form mit einem Dreieck enthält. Die Schritte decken alles ab, von der Projektkonfiguration bis zum Speichern des finalen **create word document**. Keine externen Werkzeuge sind über Aspose.Words hinaus erforderlich.

## Voraussetzungen

* Java 17 oder höher installiert  
* Maven oder Gradle für die Abhängigkeitsverwaltung  
* Eine Aspose.Words für Java Lizenz (die kostenlose Evaluierung funktioniert für diese Demo)

Wenn Sie ein anderes Build‑System bevorzugen, passen Sie die Abhängigkeits‑Syntax entsprechend an. Der Code funktioniert auf jeder Plattform, die Java unterstützt.

## Leeres Dokument mit Aspose.Words erstellen

Der erste Vorgang besteht darin, **ein leeres Dokument** im Speicher zu **erstellen**. Aspose.Words stellt die Klasse `Document` bereit, die eine Word‑Datei ohne Inhalt repräsentiert.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

Der Konstruktor `new Document()` erstellt eine leere *.docx*-Struktur, die Sie später mit Absätzen, Tabellen oder Grafiken füllen können. Da das Dokument leer ist, haben Sie die volle Kontrolle über jedes hinzugefügte Element.

## Formen zu Word hinzufügen – Einfügen einer Gruppierten Form

Eine gruppierte Form ermöglicht es, mehrere Grafiken als eine Einheit zu behandeln. Das ist nützlich, wenn Sie mehrere Formen gemeinsam verschieben oder skalieren möchten.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` ist die primäre API zum Hinzufügen von Inhalten. Der Aufruf `insertGroupShape` erstellt einen Container von 300 × 300 Punkten (ungefähr 4 × 4 Zoll). Nach diesem Aufruf befindet sich der Cursor *innerhalb* der Gruppe und ist bereit für weitere Formen.

### Warum eine gruppierte Form verwenden?

Durch Gruppierung bleiben zusammengehörige Grafiken ausgerichtet und es wird einfacher, einheitliche Formatierungen anzuwenden. Wenn Sie später das Dreieck verschieben möchten, bewegt sich die gesamte Gruppe zusammen und bewahrt das Layout.

## Wie man eine Dreiecksform innerhalb der Gruppe einfügt

Jetzt gehen wir auf **wie man ein Dreieck einfügt** ein. Das Dreieck ist einer der integrierten `ShapeType`‑Werte.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

Der Aufruf `moveTo` stellt sicher, dass der Einfügepunkt des Builders der erste Absatz der Gruppe ist. `insertShape` fügt dann ein Dreieck von 60 × 60 Punkten hinzu. Da sich der Cursor innerhalb der Gruppe befindet, wird das Dreieck zum Kind der gruppierten Form.

**Tipps zum Hinzufügen einer Dreiecksform**:

* Die Größe wird in Punkten gemessen; 72 Punkte entsprechen einem Zoll. Passen Sie die Abmessungen an Ihr Layout an.  
* Wenn Sie eine andere Ausrichtung benötigen, verwenden Sie `builder.getCurrentParagraph().getParagraphFormat().setAlignment()`, um die Form innerhalb der Gruppe auszurichten.  
* Das Dreieck erbt die Füll- und Linienstile der Gruppe, sofern Sie sie nicht mit `shape.getFillColor()` oder `shape.getStrokeColor()` überschreiben.

## Dokument speichern – create word document

Nachdem Sie die Grafiken erstellt haben, speichern Sie die Datei. Dieser Schritt schließt die **create word document**‑Operation ab.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` schreibt die im Speicher befindliche Darstellung als Standard‑Word‑Dokument auf die Festplatte. Sie können `ExtendedGroup.docx` in Microsoft Word, LibreOffice oder jedem Viewer öffnen, der das OOXML‑Format unterstützt. Die Datei zeigt eine gruppierte Form mit einem Dreieck, genau wie vom Code erzeugt.

## Vollständiges ausführbares Beispiel

Wenn wir alle Teile zusammenfügen, erhalten Sie das vollständige Programm, das Sie kopieren, kompilieren und ausführen können:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Erwartetes Ergebnis

Wenn Sie `ExtendedGroup.docx` öffnen, sehen Sie eine einzelne gruppierte Form, die die Mitte der Seite einnimmt. Innerhalb dieser Gruppe erscheint ein kleines Dreieck an der Standardposition. Das Dreieck kann ausgewählt und als Teil der Gruppe verschoben werden, was bestätigt, dass **add shapes to word** wie beabsichtigt funktioniert hat.

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| *Kann ich mehr als eine Form innerhalb der Gruppe hinzufügen?* | Ja. Nachdem Sie das Dreieck eingefügt haben, lassen Sie den Cursor innerhalb der Gruppe und rufen `builder.insertShape` erneut mit einem anderen `ShapeType` auf. |
| *Was, wenn das Dreieck rot sein soll?* | Rufen Sie die von `insertShape` zurückgegebene `Shape` ab und rufen `shape.getFillColor().setColor(Color.RED)` auf. |
| *Funktioniert das mit älteren .doc‑Dateien?* | Aspose.Words speichert im von Ihnen angegebenen Format. Verwenden Sie `doc.save("file.doc", SaveFormat.DOC)`, um ein altes Word‑Dokument zu erstellen. |
| *Wie ändere ich die Rahmenlinie der Gruppe?* | Verwenden Sie `group.getStrokeColor().setColor(Color.BLUE)` und `group.setLineWeight(2.0)`, um die Kontur anzupassen. |
| *Gibt es eine Möglichkeit, das Dreieck zu drehen?* | Rufen Sie `shape.getRotation()` auf, um einen Winkel in Grad festzulegen. |

## Profi‑Tipps

* **Den Builder wiederverwenden** – das Erstellen eines neuen `DocumentBuilder` für jede Form verursacht zusätzlichen Aufwand. Verwenden Sie einen einzigen Builder pro Dokument.  
* **Einheitenumrechnung** – wenn Sie mit Millimetern arbeiten, konvertieren Sie sie in Punkte (`points = mm * 2.83465`).  
* **Leistung** – bei großen Dokumenten rufen Sie `doc.updatePageLayout()` nur einmal nach dem Hinzufügen aller Formen auf.

## Fazit

Sie wissen jetzt, wie man **ein leeres Dokument erstellt**, **Formen zu Word hinzufügt** und speziell **wie man ein Dreieck einfügt** mit Aspose.Words für Java. Das vollständige Beispiel zeigt den gesamten Arbeitsablauf von einer leeren Datei bis zum gespeicherten **create word document**, das ein gruppiertes Dreieck enthält.

Ab hier können Sie weitere `ShapeType`‑Werte erkunden, benutzerdefinierte Stile anwenden oder mehrere Gruppen kombinieren, um komplexe Diagramme zu erstellen. Experimentieren Sie mit verschiedenen Größen, Farben und Positionen, um die Word‑Automatisierung in Java zu meistern.

--- 

*Bereit, Ihren nächsten Bericht zu automatisieren? Klonen Sie das Beispiel, passen Sie die Abmessungen an und integrieren Sie den Code noch heute in Ihre eigene Anwendung.*

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Gruppierte Form in Word‑Dokument mit Aspose.Words für .NET erstellen](/words/english/net/working-with-shapes/add-group-shape/)
- [Leeres Word‑Dokument mit schattierter Rechteckform erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Rechteckform in Word mit Aspose.Words erstellen – Schritt‑für‑Schritt‑Anleitung](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}