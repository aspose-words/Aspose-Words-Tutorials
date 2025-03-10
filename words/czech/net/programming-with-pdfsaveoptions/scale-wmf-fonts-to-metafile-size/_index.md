---
title: Zmenšete velikost PDF pomocí změny velikosti písem WMF na velikost metasouboru
linktitle: Zmenšete velikost PDF pomocí změny velikosti písem WMF na velikost metasouboru
second_title: Aspose.Words API pro zpracování dokumentů
description: Podrobný průvodce pro zmenšení velikosti PDF pomocí měřítka wmf písem na velikost metasouboru při převodu do PDF pomocí Aspose.Words pro .NET.
weight: 10
url: /cs/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zmenšete velikost PDF pomocí změny velikosti písem WMF na velikost metasouboru

## Zavedení

Při práci se soubory PDF, zejména se soubory generovanými z dokumentů aplikace Word obsahujících grafiku WMF (Windows Metafile), se může správa velikosti stát zásadním aspektem při manipulaci s dokumenty. Jedním ze způsobů, jak ovládat velikost PDF, je upravit způsob vykreslování písem WMF v dokumentu. V tomto tutoriálu prozkoumáme, jak zmenšit velikost PDF změnou velikosti písem WMF na velikost metasouboru pomocí Aspose.Words for .NET.

## Předpoklady

Než se ponoříte do kroků, ujistěte se, že máte následující:

1. Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud ne, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Tento tutoriál předpokládá, že máte nastavené vývojové prostředí .NET (jako Visual Studio), kde můžete psát a spouštět kód C#.
3. Základní porozumění programování .NET: Užitečná bude znalost základních konceptů programování .NET a syntaxe C#.
4. Dokument aplikace Word s grafikou WMF: Budete potřebovat dokument aplikace Word obsahující grafiku WMF. Můžete použít svůj vlastní dokument nebo si jej vytvořit pro testování.

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory do vašeho projektu C#. To vám umožní přístup ke třídám a metodám potřebným pro práci s Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Načtěte dokument aplikace Word

 Chcete-li začít, načtěte dokument aplikace Word, který obsahuje grafiku WMF. To se provádí pomocí`Document` třídy z Aspose.Words.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Vložte dokument
Document doc = new Document(dataDir + "WMF with text.docx");
```

 Zde,`dataDir` je zástupný symbol pro cestu k adresáři vašeho dokumentu. Vytvoříme instanci`Document` třídy předáním cesty k souboru aplikace Word. Tím se dokument načte do paměti, připraven k dalšímu zpracování.

## Krok 2: Nakonfigurujte možnosti vykreslování metasouborů

 Dále je třeba nakonfigurovat možnosti vykreslování metasouborů. Konkrétně nastavte`ScaleWmfFontsToMetafileSize`majetek do`false`. To řídí, zda jsou písma WMF změněna tak, aby odpovídala velikosti metasouboru.

```csharp
// Vytvořte novou instanci MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

 The`MetafileRenderingOptions` class poskytuje možnosti, jak se metasoubory (jako WMF) vykreslují. Nastavením`ScaleWmfFontsToMetafileSize` na`false`, dáváte Aspose.Words pokyn, aby neměnil velikost písem podle velikosti metasouboru, což může pomoci při zmenšení celkové velikosti PDF.

## Krok 3: Nastavte možnosti uložení PDF

Nyní nakonfigurujte možnosti uložení PDF tak, aby používaly možnosti vykreslování metasouborů, které jste právě nastavili. To říká Aspose.Words, jak zacházet s metasoubory při ukládání dokumentu jako PDF.

```csharp
// Vytvořte novou instanci PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

 The`PdfSaveOptions` class umožňuje určit různá nastavení pro uložení dokumentu jako PDF. Přiřazením dříve nakonfigurovaného`MetafileRenderingOptions` k`MetafileRenderingOptions` vlastnictví`PdfSaveOptions`, zajistíte, že se dokument uloží podle požadovaného nastavení vykreslování metasouboru.

## Krok 4: Uložte dokument jako PDF

Nakonec uložte dokument aplikace Word jako PDF pomocí nakonfigurovaných možností uložení. Tím se na výstupní PDF použijí všechna nastavení, včetně možností vykreslování metasouborů.


```csharp
// Uložte dokument jako PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

 V tomto kroku se`Save` metoda`Document` třída slouží k exportu dokumentu do souboru PDF. Je určena cesta, kam bude PDF uložen, spolu s`PdfSaveOptions` které zahrnují nastavení vykreslování metasouborů.

## Závěr

Změnou velikosti písem WMF na velikost metasouboru můžete výrazně zmenšit velikost souborů PDF generovaných z dokumentů aplikace Word. Tato technika pomáhá při optimalizaci ukládání a distribuce dokumentů, aniž by byla ohrožena kvalita vizuálního obsahu. Dodržením výše uvedených kroků zajistíte, že vaše soubory PDF budou lépe spravovatelné a jejich velikost je efektivnější.

## FAQ

### Co je to WMF a proč je důležité pro velikost PDF?

WMF (Windows Metafile) je grafický formát používaný v Microsoft Windows. Může obsahovat vektorová i bitmapová data. Vzhledem k tomu, že vektorová data lze škálovat a manipulovat s nimi, je důležité s nimi zacházet správně, abyste se vyhnuli zbytečně velkým souborům PDF.

### Jak změna měřítka písem WMF na velikost metasouboru ovlivní PDF?

Změna měřítka písem WMF na velikost metasouboru může pomoci snížit celkovou velikost PDF tím, že se vyhnete vykreslování písem s vysokým rozlišením, které by mohlo zvětšit velikost souboru.

### Mohu s Aspose.Words používat jiné formáty metasouborů?

Ano, Aspose.Words podporuje různé formáty metasouborů, včetně EMF (Enhanced Metafile) kromě WMF.

### Je tato technika použitelná pro všechny typy dokumentů aplikace Word?

Ano, tuto techniku lze použít na jakýkoli dokument aplikace Word, který obsahuje grafiku WMF, což pomáhá optimalizovat velikost generovaného PDF.

### Kde najdu více informací o Aspose.Words?

 Více o Aspose.Words můžete prozkoumat v[Dokumentace Aspose.Words](https://reference.aspose.com/words/net/) . Pro stažení, zkušební verze a podporu navštivte[Stránka ke stažení Aspose.Words](https://releases.aspose.com/words/net/), [Koupit Aspose.Words](https://purchase.aspose.com/buy), [Bezplatná zkušební verze](https://releases.aspose.com/), [Dočasná licence](https://purchase.aspose.com/temporary-license/) a[Podpora](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
