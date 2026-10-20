---
category: general
date: 2026-10-20
description: Skrýt/Zobrazit tvar pomocí nového parametru `Hidden` v Aspose.Words pro
  C#. Naučte se, jak přepínat viditelnost tvaru, řešit okrajové případy a uložit výsledek.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- Hide/Show a Shape with the new `Hidden` prop
- Aspose.Words hide shape
- C# shape hidden property
- Word document shape visibility
- programmatically hide shape
language: cs
lastmod: 2026-10-20
og_description: Skrývejte/Zobrazujte tvar pomocí nového parametru `Hidden` v Aspose.Words
  pro C#. Ovládněte přepínání viditelnosti tvaru a vyhněte se běžným úskalím.
og_image_alt: Screenshot of a Word document where a shape is hidden using the Hidden
  property
og_title: Skrýt/Zobrazit tvar pomocí nového parametru `Hidden` v Aspose.Words (C#)
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Hide/Show a Shape with the new `Hidden` prop using Aspose.Words for
    C#. Learn how to toggle shape visibility, handle edge cases, and save the result.
  headline: Hide/Show a Shape with the new `Hidden` prop in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Skrýt/Zobrazit tvar pomocí nového parametru `Hidden` v Aspose.Words pro C#
url: /cs/net/programming-with-shapes/hide-show-a-shape-with-the-new-hidden-prop-in-aspose-words-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skrýt/Zobrazit tvar pomocí nového vlastnosti `Hidden` v Aspose.Words pro C#

Pokud potřebujete **skrýt/zobrazit tvar pomocí nové vlastnosti `Hidden`** v dokumentu Word, tento průvodce vám ukáže, jak to provést pomocí Aspose.Words pro .NET. Ať už generujete zprávy, vytváříte šablony nebo čistíte importované dokumenty, programové řízení viditelnosti tvarů vám ušetří ruční úpravy.

V tomto tutoriálu se naučíte, jak načíst dokument, najít tvar, přepnout vlastnost `Hidden` a uložit upravený soubor. Kroky také zahrnují běžné varianty, jako je práce s více tvary a rozdíly mezi vloženou a plovoucí grafikou.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 (nebo novější) – Aspose.Words podporuje .NET Standard 2.0 a .NET Core.
* Licencovanou kopii **Aspose.Words pro .NET** (zkušební verze stačí pro vyzkoušení).
* IDE, např. Visual Studio 2022 nebo Visual Studio Code.
* Dokument Word (`input.docx`) obsahující alespoň jeden tvar (např. obrázek, SmartArt nebo kreslicí plátno).

## Krok 1: Načtení dokumentu Word

Prvním krokem je vytvořit objekt `Document`, který představuje soubor .docx na disku.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

*Proč je tento krok důležitý*: `Document` je vstupním bodem pro všechny operace Aspose.Words. Načtení souboru do paměti vám poskytne plný přístup k jeho stromu uzlů, včetně tvarů.

## Krok 2: Získání cílového tvaru

Pro přepnutí viditelnosti musíte získat odkaz na uzel tvaru. Níže uvedený příklad načte první tvar v dokumentu, ale logiku můžete upravit tak, aby vyhledávala tvary podle názvu, typu nebo indexu.

```csharp
// Get the first Shape node in the document tree
Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

if (shape == null)
{
    throw new InvalidOperationException("No shape was found in the document.");
}
```

*Proč je tento krok důležitý*: `GetChild` s parametrem `true` provádí hluboké prohledávání, takže najdete tvary i vnořené v tabulkách nebo záhlavích. Kontrola na `null` zabraňuje `NullReferenceException`, pokud dokument neobsahuje žádné tvary.

## Krok 3: Skrytí tvaru pomocí vlastnosti `Hidden`

Aspose.Words zavedl vlastnost `Hidden`, která řídí, zda se tvar vykreslí nebo vytiskne. Nastavením na `true` tvar skryjete; nastavením na `false` ho opět zobrazíte.

```csharp
// Hide the shape so it will not appear in the rendered document
shape.Hidden = true;
```

Pokud potřebujete **zobrazit** dříve skrytý tvar, stačí přiřadit `false`:

```csharp
// Show the shape again
shape.Hidden = false;
```

*Proč je tento krok důležitý*: Vlastnost `Hidden` funguje jak pro plovoucí, tak pro vložené tvary a integruje se s nativním formátováním Wordu „Hidden“. Tento přístup je spolehlivější než odstraňování tvaru, protože uzel zůstává ve stromu dokumentu a zachovává rozvržení i odkazy.

## Krok 4: Uložení upraveného dokumentu

Po úpravě viditelnosti zapište změny do nového souboru (nebo přepište původní, pokud chcete).

```csharp
// Save the document with the updated shape visibility
doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");
```

*Proč je tento krok důležitý*: `Save` serializuje strom uzlů v paměti do balíčku .docx, který může otevřít Word. Příznak skrytí je uložen, takže při otevření souboru v Microsoft Word se tvar zobrazí podle nastavení `Hidden`.

## Kompletní, spustitelný příklad

Spojením všech kroků získáte samostatný program, který můžete zkopírovat, zkompilovat a spustit.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShowShapeExample
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape in the document
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            Console.WriteLine("No shape found. Exiting.");
            return;
        }

        // 3. Toggle the Hidden property
        // Hide the shape
        shape.Hidden = true;
        // To show the shape again, uncomment the following line:
        // shape.Hidden = false;

        // 4. Save the modified document
        doc.Save("YOUR_DIRECTORY/ShapeHidden.docx");

        Console.WriteLine("Document saved. Shape hidden = " + shape.Hidden);
    }
}
```

**Očekávaný výstup** po spuštění programu:

```
Document saved. Shape hidden = True
```

Otevření `ShapeHidden.docx` v Microsoft Word zobrazí dokument bez cílového tvaru. Pokud před uložením nastavíte `shape.Hidden = false;`, tvar se znovu objeví.

## Práce s více tvary

Výše uvedený příklad funguje pro jeden tvar. Ve skutečných dokumentech se často vyskytuje mnoho grafických prvků. Použijte smyčku k skrytí nebo zobrazení všech tvarů, které splňují podmínku (např. konkrétní název nebo typ).

```csharp
// Hide every picture shape in the document
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Image)
    {
        s.Hidden = true; // hide picture
    }
}
doc.Save("YOUR_DIRECTORY/AllPicturesHidden.docx");
```

*Tip*: Filtrování podle `ShapeType` zabrání neúmyslnému skrytí dekorativních prvků, jako jsou textová pole nebo SmartArt.

## Okrajové případy a osvědčené postupy

| Situace | Doporučené řešení |
|-----------|----------------------|
| **Tvar je uvnitř záhlaví/zápatí** | Nejprve načtěte uzel záhlaví/zápatí a poté zavolejte `GetChild(NodeType.Shape, …)` na tomto poddokumentu. |
| **Dokument neobsahuje žádné tvary** | Vždy po `GetChild` zkontrolujte `null` nebo ověřte `doc.GetChildNodes(NodeType.Shape, true).Count`. |
| **Potřebujete zachovat příznak skrytí napříč různými verzemi Wordu** | Vlastnost `Hidden` je uložena v XML tvaru jako `<w:hidden/>`, což podporují Word 2007 a novější. |
| **Výkon u velkých dokumentů** | Zavolejte `doc.GetChildNodes(NodeType.Shape, true)` jednou a opakovaně používejte získanou kolekci místo opakovaného volání `GetChild`. |

## Pro tip: Kombinace `Hidden` s `WrapType`

Když je tvar skrytý, Word stále rezervuje místo, které by zabíral, pokud nezměníte i jeho způsob obtékání. Nastavením `WrapType = WrapType.None` odstraníte placeholder.

```csharp
shape.Hidden = true;
shape.WrapType = WrapType.None;
```

Tím zajistíte, že rozvržení se zhroutí, jako by tvar nikdy neexistoval – užitečné při generování čistých zpráv.

## Závěr

Nyní víte, jak **skrýt/zobrazit tvar pomocí nové vlastnosti `Hidden`** s Aspose.Words pro C#. Řešení zahrnuje načtení dokumentu, vyhledání tvaru, přepnutí vlastnosti `Hidden` a uložení změny. Dodržením tipů – kontrola na `null`, práce s více tvary a úprava nastavení obtékání – můžete spolehlivě řídit viditelnost tvarů v jakémkoli scénáři automatizace Wordu.

Chcete se dozvědět více? Zvažte následující kroky:

* **Skrýt/Zobrazit více tvarů** na základě vlastních metadat (využívá techniku „programmatically hide shape“).
* **Kombinovat `Hidden` s podmíněným obsahem** pomocí polí Aspose.Words pro dynamické generování zpráv.
* **Prozkoumat další vlastnosti uzlů**, jako je `Visible` pro grafy nebo `IsDeleted` pro řízení odstavců.

Šťastné programování a užijte si jemno‑granulární kontrolu, kterou Aspose.Words poskytuje pro viditelnost tvarů v dokumentech Word!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [jak skrýt tvar ve Wordu pomocí C# – krok za krokem](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-using-c-step-by-step-guide/)
- [Jak skrýt tvar ve Wordu s C# – podrobný návod](/words/english/net/programming-with-shapes/how-to-hide-shape-in-word-with-c-step-by-step-guide/)
- [Vytvořit prázdný dokument Word s skrytým eliptickým tvarem – kompletní C# průvodce](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}