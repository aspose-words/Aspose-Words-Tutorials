---
category: general
date: 2026-08-11
description: Wie man ein Diagramm in einem Word‑Dokument mit Python gestaltet – Word‑Dokument
  mit Python laden und vordefinierten Diagrammstil schnell anwenden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to style chart
- load word document python
- apply predefined chart style
- apply chart style word
language: de
lastmod: 2026-08-11
og_description: Wie man ein Diagramm in einem Word-Dokument mit Python gestaltet.
  Erfahren Sie, wie Sie ein Word-Dokument mit Python laden, einen vordefinierten Diagrammstil
  anwenden und die aktualisierte Datei speichern.
og_image_alt: Screenshot of Python code applying a chart style to a Word document
og_title: Wie man Diagramme in Word mit Python gestaltet – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-08-11'
  description: How to style chart in a Word document using Python – load Word document
    python and apply predefined chart style quickly.
  headline: How to style chart in a Word document using Python
  type: TechArticle
tags:
- Aspose.Words
- Python
- Chart styling
- Word automation
title: Wie man ein Diagramm in einem Word‑Dokument mit Python formatiert
url: /de/python/formatting-styles/how-to-style-chart-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Diagramm in einem Word-Dokument mit Python formatieren

Wenn Sie ein **Diagramm formatieren** in einer Word-Datei benötigen, zeigt Ihnen dieses Tutorial die genauen Schritte. Am Ende der ersten beiden Sätze wissen Sie, wie Sie ein Word-Dokument mit Python laden, ein Diagramm abrufen und einen vordefinierten Diagrammstil anwenden. Diese Lösung funktioniert mit der Aspose.Words for Python-Bibliothek und erfordert keine manuelle Bearbeitung des Dokuments.

Sie lernen, wie Sie **Word‑Dokument mit Python laden**, die erste Diagrammform auswählen, einen integrierten Stil festlegen und die geänderte Datei speichern. Der Leitfaden behandelt auch häufige Fallstricke, wie den Umgang mit Dokumenten ohne Diagramme und die Auswahl der richtigen Stil‑Enumeration. Keine externen Werkzeuge sind über das Aspose.Words‑Paket hinaus erforderlich.

## Diagramm in einem Word-Dokument mit Python formatieren

Das Anwenden eines Stils auf ein Diagramm ist ein einzeiliger Vorgang, sobald Sie ein `Chart`‑Objekt haben. Die Bibliothek stellt die `ChartStyle`‑Enumeration bereit, die Dutzende vordefinierter Darstellungen enthält (Style 1 … Style 50). In diesem Abschnitt setzen wir **Style 5**, Sie können jedoch den Enum‑Wert durch jeden Stil ersetzen, der Ihren Designrichtlinien entspricht.

```python
import aspose.words as aw

# Load the Word document that contains a chart
doc = aw.Document("YOUR_DIRECTORY/input.docx")

# Retrieve the first chart shape in the document
chart_shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
chart = chart_shape.as_chart()

# Apply a predefined chart style (Style 5) to the chart
chart.style = aw.drawing.ChartStyle.STYLE_5

# Save the modified document
doc.save("YOUR_DIRECTORY/output.docx")
```

**Warum das funktioniert:**  
* `aw.Document` analysiert die .docx‑Datei und erstellt ein Objektmodell.  
* `get_child(..., aw.NodeType.SHAPE, ...)` findet die erste Form, die den Diagramm‑Container darstellt.  
* `as_chart()` castet die Form zu einem `Chart`‑Objekt und stellt die Eigenschaft `style` bereit.  
* Durch Zuweisen von `ChartStyle.STYLE_5` wird Aspose.Words angewiesen, das visuelle Thema des Diagramms durch die vordefinierte Definition zu ersetzen.

Die Ausgabedatei `output.docx` enthält dieselben Daten wie das Original, jedoch wird das Diagramm mit dem ausgewählten Stil dargestellt.

## Word-Dokument in Python laden

