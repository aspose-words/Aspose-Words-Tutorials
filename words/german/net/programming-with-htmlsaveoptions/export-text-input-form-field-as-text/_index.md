---
"description": "Erfahren Sie in dieser umfassenden Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Texteingabeformularfelder als einfachen Text exportieren."
"linktitle": "Texteingabeformularfeld als Text exportieren"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Texteingabeformularfeld als Text exportieren"
"url": "/de/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Texteingabeformularfeld als Text exportieren

## Einführung

Tauchen Sie ein in die Welt von Aspose.Words für .NET? Eine hervorragende Wahl! Wenn Sie lernen möchten, wie Sie ein Texteingabeformular als Text exportieren, sind Sie hier genau richtig. Egal, ob Sie gerade erst anfangen oder Ihre Kenntnisse auffrischen möchten – dieser Leitfaden führt Sie durch alles, was Sie wissen müssen. Los geht’s!

## Voraussetzungen

Bevor wir ins Detail gehen, stellen wir sicher, dass Sie alles haben, was Sie brauchen, um reibungslos mitmachen zu können:

- Aspose.Words für .NET: Laden Sie die neueste Version herunter und installieren Sie sie von [Hier](https://releases.aspose.com/words/net/).
- IDE: Visual Studio oder jede C#-Entwicklungsumgebung.
- Grundlegende C#-Kenntnisse: Verständnis der grundlegenden C#-Syntax und der Konzepte der objektorientierten Programmierung.
- Dokument: Ein Beispiel-Word-Dokument (`Rendering.docx`) mit Texteingabeformularfeldern.

## Namespaces importieren

Zunächst müssen Sie die erforderlichen Namespaces importieren. Diese sind sozusagen die Bausteine, die für einen reibungslosen Ablauf sorgen.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Gut, jetzt, da wir unsere Namespaces bereit haben, können wir loslegen!

## Schritt 1: Einrichten des Projekts

Bevor wir uns mit dem Code befassen, stellen wir sicher, dass unser Projekt richtig eingerichtet ist.

## Erstellen des Projekts

1. Öffnen Sie Visual Studio: Öffnen Sie zunächst Visual Studio oder Ihre bevorzugte C#-Entwicklungsumgebung.
2. Neues Projekt erstellen: Navigieren Sie zu `File > New > Project`Wählen `Console App (.NET Core)` oder jeder andere relevante Projekttyp.
3. Benennen Sie Ihr Projekt: Geben Sie Ihrem Projekt einen aussagekräftigen Namen, etwa wie `AsposeWordsExportExample`.

## Aspose.Words hinzufügen

1. NuGet-Pakete verwalten: Klicken Sie mit der rechten Maustaste auf Ihr Projekt im Solution Explorer und wählen Sie `Manage NuGet Packages`.
2. Suchen Sie nach Aspose.Words: Suchen Sie im NuGet-Paket-Manager nach `Aspose.Words`.
3. Installieren Sie Aspose.Words: Klicken Sie auf `Install` um die Aspose.Words-Bibliothek zu Ihrem Projekt hinzuzufügen.

## Schritt 2: Laden Sie das Word-Dokument

Nachdem unser Projekt nun eingerichtet ist, laden wir das Word-Dokument, das die Text-Eingabeformularfelder enthält.

1. Geben Sie das Dokumentverzeichnis an: Definieren Sie den Pfad zum Verzeichnis, in dem Ihr Dokument gespeichert ist.
2. Laden Sie das Dokument: Verwenden Sie die `Document` Klasse, um Ihr Word-Dokument zu laden.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 3: Vorbereiten des Exportverzeichnisses

Bevor wir exportieren, stellen wir sicher, dass unser Exportverzeichnis bereit ist. Hier werden unsere HTML-Datei und Bilder gespeichert.

1. Definieren Sie das Exportverzeichnis: Geben Sie den Pfad an, in dem die exportierten Dateien gespeichert werden.
2. Überprüfen und bereinigen Sie das Verzeichnis: Stellen Sie sicher, dass das Verzeichnis vorhanden und leer ist.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Schritt 4: Speicheroptionen konfigurieren

Und hier geschieht die Magie. Wir müssen unsere Speicheroptionen so einrichten, dass das Texteingabeformularfeld als einfacher Text exportiert wird.

1. Speichern-Optionen erstellen: Initialisieren Sie eine neue `HtmlSaveOptions` Objekt.
2. Textexportoption festlegen: Konfigurieren Sie die `ExportTextInputFormFieldAsText` Eigentum zu `true`.
3. Bilderordner festlegen: Definieren Sie den Ordner, in dem die Bilder gespeichert werden.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Schritt 5: Speichern Sie das Dokument als HTML

Abschließend speichern wir das Word-Dokument mit den von uns konfigurierten Speicheroptionen als HTML-Datei.

1. Definieren Sie den Ausgabepfad: Geben Sie den Pfad an, in dem die HTML-Datei gespeichert wird.
2. Speichern Sie das Dokument: Verwenden Sie die `Save` Methode der `Document` Klasse zum Exportieren des Dokuments.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Abschluss

Und da haben Sie es! Sie haben ein Texteingabeformular erfolgreich mit Aspose.Words für .NET als Klartext exportiert. Diese Anleitung sollte Ihnen eine klare Schritt-für-Schritt-Anleitung zur Bewältigung dieser Aufgabe gegeben haben. Denken Sie daran: Übung macht den Meister. Experimentieren Sie also weiter mit verschiedenen Optionen und Einstellungen, um zu sehen, was Sie sonst noch mit Aspose.Words erreichen können.

## Häufig gestellte Fragen

### Kann ich mit derselben Methode andere Arten von Formularfeldern exportieren?

Ja, Sie können andere Formularfeldtypen exportieren, indem Sie verschiedene Eigenschaften des `HtmlSaveOptions` Klasse.

### Was ist, wenn mein Dokument Bilder enthält?

Die Bilder werden im angegebenen Bilderordner gespeichert. Stellen Sie sicher, dass Sie die `ImagesFolder` Eigentum in der `HtmlSaveOptions`.

### Benötige ich eine Lizenz für Aspose.Words?

Ja, Sie können eine kostenlose Testversion erhalten [Hier](https://releases.aspose.com/) oder eine Lizenz erwerben [Hier](https://purchase.aspose.com/buy).

### Kann ich das exportierte HTML anpassen?

Absolut! Aspose.Words bietet verschiedene Optionen zur Anpassung der HTML-Ausgabe. Siehe die [Dokumentation](https://reference.aspose.com/words/net/) für weitere Details.

### Ist Aspose.Words mit .NET Core kompatibel?

Ja, Aspose.Words ist mit .NET Core, .NET Framework und anderen .NET-Plattformen kompatibel.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}