---
category: general
date: 2026-11-18
description: Das Aspose.Words‑Beispiel für Formschatten zeigt, wie man mit Python
  einem Word‑Objekt einen Schatten hinzufügt. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung,
  um das Dokument zu bearbeiten und zu speichern.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words shape shadow example
- python shape shadow
- Aspose.Words for Python
- modify shape shadow
- document manipulation Aspose
language: de
lastmod: 2026-11-18
og_description: Das Aspose.Words-Beispiel für Formschatten demonstriert das Hinzufügen
  eines Schattens zu einer Word‑Form mit Python. Lernen Sie den vollständigen Code,
  warum jeder Schritt wichtig ist, und wie Sie ihn anpassen können.
og_image_alt: Aspose.Words shape shadow example – Word document displaying a shape
  with a shadow applied using Python
og_title: Aspose.Words Beispiel für Formschatten – Python-Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  headline: Aspose.Words shape shadow example in Python
  type: TechArticle
- description: Aspose.Words shape shadow example shows how to add a shadow to a Word
    shape using Python. Follow this step‑by‑step guide to modify and save the document.
  name: Aspose.Words shape shadow example in Python
  steps:
  - name: Expected outcome
    text: Open `output.docx` in Microsoft Word. The first shape you added should now
      display a soft shadow that is offset by 2 pt horizontally and vertically, with
      a blur radius of 5 pt. All other content remains unchanged.
  - name: 'Alternative: Find a shape by name'
    text: 'If your document contains several shapes, you might prefer to locate a
      specific one:'
  - name: Working with multiple shapes
    text: 'If you need to apply the same shadow to every shape, iterate over the node
      collection:'
  - name: Applying a shadow to a specific shape type
    text: You can filter by `ShapeType` (e.g., `aw.ShapeType.IMAGE`). This is useful
      when you only want to affect pictures, not AutoShapes.
  - name: Handling documents without shapes
    text: The script already raises a clear `ValueError` if no shape is found. In
      production code you might log the issue and continue processing other files.
  - name: Compatibility notes
    text: '* The code works with **Aspose.Words for Python via .NET** version 23.10
      and later. * The shadow effect is supported in Word 2007+ (`.docx`). Older formats
      (`.doc`) will lose the effect after conversion.'
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Aspose.Words-Beispiel für Formschatten in Python
url: /de/python/images-shapes/aspose-words-shape-shadow-example-in-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words Shape‑Schatten‑Beispiel in Python

Das Aspose.Words Shape‑Schatten‑Beispiel zeigt, wie man mit Python einen Schatteneffekt zu einer Form in einem Word‑Dokument hinzufügt. In diesem Tutorial erhalten Sie ein vollständiges, ausführbares Skript, das ein Dokument lädt, den Schatten konfiguriert und das Ergebnis speichert.

Das Anwenden eines Schattens auf eine Form ist eine gängige Methode, um die visuelle Hierarchie in Berichten, Broschüren oder Rechnungen zu verbessern. Der untenstehende Code funktioniert mit Aspose.Words for Python via .NET und erfordert keine zusätzlichen Drittanbieter‑Bibliotheken.

## Was Sie lernen werden

* Wie man eine `.docx`‑Datei mit **Aspose.Words for Python** lädt.  
* Wie man die erste Form findet (einschließlich Formen in Tabellen oder Gruppen).  
* Wie man die Unschärfe, den horizontalen Versatz und den vertikalen Versatz des Schattens konfiguriert.  
* Wie man das modifizierte Dokument speichert und dabei den gesamten anderen Inhalt beibehält.  

**Voraussetzungen**

* Python 3.8 oder höher.  
* Aspose.Words for Python via .NET installiert (`pip install aspose-words`).  
* Ein Word‑Dokument (`input.docx`), das mindestens eine Form enthält (z. B. ein Bild, AutoShape oder Textfeld).  

If you need to install the library, run:

```bash
pip install aspose-words
```

## Aspose.Words Shape‑Schatten‑Beispiel – Überblick

