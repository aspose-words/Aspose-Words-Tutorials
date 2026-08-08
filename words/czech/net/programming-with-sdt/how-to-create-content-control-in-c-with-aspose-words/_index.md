---
category: general
date: 2026-08-07
description: Jak vytvořit obsahovou kontrolu v C# pomocí Aspose.Words – naučte se
  přidat SDT, nastavit zástupný text, napsat výchozí text a vložit ovládací prvek
  prostého textu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to create content control
- how to add sdt
- how to set placeholder
- how to write default text
- insert plain text control
language: cs
lastmod: 2026-08-07
og_description: Jak vytvořit ovládací prvek obsahu v C# s Aspose.Words. Tento tutoriál
  ukazuje, jak přidat SDT, nastavit zástupný text, napsat výchozí text a vložit ovládací
  prvek prostého textu.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Jak vytvořit ovládací prvek obsahu v C# – kompletní průvodce Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  headline: How to create content control in C# with Aspose.Words
  type: TechArticle
- description: How to create content control in C# using Aspose.Words – learn how
    to add SDT, set placeholder, write default text, and insert plain text control.
  name: How to create content control in C# with Aspose.Words
  steps:
  - name: Expected output
    text: '- A `.docx` file on the desktop named `CustomerNameControl.docx`. - Inside
      the file, a single content control containing the text **John Doe**. - The placeholder
      text appears in light gray until the user types a new value.'
  - name: Adding multiple content controls
    text: You can repeat the **how to add sdt** steps to insert several controls in
      the same document. Just create a new `StructuredDocumentTag` for each field
      and move the builder accordingly.
  - name: Reading a placeholder programmatically
    text: 'If you need to verify that a placeholder was set correctly, inspect the
      `PlaceholderName` property:'
  - name: Using other SDT types
    text: Aspose.Words supports dropdown lists, date pickers, and rich‑text controls.
      Replace `SdtType.PlainText` with `SdtType.DropDownList` or `SdtType.RichText`
      to change the control type.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- SDT
title: Jak vytvořit ovládací prvek obsahu v C# pomocí Aspose.Words
url: /cs/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit obsahovou kontrolu v C# pomocí Aspose.Words

Pokud potřebujete **jak vytvořit obsahovou kontrolu** v dokumentu Word programově, tento průvodce vám přesně ukáže, jak na to. Uvidíte, jak přidat SDT, nastavit placeholder, zapsat výchozí text a vložit prostý textový kontrol – vše pomocí Aspose.Words pro .NET.

