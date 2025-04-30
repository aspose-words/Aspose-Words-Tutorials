---
"description": "Naučte se, jak spravovat substituci písem bez přípon v Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu, abyste zajistili, že vaše dokumenty budou pokaždé vypadat perfektně."
"linktitle": "Získat substituci bez přípon"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Získat substituci bez přípon"
"url": "/cs/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Získat substituci bez přípon

## Zavedení

Vítejte v tomto komplexním průvodci správou nahrazování písem pomocí Aspose.Words pro .NET. Pokud jste se někdy potýkali s tím, že se písma ve vašich dokumentech nezobrazovala správně, jste na správném místě. Tento tutoriál vás krok za krokem provede procesem efektivního nahrazování písem bez přípon.

## Předpoklady

Než se pustíte do tutoriálu, ujistěte se, že máte následující:

- Základní znalost C#: Pochopení programování v C# usnadní sledování a implementaci jednotlivých kroků.
- Knihovna Aspose.Words pro .NET: Stáhněte a nainstalujte knihovnu z [odkaz ke stažení](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Nastavte si vývojové prostředí, jako je Visual Studio, pro psaní a spouštění kódu.
- Vzorový dokument: Vzorový dokument (např. `Rendering.docx`) s nimiž budete v tomto tutoriálu pracovat.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory pro přístup ke třídám a metodám poskytovaným Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Krok 1: Definování adresáře dokumentů

Pro začátek určete adresář, kde se váš dokument nachází. To vám pomůže najít dokument, se kterým chcete pracovat.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Nastavení obslužné rutiny varování před substitucí

Dále musíme nastavit obslužnou rutinu varování, která nás upozorní vždy, když během zpracování dokumentu dojde k záměně písma. To je klíčové pro zachycení a řešení jakýchkoli problémů s písmy.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Krok 3: Přidání vlastních zdrojů písem

V tomto kroku přidáme vlastní zdroje písem, abychom zajistili, že Aspose.Words dokáže najít a použít správná písma. To je obzvláště užitečné, pokud máte specifická písma uložená ve vlastních adresářích.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

V tomto kódu:
- Načteme aktuální zdroje písem a přidáme nové `FolderFontSource` odkazující na náš vlastní adresář písem (`C:\\MyFonts\\`).
- Zdroje písem pak aktualizujeme tímto novým seznamem.

## Krok 4: Uložte dokument

Nakonec dokument po použití nastavení nahrazení písem uložte. V tomto tutoriálu jej uložíme jako PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Krok 5: Vytvoření třídy obslužné rutiny varování

Pro efektivní zpracování varování vytvořte vlastní třídu, která implementuje `IWarningCallback` rozhraní. Tato třída zachytí a zaznamená veškerá varování týkající se nahrazení fontů.

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
- Ten/Ta/To `Warning` Metoda zachycuje varování související se substitucí fontů.
- Ten/Ta/To `FontWarnings` Kolekce ukládá tato varování pro další kontrolu nebo protokolování.

## Závěr

Nyní jste zvládli proces nahrazování písem bez přípon pomocí Aspose.Words pro .NET. Tato znalost zajistí, že si vaše dokumenty zachovají zamýšlený vzhled bez ohledu na písma dostupná v systému. Neustále experimentujte s různými nastaveními a zdroji, abyste plně využili potenciál Aspose.Words.

## Často kladené otázky

### Jak mohu použít fonty z více vlastních adresářů?

Můžete přidat více `FolderFontSource` případy k `fontSources` vypsat a odpovídajícím způsobem aktualizovat zdroje písem.

### Kde si mohu stáhnout bezplatnou zkušební verzi Aspose.Words pro .NET?

Zkušební verzi zdarma si můžete stáhnout z [Zkušební stránka Aspose zdarma](https://releases.aspose.com/).

### Mohu zpracovat více typů varování pomocí `IWarningCallback`?

Ano, `IWarningCallback` Rozhraní umožňuje zpracovávat různé typy varování, nejen nahrazování fontů.

### Kde mohu získat podporu pro Aspose.Words?

Pro podporu navštivte [Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).

### Je možné si zakoupit dočasnou licenci?

Ano, můžete získat dočasnou licenci od [stránka s dočasnou licencí](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}