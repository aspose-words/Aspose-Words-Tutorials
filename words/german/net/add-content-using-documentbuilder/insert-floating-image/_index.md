---
title: Schwebendes Bild in Word-Dokument einfügen
linktitle: Schwebendes Bild in Word-Dokument einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET ein schwebendes Bild in ein Word-Dokument einfügen. Perfekt zum Verbessern Ihrer Dokumente.
weight: 10
url: /de/net/add-content-using-documentbuilder/insert-floating-image/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schwebendes Bild in Word-Dokument einfügen

## Einführung

Stellen Sie sich vor, Sie erstellen einen beeindruckenden Bericht oder Vorschlag, bei dem die Bilder perfekt positioniert sind und Ihren Text ergänzen. Mit Aspose.Words für .NET können Sie dies mühelos erreichen. Diese Bibliothek bietet leistungsstarke Funktionen zur Dokumentbearbeitung und ist damit eine Lösung für Entwickler. In diesem Tutorial konzentrieren wir uns auf das Einfügen eines schwebenden Bilds mithilfe der DocumentBuilder-Klasse. Egal, ob Sie ein erfahrener Entwickler sind oder gerade erst anfangen, diese Anleitung führt Sie durch jeden Schritt.

## Voraussetzungen

Bevor wir loslegen, stellen wir sicher, dass Sie alles haben, was Sie für den Einstieg benötigen:

1.  Aspose.Words für .NET: Sie können die Bibliothek herunterladen von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Visual Studio: Jede Version, die .NET-Entwicklung unterstützt.
3. Grundkenntnisse in C#: Kenntnisse der Grundlagen der C#-Programmierung sind hilfreich.
4. Bilddatei: Eine Bilddatei, die Sie einfügen möchten, beispielsweise ein Logo oder ein Bild.

## Namespaces importieren

Um Aspose.Words in Ihrem Projekt zu verwenden, müssen Sie die erforderlichen Namespaces importieren. Dies geschieht, indem Sie oben in Ihrer C#-Datei die folgenden Zeilen hinzufügen:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Nachdem diese Voraussetzungen und Namespaces erfüllt sind, können wir mit unserem Tutorial beginnen.

Lassen Sie uns den Vorgang des Einfügens eines schwebenden Bilds in ein Word-Dokument in überschaubare Schritte aufteilen. Jeder Schritt wird ausführlich erklärt, damit Sie ihn ohne Probleme nachvollziehen können.

## Schritt 1: Richten Sie Ihr Projekt ein

Erstellen Sie zunächst ein neues C#-Projekt in Visual Studio. Der Einfachheit halber können Sie eine Konsolen-App wählen.

1. Öffnen Sie Visual Studio und erstellen Sie ein neues Projekt.
2. Wählen Sie „Konsolen-App (.NET Core)“ und klicken Sie auf „Weiter“.
3. Geben Sie Ihrem Projekt einen Namen und wählen Sie einen Speicherort. Klicken Sie auf „Erstellen“.
4. Installieren Sie Aspose.Words für .NET über den NuGet-Paketmanager. Klicken Sie im Solution Explorer mit der rechten Maustaste auf Ihr Projekt, wählen Sie „NuGet-Pakete verwalten“ und suchen Sie nach „Aspose.Words“. Installieren Sie die neueste Version.

## Schritt 2: Dokument und DocumentBuilder initialisieren

Nachdem Ihr Projekt nun eingerichtet ist, initialisieren wir die Document- und DocumentBuilder-Objekte.

1.  Erstellen Sie eine neue Instanz des`Document` Klasse:

```csharp
Document doc = new Document();
```

2. Initialisieren Sie ein DocumentBuilder-Objekt:

```csharp
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Der`Document` Objekt stellt das Word-Dokument dar, und das`DocumentBuilder` hilft beim Hinzufügen von Inhalten.

## Schritt 3: Definieren Sie den Bildpfad

Geben Sie als Nächstes den Pfad zu Ihrer Bilddatei an. Stellen Sie sicher, dass Ihr Bild vom Verzeichnis Ihres Projekts aus zugänglich ist.

Definieren Sie das Bildverzeichnis und den Bilddateinamen:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
string imagePath = dataDir + "Transparent background logo.png";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem Ihr Bild gespeichert ist.

## Schritt 4: Einfügen des schwebenden Bildes

Nachdem alles eingerichtet ist, fügen wir das schwebende Bild in das Dokument ein.

 Verwenden Sie die`InsertImage` Methode der`DocumentBuilder` Klasse zum Einfügen des Bildes:

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

Dies bedeutet jeder Parameter:
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

Das Einfügen eines schwebenden Bilds in ein Word-Dokument mit Aspose.Words für .NET ist ein unkomplizierter Vorgang, wenn er in überschaubare Schritte unterteilt wird. Wenn Sie dieser Anleitung folgen, können Sie Ihren Dokumenten professionell aussehende Bilder hinzufügen und so deren visuelle Attraktivität steigern. Aspose.Words bietet eine robuste API, die die Dokumentbearbeitung zum Kinderspiel macht, egal ob Sie an Berichten, Vorschlägen oder einem anderen Dokumenttyp arbeiten.

## Häufig gestellte Fragen

### Kann ich mit Aspose.Words für .NET mehrere Bilder einfügen?

 Ja, Sie können mehrere Bilder einfügen, indem Sie den`InsertImage` Methode für jedes Bild mit den gewünschten Parametern.

### Wie ändere ich die Position des Bildes?

 Sie können die`RelativeHorizontalPosition`, `RelativeVerticalPosition`, und Offset-Parameter, um das Bild nach Bedarf zu positionieren.

### Welche anderen Umbrucharten sind für Bilder verfügbar?

 Aspose.Words unterstützt verschiedene Wrap-Typen wie`Inline`, `TopBottom`, `Tight`, `Through`und mehr. Sie können die Option auswählen, die am besten zu Ihrem Dokumentlayout passt.

### Kann ich verschiedene Bildformate verwenden?

Ja, Aspose.Words unterstützt eine Vielzahl von Bildformaten, darunter JPEG, PNG, BMP und GIF.

### Wie erhalte ich eine kostenlose Testversion von Aspose.Words für .NET?

 Sie erhalten eine kostenlose Testversion von[Kostenlose Testseite von Aspose](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
