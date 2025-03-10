---
title: Získejte rozsah stránek Jpeg
linktitle: Získejte rozsah stránek Jpeg
second_title: Aspose.Words API pro zpracování dokumentů
description: Převeďte konkrétní stránky dokumentů aplikace Word do formátu JPEG s vlastním nastavením pomocí Aspose.Words for .NET. Naučte se krok za krokem nastavovat jas, kontrast a rozlišení.
weight: 10
url: /cs/net/programming-with-imagesaveoptions/get-jpeg-page-range/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Získejte rozsah stránek Jpeg

## Zavedení

Převod dokumentů aplikace Word na obrázky může být neuvěřitelně užitečný, ať už vytváříte miniatury, zobrazujete náhled dokumentů online nebo sdílíte obsah v přístupnějším formátu. S Aspose.Words for .NET můžete snadno převést konkrétní stránky dokumentů Word do formátu JPEG a zároveň upravit různá nastavení, jako je jas, kontrast a rozlišení. Pojďme se ponořit do toho, jak toho dosáhnout krok za krokem!

## Předpoklady

Než začneme, budete potřebovat několik věcí:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou aplikaci Aspose.Words for .NET. Můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Vývojové prostředí AC# jako Visual Studio.
- Ukázkový dokument: Dokument aplikace Word pro práci. Pro tento výukový program můžete použít jakýkoli soubor .docx.
- Základní znalost C#: Znalost programování v C#.

Jakmile je budete mít připravené, můžeme začít!

## Importovat jmenné prostory

Chcete-li používat Aspose.Words pro .NET, budete muset na začátek kódu importovat potřebné jmenné prostory. To zajišťuje, že máte přístup ke všem třídám a metodám potřebným pro manipulaci s dokumenty.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Vložte svůj dokument

Nejprve musíme načíst dokument aplikace Word, který chceme převést. Předpokládejme, že náš dokument je pojmenován`Rendering.docx` a je umístěn v adresáři určeném zástupným symbolem`YOUR DOCUMENT DIRECTORY`.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 Tento kód inicializuje cestu k vašemu dokumentu a načte jej do souboru Aspose.Words`Document` objekt.

## Krok 2: Nastavte ImageSaveOptions

 Dále nastavíme`ImageSaveOptions` specifikovat, jak chceme, aby byl náš JPEG generován. To zahrnuje nastavení rozsahu stránek, jasu obrazu, kontrastu a rozlišení.

```csharp
ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Jpeg);
options.PageSet = new PageSet(0); // Převeďte pouze první stránku
options.ImageBrightness = 0.3f;   // Nastavte jas
options.ImageContrast = 0.7f;     // Nastavte kontrast
options.HorizontalResolution = 72f; // Nastavte rozlišení
```

## Krok 3: Uložte dokument jako JPEG

Nakonec dokument uložíme jako soubor JPEG pomocí nastavení, které jsme definovali.

```csharp
doc.Save(dataDir + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
```

 Tento kód uloží první stránku`Rendering.docx` jako obrázek JPEG se zadaným nastavením jasu, kontrastu a rozlišení.

## Závěr

tady to máte! Úspěšně jste převedli konkrétní stránku dokumentu aplikace Word na obrázek JPEG s přizpůsobeným nastavením pomocí Aspose.Words for .NET. Tento proces lze upravit tak, aby vyhovoval různým potřebám, ať už připravujete obrázky pro web, vytváříte náhledy dokumentů a podobně.

## FAQ

### Mohu převést více stránek najednou?
 Ano, můžete určit rozsah stránek pomocí`PageSet` majetek v`ImageSaveOptions`.

### Jak upravím kvalitu obrazu?
 Kvalitu JPEG můžete upravit pomocí`JpegQuality` majetek v`ImageSaveOptions`.

### Mohu uložit v jiných formátech obrázků?
 Ano, Aspose.Words podporuje různé formáty obrázků jako PNG, BMP a TIFF. Změňte`SaveFormat` v`ImageSaveOptions` podle toho.

### Existuje způsob, jak zobrazit náhled obrázku před uložením?
Mechanismus náhledu byste museli implementovat samostatně, protože Aspose.Words neposkytuje vestavěnou funkci náhledu.

### Jak získám dočasnou licenci pro Aspose.Words?
 Můžete požádat a[dočasná licence zde](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
