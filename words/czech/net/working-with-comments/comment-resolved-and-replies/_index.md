---
"description": "Automatizujte řešení a odpovídání na komentáře v dokumentech Word pomocí Aspose.Words pro .NET. Součástí je podrobný návod."
"linktitle": "Komentář vyřešen a odpovědi"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Komentář vyřešen a odpovědi"
"url": "/cs/net/working-with-comments/comment-resolved-and-replies/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Komentář vyřešen a odpovědi

## Zavedení

Pokud pracujete s dokumenty aplikace Word, pravděpodobně jste se již setkali s komentáři. Jsou skvělé pro spolupráci, ale jejich správa může být potíž. S Aspose.Words pro .NET můžete automatizovat proces řešení a odpovídání na komentáře. Tato příručka vás provede jednotlivými kroky, jak toho dosáhnout.

## Předpoklady

Než se ponoříte, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Můžete si jej stáhnout z [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Nastavení pomocí .NET Frameworku.
3. Základní znalost C#: Znalost syntaxe a konceptů.

## Importovat jmenné prostory

Nejdříve si importujme potřebné jmenné prostory. Tím zajistíme, že všechny potřebné třídy a metody budou snadno dostupné.

```csharp
using Aspose.Words;
using Aspose.Words.Comments;
```

Rozdělme si proces na jednoduché a snadno sledovatelné kroky. Každý krok vám pomůže pochopit kód a jeho funkčnost.

## Krok 1: Vložení dokumentu

Chcete-li začít, načtěte dokument Wordu obsahující komentáře. Použijte `Document` třída pro toto.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

Tento řádek kódu inicializuje nový `Document` objekt s cestou k vašemu dokumentu Word.

## Krok 2: Načtení komentářů

Dále potřebujeme získat všechny komentáře v dokumentu. Použijeme k tomu `GetChildNodes` metoda pro načtení kolekce `Comment` uzly.

```csharp
NodeCollection comments = doc.GetChildNodes(NodeType.Comment, true);
```

Tento kód načte všechny komentáře v dokumentu a uloží je do `NodeCollection`.

## Krok 3: Otevření nadřazeného komentáře

V našem příkladu se zaměříme na první komentář v kolekci. To bude náš nadřazený komentář.

```csharp
Comment parentComment = (Comment)comments[0];
```

Zde přetypujeme první uzel v kolekci na `Comment` objekt.

## Krok 4: Procházení odpovědí

Nyní si projdeme odpovědi na nadřazený komentář. Použijeme `foreach` smyčka pro iterování přes každou odpověď.

```csharp
foreach (Comment childComment in parentComment.Replies)
{
    Console.WriteLine(childComment.Ancestor.Id);
    Console.WriteLine(childComment.Done);

    childComment.Done = true;
}
```

V této smyčce vypíšeme ID komentáře předka a jeho stav (zda je hotový či nikoli). Poté označíme každou odpověď jako hotovou.

## Krok 5: Uložte dokument

Nakonec uložte upravený dokument do svého adresáře.

```csharp
doc.Save(dataDir + "WorkingWithComments.CommentResolvedAndReplies.docx");
```

Tento kód uloží změny do nového dokumentu a zajistí, že původní soubor zůstane nedotčen.

## Závěr

Zpracování komentářů v dokumentech Word nemusí být manuální povinností. S Aspose.Words pro .NET můžete tento proces automatizovat, ušetřit čas a snížit počet chyb. Postupujte podle tohoto průvodce, abyste mohli efektivně řešit a odpovídat na komentáře ve vašich dokumentech.

## Často kladené otázky

### Mohu automatizovat další úkoly související s komentáři pomocí Aspose.Words pro .NET?  
Ano, můžete automatizovat různé úkoly, jako je přidávání, mazání a úprava komentářů.

### Je Aspose.Words pro .NET kompatibilní s .NET Core?  
Ano, Aspose.Words pro .NET podporuje .NET Framework i .NET Core.

### Jak mohu získat bezplatnou zkušební verzi Aspose.Words pro .NET?  
Zkušební verzi zdarma si můžete stáhnout z [zde](https://releases.aspose.com/).

### Mohu použít Aspose.Words pro .NET pro práci s jinými typy dokumentů?  
Ano, Aspose.Words podporuje různé formáty včetně DOCX, PDF, HTML a dalších.

### Kde najdu podrobnou dokumentaci k Aspose.Words pro .NET?  
Dokumentaci si můžete prohlédnout [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}