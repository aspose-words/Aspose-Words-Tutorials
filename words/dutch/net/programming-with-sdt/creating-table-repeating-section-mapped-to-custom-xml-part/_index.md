---
title: Een herhalende tabelsectie maken die is toegewezen aan een aangepast XML-onderdeel
linktitle: Een herhalende tabelsectie maken die is toegewezen aan een aangepast XML-onderdeel
second_title: Aspose.Words API voor documentverwerking
description: Leer hoe u een tabel met een herhalende sectie kunt maken die is toegewezen aan een CustomXmlPart in een Word-document met behulp van Aspose.Words voor .NET.
weight: 10
url: /nl/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Een herhalende tabelsectie maken die is toegewezen aan een aangepast XML-onderdeel

## Invoering

In deze tutorial doorlopen we het proces van het maken van een tabel met een herhalende sectie die is toegewezen aan een aangepast XML-onderdeel met behulp van Aspose.Words voor .NET. Dit is met name handig voor het dynamisch genereren van documenten op basis van gestructureerde gegevens.

## Vereisten

Voordat we beginnen, zorg ervoor dat u het volgende heeft:
1.  Aspose.Words voor .NET-bibliotheek geïnstalleerd. U kunt het downloaden van de[Aspose-website](https://releases.aspose.com/words/net/).
2. Basiskennis van C# en XML.

## Naamruimten importeren

Zorg ervoor dat u de benodigde naamruimten in uw project opneemt:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Stap 1: Initialiseer Document en DocumentBuilder

 Maak eerst een nieuw document en initialiseer een`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Stap 2: Aangepast XML-onderdeel toevoegen

Voeg een aangepast XML-onderdeel toe aan het document. Deze XML bevat de gegevens die we willen toewijzen aan onze tabel:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Stap 3: De tabelstructuur maken

 Gebruik vervolgens de`DocumentBuilder` om de tabelkop te maken:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Stap 4: Herhalende sectie maken

 Maak een`StructuredDocumentTag` (SDT) voor het herhalende gedeelte en koppel dit aan de XML-gegevens:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Stap 5: Een herhalend sectie-item maken

Maak een SDT voor het herhalende sectie-item en voeg deze toe aan de herhalende sectie:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Stap 6: XML-gegevens toewijzen aan tabelcellen

Maak SDT's voor de titel en auteur, koppel ze aan de XML-gegevens en voeg ze toe aan de rij:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Stap 7: Sla het document op

Sla het document ten slotte op in de opgegeven directory:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Conclusie

Door deze stappen te volgen, hebt u met succes een tabel gemaakt met een herhalende sectie die is toegewezen aan een aangepast XML-onderdeel met behulp van Aspose.Words voor .NET. Dit maakt dynamische contentgeneratie mogelijk op basis van gestructureerde gegevens, waardoor documentcreatie flexibeler en krachtiger wordt.

## Veelgestelde vragen

### Wat is een StructuredDocumentTag (SDT)?
Een SDT, ook wel een content control genoemd, is een begrensd gebied in een document dat wordt gebruikt om gestructureerde gegevens te bevatten.

### Kan ik andere gegevenstypen gebruiken in het aangepaste XML-onderdeel?
Ja, u kunt uw aangepaste XML-onderdeel structureren met elk gegevenstype en deze dienovereenkomstig toewijzen.

### Hoe voeg ik meer rijen toe aan het herhalende gedeelte?
De herhalende sectie repliceert automatisch de rijstructuur voor elk item in het toegewezen XML-pad.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
