---
category: general
date: 2026-02-10
description: Erstellen Sie eine Rechteckform in einem Word‑Dokument mit Aspose.Words
  für Java. Erfahren Sie, wie Sie die Schattenfarbe festlegen, wie Sie einen Schatten
  hinzufügen und ein Word‑Dokument programmgesteuert erstellen.
draft: false
keywords:
- create rectangle shape
- set shadow color
- create word document
- how to add shadow
- how to create shape
language: de
og_description: Erstellen Sie eine Rechteckform in einem Word‑Dokument mit Aspose.Words
  für Java. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung, um die Schattenfarbe
  festzulegen, einen Schatten hinzuzufügen und ein Word‑Dokument zu erstellen.
og_title: Rechteckform in Word mit Java erstellen – Vollständige Anleitung
tags:
- Aspose.Words
- Java
- Document Automation
title: Rechteckform in Word mit Java erstellen – Vollständige Anleitung
url: /de/java/images-shapes/create-rectangle-shape-in-word-with-java-full-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Word mit Java erstellen – Vollständige Anleitung

Haben Sie jemals **eine Rechteckform** in einem Word-Dokument erstellen müssen, wussten aber nicht, wo Sie anfangen sollen? Sie sind nicht allein – viele Entwickler stoßen an diese Grenze, wenn sie zum ersten Mal versuchen, Grafiken programmgesteuert in Word zu zeichnen. Die gute Nachricht? Mit Aspose.Words für Java können Sie ein Rechteck auf eine Seite setzen, ihm einen schönen Schatten geben und die Datei in Sekunden speichern. In diesem Tutorial führen wir Sie Schritt für Schritt durch **wie man einen Schatten hinzufügt**, **die Schattenfarbe festlegt** und **ein Word-Dokument erstellt** von Grund auf.

Wir behandeln alles, was Sie benötigen: die erforderlichen Bibliotheken, jede Codezeile, warum bestimmte Einstellungen wichtig sind, und ein paar Tricks, die Sie in der offiziellen Dokumentation vielleicht nicht finden. Am Ende haben Sie ein sofort ausführbares Beispiel, das eine Rechteckform mit einem sanften grauen Schatten erstellt und als *Shadow.docx* speichert.

## Voraussetzungen – Was Sie vor dem Start benötigen

| Anforderung | Grund |
|-------------|-------|
| Java Development Kit (JDK) 8 oder neuer | Aspose.Words läuft auf jedem modernen JDK. |
| Maven oder Gradle (optional) | Vereinfacht das Hinzufügen der Aspose.Words-Abhängigkeit. |
| Aspose.Words für Java Lizenz (oder eine kostenlose Testversion) | Die Bibliothek ist kommerziell; eine Testversion reicht für Tests. |
| Eine IDE (IntelliJ IDEA, Eclipse, VS Code usw.) | Erleichtert das schnelle Ausführen und Debuggen des Beispiels. |

Wenn Sie bereits ein Java-Projekt haben, fügen Sie einfach die Maven-Koordinate hinzu:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Replace with the latest version -->
</dependency>
```

Keine aufwändige Einrichtung darüber hinaus – eine einfache `public static void main`‑Methode reicht aus.

![Beispiel für Rechteckform](https://example.com/rectangle-shadow.png "Rechteckform mit Schatten in Word")

*Bildbeschreibung: Beispiel für Rechteckform, das ein cyanblaues Rechteck mit einem grauen Schatten zeigt.*

## Schritt 1 – Neues Word-Dokument erstellen

Das erste, was wir tun müssen, ist ein leeres Dokument zu erzeugen. Stellen Sie sich das vor wie das Öffnen einer frischen Word-Datei, auf die Sie später zeichnen werden.

```java
// Step 1: Initialize a blank Document object
Document document = new Document();
```

Warum mit einem leeren `Document` beginnen? Weil Aspose.Words die Klasse `Document` als Leinwand für alle nachfolgenden Vorgänge behandelt – das Hinzufügen von Absätzen, Tabellen oder Formen. Wenn Sie diesen Schritt überspringen, erhalten Sie sofort eine `NullPointerException`, sobald Sie versuchen, etwas einzufügen.

## Schritt 2 – DocumentBuilder einrichten

Ein `DocumentBuilder` ist Ihr freundlicher Stift, der in das `Document` schreibt. Es ist die empfohlene Methode, Inhalte hinzuzufügen, da er automatisch die Cursor‑Position verwaltet.

```java
// Step 2: Create a DocumentBuilder tied to our document
DocumentBuilder builder = new DocumentBuilder(document);
```

Sie fragen sich vielleicht: „Warum das Dokument nicht direkt manipulieren?“ Die Antwort: Der Builder abstrahiert low‑level Details wie die Abschnittsverwaltung, wodurch der Code sauberer und weniger fehleranfällig wird.

## Schritt 3 – Rechteckform einfügen

Jetzt kommt der spaßige Teil – **wie man eine Form erstellt**. Wir fügen ein Rechteck mit 100 × 50 Punkten ein und geben ihm eine cyanfarbene Füllung, damit Sie es tatsächlich sehen können.

```java
// Step 3: Insert a rectangle shape of size 100x50 points
Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);

