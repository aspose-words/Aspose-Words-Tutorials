---
category: general
date: 2026-07-06
description: Povolte režim obnovy pro otevření poškozeného souboru docx pomocí Aspose.Words.
  Naučte se rychle obnovit poškozený dokument Word.
draft: false
keywords:
- enable recovery mode
- recover corrupted word document
- recover damaged docx file
- how to open corrupted docx
language: cs
og_description: Povolení režimu obnovy vám umožní otevřít poškozený soubor docx a
  pokusit se obnovit poškozený dokument Word.
og_title: Povolit režim obnovy – Obnovit poškozený dokument Word
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Enable recovery mode to open a corrupted docx file with Aspose.Words.
    Learn how to recover corrupted Word document quickly.
  headline: Enable recovery mode – Recover corrupted Word document
  type: TechArticle
- questions:
  - answer: No. It only affects how the library reads the file in memory. The source
      remains untouched unless you explicitly call `Save`.
    question: Does enabling recovery mode modify the original file?
  - answer: Usually yes, as long as the underlying ZIP entry isn’t broken. If an image
      stream is missing, Aspose.Words will skip it and continue.
    question: Can I recover images that were embedded in the corrupted docx?
  - answer: Slightly, because the parser performs additional checks. The overhead
      is negligible for typical documents (<10 MB).
    question: Is recovery mode slower?
  - answer: '`RecoveryMode.Auto` (default) tries to recover only when an error occurs.
      `RecoveryMode.None` disables any recovery attempts. `RecoveryMode.Recover` forces
      the attempt every time. ## Full Working Example Below is a self‑contained console
      app you can copy‑paste into a new .NET project. It demonstrate'
    question: What other recovery options exist?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Document Recovery
- Word
title: Povolit režim obnovy – Obnovit poškozený dokument Word
url: /cs/net/programming-with-loadoptions/enable-recovery-mode-recover-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Povolení režimu obnovy – Obnovení poškozeného dokumentu Word

Už jste někdy zkusili otevřít **poškozený docx** a sledovali chybové dialogové okno, které se na vás dívá? Je to frustrující, zejména když soubor obsahuje týdny práce. Naštěstí Aspose.Words vám poskytuje způsob, jak *povolit režim obnovy*, abyste se mohli pokusit zachránit obsah bez ručního kopírování‑vkládání.

V tomto průvodci projdeme přesné kroky k **povolení režimu obnovy**, načtení poškozeného souboru a uložení použitelné kopie. Na konci budete vědět, jak programově *obnovit poškozené soubory Word* a dokonce elegantně zvládnout scénář *obnovení poškozeného docx souboru*.

## Co budete potřebovat

- .NET 6 (nebo jakékoli aktuální .NET runtime) – knihovna funguje také na .NET Framework.
- Visual Studio 2022 nebo VS Code – postačí vám vaše oblíbené IDE.
- **Aspose.Words for .NET** NuGet balíček (`Install-Package Aspose.Words`) – jedná se o jedinou externí závislost.
- Ukázkový poškozený `docx` (nazveme ho `corrupted.docx`).

To je vše. Žádné další nástroje, žádné ruční manipulace s XML. Pouze několik řádků C#.

![enable recovery mode in Aspose.Words](image-url-placeholder.png)

*Image alt text: povolení režimu obnovy v Aspose.Words*

## Krok 1: Instalace Aspose.Words a nastavení projektu

Otevřete svůj terminál (nebo Package Manager Console) a spusťte:

```bash
dotnet add package Aspose.Words
```

Alternativně ve Visual Studio otevřete **Tools → NuGet Package Manager → Manage NuGet Packages** a vyhledejte *Aspose.Words*. Po instalaci přidejte jmenný prostor na začátek souboru:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **Tip:** Udržujte své balíčky aktuální. Logika obnovy se zlepšuje s každým vydáním.

## Krok 2: Povolení režimu obnovy pomocí `LoadOptions`

Jádrem řešení je třída `LoadOptions`. Nastavením její vlastnosti `RecoveryMode` na `RecoveryMode.Recover` řeknete Aspose.Words, aby *povolil režim obnovy* při parsování dokumentu.

```csharp
// Step 2: Create LoadOptions and enable recovery mode
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover   // <-- this line turns on recovery
};
```

Proč je to důležité? Bez režimu obnovy Aspose.Words přeruší zpracování při první známce poškození. S ním se knihovna snaží co nejlépe přeskočit poškozené části a stále vytvořit použitelný objekt `Document`.

## Krok 3: Načtení potenciálně poškozeného souboru

Nyní skutečně načteme soubor. Pokud je dokument neodstranitelně poškozen, Aspose.Words stále vrátí instanci `Document`, ale některé prvky mohou chybět.

```csharp
// Step 3: Load the potentially corrupted document using the recovery options
Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
```

Všimněte si, že cesta je absolutní řetězec; upravte ji podle umístění vašeho testovacího souboru. Konstruktor `Document` načte soubor **s povoleným režimem obnovy**, což vám dává šanci *obnovit poškozený Word dokument*.

