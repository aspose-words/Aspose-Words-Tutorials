---
title: Geteilte Tabelle
linktitle: Geteilte Tabelle
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie Tabellen in Word-Dokumenten mit Aspose.Words für .NET aufteilen. Unsere Schritt-für-Schritt-Anleitung macht die Tabellenverwaltung einfach und effizient.
weight: 10
url: /de/net/programming-with-tables/split-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Geteilte Tabelle

## Einführung

Haben Sie schon einmal mit einer großen Tabelle in einem Word-Dokument gearbeitet und sich gewünscht, Sie könnten sie in zwei kleinere, handlichere Tabellen aufteilen? Heute gehen wir genau darauf ein, wie Sie dies mit Aspose.Words für .NET erreichen können. Egal, ob Sie mit umfangreichen Datentabellen oder komplexen Dokumentstrukturen arbeiten, das Aufteilen von Tabellen kann die Lesbarkeit und Organisation verbessern. Lassen Sie uns den schrittweisen Prozess zum Aufteilen einer Tabelle mit Aspose.Words für .NET erkunden.

## Voraussetzungen

Bevor wir mit dem Tutorial beginnen, stellen Sie sicher, dass Sie über Folgendes verfügen:

1.  Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die Aspose.Words für .NET-Bibliothek heruntergeladen und installiert haben. Sie erhalten sie von[Aspose-Veröffentlichungsseite](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Richten Sie eine Entwicklungsumgebung mit .NET Framework-Unterstützung ein, beispielsweise Visual Studio.
3. Beispieldokument: Bereiten Sie ein Word-Dokument vor (`Tables.docx`) mit mindestens einer Tabelle, um den Teilungsvorgang anzuwenden.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt. Dadurch können Sie auf die von Aspose.Words bereitgestellten Klassen und Methoden zugreifen.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt 1: Dokument laden

Beginnen wir mit dem Laden des Dokuments, das die Tabelle enthält, die Sie teilen möchten. Stellen Sie sicher, dass Sie den richtigen Pfad zu Ihrem Dokument angeben.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

## Schritt 2: Identifizieren Sie die zu teilende Tabelle

Identifizieren und rufen Sie als Nächstes die Tabelle ab, die Sie teilen möchten. In diesem Beispiel zielen wir auf die erste Tabelle im Dokument.

```csharp
Table firstTable = (Table)doc.GetChild(NodeType.Table, 0, true);
```

## Schritt 3: Wählen Sie die Zeile aus, bei der geteilt werden soll

Bestimmen Sie die Zeile, in der Sie die Tabelle teilen möchten. Hier teilen wir die Tabelle in der dritten Zeile (einschließlich).

```csharp
Row row = firstTable.Rows[2];
```

## Schritt 4: Einen neuen Tabellencontainer erstellen

Erstellen Sie einen neuen Tabellencontainer, um die Zeilen aufzunehmen, die aus der Originaltabelle verschoben werden.

```csharp
Table table = (Table)firstTable.Clone(false);
```

## Schritt 5: Einfügen des neuen Tabellencontainers

Fügen Sie den neuen Tabellencontainer direkt nach der Originaltabelle in das Dokument ein.

```csharp
firstTable.ParentNode.InsertAfter(table, firstTable);
```

## Schritt 6: Einen Pufferabsatz hinzufügen

Fügen Sie zwischen den beiden Tabellen einen Pufferabsatz hinzu, um sicherzustellen, dass sie getrennt bleiben.

```csharp
firstTable.ParentNode.InsertAfter(new Paragraph(doc), firstTable);
```

## Schritt 7: Zeilen in die neue Tabelle verschieben

Verschiebt die Zeilen aus der ursprünglichen Tabelle in den neuen Tabellencontainer. Diese Schleife wird fortgesetzt, bis die angegebene Zeile (einschließlich) verschoben wurde.

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

Und da haben Sie es! Indem Sie diese Schritte befolgen, können Sie mit Aspose.Words für .NET ganz einfach eine Tabelle in einem Word-Dokument aufteilen. Mit diesem Ansatz können Sie große Tabellen effektiver verwalten und die Lesbarkeit und Organisation Ihrer Dokumente verbessern. Probieren Sie es aus und sehen Sie, wie es Ihre Arbeit mit Tabellen in Word-Dokumenten vereinfacht.

## Häufig gestellte Fragen

### Kann ich eine Tabelle in mehrere Zeilen aufteilen?
Ja, Sie können eine Tabelle in mehrere Zeilen teilen, indem Sie den Vorgang für jeden Teilungspunkt wiederholen.

### Was passiert mit der Formatierung der Originaltabelle?
Die neue Tabelle übernimmt die Formatierung der Originaltabelle. Eventuelle Formatierungsänderungen können bei Bedarf auf die neue Tabelle angewendet werden.

### Ist es möglich, Tabellen wieder zusammenzuführen?
Ja, Sie können Tabellen zusammenführen, indem Sie mit ähnlichen Methoden Zeilen von einer Tabelle in eine andere verschieben.

### Funktioniert diese Methode mit verschachtelten Tabellen?
Ja, Aspose.Words für .NET unterstützt auch Operationen an verschachtelten Tabellen.

### Kann ich diesen Vorgang für mehrere Dokumente automatisieren?
Auf jeden Fall! Sie können ein Skript oder eine Anwendung erstellen, um den Tabellenaufteilungsprozess für mehrere Dokumente zu automatisieren.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
