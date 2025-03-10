---
title: Udržujte stůl pohromadě
linktitle: Udržujte stůl pohromadě
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak zabránit rozbití tabulek na stránkách pomocí Aspose.Words for .NET pomocí tohoto podrobného průvodce. Zajistěte úhledné, profesionálně vypadající dokumenty Word
weight: 10
url: /cs/net/join-and-append-documents/keep-source-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Udržujte stůl pohromadě

## Zavedení

Tabulky jsou nezbytnou součástí mnoha dokumentů aplikace Word, ale někdy se můžete dostat do situace, kdy se tabulka rozpadne na dvě stránky. To může narušit tok vašeho dokumentu a ovlivnit jeho čitelnost. Nebylo by hezké, kdyby existoval způsob, jak udržet celou tabulku pohromadě na jedné stránce? S Aspose.Words pro .NET existuje snadné řešení tohoto problému! V tomto tutoriálu si projdeme, jak zabránit rozdělení tabulek na stránky a zajistit, aby váš dokument vypadal elegantně a profesionálně.

## Předpoklady

Než se pustíme do výukového programu, ujistěte se, že máte vše, co potřebujete, abyste mohli plynule pokračovat.

### Aspose.Words pro knihovnu .NET

Nejprve budete muset mít nainstalovanou aplikaci Aspose.Words for .NET. Toto je výkonná knihovna, která vám umožňuje programově pracovat s dokumenty aplikace Word.

- [Stáhněte si Aspose.Words pro .NET](https://releases.aspose.com/words/net/)

### Vývojové prostředí

Měli byste mít nastavené vývojové prostředí pro spouštění kódu C#, například:

- Visual Studio (jakákoli nejnovější verze)
- .NET Framework 2.0 nebo novější

### Dokument aplikace Word s tabulkou

 Budete potřebovat dokument aplikace Word, který obsahuje tabulku. V tomto tutoriálu budeme pracovat s ukázkovým dokumentem s názvem`"Table spanning two pages.docx"`. Tento soubor obsahuje tabulku, která aktuálně zahrnuje dvě stránky.

### Dočasná licence (volitelné)

 Zatímco Aspose.Words přichází s bezplatnou zkušební verzí, možná budete chtít použít a[dočasná licence](https://purchase.aspose.com/temporary-license/) odemknout plný potenciál knihovny.

## Importujte balíčky

Před napsáním jakéhokoli kódu musíme naimportovat potřebné jmenné prostory pro práci s Aspose.Words for .NET. Na začátek souboru kódu přidejte následující importy:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

 Tyto jmenné prostory vám umožňují přístup k třídám, jako je`Document`, `Table`, `Cell`, a další, které použijeme v tomto tutoriálu.

## Krok 1: Vložte dokument

 První věc, kterou musíme udělat, je načíst dokument aplikace Word, který obsahuje tabulku. K tomu použijeme`Document` třídy z Aspose.Words. Tato třída umožňuje programově otevírat a manipulovat se soubory aplikace Word.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

 V tomto fragmentu kódu určujeme umístění našeho dokumentu. Nahradit`"YOUR DOCUMENTS DIRECTORY"` se skutečným adresářem, kde je váš dokument uložen.

## Krok 2: Přístup k tabulce

Jakmile je dokument načten, dalším krokem je přístup k tabulce, kterou chceme mít pohromadě. V tomto příkladu předpokládáme, že tabulka je první tabulkou v dokumentu.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

 Tento řádek kódu najde první tabulku v dokumentu. The`GetChild` metoda načte určitý typ uzlu, což v tomto případě je`NodeType.Table` . The`0` znamená, že chceme první tabulku a`true`flag zajišťuje, že prohledáváme rekurzivně ve všech podřízených uzlech.

## Krok 3: Procházení buněk tabulky

Nyní musíme projít každou buňku v tabulce. Vzhledem k tomu, že tabulka obsahuje více řádků a každý řádek obsahuje více buněk, projdeme každou buňku a zajistíme, aby se nerozbila na stránkách.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

 Zde,`GetChildNodes` načte všechny buňky v tabulce a procházíme každou z nich. The`EnsureMinimum()` metoda zajišťuje, že každá buňka obsahuje alespoň jeden odstavec, protože prázdná buňka by mohla později způsobit problémy.

## Krok 4: Nastavte vlastnost KeepWithNext

 Aby se zabránilo rozbití tabulky přes stránky, musíme nastavit`KeepWithNext` vlastnost pro každý odstavec v tabulce. Tato vlastnost zajišťuje, že odstavec zůstane s dalším odstavcem, čímž účinně zabrání zalomení stránek mezi nimi.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

 Tato smyčka kontroluje každý odstavec uvnitř každé buňky. Podmínka zajišťuje, že nepoužijeme`KeepWithNext`vlastnost do posledního odstavce v posledním řádku. Jinak by vlastnost neměla žádný účinek, protože neexistuje žádný další odstavec.

## Krok 5: Uložte dokument

 Nakonec po aplikaci`KeepWithNext` vlastnost, musíme upravený dokument uložit.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Tento řádek uloží aktualizovaný dokument pod novým názvem a zachová původní soubor. Nyní můžete otevřít výsledný soubor a uvidíte, že tabulka již není rozdělena na dvě stránky!

## Závěr

A tady to máte! Pomocí těchto jednoduchých kroků můžete snadno zabránit rozbití tabulek na stránkách v dokumentech aplikace Word pomocí Aspose.Words for .NET. Ať už pracujete na zprávách, smlouvách nebo jiných dokumentech, udržování nedotčených tabulek zajišťuje uhlazenější a profesionálnější vzhled.

Krása Aspose.Words spočívá v její flexibilitě a snadném použití, což vám umožňuje programově manipulovat s dokumenty aplikace Word, aniž byste na vašem počítači potřebovali nainstalovaný Microsoft Word. Nyní, když už umíte držet stoly pohromadě, prozkoumejte další funkce knihovny a posuňte své dovednosti ve zpracování dokumentů na další úroveň!

## FAQ

### Proč se moje tabulka po použití tohoto kódu stále láme na různých stránkách?

 Pokud se váš stůl stále láme, ujistěte se, že jste použili`KeepWithNext` vlastnost správně. Znovu zkontrolujte, že všechny odstavce kromě posledního v každé buňce mají tuto vlastnost nastavenou.

### Mohu mít pohromadě pouze určité řádky?

 Ano, můžete selektivně použít`KeepWithNext` vlastnost na konkrétní řádky nebo odstavce v tabulce, abyste mohli řídit, které části by měly zůstat pohromadě.

### Funguje tato metoda s velkými tabulkami?

velmi velkých tabulek je může Word stále rozdělit na stránky, pokud není dostatek místa, aby se celá tabulka vešla na jednu stránku. Zvažte úpravu formátování nebo okrajů tabulky tak, aby vyhovovala větším tabulkám.

### Mohu tuto metodu použít s jinými formáty dokumentů?

Ano! Aspose.Words for .NET podporuje mnoho formátů jako DOC, DOCX, PDF a další. Stejná metoda funguje ve všech formátech, které podporují tabulky.

### Je Aspose.Words for .NET bezplatná knihovna?

 Aspose.Words for .NET nabízí bezplatnou zkušební verzi, ale pro plný přístup ke všem funkcím si budete muset zakoupit licenci. Možnosti licencování můžete prozkoumat na[Aspose nákupní stránku](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
