---
category: general
date: 2026-04-04
description: Vytvořte obdélníkový tvar v C# pomocí Aspose.Words a naučte se, jak přidat
  stín, aplikovat rozostření stínu a učinit stín průhledným – krok za krokem průvodce.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: cs
og_description: Vytvořte obdélníkový tvar v C# pomocí Aspose.Words. Naučte se, jak
  přidat stín, aplikovat rozostření na stín a učinit stín průhledným v stručném tutoriálu.
og_title: Vytvořte obdélníkový tvar a jak přidat stín v C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Vytvořit obdélníkový tvar a jak přidat stín v C#
url: /cs/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření obdélníkového tvaru a jak přidat stín v C#

Už jste někdy potřebovali **create rectangle shape** v dokumentu Word, ale nebyli jste si jisti, jak mu přidat jemný drop‑shadow? Nejste v tom sami. V mnoha scénářích reportování nebo brandingu může jednoduchý obdélník s měkkým, poloprůhledným stínem dodat rozvržení vylepšený vzhled bez velké námahy.

V tomto tutoriálu projdeme **how to create document** pomocí Aspose.Words, poté ukážeme **how to add shadow**, **apply blur to shadow** a dokonce **make shadow transparent**. Na konci budete mít připravený C# úryvek, který vytvoří soubor *.docx* s pěkně osvíceným obdélníkem – vše během několika minut.

## Co budete potřebovat

- .NET 6 nebo novější (API funguje také s .NET Framework 4.6+)
- Aspose.Words pro .NET (bezplatná zkušební verze funguje pro tento příklad)
- Editor kódu – Visual Studio, VS Code, Rider, nebo cokoli, co preferujete
- Základní znalost C# – nic složitého, jen schopnost spustit konzolovou aplikaci

Pokud to máte, můžeme rovnou přejít k řešení.

## Krok 1 – How to create document a inicializace plátna

Nejprve: potřebujete prázdný objekt `Document`. Představte si ho jako prázdný list papíru, který Aspose.Words později převede na soubor Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Proč vytváříme instanci `Document` místo načtení šablony? Začínání od nuly zaručuje, že žádné skryté styly nebo sekce nebudou zasahovat do našeho obdélníku. Také to udržuje velikost souboru malou – dobrý zvyk při generování mnoha dokumentů ve smyčce.

## Krok 2 – Create rectangle shape (jádro našeho hlavního klíčového slova)

Nyní skutečně **create rectangle shape**. Třída `Shape` je flexibilní; řeknete jí typ (Rectangle), velikost a jak má obtékat okolní text.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Všimněte si použití syntaxe inicializátoru objektu – je stručná a snižuje šanci, že později zapomenete nastavit nějakou vlastnost. Obdélník bude umístěn uvnitř prvního odstavce, který přidáme v dalším kroku.

## Krok 3 – How to add shadow a přizpůsobení vzhledu

Přidání stínu není jen jedna řádka; máte několik vlastností, které můžete upravit. Zde vstupují do hry sekundární klíčová slova **apply blur to shadow** a **make shadow transparent**.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Rychlá poznámka k číslům: `BlurRadius` 5 poskytuje jemné rozmazání; zvýšte na 10 pro měkčí vzhled, nebo snižte na 2 pro ostrý okraj. Hodnota `Transparency` se pohybuje od 0 (neprůhledná) do 1 (neviditelná). Přizpůsobte podle požadavků kontrastu vaší značky.

### Pro tip

Pokud někdy potřebujete barevný stín (např. firemní modrou), stačí nahradit `Color.DarkGray` za `Color.FromArgb(80, 0, 120, 215)`. První argument je alfa kanál – udržujte ho nízký pro jemnost.

## Krok 4 – Vložení tvaru do dokumentu

S připraveným obdélníkem a jeho stínem jej nyní umístíme do prvního odstavce dokumentu. Tento krok zajistí, že tvar se objeví úplně nahoře v souboru.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Proč první odstavec? Je to bezpečná výchozí volba, která funguje i když je dokument zcela prázdný. Pokud máte konkrétní místo (např. po nadpisu), najdete ten uzel a vložíte tam tvar.

## Krok 5 – Uložení souboru a ověření výsledku

Nakonec dokument uložíme na disk. Můžete zvolit libovolnou cestu; jen se ujistěte, že složka existuje.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Když otevřete *ShadowRectangle.docx* v Microsoft Word, měli byste vidět obdélník 200 × 100 bodů s tmavě šedým, mírně rozmazaným, 30 % průhledným stínem posunutým o tři body doprava a dolů. Efekt je jemný, ale přidává hloubku do jinak plochých rozvržení.

![vytvořit obdélníkový tvar se stínem v Aspose.Words](https://example.com/placeholder-image.png "vytvořit obdélníkový tvar se stínem v Aspose.Words")

*Text alternativy obrázku:* **vytvořit obdélníkový tvar se stínem v Aspose.Words** – obrázek ukazuje finální dokument s osvíceným obdélníkem.

## Běžné varianty a okrajové případy

### Dynamická změna barvy stínu

Pokud vaše aplikace podporuje motivy, můžete barvu stínu načíst z konfiguračního souboru:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Vytvoření tvaru mimo řádek

Někdy chcete, aby obdélník plaval nad textem. Přepněte `WrapType` na `WrapType.Square` a nastavte `RelativeHorizontalPosition` na `RelativeHorizontalPosition.Margin` pro větší kontrolu.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Zpracování více stránek

Pokud potřebujete obdélník na každé stránce, projděte smyčkou `doc.Sections` a připojte zkopírovaný tvar do prvního odstavce každé sekce. Nezapomeňte zavolat `rect.Clone(true)`, aby se duplikovaly i nastavení stínu.

## Shrnutí – Co jsme dosáhli

- **Created rectangle shape** pomocí Aspose.Words
- **How to add shadow** s barvou, posunem, rozostřením a průhledností
- Ukázáno **apply blur to shadow** a **make shadow transparent**
- Uložen soubor Word, který můžete okamžitě otevřít

Vše bylo dosaženo pomocí několika řádků, což dokazuje, že sofistikované vizuální úpravy nevyžadují vždy těžké grafické knihovny.

## Co dál?

- Experimentujte s dalšími `ShapeType` (Ellipse, Cloud, atd.) a podívejte se, jak se chovají stíny.
- Kombinujte obdélník s textovými poli pro vytvoření popiskových výkřiků.
- Ponořte se do **how to create document** šablon, které již obsahují zástupné symboly pro tvary, a poté je naplňte programově.

Neváhejte upravit poloměr rozostření, barvu nebo průhlednost, dokud stín nebude vypadat přesně tak, jak potřebujete pro svůj designový jazyk. API je shovívavé a změny jsou okamžitě viditelné po opětovném spuštění konzolové aplikace.

Šťastné kódování a ať vaše dokumenty vždy mají ten extra nádech hloubky!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}