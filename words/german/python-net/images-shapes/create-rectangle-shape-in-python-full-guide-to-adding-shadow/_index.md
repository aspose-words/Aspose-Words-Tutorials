---
category: general
date: 2026-05-04
description: Lernen Sie, wie Sie eine Rechteckform erstellen, wie Sie Formen mit Schatten
  hinzufügen, die Schattenfarbe ändern, den Schattenabstand festlegen und das Dokument
  mit Aspose.Words für Python als PDF speichern.
draft: false
keywords:
- create rectangle shape
- how to add shape
- change shadow color
- save document as pdf
- set shadow distance
language: de
og_description: Erstellen Sie ein Rechteck mit Aspose.Words für Python, lernen Sie,
  wie Sie eine Form hinzufügen, die Schattenfarbe ändern, den Schattenabstand festlegen
  und das Dokument als PDF speichern.
og_title: Rechteckform erstellen – Schatten hinzufügen, Farbe ändern & als PDF speichern
tags:
- Aspose.Words
- Python
- PDF generation
title: Rechteckform in Python erstellen – Vollständige Anleitung zum Hinzufügen von
  Schatten und Speichern als PDF
url: /de/python/images-shapes/create-rectangle-shape-in-python-full-guide-to-adding-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckige Form erstellen – Komplettes Tutorial für Python‑Entwickler

Haben Sie schon einmal **eine rechteckige Form** in einem Word‑Dokument erstellen müssen und sich gefragt, wie Sie ihr einen eleganten Schatten geben? Vielleicht bauen Sie einen Berichtsgenerator und das visuelle Finish ist wichtig – besonders wenn das Endergebnis ein PDF ist. Die gute Nachricht: Mit Aspose.Words für Python können Sie nicht nur **Formen hinzufügen**, sondern auch jede Schatten‑Eigenschaft anpassen, von der Farbe bis zum Abstand, und dann **das Dokument als PDF speichern** – alles in einem reibungslosen Ablauf.

In diesem Leitfaden gehen wir den gesamten Prozess Schritt für Schritt durch. Sie sehen den genauen Code, den Sie kopieren‑und‑einfügen können, verstehen *warum* jede Zeile wichtig ist und erhalten ein paar Tipps zum Umgang mit Sonderfällen (wie transparente Schatten oder nicht‑standardmäßige DPI). Am Ende können Sie **eine rechteckige Form erstellen**, deren Schatten anpassen und ein scharfes PDF exportieren – ganz ohne Schwitzen.

## Voraussetzungen

- Python 3.8+ auf Ihrem Rechner installiert.  
- Aspose.Words für Python via `pip install aspose-words`.  
- Grundlegende Kenntnisse in objektorientiertem Python (nichts Besonderes).  

Wenn Sie bereits eine virtuelle Umgebung eingerichtet haben, führen Sie einfach den Installationsbefehl aus und Sie können loslegen.

## Schritt 1: Dokument und Builder initialisieren

Bevor Sie **Formen hinzufügen** können, benötigen Sie ein leeres Dokument zum Arbeiten. Die Klasse `Document` repräsentiert die gesamte Datei, und `DocumentBuilder` ist Ihr Pinsel.

```python
import aspose.words as aw

# Step 1: Create a new document and a DocumentBuilder to edit it
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

*Warum das wichtig ist:* `Document` enthält alle Abschnitte, Seiten und Ressourcen. `DocumentBuilder` bietet Ihnen eine fluente API, um Inhalte genau dort einzufügen, wo Sie sie benötigen – denken Sie an einen Cursor in einem Textverarbeitungsprogramm.

## Schritt 2: Das Rechteck einfügen

Jetzt fügen wir tatsächlich **eine Form hinzu**. Die Methode `insert_shape` benötigt den Formtyp und ihre Abmessungen (in Punkten). Hier wählen wir ein 200 × 100 pt‑Rechteck und geben ihm eine hellblaue Füllung.

```python
# Step 2: Insert a rectangle shape and give it a light‑blue fill
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE,  # shape type
    200,                            # width in points
    100)                            # height in points
rectangle_shape.fill_color = aw.Color.light_blue
```

*Pro‑Tipp:* Wenn die Form mit bestehendem Text ausgerichtet werden soll, verwenden Sie `builder.move_to` vor dem Einfügen oder passen Sie die Eigenschaften `left`/`top` nach der Erstellung an.

## Schritt 3: Schatten aktivieren

Eine Form ohne Schatten wirkt flach. Um **den Schattenabstand festzulegen** und den Effekt sichtbar zu machen, holen Sie das Schatten‑Format und aktivieren es.

```python
# Step 3: Access the shape's shadow format and make the shadow visible
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
```

*Warum dieser Schritt:* Das Schatten‑Format ist ein separates Objekt; das Setzen von `visible` ist das Erste, was Sie tun müssen, sonst werden alle anderen Schatten‑Eigenschaften ignoriert.

## Schritt 4: Schatten gestalten – Farbe, Weichheit, Abstand, Richtung

Hier passiert die Magie. Wir werden **die Schattenfarbe ändern**, den Weichzeichner‑Radius anpassen, festlegen, wie weit der Schatten vom Rechteck entfernt liegt, und ihn um 45° drehen.

```python
# Step 4: Configure the appearance of the shadow
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER   # outer shadow
rectangle_shadow.blur_radius = 10.0                    # blur amount (pixels)
rectangle_shadow.distance = 5.0                        # distance from the shape
rectangle_shadow.direction = 45.0                     # angle in degrees
rectangle_shadow.color = aw.Color.gray                 # shadow colour
```

*Erklärung der einzelnen Eigenschaften:*

| Property | Was sie bewirkt | Typische Werte |
|----------|----------------|----------------|
| `style` | Bestimmt, ob der Schatten *inner* oder *outer* ist. | `OUTER` (am häufigsten) |
| `blur_radius` | Steuert die Weichheit; höher = unschärferer Rand. | 0–20 px üblich |
| `distance` | Wie weit der Schatten von der Form versetzt ist. | 0–10 pt für dezent, >10 für dramatisch |
| `direction` | Winkel der Lichtquelle, im Uhrzeigersinn von der x‑Achse gemessen. | 0‑360° |
| `color` | Schattenfarbe. | Beliebiges `aw.Color` (z. B. `gray`, `dark_red`) |

*Randfall:* Wenn Sie `distance` auf `0` setzen, liegt der Schatten direkt unter der Form und verdeckt praktisch die Füllung. Halten Sie den Wert über `0`, um einen sichtbaren Versatz zu erhalten.

## Schritt 5: Dokument als PDF speichern

Abschließend **speichern wir das Dokument als PDF**. Aspose.Words rastert den Schatten automatisch, sodass das PDF exakt wie die Word‑Ansicht aussieht.

```python
# Step 5: Save the document as a PDF with the shadowed shape
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

