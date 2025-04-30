---
"description": "Erfahren Sie, wie Sie Word-Dokumente mit Aspose.Words für Java als PDF speichern. Passen Sie Schriftarten, Eigenschaften und Bildqualität an. Eine umfassende Anleitung zur PDF-Konvertierung."
"linktitle": "Dokumente als PDF speichern"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Speichern von Dokumenten als PDF in Aspose.Words für Java"
"url": "/de/java/document-loading-and-saving/saving-documents-as-pdf/"
"weight": 22
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Speichern von Dokumenten als PDF in Aspose.Words für Java


## Einführung in das Speichern von Dokumenten als PDF in Aspose.Words für Java

In dieser Schritt-für-Schritt-Anleitung erfahren Sie, wie Sie Dokumente mit Aspose.Words für Java als PDF speichern. Wir behandeln verschiedene Aspekte der PDF-Konvertierung und stellen Codebeispiele zur Verfügung, um den Prozess zu vereinfachen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Auf Ihrem System ist das Java Development Kit (JDK) installiert.
- Aspose.Words für Java-Bibliothek. Sie können es herunterladen von [Hier](https://releases.aspose.com/words/java/).

## Konvertieren eines Dokuments in PDF

Um ein Word-Dokument in PDF zu konvertieren, können Sie den folgenden Codeausschnitt verwenden:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Ersetzen `"input.docx"` mit dem Pfad zu Ihrem Word-Dokument und `"output.pdf"` mit dem gewünschten PDF-Ausgabedateipfad.

## Steuern der PDF-Speicheroptionen

Sie können verschiedene PDF-Speicheroptionen steuern, indem Sie `PdfSaveOptions` Klasse. Beispielsweise können Sie den Anzeigetitel für das PDF-Dokument wie folgt festlegen:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Einbetten von Schriftarten in PDF

Um Schriftarten in das generierte PDF einzubetten, verwenden Sie den folgenden Code:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Anpassen von Dokumenteigenschaften

Sie können die Dokumenteigenschaften in der generierten PDF-Datei anpassen. Beispiel:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Dokumentstruktur exportieren

Um die Dokumentstruktur zu exportieren, setzen Sie die `exportDocumentStructure` Möglichkeit, `true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Bildkomprimierung

Sie können die Bildkomprimierung mit dem folgenden Code steuern:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Aktualisieren der zuletzt gedruckten Eigenschaft

Um die Eigenschaft „Zuletzt gedruckt“ im PDF zu aktualisieren, verwenden Sie:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Rendern von DML-3D-Effekten

Für das erweiterte Rendern von DML-3D-Effekten legen Sie den Rendermodus fest:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Interpolieren von Bildern

Sie können die Bildinterpolation aktivieren, um die Bildqualität zu verbessern:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Abschluss

Aspose.Words für Java bietet umfassende Funktionen zur Konvertierung von Word-Dokumenten ins PDF-Format mit Flexibilität und Anpassungsmöglichkeiten. Sie können verschiedene Aspekte der PDF-Ausgabe steuern, darunter Schriftarten, Dokumenteigenschaften, Bildkomprimierung und mehr.

## Häufig gestellte Fragen

### Wie konvertiere ich ein Word-Dokument mit Aspose.Words für Java in PDF?

Um ein Word-Dokument in PDF zu konvertieren, verwenden Sie den folgenden Code:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

Ersetzen `"input.docx"` mit dem Pfad zu Ihrem Word-Dokument und `"output.pdf"` mit dem gewünschten PDF-Ausgabedateipfad.

### Kann ich Schriftarten in das von Aspose.Words für Java generierte PDF einbetten?

Ja, Sie können Schriftarten in das PDF einbetten, indem Sie die `setEmbedFullFonts` Möglichkeit, `true` In `PdfSaveOptions`Hier ist ein Beispiel:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### Wie kann ich Dokumenteigenschaften im generierten PDF anpassen?

Sie können die Dokumenteigenschaften im PDF anpassen, indem Sie `setCustomPropertiesExport` Option in `PdfSaveOptions`. Zum Beispiel:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### Was ist der Zweck der Bildkomprimierung in Aspose.Words für Java?

Mit der Bildkomprimierung können Sie die Qualität und Größe der Bilder im generierten PDF steuern. Sie können den Bildkomprimierungsmodus einstellen mit `setImageCompression` In `PdfSaveOptions`.

### Wie aktualisiere ich die Eigenschaft „Zuletzt gedruckt“ im PDF?

Sie können die Eigenschaft "Zuletzt gedruckt" im PDF aktualisieren, indem Sie `setUpdateLastPrintedProperty` Zu `true` In `PdfSaveOptions`. Dies spiegelt das letzte Druckdatum in den PDF-Metadaten wider.

### Wie kann ich die Bildqualität beim Konvertieren in PDF verbessern?

Um die Bildqualität zu verbessern, aktivieren Sie die Bildinterpolation durch die Einstellung `setInterpolateImages` Zu `true` In `PdfSaveOptions`Dies führt zu glatteren und qualitativ hochwertigeren Bildern im PDF.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}