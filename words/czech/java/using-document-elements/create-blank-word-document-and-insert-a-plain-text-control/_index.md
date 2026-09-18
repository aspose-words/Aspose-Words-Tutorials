---
category: general
date: 2026-09-18
description: Vytvořte prázdný dokument Word pomocí C# a nastavte zástupný text, poté
  dokument uložte jako docx. Naučte se vložit ovládací prvek prostého textu a přidat
  název zástupného textu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: cs
lastmod: 2026-09-18
og_description: Vytvořte prázdný dokument Word pomocí C#. Nastavte zástupný text,
  vložte ovládací prvek pro prostý text, přidejte název zástupce a uložte dokument
  jako docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Vytvořte prázdný dokument Word se zástupným textem – průvodce C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Vytvořte prázdný dokument Word a vložte ovládací prvek prostého textu
url: /cs/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word a vložte ovládací prvek plain‑text

Pokud potřebujete **vytvořit prázdný dokument Word** programově, tento návod vám ukáže, jak to provést v C#. Naučíte se **vložit plain‑text control**, **nastavit zástupný text**, **přidat název zástupce** a nakonec **uložit dokument jako docx**. Kroky jsou zcela samostatné, takže můžete kód zkopírovat do libovolného .NET projektu a spustit ho okamžitě.

Práce se soubory Word často vyžaduje čistý výchozí bod — prázdný dokument, který již obsahuje ovládací prvky, jež uživatelé vyplní. Na konci tohoto tutoriálu budete mít soubor `.docx`, který obsahuje ovládací prvek plain‑text s užitečným zástupným textem a následným běžným obsahem.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
- Odkaz na knihovnu **Aspose.Words for .NET** (k dispozici přes NuGet `Install-Package Aspose.Words`)
- Základní znalost C# konzolových aplikací
- Oprávnění k zápisu do výstupní složky, kterou zadáte v `doc.save(...)`

## Co vytvoříte

Finální dokument (`SDT.docx`) obsahuje:

1. Prázdný soubor Word ( **blank Word document**, který jste vytvořili)
2. Ovládací prvek plain‑text (krok **insert plain text control**)
3. Zástupný text, který se zobrazí uvnitř ovládacího prvku, dokud uživatel něco nenapíše (krok **set placeholder text**)
4. Název zástupce, který lze později použít pro programový přístup (krok **add placeholder name**)
5. Řádek běžného textu za ovládacím prvkem, který ukazuje, že může následovat normální obsah

## Krok 1: Vytvořte prázdný dokument Word

Prvním krokem je vytvořit prázdný objekt `Document`. Tento objekt představuje zcela nový, **blank Word document** v paměti.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Proč je to důležité:* Prázdný `Document` vám dává plnou kontrolu nad každým prvkem, který přidáte, a zajišťuje, že žádné skryté styly nebo sekce nebudou rušit ovládací prvek, který později vložíte.

## Krok 2: Inicializujte DocumentBuilder

`DocumentBuilder` je pomocná třída, která vám umožňuje zapisovat do `Document`. Sleduje aktuální pozici kurzoru a poskytuje metody pro vkládání různých objektů Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Proč je to důležité:* Použití `DocumentBuilder` zjednodušuje proces přidání **plain‑text control**, protože builder zná přesný bod vložení.

## Krok 3: Vložte ovládací prvek plain‑text

Nyní přidáme **plain‑text content control** (také známý jako Structured Document Tag, nebo SDT). Typ ovládacího prvku `StructuredDocumentTagType.PLAIN_TEXT` říká Wordu, aby obsah považoval za prostý text, nikoli za formátovaný.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Proč je to důležité:* Metoda `InsertStructuredDocumentTag` vytvoří ovládací prvek a vrátí referenci (`sdt`), kterou můžete dále konfigurovat, například přidáním zástupného textu nebo vlastního názvu.

## Krok 4: Nastavte zástupný text a přidejte název zástupce

