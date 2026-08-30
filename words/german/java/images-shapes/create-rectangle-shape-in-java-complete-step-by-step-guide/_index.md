---
category: general
date: 2026-07-03
description: Erstelle ein Rechteck in Java und lerne, wie man dem Objekt einen Schatten
  hinzufügt, den Schatteneffekt anwendet, die Transparenz des Objekts einstellt und
  schnell ein leeres Dokument erstellt.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- apply shadow effect
- set shape transparency
- create blank document
language: de
og_description: Erstelle ein Rechteck in Java mit Schatten, Transparenz und einem
  leeren Dokument. Befolge diese Anleitung, um die Formenbearbeitung zu meistern.
og_title: Erstelle ein Rechteck in Java – Vollständiges Programmier‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  headline: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  type: TechArticle
- description: Create rectangle shape in Java and learn how to add shadow to shape,
    apply shadow effect, set shape transparency, and create blank document quickly.
  name: Create rectangle shape in Java – Complete Step‑by‑Step Guide
  steps:
  - name: What if I want a different shadow color?
    text: 'Simply change the `setColor` call:'
  - name: Can I apply the same shadow to multiple shapes?
    text: 'Yes. Create one `ShadowEffect` instance, configure it, then reuse it:'
  - name: How do I change the shadow blur dynamically?
    text: Expose a UI slider that maps to `setBlurRadius`. Values between `2` and
      `12` are typical; larger numbers produce a “glow” rather than a crisp shadow.
  - name: What if I need the shape to float rather than be inline?
    text: 'Swap the wrap type:'
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Automation
title: Rechteckform in Java erstellen – Vollständige Schritt‑für‑Schritt‑Anleitung
url: /de/java/images-shapes/create-rectangle-shape-in-java-complete-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Java erstellen – Vollständige Schritt‑für‑Schritt‑Anleitung

Haben Sie sich schon einmal gefragt, wie man **eine Rechteckform** in einem Word‑Dokument mit Java **erstellt**? Sie sind nicht allein – Entwickler benötigen häufig eine schnelle Möglichkeit, geometrische Grafiken hinzuzufügen und ihnen einen dezenten Schatten zu geben, damit das Layout professioneller wirkt. In diesem Tutorial gehen wir den gesamten Prozess durch: vom **Erstellen eines leeren Dokuments** über das **Hinzufügen eines Schattens zur Form**, das **Anwenden des Schatteneffekts** bis hin zum **Festlegen der Transparenz der Form** für ein professionelles Aussehen.

Das Code‑Snippet unten ist ein voll funktionsfähiges Beispiel, das Sie in Ihr Projekt kopieren‑und‑einfügen können. Keine externe Dokumentation nötig – folgen Sie einfach den Schritten, verstehen Sie das „Warum“ und Sie erzeugen schattierte Rechtecke in Sekundenschnelle.

## Was Sie lernen werden

- Wie man **eine Rechteckform** programmgesteuert mit Aspose.Words für Java **erstellt**.
- Welche Aufrufe nötig sind, um **einen Schatten zur Form hinzuzufügen** und deren visuelle Eigenschaften zu konfigurieren.
- Wie man **Schatteneffekt anwendet** und Parameter wie Versatz, Unschärferadius und Farbe anpasst.
- Techniken, um **die Transparenz der Form festzulegen** für ein dezenteres Erscheinungsbild.
- Wie man **ein leeres Dokument erstellt**, die Form einfügt und das Ergebnis speichert.

> **Profi‑Tipp:** All diese Aktionen werden an einer einzigen `Document`‑Instanz durchgeführt, sodass Sie sie hintereinander ausführen können, ohne sich um Zwischenspeicherungen kümmern zu müssen.

## Voraussetzungen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

- Java 17 (oder ein aktuelles JDK) installiert.
- Aspose.Words für Java‑Bibliothek zu Ihrem Projekt hinzugefügt (Maven‑Koordinaten: `com.aspose:aspose-words:23.12`).
- Eine Java‑IDE oder ein einfacher Texteditor – nichts Besonderes, nur ein Ort zum Kompilieren und Ausführen.

Falls Ihnen etwas fehlt, holen Sie sich das JDK von Oracle und binden die Aspose‑Abhängigkeit über Maven oder Gradle ein. Sobald das erledigt ist, können Sie loslegen.

## Schritt 1: **Leeres Dokument erstellen** – die Leinwand für alles

Das allererste, was Sie benötigen, ist ein leeres `Document`‑Objekt. Denken Sie daran wie an ein frisches Blatt Papier; ohne dieses gibt es keinen Platz für Ihr Rechteck.

```java
// Step 1: Create a new blank document
Document document = new Document();
```

Warum mit einem leeren Dokument beginnen? Weil jede Form innerhalb einer `Section` lebt, und ein neu instanziiertes `Document` bereits eine Standard‑Section mit einem Body enthält, der bereit ist, Knoten aufzunehmen. Würden Sie diesen Schritt überspringen, müssten Sie später manuell Sections erzeugen, was unnötige Komplexität erzeugt.

