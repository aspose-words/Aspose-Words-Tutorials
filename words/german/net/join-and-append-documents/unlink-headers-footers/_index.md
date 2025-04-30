---
"description": "Erfahren Sie, wie Sie Kopf- und Fußzeilen in Word-Dokumenten mit Aspose.Words für .NET trennen. Folgen Sie unserer detaillierten Schritt-für-Schritt-Anleitung zur perfekten Dokumentbearbeitung."
"linktitle": "Verknüpfung von Kopf- und Fußzeilen aufheben"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Verknüpfung von Kopf- und Fußzeilen aufheben"
"url": "/de/net/join-and-append-documents/unlink-headers-footers/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verknüpfung von Kopf- und Fußzeilen aufheben

## Einführung

In der Welt der Dokumentenverarbeitung kann die Konsistenz von Kopf- und Fußzeilen manchmal eine Herausforderung sein. Egal, ob Sie Dokumente zusammenführen oder einfach nur unterschiedliche Kopf- und Fußzeilen für verschiedene Abschnitte verwenden möchten – es ist wichtig zu wissen, wie man die Verknüpfungen aufhebt. Heute zeigen wir Ihnen, wie Sie dies mit Aspose.Words für .NET erreichen. Wir erklären es Schritt für Schritt, damit Sie es leicht nachvollziehen können. Sind Sie bereit, die Dokumentenbearbeitung zu meistern? Dann legen wir los!

## Voraussetzungen

Bevor wir ins Detail gehen, benötigen Sie Folgendes:

- Aspose.Words für .NET-Bibliothek: Sie können es herunterladen von der [Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
- .NET Framework: Stellen Sie sicher, dass Sie ein kompatibles .NET Framework installiert haben.
- IDE: Visual Studio oder eine andere .NET-kompatible integrierte Entwicklungsumgebung.
- Grundlegende Kenntnisse in C#: Sie benötigen grundlegende Kenntnisse der Programmiersprache C#.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt. Dadurch erhalten Sie Zugriff auf die Aspose.Words-Bibliothek und ihre Funktionen.

```csharp
using Aspose.Words;
```

Lassen Sie uns den Vorgang in überschaubare Schritte unterteilen, um Ihnen beim Aufheben der Verknüpfung von Kopf- und Fußzeilen in Ihren Word-Dokumenten zu helfen.

## Schritt 1: Richten Sie Ihr Projekt ein

Zuerst müssen Sie Ihre Projektumgebung einrichten. Öffnen Sie Ihre IDE und erstellen Sie ein neues .NET-Projekt. Fügen Sie einen Verweis auf die zuvor heruntergeladene Aspose.Words-Bibliothek hinzu.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden Sie das Quelldokument

Als Nächstes müssen Sie das Quelldokument laden, das Sie ändern möchten. Die Kopf- und Fußzeilen dieses Dokuments sind nicht verknüpft.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Schritt 3: Zieldokument laden

Laden Sie nun das Zieldokument, in das Sie das Quelldokument anhängen, nachdem Sie die Verknüpfung mit den Kopf- und Fußzeilen aufgehoben haben.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Schritt 4: Verknüpfung von Kopf- und Fußzeilen aufheben

Dieser Schritt ist entscheidend. Um die Verknüpfung der Kopf- und Fußzeilen des Quelldokuments mit denen des Zieldokuments aufzuheben, verwenden Sie die `LinkToPrevious` -Methode. Diese Methode stellt sicher, dass die Kopf- und Fußzeilen nicht in das angehängte Dokument übernommen werden.

```csharp
// Trennen Sie die Verknüpfung der Kopf- und Fußzeilen im Quelldokument, um dies zu verhindern
// daran hindern, die Kopf- und Fußzeilen des Zieldokuments fortzusetzen.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Schritt 5: Anhängen des Quelldokuments

Nachdem Sie die Verknüpfung der Kopf- und Fußzeilen aufgehoben haben, können Sie das Quelldokument an das Zieldokument anhängen. Verwenden Sie die `AppendDocument` Methode und stellen Sie den Importformatmodus auf `KeepSourceFormatting` um die ursprüngliche Formatierung des Quelldokuments beizubehalten.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Schritt 6: Speichern Sie das endgültige Dokument

Speichern Sie abschließend das neu erstellte Dokument. Der Inhalt des Quelldokuments wird an das Zieldokument angehängt, wobei die Kopf- und Fußzeilen nicht verknüpft sind.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Abschluss

Und da haben Sie es! Mit diesen Schritten haben Sie die Verknüpfung der Kopf- und Fußzeilen in Ihrem Quelldokument erfolgreich aufgehoben und sie mithilfe von Aspose.Words für .NET an Ihr Zieldokument angehängt. Diese Technik ist besonders nützlich, wenn Sie mit komplexen Dokumenten arbeiten, die unterschiedliche Kopf- und Fußzeilen für verschiedene Abschnitte erfordern. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?  
Aspose.Words für .NET ist eine leistungsstarke Bibliothek für die Arbeit mit Word-Dokumenten in .NET-Anwendungen. Entwickler können damit Dokumente programmgesteuert erstellen, ändern, konvertieren und drucken.

### Kann ich die Verknüpfung von Kopf- und Fußzeilen nur für bestimmte Abschnitte aufheben?  
Ja, Sie können die Verknüpfung von Kopf- und Fußzeilen für bestimmte Abschnitte aufheben, indem Sie auf die `HeadersFooters` Eigenschaft des gewünschten Abschnitts und mithilfe der `LinkToPrevious` Verfahren.

### Ist es möglich, die ursprüngliche Formatierung des Quelldokuments beizubehalten?  
Ja, beim Anhängen des Quelldokuments verwenden Sie die `ImportFormatMode.KeepSourceFormatting` Option zum Beibehalten der ursprünglichen Formatierung.

### Kann ich Aspose.Words für .NET mit anderen .NET-Sprachen außer C# verwenden?  
Absolut! Aspose.Words für .NET kann mit jeder .NET-Sprache verwendet werden, einschließlich VB.NET und F#.

### Wo finde ich weitere Dokumentation und Support für Aspose.Words für .NET?  
Eine umfassende Dokumentation finden Sie auf der [Aspose.Words für .NET-Dokumentationsseite](https://reference.aspose.com/words/net/)und Support ist verfügbar auf der [Aspose-Forum](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}