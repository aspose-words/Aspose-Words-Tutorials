---
title: Schriftartenordner festlegen
linktitle: Schriftartenordner festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie in Aspose.Words für .NET einen benutzerdefinierten Schriftartenordner einrichten, um sicherzustellen, dass Ihre Word-Dokumente korrekt und ohne fehlende Schriftarten gerendert werden.
weight: 10
url: /de/net/working-with-fonts/set-fonts-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Schriftartenordner festlegen

## Einführung

Hatten Sie beim Arbeiten mit Word-Dokumenten in Ihrer .NET-Anwendung schon einmal Probleme mit fehlenden Schriftarten? Nun, Sie sind nicht allein. Das Einrichten des richtigen Schriftartenordners kann dieses Problem nahtlos lösen. In dieser Anleitung zeigen wir Ihnen, wie Sie den Schriftartenordner mit Aspose.Words für .NET einrichten. Lassen Sie uns eintauchen!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Auf Ihrem Computer installiertes Visual Studio
- .NET Framework einrichten
-  Aspose.Words für .NET-Bibliothek. Falls noch nicht geschehen, können Sie es hier herunterladen:[Hier](https://releases.aspose.com/words/net/).

## Namespaces importieren

Zuerst müssen Sie die erforderlichen Namespaces importieren, um mit Aspose.Words arbeiten zu können. Fügen Sie oben in Ihrer Codedatei die folgenden Zeilen hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Das Einrichten des Schriftartenordners ist unkompliziert, wenn Sie diese Schritte sorgfältig befolgen.

## Schritt 1: Definieren Sie das Dokumentverzeichnis

Definieren Sie zunächst den Pfad zu Ihrem Dokumentverzeichnis. In diesem Verzeichnis werden Ihre Word-Dokumente und die Schriftarten gespeichert, die Sie verwenden möchten.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen Sie unbedingt`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Verzeichnis.

## Schritt 2: FontSettings initialisieren

 Nun müssen Sie die`FontSettings` Objekt. Mit diesem Objekt können Sie benutzerdefinierte Schriftartordner angeben.

```csharp
FontSettings fontSettings = new FontSettings();
```

## Schritt 3: Legen Sie den Schriftartenordner fest

 Mit dem`SetFontsFolder` Methode der`FontSettings` Objekt, geben Sie den Ordner an, in dem Ihre benutzerdefinierten Schriftarten gespeichert sind.

```csharp
fontSettings.SetFontsFolder(dataDir + "Fonts", false);
```

 Hier,`dataDir + "Fonts"` verweist auf den Ordner "Fonts" in Ihrem Dokumentverzeichnis. Der zweite Parameter,`false`, gibt an, dass der Ordner nicht rekursiv ist.

## Schritt 4: LoadOptions erstellen

 Als nächstes erstellen Sie eine Instanz des`LoadOptions` Klasse. Diese Klasse hilft Ihnen, das Dokument mit den angegebenen Schrifteinstellungen zu laden.

```csharp
LoadOptions loadOptions = new LoadOptions();
loadOptions.FontSettings = fontSettings;
```

## Schritt 5: Laden Sie das Dokument

 Laden Sie abschließend das Word-Dokument mit dem`Document` Klasse und die`LoadOptions` Objekt.

```csharp
Document doc = new Document(dataDir + "Rendering.docx", loadOptions);
```

 Stellen Sie sicher, dass`"Rendering.docx"` ist der Name Ihres Word-Dokuments. Sie können ihn durch den Namen Ihrer Datei ersetzen.

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie ganz einfach einen benutzerdefinierten Schriftartenordner in Aspose.Words für .NET einrichten und so sicherstellen, dass alle Ihre Schriftarten korrekt wiedergegeben werden. Diese einfache Einrichtung kann Ihnen viel Kopfzerbrechen ersparen und dafür sorgen, dass Ihre Dokumente genau so aussehen, wie Sie es möchten.

## Häufig gestellte Fragen

### Warum muss ich einen benutzerdefinierten Schriftartenordner einrichten?
Durch das Einrichten eines benutzerdefinierten Schriftartenordners wird sichergestellt, dass alle in Ihren Word-Dokumenten verwendeten Schriftarten korrekt wiedergegeben werden und Probleme mit fehlenden Schriftarten vermieden werden.

### Kann ich mehrere Schriftartenordner festlegen?
 Ja, Sie können die`SetFontsFolders` Methode zum Angeben mehrerer Ordner.

### Was passiert, wenn eine Schriftart nicht gefunden wird?
Aspose.Words versucht, die fehlende Schriftart durch eine ähnliche aus den Systemschriftarten zu ersetzen.

### Ist Aspose.Words mit .NET Core kompatibel?
Ja, Aspose.Words unterstützt .NET Core zusammen mit .NET Framework.

### Wo erhalte ich Unterstützung, wenn Probleme auftreten?
 Unterstützung erhalten Sie vom[Aspose.Words Support-Forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
