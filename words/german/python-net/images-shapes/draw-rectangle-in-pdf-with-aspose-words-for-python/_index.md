---
category: general
date: 2026-08-07
description: Zeichnen Sie ein Rechteck in einer PDF mit Aspose.Words für Python und
  lernen Sie, wie Sie einer Form einen Schatten hinzufügen, den Schatten der Form
  konfigurieren und das Dokument als PDF speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle in pdf
- add shadow to shape
- save document as pdf
- configure shape shadow
language: de
lastmod: 2026-08-07
og_description: Rechteck in PDF mit Aspose.Words für Python zeichnen. Dieses Tutorial
  zeigt, wie man einem Objekt Schatten hinzufügt, den Schatten des Objekts konfiguriert
  und das Dokument als PDF speichert, um professionelle Dokumente zu erstellen.
og_image_alt: PDF page showing a rectangle shape with a visible shadow created by
  Aspose.Words for Python
og_title: Rechteck in PDF mit Aspose.Words für Python zeichnen – Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Draw rectangle in PDF using Aspose.Words for Python and learn how to
    add shadow to shape, configure shape shadow, and save document as PDF.
  headline: Draw rectangle in PDF with Aspose.Words for Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF
- Shape
- Shadow
title: Rechteck in PDF mit Aspose.Words für Python zeichnen
url: /de/python/images-shapes/draw-rectangle-in-pdf-with-aspose-words-for-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteck in PDF mit Aspose.Words für Python zeichnen

Wenn Sie **ein Rechteck in PDF** in Python zeichnen müssen, bietet Ihnen diese Anleitung eine komplette, sofort ausführbare Lösung. Sie sehen genau, wie Sie **einem Shape Schatten hinzufügen**, diesen Schatten konfigurieren und schließlich **das Dokument als PDF speichern** für Verteilung oder Archivierung.

Ein schattiertes Rechteck zu erstellen ist ein häufiges Bedürfnis für Berichte, Rechnungen oder visuelle Anmerkungen. Am Ende dieses Tutorials besitzen Sie ein einzelnes Skript, das ein PDF mit einem Rechteck und einem realistischen Schatten erzeugt, und Sie wissen, wie Sie Größe, Farbe und Versatz an jedes Design anpassen können.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie folgendes haben:

* Python 3.8+ installiert.
* Das Aspose.Words for Python via .NET‑Paket (`aspose-words`) – Installation mit:

```bash
pip install aspose-words
```

* Schreibrechte für den Ordner, in dem Sie das PDF speichern möchten.

Keine zusätzlichen Bibliotheken sind nötig; Aspose.Words übernimmt die Shape‑Erstellung, Schattenkonfiguration und den PDF‑Export intern.

## Schritt 1: Neues leeres Dokument erstellen (draw rectangle in PDF – initialize)

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert die gesamte PDF‑Datei und bietet einen Container für Abschnitte, Absätze und Shapes.

```python
import aspose.words as aw

# Create an empty Word document – it will become a PDF later
doc = aw.Document()
```

**Warum das wichtig ist:** Aspose.Words behandelt die PDF‑Erstellung als Konvertierung aus einem Word‑Dokumentmodell, daher beginnen wir mit einem `Document`, obwohl die endgültige Ausgabe ein PDF ist.

## Schritt 2: Ein Rechteck‑Shape in den Dokumentenkörper einfügen

Ein Rechteck ist ein spezieller `ShapeType`. Wir fügen es dem Body des ersten Abschnitts hinzu, wodurch beim Speichern als PDF automatisch eine neue Seite erzeugt wird.

```python
# Append a rectangle shape to the first section's body
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)

# Set the rectangle's dimensions (points = 1/72 inch)
rectangle.width = 200   # 200 pt ≈ 2.78 in
rectangle.height = 100  # 100 pt ≈ 1.39 in

# Optional: give the shape some visible text
rectangle.text = "Shadow demo"
```

**Erklärung:** Die Eigenschaften `width` und `height` steuern die visuelle Größe des Shapes im PDF. Das Hinzufügen von Text erleichtert die Überprüfung des Rechtecks während des Tests.

## Schritt 3: Schatten zum Shape hinzufügen – aktivieren und anpassen

Jetzt schalten wir den Schatteneffekt ein und feintunen sein Aussehen. Hier kommt das Schlüsselwort **add shadow to shape** zum Einsatz.

```python
# Access the shape's shadow effect object
shadow = rectangle.shadow_effect

# Make the shadow visible
shadow.visible = True

# Configure blur radius (pt) – higher values produce a softer edge
shadow.blur = 8

# Set the distance (offset) from the shape in points
shadow.distance = 5

# Define the direction of the shadow in degrees (0 = right, 90 = down)
shadow.angle = 45

# Choose a shadow color – black works for most documents
shadow.color = aw.drawing.Color.black
```

**Warum den Shape‑Schatten konfigurieren?** Das Anpassen von `blur`, `distance` und `angle` ermöglicht die Simulation realistischer Beleuchtung, was die Lesbarkeit und visuelle Hierarchie in erzeugten PDFs verbessert.

