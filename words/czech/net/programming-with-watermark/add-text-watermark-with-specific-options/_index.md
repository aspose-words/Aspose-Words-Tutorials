---
"description": "Naučte se, jak přidat textový vodoznak se specifickými možnostmi do dokumentů Word pomocí Aspose.Words pro .NET. Snadno si upravte písmo, velikost, barvu a rozvržení."
"linktitle": "Přidat textový vodoznak se specifickými možnostmi"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidat textový vodoznak se specifickými možnostmi"
"url": "/cs/net/programming-with-watermark/add-text-watermark-with-specific-options/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidat textový vodoznak se specifickými možnostmi

## Zavedení

Vodoznaky mohou být stylovým a funkčním doplňkem vašich dokumentů Word a mohou sloužit k různým účelům, od označení dokumentů jako důvěrných až po přidání personalizovaného nádechu. V tomto tutoriálu se podíváme na to, jak přidat textový vodoznak do dokumentu Word pomocí Aspose.Words pro .NET. Ponoříme se do konkrétních možností, které můžete konfigurovat, jako je rodina písma, velikost písma, barva a rozvržení. Nakonec budete moci vodoznak dokumentu přizpůsobit přesně podle svých potřeb. Takže si vezměte editor kódu a pojďme na to!

## Předpoklady

Než se pustíme do práce, ujistěte se, že máte připraveno následující:

1. Knihovna Aspose.Words pro .NET: Budete potřebovat nainstalovanou knihovnu Aspose.Words. Pokud jste tak ještě neučinili, můžete si ji stáhnout z [Odkaz ke stažení Aspose.Words](https://releases.aspose.com/words/net/).
2. Základní znalost jazyka C#: Tento tutoriál bude používat C# jako programovací jazyk. Základní znalost syntaxe jazyka C# bude užitečná.
3. Vývojové prostředí .NET: Ujistěte se, že máte nastavené vývojové prostředí (například Visual Studio), kde můžete vytvářet a spouštět aplikace .NET.

## Importovat jmenné prostory

Pro práci s Aspose.Words budete muset do projektu zahrnout potřebné jmenné prostory. Zde je to, co je potřeba importovat:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Krok 1: Nastavení dokumentu

Nejprve je třeba načíst dokument, se kterým chcete pracovat. V tomto tutoriálu použijeme vzorový dokument s názvem `Document.docx`Ujistěte se, že tento dokument existuje ve vámi zadaném adresáři.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

V tomto kroku definujete adresář, kde se nachází váš dokument, a načtete ho do instance `Document` třída.

## Krok 2: Konfigurace možností vodoznaku

Dále nakonfigurujte možnosti pro textový vodoznak. Můžete si přizpůsobit různé aspekty, jako je rodina písma, velikost písma, barva a rozvržení. Pojďme si tyto možnosti nastavit.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Zde je to, co každá možnost dělá:
- `FontFamily`: Určuje písmo textu vodoznaku.
- `FontSize`Nastavuje velikost textu vodoznaku.
- `Color`: Definuje barvu textu vodoznaku.
- `Layout`Určuje orientaci vodoznaku (horizontální nebo diagonální).
- `IsSemitrasparent`: Nastavuje, zda je vodoznak poloprůhledný.

## Krok 3: Přidání textu vodoznaku

Nyní použijte vodoznak na dokument pomocí dříve nakonfigurovaných možností. V tomto kroku nastavíte text vodoznaku na „Test“ a použijete vámi definované možnosti.

```csharp
doc.Watermark.SetText("Test", options);
```

Tento řádek kódu přidá do dokumentu vodoznak s textem „Test“ s použitím zadaných možností.

## Krok 4: Uložte dokument

Nakonec uložte dokument s novým vodoznakem. Můžete jej uložit pod novým názvem, abyste zabránili přepsání původního dokumentu.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Tento úryvek kódu uloží upravený dokument do stejného adresáře s novým názvem souboru.

## Závěr

Přidání textového vodoznaku do dokumentů Word pomocí Aspose.Words pro .NET je jednoduchý proces, pokud si ho rozdělíte na snadno zvládnutelné kroky. Dodržováním tohoto tutoriálu jste se naučili, jak konfigurovat různé možnosti vodoznaku, včetně písma, velikosti, barvy, rozvržení a průhlednosti. S těmito dovednostmi si nyní můžete přizpůsobit dokumenty tak, aby lépe vyhovovaly vašim potřebám, nebo zahrnout důležité informace, jako je důvěrnost nebo branding.

Pokud máte jakékoli dotazy nebo potřebujete další pomoc, neváhejte se podívat na [Dokumentace k Aspose.Words](https://reference.aspose.com/words/net/) nebo navštivte [Fórum podpory Aspose](https://forum.aspose.com/c/words/8) pro další pomoc.

## Často kladené otázky

### Mohu pro vodoznak použít různá písma?

Ano, můžete si vybrat libovolné písmo nainstalované ve vašem systému zadáním `FontFamily` nemovitost v `TextWatermarkOptions`.

### Jak změním barvu vodoznaku?

Barvu vodoznaku můžete změnit nastavením `Color` nemovitost v `TextWatermarkOptions` k jakémukoli `System.Drawing.Color` hodnota.

### Je možné do dokumentu přidat více vodoznaků?

Aspose.Words podporuje přidávání vodoznaků po jednom. Chcete-li přidat více vodoznaků, je nutné je vytvořit a aplikovat postupně.

### Mohu upravit polohu vodoznaku?

Ten/Ta/To `WatermarkLayout` Vlastnost určuje orientaci, ale přesné úpravy umístění nejsou přímo podporovány. Pro přesné umístění může být nutné použít jiné techniky.

### Co když potřebuji poloprůhledný vodoznak?

Nastavte `IsSemitrasparent` majetek `true` aby byl váš vodoznak poloprůhledný.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}