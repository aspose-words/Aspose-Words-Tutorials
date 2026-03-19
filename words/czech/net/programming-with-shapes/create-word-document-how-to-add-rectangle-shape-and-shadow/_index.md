---
category: general
date: 2026-03-19
description: Vytvořte Word dokument v C# pomocí Aspose.Words, naučte se přidávat tvary,
  přidejte obdélníkový tvar, aplikujte stín a během několika minut uložte dokument
  jako docx.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: cs
og_description: Vytvořte Word dokument pomocí Aspose.Words, přidejte obdélníkový tvar,
  aplikujte vnější stín a uložte dokument jako docx. Průvodce krok za krokem.
og_title: Vytvořte dokument Word – Přidejte obdélníkový tvar a stín
tags:
- Aspose.Words
- C#
- Document Automation
title: Vytvořte dokument Word – Jak přidat obdélníkový tvar a stín
url: /cs/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu – Jak přidat obdélníkový tvar a stín

Už jste někdy potřebovali **create word document** programově a přemýšleli, kde začít? Nejste v tom sami. Mnoho vývojářů narazí na stejný problém, když poprvé zkusí vygenerovat soubor .docx, který obsahuje vlastní grafiku. V tomto tutoriálu projdeme celý proces – jak přidat tvar, konkrétně **add rectangle shape**, dát mu stylový **add shadow to shape**, a nakonec **save document as docx**.  

Na konci průvodce budete mít připravený C# úryvek, který můžete vložit do libovolného .NET projektu. Žádné nejasné odkazy, jen kompletní, spustitelný příklad.  

## Požadavky

- .NET 6.0 nebo novější (kód funguje i s .NET Framework).  
- Aspose.Words pro .NET nainstalováno (NuGet balíček `Aspose.Words`).  
- Základní znalost syntaxe C# – nic složitého není potřeba.  

Pokud knihovnu nemáte, spusťte:

```bash
dotnet add package Aspose.Words
```

A to je vše – žádné další SDK, žádné COM interop, jen jediná reference na NuGet.

---

## Krok 1: Vytvoření Word dokumentu (hlavní cíl)

Prvním, co potřebujeme, je čisté plátno. Představte si třídu `Document` jako novou stránku v Microsoft Word; obsahuje sekce, odstavce a vše ostatní, co později přidáte.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Proč začít s prázdným `Document`? Protože to zaručuje, že se z žádné šablony neproplíží skryté formátování. Z mé zkušenosti vyplývá, že začátek od nuly zabraňuje tajemným posunům rozvržení, když později vkládáte tvary.

---

## Krok 2: Vložení obdélníkového tvaru – Přidání vizuálního prvku

Nyní, když máme dokument, pojďme **add rectangle shape** do prvního odstavce. Objekt `Shape` je univerzální; můžete zvolit `ShapeType.Rectangle`, `Ellipse` nebo dokonce vlastní kresby. Zde je minimální kód:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Co se děje pod kapotou?**  
- `ShapeType.Rectangle` říká Aspose, že chceme jednoduchý rámeček.  
- `WrapType.Inline` zajišťuje, že se obdélník pohybuje s tokem textu, což je obvykle to, co očekáváte ve scénáři zpracování textu.  
- Přidáním k `FirstParagraph` se vyhnete nutnosti ručně vkládat nový odstavec; Aspose vytvoří jeden, pokud je dokument skutečně prázdný.  

> **Tip:** Pokud potřebujete, aby tvar byl *za* textem, změňte `WrapType` na `WrapType.Transparent`. Tato malá změna může mít obrovský vizuální dopad.

---

## Krok 3: Aplikace vnějšího stínu – Vylepšení vzhledu

Plochý obdélník je… no, plochý. Přidání **add shadow to shape** mu dodá hloubku bez dalších obrázků. `ShadowFormat` od Aspose to udělá jedním řádkem.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Proč se zabývat těmito konkrétními hodnotami?  
- **Blur** s hodnotou `5.0` poskytuje jemný rozostřený okraj, který vypadá profesionálně na většině monitorů.  
- **Distance** `3.0` a **Angle** `45` vytvářejí přirozený zdroj světla z levého horního rohu, což je běžná designová konvence.  
- **Color.Gray** funguje jak v světlých, tak tmavých tématech; můžete jej nahradit `Color.Black`, pokud potřebujete vyšší kontrast.  