Bevor Sie ein Diagramm formatieren können, müssen Sie **Word‑Dokument mit Python** korrekt **laden**. Der Konstruktor `aw.Document` akzeptiert einen Pfad zu einer .docx-, .doc- oder .rtf‑Datei. Stellen Sie sicher, dass der Dateipfad absolut ist oder dass das Arbeitsverzeichnis auf den Speicherort Ihrer Eingabedatei zeigt.

```python
# Example: absolute path on Windows
doc_path = r"C:\Projects\Charts\input.docx"
doc = aw.Document(doc_path)
```

**Tipps zum Laden von Dokumenten:**

* Verwenden Sie rohe Zeichenketten (`r"..."`) unter Windows, um das Escapen von Backslashes zu vermeiden.  
* Überprüfen Sie mit `os.path.isfile(doc_path)`, ob die Datei existiert, um Laufzeitfehler zu vermeiden.  
* Falls das Dokument geschützte Abschnitte enthält, geben Sie das Passwort über `aw.LoadOptions` an.

```python
import os
if not os.path.isfile(doc_path):
    raise FileNotFoundError(f"Document not found: {doc_path}")
```

## Vordefinierten Diagrammstil anwenden

Der Schritt **vordefinierten Diagrammstil anwenden** ist der Ort, an dem die visuelle Transformation stattfindet. Aspose.Words definiert die `ChartStyle`‑Enum mit Werten von `STYLE_1` bis `STYLE_50`. Jeder Stil entspricht einem Satz von Farben, Markern und Linienformaten, die den integrierten Diagramm‑Themes von Microsoft Office ähneln.

```python
# Choose any style from STYLE_1 to STYLE_50
desired_style = aw.drawing.ChartStyle.STYLE_12
chart.style = desired_style
```

**Wann ein vordefinierter Stil verwendet werden sollte:**  

* Sie benötigen ein einheitliches Erscheinungsbild über mehrere Dokumente hinweg.  
* Die Diagrammdaten ändern sich häufig, aber das visuelle Thema soll unverändert bleiben.  
* Sie möchten manuelle Formatierung in der Word‑Benutzeroberfläche vermeiden.

**Randfall – Dokument ohne Diagramme:**  
Wenn `doc.get_child(aw.NodeType.SHAPE, 0, True)` `None` zurückgibt, löst das Skript einen `AttributeError` aus. Schützen Sie sich davor, indem Sie den Knotentyp vor dem Casten prüfen.

```python
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart found in the document.")
chart = shape.as_chart()
```

## Das formatierte Dokument speichern

Nach dem Formatieren ist das Persistieren der Änderungen unkompliziert. Die Methode `doc.save` schreibt das aktualisierte Objektmodell zurück in eine .docx‑Datei. Sie können auch in andere Formate wie PDF, HTML oder PNG exportieren, falls die nachgelagerte Verwendung eine andere Darstellung erfordert.

```python
output_path = "YOUR_DIRECTORY/output.docx"
doc.save(output_path)          # Saves as DOCX
doc.save("output.pdf")         # Optional: export to PDF
```

**Verifizierung:** Öffnen Sie `output.docx` in Microsoft Word. Das Diagramm sollte das neue Theme anzeigen, und alle Datenreihen behalten ihre ursprünglichen Werte. Wenn Sie nach PDF exportieren, bleibt der visuelle Stil identisch.

## Häufige Fallstricke und praktische Tipps

| Problem | Ursache | Lösung |
|-------|-------|-----|
| `AttributeError: 'NoneType' object has no attribute 'as_chart'` | Keine Diagrammform bei Index 0 gefunden | Verwenden Sie `doc.get_child(..., 0, True)` innerhalb eines try/except‑Blocks oder iterieren Sie über alle Formen mit `doc.get_child_nodes(aw.NodeType.SHAPE, True)`. |
| Falscher Stil angewendet | Verwendung eines Enum‑Werts, der nicht existiert (z. B. `STYLE_0`) | Wählen Sie einen gültigen `ChartStyle`‑Wert (1‑50). |
| Datei nicht gespeichert | Ausgabepfad verweist auf ein schreibgeschütztes Verzeichnis | Stellen Sie sicher, dass der Prozess Schreibrechte hat oder ändern Sie das Verzeichnis. |
| Diagramm verschwindet nach dem Speichern | Die Form war kein Diagramm (z. B. ein Bild) | Überprüfen Sie `shape.has_chart` vor dem Casten. |

