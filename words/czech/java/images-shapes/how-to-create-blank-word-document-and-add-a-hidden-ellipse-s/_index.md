---
category: general
date: 2026-09-21
description: Vytvořte prázdný dokument Word se skrytou elipsou pomocí C#. Naučte se,
  jak v Wordu skrýt tvar a programově vytvořit skrytý tvar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: cs
lastmod: 2026-09-21
og_description: Vytvořte prázdný dokument Word se skrytou elipsou pomocí C#. Tento
  průvodce ukazuje, jak v aplikaci Word skrýt tvar a programově vytvářet skryté tvary.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Vytvořte prázdný dokument Word s skrytým eliptickým tvarem v C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Jak vytvořit prázdný dokument Word a přidat skrytou elipsu v C#
url: /cs/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit prázdný dokument Word a přidat skrytou eliptickou tvar v C#

Pokud potřebujete **vytvořit prázdný dokument Word**, který obsahuje neviditelnou grafiku, tento průvodce vám přesně ukáže, jak na to. Na konci tutoriálu budete mít soubor .docx, který vypadá prázdně, ale ve skutečnosti obsahuje eliptický tvar, který je skrytý v rozvržení.

Použijeme Aspose.Words pro .NET k vytvoření dokumentu, vložení elipsy, jejímu skrytí a uložení souboru. Kroky také zahrnují **jak vytvořit elipsu** objektů, správný způsob **skrytí tvaru ve Wordu** a jak **vytvořit skrytý tvar** kód, který funguje v jakémkoli .NET projektu.

## Požadavky

