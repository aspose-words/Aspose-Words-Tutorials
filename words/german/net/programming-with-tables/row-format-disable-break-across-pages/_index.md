---
title: Zeilenformat Umbruch über mehrere Seiten deaktivieren
linktitle: Zeilenformat Umbruch über mehrere Seiten deaktivieren
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET seitenübergreifende Zeilenumbrüche in Word-Dokumenten deaktivieren, um die Lesbarkeit und Formatierung der Tabelle beizubehalten.
weight: 10
url: /de/net/programming-with-tables/row-format-disable-break-across-pages/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zeilenformat Umbruch über mehrere Seiten deaktivieren

## Einführung

Wenn Sie mit Tabellen in Word-Dokumenten arbeiten, möchten Sie möglicherweise sicherstellen, dass Zeilen nicht über mehrere Seiten hinweg umgebrochen werden. Dies kann für die Lesbarkeit und Formatierung Ihrer Dokumente von entscheidender Bedeutung sein. Aspose.Words für .NET bietet eine einfache Möglichkeit, Zeilenumbrüche über mehrere Seiten hinweg zu deaktivieren.

In diesem Tutorial führen wir Sie durch den Prozess zum Deaktivieren von Zeilenumbrüchen über Seiten hinweg in einem Word-Dokument mit Aspose.Words für .NET.

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

## Schritt 1: Dokument laden

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

## Schritt 3: Seitenumbrüche für alle Zeilen deaktivieren

 Durchlaufen Sie jede Zeile in der Tabelle und legen Sie den`AllowBreakAcrossPages`Eigentum an`false`. Dadurch wird sichergestellt, dass die Zeilen nicht über mehrere Seiten hinweg umbrochen werden.

```csharp
// Deaktivieren Sie den Seitenumbruch für alle Zeilen in der Tabelle.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Schritt 4: Speichern Sie das Dokument

Speichern Sie das geänderte Dokument im angegebenen Verzeichnis.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Abschluss

In diesem Tutorial haben wir gezeigt, wie Sie Zeilenumbrüche über Seiten in einem Word-Dokument mit Aspose.Words für .NET deaktivieren. Indem Sie die oben beschriebenen Schritte befolgen, können Sie sicherstellen, dass Ihre Tabellenzeilen intakt bleiben und nicht über mehrere Seiten verteilt werden, sodass die Lesbarkeit und Formatierung des Dokuments erhalten bleibt.

## Häufig gestellte Fragen

### Kann ich Zeilenumbrüche seitenübergreifend für eine bestimmte Zeile statt für alle Zeilen deaktivieren?  
 Ja, Sie können Zeilenumbrüche für bestimmte Zeilen deaktivieren, indem Sie auf die gewünschte Zeile zugreifen und deren`AllowBreakAcrossPages`Eigentum an`false`.

### Funktioniert diese Methode für Tabellen mit verbundenen Zellen?  
 Ja, diese Methode funktioniert für Tabellen mit verbundenen Zellen. Die Eigenschaft`AllowBreakAcrossPages` gilt für die gesamte Zeile, unabhängig von der Zellenzusammenführung.

### Funktioniert diese Methode, wenn die Tabelle in einer anderen Tabelle verschachtelt ist?  
Ja, Sie können auf dieselbe Weise auf verschachtelte Tabellen zugreifen und diese ändern. Stellen Sie sicher, dass Sie die verschachtelte Tabelle über ihren Index oder andere Eigenschaften korrekt referenzieren.

### Wie kann ich prüfen, ob eine Zeile einen Seitenumbruch zulässt?  
 Sie können überprüfen, ob eine Zeile einen Seitenumbruch zulässt, indem Sie auf die`AllowBreakAcrossPages` Eigentum der`RowFormat` und seinen Wert überprüfen.

### Gibt es eine Möglichkeit, diese Einstellung auf alle Tabellen in einem Dokument anzuwenden?  
Ja, Sie können alle Tabellen im Dokument durchlaufen und diese Einstellung auf jede einzelne anwenden.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