## Schritt 2: **Rechteckform erstellen** und Größe festlegen

Jetzt, wo wir eine Leinwand haben, **erstellen wir die Rechteckform**. Die Klasse `Shape` benötigt die Dokumentreferenz und einen `ShapeType`. Hier wählen wir `RECTANGLE` und setzen Breite/Höhe in Punkten (1 pt ≈ 1/72 Zoll).

```java
// Step 2: Insert a rectangle shape and define its size and layout
Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
rectangleShape.setWidth(200);   // 200 pt ≈ 2.78 inches
rectangleShape.setHeight(100);  // 100 pt ≈ 1.39 inches
rectangleShape.setWrapType(WrapType.INLINE);
```

Warum `WrapType.INLINE` setzen? Inline‑Wrapping lässt die Form wie ein Zeichen im Absatz verhalten, sodass sie sich zusammen mit dem umgebenden Text bewegt. Wenn Sie ein schwebendes Verhalten benötigen, wechseln Sie zu `WrapType.SQUARE` oder `WrapType.TOP_BOTTOM`.

## Schritt 3: **Schatteneffekt anwenden** – dem Rechteck Tiefe verleihen

Ein flaches Rechteck sieht… nun ja, flach aus. Ein Schatten lässt es hervorstechen. Wir **wenden den Schatteneffekt** an, indem wir eine `ShadowEffect`‑Instanz erstellen und deren visuelle Eigenschaften anpassen.

```java
// Step 3: Create a shadow effect and configure its visual properties
ShadowEffect shadowEffect = new ShadowEffect();
shadowEffect.setColor(Color.getGray(0.5));   // medium gray
shadowEffect.setOffsetX(5);                  // horizontal offset (points)
shadowEffect.setOffsetY(5);                  // vertical offset (points)
shadowEffect.setBlurRadius(8);               // softness of the shadow
shadowEffect.setTransparency(0.3);           // 30 % transparent
```

Ein kurzer Überblick:

- **Color** – `Color.getGray(0.5)` liefert ein 50 % Grau, das neutral ist und auf den meisten Hintergründen gut funktioniert.
- **OffsetX/Y** – Positive Werte verschieben den Schatten nach rechts bzw. unten; negative Werte würden ihn nach links/oben bewegen.
- **BlurRadius** – Größere Werte erzeugen einen weicheren, stärker verbreiteten Schatten.
- **Transparency** – Werte von `0` (undurchsichtig) bis `1` (voll transparent). Hier haben wir `0.3` gewählt für einen dezenten Effekt.

## Schritt 4: **Schatten zur Form hinzufügen** – den Effekt binden

Den Effekt zu erstellen reicht nicht; wir müssen **den Schatten zur Form hinzufügen**, indem wir das `ShadowEffect`‑Objekt dem Rechteck zuweisen.

```java
// Step 4: Apply the shadow effect to the rectangle shape
rectangleShape.setShadowEffect(shadowEffect);
```

Im Hintergrund aktualisiert dieser Aufruf das zugrunde liegende OpenXML‑Markup (`<w:shdw>`), das Word zur Darstellung von Schatten verwendet. Wenn Sie die gespeicherte `.docx`‑Datei untersuchen, sehen Sie ein `<w:effect>`‑Element mit den von uns gesetzten Parametern.

## Schritt 5: **Transparenz der Form festlegen** – optional, aber oft nützlich

Manchmal möchte man, dass das Rechteck selbst halbtransparent ist, sodass der Hintergrundtext durchscheint. Die Klasse `Shape` bietet `setFillColor` und `setFillTransparency`. Hier ein kurzes Beispiel, das das Rechteck zu 40 % transparent macht:

```java
// Optional: make the rectangle partially transparent
rectangleShape.setFillColor(Color.getWhite());
rectangleShape.setFillTransparency(0.4); // 40 % transparent
```

Warum das sinnvoll sein kann? Stellen Sie sich ein Wasserzeichen oder einen hervorgehobenen Hinweis vor, bei dem der darunterliegende Inhalt lesbar bleiben muss. Passen Sie den Transparenzwert an Ihren Gestaltungsstil an.

## Schritt 6: **Form in das Dokument einfügen**

Wir haben das Rechteck gebaut, einen Schatten hinzugefügt und (optional) die Transparenz gesetzt. Der letzte Schritt ist, **die Form dem ersten Abschnitt des Dokuments hinzuzufügen**.

```java
// Step 5: Add the shape to the first section of the document
document.getFirstSection().getBody().appendChild(rectangleShape);
```

Das Anhängen der Form an den Body legt sie ans Ende des ersten Absatzes. Wenn Sie einen bestimmten Einfügepunkt benötigen, holen Sie sich das Ziel‑`Paragraph` und verwenden `insertBefore` oder `insertAfter`.

## Schritt 7: **Dokument speichern** – Ergebnis ansehen

