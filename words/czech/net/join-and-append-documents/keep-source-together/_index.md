---
"description": "Naučte se, jak zabránit zalomení tabulek napříč stránkami pomocí Aspose.Words pro .NET v tomto podrobném návodu. Zajistěte úhledné a profesionálně vypadající dokumenty Wordu."
"linktitle": "Udržujte stůl pohromadě"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Udržujte stůl pohromadě"
"url": "/cs/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Udržujte stůl pohromadě

## Zavedení

Tabulky jsou nezbytnou součástí mnoha dokumentů Wordu, ale někdy se můžete setkat se situací, kdy se tabulka rozdělí na dvě stránky. To může narušit plynulost dokumentu a ovlivnit jeho čitelnost. Nebylo by hezké, kdyby existoval způsob, jak udržet celou tabulku pohromadě na jedné stránce? S Aspose.Words pro .NET existuje snadné řešení tohoto problému! V tomto tutoriálu si ukážeme, jak zabránit rozdělení tabulek napříč stránkami a zajistit, aby váš dokument vypadal úhledně a profesionálně.

## Předpoklady

Než se pustíme do tutoriálu, ujistěme se, že máte vše potřebné k hladkému průběhu.

### Knihovna Aspose.Words pro .NET

Nejprve budete potřebovat nainstalovaný Aspose.Words pro .NET. Jedná se o výkonnou knihovnu, která vám umožňuje programově pracovat s dokumenty Wordu.

- [Stáhněte si Aspose.Words pro .NET](https://releases.aspose.com/words/net/)

### Vývojové prostředí

Měli byste mít nastavené vývojové prostředí pro spouštění kódu C#, například:

- Visual Studio (libovolná novější verze)
- .NET Framework 2.0 nebo novější

### Dokument Wordu s tabulkou

Budete potřebovat dokument aplikace Word, který obsahuje tabulku. V tomto tutoriálu budeme pracovat s ukázkovým dokumentem s názvem `"Table spanning two pages.docx"`Tento soubor obsahuje tabulku, která aktuálně zabírá dvě stránky.

### Dočasná licence (volitelné)

I když Aspose.Words nabízí bezplatnou zkušební verzi, možná budete chtít použít [dočasná licence](https://purchase.aspose.com/temporary-license/) k uvolnění plného potenciálu knihovny.

## Importovat balíčky

Než začneme psát jakýkoli kód, musíme importovat potřebné jmenné prostory pro práci s Aspose.Words pro .NET. Na začátek souboru s kódem přidejte následující importy:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Tyto jmenné prostory vám poskytují přístup ke třídám jako `Document`, `Table`, `Cell`a další, které použijeme v tomto tutoriálu.

## Krok 1: Vložení dokumentu

První věc, kterou musíme udělat, je načíst dokument Wordu, který obsahuje tabulku. K tomu použijeme `Document` třída z Aspose.Words. Tato třída umožňuje programově otevírat a manipulovat se soubory Wordu.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

V tomto úryvku kódu určujeme umístění našeho dokumentu. Nahraďte `"YOUR DOCUMENTS DIRECTORY"` se skutečným adresářem, kde je váš dokument uložen.

## Krok 2: Přístup k tabulce

Jakmile je dokument načten, dalším krokem je přístup k tabulce, kterou chceme uchovat pohromadě. V tomto příkladu předpokládáme, že tabulka je první tabulkou v dokumentu.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Tento řádek kódu vyhledá první tabulku v dokumentu. `GetChild` metoda načte specifický typ uzlu, kterým je v tomto případě `NodeType.Table`Ten/Ta/To `0` označuje, že chceme první tabulku a `true` Příznak zajišťuje, že rekurzivně prohledáváme všechny podřízené uzly.

## Krok 3: Procházení buněk tabulky

Nyní musíme projít každou buňku v tabulce. Protože tabulka obsahuje více řádků a každý řádek obsahuje více buněk, projdeme každou buňku iterací a zajistíme, aby se tabulka nezalomila mezi stránkami.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

Zde, `GetChildNodes` načte všechny buňky v tabulce a každou z nich projdeme smyčkou. `EnsureMinimum()` Metoda zajišťuje, aby každá buňka obsahovala alespoň jeden odstavec, protože prázdná buňka by mohla později způsobit problémy.

## Krok 4: Nastavení vlastnosti KeepWithNext

Abychom zabránili rozdělování tabulky na stránky, musíme nastavit `KeepWithNext` pro každý odstavec v tabulce. Tato vlastnost zajišťuje, že odstavec zůstane u dalšího odstavce, čímž efektivně zabraňuje zalomení stránek mezi nimi.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

Tato smyčka kontroluje každý odstavec uvnitř každé buňky. Podmínka zajišťuje, že nepoužijeme `KeepWithNext` vlastnost na poslední odstavec v posledním řádku. Jinak by vlastnost neměla žádný účinek, protože neexistuje žádný další odstavec.

## Krok 5: Uložte dokument

Konečně, po aplikaci `KeepWithNext` vlastnost, musíme upravený dokument uložit.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Tento řádek uloží aktualizovaný dokument s novým názvem a zachová původní soubor. Nyní můžete otevřít výsledný soubor a uvidíte, že tabulka již není rozdělena na dvě stránky!

## Závěr

A tady to máte! Dodržováním těchto jednoduchých kroků můžete snadno zabránit zalomení tabulek napříč stránkami v dokumentech Word pomocí Aspose.Words pro .NET. Ať už pracujete na zprávách, smlouvách nebo jiných dokumentech, zachování tabulek beze změny zajistí elegantnější a profesionálnější vzhled.

Krása knihovny Aspose.Words spočívá v její flexibilitě a snadném použití, což vám umožňuje programově manipulovat s dokumenty Wordu, aniž byste museli mít na svém počítači nainstalovaný Microsoft Word. Nyní, když jste se naučili uchovávat tabulky, prozkoumejte další funkce knihovny a posuňte své dovednosti v oblasti zpracování dokumentů na další úroveň!

## Často kladené otázky

### Proč se mi tabulka i po použití tohoto kódu stále rozděluje na stránky?

Pokud se vám stůl stále láme, ujistěte se, že jste použili `KeepWithNext` vlastnost správně. Zkontrolujte, zda všechny odstavce v každé buňce kromě posledního mají tuto vlastnost nastavenou.

### Mohu pohromadě uchovávat pouze určité řádky?

Ano, můžete selektivně aplikovat `KeepWithNext` vlastnost pro konkrétní řádky nebo odstavce v tabulce, abyste určili, které části by měly zůstat pohromadě.

### Funguje tato metoda s velkými tabulkami?

U velmi velkých tabulek může Word stále rozdělit tabulky na stránky, pokud není dostatek místa pro umístění celé tabulky na jednu stránku. Zvažte úpravu formátování nebo okrajů tabulky tak, aby se do ní vešly i větší tabulky.

### Mohu tuto metodu použít s jinými formáty dokumentů?

Ano! Aspose.Words pro .NET podporuje mnoho formátů, jako například DOC, DOCX, PDF a další. Stejná metoda funguje ve všech formátech, které podporují tabulky.

### Je Aspose.Words pro .NET bezplatná knihovna?

Aspose.Words pro .NET nabízí bezplatnou zkušební verzi, ale pro plný přístup ke všem funkcím si budete muset zakoupit licenci. Možnosti licencování si můžete prohlédnout na [Nákupní stránka Aspose](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}