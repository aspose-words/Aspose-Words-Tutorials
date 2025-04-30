---
"description": "Naučte se v tomto komplexním návodu krok za krokem, jak vkládat dokumenty do polí hromadné korespondence pomocí Aspose.Words pro .NET."
"linktitle": "Vložit dokument při hromadné korespondenci"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložit dokument při hromadné korespondenci"
"url": "/cs/net/clone-and-combine-documents/insert-document-at-mail-merge/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložit dokument při hromadné korespondenci

## Zavedení

Vítejte ve světě automatizace dokumentů s Aspose.Words pro .NET! Přemýšleli jste někdy, jak dynamicky vkládat dokumenty do konkrétních polí v hlavním dokumentu během hromadné korespondence? Jste na správném místě. Tento tutoriál vás krok za krokem provede procesem vkládání dokumentů do polí hromadné korespondence pomocí Aspose.Words pro .NET. Je to jako skládat puzzle, kde každý dílek dokonale zapadne na své místo. Tak se do toho pustíme!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Můžete [stáhněte si nejnovější verzi zde](https://releases.aspose.com/words/net/)Pokud potřebujete zakoupit licenci, můžete tak učinit [zde](https://purchase.aspose.com/buy)Nebo si můžete pořídit [dočasná licence](https://purchase.aspose.com/temporary-license/) nebo to zkuste s [bezplatná zkušební verze](https://releases.aspose.com/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné C# IDE.
3. Základní znalost C#: Znalost programování v C# vám tento tutoriál usnadní práci.

## Importovat jmenné prostory

Nejdříve budete muset importovat potřebné jmenné prostory. Ty jsou jako stavební kameny vašeho projektu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Rozdělme si proces na zvládnutelné kroky. Každý krok bude navazovat na předchozí a dovede vás k úplnému řešení.

## Krok 1: Nastavení adresáře

Než začnete vkládat dokumenty, musíte definovat cestu k adresáři s dokumenty. Zde jsou vaše dokumenty uloženy.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Načtení hlavního dokumentu

Dále načtete hlavní dokument. Tento dokument obsahuje slučovací pole, kam budou vloženy další dokumenty.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Krok 3: Nastavení zpětného volání pro sloučení polí

Pro zpracování procesu slučování budete muset nastavit funkci zpětného volání. Tato funkce bude zodpovědná za vkládání dokumentů do zadaných polí slučování.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Krok 4: Provedení hromadné korespondence

Nyní je čas spustit hromadnou korespondenci. A tady se začne dít zázrak. Určíte slučovací pole a dokument, který se má do tohoto pole vložit.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Krok 5: Uložení dokumentu

Po dokončení hromadné korespondence uložíte upravený dokument. Tento nový dokument bude mít vložený obsah přesně tam, kde ho chcete mít.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Krok 6: Vytvoření obslužné rutiny zpětného volání

Obslužná rutina zpětného volání je třída, která provádí speciální zpracování pro slučovací pole. Načte dokument zadaný v hodnotě pole a vloží jej do aktuálního slučovacího pole.

```csharp
private class InsertDocumentAtMailMergeHandler : IFieldMergingCallback
{
    void IFieldMergingCallback.FieldMerging(FieldMergingArgs args)
    {
        if (args.DocumentFieldName == "Document_1")
        {
            DocumentBuilder builder = new DocumentBuilder(args.Document);
            builder.MoveToMergeField(args.DocumentFieldName);

            Document subDoc = new Document((string)args.FieldValue);
            InsertDocument(builder.CurrentParagraph, subDoc);

            if (!builder.CurrentParagraph.HasChildNodes)
                builder.CurrentParagraph.Remove();

            args.Text = null;
        }
    }
}
```

## Krok 7: Vložení dokumentu

Tato metoda vloží zadaný dokument do aktuálního odstavce nebo buňky tabulky.

```csharp
private static void InsertDocument(Node insertionDestination, Document docToInsert)
{
    if (insertionDestination.NodeType == NodeType.Paragraph || insertionDestination.NodeType == NodeType.Table)
    {
        CompositeNode destinationParent = insertionDestination.ParentNode;
        NodeImporter importer = new NodeImporter(docToInsert, insertionDestination.Document, ImportFormatMode.KeepSourceFormatting);

        foreach (Section srcSection in docToInsert.Sections.OfType<Section>())
        foreach (Node srcNode in srcSection.Body)
        {
            if (srcNode.NodeType == NodeType.Paragraph)
            {
                Paragraph para = (Paragraph)srcNode;
                if (para.IsEndOfSection && !para.HasChildNodes)
                    continue;
            }

            Node newNode = importer.ImportNode(srcNode, true);
            destinationParent.InsertAfter(newNode, insertionDestination);
            insertionDestination = newNode;
        }
    }
    else
    {
        throw new ArgumentException("The destination node should be either a paragraph or table.");
    }
}
```

## Závěr

tady to máte! Úspěšně jste vložili dokumenty do konkrétních polí během hromadné korespondence pomocí Aspose.Words pro .NET. Tato výkonná funkce vám může ušetřit spoustu času a úsilí, zejména při práci s velkým množstvím dokumentů. Představte si to jako osobního asistenta, který se za vás postará o veškerou těžkou práci. Tak do toho a vyzkoušejte to. Hodně štěstí s programováním!

## Často kladené otázky

### Mohu vložit více dokumentů do různých slučovacích polí?
Ano, můžete. Jednoduše zadejte příslušná slučovací pole a odpovídající cesty k dokumentům v `MailMerge.Execute` metoda.

### Je možné formátovat vložený dokument jinak než hlavní dokument?
Rozhodně! Můžete použít `ImportFormatMode` parametr v `NodeImporter` pro ovládání formátování.

### Co když je název slučovacího pole dynamický?
Dynamické názvy slučovacích polí můžete zpracovat tak, že je předáte jako parametry obslužné rutině zpětného volání.

### Mohu tuto metodu použít s různými formáty souborů?
Ano, Aspose.Words podporuje různé formáty souborů včetně DOCX, PDF a dalších.

### Jak mám řešit chyby během procesu vkládání dokumentu?
Implementujte ošetření chyb v obslužné rutině zpětného volání, abyste mohli spravovat případné výjimky.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}