---
category: general
date: 2026-11-25
description: Fügen Sie einer Form in einem Word‑Dokument mit Python einen Schatten
  hinzu. Erfahren Sie, wie Sie eine Rechteckform in Word einfügen und mithilfe von
  Aspose.Words einen transparenten Schatten anwenden.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add shadow to shape
- insert rectangle shape word
- how to create word document python
- Aspose.Words Python
- shape formatting Python
language: de
lastmod: 2026-11-25
og_description: Fügen Sie einer Form in einem Word‑Dokument mit Python einen Schatten
  hinzu. Dieses Tutorial zeigt, wie man eine Rechteckform in Word einfügt und mit
  Aspose.Words einen zu 30 % transparenten Schatten einstellt.
og_image_alt: Add shadow to shape example in a Word document created by Python
og_title: Schatten zu einer Form in einem Word‑Dokument mit Python hinzufügen – Schritt‑für‑Schritt‑Anleitung
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Add shadow to shape in a Word document with Python. Learn how to insert
    rectangle shape in Word and apply a transparent shadow using Aspose.Words.
  headline: How to add shadow to shape in a Word document using Python
  type: TechArticle
tags:
- Python
- Aspose.Words
- Word automation
title: Wie man in einem Word‑Dokument mit Python einer Form Schatten hinzufügt
url: /de/python/images-shapes/how-to-add-shadow-to-shape-in-a-word-document-using-python/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wie man in einem Word‑Dokument mit Python einen Schatten zu einer Form hinzufügt

Wenn Sie **einen Schatten zu einer Form** in einem Word‑Dokument hinzufügen möchten, zeigt Ihnen diese Anleitung eine komplette, ausführbare Lösung. Sie sehen, wie Sie eine Word‑Datei erstellen, eine Rechteck‑Form einfügen und einen zu 30 % transparenten Schatten anwenden – alles mit der Aspose.Words for Python‑Bibliothek.

Die programmgesteuerte Arbeit mit Word‑Dokumenten erspart Ihnen manuelle Formatierung und ermöglicht das Erzeugen von Berichten, Verträgen oder Marketing‑Flyern in großem Umfang. Am Ende dieses Tutorials können Sie die Frage „**wie man ein Word‑Dokument mit Python erstellt**“ mit einem sofort einsatzbereiten Code‑Beispiel beantworten.

## Voraussetzungen

Bevor Sie beginnen, stellen Sie sicher, dass Sie Folgendes haben:

* Python 3.8 oder neuer installiert.
* Eine aktive Aspose.Words for Python‑Lizenz (die kostenlose Testversion funktioniert für Evaluierungen).
* Das Paket `aspose-words` installiert via `pip install aspose-words`.
* Einen Ordner, in den die Ausgabedatei geschrieben werden kann (ersetzen Sie `YOUR_DIRECTORY` im Code).

Weitere Abhängigkeiten sind nicht erforderlich.

## Schritt 1: Ein neues Word‑Dokument erstellen

Der erste Schritt besteht darin, ein `Document`‑Objekt zu instanziieren. Dieses Objekt repräsentiert die gesamte .docx‑Datei im Speicher.

```python
import aspose.words as aw

# Create an empty Word document
doc = aw.Document()
# DocumentBuilder provides a convenient API for adding content
builder = aw.DocumentBuilder(doc)
```

`DocumentBuilder` funktioniert wie ein virtueller Cursor. Wenn Sie seine Methoden aufrufen, fügt die Bibliothek die entsprechenden Elemente an der aktuellen Cursor‑Position ein.

## Schritt 2: Rechteck‑Form einfügen

Als Nächstes **fügen Sie eine Rechteck‑Form** mithilfe der Methode `insert_shape` des Builders ein. Die Methode benötigt den Formtyp und deren Größe in Punkten (1 Punkt = 1/72 Zoll).

```python
# Insert a rectangle shape that is 100 points wide and 50 points tall
shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)
```

Sie können die Abmessungen an Ihr Design anpassen. Das Rechteck wird Teil der Zeichenebene des Dokuments, sodass Sie später Füllung, Kontur oder Schatten ändern können.

