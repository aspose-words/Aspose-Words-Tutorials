---
title: Rozsah tagů strukturovaného dokumentu Spusťte mapování XML
linktitle: Rozsah tagů strukturovaného dokumentu Spusťte mapování XML
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak dynamicky svázat data XML se strukturovanými značkami dokumentů ve Wordu pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce.
weight: 10
url: /cs/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rozsah tagů strukturovaného dokumentu Spusťte mapování XML

## Zavedení

Chtěli jste někdy dynamicky vkládat data XML do dokumentu aplikace Word? Tak to máš štěstí! Aspose.Words pro .NET dělá tento úkol hračkou. V tomto tutoriálu se ponoříme hluboko do strukturovaného mapování rozsahu značek dokumentu XML. Tato funkce vám umožňuje svázat vlastní části XML s ovládacími prvky obsahu, což zajišťuje bezproblémovou aktualizaci obsahu dokumentu s vašimi daty XML. Jste připraveni přeměnit vaše dokumenty na dynamická mistrovská díla.

## Předpoklady

Než se pustíme do kódovací části, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words for .NET Library: Ujistěte se, že máte nejnovější verzi. Můžete si jej stáhnout[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE, které podporuje C#.
3. Základní znalost C#: Znalost programování v C# je nutností.
4. Dokument aplikace Word: Ukázkový dokument aplikace Word pro práci.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory. To zajistí, že budeme mít přístup ke všem požadovaným třídám a metodám v Aspose.Words pro .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Krok 1: Nastavte adresář dokumentů

Každý projekt potřebuje základ, ne? Zde nastavíme cestu k vašemu adresáři dokumentů.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Načtěte dokument aplikace Word

Dále načteme dokument aplikace Word. Toto je dokument, kam budeme vkládat naše XML data.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Krok 3: Přidejte vlastní část XML

Musíme vytvořit část XML obsahující data, která chceme vložit, a přidat ji do kolekce CustomXmlPart dokumentu. Tato vlastní část XML bude sloužit jako zdroj dat pro naše značky strukturovaných dokumentů.

### Vytvoření části XML

Nejprve vygenerujte jedinečné ID pro část XML a definujte její obsah.

```csharp
// Vytvořte část XML, která obsahuje data, a přidejte ji do kolekce CustomXmlPart dokumentu.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Ověřte obsah části XML

Aby bylo zajištěno správné přidání části XML, tiskneme její obsah.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Krok 4: Vytvořte štítek strukturovaného dokumentu

Značka strukturovaného dokumentu (SDT) je ovládací prvek obsahu, který se může vázat na část XML. Zde vytvoříme SDT, která zobrazí obsah naší vlastní části XML.

Nejprve v dokumentu vyhledejte začátek rozsahu SDT.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Krok 5: Nastavte mapování XML pro SDT

Nyní je čas spojit naši část XML s SDT. Nastavením mapování XML určujeme, která část dat XML se má zobrazit v SDT.

 Cesta XPath ukazuje na konkrétní prvek v části XML, který chceme zobrazit. Zde ukážeme na druhou`<text>` prvek uvnitř`<root>` živel.

```csharp
// Nastavte mapování pro náš StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Krok 6: Uložte dokument

Nakonec dokument uložte, abyste viděli změny v akci. SDT v dokumentu aplikace Word nyní zobrazí zadaný obsah XML.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Závěr

tady to máte! Úspěšně jste namapovali část XML na značku strukturovaného dokumentu v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná funkce vám umožňuje bez námahy vytvářet dynamické dokumenty založené na datech. Ať už generujete sestavy, faktury nebo jakýkoli jiný typ dokumentu, mapování XML může výrazně zefektivnit váš pracovní postup.

## FAQ

### Co je to značka strukturovaného dokumentu ve Wordu?
Značky strukturovaného dokumentu, známé také jako ovládací prvky obsahu, jsou kontejnery pro konkrétní typy obsahu v dokumentech aplikace Word. Lze je použít ke svázání dat, omezení úprav nebo vedení uživatelů při vytváření dokumentů.

### Jak mohu dynamicky aktualizovat obsah části XML?
 Obsah části XML můžete aktualizovat úpravou souboru`xmlPartContent` řetězec před jeho přidáním do dokumentu. Jednoduše aktualizujte řetězec novými daty a přidejte je do`CustomXmlParts` sbírka.

### Mohu svázat více částí XML s různými SDT ve stejném dokumentu?
Ano, můžete svázat více částí XML s různými SDT ve stejném dokumentu. Každý SDT může mít svou vlastní jedinečnou část XML a mapování XPath.

### Je možné mapovat složité struktury XML na SDT?
Absolutně! Složité struktury XML můžete mapovat na SDT pomocí podrobných výrazů XPath, které přesně ukazují na požadované prvky v části XML.

### Jak mohu odstranit část XML z dokumentu?
 Část XML můžete odstranit voláním`Remove` metoda na`CustomXmlParts` sběr, předávání`xmlPartId` části XML, kterou chcete odstranit.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
