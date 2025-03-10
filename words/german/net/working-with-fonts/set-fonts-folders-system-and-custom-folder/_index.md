---
title: Legen Sie die Schriftartenordner System und benutzerdefinierte Ordner fest
linktitle: Legen Sie die Schriftartenordner System und benutzerdefinierte Ordner fest
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET System- und benutzerdefinierte Schriftartordner in Word-Dokumenten festlegen und so sicherstellen, dass Ihre Dokumente in verschiedenen Umgebungen korrekt angezeigt werden.
weight: 10
url: /de/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Legen Sie die Schriftartenordner System und benutzerdefinierte Ordner fest

## Einführung

Stellen Sie sich vor, Sie erstellen ein Dokument mit einem einzigartigen Schriftstil und stellen dann fest, dass die Schriftarten auf einem anderen Computer nicht richtig angezeigt werden. Frustrierend, oder? Hier kommt die Konfiguration von Schriftartordnern ins Spiel. Mit Aspose.Words für .NET können Sie System- und benutzerdefinierte Schriftartordner definieren, um sicherzustellen, dass Ihre Dokumente immer wie beabsichtigt aussehen. Sehen wir uns an, wie Sie dies erreichen können.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

-  Aspose.Words für .NET-Bibliothek: Falls noch nicht geschehen, laden Sie sie herunter[Hier](https://releases.aspose.com/words/net/).
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

Lassen Sie uns den Vorgang nun in einfache Schritte unterteilen.

## Schritt 1: Dokument laden

 Laden Sie zunächst Ihr Word-Dokument in eine Aspose.Words`Document` Objekt. In diesem Dokument möchten Sie die Schriftartordner festlegen.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 2: Initialisieren Sie die Schrifteinstellungen

 Erstellen Sie eine neue Instanz von`FontSettings`. Mit diesem Objekt können Sie Schriftartquellen verwalten.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Schritt 3: Systemschriftartenquellen abrufen

Rufen Sie die Standard-Systemschriftartenquellen ab. Auf einem Windows-Rechner umfasst dies normalerweise die "Windows\Fonts\"-Verzeichnis.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

## Schritt 4: Einen benutzerdefinierten Schriftartenordner hinzufügen

Fügen Sie einen benutzerdefinierten Ordner hinzu, der Ihre zusätzlichen Schriftarten enthält. Dies ist nützlich, wenn Sie bestimmte Schriftarten haben, die nicht im Systemschriftartenverzeichnis installiert sind.

```csharp
FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);
```

## Schritt 5: Schriftartquellen aktualisieren

 Konvertieren Sie die Liste der Schriftquellen zurück in ein Array und setzen Sie es auf`FontSettings` Objekt.

```csharp
FontSourceBase[] updatedFontSources = fontSources.ToArray();
fontSettings.SetFontsSources(updatedFontSources);
```

## Schritt 6: Schrifteinstellungen auf Dokument anwenden

 Zum Schluss wenden Sie die konfigurierten`FontSettings` zu Ihrem Dokument und speichern Sie es im gewünschten Format, beispielsweise PDF.

```csharp
doc.FontSettings = fontSettings;
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersSystemAndCustomFolder.pdf");
```

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie sicherstellen, dass Ihre Word-Dokumente die richtigen Schriftarten verwenden, egal ob es sich um Systemschriftarten oder benutzerdefinierte Schriftarten handelt, die in einem bestimmten Verzeichnis gespeichert sind. Diese Einrichtung trägt dazu bei, die Integrität des Erscheinungsbilds Ihres Dokuments in verschiedenen Umgebungen aufrechtzuerhalten.

## Häufig gestellte Fragen

### Was passiert, wenn eine Schriftart sowohl im System- als auch im benutzerdefinierten Ordner fehlt?

Aspose.Words verwendet eine Standardschriftart, um die fehlende Schriftart zu ersetzen und so sicherzustellen, dass das Dokument lesbar bleibt.

### Kann ich mehrere benutzerdefinierte Schriftartordner hinzufügen?

 Ja, Sie können mehrere benutzerdefinierte Schriftartordner hinzufügen, indem Sie den Erstellungsprozess wiederholen.`FolderFontSource` -Objekte und deren Hinzufügen zur Liste der Schriftartquellen.

### Ist es möglich, Netzwerkpfade für benutzerdefinierte Schriftartordner zu verwenden?

 Ja, Sie können einen Netzwerkpfad angeben im`FolderFontSource` Konstruktor.

### Welche Dateiformate unterstützt Aspose.Words zum Speichern von Dokumenten?

Aspose.Words unterstützt verschiedene Formate, darunter DOCX, PDF, HTML und mehr.

### Wie gehe ich mit Benachrichtigungen zur Schriftartersetzung um?

 Sie können Benachrichtigungen über Schriftartenersetzungen verwalten, indem Sie`FontSettings` Klasse`FontSubstitutionWarning`Ereignis.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
