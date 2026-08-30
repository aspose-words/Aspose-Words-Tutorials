---
category: general
date: 2026-07-23
description: Vytvořte prázdný dokument Word a přidejte obdélníkový tvar v C#. Naučte
  se, jak vkládat tvary a seskupovat tvary ve Wordu pomocí Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: cs
lastmod: 2026-07-23
og_description: Vytvořte prázdný dokument Word v C# a naučte se, jak vkládat tvary,
  přidat obdélníkový tvar a seskupit tvary ve Wordu pomocí Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Vytvořte prázdný dokument Word se seskupenými obdélníky – C# tutoriál
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Vytvořte prázdný dokument Word se seskupenými obdélníky – C# průvodce
url: /cs/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření prázdného dokumentu Word se seskupenými obdélníky – průvodce C#

Už jste někdy potřebovali **vytvořit prázdný dokument Word**, který již obsahuje sadu tvarů, ale nebyli jste si jisti, jak je hezky seskupit? Nejste v tom sami. V mnoha scénářích reportování nebo generování šablon chcete čisté plátno s několika obdélníky fungujícími jako zástupné objekty a chcete, aby se pohybovaly společně jako jedna jednotka.

V tomto tutoriálu projdeme přesně kroky k **vytvoření prázdného dokumentu Word**, **přidání obdélníkového tvaru** a následnému **seskupení tvarů ve Wordu** pomocí knihovny Aspose.Words. Na konci budete mít připravený `.docx` soubor, kde jsou oba obdélníky součástí skupiny, takže jakékoli následné umístění nebo změna velikosti ovlivní oba najednou.  

Také odpovíme na časté otázky „**how to insert shapes**“ a „**how to group shapes**“, které se objevují na fórech a Stack Overflow. Žádná externí dokumentace není potřeba – vše, co potřebujete, je zde.

---

## Požadavky

- .NET 6 nebo novější (kód se také kompiluje s .NET Core)  
- Aspose.Words pro .NET (NuGet balíček `Aspose.Words`)  
- Základní znalost syntaxe C# (pokud jste už napsali „Hello World“, máte vše v pořádku)  

Pokud jste ještě nenainstalovali Aspose.Words, spusťte:

```bash
dotnet add package Aspose.Words
```

A to je vše – žádné extra DLL, žádné COM interop, jen čistý odkaz na NuGet.

---

## Krok 1: Vytvoření prázdného dokumentu Word a inicializace builderu

Prvním krokem je vytvořit prázdný objekt `Document`. Představte si ho jako čistý list papíru. Pak připojíme `DocumentBuilder`, což je praktický nástroj, který Aspose poskytuje pro vkládání obsahu.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Proč je to důležité:** Bez `DocumentBuilder` byste museli ručně manipulovat se stromem uzlů na nízké úrovni, což je náchylné k chybám. Builder abstrahuje XML složitosti souboru `.docx`.

---

## Krok 2: Jak vložit tvary – nejprve přidejte kontejner skupiny

Aspose vám umožňuje vložit *group shape*, který může později obsahovat další tvary. Toto je základ pro **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Tip:** Skupina sama o sobě je neviditelná, dokud nepřidáte podřízené tvary, takže v výsledném dokumentu neuvidíte žádné artefakty až do dalšího kroku.

---

## Krok 3: Přidání obdélníkového tvaru – skutečné viditelné objekty

Nyní **přidáme obdélníkový tvar** dvakrát, každý s vlastní velikostí. Metoda `InsertShape` přijímá `ShapeType` a rozměry v bodech (1 pt ≈ 1/72 palce).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Proč obdélníky?** Jsou to nejjednodušší geometrické tvary, ideální pro zástupné objekty, napodobení tlačítkových UI nebo jednoduché grafické prvky.

---

## Krok 4: Jak seskupit tvary – připojit obdélníky ke skupině

Po vytvoření obdélníků nyní **jak seskupit tvary** přidáním jako podřízených k group shape, který jsme vložili dříve.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Co se děje pod kapotou?** Group shape se stane rodičovským uzlem ve stromu XML dokumentu. Přesunutí skupiny přesune oba obdélníky najednou a zachová jejich relativní pozice.

---

## Krok 5: Uložení dokumentu – nyní máte Word soubor se seskupenými tvary

Nakonec dokument uložíme na disk. Změňte cestu na umístění, které ve vašem počítači existuje.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

To je celý program. Spusťte jej, otevřete `GroupShape.docx` a uvidíte dva obdélníky ležící vedle sebe. Pokud vyberete jeden, celá skupina se zvýrazní – přesně to, co má **group shapes word** dělat.

---

## Kompletní zdrojový kód na jednom místě

Pro pohodlí zde máte kompletní, připravený k zkopírování příklad:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Očekávaný výstup:** Otevření `GroupShape.docx` zobrazí prázdnou stránku se dvěma seskupenými obdélníky. Výběrem jednoho obdélníku se automaticky vybere i druhý, což potvrzuje úspěšné seskupení.

---

## Časté otázky a řešení okrajových případů

### Co když potřebuji více než dva tvary?

Stačí nadále volat `builder.InsertShape(...)` a `group.AppendChild(...)` pro každý nový tvar. Skupina může obsahovat libovolný počet podřízených.

### Můžu nastavit barvu výplně nebo okraj obdélníků?

Samozřejmě. Po vytvoření obdélníku můžete upravit jeho `FillColor`, `OutlineColor` a `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Jak přesunu celou skupinu po jejím vytvoření?

Použijte vlastnosti skupiny `Left` a `Top`, měřené v bodech:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### Co škálování skupiny?

Nastavte `group.Width` a `group.Height` nebo použijte `group.ScaleX` / `group.ScaleY`. Podřízené obdélníky si zachovají své proporce vzhledem ke skupině.

### Funguje to i se staršími soubory .doc?

Aspose.Words abstrahuje formát souboru, takže stejný kód funguje pro `.doc` i `.docx`. Jediným omezením je, že některé novější funkce tvarů mohou být při ukládání do staršího binárního formátu zmenšeny.

---

## Profesionální tipy pro produkční kód

- **Uvolnění zdrojů** – Zabalte `Document` do bloku `using`, pokud pracujete s velkými soubory, aby se paměť rychle uvolnila.  
- **Zpracování chyb** – Zachyťte `Aspose.Words.Fonts.FontSettingsException`, pokud plánujete vkládat vlastní fonty.  
- **Výkon** – Při vkládání mnoha tvarů dočasně vypněte aktualizace rozvržení pomocí `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` a po dokončení jej znovu povolte.

---

## Závěr

Nyní víte, **jak vytvořit prázdný dokument Word**, **přidat obdélníkový tvar** a **seskupit tvary ve Wordu** pomocí Aspose.Words v C#. Příklad pokrývá základní kroky „**how to insert shapes**“ a „**how to group shapes**“, vysvětluje, proč každá řádka existuje, a také se dotýká přizpůsobení, okrajových případů a nejlepších postupů.

Dále můžete zkoumat **how to insert images**, **add text inside grouped shapes**, nebo **export the document to PDF** – všechny tyto postupy používají stejný vzor s `DocumentBuilder` a manipulací tvarů. Pokračujte v experimentování; Aspose API je dostatečně bohaté na to, aby zvládlo téměř jakýkoli scénář automatizace Wordu, který si dokážete představit.

Šťastné kódování a neváhejte zanechat komentář, pokud narazíte na potíže!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}