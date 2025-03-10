---
title: Zeilenlesezeichen im Word-Dokument entwirren
linktitle: Zeilenlesezeichen im Word-Dokument entwirren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Entwirren Sie verworrene Zeilenlesezeichen in Ihren Word-Dokumenten mühelos mit Aspose.Words für .NET. Diese Anleitung führt Sie durch den Prozess für eine sauberere und sicherere Lesezeichenverwaltung.
weight: 10
url: /de/net/programming-with-bookmarks/untangle-row-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zeilenlesezeichen im Word-Dokument entwirren

## Einführung

Haben Sie schon einmal eine Situation erlebt, in der das Löschen einer Zeile in einem Word-Dokument durch ein Lesezeichen andere Lesezeichen in benachbarten Zeilen durcheinander bringt? Dies kann unglaublich frustrierend sein, insbesondere bei komplexen Tabellen. Glücklicherweise bietet Aspose.Words für .NET eine leistungsstarke Lösung: das Entwirren von Zeilenlesezeichen. 

Diese Anleitung führt Sie durch den Prozess der Entwirrung von Zeilenlesezeichen in Ihren Word-Dokumenten mit Aspose.Words für .NET. Wir zerlegen den Code in leicht verständliche Schritte und erklären den Zweck jeder Funktion, sodass Sie diese lästigen Lesezeichenprobleme selbstbewusst angehen können.

## Voraussetzungen

Bevor Sie loslegen, benötigen Sie einige Dinge:

1.  Aspose.Words für .NET: Diese kommerzielle Bibliothek bietet Funktionen für die programmgesteuerte Arbeit mit Word-Dokumenten. 2. Sie können eine kostenlose Testversion herunterladen von[Downloadlink](https://releases.aspose.com/words/net/) oder erwerben Sie eine Lizenz bei[kaufen](https://purchase.aspose.com/buy).
3. AC#-Entwicklungsumgebung: Visual Studio oder jede andere C#-IDE funktionieren einwandfrei.
4. Ein Word-Dokument mit Zeilenlesezeichen: Zu Demonstrationszwecken verwenden wir ein Beispieldokument mit dem Namen „Tabellenspaltenlesezeichen.docx“.

## Namespaces importieren

Der erste Schritt besteht darin, die erforderlichen Namespaces in Ihr C#-Projekt zu importieren. Diese Namespaces bieten Zugriff auf die Klassen und Funktionen, die wir von Aspose.Words für .NET verwenden werden:

```csharp
using Aspose.Words;
using System;
```

## Schritt 1: Laden Sie das Word-Dokument

 Wir beginnen mit dem Laden des Word-Dokuments, das die verwickelten Zeilenlesezeichen enthält.`Document` Klasse behandelt die Dokumentbearbeitung in Aspose.Words. So wird das Dokument geladen:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY"; // Ersetzen Sie es durch den Speicherort Ihres Dokuments.
Document doc = new Document(dataDir + "Table column bookmarks.docx");
```

 Denken Sie daran, zu ersetzen`"YOUR DOCUMENT DIRECTORY"` durch den tatsächlichen Pfad zu Ihrer Datei „Tabellenspalte Lesezeichen.docx“.

## Schritt 2: Zeilenlesezeichen entwirren

 Hier geschieht die Magie! Die`Untangle` Funktion kümmert sich um die Entwirrung der Zeilenlesezeichen. Lassen Sie uns die Funktionalität genauer betrachten:

```csharp
private void Untangle(Document doc)
{
   foreach (Bookmark bookmark in doc.Range.Bookmarks)
   {
	   // Holen Sie sich die übergeordnete Zeile des Lesezeichens und des Lesezeichenendes.
	   Row row1 = (Row)bookmark.BookmarkStart.GetAncestor(typeof(Row));
	   Row row2 = (Row)bookmark.BookmarkEnd.GetAncestor(typeof(Row));

	   // Prüfen, ob Zeilen gültig und benachbart sind
	   if (row1 != null && row2 != null && row1.NextSibling == row2)
		   //Verschieben Sie das Lesezeichenende zum letzten Absatz der letzten Zelle der obersten Zeile.
		   row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd);
   }
}
```

Hier ist eine schrittweise Erklärung, was der Code macht:

 Wir durchlaufen alle Lesezeichen im Dokument mit einem`foreach` Schleife.
Für jedes Lesezeichen rufen wir die übergeordnete Zeile sowohl des Lesezeichenanfangs (`bookmark.BookmarkStart`) und das Lesezeichenende (`bookmark.BookmarkEnd` ) mit dem`GetAncestor` Verfahren.
Anschließend prüfen wir, ob beide Zeilen gefunden werden (`row1 != null`Und`row2 != null`) und wenn es sich um benachbarte Zeilen handelt (`row1.NextSibling == row2`). Dadurch wird sichergestellt, dass wir nur Lesezeichen ändern, die sich über benachbarte Zeilen erstrecken.
Wenn die Bedingungen erfüllt sind, verschieben wir den Lesezeichen-Endknoten an das Ende des letzten Absatzes in der letzten Zelle der obersten Zeile (`row1.LastCell.LastParagraph.AppendChild(bookmark.BookmarkEnd)`) und entwirrt sie effektiv.

## Schritt 3: Zeile per Lesezeichen löschen

 Nachdem die Lesezeichen entwirrt sind, können wir Zeilen mit ihren Lesezeichennamen sicher löschen. Die`DeleteRowByBookmark` Funktion übernimmt diese Aufgabe:

```csharp
private void DeleteRowByBookmark(Document doc, string bookmarkName)
{
   Bookmark bookmark = doc.Range.Bookmarks[bookmarkName];

   Row row = (Row)bookmark?.BookmarkStart.GetAncestor(typeof(Row));
   row?.Remove();
}
```

Hier ist eine Aufschlüsselung dieser Funktion:

Wir nehmen den Lesezeichennamen (`bookmarkName`) als Eingabe.
 Wir ermitteln das entsprechende Lesezeichenobjekt mit`doc.Range.Bookmarks[bookmarkName]`.
Wir erhalten dann die übergeordnete Zeile des Lesezeichens mit`GetAncestor` (ähnlich wie die`Untangle` Funktion).
Abschließend prüfen wir, ob das Lesezeichen und die Zeile vorhanden sind (`bookmark != null` Und

## Schritt 4: Entwirrung überprüfen

 Während die`Untangle` Funktion soll die Sicherheit anderer Lesezeichen gewährleisten, es ist immer eine gute Praxis, dies zu überprüfen. So können wir überprüfen, ob beim Entwirrungsprozess nicht versehentlich das Ende eines anderen Lesezeichens gelöscht wurde:

```csharp
if (doc.Range.Bookmarks["ROW1"].BookmarkEnd == null)
   throw new Exception("Wrong, the end of the bookmark was deleted.");
