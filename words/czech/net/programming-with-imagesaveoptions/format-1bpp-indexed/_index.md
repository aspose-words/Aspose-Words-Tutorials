---
"description": "Naučte se, jak převést dokument Wordu na obrázek indexovaný s rozlišením 1Bpp pomocí Aspose.Words pro .NET. Pro snadnou konverzi postupujte podle našeho podrobného návodu."
"linktitle": "Formát 1Bpp Indexed"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Formát 1Bpp Indexed"
"url": "/cs/net/programming-with-imagesaveoptions/format-1bpp-indexed/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formát 1Bpp Indexed

## Zavedení

Přemýšleli jste někdy, jak uložit dokument Wordu jako černobílý obrázek pomocí jen několika řádků kódu? Máte štěstí! Dnes se ponoříme do šikovného malého triku s Aspose.Words pro .NET, který vám umožní převést dokumenty do obrázků indexovaných 1Bpp. Tento formát je ideální pro určité typy digitální archivace, tisku nebo když potřebujete ušetřit místo. Rozebereme si každý krok, aby to bylo co nejjednodušší. Jste připraveni začít? Pojďme se do toho pustit!

## Předpoklady

Než se do toho pustíme, je potřeba mít připraveno několik věcí:

- Aspose.Words pro .NET: Ujistěte se, že máte knihovnu nainstalovanou. Můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí .NET: Visual Studio je dobrou volbou, ale můžete použít jakékoli prostředí, se kterým se cítíte dobře.
- Základní znalost C#: Nebojte se, budeme to zjednodušovat, ale trocha znalosti C# vám pomůže.
- Dokument Word: Mějte připravený ukázkový dokument Word k převodu.

## Importovat jmenné prostory

Nejdříve musíme importovat potřebné jmenné prostory. To je klíčové, protože nám to umožní přístup k potřebným třídám a metodám z Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavení adresáře dokumentů

Budete muset zadat cestu k adresáři s dokumenty. Zde je uložen váš dokument aplikace Word a kam bude uložen převedený obrázek.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Načtěte dokument Wordu

Nyní si načtěme dokument Wordu do Aspose.Words. `Document` objekt. Tento objekt představuje váš soubor aplikace Word a umožňuje s ním manipulovat.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Konfigurace možností ukládání obrázků

Dále musíme nastavit `ImageSaveOptions`A tady se děje ta magie. Nakonfigurujeme to tak, aby se obrázek ukládal ve formátu PNG s indexovaným barevným režimem 1Bpp.

```csharp
ImageSaveOptions saveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(1),
    ImageColorMode = ImageColorMode.BlackAndWhite,
    PixelFormat = ImagePixelFormat.Format1bppIndexed
};
```

- SaveFormat.Png: Toto určuje, že chceme dokument uložit jako obrázek PNG.
- PageSet(1): To znamená, že převádíme pouze první stránku.
- ImageColorMode.BlackAndWhite: Toto nastaví obrázek na černobílý.
- ImagePixelFormat.Format1bppIndexed: Toto nastaví formát obrázku na indexovaný 1Bpp.

## Krok 4: Uložte dokument jako obrázek

Nakonec dokument uložíme jako obrázek pomocí `Save` metoda `Document` objekt.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Závěr

A máte to! Pomocí Aspose.Words pro .NET jste pomocí několika řádků kódu transformovali svůj dokument Word na obrázek indexovaný s rozlišením 1Bpp. Tato metoda je neuvěřitelně užitečná pro vytváření vysoce kontrastních a prostorově efektivních obrázků z vašich dokumentů. Nyní ji můžete snadno integrovat do svých projektů a pracovních postupů. Přeji vám příjemné programování!

## Často kladené otázky

### Co je to 1Bpp indexovaný obrázek?
Obrázek indexovaný 1Bpp (1 bit na pixel) je černobílý obrazový formát, kde každý pixel je reprezentován jedním bitem, buď 0, nebo 1. Tento formát je velmi prostorově efektivní.

### Mohu převést více stránek dokumentu Word najednou?
Ano, můžete. Upravit `PageSet` nemovitost v `ImageSaveOptions` zahrnout více stránek nebo celý dokument.

### Potřebuji licenci k používání Aspose.Words pro .NET?
Ano, Aspose.Words pro .NET vyžaduje pro plnou funkčnost licenci. Můžete si pořídit [dočasná licence zde](https://purchase.aspose.com/temporary-license/).

### Do jakých dalších formátů obrázků mohu převést dokument Word?
Aspose.Words podporuje různé obrazové formáty včetně JPEG, BMP a TIFF. Jednoduše změňte `SaveFormat` v `ImageSaveOptions`.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
Podrobnou dokumentaci naleznete na [Dokumentace k Aspose.Words pro .NET](https://reference.aspose.com/words/net/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}