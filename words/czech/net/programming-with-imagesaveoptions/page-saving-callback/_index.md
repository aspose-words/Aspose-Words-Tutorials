---
"description": "Naučte se ukládat každou stránku dokumentu Word jako samostatný obrázek PNG pomocí Aspose.Words pro .NET s naším podrobným návodem krok za krokem."
"linktitle": "Zpětné volání pro uložení stránky"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zpětné volání pro uložení stránky"
"url": "/cs/net/programming-with-imagesaveoptions/page-saving-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zpětné volání pro uložení stránky

## Zavedení

Ahoj! Už jste někdy cítili potřebu uložit každou stránku dokumentu Word jako samostatný obrázek? Možná chcete rozdělit rozsáhlou zprávu na snadno stravitelné vizuály, nebo potřebujete vytvořit miniatury pro náhled. Ať už je váš důvod jakýkoli, použití Aspose.Words pro .NET tento úkol usnadní. V této příručce vás provedeme procesem nastavení zpětného volání pro ukládání stránky, které uloží každou stránku dokumentu jako samostatný obrázek PNG. Pojďme se na to rovnou pustit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si a nainstalujte si jej z [zde](https://releases.aspose.com/words/net/).
2. Visual Studio: Jakákoli verze by měla fungovat, ale v této příručce budu používat Visual Studio 2019.
3. Základní znalost C#: Pro pochopení budete potřebovat základní znalosti C#.

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory. To nám pomůže přistupovat k požadovaným třídám a metodám, aniž bychom museli pokaždé zadávat celý jmenný prostor.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Nastavení adresáře dokumentů

Dobře, začněme definováním cesty k adresáři s vašimi dokumenty. Zde se nachází váš vstupní dokument Wordu a kam se budou ukládat výstupní obrázky.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Vložte dokument

Dále načteme dokument, který chcete zpracovat. Ujistěte se, že se váš dokument („Rendering.docx“) nachází v zadaném adresáři.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Krok 3: Konfigurace možností ukládání obrázků

Musíme nakonfigurovat možnosti pro ukládání obrázků. V tomto případě ukládáme stránky jako soubory PNG.

```csharp
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    PageSet = new PageSet(new PageRange(0, doc.PageCount - 1)),
    PageSavingCallback = new HandlePageSavingCallback()
};
```

Zde, `PageSet` určuje rozsah stránek, které se mají uložit, a `PageSavingCallback` odkazuje na naši vlastní třídu zpětného volání.

## Krok 4: Implementace zpětného volání pro ukládání stránky

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

Tato třída implementuje `IPageSavingCallback` rozhraní a v rámci `PageSaving` metodou definujeme vzor pojmenování pro každou uloženou stránku.

## Krok 5: Uložte dokument jako obrázky

Nakonec dokument uložíme s použitím nakonfigurovaných možností.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
```

## Závěr

A tady to máte! Úspěšně jste nastavili zpětné volání pro ukládání stránky, které uloží každou stránku dokumentu Word jako samostatný obrázek PNG pomocí Aspose.Words pro .NET. Tato technika je neuvěřitelně užitečná pro různé aplikace, od vytváření náhledů stránek až po generování jednotlivých obrázků stránek pro sestavy. 

Šťastné kódování!

## Často kladené otázky

### Mohu ukládat stránky v jiných formátech než PNG?  
Ano, stránky můžete ukládat v různých formátech, jako je JPEG, BMP a TIFF, změnou `SaveFormat` v `ImageSaveOptions`.

### Co když chci uložit pouze určité stránky?  
Stránky, které chcete uložit, můžete určit úpravou `PageSet` parametr v `ImageSaveOptions`.

### Je možné si přizpůsobit kvalitu obrazu?  
Rozhodně! Můžete nastavit vlastnosti jako `ImageSaveOptions.JpegQuality` pro kontrolu kvality výstupních obrázků.

### Jak mohu efektivně zpracovávat velké dokumenty?  
U velkých dokumentů zvažte dávkové zpracování stránek, abyste efektivně spravovali využití paměti.

### Kde najdu více informací o Aspose.Words pro .NET?  
Podívejte se na [dokumentace](https://reference.aspose.com/words/net/) pro komplexní návody a příklady.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}