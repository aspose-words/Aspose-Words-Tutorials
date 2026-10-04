---
category: general
date: 2026-10-04
description: Wie man ein Dokument in Python erstellt und einem Shape mit Aspose.Words
  einen Schatten hinzufügt. Erfahren Sie, wie Sie die Schattenfarbe festlegen, ein
  Rechteck-Shape einfügen und den äußeren Schatten anpassen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create document
- add shadow to shape
- set shadow color
- insert rectangle shape
- how to add shadow
language: de
lastmod: 2026-10-04
og_description: Wie man ein Dokument in Python erstellt und einer Form einen Schatten
  hinzufügt. Dieser Leitfaden zeigt, wie man die Schattenfarbe festlegt, ein Rechteck
  einfügt und mithilfe von Aspose.Words einen äußeren Schatten anwendet.
og_image_alt: Python code inserting a rectangle shape with a visible shadow into a
  Word document
og_title: Wie man ein Dokument mit einer Rechteckform und einem Schatten in Python
  erstellt
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  headline: How to create document with a rectangle shape and shadow in Python
  type: TechArticle
- description: How to create document in Python and add shadow to shape using Aspose.Words.
    Learn to set shadow color, insert rectangle shape, and customize outer shadow.
  name: How to create document with a rectangle shape and shadow in Python
  steps:
  - name: Why does the shadow sometimes appear invisible?
    text: The shadow is only rendered if `shadow.visible` is set to `True` **and**
      the shape’s `wrap_type` allows it to be displayed. An inline shape works reliably;
      floating shapes may require additional layout adjustments.
  - name: How can I change the shadow color to match a brand palette?
    text: 'Replace `aw.drawing.Color.black` with a custom RGB value:'
  - name: What if I need the shape to appear behind text?
    text: Set the wrap type to `WrapType.BEHIND` and adjust the `z_order_position`
      if necessary. Keep in mind that some viewers may render behind‑text shapes differently.
  - name: Can I apply the same shadow settings to multiple shapes?
    text: Yes. Create a helper function that configures the shadow and call it for
      each shape you insert. This promotes code reuse and ensures consistent styling.
  type: HowTo
tags:
- Aspose.Words
- Python
- Word automation
title: Wie man ein Dokument mit einer Rechteckform und einem Schatten in Python erstellt
url: /de/python/images-shapes/how-to-create-document-with-a-rectangle-shape-and-shadow-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Dokument mit einer Rechteckform und Schatten in Python erstellt

Wenn Sie **ein Dokument erstellen** möchten, das ein gestaltetes Rechteck enthält, bietet diese Anleitung eine vollständige Lösung. Sie sehen, wie Sie **einem Shape Schatten hinzufügen**, die Farbe des Schattens festlegen und dessen Versatz sowie Weichzeichnung steuern – alles mit Aspose.Words für Python. Am Ende des Tutorials können Sie eine `.docx`‑Datei erzeugen, die professionell aussieht und bereit zur Verteilung ist.

Die nachfolgenden Schritte decken alles ab, von der Installation der Bibliothek bis zur Anpassung des Schattens. Keine externe Dokumentation ist nötig; der Code kann kopiert, ausgeführt und an eigene Projekte angepasst werden. Sie lernen außerdem, wie Sie **ein Rechteck‑Shape einfügen**, einen **äußeren Schattenstil** wählen und häufige Stolperfallen wie unsichtbare Schatten oder falsche Umbruch‑Einstellungen behandeln.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Python 3.8 oder neuer installiert.
* Eine aktive Aspose.Words für Python Lizenz (oder einen kostenlosen Evaluierungsschlüssel).
* Grundlegende Kenntnisse im Python‑Scripting.
* Zugriff auf einen Dateisystem‑Ort, an dem das erzeugte Dokument gespeichert werden kann.

Sie können das SDK mit pip installieren:

```bash
pip install aspose-words
```

## Schritt 1: Bibliothek importieren und ein neues leeres Dokument erstellen

Ein neues Dokument zu erstellen ist die erste Aktion in jedem Word‑Automatisierungsszenario. Der Konstruktor `aw.Document()` liefert Ihnen eine leere Datei, die Sie mit Text, Bildern oder Shapes füllen können.

```python
import aspose.words as aw

# Create a new blank document
document = aw.Document()
builder = aw.DocumentBuilder(document)
```

Das Objekt `DocumentBuilder` vereinfacht das Einfügen von Inhalten. Es behält die aktuelle Cursor‑Position bei, sodass Sie Elemente nacheinander hinzufügen können, ohne Abschnitte manuell verwalten zu müssen.

## Schritt 2: Ein Rechteck‑Shape mit gewünschter Größe einfügen

