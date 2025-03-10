---
title: Zobrazit skrýt záložky v dokumentu aplikace Word
linktitle: Zobrazit skrýt záložky v dokumentu aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak dynamicky zobrazit nebo skrýt záložky v dokumentu aplikace Word pomocí Aspose.Words for .NET s naším podrobným průvodcem. Ideální pro vývojáře.
weight: 10
url: /cs/net/programming-with-bookmarks/show-hide-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Zobrazit skrýt záložky v dokumentu aplikace Word

## Úvod

Stalo se vám, že jste potřebovali dynamicky skrýt nebo zobrazit určité části dokumentu Word? Tak to máš štěstí! S Aspose.Words for .NET můžete snadno spravovat viditelnost obsahu se záložkami ve vašich dokumentech. Tento tutoriál vás provede procesem zobrazení a skrytí záložek v dokumentu aplikace Word pomocí Aspose.Words for .NET. Kód rozebereme krok za krokem, takže ať už jste ostřílený vývojář nebo nováček, tento průvodce se vám bude snadno řídit.

## Předpoklady

Než se ponoříme do kódu, ujistěte se, že máte vše, co potřebujete:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words for .NET. Pokud ne, můžete si jej stáhnout[tady](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: IDE jako Visual Studio.
3. Základní znalost C#: Výhodou bude znalost programování v C#.
4. Dokument aplikace Word: Ukázkový dokument aplikace Word se záložkami.

## Importovat jmenné prostory

Než začnete s kódem, musíte importovat potřebné jmenné prostory. Na začátek souboru C# přidejte následující:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
using Aspose.Words.Tables;
```

## Krok 1: Vložte svůj dokument

Nejprve musíte načíst dokument aplikace Word, který obsahuje záložky. Můžete to udělat takto:

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

### Vysvětlení

- dataDir: Toto je cesta k adresáři, kde se nachází váš dokument aplikace Word.
-  Dokument dokumentu: Inicializuje novou instanci souboru`Document` třídy s vaším zadaným souborem.

## Krok 2: Zobrazení nebo skrytí obsahu označeného záložkou

Dále definujeme metodu, jak zobrazit nebo skrýt obsah označený záložkou. Zde je kompletní metoda:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool showHide)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.MoveToDocumentEnd();

    // {IF "{MERGEFIELD bookmark}" = "true" "" ""}
    Field field = builder.InsertField("IF \"", null);
    builder.MoveTo(field.Start.NextSibling);
    builder.InsertField("MERGEFIELD " + bookmarkName + "", null);
    builder.Write("\" = \"true\" ");
    builder.Write("\"");
    builder.Write("\"");
    builder.Write(" \"\"");

    Node currentNode = field.Start;
    bool flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.Run)
            if (currentNode.ToString(SaveFormat.Text).Trim() == "\"")
                flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkStart.ParentNode.InsertBefore(currentNode, bm.BookmarkStart);
        currentNode = nextNode;
    }

    Node endNode = bm.BookmarkEnd;
    flag = true;
    while (currentNode != null && flag)
    {
        if (currentNode.NodeType == NodeType.FieldEnd)
            flag = false;

        Node nextNode = currentNode.NextSibling;

        bm.BookmarkEnd.ParentNode.InsertAfter(currentNode, endNode);
        endNode = currentNode;
        currentNode = nextNode;
    }

    doc.MailMerge.Execute(new[] { bookmarkName }, new object[] { showHide });
}
```

### Vysvětlení

- Záložka bm: Načte záložku z dokumentu.
- Tvůrce DocumentBuilder: Pomáhá při navigaci a úpravách dokumentu.
- Pole pole: Vloží pole KDYŽ pro kontrolu stavu záložky.
- Uzel currentNode: Prochází přes uzly, aby našel začátek a konec pole.

## Krok 3: Spusťte funkci Zobrazit/skrýt

 Nyní musíte zavolat na`ShowHideBookmarkedContent` metoda, předání dokumentu, název záložky a příznak viditelnosti:

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", false);
```

### Vysvětlení

- doc: Objekt vašeho dokumentu.
- "MyBookmark1": Název záložky, kterou chcete zobrazit/skrýt.
- false: Příznak viditelnosti (true pro zobrazení, false pro skrytí).

## Krok 4: Uložte dokument

Nakonec upravený dokument uložte:

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Vysvětlení

- dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx": Cesta a název nového dokumentu, do kterého budou uloženy změny.

## Závěr

A tady to máte! Úspěšně jste se naučili, jak zobrazit a skrýt záložky v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato technika může být neuvěřitelně užitečná pro dynamické generování dokumentů s podmíněným obsahem.

## FAQ

### Co je Aspose.Words for .NET?
Aspose.Words for .NET je výkonná knihovna pro zpracování dokumentů, která umožňuje vývojářům vytvářet, upravovat a převádět dokumenty aplikace Word programově.

### Jak získám Aspose.Words pro .NET?
 Aspose.Words for .NET si můžete stáhnout z[tady](https://releases.aspose.com/words/net/). K dispozici je také bezplatná zkušební verze.

### Mohu tuto metodu použít pro jiné typy záložek?
Ano, tuto metodu lze upravit tak, aby spravovala viditelnost všech záložek v dokumentu aplikace Word.

### Co když můj dokument neobsahuje zadanou záložku?
Pokud záložka neexistuje, metoda vyvolá chybu. Před pokusem o její zobrazení/skrytí se ujistěte, že záložka existuje.

### Jak mohu získat podporu, pokud narazím na problémy?
 Můžete získat podporu od komunity Aspose[tady](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
