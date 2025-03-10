---
title: Tisch zusammenhalten
linktitle: Tisch zusammenhalten
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET verhindern, dass Tabellen in Word-Dokumenten über mehrere Seiten verteilt werden. Folgen Sie unserer Anleitung, um professionelle, lesbare Dokumente zu erhalten.
weight: 10
url: /de/net/programming-with-tables/keep-table-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tisch zusammenhalten

## Einführung

Waren Sie schon einmal frustriert, wenn eine Tabelle in Ihrem Word-Dokument auf zwei Seiten aufgeteilt ist? Es ist, als ob Ihre sorgfältig angelegten Informationen plötzlich auf halbem Weg eine Pause einlegen würden! Tabellen auf einer Seite zusammenzuhalten ist für die Lesbarkeit und Präsentation entscheidend. Ob für einen Bericht, einen Projektvorschlag oder einfach nur ein persönliches Dokument, aufgeteilte Tabellen können ziemlich störend sein. Zum Glück hat Aspose.Words für .NET eine raffinierte Möglichkeit, dieses Problem zu lösen. In diesem Tutorial gehen wir die Schritte durch, um Ihre Tabellen intakt und gut aussehen zu lassen. Lassen Sie uns eintauchen!

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:

1.  Aspose.Words für .NET - Wenn Sie es noch nicht installiert haben, können Sie es herunterladen von[Hier](https://releases.aspose.com/words/net/).
2. Ein Word-Dokument mit einer Tabelle – Wir arbeiten mit einem Beispieldokument, das eine mehrere Seiten umfassende Tabelle enthält.
3. Grundkenntnisse in C# – Dieses Tutorial setzt voraus, dass Sie über grundlegende Kenntnisse der C#-Programmierung verfügen.

## Namespaces importieren

Als Erstes importieren wir die erforderlichen Namespaces. Dadurch erhalten wir Zugriff auf die Klassen und Methoden, die wir von Aspose.Words für .NET benötigen.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Lassen Sie uns den Vorgang in einfache, leicht verständliche Schritte unterteilen. Wir beginnen mit dem Laden unseres Dokuments und beenden es mit dem Speichern des aktualisierten Dokuments, wobei die Tabelle zusammen bleibt.

## Schritt 1: Dokument laden

 Um mit einem Word-Dokument arbeiten zu können, müssen wir es zunächst laden. Wir verwenden dazu die`Document` Klasse dafür.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Schritt 2: Zugriff auf die Tabelle

Als nächstes müssen wir die Tabelle abrufen, die wir zusammenhalten möchten. Wir gehen davon aus, dass es sich um die erste Tabelle im Dokument handelt.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Schritt 3: KeepWithNext für Absätze festlegen

 Um zu verhindern, dass die Tabelle über mehrere Seiten verteilt wird, müssen wir die`KeepWithNext` -Eigenschaft für jeden Absatz in der Tabelle, mit Ausnahme der letzten Absätze in der letzten Zeile.

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

Abschließend speichern wir das aktualisierte Dokument. Dadurch werden unsere Änderungen übernommen und die Tabelle bleibt auf einer Seite zusammen.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Abschluss

Und da haben Sie es! Mit nur wenigen Codezeilen können Sie verhindern, dass Ihre Tabellen in Ihren Word-Dokumenten auf mehrere Seiten aufgeteilt werden. Diese einfache, aber effektive Lösung sorgt dafür, dass Ihre Tabellen ordentlich und professionell bleiben und verbessert die Lesbarkeit Ihrer Dokumente. Aspose.Words für .NET macht die Handhabung solcher Formatierungsprobleme zum Kinderspiel, sodass Sie sich auf die Erstellung großartiger Inhalte konzentrieren können.

## Häufig gestellte Fragen

### Kann ich mit dieser Methode mehrere Tabellen zusammenhalten?  
Ja, Sie können die gleiche Logik auf mehrere Tabellen anwenden, indem Sie jede Tabelle in Ihrem Dokument durchlaufen.

### Was passiert, wenn meine Tabelle zu groß ist, um auf eine Seite zu passen?  
Wenn eine Tabelle zu groß ist, um auf eine einzelne Seite zu passen, wird sie sich trotzdem über mehrere Seiten erstrecken. Mit dieser Methode wird sichergestellt, dass kleinere Tabellen intakt bleiben und nicht aufgeteilt werden.

### Gibt es eine Möglichkeit, dies für alle Tabellen in einem Dokument zu automatisieren?  
 Ja, Sie können alle Tabellen in Ihrem Dokument durchlaufen und die`KeepWithNext` -Eigenschaft für jeden Absatz.

### Benötige ich eine kostenpflichtige Lizenz für Aspose.Words für .NET?  
Sie können mit einer kostenlosen Testversion beginnen von[Hier](https://releases.aspose.com/), für die volle Funktionalität wird jedoch eine kostenpflichtige Lizenz empfohlen.

### Kann ich eine andere Formatierung auf die Tabelle anwenden und sie trotzdem zusammenhalten?  
Auf jeden Fall! Sie können Ihre Tabelle nach Bedarf formatieren und gleichzeitig sicherstellen, dass sie auf einer Seite zusammenbleibt.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
