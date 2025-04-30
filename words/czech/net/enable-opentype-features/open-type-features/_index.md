---
"description": "Naučte se, jak povolit funkce OpenType v dokumentech Wordu pomocí Aspose.Words pro .NET v tomto podrobném návodu krok za krokem."
"linktitle": "Funkce otevřeného typu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Funkce otevřeného typu"
"url": "/cs/net/enable-opentype-features/open-type-features/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Funkce otevřeného typu

## Zavedení

Jste připraveni ponořit se do světa funkcí OpenType pomocí Aspose.Words pro .NET? Připoutejte se, protože se chystáme vydat na poutavou cestu, která nejen vylepší vaše dokumenty Word, ale také z vás udělá experta na Aspose.Words. Pojďme na to!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
2. .NET Framework: Ujistěte se, že máte nainstalovanou kompatibilní verzi .NET Frameworku.
3. Visual Studio: Integrované vývojové prostředí (IDE) pro kódování.
4. Základní znalost C#: Tento tutoriál předpokládá, že máte základní znalosti programování v C#.

## Importovat jmenné prostory

Nejdříve budete muset importovat potřebné jmenné prostory pro přístup k funkcím poskytovaným Aspose.Words pro .NET. Zde je návod, jak to udělat:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Shaping.HarfBuzz;
```

Nyní si příklad rozdělme do několika kroků ve formátu podrobného návodu.

## Krok 1: Nastavení projektu

### Vytvoření nového projektu

Otevřete Visual Studio a vytvořte nový projekt v C#. Pojmenujte ho nějak smysluplně, například „OpenTypeFeaturesDemo“. Toto bude naše hřiště pro experimentování s funkcemi OpenType.

### Přidání referenčního materiálu Aspose.Words

Abyste mohli používat Aspose.Words, musíte jej přidat do svého projektu. Můžete to provést pomocí Správce balíčků NuGet:

1. Klikněte pravým tlačítkem myši na projekt v Průzkumníku řešení.
2. Vyberte možnost „Spravovat balíčky NuGet“.
3. Vyhledejte „Aspose.Words“ a nainstalujte jej.

## Krok 2: Vložte dokument

### Určení adresáře dokumentů

Vytvořte řetězcovou proměnnou, která bude obsahovat cestu k adresáři s dokumenty. Zde je uložen váš dokument Wordu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde se váš dokument nachází.

### Načítání dokumentu

Nyní načtěte dokument pomocí Aspose.Words:

```csharp
Document doc = new Document(dataDir + "OpenType text shaping.docx");
```

Tento řádek kódu otevře zadaný dokument, abychom s ním mohli manipulovat.

## Krok 3: Povolte funkce OpenType

HarfBuzz je open-source engine pro tvarování textu, který bezproblémově spolupracuje s Aspose.Words. Abychom mohli povolit funkce OpenType, musíme nastavit `TextShaperFactory` majetek `LayoutOptions` objekt.

```csharp
doc.LayoutOptions.TextShaperFactory = HarfBuzzTextShaperFactory.Instance;
```

Tento úryvek kódu zajišťuje, že váš dokument používá HarfBuzz pro tvarování textu, což umožňuje pokročilé funkce OpenType.

## Krok 4: Uložte dokument

Nakonec uložte upravený dokument jako PDF, abyste si prohlédli výsledky své práce.

```csharp
doc.Save(dataDir + "WorkingWithHarfBuzz.OpenTypeFeatures.pdf");
```

Tento řádek kódu uloží dokument ve formátu PDF a zahrne do něj funkce OpenType, které umožňuje HarfBuzz.

## Závěr

A tady to máte! Úspěšně jste povolili funkce OpenType ve svém dokumentu Word pomocí Aspose.Words pro .NET. Dodržováním těchto kroků můžete odemknout pokročilé typografické možnosti a zajistit, aby vaše dokumenty vypadaly profesionálně a elegantně.

Ale nekončete tím! Prozkoumejte další funkce Aspose.Words a zjistěte, jak můžete své dokumenty dále vylepšit. Pamatujte, že praxe dělá mistra, takže experimentujte a učte se.

## Často kladené otázky

### Jaké jsou funkce OpenType?
Mezi funkce OpenType patří pokročilé typografické možnosti, jako jsou ligatury, kerning a stylistické sady, které vylepšují vzhled textu v dokumentech.

### Proč používat HarfBuzz s Aspose.Words?
HarfBuzz je open-source nástroj pro tvarování textu, který poskytuje robustní podporu pro funkce OpenType a zlepšuje typografickou kvalitu vašich dokumentů.

### Mohu s Aspose.Words používat jiné nástroje pro tvarování textu?
Ano, Aspose.Words podporuje různé nástroje pro tvarování textu. HarfBuzz je však velmi doporučován kvůli jeho komplexní podpoře funkcí OpenType.

### Je Aspose.Words kompatibilní se všemi verzemi .NET?
Aspose.Words podporuje různé verze .NET, včetně .NET Framework, .NET Core a .NET Standard. Zkontrolujte [dokumentace](https://reference.aspose.com/words/net/) pro podrobné informace o kompatibilitě.

### Jak si mohu vyzkoušet Aspose.Words před zakoupením?
Zkušební verzi zdarma si můžete stáhnout z [Webové stránky Aspose](https://releases.aspose.com/) a požádat o dočasnou licenci [zde](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}