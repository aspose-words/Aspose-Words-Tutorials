---
category: general
date: 2026-02-10
description: Vytvořte přístupný PDF z dokumentu Word v C#. Naučte se, jak převést
  Word na PDF, exportovat docx jako PDF a přidat přístupnost do PDF pomocí Aspose.Words.
draft: false
keywords:
- create accessible pdf
- convert word to pdf
- export docx as pdf
- save document as pdf
- add accessibility to pdf
language: cs
og_description: Vytvořte přístupný PDF ze souboru Word pomocí C#. Tento návod ukazuje,
  jak převést Word na PDF, exportovat docx jako PDF a přidat přístupnost do PDF.
og_title: Vytvořte přístupný PDF – Převod Wordu do PDF s přístupností
tags:
- Aspose.Words
- PDF/UA
- C#
- Document Conversion
title: Vytvořte přístupný PDF – Převod Wordu na PDF s přístupností
url: /cs/net/basic-conversions/create-accessible-pdf-convert-word-to-pdf-accessibility/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte přístupný PDF – Převod Wordu do PDF s přístupností

Už jste někdy potřebovali **vytvořit přístupný PDF** ze souboru Word, ale nebyli jste si jisti, která nastavení skutečně dělají rozdíl? Nejste v tom sami. Mnoho vývojářů se dívá na `docx` a přemýšlí, proč výsledný PDF neprojde kontrolou čteček obrazovky. Dobrá zpráva? S několika řádky C# a správnými možnostmi ukládání můžete **převést Word do PDF**, **exportovat docx jako PDF** a **přidat přístupnost do PDF** v jednom plynulém procesu.

V tomto tutoriálu projdeme celý proces krok za krokem, vysvětlíme, proč je každé nastavení důležité, a poskytneme připravený ukázkový kód. Na konci budete mít PDF, které splňuje standard PDF/UA‑2 (univerzální standard přístupnosti), a budete vědět, jak jej upravit pro své vlastní projekty.

## Co budete potřebovat

- **Aspose.Words for .NET** (nejnovější verze, např. 24.9). Jedná se o komerční knihovnu, ale nabízí bezplatnou zkušební verzi, která je ideální pro testování.
- Vývojové prostředí .NET (Visual Studio, Rider nebo `dotnet` CLI).
- Jednoduchý dokument Word (`input.docx`), který chcete učinit přístupným.
- Volitelně: validátor PDF/UA (např. nástroj PAC 2021), pokud chcete dvojitě ověřit soulad.

To je vše—žádné další balíčky NuGet, žádné složité XML, jen čisté C#.

![create accessible pdf example](image.png "create accessible pdf example")

## Krok 1: Načtení dokumentu Word

Nejprve načtěte zdrojový `.docx`. Aspose.Words abstrahuje formát souboru, takže se nemusíte starat o Office interop nebo COM.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the source Word document
Document doc = new Document(@"C:\MyFiles\input.docx");
```

**Proč je to důležité:** Načtení dokumentu vytvoří DOM v paměti, který můžete před uložením upravovat. Pokud soubor obsahuje nadpisy, tabulky nebo obrázky, Aspose.Words zachová jejich strukturu, což je později klíčové pro přístupnost.

> **Tip:** Pokud je váš dokument v proudu (např. nahraný přes API), můžete proud předat přímo konstruktoru `Document`—není nutné jej nejprve zapisovat na disk.

## Krok 2: Nastavení možností ukládání PDF pro **vytvoření přístupného PDF**

Nyní řekneme Aspose, jak má být PDF vygenerováno. Klíčová vlastnost je `PdfCompliance`, kterou nastavíme na `PdfCompliance.PdfUAXmpa2`. Tento příznak instruuje knihovnu, aby vytvořila soubor splňující PDF/UA‑2, automaticky zacházející s věcmi jako vodorovné čáry (`<hr>`) jako *artefakty* místo obsahu—právě to, co kontrolují nástroje pro přístupnost.

```csharp
// Configure PDF save options for PDF/UA‑2 compliance
PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
{
    // This ensures the output meets PDF/UA‑2 (PDF/UA‑2) standards
    PdfCompliance = PdfCompliance.PdfUAXmpa2,

    // Optional: embed the source document's fonts for better rendering
    EmbedFullFonts = true,

    // Optional: preserve the original document's structure tree
    PreserveFormFields = true
};
```

**Proč je to důležité:**  
- **Soulad s PDF/UA‑2** zajišťuje, že asistivní technologie mohou správně interpretovat nadpisy, tabulky a dekorativní prvky.  
- **Vkládání fontů** zabraňuje posunům rozvržení na zařízeních, která nemají nainstalované původní fonty.  
- **Zachování formulářových polí** udržuje interaktivní prvky použitelné pro čtečky obrazovky.

Pokud potřebujete obyčejný, nepřístupný PDF, můžete řádek `PdfCompliance` vynechat—ale pak ztratíte výhody přístupnosti, které chceme.

## Krok 3: Uložení dokumentu jako přístupného PDF

Nakonec zapište soubor na disk (nebo do proudu). Stejná metoda `Save` funguje pro každý formát, který Aspose podporuje, takže v podstatě **exportujete docx jako PDF** jedním voláním.

```csharp
// Save the document as an accessible PDF
string outputPath = @"C:\MyFiles\Accessible.pdf";
doc.Save(outputPath, pdfSaveOptions);
```

Po spuštění tohoto řádku by se `Accessible.pdf` měl otevřít v libovolném prohlížeči PDF a projít základními kontrolami PDF/UA. Můžete to ověřit pomocí nástrojů jako **PAC 2021** nebo **PDF Accessibility Checker (PAC)**.

**Očekávaný výsledek:**  
- PDF obsahuje logické pořadí čtení odpovídající nadpisům ve Wordu.  
- Dekorativní prvky, jako vodorovné čáry, jsou označeny jako *artefakty*, nikoli jako obsah.  
- Veškerý text je prohledávatelný a vybíratelný a obrázky si zachovávají svůj alt‑text (pokud jste jej nastavili ve Wordu).

## Ověření přístupnosti (volitelné, ale doporučené)

Spuštění validátoru je rychlý způsob, jak potvrdit, že skutečně **přidáváte přístupnost do PDF**.

```csharp
using System.Diagnostics;

