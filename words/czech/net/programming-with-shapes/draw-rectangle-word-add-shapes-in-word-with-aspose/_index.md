---
category: general
date: 2026-07-29
description: Nakreslete obdélník ve Wordu pomocí Aspose.Words. Naučte se, jak přidat
  tvar obdélníku, tvar čáry a spravovat více tvarů ve Wordu v jednom dokumentu.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: cs
lastmod: 2026-07-29
og_description: Nakreslete obdélník ve Wordu pomocí Aspose.Words. Postupujte podle
  tohoto krok‑za‑krokem návodu, jak přidat tvar obdélníku, přidat tvar čáry a snadno
  pracovat s více tvary ve Wordu.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: kreslit obdélník ve Wordu – Ovládněte přidávání tvarů ve Wordu
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Kreslit obdélník ve Wordu – Přidat tvary ve Wordu s Aspose
url: /cs/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Kompletní průvodce přidáváním tvarů ve Wordu

Už jste se někdy zamysleli, jak **draw rectangle word** dokumenty bez každého otevírání UI? Nejste sami. Mnoho vývojářů potřebuje generovat soubory Word za běhu a nejjednodušší způsob je nechat knihovnu udělat těžkou práci. V tomto tutoriálu vám ukážeme přesně **jak přidat tvary** – konkrétně obdélník a čáru – pomocí Aspose.Words pro .NET a zaměříme se na frázi *draw rectangle word*, abyste se nikdy neztratili.

Představte si to jako mini‑ateliér, který žije ve vašem kódu. Na konci budete schopni **add rectangle shape**, **add line shape**, a dokonce je spojit do skupin **multiple shapes word**. Žádné UI, žádné ruční manipulace, jen čistý, opakovatelný C#.

## Co se naučíte

- Nastavit nový Word dokument pomocí Aspose.Words.  
- Vytvořit **GroupShape**, který může obsahovat několik objektů.  
- **Add rectangle shape** a **add line shape** uvnitř této skupiny.  
- Vložit seskupené tvary do těla dokumentu.  
- Uložit soubor a okamžitě vidět výsledek.  

Pokud vám vyhovuje základní C# a máte kopii Aspose.Words, jste připraveni. Žádné další NuGet balíčky nad rámec základní knihovny nejsou potřeba.

> **Tip:** Aspose.Words funguje s .NET 6, .NET 7 a .NET Framework 4.6+. Vyberte runtime, který odpovídá vašemu projektu.

