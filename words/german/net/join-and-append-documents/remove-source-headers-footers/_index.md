---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET Kopf- und Fußzeilen in Word-Dokumenten entfernen. Vereinfachen Sie Ihre Dokumentenverwaltung mit unserer Schritt-für-Schritt-Anleitung."
"linktitle": "Quellkopfzeilen und -fußzeilen entfernen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Quellkopfzeilen und -fußzeilen entfernen"
"url": "/de/net/join-and-append-documents/remove-source-headers-footers/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Quellkopfzeilen und -fußzeilen entfernen

## Einführung

In dieser umfassenden Anleitung erfahren Sie, wie Sie Kopf- und Fußzeilen mit Aspose.Words für .NET effektiv aus einem Word-Dokument entfernen. Kopf- und Fußzeilen werden häufig für Seitennummerierungen, Dokumenttitel oder andere wiederkehrende Inhalte in Word-Dokumenten verwendet. Ob Sie Dokumente zusammenführen oder die Formatierung bereinigen – die Beherrschung dieses Prozesses kann Ihre Dokumentenverwaltung vereinfachen. Wir zeigen Ihnen Schritt für Schritt, wie Sie dies mit Aspose.Words für .NET erreichen.

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1. Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung muss installiert sein.
2. Aspose.Words für .NET: Stellen Sie sicher, dass Sie Aspose.Words für .NET heruntergeladen und installiert haben. Falls nicht, können Sie es hier herunterladen: [Hier](https://releases.aspose.com/words/net/).
3. Grundkenntnisse: Vertrautheit mit der C#-Programmierung und den Grundlagen des .NET-Frameworks.

## Namespaces importieren

Bevor Sie mit dem Codieren beginnen, stellen Sie sicher, dass Sie die erforderlichen Namespaces in Ihre C#-Datei importieren:

```csharp
using Aspose.Words;
```

## Schritt 1: Laden Sie das Quelldokument

Zuerst müssen Sie das Quelldokument laden, aus dem Sie Kopf- und Fußzeilen entfernen möchten. Ersetzen Sie `"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrem Dokumentverzeichnis, in dem sich das Quelldokument befindet.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Schritt 2: Zieldokument erstellen oder laden

Wenn Sie noch kein Zieldokument erstellt haben, in dem Sie den geänderten Inhalt platzieren möchten, können Sie ein neues `Document` Objekt oder laden Sie ein vorhandenes.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Schritt 3: Kopf- und Fußzeilen aus Abschnitten löschen

Durchlaufen Sie jeden Abschnitt im Quelldokument (`srcDoc`) und löschen Sie die Kopf- und Fußzeilen.

```csharp
foreach (Section section in srcDoc.Sections)
{
    section.ClearHeadersFooters();
}
```

## Schritt 4: LinkToPrevious-Einstellung verwalten

Um zu verhindern, dass Kopf- und Fußzeilen im Zieldokument fortgesetzt werden (`dstDoc`), stellen Sie sicher, dass die `LinkToPrevious` Die Einstellung für Kopf- und Fußzeilen ist auf `false`.

```csharp
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Schritt 5: Geändertes Dokument an Zieldokument anhängen

Abschließend hängen Sie den geänderten Inhalt aus dem Quelldokument an (`srcDoc`) zum Zieldokument (`dstDoc`) unter Beibehaltung der Quellformatierung.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Schritt 6: Speichern Sie das resultierende Dokument

Speichern Sie das endgültige Dokument mit entfernten Kopf- und Fußzeilen in Ihrem angegebenen Verzeichnis.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.RemoveSourceHeadersFooters.docx");
```

## Abschluss

Das Entfernen von Kopf- und Fußzeilen aus einem Word-Dokument mit Aspose.Words für .NET ist ein unkomplizierter Vorgang, der die Dokumentenverwaltung erheblich vereinfacht. Mit den oben beschriebenen Schritten können Sie Dokumente effizient bereinigen und ihnen ein professionelles Erscheinungsbild verleihen.

## Häufig gestellte Fragen

### Kann ich Kopf- und Fußzeilen nur aus bestimmten Abschnitten entfernen?
Ja, Sie können Abschnitte durchlaufen und Kopf- und Fußzeilen nach Bedarf selektiv löschen.

### Unterstützt Aspose.Words für .NET das Entfernen von Kopf- und Fußzeilen über mehrere Dokumente hinweg?
Natürlich können Sie mit Aspose.Words für .NET Kopf- und Fußzeilen in mehreren Dokumenten bearbeiten.

### Was passiert, wenn ich vergesse, `LinkToPrevious` Zu `false`?
Kopf- und Fußzeilen aus dem Quelldokument können im Zieldokument übernommen werden.

### Kann ich Kopf- und Fußzeilen programmgesteuert entfernen, ohne andere Formatierungen zu beeinträchtigen?
Ja, mit Aspose.Words für .NET können Sie Kopf- und Fußzeilen entfernen und gleichzeitig die restliche Formatierung des Dokuments beibehalten.

### Wo finde ich weitere Ressourcen und Support für Aspose.Words für .NET?
Besuchen Sie die [Aspose.Words für .NET-Dokumentation](https://reference.aspose.com/words/net/) für detaillierte API-Referenzen und Beispiele.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}