All diese Arbeit endet in einem einzigen `save`‑Aufruf. Wählen Sie einen Pfad, der zu Ihrer Umgebung passt.

```java
// Step 6: Save the document with the shadowed shape
document.save("YOUR_DIRECTORY/ShadowShape.docx");
```

Öffnen Sie die resultierende `ShadowShape.docx` in Microsoft Word oder LibreOffice, und Sie sehen ein klares Rechteck mit einem sanften grauen Schatten, leicht transparent, falls Sie den optionalen Schritt beibehalten haben. Die Darstellung entspricht exakt den programmatisch definierten Parametern.

---

![create rectangle shape with shadow in a Word document](https://example.com/images/rectangle-shadow.png "create rectangle shape with shadow")

*Bild‑Alt‑Text:* **Rechteckform mit Schatten erstellen** – visuelle Darstellung des Endergebnisses.

## Häufige Fragen & Sonderfälle

### Was tun, wenn ich eine andere Schattenfarbe möchte?

Einfach den Aufruf `setColor` ändern:

```java
shadowEffect.setColor(Color.getRed()); // bright red shadow
```

Denken Sie daran, dass zu kräftige Schatten unprofessionell wirken können; dezente Töne funktionieren in der Regel am besten.

### Kann ich denselben Schatten auf mehrere Formen anwenden?

Ja. Erzeugen Sie eine `ShadowEffect`‑Instanz, konfigurieren Sie sie und verwenden Sie sie mehrfach:

```java
Shape circle = new Shape(document, ShapeType.OVAL);
circle.setShadowEffect(shadowEffect); // same effect as rectangle
```

Vermeiden Sie jedoch, das `ShadowEffect` nach dem Anhängen an andere Formen zu verändern, es sei denn, Sie möchten alle gleichzeitig aktualisieren.

### Wie kann ich den Schatten‑Unschärferadius dynamisch ändern?

Bieten Sie einen UI‑Slider an, der auf `setBlurRadius` abbildet. Werte zwischen `2` und `12` sind üblich; höhere Zahlen erzeugen eher ein „Leuchten“ als einen klaren Schatten.

### Was, wenn die Form schweben statt inline sein soll?

Den Wrap‑Typ austauschen:

```java
rectangleShape.setWrapType(WrapType.SQUARE);
rectangleShape.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
rectangleShape.setHorizontalAlignment(HorizontalAlignment.CENTER);
```

Schwebende Formen geben Ihnen mehr Layout‑Freiheit, erfordern jedoch zusätzliche Positionierungslogik.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort einsatzbereite Programm, das alle besprochenen Schritte integriert. Führen Sie es als reguläre Java‑Anwendung aus.

```java
import com.aspose.words.*;

public class ShadowRectangleDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a blank document
        Document document = new Document();

        // 2. Build the rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.RECTANGLE);
        rectangleShape.setWidth(200);
        rectangleShape.setHeight(100);
        rectangleShape.setWrapType(WrapType.INLINE);

        // 3. Configure shadow effect
        ShadowEffect shadowEffect = new ShadowEffect();
        shadowEffect.setColor(Color.getGray(0.5));
        shadowEffect.setOffsetX(5);
        shadowEffect.setOffsetY(5);
        shadowEffect.setBlurRadius(8);
        shadowEffect.setTransparency(0.3);

        // 4. Apply shadow to the rectangle
        rectangleShape.setShadowEffect(shadowEffect);

        // 5. (Optional) Make rectangle semi‑transparent
        rectangleShape.setFillColor(Color.getWhite());
        rectangleShape.setFillTransparency(0.4);

        // 6. Insert shape into the document
        document.getFirstSection().getBody().appendChild(rectangleShape);

        // 7. Save the file
        document.save("ShadowShape.docx");
    }
}
```

**Erwartete Ausgabe:** Beim Öffnen von `ShadowShape.docx` sehen Sie ein weißes Rechteck, 200 × 100 pt, zentriert im ersten Absatz, mit einem mittelgrauen Schatten, der um 5 pt versetzt, mit einem Radius von 8 unscharf ist und zu 30 % transparent. Das Rechteck selbst ist zu 40 % transparent, sodass darunterliegender Text durchscheint.

## Fazit

Wir haben gerade **eine Rechteckform** von Grund auf **erstellt**, **einen Schatten zur Form hinzugefügt**, **den Schatteneffekt angewendet** und sogar **die Transparenz der Form festgelegt** – alles, während wir **ein leeres Dokument** als Basis nutzten. Der Ansatz ist unkompliziert, nutzt die fluente API von Aspose.Words und lässt sich leicht auf Kreise, Sterne oder benutzerdefinierte Polygone erweitern.

Was steht als Nächstes auf Ihrer Roadmap? Probieren Sie `ShapeType.RECTANGLE` durch `ShapeType.OVAL` zu ersetzen, um schattierte Kreise zu erzeugen, oder experimentieren Sie mit Farbverläufen für

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}