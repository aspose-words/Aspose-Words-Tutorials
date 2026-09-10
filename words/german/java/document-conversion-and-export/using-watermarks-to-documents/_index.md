---
date: 2025-12-18
description: Erfahren Sie, wie Sie mit Aspose.Words für Java Wasserzeichen zu Dokumenten
  hinzufügen, einschließlich eines Bildwasserzeichen-Beispiels, die Farbe des Wasserzeichens
  ändern, die Transparenz des Wasserzeichens einstellen und das Wasserzeichen aus
  dem Dokument entfernen.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Wie man mit Aspose.Words für Java Wasserzeichen zu Dokumenten hinzufügt
url: /de/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Wie man ein Wasserzeichen zu Dokumenten mit Aspose.Words für Java hinzufügt

## Einführung in das Hinzufügen von Wasserzeichen zu Dokumenten mit Aspose.Words für Java

In diesem Tutorial lernen Sie **wie man ein Wasserzeichen** zu Word‑Dokumenten mit Aspose.Words für Java hinzufügt. Wasserzeichen sind eine schnelle Möglichkeit, eine Datei als vertraulich, Entwurf oder genehmigt zu kennzeichnen, und sie können textbasiert oder bildbasiert sein. Wir führen Sie durch das Einrichten der Bibliothek, das Erstellen von Text‑ und Bildwasserzeichen, das Anpassen ihres Aussehens (einschließlich Ändern der Wasserzeichenfarbe und Einstellen der Transparenz) und sogar das Entfernen eines Wasserzeichens, wenn es nicht mehr benötigt wird.

## Schnelle Antworten
- **Was ist ein Wasserzeichen?** Ein halbtransparentes Overlay (Text oder Bild), das hinter dem Hauptinhalt des Dokuments erscheint.  
- **Kann ich mehrere Wasserzeichen hinzufügen?** Ja – erstelle mehrere `Shape`‑Objekte und füge jedes zu den gewünschten Abschnitten hinzu.  
- **Wie ändere ich die Farbe des Wasserzeichens?** Passe die `Color`‑Eigenschaft in `TextWatermarkOptions` an.  
- **Gibt es ein Beispiel für ein Bildwasserzeichen?** Siehe den Abschnitt „Adding Image Watermarks“ unten.  
- **Benötige ich eine Lizenz, um ein Wasserzeichen zu entfernen?** Eine gültige Aspose.Words‑Lizenz ist für den Produktionseinsatz erforderlich.

## Einrichten von Aspose.Words für Java

Bevor wir beginnen, Wasserzeichen zu Dokumenten hinzuzufügen, müssen wir Aspose.Words für Java einrichten. Befolgen Sie diese Schritte, um zu starten:

1. Laden Sie Aspose.Words für Java von [hier](https://releases.aspose.com/words/java/) herunter.  
2. Fügen Sie die Aspose.Words für Java‑Bibliothek zu Ihrem Java‑Projekt hinzu.  
3. Importieren Sie die erforderlichen Klassen in Ihrem Java‑Code.

Jetzt, da die Bibliothek eingerichtet ist, tauchen wir in die eigentliche Erstellung von Wasserzeichen ein.

## Hinzufügen von Textwasserzeichen

Textwasserzeichen sind eine gängige Wahl, wenn Sie Ihren Dokumenten textuelle Informationen hinzufügen möchten. So können Sie ein Textwasserzeichen mit Aspose.Words für Java hinzufügen:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Warum das wichtig ist:** Durch Anpassen von `setFontFamily`, `setFontSize` und `setColor` können Sie die **Farbe des Wasserzeichens** an Ihr Branding anpassen, und `setSemitransparent(true)` ermöglicht es Ihnen, die **Transparenz des Wasserzeichens** für einen dezenten Effekt einzustellen.

## Hinzufügen von Bildwasserzeichen

Zusätzlich zu Textwasserzeichen können Sie auch Bildwasserzeichen zu Ihren Dokumenten hinzufügen. Unten finden Sie ein **Beispiel für ein Bildwasserzeichen**, das zeigt, wie man ein PNG‑Logo oder‑Siegel einbettet:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Sie können diesen Block mit verschiedenen Bildern oder Positionen wiederholen, um **mehrere Wasserzeichen** zu einer einzelnen Datei hinzuzufügen.

## Anpassen von Wasserzeichen

Sie können Wasserzeichen anpassen, indem Sie ihr Aussehen und ihre Position ändern. Für Textwasserzeichen können Sie Schriftart, Größe, Farbe und Layout ändern. Für Bildwasserzeichen können Sie Größe, Drehung und Ausrichtung anpassen, wie in den vorherigen Beispielen gezeigt.

## Entfernen von Wasserzeichen

Wenn Sie den **Wasserzeicheninhalt** aus einem Dokument entfernen müssen, iteriert der folgende Code über alle Shapes und löscht diejenigen, die als Wasserzeichen identifiziert wurden:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Häufige Anwendungsfälle & Tipps

- **Vertrauliche Entwürfe:** Ein halbtransparentes Textwasserzeichen wie „CONFIDENTIAL“ anwenden.  
- **Branding:** Verwenden Sie ein Bildwasserzeichen, das das Logo Ihres Unternehmens enthält.  
- **Abschnittsspezifische Wasserzeichen:** Durchlaufen Sie `doc.getSections()` und fügen Sie ein Wasserzeichen nur zu den gewünschten Abschnitten hinzu.  
- **Performance‑Tipp:** Verwenden Sie dieselbe `TextWatermarkOptions`‑Instanz erneut, wenn Sie dasselbe Wasserzeichen auf viele Dokumente anwenden.

## Häufig gestellte Fragen

### Wie kann ich die Schriftart eines Textwasserzeichens ändern?

Um die Schriftart eines Textwasserzeichens zu ändern, passen Sie die `setFontFamily`‑Eigenschaft in den `TextWatermarkOptions` an. Zum Beispiel:

```java
options.setFontFamily("Times New Roman");
```

### Kann ich mehrere Wasserzeichen zu einem einzelnen Dokument hinzufügen?

Ja, Sie können mehrere Wasserzeichen zu einem Dokument hinzufügen, indem Sie mehrere `Shape`‑Objekte mit unterschiedlichen Einstellungen erstellen und sie dem Dokument hinzufügen.

### Ist es möglich, ein Wasserzeichen zu drehen?

Ja, Sie können ein Wasserzeichen drehen, indem Sie die `setRotation`‑Eigenschaft im `Shape`‑Objekt setzen. Positive Werte drehen das Wasserzeichen im Uhrzeigersinn, negative Werte gegen den Uhrzeigersinn.

### Wie kann ich ein Wasserzeichen halbtransparent machen?

Um ein Wasserzeichen halbtransparent zu machen, setzen Sie die `setSemitransparent`‑Eigenschaft in den `TextWatermarkOptions` auf `true`.

### Kann ich Wasserzeichen zu bestimmten Abschnitten eines Dokuments hinzufügen?

Ja, Sie können Wasserzeichen zu bestimmten Abschnitten eines Dokuments hinzufügen, indem Sie die Abschnitte durchlaufen und das Wasserzeichen zu den gewünschten Abschnitten hinzufügen.

---

**Zuletzt aktualisiert:** 2025-12-18  
**Getestet mit:** Aspose.Words für Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}