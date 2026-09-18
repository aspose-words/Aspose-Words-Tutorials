---
category: general
date: 2026-09-18
description: Vytvořte prázdný dokument Word a skryjte eliptický tvar pomocí Aspose.Words.
  Naučte se, jak v aplikaci Word skrýt tvar, jak vložit elipsu a jak rychle vytvořit
  skrytý tvar.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: cs
lastmod: 2026-09-18
og_description: Vytvořte prázdný dokument Word a skryjte eliptický tvar ve Wordu.
  Tento průvodce vám krok za krokem ukáže, jak vložit elipsu, skrýt tvar ve Wordu
  a vytvořit skrytý tvar pomocí Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Vytvořte prázdný dokument Word se skrytým eliptickým tvarem
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Vytvořte prázdný dokument Word se skrytým eliptickým tvarem
url: /cs/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte prázdný dokument Word s skrytým eliptickým tvarem

Pokud potřebujete **vytvořit prázdný dokument Word**, který obsahuje tvar, jenž nechcete zobrazit v rozvržení, tento návod vám ukáže, jak to provést přesně. Pomocí Aspose.Words pro .NET můžete programově vložit elipsu a poté ji skrýt, takže dokument zůstane vizuálně prázdný, ale stále bude obsahovat data tvaru.

V tomto tutoriálu se naučíte:

* jak **vytvořit prázdný dokument Word**,
* jak **vložit elipsu** pomocí `DocumentBuilder`,
* jak **skrýt tvar ve Wordu**, aby neovlivňoval stránku,
* jak **vytvořit skryté tvary** pro pozdější zpracování.

Postupy fungují s .NET 6+ a nejnovější verzí Aspose.Words (23.9 v době psaní). Není vyžadována žádná další instalace Office.

## Požadavky

* Visual Studio 2022 (nebo jakékoli C# IDE)
* .NET 6 SDK nebo novější
* NuGet balíček Aspose.Words pro .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
* Základní znalost C# a konceptů Word dokumentů

## Krok 1: Vytvořte prázdný dokument Word

Prvním krokem je vytvořit objekt `Document`. Tento objekt představuje prázdný soubor `.docx` a je základem pro všechny další operace.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Vytvoření **prázdného dokumentu Word** vám poskytne čisté plátno – žádné odstavce, žádné sekce, jen základní struktura balíčku. To je ideální výchozí bod, když potřebujete pouze skrytý tvar a nic jiného.

## Krok 2: Inicializujte DocumentBuilder

`DocumentBuilder` poskytuje pohodlné API pro přidávání obsahu do `Document`. Funguje jako kurzor, který se pohybuje dokumentem.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder automaticky vytvoří výchozí první sekci a odstavec, takže můžete začít vkládat tvary, aniž byste museli ručně přidávat sekce.

## Krok 3: Vložte eliptický tvar

Nyní **vložíme elipsu** pomocí metody `InsertShape`. Metoda přijímá výčtový typ `ShapeType`, šířku a výšku (v bodech).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Proč elipsa? Elipsa je vektorový tvar, který lze skrýt, aniž by ovlivnil tok okolního textu. Šířka 100 pt a výška 50 pt jsou libovolné; můžete je upravit podle potřeb vašeho pozdějšího zpracování.

## Krok 4: Skryjte tvar, aby se neobjevil v rozvržení

Pro **skrytí tvaru ve Wordu** nastavte vlastnost `Hidden` na objektu `Shape` na `true`. Když se dokument otevře v Microsoft Word, tvar bude neviditelný a nezabere místo v rozvržení.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

Příznak `Hidden` je uložen v XML tvaru (`<w:hidden/>`). Word tento atribut respektuje během vykreslování, což je důvod, proč dokument vypadá naprosto prázdně, i když tvar existuje.

### Tip

Pokud budete později potřebovat tvar znovu zobrazit, jednoduše nastavte `ellipse.Hidden = false;` a dokument uložte.

## Krok 5: Uložte dokument se skrytým tvarem

Nakonec dokument uložte na disk. Soubor bude běžný `.docx`, který může otevřít jakýkoli procesor Word.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Uložený soubor `HiddenEllipse.docx` je **vytvořený prázdný dokument Word**, který obsahuje skrytou elipsu. Po otevření v Microsoft Word se zobrazí prázdná stránka, ale tvar je stále přítomen ve struktuře Open XML.

## Kompletní funkční příklad

Níže je kompletní, samostatný program, který můžete zkopírovat, vložit a spustit.

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
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Očekávaný výstup**

* V adresáři `C:\Temp` se objeví soubor `HiddenEllipse.docx`.
* Otevřením souboru v Microsoft Word se zobrazí zcela prázdná stránka.
* Pokud dokument prozkoumáte pomocí Open XML SDK nebo zip prohlížeče, najdete element `<w:shape>` s `<w:hidden/>` uvnitř části dokumentu.

## Časté otázky a okrajové případy

### Co když se tvar stále zobrazuje?

* Ujistěte se, že používáte Aspose.Words 23.9 nebo novější – starší verze měly chybu, kdy se `Hidden` ignorovalo u některých typů tvarů.
* Ověřte, že nepoužíváte žádné další formátování (např. `WrapType`), které by nutilo tvar zabírat místo v rozvržení.

### Mohu skrýt i jiné typy tvarů?

Ano. Stejná vlastnost `Hidden` funguje pro `ShapeType.Rectangle`, `ShapeType.Picture` atd. Stačí nahradit `ShapeType.Ellipse` požadovaným typem.

### Jak později vypsat skryté tvary?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Tento úryvek prochází všechny tvary a vypisuje ty, které jsou skryté, což je užitečné pro **vytváření skrytých tvarů** v pracovních postupech, kde je později potřeba je zpracovat nebo odhalit.

## Závěr

Nyní víte, jak **vytvořit prázdný dokument Word**, **vložit elipsu** a **skrýt tvar ve Wordu**, abyste získali **skrytý tvar**, který zůstane neviditelný pro čtenáře. Tato technika je užitečná pro ukládání metadat, záložek nebo vlastního XML v dokumentu, aniž by se změnil jeho vizuální vzhled.

### Další kroky

* Prozkoumejte **podmíněné skrývání tvaru** na základě obsahu dokumentu.
* Naučte se **odhalovat tvar** při generování finální verze dokumentu.
* Kombinujte skryté tvary s **vlastními vlastnostmi dokumentu** pro vložení strojově čitelných dat.

Neváhejte experimentovat s různými typy tvarů, velikostmi a logikou skrytí, aby vyhovovaly vašemu automatizačnímu scénáři. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s krok‑za‑krokem vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vlastních projektech.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}