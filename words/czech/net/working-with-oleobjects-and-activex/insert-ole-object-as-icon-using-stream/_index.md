---
"description": "V tomto podrobném návodu se naučíte, jak vložit objekt OLE jako ikonu pomocí streamu s Aspose.Words pro .NET."
"linktitle": "Vložit objekt Ole jako ikonu pomocí Streamu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložit objekt Ole jako ikonu pomocí Streamu"
"url": "/cs/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon-using-stream/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložit objekt Ole jako ikonu pomocí Streamu

## Zavedení

tomto tutoriálu se ponoříme do super funkce Aspose.Words pro .NET: vkládání objektu OLE (Object Linking and Embedding) jako ikony pomocí streamu. Ať už vkládáte prezentaci v PowerPointu, tabulku v Excelu nebo jakýkoli jiný typ souboru, tento průvodce vám přesně ukáže, jak na to. Jste připraveni začít? Pojďme na to!

## Předpoklady

Než se pustíme do kódu, je tu pár věcí, které budete potřebovat:

- Aspose.Words pro .NET: Pokud jste tak ještě neučinili, [stáhnout](https://releases.aspose.com/words/net/) a nainstalujte Aspose.Words pro .NET.
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí C#.
- Vstupní soubory: Soubor, který chcete vložit (např. prezentace v PowerPointu), a obrázek ikony.

## Importovat jmenné prostory

Nejprve se ujistěte, že jste do projektu importovali potřebné jmenné prostory:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Pojďme si celý proces rozebrat krok za krokem, aby se vám snadno sledoval.

## Krok 1: Vytvořte nový dokument

Nejprve si vytvoříme nový dokument a nástroj pro tvorbu dokumentů, s nímž budeme pracovat.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Myslete na `Document` jako tvé prázdné plátno a `DocumentBuilder` jako váš štětec. Připravujeme si nástroje, abychom mohli začít tvořit naše mistrovské dílo.

## Krok 2: Příprava streamu

Dále musíme připravit paměťový stream, který obsahuje soubor, který chceme vložit. V tomto příkladu vložíme prezentaci v PowerPointu.

```csharp
using (MemoryStream stream = new MemoryStream(File.ReadAllBytes("Path_to_your_directory/Presentation.pptx")))
{
```

Tento krok je jako nanášení barvy na štětec. Připravujeme náš soubor k vložení.

## Krok 3: Vložení objektu OLE jako ikony

Nyní použijeme nástroj pro tvorbu dokumentů k vložení objektu OLE do dokumentu. Zadáme souborový proud, ProgID pro typ souboru (v tomto případě „Balíček“), cestu k obrázku ikony a popisek pro vložený soubor.

```csharp
builder.InsertOleObjectAsIcon(stream, "Package", "Path_to_your_directory/Logo icon.ico", "My embedded file");
}
```

A tady se děje ta magie! Vložíme náš soubor a zobrazíme ho jako ikonu v dokumentu.

## Krok 4: Uložte dokument

Nakonec dokument uložíme do zadané cesty.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIconUsingStream.docx");
```

Tento krok je jako byste zarámovali hotový obraz a pověsili ho na zeď. Váš dokument je nyní připraven k použití!

## Závěr

A tady to máte! Úspěšně jste vložili objekt OLE jako ikonu do dokumentu Wordu pomocí Aspose.Words pro .NET. Tato výkonná funkce vám pomůže snadno vytvářet dynamické a interaktivní dokumenty. Ať už vkládáte prezentace, tabulky nebo jiné soubory, Aspose.Words to udělá hračkou. Tak do toho, vyzkoušejte to a uvidíte, jaký rozdíl to ve vašich dokumentech udělá!

## Často kladené otázky

### Mohu touto metodou vkládat různé typy souborů?
Ano, můžete vložit jakýkoli typ souboru podporovaný technologií OLE, včetně Wordu, Excelu, PowerPointu a dalších.

### Potřebuji speciální licenci k používání Aspose.Words pro .NET?
Ano, Aspose.Words pro .NET vyžaduje licenci. Můžete si ji pořídit. [bezplatná zkušební verze](https://releases.aspose.com/) nebo si zakoupit [dočasná licence](https://purchase.aspose.com/temporary-license/) pro testování.

### Mohu si přizpůsobit ikonu používanou pro objekt OLE?
Rozhodně! Pro ikonu můžete použít libovolný soubor s obrázkem, stačí zadat jeho cestu v `InsertOleObjectAsIcon` metoda.

### Co se stane, když jsou cesty k souborům nebo ikonám nesprávné?
Metoda vyvolá výjimku. Abyste předešli chybám, ujistěte se, že cesty k souborům jsou správné.

### Je možné vložený objekt propojit místo jeho vkládání?
Ano, Aspose.Words umožňuje vkládat propojené objekty OLE, které odkazují na soubor bez vkládání jeho obsahu.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}