---
title: Maßeinheit
linktitle: Maßeinheit
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie die Maßeinheitenfunktion in Aspose.Words für .NET konfigurieren, um die Dokumentformatierung während der ODT-Konvertierung beizubehalten.
weight: 10
url: /de/net/programming-with-odtsaveoptions/measure-unit/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maßeinheit

## Einführung

Mussten Sie Ihre Word-Dokumente schon einmal in verschiedene Formate konvertieren, brauchten aber eine bestimmte Maßeinheit für Ihr Layout? Egal, ob Sie mit Zoll, Zentimetern oder Punkten arbeiten, es ist entscheidend, dass Ihr Dokument während des Konvertierungsprozesses seine Integrität behält. In diesem Tutorial erfahren Sie, wie Sie die Maßeinheitenfunktion in Aspose.Words für .NET konfigurieren. Diese leistungsstarke Funktion stellt sicher, dass die Formatierung Ihres Dokuments bei der Konvertierung in das ODT-Format (Open Document Text) genau so erhalten bleibt, wie Sie sie benötigen.

## Voraussetzungen

Bevor Sie sich in den Code vertiefen, benötigen Sie für den Anfang ein paar Dinge:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie die neueste Version von Aspose.Words für .NET installiert haben. Wenn Sie es noch nicht haben, können Sie es hier herunterladen:[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine IDE wie Visual Studio zum Schreiben und Ausführen Ihres C#-Codes.
3. Grundkenntnisse in C#: Das Verständnis der Grundlagen von C# wird Ihnen helfen, dem Tutorial zu folgen.
4. Ein Word-Dokument: Halten Sie ein Beispiel-Word-Dokument bereit, das Sie für die Konvertierung verwenden können.

## Namespaces importieren

Bevor wir mit dem Coden beginnen, stellen wir sicher, dass wir die erforderlichen Namespaces importiert haben. Fügen Sie diese using-Direktiven oben in Ihrer Codedatei hinzu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Zunächst müssen Sie den Pfad zu Ihrem Dokumentverzeichnis angeben. Hier befindet sich Ihr Word-Dokument und hier wird auch die konvertierte Datei gespeichert.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENTS DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Verzeichnis. Dadurch wird sichergestellt, dass Ihr Code weiß, wo Ihr Word-Dokument zu finden ist.

## Schritt 2: Laden Sie das Word-Dokument

 Als nächstes müssen Sie das Word-Dokument laden, das Sie konvertieren möchten. Dies geschieht mit dem`Document` Klasse von Aspose.Words.

```csharp
// Laden Sie das Word-Dokument
Document doc = new Document(dataDir + "Document.docx");
```

Stellen Sie sicher, dass Ihr Word-Dokument mit dem Namen „Dokument.docx“ im angegebenen Verzeichnis vorhanden ist.

## Schritt 3: Konfigurieren Sie die Maßeinheit

 Nun konfigurieren wir die Maßeinheit für die ODT-Konvertierung. Hier geschieht die Magie. Wir richten die`OdtSaveOptions` um Zoll als Maßeinheit zu verwenden.

```csharp
// Konfiguration der Backup-Optionen mit der Funktion „Maßeinheit“
OdtSaveOptions saveOptions = new OdtSaveOptions { MeasureUnit = OdtSaveMeasureUnit.Inches };
```

 In diesem Beispiel stellen wir die Maßeinheit auf Zoll ein. Sie können auch andere Einheiten wählen, wie`OdtSaveMeasureUnit.Centimeters` oder`OdtSaveMeasureUnit.Points` abhängig von Ihren Anforderungen.

## Schritt 4: Konvertieren Sie das Dokument in ODT

 Abschließend konvertieren wir das Word-Dokument in das ODT-Format mit dem konfigurierten`OdtSaveOptions`.

```csharp
// Konvertieren Sie das Dokument in ODT
doc.Save(dataDir + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

Diese Codezeile speichert das konvertierte Dokument mit der neuen Maßeinheit im angegebenen Verzeichnis.

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie die Maßeinheitenfunktion in Aspose.Words für .NET ganz einfach konfigurieren, um sicherzustellen, dass das Layout Ihres Dokuments während der Konvertierung erhalten bleibt. Egal, ob Sie mit Zoll, Zentimetern oder Punkten arbeiten, dieses Tutorial hat Ihnen gezeigt, wie Sie die Formatierung Ihres Dokuments problemlos steuern können.

## FAQs

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek für die programmgesteuerte Arbeit mit Word-Dokumenten. Entwickler können damit Word-Dokumente erstellen, ändern, konvertieren und verarbeiten, ohne Microsoft Word zu benötigen.

### Kann ich außer Zoll auch andere Maßeinheiten verwenden?
 Ja, Aspose.Words für .NET unterstützt andere Maßeinheiten wie Zentimeter und Punkte. Sie können die gewünschte Einheit mit dem`OdtSaveMeasureUnit` Aufzählung.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?
 Ja, Sie können eine kostenlose Testversion von Aspose.Words für .NET herunterladen von[Hier](https://releases.aspose.com/).

### Wo finde ich Dokumentation für Aspose.Words für .NET?
 Eine ausführliche Dokumentation zu Aspose.Words für .NET finden Sie unter[dieser Link](https://reference.aspose.com/words/net/).

### Wie kann ich Support für Aspose.Words für .NET erhalten?
 Für Unterstützung können Sie das Aspose.Words-Forum unter besuchen.[dieser Link](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
