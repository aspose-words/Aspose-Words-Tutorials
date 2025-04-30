---
"description": "Naučte se, jak dynamicky vázat XML data na strukturované tagy dokumentů ve Wordu pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu."
"linktitle": "Rozsah značek strukturovaného dokumentu – spuštění mapování XML"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Rozsah značek strukturovaného dokumentu – spuštění mapování XML"
"url": "/cs/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rozsah značek strukturovaného dokumentu – spuštění mapování XML

## Zavedení

Chtěli jste někdy dynamicky vkládat XML data do dokumentu Wordu? Máte štěstí! Aspose.Words pro .NET tento úkol velmi zjednodušuje. V tomto tutoriálu se ponoříme do strukturovaného mapování rozsahu značek dokumentů a jejich spuštění v XML. Tato funkce umožňuje vázat vlastní části XML na ovládací prvky obsahu, což zajišťuje bezproblémovou aktualizaci obsahu dokumentu s vašimi XML daty. Jste připraveni proměnit své dokumenty v dynamická mistrovská díla.

## Předpoklady

Než se pustíme do kódování, ujistěte se, že máte vše, co potřebujete:

1. Knihovna Aspose.Words pro .NET: Ujistěte se, že máte nejnovější verzi. Můžete si ji stáhnout [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE, které podporuje C#.
3. Základní znalost C#: Znalost programování v C# je nutností.
4. Dokument Word: Ukázkový dokument Wordu pro práci.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Tím zajistíme přístup ke všem požadovaným třídám a metodám v Aspose.Words pro .NET.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Krok 1: Nastavení adresáře dokumentů

Každý projekt potřebuje základ, že? Zde nastavíme cestu k adresáři s vašimi dokumenty.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Načtěte dokument Wordu

Dále načteme dokument aplikace Word. Toto je dokument, do kterého budeme vkládat naše XML data.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Krok 3: Přidání vlastní XML části

Potřebujeme vytvořit XML část obsahující data, která chceme vložit, a přidat ji do kolekce CustomXmlPart dokumentu. Tato vlastní XML část bude sloužit jako zdroj dat pro naše strukturované tagy dokumentů.

### Vytvoření XML části

Nejprve vygenerujte jedinečné ID pro XML část a definujte její obsah.

```csharp
// Vytvořte XML část, která obsahuje data, a přidejte ji do kolekce CustomXmlPart dokumentu.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### Ověření obsahu XML části

Abychom zajistili správné přidání části XML, vypíšeme její obsah.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Krok 4: Vytvořte tag strukturovaného dokumentu

Tag strukturovaného dokumentu (SDT) je ovládací prvek obsahu, který se může vázat na část XML. Zde vytvoříme SDT, který zobrazí obsah naší vlastní části XML.

Nejprve v dokumentu vyhledejte začátek rozsahu SDT.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Krok 5: Nastavení mapování XML pro SDT

Nyní je čas propojit naši XML část s SDT. Nastavením mapování XML určíme, která část XML dat se má v SDT zobrazit.

XPath ukazuje na konkrétní prvek v XML části, který chceme zobrazit. Zde ukazujeme na druhý `<text>` prvek v rámci `<root>` živel.

```csharp
// Nastavte mapování pro náš StructuredDocumentTag
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Krok 6: Uložte dokument

Nakonec dokument uložte, abyste viděli změny v akci. SDT v dokumentu Word nyní zobrazí zadaný obsah XML.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Závěr

tady to máte! Úspěšně jste namapovali část XML na strukturovaný tag dokumentu v dokumentu Word pomocí Aspose.Words pro .NET. Tato výkonná funkce vám umožňuje bez námahy vytvářet dynamické a datově řízené dokumenty. Ať už generujete reporty, faktury nebo jakýkoli jiný typ dokumentu, mapování XML může výrazně zefektivnit váš pracovní postup.

## Často kladené otázky

### Co je to tag strukturovaného dokumentu ve Wordu?
Štítky strukturovaných dokumentů, známé také jako ovládací prvky obsahu, jsou kontejnery pro specifické typy obsahu v dokumentech Wordu. Lze je použít k vázání dat, omezení úprav nebo k vedení uživatelů při vytváření dokumentů.

### Jak mohu dynamicky aktualizovat obsah XML části?
Obsah XML části můžete aktualizovat úpravou `xmlPartContent` řetězec před jeho přidáním do dokumentu. Jednoduše řetězec aktualizujte novými daty a přidejte ho do `CustomXmlParts` sbírka.

### Mohu svázat více částí XML s různými SDT v jednom dokumentu?
Ano, v jednom dokumentu můžete navázat více částí XML na různé SDT. Každá SDT může mít svou vlastní unikátní část XML a mapování XPath.

### Je možné mapovat složité XML struktury na SDT?
Rozhodně! Složité XML struktury můžete namapovat na SDT pomocí podrobných výrazů XPath, které přesně ukazují na požadované prvky v XML části.

### Jak mohu z dokumentu odstranit část XML?
Část XML můžete odstranit voláním metody `Remove` metoda na `CustomXmlParts` sbírka, předávání `xmlPartId` části XML, kterou chcete odstranit.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}