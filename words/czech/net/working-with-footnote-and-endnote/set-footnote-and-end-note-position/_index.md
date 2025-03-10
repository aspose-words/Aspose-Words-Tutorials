---
title: Nastavte pozici poznámky pod čarou a vysvětlivky
linktitle: Nastavit pozici poznámky pod čarou a konec poznámky
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit pozice poznámek pod čarou a vysvětlivky v dokumentech aplikace Word pomocí Aspose.Words for .NET pomocí tohoto podrobného průvodce krok za krokem.
weight: 10
url: /cs/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavte pozici poznámky pod čarou a vysvětlivky

## Zavedení

Pokud pracujete s dokumenty aplikace Word a potřebujete efektivně spravovat poznámky pod čarou a vysvětlivky, Aspose.Words for .NET je vaše oblíbená knihovna. Tento tutoriál vás provede nastavením pozic poznámek pod čarou a vysvětlivky v dokumentu aplikace Word pomocí Aspose.Words for .NET. Každý krok rozebereme, aby se dal snadno sledovat a implementovat.

## Předpoklady

Než se pustíte do výukového programu, ujistěte se, že máte následující:

-  Aspose.Words for .NET Library: Můžete si ji stáhnout z[zde](https://releases.aspose.com/words/net/).
- Visual Studio: Jakákoli nejnovější verze bude fungovat dobře.
- Základní znalost C#: Pochopení základů vám pomůže snadno pokračovat.

## Importovat jmenné prostory

Nejprve importujte potřebné jmenné prostory do svého projektu C#:

```csharp
using System;
using Aspose.Words;
```

## Krok 1: Načtěte dokument aplikace Word

Chcete-li začít, musíte načíst dokument aplikace Word do objektu Aspose.Words Document. To vám umožní manipulovat s obsahem dokumentu.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 tomto kódu nahraďte`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde se váš dokument nachází.

## Krok 2: Nastavte pozici poznámky pod čarou

Dále nastavíte polohu poznámek pod čarou. Aspose.Words for .NET umožňuje umístit poznámky pod čarou buď na konec stránky, nebo pod text.

```csharp
doc.FootnoteOptions.Position = FootnotePosition.BeneathText;
```

 Zde jsme nastavili, aby se poznámky pod čarou zobrazovaly pod textem. Pokud je preferujete na konci stránky, použijte`FootnotePosition.BottomOfPage`.

## Krok 3: Nastavte pozici koncové poznámky

Podobně můžete nastavit polohu vysvětlivek. Vysvětlivky lze umístit buď na konec oddílu, nebo na konec dokumentu.

```csharp
doc.EndnoteOptions.Position = EndnotePosition.EndOfSection;
```

 V tomto příkladu jsou vysvětlivky umístěny na konci každého oddílu. Chcete-li je umístit na konec dokumentu, použijte`EndnotePosition.EndOfDocument`.

## Krok 4: Uložte dokument

Nakonec dokument uložte, abyste použili změny. Ujistěte se, že jste zadali správnou cestu k souboru a název výstupního dokumentu.

```csharp
doc.Save(dataDir + "WorkingWithFootnotes.SetFootnoteAndEndNotePosition.docx");
```

Tento řádek uloží upravený dokument do určeného adresáře.

## Závěr

Nastavení pozic poznámek pod čarou a vysvětlivky v dokumentech aplikace Word pomocí Aspose.Words pro .NET je jednoduché, jakmile znáte kroky. Podle této příručky můžete upravit své dokumenty tak, aby vyhovovaly vašim potřebám, a zajistit, aby byly poznámky pod čarou a vysvětlivky umístěny přesně tam, kde je chcete.

## FAQ

### Mohu nastavit různé pozice pro jednotlivé poznámky pod čarou nebo vysvětlivky?

Ne, Aspose.Words for .NET nastavuje pozici pro všechny poznámky pod čarou a vysvětlivky v dokumentu jednotně.

### Je Aspose.Words for .NET kompatibilní se všemi verzemi dokumentů aplikace Word?

Ano, Aspose.Words for .NET podporuje širokou škálu formátů dokumentů Word, včetně DOC, DOCX, RTF a dalších.

### Mohu používat Aspose.Words pro .NET s jinými programovacími jazyky?

Aspose.Words for .NET je navržen pro aplikace .NET, ale můžete jej použít s jakýmkoli jazykem podporovaným .NET, jako je C#, VB.NET atd.

### Je k dispozici bezplatná zkušební verze pro Aspose.Words pro .NET?

 Ano, můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?

 K dispozici je podrobná dokumentace[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
