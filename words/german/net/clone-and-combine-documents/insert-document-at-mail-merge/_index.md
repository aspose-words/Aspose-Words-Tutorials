---
title: Dokument bei Seriendruck einfügen
linktitle: Dokument bei Seriendruck einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in diesem umfassenden Schritt-für-Schritt-Tutorial, wie Sie mit Aspose.Words für .NET Dokumente in Seriendruckfelder einfügen.
weight: 10
url: /de/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokument bei Seriendruck einfügen

## Einführung

Willkommen in der Welt der Dokumentenautomatisierung mit Aspose.Words für .NET! Haben Sie sich schon einmal gefragt, wie Sie während eines Seriendruckvorgangs Dokumente dynamisch in bestimmte Felder innerhalb eines Hauptdokuments einfügen können? Dann sind Sie hier richtig. Dieses Tutorial führt Sie Schritt für Schritt durch den Prozess des Einfügens von Dokumenten in Seriendruckfelder mit Aspose.Words für .NET. Es ist wie das Zusammensetzen eines Puzzles, bei dem jedes Teil perfekt an seinen Platz passt. Also, tauchen wir ein!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET: Sie können[Laden Sie hier die neueste Version herunter](https://releases.aspose.com/words/net/) Wenn Sie eine Lizenz erwerben müssen, können Sie dies tun[Hier](https://purchase.aspose.com/buy) Alternativ können Sie ein[vorläufige Lizenz](https://purchase.aspose.com/temporary-license/) oder probieren Sie es mit einem[Kostenlose Testversion](https://releases.aspose.com/).
2. Entwicklungsumgebung: Visual Studio oder eine andere C#-IDE.
3. Grundkenntnisse in C#: Wenn Sie mit der C#-Programmierung vertraut sind, wird dieses Tutorial zum Kinderspiel.

## Namespaces importieren

Als Erstes müssen Sie die erforderlichen Namespaces importieren. Diese sind sozusagen die Bausteine Ihres Projekts.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Lassen Sie uns den Prozess in überschaubare Schritte unterteilen. Jeder Schritt baut auf dem vorherigen auf und führt Sie zu einer vollständigen Lösung.

## Schritt 1: Einrichten Ihres Verzeichnisses

Bevor Sie mit dem Einfügen von Dokumenten beginnen können, müssen Sie den Pfad zu Ihrem Dokumentenverzeichnis festlegen. Dort werden Ihre Dokumente gespeichert.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden des Hauptdokuments

Als Nächstes laden Sie das Hauptdokument. Dieses Dokument enthält die Seriendruckfelder, in die andere Dokumente eingefügt werden.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Schritt 3: Festlegen des Callbacks für die Feldzusammenführung

Um den Zusammenführungsprozess abzuwickeln, müssen Sie eine Rückruffunktion festlegen. Diese Funktion ist für das Einfügen von Dokumenten in die angegebenen Seriendruckfelder verantwortlich.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Schritt 4: Serienbrief ausführen

Jetzt ist es an der Zeit, den Seriendruck auszuführen. Hier geschieht die Magie. Sie geben das Seriendruckfeld und das Dokument an, das in dieses Feld eingefügt werden soll.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Schritt 5: Speichern des Dokuments

Nachdem der Serienbrief abgeschlossen ist, speichern Sie das geänderte Dokument. In diesem neuen Dokument wird der eingefügte Inhalt genau dort angezeigt, wo Sie ihn haben möchten.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Schritt 6: Erstellen des Callback-Handlers

Der Callback-Handler ist eine Klasse, die spezielle Verarbeitungen für das Seriendruckfeld vornimmt. Er lädt das im Feldwert angegebene Dokument und fügt es in das aktuelle Seriendruckfeld ein.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Schritt 7: Einfügen des Dokuments

Diese Methode fügt das angegebene Dokument in den aktuellen Absatz oder die aktuelle Tabellenzelle ein.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Abschluss

Und da haben Sie es! Sie haben während eines Serienbriefvorgangs mit Aspose.Words für .NET erfolgreich Dokumente in bestimmte Felder eingefügt. Diese leistungsstarke Funktion kann Ihnen eine Menge Zeit und Mühe sparen, insbesondere bei der Arbeit mit großen Dokumentmengen. Stellen Sie es sich so vor, als hätten Sie einen persönlichen Assistenten, der Ihnen die ganze schwere Arbeit abnimmt. Probieren Sie es also einfach aus. Viel Spaß beim Programmieren!

## Häufig gestellte Fragen

### Kann ich mehrere Dokumente in verschiedene Seriendruckfelder einfügen?
Ja, das ist möglich. Geben Sie einfach die entsprechenden Seriendruckfelder und die entsprechenden Dokumentpfade im`MailMerge.Execute` Verfahren.

### Ist es möglich, das eingefügte Dokument anders zu formatieren als das Hauptdokument?
 Auf jeden Fall! Sie können die`ImportFormatMode` Parameter im`NodeImporter` um die Formatierung zu steuern.

### Was passiert, wenn der Name des Seriendruckfelds dynamisch ist?
Sie können dynamische Seriendruckfeldnamen verarbeiten, indem Sie sie als Parameter an den Rückrufhandler übergeben.

### Kann ich diese Methode mit verschiedenen Dateiformaten verwenden?
Ja, Aspose.Words unterstützt verschiedene Dateiformate, darunter DOCX, PDF und mehr.

### Wie gehe ich mit Fehlern beim Einfügen von Dokumenten um?
Implementieren Sie eine Fehlerbehandlung in Ihrem Rückrufhandler, um alle auftretenden Ausnahmen zu verwalten.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
