---
"description": "Erfahren Sie in dieser detaillierten Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET ein schwebendes Bild in ein Word-Dokument einfügen. Perfekt zur Verbesserung Ihrer Dokumente."
"linktitle": "Schwebendes Bild in Word-Dokument einfügen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Schwebendes Bild in Word-Dokument einfügen"
"url": "/de/net/add-content-using-documentbuilder/insert-floating-image/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Schwebendes Bild in Word-Dokument einfügen

## Einführung

Stellen Sie sich vor, Sie erstellen einen beeindruckenden Bericht oder Vorschlag, bei dem Bilder perfekt positioniert sind und Ihren Text ergänzen. Mit Aspose.Words für .NET gelingt Ihnen dies mühelos. Diese Bibliothek bietet leistungsstarke Funktionen zur Dokumentbearbeitung und ist damit eine ideale Lösung für Entwickler. In diesem Tutorial konzentrieren wir uns auf das Einfügen eines schwebenden Bildes mithilfe der Klasse DocumentBuilder. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, diese Anleitung führt Sie Schritt für Schritt durch die einzelnen Schritte.

## Voraussetzungen

Bevor wir loslegen, stellen wir sicher, dass Sie alles haben, was Sie für den Einstieg benötigen:

1. Aspose.Words für .NET: Sie können die Bibliothek von der [Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Visual Studio: Jede Version, die .NET-Entwicklung unterstützt.
3. Grundkenntnisse in C#: Kenntnisse der Grundlagen der C#-Programmierung sind hilfreich.
4. Bilddatei: Eine Bilddatei, die Sie einfügen möchten, beispielsweise ein Logo oder ein Bild.

## Namespaces importieren

Um Aspose.Words in Ihrem Projekt zu verwenden, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie dazu die folgenden Zeilen am Anfang Ihrer C#-Datei hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Wenn diese Voraussetzungen und Namespaces erfüllt sind, können wir mit unserem Tutorial beginnen.

Wir unterteilen den Vorgang zum Einfügen eines schwebenden Bildes in ein Word-Dokument in überschaubare Schritte. Jeder Schritt wird detailliert erklärt, damit Sie ihn problemlos nachvollziehen können.

## Schritt 1: Richten Sie Ihr Projekt ein

Erstellen Sie zunächst ein neues C#-Projekt in Visual Studio. Der Einfachheit halber können Sie eine Konsolen-App wählen.

1. Öffnen Sie Visual Studio und erstellen Sie ein neues Projekt.
2. Wählen Sie „Konsolen-App (.NET Core)“ und klicken Sie auf „Weiter“.
3. Benennen Sie Ihr Projekt und wählen Sie einen Speicherort. Klicken Sie auf „Erstellen“.
4. Installieren Sie Aspose.Words für .NET über den NuGet-Paketmanager. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, wählen Sie „NuGet-Pakete verwalten“ und suchen Sie nach „Aspose.Words“. Installieren Sie die neueste Version.

## Schritt 2: Dokument und DocumentBuilder initialisieren

Nachdem Ihr Projekt nun eingerichtet ist, initialisieren wir die Document- und DocumentBuilder-Objekte.

1. Erstellen Sie eine neue Instanz des `Document` Klasse:

```csharp
Document doc = new Document();
```

2. Initialisieren Sie ein DocumentBuilder-Objekt:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

Der `Document` Objekt stellt das Word-Dokument dar, und das `DocumentBuilder` hilft beim Hinzufügen von Inhalten.

## Schritt 3: Definieren Sie den Bildpfad

Geben Sie anschließend den Pfad zu Ihrer Bilddatei an. Stellen Sie sicher, dass Ihr Bild vom Projektverzeichnis aus zugänglich ist.

Definieren Sie das Bildverzeichnis und den Bilddateinamen:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

Ersetzen `"YOUR DOCUMENT DIRECTORY"` mit dem tatsächlichen Pfad, in dem Ihr Bild gespeichert ist.

## Schritt 4: Einfügen des schwebenden Bildes

Nachdem alles eingerichtet ist, fügen wir das schwebende Bild in das Dokument ein.

Verwenden Sie die `InsertImage` Methode der `DocumentBuilder` Klasse zum Einfügen des Bildes:

```csharp
builder.InsertImage(imagePath,
   RelativeHorizontalPosition.Margin,
   100,
   RelativeVerticalPosition.Margin,
   100,
   200,
   100,
   WrapType.Square);
```

Die einzelnen Parameter haben folgende Bedeutung:
- `imagePath`: Der Pfad zu Ihrer Bilddatei.
- `RelativeHorizontalPosition.Margin`: Die horizontale Position relativ zum Rand.
- `100`: Der horizontale Versatz vom Rand (in Punkten).
- `RelativeVerticalPosition.Margin`: Die vertikale Position relativ zum Rand.
- `100`: Der vertikale Versatz vom Rand (in Punkten).
- `200`: Die Breite des Bildes (in Punkten).
- `100`: Die Höhe des Bildes (in Punkten).
- `WrapType.Square`: Der Textumbruchstil um das Bild.

## Schritt 5: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend am gewünschten Ort.

1. Geben Sie den Ausgabedateipfad an:

```csharp
string outputPath = dataDir + "AddContentUsingDocumentBuilder.InsertFloatingImage.docx";
```

2. Speichern Sie das Dokument:

```csharp
doc.Save(outputPath);
```

Ihr Word-Dokument mit dem schwebenden Bild ist jetzt fertig!

## Abschluss

Das Einfügen eines schwebenden Bilds in ein Word-Dokument mit Aspose.Words für .NET ist ein unkomplizierter Vorgang, wenn er in überschaubare Schritte unterteilt ist. Mit dieser Anleitung können Sie Ihren Dokumenten professionell aussehende Bilder hinzufügen und so deren visuelle Attraktivität steigern. Aspose.Words bietet eine robuste API, die die Dokumentbearbeitung zum Kinderspiel macht, egal ob Sie an Berichten, Vorschlägen oder anderen Dokumenttypen arbeiten.

## Häufig gestellte Fragen

### Kann ich mit Aspose.Words für .NET mehrere Bilder einfügen?

Ja, Sie können mehrere Bilder einfügen, indem Sie die `InsertImage` Methode für jedes Bild mit den gewünschten Parametern.

### Wie ändere ich die Position des Bildes?

Sie können die `RelativeHorizontalPosition`, `RelativeVerticalPosition`, und Offset-Parameter, um das Bild nach Bedarf zu positionieren.

### Welche anderen Umbrucharten sind für Bilder verfügbar?

Aspose.Words unterstützt verschiedene Wrap-Typen wie `Inline`, `TopBottom`, `Tight`, `Through`und mehr. Sie können die Option auswählen, die am besten zu Ihrem Dokumentlayout passt.

### Kann ich verschiedene Bildformate verwenden?

Ja, Aspose.Words unterstützt eine Vielzahl von Bildformaten, darunter JPEG, PNG, BMP und GIF.

### Wie erhalte ich eine kostenlose Testversion von Aspose.Words für .NET?

Sie erhalten eine kostenlose Testversion von der [Kostenlose Testseite von Aspose](https://releases.aspose.com/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}