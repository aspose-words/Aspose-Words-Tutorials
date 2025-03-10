---
title: Preferovaný typ ovládacího prvku v dokumentu aplikace Word
linktitle: Preferovaný typ ovládacího prvku v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak vložit pole formuláře se seznamem do dokumentu aplikace Word pomocí Aspose.Words for .NET. Postupujte podle tohoto podrobného průvodce pro bezproblémovou integraci obsahu HTML.
weight: 10
url: /cs/net/programming-with-htmlloadoptions/preferred-control-type/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Preferovaný typ ovládacího prvku v dokumentu aplikace Word

## Zavedení

ponoříme se do vzrušujícího návodu, jak pracovat s možnostmi načítání HTML v Aspose.Words pro .NET, konkrétně se zaměřujeme na nastavení preferovaného typu ovládacího prvku při vkládání pole formuláře se seznamem do dokumentu aplikace Word. Tento podrobný průvodce vám pomůže pochopit, jak efektivně manipulovat a vykreslovat obsah HTML v dokumentech aplikace Word pomocí Aspose.Words for .NET.

## Předpoklady

Než se pustíme do kódu, je třeba mít připraveno několik věcí:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words for .NET. Můžete si jej stáhnout z[webové stránky](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Měli byste mít nastavené vývojové prostředí, jako je Visual Studio.
3. Základní znalost C#: Spolu s výukovým programem je nutné dodržet základní znalost programování v C#.
4. Obsah HTML: Základní znalost HTML je užitečná, protože v tomto příkladu budeme pracovat s obsahem HTML.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory, abychom mohli začít:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

Nyní rozdělme příklad do několika kroků, abychom zajistili jasnost a porozumění.

## Krok 1: Nastavte obsah HTML

Nejprve musíme definovat obsah HTML, který chceme vložit do dokumentu aplikace Word. Zde je úryvek HTML, který budeme používat:

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

Toto HTML obsahuje jednoduché pole se dvěma možnostmi. Tento HTML načteme do dokumentu aplikace Word a určíme, jak se má vykreslit.

## Krok 2: Definujte adresář dokumentů

Dále určete adresář, kam se uloží váš dokument aplikace Word. To pomáhá při organizování souborů a udržování čistoty ve správě cest.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kam chcete uložit dokument aplikace Word.

## Krok 3: Nakonfigurujte možnosti načítání HTML

 Zde nakonfigurujeme možnosti načítání HTML, zejména se zaměřením na`PreferredControlType`vlastnictví. To určuje, jak má být pole se seznamem vykresleno v dokumentu aplikace Word.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

 Nastavením`PreferredControlType` na`HtmlControlType.StructuredDocumentTag`, zajistíme, aby se pole se seznamem vykreslilo jako značka strukturovaného dokumentu (SDT) v dokumentu aplikace Word.

## Krok 4: Načtěte obsah HTML do dokumentu

Pomocí nakonfigurovaných možností načtení načteme obsah HTML do nového dokumentu aplikace Word.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Zde převedeme řetězec HTML na bajtové pole a načteme jej do dokumentu pomocí paměťového proudu. To zajišťuje, že obsah HTML je správně interpretován a vykreslen Aspose.Words.

## Krok 5: Uložte dokument

Nakonec dokument uložte do určeného adresáře ve formátu DOCX.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

Tím uložíte dokument aplikace Word s vykresleným ovládacím prvkem pole se seznamem do zadaného umístění.

## Závěr

tady to máte! Úspěšně jsme vložili pole formuláře se seznamem do dokumentu aplikace Word pomocí Aspose.Words for .NET využitím možností načítání HTML. Tento podrobný průvodce by vám měl pomoci pochopit proces a aplikovat jej na vaše projekty. Ať už automatizujete vytváření dokumentů nebo manipulujete s obsahem HTML, Aspose.Words for .NET poskytuje výkonné nástroje k dosažení vašich cílů.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro manipulaci s dokumenty, která umožňuje vývojářům vytvářet, upravovat, převádět a vykreslovat dokumenty aplikace Word programově.

### Mohu s Aspose.Words pro .NET používat jiné typy ovládacích prvků HTML?
Ano, Aspose.Words for .NET podporuje různé typy ovládacích prvků HTML. Způsob vykreslování různých ovládacích prvků v dokumentu aplikace Word můžete přizpůsobit.

### Jak zvládnu složitý obsah HTML v Aspose.Words for .NET?
 Aspose.Words for .NET poskytuje komplexní podporu pro HTML, včetně složitých prvků. Ujistěte se, že jste nakonfigurovali`HtmlLoadOptions`vhodně zpracovat váš konkrétní obsah HTML.

### Kde najdu další příklady a dokumentaci?
 Podrobnou dokumentaci a příklady naleznete na[Stránka dokumentace Aspose.Words for .NET](https://reference.aspose.com/words/net/).

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?
 Ano, můžete si stáhnout bezplatnou zkušební verzi z[Aspose webové stránky](https://releases.aspose.com/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
