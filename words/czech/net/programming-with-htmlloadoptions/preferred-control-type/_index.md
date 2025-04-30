---
"description": "Naučte se, jak vložit pole formuláře se seznamem do dokumentu Word pomocí Aspose.Words pro .NET. Postupujte podle tohoto podrobného návodu pro bezproblémovou integraci obsahu HTML."
"linktitle": "Preferovaný typ ovládacího prvku v dokumentu Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Preferovaný typ ovládacího prvku v dokumentu Word"
"url": "/cs/net/programming-with-htmlloadoptions/preferred-control-type/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Preferovaný typ ovládacího prvku v dokumentu Word

## Zavedení

Ponořujeme se do zajímavého tutoriálu o tom, jak pracovat s možnostmi načítání HTML v Aspose.Words pro .NET, se zaměřením na nastavení preferovaného typu ovládacího prvku při vkládání pole formuláře se seznamem do dokumentu Word. Tento podrobný návod vám pomůže pochopit, jak efektivně manipulovat s obsahem HTML a vykreslovat ho v dokumentech Word pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíme do samotného kódu, je potřeba mít připraveno několik věcí:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words pro .NET. Můžete si ji stáhnout z [webové stránky](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Měli byste mít nastavené vývojové prostředí, například Visual Studio.
3. Základní znalost C#: Pro pokračování v tomto tutoriálu je nezbytná základní znalost programování v C#.
4. HTML obsah: Základní znalost HTML je užitečná, protože v tomto příkladu budeme pracovat s HTML obsahem.

## Importovat jmenné prostory

Nejprve si importujme potřebné jmenné prostory, abychom mohli začít:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

Nyní si příklad rozdělme do několika kroků, abychom zajistili jasnost a pochopení.

## Krok 1: Nastavení HTML obsahu

Nejprve musíme definovat HTML obsah, který chceme vložit do dokumentu Word. Zde je úryvek HTML kódu, který použijeme:

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>item1</option>
            <option value='val2'></option>                        
        </select>
    </html>
";
```

Tento HTML kód obsahuje jednoduchý rozbalovací seznam se dvěma možnostmi. Načteme tento HTML kód do dokumentu Word a určíme, jak se má vykreslit.

## Krok 2: Definování adresáře dokumentů

Dále určete adresář, kam bude dokument Wordu uložen. To pomůže s organizací souborů a udržením přehledné správy cest.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete dokument Wordu uložit.

## Krok 3: Konfigurace možností načítání HTML

Zde konfigurujeme možnosti načítání HTML, se zvláštním zaměřením na `PreferredControlType` vlastnost. Tato vlastnost určuje, jak se má pole se seznamem vykreslit v dokumentu Word.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

Nastavením `PreferredControlType` na `HtmlControlType.StructuredDocumentTag`, zajistíme, aby se pole se seznamem v dokumentu Word vykreslilo jako tag strukturovaného dokumentu (SDT).

## Krok 4: Načtěte HTML obsah do dokumentu

Pomocí nakonfigurovaných možností načítání načteme HTML obsah do nového dokumentu Wordu.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Zde převedeme HTML řetězec na bajtové pole a načteme ho do dokumentu pomocí paměťového proudu. Tím zajistíme, že Aspose.Words správně interpretuje a vykreslí HTML obsah.

## Krok 5: Uložte dokument

Nakonec uložte dokument do zadaného adresáře ve formátu DOCX.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

Tím se uloží dokument aplikace Word s vykresleným ovládacím prvkem pole se seznamem na zadané místo.

## Závěr

A tady to máte! Úspěšně jsme vložili pole formuláře se seznamem do dokumentu Word pomocí Aspose.Words pro .NET s využitím možností načítání HTML. Tato podrobná příručka by vám měla pomoci pochopit proces a aplikovat ho na vaše projekty. Ať už automatizujete vytváření dokumentů nebo manipulujete s obsahem HTML, Aspose.Words pro .NET poskytuje výkonné nástroje k dosažení vašich cílů.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro manipulaci s dokumenty, která umožňuje vývojářům programově vytvářet, upravovat, převádět a vykreslovat dokumenty Wordu.

### Mohu s Aspose.Words pro .NET použít jiné typy HTML ovládacích prvků?
Ano, Aspose.Words pro .NET podporuje různé typy ovládacích prvků HTML. Můžete si přizpůsobit, jak se různé ovládací prvky vykreslují v dokumentu Word.

### Jak zpracuji složitý HTML obsah v Aspose.Words pro .NET?
Aspose.Words pro .NET poskytuje komplexní podporu pro HTML, včetně složitých prvků. Ujistěte se, že jste nakonfigurovali `HtmlLoadOptions` vhodně zpracovat váš specifický HTML obsah.

### Kde najdu další příklady a dokumentaci?
Podrobnou dokumentaci a příklady naleznete na [Dokumentace k Aspose.Words pro .NET](https://reference.aspose.com/words/net/).

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
Ano, můžete si stáhnout bezplatnou zkušební verzi z [Webové stránky Aspose](https://releases.aspose.com/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}