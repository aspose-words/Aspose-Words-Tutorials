---
category: general
date: 2026-10-07
description: Erfahren Sie, wie Sie ein Dokument als PDF speichern und dabei eine Rechteckform
  sowie einen benutzerdefinierten Schatten mit Aspose.Words für Python hinzufügen.
  Schritt‑für‑Schritt‑Code enthalten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save document as pdf
- add rectangle shape
- export word to pdf
- set rectangle dimensions
- draw rectangle word
language: de
lastmod: 2026-10-07
og_description: Speichern Sie das Dokument als PDF mit einer benutzerdefinierten Rechteckform
  mithilfe von Aspose.Words für Python. Folgen Sie dem vollständigen Beispiel, um
  zu zeichnen, zu formatieren und Word nach PDF zu exportieren.
og_image_alt: Screenshot of the generated PDF showing the rectangle shape after save
  document as pdf
og_title: Dokument als PDF mit Rechteckform speichern – vollständige Python-Anleitung
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  headline: How to save document as PDF with a custom rectangle shape in Python
  type: TechArticle
- description: Learn how to save document as PDF while adding a rectangle shape and
    custom shadow using Aspose.Words for Python. Step‑by‑step code included.
  name: How to save document as PDF with a custom rectangle shape in Python
  steps:
  - name: Initialize a new blank document
    text: '```python import aspose.words as aw'
  - name: Add rectangle shape to the document
    text: '```python # Create a rectangle shape and attach it to the document. rectangle
      = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)'
  - name: Set rectangle dimensions
    text: '```python # Define width and height in points (1 point = 1/72 inch). rectangle.width
      = 200 # 200 points ≈ 2.78 inches rectangle.height = 100 # 100 points ≈ 1.39
      inches ```'
  - name: (Optional) Apply a visible custom shadow
    text: '```python shadow = rectangle.shadow_format shadow.visible = True # Show
      the shadow shadow.blur = 5.0 # Softness of the shadow edge shadow.distance =
      3.0 # How far the shadow is offset shadow.angle = 45 # Direction in degrees
      shadow.color = aw.drawing.Color.black ```'
  - name: Save document as PDF
    text: '```python output_path = "output/shadow_rectangle.pdf" document.save(output_path)
      print(f"PDF saved to {output_path}") ```'
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
- Word automation
title: Wie man ein Dokument in Python als PDF mit einer benutzerdefinierten Rechteckform
  speichert
url: /de/python/document-conversion/how-to-save-document-as-pdf-with-a-custom-rectangle-shape-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Dokument als PDF mit einer benutzerdefinierten Rechteckform in Python speichert

Wenn Sie ein **Dokument als PDF speichern** müssen, während Sie benutzerdefinierte Grafiken hinzufügen, zeigt Ihnen diese Anleitung, wie es geht. Wir gehen durch das Erstellen einer leeren Word-Datei, das **Zeichnen einer Rechteckform**, das Festlegen ihrer Größe, das Anwenden eines sichtbaren Schattens und schließlich das **Exportieren von Word nach PDF** mit der Aspose.Words für Python-Bibliothek.

Am Ende erhalten Sie ein PDF, das ein perfekt positioniertes Rechteck enthält, bereit für Berichte, Rechnungen oder jedes Dokument‑Automatisierungsszenario. Es werden keine externen Tools benötigt – nur Python und das Aspose.Words-Paket.

## Was Sie benötigen

| Anforderung | Warum es wichtig ist |
|-------------|----------------------|
| Python 3.8+ | Die Aspose.Words für Python API richtet sich an moderne Interpreter. |
| `aspose-words` package (`pip install aspose-words`) | Stellt den im Codebeispielen verwendeten `aw`-Namespace bereit. |
| Basic familiarity with Python and object‑oriented programming | Das Tutorial manipuliert Objekte wie `Document` und `Shape`. |
| Write permission to a folder where the PDF will be saved | Der Schritt `save document as pdf` schreibt eine Datei auf die Festplatte. |

> **Pro tip:** Verwenden Sie eine virtuelle Umgebung (`python -m venv venv`), um Abhängigkeiten zu isolieren.

## Wie man ein Dokument als PDF mit einer Rechteckform speichert

Unten finden Sie ein vollständiges, ausführbares Beispiel. Jeder Schritt wird erklärt, damit Sie **warum** wir die Aktion ausführen, und nicht nur **was** der Code tut, verstehen.

### Schritt 1: Ein neues leeres Dokument initialisieren

```python
import aspose.words as aw

