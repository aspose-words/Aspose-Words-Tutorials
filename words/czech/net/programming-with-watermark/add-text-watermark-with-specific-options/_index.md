---
title: Přidat textový vodoznak se specifickými možnostmi
linktitle: Přidat textový vodoznak se specifickými možnostmi
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak přidat textový vodoznak se specifickými možnostmi do dokumentů aplikace Word pomocí Aspose.Words for .NET. Snadno si přizpůsobte písmo, velikost, barvu a rozvržení.
weight: 10
url: /cs/net/programming-with-watermark/add-text-watermark-with-specific-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidat textový vodoznak se specifickými možnostmi

## Zavedení

Vodoznaky mohou být stylovým a funkčním doplňkem vašich dokumentů aplikace Word, který slouží účelům od označení dokumentů jako důvěrných až po přidání personalizovaného doteku. V tomto tutoriálu prozkoumáme, jak přidat textový vodoznak do dokumentu aplikace Word pomocí Aspose.Words for .NET. Ponoříme se do konkrétních možností, které můžete nakonfigurovat, jako je rodina písem, velikost písma, barva a rozvržení. Na konci budete moci upravit vodoznak dokumentu tak, aby přesně odpovídal vašim potřebám. Takže popadněte editor kódu a můžeme začít!

## Předpoklady

Než začneme, ujistěte se, že máte na svém místě následující:

1.  Aspose.Words for .NET Library: Budete potřebovat nainstalovanou knihovnu Aspose.Words. Pokud jste tak ještě neučinili, můžete si jej stáhnout z[Odkaz ke stažení Aspose.Words](https://releases.aspose.com/words/net/).
2. Základní porozumění C#: Tento tutoriál bude používat C# jako programovací jazyk. Bude užitečné základní pochopení syntaxe C#.
3. Vývojové prostředí .NET: Ujistěte se, že máte nastavené vývojové prostředí (jako Visual Studio), kde můžete vytvářet a spouštět své aplikace .NET.

## Importovat jmenné prostory

Chcete-li pracovat s Aspose.Words, budete muset do projektu zahrnout potřebné jmenné prostory. Zde je to, co potřebujete k importu:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Krok 1: Nastavte svůj dokument

 Nejprve musíte načíst dokument, se kterým chcete pracovat. Pro tento tutoriál použijeme vzorový dokument s názvem`Document.docx`. Ujistěte se, že tento dokument existuje ve vašem zadaném adresáři.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 V tomto kroku definujete adresář, kde je umístěn váš dokument, a načtete jej do instance souboru`Document` třída.

## Krok 2: Nakonfigurujte možnosti vodoznaku

Dále nakonfigurujte možnosti pro textový vodoznak. Můžete přizpůsobit různé aspekty, jako je rodina písem, velikost písma, barva a rozvržení. Pojďme nastavit tyto možnosti.

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

Co každá možnost dělá:
- `FontFamily`: Určuje písmo textu vodoznaku.
- `FontSize`: Nastaví velikost textu vodoznaku.
- `Color`: Definuje barvu textu vodoznaku.
- `Layout`Určuje orientaci vodoznaku (horizontální nebo diagonální).
- `IsSemitrasparent`: Nastaví, zda je vodoznak poloprůhledný.

## Krok 3: Přidejte text vodoznaku

Nyní použijte vodoznak na dokument pomocí dříve nakonfigurovaných možností. V tomto kroku nastavíte text vodoznaku na "Test" a použijete vámi definované možnosti.

```csharp
doc.Watermark.SetText("Test", options);
```

Tento řádek kódu přidá do dokumentu vodoznak s textem "Test" s použitím zadaných možností.

## Krok 4: Uložte dokument

Nakonec uložte dokument s novým vodoznakem. Můžete jej uložit pod novým názvem, abyste předešli přepsání původního dokumentu.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Tento fragment kódu uloží upravený dokument do stejného adresáře s novým názvem souboru.

## Závěr

Přidání textového vodoznaku do dokumentů aplikace Word pomocí Aspose.Words for .NET je jednoduchý proces, když jej rozdělíte na zvládnutelné kroky. Podle tohoto kurzu jste se naučili, jak konfigurovat různé možnosti vodoznaku, včetně písma, velikosti, barvy, rozvržení a průhlednosti. S těmito dovednostmi nyní můžete upravit své dokumenty tak, aby lépe vyhovovaly vašim potřebám nebo aby obsahovaly základní informace, jako je důvěrnost nebo branding.

 Pokud máte nějaké dotazy nebo potřebujete další pomoc, neváhejte se podívat na[Dokumentace Aspose.Words](https://reference.aspose.com/words/net/) nebo navštivte[Aspose Support Forum](https://forum.aspose.com/c/words/8) pro další pomoc.

## FAQ

### Mohu pro vodoznak použít různá písma?

 Ano, můžete si vybrat libovolné písmo nainstalované ve vašem systému zadáním`FontFamily` nemovitost v`TextWatermarkOptions`.

### Jak změním barvu vodoznaku?

 Barvu vodoznaku můžete změnit nastavením`Color` nemovitost v`TextWatermarkOptions` na jakoukoli`System.Drawing.Color` hodnota.

### Je možné do dokumentu přidat více vodoznaků?

Aspose.Words podporuje přidávání jednoho vodoznaku najednou. Chcete-li přidat více vodoznaků, musíte je vytvořit a aplikovat postupně.

### Mohu upravit polohu vodoznaku?

 The`WatermarkLayout`vlastnost určuje orientaci, ale přesné úpravy umístění nejsou podporovány přímo. Možná budete muset použít jiné techniky pro přesné umístění.

### Co když potřebuji poloprůhledný vodoznak?

 Nastavte`IsSemitrasparent`majetek do`true` aby byl váš vodoznak poloprůhledný.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
