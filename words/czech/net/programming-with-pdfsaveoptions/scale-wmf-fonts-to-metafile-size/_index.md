---
"description": "Podrobný návod, jak zmenšit velikost PDF pomocí škálování písem WMF na velikost metasouboru při převodu do PDF pomocí Aspose.Words pro .NET."
"linktitle": "Zmenšení velikosti PDF pomocí škálování písem WMF na velikost metasouboru"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zmenšení velikosti PDF pomocí škálování písem WMF na velikost metasouboru"
"url": "/cs/net/programming-with-pdfsaveoptions/scale-wmf-fonts-to-metafile-size/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zmenšení velikosti PDF pomocí škálování písem WMF na velikost metasouboru

## Zavedení

Při práci se soubory PDF, zejména s těmi, které jsou generovány z dokumentů Wordu obsahujících grafiku WMF (Windows Metafile), se může správa velikosti stát klíčovým aspektem práce s dokumenty. Jedním ze způsobů, jak ovládat velikost PDF, je úprava způsobu vykreslování písem WMF v dokumentu. V tomto tutoriálu se podíváme na to, jak zmenšit velikost PDF změnou velikosti písem WMF na velikost metasouboru pomocí Aspose.Words pro .NET.

## Předpoklady

Než se pustíte do jednotlivých kroků, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud ne, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Tento tutoriál předpokládá, že máte nastavené vývojové prostředí .NET (například Visual Studio), kde můžete psát a spouštět kód C#.
3. Základní znalost programování v .NET: Znalost základních konceptů programování v .NET a syntaxe C# bude užitečná.
4. Dokument Word s grafikou WMF: Budete potřebovat dokument Word obsahující grafiku WMF. Můžete použít vlastní dokument nebo si vytvořit nový pro testování.

## Importovat jmenné prostory

Nejprve je třeba importovat potřebné jmenné prostory do vašeho projektu v C#. To vám umožní přístup ke třídám a metodám potřebným pro práci s Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Načtěte dokument Wordu

Chcete-li začít, načtěte dokument aplikace Word, který obsahuje grafiku WMF. To se provádí pomocí `Document` třída z Aspose.Words.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Načíst dokument
Document doc = new Document(dataDir + "WMF with text.docx");
```

Zde, `dataDir` je zástupný symbol pro cestu k adresáři dokumentů. Vytvoříme instanci třídy `Document` třídu předáním cesty k souboru aplikace Word. Tím se dokument načte do paměti a připraví k dalšímu zpracování.

## Krok 2: Konfigurace možností vykreslování metasouborů

Dále je třeba nakonfigurovat možnosti vykreslování metasouborů. Konkrétně nastavit `ScaleWmfFontsToMetafileSize` majetek `false`Toto určuje, zda se písma WMF škálují tak, aby odpovídala velikosti metasouboru.

```csharp
// Vytvořte novou instanci MetafileRenderingOptions
MetafileRenderingOptions metafileRenderingOptions = new MetafileRenderingOptions
{
    ScaleWmfFontsToMetafileSize = false
};
```

Ten/Ta/To `MetafileRenderingOptions` Třída poskytuje možnosti pro způsob vykreslování metasouborů (například WMF). Nastavením `ScaleWmfFontsToMetafileSize` na `false`, dáváte pokyn Aspose.Words, aby neměnil velikost písma podle velikosti metasouboru, což může pomoci zmenšit celkovou velikost PDF.

## Krok 3: Nastavení možností ukládání PDF

Nyní nakonfigurujte možnosti ukládání PDF tak, aby používaly právě nastavené možnosti vykreslování metasouborů. Tím se Aspose.Words dozví, jak má zpracovávat metasoubory při ukládání dokumentu jako PDF.

```csharp
// Vytvořte novou instanci PdfSaveOptions
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    MetafileRenderingOptions = metafileRenderingOptions
};
```

Ten/Ta/To `PdfSaveOptions` třída umožňuje zadat různá nastavení pro uložení dokumentu jako PDF. Přiřazením dříve nakonfigurovaných `MetafileRenderingOptions` k `MetafileRenderingOptions` majetek `PdfSaveOptions`, zajistíte, aby byl dokument uložen podle požadovaného nastavení vykreslování metasouborů.

## Krok 4: Uložte dokument jako PDF

Nakonec uložte dokument Wordu jako PDF pomocí nakonfigurovaných možností ukládání. Tím se všechna nastavení, včetně možností vykreslování metasouborů, použijí na výstupní PDF.


```csharp
// Uložit dokument jako PDF
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ScaleWmfFontsToMetafileSize.pdf", saveOptions);
```

V tomto kroku `Save` metoda `Document` Třída se používá k exportu dokumentu do souboru PDF. Je zadána cesta, kam bude PDF uložen, spolu s `PdfSaveOptions` které zahrnují nastavení vykreslování metasouborů.

## Závěr

Změnou velikosti písem WMF na metasoubor můžete výrazně zmenšit velikost souborů PDF generovaných z dokumentů aplikace Word. Tato technika pomáhá optimalizovat ukládání a distribuci dokumentů bez kompromisů v kvalitě vizuálního obsahu. Dodržení výše uvedených kroků zajistí, že vaše soubory PDF budou lépe spravovatelné a efektivnější co do velikosti.

## Často kladené otázky

### Co je WMF a proč je důležitý pro velikost PDF?

WMF (Windows Metafile) je grafický formát používaný v systému Microsoft Windows. Může obsahovat vektorová i bitmapová data. Vzhledem k tomu, že vektorová data lze škálovat a manipulovat s nimi, je důležité s nimi správně zacházet, aby se předešlo zbytečně velkým souborům PDF.

### Jak ovlivní formátování písem WMF na velikost metasouboru PDF?

Změna velikosti písem WMF na velikost metasouboru může pomoci zmenšit celkovou velikost PDF, protože se zabrání vykreslování písem s vysokým rozlišením, které by mohlo zvětšit velikost souboru.

### Mohu s Aspose.Words použít jiné formáty metasouborů?

Ano, Aspose.Words podporuje různé formáty metasouborů, včetně EMF (Enhanced Metafile) a WMF.

### Je tato technika použitelná pro všechny typy dokumentů Wordu?

Ano, tuto techniku lze použít na jakýkoli dokument aplikace Word, který obsahuje grafiku WMF, což pomáhá optimalizovat velikost vygenerovaného PDF.

### Kde najdu více informací o Aspose.Words?

Více informací o Aspose.Words naleznete v [Dokumentace k Aspose.Words](https://reference.aspose.com/words/net/)Pro stažení, zkušební verze a podporu navštivte [Stránka pro stažení Aspose.Words](https://releases.aspose.com/words/net/), [Koupit Aspose.Words](https://purchase.aspose.com/buy), [Bezplatná zkušební verze](https://releases.aspose.com/), [Dočasná licence](https://purchase.aspose.com/temporary-license/)a [Podpora](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}