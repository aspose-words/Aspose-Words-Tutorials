---
title: Dokument beim Ersetzen einfügen
linktitle: Dokument beim Ersetzen einfügen
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer ausführlichen Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET ein Word-Dokument nahtlos in ein anderes einfügen. Perfekt für Entwickler, die die Dokumentverarbeitung optimieren möchten.
weight: 10
url: /de/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokument beim Ersetzen einfügen

## Einführung

Hallo, Dokument-Meister! Haben Sie sich schon einmal mitten im Code verfangen und versucht, herauszufinden, wie Sie ein Word-Dokument nahtlos in ein anderes einfügen können? Keine Angst, denn heute tauchen wir in die Welt von Aspose.Words für .NET ein, um diese Aufgabe zu einem Kinderspiel zu machen. Wir werden Sie Schritt für Schritt durch die Verwendung dieser leistungsstarken Bibliothek führen, um Dokumente an bestimmten Stellen während eines Such- und Ersetzungsvorgangs einzufügen. Sind Sie bereit, ein Aspose.Words-Zauberer zu werden? Dann legen wir los!

## Voraussetzungen

Bevor wir uns in den Code stürzen, müssen einige Dinge bereitstehen:

-  Visual Studio: Stellen Sie sicher, dass Visual Studio auf Ihrem Computer installiert ist. Wenn Sie es noch nicht haben, können Sie es hier herunterladen:[Hier](https://visualstudio.microsoft.com/).
-  Aspose.Words für .NET: Sie benötigen die Aspose.Words-Bibliothek. Sie erhalten sie von[Aspose-Website](https://releases.aspose.com/words/net/).
- Grundlegende C#-Kenntnisse: Grundlegende Kenntnisse von C# und .NET helfen Ihnen, diesem Tutorial zu folgen.

Gut, nachdem wir das geklärt haben, machen wir uns mit etwas Code die Hände schmutzig!

## Namespaces importieren

Als Erstes müssen wir die erforderlichen Namespaces importieren, um mit Aspose.Words arbeiten zu können. Das ist so, als ob Sie alle Ihre Werkzeuge zusammentragen, bevor Sie ein Projekt starten. Fügen Sie diese using-Direktiven oben in Ihrer C#-Datei hinzu:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Nachdem wir nun die Voraussetzungen geschaffen haben, können wir den Prozess in kleinere Schritte unterteilen. Jeder Schritt ist entscheidend und bringt uns unserem Ziel näher.

## Schritt 1: Einrichten des Dokumentenverzeichnisses

Zuerst müssen wir das Verzeichnis angeben, in dem unsere Dokumente gespeichert sind. Das ist wie die Vorbereitung der Bühne vor der großen Aufführung.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Ersetzen`"YOUR DOCUMENT DIRECTORY"` mit dem Pfad zu Ihrem Verzeichnis. Hier leben und atmen Ihre Dokumente.

## Schritt 2: Hauptdokument laden

Als nächstes laden wir das Hauptdokument, in das wir ein weiteres Dokument einfügen möchten. Betrachten Sie dies als unsere Hauptbühne, auf der die ganze Aktion stattfindet.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Dieser Code lädt das Hauptdokument aus dem angegebenen Verzeichnis.

## Schritt 3: Suchen- und Ersetzen-Optionen festlegen

Um die genaue Stelle zu finden, an der wir unser Dokument einfügen möchten, verwenden wir die Funktion „Suchen und Ersetzen“. Das ist, als würden wir eine Karte verwenden, um die genaue Stelle für unseren neuen Zusatz zu finden.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Hier stellen wir die Richtung auf „rückwärts“ ein und geben einen benutzerdefinierten Rückrufhandler an, den wir als Nächstes definieren.

## Schritt 4: Ersetzen durchführen

Jetzt weisen wir unser Hauptdokument an, nach einem bestimmten Platzhaltertext zu suchen und ihn durch nichts zu ersetzen, während wir unseren benutzerdefinierten Rückruf verwenden, um ein anderes Dokument einzufügen.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Dieser Code führt den Such- und Ersetzungsvorgang aus und speichert dann das aktualisierte Dokument.

## Schritt 5: Erstellen Sie einen benutzerdefinierten Callback-Ersetzungshandler

In unserem benutzerdefinierten Callback-Handler geschieht die Magie. Dieser Handler definiert, wie das Einfügen des Dokuments während des Such- und Ersetzungsvorgangs durchgeführt wird.

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

Hier laden wir das einzufügende Dokument und rufen dann eine Hilfsmethode auf, um den Einfügungsvorgang durchzuführen.

## Schritt 6: Definieren Sie die Methode „Dokument einfügen“

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

Bei dieser Methode werden die einzufügenden Knoten aus dem Dokument importiert und an der richtigen Stelle im Hauptdokument platziert.

## Abschluss

Und da haben Sie es! Eine umfassende Anleitung zum Einfügen eines Dokuments in ein anderes mit Aspose.Words für .NET. Indem Sie diese Schritte befolgen, können Sie Aufgaben zur Dokumentzusammenstellung und -bearbeitung problemlos automatisieren. Egal, ob Sie ein Dokumentenverwaltungssystem erstellen oder einfach nur Ihren Dokumentenverarbeitungs-Workflow optimieren möchten, Aspose.Words ist Ihr zuverlässiger Kumpel.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Bibliothek zur programmgesteuerten Bearbeitung von Word-Dokumenten. Sie können damit problemlos Word-Dokumente erstellen, ändern, konvertieren und verarbeiten.

### Kann ich mehrere Dokumente gleichzeitig einfügen?
Ja, Sie können den Rückrufhandler so ändern, dass er mehrere Einfügungen verarbeitet, indem er über eine Sammlung von Dokumenten iteriert.

### Gibt es eine kostenlose Testversion?
 Auf jeden Fall! Sie können eine kostenlose Testversion herunterladen unter[Hier](https://releases.aspose.com/).

### Wie erhalte ich Support für Aspose.Words?
 Sie erhalten Unterstützung durch den Besuch der[Aspose.Words-Forum](https://forum.aspose.com/c/words/8).

### Kann ich die Formatierung des eingefügten Dokuments beibehalten?
 Ja, die`NodeImporter` Mit der Klasse können Sie angeben, wie die Formatierung beim Importieren von Knoten von einem Dokument in ein anderes gehandhabt wird.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
