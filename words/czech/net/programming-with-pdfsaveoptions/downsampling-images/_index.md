---
title: Zmenšete velikost dokumentu PDF pomocí převzorkování obrázků
linktitle: Zmenšete velikost dokumentu PDF pomocí převzorkování obrázků
second_title: Aspose.Words API pro zpracování dokumentů
description: Zmenšete velikost dokumentu PDF převzorkováním obrázků pomocí Aspose.Words for .NET. Optimalizujte své soubory PDF pro rychlejší nahrávání a stahování.
weight: 10
url: /cs/net/programming-with-pdfsaveoptions/downsampling-images/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zmenšete velikost dokumentu PDF pomocí převzorkování obrázků

## Zavedení

Soubory PDF jsou v digitálním světě základem a používají se ke všemu, od sdílení dokumentů po vytváření elektronických knih. Jejich velikost však může být někdy překážkou, zejména pokud jde o obsah bohatý na obrázky. Zde přichází na řadu převzorkování obrázků. Snížením rozlišení obrázků v PDF můžete výrazně zmenšit velikost souboru, aniž byste příliš ohrozili kvalitu. V tomto tutoriálu si projdeme kroky, jak toho dosáhnout pomocí Aspose.Words for .NET.

## Předpoklady

Než se pustíme do kódu, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud ne, můžete si jej stáhnout[zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Jakékoli vývojové prostředí .NET, jako je Visual Studio.
3. Základní znalost C#: Bude užitečné porozumět základům programování v C#.
4.  Ukázkový dokument: Dokument aplikace Word (např.`Rendering.docx`) s obrázky pro převod do PDF.

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory. Přidejte tyto v horní části souboru kódu:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nyní si tento proces rozdělíme na zvládnutelné kroky.

## Krok 1: Vložte dokument

Prvním krokem je načtení dokumentu aplikace Word. Zde zadáte cestu k adresáři dokumentů.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 tomto kroku načítáme dokument Word ze zadaného adresáře. Nezapomeňte vyměnit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde se váš dokument nachází.

## Krok 2: Nakonfigurujte možnosti převzorkování

Dále musíme nakonfigurovat možnosti převzorkování. To zahrnuje nastavení rozlišení a prahu rozlišení pro obrázky.

```csharp
// Můžeme nastavit minimální práh pro downsampling.
// Tato hodnota zabrání převzorkování druhého obrázku ve vstupním dokumentu.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

 Zde vytváříme novou instanci`PdfSaveOptions` a nastavení`Resolution` až 36 DPI a`ResolutionThreshold` až 128 DPI. To znamená, že jakýkoli obrázek s rozlišením vyšším než 128 DPI bude převzorkován na 36 DPI.

## Krok 3: Uložte dokument jako PDF

Nakonec dokument uložíme jako PDF s nakonfigurovanými možnostmi.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

V tomto posledním kroku ukládáme dokument jako PDF do stejného adresáře se zadanými možnostmi převzorkování.

## Závěr

tady to máte! Úspěšně jste zmenšili velikost svého PDF převzorkováním obrázků pomocí Aspose.Words for .NET. Díky tomu jsou vaše soubory PDF nejen lépe spravovatelné, ale také pomáhá rychleji nahrávat, stahovat a plynuleji sledovat.

## FAQ

### Co je to downsampling?
Převzorkování je proces snižování rozlišení obrázků, který pomáhá zmenšit velikost souboru dokumentů obsahujících tyto obrázky.

### Ovlivní downsampling kvalitu obrázků?
Ano, převzorkování sníží kvalitu obrazu. Dopad však závisí na stupni snížení rozlišení. Je to kompromis mezi velikostí souboru a kvalitou obrazu.

### Mohu si vybrat, které obrázky převzorkovat?
 Ano, nastavením`ResolutionThreshold`, můžete ovládat, které obrázky budou převzorkovány na základě jejich původního rozlišení.

### Jaké je ideální rozlišení pro downsampling?
Ideální rozlišení závisí na vašich konkrétních potřebách. Běžně se pro webové obrázky používá 72 DPI, zatímco vyšší rozlišení se používá pro kvalitu tisku.

### Je Aspose.Words for .NET zdarma?
 Aspose.Words for .NET je komerční produkt, ale můžete si stáhnout bezplatnou zkušební verzi[zde](https://releases.aspose.com/) nebo požádat o a[dočasná licence](https://purchase.aspose.com/temporary-license/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
