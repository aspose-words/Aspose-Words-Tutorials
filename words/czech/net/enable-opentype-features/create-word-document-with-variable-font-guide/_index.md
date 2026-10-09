---
category: general
date: 2026-03-19
description: Vytvořte dokument Word pomocí Aspose.Words a proměnného písma. Naučte
  se, jak změnit váhu písma, nastavit šířku písma a definovat variaci písma v C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: cs
og_description: Vytvořte dokument Word s proměnným fontem pomocí Aspose.Words. Tento
  tutoriál vám ukáže, jak načíst font, změnit váhu písma, nastavit šířku písma a definovat
  variaci písma.
og_title: Vytvořte Word dokument s proměnným fontem – kompletní průvodce
tags:
- Aspose.Words
- C#
- Variable Font
title: Vytvořte dokument Word s proměnným fontem – průvodce
url: /cs/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu s proměnným fontem – Průvodce

Už jste někdy potřebovali **vytvořit Word dokument**, který používá moderní proměnný font, ale nebyli jste si jisti, kde začít? Nejste v tom sami. V mnoha projektech – například dynamické zprávy nebo firemní brožury – schopnost **change font weight** za běhu je skutečným průlomem.  

V tomto tutoriálu projdeme celý proces: od načtení proměnného fontu do Aspose.Words, přes nastavení jeho tloušťky a šířky, až po uložení DOCX, který vypadá přesně tak, jak jste jej navrhli. Žádné vágní odkazy, jen konkrétní kód, který můžete hned vložit do svého C# projektu.

## Co se naučíte

- Jak **load variable font** soubory načíst do Aspose.Words pomocí `FontSettings`.
- Syntax pro **define font variation** osy jako `wght` (weight) a `wdth` (width).
- Způsoby, jak **set font width** a **change font weight** na jednom `Run`.
- Tipy pro řešení běžných problémů (chybějící glyfy, nesprávné cesty ke složkám atd.).
- Kompletní, spustitelný příklad, který můžete okamžitě zkopírovat a otestovat.

> **Prerequisites**: .NET 6+ (nebo .NET Framework 4.6+), Aspose.Words pro .NET nainstalovaný přes NuGet a soubor proměnného fontu jako *RobotoFlex.ttf* umístěný v lokální složce *Fonts*.

---

## Krok 1 – Načtení proměnného fontu do Aspose.Words

Nejprve musíme Aspose.Words říct, kde má hledat naše vlastní fonty. Třída `FontSettings` dělá těžkou práci.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Why this matters**: Bez registrace složky se Aspose.Words vrátí k systémovým fontům a ignoruje jakákoli data OpenType variací, která se pokusíte později použít. Ukázáním konkrétního adresáře zajistíte, že *RobotoFlex* (nebo jakýkoli jiný proměnný font) bude nalezen pokaždé, když se kód spustí.

> **Pro tip**: Nastavte druhý parametr `SetFontsFolder` na `true`, pokud chcete, aby Aspose prohledával i podadresáře. To pomáhá, když organizujete fonty podle stylu nebo tloušťky.

---

## Krok 2 – Vytvoření nového dokumentu a přidání ukázkového textu

