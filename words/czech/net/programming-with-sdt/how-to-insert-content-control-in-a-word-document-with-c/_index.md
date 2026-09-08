---
category: general
date: 2026-09-08
description: Naučte se, jak vložit prvek řízení obsahu do dokumentu Word pomocí C#
  a Aspose.Words. Obsahuje kroky pro vytvoření prvku řízení obsahu, nastavení zástupného
  textu a uložení souboru.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert content control
- create content control
language: cs
lastmod: 2026-09-08
og_description: Vložte ovládací prvek obsahu do souboru Word pomocí C# a Aspose.Words.
  Postupujte podle tohoto návodu, jak vytvořit ovládací prvek obsahu, nastavit zástupný
  text a uložit dokument.
og_image_alt: Insert content control example in a Word document
og_title: Vložení ovládacího prvku obsahu do Wordu pomocí C# – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to insert content control in a Word document using C# and
    Aspose.Words. Includes steps to create content control, set placeholder, and save
    the file.
  headline: How to insert content control in a Word document with C#
  type: TechArticle
tags:
- content control
- Aspose.Words
- C#
- Word automation
title: Jak vložit ovládací prvek obsahu do dokumentu Word pomocí C#
url: /cs/net/programming-with-sdt/how-to-insert-content-control-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vložit ovládací prvek obsahu do dokumentu Word pomocí C#

Pokud potřebujete **vložit ovládací prvek obsahu** do dokumentu Word, tento návod vám ukáže kompletní, spustitelný řešení. Také se naučíte, jak **programově vytvořit ovládací prvek obsahu**, nastavit text zástupce a zapsat soubor na disk.

Ovládací prvky obsahu vám umožňují definovat oblasti, které uživatelé mohou vyplnit, opakovat nebo zamknout. Jsou široce používány pro šablony, formuláře a dynamické zprávy. Níže uvedené kroky používají knihovnu Aspose.Words pro .NET, která funguje s .NET 6+, .NET Framework 4.6+ a .NET Core.

## Jak vložit ovládací prvek obsahu do dokumentu Word

1. **Přidejte Aspose.Words do svého projektu**  
   Otevřete terminál ve složce projektu a spusťte:

   ```bash
   dotnet add package Aspose.Words
   ```

   Balíček obsahuje třídy `Document`, `DocumentBuilder` a `StructuredDocumentTag`, které jsou potřebné pro ovládací prvky obsahu.

2. **Vytvořte nový prázdný dokument**  

   ```csharp
   // Step 1: Create a new empty document and a DocumentBuilder
   Document doc = new Document();
   DocumentBuilder builder = new DocumentBuilder(doc);
   ```

   Objekt `Document` představuje celý soubor .docx, zatímco `DocumentBuilder` poskytuje pohodlný kurzor pro vkládání uzlů.

## Vytvoření ovládacího prvku obsahu pomocí Aspose.Words

Ovládací prvky obsahu jsou reprezentovány třídou `StructuredDocumentTag` (SDT). Následující kód vytvoří **plain‑text** ovládací prvek obsahu a přiřadí mu název, který můžete později dotazovat.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (content control)
//         - Set a title that can be used to identify the control
//         - Provide placeholder text that appears when the control is empty
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,
    SdtType.PlainText,      // Plain‑text control
    MarkupLevel.Block);    // Block‑level control (behaves like a paragraph)

