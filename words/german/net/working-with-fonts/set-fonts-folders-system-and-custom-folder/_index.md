---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET System- und benutzerdefinierte Schriftartordner in Word-Dokumenten festlegen und so sicherstellen, dass Ihre Dokumente in verschiedenen Umgebungen korrekt angezeigt werden."
"linktitle": "Legen Sie das System und den benutzerdefinierten Ordner für Schriftartenordner fest"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Legen Sie das System und den benutzerdefinierten Ordner für Schriftartenordner fest"
"url": "/de/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Legen Sie das System und den benutzerdefinierten Ordner für Schriftartenordner fest

## Einführung

Stellen Sie sich vor, Sie erstellen ein Dokument mit einem einzigartigen Schriftstil und stellen dann fest, dass die Schriftarten auf einem anderen Rechner nicht korrekt angezeigt werden. Frustrierend, oder? Hier kommt die Konfiguration von Schriftartenordnern ins Spiel. Mit Aspose.Words für .NET können Sie System- und benutzerdefinierte Schriftartenordner definieren, um sicherzustellen, dass Ihre Dokumente immer wie gewünscht aussehen. Sehen wir uns an, wie Sie das erreichen können.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

- Aspose.Words für .NET-Bibliothek: Falls noch nicht geschehen, laden Sie sie herunter [Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Eine IDE wie Visual Studio.
- Grundkenntnisse in C#: Wenn Sie mit C# vertraut sind, können Sie den Codebeispielen leichter folgen.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns den Prozess nun in einfache Schritte unterteilen.

## Schritt 1: Laden Sie das Dokument

Laden Sie zunächst Ihr Word-Dokument in ein Aspose.Words `Document` Objekt. In diesem Dokument möchten Sie die Schriftartordner festlegen.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 2: Initialisieren Sie die Schriftarteinstellungen

Erstellen Sie eine neue Instanz von `FontSettings`. Mit diesem Objekt können Sie Schriftartquellen verwalten.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Schritt 3: Abrufen der Systemschriftquellen

Ruft die Standard-Systemschriftquellen ab. Auf einem Windows-Computer umfasst dies normalerweise das Verzeichnis "Windows\Fonts".

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Schritt 4: Fügen Sie einen benutzerdefinierten Schriftartenordner hinzu

Fügen Sie einen benutzerdefinierten Ordner hinzu, der Ihre zusätzlichen Schriftarten enthält. Dies ist nützlich, wenn Sie bestimmte Schriftarten haben, die nicht im Systemschriftartenverzeichnis installiert sind.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Schritt 5: Schriftartquellen aktualisieren

Konvertieren Sie die Liste der Schriftartquellen zurück in ein Array und setzen Sie es auf `FontSettings` Objekt.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Schritt 6: Schrifteinstellungen auf Dokument anwenden

Abschließend wenden Sie die konfigurierten `FontSettings` zu Ihrem Dokument und speichern Sie es im gewünschten Format, beispielsweise PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Abschluss

Und fertig! Mit diesen Schritten stellen Sie sicher, dass Ihre Word-Dokumente die richtigen Schriftarten verwenden, egal ob es sich um Systemschriftarten oder benutzerdefinierte Schriftarten handelt, die in einem bestimmten Verzeichnis gespeichert sind. So bleibt die Integrität des Erscheinungsbilds Ihres Dokuments in verschiedenen Umgebungen erhalten.

## Häufig gestellte Fragen

### Was passiert, wenn eine Schriftart sowohl im Systemordner als auch im benutzerdefinierten Ordner fehlt?

Aspose.Words verwendet eine Standardschriftart, um die fehlende Schriftart zu ersetzen und so sicherzustellen, dass das Dokument lesbar bleibt.

### Kann ich mehrere benutzerdefinierte Schriftartenordner hinzufügen?

Ja, Sie können mehrere benutzerdefinierte Schriftartenordner hinzufügen, indem Sie den Vorgang der Erstellung wiederholen `FolderFontSource` Objekte und fügen Sie sie der Liste der Schriftartquellen hinzu.

### Ist es möglich, Netzwerkpfade für benutzerdefinierte Schriftartenordner zu verwenden?

Ja, Sie können einen Netzwerkpfad angeben in der `FolderFontSource` Konstruktor.

### Welche Dateiformate unterstützt Aspose.Words zum Speichern von Dokumenten?

Aspose.Words unterstützt verschiedene Formate, darunter DOCX, PDF, HTML und mehr.

### Wie gehe ich mit Benachrichtigungen zur Schriftartersetzung um?

Sie können Benachrichtigungen zur Schriftartersetzung verwalten, indem Sie das `FontSettings` Klasse `FontSubstitutionWarning` Ereignis.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}