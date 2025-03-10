---
title: Liste der verfügbaren Schriftarten abrufen
linktitle: Liste der verfügbaren Schriftarten abrufen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: In diesem ausführlichen Schritt-für-Schritt-Tutorial erfahren Sie, wie Sie mit Aspose.Words für .NET eine Liste der verfügbaren Schriftarten erhalten. Verbessern Sie Ihre Fähigkeiten im Bereich der Schriftartenverwaltung.
weight: 10
url: /de/net/working-with-fonts/get-list-of-available-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Liste der verfügbaren Schriftarten abrufen

## Einführung

Hatten Sie schon einmal Probleme, die Schriftarten in Ihren Word-Dokumenten zu verwalten? Wenn Sie ein .NET-Entwickler sind, ist Aspose.Words für .NET die Rettung für Sie! Diese leistungsstarke Bibliothek hilft Ihnen nicht nur dabei, Word-Dokumente programmgesteuert zu erstellen und zu bearbeiten, sondern bietet auch umfangreiche Funktionen zur Schriftartenverwaltung. In dieser Anleitung führen wir Sie Schritt für Schritt durch die Anleitung, wie Sie mit Aspose.Words für .NET eine Liste der verfügbaren Schriftarten erhalten. Wir unterteilen es in leicht verständliche Schritte, damit Sie es problemlos befolgen können. Lassen Sie uns also loslegen und die Schriftartenverwaltung zum Kinderspiel machen!

## Voraussetzungen

Bevor wir beginnen, benötigen Sie einige Dinge:

-  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET installiert haben. Sie können sie hier herunterladen:[Hier](https://releases.aspose.com/words/net/).
- Visual Studio: Dieses Beispiel verwendet Visual Studio als Entwicklungsumgebung.
- .NET Framework: Stellen Sie sicher, dass .NET Framework auf Ihrem Computer installiert ist.
- Dokumentverzeichnis: Ein Verzeichnispfad, in dem Ihre Dokumente gespeichert sind.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Schritt 1: Initialisieren Sie die Schrifteinstellungen

Der erste Schritt besteht darin, die Schriftarteinstellungen zu initialisieren. Dadurch können Sie die Schriftartquellen für Ihre Dokumente verwalten.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: Mit dieser Klasse werden die Einstellungen für Schriftartersetzung und Schriftartquellen festgelegt.
- fontSources: Wir erstellen eine Liste vorhandener Schriftquellen aus den aktuellen Schrifteinstellungen.

## Schritt 2: Dokumentverzeichnis definieren

Geben Sie als Nächstes den Pfad zu Ihrem Dokumentverzeichnis an. Hier sucht Aspose.Words nach Schriftarten.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

-  dataDir: Diese Zeichenfolge enthält den Pfad zum Verzeichnis, in dem sich Ihre Schriftarten befinden. Ersetzen Sie`"YOUR DOCUMENT DIRECTORY"` mit dem tatsächlichen Pfad.

## Schritt 3: Benutzerdefinierten Schriftartordner hinzufügen

Fügen Sie jetzt eine neue Ordnerquelle hinzu, um Aspose.Words anzuweisen, in diesem Ordner nach Schriftarten zu suchen.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Diese Klasse repräsentiert eine Ordner-Schriftartquelle. Der zweite Parameter (`true`) gibt an, ob rekursiv in Unterordnern nach Schriftarten gesucht werden soll.

## Schritt 4: Schriftartquellen aktualisieren

Fügen Sie den benutzerdefinierten Schriftartordner zur Liste der vorhandenen Schriftartquellen hinzu und aktualisieren Sie die Schriftarteinstellungen.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): Fügt den benutzerdefinierten Schriftartenordner zu den vorhandenen Schriftartenquellen hinzu.
- updatedFontSources: Konvertiert die Liste der Schriftquellen in ein Array.

## Schritt 5: Schriftarten abrufen und anzeigen

Rufen Sie abschließend die verfügbaren Schriftarten ab und zeigen Sie deren Details an.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): Ruft die Liste der verfügbaren Schriftarten aus der ersten Schriftartquelle in der aktualisierten Liste ab.
-  fontInfo: Eine Instanz von`PhysicalFontInfo` mit Details zu jeder Schriftart.

## Abschluss

Herzlichen Glückwunsch! Sie haben mit Aspose.Words für .NET erfolgreich eine Liste der verfügbaren Schriftarten abgerufen. Dieses Tutorial hat Sie durch jeden Schritt geführt, von der Initialisierung der Schriftarteinstellungen bis zur Anzeige der Schriftartdetails. Mit diesem Wissen können Sie jetzt Schriftarten in Ihren Word-Dokumenten problemlos verwalten. Denken Sie daran, dass Aspose.Words für .NET ein leistungsstarkes Tool ist, das Ihre Dokumentverarbeitungsfunktionen erheblich verbessern kann. Entdecken Sie also weitere Funktionen, um Ihren Entwicklungsprozess noch effizienter zu gestalten.

## Häufig gestellte Fragen

### Kann ich Aspose.Words für .NET mit anderen .NET-Frameworks verwenden?
Ja, Aspose.Words für .NET ist mit verschiedenen .NET-Frameworks kompatibel, einschließlich .NET Core und .NET 5+.

### Wie installiere ich Aspose.Words für .NET?
Sie können es über den NuGet Package Manager in Visual Studio installieren, indem Sie nach „Aspose.Words“ suchen.

### Ist es möglich, mehrere benutzerdefinierte Schriftartordner hinzuzufügen?
 Ja, Sie können mehrere benutzerdefinierte Schriftartenordner hinzufügen, indem Sie mehrere erstellen`FolderFontSource` Instanzen und Hinzufügen dieser zur Liste der Schriftartquellen.

### Kann ich Schriftdetails aus einer bestimmten Schriftquelle abrufen?
 Ja, Sie können Schriftartdetails aus jeder Schriftartquelle abrufen, indem Sie den Index der Schriftartquelle im`updatedFontSources` -Array.

### Unterstützt Aspose.Words für .NET die Schriftartenersetzung?
Ja, es unterstützt die Schriftartersetzung, um sicherzustellen, dass Text auch dann korrekt wiedergegeben wird, wenn die Originalschriftart nicht verfügbar ist.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
