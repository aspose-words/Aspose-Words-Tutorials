---
category: general
date: 2026-10-20
description: Nastavte zástupný text ve Word dokumentu pomocí C#. Naučte se, jak rychle
  přidat ovládací prvek a nastavit zástupný text pomocí Aspose.Words pro .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: cs
lastmod: 2026-10-20
og_description: Nastavte zástupný text v dokumentu Word pomocí C#. Tento tutoriál
  vám ukáže, jak přidat ovládací prvek, nastavit zástupný text a programově generovat
  soubory Word.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Nastavte zástupný text v dokumentu Word pomocí C# – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Nastavte zástupný text ve Word dokumentu pomocí C#
url: /cs/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Nastavení zástupného textu ve Word dokumentu pomocí C#

Pokud potřebujete **nastavit zástupný text** v souboru Microsoft Word při jeho generování v C#, tento návod vám ukáže přesně jak. Uvidíte stručné, end‑to‑end řešení, které přidá ovládací prvek, definuje jeho zástupný text a uloží dokument — vše pomocí Aspose.Words pro .NET.

Mnoho vývojářů se ptá **jak přidat ovládací prvek** do Word dokumentu nebo **jak nastavit zástupný text** bez ručního otevírání Wordu. Tento tutoriál odpovídá na tyto otázky a také ukazuje čistý způsob, jak **generovat Word C#** soubory připravené pro zadání uživatele.

## Co dosáhnete

Na konci tohoto tutoriálu budete umět:

* Programově vytvořit prázdný Word dokument.
* Vložit plain‑text Structured Document Tag (SDT), což je technický název pro ovládací prvek.
* Přiřadit smysluplný název a zástupný text k SDT.
* Uložit výsledný soubor `.docx` na disk.

Žádné další nástroje nejsou potřeba kromě knihovny Aspose.Words a vývojového prostředí .NET 6 (nebo novějšího).

## Požadavky

* .NET 6 SDK nebo novější nainstalovaný.  
* Visual Studio 2022 (nebo jakékoli IDE podporující .NET).  
* NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`).  

> **Tip:** Použijte bezplatnou evaluační verzi Aspose.Words, pokud jen testujete; přidá vodoznak, ale jinak funguje stejně jako licencovaná verze.

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte nový konzolový projekt a přidejte požadované `using` direktivy. Tyto přinesou hlavní třídy Aspose.Words a markup jmenný prostor do dosahu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Proč je tento krok důležitý:* Import `Aspose.Words.Markup` vám poskytuje přístup k `StructuredDocumentTag`, `SdtType` a `MarkupLevel` — objektům potřebným pro **přidání ovládacího prvku** a **nastavení zástupného textu**.

## Krok 2: Vytvoření prázdného dokumentu a DocumentBuilderu

`Document` představuje celý Word soubor, zatímco `DocumentBuilder` poskytuje pohodlný kurzor pro vkládání elementů.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je tento krok důležitý:* Začátek s čistým dokumentem zajišťuje, že zástupný text, který nastavíte, se objeví přesně tam, kde chcete, bez rušení existujícím obsahem.

## Krok 3: Vytvoření ovládacího prvku (Structured Document Tag)

Zde vytvoříme plain‑text SDT, přiřadíme mu název a nastavíme zástupný text, který uživatel uvidí, když bude ovládací prvek prázdný.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Proč je tento krok důležitý:* Vlastnost `Title` vám umožní odkazovat na ovládací prvek později (např. pro datové vazby). `PlaceholderName` je přesně ten **nastavený zástupný text**, který chcete zobrazit, a vede koncového uživatele.

## Krok 4: Vložení ovládacího prvku na aktuální pozici kurzoru

Pomocí `DocumentBuilder` vložte SDT do dokumentu tam, kde je builder právě umístěn.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Proč je tento krok důležitý:* Vložení uzlu připojí ovládací prvek k DOM dokumentu. Pokud potřebujete přidat více zástupných textů, můžete přesunout kurzor builderu a tento krok opakovat.

## Krok 5: Uložení dokumentu

Nakonec zapíšete dokument na disk. Nahraďte `YOUR_DIRECTORY` skutečnou cestou na vašem počítači.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Když otevřete `SDT.docx` v Microsoft Word, uvidíte šedě podbarvený inline textový rámeček s textem **Enter name here**. Kliknutím dovnitř se zástupný text vymaže a uživatel může zadat jméno zákazníka.

### Očekávaný výstup

| Umístění souboru | Náhled obsahu |
|------------------|---------------|
| `C:\Temp\SDT.docx` | Inline zástupný text **Enter name here** uvnitř plain‑textového ovládacího prvku s názvem *CustomerName*. |

## Okrajové případy a varianty

| Situace | Doporučené úpravy |
|---------|-------------------|
| **Více zástupných textů** | Vytvořte další objekty `StructuredDocumentTag` s různými hodnotami `Title` a `PlaceholderName`, pak je vložte na požadovaná místa. |
| **Rich‑textový zástupný text** | Použijte `SdtType.RichText` místo `PlainText`, aby bylo možné formátovat text uvnitř zástupného textu. |
| **Blok‑úrovňový ovládací prvek** | Změňte `MarkupLevel.Inline` na `MarkupLevel.Block`, aby se ovládací prvek choval jako celý odstavec. |
| **Zástupný text není viditelný** | Ujistěte se, že nastavení zobrazení v aplikaci Word není nastaveno na skrytí ovládacích prvků (`File → Options → Advanced → Show content controls`). |
| **Ukládání do proudu** | Zavolejte `doc.Save(stream, SaveFormat.Docx)`, pokud potřebujete soubor poslat přes HTTP místo zápisu na disk. |

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit. Obsahuje všechny výše uvedené kroky v jedné metodě `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Spusťte program, otevřete vygenerovaný soubor a uvidíte připravený zástupný text k zadání uživatele.

## Často kladené otázky

**Q: Funguje to s .NET Core?**  
A: Ano. Aspose.Words pro .NET je kompatibilní s .NET Core, .NET 5 i .NET 6+. Stejný kód běží beze změny.

**Q: Můžu nastavit výchozí hodnotu kromě zástupného textu?**  
A: Použijte `sdt.SetText("Default value")` po vytvoření SDT. Zástupný text zmizí, jakmile je hodnota nastavena.

**Q: Co když potřebuji později načíst zadanou hodnotu?**  
A: Načtěte dokument, najděte SDT podle jeho `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) a přečtěte `sdt.GetText()`.

## Závěr

Nyní víte, jak **nastavit zástupný text** ve Word dokumentu pomocí C#. Vytvořením plain‑text `StructuredDocumentTag`, přiřazením názvu a zástupného textu, vložením pomocí `DocumentBuilder` a uložením souboru můžete **přidat ovládací prvek** a **generovat Word C#** soubory programově.  

Odtud můžete dále zkoumat:

* Přidání rich‑textových nebo rozbalovacích seznamových ovládacích prvků (`SdtType.RichText`, `SdtType.DropDownList`).  
* Naplnění více zástupných textů z databáze.  
* Konverzi vygenerovaného `.docx` do PDF pomocí Aspose.Words.

Experimentujte s různými typy ovládacích prvků a styly zástupných textů, aby vyhovovaly potřebám vaší aplikace. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Set Placeholder Text in Aspose.Words – Complete C# Guide](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Create word document programmatically – add content control and placeholder](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [How to Add Content Control and Create Word Document with Aspose – Complete](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}