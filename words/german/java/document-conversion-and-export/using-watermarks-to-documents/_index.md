---
date: 2026-02-19
description: Erfahren Sie, wie Sie mit Aspose.Words für Java ein Dokument mit Wasserzeichen
  erstellen und ein Bildwasserzeichen in Java hinzufügen, um professionell aussehende
  Dokumente zu erzeugen.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Dokument mit Wasserzeichen erstellen mit Aspose.Words für Java
url: /de/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokument mit Wasserzeichen erstellen mit Aspose.Words für Java

In diesem Tutorial **erstellen Sie ein Dokument mit Wasserzeichen** mithilfe der Aspose.Words für Java API. Wasserzeichen – ob Text oder Bilder – helfen Ihnen, eine Datei als vertraulich, Entwurf oder genehmigt zu kennzeichnen, und sie können programmatisch auf jedes Word‑Dokument angewendet werden. Wir führen Sie durch die Einrichtung der Bibliothek, das Hinzufügen von Text‑ und Bildwasserzeichen, die Anpassung ihres Aussehens und sogar das Entfernen, wenn sie nicht mehr benötigt werden.

## Schnelle Antworten
- **Was macht ein Wasserzeichen?** Es überlagert Text oder ein Bild auf jeder Seite, um Status oder Markenkennzeichnung zu vermitteln.  
- **Welche Bibliothek fügt Wasserzeichen in Java hinzu?** Aspose.Words für Java bietet integrierte Wasserzeichen‑Unterstützung.  
- **Kann ich ein Bildwasserzeichen hinzufügen?** Ja – verwenden Sie die `Shape`‑Klasse und den Ansatz `add image watermark java`.  
- **Ist das Wasserzeichen halbtransparent?** Sie können die Deckkraft über `setSemitransparent` für Textwasserzeichen steuern.  
- **Brauche ich eine Lizenz?** Eine kostenlose Testversion funktioniert zum Testen; für die Produktion ist eine kommerzielle Lizenz erforderlich.

## Was ist ein Wasserzeichen und warum verwenden?

Ein Wasserzeichen ist ein schwaches Overlay – textuell oder grafisch – das jeder Seite eines Dokuments hinzugefügt wird. Es wird häufig verwendet, um **Vertraulichkeit**, **Entwurfsstatus** oder **Markenkennzeichnung** anzuzeigen, ohne den zugrunde liegenden Inhalt zu verändern. Das programmatische Hinzufügen von Wasserzeichen sorgt für Konsistenz bei großen Dateimengen und spart Zeit im Vergleich zur manuellen Bearbeitung.

## Einrichtung von Aspose.Words für Java

Bevor wir beginnen, Wasserzeichen hinzuzufügen, stellen Sie sicher, dass die Bibliothek in Ihrem Projekt bereitsteht:

1. Laden Sie Aspose.Words für Java von [here](https://releases.aspose.com/words/java/) herunter.  
2. Fügen Sie die heruntergeladene JAR‑Datei (oder Maven/Gradle‑Abhängigkeit) zum Klassenpfad Ihres Projekts hinzu.  
3. Importieren Sie die erforderlichen Klassen in Ihrer Java‑Quelldatei:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Jetzt, wo die Bibliothek eingerichtet ist, tauchen wir in den eigentlichen Wasserzeichen‑Code ein.

## Wie man ein Textwasserzeichen hinzufügt

Textwasserzeichen sind ideal, um ein Dokument als „CONFIDENTIAL“ oder „DRAFT“ zu kennzeichnen. Das folgende Snippet zeigt eine saubere Methode, **ein Dokument mit Wasserzeichen** mithilfe von `TextWatermarkOptions` zu erstellen.

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

### Anpassen des Textwasserzeichens
- **Schriftfamilie & Größe** – ändern Sie `setFontFamily` und `setFontSize`.  
- **Farbe** – verwenden Sie jedes `java.awt.Color`.  
- **Layout** – wählen Sie `HORIZONTAL`, `DIAGONAL` usw.  
- **Transparenz** – schalten Sie `setSemitransparent(true)` für ein leichteres Aussehen ein.

## Wie man ein Bildwasserzeichen hinzufügt (add image watermark java)

Bildwasserzeichen sind perfekt für Logos oder benutzerdefinierte Grafiken. Unten finden Sie das **add image watermark java**‑Beispiel, das ein PNG in die Mitte jeder Seite einfügt.

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

### Tipps für Bildwasserzeichen
- **Größe ändern** mit `setWidth` / `setHeight`, um auf die Seite zu passen.  
- **Position** kann zentriert oder an jedem Rand ausgerichtet werden mittels `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparenz** kann durch Anpassen des Alpha‑Kanals des Bildes vor dem Laden angewendet werden.

## Wie man Wasserzeichen entfernt

Wenn ein Dokument kein Wasserzeichen mehr benötigt, können Sie es programmatisch löschen. Der untenstehende Code durchläuft alle Shapes und entfernt diejenigen, deren Name „Watermark“ enthält.

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

## Häufige Fallstricke und Fehlersuche

- **Wasserzeichen fehlt nach dem Speichern** – stellen Sie sicher, dass Sie `doc.save()` nach dem Setzen des Wasserzeichens aufrufen.  
- **Bild wird nicht angezeigt** – prüfen Sie, ob der Bildpfad korrekt ist und die Datei ein unterstütztes Format (PNG, JPEG, BMP) hat.  
- **Transparenz nicht angewendet** – `setSemitransparent(true)` funktioniert nur bei Textwasserzeichen; bei Bildern bearbeiten Sie den Alpha‑Kanal der PNG.  
- **Mehrere Abschnitte** – hat Ihr Dokument mehrere Abschnitte, fügen Sie das Wasserzeichen jedem Abschnitts‑Body hinzu oder verwenden Sie `doc.getWatermark().setText(...)`, das global gilt.

## Häufig gestellte Fragen

**F: Wie kann ich die Schriftart eines Textwasserzeichens ändern?**  
A: Ändern Sie die Eigenschaft `setFontFamily` in `TextWatermarkOptions`, z. B. `options.setFontFamily("Times New Roman");`.

**F: Kann ich mehrere Wasserzeichen zu einem einzigen Dokument hinzufügen?**  
A: Ja. Erstellen Sie mehrere `Shape`‑Objekte (für Bilder) oder rufen Sie `doc.getWatermark().setText(...)` mit unterschiedlichen Optionen für jedes Wasserzeichen auf.

**F: Ist es möglich, ein Wasserzeichen zu drehen?**  
A: Bei Bildwasserzeichen setzen Sie die Drehung am `Shape`‑Objekt mit `watermark.setRotation(angle)`. Bei Textwasserzeichen verwenden Sie die Eigenschaft `setLayout` (z. B. `WatermarkLayout.DIAGONAL`).

**F: Wie kann ich ein Wasserzeichen halbtransparent machen?**  
A: Setzen Sie `options.setSemitransparent(true)` in `TextWatermarkOptions`. Für Bilder passen Sie die Opazität des Bildes vor dem Laden an.

**F: Kann ich Wasserzeichen zu bestimmten Abschnitten eines Dokuments hinzufügen?**  
A: Ja. Durchlaufen Sie `doc.getSections()` und fügen Sie das Wasserzeichen nur zu den gewünschten Abschnitten hinzu.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Last Updated:** 2026-02-19  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose