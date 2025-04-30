---
"description": "Naučte se, jak nastavit pozice poznámek pod čarou a koncových poznámek v dokumentech Word pomocí Aspose.Words pro .NET s tímto podrobným návodem krok za krokem."
"linktitle": "Nastavení pozice poznámky pod čarou a koncové poznámky"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Nastavení pozice poznámky pod čarou a poznámky na konci"
"url": "/cs/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení pozice poznámky pod čarou a poznámky na konci

## Zavedení

Pokud pracujete s dokumenty Wordu a potřebujete efektivně spravovat poznámky pod čarou a koncové poznámky, Aspose.Words pro .NET je vaše oblíbená knihovna. Tento tutoriál vás provede nastavením pozic poznámek pod čarou a koncových poznámek v dokumentu Wordu pomocí Aspose.Words pro .NET. Rozebereme si jednotlivé kroky, aby se snadno sledovaly a implementovaly.

## Předpoklady

Než se pustíte do tutoriálu, ujistěte se, že máte následující:

- Knihovna Aspose.Words pro .NET: Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/net/).
- Visual Studio: Jakákoli novější verze bude fungovat dobře.
- Základní znalost C#: Pochopení základů vám pomůže snadno se orientovat.

## Importovat jmenné prostory

Nejprve importujte potřebné jmenné prostory do svého projektu C#:

```csharp
using System;
using Aspose.Words;
```

## Krok 1: Načtěte dokument Wordu

Nejprve je třeba načíst dokument aplikace Word do objektu Aspose.Words Document. To vám umožní manipulovat s obsahem dokumentu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

V tomto kódu nahraďte `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde se váš dokument nachází.

## Krok 2: Nastavení pozice poznámky pod čarou

Dále nastavíte umístění poznámek pod čarou. Aspose.Words pro .NET umožňuje umístit poznámky pod čarou buď do dolní části stránky, nebo pod text.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

Zde jsme nastavili, aby se poznámky pod čarou zobrazovaly pod textem. Pokud je chcete mít ve spodní části stránky, použijte `FootnotePosition.BottomOfPage`.

## Krok 3: Nastavení pozice koncové poznámky

Podobně můžete nastavit umístění koncových poznámek. Koncové poznámky lze umístit buď na konec sekce, nebo na konec dokumentu.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

V tomto příkladu jsou poznámky na konci každé sekce umístěny na konci. Chcete-li je umístit na konec dokumentu, použijte `EndnotePosition.EndOfDocument`.

## Krok 4: Uložte dokument

Nakonec dokument uložte, aby se změny projevily. Ujistěte se, že jste zadali správnou cestu k souboru a název výstupního dokumentu.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Tento řádek uloží upravený dokument do vámi zadaného adresáře.

## Závěr

Nastavení pozic poznámek pod čarou a koncových poznámek v dokumentech Wordu pomocí Aspose.Words pro .NET je jednoduché, jakmile znáte jednotlivé kroky. Dodržováním tohoto návodu si můžete přizpůsobit dokumenty svým potřebám a zajistit, aby poznámky pod čarou a koncové poznámky byly umístěny přesně tam, kde je chcete.

## Často kladené otázky

### Mohu nastavit různé pozice pro jednotlivé poznámky pod čarou nebo vysvětlivky?

Ne, Aspose.Words pro .NET nastavuje pozici všech poznámek pod čarou a vysvětlivek v dokumentu jednotně.

### Je Aspose.Words pro .NET kompatibilní se všemi verzemi dokumentů Wordu?

Ano, Aspose.Words pro .NET podporuje širokou škálu formátů dokumentů Word, včetně DOC, DOCX, RTF a dalších.

### Mohu používat Aspose.Words pro .NET s jinými programovacími jazyky?

Aspose.Words pro .NET je určen pro .NET aplikace, ale můžete ho použít s jakýmkoli jazykem podporovaným .NET, jako je C#, VB.NET atd.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?

Ano, můžete získat bezplatnou zkušební verzi [zde](https://releases.aspose.com/).

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?

Podrobná dokumentace je k dispozici [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}