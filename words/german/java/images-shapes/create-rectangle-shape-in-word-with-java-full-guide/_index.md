---
category: general
date: 2026-02-15
description: Erstellen Sie ein Rechteck in einem Word‑Dokument mit Java. Erfahren
  Sie, wie Sie einem Shape einen Schatten hinzufügen, das Word‑Dokument speichern
  und ein Rechteck mit Aspose.Words hinzufügen.
draft: false
keywords:
- create rectangle shape
- save word document
- how to shadow shape
- add shape shadow
- add rectangle shape
language: de
og_description: Erstelle ein Rechteck in einer Word‑Datei mit Java. Diese Anleitung
  zeigt, wie man einen Formschatten hinzufügt, das Word‑Dokument speichert und Schritt
  für Schritt ein Rechteck einfügt.
og_title: Rechteckform erstellen – Java Aspose.Words‑Tutorial
tags:
- Aspose.Words
- Java
- Document Automation
title: Rechteckform in Word mit Java erstellen – Vollständiger Leitfaden
url: /de/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

final content.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Word mit Java erstellen – Vollständige Anleitung

Haben Sie schon einmal **eine Rechteckform** in einer Word‑Datei erstellen wollen, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein – viele Entwickler stoßen an diese Hürde, wenn sie Berichte oder Rechnungen automatisieren. Die gute Nachricht? Mit Aspose.Words für Java können Sie ein Rechteck erzeugen, ihm einen schönen Schatten geben und das Word‑Dokument in wenigen Zeilen speichern.

In diesem Tutorial führen wir Sie durch alles, was Sie benötigen: vom Initialisieren eines leeren Dokuments über das Konfigurieren eines Schattens bis hin zum endgültigen Speichern der Datei. Am Ende wissen Sie, **wie man Form‑Schatten** verwendet, wie man **einen Form‑Schatten hinzufügt** und wie man **eine Rechteckform** zu jedem von Ihnen erzeugten Word‑Dokument hinzufügt. Keine externen Dokumente nötig – nur reiner, ausführbarer Code.

## Voraussetzungen

- Java 8 oder neuer (die API funktioniert auch mit Java 11+).  
- Aspose.Words für Java Bibliothek (Version 23.9 oder später).  
- Eine IDE wie IntelliJ IDEA oder Eclipse – jede ist geeignet.  
- Grundlegende Kenntnisse der Java‑Syntax.

> **Pro‑Tipp:** Wenn Sie Maven verwenden, fügen Sie die Aspose.Words‑Abhängigkeit zu Ihrer `pom.xml` hinzu und lassen Sie die IDE den Rest erledigen.

---

## Schritt 1: Ein neues Dokument initialisieren – Wie man **eine Rechteckform erstellt**  

Zuerst brauchen Sie eine leere Zeichenfläche. In Aspose.Words ist diese Zeichenfläche ein `Document`‑Objekt.

```java
import com.aspose.words.*;

public class ShadowShapeExample {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();
```

Die Klasse `Document` repräsentiert die gesamte .docx‑Datei. Denken Sie daran wie an ein Notizbuch, in das Sie später **eine Rechteckform** und deren Schatten **hinzufügen**.

## Schritt 2: Das Rechteck bauen – **Rechteckform hinzufügen**  

Jetzt konstruieren wir das eigentliche Rechteck. Wir setzen Größe, Layout und Füllfarbe.

```java
        // Step 2: Create a rectangle shape and set its size and layout
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);
        rectangleShape.setFillColor(java.awt.Color.LIGHT_GRAY);
```

Warum `INLINE`‑Wrap? Weil wir möchten, dass sich die Form wie ein Absatz verhält – ideal für einfache Berichte. Sie können es zu `TOPBOTTOM` ändern, falls später Text um die Form fließen soll.

## Schritt 3: Einen Schatten anwenden – **Wie man Form‑Schatten verwendet**  

Ein flaches Rechteck wirkt etwas langweilig. Ein Schatten verleiht Tiefe und lässt das Dokument professioneller erscheinen. Hier beantworten wir praktisch die Frage „**wie man Form‑Schatten verwendet**“.

```java
        // Step 3: Configure the shape's shadow appearance
        rectangleShape.getShadowFormat().setVisible(true);
        rectangleShape.getShadowFormat().setColor(java.awt.Color.DARK_GRAY);
        rectangleShape.getShadowFormat().setBlurRadius(5.0);
        rectangleShape.getShadowFormat().setOffsetX(4.0);
        rectangleShape.getShadowFormat().setOffsetY(4.0);
        rectangleShape.getShadowFormat().setTransparency(0.3);
```

Jede Eigenschaft bewirkt Folgendes:

