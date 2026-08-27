---
category: general
date: 2026-01-11
description: Obnovte poškozený dokument v C# pomocí Aspose.Words. Naučte se, jak nastavit
  režim obnovy, načíst docx s obnovou a při chybě upozornit uživatele v několika jednoduchých
  krocích.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: cs
og_description: Obnovte poškozený dokument v C# nastavením režimu obnovy, načtením
  DOCX s obnovou a výzvou uživatele při chybě. Kompletní krok‑za‑krokem tutoriál.
og_title: Obnova poškozeného dokumentu v C# – Rychlý průvodce
tags:
- Aspose.Words
- C#
- Document Recovery
title: Obnovit poškozený dokument v C# – nastavit režim obnovy a vyzvat uživatele
url: /cs/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Obnovit poškozený dokument v C# – Kompletní průvodce

Už jste někdy zkusili otevřít DOCX, který vypadá v Wordu v pořádku, ale ve vašem kódu vyvolá výjimku? Pravděpodobně se potýkáte se scénářem **recover corrupted document**. Dobrou zprávou je, že Aspose.Words vám poskytuje detailní kontrolu nad tím, jak s těmito nepříjemnými soubory zacházet – ať už je chcete tiše opravit, vyvolat výjimku, nebo se zeptat uživatele, co má dělat.

V tomto tutoriálu projdeme vše, co potřebujete k **recover corrupted document** souborům, od instalace knihovny po výběr správné možnosti **set recovery mode**, **load docx with recovery**, a nakonec **prompt user on error**, když se něco pokazí. Žádné zbytečnosti, jen kompletní, spustitelný příklad, který můžete vložit do libovolného .NET projektu.

> **Rychlý náhled:** Na konci budete mít konzolovou aplikaci, která načte možná poškozený `corrupt.docx`, zaznamená všechna varování a zeptá se uživatele, zda chce pokračovat, když oprava selže.

## Co budete potřebovat

- **.NET 6.0** nebo novější (kód funguje také na .NET Framework 4.6+).  
- **Aspose.Words for .NET** – nainstalujte přes NuGet (`Install-Package Aspose.Words`).  
- **Poškozený DOCX** soubor připravený k testování (můžete soubor úmyslně poškodit otevřením v hex editoru nebo přejmenováním jeho přípony).  
- Jakékoliv IDE, které máte rádi – Visual Studio, Rider nebo i VS Code vám bude stačit.

> *Tip:* Uchovejte zálohu originálního souboru. Obnova může přepsat části dokumentu a nechcete přijít o dobré části.

## Krok 1 – Instalace Aspose.Words a přidání jmenných prostorů

Nejprve. Získejte knihovnu z NuGet a přidejte požadované jmenné prostory do rozsahu.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

To je vše, co potřebujete pro zbytek průvodce. Jmenný prostor `Aspose.Words.Loading` obsahuje třídu `LoadOptions`, která je klíčem k **set recovery mode**.

## Krok 2 – Vyberte režim obnovy (Primary H2 with Keyword)

### Obnovit poškozený dokument – Nastavení správného režimu obnovy

Aspose.Words nabízí tři chování při obnově:

| Mode | What Happens | When to Use |
|------|--------------|------------|
| **PromptUser** | Zobrazí dialog (nebo můžete implementovat vlastní výzvu) a pokusí se soubor opravit. | Ideální pro interaktivní nástroje, kde může uživatel rozhodnout. |
| **Silent** | Pokusí se opravit automaticky, bez UI. | Vhodné pro dávkové úlohy nebo služby. |
| **ThrowException** | Zastaví zpracování a vyvolá výjimku. | Použijte, když chcete přísnou validaci. |

Níže je ukázáno, jak **set recovery mode** na `PromptUser`. Pokud dáváte přednost tichému zpracování, stačí vyměnit hodnotu výčtu.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

> **Proč je to důležité:** Tím, že explicitně **set recovery mode**, říkáte Aspose.Words, jak agresivní má být. Výchozí hodnota je `PromptUser`, ale explicitnost jasně vyjadřuje váš záměr – jak pro budoucí údržbu, tak pro vyhledávače procházející kód.

## Krok 3 – Načtení DOCX s obnovou

Nyní **load docx with recovery** pomocí `LoadOptions`, které jsme právě nakonfigurovali. Pokud je soubor poškozený, Aspose.Words jej buď opraví, nebo vyvolá varování, v závislosti na režimu.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

