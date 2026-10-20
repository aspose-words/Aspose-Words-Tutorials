---
category: general
date: 2026-03-27
description: 'Aspose náhrada fontů usnadněna: naučte se konfigurovat nastavení fontů,
  zachytávat varování a řešit chybějící fonty ve vašich .NET aplikacích.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: cs
og_description: Zvládněte nahrazování fontů v Aspose konfigurací nastavení fontů a
  zpracováním chybějících fontů pomocí varovného callbacku. Kompletní průvodce v C#.
og_title: Aspose nahrazení fontů – Konfigurace nastavení fontů v C#
tags:
- Aspose.Words
- C#
- Font Management
title: Nahrazení fontů v Aspose – Jak konfigurovat nastavení fontů v C#
url: /cs/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Kompletní průvodce nastavením fontů

Už jste někdy narazili na dokument, který najednou nahradí vaše vlastní písmo něčím generickým? To je **aspose font substitution**, který dělá svou práci – nahrazuje chybějící písma nejbližšími, které najde. Je to užitečné, ale pokud potřebujete vědět *přesně*, které písmo bylo nahrazeno, musíte využít varovný systém knihovny a nastavit fonty sami.

V tomto tutoriálu projdeme reálný scénář: načtení DOCX, který odkazuje na písmo, které nemáte, zachycení události nahrazení a vytištění přátelské zprávy do konzole. Na konci budete pohodlně ovládat **configure font settings**, nastavit **Aspose.Words warning callback** a rozšířit ukázku podle libovolného workflow.

> **Co budete potřebovat**  
> • .NET 6+ (nebo .NET Framework 4.7.2+)  
> • Aspose.Words pro .NET (nejnovější NuGet)  
> • DOCX, který odkazuje na chybějící písmo (nazveme ho `MissingFont.docx`)  

Pojďme na to.

---

## Krok 1: Instalace Aspose.Words a příprava projektu

Než napíšeme jakýkoli kód, ujistěte se, že je odkaz na balíček Aspose.Words:

```bash
dotnet add package Aspose.Words
```

> **Tip:** Použijte nejnovější stabilní verzi; k březnu 2026 je to 23.11.0. Novější vydání vylepšují algoritmy pro hledání fontů a přidávají další typy varování.

Vytvořte novou konzolovou aplikaci (nebo vložte kód do existujícího projektu) a přidejte obvyklé `using` direktivy:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Tyto jmenné prostory nám poskytují přístup k třídám `Document`, `LoadOptions` a dalším souvisejícím s fonty.

---

## Krok 2: Nastavení fontů pomocí LoadOptions

Jádro kontroly **aspose font substitution** spočívá v `LoadOptions.FontSettings`. Poskytnutím prázdného objektu `FontSettings` říkáme Aspose, aby použil výchozí cesty pro hledání *a* aby hlásil jakékoli nahrazení pomocí varovacího callbacku.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Proč se nespoléhat jen na výchozí nastavení? Protože připojení varovacího callbacku (další krok) funguje jen tehdy, když je vlastnost `FontSettings` nenulová. Tento malý řádek nám poskytuje háček do procesu nahrazování, aniž by měnil samotné chování vyhledávání fontů.

---

## Krok 3: Připojení varovacího callbacku pro zachycení nahrazení

Aspose.Words implementuje rozhraní `IWarningCallback`. Kdykoli se stane něco pozoruhodného – například chybějící písmo – volá naši metodu `Warning`. Implementujeme malý handler, který filtruje `WarningType.FontSubstitution` a vypíše popis.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

A zde je samotný handler:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Proč je to důležité** – Bez callbacku Aspose tiše nahrazuje písma a nikdy nevíte, které bylo použito. Callback proces zpřehlední, což je zásadní pro zprávy o shodě nebo ladění problémů s rozvržením.

---

## Krok 4: Načtení dokumentu s nakonfigurovanými možnostmi

Nyní konečně načteme dokument a předáme mu `loadOptions`, které jsme právě připravili. Pokud zdrojový soubor odkazuje na písmo, které není nainstalováno, náš handler se spustí.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Nahraďte `YOUR_DIRECTORY` skutečnou cestou, kde se nachází `MissingFont.docx`. Po spuštění programu byste měli vidět výstup podobný tomuto:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Tento řádek vám přesně řekne, které písmo chybělo a jaký náhradní font Aspose vybral.

---

## Krok 5: (Volitelné) Doladění cest pro vyhledávání fontů

Pokud máte soukromou složku s firemními fonty, můžete Aspose říct, kde má hledat, než přejde na systémové fonty. Jedná se o pokročilé využití **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Nastavení `recursive: true` způsobí, že Aspose prohledá i podadresáře. Nyní knihovna nejprve zkusí vaše soukromé fonty, čímž se sníží šance na nežádoucí nahrazení.

---

## Kompletní funkční příklad

Sestavením všeho dohromady získáte kompletní, připravený program:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Očekávaný výstup** (když je nalezen chybějící font):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Pokud jsou všechna písma přítomna, program běží tiše (žádná varování) a stále vytvoří PDF.

---

## Často kladené otázky a okrajové případy

### Co když potřebuji *zabránit* nahrazení úplně?

Nastavte `FontSettings.SubstitutionSettings` na `null` nebo použijte `FontSettings.FontSubstitutionSettings` k řízení chování. Například:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Nyní Aspose vyhodí výjimku místo tichého nahrazení, kterou můžete zachytit a zpracovat.

### Funguje to i s jinými formáty souborů (např. .doc, .rtf)?

Ano. Stejný objekt `LoadOptions` lze předat libovolnému konstruktoru `Document`, který přijímá cestu k souboru. Varovací callback se spustí pro všechny formáty, které používají fonty.

### Můžu zachytit *přesný* náhradní název fontu?

Ano. Řetězec `info.Description` obsahuje jak chybějící písmo, tak náhradu. Pokud potřebujete název programově, můžete jej parsovat nebo použít objekt `FontInfo` (k dispozici v novějších verzích).

### Jak se to chová v prostředí s více vlákny?

`FontSettings` **není** thread‑safe. Vytvořte samostatný `LoadOptions` (s vlastním `FontSettings`) pro každé vlákno, nebo přístup chráníte pomocí zámku.

---

## Závěr

Probrali jsme vše, co potřebujete k ovládnutí **aspose font substitution** a **configure font settings** v aplikaci C#:

1. Nainstalujte Aspose.Words a přidejte potřebné `using` direktivy.  
2. Vytvořte objekt `LoadOptions` s novým `FontSettings`.  
3. Připojte vlastní `IWarningCallback` pro zobrazení událostí nahrazení.  
4. Načtěte dokument a nechte callback hlásit chybějící písma.  
5. (Volitelné) Rozšiřte cestu pro vyhledávání nebo úplně zakázat nahrazení.

S tímto vzorem můžete logovat chybějící písma pro shodu, upozorňovat uživatele v UI nebo automaticky vkládat náhradní fonty před publikací. Dále můžete prozkoumat **Aspose.Words font substitution policies** nebo integrovat workflow do většího pipeline pro zpracování dokumentů.

Šťastné programování a ať se vaše dokumenty vždy vykreslí s požadovaným typem písma!  

---  

![Diagram showing Aspose.Words loading a document, invoking FontSettings, triggering a warning callback, and outputting substitution info](image-placeholder.png "aspose font substitution workflow")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}