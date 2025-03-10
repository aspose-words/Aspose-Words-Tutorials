---
title: Vložit dokument při nahrazení
linktitle: Vložit dokument při nahrazení
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak bezproblémově vložit jeden dokument Wordu do druhého pomocí Aspose.Words for .NET s naším podrobným průvodcem krok za krokem. Ideální pro vývojáře, kteří chtějí zefektivnit zpracování dokumentů.
weight: 10
url: /cs/net/clone-and-combine-documents/insert-document-at-replace/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit dokument při nahrazení

## Zavedení

Ahoj, mistři dokumentů! Přistihli jste se někdy po kolena v kódu a snažili se přijít na to, jak hladce vložit jeden dokument Wordu do druhého? Nebojte se, protože dnes se ponoříme do světa Aspose.Words pro .NET, abychom tento úkol usnadnili. Projdeme si podrobným průvodcem krok za krokem, jak používat tuto výkonnou knihovnu k vkládání dokumentů do konkrétních bodů během operace hledání a nahrazení. Jste připraveni stát se průvodcem Aspose.Words? Začněme!

## Předpoklady

Než se pustíme do kódu, je třeba mít připraveno několik věcí:

-  Visual Studio: Ujistěte se, že máte na svém počítači nainstalované Visual Studio. Pokud ji ještě nemáte, můžete si ji stáhnout z[zde](https://visualstudio.microsoft.com/).
-  Aspose.Words for .NET: Budete potřebovat knihovnu Aspose.Words. Můžete to získat z[Aspose webové stránky](https://releases.aspose.com/words/net/).
- Základní znalosti C#: Základní znalost C# a .NET vám pomůže pokračovat v tomto tutoriálu.

Dobře, s těmi z cesty, pojďme si ušpinit ruce nějakým kódem!

## Importovat jmenné prostory

Nejprve musíme importovat potřebné jmenné prostory pro práci s Aspose.Words. Je to jako shromáždit všechny své nástroje před zahájením projektu. Přidejte je pomocí direktiv v horní části souboru C#:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Nyní, když máme připraveny naše předpoklady, pojďme si celý proces rozdělit na malé kroky. Každý krok je zásadní a přiblíží nás k našemu cíli.

## Krok 1: Nastavení adresáře dokumentů

Nejprve musíme určit adresář, kde jsou naše dokumenty uloženy. Je to jako připravit jeviště před velkým představením.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` s cestou k vašemu adresáři. Tady budou vaše dokumenty žít a dýchat.

## Krok 2: Vložte hlavní dokument

Dále načteme hlavní dokument, do kterého chceme vložit další dokument. Berte to jako naši hlavní scénu, kde se bude odehrávat veškerá akce.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Tento kód načte hlavní dokument ze zadaného adresáře.

## Krok 3: Nastavte možnosti Najít a nahradit

vyhledání konkrétního umístění, kam chceme vložit náš dokument, používáme funkci najít a nahradit. Je to jako pomocí mapy najít přesné místo pro náš nový přírůstek.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Zde nastavujeme směr zpět a určujeme vlastní obsluhu zpětného volání, kterou definujeme dále.

## Krok 4: Proveďte operaci výměny

Nyní řekneme našemu hlavnímu dokumentu, aby hledal konkrétní zástupný text a nenahradil jej ničím, přičemž k vložení jiného dokumentu použijeme naše vlastní zpětné volání.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Tento kód provede operaci najít a nahradit a poté uloží aktualizovaný dokument.

## Krok 5: Vytvořte vlastní obslužnou rutinu zpětného volání nahrazující

Naše vlastní obsluha zpětného volání je místo, kde se kouzlo odehrává. Tento obslužný program definuje, jak se provádí vkládání dokumentu během operace hledání a nahrazení.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Vložte dokument za odstavec obsahující odpovídající text.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Odstraňte odstavec s odpovídajícím textem.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Zde načteme dokument, který se má vložit, a poté zavoláme pomocnou metodu, která vložení provede.

## Krok 6: Definujte metodu vložení dokumentu

Posledním kouskem naší skládačky je metoda, která skutečně vloží dokument na určené místo.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Zkontrolujte, zda je cílem vložení odstavec nebo tabulka
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Vytvořte NodeImporter pro import uzlů ze zdrojového dokumentu
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Projděte všechny uzly na úrovni bloku v částech zdrojového dokumentu
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Přeskočte poslední prázdný odstavec oddílu
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Importujte a vložte uzel do cíle
                Node newNode = importer.ImportNode(srcNode, true);
                destinationParent.InsertAfter(newNode, insertionDestination);
                insertionDestination = newNode;
            }
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}

```

Tato metoda se stará o import uzlů z vkládaného dokumentu a jejich umístění na správné místo v hlavním dokumentu.

## Závěr

tady to máte! Komplexní průvodce vkládáním jednoho dokumentu do druhého pomocí Aspose.Words pro .NET. Pomocí těchto kroků můžete snadno automatizovat úlohy sestavování dokumentů a manipulace s nimi. Ať už budujete systém správy dokumentů nebo jen potřebujete zefektivnit pracovní tok zpracování dokumentů, Aspose.Words je vaším spolehlivým pomocníkem.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro programovou manipulaci s dokumenty Wordu. Umožňuje vám snadno vytvářet, upravovat, převádět a zpracovávat dokumenty aplikace Word.

### Mohu vložit více dokumentů najednou?
Ano, obslužnou rutinu zpětného volání můžete upravit tak, aby zvládla více vkládání iterací přes kolekci dokumentů.

### Je k dispozici bezplatná zkušební verze?
 Absolutně! Bezplatnou zkušební verzi si můžete stáhnout z[zde](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Words?
 Podporu můžete získat návštěvou stránky[Fórum Aspose.Words](https://forum.aspose.com/c/words/8).

### Mohu zachovat formátování vloženého dokumentu?
 Ano,`NodeImporter` třída umožňuje určit, jak se bude pracovat s formátováním při importu uzlů z jednoho dokumentu do druhého.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
