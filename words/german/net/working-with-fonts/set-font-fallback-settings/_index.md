---
"description": "Erfahren Sie, wie Sie die Font-Fallback-Einstellungen in Aspose.Words für .NET einrichten. Diese umfassende Anleitung stellt sicher, dass alle Zeichen in Ihren Dokumenten korrekt angezeigt werden."
"linktitle": "Festlegen der Fallback-Einstellungen für Schriftarten"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Festlegen der Fallback-Einstellungen für Schriftarten"
"url": "/de/net/working-with-fonts/set-font-fallback-settings/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Festlegen der Fallback-Einstellungen für Schriftarten

## Einführung

Bei der Arbeit mit Dokumenten, die unterschiedliche Textelemente enthalten, wie z. B. verschiedene Sprachen oder Sonderzeichen, ist die korrekte Darstellung dieser Elemente entscheidend. Aspose.Words für .NET bietet die leistungsstarke Funktion „Font Fallback Settings“, mit der Sie Regeln für den Ersatz von Schriftarten definieren können, wenn die Originalschrift bestimmte Zeichen nicht unterstützt. In dieser Anleitung erfahren Sie Schritt für Schritt, wie Sie „Font Fallback Settings“ mit Aspose.Words für .NET einrichten.

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Grundkenntnisse in C#: Vertrautheit mit der Programmiersprache C# und dem .NET-Framework.
- Aspose.Words für .NET: Herunterladen und installieren von der [Download-Link](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Ein Setup wie Visual Studio zum Schreiben und Ausführen Ihres Codes.
- Beispieldokument: Halten Sie ein Beispieldokument bereit (z. B. `Rendering.docx`) bereit zum Testen.
- XML-Fallback-Regeln für Schriftarten: Bereiten Sie eine XML-Datei vor, die die Fallback-Regeln für Schriftarten definiert.

## Namespaces importieren

Um Aspose.Words verwenden zu können, müssen Sie die erforderlichen Namespaces importieren. Dies ermöglicht den Zugriff auf verschiedene Klassen und Methoden, die für die Dokumentverarbeitung erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Schritt 1: Definieren Sie das Dokumentverzeichnis

Definieren Sie zunächst das Verzeichnis, in dem Ihr Dokument gespeichert ist. Dies ist wichtig, um Ihr Dokument finden und bearbeiten zu können.

```csharp
// Der Pfad zum Dokumentenverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden Sie das Dokument

Laden Sie Ihr Dokument in ein Aspose.Words `Document` Objekt. Dieser Schritt ermöglicht Ihnen die programmgesteuerte Arbeit mit dem Dokument.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 3: Schriftarteinstellungen konfigurieren

Erstellen Sie ein neues `FontSettings` Objekt und laden Sie die Schriftart-Fallback-Einstellungen aus einer XML-Datei. Diese XML-Datei enthält die Regeln für den Schriftart-Fallback.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Schritt 4: Schrifteinstellungen auf das Dokument anwenden

Weisen Sie die konfigurierten `FontSettings` zum Dokument. Dadurch wird sichergestellt, dass die Schriftart-Fallback-Regeln beim Rendern des Dokuments angewendet werden.

```csharp
doc.FontSettings = fontSettings;
```

## Schritt 5: Speichern Sie das Dokument

Speichern Sie abschließend das Dokument. Die Schriftart-Fallback-Einstellungen werden beim Speichern verwendet, um eine korrekte Schriftartenersetzung zu gewährleisten.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML-Datei: Font-Fallback-Regeln

Hier ist ein Beispiel, wie Ihre XML-Datei, die die Schriftart-Fallback-Regeln definiert, aussehen sollte:

```xml
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<FontFallbackSettings xmlns="Aspose.Words">
    <FallbackTable>
        <Rule Ranges="0B80-0BFF" FallbackFonts="Vijaya"/>
        <Rule Ranges="1F300-1F64F" FallbackFonts="Segoe UI Emoji, Segoe UI Symbol"/>
        <Rule Ranges="2000-206F, 2070-209F, 20B9" FallbackFonts="Arial" />
        <Rule Ranges="3040-309F" FallbackFonts="MS Gothic" BaseFonts="Times New Roman"/>
        <Rule Ranges="3040-309F" FallbackFonts="MS Mincho"/>
        <Rule FallbackFonts="Arial Unicode MS"/>
    </FallbackTable>
</FontFallbackSettings>
```

## Abschluss

Mit diesen Schritten können Sie die Font-Fallback-Einstellungen in Aspose.Words für .NET effektiv einrichten und nutzen. Dadurch wird sichergestellt, dass Ihre Dokumente alle Zeichen korrekt darstellen, auch wenn die Originalschriftart bestimmte Zeichen nicht unterstützt. Die Implementierung dieser Einstellungen verbessert die Qualität und Lesbarkeit Ihrer Dokumente erheblich.

## Häufig gestellte Fragen

### F1: Was ist Font Fallback?

Font Fallback ist eine Funktion, die das Ersetzen von Schriftarten ermöglicht, wenn die Originalschriftart bestimmte Zeichen nicht unterstützt, und so die korrekte Anzeige aller Textelemente gewährleistet.

### F2: Kann ich mehrere Ersatzschriftarten angeben?

Ja, Sie können in den XML-Regeln mehrere Ersatzschriften angeben. Aspose.Words prüft jede Schrift in der angegebenen Reihenfolge, bis eine gefunden wird, die das Zeichen unterstützt.

### F3: Wo kann ich Aspose.Words für .NET herunterladen?

Sie können es herunterladen von der [Aspose-Downloadseite](https://releases.aspose.com/words/net/).

### F4: Wie erstelle ich die XML-Datei für Schriftart-Fallback-Regeln?

Die XML-Datei kann mit einem beliebigen Texteditor erstellt werden. Sie sollte der im Beispiel dieses Tutorials gezeigten Struktur entsprechen.

### F5: Gibt es Support für Aspose.Words?

Ja, Sie finden Unterstützung auf der [Aspose.Words Support-Forum](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}