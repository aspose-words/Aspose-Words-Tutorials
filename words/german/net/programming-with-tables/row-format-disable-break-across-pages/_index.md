---
"description": "Erfahren Sie, wie Sie mit Aspose.Words für .NET seitenübergreifende Zeilenumbrüche in Word-Dokumenten deaktivieren, um die Lesbarkeit und Formatierung der Tabelle beizubehalten."
"linktitle": "Zeilenformat&#58; Seitenumbruch deaktivieren"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Zeilenformat&#58; Seitenumbruch deaktivieren"
"url": "/de/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zeilenformat: Seitenumbruch deaktivieren

## Einführung

Beim Arbeiten mit Tabellen in Word-Dokumenten möchten Sie möglicherweise sicherstellen, dass Zeilen nicht über mehrere Seiten hinweg umgebrochen werden. Dies kann für die Lesbarkeit und Formatierung Ihrer Dokumente von entscheidender Bedeutung sein. Aspose.Words für .NET bietet eine einfache Möglichkeit, seitenübergreifende Zeilenumbrüche zu deaktivieren.

In diesem Tutorial führen wir Sie durch den Vorgang zum Deaktivieren von Zeilenumbrüchen über Seiten hinweg in einem Word-Dokument mit Aspose.Words für .NET.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllen:
- Aspose.Words für .NET-Bibliothek installiert.
- Ein Word-Dokument mit einer Tabelle, die sich über mehrere Seiten erstreckt.

## Namespaces importieren

Importieren Sie zunächst die erforderlichen Namespaces in Ihr Projekt:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Schritt 1: Laden Sie das Dokument

Laden Sie das Dokument mit der mehrseitigen Tabelle.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Schritt 2: Zugriff auf die Tabelle

Greifen Sie auf die erste Tabelle im Dokument zu. Dabei wird davon ausgegangen, dass die zu ändernde Tabelle die erste Tabelle im Dokument ist.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Schritt 3: Deaktivieren Sie den Seitenumbruch für alle Zeilen

Durchlaufen Sie jede Zeile in der Tabelle und legen Sie die `AllowBreakAcrossPages` Eigentum zu `false`Dadurch wird sichergestellt, dass die Zeilen nicht über mehrere Seiten hinweg umbrochen werden.

```csharp
// Deaktivieren Sie den Seitenumbruch für alle Zeilen in der Tabelle.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Schritt 4: Speichern Sie das Dokument

Speichern Sie das geänderte Dokument in Ihrem angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Abschluss

In diesem Tutorial haben wir gezeigt, wie Sie Zeilenumbrüche über Seiten hinweg in einem Word-Dokument mit Aspose.Words für .NET deaktivieren. Indem Sie die oben beschriebenen Schritte befolgen, stellen Sie sicher, dass Ihre Tabellenzeilen erhalten bleiben und nicht über mehrere Seiten verteilt werden. So bleiben Lesbarkeit und Formatierung des Dokuments erhalten.

## Häufig gestellte Fragen

### Kann ich Zeilenumbrüche seitenübergreifend für eine bestimmte Zeile statt für alle Zeilen deaktivieren?  
Ja, Sie können Zeilenumbrüche für bestimmte Zeilen deaktivieren, indem Sie auf die gewünschte Zeile zugreifen und deren `AllowBreakAcrossPages` Eigentum zu `false`.

### Funktioniert diese Methode für Tabellen mit verbundenen Zellen?  
Ja, diese Methode funktioniert für Tabellen mit verbundenen Zellen. Die Eigenschaft `AllowBreakAcrossPages` gilt für die gesamte Zeile, unabhängig von der Zellenzusammenführung.

### Funktioniert diese Methode, wenn die Tabelle in einer anderen Tabelle verschachtelt ist?  
Ja, Sie können auf verschachtelte Tabellen auf die gleiche Weise zugreifen und diese ändern. Stellen Sie sicher, dass Sie die verschachtelte Tabelle über ihren Index oder andere Eigenschaften korrekt referenzieren.

### Wie kann ich überprüfen, ob eine Zeile einen Seitenumbruch zulässt?  
Sie können überprüfen, ob eine Zeile einen Seitenumbruch zulässt, indem Sie auf die `AllowBreakAcrossPages` Eigentum der `RowFormat` und seinen Wert überprüfen.

### Gibt es eine Möglichkeit, diese Einstellung auf alle Tabellen in einem Dokument anzuwenden?  
Ja, Sie können alle Tabellen im Dokument durchlaufen und diese Einstellung auf jede einzelne anwenden.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}