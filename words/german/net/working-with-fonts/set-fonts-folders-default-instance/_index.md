---
title: Standardinstanz für Schriftartenordner festlegen
linktitle: Standardinstanz für Schriftartenordner festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem Schritt-für-Schritt-Tutorial, wie Sie Schriftartenordner für die Standardinstanz in Aspose.Words für .NET festlegen. Passen Sie Ihre Word-Dokumente mühelos an.
weight: 10
url: /de/net/working-with-fonts/set-fonts-folders-default-instance/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Standardinstanz für Schriftartenordner festlegen

## Einführung

Hallo, Programmierkollege! Wenn Sie mit Word-Dokumenten in .NET arbeiten, wissen Sie wahrscheinlich, wie wichtig es ist, dass Ihre Schriftarten genau richtig sind. Heute tauchen wir ein in die Einrichtung von Schriftartenordnern für die Standardinstanz mit Aspose.Words für .NET. Stellen Sie sich vor, Sie hätten alle Ihre benutzerdefinierten Schriftarten zur Hand und Ihre Dokumente würden genau so aussehen, wie Sie es sich vorstellen. Klingt großartig, oder? Lassen Sie uns anfangen!

## Voraussetzungen

Bevor wir uns in die Einzelheiten stürzen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:
-  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek installiert haben. Wenn nicht, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere .NET-kompatible IDE.
- Grundkenntnisse in C#: Sie sollten mit der C#-Programmierung vertraut sein.
- Schriftartenordner: Ein Verzeichnis, das Ihre benutzerdefinierten Schriftarten enthält.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. Dies erleichtert den Zugriff auf die Klassen und Methoden, die zum Festlegen des Schriftartenordners erforderlich sind.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Lassen Sie uns den Prozess in einfache, leicht verständliche Schritte aufteilen.

## Schritt 1: Definieren Sie das Datenverzeichnis

Jede große Reise beginnt mit einem einzigen Schritt. Unsere beginnt mit der Definition des Verzeichnisses, in dem Ihr Dokument gespeichert ist. Hier sucht Aspose.Words nach Ihrem Word-Dokument.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen Sie hier`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokumentverzeichnis. Hier befindet sich Ihr Quelldokument und hier wird auch die Ausgabe gespeichert.

## Schritt 2: Legen Sie den Schriftartenordner fest

 Nun sagen wir Aspose.Words, wo Ihre benutzerdefinierten Schriftarten zu finden sind. Dies geschieht durch Festlegen des Schriftartenordners mithilfe der`FontSettings.DefaultInstance.SetFontsFolder` Verfahren.

```csharp
FontSettings.DefaultInstance.SetFontsFolder("C:\\MyFonts\\", true);
```

 In dieser Zeile`"C:\\MyFonts\\"` ist der Pfad zu Ihrem benutzerdefinierten Schriftartenordner. Der zweite Parameter,`true`, gibt an, dass die Schriftarten in diesem Ordner rekursiv gescannt werden sollen.

## Schritt 3: Laden Sie Ihr Dokument

 Nachdem der Ordner „Fonts“ eingerichtet wurde, besteht der nächste Schritt darin, Ihr Word-Dokument in Aspose.Words zu laden. Dies geschieht mit dem`Document` Klasse.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Hier,`dataDir + "Rendering.docx"` bezieht sich auf den vollständigen Pfad Ihres Word-Dokuments. Stellen Sie sicher, dass sich Ihr Dokument im angegebenen Verzeichnis befindet.

## Schritt 4: Speichern Sie das Dokument

Der letzte Schritt besteht darin, Ihr Dokument zu speichern, nachdem Sie den Schriftartenordner festgelegt haben. Dadurch wird sichergestellt, dass Ihre benutzerdefinierten Schriftarten in der Ausgabe korrekt angewendet werden.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersDefaultInstance.pdf");
```

Diese Zeile speichert Ihr Dokument als PDF mit den angewendeten benutzerdefinierten Schriftarten. Die Ausgabedatei befindet sich im selben Verzeichnis wie Ihr Quelldokument.

## Abschluss

Und da haben Sie es! Das Einrichten von Schriftartenordnern für die Standardinstanz in Aspose.Words für .NET ist ein Kinderspiel, wenn Sie es in einfache Schritte aufteilen. Wenn Sie dieser Anleitung folgen, können Sie sicherstellen, dass Ihre Word-Dokumente genau so aussehen, wie Sie es möchten, mit all Ihren benutzerdefinierten Schriftarten an Ort und Stelle. Also los, probieren Sie es aus und bringen Sie Ihre Dokumente zum Strahlen!

## Häufig gestellte Fragen

### Kann ich mehrere Schriftartenordner festlegen?
 Ja, Sie können mehrere Schriftartenordner festlegen, indem Sie`SetFontsFolders` Methode, die ein Array von Ordnerpfaden akzeptiert.

### Welche Dateiformate unterstützt Aspose.Words zum Speichern von Dokumenten?
Aspose.Words unterstützt verschiedene Formate, darunter DOCX, PDF, HTML, EPUB und mehr.

### Ist es möglich, Online-Schriftarten in Aspose.Words zu verwenden?
Nein, Aspose.Words unterstützt derzeit nur lokale Schriftdateien.

### Wie kann ich sicherstellen, dass meine benutzerdefinierten Schriftarten in die gespeicherte PDF-Datei eingebettet sind?
 Durch die Einstellung der`FontSettings` korrekt ist und die Schriftarten verfügbar sind, bettet Aspose.Words sie in die PDF-Ausgabe ein.

### Was passiert, wenn eine Schriftart im angegebenen Ordner nicht gefunden wird?
Aspose.Words verwendet eine Ersatzschriftart, wenn die angegebene Schriftart nicht gefunden wird.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
