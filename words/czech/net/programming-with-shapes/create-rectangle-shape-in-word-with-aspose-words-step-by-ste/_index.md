---
category: general
date: 2026-02-18
description: Vytvořte obdélníkový tvar pomocí Aspose.Words a naučte se, jak přidat
  stín, nastavit velikost tvaru a uložit dokument Word během několika minut.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: cs
og_description: Vytvořte obdélníkový tvar v souboru Word, naučte se, jak přidat stín,
  nastavit velikost tvaru a uložit dokument pomocí Aspose.Words v C#.
og_title: Vytvořte obdélníkový tvar ve Wordu – Kompletní tutoriál Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Vytvořte obdélníkový tvar ve Wordu pomocí Aspose.Words – krok za krokem průvodce
url: /cs/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

names: keep.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru ve Wordu s Aspose.Words – krok za krokem průvodce

Už jste někdy potřebovali **vytvořit obdélníkový tvar** v souboru Word, ale nebyli jste si jisti, kde začít? Nejste jediní – vývojáři se často ptají: „jak přidat stín k tvaru a zároveň zachovat editovatelnost dokumentu?“ V tomto tutoriálu na to odpovíme a také vám ukážeme **jak přidat stín**, **nastavit velikost tvaru** a **uložit Word dokument** v jednom plynulém postupu.

Provedeme vás vším, co potřebujete, od inicializace nového dokumentu (ano, to je první krok k **jak vytvořit dokument**) až po uložení finálního *.docx* na disk. Žádné externí odkazy, jen samostatný příklad, který můžete zkopírovat a vložit do Visual Studia a spustit ještě dnes.

---

## Požadavky

- .NET 6+ (nebo .NET Framework 4.7+). Aspose.Words funguje s jakýmkoli moderním .NET runtime.
- Platná licence Aspose.Words (nebo bezplatný evaluační klíč) – jinak se zobrazí vodoznak.
- Visual Studio, Rider nebo jakýkoli C# editor, který preferujete.
- Základní znalost C# – nic složitého, jen schopnost spustit konzolovou aplikaci.

> **Tip:** Pokud používáte Mac, stejný kód běží pod .NET 6 s VS Code – jen se ujistěte, že odkazujete na NuGet balíček `Aspose.Words`.

## Krok 1: Inicializace dokumentu – základ **jak vytvořit dokument**

Než budeme moci něco kreslit, potřebujeme prázdné plátno. Aspose.Words tomu říká `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Proč je to důležité:** Objekt `Document` představuje celý soubor *.docx*. Všechny tvary, odstavce a sekce, které přidáte, se stávají potomky tohoto objektu. Začátek s čistým dokumentem zajišťuje, že žádné skryté styly nebudou zasahovat do vašeho obdélníku.

## Krok 2: Definice obdélníku a **nastavení velikosti tvaru**

Obdélník je jen `Shape` s `ShapeType.Rectangle`. Poskytneme mu explicitní rozměry, aby vypadal přesně podle očekávání.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Co čísla znamenají:** Aspose.Words používá body (1 pt = 1/72 in). Upravit hodnoty tak, aby vyhovovaly vašemu rozvržení; pro typickou stránku A4 je 200 pt pohodlná šířka.

## Krok 3: **Jak přidat stín** – aby tvar vynikl

Stíny poskytují vizuální náznak, že je tvar „zvednutý“ od stránky. Vlastnost `Shadow` vám umožní upravit barvu, vzdálenost, průhlednost a rozostření.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Proč použít průhlednost?** Plně neprůhledný stín může vypadat drsně. Nastavením na 0,4 získáte jemný a profesionální efekt.

## Krok 4: Umístění obdélníku – inline tok s okolním textem

Pokud chcete, aby se tvar choval jako znak v odstavci, nastavte jeho `WrapType` na `Inline`. To udržuje rozvržení předvídatelné, zejména když je dokument později upravován.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Hraniční případ:** Pokud potřebujete, aby obdélník plaval nad textem (např. vodoznak), změňte `WrapType` na `Square` nebo `BehindText`.

## Krok 5: Vložení tvaru do těla dokumentu

Nyní skutečně umístíme obdélník do prvního odstavce. Pokud dokument zatím neobsahuje žádný obsah, `FirstParagraph` se vytvoří automaticky.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Tip:** Můžete také nejprve vytvořit nový odstavec a pak připojit tvar – užitečné, když potřebujete okolní text.

## Krok 6: **Uložit Word dokument** – poslední krok

Když je vše na svém místě, uložení souboru je jednorázový řádek. Vyberte libovolnou cestu; příklad používá zástupný znak, který byste měli nahradit svou vlastní složkou.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Výsledek:** Otevřete vygenerovaný *.docx* v Microsoft Word. Uvidíte černě stínovaný obdélník, široký 200 pt a vysoký 100 pt, umístěný inline s prvním odstavcem.

## Očekávaný výstup

Když otevřete **ShadowShape.docx**, dokument zobrazí:

- Jeden odstavec obsahující obdélníkový tvar.
- Obdélník má jemný černý stín posunutý o 5 pt.
- Velikost tvaru odpovídá rozměrům nastaveným v Kroku 2.
- Žádný další text se neobjeví, pokud jej nepřidáte ručně.

Pokud se tvar neobjeví, zkontrolujte, že odkazujete na správnou verzi Aspose.Words a že je vaše licence (nebo zkušební verze) aktivní.

## Časté otázky a varianty

| Question | Answer |
|----------|--------|
| *Mohu změnit barvu stínu na něco jiného než černou?* | Určitě—nastavte `rectangleShape.Shadow.Color = Color.Blue;` nebo libovolnou `System.Drawing.Color`. |
| *Co když potřebuji větší obdélník?* | Upravte hodnoty `Width` a `Height`. Pamatujte, že jsou v bodech; 72 pt = 1 in. |
| *Je možné umístit tvar na absolutní pozici?* | Ano—použijte `WrapType = WrapType.Absolute` a nastavte vlastnosti `Top`/`Left`. |
| *Funguje to s .NET Core?* | Ano. Aspose.Words je multiplatformní; stačí nainstalovat NuGet balíček pro .NET Standard. |
| *Mohu přidat text uvnitř obdélníku?* | Ne přímo; museli byste vložit tvar `TextBox` místo obyčejného obdélníku. |

## Kompletní funkční příklad (připravený ke kopírování a vložení)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Spusťte program, přejděte do `C:\Temp\ShadowShape.docx` a uvidíte obdélník se stínem přesně tak, jak je popsáno.

## Závěr

Nyní víte, jak **vytvořit obdélníkový tvar** v souboru Word pomocí Aspose.Words, jak **nastavit velikost tvaru**, **přidat stín** a nakonec **uložit Word dokument** s těmito změnami. Celý proces – od **jak vytvořit dokument** až po uložení výsledku – se vejde do několika řádků C# a lze jej rozšířit pro složitější rozvržení.

Jste připraveni na další výzvu? Zkuste nahradit obdélník tvarem se zaoblenými rohy, experimentujte s různými barvami stínů nebo vložte tvar do buňky tabulky. Každá úprava posiluje stejné základní koncepty, které jsme zde probírali.

Pokud se vám tento průvodce líbil, sdílejte ho, zanechte komentář s vlastními variantami nebo prozkoumejte naše další tutoriály o automatizaci Wordu, například vkládání obrázků nebo generování tabulek pomocí Aspose.Words. Šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}