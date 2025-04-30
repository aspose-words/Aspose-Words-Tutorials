---
"description": "Zmenšete velikost PDF dokumentu převzorkováním obrázků pomocí Aspose.Words pro .NET. Optimalizujte své PDF soubory pro rychlejší nahrávání a stahování."
"linktitle": "Zmenšení velikosti PDF dokumentu pomocí převzorkování obrázků"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zmenšení velikosti PDF dokumentu pomocí převzorkování obrázků"
"url": "/cs/net/programming-with-pdfsaveoptions/downsampling-images/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zmenšení velikosti PDF dokumentu pomocí převzorkování obrázků

## Zavedení

PDF soubory jsou v digitálním světě nedílnou součástí a používají se ke všemu od sdílení dokumentů až po tvorbu elektronických knih. Jejich velikost však může být někdy překážkou, zejména při práci s obsahem bohatým na obrázky. Zde přichází na řadu převzorkování obrázků. Snížením rozlišení obrázků v PDF můžete výrazně zmenšit velikost souboru, aniž byste museli příliš snižovat kvalitu. V tomto tutoriálu si ukážeme kroky, jak toho dosáhnout pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíme do kódu, ujistěme se, že máte vše potřebné:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud ne, můžete si ji stáhnout. [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Jakékoli vývojové prostředí pro .NET, například Visual Studio.
3. Základní znalost C#: Pochopení základů programování v C# bude užitečné.
4. Ukázkový dokument: Dokument aplikace Word (např. `Rendering.docx`) s obrázky k převodu do PDF.

## Importovat jmenné prostory

Nejdříve je potřeba importovat potřebné jmenné prostory. Přidejte je na začátek souboru s kódem:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Nyní si celý proces rozdělme na zvládnutelné kroky.

## Krok 1: Vložení dokumentu

Prvním krokem je načtení dokumentu Wordu. Zde zadáte cestu k adresáři s dokumenty.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

V tomto kroku načítáme dokument aplikace Word ze zadaného adresáře. Nezapomeňte nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde se váš dokument nachází.

## Krok 2: Konfigurace možností převzorkování

Dále je třeba nakonfigurovat možnosti převzorkování. To zahrnuje nastavení rozlišení a prahové hodnoty rozlišení pro obrázky.

```csharp
// Můžeme nastavit minimální prahovou hodnotu pro podvzorkování.
// Tato hodnota zabrání převzorkování druhého obrázku ve vstupním dokumentu.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    DownsampleOptions = { Resolution = 36, ResolutionThreshold = 128 }
};
```

Zde vytváříme novou instanci `PdfSaveOptions` a nastavení `Resolution` na 36 DPI a `ResolutionThreshold` na 128 DPI. To znamená, že jakýkoli obrázek s rozlišením vyšším než 128 DPI bude převzorkován na 36 DPI.

## Krok 3: Uložte dokument jako PDF

Nakonec dokument uložíme jako PDF s nakonfigurovanými možnostmi.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DownsamplingImages.pdf", saveOptions);
```

V tomto posledním kroku ukládáme dokument jako PDF do stejného adresáře se zadanými možnostmi převzorkování.

## Závěr

A tady to máte! Úspěšně jste zmenšili velikost PDF souboru převzorkováním obrázků pomocí Aspose.Words pro .NET. Díky tomu se vaše PDF soubory nejen lépe spravují, ale také se rychleji nahrávají, stahují a jejich prohlížení je plynulejší.

## Často kladené otázky

### Co je to podvzorkování?
Downsampling je proces snižování rozlišení obrázků, který pomáhá zmenšit velikost souborů dokumentů obsahujících tyto obrázky.

### Ovlivní downsampling kvalitu obrázků?
Ano, podvzorkování sníží kvalitu obrazu. Dopad však závisí na stupni snížení rozlišení. Jde o kompromis mezi velikostí souboru a kvalitou obrazu.

### Mohu si vybrat, které obrázky mám převzorkovat?
Ano, nastavením `ResolutionThreshold`, můžete ovládat, které obrázky budou převzorkovány na základě jejich původního rozlišení.

### Jaké je ideální rozlišení pro downsampling?
Ideální rozlišení závisí na vašich specifických potřebách. Pro webové obrázky se obvykle používá 72 DPI, zatímco vyšší rozlišení se používá pro kvalitu tisku.

### Je Aspose.Words pro .NET zdarma?
Aspose.Words pro .NET je komerční produkt, ale můžete si stáhnout bezplatnou zkušební verzi. [zde](https://releases.aspose.com/) nebo si zažádat o [dočasná licence](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}