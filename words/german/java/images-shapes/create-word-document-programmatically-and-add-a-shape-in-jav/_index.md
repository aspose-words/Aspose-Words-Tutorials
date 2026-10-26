---
category: general
date: 2026-10-26
description: Erfahren Sie, wie Sie ein Word‑Dokument programmgesteuert erstellen,
  eine Form hinzufügen und ein Objekt in Word mit Aspose.Words für Java ausblenden
  – Schritt‑für‑Schritt‑Anleitung.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- how to hide shape
- how to add shape
- hide object in word
language: de
lastmod: 2026-10-26
og_description: Erstellen Sie ein Word‑Dokument programmgesteuert, lernen Sie, wie
  Sie mit Aspose.Words für Java Formen hinzufügen und Objekte in Word ausblenden.
  Vollständiges, ausführbares Beispiel.
og_image_alt: Screenshot of a Word document created programmatically with a hidden
  ellipse shape
og_title: Word-Dokument programmgesteuert erstellen – Formen in Java hinzufügen und
  ausblenden
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn how to create Word document programmatically, add a shape, and
    hide object in Word using Aspose.Words for Java – step‑by‑step guide.
  headline: Create Word document programmatically and add a shape in Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Word-Dokument programmgesteuert erstellen und eine Form in Java hinzufügen
url: /de/java/images-shapes/create-word-document-programmatically-and-add-a-shape-in-jav/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Word-Dokument programmgesteuert erstellen und eine Form in Java hinzufügen

Wenn Sie **Word-Dokument programmgesteuert erstellen** müssen, zeigt Ihnen dieses Tutorial genau, wie Sie das tun, eine Form hinzufügen und dann das Objekt in Word ausblenden. Egal, ob Sie einen Berichtsgenerator oder ein automatisiertes Vertragssystem erstellen, Sie erhalten in nur wenigen Minuten eine komplette, sofort lauffähige Lösung.

Sie lernen, wie man:

* Ein Word-Dokument mit Aspose.Words für Java initialisiert.  
* Eine Ellipse (oder jede andere Form) mit der **how to add shape**‑Technik einfügt.  
* Diese Form ausblendet, sodass sie nie erscheint, wenn die Datei geöffnet wird, und damit die **how to hide shape**‑Frage beantwortet.  

Keine externen Werkzeuge sind über die Aspose.Words-Bibliothek hinaus erforderlich, und der Code funktioniert mit Java 17 und später.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Java Development Kit (JDK) 17 oder neuer installiert.  
* Maven oder Gradle zur Verwaltung der Abhängigkeiten (das Beispiel verwendet Maven).  
* Eine gültige Aspose.Words für Java Lizenz (die kostenlose Evaluierung funktioniert zum Testen).  

Wenn Sie neu bei Aspose.Words sind, lesen Sie den offiziellen Getting Started‑Leitfaden, aber Sie müssen ihn nicht lesen, um diesem Tutorial zu folgen.

## Maven-Abhängigkeit

Fügen Sie die folgende Abhängigkeit zu Ihrer `pom.xml` hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

> **Pro tip:** Halten Sie die Versionsnummer aktuell; neuere Releases enthalten Fehlerbehebungen für die Formverarbeitung.

## Schritt 1: Word-Dokument programmgesteuert erstellen – Initialisierung des Dokuments

Das Erste, was Sie tun, wenn Sie **Word-Dokument programmgesteuert erstellen**, ist, ein `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert die gesamte .docx‑Datei im Speicher.

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Initialize a new empty document
        Document doc = new Document();

        // Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Warum dieser Schritt wichtig ist*: Die `Document`‑Klasse ist der Einstiegspunkt für alle Word‑Verarbeitungs‑Operationen. Ohne sie können Sie keine Seiten, Absätze oder Formen hinzufügen.

## Schritt 2: How to add shape – Einfügen einer Ellipse

Jetzt gehen wir auf den **how to add shape**‑Teil des Tutorials ein. Aspose.Words unterstützt viele Formtypen (Ellipse, Rechteck, TextBox usw.). Im Folgenden fügen wir eine Ellipse mit einer Breite und Höhe von 50 Punkten ein.

```java
        // Insert an ellipse shape of size 50x50 points
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);

        // Position the shape (optional)
        ellipse.setLeft(100);
        ellipse.setTop(100);
```

Die Methode `insertShape` gibt ein `Shape`‑Objekt zurück, das Sie weiter anpassen können – Farbe, Linienstil, Drehung und mehr. Die Koordinaten werden in Punkten (1/72 Zoll) gemessen.

*Warum Sie eine Form hinzufügen möchten*: Formen sind nützlich für Wasserzeichen, dekorative Elemente oder Platzhalter, die Sie später ausblenden oder ersetzen.

## Schritt 3: How to hide shape – Das Objekt in Word unsichtbar machen

Um die **how to hide shape**‑Frage zu beantworten, setzen Sie einfach die `Hidden`‑Eigenschaft der Form auf `true`. Dadurch behandelt Word die Form als verstecktes Objekt, sodass sie weder in der Dokumentansicht noch im Ausdruck angezeigt wird.

```java
        // Hide the shape so it does not appear in the rendered document
        ellipse.setHidden(true);
