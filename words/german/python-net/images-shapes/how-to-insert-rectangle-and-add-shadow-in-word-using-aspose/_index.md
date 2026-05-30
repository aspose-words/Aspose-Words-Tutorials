---
category: general
date: 2026-05-30
description: Wie man ein Rechteck einfügt und in Word mit Aspose einen Schatten hinzufügt
  – eine Schritt‑für‑Schritt‑Python‑Anleitung zur Erstellung eines Word‑Dokuments
  mit Formschatten‑Effekt.
draft: false
keywords:
- how to insert rectangle
- add shadow to shape
- how to add shape shadow
- apply shadow effect word
- create word document aspose
language: de
og_description: Wie man ein Rechteck einfügt und einen Schatten in Word mit Aspose
  hinzufügt – lernen Sie, ein Word-Dokument mit Formschatteneffekt in Python zu erstellen.
og_title: Wie man ein Rechteck einfügt und in Word mit Aspose einen Schatten hinzufügt
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  headline: How to insert rectangle and add shadow in Word using Aspose
  type: TechArticle
- description: How to insert rectangle and add shadow in Word using Aspose – a step‑by‑step
    Python guide to create a Word document with shape shadow effect.
  name: How to insert rectangle and add shadow in Word using Aspose
  steps:
  - name: What each property does
    text: '| Property | Effect | Typical Range | |----------|--------|---------------|
      | `visible` | Turns the shadow on/off | `True` / `False` | | `distance` | How
      far the shadow sits from the shape | 2 – 10 pts | | `blur` | Softness of the
      shadow edges | 4 – 12 pts | | `color` | Shadow hue; dark gray is a sa'
  - name: Adding Multiple Shapes
    text: If you need more than one rectangle, simply repeat the `insert_shape` call.
      Remember to move the builder’s cursor (`builder.move_to(shape)`) or adjust `shape.left`/`shape.top`
      to avoid overlap.
  - name: Changing the Shape Type
    text: While this guide focuses on rectangles, the same pattern works for ovals,
      stars, or custom free‑form shapes. Replace `ShapeType.RECTANGLE` with `ShapeType.OVAL`,
      `ShapeType.CLOUD`, etc., and the shadow settings remain identical.
  - name: Saving to Other Formats
    text: 'Aspose.Words can export to PDF, PNG, or even XPS with a single line:'
  - name: Handling Large Documents
    text: When generating massive reports, consider calling `doc.update_page_layout()`
      after inserting all shapes. This forces a layout pass and can improve performance
      when you later convert to PDF.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word Automation
title: Wie man ein Rechteck einfügt und in Word mit Aspose einen Schatten hinzufügt
url: /de/python/images-shapes/how-to-insert-rectangle-and-add-shadow-in-word-using-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Rechteck einfügt und einen Schatten in Word mit Aspose hinzufügt

Haben Sie sich jemals gefragt, **wie man ein Rechteck einfügt** in eine Word‑Datei, ohne die Benutzeroberfläche zu öffnen? Sie sind nicht allein. Viele Entwickler müssen Berichte, Rechnungen oder Zertifikate on‑the‑fly erzeugen, und das Zeichnen eines einfachen Rechtecks mit einem schönen Schatten lässt das Ergebnis professionell wirken. In diesem Tutorial gehen wir die genauen Schritte durch, um ein Word‑Dokument zu erstellen, eine Rechteckform einzufügen und mit Aspose.Words für Python einen realistischen Schatten anzuwenden.

Wir behandeln alles von der Einrichtung des Aspose‑Pakets bis zum Feintuning von Abstand, Weichzeichnung und Deckkraft des Schattens. Am Ende haben Sie ein wiederverwendbares Snippet, das Sie in jede Automatisierungspipeline einbinden können. Kein Hexenwerk, nur klarer Code und ein paar praktische Tipps.

## Voraussetzungen

Bevor wir starten, stellen Sie sicher, dass Sie Folgendes haben:

