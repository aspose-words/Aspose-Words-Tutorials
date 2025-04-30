---
"description": "Erfahren Sie, wie Sie die Maßeinheitenfunktion in Aspose.Words für .NET konfigurieren, um die Dokumentformatierung während der ODT-Konvertierung beizubehalten."
"linktitle": "Maßeinheit"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Maßeinheit"
"url": "/de/net/programming-with-odtsaveoptions/measure-unit/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Maßeinheit

## Einführung

Mussten Sie Ihre Word-Dokumente schon einmal in verschiedene Formate konvertieren, benötigten aber eine bestimmte Maßeinheit für Ihr Layout? Egal, ob Sie Zoll, Zentimeter oder Punkte verwenden – die Integrität Ihres Dokuments während der Konvertierung ist entscheidend. In diesem Tutorial erfahren Sie, wie Sie die Maßeinheitenfunktion in Aspose.Words für .NET konfigurieren. Diese leistungsstarke Funktion stellt sicher, dass die Formatierung Ihres Dokuments bei der Konvertierung ins ODT-Format (Open Document Text) genau Ihren Anforderungen entspricht.

## Voraussetzungen

Bevor Sie sich in den Code vertiefen, benötigen Sie für den Anfang ein paar Dinge:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version von Aspose.Words für .NET installiert haben. Falls Sie sie noch nicht haben, können Sie sie hier herunterladen. [Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine IDE wie Visual Studio zum Schreiben und Ausführen Ihres C#-Codes.
3. Grundkenntnisse in C#: Wenn Sie die Grundlagen von C# verstehen, können Sie dem Lernprogramm leichter folgen.
4. Ein Word-Dokument: Halten Sie ein Beispiel-Word-Dokument bereit, das Sie für die Konvertierung verwenden können.

## Namespaces importieren

Bevor wir mit dem Programmieren beginnen, stellen wir sicher, dass die erforderlichen Namespaces importiert sind. Fügen Sie diese using-Direktiven oben in Ihre Codedatei ein:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Zunächst müssen Sie den Pfad zu Ihrem Dokumentverzeichnis angeben. Hier befindet sich Ihr Word-Dokument und dort wird auch die konvertierte Datei gespeichert.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

Ersetzen `"YOUR DOCUMENTS DIRECTORY"` mit dem tatsächlichen Pfad zu Ihrem Verzeichnis. Dadurch weiß Ihr Code, wo Ihr Word-Dokument zu finden ist.

## Schritt 2: Laden Sie das Word-Dokument

Als nächstes müssen Sie das Word-Dokument laden, das Sie konvertieren möchten. Dies geschieht mit dem `Document` Klasse von Aspose.Words.

```csharp
// Laden Sie das Word-Dokument
Document doc = new Document(dataDir + "Document.docx");
```

Stellen Sie sicher, dass Ihr Word-Dokument mit dem Namen „Document.docx“ im angegebenen Verzeichnis vorhanden ist.

## Schritt 3: Konfigurieren der Maßeinheit

Konfigurieren wir nun die Maßeinheit für die ODT-Konvertierung. Hier geschieht die Magie. Wir richten die `OdtSaveOptions` Zoll als Maßeinheit zu verwenden.

```csharp
// Konfiguration der Backup-Optionen mit der Funktion „Maßeinheit“
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

In diesem Beispiel wird die Maßeinheit auf Zoll eingestellt. Sie können auch andere Einheiten wählen, wie z. B. `OdtSaveMeasureUnit.Centimeters` oder `OdtSaveMeasureUnit.Points` je nach Ihren Anforderungen.

## Schritt 4: Konvertieren Sie das Dokument in ODT

Abschließend konvertieren wir das Word-Dokument in das ODT-Format mit dem konfigurierten `OdtSaveOptions`.

```csharp
// Konvertieren Sie das Dokument in ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Diese Codezeile speichert das konvertierte Dokument mit der neuen Maßeinheit im angegebenen Verzeichnis.

## Abschluss

Und fertig! Mit diesen Schritten können Sie die Maßeinheitenfunktion in Aspose.Words für .NET ganz einfach konfigurieren, um sicherzustellen, dass das Layout Ihres Dokuments bei der Konvertierung erhalten bleibt. Egal, ob Sie mit Zoll, Zentimetern oder Punkten arbeiten – dieses Tutorial zeigt Ihnen, wie Sie die Formatierung Ihres Dokuments mühelos steuern.

## FAQs

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek für die programmgesteuerte Arbeit mit Word-Dokumenten. Entwickler können Word-Dokumente erstellen, ändern, konvertieren und verarbeiten, ohne Microsoft Word zu benötigen.

### Kann ich neben Zoll auch andere Maßeinheiten verwenden?
Ja, Aspose.Words für .NET unterstützt andere Maßeinheiten wie Zentimeter und Punkte. Sie können die gewünschte Einheit mit dem `OdtSaveMeasureUnit` Aufzählung.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
Ja, Sie können eine kostenlose Testversion von Aspose.Words für .NET herunterladen von [Hier](https://releases.aspose.com/).

### Wo finde ich Dokumentation für Aspose.Words für .NET?
Sie können auf die umfassende Dokumentation für Aspose.Words für .NET zugreifen unter [dieser Link](https://reference.aspose.com/words/net/).

### Wie erhalte ich Support für Aspose.Words für .NET?
Für Unterstützung können Sie das Aspose.Words-Forum unter besuchen [dieser Link](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}