---
category: general
date: 2026-06-24
description: Erstellen Sie ein Rechteck-Shape in Python mit Aspose.Words, lernen Sie,
  wie Sie dem Shape einen Schatten hinzufügen, den Schattenwinkel einstellen und das
  Dokument in wenigen Minuten als PDF speichern.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shape shadow
- set shadow angle
language: de
og_description: Erstellen Sie eine Rechteckform in Python, fügen Sie der Form einen
  Schatten hinzu, setzen Sie den Schattenwinkel und speichern Sie das Dokument als
  PDF mit Aspose.Words. Folgen Sie dieser Schritt‑für‑Schritt‑Anleitung.
og_title: Rechteckform in Python erstellen – Vollständiges Aspose.Words‑Tutorial
schemas:
- author: Aspose
  dateModified: '2026-06-24'
  description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  headline: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  type: TechArticle
- description: Create rectangle shape in Python with Aspose.Words, learn how to add
    shadow to shape, set shadow angle, and save document as PDF in minutes.
  name: Create Rectangle Shape in Python – Complete Aspose.Words Guide
  steps:
  - name: What if I need a different shape?
    text: Aspose.Words supports many `ShapeType` values (ellipse, star, callout, etc.).
      Simply replace `aw.drawing.ShapeType.RECTANGLE` with the desired enum, like
      `aw.drawing.ShapeType.ELLIPSE`.
  - name: Can I add multiple shadows?
    text: The API exposes only one `ShadowFormat` per shape, but you can simulate
      multiple shadows by duplicating the shape, offsetting each copy, and adjusting
      transparency.
  - name: How do I change the shadow color to match my brand?
    text: Just set `shadow.color` to any `aw.drawing.Color`. For a brand blue, use
      `aw.drawing.Color.from_argb(255, 0, 120, 215)`.
  - name: What about saving as DOCX instead of PDF?
    text: Replace `document.save(pdf_path)` with `document.save("output/shadowed_rectangle.docx")`.
      The shadow rendering is preserved across both formats.
  - name: Does the shadow work on older PDF viewers?
    text: Aspose.Words renders the shadow as a vector effect, which is widely supported.
      However, very old viewers might flatten the effect; testing on your target audience’s
      devices is always a good habit.
  type: HowTo
tags:
- Aspose.Words
- Python
- PDF generation
title: Rechteckform in Python erstellen – Vollständiger Aspose.Words Leitfaden
url: /de/python/images-shapes/create-rectangle-shape-in-python-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechteckform in Python erstellen – Vollständiger Aspose.Words Leitfaden

Haben Sie sich jemals gefragt, wie man **create rectangle shape** in einem Word-Dokument mit Python erstellt? Vielleicht benötigen Sie ein fettgedrucktes Hinweisfeld, einen visuellen Hinweis für ein Diagramm oder einfach ein schickes Rechteck für einen Bericht. Wie auch immer, Sie sind an der richtigen Stelle gelandet. In diesem Tutorial führen wir Sie durch den gesamten Prozess – vom Einfügen des Rechtecks über das Hinzufügen eines dezenten Schattens, das Anpassen des Schattenwinkels bis hin zum **save document as PDF**, damit Sie es mit jedem teilen können.

Wir verwenden **Aspose.Words for Python via .NET**, eine leistungsstarke Bibliothek, mit der Sie Word‑Dateien manipulieren können, ohne Word selbst zu öffnen. Am Ende dieses Leitfadens können Sie die Frage *„how to add shape shadow“* selbstbewusst beantworten und Sie haben ein sofort einsatzbereites Skript, das Sie in jedes Projekt einbinden können.

---

## Was Sie benötigen

- **Python 3.8+** auf Ihrem Rechner installiert.  
- **Aspose.Words for Python via .NET** (`aspose-words` package). Installieren Sie es mit:

  ```bash
  pip install aspose-words
  ```

- Ein beschreibbarer Ordner, in dem das erzeugte PDF gespeichert wird.  
- (Optional) Eine IDE oder ein Texteditor – VS Code funktioniert hervorragend.

Das war's. Keine zusätzlichen DLLs, keine Office-Installation, nur ein einziges pip‑Paket.

## Schritt 1: Dokument und Builder einrichten

Das Erste, was Sie tun müssen, ist **create rectangle shape**‑freundliche Objekte zu erstellen: ein `Document` und ein `DocumentBuilder`. Denken Sie an den Builder wie an Ihren Stift; er zeichnet alles für Sie.

