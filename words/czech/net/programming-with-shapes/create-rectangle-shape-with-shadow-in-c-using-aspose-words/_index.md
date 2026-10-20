---
category: general
date: 2026-03-22
description: Vytvořte obdélníkový tvar v C# a přidejte k tvaru stín pomocí Aspose.Words.
  Naučte se, jak přidat stín, jak vytvořit obdélník a jak nastavit vlastnosti stínu.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: cs
og_description: Vytvořte obdélníkový tvar v C# a přidejte stín k tvaru pomocí Aspose.Words.
  Podrobný návod krok za krokem, jak přidat stín, jak vytvořit obdélník a jak nastavit
  stín.
og_title: Vytvořte obdélníkový tvar se stínem v C# – kompletní průvodce
tags:
- Aspose.Words
- C#
- Document Automation
title: Vytvořte obdélníkový tvar se stínem v C# pomocí Aspose.Words
url: /cs/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru s vrženým stínem v C# pomocí Aspose.Words

Už jste někdy potřebovali **create rectangle shape** v dokumentu Word, ale nebyli jste si jisti, jak mu přidat jemný vržený stín? Nejste sami – mnoho vývojářů narazí na tento problém, když poprvé experimentují s automatizací dokumentů. V tomto průvodci vám ukážeme, jak **add shadow to shape** pomocí Aspose.Words, a také odpovíme na otázky „**how to add shadow**“, „**how to create rectangle**“ a „**how to set shadow**“.

Začneme s čistým `Document`, nakreslíme obdélník, zapneme jeho stín, upravíme rozostření, vzdálenost, úhel a barvu a nakonec soubor uložíme. Na konci budete mít připravený `.docx`, který zobrazuje šedý obdélník plovoucí těsně nad stránkou. Žádná záhada, jen přímočarý kód, který můžete zkopírovat a vložit do libovolného .NET projektu.

## Požadavky

* **Aspose.Words for .NET** (nejnovější verze k březnu 2026). Můžete ji získat z NuGet pomocí `Install-Package Aspose.Words`.
* Vývojové prostředí .NET – Visual Studio, Rider nebo i VS Code s rozšířením C# funguje dobře.
* Základní znalost C# – nic složitého, jen schopnost vytvořit konzolovou nebo WinForms aplikaci.

To je vše. Žádné další knihovny, žádné skryté kroky. Připravení? Pojďme na to.

## Krok 1: Inicializace nového prázdného dokumentu

Pro **create rectangle shape** nejprve potřebujeme kontejner – objekt `Document`, který představuje soubor Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

Třída `Document` je vstupním bodem pro vše, co Aspose.Words dělá. Představte si ji jako prázdné plátno; bez ní nemůžete přidávat žádné tvary, tabulky ani text.

## Krok 2: Vytvoření obdélníku, který bude mít stín

Nyní ukážeme **how to create rectangle** vytvořením instance `Shape` typu `Rectangle`. Také nastavíme jeho velikost v bodech (1 bod ≈ 1/72 palce).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Proč zvolit 200 × 100 bodů? Je to rozumná velikost pro ukázku – dostatečně velká, aby byl stín dobře vidět, ale ne tak obrovská, aby přehlušila stránku. Klidně upravte tato čísla podle svého rozvržení.

## Krok 3: Povolení efektu stínu a nastavení jeho vzhledu

Zde je jádro tutoriálu: **how to add shadow** a **how to set shadow** vlastnosti. Aspose.Words poskytuje objekt `Shadow` u každého tvaru, který vám umožní zapnout efekt a upravit vizuální parametry.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** změkčuje hrany – vyšší hodnota způsobí, že stín bude vypadat rozptýleněji.
* **Distance** posouvá stín dále od obdélníku.
* **Angle** určuje, odkud světlo přichází; 45° dává diagonální, přirozený vzhled.
* **Color** vám umožní vybrat libovolnou `System.Drawing.Color`. Šedá je bezpečná výchozí hodnota, ale můžete zvolit odvážně `Color.Black` nebo jemně `Color.LightGray`.

Tip: Pokud nastavíte `Enabled = false`, všechna ostatní nastavení stínu jsou ignorována, takže vždy dvojitě zkontrolujte tento příznak.

## Krok 4: Vložení tvaru do těla dokumentu