*Warum PDF?* PDFs bewahren das Layout plattformübergreifend, was sie perfekt für Berichte, Rechnungen oder andere druckbare Artefakte macht.

---

![Rechteck mit Schatten erstellen](https://example.com/images/rectangle-shadow.png){: .align-center alt="Beispiel für ein Rechteck mit Schatten"}

*Das obige Bild zeigt die endgültige PDF‑Ausgabe – ein hellblaues Rechteck mit einem weichen grauen äußeren Schatten, genau wie konfiguriert.*

## Häufige Fragen & Varianten

### Was tun, wenn ich einen **transparenten** Schatten brauche?

Setzen Sie den Alpha‑Kanal der Schattenfarbe:

```python
transparent_gray = aw.Color.from_argb(128, 0, 0, 0)  # 50% opacity black
rectangle_shadow.color = transparent_gray
```

### Kann ich denselben Schatten auf mehrere Formen anwenden?

Ja. Extrahieren Sie das `ShadowFormat` einer Form und weisen Sie es einer anderen zu:

```python
another_shape = builder.insert_shape(aw.drawing.ShapeType.ELLIPSE, 150, 150)
another_shape.shadow_format = rectangle_shadow.clone()
```

### Wie ändere ich den Schatten für einen **anderen Formtyp**?

Alle Formtypen teilen dieselben `ShadowFormat`‑Eigenschaften, sodass Sie denselben Konfigurationsblock wiederverwenden können – ersetzen Sie einfach `ShapeType.RECTANGLE` durch `ShapeType.OVAL`, `ShapeType.TRIANGLE` usw.

### Was ist mit **hochauflösenden PDFs** für den Druck?

Geben Sie `PdfSaveOptions` mit einer höheren DPI an:

```python
options = aw.saving.PdfSaveOptions()
options.image_resolution = 300  # 300 DPI for print quality
document.save(output_path, options)
```

## Zusammenfassung

Wir haben alles behandelt, was Sie benötigen, um **eine rechteckige Form zu erstellen**, **Formen hinzuzufügen**, deren **Schattenfarbe** anzupassen, **den Schattenabstand festzulegen** und schließlich **das Dokument als PDF zu speichern**. Das komplette, ausführbare Skript sieht so aus:

```python
import aspose.words as aw

# Initialise document
document = aw.Document()
builder = aw.DocumentBuilder(document)

# Insert rectangle shape
rectangle_shape = builder.insert_shape(
    aw.drawing.ShapeType.RECTANGLE, 200, 100)
rectangle_shape.fill_color = aw.Color.light_blue

# Enable and style shadow
rectangle_shadow = rectangle_shape.shadow_format
rectangle_shadow.visible = True
rectangle_shadow.style = aw.drawing.ShadowStyle.OUTER
rectangle_shadow.blur_radius = 10.0
rectangle_shadow.distance = 5.0
rectangle_shadow.direction = 45.0
rectangle_shadow.color = aw.Color.gray

# Save as PDF
output_path = "YOUR_DIRECTORY/ShadowedShape.pdf"
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Führen Sie das Skript aus, öffnen Sie die resultierende `ShadowedShape.pdf` und Sie sehen ein scharfes Rechteck mit einem dezenten grauen Schatten – genau das, was Sie von einem professionell formatierten Bericht erwarten würden.

## Was kommt als Nächstes?

- **Weitere Formtypen erkunden** (`ShapeType.OVAL`, `ShapeType.LINE`), um Ihre Dokumente zu bereichern.  
- **Mehrere Schatten kombinieren**, indem Sie Formen schichten; Sie können sogar einen „Glow“-Effekt erzeugen, indem Sie einen inneren Schatten mit einer hellen Farbe verwenden.  
- **Batch‑Verarbeitung automatisieren**: Durchlaufen Sie eine Sammlung von Datenzeilen, erzeugen Sie pro Zeile eine Form und fügen Sie alles zu einem einzigen PDF zusammen.  
- **Integration mit anderen Aspose‑Bibliotheken** (z. B. Aspose.Slides), falls Sie dieselbe Visualisierung nach PowerPoint exportieren müssen.

Experimentieren Sie gern – ändern Sie den `blur_radius`, spielen Sie mit `direction` oder tauschen Sie `gray` gegen eine markenspezifische Farbe aus. Die API ist so flexibel, dass ein paar Anpassungen die visuelle Wirkung dramatisch verändern können.

Haben Sie Fragen oder ein kniffliges Szenario? Hinterlassen Sie einen Kommentar unten oder besuchen Sie die Aspose‑Community‑Foren. Viel Spaß beim Coden und genießen Sie die schön beschatteten Rechtecke!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}