Ein Rechteck‑Shape dient als Container für visuelle Elemente. Sie können seine Breite und Höhe in Punkten (1 pt ≈ 1/72 in) festlegen.

```python
# Insert a rectangle shape that is 150 pt wide and 80 pt tall
rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)
```

Zu diesem Zeitpunkt hat das Shape keine visuelle Gestaltung, daher erscheint es nur als einfache Kontur. Die nächsten Schritte verleihen ihm Tiefe und Farbe.

## Schritt 3: Das Shape so einstellen, dass es inline mit dem umgebenden Text fließt

Wenn ein Shape **inline** ist, verhält es sich wie ein Zeichen in einem Absatz. Das sorgt dafür, dass das Rechteck dort bleibt, wo Sie es im Dokumentlayout erwarten.

```python
# Make the shape inline so it follows the text flow
rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE
```

Falls Sie bevorzugen, dass das Shape über dem Text schwebt, könnten Sie `WrapType.SQUARE` oder `WrapType.TOP_BOTTOM` verwenden, aber für die meisten Berichte sorgt ein Inline‑Shape für ein vorhersehbares Layout.

## Schritt 4: Den Schatten sichtbar machen und seine Farbe wählen

Ein Schatten, der nicht sichtbar ist, bringt keinen visuellen Nutzen. Das Flag `visible` aktiviert den Effekt, und die Eigenschaft `color` bestimmt seine Farbgebung. Schwarz liefert eine klassische, dezente Tiefe.

```python
# Enable the shadow and set its color to black
rectangle_shape.shadow.visible = True
rectangle_shape.shadow.color = aw.drawing.Color.black
```

Sie können `aw.drawing.Color.black` durch jede andere Farbe ersetzen, etwa `aw.drawing.Color.gray` oder einen benutzerdefinierten RGB‑Wert (`aw.drawing.Color.from_argb(255, 128, 128, 128)`).

## Schritt 5: Versatz und Weichzeichnung des Schattens festlegen, um Tiefe zu erzeugen

Der Versatz bestimmt, wie weit der Schatten vom Shape verschoben wird, während der Weichzeichnungsradius die Kanten verwischt. Kleine Werte erzeugen einen scharfen Schatten; größere Werte erzeugen ein weicheres Aussehen.

```python
# Horizontal and vertical offset of 5 pt each
rectangle_shape.shadow.offset_x = 5
rectangle_shape.shadow.offset_y = 5

# Blur radius of 3 pt for a gentle feather
rectangle_shape.shadow.blur = 3
```

Experimentieren Sie mit diesen Zahlen, um Ihren Gestaltungsrichtlinien zu entsprechen. Für einen starken Drop‑Shadow können Sie sowohl Versatz als auch Weichzeichnung erhöhen.

## Schritt 6: Einen äußeren Schattenstil wählen

Aspose.Words bietet mehrere Schattenstile, wie `INNER`, `OUTER` und `PERSPECTIVE`. Der **äußere** Stil platziert den Schatten außerhalb der Shape‑Grenze, was für ein sauberes, professionelles Erscheinungsbild ideal ist.

```python
# Apply an outer shadow style
rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

Wenn Sie einen dramatischeren Effekt wünschen, probieren Sie `ShadowStyle.PERSPECTIVE` – er fügt eine dreidimensionale Neigung hinzu.

## Schritt 7: Das Dokument mit dem geformten Schatten speichern

Das Speichern finalisiert die Datei und schreibt alle Formatierungen auf die Festplatte. Wählen Sie ein Verzeichnis, für das Sie Schreibrechte besitzen, und geben Sie der Datei einen aussagekräftigen Namen.

```python
# Save the document to the desired location
output_path = "output/ShapeWithShadow.docx"
document.save(output_path)
print(f"Document saved to {output_path}")
```

Das Ausführen des Skripts erzeugt eine Word‑Datei, die ein Rechteck mit einem sichtbaren, farbigen Schatten enthält. Öffnen Sie die Datei in Microsoft Word oder LibreOffice, um das Ergebnis zu überprüfen.

## Vollständig ausführbares Beispiel

Im Folgenden finden Sie das komplette Skript, das jeden besprochenen Schritt integriert. Kopieren Sie den Code in eine Datei namens `create_shadowed_shape.py` und führen Sie ihn mit `python create_shadowed_shape.py` aus.

```python
import aspose.words as aw
import os