// Apply a solid fill color to make the shape visible
rectangle.setFillColor(java.awt.Color.CYAN);
```

* `ShapeType.RECTANGLE` teilt Aspose mit, dass wir ein Rechteck wollen; Sie könnten es gegen `OVAL`, `LINE` usw. austauschen.
* Die Abmessungen werden in Punkten angegeben (1 pt ≈ 1/72 in). Passen Sie sie an Ihr Layout an.
* Ohne Füllfarbe wäre die Form auf einer weißen Seite unsichtbar – daher das Cyan.

## Schritt 4 – Schatten hinzufügen und **Schattenfarbe festlegen**

Hier beantworten wir den **how to add shadow**‑Teil des Puzzles. Das Objekt `ShadowFormat` steuert jeden visuellen Aspekt des Schattens, von der Farbe bis zum Unschärferadius.

```java
// Step 4: Enable the shape's shadow and configure its appearance
rectangle.getShadowFormat().setVisible(true);                     // Turn the shadow on
rectangle.getShadowFormat().setColor(java.awt.Color.GRAY);      // **set shadow color** to gray
rectangle.getShadowFormat().setBlurRadius(5.0);                  // Soft blur for realism
rectangle.getShadowFormat().setOffsetX(4.0);                     // Horizontal offset
rectangle.getShadowFormat().setOffsetY(4.0);                     // Vertical offset
rectangle.getShadowFormat().setTransparency(0.3);               // 30 % transparent
```

Warum genau diese Werte?

* **Sichtbarkeit** – Ohne `setVisible(true)` werden die übrigen Einstellungen ignoriert.
* **Farbe** – Grau ist eine neutrale Wahl, die sowohl auf hellen als auch dunklen Hintergründen funktioniert. Ersetzen Sie `java.awt.Color.GRAY` gern durch jede gewünschte `java.awt.Color`.
* **Unschärferadius** – Ein Wert von `5.0` erzeugt ein sanftes Feder‑Gefühl; größere Zahlen lassen den Schatten diffuser erscheinen.
* **OffsetX/Y** – Offsets verschieben den Schatten nach rechts und unten und simulieren eine Lichtquelle von oben‑links.
* **Transparenz** – Ein halbtransparenter Schatten fügt sich besser in die Seite ein, besonders beim Drucken.

Wenn Sie ein schärferes Aussehen benötigen, setzen Sie den Unschärferadius auf `0` und erhöhen Sie den Offset. Experimentieren Sie – Schatten sind stark visuell, und die richtigen Einstellungen hängen vom Design Ihres Dokuments ab.

## Schritt 5 – Dokument speichern

Abschließend speichern wir alles in einer `.docx`‑Datei. Sie können jeden gewünschten Pfad wählen; stellen Sie nur sicher, dass das Verzeichnis existiert.

```java
// Step 5: Save the document with the shaped shadow to a file
document.save("YOUR_DIRECTORY/Shadow.docx");
```

Wenn Sie *Shadow.docx* in Microsoft Word öffnen, sehen Sie ein cyanblaues Rechteck mit einem dezenten grauen Schatten, der 4 pts nach rechts und unten schwebt. Das ist der komplette **create word document**‑Ablauf.

### Erwartetes Ergebnis

| Element | Aussehen |
|---------|----------|
| Rechteck | Cyan‑Füllung, Größe 100 × 50 pt |
| Schatten | Grau, 30 % transparent, 5 pt Unschärfe, Offset (4, 4) |
| Datei | `Shadow.docx` gespeichert am von Ihnen angegebenen Pfad |

Falls die Form nicht erscheint, prüfen Sie, ob die Füllfarbe nicht mit dem Seitenhintergrund übereinstimmt und ob der Schatten auf sichtbar gesetzt ist.

## Profi‑Tipps & häufige Stolperfallen

* **Pro‑Tipp:** Verwenden Sie `rectangle.setStrokeColor(java.awt.Color.BLACK);`, wenn Sie einen Rand um die Form wünschen. Das lässt das Rechteck auf einer gedruckten Seite stärker hervortreten.
* **Achten Sie auf:** Das Speichern in einem schreibgeschützten Ordner löst eine `IOException` aus. Wählen Sie einen beschreibbaren Ort oder passen Sie die Dateiberechtigungen an.
* **Randfall:** Wenn Sie eine transparente Füllung (keine Farbe) benötigen, rufen Sie `rectangle.setFillColor(java.awt.Color.WHITE); rectangle.setFillOpacity(0.0);` auf. Die Form wirft weiterhin einen Schatten, was für wasserzeichenartige Grafiken nützlich sein kann.
* **Leistungshinweis:** Das Hinzufügen von Hunderten von Formen in einer Schleife kann den Speicherverbrauch erhöhen. Rufen Sie `document.save` nur einmal nach dem Hinzufügen aller Formen auf.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das gesamte Programm, das Sie in eine Java‑Klasse namens `ShadowDemo` kopieren können. Es kompiliert und läuft unverändert (vorausgesetzt, Sie haben das Aspose.Words‑JAR im Klassenpfad).

```java
import com.aspose.words.*;

