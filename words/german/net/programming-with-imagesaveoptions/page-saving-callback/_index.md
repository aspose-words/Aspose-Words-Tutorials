---
"description": "Erfahren Sie mit unserer ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET jede Seite eines Word-Dokuments als separates PNG-Bild speichern."
"linktitle": "Rückruf zum Speichern der Seite"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Rückruf zum Speichern der Seite"
"url": "/de/net/programming-with-imagesaveoptions/page-saving-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rückruf zum Speichern der Seite

## Einführung

Hallo! Wollten Sie schon einmal jede Seite eines Word-Dokuments als separates Bild speichern? Vielleicht möchten Sie einen umfangreichen Bericht in übersichtliche Grafiken aufteilen oder Miniaturansichten für die Vorschau erstellen. Was auch immer Ihr Grund ist, mit Aspose.Words für .NET wird diese Aufgabe zum Kinderspiel. In dieser Anleitung führen wir Sie durch die Einrichtung eines Callbacks zum Speichern von Seiten, um jede Seite eines Dokuments als einzelnes PNG-Bild zu speichern. Los geht‘s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. Aspose.Words für .NET: Falls noch nicht geschehen, laden Sie es herunter und installieren Sie es von [Hier](https://releases.aspose.com/words/net/).
2. Visual Studio: Jede Version sollte funktionieren, aber ich verwende für diese Anleitung Visual Studio 2019.
3. Grundkenntnisse in C#: Sie benötigen grundlegende Kenntnisse in C#, um folgen zu können.

## Namespaces importieren

Zunächst müssen wir die benötigten Namespaces importieren. So können wir auf die benötigten Klassen und Methoden zugreifen, ohne jedes Mal den vollständigen Namespace eingeben zu müssen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Beginnen wir mit der Definition des Pfads zu Ihrem Dokumentverzeichnis. Hier befindet sich Ihr Word-Eingabedokument und hier werden die Ausgabebilder gespeichert.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden Sie Ihr Dokument

Als Nächstes laden wir das zu verarbeitende Dokument. Stellen Sie sicher, dass sich Ihr Dokument („Rendering.docx“) im angegebenen Verzeichnis befindet.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 3: Konfigurieren der Bildspeicheroptionen

Wir müssen die Optionen zum Speichern von Bildern konfigurieren. In diesem Fall speichern wir die Seiten als PNG-Dateien.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

Hier, `PageSet` gibt den zu speichernden Seitenbereich an und `PageSavingCallback` verweist auf unsere benutzerdefinierte Rückrufklasse.

## Schritt 4: Implementieren des Rückrufs zum Speichern der Seite

Lassen Sie uns nun die Rückrufklasse implementieren, die regelt, wie jede Seite gespeichert wird.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

Diese Klasse implementiert die `IPageSavingCallback` Schnittstelle und innerhalb der `PageSaving` Methode definieren wir das Benennungsmuster für jede gespeicherte Seite.

## Schritt 5: Speichern Sie das Dokument als Bilder

Abschließend speichern wir das Dokument mit den konfigurierten Optionen.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Abschluss

Und da haben Sie es! Sie haben erfolgreich einen Rückruf zum Speichern von Seiten eingerichtet, um jede Seite eines Word-Dokuments mit Aspose.Words für .NET als separates PNG-Bild zu speichern. Diese Technik ist für verschiedene Anwendungen äußerst nützlich, von der Erstellung von Seitenvorschauen bis hin zur Generierung einzelner Seitenbilder für Berichte. 

Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich Seiten in anderen Formaten als PNG speichern?  
Ja, Sie können Seiten in verschiedenen Formaten wie JPEG, BMP und TIFF speichern, indem Sie die `SaveFormat` In `ImageSaveOptions`.

### Was ist, wenn ich nur bestimmte Seiten speichern möchte?  
Sie können die Seiten angeben, die Sie speichern möchten, indem Sie die `PageSet` Parameter in `ImageSaveOptions`.

### Ist es möglich, die Bildqualität anzupassen?  
Absolut! Sie können Eigenschaften wie `ImageSaveOptions.JpegQuality` um die Qualität der Ausgabebilder zu steuern.

### Wie kann ich große Dokumente effizient verarbeiten?  
Erwägen Sie bei großen Dokumenten die Stapelverarbeitung der Seiten, um die Speichernutzung effektiv zu verwalten.

### Wo finde ich weitere Informationen zu Aspose.Words für .NET?  
Schauen Sie sich die [Dokumentation](https://reference.aspose.com/words/net/) für umfassende Anleitungen und Beispiele.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}