---
category: general
date: 2026-10-16
description: Erstelle ein leeres Word‑Dokument, füge in Word eine Form ein, füge einen
  äußeren Schatten hinzu und speichere es mit Python als PDF.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert shape in word
- save as pdf python
- add outer shadow shape
- create pdf with shape
language: de
lastmod: 2026-10-16
og_description: Erstellen Sie ein leeres Word‑Dokument mit einer äußeren Schattenform
  mithilfe von Aspose.Words für Python. Diese Anleitung zeigt, wie Sie die Form einfügen,
  den Schatten anwenden und die Datei als PDF speichern.
og_image_alt: Screenshot of a Word document containing a rectangle shape with an outer
  shadow, saved as PDF
og_title: Leeres Word‑Dokument mit Formschatten erstellen – Python‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-16'
  description: Create a blank Word document, insert shape in Word, add outer shadow,
    and save as PDF using Python.
  headline: Create blank Word document with shadowed shape in Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- PDF generation
- Shape styling
title: Erstelle ein leeres Word‑Dokument mit schattierter Form in Python
url: /de/python/word-automation/create-blank-word-document-with-shadowed-shape-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Leeres Word-Dokument mit schattierter Form in Python erstellen

Wenn Sie ein **leeres Word-Dokument** erstellen und eine benutzerdefinierte Grafik hinzufügen müssen, deckt dieser Leitfaden alles ab. Wir führen Sie Schritt für Schritt durch das **Einfügen einer Form in Word**, das Anwenden einer **äußeren Schattenform** und schließlich das **Speichern als PDF mit Python**.

Sie lernen, wie Sie Aspose.Words für Python einrichten, ein Rechteck erstellen, dessen Schatten gestalten und ein PDF erzeugen, das den visuellen Effekt beibehält. Vorkenntnisse der Aspose‑API sind nicht erforderlich, jedoch sollten Sie Grundkenntnisse in Python und eine funktionierende Installation von Python 3.10 oder höher besitzen.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Python 3.10 oder neuer installiert.
* Eine aktive Aspose.Words für Python Lizenz (eine kostenlose Testversion ist für die Evaluierung ausreichend).
* `pip`‑Zugriff, um das Paket `aspose-words` zu installieren.
* Schreibberechtigung für das Verzeichnis, in dem das PDF gespeichert wird.

Sie können die Bibliothek mit einem einzigen Befehl installieren:

```bash
pip install aspose-words
```

## Leeres Word-Dokument erstellen – Umgebung einrichten

Der erste Schritt besteht darin, eine leere Word-Datei zu erstellen, die als Zeichenfläche für die Form dient.

```python
import aspose.words as aw

# Initialize a new, empty document
doc = aw.Document()
# DocumentBuilder provides convenient methods for adding content
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` stellt ein komplett leeres Word-Dokument dar. Durch die Verwendung von `DocumentBuilder` erhalten Sie Zugriff auf Methoden wie `insert_shape`, die wir im nächsten Schritt verwenden werden.

## Form in Word einfügen und Abmessungen festlegen

Jetzt fügen wir ein Rechteck hinzu, das später einen äußeren Schatten erhalten soll. Die Größe wird in Punkten angegeben (1 pt ≈ 1/72 Zoll).

```python
# Insert a rectangle shape with a width of 200 pt and a height of 100 pt
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)
```

Der Aufruf `insert_shape` gibt ein `Shape`‑Objekt zurück, das Sie weiter anpassen können. Zu diesem Zeitpunkt enthält das Dokument bereits ein sichtbares Rechteck, wenn es in Microsoft Word geöffnet wird.

## Äußere Schattenform hinzufügen – Anpassung des Effekts

Aspose.Words stellt die Klasse `ShadowEffect` zur Verfügung, um Schatteneigenschaften wie Stil, Unschärfe, Abstand und Farbe zu definieren.

```python
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Create a new shadow effect instance
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER          # Choose an outer shadow
shadow.blur = 5.0                         # Softness of the shadow edges
shadow.distance = 3.0                     # Offset distance from the shape
shadow.color = aw.Color.black             # Shadow color

# Apply the shadow to the rectangle
rectangle.shadow = shadow
```