```python
import aspose.words as aw

# Initialize a new blank document
document = aw.Document()

# DocumentBuilder gives us a convenient way to add content
builder = aw.DocumentBuilder(document)
```

> **Warum das wichtig ist:** Das `Document`‑Objekt repräsentiert die gesamte .docx‑Datei, während der `DocumentBuilder` Methoden wie `insert_shape` bereitstellt, die das Zeichnen von Formen zum Kinderspiel machen.

## Schritt 2: Das Rechteck einfügen

Jetzt, wo wir einen Builder haben, können wir endlich **create rectangle shape**. Die Methode `insert_shape` benötigt drei Argumente: den Formtyp, die Breite und die Höhe. Wir verwenden eine Breite von 200 pt und eine Höhe von 100 pt für ein gutes Verhältnis.

```python
# Insert a rectangle with a width of 200 points and a height of 100 points
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)
```

An diesem Punkt haben Sie erfolgreich **create rectangle shape** in Ihrem Dokument erstellt. Wenn Sie das erzeugte DOCX öffnen (das machen wir später), sehen Sie ein einfaches Rechteck dort, wo der Cursor war.

## Schritt 3: Auf das Schattenformatierungsobjekt zugreifen

Um **add shadow to shape** zu erreichen, müssen wir zunächst das Schattenformat der Form abrufen. Jede Form in Aspose.Words verfügt über die Eigenschaft `shadow_format`, die alle schattenbezogenen Einstellungen bereitstellt.

```python
# Grab the shadow formatting object for later tweaks
shadow = rectangle.shadow_format
```

Mit der `shadow`‑Referenz können wir Sichtbarkeit, Unschärfe, Abstand, Winkel, Farbe und Transparenz umschalten – alles in wenigen Codezeilen.

## Schritt 4: Schatten aktivieren und Aussehen konfigurieren

Hier passiert die Magie. Wir werden **add shadow to shape**, es leicht unscharf machen, ein wenig versetzen, die Richtung festlegen (der **set shadow angle** Teil) und ihm einen halbtransparenten schwarzen Farbton geben.

```python
# Turn the shadow on
shadow.visible = True

# Soften the edges – a blur radius of 8 points looks natural
shadow.blur_radius = 8.0

# Push the shadow away from the rectangle by 5 points
shadow.distance = 5.0

# Set the direction of the light source – 45 degrees creates a diagonal drop
shadow.angle = 45

# Choose a color; black works well for most documents
shadow.color = aw.drawing.Color.black

# Make the shadow 30 % transparent for a subtle effect
shadow.transparency = 0.3
```

> **Profi‑Tipp:** Wenn Sie jemals einen dramatischeren Effekt benötigen, erhöhen Sie `blur_radius` oder verringern Sie `transparency`. Umgekehrt kann ein scharfer, vollständig undurchsichtiger Schatten mit `blur_radius = 0` und `transparency = 0` erzielt werden.

## Schritt 5: Dokument als PDF speichern

Wir haben **create rectangle shape**, wir haben **add shadow to shape**, und jetzt werden wir **save document as PDF**, damit das Ergebnis auf jedem Gerät identisch aussieht. Aspose.Words macht das zu einer Einzeiler‑Anweisung.

```python
# Define where you want the PDF to land
output_path = "output/shadowed_rectangle.pdf"

# Save the whole document (including the rectangle with its shadow) as PDF
document.save(output_path)
print(f"PDF saved to {output_path}")
```

Das Ausführen des Skripts erzeugt `shadowed_rectangle.pdf` im Ordner `output`. Öffnen Sie es mit einem beliebigen PDF‑Betrachter und Sie sehen ein klares Rechteck mit einem weichen, 45‑Grad‑Schatten – genau das, was wir konfiguriert haben.

## Vollständiges funktionierendes Beispiel

Unten finden Sie das komplette, sofort ausführbare Skript, das alle oben genannten Schritte kombiniert. Kopieren Sie es in eine Datei namens `create_rectangle_with_shadow.py` und führen Sie `python create_rectangle_with_shadow.py` aus.

