---
category: general
date: 2026-08-17
description: Wie man PNG mit Aspose.Words für Python speichert. Lernen Sie, einem
  Objekt einen Schatten hinzuzufügen, das Dokument als PDF zu speichern und Word in
  PNG zu exportieren – alles in einem Leitfaden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to save png
- add shadow to shape
- save document as pdf
- export word to png
- convert word to pdf
language: de
lastmod: 2026-08-17
og_description: Wie man PNG mit Aspose.Words speichert. Dieses Tutorial zeigt das
  Hinzufügen eines Schattens zu einer Form, das Speichern des Dokuments als PDF und
  den Export von Word nach PNG.
og_image_alt: Screenshot of a Word document with a rectangle shape that has a shadow,
  saved as PNG and PDF
og_title: Wie man PNG speichert und einer Form Schatten hinzufügt mit Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  headline: How to save PNG and add shadow to shape with Aspose.Words
  type: TechArticle
- description: How to save PNG using Aspose.Words for Python. Learn to add shadow
    to shape, save document as PDF and export Word to PNG in one guide.
  name: How to save PNG and add shadow to shape with Aspose.Words
  steps:
  - name: Pro tip
    text: If you need a sharper shadow, reduce `blur`. For a more pronounced offset,
      increase `distance`. The `Shadow` class also exposes `angle` and `transparency`
      for fine‑tuned control.
  - name: 'Optional: higher‑resolution PNG'
    text: '```python png_options = aw.image.PngSaveOptions() png_options.resolution
      = 300 # DPI doc.save("output/high_res_output.png", png_options) ```'
  - name: Expected output
    text: 'Running the script creates three files:'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Image export
title: Wie man PNG speichert und einem Shape Schatten hinzufügt mit Aspose.Words
url: /de/python/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man PNG speichert und einem Shape einen Schatten hinzufügt mit Aspose.Words

Wenn Sie **wie man PNG speichert** aus einer Word‑Datei, bietet Ihnen dieser Leitfaden eine vollständige, ausführbare Lösung. Sie sehen außerdem, wie man **einem Shape einen Schatten hinzufügt**, **ein Dokument als PDF speichert** und **Word nach PNG exportiert**, ohne die Aspose.Words‑Umgebung zu verlassen.

Das Tutorial behandelt alles, was nötig ist, um ein leeres Word‑Dokument in ein PDF und ein PNG‑Bild zu verwandeln, wobei ein einfacher Schatteneffekt auf ein Rechteck‑Shape angewendet wird. Keine externen Werkzeuge sind erforderlich, und der Code funktioniert mit Aspose.Words für Python via .NET 7 oder höher.

## Was Sie erreichen werden

Am Ende dieses Artikels können Sie:

* Ein neues Word‑Dokument programmgesteuert erstellen.  
* Ein Rechteck‑Shape einfügen und einen Schatteneffekt konfigurieren.  
* Dasselbe Dokument als PDF‑Datei speichern.  
* Das Dokument als PNG‑Bild exportieren.  

Diese Schritte beantworten die häufige Frage **wie man PNG speichert**, während sie gleichzeitig **einem Shape einen Schatten hinzufügen** und **ein Dokument als PDF speichern** in einem einzigen Workflow behandeln.

## Voraussetzungen

* Python 3.9 oder neuer.  
* Aspose.Words für Python via .NET installiert (`pip install aspose-words`).  
* Schreibrechte für das Ausgabeverzeichnis, das Sie angeben.  

Falls Sie Aspose.Words noch nicht installiert haben, führen Sie aus:

```bash
pip install aspose-words
```

## Wie man PNG mit Aspose.Words speichert

Der erste wichtige Schritt besteht darin, ein Dokument und einen `DocumentBuilder` zu erstellen. Der Builder bietet Ihnen eine fluente API zum Einfügen von Inhalten wie Shapes, Tabellen oder Text.

```python
import aspose.words as aw

# Create a new blank document
doc = aw.Document()
builder = aw.DocumentBuilder(doc)
```

