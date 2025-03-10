---
title: Změnit zarážky tabulátoru obsahu v dokumentu aplikace Word
linktitle: Změnit zarážky tabulátoru obsahu v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Přečtěte si, jak změnit zarážky tabulátoru obsahu v dokumentech aplikace Word pomocí Aspose.Words for .NET. Tento podrobný průvodce vám pomůže vytvořit profesionálně vypadající obsah.
weight: 10
url: /cs/net/programming-with-table-of-content/change-toc-tab-stops/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Změnit zarážky tabulátoru obsahu v dokumentu aplikace Word

## Zavedení

Přemýšleli jste někdy, jak oživit obsah (TOC) v dokumentech aplikace Word? Možná chcete, aby zarážky tabulátoru dokonale zapadaly do profesionálního vzhledu. Jste na správném místě! Dnes se ponoříme hluboko do toho, jak můžete změnit zarážky TOC pomocí Aspose.Words pro .NET. Držte se a slibuji, že odejdete s veškerým know-how, aby váš TOC vypadal elegantně a úhledně.

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words pro .NET: Můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli IDE kompatibilní s C#.
3. Dokument aplikace Word: Konkrétně takový, který obsahuje TOC.

Máš to všechno? Děsivý! Pojďme válet.

## Importovat jmenné prostory

Nejprve budete muset importovat potřebné jmenné prostory. Je to jako sbalit si nástroje před zahájením projektu.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Pojďme si tento proces rozebrat do jednoduchých, stravitelných kroků. Projdeme načtením dokumentu, úpravou zarážek záložky TOC a uložením aktualizovaného dokumentu.

## Krok 1: Vložte dokument

Proč? Potřebujeme získat přístup k dokumentu aplikace Word, který obsahuje obsah, který chceme upravit.

Jak? Zde je jednoduchý úryvek kódu, který vám pomůže začít:

```csharp
// Cesta k adresáři vašich dokumentů
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Vložte dokument obsahující obsah
Document doc = new Document(dataDir + "Table of contents.docx");
```

Představte si, že váš dokument je jako dort a my se chystáme přidat trochu polevy. Prvním krokem je dostat ten dort z krabice.

## Krok 2: Identifikujte odstavce TOC

Proč? Musíme přesně určit odstavce, které tvoří TOC. 

Jak? Projděte si odstavce a zkontrolujte jejich styly:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        // Byl nalezen odstavec TOC
    }
}
```

Berte to jako skenování davu, abyste našli své přátele. Zde hledáme odstavce stylizované jako položky obsahu.

## Krok 3: Upravte zarážky tabulátoru

Proč? Tady se děje kouzlo. Výměna zarážek dává vašemu obsahu čistší vzhled.

Jak? Odeberte stávající zarážku tabulátoru a přidejte novou na změněné místo:

```csharp
foreach(Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.Style.StyleIdentifier >= StyleIdentifier.Toc1 &&
        para.ParagraphFormat.Style.StyleIdentifier <= StyleIdentifier.Toc9)
    {
        TabStop tab = para.ParagraphFormat.TabStops[0];
        para.ParagraphFormat.TabStops.RemoveByPosition(tab.Position);
        para.ParagraphFormat.TabStops.Add(tab.Position - 50, tab.Alignment, tab.Leader);
    }
}
```

Je to jako upravovat nábytek v obývacím pokoji, dokud vám to nebude vyhovovat. Tyto zarážky vylepšujeme k dokonalosti.

## Krok 4: Uložte upravený dokument

Proč? Aby bylo zajištěno, že veškerá vaše tvrdá práce bude uložena a bude možné ji prohlížet nebo sdílet.

Jak? Uložte dokument pod novým názvem, aby původní zůstal nedotčený:

```csharp
// Uložte upravený dokument
doc.Save(dataDir + "WorkingWithTableOfContent.ChangeTocTabStops.docx");
```

A voila! Váš obsah má nyní zarážky tabulátoru přesně tam, kde je chcete.

## Závěr

Změna zarážek tabulátoru obsahu v dokumentu aplikace Word pomocí Aspose.Words for .NET je jednoduchá, jakmile to rozeberete. Načtením dokumentu, identifikací odstavců obsahu, úpravou zarážek tabulátoru a uložením dokumentu můžete dosáhnout uhlazeného a profesionálního vzhledu. Pamatujte, že cvičení dělá mistra, takže pokračujte v experimentování s různými pozicemi zarážek tabulátoru, abyste získali přesné rozložení, které si přejete.

## FAQ

### Mohu upravit zarážky tabulátoru pro různé úrovně obsahu samostatně?
Ano, můžete! Stačí zkontrolovat každou konkrétní úroveň TOC (Toc1, Toc2 atd.) a podle toho upravit.

### Co když má můj dokument více obsahu?
Kód vyhledá všechny odstavce ve stylu TOC, takže změní všechny TOC přítomné v dokumentu.

### Je možné přidat více zarážek tabulátoru do položky TOC?
 Absolutně! Úpravou tabulátoru můžete přidat libovolný počet zarážek tabulátoru`para.ParagraphFormat.TabStops` sbírka.

### Mohu změnit zarovnání zarážky tabulátoru a styl odkazu?
Ano, při přidávání nové zarážky tabulátoru můžete určit různé zarovnání a styly odkazu.

### Potřebuji licenci k používání Aspose.Words pro .NET?
 Ano, k používání Aspose.Words for .NET po zkušební době potřebujete platnou licenci. Můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/) nebo[koupit jeden](https://purchase.aspose.com/buy).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
