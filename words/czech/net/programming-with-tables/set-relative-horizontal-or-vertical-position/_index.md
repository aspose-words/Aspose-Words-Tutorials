---
"description": "Naučte se, jak nastavit relativní horizontální a vertikální pozice tabulek v dokumentech Word pomocí Aspose.Words pro .NET v tomto podrobném návodu."
"linktitle": "Nastavení relativní horizontální nebo vertikální polohy"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení relativní horizontální nebo vertikální polohy"
"url": "/cs/net/programming-with-tables/set-relative-horizontal-or-vertical-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení relativní horizontální nebo vertikální polohy

## Zavedení

Už jste si někdy lámali hlavu s tím, jak umístit tabulky ve vašich dokumentech Word přesně tak, jak chcete? Nejste sami. Ať už vytváříte profesionální zprávu nebo stylovou brožuru, zarovnání tabulek může mít obrovský význam. A právě v tom se hodí Aspose.Words pro .NET. Tento tutoriál vás krok za krokem provede nastavením relativní horizontální nebo vertikální pozice tabulek ve vašich dokumentech Word. Pojďme se na to pustit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Pokud jste tak ještě neučinili, můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE kompatibilní s .NET.
3. Základní znalost jazyka C#: Tento tutoriál předpokládá, že jste obeznámeni se základy programování v jazyce C#.

## Importovat jmenné prostory

Nejdříve je potřeba importovat potřebné jmenné prostory. To je nezbytné pro přístup k funkcím Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Krok 1: Vložte dokument

Chcete-li začít, budete muset načíst dokument Word do programu. Zde je návod, jak to udělat:

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Tento úryvek kódu nastaví cestu k adresáři s dokumenty a načte konkrétní dokument, se kterým chcete pracovat. Abyste předešli problémům s načítáním, ujistěte se, že je cesta k dokumentu správná.

## Krok 2: Přístup k tabulce

Dále potřebujeme přistupovat k tabulce v dokumentu. Obvykle byste chtěli pracovat s první tabulkou v části těla.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Tento řádek kódu načte první tabulku z těla dokumentu. Pokud váš dokument obsahuje více tabulek, můžete index odpovídajícím způsobem upravit.

## Krok 3: Nastavení horizontální polohy

Nyní nastavme horizontální polohu tabulky vzhledem ke konkrétnímu prvku. V tomto příkladu ji umístíme vzhledem ke sloupci.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

Nastavením `HorizontalAnchor` na `RelativeHorizontalPosition.Column`, říkáte tabulce, aby se zarovnala vodorovně vzhledem ke sloupci, ve kterém se nachází.

## Krok 4: Nastavení svislé polohy

Podobně jako u horizontálního umístění můžete nastavit i vertikální umístění. Zde jej umístíme vzhledem ke stránce.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

Nastavení `VerticalAnchor` na `RelativeVerticalPosition.Page` zajišťuje, že tabulka je svisle zarovnána podle stránky.

## Krok 5: Uložte dokument

Nakonec uložte změny do nového dokumentu. Toto je klíčový krok k zajištění zachování změn.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Tento příkaz uloží upravený dokument pod novým názvem, čímž zajistí, že nepřepíšete původní soubor.

## Závěr

A tady to máte! Úspěšně jste nastavili relativní horizontální a vertikální pozice tabulky v dokumentu Word pomocí Aspose.Words pro .NET. S touto nově nabytou dovedností můžete vylepšit rozvržení a čitelnost svých dokumentů, aby vypadaly profesionálněji a elegantněji. Experimentujte s různými pozicemi a zjistěte, co nejlépe vyhovuje vašim potřebám.

## Často kladené otázky

### Mohu umístit tabulky vzhledem k ostatním prvkům?  
Ano, Aspose.Words umožňuje umisťovat tabulky vzhledem k různým prvkům, jako jsou okraje, stránky, sloupce a další.

### Potřebuji licenci k používání Aspose.Words pro .NET?  
Ano, můžete si zakoupit licenci [zde](https://purchase.aspose.com/buy) nebo si pořídit dočasný řidičský průkaz [zde](https://purchase.aspose.com/temporary-license/).

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?  
Rozhodně! Můžete si stáhnout bezplatnou zkušební verzi [zde](https://releases.aspose.com/).

### Mohu používat Aspose.Words s jinými programovacími jazyky?  
Aspose.Words je primárně navržen pro .NET, ale existují verze pro Javu, Python a další platformy.

### Kde najdu podrobnější dokumentaci?  
Pro podrobnější informace se podívejte do dokumentace k Aspose.Words. [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}