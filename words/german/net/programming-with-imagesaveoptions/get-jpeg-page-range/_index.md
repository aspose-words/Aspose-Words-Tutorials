---
title: JPEG-Seitenbereich abrufen
linktitle: JPEG-Seitenbereich abrufen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Konvertieren Sie bestimmte Seiten von Word-Dokumenten mit benutzerdefinierten Einstellungen mit Aspose.Words für .NET in JPEG. Erfahren Sie Schritt für Schritt, wie Sie Helligkeit, Kontrast und Auflösung anpassen.
weight: 10
url: /de/net/programming-with-imagesaveoptions/get-jpeg-page-range/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# JPEG-Seitenbereich abrufen

## Einführung

Das Konvertieren von Word-Dokumenten in Bilder kann unglaublich nützlich sein, egal ob Sie Miniaturansichten erstellen, Dokumente online in der Vorschau anzeigen oder Inhalte in einem zugänglicheren Format freigeben. Mit Aspose.Words für .NET können Sie bestimmte Seiten Ihrer Word-Dokumente problemlos in das JPEG-Format konvertieren und dabei verschiedene Einstellungen wie Helligkeit, Kontrast und Auflösung anpassen. Lassen Sie uns Schritt für Schritt durchgehen, wie Sie dies erreichen!

## Voraussetzungen

Bevor wir beginnen, müssen Sie einige Dinge vorbereitet haben:

-  Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Sie können[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: AC#-Entwicklungsumgebung wie Visual Studio.
- Beispieldokument: Ein Word-Dokument zum Arbeiten. Sie können für dieses Tutorial jede beliebige DOCX-Datei verwenden.
- Grundlegende C#-Kenntnisse: Vertrautheit mit der C#-Programmierung.

Sobald Sie diese bereit haben, können wir loslegen!

## Namespaces importieren

Um Aspose.Words für .NET zu verwenden, müssen Sie die erforderlichen Namespaces am Anfang Ihres Codes importieren. Dadurch wird sichergestellt, dass Sie Zugriff auf alle Klassen und Methoden haben, die für die Dokumentbearbeitung erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Laden Sie Ihr Dokument

Zuerst müssen wir das Word-Dokument laden, das wir konvertieren möchten. Nehmen wir an, unser Dokument heißt`Rendering.docx` und befindet sich in dem durch den Platzhalter angegebenen Verzeichnis`YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Dieser Code initialisiert den Pfad zu Ihrem Dokument und lädt es in ein Aspose.Words`Document` Objekt.

## Schritt 2: ImageSaveOptions einrichten

 Als nächstes richten wir die`ImageSaveOptions` um anzugeben, wie unser JPEG generiert werden soll. Dazu gehört das Einstellen des Seitenbereichs, der Bildhelligkeit, des Kontrasts und der Auflösung.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // Konvertieren Sie nur die erste Seite
options.ImageBrightness = 0.3f;   // Helligkeit einstellen
options.ImageContrast = 0.7f;     // Kontrast einstellen
options.HorizontalResolution = 72f; // Auflösung festlegen
```

## Schritt 3: Speichern Sie das Dokument als JPEG

Abschließend speichern wir das Dokument mit den von uns festgelegten Einstellungen als JPEG-Datei ab.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

 Dieser Code speichert die erste Seite von`Rendering.docx` als JPEG-Bild mit den angegebenen Helligkeits-, Kontrast- und Auflösungseinstellungen.

## Abschluss

Und da haben Sie es! Sie haben eine bestimmte Seite eines Word-Dokuments erfolgreich mit benutzerdefinierten Einstellungen mithilfe von Aspose.Words für .NET in ein JPEG-Bild konvertiert. Dieser Vorgang kann an verschiedene Anforderungen angepasst werden, unabhängig davon, ob Sie Bilder für eine Website vorbereiten, Dokumentvorschauen erstellen oder mehr.

## Häufig gestellte Fragen

### Kann ich mehrere Seiten gleichzeitig konvertieren?
 Ja, Sie können einen Seitenbereich angeben mit dem`PageSet` Immobilien in`ImageSaveOptions`.

### Wie passe ich die Bildqualität an?
 Sie können die Qualität des JPEG anpassen, indem Sie`JpegQuality` Immobilien in`ImageSaveOptions`.

### Kann ich in anderen Bildformaten speichern?
 Ja, Aspose.Words unterstützt verschiedene Bildformate wie PNG, BMP und TIFF. Ändern Sie die`SaveFormat` In`ImageSaveOptions` entsprechend.

### Gibt es eine Möglichkeit, das Bild vor dem Speichern in der Vorschau anzuzeigen?
Sie müssten einen Vorschaumechanismus separat implementieren, da Aspose.Words keine integrierte Vorschaufunktion bietet.

### Wie erhalte ich eine temporäre Lizenz für Aspose.Words?
 Sie können eine[vorläufige Lizenz hier](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
