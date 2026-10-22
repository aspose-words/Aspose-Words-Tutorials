---
category: general
date: 2026-10-13
description: Vytvořte nový dokument Word v C# a vložte obsahový ovládací prvek se
  zástupným textem. Naučte se, jak nastavit zástupný text a efektivně uložit dokument
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: cs
lastmod: 2026-10-13
og_description: Vytvořte nový dokument Word v C# pomocí Aspose.Words, vložte ovládací
  prvek obsahu, nastavte zástupný text a uložte dokument Word – vše v jednom průvodci.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Vytvořte nový dokument Word a vložte ovládací prvek obsahu v C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Vytvořte nový dokument Word a vložte ovládací prvek obsahu v C#
url: /cs/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte nový dokument Word a vložte ovládací prvek obsahu v C#

Pokud potřebujete **programově vytvořit nový dokument Word**, tento průvodce vám ukáže, jak to provést pomocí Aspose.Words pro .NET. Naučíte se **vložit ovládací prvek obsahu**, přiřadit **zástupný text** a nakonec **uložit dokument Word C#** kód, který můžete zkopírovat do svého projektu.

Tutoriál vás provede každým krokem, vysvětlí, proč je každé volání API důležité, a pokryje běžné varianty, jako je přidání rich‑textového SDT nebo práce s existujícími dokumenty. Na konci budete mít kompletní, spustitelný příklad, který můžete přizpůsobit fakturám, smlouvám nebo jakémukoli šablonovanému výstupu Word.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.7+)
* NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)
* IDE, například Visual Studio 2022 nebo Visual Studio Code

Žádné další knihovny nejsou potřeba.

## Vytvoření nového dokumentu Word s Aspose.Words

Prvním krokem je vytvořit objekt `Document`. Tento objekt představuje prázdný soubor Word v paměti.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` vám poskytuje plynulé API pro vkládání prvků na aktuální pozici kurzoru. Protože je dokument prázdný, kurzor začíná na začátku první (a jediné) sekce.

## Vložení ovládacího prvku obsahu (StructuredDocumentTag)

**Ovládací prvek obsahu** ve Wordu se nazývá Structured Document Tag (SDT). Následující kód vytvoří plain‑text SDT, nastaví jeho název a definuje zástupný text, který se zobrazí, když uživatel otevře soubor.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Proč je to důležité:**  
* `SdtType.PlainText` omezuje obsah na jeden řádek prostého textu, což je ideální pro jednoduchá pole jako jméno nebo e‑mail.  
* Nastavení `PlaceholderName` poskytuje vizuální nápovědu (`Enter name here`), která uživatele provede.

Pokud potřebujete bohatší pole (např. víceřádkový text nebo výběr data), nahraďte `SdtType.PlainText` za `SdtType.RichText` nebo `SdtType.Date`.

## Přidání volitelného okolního textu

Většina šablon obsahuje popisek před ovládacím prvkem. Můžete jej přidat stejnou instancí `DocumentBuilder`:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

Výsledný soubor Word ukazuje:

```
Customer Name: [Enter name here]
```

## Uložení dokumentu Word v C# stylu

Nakonec zapíšete dokument na disk. Aspose.Words automaticky určuje formát podle přípony souboru.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Když otevřete `output.docx` v Microsoft Word, uvidíte zástupný text uvnitř šedě ohraničeného ovládacího prvku. Uživatelé mohou kliknout na ovládací prvek a nahradit zástupný text svým vlastním hodnotou.

## Kompletní spustitelný příklad

Níže je samostatný konzolový program, který spojuje všechny kroky. Zkopírujte kód do nového konzolového projektu a spusťte jej.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Očekávaný výstup** (konzole):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Otevření `output.docx` zobrazí jeden řádek s popiskem *Customer Name:* následovaným ovládacím prvkem, který zobrazuje *Enter name here*.

## Běžné varianty a okrajové případy

| Scénář | Změna kódu | Důvod |
|----------|-------------|--------|
| **Rich‑textové pole** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Umožňuje víceřádkový vstup a základní formátování. |
| **Ovládací prvek jen pro čtení** | `sdt.LockContentControl = true;` | Zabrání uživatelům upravovat obsah ovládacího prvku. |
| **Předvyplnění daty** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Vloží výchozí hodnotu, která přepíše zástupný text. |
| **Přidání do existujícího dokumentu** | Načtěte pomocí `new Document("template.docx")` místo prázdného `Document` | Umožňuje scénáře šablon, kde je ovládací prvek umístěn v předdefinovaném rozložení. |
| **Více ovládacích prvků** | Opakujte blok tvorby s různými názvy a zástupnými texty | Užitečné pro formuláře sbírající několik informací. |

### Tip

Při generování velkých dokumentů znovu použijte jedinou instanci `DocumentBuilder` místo vytváření nové pro každý ovládací prvek. Tím snížíte paměťovou zátěž a zlepšíte výkon.

## Testování výsledku

1. Spusťte konzolovou aplikaci.  
2. Otevřete `output.docx` v Microsoft Word.  
3. Ověřte, že se zástupný text zobrazuje uvnitř šedě ohraničeného pole.  
4. Klikněte do pole, napište jméno a soubor uložte. Zadaný text nahradí zástupný.

Pokud se zástupný text nezobrazí, ujistěte se, že používáte Aspose.Words verze 23.9 nebo novější, protože starší verze měly chybu s `PlaceholderName` u plain‑text SDT.

## Závěr

Nyní víte, jak **vytvořit nový dokument Word**, **vložit ovládací prvek obsahu**, **nastavit zástupný text** a **uložit dokument Word C#** pomocí Aspose.Words. Kompletní příklad ukazuje standardní vzor a tabulka variant ukazuje, jak řešení přizpůsobit bohatším scénářům.

Dále můžete zkoumat:

* **Vložení ovládacího prvku pro datum** – použijte výčtový typ `SdtType.Date`.  
* **Naplnění šablony daty** – kombinujte `StructuredDocumentTag` s polemi pro hromadnou korespondenci.  
* **Export do PDF** – zavolejte `doc.Save("output.pdf")` po přidání ovládacích prvků.

Neváhejte experimentovat s různými typy SDT, nastavením zamčení a stylováním, aby vyhovovaly požadavkům vašeho projektu. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Create New Word Document](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}