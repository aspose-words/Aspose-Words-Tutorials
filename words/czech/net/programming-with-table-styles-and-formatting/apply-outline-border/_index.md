---
"description": "Naučte se, jak v aplikaci Word použít ohraničení tabulky pomocí nástroje Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu pro perfektní formátování tabulky."
"linktitle": "Použít obrysový okraj"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Použít obrysový okraj"
"url": "/cs/net/programming-with-table-styles-and-formatting/apply-outline-border/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Použít obrysový okraj

## Zavedení

dnešním tutoriálu se ponoříme do světa manipulace s dokumenty pomocí Aspose.Words pro .NET. Konkrétně se naučíme, jak v dokumentu Wordu použít ohraničení tabulky. Pokud často pracujete s automatickým generováním a formátováním dokumentů, je to fantastická dovednost, kterou byste měli mít ve své sadě nástrojů. Pojďme se tedy na tuto cestu k tomu, aby vaše tabulky byly nejen funkční, ale i vizuálně přitažlivé.

## Předpoklady

Než se pustíme do kódu, je tu pár věcí, které budete potřebovat:

1. Aspose.Words pro .NET: Musíte mít nainstalovaný Aspose.Words pro .NET. Můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Vhodné vývojové prostředí, jako je Visual Studio.
3. Základní znalost jazyka C#: Základní znalost jazyka C# vám pomůže s plněním úkolů v tutoriálu.

## Importovat jmenné prostory

Nejprve se ujistěte, že máte importované potřebné jmenné prostory. To je klíčové pro přístup k funkcím Aspose.Words.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Rozdělme si proces na jednoduché a zvládnutelné kroky.

## Krok 1: Vložení dokumentu

Nejprve musíme načíst dokument Wordu, který obsahuje tabulku, kterou chceme formátovat.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

V tomto kroku používáme `Document` třída z Aspose.Words pro načtení existujícího dokumentu. Nahraďte `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde je váš dokument uložen.

## Krok 2: Přístup k tabulce

Dále potřebujeme přístup ke konkrétní tabulce, kterou chceme formátovat. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

Zde, `GetChild` Metoda načte první tabulku v dokumentu. Parametry `NodeType.Table, 0, true` ujistíme se, že získáme správný typ uzlu.

## Krok 3: Zarovnání tabulky

Nyní zarovnáme tabulku na stránce na střed.

```csharp
table.Alignment = TableAlignment.Center;
```

Tento krok zajišťuje, že stůl je úhledně vystředěný a dodává mu profesionální vzhled.

## Krok 4: Vymazání stávajících okrajů

Než naneseme nové ohraničení, musíme vyčistit všechny stávající.

```csharp
table.ClearBorders();
```

Vyčištění okrajů zajišťuje, že naše nové okraje budou aplikovány čistě, aniž by do nich zasahovaly staré styly.

## Krok 5: Nastavení obrysových ohraničení

Nyní na tabulku aplikujme zelené obrysové ohraničení.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

Každý typ ohraničení (levý, pravý, horní, dolní) se nastavuje individuálně. Používáme `LineStyle.Single` pro plnou čáru, `1.5` pro šířku čáry a `Color.Green` pro barvu okraje.

## Krok 6: Použití stínování buněk

Aby byla tabulka vizuálně atraktivnější, vyplňme buňky světle zelenou barvou.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

Zde, `SetShading` se používá k nanesení plné světle zelené barvy na buňky, čímž tabulka vynikne.

## Krok 7: Uložte dokument

Nakonec upravený dokument uložte.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Tento krok uloží dokument s použitým formátováním. Můžete jej otevřít a zobrazit si krásně naformátovanou tabulku.

## Závěr

máte to! Pomocí těchto kroků jste úspěšně použili obrysový okraj na tabulku v dokumentu Word pomocí Aspose.Words pro .NET. Tento tutoriál se zabýval načtením dokumentu, přístupem k tabulce, jejím zarovnáním, vyčištěním stávajících okrajů, použitím nových okrajů, přidáním stínování buněk a nakonec uložením dokumentu. 

S těmito dovednostmi můžete vylepšit vizuální prezentaci vašich tabulek, čímž se vaše dokumenty stanou profesionálnějšími a atraktivnějšími. Šťastné programování!

## Často kladené otázky

### Mohu na každý okraj tabulky použít různé styly?  
Ano, na každý okraj můžete použít různé styly a barvy úpravou parametrů v `SetBorder` metoda.

### Jak mohu změnit šířku ohraničení?  
Šířku můžete změnit úpravou třetího parametru v `SetBorder` metoda. Například, `1.5` nastavuje šířku 1,5 bodu.

### Je možné aplikovat stínování na jednotlivé buňky?  
Ano, stínování můžete použít na jednotlivé buňky tak, že k jednotlivým buňkám přistoupíte a použijete `SetShading` metoda.

### Mohu použít jiné barvy pro ohraničení a stínování?  
Rozhodně! Můžete použít jakoukoli barvu dostupnou v `System.Drawing.Color` třída.

### Jak zarovnám tabulku vodorovně na střed?  
Ten/Ta/To `table.Alignment = TableAlignment.Center;` řádek v kódu vycentruje tabulku vodorovně na stránce.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}