Zástupný text poskytuje uživatelům vizuální vodítko, co mají psát. Krok **add placeholder name** přiřadí programový identifikátor, který můžete později dotazovat pomocí `doc.GetChildNodes` nebo podobných API.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Proč je to důležité:* `SetPlaceholderName` řídí šedý nápovědní text zobrazovaný uvnitř ovládacího prvku. Nastavení `Tag` (akce **add placeholder name**) vám umožní najít ovládací prvek ve stromu dokumentu, aniž byste museli prohledávat celý soubor.

## Krok 5: Přidejte běžný obsah za ovládací prvek

Abychom dokázali, že dokument pokračuje normálně po ovládacím prvku, napíšeme jednoduchý řádek textu.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Krok 6: Uložte dokument jako docx

Nakonec uložíme dokument v paměti na disk. Toto je operace **save document as docx**, která vytvoří soubor, který můžete otevřít v Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Proč je to důležité:* Použití formátu `.docx` zajišťuje maximální kompatibilitu s moderními verzemi Wordu, Google Docs a dalšími nástroji kompatibilními s Office.

## Kompletní, spustitelný příklad

Níže je celý program, který můžete zkopírovat do projektu konzolové aplikace. Nahraďte `YOUR_DIRECTORY` skutečnou cestou ke složce na vašem počítači.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Očekávaný výsledek

- Otevření `SDT.docx` ve Wordu zobrazí prázdný šedý rámeček s textem **Enter text…** uvnitř.
- Rámeček je plain‑text content control; můžete do něj psát přímo.
- Pod rámečkem se řádek **After the tag.** zobrazí jako běžný odstavec.

Pokud se zástupný text nezobrazí, ověřte, že používáte aktuální verzi Aspose.Words (v23.1 nebo novější) a že dokument je otevřen ve verzi Wordu, která podporuje ovládací prvky (Word 2007+).

## Běžné varianty a okrajové případy

| Scenario | How to adapt the code |
|----------|-----------------------|
| **Více zástupců** | Zavolejte `InsertStructuredDocumentTag` znovu s jiným ID tagu a názvem zástupce. |
| **Rich‑text control** | Použijte `StructuredDocumentTagType.RichText` místo `PlainText`. |
| **Nastavení výchozího textu** | Po vložení přiřaďte `sdt.Text = "Default value";` – tento text nahradí zástupný text při načtení dokumentu. |
| **Ukládání do proudu** | Nahraďte `doc.Save(outputPath);` za `doc.Save(stream, SaveFormat.Docx);` pro odeslání souboru přes HTTP. |
| **Změna barvy zástupného textu** | Použijte `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (vyžaduje `using System.Drawing`). |

## Profesionální tipy

- **Znovu použijte ID tagu**: Udržení tagu (`MyTag`) konzistentního napříč dokumenty vám umožní později automatizovat naplňování dat pomocí `doc.Range.Replace` nebo `StructuredDocumentTagCollection`.
- **Vyhněte se pevně zakódovaným cestám**: Použijte `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` pro přenosné umístění výstupu.
- **Výkon**: Pokud potřebujete generovat tisíce dokumentů, vytvořte jedinou šablonu `Document` se SDT již vloženým, a poté ji pro každou iteraci klonujte pomocí `doc.Clone()`.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **vložit plain text control**, **nastavit zástupný text**, **přidat název zástupce** a **uložit dokument jako docx** pomocí Aspose.Words for .NET. Tento vzor tvoří základ pro tvorbu Word šablon vyplněných formulářem, automatizovaných reportů nebo jakéhokoli řešení, které vyžaduje uživatelem editovatelné zástupce.

Neváhejte experimentovat s dalšími typy ovládacích prvků, kombinovat více zástupců nebo integrovat tento kód do webového API, které vrací vygenerovaný soubor `.docx` přímo volajícím. Pro další krok prozkoumejte **naplnění ovládacího prvku daty programově** nebo **převod vygenerovaného souboru Word do PDF** pomocí vestavěných konverzních funkcí Aspose.Words. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto návodu. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}