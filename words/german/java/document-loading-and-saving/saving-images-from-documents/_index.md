---
title: Speichern von Bildern aus Dokumenten in Aspose.Words für Java
linktitle: Bilder aus Dokumenten speichern
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie in unserer umfassenden Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für Java Bilder aus Dokumenten speichern. Passen Sie Formate, Komprimierung und mehr an.
weight: 17
url: /de/java/document-loading-and-saving/saving-images-from-documents/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Speichern von Bildern aus Dokumenten in Aspose.Words für Java


## Einführung in das Speichern von Bildern aus Dokumenten in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie mit Aspose.Words für Java Bilder aus Dokumenten speichern. Wir behandeln verschiedene Szenarien und Anpassungsoptionen zum Speichern von Bildern. Diese Anleitung enthält schrittweise Anweisungen mit Quellcodebeispielen.

## Voraussetzungen

 Bevor Sie beginnen, stellen Sie sicher, dass Sie die Aspose.Words für Java-Bibliothek in Ihr Projekt integriert haben. Sie können sie hier herunterladen:[Hier](https://releases.aspose.com/words/java/).

## Schritt 1: Bilder als TIFF mit Schwellenwertkontrolle speichern

Um Bilder im TIFF-Format mit Schwellenwertsteuerung zu speichern, führen Sie diese Schritte aus:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Schritt 2: Speichern einer bestimmten Seite als mehrseitiges TIFF

Um eine bestimmte Seite als mehrseitiges TIFF zu speichern, verwenden Sie den folgenden Code:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Schritt 3: Bilder als 1 BPP indiziertes PNG speichern

Um Bilder als 1 BPP-indiziertes PNG zu speichern, folgen Sie diesen Schritten:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Schritt 4: Speichern einer Seite als JPEG mit Anpassung

Um eine bestimmte Seite mit Anpassungsoptionen als JPEG zu speichern, verwenden Sie diesen Code:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Schritt 5: Verwenden des Rückrufs zum Speichern von Seiten

Sie können einen Rückruf verwenden, um das Speichern von Seiten anzupassen. Hier ist ein Beispiel:

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

## Vollständiger Quellcode zum Speichern von Bildern aus Dokumenten in Aspose.Words für Java

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
	// Setzen Sie „PageSet“ auf „0“, um nur die erste Seite eines Dokuments zu konvertieren.
	options.setPageSet(new PageSet(0));
	// Ändern Sie Helligkeit und Kontrast des Bildes.
	// Beide liegen auf einer Skala von 0 bis 1 und sind standardmäßig auf 0,5 eingestellt.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Ändern Sie die horizontale Auflösung.
	// Der Standardwert für diese Eigenschaften ist 96,0 bei einer Auflösung von 96 dpi.
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

## Abschluss

Sie haben gelernt, wie Sie mit Aspose.Words für Java Bilder aus Dokumenten speichern. Diese Beispiele zeigen verschiedene Anpassungsoptionen zum Speichern von Bildern, einschließlich Format, Komprimierung und Rückrufnutzung. Entdecken Sie weitere Möglichkeiten mit den leistungsstarken Funktionen von Aspose.Words für Java.

## Häufig gestellte Fragen

### Wie ändere ich das Bildformat beim Speichern mit Aspose.Words für Java?

 Sie können das Bildformat ändern, indem Sie das gewünschte Format im Feld`ImageSaveOptions` . Um beispielsweise als PNG zu speichern, verwenden Sie`SaveFormat.PNG` wie im Code gezeigt:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Kann ich die Komprimierungseinstellungen für TIFF-Bilder anpassen?

Ja, Sie können die Komprimierungseinstellungen für TIFF-Bilder anpassen. Um beispielsweise die Komprimierungsmethode auf CCITT_3 einzustellen, verwenden Sie den folgenden Code:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Wie kann ich eine bestimmte Seite aus einem Dokument als separates Bild speichern?

 Um eine bestimmte Seite als Bild zu speichern, verwenden Sie die`setPageSet`Methode in`ImageSaveOptions` . Um beispielsweise nur die erste Seite zu speichern, setzen Sie den`PageSet` Zu`new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Erste Seite als Bild speichern
```

### Wie wende ich beim Speichern benutzerdefinierte Einstellungen auf JPEG-Bilder an?

Sie können benutzerdefinierte Einstellungen auf JPEG-Bilder anwenden mit`ImageSaveOptions`. Passen Sie Eigenschaften wie Helligkeit, Kontrast und Auflösung an. Um beispielsweise die Helligkeit auf 0,3 und den Kontrast auf 0,7 zu ändern, verwenden Sie diesen Code:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Wie kann ich einen Rückruf zum Anpassen der Bildspeicherung verwenden?

 Um einen Callback für die Anpassung der Bildspeicherung zu verwenden, setzen Sie die`PageSavingCallback` In`ImageSaveOptions` . Erstellen Sie eine Klasse, die das implementiert`IPageSavingCallback` Schnittstelle und überschreiben Sie die`pageSaving` Verfahren.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

 Erstellen Sie dann eine Klasse, die das implementiert`IPageSavingCallback` Schnittstelle und passen Sie den Dateinamen und den Speicherort im`pageSaving` Verfahren.

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