- Python 3.8+ installiert (der Code funktioniert mit 3.9, 3.10 und neueren Versionen)
- Eine aktive Aspose.Words‑für‑Python‑Lizenz oder einen kostenlosen Evaluierungsschlüssel
- `aspose-words`‑Paket installiert via `pip install aspose-words`
- Einen beschreibbaren Ordner, in dem das erzeugte **create word document aspose** gespeichert wird

Das war’s – keine zusätzlichen DLLs, kein COM‑Interop, nur reines Python.

## Schritt 1: Dokument initialisieren (How to create word document aspose)

Zuerst benötigen Sie ein frisches `Document`‑Objekt. Stellen Sie sich das als leere Leinwand vor. Der folgende Code erstellt das Dokument und einen `DocumentBuilder`, mit dem wir Formen einfügen können.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

*Warum das wichtig ist:* Der `DocumentBuilder` bietet Ihnen eine High‑Level‑API, um Absätze, Tabellen und – ja – Formen hinzuzufügen, ohne sich mit Low‑Level‑Node‑Bäumen zu beschäftigen. Wenn Sie den Builder überspringen und Knoten direkt manipulieren, endet man mit sehr ausführlichem Code, der schwer zu warten ist.

## Schritt 2: Das Rechteck einfügen (how to insert rectangle)

Jetzt fügen wir tatsächlich **wie man ein Rechteck einfügt**. Aspose.Words behandelt ein Rechteck als generischen Formtyp. Sie geben Breite und Höhe in Punkten an (1 Punkt ≈ 1/72 Zoll). Passen Sie die Zahlen gern an Ihr Layout an.

```python
# Step 2: Insert a rectangle shape of the desired size
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

> **Pro‑Tipp:** Wenn das Rechteck an einer bestimmten Position auf der Seite liegen soll, setzen Sie nach dem Einfügen `shape.left` und `shape.top`. So erhalten Sie pixelgenaue Kontrolle.

## Schritt 3: Auf das ShadowFormat der Form zugreifen (add shadow to shape)

Der visuelle Flair einer Form steckt in ihrem `ShadowFormat`. Durch das Abrufen erhalten wir Zugriff auf jede Eigenschaft, die das Aussehen des Schattens definiert.

```python
# Step 3: Access the shape's shadow format
shadow = shape.shadow_format
```

An diesem Punkt ist der Schatten unsichtbar – denken Sie an eine versteckte Ebene, die auf Ihre Anweisungen wartet.

## Schritt 4: Schatten konfigurieren (how to add shape shadow, apply shadow effect word)

Hier passiert die Magie. Wir schalten den Schatten ein und passen sein Aussehen an. Die untenstehenden Werte erzeugen einen weichen, diagonalen Schatten, der für die meisten Dokumente gut funktioniert, aber Sie können experimentieren.

```python
# Step 4: Make the shadow visible and configure its appearance
shadow.visible = True                # Show the shadow
shadow.distance = 5.0                # Distance from the shape (points)
shadow.blur = 8.0                    # Blur radius (points)
shadow.color = aw.Color.dark_grey   # Shadow color
shadow.opacity = 0.6                 # Opacity (0‑1)
shadow.angle = 45.0                  # Direction in degrees
```

### Was jede Eigenschaft bewirkt

| Property | Effect | Typical Range |
|----------|--------|---------------|
| `visible` | Schaltet den Schatten ein/aus | `True` / `False` |
| `distance` | Abstand des Schattens von der Form | 2 – 10 pts |
| `blur` | Weichheit der Schattenkanten | 4 – 12 pts |
| `color` | Schattenfarbe; Dunkelgrau ist ein sicherer Standard | Beliebiges `aw.Color` |
| `opacity` | Transparenz; 0 = unsichtbar, 1 = undurchsichtig | 0.3 – 0.8 für einen dezenten Look |
| `angle` | Richtung, aus der das Licht kommt | 0 – 360° |

**Warum das anpassen?** Ein gut abgestimmter Schatten lässt ein flaches Rechteck gehoben wirken und verleiht Tiefe, ohne Bilder zu benötigen. Ist die `opacity` zu hoch, wirkt der Schatten hart; ist sie zu niedrig, verschwindet er.

## Schritt 5: Dokument speichern (create word document aspose)

Zum Schluss schreiben wir die Datei auf die Festplatte. Sie können jede von Aspose.Words unterstützte Erweiterung verwenden (`.docx`, `.pdf`, `.html`). Für dieses Tutorial bleiben wir bei `.docx`.

```python
# Step 5: Save the document with the shaped shadow
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Öffnen Sie die resultierende Datei in Microsoft Word, und Sie sehen ein klares Rechteck mit einem dezenten Schatten – genau das, was man von einer professionell gestalteten Vorlage erwartet.

