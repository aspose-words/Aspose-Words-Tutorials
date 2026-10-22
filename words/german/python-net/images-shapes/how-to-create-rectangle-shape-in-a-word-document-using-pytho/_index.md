---
category: general
date: 2026-09-30
description: Lernen Sie, wie Sie eine Rechteckform erstellen, der Form einen Schatten
  hinzufügen und das Word‑Dokument mit der Form mithilfe von Aspose.Words für Python
  speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- how to add shape
- apply shadow to shape
- set shadow blur
- save word with shape
language: de
lastmod: 2026-09-30
og_description: Erstelle schnell ein Rechteck in einem Word-Dokument. Dieses Tutorial
  zeigt, wie man eine Form hinzufügt, Schatten auf die Form anwendet, die Schattenweichzeichnung
  einstellt und das Word-Dokument mit der Form speichert.
og_image_alt: Screenshot of a Word document showing a rectangle shape with a soft
  shadow
og_title: Rechteckform in Word mit Python erstellen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Learn how to create rectangle shape, apply shadow to shape, and save
    Word with shape using Aspose.Words for Python.
  headline: How to create rectangle shape in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Word automation
- Shapes
title: Wie man mit Python ein Rechteck in einem Word‑Dokument erstellt
url: /de/python/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Rechteck‑Shape in einem Word‑Dokument mit Python erstellt

Wenn Sie ein **Rechteck‑Shape** in einer Word‑Datei **erstellen** müssen, zeigt Ihnen diese Anleitung eine vollständige, ausführbare Lösung. Sie sehen, wie Sie das Shape hinzufügen, einen Schatten‑Effekt anwenden, die Unschärfe anpassen und schließlich **Word mit Shape speichern**, sodass das Ergebnis in Microsoft Word oder einem kompatiblen Viewer geöffnet werden kann.

Das Beispiel verwendet **Aspose.Words for Python via .NET**, eine Bibliothek, mit der Sie Word‑Dokumente manipulieren können, ohne dass Microsoft Office installiert sein muss. Vorkenntnisse mit der API sind nicht erforderlich – nur Grundkenntnisse in Python.

## Was Sie erreichen werden

- Ein Rechteck in den ersten Abschnitt eines neuen Dokuments einfügen.  
- Einen weichen Schatten konfigurieren, indem Sie Unschärfe, Versatz und Farbe festlegen.  
- Das Dokument auf die Festplatte schreiben und das visuelle Ergebnis überprüfen.

## Voraussetzungen

- Python 3.8 oder neuer.  
- `aspose-words`‑Paket installiert (`pip install aspose-words`).  
- Schreibrechte für das Ausgabeverzeichnis.

## Rechteck‑Shape erstellen und Aussehen konfigurieren

Der erste Schritt besteht darin, ein leeres Dokument zu instanziieren und ein Rechteck‑Shape hinzuzufügen. Das Shape dient als Leinwand für den Schatten‑Effekt.

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Step 1: Create a new blank document
doc = aw.Document()

# Step 2: Add a rectangle shape to the first section
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Optional: Define the shape’s size and position (in points)
shape.width = aw.ConvertUtil.inch_to_point(2)   # 2 inches wide
shape.height = aw.ConvertUtil.inch_to_point(1)  # 1 inch tall
shape.left = aw.ConvertUtil.inch_to_point(1)    # 1 inch from the left margin
shape.top = aw.ConvertUtil.inch_to_point(1)     # 1 inch from the top margin
```

**Warum das wichtig ist:**  
Das Erstellen des Rechtecks liefert Ihnen ein konkretes Objekt (`shape`), das Sie später formatieren können. Durch explizite Abmessungen stellen Sie sicher, dass das Shape auf jeder Plattform gleich aussieht.

## Wie man ein Shape zu einem Word‑Dokument hinzufügt

Obwohl der obige Code das Rechteck bereits hinzufügt, möchten Sie später möglicherweise weitere Shapes (z. B. Kreise, Pfeile) einfügen. Das gleiche Muster gilt: Rufen Sie `append_child` auf dem Body des Dokuments auf und übergeben Sie den gewünschten `ShapeType`.

```python
# Example: Adding a second shape – an ellipse
ellipse = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.ELLIPSE)
)
ellipse.width = aw.ConvertUtil.inch_to_point(1.5)
ellipse.height = aw.ConvertUtil.inch_to_point(1)
ellipse.left = aw.ConvertUtil.inch_to_point(3.5)
ellipse.top = aw.ConvertUtil.inch_to_point(1)
```

**Tipp:** Verwenden Sie die Aufzählung `ShapeType`, um alle unterstützten Shapes zu erkunden. Das hält Ihren Code lesbar und vermeidet Magic Numbers.

## Schatten auf das Shape anwenden und Unschärfe setzen

Ein Schatten verleiht Tiefe und visuelles Interesse. Die Klasse `ShadowEffect` ermöglicht die Steuerung von Unschärfe, Versatz und Farbe. Im Folgenden wenden wir einen weichen schwarzen Schatten auf das Rechteck an.

```python
# Step 3: Configure a shadow effect for the rectangle
shadow = ShadowEffect()
shadow.blur = 5.0          # Sets the softness of the shadow edge
shadow.offset_x = 2.0      # Horizontal displacement from the shape
shadow.offset_y = 2.0      # Vertical displacement from the shape
shadow.color = aw.Color.black

