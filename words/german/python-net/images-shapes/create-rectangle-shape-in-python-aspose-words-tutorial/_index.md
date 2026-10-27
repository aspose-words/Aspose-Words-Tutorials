---
category: general
date: 2026-06-21
description: Erstellen Sie eine Rechteckform in Python mit Aspose.Words. Erfahren
  Sie, wie Sie einer Form einen Schatten hinzufügen, die Füllfarbe der Form festlegen
  und das Dokument in wenigen Minuten als PDF speichern.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- set shape fill color
language: de
og_description: Erstellen Sie ein Rechteck-Shape in Python mit Aspose.Words. Dieser
  Leitfaden zeigt, wie man einem Shape einen Schatten hinzufügt, die Füllfarbe des
  Shapes festlegt und das Dokument als PDF speichert.
og_title: Rechteckform in Python erstellen – Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-21'
  description: Create rectangle shape in Python using Aspose.Words. Learn how to add
    shadow to shape, set shape fill color, and save document as PDF in minutes.
  headline: Create rectangle shape in Python – Aspose.Words tutorial
  type: TechArticle
tags:
- Aspose.Words
- Python
- PDF generation
title: Rechteckform in Python erstellen – Aspose.Words‑Tutorial
url: /de/python/images-shapes/create-rectangle-shape-in-python-aspose-words-tutorial/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Python erstellen – Aspose.Words‑Tutorial

Haben Sie sich schon einmal gefragt, **wie man eine Rechteckform** in einem Word‑Dokument erstellt, während Sie in Python programmieren? Sie sind nicht allein. Viele Entwickler stoßen an ihre Grenzen, wenn sie ein schnelles visuelles Element benötigen – etwa ein farbiger Kasten mit einem dezenten Schatten – und das Ganze anschließend als PDF exportieren wollen.  

In diesem Leitfaden gehen wir Schritt für Schritt durch ein vollständiges, ausführbares Beispiel, das **eine Rechteckform erstellt**, **die Füllfarbe der Form setzt**, **einen Schatten zur Form hinzufügt** und schließlich **das Dokument als PDF speichert**. Keine vagen Verweise, sondern konkreter Code, den Sie noch heute kopieren‑und‑einsetzen können.

## Was Sie benötigen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes auf Ihrem Rechner haben:

- Python 3.8 oder neuer (die hier gezeigte Syntax funktioniert mit jeder aktuellen Version).
- Eine aktive Aspose.Words‑für‑Python‑Lizenz oder eine kostenlose Testversion (die Bibliothek ist reines Python, kein COM‑Interop nötig).
- Einen Text‑Editor oder eine IDE, mit der Sie sich wohlfühlen – VS Code funktioniert hervorragend, aber jede Umgebung reicht aus.

Das war’s. Keine schweren Frameworks, keine zusätzlichen OS‑Abhängigkeiten. Los geht’s.

## Schritt 1: Aspose.Words für Python installieren

Erstmal das Wichtigste. Falls Sie das Paket noch nicht haben, holen Sie es von PyPI:

```bash
pip install aspose-words
```

Warum dieser Schritt wichtig ist: Aspose.Words liefert die Klassen `Document` und `DocumentBuilder`, auf die wir uns verlassen. Ohne die Bibliothek gibt es die späteren Aufrufe – etwa `insert_shape` – nicht, sodass das Skript bereits beim ersten Versuch abstürzt.

> **Pro‑Tipp:** Halten Sie Ihre virtuelle Umgebung sauber. Führen Sie `python -m venv .venv && source .venv/bin/activate` aus, bevor Sie installieren, damit die Bibliothek von den System‑Paketen isoliert bleibt.

## Schritt 2: Ein neues Dokument und einen DocumentBuilder erstellen

Jetzt **erstellen wir die Rechteckform** – aber zuerst benötigen wir eine leere Leinwand.

```python
import aspose.words as aw

# Initialize a new, empty Word document
doc = aw.Document()
# DocumentBuilder lets us add content programmatically
builder = aw.DocumentBuilder(doc)
```

Das Objekt `Document` repräsentiert die gesamte Datei, während `DocumentBuilder` ein praktischer Helfer ist, der weiß, wo sich der Cursor befindet, und an dieser Stelle Elemente einfügen kann. Denken Sie an den Builder wie an einen Stift, der auf die Seite schreibt.

## Schritt 3: Die Rechteckform einfügen

Hier passiert die eigentliche Aktion. Wir **erstellen eine Rechteckform** mit fester Breite und Höhe und positionieren sie auf der Seite.