```

Wenn Sie **hide object in Word** für einen bestimmten Benutzer oder eine Bedingung benötigen, können Sie diese Eigenschaft zur Laufzeit basierend auf Ihrer Geschäftslogik umschalten.

> **Hinweis:** Versteckte Formen sind weiterhin Teil der XML‑Struktur des Dokuments. Sie können später wieder sichtbar gemacht werden, indem Sie `setHidden(false)` setzen.

## Schritt 4: Dokument speichern

Nachdem Sie die Form hinzugefügt und ausgeblendet haben, schreiben Sie das Dokument auf die Festplatte.

```java
        // Save the document as a .docx file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

Wenn Sie `HiddenShapeDemo.docx` in Microsoft Word öffnen, sehen Sie eine leere Seite, weil die Ellipse ausgeblendet ist. Das Dokument verhält sich ansonsten wie jede normale Word‑Datei.

## Vollständiges funktionierendes Beispiel

Wenn wir alle Teile zusammenfügen, erhalten Sie das vollständige, ausführbare Programm:

```java
import com.aspose.words.*;

public class WordShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a document programmatically
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: How to add shape – insert an ellipse (50x50 points)
        Shape ellipse = builder.insertShape(ShapeType.ELLIPSE, 50.0, 50.0);
        ellipse.setLeft(100);
        ellipse.setTop(100);

        // Step 3: How to hide shape – hide the ellipse so it never appears
        ellipse.setHidden(true);

        // Step 4: Save the file
        doc.save("HiddenShapeDemo.docx");
        System.out.println("Document created successfully.");
    }
}
```

**Erwartete Ausgabe**

```
Document created successfully.
```

Beim Öffnen von `HiddenShapeDemo.docx` wird eine leere Seite angezeigt; die ausgeblendete Ellipse wird nicht gerendert, was bestätigt, dass die **hide object in Word**‑Operation erfolgreich war.

## Randfälle und Variationen

| Situation | Was zu ändern ist | Warum |
|-----------|-------------------|-------|
| Ein Rechteck anstelle einer Ellipse ausblenden | Verwenden Sie `ShapeType.RECTANGLE` in `insertShape` | Anderer visueller Platzhalter |
| Mehrere Formen gleichzeitig ausblenden | Durchlaufen Sie `doc.getChildNodes(NodeType.SHAPE, true)` und setzen Sie `setHidden(true)` | Nützlich für die Massenverarbeitung |
| Die Form nur in der Druckansicht anzeigen | Setzen Sie `shape.setVisible(false)` und `shape.setPrint(true)` | Word unterscheidet zwischen Bildschirm‑ und Drucksichtbarkeit |
| Eine andere Maßeinheit verwenden | Rufen Sie `builder.getDocument().getCompatibilityOptions().setMeasureUnit(MeasureUnit.INCHES)` auf | Passt zu Ihren Layout‑Anforderungen |

## Häufige Fallstricke

* **Vergessen, `setHidden(true)` aufzurufen** – die Form wird normal angezeigt.  
* **Speichern des Dokuments vor dem Ausblenden der Form** – die Reihenfolge ist wichtig; zuerst ausblenden, dann speichern.  
* **Verwendung einer veralteten Aspose.Words‑Version** – ältere Releases könnten die `setHidden`‑API nicht enthalten.  

Testen Sie die erzeugte Datei stets in der Zielversion von Microsoft Word, um sicherzustellen, dass der ausgeblendete Zustand wie erwartet funktioniert.

## Fazit

In diesem Leitfaden haben Sie gelernt, wie man **Word-Dokument programmgesteuert erstellt**, **Formen hinzufügt** und **Objekte in Word ausblendet** mit Aspose.Words für Java. Das vollständige Beispiel demonstriert die genauen Schritte, von der Initialisierung des Dokuments bis zum Speichern einer Datei, in der die Form nie erscheint.  

Von hier aus können Sie:

* Mit anderen Formtypen experimentieren (`ShapeType.LINE`, `ShapeType.TEXT_BOX`).  
* Versteckte Formen mit Lesezeichen kombinieren, um dynamische Vorlagen zu erstellen.  
* Die Eigenschaften `setVisible` und `setPrint` erkunden, um eine feinere Kontrolle über die Sichtbarkeit von Objekten zu erhalten.

Viel Spaß beim Programmieren und beim Automatisieren Ihrer Word‑Dokumente!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält komplette funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Wie man ein leeres Word‑Dokument mit Aspose.Words für Java erstellt](/words/english/java/document-manipulation/how-to-create-blank-word-document-with-aspose-words-for-java/)
- [Wie man eine Form in einem Word‑Dokument mit Java ausblendet](/words/english/java/images-shapes/how-to-hide-shape-in-a-word-document-using-java/)
- [Word‑Dokument mit Java erstellen – Rechteckform mit Schatteneffekt hinzufügen](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}