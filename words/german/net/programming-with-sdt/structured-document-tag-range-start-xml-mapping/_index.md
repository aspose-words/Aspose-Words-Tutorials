---
"description": "Erfahren Sie, wie Sie XML-Daten mit Aspose.Words für .NET dynamisch an strukturierte Dokument-Tags in Word binden. Folgen Sie unserer Schritt-für-Schritt-Anleitung."
"linktitle": "Strukturiertes Dokument Tag-Bereich Start XML-Mapping"
"second_title": "Aspose.Words Dokumentverarbeitungs-API"
"title": "Strukturiertes Dokument Tag-Bereich Start XML-Mapping"
"url": "/de/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Strukturiertes Dokument Tag-Bereich Start XML-Mapping

## Einführung

Wollten Sie schon immer XML-Daten dynamisch in ein Word-Dokument einfügen? Dann haben Sie Glück! Aspose.Words für .NET macht diese Aufgabe zum Kinderspiel. In diesem Tutorial tauchen wir tief in die strukturierte XML-Zuordnung von Tag-Bereichen in Dokumenten ein. Mit dieser Funktion können Sie benutzerdefinierte XML-Teile an Inhaltssteuerelemente binden und so sicherstellen, dass Ihr Dokumentinhalt nahtlos mit Ihren XML-Daten aktualisiert wird. Verwandeln Sie Ihre Dokumente in dynamische Meisterwerke.

## Voraussetzungen

Bevor wir mit dem Codieren beginnen, stellen wir sicher, dass Sie alles haben, was Sie brauchen:

1. Aspose.Words für .NET-Bibliothek: Stellen Sie sicher, dass Sie die neueste Version haben. Sie können es herunterladen [Hier](https://releases.aspose.com/words/net/).
2. Entwicklungsumgebung: Visual Studio oder jede andere IDE, die C# unterstützt.
3. Grundkenntnisse in C#: Kenntnisse in der C#-Programmierung sind ein Muss.
4. Word-Dokument: Ein Beispiel-Word-Dokument zum Arbeiten.

## Namespaces importieren

Zunächst importieren wir die erforderlichen Namespaces. Dadurch stellen wir sicher, dass wir Zugriff auf alle erforderlichen Klassen und Methoden in Aspose.Words für .NET haben.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Schritt 1: Richten Sie Ihr Dokumentverzeichnis ein

Jedes Projekt braucht eine Grundlage, oder? Hier richten wir den Pfad zu Ihrem Dokumentverzeichnis ein.

```csharp
// Pfad zu Ihrem Dokumentverzeichnis 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Schritt 2: Laden Sie das Word-Dokument

Als Nächstes laden wir das Word-Dokument. In dieses Dokument fügen wir unsere XML-Daten ein.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Schritt 3: Benutzerdefinierten XML-Teil hinzufügen

Wir müssen einen XML-Teil mit den einzufügenden Daten erstellen und ihn der CustomXmlPart-Sammlung des Dokuments hinzufügen. Dieser benutzerdefinierte XML-Teil dient als Datenquelle für unsere strukturierten Dokument-Tags.

### Erstellen eines XML-Teils

Generieren Sie zunächst eine eindeutige ID für den XML-Teil und definieren Sie dessen Inhalt.

```csharp
// Erstellen Sie einen XML-Teil, der Daten enthält, und fügen Sie ihn der CustomXmlPart-Sammlung des Dokuments hinzu.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Überprüfen des XML-Teilinhalts

Um sicherzustellen, dass der XML-Teil korrekt hinzugefügt wurde, drucken wir seinen Inhalt.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Schritt 4: Erstellen Sie ein strukturiertes Dokument-Tag

Ein Structured Document Tag (SDT) ist ein Inhaltssteuerelement, das an einen XML-Teil gebunden werden kann. Hier erstellen wir ein SDT, das den Inhalt unseres benutzerdefinierten XML-Teils anzeigt.

Suchen Sie zunächst den SDT-Bereichsanfang im Dokument.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Schritt 5: XML-Mapping für das SDT festlegen

Nun ist es an der Zeit, unseren XML-Teil an das SDT zu binden. Durch die Festlegung eines XML-Mappings legen wir fest, welcher Teil der XML-Daten im SDT angezeigt werden soll.

Der XPath zeigt auf das spezifische Element im XML-Teil, das wir anzeigen möchten. Hier zeigen wir auf das zweite `<text>` Element innerhalb der `<root>` Element.

```csharp
// Legen Sie eine Zuordnung für unser StructuredDocumentTag fest
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Schritt 6: Speichern Sie das Dokument

Speichern Sie das Dokument abschließend, um die Änderungen in Aktion zu sehen. Das SDT im Word-Dokument zeigt nun den angegebenen XML-Inhalt an.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Abschluss

Und da haben Sie es! Sie haben mit Aspose.Words für .NET erfolgreich einen XML-Teil einem strukturierten Dokument-Tag in einem Word-Dokument zugeordnet. Mit dieser leistungsstarken Funktion können Sie mühelos dynamische und datenbasierte Dokumente erstellen. Ob Sie Berichte, Rechnungen oder andere Dokumenttypen erstellen – XML-Mapping kann Ihren Workflow erheblich optimieren.

## Häufig gestellte Fragen

### Was ist ein strukturiertes Dokument-Tag in Word?
Strukturierte Dokument-Tags, auch Inhaltssteuerelemente genannt, sind Container für bestimmte Inhaltstypen in Word-Dokumenten. Sie können verwendet werden, um Daten zu binden, die Bearbeitung einzuschränken oder Benutzer bei der Dokumenterstellung zu unterstützen.

### Wie kann ich den XML-Teilinhalt dynamisch aktualisieren?
Sie können den XML-Teilinhalt aktualisieren, indem Sie den `xmlPartContent` Zeichenfolge, bevor Sie sie zum Dokument hinzufügen. Aktualisieren Sie einfach die Zeichenfolge mit den neuen Daten und fügen Sie sie dem `CustomXmlParts` Sammlung.

### Kann ich mehrere XML-Teile an verschiedene SDTs im selben Dokument binden?
Ja, Sie können mehrere XML-Teile an verschiedene SDTs im selben Dokument binden. Jedes SDT kann über einen eigenen XML-Teil und eine eigene XPath-Zuordnung verfügen.

### Ist es möglich, komplexe XML-Strukturen auf SDTs abzubilden?
Absolut! Sie können komplexe XML-Strukturen in SDTs abbilden, indem Sie detaillierte XPath-Ausdrücke verwenden, die präzise auf die gewünschten Elemente innerhalb des XML-Teils verweisen.

### Wie kann ich einen XML-Teil aus einem Dokument entfernen?
Sie können einen XML-Teil entfernen, indem Sie den `Remove` Methode auf der `CustomXmlParts` Sammlung, vorbei an der `xmlPartId` des XML-Teils, den Sie entfernen möchten.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}