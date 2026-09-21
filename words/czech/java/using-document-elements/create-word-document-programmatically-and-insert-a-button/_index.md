---
category: general
date: 2026-09-21
description: Vytvořte Word dokument programově a naučte se, jak uložit tlačítko pro
  uložení dokumentu Word, vložit příkazové tlačítko Word a nastavit popisek příkazového
  tlačítka pomocí DocumentBuilder.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- save word document button
- insert command button word
- set command button caption
- how to use documentbuilder
language: cs
lastmod: 2026-09-21
og_description: Vytvořte programově dokument Word pomocí Aspose.Words. Naučte se,
  jak uložit dokument Word tlačítkem, vložit příkazové tlačítko, nastavit popisek
  příkazového tlačítka a použít DocumentBuilder pro interaktivní formuláře.
og_image_alt: Screenshot of a Word file that contains an inserted CommandButton created
  programmatically
og_title: Vytvořte Word dokument programově a přidejte tlačítko
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create word document programmatically and learn how to save word document
    button, insert command button word, and set command button caption using DocumentBuilder.
  headline: Create word document programmatically and insert a button
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Vytvořit dokument Word programově a vložit tlačítko
url: /cs/java/using-document-elements/create-word-document-programmatically-and-insert-a-button/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořit Word dokument programově a vložit tlačítko

Pokud potřebujete **vytvořit Word dokument programově**, Aspose.Words poskytuje plynulé API, které vám umožní přidávat interaktivní ovládací prvky, jako je CommandButton. Tento tutoriál také vysvětluje **jak používat DocumentBuilder**, jak **uložit tlačítko Word dokumentu**, a jak **nastavit popisek tlačítka**, tak aby se tlačítko zobrazovalo přesně tak, jak očekáváte, uvnitř souboru .docx.

Dozvíte se, jak:

* Inicializovat prázdný dokument pomocí `Document`.
* Pracovat s `DocumentBuilder` pro úpravu dokumentu.
* Vložit **CommandButton** (`insert command button word`).
* Nastavit název tlačítka a viditelný popisek (`set command button caption`).
* Uložit výsledek na disk (`save word document button`).

Kroky jsou napsány pro vývojáře .NET používající C# a nejnovější Aspose.Words pro .NET (v24.10). Žádné další NuGet balíčky nejsou potřeba kromě Aspose.Words.

---

## Co potřebujete před zahájením