![draw rectangle word example](https://example.com/placeholder-image.png "draw rectangle word – grouped shapes in a Word file")

## draw rectangle word – Nastavení dokumentu

Než budeme moci **draw rectangle word**, potřebujeme čisté plátno. Třída `Document` je to plátno; `DocumentBuilder` je náš štětec.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Tyto dva řádky nám vytvoří čerstvý, v‑paměti `.docx`. Zatím se nic neukládá na disk, což znamená, že můžeme experimentovat bez zaplňování souborového systému.

## Jak přidat tvary – Vytvoření kontejneru GroupShape

Když chcete, aby **multiple shapes word** fungovaly jako jediná jednotka – pohybovaly se společně, otáčely se společně – zabalíte je do `GroupShape`. Představte si skupinu jako složku, která obsahuje další tvary.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Proč skupina? Protože později můžete chtít **add rectangle shape** a **add line shape** a pak je přesunout společně. Bez skupiny byste museli každému tvaru měnit pozici samostatně.

## add rectangle shape – Vložení obdélníku do skupiny

Nyní, když kontejner existuje, pojďme **add rectangle shape**. Obdélník je `Shape`, jehož `ShapeType` je `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Všimněte si, že hodnoty `Left` a `Top` jsou relativní k počátku skupiny, ne k stránce. To usnadňuje přesné zarovnání tvarů. Obdélník se objeví blízko levého horního rohu skupiny.

## add line shape – Přidání čáry do stejné skupiny

Čára je jen další `Shape`, ale její `ShapeType` je `Line`. Umístíme ji pod obdélník.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Protože výška čáry je nula, vlastnost `Top` určuje, kde čára leží vertikálně. `Width` řídí, jak dlouho se čára rozprostírá horizontálně.

## multiple shapes word – Vložení skupiny do těla dokumentu

Máme skupinu, která nyní obsahuje **add rectangle shape** a **add line shape**. Posledním krokem je vložit celou tuto skupinu do dokumentu.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` umístí skupinu přesně tam, kde je aktuálně umístěn `DocumentBuilder`. Pokud ji potřebujete v konkrétním odstavci, nejprve posuňte builder pomocí `builder.MoveToParagraph(index)`.

## Ukládání výsledku – Zobrazení výstupu draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Otevřete vygenerovaný soubor v Microsoft Word a uvidíte jedinou skupinu obsahující obdélník a čáru. Můžete na skupinu kliknout, přetáhnout ji nebo ji dokonce změnit velikost – všechny tvary se pohybují společně. To je síla **multiple shapes word**.

### Očekávaný výstup

- Soubor `.docx` pojmenovaný `GroupShape.docx`.  
- Jedna stránka se seskupeným obdélníkem (120 × 80 pt) blízko levého horního rohu.  
- Horizontální čára (150 pt dlouhá) umístěná těsně pod obdélníkem.  
- Oba tvary jsou vybratelné jako jeden objekt.

Pokud dvojkliknete na skupinu, Word vám umožní upravit každý tvar samostatně – ideální pro jemné doladění.

## Časté otázky a okrajové případy

**Co když potřebuji více než dva tvary?**  
Jednoduše pokračujte voláním `group.AppendChild(yourShape)` pro každý další objekt. Skupina může obsahovat libovolný počet tvarů, což ji činí ideální pro složité diagramy.

**Mohu změnit barvu výplně obdélníku?**  
Určitě. Po vytvoření obdélníku nastavte `rectangle.FillColor = System.Drawing.Color.LightBlue;`. To funguje pro jakýkoli tvar, který podporuje výplň.

**Musím nastavit `Height = 0` pro čáru?**  
Ano, pro přímou horizontální čáru by výška měla být nula. Pro vertikální čáru nastavte `Width = 0` a dejte `Height` kladnou hodnotu.

**Bude to fungovat s .doc soubory (Word 97‑2003)?**  
Aspose.Words může ukládat do staršího formátu `.doc`, ale některé moderní funkce tvarů mohou být omezené. Pro plnou věrnost používejte `.docx`.

**Jak otočím celou skupinu?**  
Můžete nastavit `group.Rotation = 45;` (stupně) před jejím vložením. Rotace se aplikuje na každý podřazený tvar.

## Shrnutí – Jak programově přidávat tvary do Wordu

- **draw rectangle word** začíná vytvořením `Document` a `DocumentBuilder`.  
- Vytvořte **GroupShape**, která bude obsahovat **multiple shapes word**.  
- **add rectangle shape** a **add line shape** jsou přidány do skupiny.  
- Vložte skupinu do těla pomocí `builder.InsertNode`.  
- Uložte soubor a otevřete jej pro ověření vizuálního výsledku.

To je celý pracovní postup, zabalený do jediného, snadno čitelného výpisu kódu.

## Další kroky a související témata

Nyní, když víte **how to add shapes**, zvažte prozkoumání:

- **add rectangle shape** s zaoblenými rohy (`ShapeType.Rectangle` + `CornerRadius`).  
- Stylování čar s různými vzory čárkování (`line.LineFormat.DashStyle`).  
- Vkládání obrázků vedle tvarů pro bohatší reporty.  
- Použití **multiple shapes word** k tvorbě diagramů toku nebo jednoduchých UML diagramů.

Každé z těchto témat přirozeně navazuje na základ, který zde položili, a všechny následují stejný vzor: vytváření tvarů, jejich konfiguraci a případné seskupování.

---

Šťastné kódování! Pokud narazíte na podivnosti nebo máte zajímavý případ použití, který chcete sdílet, zanechte komentář níže. Vaše zpětná vazba nám všem pomáhá ovládnout umění **draw rectangle word** a dál.

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit obdélníkový tvar ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Vytvořit obdélníkový tvar ve Wordu s Aspose.Words – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Vložit tvary do Word dokumentů pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}