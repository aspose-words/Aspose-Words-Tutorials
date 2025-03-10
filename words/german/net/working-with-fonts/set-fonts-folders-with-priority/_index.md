---
title: Legen Sie Schriftartenordner mit Priorität fest
linktitle: Legen Sie Schriftartenordner mit Priorität fest
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET Schriftartordner mit Priorität in Word-Dokumenten festlegen. Unser Leitfaden stellt sicher, dass Ihre Dokumente jedes Mal perfekt dargestellt werden.
weight: 10
url: /de/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Legen Sie Schriftartenordner mit Priorität fest

## Einführung

In der Welt der Dokumentbearbeitung kann das Festlegen benutzerdefinierter Schriftartordner einen großen Unterschied machen, um sicherzustellen, dass Ihre Dokumente perfekt dargestellt werden, unabhängig davon, wo sie angezeigt werden. Heute werden wir uns damit befassen, wie Sie mit Aspose.Words für .NET Schriftartordner mit Priorität in Ihren Word-Dokumenten festlegen können. Diese umfassende Anleitung führt Sie durch jeden Schritt und macht den Vorgang so reibungslos wie möglich.

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass wir alles haben, was wir brauchen. Hier ist eine kurze Checkliste:

-  Aspose.Words für .NET: Sie müssen diese Bibliothek installiert haben. Wenn Sie sie noch nicht haben, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Stellen Sie sicher, dass Sie über eine funktionierende .NET-Entwicklungsumgebung wie Visual Studio verfügen.
-  Dokumentverzeichnis: Stellen Sie sicher, dass Sie ein Verzeichnis für Ihre Dokumente haben. Für unsere Beispiele verwenden wir`"YOUR DOCUMENT DIRECTORY"` als Platzhalter für diesen Pfad.

## Namespaces importieren

Als Erstes müssen wir die erforderlichen Namespaces importieren. Diese Namespaces sind für den Zugriff auf die von Aspose.Words bereitgestellten Klassen und Methoden unerlässlich.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns nun jeden Schritt aufschlüsseln, um Schriftartordner mit Priorität festzulegen.

## Schritt 1: Richten Sie Ihre Schriftartquellen ein

Zu Beginn müssen Sie die Schriftartquellen definieren. Hier teilen Sie Aspose.Words mit, wo nach Schriftarten gesucht werden soll. Sie können mehrere Schriftartenordner angeben und sogar deren Priorität festlegen.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

In diesem Beispiel legen wir zwei Schriftartquellen fest:
- SystemFontSource: Dies ist die Standardschriftartquelle, die alle auf Ihrem System installierten Schriftarten enthält.
-  FolderFontSource: Dies ist ein benutzerdefinierter Schriftartenordner unter`C:\\MyFonts\\` . Der`true` Parameter gibt an, dass dieser Ordner rekursiv gescannt werden soll, und`1` legt seine Priorität fest.

## Schritt 2: Laden Sie Ihr Dokument

Laden Sie als Nächstes das Dokument, mit dem Sie arbeiten möchten. Stellen Sie sicher, dass sich das Dokument im angegebenen Verzeichnis befindet.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Diese Codezeile lädt ein Dokument namens`Rendering.docx` aus Ihrem Dokumentverzeichnis.

## Schritt 3: Speichern Sie Ihr Dokument mit den neuen Schrifteinstellungen

Speichern Sie abschließend Ihr Dokument. Wenn Sie das Dokument speichern, verwendet Aspose.Words die von Ihnen angegebenen Schrifteinstellungen.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

 Dadurch wird das Dokument als PDF in Ihrem Dokumentverzeichnis unter dem Namen`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich Schriftartenordner mit Priorität mithilfe von Aspose.Words für .NET eingerichtet. Durch die Angabe benutzerdefinierter Schriftartenordner und -prioritäten können Sie sicherstellen, dass Ihre Dokumente konsistent gerendert werden, unabhängig davon, wo sie angezeigt werden. Dies ist insbesondere in Umgebungen nützlich, in denen bestimmte Schriftarten nicht standardmäßig installiert sind.

## Häufig gestellte Fragen

### Warum muss ich benutzerdefinierte Schriftartordner einrichten?
Durch das Einrichten benutzerdefinierter Schriftartordner wird sichergestellt, dass Ihre Dokumente korrekt wiedergegeben werden, auch wenn sie Schriftarten verwenden, die auf dem System, auf dem sie angezeigt werden, nicht installiert sind.

### Kann ich mehrere benutzerdefinierte Schriftartordner festlegen?
Ja, Sie können mehrere Schriftartenordner angeben. Mit Aspose.Words können Sie die Priorität für jeden Ordner festlegen und so sicherstellen, dass die wichtigsten Schriftarten zuerst gefunden werden.

### Was passiert, wenn eine Schriftart in allen angegebenen Quellen fehlt?
Wenn eine Schriftart in allen angegebenen Quellen fehlt, verwendet Aspose.Words eine Ersatzschriftart, um sicherzustellen, dass das Dokument weiterhin lesbar ist.

### Kann ich die Priorität der Systemschriftarten ändern?
Die Systemschriftarten sind standardmäßig immer enthalten, Sie können jedoch ihre Priorität relativ zu Ihren benutzerdefinierten Schriftartordnern festlegen.

### Ist es möglich, Netzwerkpfade für benutzerdefinierte Schriftartordner zu verwenden?
Ja, Sie können Netzwerkpfade als benutzerdefinierte Schriftartordner angeben und so Schriftartressourcen an einem Netzwerkspeicherort zentralisieren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
