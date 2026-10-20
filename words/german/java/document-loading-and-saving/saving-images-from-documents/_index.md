---
date: 2025-12-27
description: Erfahren Sie, wie Sie eine Seite als JPEG speichern und Bilder aus Word‑Dokumenten
  mit Aspose.Words für Java extrahieren. Enthält Tipps zum Einstellen von Bildhelligkeit,
  Auflösung und zum Erstellen mehrseitiger TIFF‑Dateien.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Wie man eine Seite als JPEG speichert und Bilder aus Dokumenten mit Aspose.Words
  für Java extrahiert
url: /de/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Seite als JPEG speichern und Bilder aus Dokumenten in Aspose.Words für Java extrahieren

In diesem Tutorial erfahren Sie, wie Sie **Seite als JPEG speichern** aus einem Word‑Dokument und wie Sie **Bilder aus Word**‑Dateien mit Aspose.Words für Java extrahieren. Wir gehen reale Anwendungsfälle durch, wie das Einstellen der Bildhelligkeit, das Anpassen der Bildauflösung in Java und das Erstellen eines mehrseitigen TIFFs. Jeder Schritt enthält sofort ausführbare Code‑Snippets, die Sie kopieren, einfügen und sofort Ergebnisse sehen können.

## Schnelle Antworten
- **Kann ich eine einzelne Seite als JPEG speichern?** Ja – verwenden Sie `ImageSaveOptions` mit `setPageSet(new PageSet(pageIndex))`.
- **Wie ändere ich die Bildhelligkeit?** Rufen Sie `options.setImageBrightness(floatValue)` auf (Bereich 0‑1).
- **Was, wenn ich ein mehrseitiges TIFF benötige?** Definieren Sie ein `PageSet`, das die gewünschten Seiten abdeckt, und wählen Sie eine TIFF‑Kompressionsmethode.
- **Wie kann ich die Bildauflösung steuern?** Verwenden Sie `setResolution(floatDpi)` oder `setHorizontalResolution(floatDpi)`.
- **Benötige ich eine Lizenz für die Produktion?** Für den produktiven Einsatz ist eine gültige Aspose.Words‑Lizenz erforderlich.

## Was bedeutet „Seite als JPEG speichern“?
Eine Seite als JPEG zu speichern bedeutet, eine einzelne Seite eines Word‑Dokuments in eine Rasterbilddatei (JPEG) zu konvertieren. Das ist nützlich für die Vorschau‑Erstellung, Thumbnail‑Generierung oder das Einbetten von Dokumentenseiten in Webseiten, wo das Rendern von PDFs nicht praktikabel ist.

## Warum Bilder aus Word‑Dokumenten extrahieren?
Viele Geschäftsprozesse erfordern das Herausziehen der ursprünglichen Grafiken (Logos, Diagramme, Fotos) aus einer DOCX‑Datei zur Wiederverwendung, Archivierung oder Analyse. Aspose.Words ermöglicht das unkomplizierte Extrahieren jedes Bildes in seinem nativen Format, ohne Qualitätsverlust.

