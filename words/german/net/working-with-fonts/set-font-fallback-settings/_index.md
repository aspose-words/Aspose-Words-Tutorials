---
title: Festlegen der Fallback-Einstellungen für Schriftarten
linktitle: Festlegen der Fallback-Einstellungen für Schriftarten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie Font-Fallback-Einstellungen in Aspose.Words für .NET einrichten. Diese umfassende Anleitung stellt sicher, dass alle Zeichen in Ihren Dokumenten korrekt angezeigt werden.
weight: 10
url: /de/net/working-with-fonts/set-font-fallback-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Festlegen der Fallback-Einstellungen für Schriftarten

## Einführung

Beim Arbeiten mit Dokumenten, die unterschiedliche Textelemente enthalten, wie z. B. verschiedene Sprachen oder Sonderzeichen, ist es wichtig, sicherzustellen, dass diese Elemente korrekt angezeigt werden. Aspose.Words für .NET bietet eine leistungsstarke Funktion namens „Font Fallback Settings“, die beim Definieren von Regeln zum Ersetzen von Schriftarten hilft, wenn die Originalschriftart bestimmte Zeichen nicht unterstützt. In diesem Handbuch erfahren Sie in einem Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET „Font Fallback Settings“ einrichten.

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

- Grundlegende Kenntnisse in C#: Vertrautheit mit der Programmiersprache C# und dem .NET-Framework.
-  Aspose.Words für .NET: Download und Installation von der[Downloadlink](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Ein Setup wie Visual Studio zum Schreiben und Ausführen Ihres Codes.
-  Beispieldokument: Halten Sie ein Beispieldokument bereit (z. B.`Rendering.docx`) bereit zum Testen.
- XML-Fallbackregeln für Schriftarten: Bereiten Sie eine XML-Datei vor, die die Fallbackregeln für Schriftarten definiert.

## Namespaces importieren

Um Aspose.Words verwenden zu können, müssen Sie die erforderlichen Namespaces importieren. Dies ermöglicht den Zugriff auf verschiedene Klassen und Methoden, die für die Dokumentverarbeitung erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System;
```

## Schritt 1: Definieren Sie das Dokumentverzeichnis

Definieren Sie zunächst das Verzeichnis, in dem Ihr Dokument gespeichert ist. Dies ist wichtig, damit Sie Ihr Dokument finden und verarbeiten können.

```csharp
// Der Pfad zum Dokumentenverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden Sie das Dokument

 Laden Sie Ihr Dokument in ein Aspose.Words`Document` Objekt. Dieser Schritt ermöglicht Ihnen, programmgesteuert mit dem Dokument zu arbeiten.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Schritt 3: Schriftarteinstellungen konfigurieren

 Erstellen Sie ein neues`FontSettings` Objekt und laden Sie die Schriftart-Fallback-Einstellungen aus einer XML-Datei. Diese XML-Datei enthält die Regeln für den Schriftart-Fallback.

```csharp
FontSettings fontSettings = new FontSettings();
fontSettings.FallbackSettings.Load(dataDir + "Font fallback rules.xml");
```

## Schritt 4: Schrifteinstellungen auf das Dokument anwenden

 Weisen Sie die konfigurierten`FontSettings`zum Dokument. Dadurch wird sichergestellt, dass beim Rendern des Dokuments die Fallback-Regeln für Schriftarten angewendet werden.

```csharp
doc.FontSettings = fontSettings;
```

## Schritt 5: Speichern Sie das Dokument

Speichern Sie abschließend das Dokument. Die Fallback-Einstellungen für Schriftarten werden während des Speichervorgangs verwendet, um eine ordnungsgemäße Schriftartenersetzung sicherzustellen.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontFallbackSettings.pdf");
```

## XML-Datei: Fallback-Regeln für Schriftarten

Hier ist ein Beispiel, wie Ihre XML-Datei mit den Fallback-Regeln für Schriftarten aussehen sollte:

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

Wenn Sie diese Schritte befolgen, können Sie die Font-Fallback-Einstellungen in Aspose.Words für .NET effektiv einrichten und verwenden. Dadurch wird sichergestellt, dass Ihre Dokumente alle Zeichen korrekt anzeigen, auch wenn die Originalschriftart bestimmte Zeichen nicht unterstützt. Durch die Implementierung dieser Einstellungen verbessern Sie die Qualität und Lesbarkeit Ihrer Dokumente erheblich.

## Häufig gestellte Fragen

### F1: Was ist Font Fallback?

Font Fallback ist eine Funktion, die den Ersatz von Schriftarten ermöglicht, wenn die Originalschriftart bestimmte Zeichen nicht unterstützt. So wird die korrekte Anzeige aller Textelemente sichergestellt.

### F2: Kann ich mehrere Ersatzschriftarten angeben?

Ja, Sie können in den XML-Regeln mehrere Ersatzschriftarten angeben. Aspose.Words überprüft jede Schriftart in der angegebenen Reihenfolge, bis es eine findet, die das Zeichen unterstützt.

### F3: Wo kann ich Aspose.Words für .NET herunterladen?

 Sie können es herunterladen von der[Aspose-Downloadseite](https://releases.aspose.com/words/net/).

### F4: Wie erstelle ich die XML-Datei für Schriftart-Fallbackregeln?

Die XML-Datei kann mit jedem Texteditor erstellt werden. Sie sollte der Struktur des Beispiels in diesem Tutorial entsprechen.

### F5: Gibt es Support für Aspose.Words?

 Ja, Sie finden Unterstützung auf der[Aspose.Words Support-Forum](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
