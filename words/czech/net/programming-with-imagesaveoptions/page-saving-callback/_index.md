---
title: Zpětné volání pro ukládání stránky
linktitle: Zpětné volání pro ukládání stránky
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se uložit každou stránku dokumentu aplikace Word jako samostatný obrázek PNG pomocí Aspose.Words for .NET s naším podrobným průvodcem krok za krokem.
weight: 10
url: /cs/net/programming-with-imagesaveoptions/page-saving-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zpětné volání pro ukládání stránky

## Zavedení

Ahoj! Cítili jste někdy potřebu uložit každou stránku dokumentu aplikace Word jako samostatné obrázky? Možná chcete rozdělit velkou sestavu do snadno stravitelných vizuálů nebo možná potřebujete vytvořit miniatury pro náhled. Ať už je váš důvod jakýkoli, pomocí Aspose.Words pro .NET je tento úkol hračkou. V této příručce vás provedeme procesem nastavení zpětného volání pro uložení stránky, aby se každá stránka dokumentu uložila jako samostatný obrázek PNG. Pojďme se rovnou ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words for .NET: Pokud jste to ještě neudělali, stáhněte si a nainstalujte jej z[zde](https://releases.aspose.com/words/net/).
2. Visual Studio: Jakákoli verze by měla fungovat, ale pro tuto příručku budu používat Visual Studio 2019.
3. Základní znalost C#: Abyste mohli pokračovat, budete potřebovat základní znalosti C#.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. To nám pomáhá přistupovat k požadovaným třídám a metodám, aniž bychom pokaždé museli zadávat celý jmenný prostor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavte adresář dokumentů

Dobře, začněme definováním cesty k adresáři s dokumenty. Zde je umístěn váš vstupní dokument aplikace Word a kde budou uloženy výstupní obrázky.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vložte svůj dokument

Dále načteme dokument, který chcete zpracovat. Ujistěte se, že váš dokument ("Rendering.docx") je v zadaném adresáři.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Nakonfigurujte možnosti uložení obrázku

Musíme nakonfigurovat možnosti ukládání obrázků. V tomto případě ukládáme stránky jako soubory PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

 Zde,`PageSet` určuje rozsah stránek k uložení a`PageSavingCallback` ukazuje na naši vlastní třídu zpětného volání.

## Krok 4: Implementujte zpětné volání pro ukládání stránky

Nyní implementujme třídu zpětného volání, která se stará o to, jak se každá stránka ukládá.

```csharp
private class HandlePageSavingCallback : IPageSavingCallback
{
    public void PageSaving(PageSavingArgs args)
    {
        args.PageFileName = string.Format(dataDir + "Page_{0}.png", args.PageIndex);
    }
}
```

 Tato třída implementuje`IPageSavingCallback` rozhraní a v rámci`PageSaving` definujeme vzor pojmenování pro každou uloženou stránku.

## Krok 5: Uložte dokument jako obrázky

Nakonec dokument uložíme pomocí nakonfigurovaných možností.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Závěr

A tady to máte! Úspěšně jste pomocí Aspose.Words for .NET nastavili zpětné volání pro uložení stránky pro uložení každé stránky dokumentu aplikace Word jako samostatný obrázek PNG. Tato technika je neuvěřitelně užitečná pro různé aplikace, od vytváření náhledů stránek až po generování jednotlivých obrázků stránek pro zprávy. 

Šťastné kódování!

## FAQ

### Mohu ukládat stránky v jiných formátech než PNG?  
 Ano, můžete ukládat stránky v různých formátech, jako jsou JPEG, BMP a TIFF, změnou`SaveFormat` v`ImageSaveOptions`.

### Co když chci uložit pouze konkrétní stránky?  
 Můžete určit stránky, které chcete uložit úpravou`PageSet` parametr v`ImageSaveOptions`.

### Je možné upravit kvalitu obrazu?  
 Absolutně! Můžete nastavit vlastnosti jako`ImageSaveOptions.JpegQuality` pro kontrolu kvality výstupních obrázků.

### Jak mohu efektivně zpracovávat velké dokumenty?  
U velkých dokumentů zvažte zpracování stránek v dávkách, abyste efektivně řídili využití paměti.

### Kde najdu další informace o Aspose.Words pro .NET?  
 Podívejte se na[dokumentace](https://reference.aspose.com/words/net/) pro komplexní návody a příklady.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
