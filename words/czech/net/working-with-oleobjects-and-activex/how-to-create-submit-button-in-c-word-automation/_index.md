---
category: general
date: 2026-08-23
description: Vytvořte tlačítko Odeslat v automatizaci Wordu pomocí C#. Naučte se přidat
  ActiveX tlačítko, nastavit název tlačítka, popisek a text programově.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create submit button
- set button text
- set button name
- add activex button
- set button caption
language: cs
lastmod: 2026-08-23
og_description: Vytvořte tlačítko Odeslat v automatizaci Wordu v C#. Tento průvodce
  ukazuje, jak přidat ActiveX tlačítko, nastavit jeho název, popisek a text pomocí
  Aspose.Words.
og_image_alt: Screenshot of a Word document showing a created submit button
og_title: Vytvořte tlačítko Odeslat v automatizaci Wordu pomocí C#
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  headline: How to create submit button in C# Word automation
  type: TechArticle
- description: Create submit button in C# Word automation. Learn to add an ActiveX
    button, set button name, caption, and text programmatically.
  name: How to create submit button in C# Word automation
  steps:
  - name: Expected output
    text: 'Running the program creates `SubmitButton.docx`. When you open the file
      in Microsoft Word:'
  - name: Handling naming collisions
    text: 'If you run the routine multiple times on the same document, Word may auto‑rename
      duplicate controls. To guarantee uniqueness, you can prepend a GUID:'
  - name: Localizing the button caption
    text: 'For multilingual documents, store captions in a resource file and assign
      them at runtime:'
  - name: Responding to the button click
    text: 'The button itself does not contain click logic in C#. You typically attach
      a VBA macro:'
  type: HowTo
tags:
- C#
- Word automation
- ActiveX
- Aspose.Words
title: Jak vytvořit tlačítko Odeslat v automatizaci Wordu pomocí C#
url: /cs/net/working-with-oleobjects-and-activex/how-to-create-submit-button-in-c-word-automation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit tlačítko odeslat v C# Word automatizaci

Pokud potřebujete **vytvořit tlačítko odeslat** uvnitř dokumentu Word pomocí C#, tento návod vás provede celým procesem. Ukážeme si, jak přidat ActiveX tlačítko, přiřadit mu programový název a nastavit popisek tlačítka tak, aby vypadal jako běžný ovládací prvek *Submit*.

Automatizace formulářových ovládacích prvků ve Wordu může nahradit ruční práci s rozvržením a zajistit konzistenci napříč stovkami dokumentů. V následujících krocích se také naučíte, jak **nastavit text tlačítka**, **nastavit název tlačítka** a **nastavit popisek tlačítka** — všechny tyto kroky jsou nezbytné, když tlačítko spolupracuje s makro‑řízeným pracovním tokem.

## Požadavky

Než začnete, ujistěte se, že máte:

* .NET 6.0 (nebo novější) nainstalovaný.
* Odkaz na **Aspose.Words for .NET** (knihovna, která poskytuje `DocumentBuilder.InsertForms2OleControl`).
* Základní znalosti C# a ActiveX formulářových ovládacích prvků ve Wordu.

Aspose.Words můžete nainstalovat přes NuGet:

```bash
dotnet add package Aspose.Words
```

> **Tip:** Použijte nejnovější stabilní verzi Aspose.Words, abyste získali opravy chyb a nové funkce související s ActiveX ovládacími prvky.

## Přehled řešení

Návod je rozdělen do tří jasných kroků:

1. **Přidat ActiveX tlačítko** — použijte metodu `InsertForms2OleControl` k umístění tlačítka příkazu do dokumentu.  
2. **Nastavit název tlačítka** — přiřaďte jedinečný programový identifikátor pomocí vlastnosti `Name`.  
3. **Nastavit popisek tlačítka** — definujte viditelný text na tlačítku pomocí vlastnosti `Caption` (která také řídí **nastavení textu tlačítka**, který vidíte v UI).

Na konci tohoto návodu budete mít plně funkční **vytvořit tlačítko odeslat** rutinu, kterou můžete použít v jakémkoli projektu Word automatizace.

## Krok 1: Přidat ActiveX tlačítko do dokumentu

Prvním úkolem je **přidat ActiveX tlačítko** do souboru Word. Aspose.Words poskytuje výčtový typ `Forms2OleControlType.CommandButton` právě pro tento účel.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Load or create a new document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a CommandButton ActiveX control at the cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl(
    Forms2OleControlType.CommandButton);