// Assuming you have PAC installed and added to PATH
Process.Start("pac.exe", $"\"{outputPath}\"");
```

Pokud nástroj nehlásí žádné chyby, máte vše v pořádku. Pokud vidíte varování o chybějícím alt‑textu, vraťte se k původnímu dokumentu Word a přidejte popisy k obrázkům—Aspose je automaticky přenese.

## Běžné varianty a okrajové případy

| Scénář | Co upravit | Proč |
|----------|----------------|-----|
| **Velké dokumenty (100+ stránek)** | Nastavte `MemoryUsage` na `MemoryUsageMode.LowMemory` v `PdfSaveOptions` | Zabraňuje výjimkám nedostatku paměti na 32‑bitových procesech |
| **Vlastní PDF tagy** | Použijte `doc.CustomDocumentProperties` nebo `doc.Markup` k přidání položek `StructureTreeRoot` | Dává vám jemnozrnnou kontrolu nad stromem přístupnosti |
| **PDF chráněné heslem** | Nastavte `pdfSaveOptions.EncryptionDetails` s uživatelským heslem | Udržuje PDF zabezpečené a zároveň přístupné oprávněným uživatelům |
| **Obrázky bez alt‑textu** | Předzpracujte Word soubor: `foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true)) { if (string.IsNullOrEmpty(shape.AlternativeText)) shape.AlternativeText = "Descriptive alt text"; }` | Zajišťuje, že čtečky obrazovky mají co číst |

Tyto úpravy vám umožní **uložit dokument jako PDF** způsobem, který odpovídá omezením vašeho projektu, aniž byste obětovali přístupnost.

## Kompletní funkční příklad

Zde je kompletní, připravený program. Vložte jej do konzolové aplikace, upravte cesty a stiskněte **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

namespace AccessiblePdfDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source Word document
            string inputPath = @"C:\MyFiles\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF save options for PDF/UA‑2 compliance
            PdfSaveOptions pdfSaveOptions = new PdfSaveOptions
            {
                PdfCompliance = PdfCompliance.PdfUAXmpa2,
                EmbedFullFonts = true,
                PreserveFormFields = true
            };

            // Optional: handle large files gracefully
            // pdfSaveOptions.MemoryUsage = MemoryUsageMode.LowMemory;

            // 3️⃣ Save the document as an accessible PDF
            string outputPath = @"C:\MyFiles\Accessible.pdf";
            doc.Save(outputPath, pdfSaveOptions);

            Console.WriteLine($"✅ Accessible PDF created at: {outputPath}");
        }
    }
}
```

Spusťte jej, poté otevřete `Accessible.pdf` v Adobe Readeru. Zvolte **File → Properties → Description**—uvidíte „PDF/UA“ uvedené pod „PDF/A Conformance“. To je vizuální indikátor, že jste úspěšně **vytvořili přístupný pdf**.

## Často kladené otázky

**Q: Funguje to s .NET Core?**  
A: Naprosto. Aspose.Words podporuje .NET Standard 2.0+, takže stejný kód běží na .NET 5/6/7 bez úprav.

**Q: Co když potřebuji převést mnoho souborů najednou?**  
A: Zabalte logiku do

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}