# Step 4: Apply the shadow effect to the shape
shape.shadow = shadow
```

**Warum Unschärfe setzen?**  
`blur` bestimmt, wie diffus der Schatten erscheint. Ein niedriger Wert (z. B. 1.0) erzeugt eine scharfe Kante, während ein höherer Wert (z. B. 5.0) ein sanftes Ausblenden erzeugt, das oft ästhetischer wirkt.

**Randfall:** Wenn Sie `blur` auf 0 setzen, wird der Schatten zu einer festen Silhouette. Einige Viewer könnten dabei Aliasing‑Artefakte erzeugen, daher sollte ein Wert > 0 gewählt werden, um ein glatteres Ergebnis zu erhalten.

## Word mit Shape speichern

Das Persistieren des Dokuments finalisiert alle Änderungen. Die Methode `save` schreibt eine `.docx`‑Datei, die jeder moderne Textverarbeiter öffnen kann.

```python
# Step 5: Save the document to see the result
output_path = "output.docx"   # Adjust the path as needed
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Wenn Sie `output.docx` öffnen, sehen Sie ein Rechteck, das einen Zoll vom oberen linken Rand entfernt ist, mit einem weichen schwarzen Schatten, der um zwei Punkte nach rechts und unten verschoben ist. Die Unschärfe des Schattens lässt das Shape so wirken, als würde es von der Seite abheben.

**Pro‑Tipp:** Wenn Sie viele Dokumente in einer Schleife erzeugen müssen, verwenden Sie dieselbe `Document`‑Instanz und leeren Sie deren Body zwischen den Durchläufen, um den Speicherverbrauch zu reduzieren.

## Häufige Varianten und Fehlersuche

| Situation | Was zu ändern ist | Grund |
|-----------|-------------------|-------|
| Andere Schattenfarbe | `shadow.color = aw.Color.red` | Markenfarben verwenden oder wichtige Shapes hervorheben. |
| Größerer Schattenversatz | `shadow.offset_x`/`offset_y` erhöhen | Tiefe für UI‑Mock‑ups betonen. |
| Kein Schatten | Zeile `shape.shadow = shadow` weglassen | Für minimalistische Berichte nützlich. |
| Export nach PDF statt DOCX | `doc.save("output.pdf")` | PDF ist ideal für reine Verteilung. |

Erscheint das Shape nicht, prüfen Sie, ob Sie es dem richtigen Abschnitt (`get_first_section()`) hinzufügen und ob das Dokument nach den Änderungen gespeichert wurde.

## Vollständiges, ausführbares Beispiel

```python
import aspose.words as aw
from aspose.words.drawing import ShadowEffect

# Create a new blank document
doc = aw.Document()

# Add a rectangle shape
shape = doc.get_first_section().body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
shape.width = aw.ConvertUtil.inch_to_point(2)
shape.height = aw.ConvertUtil.inch_to_point(1)
shape.left = aw.ConvertUtil.inch_to_point(1)
shape.top = aw.ConvertUtil.inch_to_point(1)

# Configure and apply a shadow
shadow = ShadowEffect()
shadow.blur = 5.0
shadow.offset_x = 2.0
shadow.offset_y = 2.0
shadow.color = aw.Color.black
shape.shadow = shadow

# Save the document
output_path = "output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Das Ausführen des Skripts erzeugt `output.docx`, das das Rechteck mit einem weichen Schatten enthält. Öffnen Sie die Datei in Microsoft Word, um zu bestätigen, dass der visuelle Effekt der Beschreibung entspricht.

## Fazit

Sie wissen jetzt, wie man **ein Rechteck‑Shape erstellt**, **ein Shape zu einem Word‑Dokument hinzufügt**, **einen Schatten auf das Shape anwendet**, **die Schatten‑Unschärfe setzt** und schließlich **Word mit Shape speichert** – und das mit Aspose.Words for Python. Das gleiche Muster lässt sich auf andere Shape‑Typen, Farben und Effekte ausweiten, sodass Sie die Grafik in Dokumenten vollständig kontrollieren können, ohne Office‑Automatisierung zu benötigen.

**Nächste Schritte**

- Experimentieren Sie mit `Shape.fill`, um Farbverläufe oder Bild‑Hintergründe hinzuzufügen.  
- Verwenden Sie `Paragraph`‑Objekte, um Text innerhalb des Rechtecks zu platzieren.  
- Kombinieren Sie mehrere Shapes, um komplexe Diagramme zu erstellen, und exportieren Sie anschließend nach PDF für die Verteilung.  

Passen Sie den Code gern an Ihre eigenen Reporting‑ oder Templating‑Bedürfnisse an und teilen Sie Ihre Ergebnisse in den Kommentaren!

## Was Sie als Nächstes lernen sollten

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren Projekten erkunden können.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}