`aw.Document()` repräsentiert die gesamte Word‑Datei im Speicher. `aw.DocumentBuilder` verweist auf den aktuellen Einfügeort, der zunächst der Anfang des ersten (und einzigen) Abschnitts ist.

## Schatten zum Shape hinzufügen vor dem Export

Ein Shape kann jedes Zeichenobjekt sein – Rechteck, Ellipse oder benutzerdefiniertes Polygon. Hier erstellen wir ein 100 × 100 Punkt‑Rechteck und wenden einen weichen Schatten an.

```python
# Insert a rectangle shape (100x100 points)
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

# Configure a simple shadow
shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Softness of the shadow edges
shape.shadow.distance = 3.0      # Distance from the shape
shape.shadow.color = aw.Color.black
```

Warum den Schatten vor dem Speichern konfigurieren? Aspose.Words rendert den Schatten während der PDF‑ und PNG‑Exportphasen, sodass der visuelle Effekt in beiden Ausgabeformaten erhalten bleibt.

### Profi‑Tipp
Wenn Sie einen schärferen Schatten benötigen, reduzieren Sie `blur`. Für einen stärker ausgeprägten Versatz erhöhen Sie `distance`. Die Klasse `Shadow` stellt außerdem `angle` und `transparency` für fein abgestimmte Kontrolle bereit.

## Dokument als PDF speichern

Ein Word‑Dokument als PDF zu speichern ist ein Einzeiler, sobald der Inhalt fertig ist. Die Konstante `SaveFormat.PDF` teilt Aspose.Words mit, die Konvertierung durchzuführen.

```python
# Save the document as PDF (shadow is rendered in the output)
pdf_path = "output/output.pdf"
doc.save(pdf_path, aw.SaveFormat.PDF)
```

Das resultierende PDF enthält das Rechteck mit dem exakt definierten Schatten. Aspose.Words verarbeitet Vektorgrafiken, sodass die PDF‑Größe modest bleibt.

## Word nach PNG exportieren

Der Export nach PNG erzeugt ein Rasterbild jeder Seite. Standardmäßig verwendet Aspose.Words 96 DPI; Sie können diesen Wert für eine höherauflösende Ausgabe erhöhen, indem Sie ein `PngSaveOptions`‑Objekt übergeben.

```python
# Export the same document as PNG
png_path = "output/output.png"
doc.save(png_path, aw.SaveFormat.PNG)
```

Wenn Sie **Word nach PNG exportieren**, wird jede Seite als separate PNG‑Datei gespeichert. Da unser Beispiel‑Dokument nur eine Seite hat, erscheint nur eine einzige PNG‑Datei.

### Optional: hochauflösendes PNG

```python
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI
doc.save("output/high_res_output.png", png_options)
```

Eine höhere DPI ist nützlich, wenn das PNG für den Druck verwendet wird oder Sie ein gestochen scharfes Thumbnail benötigen.

## Vollständiges Skript – kopieren, einfügen und ausführen

Unten finden Sie das komplette, eigenständige Skript, das jeden im Tutorial beschriebenen Schritt implementiert. Speichern Sie es als `generate_assets.py` und führen Sie es über die Befehlszeile aus.

```python
import os
import aspose.words as aw

# ------------------------------------------------------------------
# 1. Prepare output folder
# ------------------------------------------------------------------
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# ------------------------------------------------------------------
# 2. Create a new blank document and a builder
# ------------------------------------------------------------------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ------------------------------------------------------------------
# 3. Insert a rectangle shape and add a shadow
# ------------------------------------------------------------------
shape = aw.Shape(aw.ShapeType.RECTANGLE, 100, 100)
builder.insert_node(shape)

shape.shadow = aw.Shadow()
shape.shadow.blur = 5.0          # Soft edges
shape.shadow.distance = 3.0      # Offset from shape
shape.shadow.color = aw.Color.black

# ------------------------------------------------------------------
# 4. Save as PDF (demonstrates "save document as pdf")
# ------------------------------------------------------------------
pdf_path = os.path.join(output_dir, "output.pdf")
doc.save(pdf_path, aw.SaveFormat.PDF)

# ------------------------------------------------------------------
# 5. Export as PNG (demonstrates "how to save png")
# ------------------------------------------------------------------
png_path = os.path.join(output_dir, "output.png")
doc.save(png_path, aw.SaveFormat.PNG)

# ------------------------------------------------------------------
# 6. Optional high‑resolution PNG (demonstrates "export word to png")
# ------------------------------------------------------------------
png_options = aw.image.PngSaveOptions()
png_options.resolution = 300  # DPI for sharper output
high_res_png_path = os.path.join(output_dir, "high_res_output.png")
doc.save(high_res_png_path, png_options)

print(f"Files written to {os.path.abspath(output_dir)}")
```

