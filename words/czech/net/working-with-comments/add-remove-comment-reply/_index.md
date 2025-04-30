---
"description": "Naučte se, jak přidávat a odebírat odpovědi na komentáře v dokumentech Word pomocí Aspose.Words pro .NET. Vylepšete si spolupráci na dokumentech s tímto podrobným návodem."
"linktitle": "Přidat Odebrat komentář Odpovědět"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidat Odebrat komentář Odpovědět"
"url": "/cs/net/working-with-comments/add-remove-comment-reply/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidat Odebrat komentář Odpovědět

## Zavedení

Práce s komentáři a jejich odpověďmi v dokumentech Word může výrazně vylepšit proces recenzování dokumentů. S Aspose.Words pro .NET můžete tyto úkoly automatizovat, čímž zefektivníte a zjednodušíte svůj pracovní postup. Tento tutoriál vás provede přidáváním a odebíráním odpovědí na komentáře a poskytne vám podrobný návod, jak tuto funkci zvládnout.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte následující:

- Aspose.Words pro .NET: Stáhněte si a nainstalujte z [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE, které podporuje .NET.
- Základní znalost C#: Znalost programování v C# je nezbytná.

## Importovat jmenné prostory

Chcete-li začít, importujte potřebné jmenné prostory do svého projektu C#:

```csharp
using System;
using Aspose.Words;
```

## Krok 1: Načtěte dokument aplikace Word

Nejprve je třeba načíst dokument aplikace Word, který obsahuje komentáře, které chcete spravovat. V tomto příkladu předpokládáme, že máte ve svém adresáři dokument s názvem „Comments.docx“.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

## Krok 2: Přejděte k prvnímu komentáři

Dále otevřete první komentář v dokumentu. Tento komentář bude cílem pro přidávání a odebírání odpovědí.

```csharp
Comment comment = (Comment)doc.GetChild(NodeType.Comment, 0, true);
```

## Krok 3: Odstranění existující odpovědi

Pokud na komentář již existují odpovědi, můžete jednu z nich odstranit. Zde je návod, jak odstranit první odpověď na komentář:

```csharp
comment.RemoveReply(comment.Replies[0]);
```

## Krok 4: Přidat novou odpověď

Nyní přidejme novou odpověď ke komentáři. Můžete zadat jméno autora, iniciály, datum a čas odpovědi a text odpovědi.

```csharp
comment.AddReply("John Doe", "JD", new DateTime(2017, 9, 25, 12, 15, 0), "New reply");
```

## Krok 5: Uložte aktualizovaný dokument

Nakonec uložte upravený dokument do svého adresáře.

```csharp
doc.Save(dataDir + "WorkingWithComments.AddRemoveCommentReply.docx");
```

## Závěr

Programová správa odpovědí na komentáře v dokumentech Word vám může ušetřit spoustu času a úsilí, zejména při práci s rozsáhlými recenzemi. Aspose.Words pro .NET tento proces zjednodušuje a zefektivňuje. Dodržováním kroků uvedených v této příručce můžete snadno přidávat a odebírat odpovědi na komentáře, což vylepší vaše zkušenosti se spoluprací na dokumentech.

## Často kladené otázky

### Jak přidám více odpovědí k jednomu komentáři?

K jednomu komentáři můžete přidat více odpovědí voláním funkce `AddReply` metodu vícekrát na stejném objektu komentáře.

### Mohu si u každé odpovědi přizpůsobit údaje o autorovi?

Ano, při použití funkce můžete u každé odpovědi zadat jméno autora, iniciály a datum a čas `AddReply` metoda.

### Je možné odstranit všechny odpovědi z komentáře najednou?

Chcete-li odstranit všechny odpovědi, musíte projít celý proces. `Replies` shromažďování komentářů a jejich odstraňování jednotlivě.

### Mohu mít přístup ke komentářům v určité části dokumentu?

Ano, sekcemi dokumentu se můžete pohybovat a komentářům v každé sekci se můžete přistupovat pomocí `GetChild` metoda.

### Podporuje Aspose.Words pro .NET i další funkce související s komentáři?

Ano, Aspose.Words pro .NET poskytuje rozsáhlou podporu pro různé funkce související s komentáři, včetně přidávání nových komentářů, nastavení vlastností komentářů a dalších.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}