---
category: general
date: 2026-08-17
description: Vložte příklad OleControlType.CommandButton do Wordu pomocí Aspose.Words.
  Naučte se, jak programově přidávat formulářové ovládací prvky do dokumentu Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert olecontroltype.commandbutton example
- how to add form controls to word document
- Aspose.Words ActiveX button
- C# Word automation
- programmatic form controls
language: cs
lastmod: 2026-08-17
og_description: Vložte příklad OleControlType.CommandButton do Wordu s Aspose.Words.
  Postupujte podle tohoto návodu a přidejte formulářové ovládací prvky do dokumentu
  Word.
og_image_alt: Screenshot showing an ActiveX CommandButton inserted into a Word document
  using Aspose.Words
og_title: Vložte příklad OleControlType.CommandButton do Wordu
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: Insert OleControlType.CommandButton example in Word using Aspose.Words.
    Learn how to add form controls to a Word document programmatically.
  headline: Insert OleControlType.CommandButton example in Word
  type: TechArticle
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Vložte příklad OleControlType.CommandButton do Wordu
url: /cs/net/working-with-oleobjects-and-activex/insert-olecontroltype-commandbutton-example-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vložení příkladu OleControlType.CommandButton do Wordu

Pokud potřebujete **vložit příklad OleControlType.CommandButton** do souboru Word, tento průvodce vám ukáže, jak na to. Naučíte se **jak přidat ovládací prvky formuláře do dokumentu Word** pomocí Aspose.Words, s kompletním spustitelným programem v C#.

Ovládací prvky formuláře, jako jsou ActiveX tlačítka, vám umožňují vytvářet interaktivní šablony Wordu – užitečné pro smlouvy, dotazníky nebo interní nástroje. Níže uvedené kroky pokrývají vše od nastavení projektu až po ověření, že tlačítko se v uloženém souboru `.docx` zobrazí správně.

## Požadavky

- .NET 6.0 SDK nebo novější nainstalováno  
- Visual Studio 2022 (nebo jakékoli C# IDE)  
- Licence Aspose.Words pro .NET nebo bezplatná dočasná licence  
- Základní znalost C# a konceptů souborů Word  

> **Tip:** Pokud používáte bezplatnou zkušební verzi, umístěte soubor licence do stejné složky jako spustitelný soubor a načtěte jej na začátku `Main`.

## Krok 1: Vytvořte nový konzolový projekt a přidejte Aspose.Words

Otevřete terminál a spusťte:

```bash
dotnet new console -n OleCommandButtonDemo
cd OleCommandButtonDemo
dotnet add package Aspose.Words
```

Tím se vytvoří čistý projekt a stáhne nejnovější balíček Aspose.Words, který poskytuje API `Document`, `DocumentBuilder` a `InsertForms2OleControl` potřebné pro **vložený příklad OleControlType.CommandButton**.

## Krok 2: Napište celý program

Vytvořte nebo nahraďte soubor `Program.cs` následujícím kódem. Obsahuje všechny požadované `using` direktivy, načtení licence a čtyřkrokový pracovní postup zobrazený v původním úryvku.

```csharp
using System;
using System.Drawing;               // For Rectangle
using Aspose.Words;
using Aspose.Words.Drawing;          // For OleControlType

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // Optional: load a trial or commercial license.
        // -------------------------------------------------
        // var license = new Aspose.Words.License();
        // license.SetLicense("Aspose.Words.lic");

        // -------------------------------------------------
        // Step 1: Create a new blank document
        // -------------------------------------------------
        Document doc = new Document();

        // -------------------------------------------------
        // Step 2: Initialize a DocumentBuilder to work with the document
        // -------------------------------------------------
        DocumentBuilder builder = new DocumentBuilder(doc);

        // -------------------------------------------------
        // Step 3: Insert an ActiveX CommandButton control
        // -------------------------------------------------
        // OleControlType.CommandButton creates a CommandButton.
        // "ClickMe" is the control's name.
        // The Rectangle defines the button's position (x, y) and size (width, height).
        builder.InsertForms2OleControl(
            OleControlType.CommandButton,
            "ClickMe",
            new Rectangle(100, 100, 80, 30));

        // -------------------------------------------------
        // Step 4: Save the document containing the ActiveX button
        // -------------------------------------------------
        string outputPath = "ActiveXButton.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

### Proč je každý řádek důležitý

* **Načtení licence** – zajišťuje, že nejste omezeni evaluačními omezeními.  
* **`Document doc = new Document();`** – vytváří kontejner pro veškerý obsah Wordu; to je základ **vloženého příkladu OleControlType.CommandButton**.  
* **`DocumentBuilder builder = new DocumentBuilder(doc);`** – poskytuje plynulé API pro přidávání textu, obrázků a ovládacích prvků.  
* **`InsertForms2OleControl`** – hlavní metoda, která implementuje **jak přidat ovládací prvky formuláře do dokumentu Word**. Hodnota výčtu `OleControlType.CommandButton` říká Aspose.Words, aby vytvořil ActiveX tlačítko.  
* **`new Rectangle(100, 100, 80, 30)`** – umisťuje tlačítko 100 pt od levého a horního okraje, s šířkou 80 pt a výškou 30 pt. Přizpůsobte tato čísla podle vašeho rozvržení.  
* **`doc.Save`** – zapíše soubor .docx na disk; soubor nyní obsahuje vložené tlačítko.

## Krok 3: Sestavte a spusťte program

Z adresáře projektu spusťte:

```bash
dotnet run
```

Měli byste vidět zprávu v konzoli:

```
Document saved to ActiveXButton.docx
```

Otevřete `ActiveXButton.docx` v Microsoft Word. Uvidíte tlačítko s popiskem **ClickMe**, umístěné přibližně uprostřed stránky. Kliknutím na tlačítko spustíte výchozí chování ActiveX (což je obvykle žádná operace, pokud nepřipojíte makro).

![vložený příklad olecontroltype.commandbutton](/images/activex-button.png "ActiveX CommandButton vložený do dokumentu Word")

*Image alt text:* vložený příklad olecontroltype.commandbutton – ActiveX CommandButton zobrazený v dokumentu Word.

## Krok 4: Přizpůsobení tlačítka (volitelné)

Základní **vložený příklad OleControlType.CommandButton** vytvoří výchozí tlačítko. Můžete upravit jeho popisek, písmo nebo dokonce připojit makro úpravou podkladového OLE objektu. Níže je stručný způsob, jak po vložení změnit popisek tlačítka:

```csharp
// Retrieve the first shape (our button) from the document
Shape buttonShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);