Nyní, když fontový engine ví, kde hledat, vytvoříme prázdný `Document` a vložíme odstavec s `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**What’s happening**: `Run` představuje souvislý úsek textu s jednotným formátováním. Vytvořením nejdříve ho izolujeme – ideální pro pozdější aplikaci různých os variací na samostatné běhy, pokud bude potřeba.

---

## Krok 3 – Definování požadovaných os variací (Weight & Width)

Proměnné fonty odhalují *axes*, které můžete během běhu upravovat. Dvě nejčastější jsou `wght` (tloušťka písma) a `wdth` (šířka písma). Aspose.Words to modeluje pomocí kolekce `OpenTypeFontVariation`.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Why these numbers**: Ve specifikaci OpenType se `wght` pohybuje od minimální po maximální hodnotu fontu (často 100–900). Hodnota **700** odpovídá tučnému vzhledu. `wdth` funguje podobně; **100** znamená výchozí (normální) šířku, zatímco hodnoty pod 100 zúží glyfy.

> **Edge case**: Některé proměnné fonty nepodporují konkrétní osu. Pokud zadáte nepodporovaný tag, Aspose jej tiše ignoruje. Vždy si ověřte specifikaci fontu (obvykle v metadatech souboru `.ttf` nebo `.otf`).

---

## Krok 4 – Aplikace variace na Run pomocí názvu fontu

Nyní svázeme data variace s konkrétním textem. Třída `FontInfo` obsahuje název rodiny fontu a kolekci os.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Explanation**: Nastavením `FontInfo` obejdeme běžnou vlastnost `Font.Name` a předáme enginu plně kvalifikovanou konfiguraci fontu. Toto je jediný způsob, jak říci Aspose.Words, aby použil proměnný font s vlastními osami.

> **Common mistake**: Zapomenout přesně odpovídat názvu rodiny uvnitř souboru fontu (`RobotoFlex` v tomto příkladu). Překlep způsobí, že Aspose přejde na výchozí font a vaše variace se ztratí.

---

## Krok 5 – Uložení dokumentu a ověření výsledku

Nakonec zapíšeme dokument na disk. Vygenerovaný DOCX bude obsahovat instrukce pro proměnný font, které Microsoft Word (2016+) dokáže správně vykreslit.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Otevřete výsledný soubor ve Wordu, vyberte text a podívejte se do dialogu **Font**. Měli byste vidět *Roboto Flex* v seznamu a text bude tučnější než okolní obsah – přesně to, co nastavení `wght = 700` požadovalo.

> **Verification tip**: Pokud se text nezdá změněn, ověřte, že soubor fontu skutečně podporuje osu `wght`. Některé “proměnné” fonty nabízejí jen `ital` (kurzívu) nebo `opsz` (optickou velikost).

---

## Volitelné: Přidání dalších variací – Dynamické měnění šířky

Pokud chcete *set font width* odlišně pro další odstavec, stačí zopakovat kroky 3‑4 s novou kolekcí `OpenTypeFontVariation`.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Nyní máte dva běhy – jeden tučný, druhý mírně širší – což demonstruje jak **change font weight**, tak **set font width** ve stejném dokumentu.

---

## Kompletní funkční příklad

Zkopírujte úryvek níže do nové konzolové aplikace (`Program.cs`) a spusťte ji. Ujistěte se, že složka `Fonts` obsahuje `RobotoFlex.ttf` (nebo jakýkoli jiný proměnný font, který preferujete).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Expected output**: Soubor `VariableFont.docx`, kde se fráze “Variable‑weight text” zobrazí tučně díky ose `wght = 700`, přičemž šířka zůstane výchozí.

---

## Často kladené otázky a okrajové případy

| Question | Answer |
|----------|--------|
| *What if the font isn’t found?* | Ověřte cestu ke složce, ujistěte se, že název souboru odpovídá, a že proces má oprávnění ke čtení. Můžete také zavolat `fontSettings.GetFonts()` pro výpis detekovaných fontů. |
| *Can I combine multiple runs with different variations?* | Ano. Každý `Run` může nést svůj vlastní `FontInfo`. Stačí opakovat kroky 3‑4 pro každý běh. |
| *Do older versions of Word support variable fonts?* | Word 2016 (Build 16.0.8001) zavedl základní podporu. Pokud cílíte na starší verze, dokument přejde na nejbližší statickou variantu fontu. |
| *Is there a limit to how many axes I can set?* | Můžete nastavit libovolný počet os, které font definuje. Běžné tagy jsou `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Zadání nepodporovaného tagu jednoduše nemá žádný efekt. |
| *How do I debug missing glyphs?* | Použijte `FontSettings.GetFontSources()` k prozkoumání načtených fontů a `FontInfo.HasGlyph(char)` k otestování jednotlivých znaků. |

---

## Závěr

V několika krocích jsme ukázali, **jak vytvořit Word dokument** soubory, které využívají sílu proměnných fontů, umožňují **change font weight**, **set font width**, **load variable font** soubory a **define font variation** osy – vše pomocí Aspose.Words pro .NET.  

Klíčová myšlenka je jednoduchá: zaregistrujte složku s fonty, popište požadované osy, připojte je k `Run` a uložte. Odtud můžete techniku rozšířit na celé sekce, tabulky nebo dokonce programově generovat značkové zprávy.

**Next steps**: vyzkoušejte výměnu `RobotoFlex` za jiný proměnný font, experimentujte s osou `ital` (kurzíva) nebo vygenerujte PDF verzi stejného dokumentu pomocí Aspose.PDF. Stejný vzor platí – načíst, definovat, aplikovat, uložit.

Happy coding, and enjoy the flexibility that variable fonts bring to your Word automation projects!  

<img src="variable-font-demo.png" alt="Příklad vytvoření Word dokumentu s proměnným fontem">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}