**Pro‑Tipp:** Cachen Sie den am häufigsten verwendeten `ChartStyle` in einer Konstanten, sodass Sie ihn in mehreren Skripten wiederverwenden können, ohne jedes Mal das Enum einzugeben.

```python
DEFAULT_CHART_STYLE = aw.drawing.ChartStyle.STYLE_5
chart.style = DEFAULT_CHART_STYLE
```

## Vollständiges End‑zu‑Ende‑Beispiel

Unten finden Sie das vollständige, ausführbare Skript, das alle oben besprochenen bewährten Methoden integriert. Ersetzen Sie `YOUR_DIRECTORY` durch den tatsächlichen Ordner, der Ihre Word‑Dateien enthält.

```python
import os
import aspose.words as aw

# ----------------------------------------------------------------------
# Configuration
# ----------------------------------------------------------------------
INPUT_PATH = r"YOUR_DIRECTORY/input.docx"
OUTPUT_PATH = r"YOUR_DIRECTORY/output.docx"
DEFAULT_STYLE = aw.drawing.ChartStyle.STYLE_5

# ----------------------------------------------------------------------
# Load the document
# ----------------------------------------------------------------------
if not os.path.isfile(INPUT_PATH):
    raise FileNotFoundError(f"Input file not found: {INPUT_PATH}")

doc = aw.Document(INPUT_PATH)

# ----------------------------------------------------------------------
# Locate the first chart
# ----------------------------------------------------------------------
shape = doc.get_child(aw.NodeType.SHAPE, 0, True)
if shape is None or not shape.has_chart:
    raise ValueError("No chart shape found in the document.")

chart = shape.as_chart()

# ----------------------------------------------------------------------
# Apply the predefined chart style
# ----------------------------------------------------------------------
chart.style = DEFAULT_STYLE

# ----------------------------------------------------------------------
# Save the modified document
# ----------------------------------------------------------------------
doc.save(OUTPUT_PATH)

print(f"Chart style applied successfully. Saved to {OUTPUT_PATH}")
```

**Erwartetes Ergebnis:**  
Wenn Sie `output.docx` öffnen, zeigt das erste Diagramm das visuelle Theme, das durch `STYLE_5` definiert ist. Alle Datenpunkte, Achsen und Legenden bleiben unverändert, was zeigt, dass die Formatierung unabhängig von den zugrunde liegenden Daten ist.

## Fazit

Sie wissen jetzt, **wie man ein Diagramm** in einem Word‑Dokument mit Python formatieren kann. Das Tutorial behandelte, wie man **Word‑Dokument mit Python lädt**, die Diagrammform abruft, **vordefinierten Diagrammstil anwendet** und die aktualisierte Datei speichert. Mit diesen Bausteinen können Sie die Berichtserstellung automatisieren, Corporate Branding durchsetzen oder Dutzende von Dokumenten stapelweise verarbeiten, ohne manuellen Aufwand.

Als Nächstes können Sie weitere Diagramm‑Anpassungen erkunden, z. B. das Ändern von Serienfarben, das Hinzufügen von Datenbeschriftungen oder das Exportieren des Diagramms als Bild. Werfen Sie einen Blick in die Aspose.Words‑Dokumentation zu Themen wie **Diagrammstil in Word anwenden**, **Diagrammdaten manipulieren** und **Dokumentkonvertierung**, um Ihre Automatisierungsfähigkeiten zu erweitern.

Fühlen Sie sich frei, mit verschiedenen `ChartStyle`‑Werten zu experimentieren und dieses Skript in größere Pipelines zu integrieren, die Word‑Berichte aus Datenbanken oder APIs erzeugen. Viel Spaß beim Coden!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Spalten‑Diagramm in ein Word‑Dokument einfügen](/words/english/net/programming-with-charts/insert-column-chart/)
- [Einfaches Spalten‑Diagramm in ein Word‑Dokument einfügen](/words/english/net/programming-with-charts/insert-simple-column-chart/)
- [Flächen‑Diagramm in ein Word‑Dokument einfügen](/words/english/net/programming-with-charts/insert-area-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}