---
"description": "Erfahren Sie, wie Sie die Eigenschaft „Zuletzt gespeicherte Zeit“ in Word-Dokumenten mit Aspose.Words für .NET aktualisieren. Folgen Sie unserer detaillierten Schritt-für-Schritt-Anleitung."
"linktitle": "Eigenschaft „Letzte Speicherungszeit aktualisieren“"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Eigenschaft „Letzte Speicherungszeit aktualisieren“"
"url": "/de/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Eigenschaft „Letzte Speicherungszeit aktualisieren“

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie die letzte Speicherzeit in Ihren Word-Dokumenten programmgesteuert verfolgen können? Wenn Sie mehrere Dokumente bearbeiten und deren Metadaten verwalten müssen, kann die Aktualisierung der letzten Speicherzeit sehr praktisch sein. Heute führe ich Sie mit Aspose.Words für .NET durch diesen Prozess. Also, anschnallen und los geht‘s!

## Voraussetzungen

Bevor wir mit der Schritt-für-Schritt-Anleitung beginnen, benötigen Sie einige Dinge:

1. Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Falls nicht, können Sie [Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine Entwicklungsumgebung wie Visual Studio.
3. Grundkenntnisse in C#: Kenntnisse der Grundlagen der C#-Programmierung sind hilfreich.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt. Dadurch erhalten Sie Zugriff auf die Klassen und Methoden, die Sie für die Bearbeitung von Word-Dokumenten benötigen.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Vorgang nun in einfache Schritte unterteilen. Jeder Schritt führt Sie durch den Prozess der Aktualisierung der Eigenschaft „Zuletzt gespeicherte Zeit“ in Ihrem Word-Dokument.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Geben Sie zunächst den Pfad zu Ihrem Dokumentverzeichnis an. Dort wird Ihr bestehendes Dokument abgelegt und das aktualisierte Dokument wird dort gespeichert.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersetzen `"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Verzeichnis.

## Schritt 2: Laden Sie Ihr Word-Dokument

Laden Sie anschließend das Word-Dokument, das Sie aktualisieren möchten. Erstellen Sie dazu eine Instanz des `Document` Klasse und übergeben Sie den Pfad Ihres Dokuments.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

Stellen Sie sicher, dass das Dokument mit dem Namen `Document.docx` ist im angegebenen Verzeichnis vorhanden.

## Schritt 3: Speicheroptionen konfigurieren

Erstellen Sie nun eine Instanz des `OoxmlSaveOptions` Klasse. Mit dieser Klasse können Sie Optionen zum Speichern Ihres Dokuments im Office Open XML (OOXML)-Format festlegen. Hier legen Sie die `UpdateLastSavedTimeProperty` Zu `true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Dies weist Aspose.Words an, die Eigenschaft „Letzte Speicherungszeit“ des Dokuments zu aktualisieren.

## Schritt 4: Speichern Sie das aktualisierte Dokument

Speichern Sie das Dokument abschließend mit dem `Save` Methode der `Document` Klasse und geben Sie den Pfad ein, in dem Sie das aktualisierte Dokument speichern möchten, sowie die Speicheroptionen.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Dadurch wird das Dokument mit der aktualisierten Eigenschaft „Letzte Speicherungszeit“ gespeichert.

## Abschluss

Und da haben Sie es! Mit diesen Schritten können Sie die Eigenschaft „Letzte Speicherungszeit“ Ihrer Word-Dokumente mit Aspose.Words für .NET ganz einfach aktualisieren. Dies ist besonders nützlich, um genaue Metadaten in Ihren Dokumenten zu pflegen, was für Dokumentenmanagementsysteme und verschiedene andere Anwendungen von entscheidender Bedeutung sein kann.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek zum Erstellen, Bearbeiten und Konvertieren von Word-Dokumenten in .NET-Anwendungen.

### Warum sollte ich die Eigenschaft „Zuletzt gespeicherte Zeit“ aktualisieren?
Durch die Aktualisierung der Eigenschaft „Zuletzt gespeicherter Zeitpunkt“ können genaue Metadaten beibehalten werden, was für die Dokumentenverfolgung und -verwaltung von entscheidender Bedeutung ist.

### Kann ich mit Aspose.Words für .NET andere Eigenschaften aktualisieren?
Ja, mit Aspose.Words für .NET können Sie verschiedene Dokumenteigenschaften wie Titel, Autor und Betreff aktualisieren.

### Ist Aspose.Words für .NET kostenlos?
Aspose.Words für .NET bietet eine kostenlose Testversion an, für die volle Funktionalität ist jedoch eine Lizenz erforderlich. Sie können eine Lizenz erwerben [Hier](https://purchase.aspose.com/buy).

### Wo finde ich weitere Tutorials zu Aspose.Words für .NET?
Weitere Tutorials und Dokumentationen finden Sie [Hier](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}