sdt.Title = "CustomerName";
sdt.PlaceholderName = "Enter name here";
```

*Proč je to důležité:*  
- `SdtType.PlainText` zajišťuje, že ovládací prvek přijímá pouze prosté znaky.  
- `MarkupLevel.Block` způsobí, že se ovládací prvek chová jako celý odstavec, což je ideální pro formulářová pole.  
- Vlastnost `Title` je stabilní identifikátor, který můžete použít při vyhledávání nebo vazbě dat.

## Nastavení zástupného a výchozího textu

Zástupný text (placeholder) uživatele navádí, než něco napíše. Můžete také předvyplnit ovládací prvek výchozím obsahem.

```csharp
// Step 4: Optionally set default content for the control
sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");
```

XML fragment musí odpovídat datovému typu ovládacího prvku. Pro plain‑text ovládací prvky je vyžadován prvek `<text>`. Pokud tento krok vynecháte, bude místo toho zobrazen dříve definovaný zástupný text.

## Vložení ovládacího prvku obsahu na požadované místo

Kurzorem `DocumentBuilder` se určuje, kde se ovládací prvek objeví. Ve výchozím nastavení je kurzor na začátku dokumentu.

```csharp
// Step 3: Insert the StructuredDocumentTag into the document at the builder's current position
builder.InsertNode(sdt);
```

Pokud potřebujete ovládací prvek uvnitř tabulky, záhlaví nebo za existujícími odstavci, nejprve přesuňte builder:

```csharp
builder.MoveToDocumentEnd();   // Example: place the control at the end of the file
builder.InsertNode(sdt);
```

## Uložení dokumentu s vloženým ovládacím prvkem obsahu

```csharp
// Step 5: Save the document with the content control
doc.Save(@"C:\Temp\SDT.docx");
```

Soubor `SDT.docx` nyní obsahuje plain‑text ovládací prvek s názvem **CustomerName** a zástupným textem „Enter name here“ a výchozím textem „John Doe“.

![Příklad vložení ovládacího prvku obsahu v dokumentu Word](insert-content-control.png)

*Text alternativy obrázku:* Příklad vložení ovládacího prvku obsahu v dokumentu Word

### Očekávaný výsledek

Když otevřete `SDT.docx` v Microsoft Word:

- Šedý zástupný text „Enter name here“ se zobrazí, pokud vymažete výchozí text.  
- Ovládací prvek je zvýrazněn, když do něj kliknete, což naznačuje, že jej lze upravit.  
- Karta **Developer** (pokud je povolena) zobrazuje název ovládacího prvku **CustomerName** v panelu Vlastnosti.

## Kompletní funkční příklad

Níže je jeden samostatný program, který můžete zkopírovat, zkompilovat a spustit. Ukazuje každý krok od nastavení projektu až po uložení souboru.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class InsertContentControlDemo
{
    static void Main()
    {
        // 1. Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a plain‑text content control (StructuredDocumentTag)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            doc,
            SdtType.PlainText,
            MarkupLevel.Block);

        sdt.Title = "CustomerName";          // Identifier for later use
        sdt.PlaceholderName = "Enter name here";

        // 3. Insert the control at the current cursor position
        builder.InsertNode(sdt);

        // 4. Set default text (optional)
        sdt.XmlMapping.SetXmlFragment("<text>John Doe</text>");

        // 5. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Spusťte program pomocí `dotnet run`. Po provedení otevřete vygenerovaný soubor a ověřte, že se ovládací prvek objeví podle popisu.

## Praktické tipy a časté úskalí

| Situace | Doporučený přístup |
|-----------|----------------------|
| **Více ovládacích prvků stejného typu** | Dejte každému ovládacímu prvku jedinečný `Title`. Později můžete získat ovládací prvek pomocí `doc.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().FirstOrDefault(s => s.Title == "YourTitle")`. |
| **Ovládací prvek není ve Wordu viditelný** | Ujistěte se, že jste dokument uložili s příponou `.docx` a že verze `Aspose.Words` je kompatibilní s vaší verzí Office. |
| **Potřebujete ovládací prvek rich‑text** | Použijte `SdtType.RichText` místo `PlainText`. XML fragment pak používá elementy `<w:richText>`. |
| **Umístění ovládacího prvku do buňky tabulky** | Nejprve přesuňte builder do buňky: `builder.MoveTo(cell.FirstParagraph); builder.InsertNode(sdt);`. |
| **Výkon u velkých dokumentů** | Vytvořte `StructuredDocumentTag` jednou a znovu jej použijte, pokud potřebujete mnoho identických ovládacích prvků; klonujte jej pomocí `sdt.Clone(true)`. |

## Další kroky

- **Vytvořte opakující se ovládací prvky** (`SdtType.RepeatingSection`) pro tabulky, které se dynamicky rozšiřují.  
- **Vazte ovládací prvky na XML data** pomocí `sdt.XmlMapping.LoadXml(xmlString)`.  
- **Uzamkněte ovládací prvek** (`sdt.LockContentControl = true`) aby se zabránilo úpravám uživatele, přičemž programové aktualizace jsou stále povoleny.  

Prozkoumání těchto témat prohloubí vaši schopnost vytvářet robustní Word šablony pomocí Aspose.Words.

---

**Závěr**  
Nyní víte, jak **vložit ovládací prvek obsahu** do dokumentu Word pomocí C#. Tutoriál pokryl vytvoření ovládacího prvku, nastavení zástupného a výchozího textu, jeho vložení na požadované místo a uložení finálního souboru. S tímto základem můžete vytvářet sofistikované formuláře, šablony pro hromadnou korespondenci a automatizované zprávy, které využívají nativní funkce ovládacích prvků Wordu.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Nastavit styl ovládacího prvku obsahu](/words/english/net/programming-with-sdt/set-content-control-style/)
- [Nastavit barvu ovládacího prvku obsahu](/words/english/net/programming-with-sdt/set-content-control-color/)
- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}