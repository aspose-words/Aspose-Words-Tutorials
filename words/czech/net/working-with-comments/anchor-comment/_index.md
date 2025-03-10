---
title: Komentář kotvy
linktitle: Komentář kotvy
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se přidávat kotvící komentáře do dokumentů aplikace Word pomocí Aspose.Words for .NET. Postupujte podle našeho podrobného průvodce pro efektivní spolupráci na dokumentech.
weight: 10
url: /cs/net/working-with-comments/anchor-comment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Komentář kotvy

## Zavedení

Ocitli jste se někdy v situaci, kdy jste potřebovali programově přidávat komentáře ke konkrétním textovým oddílům v dokumentu aplikace Word? Představte si, že spolupracujete na dokumentu se svým týmem a potřebujete zvýraznit určité části komentáři, aby je ostatní mohli zkontrolovat. V tomto tutoriálu se ponoříme hluboko do toho, jak vkládat kotvící komentáře do dokumentů aplikace Word pomocí Aspose.Words for .NET. Tento proces rozdělíme do jednoduchých kroků, abyste jej mohli snadno sledovat a implementovat do svých projektů.

## Předpoklady

Než začneme, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Jakékoli vývojové prostředí .NET, jako je Visual Studio.
- Základní porozumění C#: Znalost programování C# vám pomůže snadno postupovat podle kroků.

Nyní se pojďme ponořit do jmenných prostorů, které budete muset pro tento úkol importovat.

## Importovat jmenné prostory

Nejprve se ujistěte, že jste do projektu importovali potřebné jmenné prostory. Zde jsou požadované jmenné prostory:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.CommentRangeStart;
using Aspose.Words.CommentRangeEnd;
```

předpoklady a jmennými prostory z cesty, pojďme k zábavnější části: rozebrání procesu krok za krokem.

## Krok 1: Vytvořte nový dokument

Nejprve vytvořte nový dokument aplikace Word. To bude sloužit jako plátno pro naše komentáře.

```csharp
// Definujte adresář, do kterého bude dokument uložen
string dataDir = "YOUR DOCUMENT DIRECTORY";        

// Vytvořte instanci třídy Document
Document doc = new Document();
```

 V tomto kroku inicializujeme nový`Document` objekt, který bude použit k přidání našich komentářů.

## Krok 2: Přidejte text do dokumentu

Dále do dokumentu přidáme nějaký text. Tento text bude cílem našich komentářů.

```csharp
// Vytvořte první odstavec a spustí se
Paragraph para1 = new Paragraph(doc);
Run run1 = new Run(doc, "Some ");
Run run2 = new Run(doc, "text ");
para1.AppendChild(run1);
para1.AppendChild(run2);
doc.FirstSection.Body.AppendChild(para1);

// Vytvořte druhý odstavec a spustí se
Paragraph para2 = new Paragraph(doc);
Run run3 = new Run(doc, "is ");
Run run4 = new Run(doc, "added ");
para2.AppendChild(run3);
para2.AppendChild(run4);
doc.FirstSection.Body.AppendChild(para2);
```

 Zde vytvoříme dva odstavce s nějakým textem. Každý text je zapouzdřen v a`Run` objekt, který se pak přidá do odstavců.

## Krok 3: Vytvořte komentář

Nyní vytvoříme komentář, který připojíme k našemu textu.

```csharp
// Vytvořte nový komentář
Comment comment = new Comment(doc, "Awais Hafeez", "AH", DateTime.Today);
comment.SetText("Comment text.");
```

 V tomto kroku vytvoříme a`Comment` objekt a přidejte odstavec a běh s textem komentáře.

## Krok 4: Definujte rozsah komentářů

Pro ukotvení komentáře ke konkrétnímu textu musíme definovat začátek a konec rozsahu komentáře.

```csharp
// Definujte CommentRangeStart a CommentRangeEnd
CommentRangeStart commentRangeStart = new CommentRangeStart(doc, comment.Id);
CommentRangeEnd commentRangeEnd = new CommentRangeEnd(doc, comment.Id);

// Vložte CommentRangeStart a CommentRangeEnd do dokumentu
run1.ParentNode.InsertAfter(commentRangeStart, run1);
run3.ParentNode.InsertAfter(commentRangeEnd, run3);

// Přidejte komentář k dokumentu
commentRangeEnd.ParentNode.InsertAfter(comment, commentRangeEnd);
```

 Tady tvoříme`CommentRangeStart` a`CommentRangeEnd` objekty a spojí je s komentářem pomocí jeho ID. Tyto rozsahy pak vložíme do dokumentu, čímž efektivně ukotvíme náš komentář k zadanému textu.

## Krok 5: Uložte dokument

Nakonec uložme náš dokument do zadaného adresáře.

```csharp
// Uložte dokument
doc.Save(dataDir + "WorkingWithComments.AnchorComment.doc");
```

Tento krok uloží dokument s ukotveným komentářem do vámi zadaného adresáře.

## Závěr

A tady to máte! Úspěšně jste se naučili, jak přidávat kotvící komentáře ke konkrétním textovým oddílům v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato technika je neuvěřitelně užitečná pro spolupráci na dokumentech, umožňuje vám snadno zvýrazňovat a komentovat konkrétní části textu. Ať už pracujete na projektu se svým týmem nebo kontrolujete dokumenty, tato metoda zvýší vaši produktivitu a zefektivní váš pracovní postup.

## FAQ

### Jaký je účel použití kotevních komentářů v dokumentech aplikace Word?
Kotevní komentáře se používají ke zvýraznění a komentování konkrétních částí textu, což usnadňuje poskytování zpětné vazby a spolupráci na dokumentech.

### Mohu přidat více komentářů do stejné textové části?
Ano, do stejné textové části můžete přidat více komentářů definováním více rozsahů komentářů.

### Je Aspose.Words for .NET zdarma k použití?
 Aspose.Words for .NET nabízí bezplatnou zkušební verzi, kterou si můžete stáhnout[zde](https://releases.aspose.com/) . Pro plné funkce si můžete zakoupit licenci[zde](https://purchase.aspose.com/buy).

### Mohu upravit vzhled komentářů?
Zatímco Aspose.Words se zaměřuje na funkčnost, vzhled komentářů v dokumentech Wordu je obecně řízen samotným Wordem.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
 Můžete najít podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