## Krok 4: Ověření, co bylo obnoveno (volitelné, ale užitečné)

Je dobrým zvykem prozkoumat načtený dokument, než se rozhodnete něco přepsat. Pro rychlou kontrolu můžete vypsat prvních několik odstavců do konzole:

```csharp
// Optional: Print first 3 paragraphs to verify recovery
for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
{
    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
}
```

Pokud uvidíte poškozený text nebo spoustu prázdných řetězců, soubor může být **příliš poškozen**. Přesto nyní máte objekt `Document`, který můžete upravovat – přidat záhlaví, nahradit chybějící obrázky atd.

## Krok 5: Uložení obnoveného dokumentu

Předpokládáme, že kontrola proběhla v pořádku, zapište obnovenou verzi do nového souboru. Tento krok efektivně *obnoví poškozený docx soubor* a poskytne vám čistou kopii, kterou můžete otevřít ve Wordu.

```csharp
// Step 5: Save the recovered document
string outputPath = @"C:\Temp\recovered.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Recovered document saved to: {outputPath}");
```

Pokud byl původní soubor `.doc` nebo jiný formát, můžete podle toho změnit `SaveFormat` (např. `SaveFormat.Pdf` pro výstup PDF).

## Krok 6: Zpracování výjimek a okrajových případů

I při povoleném režimu obnovy jsou některé katastrofy neobnovitelné (např. zcela oříznuté zip struktury). Zabalte načítání do bloku try‑catch, abyste tyto problémy odhalili:

```csharp
try
{
    Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
    // proceed with saving...
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to recover the document: {ex.Message}");
    // You might log the stack trace or notify the user.
}
```

Často kladená otázka je **„jak otevřít poškozený docx“**, když je soubor chráněn heslem. Režim obnovy **neobchází** šifrování; stále budete potřebovat heslo. V takovém případě nastavte `LoadOptions.Password` před načtením.

## Často kladené otázky (FAQ)

**Q: Modifikuje povolení režimu obnovy původní soubor?**  
A: Ne. Ovlivňuje pouze to, jak knihovna čte soubor v paměti. Zdroj zůstane nedotčen, pokud výslovně nevoláte `Save`.

**Q: Mohu obnovit obrázky, které byly vloženy do poškozeného docx?**  
A: Obvykle ano, pokud není poškozena podkladová ZIP položka. Pokud chybí stream obrázku, Aspose.Words jej přeskočí a pokračuje.

**Q: Je režim obnovy pomalejší?**  
A: Mírně, protože parser provádí další kontroly. Zátěž je zanedbatelná pro typické dokumenty (<10 MB).

**Q: Jaké další možnosti obnovy existují?**  
A: `RecoveryMode.Auto` (výchozí) se pokouší o obnovu pouze při výskytu chyby. `RecoveryMode.None` zakazuje jakékoli pokusy o obnovu. `RecoveryMode.Recover` vynutí pokus při každém načtení.

## Kompletní funkční příklad

Níže je samostatná konzolová aplikace, kterou můžete zkopírovat a vložit do nového .NET projektu. Ukazuje celý tok – od instalace balíčku po uložení obnoveného souboru.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace RecoverCorruptedDocx
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the corrupted document
            string inputPath = @"C:\Temp\corrupted.docx";
            // Where the recovered file will be written
            string outputPath = @"C:\Temp\recovered.docx";

            // Step 1: Create LoadOptions and enable recovery mode
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Recover
            };

            try
            {
                // Step 2: Load the document with recovery enabled
                Document doc = new Document(inputPath, loadOptions);

                // Optional sanity check – print first three paragraphs
                Console.WriteLine("=== First three paragraphs after recovery ===");
                for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
                {
                    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
                }

                // Step 3: Save the recovered document
                doc.Save(outputPath, SaveFormat.Docx);
                Console.WriteLine($"\nRecovered document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to open or recover the document: {ex.Message}");
            }
        }
    }
}
```

**Očekávaný výstup (při úspěšné obnově):**

```
=== First three paragraphs after recovery ===
Paragraph 1: Project Overview
Paragraph 2: This document outlines...
Paragraph 3: ...

Recovered document saved to: C:\Temp\recovered.docx
```

Pokud je soubor nevyhnutelně poškozen, uvidíte chybovou zprávu místo výpisu odstavců.

## Závěr

Právě jsme ukázali, jak **povolit režim obnovy** v Aspose.Words, načíst poškozený `docx` a **obnovit poškozená data Word dokumentu** do nového souboru. Stejný vzor vám umožní *obnovit poškozený docx soubor* ve dávkových úlohách, automatizovaných e‑mailových přílohách, nebo

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [jak obnovit docx – nastavit režim obnovy a otevřít poškozené soubory Word](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [jak obnovit docx s Aspose.Words – krok za krokem](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Obnovení poškozeného souboru Word – Kompletní průvodce otevřením poškozeného DOCX a získáním stránky](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}