- `setVisible(true)` schaltet den Schatten ein.  
- `setColor` wählt ein dunkles Grau für einen dezenten Effekt.  
- `setBlurRadius` steuert, wie weich die Kanten erscheinen.  
- `setOffsetX/Y` verschiebt den Schatten nach rechts und unten und simuliert eine Lichtquelle.  
- `setTransparency` macht ihn leicht durchsichtig, sodass die Form im Vordergrund bleibt.

> **Hinweis:** Wenn Sie einen farbigen Schatten benötigen, übergeben Sie einfach ein anderes `java.awt.Color` an `setColor`.

## Schritt 4: Die Form in das Dokument einfügen  

Mit dem Rechteck und seinem Schatten fertig, fügen wir es in den ersten Abschnitt des Dokuments ein.

```java
        // Step 4: Add the shape to the first section of the document
        document.getFirstSection().getBody().appendChild(rectangleShape);
```

Das Anhängen an den Body platziert die Form dort, wo ein neuer Absatz stehen würde. Wenn Sie das Rechteck an einer bestimmten Stelle haben möchten, können Sie `insertBefore` verwenden oder die `Paragraph`‑Sammlung manipulieren.

## Schritt 5: **Word‑Dokument speichern** – Ihre Arbeit persistieren  

Der letzte Schritt besteht darin, die Datei auf die Festplatte zu schreiben. Jetzt **speichern Sie das Word‑Dokument** wirklich.

```java
        // Step 5: Save the document with the shadowed shape
        document.save("YOUR_DIRECTORY/ShadowShape.docx");
    }
}
```

Ersetzen Sie `YOUR_DIRECTORY` durch einen absoluten oder relativen Pfad auf Ihrem Rechner. Nach dem Ausführen des Programms öffnen Sie `ShadowShape.docx` in Microsoft Word – Sie sollten ein hellgraues Rechteck mit einem weichen dunklen Schatten sehen.

![Diagramm, das ein Rechteck mit Schatten zeigt, erstellt mit Aspose.Words](https://example.com/rectangle-shadow.png "Rechteck mit Schatten erstellen")

---

## Häufige Fragen & Sonderfälle  

### Was, wenn ich mehrere Rechtecke brauche?  

Wiederholen Sie einfach **Schritt 2** und **Schritt 3** in einer Schleife und passen Sie `setWidth`, `setHeight` oder `setFillColor` bei jedem Durchlauf an. Denken Sie daran, jeder Form einen eindeutigen Variablennamen zu geben oder sie in einer Liste zu speichern.

### Kann ich stattdessen nach PDF exportieren?  

Natürlich. Nachdem die Form hinzugefügt wurde, rufen Sie `document.save("output.pdf")` auf. Aspose.Words übernimmt die Konvertierung und behält den Schatten bei.

### Was ist mit älteren Word‑Versionen?  

Verwenden Sie die Überladung `document.save("file.doc", SaveFormat.DOC)`. Die API downgradet die Features automatisch, aber beachten Sie, dass einige Schattenstile in Legacy‑Formaten leicht anders aussehen können.

### Wie ändere ich die Schattenrichtung?  

Passen Sie `setOffsetX` und `setOffsetY` an. Positives X verschiebt den Schatten nach rechts, negatives nach links. Positives Y nach unten, negatives nach oben. Experimentieren Sie mit diesen Werten, um eine Lichtquelle aus jedem Winkel zu simulieren.

---

## Tipps für die Arbeit mit Formen  

- **Formen gruppieren**: Wenn Sie neben dem Rechteck ein Label benötigen, erstellen Sie ein `GroupShape` und fügen sowohl das Rechteck als auch ein `TextBox` hinzu.  
- **Z‑Reihenfolge beachten**: Verwenden Sie `shape.moveToFront()` oder `shape.moveToBack()`, um zu steuern, welche Form oben liegt.  
- **Performance**: Das Hinzufügen von Hunderten von Formen kann langsam sein. Bündeln Sie sie in einem einzigen Abschnitt und rufen Sie am Ende einmal `document.updatePageLayout()` auf.

---

## Zusammenfassung  

Wir haben behandelt, wie man **eine Rechteckform** in einem Word‑Dokument mit Java erstellt, wie man **einen Form‑Schatten hinzufügt** und wie man das **Word‑Dokument speichert**. Der vollständige, ausführbare Code befindet sich in den obigen Snippets, und Sie verstehen jetzt das „Warum“ hinter jeder Eigenschaft – sodass Sie Farben, Unschärfe und Offsets nach Belieben anpassen können.

Bereit für die nächste Herausforderung? Kombinieren Sie das Rechteck mit einem Diagramm oder exportieren Sie die Datei als PDF und prüfen Sie, wie der Schatten dargestellt wird. Sie können auch **Rechteckformen** in Tabellen einfügen, um ausgefallene Berichtslayouts zu erstellen.

Viel Spaß beim Coden und mögen Ihre Dokumente immer so scharf aussehen wie Ihr Code!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}