Konstruktor `Document` vykonává těžkou práci. V režimu **PromptUser** uvidíte výzvu v konzoli (nebo vlastní UI, pokud se připojíte k událostem `LoadOptions`), která se ptá, zda pokračovat. V režimu **Silent** metoda prostě udělá, co může, a pokračuje dál.

## Krok 4 – Prohlédněte varování a vyzvěte uživatele

Aspose.Words zaznamenává všechny problémy, na které narazí, ve sbírce `Warnings`. Projděme je a dejme uživateli šanci rozhodnout, co dál.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

Úryvek výše **prompt user on error** způsobem přátelským pro konzoli. Pokud vytváříte aplikaci Windows Forms nebo WPF, nahraďte `Console.ReadLine` za `MessageBox` nebo vlastní dialog.

## Krok 5 – Práce s obnoveným dokumentem

V tomto okamžiku je dokument v paměti, opravený tak dobře, jak to Aspose.Words dokázalo. Nyní můžete číst jeho obsah, uložit čistou kopii nebo provést jakoukoli potřebnou manipulaci.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Spuštění celého programu proti poškozenému souboru vytvoří výstup v konzoli podobný tomuto:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Pokud byl soubor ve skutečnosti v pořádku, uvidíte „Document loaded without any warnings.“ a čistá kopie bude identická se zdrojem.

## Kompletní funkční příklad

Zde je celý program na jednom místě. Zkopírujte‑vložte jej do nového konzolového projektu a stiskněte **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Spusťte jej, poškoďte testovací soubor a sledujte obnovu v akci. 🎉

## Okrajové případy a varianty

| Scenario | What to Change | Why |
|----------|----------------|-----|
| **Dávkové zpracování** (bez uživatelské interakce) | Nastavte `RecoveryMode = RecoveryMode.Silent` a odstraňte výzvu v konzoli. | Udržuje pipeline automaticky v chodu. |
| **Přísná validace** (rychlé selhání) | Použijte `RecoveryMode.ThrowException`. Zabalte volání načtení do try/catch a zaznamenejte výjimku. | Zaručuje, že nebudete pracovat s částečně opraveným souborem. |
| **Vlastní UI** (WinForms/WPF) | Přihlaste se k `LoadOptions.LoadingProgress` nebo použijte události `Document.LoadOptions` k zobrazení dialogu. | Poskytuje bohatší zážitek než konzole. |
| **Velké dokumenty** (paměťová omezení) | Načtěte s `LoadOptions.LoadFormat = LoadFormat.Docx` a zvažte `Document.SaveOptions` pro streamování výstupu. | Zabraňuje výjimkám OutOfMemory. |

## Praktické tipy (E‑E‑A‑T signály)

- **Vždy si uchovávejte zálohu** před pokusem o obnovu; proces může přepsat části souboru.  
- **Zaznamenávejte varování** do souboru pro pozdější analýzu; často naznačují příčinu (např. chybějící části, poškozené XML).  
- **Testujte s různými typy poškození** – zkraťte soubor, poškoďte XML tagy nebo změňte strukturu zipu, abyste viděli, jak se chová každý režim.  
- **Pravidelně aktualizujte Aspose.Words**; novější verze zlepšují algoritmy obnovy a přidávají nové typy varování.  
- **Kombinujte s validací** – po obnově spusťte rychlé `document.UpdateFields()` a `document.Save()`, aby byl dokument plně funkční.

## Závěr

Nyní víte, jak **recover corrupted document** soubory v C# pomocí **set recovery mode**, **load docx with recovery** a **prompt user on error**, když se něco pokazí. Kompletní příklad ukazuje čistý, end‑to‑end tok, který funguje v konzolových aplikacích, službách nebo UI projektech.

Další kroky? Zkuste nahradit výzvu v konzoli modálním dialogem ve WinForms aplikaci, experimentujte s režimem **Silent** pro úlohy na pozadí, nebo integrujte logiku obnovy do ASP.NET endpointu pro nahrávání souborů, aby uživatelé mohli nahrát poškozené DOCX soubory a okamžitě získat opravenou verzi.

Šťastné programování a ať vaše dokumenty zůstávají celé!  

![Příklad obnovení poškozeného dokumentu](/images/recover-corrupted-document.png "obnovit poškozený dokument")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}