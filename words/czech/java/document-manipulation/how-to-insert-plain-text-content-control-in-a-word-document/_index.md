---
category: general
date: 2026-10-26
description: Naučte se vkládat ovládací prvek prostého textu pomocí Aspose.Words v
  C#. Podrobný průvodce krok za krokem, který zahrnuje StructuredDocumentTag, názvy
  a ID značek.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: cs
lastmod: 2026-10-26
og_description: Vložte ovládací prvek prostého textu pomocí Aspose.Words v C#. Postupujte
  podle tohoto návodu, abyste přidali názvy, ID značek a přizpůsobili vzhled.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Vložení ovládacího prvku prostého textu ve Wordu pomocí C# – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vložit ovládací prvek prostého textu do dokumentu Word pomocí C#
url: /cs/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení ovládacího prvku prostého textu do dokumentu Word pomocí C#

Pokud potřebujete **vložit ovládací prvek prostého textu** do souboru Word, tento tutoriál vám přesně ukáže, jak to provést pomocí Aspose.Words pro .NET. Ať už vytváříte službu pro generování dokumentů nebo automatizujete tvorbu formulářů, níže uvedené kroky vám umožní přidat znovupoužitelnou, editovatelnou oblast, kterou mohou koncoví uživatelé vyplnit.

Naučíte se, jak vytvořit `Document`, použít `DocumentBuilder` k umístění prostého Structured Document Tag (SDT), nastavit přátelský název a přiřadit jedinečný identifikátor tagu. Průvodce také vysvětluje běžné varianty – například změnu vzhledu nebo vnoření ovládacích prvků – takže můžete řešení přizpůsobit jakémukoli projektu.

## Požadavky

- .NET 6.0 nebo novější (kód také funguje s .NET Framework 4.6+)
- Platná licence Aspose.Words pro .NET (nebo bezplatný evaluační klíč)
- Visual Studio 2022 nebo jakékoli IDE kompatibilní s C#
- Základní znalost syntaxe C#

> **Tip:** Pokud používáte bezplatnou evaluační verzi, pamatujte, že výstupní dokument bude obsahovat vodoznak. Licencovaná verze jej automaticky odstraní.

## Jak vložit ovládací prvek prostého textu pomocí Aspose.Words

Jádrem řešení je proces ve třech krocích:

1. **Vytvořte `Document` a `DocumentBuilder`.**  
2. **Vložte Structured Document Tag (SDT) typu plain‑text s výchozím vzhledem.**  
3. **Přiřaďte SDT název a identifikátor tagu.**  

Každý krok je vysvětlen níže, spolu s kompletním, spustitelným kódem.

### Krok 1: Inicializace dokumentu a builderu

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` představuje celý soubor Word, zatímco `DocumentBuilder` poskytuje metody jako `InsertParagraph`, `InsertImage` a, co je pro tento tutoriál klíčové, `InsertStructuredDocumentTag`. Jejich inicializace vám nejprve poskytne plátno, na které můžete umístit **ovládací prvek prostého textu**.

### Krok 2: Vložení ovládacího prvku prostého textu (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` říká Aspose.Words, aby vytvořil **ovládací prvek prostého textu**, který se chová jako jednoduché textové pole, které uživatelé mohou upravovat. `SdtAppearance.Default` vykreslí ovládací prvek s jemným pozadím, což v dokumentu jasně ukazuje, že oblast je editovatelná.

> **Proč použít `SdtAppearance.Default`?**  
> Výchozí vzhled je nejuniverzálnější kompatibilní styl napříč verzemi Wordu. Pokud potřebujete vzhled bez okraje, můžete později přepnout na `SdtAppearance.Hidden`.