def main():
    # Ensure the output directory exists
    output_dir = "output"
    os.makedirs(output_dir, exist_ok=True)

    # Step 1: Create a new blank document
    document = aw.Document()
    builder = aw.DocumentBuilder(document)

    # Step 2: Insert a rectangle shape of the desired size
    rectangle_shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 150, 80)

    # Step 3: Set the shape to be inline with the text flow
    rectangle_shape.wrap_type = aw.drawing.WrapType.INLINE

    # Step 4: Make the shadow visible and choose its color
    rectangle_shape.shadow.visible = True
    rectangle_shape.shadow.color = aw.drawing.Color.black

    # Step 5: Define the shadow's offset and blur to give it depth
    rectangle_shape.shadow.offset_x = 5   # horizontal offset in points
    rectangle_shape.shadow.offset_y = 5   # vertical offset in points
    rectangle_shape.shadow.blur = 3       # blur radius in points

    # Step 6: Choose an outer shadow style
    rectangle_shape.shadow.style = aw.drawing.ShadowStyle.OUTER

    # Step 7: Save the document with the shaped shadow
    output_path = os.path.join(output_dir, "ShapeWithShadow.docx")
    document.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    main()
```

**Erwartete Ausgabe**

Wenn Sie `ShapeWithShadow.docx` öffnen, sehen Sie ein einzelnes Rechteck, das zentriert auf der Seite steht. Das Rechteck wird von einem dezenten schwarzen Schatten nach unten‑rechts versetzt, leicht verwischt, um Tiefe zu erzeugen. Der Schatten respektiert den äußeren Stil, sodass er nicht in das Innere des Rechtecks eingreift.

## Häufige Fragen und Sonderfälle

### Warum erscheint der Schatten manchmal unsichtbar?

Der Schatten wird nur gerendert, wenn `shadow.visible` auf `True` gesetzt ist **und** der `wrap_type` des Shapes die Anzeige zulässt. Ein Inline‑Shape funktioniert zuverlässig; schwebende Shapes können zusätzliche Layout‑Anpassungen erfordern.

### Wie kann ich die Schattenfarbe an eine Markenpalette anpassen?

Ersetzen Sie `aw.drawing.Color.black` durch einen benutzerdefinierten RGB‑Wert:

```python
rectangle_shape.shadow.color = aw.drawing.Color.from_argb(255, 0, 120, 215)  # corporate blue
```

### Was, wenn das Shape hinter dem Text erscheinen soll?

Setzen Sie den Wrap‑Typ auf `WrapType.BEHIND` und passen Sie bei Bedarf die `z_order_position` an. Beachten Sie, dass einige Viewer hinter‑Text‑Shapes unterschiedlich rendern können.

### Kann ich dieselben Schatten‑Einstellungen auf mehrere Shapes anwenden?

Ja. Erstellen Sie eine Hilfsfunktion, die den Schatten konfiguriert, und rufen Sie sie für jedes eingefügte Shape auf. Das fördert Code‑Wiederverwendung und sorgt für konsistente Gestaltung.

```python
def apply_shadow(shape, color=aw.drawing.Color.black, offset=5, blur=3):
    shape.shadow.visible = True
    shape.shadow.color = color
    shape.shadow.offset_x = offset
    shape.shadow.offset_y = offset
    shape.shadow.blur = blur
    shape.shadow.style = aw.drawing.ShadowStyle.OUTER
```

## Fazit

Sie wissen jetzt **wie man ein Dokument erstellt**, das ein Rechteck‑Shape mit einem individuell angepassten Schatten enthält, und zwar mit Aspose.Words für Python. Das Tutorial behandelte das Einfügen eines Rechtecks, das Inline‑Setzen des Shapes, das Aktivieren des Schattens, das Festlegen von Farbe, Versatz, Weichzeichnung und Stil sowie das abschließende Speichern der Datei.

Ab hier können Sie verwandte Themen erkunden, etwa **Schatten zu Shapes hinzufügen** für andere Shape‑Typen, **Schattenfarbe dynamisch setzen** basierend auf Daten, oder **Schatten zu Bildern und Textfeldern hinzufügen**. Experimentieren Sie mit verschiedenen Abmessungen, Farben und Schattenstilen, um Ihre Markenrichtlinien oder Ihr Designsystem zu erfüllen.

Bereit, weitere Word‑Dokumente zu automatisieren? Versuchen Sie als Nächstes das Hinzufügen von Tabellen, Kopfzeilen oder dynamischen Inhalten – jeder Schritt baut auf den hier gezeigten Prinzipien auf. Viel Spaß beim Coden!


## Was sollten Sie als Nächstes lernen?


Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden demonstrierten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [Create rectangle shape, add shadow & save PDF](/words/english/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [How to Manage Document Variables with Aspose.Words in Python&#58; A Complete Guide](/words/english/python-net/document-properties-metadata/aspose-words-python-manage-document-variables/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}