## Schritt 3: Auf das Schattenformat der Form zugreifen

Jedes Zeichenobjekt stellt eine Eigenschaft `shadow_format` bereit, die das Erscheinungsbild des Schattens steuert. Rufen Sie sie ab, um Transparenz, Versatz, Weichzeichnung und Farbe anzupassen.

```python
# Get the ShadowFormat object for the rectangle
shadow = shape.shadow_format
```

Zu diesem Zeitpunkt hat die Form den Standardschatten (keinen Schatten). Das Objekt `ShadowFormat` enthält alle Parameter, die Sie benötigen, um einen realistischen Effekt zu erzeugen.

## Schritt 4: Schatten zu 30 % transparent machen

Transparenz wird als Wert zwischen `0` (vollständig undurchsichtig) und `1` (vollständig transparent) angegeben. Das Setzen auf `0.3` ergibt einen zu 30 % transparenten Schatten, was oft ausreicht, um Tiefe zu erzeugen, ohne den Text zu überlagern.

```python
# Apply a 30 % transparent shadow
shadow.transparency = 0.3
# Optional: adjust other shadow properties for a nicer look
shadow.visible = True               # Ensure the shadow is turned on
shadow.distance = 4                 # Distance of the shadow from the shape (points)
shadow.blur = 4                     # Amount of blur applied to the shadow
shadow.color = aw.Color.black       # Shadow color
```

Diese zusätzlichen Eigenschaften sind nicht zwingend erforderlich, illustrieren jedoch, wie Sie den Effekt feinjustieren können. Das Flag `visible` ist essenziell; wenn Sie es vergessen, erscheint der Schatten nicht, obwohl die anderen Einstellungen konfiguriert sind.

## Schritt 5: Dokument speichern, um das Ergebnis zu sehen

Abschließend schreiben Sie das Dokument auf die Festplatte. Öffnet man die resultierende `.docx`‑Datei in Microsoft Word oder einem kompatiblen Viewer, sieht man das Rechteck mit dem angewendeten transparenten Schatten.

```python
# Save the document to the desired location
output_path = r"YOUR_DIRECTORY/output.docx"
doc.save(output_path)
print(f"Document saved to {output_path}")
```

Wenn Sie `output.docx` öffnen, sehen Sie ein einfaches Rechteck mit einem dezenten grauen Schatten, der nach unten rechts versetzt ist. Die 30 %ige Transparenz lässt die Form scheinbar von der Seite abheben.

![Add shadow to shape example](placeholder-image.png){: .align-center alt="Beispiel für Schatten zu Form in einem Word-Dokument, erstellt mit Python"}

## Vollständiges, ausführbares Skript

Alle Bausteine zusammen ergeben ein eigenständiges Skript, das Sie kopieren, einfügen und sofort ausführen können.

```python
import aspose.words as aw

def create_word_with_shadow(output_path: str):
    """
    Creates a Word document that contains a rectangle shape
    with a 30 % transparent shadow.
    """
    # Step 1: Initialize document and builder
    doc = aw.Document()
    builder = aw.DocumentBuilder(doc)

    # Step 2: Insert rectangle shape
    shape = builder.insert_shape(aw.drawing.ShapeType.RECTANGLE, 100, 50)

    # Step 3: Access shadow format
    shadow = shape.shadow_format

    # Step 4: Configure shadow properties
    shadow.visible = True
    shadow.transparency = 0.3
    shadow.distance = 4
    shadow.blur = 4
    shadow.color = aw.Color.black

    # Step 5: Save the document
    doc.save(output_path)
    print(f"Document saved to {output_path}")

if __name__ == "__main__":
    # Replace with a valid folder on your machine
    create_word_with_shadow(r"YOUR_DIRECTORY/output.docx")
```

**Erwartete Ausgabe:** Das Öffnen der erzeugten `output.docx` zeigt eine einzelne Seite mit einem Rechteck, das einen leichten, halbtransparenten Schatten wirft. Weitere Formatierungen sind nicht nötig.

## Häufige Varianten und Sonderfälle