Durch das Setzen von `style` auf `OUTER` wird der Schatten außerhalb der Rechteckkante angezeigt, was einen dezenten 3‑D‑Effekt erzeugt. Sie können mit `blur` und `distance` experimentieren, um einen kompakteren oder stärker verbreiteten Schatten zu erzielen.

## Als PDF speichern mit Python – Dokument finalisieren

Nachdem die Form gestaltet wurde, kann das Dokument direkt als PDF gespeichert werden. Aspose.Words übernimmt die Konvertierung intern und bewahrt den Schatteneffekt.

```python
output_path = "output/shape_with_shadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Wenn Sie `shape_with_shadow.pdf` in einem beliebigen PDF‑Betrachter öffnen, sehen Sie das Rechteck mit dem äußeren Schatten exakt so, wie es in Word erschien.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das vollständige Skript, das alle Schritte kombiniert. Kopieren Sie es in eine Datei namens `create_word_with_shadow.py` und führen Sie sie aus.

```python
import os
import aspose.words as aw
from aspose.words.drawing import ShadowEffect, ShadowStyle

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1. Create a blank Word document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# 2. Insert a rectangle shape
rectangle = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,
    width=200,
    height=100
)

# 3. Define and apply an outer shadow
shadow = ShadowEffect()
shadow.style = ShadowStyle.OUTER
shadow.blur = 5.0
shadow.distance = 3.0
shadow.color = aw.Color.black
rectangle.shadow = shadow

# 4. Save the document as PDF
pdf_path = os.path.join(output_dir, "shape_with_shadow.pdf")
doc.save(pdf_path)

print(f"PDF generated at: {pdf_path}")
```

**Erwartete Ausgabe**

Beim Ausführen des Skripts wird eine Bestätigungszeile ausgegeben, z. B.:

```
PDF generated at: output/shape_with_shadow.pdf
```

Das Öffnen des resultierenden PDFs zeigt eine einzelne Seite mit einem 200 pt × 100 pt großen Rechteck und einem weichen schwarzen äußeren Schatten.

## Häufige Varianten und Sonderfälle

* **Farbe des Schattens ändern** – Ersetzen Sie `aw.Color.black` durch einen anderen `aw.Color`‑Wert, z. B. `aw.Color.red` oder `aw.Color.from_argb(255, 0, 120, 215)`.
* **Eine andere Form verwenden** – Ändern Sie `aw.drawing.ShapeType.RECTANGLE` zu `OVAL`, `DIAMOND` oder einem anderen unterstützten Enum‑Wert.
* **Als DOCX statt PDF speichern** – Rufen Sie `doc.save("output/shape.docx")` auf, um das Word‑Format beizubehalten.
* **Mehrere Formen** – Erstellen Sie zusätzliche Formen, indem Sie erneut `builder.insert_shape` aufrufen; jede Form kann ihr eigenes `ShadowEffect` besitzen.

**Pro‑Tipp:** Wenn Sie die Form an einer bestimmten Position platzieren müssen, setzen Sie nach dem Einfügen `rectangle.left` und `rectangle.top`. Das gibt Ihnen pixelgenaue Kontrolle über die Platzierung.

## Fazit

Sie wissen jetzt, wie man **ein leeres Word-Dokument erstellt**, **eine Form in Word einfügt**, **eine äußere Schattenform hinzufügt** und **mit Python als PDF speichert**. Das vollständige Code‑Beispiel demonstriert den End‑zu‑End‑Workflow, und die Erklärungen verdeutlichen, warum jeder API‑Aufruf notwendig ist.

Ab hier können Sie weiterführende Stiloptionen erkunden, Text in die Form einfügen oder mehrere Formen kombinieren, um komplexe Diagramme zu erstellen. Experimentieren Sie mit verschiedenen Schattenparametern, um die visuelle Sprache Ihrer Marke zu treffen, und integrieren Sie diesen Ansatz in größere Dokument‑Generierungs‑Pipelines.

Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform erstellen, Schatten hinzufügen & PDF speichern](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [PDF aus Word erstellen – Vollständiger Python‑Leitfaden mit Aspose.Words](/words/english/python-net/document-conversion/create-pdf-from-word-complete-python-guide-with-aspose-words/)
- [Schatten zu Form in Word mit Aspose.Words hinzufügen – Schritt für Schritt](/words/english/net/programming-with-shapes/add-shadow-to-shape-in-word-with-aspose-words-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}