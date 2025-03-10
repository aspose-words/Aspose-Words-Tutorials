---
title: Vložit dokument při hromadné korespondenci
linktitle: Vložit dokument při hromadné korespondenci
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se vkládat dokumenty do polí hromadné korespondence pomocí Aspose.Words for .NET v tomto komplexním, podrobném tutoriálu.
weight: 10
url: /cs/net/clone-and-combine-documents/insert-document-at-mail-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložit dokument při hromadné korespondenci

## Zavedení

Vítejte ve světě automatizace dokumentů s Aspose.Words pro .NET! Přemýšleli jste někdy o tom, jak dynamicky vkládat dokumenty do určitých polí v hlavním dokumentu během operace hromadné korespondence? Tak to jste na správném místě. Tento tutoriál vás krok za krokem provede procesem vkládání dokumentů do polí hromadné korespondence pomocí Aspose.Words for .NET. Je to jako skládání puzzle, kde každý dílek dokonale zapadne na své místo. Takže, pojďme se ponořit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words pro .NET: Můžete[stáhněte si nejnovější verzi zde](https://releases.aspose.com/words/net/) . Pokud potřebujete zakoupit licenci, můžete tak učinit[zde](https://purchase.aspose.com/buy) . Případně můžete získat a[dočasná licence](https://purchase.aspose.com/temporary-license/) nebo to zkuste s a[zkušební verze zdarma](https://releases.aspose.com/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné C# IDE.
3. Základní znalost C#: Díky znalosti programování v C# bude tento tutoriál hračkou.

## Importovat jmenné prostory

Nejprve budete muset importovat potřebné jmenné prostory. Jsou to jako stavební kameny vašeho projektu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.MailMerging;
using System.Linq;
```

Pojďme si tento proces rozdělit na zvládnutelné kroky. Každý krok bude navazovat na předchozí a povede vás ke kompletnímu řešení.

## Krok 1: Nastavení adresáře

Než budete moci začít vkládat dokumenty, musíte definovat cestu k adresáři dokumentů. Zde jsou uloženy vaše dokumenty.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Načtení hlavního dokumentu

Dále načtete hlavní dokument. Tento dokument obsahuje slučovací pole, kam budou vloženy další dokumenty.

```csharp
Document mainDoc = new Document(dataDir + "Document insertion 1.docx");
```

## Krok 3: Nastavení zpětného volání sloučení polí

Abyste zvládli proces sloučení, budete muset nastavit funkci zpětného volání. Tato funkce bude zodpovědná za vkládání dokumentů do zadaných slučovacích polí.

```csharp
mainDoc.MailMerge.FieldMergingCallback = new InsertDocumentAtMailMergeHandler();
```

## Krok 4: Provedení hromadné korespondence

Nyní je čas provést hromadnou korespondenci. Tady se děje kouzlo. Určíte slučovací pole a dokument, který má být vložen do tohoto pole.

```csharp
mainDoc.MailMerge.Execute(new[] { "Document_1" }, new object[] { dataDir + "Document insertion 2.docx" });
```

## Krok 5: Uložení dokumentu

Po dokončení hromadné korespondence upravený dokument uložíte. Tento nový dokument bude mít vložený obsah přesně tam, kde ho chcete mít.

```csharp
mainDoc.Save(dataDir + "CloneAndCombineDocuments.InsertDocumentAtMailMerge.doc");
```

## Krok 6: Vytvoření obsluhy zpětného volání

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

Tato metoda vloží zadaný dokument do aktuální buňky odstavce nebo tabulky.

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

A tady to máte! Úspěšně jste vložili dokumenty do určitých polí během operace hromadné korespondence pomocí Aspose.Words for .NET. Tato výkonná funkce vám může ušetřit spoustu času a úsilí, zejména při práci s velkými objemy dokumentů. Berte to tak, že máte osobního asistenta, který se za vás postará o veškeré těžké zvedání. Takže do toho a vyzkoušejte to. Šťastné kódování!

## FAQ

### Mohu vložit více dokumentů do různých slučovacích polí?
Ano, můžete. Jednoduše zadejte příslušná slučovací pole a odpovídající cesty dokumentu v`MailMerge.Execute` metoda.

### Je možné formátovat vložený dokument jinak než hlavní dokument?
 Absolutně! Můžete použít`ImportFormatMode` parametr v`NodeImporter` k ovládání formátování.

### Co když je název slučovacího pole dynamický?
Názvy polí dynamického sloučení můžete zpracovat tak, že je předáte jako parametry obsluze zpětného volání.

### Mohu tuto metodu použít s různými formáty souborů?
Ano, Aspose.Words podporuje různé formáty souborů včetně DOCX, PDF a dalších.

### Jak se vypořádám s chybami během procesu vkládání dokumentu?
Implementujte zpracování chyb v obslužné rutině zpětného volání, abyste mohli spravovat všechny výjimky, které mohou nastat.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