| Situation | Wie man den Code anpasst |
|-----------|--------------------------|
| **Anderer Formtyp** (z. B. Ellipse) | Ändern Sie `aw.drawing.ShapeType.RECTANGLE` zu `aw.drawing.ShapeType.ELLIPSE`. |
| **Benutzerdefinierte Schattenfarbe** | Setzen Sie `shadow.color = aw.Color.from_argb(255, 128, 0, 0)` für einen rötlichen Schatten. |
| **Mehrere Formen** | Rufen Sie `builder.insert_shape` wiederholt auf; jeder Aufruf liefert ein separates `Shape`‑Objekt, das Sie unabhängig formatieren können. |
| **Als PDF speichern** | Ersetzen Sie `doc.save(output_path)` durch `doc.save(output_path.replace('.docx', '.pdf'))` und verwenden Sie die `.pdf`‑Erweiterung. |
| **Ausführen ohne Lizenz** | Die kostenlose Testversion fügt dem ersten Blatt ein Wasserzeichen hinzu. Beschaffen Sie eine Lizenz, um es in der Produktion zu entfernen. |

Diese Varianten zeigen, dass das gleiche Muster – Dokument erstellen, Form einfügen, `shadow_format` anpassen, speichern – die meisten Automatisierungsszenarien abdeckt.

## Tipps und bewährte Vorgehensweisen

* **Builder wiederverwenden**: Halten Sie eine einzige `DocumentBuilder`‑Instanz für das gesamte Dokument, um unnötige Objektinstanzen zu vermeiden.
* **Ressourcen freigeben**: In langlaufenden Diensten rufen Sie nach dem Speichern `doc.dispose()` auf, um nativen Speicher freizugeben.
* **Ausgabe validieren**: Verwenden Sie `doc.validate(aw.ValidationType.FULL_VALIDATION)` vor dem Speichern, wenn Sie die Einhaltung des Open‑XML‑Standards sicherstellen müssen.
* **Versionskompatibilität**: Der Code funktioniert mit Aspose.Words for Python ≥ 22.9. Stellen Sie sicher, dass Ihr Paket mit `pip install --upgrade aspose-words` aktuell ist.

## Fazit

Sie wissen jetzt, wie man **einen Schatten zu einer Form** in einem Word‑Dokument mit Python hinzufügt. Indem Sie die fünf Schritte befolgen – Dokument erstellen, **Rechteck‑Form einfügen**, Schatten konfigurieren und speichern – können Sie die automatisierte Erstellung von professionell aussehenden Dokumenten für Berichte, Rechnungen oder Marketing‑Materialien automatisieren.

Ab hier können Sie weitere Formatierungsoptionen erkunden, etwa Farbverläufe, Textumfluss oder die Konvertierung des Dokuments nach PDF. All diese Themen bauen auf denselben `DocumentBuilder`‑ und Form‑Formatierungskonzepten auf, die in diesem Tutorial vorgestellt wurden.

Viel Spaß beim Coden und genießen Sie die visuelle Tiefe, die ein einfacher Schatten Ihren automatisierten Word‑Dokumenten verleihen kann!

## Was sollten Sie als Nächstes lernen?

Die folgenden Tutorials behandeln eng verwandte Themen, die auf den in diesem Leitfaden gezeigten Techniken aufbauen. Jede Ressource enthält vollständige, funktionierende Code‑Beispiele mit Schritt‑für‑Schritt‑Erklärungen, um Ihnen zu helfen, weitere API‑Funktionen zu meistern und alternative Implementierungsansätze in Ihren eigenen Projekten zu erkunden.

- [How to create rectangle shape in a Word document using Python](/words/english/python-net/images-shapes/how-to-create-rectangle-shape-in-a-word-document-using-pytho/)
- [Add Shadow to Shape in Python – Complete Aspose.Words Tutorial](/words/english/python-net/images-shapes/add-shadow-to-shape-in-python-complete-aspose-words-tutorial/)
- [Create Blank Word Document and Add Shadow to Shape – Full Python Guide](/words/english/python-net/images-shapes/create-blank-word-document-and-add-shadow-to-shape-full-pyth/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}