// Access the OLE format and set the caption
buttonShape.OleFormat.GetControl().SetProperty("Caption", "Submit");
```

> **Poznámka:** Přímá manipulace s OLE vlastnostmi vyžaduje pochopení podkladového COM rozhraní. Ve většině scénářů je výchozí popisek dostačující.

## Krok 5: Časté problémy a jak se jim vyhnout

| Problém | Proč se to děje | Řešení |
|---------|----------------|--------|
| Tlačítko se ve Wordu nezobrazuje | Dokument byl uložen jako `.docx`, ale otevřen v prohlížeči, který odstraňuje OLE ovládací prvky (např. Google Docs). | Otevřete soubor v Microsoft Word nebo Word Online s právy pro úpravy. |
| Chyba běhu `ArgumentOutOfRangeException` | Souřadnice `Rectangle` jsou mimo okraje stránky. | Použijte hodnoty v rámci velikosti stránky (např. 0‑500 pro A4). |
| Výjimka licence | Zkušební licence vyprší po 30 dnech. | Načtěte platný soubor licence nebo požádejte o prodlouženou zkušební verzi od Aspose. |

## Krok 6: Jak tento příklad zapadá do větších automatizačních projektů

Pokud potřebujete **jak přidat ovládací prvky formuláře do dokumentu Word** ve velkém měřítku – například generovat stovky šablon smluv – zabalte logiku vkládání do znovupoužitelné metody:

```csharp
static void AddCommandButton(DocumentBuilder builder, string name, Rectangle bounds)
{
    builder.InsertForms2OleControl(OleControlType.CommandButton, name, bounds);
}
```

Pak můžete volat `AddCommandButton` uvnitř smyček, které zpracovávají řádky dat, a zajistit, že každý vygenerovaný dokument obsahuje jedinečně pojmenované tlačítko (např. `Approve_001`, `Approve_002`).

## Závěr

Nyní máte kompletní **vložený příklad OleControlType.CommandButton**, který demonstruje **jak přidat ovládací prvky formuláře do dokumentu Word** pomocí Aspose.Words pro .NET. Tutoriál pokryl nastavení projektu, celý zdrojový kód, tipy pro přizpůsobení a běžné kroky řešení problémů.

Odtud můžete zkoumat:

- Přidání dalších typů ovládacích prvků, jako jsou **CheckBox** nebo **ComboBox** (`OleControlType.CheckBox`, `OleControlType.ComboBox`).  
- Propojení tlačítka s VBA makrem pro bohatší interaktivitu.  
- Generování PDF ze stejného dokumentu při zachování formulářových polí.

Experimentujte s různými velikostmi, pozicemi a názvy ovládacích prvků, aby vyhovovaly vašemu konkrétnímu případu použití. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Vložit pole formuláře Combo Box do dokumentu Word](/words/english/net/add-content-using-documentbuilder/insert-combo-box-form-field/)
- [Vložit pole formuláře Check Box do dokumentu Word](/words/english/net/add-content-using-documentbuilder/insert-check-box-form-field/)
- [Vložit pole formuláře Text Input do dokumentu Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}