Pokud někdy potřebujete *vnitřní* stín (představte si zapuštěné tlačítko), stačí změnit `ShadowType.OuterShadow` na `ShadowType.InnerShadow`. Stejné vlastnosti stále platí.

---

## Krok 4: Uložení dokumentu jako DOCX – Uložení vaší práce

Všechno to je skvělé, ale nakonec budete chtít soubor na disku. Krok **save document as docx** je jednoduchý:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Několik poznámek:  
- Enum `SaveFormat.Docx` zaručuje moderní formát Office Open XML, který je kompatibilní s Word 2007+.  
- Pokud potřebujete streamovat soubor přímo do webové odpovědi, nahraďte cestu k souboru `MemoryStream` a zapište jej do HTTP odpovědi.  

Po spuštění kódu otevřete `ShadowedRectangle.docx` v Microsoft Word. Měli byste vidět šedý obdélník s jemným stínem, umístěný inline s prvním odstavcem – přesně to, co jsme chtěli dosáhnout.

---

## Jak přidat tvar – Alternativní přístupy

Příklad výše používá přístup *inline*, ale někdy chcete tvar, který plave nad textem. Zde vstupuje do hry **how to add shape** s různým obalením.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Zde jsme změnili `WrapType` na `Square` a vycentrovali tvar na stránce. Tento vzor je užitečný pro titulní stránky nebo dekorativní bannery. Pamatujte: plovoucí tvary mírně zvětší velikost souboru, protože Word ukládá další údaje o umístění.

---

## Očekávaný výstup a ověření

Když otevřete vygenerovaný soubor, měli byste vidět:

- Jeden odstavec obsahující šedý obdélník.  
- Obdélník má přibližně rozměry 2,8 × 1,4 palce.  
- Jemný vnější stín posunutý dolů a doprava.  

Pokud se tvar objeví *mimo* odstavec, zkontrolujte `WrapType`. Pokud stín vypadá příliš tvrdě, snižte hodnotu `Blur` nebo změňte `Color` na světlejší odstín.

---

## Časté problémy a jak se jim vyhnout

| Problém | Proč se to děje | Řešení |
|-------|----------------|-----|
| Tvar zmizí po uložení | `WrapType` nastaven na `Inline`, ale odstavec byl odstraněn | Zajistěte, aby odstavec existoval; použijte `doc.FirstSection.Body.FirstParagraph` pro jeho zajištění. |
| Stín vypadá pixelově | Použití velmi nízké hodnoty `Blur` | Zvyšte `Blur` alespoň na `3.0` pro hladké hrany. |
| Velikost souboru roste | Přidání mnoha vysoce rozlišených obrázků spolu s tvary | Použijte `doc.RemoveUnusedResources()` před uložením, pokud jste přidali obrázky. |
| Barva se nezobrazuje v tmavém režimu | Použití tmavé `Color` pro samotný tvar | Zvolte kontrastní barvu (např. `Color.White`) pro lepší viditelnost. |

---

## Kompletní funkční příklad

Níže je kompletní kód připravený ke kopírování a vložení, který zahrnuje vše, o čem jsme mluvili. Klidně jej spusťte jako konzolovou aplikaci.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Vysvětlení každého bloku** je vloženo jako komentáře, což vyhovuje jak čtenářům SEO, tak AI asistentům, kteří milují samostatné odpovědi.

---

## Závěr

Právě jsme **create word document** od začátku, naučili se **how to add shape**, konkrétně **add rectangle shape**, dali mu **add shadow to shape**, a nakonec **save document as docx**. Kroky jsou jednoduché, kód je stručný a výsledek vypadá profesionálně.  

Pokud jste připraveni jít dál, zkuste nahradit obdélník vlastním obrázkem, experimentujte s různými barvami stínů, nebo vygenerujte celý report s více sekcemi obsahujícími tvary. Aspose.Words API je dostatečně flexibilní na to, aby zvládlo vše od faktur po marketingové brožury.  

Máte otázky ohledně jiných typů tvarů nebo potřebujete pomoc s integrací do služby ASP.NET Core? Zanechte komentář níže a šťastné kódování! 

![vytvořit word dokument s obdélníkovým tvarem a stínem](placeholder-image.png "vytvořit word dokument s obdélníkovým tvarem a stínem

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}