---
category: general
date: 2026-05-26
description: Vytvořte Word dokument v C# pomocí Aspose.Words, vložte obdélníkový tvar,
  nastavte barvu výplně a přidejte stínový efekt – krok za krokem návod.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: cs
og_description: Vytvořte Word dokument v C# pomocí Aspose.Words. Naučte se, jak vložit
  obdélníkový tvar, nastavit jeho barvu výplně a přidat stínový efekt.
og_title: Vytvořte dokument Word – vložte obdélníkový tvar a stín v C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Vytvořit dokument Word – vložit obdélníkový tvar a stín v C#
url: /cs/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu – Vložení obdélníkového tvaru a stínu v C#

Už jste se někdy zamysleli, jak **vytvořit Word dokument** programově, aniž byste nejprve otevírali Microsoft Word? Nejste v tom sami. V mnoha automatizačních scénářích—například faktur, smluv nebo hromadného generování reportů—potřebujete spolehlivý způsob, jak vytvořit soubor .docx, vložit do něj tvar, nastavit barvu a možná i stín pro dokonalý vzhled.

V tomto tutoriálu vás provedeme přesně tímto: pomocí Aspose.Words pro .NET **vytvoříme Word dokument**, **vložíme obdélníkový tvar**, aplikujeme výplň a **přidáme stín**. Na konci budete mít připravený soubor k uložení, který můžete předat do jakéhokoli následného workflowu.  

Také se podíváme na **jak vložit tvar** flexibilním způsobem a proč **jak nastavit výplň** má význam pro vizuální konzistenci. Žádné zbytečnosti, jen kód, který můžete zkopírovat‑vložit a spustit.

## Požadavky

- .NET 6+ (nebo .NET Framework 4.7+) nainstalovaný.
- Platná licence Aspose.Words pro .NET (nebo dočasný evaluační klíč).
- Visual Studio, Rider nebo jakékoli C# IDE, které máte rádi.
- Základní znalost syntaxe C# — nic složitého není potřeba.

Máte vše? Skvělé, pojďme na to.

## Krok 1 – Vytvoření Word dokumentu

