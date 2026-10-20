---
category: general
date: 2026-04-21
description: Vytvořte dokument Word se stylizovaným obdélníkem a stínem. Naučte se,
  jak přidat stín, vložit tvar obdélníku, nastavit barvu stínu a další v C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: cs
og_description: Vytvořte dokument Word a přidejte do něj stínovaný obdélníkový tvar
  v C#. Postupujte podle tohoto návodu, abyste snadno nastavili barvu stínu, rozostření
  a posuny.
og_title: Vytvořte dokument Word se stínovaným obdélníkem – krok za krokem
tags:
- Aspose.Words
- C#
- Document Automation
title: Vytvořte dokument Word se stínovaným obdélníkem – kompletní průvodce
url: /cs/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvoření Word dokumentu s obdélníkem se stínem – Kompletní průvodce

Už jste někdy potřebovali **vytvořit Word dokument**, který vypadá o něco uhlazeněji než obyčejná stránka textu? Možná vytváříte šablonu zprávy nebo leták a jednoduchý obdélník s jemným stínem by stačil. V tomto tutoriálu vás provedeme přesně tím – jak vložit tvar obdélníku, zapnout stín a přizpůsobit jeho barvu, rozostření a posuny – vše pomocí C# a Aspose.Words.

Také se podíváme na **jak přidat stín** způsobem, který funguje, ať už cílíte na Word 2016, 2019 nebo nejnovější verzi Office 365. Na konci budete mít připravený soubor *.docx* k uložení, který ukazuje pěkně stínovaný obdélník, a pochopíte „proč“ za každým nastaveným vlastností.

## Požadavky

