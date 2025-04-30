---
"description": "Kopieren Sie mit Aspose.Words für .NET mühelos markierten Text zwischen Word-Dokumenten. Erfahren Sie in dieser Schritt-für-Schritt-Anleitung, wie das geht."
"linktitle": "Mit Lesezeichen versehenen Text im Word-Dokument kopieren"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Mit Lesezeichen versehenen Text im Word-Dokument kopieren"
"url": "/de/net/programming-with-bookmarks/copy-bookmarked-text/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mit Lesezeichen versehenen Text im Word-Dokument kopieren

## Einführung

Mussten Sie schon einmal bestimmte Abschnitte von einem Word-Dokument in ein anderes kopieren? Dann haben Sie Glück! In diesem Tutorial zeigen wir Ihnen, wie Sie mit Aspose.Words für .NET markierten Text von einem Word-Dokument in ein anderes kopieren. Ob Sie einen dynamischen Bericht erstellen oder die Dokumentgenerierung automatisieren – diese Anleitung vereinfacht den Vorgang.

## Voraussetzungen

Bevor wir loslegen, stellen Sie sicher, dass Sie Folgendes haben:

- Aspose.Words für .NET-Bibliothek: Sie können es herunterladen von [Hier](https://releases.aspose.com/words/net/).
- Entwicklungsumgebung: Visual Studio oder eine andere .NET-Entwicklungsumgebung.
- Grundkenntnisse in C#: Vertrautheit mit der C#-Programmierung und dem .NET-Framework.

## Namespaces importieren

Stellen Sie zunächst sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt importiert haben:

```csharp
using Aspose.Words;
using Aspose.Words.Import;
using Aspose.Words.Bookmark;
```

## Schritt 1: Laden Sie das Quelldokument

Als Erstes müssen Sie das Quelldokument laden, das den mit einem Lesezeichen versehenen Text enthält, den Sie kopieren möchten.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Bookmarks.docx");
```

Hier, `dataDir` ist der Pfad zu Ihrem Dokumentverzeichnis und `Bookmarks.docx` ist das Quelldokument.

## Schritt 2: Identifizieren Sie das Lesezeichen

Identifizieren Sie als Nächstes das Lesezeichen, das Sie aus dem Quelldokument kopieren möchten.

```csharp
Bookmark srcBookmark = srcDoc.Range.Bookmarks["MyBookmark1"];
```

Ersetzen `"MyBookmark1"` durch den tatsächlichen Namen Ihres Lesezeichens.

## Schritt 3: Zieldokument erstellen

Erstellen Sie nun ein neues Dokument, in das der mit Lesezeichen versehene Text kopiert wird.

```csharp
Document dstDoc = new Document();
CompositeNode dstNode = dstDoc.LastSection.Body;
```

## Schritt 4: Mit Lesezeichen versehenen Inhalt importieren

Um sicherzustellen, dass die Stile und Formatierungen erhalten bleiben, verwenden Sie `NodeImporter` um den mit Lesezeichen versehenen Inhalt aus dem Quelldokument in das Zieldokument zu importieren.

```csharp
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting);
AppendBookmarkedText(importer, srcBookmark, dstNode);
```

## Schritt 5: Definieren der AppendBookmarkedText-Methode

Und hier geschieht die Magie. Definieren Sie eine Methode zum Kopieren des mit Lesezeichen versehenen Textes:

```csharp
private void AppendBookmarkedText(NodeImporter importer, Bookmark srcBookmark, CompositeNode dstNode)
{
    Paragraph startPara = (Paragraph)srcBookmark.BookmarkStart.ParentNode;
    Paragraph endPara = (Paragraph)srcBookmark.BookmarkEnd.ParentNode;

    if (startPara == null || endPara == null)
        throw new InvalidOperationException("Parent of the bookmark start or end is not a paragraph, cannot handle this scenario yet.");

    if (startPara.ParentNode != endPara.ParentNode)
        throw new InvalidOperationException("Start and end paragraphs have different parents, cannot handle this scenario yet.");

    Node endNode = endPara.NextSibling;

    for (Node curNode = startPara; curNode != endNode; curNode = curNode.NextSibling)
    {
        Node newNode = importer.ImportNode(curNode, true);
        dstNode.AppendChild(newNode);
    }
}
```

## Schritt 6: Zieldokument speichern

Speichern Sie abschließend das Zieldokument, um den kopierten Inhalt zu überprüfen.

```csharp
dstDoc.Save(dataDir + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

## Abschluss

Und das war’s! Sie haben mit Aspose.Words für .NET erfolgreich markierten Text von einem Word-Dokument in ein anderes kopiert. Diese Methode eignet sich hervorragend zur Automatisierung von Dokumentbearbeitungsaufgaben und gestaltet Ihren Workflow effizienter und optimierter.

## Häufig gestellte Fragen

### Kann ich mehrere Lesezeichen gleichzeitig kopieren?
Ja, Sie können mehrere Lesezeichen durchlaufen und jedes mit derselben Methode kopieren.

### Was passiert, wenn das Lesezeichen nicht gefunden wird?
Der `Range.Bookmarks` Eigentum wird zurückgegeben `null`, stellen Sie also sicher, dass Sie diesen Fall behandeln, um Ausnahmen zu vermeiden.

### Kann ich die Formatierung des ursprünglichen Lesezeichens beibehalten?
Absolut! Mit `ImportFormatMode.KeepSourceFormatting` stellt sicher, dass die ursprüngliche Formatierung erhalten bleibt.

### Gibt es eine Begrenzung für die Größe des mit Lesezeichen versehenen Textes?
Es gibt keine konkrete Begrenzung, aber die Leistung kann bei extrem großen Dokumenten variieren.

### Kann ich Text zwischen verschiedenen Word-Dokumentformaten kopieren?
Ja, Aspose.Words unterstützt verschiedene Word-Formate und die Methode funktioniert über diese Formate hinweg.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}