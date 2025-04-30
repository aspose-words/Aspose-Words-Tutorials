---
"description": "Erfahren Sie in unserer detaillierten Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET ein Word-Dokument nahtlos in ein anderes einfügen. Perfekt für Entwickler, die die Dokumentenverarbeitung optimieren möchten."
"linktitle": "Dokument beim Ersetzen einfügen"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Dokument beim Ersetzen einfügen"
"url": "/de/net/clone-and-combine-documents/insert-document-at-replace/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokument beim Ersetzen einfügen

## Einführung

Hallo, Dokumenten-Experten! Haben Sie sich schon einmal tief in Code vergraben und versucht, ein Word-Dokument nahtlos in ein anderes einzufügen? Keine Sorge, heute tauchen wir in die Welt von Aspose.Words für .NET ein, um diese Aufgabe zum Kinderspiel zu machen. Wir zeigen Ihnen Schritt für Schritt, wie Sie mit dieser leistungsstarken Bibliothek Dokumente an bestimmten Stellen während eines Suchen-und-Ersetzen-Vorgangs einfügen. Sind Sie bereit, ein Aspose.Words-Experte zu werden? Los geht‘s!

## Voraussetzungen

Bevor wir uns in den Code stürzen, müssen Sie einige Dinge vorbereitet haben:

- Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem Computer installiert ist. Falls Sie es noch nicht haben, können Sie es hier herunterladen: [Hier](https://visualstudio.microsoft.com/).
- Aspose.Words für .NET: Sie benötigen die Aspose.Words-Bibliothek. Sie erhalten sie von der [Aspose-Website](https://releases.aspose.com/words/net/).
- Grundlegende C#-Kenntnisse: Ein grundlegendes Verständnis von C# und .NET wird Ihnen helfen, diesem Tutorial zu folgen.

Okay, nachdem wir das geklärt haben, können wir uns mit etwas Code die Hände schmutzig machen!

## Namespaces importieren

Zunächst müssen wir die notwendigen Namespaces für die Arbeit mit Aspose.Words importieren. Das ist so, als ob man vor Projektbeginn alle Werkzeuge zusammensucht. Füge diese using-Direktiven oben in deiner C#-Datei ein:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Nachdem wir nun die Voraussetzungen geschaffen haben, können wir den Prozess in kleine Schritte unterteilen. Jeder Schritt ist entscheidend und bringt uns unserem Ziel näher.

## Schritt 1: Einrichten des Dokumentenverzeichnisses

Zuerst müssen wir das Verzeichnis angeben, in dem unsere Dokumente gespeichert werden. Das ist wie die Vorbereitung der Bühne für die große Aufführung.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Ersetzen `"YOUR DOCUMENT DIRECTORY"` mit dem Pfad zu Ihrem Verzeichnis. Hier werden Ihre Dokumente gespeichert und gespeichert.

## Schritt 2: Laden Sie das Hauptdokument

Als Nächstes laden wir das Hauptdokument, in das wir ein weiteres Dokument einfügen möchten. Betrachten Sie dies als unsere Hauptbühne, auf der die gesamte Aktion stattfindet.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Dieser Code lädt das Hauptdokument aus dem angegebenen Verzeichnis.

## Schritt 3: Optionen zum Suchen und Ersetzen festlegen

Um die genaue Stelle zu finden, an der wir unser Dokument einfügen möchten, verwenden wir die Suchen-und-Ersetzen-Funktion. Das ist, als würden wir eine Karte verwenden, um den genauen Ort für unseren neuen Anbau zu finden.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Hier legen wir die Richtung auf „rückwärts“ fest und geben einen benutzerdefinierten Rückrufhandler an, den wir als Nächstes definieren.

## Schritt 4: Ausführen des Ersetzungsvorgangs

Jetzt weisen wir unser Hauptdokument an, nach einem bestimmten Platzhaltertext zu suchen und ihn durch nichts zu ersetzen, während wir unseren benutzerdefinierten Rückruf verwenden, um ein anderes Dokument einzufügen.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Dieser Code führt den Such- und Ersetzungsvorgang aus und speichert dann das aktualisierte Dokument.

## Schritt 5: Erstellen Sie einen benutzerdefinierten Callback-Ersetzungshandler

Unser benutzerdefinierter Callback-Handler ist der Ort, an dem die Magie passiert. Dieser Handler definiert, wie das Einfügen des Dokuments während des Suchen- und Ersetzen-Vorgangs erfolgt.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Fügen Sie nach dem Absatz, der den übereinstimmenden Text enthält, ein Dokument ein.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Entfernen Sie den Absatz mit dem übereinstimmenden Text.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Hier laden wir das einzufügende Dokument und rufen dann eine Hilfsmethode auf, um das Einfügen durchzuführen.

## Schritt 6: Definieren Sie die Methode zum Einfügen von Dokumenten

Das letzte Teil unseres Puzzles ist die Methode, die das Dokument tatsächlich an der angegebenen Stelle einfügt.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Überprüfen Sie, ob das Einfügeziel ein Absatz oder eine Tabelle ist
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Erstellen Sie einen NodeImporter, um Knoten aus dem Quelldokument zu importieren
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Durchlaufen Sie alle Knoten auf Blockebene in den Abschnitten des Quelldokuments
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Überspringen Sie den letzten leeren Absatz eines Abschnitts
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Importieren und fügen Sie den Knoten in das Ziel ein
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Diese Methode sorgt dafür, dass Knoten aus dem einzufügenden Dokument importiert und an der richtigen Stelle im Hauptdokument platziert werden.

## Abschluss

Und da haben Sie es! Eine umfassende Anleitung zum Einfügen eines Dokuments in ein anderes mit Aspose.Words für .NET. Mit diesen Schritten können Sie die Dokumenterstellung und -bearbeitung ganz einfach automatisieren. Egal, ob Sie ein Dokumentenmanagementsystem erstellen oder einfach Ihren Dokumentenverarbeitungs-Workflow optimieren möchten – Aspose.Words ist Ihr zuverlässiger Begleiter.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek zur programmgesteuerten Bearbeitung von Word-Dokumenten. Sie ermöglicht Ihnen das einfache Erstellen, Ändern, Konvertieren und Verarbeiten von Word-Dokumenten.

### Kann ich mehrere Dokumente gleichzeitig einfügen?
Ja, Sie können den Rückrufhandler so ändern, dass er mehrere Einfügungen verarbeitet, indem er über eine Sammlung von Dokumenten iteriert.

### Gibt es eine kostenlose Testversion?
Absolut! Sie können eine kostenlose Testversion herunterladen von [Hier](https://releases.aspose.com/).

### Wie erhalte ich Support für Aspose.Words?
Sie erhalten Unterstützung durch den Besuch der [Aspose.Words-Forum](https://forum.aspose.com/c/words/8).

### Kann ich die Formatierung des eingefügten Dokuments beibehalten?
Ja, die `NodeImporter` Mit der Klasse können Sie angeben, wie die Formatierung beim Importieren von Knoten von einem Dokument in ein anderes gehandhabt wird.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}