## Schritt 4: Dokument als PDF speichern – Endergebnis

Nachdem Rechteck und Schatten definiert sind, ist der letzte Schritt, das Word‑Dokument nach PDF zu exportieren. Damit ist die Anforderung **save document as pdf** erfüllt.

```python
# Define the output path – replace YOUR_DIRECTORY with an actual folder
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)
print(f"PDF saved to {output_path}")
```

Wenn Sie `shadow_rectangle.pdf` öffnen, sehen Sie eine einzelne Seite mit einem grau umrandeten Rechteck mit dem Titel „Shadow demo“ und einem klaren, diagonalen Schatten.

### Erwartetes Ergebnis

* Eine PDF‑Datei namens `shadow_rectangle.pdf`.
* Eine Seite mit einem Rechteck von 200 pt × 100 pt.
* Einen sichtbaren Schatten, versetzt um 5 pt bei einem Winkel von 45°, unscharf gestellt mit 8 pt.

## Schritt 5: Varianten und Sonderfälle erkunden (optional)

Im Folgenden finden Sie gängige Anpassungen, die Sie in realen Projekten benötigen könnten:

| Variante | Code‑Snippet | Wann verwenden |
|-----------|--------------|-----------------|
| **Anderer Shape‑Typ** (z. B. Ellipse) | `aw.drawing.ShapeType.OVAL` statt `RECTANGLE` | Für abgerundete Grafiken oder Badges |
| **Benutzerdefinierte Schattenfarbe** | `shadow.color = aw.drawing.Color.from_argb(255, 100, 100, 100)` | Wenn ein grauer oder markenspezifischer Schatten nötig ist |
| **Mehrere Shapes** | Wiederholen Sie den Shape‑Erstellungsblock und passen Sie `left`/`top` an | Zum Aufbau komplexer Diagramme |
| **Kein Text im Shape** | Entfernen Sie `rectangle.text = "..."` | Wenn das Shape rein dekorativ ist |
| **Höhere DPI‑Ausgabe** | `doc.save(output_path, aw.SaveFormat.PDF, aw.PdfSaveOptions())` mit entsprechenden `PdfSaveOptions` für Bildqualität | Für druckfertige PDFs |

**Pro‑Tipp:** Setzen Sie immer `shadow.visible = True`, bevor Sie andere Eigenschaften anpassen; sonst werden die Änderungen stillschweigend ignoriert.

## Komplettes Skript – kopieren, einfügen und ausführen

```python
import aspose.words as aw

# 1️⃣ Create a new blank document
doc = aw.Document()

# 2️⃣ Add a rectangle shape
rectangle = doc.first_section.body.append_child(
    aw.drawing.Shape(doc, aw.drawing.ShapeType.RECTANGLE)
)
rectangle.width = 200          # width in points
rectangle.height = 100         # height in points
rectangle.text = "Shadow demo"

# 3️⃣ Configure a visible shadow effect
shadow = rectangle.shadow_effect
shadow.visible = True
shadow.blur = 8                # blur radius (pt)
shadow.distance = 5            # offset distance (pt)
shadow.angle = 45              # direction (degrees)
shadow.color = aw.drawing.Color.black

# 4️⃣ Save the document as a PDF
output_path = "YOUR_DIRECTORY/shadow_rectangle.pdf"
doc.save(output_path)

print(f"PDF successfully created at: {output_path}")
```

Führen Sie das Skript in Ihrem Terminal oder Ihrer IDE aus. Ersetzen Sie `YOUR_DIRECTORY` durch einen echten Ordnerpfad, z. B. `"/tmp"` oder `"C:\\Users\\Me\\Documents"`.

## Fazit

Sie wissen jetzt, wie man **ein Rechteck in PDF** mit Aspose.Words für Python **zeichnet**, **einem Shape Schatten hinzufügt**, **den Shape‑Schatten konfiguriert** und **das Dokument als PDF speichert**. Das vollständige Beispiel demonstriert jeden Schritt von der Dokumenterstellung bis zum finalen Export, und die optionalen Varianten zeigen, wie der Code für komplexere Szenarien angepasst werden kann.

Als Nächstes könnten Sie:

* Weitere Shape‑Typen hinzufügen (`ShapeType.LINE`, `ShapeType.ELLIPSE`).
* Farbverläufe oder Rahmen anwenden, um die visuelle Attraktivität zu steigern.
* `PdfSaveOptions` nutzen, um Schriftarten einzubetten oder die Bildkompression zu steuern.

Experimentieren Sie gern mit den Parametern, um Ihre Marken‑ oder Designrichtlinien zu erfüllen. Viel Spaß beim PDF‑Scripting!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [PDF-Lesezeichen optimieren mit Aspose.Words für Python](/words/english/python-net/performance-optimization/optimize-pdf-bookmarks-aspose-words-python/)
- [PDF‑Laden optimieren – Bilder überspringen mit Aspose.Words für Python](/words/hindi/python-net/performance-optimization/optimize-pdf-loading-python-aspose-words-skip-images/)
- [Aspose Words Python PDF‑Manipulation](/words/hongkong/python-net/document-operations/aspose-words-python-pdf-manipulation/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}