Das folgende Skript ist die vollständige Lösung. Es folgt den vier logischen Schritten eines typischen **document manipulation Aspose** Workflows: Laden, Finden, Ändern und Speichern.

```python
import aspose.words as aw

# ----------------------------------------------------------------------
# Step 1: Load the Word document
# ----------------------------------------------------------------------
# Replace YOUR_DIRECTORY with the path that contains input.docx.
doc_path = "YOUR_DIRECTORY/input.docx"
doc = aw.Document(doc_path)

# ----------------------------------------------------------------------
# Step 2: Access the first shape (including descendants)
# ----------------------------------------------------------------------
# NodeType.SHAPE searches for any shape node. The third argument (True)
# tells Aspose.Words to search recursively through all child nodes.
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)

# Verify that a shape was found; raise a clear error if not.
if shape is None:
    raise ValueError("No shape found in the document. Ensure input.docx contains a shape.")

# ----------------------------------------------------------------------
# Step 3: Configure the shape's shadow
# ----------------------------------------------------------------------
# The Shadow object controls visual appearance. Adjust the properties
# to achieve the desired effect.
shape.shadow.blur = 5          # Softness of the shadow (0‑15 is typical)
shape.shadow.offset_x = 2      # Horizontal displacement in points
shape.shadow.offset_y = 2      # Vertical displacement in points

# Optional: Change shadow color or transparency if needed.
# shape.shadow.color = aw.Color.black
# shape.shadow.transparency = 0.5

# ----------------------------------------------------------------------
# Step 4: Save the modified document
# ----------------------------------------------------------------------
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)

print(f"Shadow applied successfully. Saved to {output_path}")
```

### Erwartetes Ergebnis

Öffnen Sie `output.docx` in Microsoft Word. Die erste von Ihnen hinzugefügte Form sollte nun einen weichen Schatten anzeigen, der horizontal und vertikal um 2 pt versetzt ist, mit einem Unschärferadius von 5 pt. Der gesamte andere Inhalt bleibt unverändert.

## Schritt 1: Word‑Dokument laden

Das Laden eines Dokuments ist die erste Operation in jedem **Aspose.Words for Python** Workflow. Die Klasse `Document` analysiert die Datei und erstellt ein In‑Memory‑Objektmodell. Da die Bibliothek auf der .NET‑Plattform arbeitet, kann sie große Dateien effizient verarbeiten.

*Warum das wichtig ist:* Das Dokument einmal zu laden und eine Referenz (`doc`) zu behalten, vermeidet wiederholte I/O‑Vorgänge, was die Leistung verbessert, wenn mehrere Änderungen angewendet werden müssen.

## Schritt 2: Auf die Form zugreifen

Formen können direkte Kinder des Dokumentenkörpers sein oder in Tabellen, Gruppen oder Zeichenflächen verschachtelt sein. Mit `get_child(NodeType.SHAPE, 0, True)` wird rekursiv gesucht und die erste passende Form zurückgegeben.

*Warum das wichtig ist:* Das Flag `True` stellt sicher, dass Sie keine Formen übersehen, die in anderen Knoten versteckt sind. Wenn Sie es weglassen, werden nur Formen der obersten Ebene berücksichtigt, und viele reale Dokumente würden `None` zurückgeben.

### Alternative: Eine Form nach Namen finden

Wenn Ihr Dokument mehrere Formen enthält, möchten Sie möglicherweise eine bestimmte finden:

```python
shape = doc.get_child(aw.NodeType.SHAPE, lambda n: n.name == "MyLogo", True)
```

Dieses Snippet demonstriert eine **python shape shadow**‑Variation, die nach der `name`‑Eigenschaft der Form filtert.

## Schritt 3: Den Schatten der Form konfigurieren

Die `shadow`‑Eigenschaft eines `Shape`‑Objekts bietet Ihnen eine feinkörnige Kontrolle über den visuellen Effekt. Die drei am häufigsten angepassten Attribute sind:

| Property | Typischer Bereich | Visuelle Auswirkung |
|----------|-------------------|---------------------|
| `blur`   | 0 – 15            | Höhere Werte erzeugen einen weicheren Rand. |
| `offset_x` | –10 – 10       | Positive Werte verschieben den Schatten nach rechts. |
| `offset_y` | –10 – 10       | Positive Werte verschieben den Schatten nach unten. |

