---
"description": "Erfahren Sie in dieser ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Fußnoten- und Endnotenpositionen in Word-Dokumenten festlegen."
"linktitle": "Position von Fuß- und Endnoten festlegen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Position von Fuß- und Endnoten festlegen"
"url": "/de/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Position von Fuß- und Endnoten festlegen

## Einführung

Wenn Sie mit Word-Dokumenten arbeiten und Fußnoten und Endnoten effektiv verwalten müssen, ist Aspose.Words für .NET die ideale Bibliothek. Dieses Tutorial führt Sie durch das Festlegen von Fußnoten- und Endnotenpositionen in einem Word-Dokument mit Aspose.Words für .NET. Wir erklären jeden Schritt detailliert, damit er leicht nachvollziehbar und umsetzbar ist.

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

- Aspose.Words für .NET-Bibliothek: Sie können es herunterladen von [Hier](https://releases.aspose.com/words/net/).
- Visual Studio: Jede aktuelle Version funktioniert einwandfrei.
- Grundkenntnisse in C#: Wenn Sie die Grundlagen verstehen, können Sie den Schritten problemlos folgen.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt:

```csharp
using System;
using Aspose.Words;
```

## Schritt 1: Laden Sie das Word-Dokument

Zunächst müssen Sie Ihr Word-Dokument in das Aspose.Words-Dokumentobjekt laden. Dadurch können Sie den Inhalt des Dokuments bearbeiten.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Ersetzen Sie in diesem Code `"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem sich Ihr Dokument befindet.

## Schritt 2: Fußnotenposition festlegen

Als Nächstes legen Sie die Position der Fußnoten fest. Mit Aspose.Words für .NET können Sie Fußnoten entweder am unteren Seitenrand oder unter dem Text platzieren.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

Hier haben wir die Fußnoten so eingestellt, dass sie unter dem Text erscheinen. Wenn Sie sie lieber unten auf der Seite haben möchten, verwenden Sie `FootnotePosition.BottomOfPage`.

## Schritt 3: Endnotenposition festlegen

Ebenso können Sie die Position von Endnoten festlegen. Endnoten können entweder am Ende des Abschnitts oder am Ende des Dokuments positioniert werden.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

In diesem Beispiel werden Endnoten am Ende jedes Abschnitts platziert. Um sie am Ende des Dokuments zu platzieren, verwenden Sie `EndnotePosition.EndOfDocument`.

## Schritt 4: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend, um die Änderungen zu übernehmen. Stellen Sie sicher, dass Sie den korrekten Dateipfad und -namen für das Ausgabedokument angeben.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Diese Zeile speichert das geänderte Dokument in Ihrem angegebenen Verzeichnis.

## Abschluss

Das Festlegen von Fußnoten- und Endnotenpositionen in Word-Dokumenten mit Aspose.Words für .NET ist unkompliziert, sobald Sie die Schritte kennen. Mit dieser Anleitung können Sie Ihre Dokumente an Ihre Bedürfnisse anpassen und sicherstellen, dass Fußnoten und Endnoten genau dort positioniert sind, wo Sie sie haben möchten.

## Häufig gestellte Fragen

### Kann ich für einzelne Fußnoten bzw. Endnoten unterschiedliche Positionen festlegen?

Nein, Aspose.Words für .NET legt die Position für alle Fußnoten und Endnoten in einem Dokument einheitlich fest.

### Ist Aspose.Words für .NET mit allen Versionen von Word-Dokumenten kompatibel?

Ja, Aspose.Words für .NET unterstützt eine Vielzahl von Word-Dokumentformaten, darunter DOC, DOCX, RTF und mehr.

### Kann ich Aspose.Words für .NET mit anderen Programmiersprachen verwenden?

Aspose.Words für .NET ist für .NET-Anwendungen konzipiert, Sie können es jedoch mit jeder .NET-unterstützten Sprache wie C#, VB.NET usw. verwenden.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?

Ja, Sie können eine kostenlose Testversion erhalten [Hier](https://releases.aspose.com/).

### Wo finde ich ausführlichere Dokumentation zu Aspose.Words für .NET?

Ausführliche Dokumentation ist verfügbar [Hier](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}