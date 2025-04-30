---
"description": "Erfahren Sie, wie Sie in Aspose.Words für Java Wasserzeichen zu Dokumenten hinzufügen. Passen Sie Text- und Bildwasserzeichen für professionell aussehende Dokumente an."
"linktitle": "Verwenden von Wasserzeichen in Dokumenten"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Verwenden von Wasserzeichen in Dokumenten in Aspose.Words für Java"
"url": "/de/java/document-conversion-and-export/using-watermarks-to-documents/"
"weight": 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Wasserzeichen in Dokumenten in Aspose.Words für Java


## Einführung in das Hinzufügen von Wasserzeichen zu Dokumenten in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie mithilfe der Aspose.Words für Java-API Wasserzeichen zu Dokumenten hinzufügen. Wasserzeichen sind eine nützliche Möglichkeit, Dokumente mit Text oder Grafiken zu kennzeichnen, um deren Status, Vertraulichkeit oder andere relevante Informationen anzuzeigen. Wir behandeln in dieser Anleitung sowohl Text- als auch Bildwasserzeichen.

## Einrichten von Aspose.Words für Java

Bevor wir Wasserzeichen in Dokumente einfügen, müssen wir Aspose.Words für Java einrichten. Befolgen Sie diese Schritte, um zu beginnen:

1. Laden Sie Aspose.Words für Java herunter von [Hier](https://releases.aspose.com/words/java/).
2. Fügen Sie Ihrem Java-Projekt die Bibliothek Aspose.Words für Java hinzu.
3. Importieren Sie die erforderlichen Klassen in Ihren Java-Code.

Nachdem wir die Bibliothek eingerichtet haben, können wir mit dem Hinzufügen von Wasserzeichen fortfahren.

## Textwasserzeichen hinzufügen

Textwasserzeichen werden häufig verwendet, wenn Sie Ihren Dokumenten Textinformationen hinzufügen möchten. So fügen Sie mit Aspose.Words für Java ein Textwasserzeichen hinzu:

```java
// Erstellen einer Dokumentinstanz
Document doc = new Document("Document.docx");

// TextWasserzeichenoptionen definieren
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Legen Sie den Wasserzeichentext und die Optionen fest
doc.getWatermark().setText("Test", options);

// Speichern Sie das Dokument mit dem Wasserzeichen
doc.save("DocumentWithWatermark.docx");
```

## Bildwasserzeichen hinzufügen

Zusätzlich zu Textwasserzeichen können Sie Ihren Dokumenten auch Bildwasserzeichen hinzufügen. So fügen Sie ein Bildwasserzeichen hinzu:

```java
// Erstellen einer Dokumentinstanz
Document doc = new Document("Document.docx");

// Laden Sie das Bild für das Wasserzeichen
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Legen Sie die Größe und Position des Wasserzeichens fest
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Fügen Sie dem Dokument das Wasserzeichen hinzu
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Speichern Sie das Dokument mit dem Wasserzeichen
doc.save("DocumentWithImageWatermark.docx");
```

## Anpassen von Wasserzeichen

Sie können Wasserzeichen anpassen, indem Sie deren Aussehen und Position anpassen. Bei Textwasserzeichen können Sie Schriftart, Größe, Farbe und Layout ändern. Bei Bildwasserzeichen können Sie Größe und Position wie in den vorherigen Beispielen gezeigt anpassen.

## Wasserzeichen entfernen

Um Wasserzeichen aus einem Dokument zu entfernen, können Sie den folgenden Code verwenden:

```java
// Erstellen einer Dokumentinstanz
Document doc = new Document("DocumentWithWatermark.docx");

// Entfernen Sie das Wasserzeichen
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Speichern Sie das Dokument ohne Wasserzeichen
doc.save("DocumentWithoutWatermark.docx");
```


## Abschluss

In diesem Tutorial haben wir gelernt, wie man mit Aspose.Words für Java Wasserzeichen zu Dokumenten hinzufügt. Ob Text- oder Bildwasserzeichen – Aspose.Words bietet die Tools für deren effiziente Anpassung und Verwaltung. Sie können Wasserzeichen auch entfernen, wenn sie nicht mehr benötigt werden, um sicherzustellen, dass Ihre Dokumente sauber und professionell aussehen.

## Häufig gestellte Fragen

### Wie kann ich die Schriftart eines Textwasserzeichens ändern?

Um die Schriftart eines Textwasserzeichens zu ändern, ändern Sie die `setFontFamily` Eigentum in der `TextWatermarkOptions`. Zum Beispiel:

```java
options.setFontFamily("Times New Roman");
```

### Kann ich einem einzelnen Dokument mehrere Wasserzeichen hinzufügen?

Ja, Sie können einem Dokument mehrere Wasserzeichen hinzufügen, indem Sie mehrere `Shape` Objekte mit unterschiedlichen Einstellungen und fügen Sie sie dem Dokument hinzu.

### Ist es möglich, ein Wasserzeichen zu drehen?

Ja, Sie können ein Wasserzeichen drehen, indem Sie die `setRotation` Eigentum in der `Shape` Objekt. Positive Werte drehen das Wasserzeichen im Uhrzeigersinn, negative Werte gegen den Uhrzeigersinn.

### Wie kann ich ein Wasserzeichen halbtransparent machen?

Um ein Wasserzeichen halbtransparent zu machen, stellen Sie die `setSemitransparent` Eigentum zu `true` im `TextWatermarkOptions`.

### Kann ich bestimmten Abschnitten eines Dokuments Wasserzeichen hinzufügen?

Ja, Sie können bestimmten Abschnitten eines Dokuments Wasserzeichen hinzufügen, indem Sie die Abschnitte durchlaufen und das Wasserzeichen zu den gewünschten Abschnitten hinzufügen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}