Sie können auch `color`, `transparency`, `visible` und `style` ändern. Das Beispiel setzt eine moderate Unschärfe und einen leichten Versatz, um den Schatten dezent zu halten.

**Pro‑Tipp:** Wenn eine Form bereits einen Schatten hat, überschreiben die obigen Eigenschaften die bestehenden Einstellungen. Wenn Sie den ursprünglichen Stil beibehalten müssen, lesen Sie die aktuellen Werte, bevor Sie sie ändern.

## Schritt 4: Das modifizierte Dokument speichern

Der Aufruf von `doc.save()` schreibt die In‑Memory‑Darstellung zurück in eine `.docx`‑Datei. Aspose.Words aktualisiert automatisch alle internen Beziehungen, sodass die Ausgabedatei vollständig mit Microsoft Word kompatibel bleibt.

*Warum das wichtig ist:* Das einmalige Speichern am Ende des Prozesses reduziert das Risiko von Dateikorruption und verbessert die Gesamtschnelligkeit, insbesondere beim Verarbeiten vieler Dokumente in einem Batch‑Job.

## Übliche Variationen und Sonderfälle

### Arbeiten mit mehreren Formen

Wenn Sie denselben Schatten auf jede Form anwenden müssen, iterieren Sie über die Knotensammlung:

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    shp.shadow.blur = 5
    shp.shadow.offset_x = 2
    shp.shadow.offset_y = 2
```

### Einen Schatten auf einen bestimmten Formtyp anwenden

Sie können nach `ShapeType` filtern (z. B. `aw.ShapeType.IMAGE`). Dies ist nützlich, wenn Sie nur Bilder und nicht AutoShapes beeinflussen möchten.

```python
for shp in doc.get_child_nodes(aw.NodeType.SHAPE, True):
    if shp.shape_type == aw.ShapeType.IMAGE:
        shp.shadow.blur = 4
```

### Umgang mit Dokumenten ohne Formen

Das Skript wirft bereits einen klaren `ValueError`, wenn keine Form gefunden wird. Im Produktionscode könnten Sie das Problem protokollieren und mit der Verarbeitung anderer Dateien fortfahren.

### Kompatibilitätshinweise

* Der Code funktioniert mit **Aspose.Words for Python via .NET** Version 23.10 und höher.  
* Der Schatteneffekt wird in Word 2007+ (`.docx`) unterstützt. Ältere Formate (`.doc`) verlieren den Effekt nach der Konvertierung.

## Fazit

Dieses **aspose.words shape shadow example** führt Sie durch das Laden einer Word‑Datei, das Finden einer Form, das Konfigurieren ihres Schattens und das Speichern des Ergebnisses mit **Aspose.Words for Python**. Sie haben nun ein wiederverwendbares Muster für jedes **document manipulation Aspose**‑Szenario, das visuelle Verbesserungen beinhaltet.

Als Nächstes könnten Sie erkunden:

* Gradientenfüllungen oder Linienstile zu Formen hinzufügen (`modify shape shadow` und andere visuelle Eigenschaften).  
* Schattenkonfiguration mit Textformatierung kombinieren, um vollständig gestaltete Vorlagen zu erstellen.  
* Den Prozess für eine Stapelverarbeitung von Dokumenten automatisieren, indem Sie `os.listdir` und das oben gezeigte Muster verwenden.

Fühlen Sie sich frei, mit verschiedenen Unschärfe‑Werten, Versätzen und Farben zu experimentieren, um Ihren Markenrichtlinien zu entsprechen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Schatten zu Form in Python hinzufügen – Komplettes Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Wie man einen Schatten auf eine Form in Aspose.Words für Python setzt](/words/english/python-net/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-for-python/)
- [Wie man PNG speichert und einen Schatten zu einer Form mit Aspose.Words hinzufügt](/words/english/python-net/images-shapes/how-to-save-png-and-add-shadow-to-shape-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}