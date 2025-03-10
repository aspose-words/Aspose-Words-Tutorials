---
title: Vytvořit záhlaví zápatí
linktitle: Vytvořit záhlaví zápatí
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se přidávat a upravovat záhlaví a zápatí v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tento podrobný průvodce zajišťuje profesionální formátování dokumentů.
weight: 10
url: /cs/net/working-with-headers-and-footers/create-header-footer/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořit záhlaví zápatí

## Zavedení

Přidáním záhlaví a zápatí do dokumentů můžete zvýšit jejich profesionalitu a čitelnost. S Aspose.Words for .NET můžete snadno vytvářet a upravovat záhlaví a zápatí pro vaše dokumenty Word. V tomto tutoriálu vás provedeme procesem krok za krokem a zajistíme, že tyto funkce můžete bezproblémově implementovat.

## Předpoklady

Než začnete, ujistěte se, že máte následující:

-  Aspose.Words for .NET: Stáhněte a nainstalujte z[odkaz ke stažení](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Například Visual Studio pro psaní a spouštění kódu.
- Základní znalost C#: Pochopení C# a .NET frameworku.
- Ukázkový dokument: Ukázkový dokument pro použití záhlaví a zápatí nebo vytvoření nového, jak je znázorněno ve výukovém programu.

## Importovat jmenné prostory

Nejprve musíte importovat potřebné jmenné prostory pro přístup ke třídám a metodám Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Krok 1: Definujte adresář dokumentů

Definujte adresář, kam bude dokument uložen. To pomáhá při efektivním řízení cesty.

```csharp
// Cesta k adresáři dokumentů
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Krok 2: Vytvořte nový dokument

 Vytvořte nový dokument a a`DocumentBuilder`pro usnadnění přidávání obsahu.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Nakonfigurujte nastavení stránky

Nastavte nastavení stránky, včetně toho, zda bude mít první stránka jiné záhlaví/zápatí.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Krok 4: Přidejte záhlaví na první stránku

Přejděte do sekce záhlaví pro první stránku a nakonfigurujte text záhlaví.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Krok 5: Přidejte primární záhlaví

Přejděte do primární sekce záhlaví a vložte obrázek a text.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Vložte obrázek do záhlaví
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Krok 6: Přidejte primární zápatí

Přejděte do primární sekce zápatí a vytvořte tabulku pro formátování obsahu zápatí.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Přidejte číslování stránek
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Krok 7: Přidejte obsah a konce stránek

Přejděte na konec dokumentu, přidejte konec stránky a vytvořte nový oddíl s jiným nastavením stránky.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Krok 8: Zkopírujte záhlaví a zápatí z předchozí části

Pokud chcete znovu použít záhlaví a zápatí z předchozí sekce, zkopírujte je a použijte potřebné úpravy.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Závěr

Pomocí následujících kroků můžete efektivně přidávat a upravovat záhlaví a zápatí v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tím se zlepší vzhled a profesionalita vašeho dokumentu, takže bude čitelnější a poutavější.

## FAQ

### Co je Aspose.Words for .NET?

Aspose.Words for .NET je knihovna, která umožňuje vývojářům vytvářet, upravovat a převádět dokumenty aplikace Word programově v rámci aplikací .NET.

### Mohu přidat obrázky do záhlaví nebo zápatí?

 Ano, obrázky můžete snadno přidat do záhlaví nebo zápatí pomocí`DocumentBuilder.InsertImage` metoda.

### Jak nastavím různá záhlaví a zápatí pro první stránku?

 Můžete nastavit různá záhlaví a zápatí pro první stránku pomocí`DifferentFirstPageHeaderFooter` vlastnictvím`PageSetup` třída.

### Kde najdu další dokumentaci k Aspose.Words?

 Komplexní dokumentaci naleznete na[Stránka dokumentace API Aspose.Words](https://reference.aspose.com/words/net/).

### Je k dispozici podpora pro Aspose.Words?

 Ano, Aspose nabízí podporu prostřednictvím jejich[fórum podpory](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
