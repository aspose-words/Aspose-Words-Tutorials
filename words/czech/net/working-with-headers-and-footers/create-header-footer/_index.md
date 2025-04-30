---
"description": "Naučte se, jak přidávat a upravovat záhlaví a zápatí v dokumentech Wordu pomocí Aspose.Words pro .NET. Tento podrobný návod zajišťuje profesionální formátování dokumentů."
"linktitle": "Vytvořit záhlaví a zápatí"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vytvořit záhlaví a zápatí"
"url": "/cs/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořit záhlaví a zápatí

## Zavedení

Přidání záhlaví a zápatí do dokumentů může zvýšit jejich profesionalitu a čitelnost. S Aspose.Words pro .NET můžete snadno vytvářet a upravovat záhlaví a zápatí pro dokumenty Word. V tomto tutoriálu vás krok za krokem provedeme celým procesem a zajistíme, že tyto funkce budete moci bez problémů implementovat.

## Předpoklady

Než začnete, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Stáhněte a nainstalujte z [odkaz ke stažení](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Například Visual Studio, pro psaní a spouštění kódu.
- Základní znalost C#: Znalost C# a .NET frameworku.
- Ukázkový dokument: Ukázkový dokument pro použití záhlaví a zápatí nebo vytvoření nového dokumentu, jak je znázorněno v tutoriálu.

## Importovat jmenné prostory

Nejprve je třeba importovat potřebné jmenné prostory pro přístup ke třídám a metodám Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Krok 1: Definování adresáře dokumentů

Definujte adresář, kam bude dokument uložen. To pomůže efektivně spravovat cestu.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Krok 2: Vytvořte nový dokument

Vytvořte nový dokument a `DocumentBuilder` pro usnadnění přidávání obsahu.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Konfigurace nastavení stránky

Nastavte nastavení stránky, včetně toho, zda bude mít první stránka jinou záhlaví/zápatí.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Krok 4: Přidání záhlaví na první stránku

Přejděte do sekce záhlaví první stránky a nakonfigurujte text záhlaví.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Krok 5: Přidání primární hlavičky

Přejděte do hlavní sekce záhlaví a vložte obrázek a text.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Vložte obrázek do záhlaví
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Krok 6: Přidání primární patičky

Přejděte do primární sekce zápatí a vytvořte tabulku pro formátování obsahu zápatí.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Přidat číslování stránek
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

## Krok 7: Přidání obsahu a zalomení stránek

Přejděte na konec dokumentu, přidejte zalomení stránky a vytvořte novou sekci s jiným nastavením stránky.

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

## Krok 8: Zkopírujte záhlaví a zápatí z předchozí sekce

Pokud chcete znovu použít záhlaví a zápatí z předchozí sekce, zkopírujte je a proveďte potřebné úpravy.

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

Pomocí těchto kroků můžete efektivně přidávat a upravovat záhlaví a zápatí v dokumentech Word pomocí Aspose.Words pro .NET. Tím se vylepší vzhled a profesionalita vašeho dokumentu, díky čemuž bude čitelnější a poutavější.

## Často kladené otázky

### Co je Aspose.Words pro .NET?

Aspose.Words pro .NET je knihovna, která umožňuje vývojářům programově vytvářet, upravovat a převádět dokumenty Wordu v aplikacích .NET.

### Mohu přidat obrázky do záhlaví nebo zápatí?

Ano, obrázky můžete snadno přidat do záhlaví nebo zápatí pomocí `DocumentBuilder.InsertImage` metoda.

### Jak nastavím různé záhlaví a zápatí pro první stránku?

Pro první stránku můžete nastavit různá záhlaví a zápatí pomocí `DifferentFirstPageHeaderFooter` majetek `PageSetup` třída.

### Kde najdu další dokumentaci k Aspose.Words?

Komplexní dokumentaci naleznete na [Stránka s dokumentací k API Aspose.Words](https://reference.aspose.com/words/net/).

### Je k dispozici podpora pro Aspose.Words?

Ano, Aspose nabízí podporu prostřednictvím svých [fórum podpory](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}