```

Dieser Codeausschnitt prüft, ob das Ende des Lesezeichens mit dem Namen „ROW1“ noch vorhanden ist, nachdem die Zeile mit dem Lesezeichen „ROW2“ gelöscht wurde. Wenn es null ist, wird eine Ausnahme ausgelöst, die auf ein Problem beim Entwirrungsprozess hinweist. 

## Schritt 5: Speichern Sie das Dokument

 Nachdem Sie die Lesezeichen entwirrt und ggf. Zeilen gelöscht haben, speichern Sie das geänderte Dokument mit dem`Save` Verfahren:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

Dadurch wird das Dokument mit den entwirrten Lesezeichen und allen gelöschten Zeilen unter einem neuen Dateinamen „WorkingWithBookmarks.UntangleRowBookmarks.docx“ gespeichert. 

## Abschluss

 Wenn Sie diese Schritte befolgen und die`Untangle`Funktion können Sie Zeilenlesezeichen in Ihren Word-Dokumenten mit Aspose.Words für .NET effektiv entwirren. Dadurch wird sichergestellt, dass das Löschen von Zeilen nach Lesezeichen keine unbeabsichtigten Folgen mit anderen Lesezeichen in benachbarten Zeilen hat. Denken Sie daran, Platzhalter wie`"YOUR DOCUMENT DIRECTORY"` durch Ihre tatsächlichen Pfade und Dateinamen.

## Häufig gestellte Fragen

### Ist Aspose.Words für .NET kostenlos?

 Aspose.Words für .NET ist eine kommerzielle Bibliothek mit einer kostenlosen Testversion. Sie können sie herunterladen von[Downloadlink](https://releases.aspose.com/words/net/).

### Kann ich Zeilenlesezeichen in Word manuell entwirren?

Obwohl es technisch möglich ist, kann das manuelle Entwirren von Lesezeichen in Word mühsam und fehleranfällig sein. Aspose.Words für .NET automatisiert diesen Prozess und spart Ihnen Zeit und Mühe.

###  Was passiert, wenn die`Untangle` function encounters an error?

Der Code enthält einen Ausnahmehandler, der eine Ausnahme auslöst, wenn beim Entwirrungsprozess versehentlich das Ende eines anderen Lesezeichens gelöscht wird. Sie können diese Fehlerbehandlung an Ihre spezifischen Anforderungen anpassen.

### Kann ich diesen Code verwenden, um Lesezeichen über nicht benachbarte Zeilen hinweg zu entwirren?

Derzeit konzentriert sich der Code auf das Entwirren von Lesezeichen, die sich über nebeneinanderliegende Zeilen erstrecken. Das Ändern des Codes zum Verarbeiten nicht nebeneinanderliegender Zeilen würde zusätzliche Logik erfordern, um diese Szenarien zu identifizieren und zu verarbeiten.

### Gibt es bei der Verwendung dieses Ansatzes irgendwelche Einschränkungen?

Bei diesem Ansatz wird davon ausgegangen, dass Lesezeichen innerhalb der Tabellenzellen klar definiert sind. Wenn Lesezeichen außerhalb von Zellen oder an unerwarteten Stellen platziert werden, funktioniert der Entwirrungsprozess möglicherweise nicht wie beabsichtigt.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
