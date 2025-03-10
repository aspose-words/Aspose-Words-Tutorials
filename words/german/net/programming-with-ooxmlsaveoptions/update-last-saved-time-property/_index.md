---
title: Eigenschaft „Zuletzt gespeicherter Zeitpunkt aktualisieren“
linktitle: Eigenschaft „Zuletzt gespeicherter Zeitpunkt aktualisieren“
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie die Eigenschaft „Zuletzt gespeicherte Zeit“ in Word-Dokumenten mit Aspose.Words für .NET aktualisieren. Folgen Sie unserer detaillierten Schritt-für-Schritt-Anleitung.
weight: 10
url: /de/net/programming-with-ooxmlsaveoptions/update-last-saved-time-property/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Eigenschaft „Zuletzt gespeicherter Zeitpunkt aktualisieren“

## Einführung

Haben Sie sich schon einmal gefragt, wie Sie die Eigenschaft „Zuletzt gespeicherte Zeit“ in Ihren Word-Dokumenten programmgesteuert verfolgen können? Wenn Sie mit mehreren Dokumenten arbeiten und deren Metadaten verwalten müssen, kann es sehr praktisch sein, die Eigenschaft „Zuletzt gespeicherte Zeit“ zu aktualisieren. Heute werde ich Sie mithilfe von Aspose.Words für .NET durch diesen Prozess führen. Also, schnallen Sie sich an und legen Sie los!

## Voraussetzungen

Bevor wir mit der Schritt-für-Schritt-Anleitung beginnen, benötigen Sie einige Dinge:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET installiert haben. Wenn nicht, können Sie[Laden Sie es hier herunter](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine Entwicklungsumgebung wie Visual Studio.
3. Grundkenntnisse in C#: Kenntnisse der Grundlagen der C#-Programmierung sind hilfreich.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importieren. Dadurch können Sie auf die Klassen und Methoden zugreifen, die zum Bearbeiten von Word-Dokumenten erforderlich sind.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Lassen Sie uns den Vorgang nun in einfache Schritte unterteilen. Jeder Schritt führt Sie durch den Vorgang zum Aktualisieren der Eigenschaft „Zuletzt gespeicherte Zeit“ in Ihrem Word-Dokument.

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Zunächst müssen Sie den Pfad zu Ihrem Dokumentverzeichnis angeben. Hier ist Ihr bestehendes Dokument gespeichert und hier wird auch das aktualisierte Dokument gespeichert.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Verzeichnis.

## Schritt 2: Laden Sie Ihr Word-Dokument

 Laden Sie als nächstes das Word-Dokument, das Sie aktualisieren möchten. Sie können dies tun, indem Sie eine Instanz des`Document` Klasse und übergeben Sie den Pfad Ihres Dokuments.

```csharp
Document doc = new Document(dataDir + "Document.docx");
```

 Stellen Sie sicher, dass das Dokument mit dem Namen`Document.docx` ist im angegebenen Verzeichnis vorhanden.

## Schritt 3: Speicheroptionen konfigurieren

 Erstellen Sie nun eine Instanz des`OoxmlSaveOptions` Klasse. Mit dieser Klasse können Sie Optionen zum Speichern Ihres Dokuments im Office Open XML (OOXML)-Format festlegen. Hier legen Sie die`UpdateLastSavedTimeProperty` Zu`true`.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions
{
    UpdateLastSavedTimeProperty = true
};
```

Dies weist Aspose.Words an, die Eigenschaft „Zuletzt gespeicherte Zeit“ des Dokuments zu aktualisieren.

## Schritt 4: Speichern Sie das aktualisierte Dokument

 Speichern Sie das Dokument abschließend mit dem`Save` Methode der`Document` Klasse und geben Sie den Pfad ein, in dem Sie das aktualisierte Dokument speichern möchten, sowie die Speicheroptionen.

```csharp
doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
```

Dadurch wird das Dokument mit der aktualisierten Eigenschaft „Letzte Speicherungszeit“ gespeichert.

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie die Eigenschaft „Zuletzt gespeicherte Zeit“ Ihrer Word-Dokumente mithilfe von Aspose.Words für .NET ganz einfach aktualisieren. Dies ist besonders nützlich, um genaue Metadaten in Ihren Dokumenten beizubehalten, was für Dokumentenverwaltungssysteme und verschiedene andere Anwendungen von entscheidender Bedeutung sein kann.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek zum Erstellen, Bearbeiten und Konvertieren von Word-Dokumenten in .NET-Anwendungen.

### Warum sollte ich die Eigenschaft „Zuletzt gespeicherte Zeit“ aktualisieren?
Durch die Aktualisierung der Eigenschaft „Zuletzt gespeicherter Zeitpunkt“ können genaue Metadaten verwaltet werden, was für die Dokumentenverfolgung und -verwaltung von entscheidender Bedeutung ist.

### Kann ich mit Aspose.Words für .NET andere Eigenschaften aktualisieren?
Ja, mit Aspose.Words für .NET können Sie verschiedene Dokumenteigenschaften wie Titel, Autor und Betreff aktualisieren.

### Ist Aspose.Words für .NET kostenlos?
 Aspose.Words für .NET bietet eine kostenlose Testversion an, für die volle Funktionalität ist jedoch eine Lizenz erforderlich. Sie können eine Lizenz erwerben[Hier](https://purchase.aspose.com/buy).

### Wo finde ich weitere Tutorials zu Aspose.Words für .NET?
Weitere Tutorials und Dokumentationen finden Sie[Hier](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
