---
title: Vložit OLE objekt jako ikonu pomocí proudu
linktitle: Vložit OLE objekt jako ikonu pomocí proudu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak vložit objekt OLE jako ikonu pomocí streamu s Aspose.Words for .NET v tomto podrobném, podrobném tutoriálu.
weight: 10
url: /cs/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon-using-stream/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit OLE objekt jako ikonu pomocí proudu

## Zavedení

tomto tutoriálu se ponoříme do super skvělé funkce Aspose.Words pro .NET: vložení objektu OLE (Object Linking and Embedding) jako ikony pomocí streamu. Ať už vkládáte powerpointovou prezentaci, excelovou tabulku nebo jakýkoli jiný typ souboru, tato příručka vám přesně ukáže, jak na to. Jste připraveni začít? Jdeme na to!

## Předpoklady

Než se pustíme do kódu, budete potřebovat několik věcí:

-  Aspose.Words for .NET: Pokud jste to ještě neudělali,[stáhnout](https://releases.aspose.com/words/net/) a nainstalujte Aspose.Words for .NET.
- Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí C#.
- Vstupní soubory: Soubor, který chcete vložit (např. prezentace PowerPoint) a obrázek ikony.

## Importovat jmenné prostory

Chcete-li začít, ujistěte se, že jste do projektu importovali potřebné jmenné prostory:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Pojďme si proces rozebrat krok za krokem, aby bylo snadné jej sledovat.

## Krok 1: Vytvořte nový dokument

Nejprve vytvoříme nový dokument a tvůrce dokumentů pro práci s ním.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Myslete na to`Document` jako vaše prázdné plátno a`DocumentBuilder` jako váš štětec. Nastavujeme naše nástroje, abychom mohli začít vytvářet naše mistrovské dílo.

## Krok 2: Připravte stream

Dále musíme připravit paměťový stream, který obsahuje soubor, který chceme vložit. V tomto příkladu vložíme prezentaci v PowerPointu.

```csharp
using (MemoryStream stream = new MemoryStream(File.ReadAllBytes("Path_to_your_directory/Presentation.pptx")))
{
```

Tento krok je jako nakládání barvy na štětec. Připravujeme náš soubor k vložení.

## Krok 3: Vložte objekt OLE jako ikonu

Nyní použijeme tvůrce dokumentů k vložení objektu OLE do dokumentu. Zadáme datový proud souboru, ProgID pro typ souboru (v tomto případě "Balík"), cestu k obrázku ikony a štítek pro vložený soubor.

```csharp
builder.InsertOleObjectAsIcon(stream, "Package", "Path_to_your_directory/Logo icon.ico", "My embedded file");
}
```

Tady se děje kouzlo! Vkládáme náš soubor a zobrazujeme jej jako ikonu v dokumentu.

## Krok 4: Uložte dokument

Nakonec dokument uložíme na zadanou cestu.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIconUsingStream.docx");
```

Tento krok je jako vložení hotového obrazu do rámu a jeho zavěšení na zeď. Váš dokument je nyní připraven k použití!

## Závěr

tady to máte! Úspěšně jste vložili objekt OLE jako ikonu do dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná funkce vám může pomoci snadno vytvářet dynamické a interaktivní dokumenty. Ať už vkládáte prezentace, tabulky nebo jiné soubory, s Aspose.Words to bude hračka. Takže jděte do toho, vyzkoušejte to a uvidíte rozdíl, který to může udělat ve vašich dokumentech!

## FAQ

### Mohu pomocí této metody vložit různé typy souborů?
Ano, můžete vložit jakýkoli typ souboru podporovaný OLE, včetně Wordu, Excelu, PowerPointu a dalších.

### Potřebuji k používání Aspose.Words pro .NET speciální licenci?
 Ano, Aspose.Words for .NET vyžaduje licenci. Můžete získat a[zkušební verze zdarma](https://releases.aspose.com/) nebo koupit a[dočasná licence](https://purchase.aspose.com/temporary-license/) pro testování.

### Mohu upravit ikonu použitou pro objekt OLE?
 Absolutně! Pro ikonu můžete použít libovolný soubor obrázku zadáním její cesty v`InsertOleObjectAsIcon` metoda.

### Co se stane, pokud jsou cesty k souboru nebo ikoně nesprávné?
Metoda vyvolá výjimku. Ujistěte se, že cesty k souborům jsou správné, abyste předešli chybám.

### Je možné propojit vložený objekt místo jeho vložení?
Ano, Aspose.Words umožňuje vkládat propojené objekty OLE, které odkazují na soubor, aniž by vkládaly jeho obsah.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