Prvním, co potřebujete, je prázdný objekt dokumentu. To je plátno, na kterém vše ostatní žije.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` představuje soubor .docx v paměti, zatímco `DocumentBuilder` poskytuje pohodlné API pro vkládání textu, tabulek a tvarů. **Vytvoření Word dokumentu** tímto způsobem je okamžité — žádné UI, žádná COM interop, jen čistý .NET.

## Krok 2 – Vložení obdélníkového tvaru

Nyní, když máme dokument, **vložíme obdélníkový tvar**. Metoda `InsertShape` přijímá výčtový typ `ShapeType`, šířku a výšku (v bodech). Použijeme obdélník o rozměrech 150 × 80 bodů, což přibližně odpovídá 2 × 1 palci.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Za scénou Aspose vytvoří objekt `Shape`, přidá ho do aktuálního odstavce a vrátí referenci, kterou můžete stylovat. To je podstata **jak vložit tvar** — jen jeden řádek kódu, ale neuvěřitelně výkonný.

## Krok 3 – Jak nastavit výplň

Tvar bez výplně je na bílé stránce neviditelný. Dáme mu příjemné světle‑modré pozadí.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Můžete také použít gradienty, textury nebo dokonce výplň obrázkem, ale jednobarevná výplň udržuje příklad jednoduchý. Toto ukazuje **jak nastavit výplň** na libovolném tvaru, který vytvoříte, a zajišťuje vizuální vodítko, které čtenáři očekávají.

## Krok 4 – Jak přidat stín

Stíny přidávají hloubku a způsobují, že tvar „vystoupí“. Aspose.Words vystavuje objekt `ShadowFormat`, kde můžete přepínat viditelnost, vybrat barvu a doladit rozostření, vzdálenost a úhel.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Proč právě tyto hodnoty? Úhel 45° poskytuje přirozený světelný zdroj zprava nahoře, mírné rozostření udržuje stín decentní a krátká vzdálenost zabraňuje tomu, aby tvar vypadal odtrženě. Klidně experimentujte — změna úhlu na 135° způsobí, že stín spadne dolů vlevo, například.

## Krok 5 – Uložení dokumentu

Veškerá práce je hotová; nyní zapíšeme soubor na disk. Vyberte libovolnou cestu, jen se ujistěte, že složka existuje.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Když otevřete `ShadowShape.docx` v Microsoft Word, uvidíte světle‑modrý obdélník s jemným šedým stínem — přesně to, co jsme naprogramovali.

## Úplný funkční příklad

Sestavíme vše dohromady, zde je kompletní, připravený program ke kopírování‑vkládání:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Očekávaný výsledek

- Soubor pojmenovaný **ShadowShape.docx** se objeví v cílové složce.
- Po otevření ve Wordu se zobrazí světle‑modrý obdélník vycentrovaný na první stránce.
- Obdélník vrhá šedý stín pod úhlem 45°, což vytváří jemný 3‑D efekt.

## Často kladené otázky a okrajové případy

**Co když potřebuji jiný tvar?**  
Nahraďte `ShapeType.Rectangle` libovolnou jinou hodnotou výčtu (`Ellipse`, `Star`, `Arrow` atd.). Zbytek kódu zůstane stejný.

**Mohu do tvaru vložit text?**  
Ano — po vytvoření tvaru zavolejte `shape.AppendChild(new Paragraph(doc))` a poté vložte `Run` s vaším textem. Nezapomeňte nastavit vlastnosti `shape.TextBox`, pokud chcete zalamování.

**Co s DPI nebo jednotkami měření?**  
Aspose pracuje v bodech (1 pt = 1/72 palce). Pokud preferujete centimetry, vynásobte 28,35 (protože 1 cm ≈ 28,35 pt).

**Potřebuji licenci, aby to fungovalo?**  
Evaluační verze přidá vodoznak na první stránku. Platná licence jej odstraní a odemkne plné API.

## Tipy a úskalí

- **Pro tip:** Zavolejte `builder.MoveToDocumentEnd()` před vložením tvaru, pokud jej chcete umístit na úplný konec dokumentu.
- **Dejte si pozor na:** Ukládání do složky jen pro čtení vyvolá `UnauthorizedAccessException`. Ujistěte se, že má vaše aplikace oprávnění k zápisu.
- **Poznámka o výkonu:** Pro hromadnou generaci (stovky dokumentů) znovu použijte jedinou instanci `Document` jako šablonu a klonujte ji pomocí `doc.Clone(true)`, abyste se vyhnuli opakovanému inicializačnímu zatížení.

## Závěr

Nyní už víte, jak **vytvořit Word dokument**, **vložit obdélníkový tvar**, **nastavit výplň** a **přidat stín** pomocí Aspose.Words pro .NET. Výše uvedený úryvek je samostatné řešení, které můžete vložit do libovolného C# projektu, ať už jde o konzolovou aplikaci, webové API nebo background službu.

Od sem můžete dále zkoumat:

- Přidávání více tvarů s různými barvami.
- Použití gradientů nebo obrázkových výplní (`shape.FillColor = ...` → `shape.FillPattern`).
- Kombinování tvarů s tabulkami pro složité rozvržení reportů.

Vyzkoušejte to, upravte parametry a sledujte, jak vaše automatizované Word soubory vypadají profesionálněji jen s několika řádky kódu. Šťastné programování!

## Související tutoriály

- [Vytvoření obdélníkového tvaru ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutoriál stínu tvaru v Aspose.Words – Přidání stínu k tvaru ve Wordu v C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Vytvoření skupinového tvaru ve Word dokumentu pomocí Aspose.Words pro .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}