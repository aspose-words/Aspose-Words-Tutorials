---
title: Vytvoření části opakování tabulky mapované na vlastní část XML
linktitle: Vytvoření části opakování tabulky mapované na vlastní část XML
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak vytvořit tabulku s opakující se částí namapovanou na CustomXmlPart v dokumentu aplikace Word pomocí Aspose.Words for .NET.
weight: 10
url: /cs/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření části opakování tabulky mapované na vlastní část XML

## Zavedení

V tomto tutoriálu si projdeme procesem vytváření tabulky s opakující se částí, která je mapována na vlastní XML část pomocí Aspose.Words for .NET. To je užitečné zejména pro dynamické generování dokumentů na základě strukturovaných dat.

## Předpoklady

Než začneme, ujistěte se, že máte následující:
1.  Nainstalovaná knihovna Aspose.Words for .NET. Můžete si jej stáhnout z[Aspose webové stránky](https://releases.aspose.com/words/net/).
2. Základní znalost C# a XML.

## Importovat jmenné prostory

Nezapomeňte do projektu zahrnout potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Krok 1: Inicializujte Document a DocumentBuilder

 Nejprve vytvořte nový dokument a inicializujte jej`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Přidejte vlastní část XML

Přidejte do dokumentu vlastní část XML. Tento XML obsahuje data, která chceme mapovat do naší tabulky:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Krok 3: Vytvořte strukturu tabulky

 Dále použijte`DocumentBuilder` pro vytvoření záhlaví tabulky:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Krok 4: Vytvořte opakující se oddíl

 Vytvořte a`StructuredDocumentTag` (SDT) pro opakující se sekci a namapujte ji na data XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Krok 5: Vytvořte položku opakující se sekce

Vytvořte SDT pro položku opakující se sekce a přidejte ji do opakující se sekce:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Krok 6: Mapování dat XML na buňky tabulky

Vytvořte SDT pro název a autora, namapujte je na data XML a připojte je k řádku:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Krok 7: Uložte dokument

Nakonec uložte dokument do určeného adresáře:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Závěr

Pomocí těchto kroků jste úspěšně vytvořili tabulku s opakující se částí mapovanou na vlastní část XML pomocí Aspose.Words for .NET. To umožňuje dynamické generování obsahu na základě strukturovaných dat, díky čemuž je tvorba dokumentů flexibilnější a výkonnější.

## FAQ

### Co je to StructuredDocumentTag (SDT)?
SDT, také známý jako ovládací prvek obsahu, je ohraničená oblast v dokumentu, která se používá k obsahu strukturovaných dat.

### Mohu ve vlastní části XML použít jiné datové typy?
Ano, svou vlastní část XML můžete strukturovat pomocí libovolných datových typů a podle toho je mapovat.

### Jak přidám další řádky do opakující se části?
Opakující se část automaticky replikuje řádkovou strukturu pro každou položku v mapované cestě XML.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
