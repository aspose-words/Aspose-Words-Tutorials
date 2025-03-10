---
title: Export do Markdown se zarovnáním obsahu tabulky
linktitle: Export do Markdown se zarovnáním obsahu tabulky
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se exportovat dokumenty Wordu do Markdown se zarovnanými tabulkami pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce pro dokonalé stoly Markdown.
weight: 10
url: /cs/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export do Markdown se zarovnáním obsahu tabulky

## Zavedení

Ahoj! Přemýšleli jste někdy, jak exportovat dokument aplikace Word do formátu Markdown s dokonale zarovnanými tabulkami? Ať už jste vývojář pracující na dokumentaci nebo jen někdo, kdo miluje Markdown, tento průvodce je pro vás. Abychom toho dosáhli, ponoříme se do toho nejnutnějšího použití Aspose.Words pro .NET. Jste připraveni přeměnit své Word tabulky na úhledně zarovnané Markdown tabulky? Začněme!

## Předpoklady

Než se ponoříme do kódu, je třeba mít připraveno několik věcí:

1.  Knihovna Aspose.Words for .NET: Ujistěte se, že máte knihovnu Aspose.Words for .NET. Můžete si jej stáhnout z[Aspose Releases Page](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Nastavte své vývojové prostředí. Visual Studio je oblíbenou volbou pro vývoj .NET.
3. Základní znalost C#: Pochopení C# je nezbytné, protože budeme psát kód v tomto jazyce.
4. Ukázkový dokument Word: Mějte dokument Word, který můžete použít pro testování.

## Importovat jmenné prostory

Než začneme kódovat, naimportujeme potřebné jmenné prostory. Ty nám umožní přístup ke třídám a metodám Aspose.Words, které budeme používat.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 1: Inicializujte Document a DocumentBuilder

Nejprve musíme vytvořit nový dokument aplikace Word a inicializovat a`DocumentBuilder` začněte budovat náš dokument.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Vytvořte nový dokument.
Document doc = new Document();

// Inicializujte DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 2: Vložte buňky a zarovnejte obsah

Dále do našeho dokumentu vložíme nějaké buňky a nastavíme jejich zarovnání. To je klíčové pro zajištění toho, aby si export Markdown zachoval správné zarovnání.

```csharp
// Vložte buňku a nastavte zarovnání doprava.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Vložte další buňku a nastavte zarovnání na střed.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Krok 3: Nastavte zarovnání obsahu tabulky pro export Markdown

 Nyní je čas nakonfigurovat`MarkdownSaveOptions` k ovládání zarovnání obsahu tabulky v exportovaném souboru Markdown. Uložíme dokument s různým nastavením zarovnání, abychom viděli, jak to funguje.

```csharp
// Vytvořte objekt MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Uložte dokument se zarovnáním doleva.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Změňte zarovnání doprava a uložte.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Změňte zarovnání na střed a uložte.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Krok 4: Použijte automatické zarovnání obsahu tabulky

 The`Auto`volba zarovnání převezme zarovnání z prvního odstavce v odpovídajícím sloupci tabulky. To může být užitečné, když máte smíšená zarovnání v jedné tabulce.

```csharp
// Nastavte zarovnání na Auto.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Uložte dokument pomocí automatického zarovnání.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Závěr

A tady to máte! Export dokumentů Wordu do Markdown se zarovnanými tabulkami pomocí Aspose.Words for .NET je hračka, jakmile víte, jak na to. Tato výkonná knihovna usnadňuje ovládání formátování a zarovnání vašich tabulek a zajišťuje, že vaše dokumenty Markdown vypadají přesně tak, jak chcete. Šťastné kódování!

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna, která umožňuje vývojářům vytvářet, upravovat, převádět a exportovat dokumenty aplikace Word programově.

### Mohu nastavit různá zarovnání pro různé sloupce ve stejné tabulce?
 Ano, pomocí`Auto` možnost zarovnání, můžete mít různá zarovnání na základě prvního odstavce v každém sloupci.

### Potřebuji licenci k používání Aspose.Words pro .NET?
 Ano, Aspose.Words for .NET vyžaduje licenci pro plnou funkčnost. Můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/) pro hodnocení.

### Je možné exportovat další prvky dokumentu do Markdown pomocí Aspose.Words?
Ano, Aspose.Words podporuje export různých prvků, jako jsou nadpisy, seznamy a obrázky, do formátu Markdown.

### Kde mohu získat podporu, pokud narazím na problémy?
 Můžete získat podporu od[Fórum podpory Aspose.Words](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
