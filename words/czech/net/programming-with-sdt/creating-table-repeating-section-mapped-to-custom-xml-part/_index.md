---
"description": "Naučte se, jak vytvořit tabulku s opakující se sekcí namapovanou na CustomXmlPart v dokumentu Word pomocí Aspose.Words pro .NET."
"linktitle": "Vytvoření opakující se sekce tabulky namapované na vlastní část XML"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vytvoření opakující se sekce tabulky namapované na vlastní část XML"
"url": "/cs/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření opakující se sekce tabulky namapované na vlastní část XML

## Zavedení

V tomto tutoriálu si projdeme procesem vytvoření tabulky s opakující se sekcí, která je namapována na vlastní XML část, pomocí Aspose.Words pro .NET. To je obzvláště užitečné pro dynamické generování dokumentů založených na strukturovaných datech.

## Předpoklady

Než začneme, ujistěte se, že máte následující:
1. Je nainstalována knihovna Aspose.Words pro .NET. Můžete si ji stáhnout z [Webové stránky Aspose](https://releases.aspose.com/words/net/).
2. Základní znalost C# a XML.

## Importovat jmenné prostory

Nezapomeňte do projektu zahrnout potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Krok 1: Inicializace dokumentu a DocumentBuilderu

Nejprve vytvořte nový dokument a inicializujte jej `DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Přidání vlastní XML části

Přidejte do dokumentu vlastní XML část. Tato XML část obsahuje data, která chceme namapovat do naší tabulky:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Krok 3: Vytvořte strukturu tabulky

Dále použijte `DocumentBuilder` vytvoření záhlaví tabulky:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Krok 4: Vytvořte opakující se sekci

Vytvořte `StructuredDocumentTag` (SDT) pro opakující se sekci a namapujte ji na data XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Krok 5: Vytvořte opakující se položku sekce

Vytvořte SDT pro položku opakující se sekce a přidejte ji do opakující se sekce:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Krok 6: Mapování XML dat na buňky tabulky

Vytvořte SDT pro název a autora, namapujte je na data XML a přidejte je do řádku:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Krok 7: Uložte dokument

Nakonec uložte dokument do zadaného adresáře:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Závěr

Pomocí těchto kroků jste úspěšně vytvořili tabulku s opakující se sekcí namapovanou na vlastní XML část pomocí Aspose.Words pro .NET. To umožňuje dynamické generování obsahu na základě strukturovaných dat, čímž se tvorba dokumentů stává flexibilnější a efektivnější.

## Často kladené otázky

### Co je to StructuredDocumentTag (SDT)?
SDT, také známý jako ovládací prvek obsahu, je ohraničená oblast v dokumentu, která se používá k uložení strukturovaných dat.

### Mohu ve vlastní části XML použít jiné datové typy?
Ano, vlastní XML část můžete strukturovat s libovolnými datovými typy a podle toho je namapovat.

### Jak přidám další řádky do opakující se sekce?
Opakující se sekce automaticky replikuje strukturu řádků pro každou položku v mapované cestě XML.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}