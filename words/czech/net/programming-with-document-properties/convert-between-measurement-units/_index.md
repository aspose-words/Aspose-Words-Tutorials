---
title: Převod mezi měrnými jednotkami
linktitle: Převod mezi měrnými jednotkami
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se převádět měrné jednotky v Aspose.Words pro .NET. Postupujte podle našeho podrobného průvodce a nastavte okraje, záhlaví a zápatí dokumentu v palcích a bodech.
weight: 10
url: /cs/net/programming-with-document-properties/convert-between-measurement-units/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Převod mezi měrnými jednotkami

## Zavedení

Ahoj! Jste vývojář pracující s dokumenty Word pomocí Aspose.Words for .NET? Pokud ano, může se stát, že budete často potřebovat nastavit okraje, záhlaví nebo zápatí v různých měrných jednotkách. Převod mezi jednotkami, jako jsou palce a body, může být složitý, pokud nejste obeznámeni s funkcemi knihovny. V tomto komplexním tutoriálu vás provedeme procesem převodu mezi měrnými jednotkami pomocí Aspose.Words for .NET. Pojďme se ponořit a zjednodušit tyto převody!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words for .NET Library: Pokud jste tak ještě neučinili, stáhněte si ji[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
3. Základní znalost C#: Pochopení základů C# vám pomůže snadno pokračovat.
4.  Aspose License: Volitelné, ale doporučené pro plnou funkčnost. Můžete získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory. To je zásadní pro přístup ke třídám a metodám poskytovaným Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Layout;
```

Pojďme si rozebrat proces převodu měrných jednotek v Aspose.Words pro .NET. Chcete-li nastavit a přizpůsobit okraje a vzdálenosti dokumentu, postupujte podle těchto podrobných kroků.

## Krok 1: Vytvořte nový dokument

Nejprve musíte vytvořit nový dokument pomocí Aspose.Words.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Tím se inicializuje nový dokument aplikace Word a a`DocumentBuilder` pro usnadnění tvorby a formátování obsahu.

## Krok 2: Přístup k nastavení stránky

 Chcete-li nastavit okraje, záhlaví a zápatí, musíte mít přístup k`PageSetup` objekt.

```csharp
PageSetup pageSetup = builder.PageSetup;
```

To vám umožní přístup k různým vlastnostem nastavení stránky, jako jsou okraje, vzdálenost záhlaví a vzdálenost zápatí.

## Krok 3: Převeďte palce na body

 Aspose.Words ve výchozím nastavení používá jako měrnou jednotku body. Chcete-li nastavit okraje v palcích, budete muset palce převést na body pomocí`ConvertUtil.InchToPoint` metoda.

```csharp
pageSetup.TopMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.BottomMargin = ConvertUtil.InchToPoint(1.0);
pageSetup.LeftMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.RightMargin = ConvertUtil.InchToPoint(1.5);
pageSetup.HeaderDistance = ConvertUtil.InchToPoint(0.2);
pageSetup.FooterDistance = ConvertUtil.InchToPoint(0.2);
```

Zde je rozpis toho, co každý řádek dělá:
- Nastaví horní a dolní okraj na 1 palec (převedeno na body).
- Nastaví levý a pravý okraj na 1,5 palce (převedeno na body).
- Nastaví vzdálenosti záhlaví a zápatí na 0,2 palce (převedeno na body).

## Krok 4: Uložte dokument

Nakonec dokument uložte, abyste zajistili použití všech změn.

```csharp
doc.Save("ConvertedDocument.docx");
```

Tím se dokument uloží se zadanými okraji a vzdálenostmi v bodech.

## Závěr

A tady to máte! Úspěšně jste převedli a nastavili okraje a vzdálenosti v dokumentu aplikace Word pomocí Aspose.Words for .NET. Podle těchto kroků můžete snadno zvládnout různé převody jednotek, takže proces přizpůsobení dokumentu bude hračkou. Pokračujte v experimentování s různými nastaveními a prozkoumejte rozsáhlé funkce, které Aspose.Words nabízí. Šťastné kódování!

## FAQ

### Mohu pomocí Aspose.Words převést jiné jednotky, jako jsou centimetry, na body?
 Ano, Aspose.Words poskytuje metody jako`ConvertUtil.CmToPoint` pro převod centimetrů na body.

### Je pro použití Aspose.Words pro .NET nutná licence?
I když můžete Aspose.Words používat bez licence, některé pokročilé funkce mohou být omezeny. Získání licence zajišťuje plnou funkčnost.

### Jak nainstaluji Aspose.Words for .NET?
 Můžete si jej stáhnout z[webové stránky](https://releases.aspose.com/words/net/) a postupujte podle pokynů k instalaci.

### Mohu nastavit různé jednotky pro různé části dokumentu?
 Ano, můžete upravit okraje a další nastavení pro různé sekce pomocí`Section` třída.

### Jaké další funkce Aspose.Words nabízí?
 Aspose.Words podporuje širokou škálu funkcí včetně převodu dokumentů, hromadné korespondence a rozsáhlých možností formátování. Zkontrolujte[dokumentace](https://reference.aspose.com/words/net/) pro více podrobností.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