### Erwartete Ausgabe

Beim Ausführen des Skripts werden drei Dateien erstellt:

* `output/output.pdf` – ein PDF mit einem Rechteck, das einen schwarzen Schatten wirft.  
* `output/output.png` – ein 96 DPI PNG‑Rendering derselben Seite.  
* `output/high_res_output.png` – ein 300 DPI PNG für höhere Qualität.

Öffnen Sie eine der Dateien in Ihrem bevorzugten Viewer, um zu überprüfen, dass der Schatten exakt wie definiert erscheint.

## Häufige Fragen und Sonderfälle

**Was passiert, wenn das Ausgabeverzeichnis nicht existiert?**  
Das Skript ruft `os.makedirs(output_dir, exist_ok=True)` auf, wodurch der Ordner automatisch erstellt wird. Das verhindert einen `FileNotFoundError` während der Speicheroperationen.

**Kann ich mehrere Shapes mit unterschiedlichen Schatten hinzufügen?**  
Ja. Erstellen Sie zusätzliche `Shape`‑Objekte, konfigurieren Sie jede `shadow`‑Eigenschaft unabhängig und fügen Sie sie mit `builder.insert_node(shape)` vor dem Speichern ein.

**Wird der Schatten beim Konvertieren in andere Rasterformate (z. B. JPEG) erhalten bleiben?**  
Aspose.Words rendert den Schatten für alle Rasterformate, die von `SaveFormat` unterstützt werden. Sie können `aw.SaveFormat.PNG` durch `aw.SaveFormat.JPEG` ersetzen, und der Schatten wird weiterhin angezeigt.

**Wie unterscheidet sich das von „convert word to pdf“?**  
`convert word to pdf` ist im Wesentlichen dieselbe Operation, die in Schritt 4 durchgeführt wird. Der gleiche `doc.save`‑Aufruf mit `SaveFormat.PDF` übernimmt die Konvertierung intern und bewahrt Layout, Schriftarten und Grafiken wie Schatten.

**Gibt es ein Limit für die Größe von Shapes?**  
Shapes werden in Punkten gemessen (1 pt ≈ 1/72 Zoll). Sehr große Abmessungen können die resultierende Dateigröße erhöhen, aber Aspose.Words setzt keine harte Grenze. Passen Sie die Argumente `width` und `height` beim Erzeugen von `aw.Shape` an Ihr Layout an.

## Fazit

Sie wissen jetzt **wie man PNG speichert** aus einem Word‑Dokument und haben gleichzeitig gelernt, **einem Shape einen Schatten hinzuzufügen**, **ein Dokument als PDF zu speichern** und **Word nach PNG zu exportieren** mit Aspose.Words für Python. Das komplette Skript demonstriert ein sauberes, wiederholbares Muster, das Sie für größere Dokumente, mehrere Seiten oder komplexere Grafikeffekte anpassen können.

Nächste Schritte könnten sein:

* Experimentieren mit anderen `ShapeType`‑Werten (Ellipse, Wolke usw.).  
* Verwendung von  

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [How to Convert DOCX to PNG in Java – Aspose.Words](/words/english/java/document-converting/converting-documents-images/)
- [Save Word Documents as PostScript in Python Using Aspose.Words: A Comprehensive Guide](/words/english/python-net/document-operations/save-docs-as-postscript-using-aspose-words-python/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}