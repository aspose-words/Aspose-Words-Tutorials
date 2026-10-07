---
category: general
date: 2026-02-26
description: Vytvořte obdélníkový tvar ve Wordu pomocí Aspose.Words a naučte se, jak
  přidat tvar do Wordu, aplikovat na něj stín a nastavit průhlednost během několika
  minut.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: cs
og_description: Vytvořte obdélníkový tvar ve Wordu pomocí Aspose.Words. Naučte se
  přidávat tvar do Wordu, aplikovat stín na tvar a rychle nastavit průhlednost tvaru.
og_title: Vytvořte obdélníkový tvar ve Wordu – Kompletní průvodce Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Vytvoření obdélníkového tvaru ve Wordu – Kompletní průvodce Aspose.Words
url: /cs/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru ve Wordu – Kompletní průvodce Aspose.Words

Už jste někdy potřebovali **vytvořit obdélníkový tvar** v dokumentu Word, ale nevedeli jste, kde začít? Nejste v tom sami – mnoho vývojářů narazí na tuto překážku při automatizaci reportů nebo faktur. V tomto tutoriálu vás provedeme kompletním, připraveným příkladem, který ukazuje, jak **přidat tvar do Wordu**, aplikovat decentní stín a řídit průhlednost tvaru, a to vše pomocí Aspose.Words pro .NET.

Na konci průvodce budete mít soubor `.docx` obsahující čistý obdélník s vylepšeným stínem – ideální pro branding, zvýraznění nebo jen pro profesionálnější vzhled dokumentu. Nepotřebujete žádné externí nástroje, stačí pár řádků C#.

## Co budete potřebovat