| Požadavek | Důvod |
|--------------|--------|
| Visual Studio 2022 (or any C# IDE) | Pro kompilaci a spuštění ukázkového kódu. |
| .NET 6.0 SDK or later | Poskytuje runtime pro příklad. |
| Aspose.Words for .NET (v24.10 or newer) | Knihovna, která vám umožní **vytvořit Word dokument programově** a manipulovat s ovládacími prvky formuláře. |
| Basic familiarity with C# and OOP concepts | Vyžadováno pro pochopení toku kódu. |

Aspose.Words můžete nainstalovat přes NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Vytvořit Word dokument programově

Prvním krokem je vytvořit prázdný `Document`. Tento objekt představuje celý Word soubor v paměti.

```csharp
// Step 1: Create a new blank document
Document doc = new Document();
```

Vytvoření dokumentu programově vám poskytuje čisté plátno, na které můžete přidávat odstavce, tabulky nebo interaktivní ovládací prvky.  

---

## Jak používat DocumentBuilder

`DocumentBuilder` je hlavní třída pro úpravu `Document`. Poskytuje metody pro vkládání textu, obrázků a formulářových polí. V tomto tutoriálu ji používáme k umístění CommandButton.

```csharp
// Step 2: Initialize a DocumentBuilder to edit the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Builder udržuje interní kurzor, který ukazuje na aktuální místo vkládání. Ve výchozím nastavení začíná na začátku první sekce, což je pro náš příklad ideální.

---

## Vložit CommandButton do Wordu

Aspose.Words zachází s CommandButton jako s ActiveX ovládacím prvkem. Metoda `InsertForms2OleControl` vytvoří obecný OLE ovládací prvek, který následně nakonfigurujeme jako tlačítko.

```csharp
// Step 3: Insert an ActiveX Forms2OleControl (a CommandButton)
Forms2OleControl commandButton = builder.InsertForms2OleControl();
```

V tomto okamžiku ovládací prvek existuje v dokumentu, ale nemá žádnou vizuální reprezentaci, dokud neurčíme jeho typ.

---

## Nastavit popisek CommandButton

Nyní řekneme OLE ovládacímu prvku, aby se choval jako CommandButton a přiřadíme mu přátelský popisek.

```csharp
// Step 4: Define the control as a CommandButton
commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

// Step 5: Set a unique name for the button (used for identification)
commandButton.SetName("btnSubmit");

// Step 6: Set the visible caption that appears on the button
commandButton.SetCaption("Submit");
```

Nastavení **popisku tlačítka** je nezbytné, protože Word zobrazuje tento text na povrchu tlačítka. Pokud vynecháte `SetCaption`, tlačítko se zobrazí s generickým popiskem.

---

## Uložit Word dokument s tlačítkem

Nakonec dokument uložíme na disk. Metoda `Save` zapíše celý Word balíček, včetně nově vloženého tlačítka, do souboru .docx.

```csharp
// Step 7: Save the document containing the CommandButton
doc.Save("YOUR_DIRECTORY/CommandButton.docx");
```

Soubor `CommandButton.docx` nyní obsahuje plně funkční tlačítko s popiskem **Submit**. Když uživatel otevře soubor v Microsoft Word a klikne na tlačítko, spustí se výchozí akce (kterou můžete později napojit pomocí VBA).

---

## Kompletní funkční příklad

Níže je kompletní program, který můžete zkopírovat, vložit a spustit. Ukazuje celý postup od vytvoření dokumentu až po uložení tlačítka.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Initialize DocumentBuilder (how to use DocumentBuilder)
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a CommandButton (insert command button word)
        Forms2OleControl commandButton = builder.InsertForms2OleControl();

        // 4. Define the control type as CommandButton
        commandButton.SetControlType(Forms2OleControlType.COMMANDBUTTON);

        // 5. Give the button a unique name (optional but useful)
        commandButton.SetName("btnSubmit");

        // 6. Set the visible caption (set command button caption)
        commandButton.SetCaption("Submit");

        // 7. Save the document (save word document button)
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Očekávaný výsledek**

* Soubor pojmenovaný `CommandButton.docx` umístěný na vámi zadané cestě.
* Otevření souboru v Microsoft Word zobrazí jedno **Submit** tlačítko na první stránce.
* Tlačítko lze vybrat, změnit jeho velikost nebo propojit s makrem z karty **Developer** ve Wordu.

---

## Časté otázky a řešení okrajových případů

| Otázka | Odpověď |
|----------|--------|
| *Co když potřebuji více než jedno tlačítko?* | Opakujte kroky 3–6 s různými názvy a popisky. Každé tlačítko musí mít jedinečnou hodnotu `SetName`. |
| *Mohu nastavit velikost tlačítka?* | Ano. Po vložení ovládacího prvku můžete upravit jeho vlastnosti `Width` a `Height` pomocí objektu `OleFormat`. |
| *Bude tlačítko fungovat ve všech verzích Wordu?* | ActiveX ovládací prvky jsou podporovány v desktopové verzi Wordu (Windows). V Word Online ani na macOS se nezobrazují. |
| *Jak přidat obslužnou rutinu kliknutí?* | Musíte napsat VBA kód, který odkazuje na název tlačítka (`btnSubmit`). VBA makro lze vložit pomocí `doc.VbaProject`. |
| *Co když potřebuji vložit tlačítko do buňky tabulky?* | Přesuňte kurzor builderu do požadované buňky (`builder.MoveTo(cell.FirstParagraph)`) před voláním `InsertForms2OleControl`. |

---

## Pro tipy

* **Tip:** Vždy nastavte smysluplný název pomocí `SetName`. Zjednodušuje to automatizaci VBA a usnadňuje ladění.
* **Pozor:** Zapomenutí volání `SetControlType`. Bez tohoto volání se OLE objekt zobrazí jako obecný zástupce místo klikatelného tlačítka.
* **Tip pro výkon:** Pokud generujete mnoho dokumentů ve smyčce, znovu použijte jedinou instanci `DocumentBuilder` a před každým vložením zavolejte `builder.MoveToDocumentEnd()`, aby se předešlo zbytečným resetům kurzoru.

---

## Další kroky

Nyní, když víte, jak **vytvořit Word dokument programově**, **vložit CommandButton do Wordu**, **nastavit popisek tlačítka** a **uložit Word dokument s tlačítkem**, můžete prozkoumat pokročilejší scénáře:

* Přidat ovládací prvky **TextFormField** pro vstup uživatele.
* Kombinovat tlačítka s poli **MacroButton** pro přímé spouštění VBA.
* Použít **DocumentBuilder.InsertImage** k umístění ikon na tlačítka.
* Integrovat s ASP.NET pro generování Word formulářů na

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vytvořit nový Word dokument](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Vytvořit Word dokument pomocí Aspose.Words pro .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Vložit inline obrázek do Word dokumentu pomocí Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}