### Krok 3: Nastavení názvu a identifikátoru tagu

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) se zobrazuje v panelu *Content Controls* ve Wordu a pomáhá koncovým uživatelům pochopit účel pole.  
- **Tag** (`sdt.Tag`) je identifikátor orientovaný na vývojáře, který můžete později dotazovat pomocí `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** poskytuje šedý nápovědní text, který zlepšuje uživatelský zážitek.  

Úplný úryvek kódu výše tvoří samostatný program, který můžete zkompilovat a spustit. Po provedení bude `output.docx` obsahovat jediný ovládací prvek prostého textu s názvem *MyTag* a tagem *TagId*.

![Diagram ukazující vložení ovládacího prvku prostého textu do dokumentu Word](image.png){alt="vložit ovládací prvek prostého textu"}

## Porozumění StructuredDocumentTag (SDT) a jeho vlastnostem

Structured Document Tag (SDT) je základní objektový model pro ovládací prvky Wordu. Nejdůležitější vlastnosti pro vložení ovládacího prvku prostého textu jsou:

| Vlastnost | Účel | Typické hodnoty |
|----------|------|----------------|
| `SdtType` | Určuje typ ovládacího prvku (plain text, rich text, picture, atd.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Vizuální styl ovládacího prvku | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Lidsky čitelný název zobrazovaný v panelu *Content Controls* | Jakýkoli krátký řetězec |
| `Tag` | Strojově čitelný identifikátor používaný v kódu | Alfanumerický řetězec |
| `PlaceholderName` | Text zobrazený, když je ovládací prvek prázdný | Vlastní nápovědní text |

Když nastavíte `SdtType.PlainText`, Word omezuje obsah na prosté znaky, čímž zabraňuje formátování. To činí ovládací prvek ideálním pro jednoduchá pole formuláře, jako je *Name*, *Email* nebo *Phone Number*.

### Varianty, které můžete potřebovat

| Scénář | Změna kódu |
|----------|-------------|
| **Žádné vizuální stínování** (bez okraje) | Použijte `SdtAppearance.Hidden` místo `Default`. |
| **Pole jen pro čtení** | Po vložení nastavte `sdt.LockContentControl = true`. |
| **Předvyplnění daty** | Nastavte `sdt.Text = "John Doe";` po vytvoření tagu. |
| **Více ovládacích prvků v tabulce** | Vložte SDT do buňky tabulky pomocí `builder.InsertCell();` před voláním `InsertStructuredDocumentTag`. |

## Časté úskalí a jak se jim vyhnout

1. **Zapomenutí nastavit název** – Word stále vytvoří ovládací prvek, ale uživatelé neuvidí smysluplný popis v panelu *Content Controls*. Vždy přiřaďte `sdt.Title`.  
2. **Použití špatného `SdtType`** – Pokud potřebujete prostý text, ale omylem zvolíte `RichText`, ovládací prvek umožní formátování, což může narušit následné zpracování. Zkontrolujte hodnotu enumu.  
3. **Ukládání do složky jen pro čtení** – Volání `doc.Save` vyhodí `UnauthorizedAccessException`. Ujistěte se, že cílový adresář je zapisovatelný, nebo pro testování použijte `Path.GetTempPath()`.  
4. **Licence nebyla použita** – Bez platné licence obsahuje výstupní dokument evaluační vodoznak. Licenci aplikujte co nejdříve ve vašem programu:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Kompletní, spustitelný příklad

Níže je celý program, připravený ke zkopírování a vložení do nového konzolového projektu.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Očekávaný výstup:** Po otevření `output.docx` v Microsoft Word se zobrazí řádek textu *„Please fill in the following field:“* následovaný světle šedou ohraničenou oblastí označenou *MyTag*. Zástupný text *Enter your text here* se zobrazí ve světle šedé barvě, dokud uživatel nezačne psát.

## Závěr

Nyní víte, jak **vložit ovládací prvek prostého textu** do dokumentu Word pomocí Aspose.Words pro .NET. Tutoriál pokryl inicializaci `Document`, vložení `StructuredDocumentTag` typu `PlainText` a přizpůsobení jeho názvu, tagu a zástupného textu. Porozuměním možnostem `SdtAppearance` a běžným úskalím můžete sebejistě vytvářet formuláře, šablony a automatizované zprávy, které využívají editovatelné ovládací prvky.

### Co dál?

- Prozkoumejte další typy SDT, jako jsou `RichText` nebo `ComboBox` pro rozbalovací seznamy.  
- Kombinujte více ovládacích prvků v tabulkách nebo je opakujte pomocí `RepeatingSection`.  
- Použijte `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` k programovému čtení nebo úpravě hodnot ovládacích prvků.

Neváhejte experimentovat s výše uvedenými variantami a začlenit tento vzor do vašich rozsáhlejších pipeline pro generování dokumentů. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Jak vytvořit ovládací prvek v C# pomocí Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Vytvořit nový dokument Word a vložit ovládací prvek v C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Přidat obsah pomocí Document Builder v Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}