* .NET 6.0 SDK nebo novější nainstalováno  
* Visual Studio 2022 (nebo jakýkoli editor C#)  
* Licence Aspose.Words pro .NET nebo bezplatná zkušební kopie  
* Základní znalost syntaxe C#  

Žádné další balíčky NuGet nejsou vyžadovány nad rámec `Aspose.Words`.

## Vytvoření prázdného dokumentu Word pomocí Aspose.Words

Prvním krokem je vygenerovat prázdný soubor Word. To nám poskytne čisté plátno, kam můžeme později vložit skrytou grafiku.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Proč začínáme s prázdným dokumentem** – Začátek s prázdným souborem zaručuje, že žádný nechtěný obsah nezasahuje do skrytého tvaru. Také udržuje velikost souboru na minimu, což je užitečné, když je dokument později použit jako šablona.

## Jak vytvořit elipsu uvnitř prázdného dokumentu

Dále potřebujeme `DocumentBuilder` k přidání obsahu. Builder nám umožňuje umístit tvary přesně tam, kde je chceme.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Vysvětlení** – `ShapeType.Ellipse` říká Aspose.Words, aby nakreslil kruhovitý tvar. Šířka a výška jsou měřeny v bodech (1 pt ≈ 1/72 palce). Tyto hodnoty můžete upravit podle svých návrhových potřeb.

## Skrytí tvaru ve Wordu, aby se neobjevil v rozvržení

Tvar, který je skrytý, stále existuje v XML dokumentu, což může být užitečné pro metadata, podmíněné formátování nebo pozdější programové úpravy. Pro jeho skrytí nastavíme vlastnost `Hidden` na `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Proč skrýt tvar** – Skryté tvary jsou ignorovány layoutovým enginem, takže stránka vypadá zcela prázdně. Data tvaru však přetrvávají, což může být užitečné pro ukládání značek, záložek nebo vlastního XML, které mohou číst následné procesy.

## Uložení dokumentu se skrytým tvarem

Nakonec zapíšeme soubor na disk. Uložený `.docx` se otevře v Microsoft Wordu bez viditelného obsahu, přesto je skrytá elipsa stále přítomna.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Ověření** – Otevřete vygenerovaný soubor ve Wordu, poté stiskněte `Alt+F9` pro přepnutí kódů polí a `Ctrl+A` → `Ctrl+Shift+F9` pro zobrazení skrytých objektů. V XML dokumentu (`word/document.xml`) uvidíte elipsu, ale na stránce nic.

---

## Kompletní, spustitelný příklad

Níže je kompletní program, který můžete zkopírovat a vložit do nového konzolového projektu. Obsahuje všechny `using` direktivy a metodu `Main`, takže jej můžete spustit bez dalšího nastavení.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Očekávaný výstup** – Po spuštění programu konzole vypíše cestu k souboru a výsledný Word soubor neobsahuje žádné viditelné objekty. Pokud dokument prozkoumáte pomocí nástroje zip (`.docx` je zip archiv), najdete prvek `<w:pict>` popisující elipsu uvnitř `word/document.xml`.

---

## Běžné varianty a okrajové případy

| Scénář | Co změnit | Proč je to důležité |
|----------|----------------|----------------|
| **Různý tvar** | Nahraďte `ShapeType.Ellipse` za `ShapeType.Rectangle`, `ShapeType.Line` atd. | Umožňuje skrýt jiné grafiky při zachování stejného pracovního postupu. |
| **Více skrytých tvarů** | Zavolejte `InsertShape` několikrát a nastavte `Hidden = true` u každého. | Užitečné pro vložení kolekce značek nebo zástupných objektů. |
| **Podmíněná viditelnost** | Použijte `shape.Visible = false` spolu s `shape.Hidden = true` pro extra bezpečnost. | Některé starší verze Wordu respektují `Visible` jinak; nastavení obojího pokrývá všechny případy. |
| **Ukládání do proudu** | Nahraďte `doc.Save(path)` za `doc.Save(stream, SaveFormat.Docx)`. | Umožňuje odeslat dokument přímo přes HTTP nebo jej uložit do databáze. |
| **Aplikace stylu** | Po vložení upravte `ellipse.FillColor`, `ellipse.LineWeight` atd. před skrytím. | Styl tvaru je zachován v XML, což může být užitečné pro pozdější odhalení. |

**Tip:** Vždy testujte skrytý tvar na cílové verzi Wordu (např. Word 2019, Word 365), protože se občas objeví problémy s vykreslováním, když skryté objekty interagují s komplexními rozvrženími stránek.

---

## Často kladené otázky

**Q: Ovlivňuje skrytí tvaru velikost dokumentu?**  
A: XML tvaru přidá několik stovek bajtů, což je pro většinu případů zanedbatelné. Soubor zůstává v podstatě stejně velký jako skutečně prázdný dokument.

**Q: Můžu tvar později programově odkrýt?**  
A: Ano. Načtěte dokument, najděte tvar (`doc.GetChildNodes(NodeType.Shape, true)`) a nastavte `shape.Hidden = false`.

**Q: Objeví se skrytý tvar při tisku?**  
A: Ne. Skryté objekty jsou vyloučeny z tiskového rozvržení, takže tištěná stránka zůstane prázdná.

**Q: Je tento přístup kompatibilní pouze s Office Open XML (OOXML)?**  
A: Vlastnost `Hidden` je součástí specifikace OOXML, takže jakýkoli procesor Wordu, který plně implementuje OOXML (Word, LibreOffice, Google Docs), bude respektovat skrytý příznak.

---

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **jak vytvořit elipsu**, **skrýt tvar ve Wordu** a **vytvořit skrytý tvar** pomocí Aspose.Words pro .NET. Tutoriál pokryl celý životní cyklus – od inicializace prázdného souboru po vložení, skrytí a uložení tvaru – včetně ověřovacích kroků a běžných variant.

Další kroky, které můžete prozkoumat:

* Přidání skrytých textových polí pro metadata (technika `hide shape in word` aplikovaná na text)  
* Použití vlastních XML částí k ukládání strukturovaných dat vedle skrytých tvarů  
* Převod dokumentu se skrytým tvarem do PDF při zachování skrytých prvků  

Experimentujte s různými tvary a nastavením viditelnosti, abyste viděli, jak může skrytý obsah sloužit jako lehká datová úložiště uvnitř souborů Word.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s podrobným vysvětlením, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}