---
title: Verknüpfung von Kopf- und Fußzeilen aufheben
linktitle: Verknüpfung von Kopf- und Fußzeilen aufheben
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET die Verknüpfung von Kopf- und Fußzeilen in Word-Dokumenten aufheben. Folgen Sie unserer detaillierten Schritt-für-Schritt-Anleitung zur perfekten Dokumentbearbeitung.
weight: 10
url: /de/net/join-and-append-documents/unlink-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verknüpfung von Kopf- und Fußzeilen aufheben

## Einführung

In der Welt der Dokumentenverarbeitung kann es manchmal eine Herausforderung sein, Kopf- und Fußzeilen konsistent zu halten. Egal, ob Sie Dokumente zusammenführen oder einfach nur unterschiedliche Kopf- und Fußzeilen für unterschiedliche Abschnitte haben möchten, es ist wichtig zu wissen, wie man sie voneinander trennt. Heute werden wir uns damit befassen, wie Sie dies mit Aspose.Words für .NET erreichen können. Wir werden es Schritt für Schritt aufschlüsseln, damit Sie es leicht nachvollziehen können. Sind Sie bereit, die Dokumentbearbeitung zu meistern? Dann legen wir los!

## Voraussetzungen

Bevor wir ins Detail gehen, benötigen Sie einige Dinge:

-  Aspose.Words für .NET-Bibliothek: Sie können es herunterladen von der[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
- .NET Framework: Stellen Sie sicher, dass Sie ein kompatibles .NET Framework installiert haben.
- IDE: Visual Studio oder eine andere .NET-kompatible integrierte Entwicklungsumgebung.
- Grundlegende Kenntnisse in C#: Sie benötigen grundlegende Kenntnisse der Programmiersprache C#.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importieren. Dadurch können Sie auf die Aspose.Words-Bibliothek und ihre Funktionen zugreifen.

```csharp
using Aspose.Words;
```

Lassen Sie uns den Vorgang in überschaubare Schritte aufteilen, um Ihnen beim Aufheben der Verknüpfung von Kopf- und Fußzeilen in Ihren Word-Dokumenten zu helfen.

## Schritt 1: Richten Sie Ihr Projekt ein

Zuerst müssen Sie Ihre Projektumgebung einrichten. Öffnen Sie Ihre IDE und erstellen Sie ein neues .NET-Projekt. Fügen Sie einen Verweis auf die Aspose.Words-Bibliothek hinzu, die Sie zuvor heruntergeladen haben.

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

Laden Sie nun das Zieldokument, an das Sie das Quelldokument anhängen möchten, nachdem Sie die Verknüpfung mit Kopf- und Fußzeilen aufgehoben haben.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Schritt 4: Verknüpfung von Kopf- und Fußzeilen aufheben

 Dieser Schritt ist entscheidend. Um die Verknüpfung der Kopf- und Fußzeilen des Quelldokuments mit denen des Zieldokuments aufzuheben, verwenden Sie die`LinkToPrevious` -Methode. Diese Methode stellt sicher, dass die Kopf- und Fußzeilen nicht in das angehängte Dokument übernommen werden.

```csharp
// Um dies zu verhindern, entfernen Sie die Verknüpfungen zwischen Kopf- und Fußzeilen im Quelldokument.
//daran hindert, die Kopf- und Fußzeilen des Zieldokuments fortzusetzen.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Schritt 5: Das Quelldokument anhängen

 Nachdem Sie die Verknüpfung der Kopf- und Fußzeilen aufgehoben haben, können Sie das Quelldokument an das Zieldokument anhängen. Verwenden Sie die`AppendDocument` und stellen Sie den Importformatmodus auf`KeepSourceFormatting` um die ursprüngliche Formatierung des Quelldokuments beizubehalten.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Schritt 6: Speichern Sie das endgültige Dokument

Speichern Sie abschließend das neu erstellte Dokument. In diesem Dokument wird der Inhalt des Quelldokuments an das Zieldokument angehängt, wobei die Kopf- und Fußzeilen nicht verknüpft sind.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Abschluss

Und da haben Sie es! Indem Sie diese Schritte befolgen, haben Sie die Verknüpfung der Kopf- und Fußzeilen in Ihrem Quelldokument erfolgreich aufgehoben und sie mithilfe von Aspose.Words für .NET an Ihr Zieldokument angehängt. Diese Technik kann besonders nützlich sein, wenn Sie mit komplexen Dokumenten arbeiten, die unterschiedliche Kopf- und Fußzeilen für unterschiedliche Abschnitte erfordern. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?  
Aspose.Words für .NET ist eine leistungsstarke Bibliothek für die Arbeit mit Word-Dokumenten in .NET-Anwendungen. Entwickler können damit Dokumente programmgesteuert erstellen, ändern, konvertieren und drucken.

### Kann ich die Verknüpfung von Kopf- und Fußzeilen nur für bestimmte Abschnitte aufheben?  
 Ja, Sie können die Verknüpfung von Kopf- und Fußzeilen für bestimmte Abschnitte aufheben, indem Sie auf das`HeadersFooters` Eigenschaft des gewünschten Abschnitts und mit dem`LinkToPrevious` Verfahren.

### Ist es möglich, die ursprüngliche Formatierung des Quelldokuments beizubehalten?  
 Ja, beim Anhängen des Quelldokuments verwenden Sie die`ImportFormatMode.KeepSourceFormatting` Option zum Beibehalten der ursprünglichen Formatierung.

### Kann ich Aspose.Words für .NET mit anderen .NET-Sprachen außer C# verwenden?  
Absolut! Aspose.Words für .NET kann mit jeder .NET-Sprache verwendet werden, einschließlich VB.NET und F#.

### Wo finde ich weitere Dokumentation und Support für Aspose.Words für .NET?  
 Eine ausführliche Dokumentation finden Sie auf der[Aspose.Words für .NET-Dokumentationsseite](https://reference.aspose.com/words/net/) , und Support ist verfügbar auf der[Aspose-Forum](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
