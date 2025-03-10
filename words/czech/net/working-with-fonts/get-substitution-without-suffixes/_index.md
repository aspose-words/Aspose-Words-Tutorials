---
title: Získejte substituci bez přípon
linktitle: Získejte substituci bez přípon
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se spravovat nahrazování písem bez přípon v Aspose.Words pro .NET. Postupujte podle našeho podrobného průvodce, abyste zajistili, že vaše dokumenty budou vždy vypadat dokonale.
weight: 10
url: /cs/net/working-with-fonts/get-substitution-without-suffixes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Získejte substituci bez přípon

## Zavedení

Vítejte v této komplexní příručce o správě nahrazování písem pomocí Aspose.Words pro .NET. Pokud jste se někdy potýkali s tím, že se písma ve vašich dokumentech nezobrazují správně, jste na správném místě. Tento výukový program vás krok za krokem provede procesem efektivního nahrazování písem bez přípon.

## Předpoklady

Než se pustíte do výukového programu, ujistěte se, že máte následující:

- Základní znalost C#: Pochopení programování v C# vám usnadní sledování a implementaci kroků.
-  Aspose.Words for .NET Library: Stáhněte a nainstalujte knihovnu z[odkaz ke stažení](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Nastavte vývojové prostředí, jako je Visual Studio, abyste mohli psát a spouštět svůj kód.
-  Vzorový dokument: Vzorový dokument (např.`Rendering.docx`), se kterými budete pracovat během tohoto tutoriálu.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory pro přístup ke třídám a metodám poskytovaným Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Krok 1: Definujte adresář dokumentů

Chcete-li začít, zadejte adresář, ve kterém je umístěn váš dokument. Pomůže vám to najít dokument, na kterém chcete pracovat.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Nastavte obslužný program varování při nahrazení

Dále musíme nastavit obsluhu varování, která nás upozorní, kdykoli dojde během zpracování dokumentu k záměně písem. To je zásadní pro zachycení a řešení jakýchkoli problémů s písmem.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Krok 3: Přidejte vlastní zdroje písem

V tomto kroku přidáme vlastní zdroje písem, abychom zajistili, že Aspose.Words dokáže najít a použít správná písma. To je zvláště užitečné, pokud máte konkrétní fonty uloženy ve vlastních adresářích.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

V tomto kódu:
-  Načteme aktuální zdroje písem a přidáme nové`FolderFontSource` ukazující na náš vlastní adresář písem (`C:\\MyFonts\\`).
- Poté aktualizujeme zdroje písem tímto novým seznamem.

## Krok 4: Uložte dokument

Nakonec uložte dokument po použití nastavení náhrady písem. Pro tento tutoriál jej uložíme jako PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Krok 5: Vytvořte třídu Warning Handler

 Chcete-li efektivně zpracovávat varování, vytvořte vlastní třídu, která implementuje`IWarningCallback` rozhraní. Tato třída zachytí a zaprotokoluje všechna varování o záměně písem.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

V této třídě:
-  The`Warning`metoda zachycuje varování související se záměnou písem.
-  The`FontWarnings` kolekce ukládá tato varování pro další kontrolu nebo protokolování.

## Závěr

Nyní jste zvládli proces nahrazování písem bez přípon pomocí Aspose.Words for .NET. Tyto znalosti zajistí, že si vaše dokumenty zachovají svůj zamýšlený vzhled bez ohledu na písma dostupná v systému. Pokračujte v experimentování s různými nastaveními a zdroji, abyste plně využili sílu Aspose.Words.

## FAQ

### Jak mohu používat písma z více vlastních adresářů?

 Můžete přidat více`FolderFontSource` instance k`fontSources` seznam a odpovídajícím způsobem aktualizujte zdroje písem.

### Kde si mohu stáhnout bezplatnou zkušební verzi Aspose.Words pro .NET?

 Můžete si stáhnout bezplatnou zkušební verzi z[Aspose zkušební stránku zdarma](https://releases.aspose.com/).

###  Mohu zpracovat více typů varování pomocí`IWarningCallback`?

 Ano,`IWarningCallback` rozhraní vám umožňuje zpracovávat různé typy varování, nejenom nahrazování písem.

### Kde mohu získat podporu pro Aspose.Words?

 Pro podporu navštivte[Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).

### Je možné zakoupit dočasnou licenci?

 Ano, můžete získat dočasnou licenci od[dočasná licenční stránka](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
