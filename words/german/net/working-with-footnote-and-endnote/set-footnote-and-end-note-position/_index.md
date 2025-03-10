---
title: Festlegen der Position von Fußnoten und Endnoten
linktitle: Position von Fußnote und Endnote festlegen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in dieser ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Fußnoten- und Endnotenpositionen in Word-Dokumenten festlegen.
weight: 10
url: /de/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Festlegen der Position von Fußnoten und Endnoten

## Einführung

Wenn Sie mit Word-Dokumenten arbeiten und Fußnoten und Endnoten effektiv verwalten müssen, ist Aspose.Words für .NET Ihre Bibliothek. Dieses Tutorial führt Sie durch das Festlegen von Fußnoten- und Endnotenpositionen in einem Word-Dokument mit Aspose.Words für .NET. Wir werden jeden Schritt aufschlüsseln, damit er leicht nachvollziehbar und umsetzbar ist.

## Voraussetzungen

Bevor Sie mit dem Lernprogramm beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

-  Aspose.Words für .NET-Bibliothek: Sie können es herunterladen von[Hier](https://releases.aspose.com/words/net/).
- Visual Studio: Jede aktuelle Version funktioniert einwandfrei.
- Grundkenntnisse in C#: Wenn Sie die Grundlagen verstehen, können Sie den Schritten problemlos folgen.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr C#-Projekt:

```csharp
using System;
using Aspose.Words;
```

## Schritt 1: Laden Sie das Word-Dokument

Zu Beginn müssen Sie Ihr Word-Dokument in das Aspose.Words-Dokumentobjekt laden. Dadurch können Sie den Inhalt des Dokuments bearbeiten.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

Ersetzen Sie in diesem Code`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad, in dem sich Ihr Dokument befindet.

## Schritt 2: Fußnotenposition festlegen

Als Nächstes legen Sie die Position der Fußnoten fest. Aspose.Words für .NET ermöglicht es Ihnen, Fußnoten entweder am unteren Seitenrand oder unter dem Text zu positionieren.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

 Hier haben wir die Fußnoten so eingestellt, dass sie unter dem Text erscheinen. Wenn Sie sie lieber unten auf der Seite haben möchten, verwenden Sie`FootnotePosition.BottomOfPage`.

## Schritt 3: Endnotenposition festlegen

Ebenso können Sie die Position von Endnoten festlegen. Endnoten können entweder am Ende des Abschnitts oder am Ende des Dokuments positioniert werden.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

 In diesem Beispiel werden Endnoten am Ende jedes Abschnitts platziert. Um sie am Ende des Dokuments zu platzieren, verwenden Sie`EndnotePosition.EndOfDocument`.

## Schritt 4: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend, um die Änderungen anzuwenden. Stellen Sie sicher, dass Sie den richtigen Dateipfad und -namen für das Ausgabedokument angeben.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Diese Zeile speichert das geänderte Dokument in Ihrem angegebenen Verzeichnis.

## Abschluss

Das Festlegen von Fußnoten- und Endnotenpositionen in Word-Dokumenten mit Aspose.Words für .NET ist unkompliziert, wenn Sie die Schritte kennen. Wenn Sie dieser Anleitung folgen, können Sie Ihre Dokumente an Ihre Bedürfnisse anpassen und sicherstellen, dass Fußnoten und Endnoten genau dort positioniert werden, wo Sie sie haben möchten.

## Häufig gestellte Fragen

### Kann ich für einzelne Fußnoten bzw. Endnoten unterschiedliche Positionen festlegen?

Nein, Aspose.Words für .NET legt die Position für alle Fußnoten und Endnoten in einem Dokument einheitlich fest.

### Ist Aspose.Words für .NET mit allen Versionen von Word-Dokumenten kompatibel?

Ja, Aspose.Words für .NET unterstützt eine breite Palette von Word-Dokumentformaten, darunter DOC, DOCX, RTF und mehr.

### Kann ich Aspose.Words für .NET mit anderen Programmiersprachen verwenden?

Aspose.Words für .NET ist für .NET-Anwendungen konzipiert, Sie können es aber mit jeder .NET-unterstützten Sprache wie C#, VB.NET usw. verwenden.

### Gibt es eine kostenlose Testversion für Aspose.Words für .NET?

 Ja, Sie können eine kostenlose Testversion erhalten[Hier](https://releases.aspose.com/).

### Wo finde ich ausführlichere Dokumentation für Aspose.Words für .NET?

 Detaillierte Dokumentation ist verfügbar[Hier](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