![how to insert rectangle shape with shadow using Aspose.Words](/images/rectangle-shadow.png){alt="wie man ein Rechteck mit Schatten mit Aspose.Words einfügt"}

*Der Screenshot (oben) zeigt das Rechteck mit angewendetem Schatten. Beachten Sie die sanfte Weichzeichnung und den 45°‑Winkel, der einen natürlichen Look erzeugt.*

## Häufige Varianten und Randfälle

### Mehrere Formen hinzufügen

Wenn Sie mehr als ein Rechteck benötigen, wiederholen Sie einfach den Aufruf `insert_shape`. Denken Sie daran, den Cursor des Builders zu bewegen (`builder.move_to(shape)`) oder `shape.left`/`shape.top` anzupassen, um Überlappungen zu vermeiden.

```python
# Example: Insert a second rectangle 200 points to the right
second_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
second_shape.left = shape.left + 200
second_shape.top = shape.top
```

### Formtyp ändern

Obwohl dieser Leitfaden sich auf Rechtecke konzentriert, funktioniert das gleiche Muster für Ovale, Sterne oder benutzerdefinierte Freiform‑Formen. Ersetzen Sie `ShapeType.RECTANGLE` durch `ShapeType.OVAL`, `ShapeType.CLOUD` usw., und die Schatteneinstellungen bleiben identisch.

### In andere Formate speichern

Aspose.Words kann mit einer einzigen Zeile in PDF, PNG oder sogar XPS exportieren:

```python
doc.save("output/ShapeWithShadow.pdf")
```

Die Schattendarstellung bleibt in allen Formaten erhalten, sodass Ihr PDF genauso aussieht wie die Word‑Datei.

### Umgang mit großen Dokumenten

Beim Erzeugen riesiger Berichte sollten Sie nach dem Einfügen aller Formen `doc.update_page_layout()` aufrufen. Das erzwingt einen Layout‑Durchlauf und kann die Performance beim späteren PDF‑Export verbessern.

## Vollständiges funktionierendes Beispiel (Alle Schritte kombiniert)

Unten finden Sie das komplette Skript, das Sie in eine Datei namens `rectangle_shadow.py` kopieren können. Führen Sie es mit `python rectangle_shadow.py` aus und prüfen Sie den Ordner `output`.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
os.makedirs("output", exist_ok=True)

# Initialize the document and builder
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# Insert a rectangle
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

# Configure the shadow
shadow = shape.shadow_format
shadow.visible = True
shadow.distance = 5.0
shadow.blur = 8.0
shadow.color = aw.Color.dark_grey
shadow.opacity = 0.6
shadow.angle = 45.0

# Save the document
output_path = "output/ShapeWithShadow.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Das Ausführen dieses Skripts erzeugt exakt das gleiche Dokument, das wir zuvor besprochen haben. Passen Sie die Werte gern an; der Code ist bewusst einfach gehalten, damit Sie ohne Angst experimentieren können.

## Häufig gestellte Fragen

**F: Funktioniert das unter Linux?**


## Was sollten Sie als Nächstes lernen?

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}