public class ShadowDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Initialize a DocumentBuilder to construct the document content
        DocumentBuilder builder = new DocumentBuilder(document);

        // Step 3: Insert a rectangle shape of size 100x50 points
        Shape rectangle = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Apply a solid fill color to make the shape visible
        rectangle.setFillColor(java.awt.Color.CYAN);

        // Step 4: Enable the shape's shadow and configure its appearance
        rectangle.getShadowFormat().setVisible(true);
        rectangle.getShadowFormat().setColor(java.awt.Color.GRAY); // set shadow color
        rectangle.getShadowFormat().setBlurRadius(5.0);
        rectangle.getShadowFormat().setOffsetX(4.0);
        rectangle.getShadowFormat().setOffsetY(4.0);
        rectangle.getShadowFormat().setTransparency(0.3);

        // Step 5: Save the document with the shaped shadow to a file
        document.save("YOUR_DIRECTORY/Shadow.docx");
    }
}
```

Führen Sie das Programm aus, öffnen Sie das resultierende *Shadow.docx* und Sie sehen das Rechteck mit seinem Schatten exakt wie beschrieben.

## Was, wenn Sie mehr Formen benötigen?

Sie fragen sich vielleicht: „Kann ich **eine Rechteckform** mehrfach erstellen oder andere Formen verwenden?“ Absolut. Durchlaufen Sie einfach den Einfüge‑Code in einer Schleife und passen Sie die Koordinaten mit `builder.moveTo` oder `builder.insertParagraph` an. Die gleichen Schatteneinstellungen können wiederverwendet werden, indem Sie sie in eine Hilfsmethode auslagern:

```java
private static void applyStandardShadow(Shape shape) {
    shape.getShadowFormat().setVisible(true);
    shape.getShadowFormat().setColor(java.awt.Color.GRAY);
    shape.getShadowFormat().setBlurRadius(5.0);
    shape.getShadowFormat().setOffsetX(4.0);
    shape.getShadowFormat().setOffsetY(4.0);
    shape.getShadowFormat().setTransparency(0.3);
}
```

Rufen Sie `applyStandardShadow(rectangle);` nach jedem Form‑Einfügen auf, um Ihren Code DRY (Don’t Repeat Yourself) zu halten.

## Nächste Schritte – über die Grundlagen hinaus

Jetzt, wo Sie **wissen, wie man einen Schatten hinzufügt**, sollten Sie diese verwandten Themen erkunden:

* **Wie man die Schattenfarbe** für Textläufe festlegt – verleiht Überschriften einen dezenten Auftrieb.
* **Word-Dokument erstellen** mit Tabellen und Bildern – Formen mit anderem Inhalt kombinieren.
* **Wie man Form‑Animationen** mit Word‑eingebauten Möglichkeiten erstellt

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}