---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET verhindern, dass Tabellen in Word-Dokumenten über mehrere Seiten verteilt werden. Folgen Sie unserer Anleitung, um professionelle, lesbare Dokumente zu erhalten."
"linktitle": "Tisch zusammenhalten"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Tisch zusammenhalten"
"url": "/de/net/programming-with-tables/keep-table-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tisch zusammenhalten

## Einführung

Haben Sie sich schon einmal darüber geärgert, dass eine Tabelle in Ihrem Word-Dokument über zwei Seiten verteilt ist? Es ist, als ob Ihre sorgfältig zusammengestellten Informationen plötzlich mittendrin eine Pause einlegen würden! Tabellen auf einer Seite zusammenzuhalten ist entscheidend für Lesbarkeit und Präsentation. Ob für einen Bericht, einen Projektvorschlag oder einfach nur ein persönliches Dokument – geteilte Tabellen können ziemlich störend sein. Zum Glück bietet Aspose.Words für .NET eine clevere Lösung für dieses Problem. In diesem Tutorial zeigen wir Ihnen, wie Sie Ihre Tabellen intakt und ansprechend halten. Los geht‘s!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1. Aspose.Words für .NET - Wenn Sie es noch nicht installiert haben, können Sie es herunterladen von [Hier](https://releases.aspose.com/words/net/).
2. Ein Word-Dokument mit einer Tabelle – Wir arbeiten mit einem Beispieldokument, das eine mehrere Seiten umfassende Tabelle enthält.
3. Grundkenntnisse in C# – Dieses Tutorial setzt voraus, dass Sie über grundlegende Kenntnisse der C#-Programmierung verfügen.

## Namespaces importieren

Zunächst importieren wir die erforderlichen Namespaces. Dadurch erhalten wir Zugriff auf die benötigten Klassen und Methoden von Aspose.Words für .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Lassen Sie uns den Prozess in einfache, verständliche Schritte unterteilen. Wir beginnen mit dem Laden unseres Dokuments und beenden den Vorgang mit dem Speichern des aktualisierten Dokuments, wobei die Tabelle zusammen bleibt.

## Schritt 1: Laden Sie das Dokument

Um mit einem Word-Dokument zu arbeiten, müssen wir es zunächst laden. Wir verwenden die `Document` Klasse dafür.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Schritt 2: Zugriff auf die Tabelle

Als Nächstes müssen wir die Tabelle abrufen, die wir zusammenhalten möchten. Wir gehen davon aus, dass es sich um die erste Tabelle im Dokument handelt.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Schritt 3: KeepWithNext für Absätze festlegen

Um zu verhindern, dass die Tabelle über mehrere Seiten hinweg umbricht, müssen wir Folgendes festlegen: `KeepWithNext` -Eigenschaft für jeden Absatz in der Tabelle, mit Ausnahme der letzten Absätze in der letzten Zeile.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## Schritt 4: Speichern Sie das Dokument

Abschließend speichern wir das aktualisierte Dokument. Dadurch werden unsere Änderungen übernommen und die Tabelle bleibt auf einer Seite zusammengefasst.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Abschluss

Und da haben Sie es! Mit nur wenigen Codezeilen können Sie verhindern, dass Tabellen in Ihren Word-Dokumenten über mehrere Seiten verteilt werden. Diese einfache, aber effektive Lösung sorgt dafür, dass Ihre Tabellen übersichtlich und professionell aussehen und verbessert die Lesbarkeit Ihrer Dokumente. Aspose.Words für .NET macht die Bearbeitung solcher Formatierungsprobleme zum Kinderspiel, sodass Sie sich auf die Erstellung hochwertiger Inhalte konzentrieren können.

## Häufig gestellte Fragen

### Kann ich mit dieser Methode mehrere Tabellen zusammenhalten?  
Ja, Sie können dieselbe Logik auf mehrere Tabellen anwenden, indem Sie jede Tabelle in Ihrem Dokument durchlaufen.

### Was ist, wenn meine Tabelle zu groß ist, um auf eine Seite zu passen?  
Wenn eine Tabelle zu groß für eine einzelne Seite ist, erstreckt sie sich dennoch über mehrere Seiten. Diese Methode stellt sicher, dass kleinere Tabellen intakt bleiben und nicht aufgeteilt werden.

### Gibt es eine Möglichkeit, dies für alle Tabellen in einem Dokument zu automatisieren?  
Ja, Sie können alle Tabellen in Ihrem Dokument durchlaufen und die `KeepWithNext` Eigenschaft für jeden Absatz.

### Benötige ich eine kostenpflichtige Lizenz für Aspose.Words für .NET?  
Sie können mit einer kostenlosen Testversion beginnen von [Hier](https://releases.aspose.com/), für die volle Funktionalität wird jedoch eine kostenpflichtige Lizenz empfohlen.

### Kann ich der Tabelle eine andere Formatierung zuweisen und sie trotzdem zusammenhalten?  
Absolut! Sie können Ihre Tabelle nach Bedarf formatieren und gleichzeitig sicherstellen, dass sie auf einer Seite zusammenhält.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}