```

**Proč je tento krok důležitý:**  
ActiveX ovládací prvky jsou jediné formulářové elementy ve Wordu, které mohou spouštět VBA makra nebo komunikovat s externím kódem. Přidání ovládacího prvku vytvoří zástupce, který mohou následné kroky konfigurovat.

> **Okrajový případ:** Pokud dokument již obsahuje ovládací prvek se stejným názvem, Word automaticky přejmenuje nový (např. `CommandButton1`). Explicitní nastavení názvu v dalším kroku tomuto kolizi předchází.

## Krok 2: Nastavit název tlačítka

Spolehlivé **nastavení názvu tlačítka** je klíčové, když potřebujete odkazovat na ovládací prvek z VBA nebo z jiných částí vašeho C# kódu. Vlastnost `Name` dává tlačítku programový identifikátor.

```csharp
// Assign a unique programmatic name
commandBtn.Name = "btnSubmit";
```

**Proč byste měli nastavit název:**  
Když se dokument otevře, VBA může získat tlačítko pomocí `ActiveDocument.InlineShapes("btnSubmit")`. Smysluplný název jako `btnSubmit` také usnadňuje pochopení záměru při prohlížení XML dokumentu.

> **Tip:** Používejte krátké, alfanumerické názvy, které začínají písmenem, aby byly kompatibilní s pravidly pojmenování ve VBA.

## Krok 3: Nastavit popisek tlačítka (viditelný text)

Text, který uživatelé vidí na tlačítku, je řízen vlastností **nastavit popisek tlačítka**. V uživatelském rozhraní Wordu se to zobrazuje jako popisek tlačítka, což je také **nastavení textu tlačítka**, který chcete zobrazit.

```csharp
// Define the text shown on the button
commandBtn.Caption = "Submit";
```

**Proč je popisek důležitý:**  
Popisek je uživatelsky viditelná značka. Změna popisku později neovlivní název tlačítka, takže můžete lokalizovat UI, aniž byste rozbili kód, který závisí na `btnSubmit`.

> **Často kladená otázka:** *Mohu nastavit jak Caption, tak Value?*  
> Pro `CommandButton` vlastnost `Caption` řídí popisek, zatímco `Value` se nepoužívá. Pokud potřebujete skrytou hodnotu, uložte ji do vlastního dokumentového vlastnosti.

## Kompletní funkční příklad

Spojením tří kroků získáte kompletní rutinu, kterou můžete vložit do libovolné konzolové nebo Windows aplikace:

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
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert the ActiveX command button
        Forms2OleControl commandBtn = builder.InsertForms2OleControl(
            Forms2OleControlType.CommandButton);

        // 3. Set a meaningful name for later reference
        commandBtn.Name = "btnSubmit";

        // 4. Set the visible caption (this is the button text)
        commandBtn.Caption = "Submit";

        // Optional: position the button (in points)
        commandBtn.Left = 100;   // distance from left margin
        commandBtn.Top = 200;    // distance from top margin
        commandBtn.Width = 80;
        commandBtn.Height = 30;

        // Save the document
        doc.Save("SubmitButton.docx");
        Console.WriteLine("Document with submit button created successfully.");
    }
}
```

### Očekávaný výstup

Po spuštění programu se vytvoří soubor `SubmitButton.docx`. Když soubor otevřete v Microsoft Word:

* Zobrazí se **Submit** tlačítko na určeném místě.
* Název tlačítka je `btnSubmit` (ověříte v *Developer → Design Mode → Properties*).
* Kliknutí na tlačítko v režimu návrhu zobrazí popisek *Submit*.

Nyní máte znovupoužitelný stavební blok pro jakékoli řešení založené na formulářích ve Wordu.

## Další úvahy

### Řešení kolizí názvů

Pokud rutinu spustíte vícekrát na stejném dokumentu, Word může automaticky přejmenovat duplicitní ovládací prvky. Pro zajištění jedinečnosti můžete předřadit GUID:

```csharp
commandBtn.Name = $"btnSubmit_{Guid.NewGuid():N}";
```

### Lokalizace popisku tlačítka

Pro vícejazyčné dokumenty uložte popisky do souboru zdrojů a při běhu je přiřaďte:

```csharp
commandBtn.Caption = Resources.SubmitButtonLabel;
```

### Reakce na kliknutí tlačítka

Tlačítko samo o sobě neobsahuje logiku kliknutí v C#. Obvykle k němu připojíte VBA makro:

```vba
Sub btnSubmit_Click()
    MsgBox "Form submitted!"
End Sub
```

Protože jste **nastavili název tlačítka** na `btnSubmit`, název makra automaticky následuje konvenci `<Name>_Click`.

## Často kladené otázky (FAQ)

| Otázka | Odpověď |
|----------|--------|
| **Proč se tlačítko zobrazuje prázdně?** | Ujistěte se, že jste nastavili vlastnost `Caption`; bez ní tlačítko nezobrazuje žádný text. |
| **Mohu použít jiný ActiveX ovládací prvek?** | Ano. Nahraďte `Forms2OleControlType.CommandButton` za `CheckBox`, `OptionButton` apod., ale vlastnosti se liší. |
| **Je to kompatibilní s .NET Core?** | Aspose.Words for .NET podporuje .NET 6+, takže stejný kód funguje na .NET Core i .NET Framework. |
| **Co když dokument už obsahuje tlačítko?** | Použijte jedinečný `Name` (např. připojte GUID), aby nedošlo ke konfliktům. |

## Závěr

Nyní víte, jak **vytvořit tlačítko odeslat** programově v dokumentu Word pomocí C#. Dodržením tří kroků — **přidat ActiveX tlačítko**, **nastavit název tlačítka** a **nastavit popisek tlačítka** — můžete spolehlivě **nastavit text tlačítka**, **nastavit název tlačítka** a **nastavit popisek tlačítka** pro jakékoli automatizované formulářové řešení.  

Od sem můžete pokračovat:

* Přidáním VBA makra, které reaguje na kliknutí **tlačítka odeslat**.  
* Stylováním tlačítka pomocí vlastních fontů nebo barev prostřednictvím podkladového XML.  
* Generováním více tlačítek ve smyčce pro dynamické formuláře.

Neváhejte experimentovat s různými popisky, názvy a pozicemi, aby vyhovovaly vašemu konkrétnímu pracovnímu postupu. Šťastnou automatizaci!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobným krok‑za‑krokem vysvětlením, které vám pomohou zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create a Line Chart in Word using Aspose.Words for .NET](/words/english/net/working-with-charts/create-chart-using-shape/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}