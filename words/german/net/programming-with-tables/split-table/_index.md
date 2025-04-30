---
"description": "Erfahren Sie, wie Sie Tabellen in Word-Dokumenten mit Aspose.Words für .NET aufteilen. Unsere Schritt-für-Schritt-Anleitung macht die Tabellenverwaltung einfach und effizient."
"linktitle": "Geteilte Tabelle"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Geteilte Tabelle"
"url": "/de/net/programming-with-tables/split-table/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Geteilte Tabelle

## Einführung

Haben Sie schon einmal mit einer großen Tabelle in einem Word-Dokument gearbeitet und sich gewünscht, diese in zwei kleinere, übersichtlichere Tabellen aufteilen zu können? Heute zeigen wir Ihnen, wie Sie dies mit Aspose.Words für .NET erreichen können. Ob umfangreiche Datentabellen oder komplexe Dokumentstrukturen – das Aufteilen von Tabellen verbessert die Lesbarkeit und Übersichtlichkeit. Wir zeigen Ihnen Schritt für Schritt, wie Sie eine Tabelle mit Aspose.Words für .NET aufteilen.

## Voraussetzungen

Bevor wir mit dem Tutorial beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1. Aspose.Words für .NET Bibliothek: Stellen Sie sicher, dass Sie die Aspose.Words für .NET Bibliothek heruntergeladen und installiert haben. Sie finden sie unter [Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung mit .NET Framework-Unterstützung ein, beispielsweise Visual Studio.
3. Beispieldokument: Bereiten Sie ein Word-Dokument vor (`Tables.docx`) mit mindestens einer Tabelle, um den Aufteilungsvorgang anzuwenden.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt. Dadurch können Sie auf die von Aspose.Words bereitgestellten Klassen und Methoden zugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt 1: Laden Sie das Dokument

Laden Sie zunächst das Dokument mit der zu teilenden Tabelle. Geben Sie unbedingt den korrekten Pfad zu Ihrem Dokument an.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Schritt 2: Identifizieren Sie die zu teilende Tabelle

Identifizieren und rufen Sie anschließend die Tabelle ab, die Sie teilen möchten. In diesem Beispiel wird die erste Tabelle im Dokument ausgewählt.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Schritt 3: Wählen Sie die Zeile aus, bei der geteilt werden soll

Bestimmen Sie die Zeile, in der Sie die Tabelle teilen möchten. Hier teilen wir die Tabelle in der dritten Zeile (einschließlich).

```csharp
Row row = firstTable.Rows[2];
```

## Schritt 4: Erstellen Sie einen neuen Tabellencontainer

Erstellen Sie einen neuen Tabellencontainer, um die Zeilen aufzunehmen, die aus der ursprünglichen Tabelle verschoben werden.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Schritt 5: Einfügen des neuen Tabellencontainers

Fügen Sie den neuen Tabellencontainer direkt nach der Originaltabelle in das Dokument ein.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Schritt 6: Fügen Sie einen Pufferabsatz hinzu

Fügen Sie zwischen den beiden Tabellen einen Pufferabsatz ein, um sicherzustellen, dass sie getrennt bleiben.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## Schritt 7: Zeilen in die neue Tabelle verschieben

Verschiebt die Zeilen aus der ursprünglichen Tabelle in den neuen Tabellencontainer. Diese Schleife wird so lange fortgesetzt, bis die angegebene Zeile (einschließlich) verschoben wurde.

```csharp
Row currentRow;
do
{
    currentRow = firstTable.LastRow;
    table.PrependChild(currentRow);
} while (currentRow != row);
```

## Schritt 8: Speichern Sie das Dokument

Speichern Sie abschließend das geänderte Dokument mit den aufgeteilten Tabellen.

```csharp
doc.Save(dataDir + "WorkingWithTables.SplitTable.docx");
```

## Abschluss

Und fertig! Mit diesen Schritten können Sie eine Tabelle in einem Word-Dokument mit Aspose.Words für .NET ganz einfach teilen. Dieser Ansatz hilft Ihnen, große Tabellen effektiver zu verwalten und die Lesbarkeit und Organisation Ihrer Dokumente zu verbessern. Probieren Sie es aus und erleben Sie, wie es Ihre Arbeit mit Tabellen in Word-Dokumenten vereinfacht.

## Häufig gestellte Fragen

### Kann ich eine Tabelle in mehrere Zeilen aufteilen?
Ja, Sie können eine Tabelle in mehrere Zeilen aufteilen, indem Sie den Vorgang für jeden Teilungspunkt wiederholen.

### Was passiert mit der Formatierung der Originaltabelle?
Die neue Tabelle übernimmt die Formatierung der Originaltabelle. Spezifische Formatierungsänderungen können bei Bedarf auf die neue Tabelle angewendet werden.

### Ist es möglich, Tabellen wieder zusammenzuführen?
Ja, Sie können Tabellen zusammenführen, indem Sie mit ähnlichen Methoden Zeilen von einer Tabelle in eine andere verschieben.

### Funktioniert diese Methode mit verschachtelten Tabellen?
Ja, Aspose.Words für .NET unterstützt auch Operationen an verschachtelten Tabellen.

### Kann ich diesen Vorgang für mehrere Dokumente automatisieren?
Absolut! Sie können ein Skript oder eine Anwendung erstellen, um den Tabellenaufteilungsprozess für mehrere Dokumente zu automatisieren.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}