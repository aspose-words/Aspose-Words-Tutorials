---
title: Přidat Odebrat komentář Odpovědět
linktitle: Přidat Odebrat komentář Odpovědět
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se přidávat a odebírat odpovědi na komentáře v dokumentech aplikace Word pomocí Aspose.Words for .NET. Vylepšete spolupráci na dokumentech pomocí tohoto podrobného průvodce.
weight: 10
url: /cs/net/working-with-comments/add-remove-comment-reply/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidat Odebrat komentář Odpovědět

## Zavedení

Práce s komentáři a jejich odpověďmi v dokumentech aplikace Word může výrazně zlepšit proces kontroly dokumentu. S Aspose.Words for .NET můžete tyto úkoly automatizovat, čímž se vaše pracovní postupy zefektivní a zefektivní. Tento tutoriál vás provede přidáváním a odebíráním odpovědí na komentáře a poskytne vám podrobného průvodce, jak tuto funkci zvládnout.

## Předpoklady

Než se ponoříte do kódu, ujistěte se, že máte následující:

-  Aspose.Words for .NET: Stáhněte a nainstalujte jej z[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí: Visual Studio nebo jakékoli jiné IDE, které podporuje .NET.
- Základní znalost C#: Znalost programování v C# je nezbytná.

## Importovat jmenné prostory

Chcete-li začít, importujte potřebné jmenné prostory do svého projektu C#:

```csharp
using System;
using Aspose.Words;
```

## Krok 1: Načtěte dokument aplikace Word

Nejprve musíte načíst dokument aplikace Word, který obsahuje komentáře, které chcete spravovat. V tomto příkladu předpokládáme, že máte ve svém adresáři dokument s názvem "Comments.docx".

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Comments.docx");
```

## Krok 2: Přístup k prvnímu komentáři

Dále otevřete první komentář v dokumentu. Tento komentář bude cílem pro přidávání a odstraňování odpovědí.

```csharp
Comment comment = (Comment)doc.GetChild(NodeType.Comment, 0, true);
```

## Krok 3: Odstraňte existující odpověď

Pokud již komentář obsahuje odpovědi, možná budete chtít jednu odstranit. Zde je návod, jak odstranit první odpověď na komentář:

```csharp
comment.RemoveReply(comment.Replies[0]);
```

## Krok 4: Přidejte novou odpověď

Nyní přidáme ke komentáři novou odpověď. Můžete zadat jméno autora, iniciály, datum a čas odpovědi a text odpovědi.

```csharp
comment.AddReply("John Doe", "JD", new DateTime(2017, 9, 25, 12, 15, 0), "New reply");
```

## Krok 5: Uložte aktualizovaný dokument

Nakonec upravený dokument uložte do svého adresáře.

```csharp
doc.Save(dataDir + "WorkingWithComments.AddRemoveCommentReply.docx");
```

## Závěr

Programová správa odpovědí na komentáře v dokumentech Word vám může ušetřit spoustu času a úsilí, zejména při práci s rozsáhlými recenzemi. Aspose.Words for .NET činí tento proces přímočarým a efektivním. Podle kroků popsaných v této příručce můžete snadno přidávat a odebírat odpovědi na komentáře a vylepšovat tak spolupráci na dokumentech.

## FAQ

### Jak přidám více odpovědí do jednoho komentáře?

 K jednomu komentáři můžete přidat více odpovědí zavoláním na`AddReply` vícekrát na stejném objektu komentáře.

### Mohu upravit podrobnosti o autorovi pro každou odpověď?

 Ano, můžete zadat jméno autora, iniciály a datum a čas pro každou odpověď při použití`AddReply` metoda.

### Je možné odstranit všechny odpovědi z komentáře najednou?

Chcete-li odstranit všechny odpovědi, musíte procházet`Replies` sbírejte komentáře a odstraňte každý jednotlivě.

### Mohu získat přístup ke komentářům v konkrétní části dokumentu?

 Ano, můžete procházet sekcemi dokumentu a přistupovat ke komentářům v každé sekci pomocí`GetChild` metoda.

### Podporuje Aspose.Words for .NET další funkce související s komentáři?

Ano, Aspose.Words for .NET poskytuje rozsáhlou podporu pro různé funkce související s komentáři, včetně přidávání nových komentářů, nastavení vlastností komentářů a dalších.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
