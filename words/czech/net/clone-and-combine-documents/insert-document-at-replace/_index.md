---
"description": "Naučte se, jak bez problémů vkládat jeden dokument Wordu do druhého pomocí Aspose.Words pro .NET s naším podrobným návodem krok za krokem. Ideální pro vývojáře, kteří chtějí zefektivnit zpracování dokumentů."
"linktitle": "Vložit dokument na místo nahrazení"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložit dokument na místo nahrazení"
"url": "/cs/net/clone-and-combine-documents/insert-document-at-replace/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložit dokument na místo nahrazení

## Zavedení

Ahoj, mistři dokumentů! Už jste se někdy ocitli po kolena v kódu a snažili se přijít na to, jak bez problémů vložit jeden dokument Wordu do druhého? Nebojte se, protože dnes se ponoříme do světa Aspose.Words pro .NET, abychom vám tento úkol usnadnili. Projdeme si podrobným návodem krok za krokem, jak používat tuto výkonnou knihovnu k vkládání dokumentů na konkrétní místa během operace hledání a nahrazování. Jste připraveni stát se průvodcem Aspose.Words? Pojďme na to!

## Předpoklady

Než se pustíme do samotného kódu, je potřeba mít připraveno několik věcí:

- Visual Studio: Ujistěte se, že máte na svém počítači nainstalované Visual Studio. Pokud ho ještě nemáte, můžete si ho stáhnout z [zde](https://visualstudio.microsoft.com/).
- Aspose.Words pro .NET: Budete potřebovat knihovnu Aspose.Words. Můžete ji získat z [Webové stránky Aspose](https://releases.aspose.com/words/net/).
- Základní znalost C#: Základní znalost C# a .NET vám pomůže s tímto tutoriálem.

Dobře, když už máme to za sebou, pojďme se pustit do kódování!

## Importovat jmenné prostory

Nejdříve musíme importovat potřebné jmenné prostory pro práci s Aspose.Words. Je to jako shromáždit všechny nástroje před zahájením projektu. Přidejte je pomocí direktiv na začátek souboru C#:

```csharp
using System;
using System.Text.RegularExpressions;
using Aspose.Words;
using Aspose.Words.Replacing;
using Aspose.Words.Tables;
```

Nyní, když máme připravené všechny předpoklady, rozdělme si proces na několik kroků. Každý krok je klíčový a přiblíží nás k našemu cíli.

## Krok 1: Nastavení adresáře dokumentů

Nejprve musíme určit adresář, kde jsou uloženy naše dokumenty. Je to jako příprava na velké představení.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` s cestou k vašemu adresáři. Zde budou vaše dokumenty uloženy.

## Krok 2: Načtěte hlavní dokument

Dále načteme hlavní dokument, do kterého chceme vložit další dokument. Představte si to jako naši hlavní scénu, kde se bude odehrávat veškerá akce.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

Tento kód načte hlavní dokument ze zadaného adresáře.

## Krok 3: Nastavení možností hledání a nahrazení

Abychom našli konkrétní místo, kam chceme vložit náš dokument, použijeme funkci najít a nahradit. Je to jako použití mapy k nalezení přesného místa pro nový přídavek.

```csharp
FindReplaceOptions options = new FindReplaceOptions
{
    Direction = FindReplaceDirection.Backward,
    ReplacingCallback = new InsertDocumentAtReplaceHandler()
};
```

Zde nastavujeme směr zpět a určujeme vlastní obslužnou rutinu zpětného volání, kterou definujeme dále.

## Krok 4: Proveďte operaci nahrazení

Nyní řekneme našemu hlavnímu dokumentu, aby vyhledal konkrétní zástupný text a nahradil ho ničím, zatímco pomocí vlastního zpětného volání vloží další dokument.

```csharp
mainDoc.Range.Replace(new Regex("\\[MY_DOCUMENT\\]"), "", options);
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtReplace.docx");
```

Tento kód provede operaci hledání a nahrazení a poté uloží aktualizovaný dokument.

## Krok 5: Vytvořte vlastní obslužnou rutinu zpětného volání pro nahrazování

Náš vlastní obslužný program zpětného volání je místem, kde se kouzlo děje. Tento obslužný program definuje, jak se vkládání dokumentu provádí během operace hledání a nahrazování.

```csharp
private class InsertDocumentAtReplaceHandler : IReplacingCallback
{
    ReplaceAction IReplacingCallback.Replacing(ReplacingArgs args)
    {
        Document subDoc = new Document(dataDir + "Document insertion 2.docx");

        // Vložte dokument za odstavec obsahující hledaný text.
        Paragraph para = (Paragraph)args.MatchNode.ParentNode;
        InsertDocument(para, subDoc);

        // Odstraňte odstavec se shodným textem.
        para.Remove();
        return ReplaceAction.Skip;
    }
}
```

Zde načteme dokument, který má být vložen, a poté zavoláme pomocnou metodu pro provedení vložení.

## Krok 6: Definování metody vkládání dokumentu

Posledním dílkem naší skládačky je metoda, která dokument skutečně vloží na zadané místo.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    // Zkontrolujte, zda je cílem vkládání odstavec nebo tabulka
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;

        // Vytvořte NodeImporter pro import uzlů ze zdrojového dokumentu.
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        // Procházet všechny uzly na úrovni bloků v sekcích zdrojového dokumentu
        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        {
            foreach (Node srcNode in srcSection.Body)
            {
                // Přeskočit poslední prázdný odstavec sekce
                if (srcNode.NodeType == NodeType.Paragraph)
                {
                    Paragraph para = (Paragraph)srcNode;
                    if (para.IsEndOfSection && !para.HasChildNodes)
                        continue;
                }

                // Importovat a vložit uzel do cíle
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

Tato metoda se postará o import uzlů z dokumentu, které mají být vloženy, a jejich umístění na správné místo v hlavním dokumentu.

## Závěr

tady to máte! Komplexní průvodce vkládáním jednoho dokumentu do druhého pomocí Aspose.Words pro .NET. Dodržováním těchto kroků můžete snadno automatizovat úlohy sestavování a manipulace s dokumenty. Ať už vytváříte systém pro správu dokumentů, nebo jen potřebujete zefektivnit pracovní postup zpracování dokumentů, Aspose.Words je váš spolehlivý pomocník.

## Často kladené otázky

### Co je Aspose.Words pro .NET?
Aspose.Words pro .NET je výkonná knihovna pro programovou manipulaci s dokumenty Wordu. Umožňuje snadno vytvářet, upravovat, převádět a zpracovávat dokumenty Wordu.

### Mohu vložit více dokumentů najednou?
Ano, obslužnou rutinu zpětného volání můžete upravit tak, aby zvládala více vkládání iterací přes kolekci dokumentů.

### Je k dispozici bezplatná zkušební verze?
Rozhodně! Zkušební verzi si můžete stáhnout zdarma z [zde](https://releases.aspose.com/).

### Jak získám podporu pro Aspose.Words?
Podporu můžete získat návštěvou [Fórum Aspose.Words](https://forum.aspose.com/c/words/8).

### Mohu zachovat formátování vloženého dokumentu?
Ano, `NodeImporter` Třída umožňuje určit, jak se formátování zpracovává při importu uzlů z jednoho dokumentu do druhého.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}