- .NET 6 (nebo jakákoli recentní verze .NET Framework)  
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`)  
- Základní znalost syntaxe C#  
- IDE jako Visual Studio (ale jakýkoli editor stačí)

Žádné další knihovny nejsou potřeba; vše ostatní je součástí Aspose.Words.

## Krok 1 – Inicializace dokumentu a builderu (Create Word Document)

Pro **vytvoření Word dokumentu** programově začínáte třídou `Document`. `DocumentBuilder` je vaše štětec; umožňuje vám přidávat text, tvary a další prvky.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Proč je to důležité:* Objekt `Document` představuje celý soubor .docx. Bez něj nemáte kam připojit obdélník nebo jeho stín.

## Krok 2 – Vložení tvaru obdélníku (Insert Rectangle Shape)

Nyní skutečně **vložíme tvar obdélníku**. Metoda `InsertShape` přijímá výčtový typ `ShapeType` a dále šířku a výšku v bodech.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Tip:* 1 bod ≈ 1/72 palce, takže 200 bodů je přibližně 2,78 palce na šířku. Přizpůsobte tato čísla podle svého rozvržení.

## Krok 3 – Povolení stínu (How to Add Shadow)

Stíny jsou ve výchozím nastavení vypnuté. Přepněte příznak `Visible`, aby se zapnul.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Co se děje?* Když je `Visible` nastaven na true, Word vykreslí vržený stín na základě dalších vlastností, které nastavíte dále.

## Krok 4 – Přizpůsobení vzhledu stínu (Set Shadow Color, Blur, Offsets)

Zde **nastavujete barvu stínu**, poloměr rozostření a posuny X/Y. Nebojte se experimentovat – různé hodnoty vám poskytnou měkký zář, hluboký vrh nebo dokonce „plovoucí“ efekt.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Proč tyto čísla?* Rozostření 5 bodů dává jemný perleťový okraj, zatímco posun 4 bodů posouvá stín dolů‑doprava, napodobujíc světelný zdroj z horního levého rohu. Změňte `Color` na `Color.Black` pro silnější kontrast, nebo použijte `Color.FromArgb(128, 0, 0, 0)` pro poloprůhlednou černou.

### Okrajové případy a varianty

- **Žádné rozostření:** Nastavte `Blur = 0` pro ostrý, tvrdý okraj stínu.  
- **Negativní posuny:** Použijte `OffsetX = -4` pro posunutí stínu doleva.  
- **Různé tvary:** Stejné vlastnosti stínu fungují pro kruhy, trojúhelníky nebo i volně kreslené tvary – stačí změnit `ShapeType` v Kroku 2.  
- **Kompatibilita:** Aspose.Words zapisuje data stínu ve formátu Office Open XML, který funguje napříč Word 2010‑2021 a Office 365.

## Krok 5 – Uložení dokumentu (Create Word Document)

Nakonec soubor uložte na disk. Můžete zvolit libovolný podporovaný formát (`.docx`, `.pdf`, `.odt`, …), ale v tomto průvodci zůstaneme u klasického formátu Word.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Když otevřete **ShadowRectangle.docx** v Microsoft Word, uvidíte šedý obdélník s jemným, rozostřeným stínem posunutým dolů‑doprava – přesně to, co jsme naprogramovali.

### Očekávaný výstup

- Jednostránkový soubor *.docx*.  
- Obdélník 200 pt × 100 pt umístěný uprostřed tam, kde byl kurzor při volání `InsertShape`.  
- Šedý stín, který se objeví 4 bodů vpravo a 4 bodů dolů, s rozostřením 5 bodů.

Pokud se tvar zdá být mimo střed, můžete kurzor přesunout pomocí `builder.MoveTo` před vložením, nebo po vložení upravit vlastnosti `Left` a `Top` tvaru.

## Často kladené otázky a řešení problémů

**Q: Stín se ve Wordu nezobrazuje.**  
A: Ujistěte se, že `ShadowFormat.Visible` je `true`. Také ověřte, že používáte aktuální verzi Aspose.Words (funkce stínu byla přidána ve verzi 20.3).  

**Q: Můžu na stín použít gradient?**  
A: Ne přímo pomocí `ShadowFormat`. UI Wordu podporuje gradientní stíny, ale schéma Open XML (kterému Aspose.Words odpovídá) poskytuje jen stíny s plnou barvou. Museli byste ručně upravit podkladové XML – pokročilejší scénář.  

**Q: Co když potřebuji průhledný obdélník jen se stínem?**  
A: Po vložení nastavte `rectangle.FillColor = Color.Transparent;`. Stín se stále vykreslí, protože je nezávislý na výplni.

## Tipy pro produkční kód

- **Znovupoužití builderu:** Pokud přidáváte více tvarů, používejte stejnou instanci `DocumentBuilder` – vytvoření nové pro každý tvar přidává zbytečnou režii.  
- **Dávkové ukládání:** Uložte jednou po všech úpravách; časté I/O zpomaluje generování velkých dokumentů.  
- **Zpracování chyb:** Zabalte celý blok do `try / catch` a logujte výjimky `Aspose.Words`; často obsahují užitečná čísla řádků, pokud je šablona dokumentu poškozena.

## Další kroky (Související témata)

- **Jak přidat stín** k obrázkům nebo textovým rámečkům (podobné použití `ShadowFormat`).  
- **Vložit tvar obdélníku** do buňky tabulky pro vlastní stylování buňky.  
- **Vytvořit obdélník ve Wordu** pomocí nativního XML Wordu (pro ty, kteří preferují čisté Open XML).  
- **Nastavit barvu stínu** dynamicky na základě vstupu uživatele nebo tématických barev.

Experimentujte s různými barvami, poloměry rozostření a posuny – třeba jemný modrý zář pro firemní zprávu, nebo hluboký černý stín pro dramatický leták. Možnosti jsou nekonečné a změny v kódu jsou minimální.

---

### Rychlé shrnutí

- **Vytvořili jsme Word dokument** od nuly.  
- **Vložili jsme tvar obdélníku** a zapnuli jeho stín.  
- **Nastavili jsme barvu stínu**, rozostření a posuny pro profesionální vzhled.  
- Soubor jsme uložili, připravený k distribuci.

Nyní máte pevný základ pro přidání vizuálního šmrncu do jakéhokoli projektu automatizace Wordu. Máte další nápady? Zanechte komentář a pojďme konverzaci dál rozvíjet. Šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}