```python
import aspose.words as aw
import os

# Ensure the output directory exists
output_dir = "output"
os.makedirs(output_dir, exist_ok=True)

# 1️⃣ Initialize document and builder
document = aw.Document()
builder = aw.DocumentBuilder(document)

# 2️⃣ Insert the rectangle shape (200 pt × 100 pt)
rectangle = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 200, 100)

# 3️⃣ Access shadow formatting
shadow = rectangle.shadow_format

# 4️⃣ Configure shadow – visible, blurred, offset, angled, colored, semi‑transparent
shadow.visible = True
shadow.blur_radius = 8.0          # softer edges
shadow.distance = 5.0            # how far the shadow sits from the shape
shadow.angle = 45                # direction in degrees – this is the **set shadow angle** step
shadow.color = aw.drawing.Color.black
shadow.transparency = 0.3        # 30 % transparent

# 5️⃣ Save the document as PDF
pdf_path = os.path.join(output_dir, "shadowed_rectangle.pdf")
document.save(pdf_path)

print(f"✅ PDF created at: {pdf_path}")
```

**Erwartete Ausgabe:** Eine PDF‑Datei, die ein einzelnes Rechteck mit einem sanften, diagonalen Schatten zeigt. Keine zusätzlichen Seiten, keine versteckten Artefakte – nur die von uns erstellte Form.

## Häufige Fragen & Sonderfälle

### Was, wenn ich eine andere Form benötige?

Aspose.Words unterstützt viele `ShapeType`‑Werte (Ellipse, Stern, Callout usw.). Ersetzen Sie einfach `aw.drawing.ShapeType.RECTANGLE` durch das gewünschte Enum, z. B. `aw.drawing.ShapeType.ELLIPSE`.

### Kann ich mehrere Schatten hinzufügen?

Die API stellt pro Form nur ein `ShadowFormat` bereit, aber Sie können mehrere Schatten simulieren, indem Sie die Form duplizieren, jede Kopie versetzen und die Transparenz anpassen.

### Wie ändere ich die Schattenfarbe, um meiner Marke zu entsprechen?

Setzen Sie einfach `shadow.color` auf ein beliebiges `aw.drawing.Color`. Für ein Marken‑Blau verwenden Sie `aw.drawing.Color.from_argb(255, 0, 120, 215)`.

### Was ist mit dem Speichern als DOCX statt PDF?

Ersetzen Sie `document.save(pdf_path)` durch `document.save("output/shadowed_rectangle.docx")`. Die Schattenrendering wird in beiden Formaten beibehalten.

### Funktioniert der Schatten in älteren PDF‑Betrachtern?

Aspose.Words rendert den Schatten als Vektoreffekt, der breit unterstützt wird. Sehr alte Betrachter könnten den Effekt jedoch flach darstellen; Tests auf den Geräten Ihrer Zielgruppe sind stets empfehlenswert.

## Tipps zur Verfeinerung Ihres PDFs

- **Add a border:** `rectangle.line_format.width = 1.5` und setzen Sie eine Farbe für eine klare Kontur.  
- **Center the rectangle:** Verwenden Sie `builder.move_to_document_start()` vor dem Einfügen, dann `builder.paragraph_format.alignment = aw.ParagraphAlignment.CENTER`.  
- **Combine with text:** Fügen Sie nach dem Rechteck ein `TextFragment` ein, um es zu beschriften, z. B. `"Important Section"`.

Diese kleinen Anpassungen können ein einfaches Rechteck in ein poliertes Hinweisfeld verwandeln, das in Berichten, Angeboten oder E‑Books professionell wirkt.

## Fazit

Sie haben nun ein solides, durchgängiges Rezept, um **create rectangle shape** in Python zu **add shadow to shape**, **set shadow angle** und **save document as PDF** mit Aspose.Words zu erstellen. Die Schritte sind einfach, der Code ist vollständig eigenständig, und Sie haben gesehen, warum jede Zeile wichtig ist – vom Initialisieren des Dokuments bis zum Verfeinern des finalen PDFs.

Als Nächstes könnten Sie **how to add shape shadow** zu komplexeren Zeichnungen erkunden, mit Farbverläufen experimentieren oder Tabellen in Ihren Formen erzeugen. Die Bibliothek unterstützt außerdem das Verknüpfen von Formen mit Lesezeichen, was für interaktive PDFs praktisch sein kann.

Haben Sie eine Variante ausprobiert? Teilen Sie sie in den Kommentaren oder stellen Sie weitere Fragen. Viel Spaß beim Programmieren und genießen Sie das Hinzufügen dieser zusätzlichen Tiefe zu Ihren Dokumenten! 

![Rectangle shape with shadow – example of create rectangle shape in Python](/images/rectangle-shadow.png)


## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige funktionierende Codebeispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, zusätzliche API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}