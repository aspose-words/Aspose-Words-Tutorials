---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET mehrere Schriftartenordner in Ihren Word-Dokumenten einrichten. Diese Schritt-für-Schritt-Anleitung stellt sicher, dass Ihre Dokumente genau die Schriftarten verwenden, die Sie benötigen."
"linktitle": "Schriftartenordner festlegen Mehrere Ordner"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Schriftartenordner festlegen Mehrere Ordner"
"url": "/de/net/working-with-fonts/set-fonts-folders-multiple-folders/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Schriftartenordner festlegen Mehrere Ordner

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie mehrere Schriftarten in Ihren Word-Dokumenten verwalten? Vielleicht haben Sie eine Sammlung von Schriftarten in verschiedenen Ordnern und benötigen eine Möglichkeit, diese nahtlos in Ihren Dokumenten zu verwenden. Sie haben Glück! Heute zeigen wir Ihnen, wie Sie Schriftartenordner mit Aspose.Words für .NET einrichten. Diese Anleitung führt Sie Schritt für Schritt durch den Prozess und sorgt dafür, dass Ihre Dokumente genau so aussehen, wie Sie es möchten.

## Voraussetzungen

Bevor wir beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen. Folgendes benötigen Sie:

- Aspose.Words für .NET: Falls noch nicht geschehen, laden Sie Aspose.Words für .NET herunter und installieren Sie es. Sie erhalten es [Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere .NET-kompatible Entwicklungsumgebung.
- Grundkenntnisse in C#: Ein wenig Vertrautheit mit C# wird Ihnen helfen, den Beispielen zu folgen.
- Schriftdateien: Stellen Sie sicher, dass Ihre Schriftdateien in Verzeichnissen gespeichert sind, auf die Sie leicht zugreifen können.

## Namespaces importieren

Zunächst importieren wir die erforderlichen Namespaces in Ihr C#-Projekt. Dadurch stellen wir sicher, dass Sie Zugriff auf alle benötigten Aspose.Words-Funktionen haben.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns nun mit der Schritt-für-Schritt-Anleitung zum Einrichten von Schriftartenordnern in Aspose.Words für .NET beginnen.

## Schritt 1: Laden Sie Ihr Dokument

Laden wir zunächst das Word-Dokument, mit dem Sie arbeiten möchten. Stellen Sie sicher, dass Sie den Dokumentpfad bereit haben. Für dieses Beispiel verwenden wir ein Dokument mit dem Namen „Rendering.docx“.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Hier laden wir das Dokument aus dem angegebenen Verzeichnis. Ganz einfach, oder?

## Schritt 2: FontSettings-Objekt erstellen

Als nächstes müssen wir eine `FontSettings` Objekt. Mit diesem Objekt können wir die Schriftartquellen für unser Dokument verwalten.

```csharp
FontSettings fontSettings = new FontSettings();
```

Das `FontSettings` Das Objekt hilft uns bei der Definition der zu verwendenden Schriftartordner.

## Schritt 3: Schriftartenordner festlegen

Jetzt kommt der entscheidende Teil: das Festlegen der Schriftartenordner. Hier geben Sie die Verzeichnisse an, in denen sich Ihre Schriftarten befinden. In diesem Beispiel befinden sich die Schriftarten in „C:\MyFonts“ und „D:\Misc\Fonts“.

```csharp
fontSettings.SetFontsFolders(new[] { @"C:\MyFonts\", @"D:\Misc\Fonts\" }, true);
```

Der zweite Parameter (`true`) gibt an, dass diese Ordner alle Standardschriftquellen überschreiben. Wenn Sie auch die Systemschriftquellen beibehalten möchten, können Sie eine Kombination aus `GetFontSources` Und `SetFontSources`.

## Schritt 4: Schrifteinstellungen auf das Dokument anwenden

Nachdem die Schriftartenordner festgelegt wurden, müssen wir diese Einstellungen auf unser Dokument anwenden. Dadurch wird sichergestellt, dass das Dokument beim Rendern die angegebenen Schriftarten verwendet.

```csharp
doc.FontSettings = fontSettings;
```

## Schritt 5: Speichern Sie das Dokument

Speichern wir das Dokument abschließend. Wir speichern es als PDF, um die Schriftarten in Aktion zu sehen.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersMultipleFolders.pdf");
```

Und da haben Sie es! Sie haben erfolgreich mehrere Schriftartenordner für Ihr Dokument eingerichtet.

## Abschluss

Die Verwaltung von Schriftarten in Ihren Dokumenten kann eine gewaltige Aufgabe sein, aber mit Aspose.Words für .NET ist es ein Kinderspiel! Mit diesen einfachen Schritten können Sie sicherstellen, dass Ihre Dokumente professionell aussehen und genau die Schriftarten verwenden, die Sie benötigen. Egal, ob Sie an einem Projekt arbeiten, das ein bestimmtes Branding erfordert, oder einfach mehr Kontrolle über das Erscheinungsbild Ihres Dokuments wünschen – das Anlegen von Schriftartenordnern ist eine lohnende Fähigkeit.

## Häufig gestellte Fragen

### Kann ich Netzwerkpfade für Schriftartenordner verwenden?
Ja, Sie können Netzwerkpfade für Ihre Schriftartenordner verwenden. Stellen Sie lediglich sicher, dass die Pfade von Ihrer Anwendung aus zugänglich sind.

### Was passiert, wenn in den angegebenen Ordnern eine Schriftart fehlt?
Wenn eine Schriftart fehlt, greift Aspose.Words auf die angegebene Standardschriftart zurück oder verwendet eine Ersatzschriftart.

### Kann ich Schriftartenordner hinzufügen, ohne Systemschriftarten zu überschreiben?
Absolut! Verwenden `FontSettings.GetFontSources` um vorhandene Quellen abzurufen und sie mit Ihren benutzerdefinierten Ordnern zu kombinieren, indem Sie `FontSettings.SetFontSources`.

### Gibt es eine Begrenzung für die Anzahl der Schriftartenordner, die ich hinzufügen kann?
Es gibt keine strikte Begrenzung für die Anzahl der Schriftartenordner. Achten Sie jedoch auf die Leistung, da mehr Ordner die Ladezeiten der Schriftarten verlängern können.

### Wie kann ich überprüfen, welche Schriftarten in meinem Dokument verwendet werden?
Sie können die `FontSettings.GetFontsSources` Methode zum Abrufen und Überprüfen der aktuell für Ihr Dokument festgelegten Schriftartquellen.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}