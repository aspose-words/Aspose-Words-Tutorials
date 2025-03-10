---
title: Lesezeichen im Word-Dokument ein- und ausblenden
linktitle: Lesezeichen im Word-Dokument ein- und ausblenden
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie in unserer Schritt-für-Schritt-Anleitung, wie Sie mit Aspose.Words für .NET Lesezeichen in einem Word-Dokument dynamisch ein- oder ausblenden. Perfekt für Entwickler.
weight: 10
url: /de/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lesezeichen im Word-Dokument ein- und ausblenden

## Einführung

Mussten Sie schon einmal bestimmte Teile Ihres Word-Dokuments dynamisch ausblenden oder anzeigen? Dann haben Sie Glück! Mit Aspose.Words für .NET können Sie die Sichtbarkeit von mit Lesezeichen versehenen Inhalten in Ihren Dokumenten ganz einfach verwalten. Dieses Tutorial führt Sie durch den Vorgang des Ein- und Ausblendens von Lesezeichen in einem Word-Dokument mit Aspose.Words für .NET. Wir werden den Code Schritt für Schritt aufschlüsseln, sodass Sie diese Anleitung leicht befolgen können, egal ob Sie ein erfahrener Entwickler oder ein Neuling sind.

## Voraussetzungen

Bevor wir uns in den Code vertiefen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1.  Aspose.Words für .NET: Stellen Sie sicher, dass Sie die Bibliothek Aspose.Words für .NET installiert haben. Wenn nicht, können Sie sie herunterladen[Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Eine IDE wie Visual Studio.
3. Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind von Vorteil.
4. Ein Word-Dokument: Ein Beispiel-Word-Dokument mit Lesezeichen.

## Namespaces importieren

Bevor Sie mit dem Code beginnen, müssen Sie die erforderlichen Namespaces importieren. Fügen Sie am Anfang Ihrer C#-Datei Folgendes hinzu:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Schritt 1: Laden Sie Ihr Dokument

Zunächst müssen Sie das Word-Dokument laden, das die Lesezeichen enthält. So können Sie das tun:

```csharp
// Der Pfad zum Dokumentverzeichnis.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Erläuterung

- dataDir: Dies ist der Verzeichnispfad, in dem sich Ihr Word-Dokument befindet.
-  Dokument doc: Dies initialisiert eine neue Instanz des`Document` Klasse mit Ihrer angegebenen Datei.

## Schritt 2: Mit Lesezeichen versehenen Inhalt ein- oder ausblenden

Als nächstes definieren wir eine Methode zum Anzeigen oder Ausblenden des mit Lesezeichen versehenen Inhalts. Hier ist die vollständige Methode:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD-Lesezeichen}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Erläuterung

- Bookmark bm: Holt das Lesezeichen aus dem Dokument.
- DocumentBuilder-Builder: Hilft bei der Navigation und Änderung des Dokuments.
- Feldfeld: Fügt ein WENN-Feld ein, um den Zustand des Lesezeichens zu überprüfen.
- Knoten currentNode: Durchläuft die Knoten, um den Feldanfang und das Feldende zu finden.

## Schritt 3: Ausführen der Show/Hide-Funktion

 Jetzt müssen Sie den`ShowHideBookmarkedContent` Methode, wobei das Dokument, der Lesezeichenname und das Sichtbarkeitsflag übergeben werden:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Erläuterung

- doc: Ihr Dokumentobjekt.
- „MyBookmark1“: Der Name des Lesezeichens, das Sie anzeigen/ausblenden möchten.
- false: Das Sichtbarkeits-Flag (true zum Anzeigen, false zum Ausblenden).

## Schritt 4: Speichern Sie Ihr Dokument

Speichern Sie abschließend das geänderte Dokument:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Erläuterung

- dataDir + „WorkingWithBookmarks.ShowHideBookmarks.docx“: Der Pfad und der Name des neuen Dokuments, in dem die Änderungen gespeichert werden.

## Abschluss

Und da haben Sie es! Sie haben erfolgreich gelernt, wie Sie mit Aspose.Words für .NET Lesezeichen in einem Word-Dokument ein- und ausblenden. Diese Technik kann unglaublich nützlich sein, um Dokumente mit bedingtem Inhalt dynamisch zu generieren.

## Häufig gestellte Fragen

### Was ist Aspose.Words für .NET?
Aspose.Words für .NET ist eine leistungsstarke Dokumentverarbeitungsbibliothek, mit der Entwickler Word-Dokumente programmgesteuert erstellen, ändern und konvertieren können.

### Wie bekomme ich Aspose.Words für .NET?
 Sie können Aspose.Words für .NET herunterladen von[Hier](https://releases.aspose.com/words/net/)Eine kostenlose Testversion ist ebenfalls verfügbar.

### Kann ich diese Methode für andere Arten von Lesezeichen verwenden?
Ja, diese Methode kann angepasst werden, um die Sichtbarkeit aller Lesezeichen in Ihrem Word-Dokument zu verwalten.

### Was ist, wenn mein Dokument das angegebene Lesezeichen nicht enthält?
Wenn das Lesezeichen nicht vorhanden ist, gibt die Methode einen Fehler aus. Stellen Sie sicher, dass das Lesezeichen vorhanden ist, bevor Sie versuchen, es anzuzeigen/auszublenden.

### Wie kann ich Unterstützung erhalten, wenn ich auf Probleme stoße?
 Sie können Unterstützung von der Aspose-Community erhalten[Hier](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