```python
# Insert a rectangle 200 points wide and 100 points tall
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

Warum ein Rechteck? Es ist die einfachste Form, mit der wir dennoch Füllfarben und Schatten demonstrieren können. Wenn Sie später einen Kreis oder einen Stern benötigen, ersetzen Sie einfach `ShapeType.RECTANGLE` durch einen anderen Enum‑Wert.

## Schritt 4: Füllfarbe der Form setzen

Ein schlichtes weißes Kästchen ist nicht besonders spannend, also **setzen wir die Füllfarbe der Form** auf etwas Sanftes – hellblau funktioniert gut für Berichte.

```python
# Apply a light‑blue background to the rectangle
rectangle.fill_color = aw.Color.light_blue
```

Sie können jedes der vordefinierten `aw.Color`‑Mitglieder (`red`, `green`, `dark_gray` usw.) verwenden oder ein RGB‑Tupel übergeben (`aw.Color.from_argb(255, 30, 144, 255)`). Die Füllfarbe ist das, was der Benutzer sieht, bevor ein Schatten oder ein Rahmen angewendet wird.

## Schritt 5: Schatten zur Form hinzufügen

Jetzt zum visuellen Feinschliff: **Schatten zur Form hinzufügen**. Schatten verleihen Tiefe und lassen das Rechteck auf der Seite hervortreten.

```python
# Grab the shadow format object
shadow = rectangle.shadow_format

# Turn the shadow on
shadow.visible = True
# Choose a dark gray tone for realism
shadow.color = aw.Color.dark_gray
# Blur radius controls softness (5 points is a nice middle ground)
shadow.blur = 5
# Horizontal and vertical offsets shift the shadow relative to the shape
shadow.offset_x = 3
shadow.offset_y = 3
# Slight transparency makes the shadow feel natural
shadow.transparency = 0.2
# Use an outer shadow – you could also try INSET for a different effect
shadow.type = aw.drawing.ShadowType.OUTER
```

**Wie man einen Schatten hinzufügt**? Der obige Code macht genau das, aber wir erklären kurz, warum jede Eigenschaft wichtig ist:

- `visible` – schaltet den Effekt ein/aus.
- `color` – definiert den Farbton; ein dunkles Grau ahmt natürliches Licht nach.
- `blur` – höhere Werte erzeugen einen weicheren Rand.
- `offset_x` / `offset_y` – verschieben den Schatten von der Form weg; passen Sie diese Werte an, um unterschiedliche Lichtwinkel zu simulieren.
- `transparency` – 0 ist undurchsichtig, 1 ist unsichtbar; 0.2 ergibt einen dezenten Eindruck.
- `type` – `OUTER` wirft den Schatten außerhalb der Form, während `INNER` ihn nach innen legen würde.

Falls Sie einen dramatischen Drop‑Shadow benötigen, erhöhen Sie `blur` auf 10‑15 und setzen `offset_x`/`offset_y` auf 6‑8.

## Schritt 6: Das Dokument als PDF speichern

All die Arbeit ist sinnlos, wenn wir das **Dokument nicht als PDF speichern** und teilen können. Aspose.Words macht das mit einer einzigen Zeile:

```python
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Warum PDF? PDFs erhalten das Layout plattformübergreifend, was sie ideal für Berichte, Rechnungen oder jedes druckbare Material macht. Die Methode `save` erkennt automatisch die Dateierweiterung und wählt das passende Format – achten Sie nur darauf, dass der Pfad mit `.pdf` endet.

### Erwartetes Ergebnis

Öffnen Sie die erzeugte Datei `ShapeWithShadow.pdf`. Sie sollten ein hellblaues Rechteck sehen, das nahe dem oberen Rand der ersten Seite zentriert ist, mit einem weichen, dunkelgrauen Schatten, der leicht nach rechts und unten versetzt ist. Die Kanten der Form sind scharf, der Schatten dezent, und die Dateigröße liegt typischerweise unter 100 KB.

## Bonus: Schatten anpassen – Antworten auf „wie man Schatten hinzufügt“

Vielleicht fragen Sie sich: *„Kann ich die Schattenrichtung ändern, ohne die Form zu bewegen?“* Absolut. Die Position des Schattens ist unabhängig von den Koordinaten der Form; passen Sie einfach `offset_x` und `offset_y` an. Positive Werte verschieben den Schatten nach rechts/unten, negative nach links/oben. Für eine Lichtquelle oben links verwenden Sie `offset_x = -3` und `offset_y = -3`.

