---
title: Substitution ohne Suffixe erhalten
linktitle: Substitution ohne Suffixe erhalten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie die Schriftartenersetzung ohne Suffixe in Aspose.Words für .NET verwalten. Folgen Sie unserer Schritt-für-Schritt-Anleitung, um sicherzustellen, dass Ihre Dokumente jedes Mal perfekt aussehen.
weight: 10
url: /de/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Substitution ohne Suffixe erhalten

## Einführung

Willkommen zu diesem umfassenden Leitfaden zur Verwaltung der Schriftartenersetzung mit Aspose.Words für .NET. Wenn Sie jemals Probleme damit hatten, dass Schriftarten in Ihren Dokumenten nicht richtig angezeigt wurden, sind Sie hier richtig. Dieses Tutorial führt Sie Schritt für Schritt durch den Prozess der effizienten Handhabung der Schriftartenersetzung ohne Suffixe.

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Grundkenntnisse in C#: Wenn Sie die C#-Programmierung verstehen, können Sie die Schritte leichter nachvollziehen und implementieren.
-  Aspose.Words für .NET-Bibliothek: Laden Sie die Bibliothek herunter und installieren Sie sie von der[Downloadlink](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung wie Visual Studio ein, um Ihren Code zu schreiben und auszuführen.
-  Beispieldokument: Ein Beispieldokument (z. B.`Rendering.docx`), mit dem Sie während dieses Tutorials arbeiten können.

## Namespaces importieren

Zuerst müssen wir die erforderlichen Namespaces importieren, um auf die von Aspose.Words bereitgestellten Klassen und Methoden zuzugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Schritt 1: Definieren Sie das Dokumentverzeichnis

Geben Sie zunächst das Verzeichnis an, in dem sich Ihr Dokument befindet. So können Sie das Dokument, an dem Sie arbeiten möchten, leichter finden.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Einrichten des Substitutionswarnungshandlers

Als Nächstes müssen wir einen Warnhandler einrichten, der uns benachrichtigt, wenn während der Dokumentverarbeitung eine Schriftart ersetzt wird. Dies ist entscheidend, um etwaige Schriftartprobleme zu erkennen und zu behandeln.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Schritt 3: Benutzerdefinierte Schriftartquellen hinzufügen

In diesem Schritt fügen wir benutzerdefinierte Schriftartquellen hinzu, um sicherzustellen, dass Aspose.Words die richtigen Schriftarten finden und verwenden kann. Dies ist insbesondere nützlich, wenn Sie bestimmte Schriftarten in benutzerdefinierten Verzeichnissen gespeichert haben.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

In diesem Code:
-  Wir holen uns die aktuellen Fontquellen und fügen eine neue hinzu`FolderFontSource` verweist auf unser benutzerdefiniertes Schriftartenverzeichnis (`C:\\MyFonts\\`).
- Anschließend aktualisieren wir die Schriftartquellen mit dieser neuen Liste.

## Schritt 4: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend, nachdem Sie die Einstellungen zur Schriftartersetzung angewendet haben. Für dieses Tutorial speichern wir es als PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Schritt 5: Erstellen Sie die Warnungshandlerklasse

 Um Warnungen effektiv zu behandeln, erstellen Sie eine benutzerdefinierte Klasse, die Folgendes implementiert:`IWarningCallback` Schnittstelle. Diese Klasse erfasst und protokolliert alle Warnungen zur Schriftartersetzung.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

In dieser Klasse:
-  Der`Warning`Methode erfasst Warnungen im Zusammenhang mit der Schriftartersetzung.
-  Der`FontWarnings` Die Sammlung speichert diese Warnungen zur weiteren Überprüfung oder Protokollierung.

## Abschluss

Sie beherrschen jetzt den Prozess der Schriftartenersetzung ohne Suffixe mit Aspose.Words für .NET. Mit diesem Wissen stellen Sie sicher, dass Ihre Dokumente unabhängig von den auf dem System verfügbaren Schriftarten ihr beabsichtigtes Erscheinungsbild beibehalten. Experimentieren Sie weiter mit verschiedenen Einstellungen und Quellen, um die Leistungsfähigkeit von Aspose.Words voll auszuschöpfen.

## Häufig gestellte Fragen

### Wie kann ich Schriftarten aus mehreren benutzerdefinierten Verzeichnissen verwenden?

 Sie können mehrere hinzufügen`FolderFontSource` Instanzen zum`fontSources` Liste und aktualisieren Sie die Schriftartquellen entsprechend.

### Wo kann ich eine kostenlose Testversion von Aspose.Words für .NET herunterladen?

 Sie können eine kostenlose Testversion herunterladen von der[Kostenlose Testseite von Aspose](https://releases.aspose.com/).

###  Kann ich mehrere Arten von Warnungen verarbeiten mit`IWarningCallback`?

 Ja, die`IWarningCallback` Die Schnittstelle ermöglicht Ihnen die Handhabung verschiedener Arten von Warnungen, nicht nur die Schriftartersetzung.

### Wo erhalte ich Support für Aspose.Words?

 Für Unterstützung besuchen Sie die[Aspose.Words Support-Forum](https://forum.aspose.com/c/words/8).

### Ist es möglich, eine temporäre Lizenz zu erwerben?

 Ja, Sie können eine vorläufige Lizenz erhalten von der[Seite mit der temporären Lizenz](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