# Create an empty Word document – this is the canvas for our shape.
document = aw.Document()
```

Das Erstellen eines frischen `Document`-Objekts liefert Ihnen eine saubere Seitensammlung. Sie könnten auch ein vorhandenes *.docx* laden, wenn Sie später **Word nach PDF exportieren** möchten, aber ein leeres Dokument hält das Beispiel fokussiert.

### Schritt 2: Rechteckform zum Dokument hinzufügen

```python
# Create a rectangle shape and attach it to the document.
rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

# The shape must be placed inside a paragraph before it appears.
paragraph = document.first_section.body.first_paragraph
paragraph.append_child(rectangle)
```

Der Schritt `add rectangle shape` verwendet `ShapeType.RECTANGLE`. Durch das Anhängen der Form an einen Absatz weiß Aspose.Words, wo sie im endgültigen PDF gerendert werden soll.

### Schritt 3: Rechteckabmessungen festlegen

```python
# Define width and height in points (1 point = 1/72 inch).
rectangle.width = 200   # 200 points ≈ 2.78 inches
rectangle.height = 100  # 100 points ≈ 1.39 inches
```

Das Festlegen expliziter **Rechteckabmessungen** stellt sicher, dass die Form plattformübergreifend konsistent aussieht. Sie können auch `convert_to_inches`-Hilfsfunktionen verwenden, wenn Sie imperiale Einheiten bevorzugen.

### Schritt 4: (Optional) Sichtbaren benutzerdefinierten Schatten anwenden

```python
shadow = rectangle.shadow_format
shadow.visible = True          # Show the shadow
shadow.blur = 5.0              # Softness of the shadow edge
shadow.distance = 3.0          # How far the shadow is offset
shadow.angle = 45              # Direction in degrees
shadow.color = aw.drawing.Color.black
```

Ein Schatten lässt das Rechteck im PDF hervorstechen. Das Flag `shadow.visible` ist erforderlich; ohne es haben die anderen Eigenschaften keine Wirkung.

### Schritt 5: Dokument als PDF speichern

```python
output_path = "output/shadow_rectangle.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Durch Aufrufen von `document.save` mit einer **.pdf**-Erweiterung wird das **save document as pdf** automatisch mit dem integrierten PDF-Renderer von Aspose.Words durchgeführt. Es sind keine zusätzlichen Konvertierungsschritte erforderlich, weshalb diese Methode der empfohlene Weg ist, **Word nach PDF zu exportieren**.

> **Warum das funktioniert:** Aspose.Words schreibt das Layout des Dokuments, einschließlich des Rechtecks und seines Schattens, direkt in den PDF-Stream. Der Vorgang ist verlustfrei und behält die Vektorqualität bei.

## Vollständiger Quellcode (einzelnes Skript)

