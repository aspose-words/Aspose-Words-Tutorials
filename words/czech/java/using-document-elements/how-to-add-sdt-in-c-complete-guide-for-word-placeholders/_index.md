---
category: general
date: 2026-08-14
description: Jak rychle přidat SDT pomocí Aspose.Words. Naučte se vytvořit zástupný
  znak slova a vložit ovládací prvek prostého textu do souboru .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: cs
lastmod: 2026-08-14
og_description: Jak přidat SDT v C# pomocí Aspose.Words. Postupujte podle tohoto tutoriálu
  k vytvoření zástupného prvku ve Wordu a vložení ovládacího prvku prostého textu
  pro dynamické dokumenty.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Jak přidat SDT v C# – krok za krokem průvodce placeholdery ve Wordu
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Jak přidat SDT v C# – kompletní průvodce pro zástupné prvky Wordu
url: /cs/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak přidat SDT v C# – kompletní průvodce pro Word placeholdery

Pokud potřebujete **how to add sdt** v souboru Word, tento tutoriál vám ukáže přesné kroky pomocí Aspose.Words pro .NET. Na konci průvodce budete schopni **create word placeholder** značky, které umožní koncovým uživatelům psát přímo do dokumentu, a pochopíte, jak **insert plain text control** spolehlivě.

Práce se Structured Document Tags (SDT) odstraňuje potřebu ručních formulářových polí a poskytuje čistý, programový způsob, jak vytvářet dynamické smlouvy, zprávy nebo dopisy. Níže uvedený příklad pokrývá vše od nastavení projektu až po uložení finálního souboru .docx, takže můžete kód zkopírovat a vložit do svého řešení, aniž by vám chyběla jakákoli závislost.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
- Visual Studio 2022 nebo jakékoli C# IDE, které preferujete
- Licence Aspose.Words pro .NET (pro testování funguje i bezplatná dočasná licence)
- Základní znalost syntaxe C# a konceptu SDT

> **Tip:** Pokud plánujete distribuovat generované dokumenty, vložte soubor licence, aby se zabránilo vodoznaku z hodnocení.

## Krok 1: Nastavte projekt a importujte Aspose.Words

Create a new console application and add the Aspose.Words NuGet package:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

These `using` directives give you access to the `Document`, `DocumentBuilder`, and `StructuredDocumentTag` classes that are required for **insert plain text control** operations.

## Krok 2: Inicializujte dokument a builder

The first code block creates an empty Word document and a `DocumentBuilder` that lets you write content into it.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funguje jako kurzor; každé následné volání přidá obsah na aktuální pozici. Inicializace dokumentu je základem pro každý scénář **how to add sdt**, protože SDT musí patřit k živé instanci `Document`.

## Krok 3: Vložte plain‑text Structured Document Tag (SDT)

Nyní **insert plain text control**, který funguje jako placeholder, kde uživatel může zadat jméno, datum nebo libovolnou vlastní hodnotu.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` říká Aspose.Words, aby vytvořil jednoduché textové pole.
- `SdtAppearanceTags.Default` dává značce standardní vizuální styl Wordu (šedý rámeček při otevření dokumentu ve Wordu).

## Krok 4: Nakonfigurujte SDT s názvem a textem placeholderu

Dobře pojmenované SDT činí dokument samovysvětlujícím pro koncové uživatele. Zde **create word placeholder** metadata a nastavíme nápovědu, která se zobrazí uvnitř pole.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` je interní identifikátor, který můžete později použít při programovém získávání nebo aktualizaci hodnoty.
- `PlaceholderName` je šedá nápověda zobrazovaná ve Wordu, která uživateli říká, co má zadat.

## Krok 5: Přidejte okolní obsah

Dokument zřídka obsahuje jen jedno SDT. Obvykle potřebujete běžné odstavce před a po placeholderu. Použijte metodu `WriteLine` builderu k přidání statického textu.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

Volání `InsertNode` umístí dříve vytvořené SDT přesně tam, kde jej potřebujete, a zachová tok okolního textu.

## Krok 6: Uložte dokument do souboru .docx

Nakonec uložte dokument na disk. Cesta může být absolutní nebo relativní k složce projektu.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Otevření `SDT.docx` v Microsoft Word zobrazí šedý placeholder s textem **Enter name here**. Uživatelé mohou kliknout na pole, zadat hodnotu a dokument si tuto hodnotu při dalším uložení zachová.

## Kompletní, spustitelný příklad

Sestavením všech částí dohromady získáte samostatný program, který můžete spustit okamžitě:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Očekávaný výstup** při spuštění programu:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Otevření vygenerovaného `SDT.docx` ukazuje:

```
Dear [Enter name here],
After the SDT
```

Text v hranatých závorkách je placeholder **insert plain text control**, který uživatelé mohou nahradit.

## Běžné varianty a okrajové případy

| Situace | Jak upravit kód |
|-----------|-----------------------|
| **Multiple placeholders** | Call `InsertStructuredDocumentTag` repeatedly and give each tag a unique `Title`. |
| **Rich‑text SDT** | Use `StructuredDocumentTagType.RichText` instead of `PlainText`. |
| **Lock the placeholder** | Set `plainTextTag.LockContentControl = true;` to prevent users from deleting the field. |
| **Pre‑populate with a value** | Assign `plainTextTag.Text = "John Doe";` before saving. |
| **Conditional appearance** | Use `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` for a tick‑box control. |

Tyto varianty vám umožní **create word placeholder** struktury, které odpovídají téměř jakémukoli scénáři podobnému formuláři.

## Tipy pro řešení problémů

- **Placeholder není viditelný** – Ujistěte se, že soubor otevíráte v Microsoft Word (nebo kompatibilním prohlížeči). Některé lehké editory SDT skrývají.
- **Upozornění na licenci** – Pokud vidíte vodoznak hodnocení, ověřte, že je soubor licence správně načten (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Nesprávná pozice kurzoru** – Po vložení SDT zůstává kurzor builderu *za* značkou. Pokud potřebujete přidat text *uvnitř* značky, použijte `builder.MoveTo(plainTextTag);` před zápisem.

## Závěr

Nyní víte, jak **how to add sdt** do dokumentu Word pomocí Aspose.Words pro .NET, jak **create word placeholder** značky, a jak **insert plain text control**, které uživatelé mohou přímo ve Wordu upravovat. Kompletní příklad demonstruje inicializaci, vložení značky, konfiguraci, okolní obsah a uložení – vše v jednom spustitelném programu.

Dále prozkoumejte související témata, jako je **insert rich text control**, **populate SDTs from a database**, nebo **convert the final document to PDF**. Všechny tyto položky staví na stejných základech, které jsou zde popsány, takže můžete s jistotou rozšířit svůj automatizační pipeline.

Šťastné programování a nebojte se experimentovat s různými typy SDT, aby vyhovovaly vašim potřebám automatizace dokumentů!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit formulářová pole a přidat obsah pomocí DocumentBuilder v Aspose.Words pro Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Jak vytvořit editovatelné rozsahy v dokumentech jen pro čtení pomocí Aspose.Words pro Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Přidání záložek do Wordu pomocí Aspose.Words pro Java – Vložení, aktualizace, smazání](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}