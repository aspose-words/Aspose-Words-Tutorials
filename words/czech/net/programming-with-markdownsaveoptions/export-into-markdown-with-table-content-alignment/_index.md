---
"description": "Naučte se, jak exportovat dokumenty Wordu do Markdownu se zarovnanými tabulkami pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu pro perfektní tabulky v Markdownu."
"linktitle": "Export do Markdownu se zarovnáním obsahu tabulky"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Export do Markdownu se zarovnáním obsahu tabulky"
"url": "/cs/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Export do Markdownu se zarovnáním obsahu tabulky

## Zavedení

Ahoj! Přemýšleli jste někdy, jak exportovat dokument Wordu do formátu Markdown s dokonale zarovnanými tabulkami? Ať už jste vývojář pracující na dokumentaci, nebo jen někdo, kdo miluje Markdown, tento průvodce je pro vás. Ponoříme se do detailů používání Aspose.Words pro .NET k dosažení tohoto cíle. Jste připraveni proměnit tabulky Wordu v úhledně zarovnané tabulky Markdownu? Pojďme na to!

## Předpoklady

Než se ponoříme do kódu, je třeba mít připraveno několik věcí:

1. Knihovna Aspose.Words pro .NET: Ujistěte se, že máte knihovnu Aspose.Words pro .NET. Můžete si ji stáhnout z [Stránka s vydáními Aspose](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Nastavte si vývojové prostředí. Visual Studio je oblíbenou volbou pro vývoj v .NET.
3. Základní znalost C#: Znalost C# je nezbytná, protože budeme v tomto jazyce psát kód.
4. Ukázkový dokument Wordu: Mějte dokument Wordu, který můžete použít k testování.

## Importovat jmenné prostory

Než začneme s kódováním, importujme potřebné jmenné prostory. Ty nám umožní přístup ke třídám a metodám Aspose.Words, které budeme používat.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Inicializace dokumentu a DocumentBuilderu

Nejdříve musíme vytvořit nový dokument Wordu a inicializovat jej. `DocumentBuilder` objekt pro zahájení tvorby našeho dokumentu.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Vytvořte nový dokument.
Document doc = new Document();

// Inicializujte nástroj DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložení buněk a zarovnání obsahu

Dále vložíme do dokumentu několik buněk a nastavíme jejich zarovnání. To je klíčové pro zajištění správného zarovnání exportu do Markdownu.

```csharp
// Vložte buňku a nastavte zarovnání doprava.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Vložte další buňku a zarovnejte ji na střed.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Krok 3: Nastavení zarovnání obsahu tabulky pro export Markdownu

Nyní je čas nakonfigurovat `MarkdownSaveOptions` pro ovládání zarovnání obsahu tabulky v exportovaném souboru Markdown. Uložíme dokument s různým nastavením zarovnání, abychom viděli, jak to funguje.

```csharp
// Vytvořte objekt MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Uložit dokument se zarovnáním doleva.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Změňte zarovnání doprava a uložte.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Změňte zarovnání na střed a uložte.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Krok 4: Použití automatického zarovnání obsahu tabulky

Ten/Ta/To `Auto` Možnost zarovnání převezme zarovnání od prvního odstavce v odpovídajícím sloupci tabulky. To může být užitečné, pokud máte v jedné tabulce smíšené zarovnání.

```csharp
// Nastavte zarovnání na Automaticky.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Uložit dokument s automatickým zarovnáním.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Závěr

A je to! Export dokumentů Wordu do Markdownu se zarovnanými tabulkami pomocí Aspose.Words pro .NET je hračka, jakmile víte, jak na to. Tato výkonná knihovna usnadňuje správu formátování a zarovnání tabulek a zajišťuje, že vaše dokumenty v Markdownu vypadají přesně tak, jak chcete. Hodně štěstí s programováním!

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna, která umožňuje vývojářům programově vytvářet, upravovat, převádět a exportovat dokumenty Wordu.

### Mohu nastavit různá zarovnání pro různé sloupce ve stejné tabulce?
Ano, pomocí `Auto` možnost zarovnání, můžete mít různá zarovnání na základě prvního odstavce v každém sloupci.

### Potřebuji licenci k používání Aspose.Words pro .NET?
Ano, Aspose.Words pro .NET vyžaduje pro plnou funkčnost licenci. Můžete si pořídit [dočasná licence](https://purchase.aspose.com/temporary-license/) pro hodnocení.

### Je možné exportovat další prvky dokumentu do Markdownu pomocí Aspose.Words?
Ano, Aspose.Words podporuje export různých prvků, jako jsou nadpisy, seznamy a obrázky, do formátu Markdown.

### Kde mohu získat podporu, pokud narazím na problémy?
Podporu můžete získat od [Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}