S připraveným obdélníkem a nastaveným stínem jej musíme vložit do dokumentu. Nejjednodušší způsob je připojit jej k prvnímu odstavci první sekce.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Pokud váš dokument již obsahuje text, můžete najít konkrétní `Paragraph` nebo dokonce buňku `Table` a vložit tam tvar. Metoda `AppendChild` je univerzální – funguje s libovolným typem `Node`.

## Krok 5: Uložení dokumentu a ověření výsledku

Nakonec zapíšeme soubor na disk. Změňte cestu na libovolné místo; složka musí existovat, jinak dostanete výjimku.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Otevřete vzniklý `ShadowedRectangle.docx` v Microsoft Word (nebo LibreOffice) a měli byste vidět šedý obdélník s ostrým, diagonálním stínem, který se táhne dolů‑vpravo. Pokud stín vypadá příliš slabě, zvyšte `BlurRadius` nebo `Distance` a znovu spusťte kód – experimentování je součástí zábavy.

![Příklad vytvoření obdélníkového tvaru s vrženým stínem](rectangle-shadow.png){alt="Příklad vytvoření obdélníkového tvaru s vrženým stínem"}

### Očekávaný výstup

* Jednostránkový dokument Word.
* Šedý obdélník o rozměrech 200 × 100 bodů umístěný v levém horním rohu stránky.
* Jemný šedý stín posunutý o 8 pixelů pod úhlem 45°, rozostřený o 5 pixelů.

## Jak přidat stín k tvaru – podrobnější pohled

Možná se ptáte, *„Mohu animovat stín nebo ho měnit na základě vstupu uživatele?“* Zatímco Aspose.Words samotný nepodporuje animaci, můžete programově upravit vlastnosti stínu před uložením, čímž efektivně vytvoříte více verzí stejného dokumentu s různým vzhledem. Například iterací přes kolekci barev:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Tento malý úryvek ukazuje **how to set shadow** dynamicky – skvělé pro generování tematických reportů.

## Jak vytvořit obdélník – alternativní tvary

Pokud potřebujete zaoblený obdélník, stačí změnit `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Nebo pro dokonalý čtverec nastavte `Width` stejnou jako `Height`. Stejné vlastnosti stínu platí, takže už máte pokryté **how to add shadow** pro jakýkoli tvar, který zvolíte.

## Časté problémy a řešení

| Problém | Pravděpodobná příčina | Řešení |
|---------|-----------------------|--------|
| Stín se nezobrazuje | `Shadow.Enabled` left as `false` | Set `rectangleShape.Shadow.Enabled = true;` |
| Stín vypadá příliš ostrý | `BlurRadius` set to 0 | Increase `BlurRadius` to at least 3 |
| Dokument při ukládání vyvolá `FileNotFoundException` | Destination folder doesn’t exist | Create the folder first or use a valid path |
| Tvar je neviditelný | Width/Height set to 0 | Ensure both dimensions are > 0 |

## Shrnutí – co jsme dosáhli

* **Create rectangle shape** v novém dokumentu Word pomocí Aspose.Words.  
* **Add shadow to shape** přepnutím příznaku `Shadow.Enabled` a úpravou rozostření, vzdálenosti, úhlu a barvy.  
* Ukázáno **how to add shadow**, **how to create rectangle** a **how to set shadow** v čistém, znovupoužitelném úryvku kódu.  
* Poskytnut kompletní, připravený příklad, který můžete vložit do libovolného C# projektu.

## Co dál?

Nyní, když ovládáte základy, zvažte prozkoumání:

* **How to add shadow to images** – stejná API `Shadow` funguje pro `ShapeType.Image`.
* **Combining multiple shapes** – vytvořte diagramy nebo infografiky přímo ve Wordu.
* **Exporting to PDF** – zavolejte `document.Save("output.pdf")` po přidání stínů pro tiskovou verzi.

Klidně experimentujte s různými barvami, úhly nebo dokonce gradientními výplněmi. API je dostatečně flexibilní, aby vám umožnilo vytvářet profesionálně vypadající dokumenty, aniž byste museli ručně otevírat Word.

Šťastné kódování! Pokud narazíte na nějaké potíže, zanechte komentář níže nebo navštivte fóra Aspose.Words – komunita je rychlá s pomocí.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}