```python
import aspose.words as aw

def create_pdf_with_rectangle(output_path: str):
    """
    Creates a PDF that contains a single rectangle shape with a custom shadow.
    The function demonstrates:
    • add rectangle shape
    • set rectangle dimensions
    • export Word to PDF (save document as pdf)
    """
    # 1️⃣ Create a new blank document
    document = aw.Document()

    # 2️⃣ Insert a rectangle shape
    rectangle = aw.drawing.Shape(document, aw.drawing.ShapeType.RECTANGLE)

    # 3️⃣ Set the shape's size
    rectangle.width = 200   # points
    rectangle.height = 100  # points

    # 4️⃣ Configure a visible shadow
    shadow = rectangle.shadow_format
    shadow.visible = True
    shadow.blur = 5.0
    shadow.distance = 3.0
    shadow.angle = 45
    shadow.color = aw.drawing.Color.black

    # 5️⃣ Add shape to the first paragraph
    paragraph = document.first_section.body.first_paragraph
    paragraph.append_child(rectangle)

    # 6️⃣ Save the document as PDF
    document.save(output_path)
    print(f"PDF successfully saved to: {output_path}")

if __name__ == "__main__":
    create_pdf_with_rectangle("output/shadow_rectangle.pdf")
```

Das Ausführen dieses Skripts erzeugt `shadow_rectangle.pdf`, das folgendermaßen aussieht:

![Diagramm des erzeugten PDFs, das die Rechteckform nach dem Speichern des Dokuments als PDF zeigt](placeholder-image.png)

*Das PDF enthält eine einzelne Seite mit einem schwarz‑schattierten Rechteck, das in der Mitte des Dokuments zentriert ist.*

## Häufige Fragen und Sonderfälle

| Frage | Antwort |
|----------|--------|
| **Kann ich das Rechteck an einer bestimmten Position platzieren?** | Ja. Setzen Sie `rectangle.left` und `rectangle.top` (in Punkten) vor dem Speichern. |
| **Was, wenn ich mehrere Formen benötige?** | Erstellen Sie zusätzliche `Shape`-Objekte, konfigurieren Sie jedes und hängen Sie sie an denselben oder verschiedene Absätze an. |
| **Beeinflusst der Schatten die PDF-Größe?** | Nur marginal; der Schatten wird als Vektormetadaten gespeichert, nicht als Rasterbild. |
| **Kann ich dies verwenden, um vorhandene *.docx*-Dateien zu konvertieren?** | Absolut. Ersetzen Sie `aw.Document()` durch `aw.Document("input.docx")` und der Rest der Schritte bleibt unverändert. |
| **Gibt es eine Möglichkeit, die Füllfarbe des Rechtecks zu ändern?** | Setzen Sie `rectangle.fill_color = aw.drawing.Color.light_blue` (oder jede `Color`, die Sie bevorzugen). |

## Nächste Schritte

Jetzt, da Sie wissen, wie man **ein Dokument als PDF speichert** mit einem benutzerdefinierten Rechteck, könnten Sie folgendes erkunden:

* **Export Word to PDF** mit Kopf‑ und Fußzeilen sowie Seitenzahlen.  
* **Weitere Zeichenobjekte hinzufügen** (`Ellipse`, `Polygon`) mit derselben `Shape`‑Klasse.  
* **Stapelverarbeitung** eines Ordners mit Word‑Dateien, wobei für jede dieselbe Rechteck‑Überlagerung angewendet wird.  

Diese Erweiterungen folgen dem gleichen Muster: Eine Form erstellen, ihre Eigenschaften konfigurieren und **save document as pdf**.

---

**Zusammenfassung:** Dieses Tutorial zeigte Ihnen, wie man **ein Dokument als PDF speichert** während man **eine Rechteckform hinzufügt**, **Rechteckabmessungen festlegt** und einen benutzerdefinierten Schatten mit Aspose.Words für Python anwendet. Das vollständige Skript ist bereit zum Kopieren, Ausführen und Anpassen an Ihre eigenen Dokument‑Automatisierungspipelines. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Rechteckform erstellen, Schatten hinzufügen & PDF speichern](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Rechteck zu PDF mit Aspose.Words hinzufügen – Schritt‑für‑Schritt‑Anleitung](/words/english/python-net/images-shapes/add-rectangle-to-pdf-with-aspose-words-step-by-step-guide/)
- [Dokument als PDF speichern mit Aspose.Words – Vollständige C#‑Anleitung](/words/english/net/programming-with-pdfsaveoptions/save-document-as-pdf-with-aspose-words-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}