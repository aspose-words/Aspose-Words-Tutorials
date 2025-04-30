---
"description": "Erfahren Sie in diesem Schritt-für-Schritt-Tutorial, wie Sie Schriftartenordner für die Standardinstanz in Aspose.Words für .NET festlegen. Passen Sie Ihre Word-Dokumente mühelos an."
"linktitle": "Standardinstanz für Schriftartenordner festlegen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Standardinstanz für Schriftartenordner festlegen"
"url": "/de/net/working-with-fonts/set-fonts-folders-default-instance/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Standardinstanz für Schriftartenordner festlegen

## Einführung

Hallo Programmierer! Wenn Sie mit Word-Dokumenten in .NET arbeiten, wissen Sie wahrscheinlich, wie wichtig die richtigen Schriftarten sind. Heute zeigen wir Ihnen, wie Sie mit Aspose.Words für .NET Schriftartenordner für die Standardinstanz einrichten. Stellen Sie sich vor, Sie hätten alle Ihre benutzerdefinierten Schriftarten zur Hand und Ihre Dokumente sehen genau so aus, wie Sie es sich vorstellen. Klingt super, oder? Los geht's!

## Voraussetzungen

Bevor wir in die Einzelheiten eintauchen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:
- Aspose.Words für .NET: Stellen Sie sicher, dass die Bibliothek installiert ist. Falls nicht, können Sie [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere .NET-kompatible IDE.
- Grundkenntnisse in C#: Sie sollten mit der C#-Programmierung vertraut sein.
- Schriftartenordner: Ein Verzeichnis, das Ihre benutzerdefinierten Schriftarten enthält.

## Namespaces importieren

Zunächst importieren wir die erforderlichen Namespaces. Dies erleichtert den Zugriff auf die Klassen und Methoden, die zum Festlegen des Schriftartenordners erforderlich sind.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns den Prozess in einfache, verständliche Schritte unterteilen.

## Schritt 1: Definieren des Datenverzeichnisses

Jede große Reise beginnt mit einem einzigen Schritt. Unsere beginnt mit der Definition des Verzeichnisses, in dem Ihr Dokument gespeichert ist. Hier sucht Aspose.Words nach Ihrem Word-Dokument.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersetzen Sie hier `"YOUR DOCUMENT DIRECTORY"` mit dem tatsächlichen Pfad zu Ihrem Dokumentverzeichnis. Hier befindet sich Ihr Quelldokument und hier wird die Ausgabe gespeichert.

## Schritt 2: Legen Sie den Schriftartenordner fest

Nun teilen wir Aspose.Words mit, wo Ihre benutzerdefinierten Schriftarten zu finden sind. Dies geschieht durch die Festlegung des Schriftartenordners mit dem `FontSettings.DefaultInstance.SetFontsFolder` Verfahren.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

In dieser Zeile, `"C:\\MyFonts\\"` ist der Pfad zu Ihrem benutzerdefinierten Schriftartenordner. Der zweite Parameter, `true`, gibt an, dass die Schriftarten in diesem Ordner rekursiv gescannt werden sollen.

## Schritt 3: Laden Sie Ihr Dokument

Nachdem der Ordner „Fonts“ eingerichtet ist, laden Sie Ihr Word-Dokument in Aspose.Words. Dies geschieht mit dem `Document` Klasse.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Hier, `dataDir + "Rendering.docx"` bezieht sich auf den vollständigen Pfad Ihres Word-Dokuments. Stellen Sie sicher, dass sich Ihr Dokument im angegebenen Verzeichnis befindet.

## Schritt 4: Speichern Sie das Dokument

Der letzte Schritt besteht darin, Ihr Dokument nach dem Festlegen des Schriftartenordners zu speichern. Dadurch wird sichergestellt, dass Ihre benutzerdefinierten Schriftarten in der Ausgabe korrekt angewendet werden.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Diese Zeile speichert Ihr Dokument als PDF mit den angewendeten benutzerdefinierten Schriftarten. Die Ausgabedatei befindet sich im selben Verzeichnis wie Ihr Quelldokument.

## Abschluss

Und da haben Sie es! Das Einrichten von Schriftartenordnern für die Standardinstanz in Aspose.Words für .NET ist kinderleicht, wenn Sie es in einfache Schritte unterteilen. Mit dieser Anleitung stellen Sie sicher, dass Ihre Word-Dokumente genau so aussehen, wie Sie es möchten, mit all Ihren benutzerdefinierten Schriftarten. Probieren Sie es aus und bringen Sie Ihre Dokumente zum Strahlen!

## Häufig gestellte Fragen

### Kann ich mehrere Schriftartenordner einrichten?
Ja, Sie können mehrere Schriftartenordner festlegen, indem Sie die `SetFontsFolders` Methode, die ein Array von Ordnerpfaden akzeptiert.

### Welche Dateiformate unterstützt Aspose.Words zum Speichern von Dokumenten?
Aspose.Words unterstützt verschiedene Formate, darunter DOCX, PDF, HTML, EPUB und mehr.

### Ist es möglich, Online-Schriftarten in Aspose.Words zu verwenden?
Nein, Aspose.Words unterstützt derzeit nur lokale Schriftdateien.

### Wie kann ich sicherstellen, dass meine benutzerdefinierten Schriftarten in die gespeicherte PDF-Datei eingebettet sind?
Durch die Einstellung der `FontSettings` korrekt und stellt sicher, dass die Schriftarten verfügbar sind. Aspose.Words bettet sie in die PDF-Ausgabe ein.

### Was passiert, wenn eine Schriftart im angegebenen Ordner nicht gefunden wird?
Aspose.Words verwendet eine Ersatzschriftart, wenn die angegebene Schriftart nicht gefunden wird.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}