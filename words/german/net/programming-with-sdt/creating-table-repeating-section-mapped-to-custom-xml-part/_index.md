---
title: Erstellen eines sich wiederholenden Tabellenabschnitts, der einem benutzerdefinierten XML-Teil zugeordnet ist
linktitle: Erstellen eines sich wiederholenden Tabellenabschnitts, der einem benutzerdefinierten XML-Teil zugeordnet ist
second_title: Aspose.Words Dokumentverarbeitungs-API
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET eine Tabelle mit einem sich wiederholenden Abschnitt erstellen, der einem CustomXmlPart in einem Word-Dokument zugeordnet ist.
weight: 10
url: /de/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Erstellen eines sich wiederholenden Tabellenabschnitts, der einem benutzerdefinierten XML-Teil zugeordnet ist

## Einführung

In diesem Tutorial führen wir Sie durch den Prozess der Erstellung einer Tabelle mit einem sich wiederholenden Abschnitt, der mit Aspose.Words für .NET einem benutzerdefinierten XML-Teil zugeordnet ist. Dies ist besonders nützlich für die dynamische Generierung von Dokumenten basierend auf strukturierten Daten.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass Sie Folgendes haben:
1.  Aspose.Words für .NET-Bibliothek installiert. Sie können es herunterladen von der[Aspose-Website](https://releases.aspose.com/words/net/).
2. Grundlegende Kenntnisse in C# und XML.

## Namespaces importieren

Stellen Sie sicher, dass Sie die erforderlichen Namespaces in Ihr Projekt einschließen:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Schritt 1: Dokument und DocumentBuilder initialisieren

 Erstellen Sie zunächst ein neues Dokument und initialisieren Sie ein`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Schritt 2: Benutzerdefinierten XML-Teil hinzufügen

Fügen Sie dem Dokument einen benutzerdefinierten XML-Teil hinzu. Dieses XML enthält die Daten, die wir unserer Tabelle zuordnen möchten:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Schritt 3: Erstellen der Tabellenstruktur

 Verwenden Sie als nächstes die`DocumentBuilder` So erstellen Sie die Tabellenüberschrift:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Schritt 4: Wiederholenden Abschnitt erstellen

 Erstellen Sie ein`StructuredDocumentTag` (SDT) für den sich wiederholenden Abschnitt und ordnen Sie ihn den XML-Daten zu:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Schritt 5: Wiederholendes Abschnittselement erstellen

Erstellen Sie ein SDT für das sich wiederholende Abschnittselement und fügen Sie es dem sich wiederholenden Abschnitt hinzu:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Schritt 6: XML-Daten Tabellenzellen zuordnen

Erstellen Sie SDTs für Titel und Autor, ordnen Sie sie den XML-Daten zu und hängen Sie sie an die Zeile an:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Schritt 7: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend im angegebenen Verzeichnis:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Abschluss

Wenn Sie diese Schritte befolgen, haben Sie erfolgreich eine Tabelle mit einem sich wiederholenden Abschnitt erstellt, der mit Aspose.Words für .NET einem benutzerdefinierten XML-Teil zugeordnet ist. Dies ermöglicht die dynamische Inhaltsgenerierung auf der Grundlage strukturierter Daten und macht die Dokumenterstellung flexibler und leistungsfähiger.

## Häufig gestellte Fragen

### Was ist ein StructuredDocumentTag (SDT)?
Ein SDT (auch Inhaltssteuerelement genannt) ist ein begrenzter Bereich in einem Dokument, der zur Aufnahme strukturierter Daten verwendet wird.

### Kann ich im benutzerdefinierten XML-Teil andere Datentypen verwenden?
Ja, Sie können Ihren benutzerdefinierten XML-Teil mit beliebigen Datentypen strukturieren und entsprechend zuordnen.

### Wie füge ich dem sich wiederholenden Abschnitt weitere Zeilen hinzu?
Der sich wiederholende Abschnitt repliziert automatisch die Zeilenstruktur für jedes Element im zugeordneten XML-Pfad.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
