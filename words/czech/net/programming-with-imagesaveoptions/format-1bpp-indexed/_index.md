---
title: Formát 1Bpp Indexováno
linktitle: Formát 1Bpp Indexováno
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak převést dokument aplikace Word na indexovaný obrázek 1 Bpp pomocí Aspose.Words for .NET. Pro snadnou konverzi postupujte podle našeho podrobného průvodce.
weight: 10
url: /cs/net/programming-with-imagesaveoptions/format-1bpp-indexed/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formát 1Bpp Indexováno

## Zavedení

Přemýšleli jste někdy nad tím, jak uložit dokument aplikace Word jako černobílý obrázek s několika řádky kódu? Tak to máš štěstí! Dnes se ponoříme do úhledného malého triku pomocí Aspose.Words pro .NET, který vám umožní převést vaše dokumenty na 1Bpp indexované obrázky. Tento formát je ideální pro určité typy digitální archivace, tisku nebo když potřebujete ušetřit místo. Každý krok rozebereme, aby to bylo snadné jako facka. Jste připraveni začít? Pojďme se ponořit!

## Předpoklady

Než si ušpiníme ruce, je potřeba mít připraveno několik věcí:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu. Můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí .NET: Visual Studio je dobrá volba, ale můžete použít jakékoli prostředí, které vám vyhovuje.
- Základní znalost C#: Nebojte se, budeme to dělat jednoduše, ale trocha znalosti C# pomůže.
- Dokument aplikace Word: Připravte si ukázkový dokument aplikace Word ke konverzi.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. To je zásadní, protože nám to umožňuje přístup ke třídám a metodám, které potřebujeme z Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavte adresář dokumentů

Budete muset zadat cestu k adresáři dokumentů. Zde je uložen váš dokument aplikace Word a kam se uloží převedený obrázek.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Načtěte dokument aplikace Word

 Nyní načteme dokument aplikace Word do souboru Aspose.Words`Document` objekt. Tento objekt představuje váš soubor aplikace Word a umožňuje vám s ním manipulovat.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Nakonfigurujte možnosti uložení obrázku

 Dále musíme nastavit`ImageSaveOptions`Tady se děje kouzlo. Nakonfigurujeme jej tak, aby ukládal obrázek ve formátu PNG s indexovaným barevným režimem 1Bpp.

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

 Nakonec dokument uložíme jako obrázek pomocí`Save` metoda`Document` objekt.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
```

## Závěr

A tady to máte! Pomocí několika řádků kódu jste pomocí Aspose.Words for .NET transformovali svůj dokument aplikace Word na indexovaný obrázek o velikosti 1 Bpp. Tato metoda je neuvěřitelně užitečná pro vytváření vysoce kontrastních a prostorově úsporných obrázků z vašich dokumentů. Nyní to můžete snadno integrovat do svých projektů a pracovních postupů. Šťastné kódování!

## FAQ

### Co je 1Bpp indexovaný obrázek?
Indexovaný obrázek 1Bpp (1 bit na pixel) je formát černobílého obrázku, kde je každý pixel reprezentován jedním bitem, buď 0, nebo 1. Tento formát je vysoce prostorově nenáročný.

### Mohu převést více stránek dokumentu aplikace Word najednou?
 Ano, můžete. Upravte`PageSet` nemovitost v`ImageSaveOptions` zahrnout více stránek nebo celý dokument.

### Potřebuji licenci k používání Aspose.Words pro .NET?
 Ano, Aspose.Words for .NET vyžaduje licenci pro plnou funkčnost. Můžete získat a[dočasná licence zde](https://purchase.aspose.com/temporary-license/).

### Na jaké další formáty obrázků mohu převést svůj dokument Word?
 Aspose.Words podporuje různé formáty obrázků včetně JPEG, BMP a TIFF. Jednoduše změňte`SaveFormat` v`ImageSaveOptions`.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
 Podrobnou dokumentaci najdete na[Stránka dokumentace Aspose.Words for .NET](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
