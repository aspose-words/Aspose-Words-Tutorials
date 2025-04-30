---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET ein Word-Dokument in ein 1Bpp-indiziertes Bild konvertieren. Folgen Sie unserer Schritt-für-Schritt-Anleitung für eine einfache Konvertierung."
"linktitle": "Format 1Bpp indiziert"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Format 1Bpp indiziert"
"url": "/de/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Format 1Bpp indiziert

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie ein Word-Dokument mit nur wenigen Codezeilen als Schwarzweißbild speichern können? Sie haben Glück! Heute zeigen wir Ihnen einen kleinen Trick mit Aspose.Words für .NET, mit dem Sie Ihre Dokumente in 1Bpp-indizierte Bilder konvertieren können. Dieses Format eignet sich perfekt für bestimmte Arten der digitalen Archivierung, zum Drucken oder wenn Sie Platz sparen müssen. Wir erklären Ihnen jeden Schritt, damit es kinderleicht ist. Bereit zum Start? Los geht’s!

## Voraussetzungen

Bevor wir loslegen, müssen Sie einige Dinge vorbereitet haben:

- Aspose.Words für .NET: Stellen Sie sicher, dass die Bibliothek installiert ist. Sie können [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- .NET-Entwicklungsumgebung: Visual Studio ist eine gute Option, Sie können jedoch jede Umgebung verwenden, mit der Sie vertraut sind.
- Grundkenntnisse in C#: Keine Sorge, wir halten es einfach, aber ein wenig Vertrautheit mit C# ist hilfreich.
- Ein Word-Dokument: Halten Sie ein Beispiel-Word-Dokument zur Konvertierung bereit.

## Namespaces importieren

Zuerst müssen wir die erforderlichen Namespaces importieren. Dies ist wichtig, da wir so auf die benötigten Klassen und Methoden von Aspose.Words zugreifen können.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Sie müssen den Pfad zu Ihrem Dokumentverzeichnis angeben. Hier wird Ihr Word-Dokument gespeichert und auch das konvertierte Bild.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden Sie das Word-Dokument

Laden wir nun das Word-Dokument in ein Aspose.Words `Document` Objekt. Dieses Objekt stellt Ihre Word-Datei dar und ermöglicht Ihnen deren Bearbeitung.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 3: Konfigurieren der Bildspeicheroptionen

Als nächstes müssen wir Folgendes einrichten: `ImageSaveOptions`. Hier geschieht die Magie. Wir konfigurieren es so, dass das Bild im PNG-Format mit indiziertem 1Bpp-Farbmodus gespeichert wird.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Dies gibt an, dass wir das Dokument als PNG-Bild speichern möchten.
- PageSet(1): Dies zeigt an, dass wir nur die erste Seite konvertieren.
- ImageColorMode.BlackAndWhite: Dadurch wird das Bild auf Schwarzweiß eingestellt.
- ImagePixelFormat.Format1bppIndexed: Dadurch wird das Bildformat auf 1Bpp indiziert eingestellt.

## Schritt 4: Speichern Sie das Dokument als Bild

Abschließend speichern wir das Dokument als Bild mit dem `Save` Methode der `Document` Objekt.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Abschluss

Und da haben Sie es! Mit nur wenigen Codezeilen haben Sie Ihr Word-Dokument mithilfe von Aspose.Words für .NET in ein 1Bpp-indiziertes Bild umgewandelt. Diese Methode ist unglaublich nützlich, um aus Ihren Dokumenten kontrastreiche, platzsparende Bilder zu erstellen. Jetzt können Sie dies problemlos in Ihre Projekte und Arbeitsabläufe integrieren. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist ein 1Bpp-indiziertes Bild?
Ein 1Bpp-indexiertes (1 Bit pro Pixel) Bild ist ein Schwarzweißbildformat, bei dem jedes Pixel durch ein einzelnes Bit, entweder 0 oder 1, dargestellt wird. Dieses Format ist äußerst platzsparend.

### Kann ich mehrere Seiten eines Word-Dokuments gleichzeitig konvertieren?
Ja, das können Sie. Ändern Sie die `PageSet` Eigentum in der `ImageSaveOptions` um mehrere Seiten oder das gesamte Dokument einzuschließen.

### Benötige ich eine Lizenz, um Aspose.Words für .NET zu verwenden?
Ja, Aspose.Words für .NET benötigt eine Lizenz für die volle Funktionalität. Sie erhalten eine [vorläufige Lizenz hier](https://purchase.aspose.com/temporary-license/).

### In welche anderen Bildformate kann ich mein Word-Dokument konvertieren?
Aspose.Words unterstützt verschiedene Bildformate, darunter JPEG, BMP und TIFF. Ändern Sie einfach die `SaveFormat` im `ImageSaveOptions`.

### Wo finde ich weitere Dokumentation zu Aspose.Words für .NET?
Eine ausführliche Dokumentation finden Sie auf der [Aspose.Words für .NET-Dokumentationsseite](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}