Tutoriál pokrývá každý krok od nastavení projektu až po uložení finálního souboru `.docx`. Na konci budete schopni generovat dokumenty, které obsahují plně nakonfigurované obsahové kontroly, připravené pro následné zpracování nebo interakci s uživatelem.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.7+)
- Licence Aspose.Words pro .NET nebo dočasný evaluační klíč
- Visual Studio 2022 (nebo jakékoli IDE podporující C#)
- Základní znalost syntaxe C#

Kromě `Aspose.Words` nejsou vyžadovány žádné další balíčky NuGet.

## Jak vytvořit obsahovou kontrolu – krok 1: nastavení projektu

Vytvořte novou konzolovou aplikaci a přidejte balíček Aspose.Words:

```bash
dotnet new console -n ContentControlDemo
cd ContentControlDemo
dotnet add package Aspose.Words
```

Proces **jak vytvořit obsahovou kontrolu** začíná čerstvým objektem `Document`. Tento objekt představuje soubor Word, který budete upravovat.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

> **Tip:** Uchovávejte instanci `DocumentBuilder` po celou životnost dokumentu; její zbytečné opětovné vytvoření přidává režii.

## Jak přidat SDT – krok 2: vložit prostý Structured Document Tag

SDT (Structured Document Tag) je technický název pro obsahovou kontrolu. Pro **jak přidat sdt**, vytvořte instanci `StructuredDocumentTag` s požadovaným typem.

```csharp
        // Create a plain‑text SDT (content control)
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document,
            SdtType.PlainText,   // Plain‑text control
            true);               // Is it a repeating section? false for single use

        // Give the control a title – this is how you reference it later
        sdt.Title = "CustomerName";

        // Insert the SDT at the current cursor position
        builder.InsertNode(sdt);
```

Možnost `SdtType.PlainText` vytvoří jednoduché textové pole, které uživatelé mohou upravovat. Nastavení `Title` vám pomůže najít kontrolu, když budete později potřebovat získat nebo upravit její obsah.

## Jak nastavit placeholder – krok 3: nakonfigurovat text placeholderu

Placeholder (zástupný text) vede koncového uživatele tím, že zobrazí ukázkový text před tím, než něco napíše. Pro **jak nastavit placeholder**, přiřaďte vlastnost `PlaceholderName`.

```csharp
        // Define the placeholder that appears when the control is empty
        sdt.PlaceholderName = "Enter name here";
```

Když se dokument otevře v Microsoft Word, šedý placeholder text se objeví uvnitř kontroly, dokud uživatel nezadá hodnotu.

## Jak zapsat výchozí text – krok 4: přidat počáteční obsah do SDT

Pokud chcete, aby kontrola obsahovala předdefinovaný obsah, musíte přesunout builder do SDT a text zapsat. Toto ukazuje **jak zapsat výchozí text**.

```csharp
        // Position the builder inside the SDT so we can add content
        builder.MoveTo(sdt);

        // Write the default text that will be visible initially
        builder.Write("John Doe");
```

Volání `MoveTo` změní umístění kurzoru do vnitřku SDT. Po `Write` kontrola zobrazí „John Doe“ jako svou počáteční hodnotu.

## Vložit prostý textový kontrol – krok 5: uložit dokument

Nakonec uložte dokument na disk. Tím se dokončí operace **vložit prostý textový kontrol**.

```csharp
        // Save the document with the content control embedded
        string outputPath = Path.Combine(
            Environment.GetFolderPath(Environment.SpecialFolder.Desktop),
            "CustomerNameControl.docx");

        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Když otevřete `CustomerNameControl.docx` ve Wordu, uvidíte prostý textový obsahový kontrol s názvem **CustomerName**, zobrazující placeholder „Enter name here“ a výchozí text „John Doe“.

### Očekávaný výstup

- Soubor `.docx` na ploše pojmenovaný `CustomerNameControl.docx`.
- V souboru jedna obsahová kontrola obsahující text **John Doe**.
- Placeholder text se zobrazuje světle šedě, dokud uživatel nezadá novou hodnotu.

## Další varianty a okrajové případy

### Přidání více obsahových kontrol

Můžete opakovat kroky **jak přidat sdt** pro vložení několika kontrol ve stejném dokumentu. Stačí vytvořit nový `StructuredDocumentTag` pro každé pole a podle toho přesunout builder.

```csharp
// Example: add a second control for "OrderNumber"
StructuredDocumentTag orderTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
orderTag.Title = "OrderNumber";
orderTag.PlaceholderName = "Enter order #";
builder.InsertNode(orderTag);
builder.MoveTo(orderTag);
builder.Write("12345");
```

### Programové čtení placeholderu

Pokud potřebujete ověřit, že placeholder byl nastaven správně, zkontrolujte vlastnost `PlaceholderName`:

```csharp
string placeholder = sdt.PlaceholderName; // returns "Enter name here"
```

### Použití jiných typů SDT

Aspose.Words podporuje rozbalovací seznamy, výběr dat a rich‑textové kontroly. Nahraďte `SdtType.PlainText` za `SdtType.DropDownList` nebo `SdtType.RichText` pro změnu typu kontroly.

## Časté úskalí a jak se jim vyhnout

| Symptom | Příčina | Oprava |
|---------|----------|--------|
| Placeholder se nikdy neobjeví | Dokument byl uložen před přiřazením placeholderu | Ujistěte se, že `PlaceholderName` je nastaven **před** voláním `Save`. |
| Výchozí text chybí | Builder nebyl přesunut do vnitřku SDT | Zavolejte `builder.MoveTo(sdt)` před `builder.Write`. |
| Název kontroly je prázdný | Vlastnost `Title` není nastavena | Vždy přiřaďte smysluplný `Title` pro pozdější načtení. |

## Závěr

Nyní víte **jak vytvořit obsahovou kontrolu** v C# pomocí Aspose.Words, včetně **jak přidat sdt**, **jak nastavit placeholder**, **jak zapsat výchozí text** a **vložit prostý textový kontrol**. Kompletní příklad se přeloží do připraveného souboru Word, který demonstruje každý koncept.

Odtud můžete zkoumat pokročilejší scénáře, jako je vazba obsahových kontrol na XML data, zpracování opakujících se sekcí nebo převod dokumentu do PDF při zachování kontrol. Každé z těchto témat staví přímo na základech pokrytých v tomto tutoriálu.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Rich Text Box Content Control](/words/hindi/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/hongkong/net/programming-with-sdt/rich-text-box-content-control/)
- [Rich Text Box Content Control](/words/spanish/net/programming-with-sdt/rich-text-box-content-control/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}