Eine weitere häufige Frage: *„Was, wenn ich mehrere Schatten auf derselben Form brauche?“* Aspose.Words unterstützt nur einen Schatten pro Form. Wenn Sie geschichtete Effekte benötigen, erstellen Sie eine doppelte Form, versetzen sie leicht und wenden jeweils einen anderen Schatten an. Es ist ein kleiner Hack, aber er funktioniert.

## Vollständiges Skript – Bereit zum Ausführen

Unten finden Sie das komplette, eigenständige Skript. Kopieren Sie es in eine Datei namens `create_rectangle_with_shadow.py` und führen Sie es mit `python create_rectangle_with_shadow.py` aus.

```python
import aspose.words as aw

# ---------- Initialize document ----------
doc = aw.Document()
builder = aw.DocumentBuilder(doc)

# ---------- Insert rectangle ----------
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# ---------- Set fill color ----------
rectangle.fill_color = aw.Color.light_blue

# ---------- Configure shadow ----------
shadow = rectangle.shadow_format
shadow.visible = True
shadow.color = aw.Color.dark_gray
shadow.blur = 5
shadow.offset_x = 3
shadow.offset_y = 3
shadow.transparency = 0.2
shadow.type = aw.drawing.ShadowType.OUTER

# ---------- Save as PDF ----------
output_path = r"YOUR_DIRECTORY/ShapeWithShadow.pdf"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

> **Hinweis:** Ersetzen Sie `YOUR_DIRECTORY` durch einen absoluten oder relativen Pfad, der auf Ihrem Rechner existiert. Wenn der Ordner nicht existiert, wirft Python einen `FileNotFoundError`.

## Häufige Stolperfallen & wie man sie vermeidet

| Problem | Warum es passiert | Lösung |
|---------|-------------------|--------|
| Schatten erscheint nicht | `shadow.visible` bleibt beim Standardwert `False` | Setzen Sie `shadow.visible = True` |
| Form ist unsichtbar | Füllfarbe ist `aw.Color.transparent` oder `None` | Verwenden Sie eine solide Farbe wie `aw.Color.light_blue` |
| PDF ist leer | `doc.save` wurde vergessen oder mit falscher Erweiterung gespeichert | Rufen Sie `doc.save("output.pdf")` auf und prüfen Sie den Pfad |
| Laufzeitfehler `ImportError` | Aspose.Words nicht installiert oder falsche Python‑Umgebung | Führen Sie `pip install aspose-words` in der aktiven venv aus |

## Nächste Schritte – Weitere Formen und Formatierungen erkunden

Jetzt, wo Sie **Rechteckform erstellen** beherrschen, können Sie:

- `ShapeType.RECTANGLE` durch `ShapeType.ELLIPSE` oder `ShapeType.PENTAGON` ersetzen, um andere Geometrien zu testen.
- Text in die Form einfügen, indem Sie `builder.move_to(rectangle.absolute_position)` verwenden und anschließend `builder.writeln("Hello World")` aufrufen.
- Mehrere Formen zu einer Gruppe zusammenfassen mit `group = aw.drawing.GroupShape(doc)` für komplexe Diagramme.
- In andere Formate exportieren, z. B. DOCX (`doc.save("output.docx")`) oder HTML (`doc.save("output.html")`), um zu sehen, wie der Schatten übertragen wird.

All diese Erweiterungen bauen auf denselben Kernkonzepten auf: **Schatten zur Form hinzufügen**, **Füllfarbe der Form setzen** und **Dokument als PDF speichern** (oder in ein anderes Format).

---

### Bildvorschau *(optional)*

![Create rectangle shape with shadow in Python](https://example.com/rectangle-shadow.png "Create rectangle shape with shadow in Python")

*Der Screenshot zeigt das endgültige PDF‑Ergebnis mit einem hellblauen Rechteck und einem dezenten äußeren Schatten.*

---

## Fazit

Wir haben jeden Schritt durchgearbeitet, der nötig ist, um **eine Rechteckform** in Python zu erstellen, eine benutzerdefinierte Füllung anzuwenden, **einen Schatten zur Form hinzuzufügen** und schließlich **das Dokument als PDF zu speichern**. Der Code ist vollständig ausführbar, die Erklärungen decken das *Warum* jeder Eigenschaft ab, und wir haben gängige Edge‑Cases sowie weiterführende Ideen behandelt.

---

## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, damit Sie weitere API‑Funktionen meistern und alternative Implementierungsansätze in Ihren eigenen Projekten erkunden können.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}