## Voraussetzungen
- Java Development Kit (JDK 8 oder neuer) installiert.
- Aspose.Words für Java‑Bibliothek zu Ihrem Projekt hinzugefügt. Laden Sie sie von [hier](https://releases.aspose.com/words/java/) herunter.
- Ein Beispiel‑Word‑Dokument (z. B. `Rendering.docx`) in einem bekannten Verzeichnis abgelegt.

## Schritt 1: Bilder als TIFF mit Schwellenwert‑Steuerung speichern (Mehrseitiges TIFF erstellen)
Um ein hochkontrastreiches, Graustufen‑TIFF zu erzeugen, können Sie den Binärisierungs‑Schwellenwert steuern. Das ist praktisch, wenn Sie eine druckbare Schwarz‑weiß‑Version Ihres Dokuments benötigen.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Schritt 2: Eine bestimmte Seite als mehrseitiges TIFF speichern
Wenn Sie ein TIFF benötigen, das nur einen Teil der Seiten enthält (z. B. Seiten 1‑2), konfigurieren Sie ein `PageSet`. Dies demonstriert **mehrseitiges TIFF erstellen**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Schritt 3: Bilder als 1 BPP indiziertes PNG speichern
Wenn Sie ultraleichte Schwarz‑weiß‑PNGs (1 Bit pro Pixel) benötigen, setzen Sie das Pixel‑Format entsprechend. Das ist nützlich, um einfache Grafiken in Szenarien mit geringer Bandbreite einzubetten.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Schritt 4: Eine Seite als JPEG mit Anpassungen speichern (Bildhelligkeit & Auflösung setzen)
Hier **speichern wir eine Seite als JPEG**, während wir Helligkeit, Kontrast und Auflösung anpassen – perfekt für Thumbnails oder web‑fertige Vorschauen.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Schritt 5: Verwendung eines Page‑Saving‑Callbacks (Erweiterte Anpassungen)
Ein Callback ermöglicht es, jede Ausgabedatei dynamisch umzubenennen, was beim Export vieler Seiten auf einmal nützlich ist.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
doc.save("Your Directory Path" + "PageSavingCallback.png", imageSaveOptions);
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Vollständiger Quellcode für alle Szenarien
Unten finden Sie eine einzelne Klasse, die jede oben demonstrierte Methode enthält. Sie können jeden Test einzeln ausführen.

```java
public void exposeThresholdControlForTiffBinarization() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setTiffCompression(TiffCompression.CCITT_3);
		saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
		saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
		saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.ExposeThresholdControlForTiffBinarization.tiff", saveOptions);
}
@Test
public void getTiffPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.MultipageTiff.tiff");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(new PageRange(0, 1))); saveOptions.setTiffCompression(TiffCompression.CCITT_4); saveOptions.setResolution(160f);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetTiffPageRange.tiff", saveOptions);
}
@Test
public void format1BppIndexed() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(1));
		saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
		saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
}
@Test
public void getJpegPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions options = new ImageSaveOptions();
	// Set the "PageSet" to "0" to convert only the first page of a document.
	options.setPageSet(new PageSet(0));
	// Change the image's brightness and contrast.
	// Both are on a 0-1 scale and are at 0.5 by default.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Change the horizontal resolution.
	// The default value for these properties is 96.0, for a resolution of 96dpi.
	options.setHorizontalResolution(72f);
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
}
@Test
public static void pageSavingCallback() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
	{
		imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
		imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
}
private static class HandlePageSavingCallback implements IPageSavingCallback
{
	public void pageSaving(PageSavingArgs args)
	{
		args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
	}
```

## Häufige Probleme und Lösungen
- **„Dokumentdatei nicht gefunden“** – Überprüfen Sie, ob der Dateipfad den korrekten Trenner (`/` oder `\\`) für Ihr Betriebssystem verwendet.
- **Bilder erscheinen leer** – Stellen Sie sicher, dass Sie einen geeigneten `ImageColorMode` setzen (z. B. `GRAYSCALE` für TIFF).
- **Out‑of‑Memory‑Fehler bei großen Dokumenten** – Verarbeiten Sie Seiten in Batches, indem Sie den `PageSet`‑Bereich anpassen.
- **JPEG‑Qualität ist schlecht** – Erhöhen Sie die Auflösung mit `setHorizontalResolution` oder `setResolution`.

## Häufig gestellte Fragen

**F: Wie ändere ich das Bildformat beim Speichern mit Aspose.Words für Java?**  
A: Setzen Sie das gewünschte Format in `ImageSaveOptions`. Für PNG können Sie einfach `ImageSaveOptions` instanziieren und `SaveFormat.PNG` zuweisen, falls nötig.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**F: Kann ich die Kompressionseinstellungen für TIFF‑Bilder anpassen?**  
A: Ja. Verwenden Sie `setTiffCompression`, um einen Kompressionsalgorithmus wie `CCITT_3` auszuwählen.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**F: Wie kann ich eine bestimmte Seite aus einem Dokument als separates Bild speichern?**  
A: Nutzen Sie die Methode `setPageSet` mit einem einzelnen Seitenindex.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**F: Wie wende ich benutzerdefinierte Einstellungen auf JPEG‑Bilder beim Speichern an?**  
A: Passen Sie Eigenschaften wie Helligkeit, Kontrast und Auflösung über `ImageSaveOptions` an.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**F: Wie kann ich einen Callback für die Anpassung des Bildspeicherns verwenden?**  
A: Implementieren Sie `IPageSavingCallback` und weisen Sie ihn mit `setPageSavingCallback` zu.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Fazit
Sie verfügen nun über ein komplettes Werkzeugset zum **Speichern einer Seite als JPEG**, zum Extrahieren von Bildern, zum Steuern der Bildhelligkeit, zum Festlegen der Bildauflösung in Java und zum Erstellen mehrseitiger TIFF‑Dateien mit Aspose.Words für Java. Experimentieren Sie mit verschiedenen `ImageSaveOptions`‑Einstellungen, um die Anforderungen Ihres Projekts zu erfüllen, und erkunden Sie die umfangreiche Aspose.Words‑API für noch mehr Dokumenten‑Manipulationsmöglichkeiten.

---

**Zuletzt aktualisiert:** 2025-12-27  
**Getestet mit:** Aspose.Words für Java 24.12 (zum Zeitpunkt der Erstellung)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}