- **Aspose.Words pro .NET** (nejnovější verze k začátku 2026). Získáte ji z NuGet (`Install-Package Aspose.Words`).
- Vývojové prostředí .NET (Visual Studio, Rider nebo VS Code s rozšířením C#).
- Základní znalost syntaxe C# – nic složitého, jen běžné `using` direktivy a tvorba objektů.

Pokud už máte vše připravené, pojďme na to.

## Vytvoření obdélníkového tvaru – hlavní kroky

Níže je kompletní zdrojový kód. Zkopírujte jej do nového konzolového projektu, stiskněte **F5** a soubor `ShadowDemo.docx` se objeví ve vámi zadané složce.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Proč to funguje

- **`Document`** je vstupní bod; představuje celý Word soubor.
- **`Shape`** s `ShapeType.Rectangle` říká Aspose, že chceme obdélníkový kreslicí objekt.
- Nastavení **`Width`** a **`Height`** dává tvaru konkrétní rozměry; jinak by byl výchozí jako malý zástupný objekt.
- Objekt **`Shadow`** nám umožňuje doladit každý vizuální aspekt: rozostření, vzdálenost, směr, barvu, průhlednost a rozšíření. To je podstata *aplikace stínu na tvar*.
- Nakonec **`AppendChild`** vloží tvar do prvního odstavce dokumentu, což je nejjednodušší způsob, jak *přidat tvar do Wordu* bez práce s tabulkami nebo záhlavími.

Když otevřete `ShadowDemo.docx`, uvidíte šedý obdélník pohodlně umístěný v dokumentu, jehož stín směřuje dolů‑vpravo pod úhlem 45°. Stín není pevný blok; poloměr rozostření změkčuje hrany a průhlednost působí jako přirozený vržený stín, nikoli jako tvrdý překryv.

![vytvoření obdélníkového tvaru příklad](image.png "vytvoření obdélníkového tvaru se stínem ve Wordu pomocí Aspose.Words")

*(Obrázek výše ukazuje finální výsledek kódu.)*

## Přidání tvaru do Word dokumentu – možnosti umístění

Příklad používá **první odstavec**, protože je to nejrychlejší způsob, jak něco zobrazit. V reálných scénářích můžete chtít:

- Vložit tvar do konkrétní **sekce** nebo **záhlaví/patičky**.
- Umístit jej do **buňky tabulky** pro zarovnání s tabulkovými daty.
- Zabalit jej pomocí **textového obtékání** (např. `WrapType.Square`), aby se okolní text obtékal kolem obdélníku.

Zde je rychlá varianta, která umístí tvar do nového odstavce s vlastním stylem:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Tip:* Vždy přidejte tvar **po** nastavení jeho vlastností; jinak může být nutné zavolat `UpdateLayout` pro obnovení vizuálního vzhledu.

## Aplikace stínu na tvar – jemné doladění vzhledu

Stíny mohou dramaticky změnit estetiku dokumentu. Třída `Shadow` poskytuje několik vlastností:

| Vlastnost      | Co řídí                                            | Typické hodnoty |
|----------------|----------------------------------------------------|-----------------|
| `BlurRadius`   | Měkčení okrajů stínu                               | 2.0 – 10.0      |
| `Distance`     | Vzdálenost posunu stínu od tvaru                    | 1.0 – 8.0       |
| `Direction`    | Úhel ve stupních (0 = vlevo, 90 = nahoru)          | 0 – 360         |
| `Color`        | Barva stínu (libovolná `System.Drawing.Color`)    | Šedá, Černá, Vlastní |
| `Transparency`| Průhlednost (0 = plně neprůhledný, 1 = neviditelný) | 0.0 – 0.5       |
| `Spread`       | Rozšíření stínu před aplikací rozostření           | 0.0 – 1.0       |

Pokud chcete **jemný, profesionální vzhled**, držte `BlurRadius` kolem 4‑6 a `Transparency` blízko 0.2, stejně jako v ukázkovém kódu. Pro **dramatický efekt** zvyšte `Distance` na 6, nastavte `Direction` na 135° a snižte `Transparency` na 0.05.

## Nastavení průhlednosti tvaru a rozšíření stínu

Průhlednost se netýká jen stínu; můžete také učinit samotný obdélník částečně průhledným:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Kombinace poloprůhledného výplně a měkkého stínu často vytváří moderní UI dojem – skvělé pro dashboardy nebo designové mockupy vložené do reportů.

### Okrajové případy, na které si dát pozor

1. **Starší verze Wordu** (před 2007) nepodporují některé vlastnosti stínu. Pokud cílíte na soubory `.doc`, zvažte zjednodušení stínu (např. nastavit `BlurRadius` na 0).
2. **Displeje s vysokým DPI** mohou stín vykreslovat mírně odlišně. Otestujte ve cílovém prostředí, pokud je vizuální věrnost kritická.
3. **Překrývající se tvary** – Aspose vykresluje stíny v pořadí, v jakém jsou přidány. Vkládejte tvary od pozadí k popředí, abyste předešli nechtěnému překrytí.

## Uložení a ověření výsledku

Metoda `Document.Save` automaticky rozpozná výstupní formát podle přípony souboru. Pro **`.docx`** získáte formát Open XML, který rozumí většina moderních procesorů Wordu. Pokud potřebujete **PDF** verzi se stejným vizuálem, stačí změnit příponu:

```csharp
document.Save("ShadowDemo.pdf");
```

Otevření vygenerovaného `ShadowDemo.docx` (nebo `ShadowDemo.pdf`) by mělo zobrazit čistý **obdélník se stínem**, což potvrzuje, že jste úspěšně *vytvořili obdélníkový tvar* a *aplikovali stín na tvar* pomocí Aspose.Words.

## Často kladené otázky

**Q: Můžu použít jiný tvar, například elipsu?**  
A: Rozhodně. Zaměňte `ShapeType.Rectangle` za `ShapeType.Ellipse` (nebo jakýkoli jiný enum `ShapeType`). Vlastnosti stínu zůstávají stejné.

**Q: Co když potřebuji, aby byl obdélník klikací?**  
A: Můžete tvaru přiřadit hypertextový odkaz:

```csharp
rectangleShape.Href = "https://example.com";
```

**Q: Funguje to na .NET 6+?**  
A: Ano. Aspose.Words 23.11 a novější plně podporují .NET 6, .NET 7 i .NET 8. Stačí odkazovat na odpovídající NuGet balíček.

**Q: Jak změním barvu stínu, aby odpovídala mé značce?**  
A: Použijte libovolnou `System.Drawing.Color`:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Závěr

Probrali jsme vše, co potřebujete k **vytvoření obdélníkového tvaru** v dokumentu Word, **přidání tvaru do Wordu**, **aplikaci stínu na tvar** a **nastavení průhlednosti tvaru**. Kompletní, spustitelný kód najdete na začátku této stránky a vysvětlení by vám mělo poskytnout dostatek jistoty pro úpravu velikostí, barev a parametrů stínu v jakémkoli projektu.

Připravení na další krok? Vyzkoušejte experimentovat s:

- Více tvary vrstvenými dohromady pro efekt odznaku.
- Dynamickým nastavením velikosti na základě obsahu dokumentu (např. výpočet šířky z sloupce tabulky).
- Exportem dokumentu do PDF nebo HTML při zachování stínu.

Neváhejte zanechat komentář, pokud narazíte na potíže, nebo sdílet své vlastní variace na téma „obdélník se stínem“.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}