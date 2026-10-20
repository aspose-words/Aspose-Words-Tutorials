---
category: general
date: 2026-04-24
description: Uložte dokument jako txt a převádějte Word na LaTeX pomocí Aspose.Words.
  Naučte se rychle exportovat matematické rovnice z Wordu do LaTeXu.
draft: false
keywords:
- save document as txt
- convert word to latex
- convert word equations to latex
- export word math latex
language: cs
og_description: Uložte dokument jako txt a převádějte rovnice z Wordu do LaTeXu pomocí
  C#. Kompletní krok‑za‑krokem průvodce s kódem.
og_title: Uložit dokument jako TXT – Exportovat Word Math do LaTeXu
tags:
- Aspose.Words
- C#
- LaTeX
title: Uložit dokument jako TXT – exportovat matematiku z Wordu do LaTeXu v C#
url: /cs/net/programming-with-officemath/save-document-as-txt-export-word-math-to-latex-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uložení dokumentu jako TXT – Export rovnic z Wordu do LaTeXu v C#

Už jste někdy potřebovali **save document as txt** a zároveň zachovat své složité rovnice? Nejste v tom sami. Vestavěná funkce Wordu „Uložit jako prostý text“ zahodí Office Math a zanechá vás s nečitelné nesmysly. Co kdybyste mohli tyto rovnice zachovat, ale ve čistém LaTeXu?  

V tomto tutoriálu projdeme přesně kroky, jak **convert Word to LaTeX**‑ready text pomocí Aspose.Words pro .NET. Na konci budete mít soubor `.txt`, kde je každá rovnice reprezentována správným LaTeX markupem, připravená k vložení do článku nebo markdown souboru. Žádné externí konvertory, žádné ruční kopírování — pouze pár řádků C#.

## Co se naučíte

- Jak načíst soubor `.docx` pomocí Aspose.Words.
- Jak nakonfigurovat `TxtSaveOptions`, aby byl Office Math exportován jako LaTeX.
- Uložení výsledku do prostého textového souboru, který můžete otevřít v libovolném editoru.
- Řešení okrajových případů pro inline a display rovnice a rychlá rada pro hromadné zpracování více dokumentů.

### Požadavky

- .NET 6.0 nebo novější (kód funguje také s .NET Framework 4.6+).
- NuGet balíček Aspose.Words pro .NET (`Install-Package Aspose.Words`).
- Word dokument, který obsahuje alespoň jednu rovnici (objekt Office Math).

---

## Krok 1: Instalace Aspose.Words a nastavení projektu

Nejprve přidejte knihovnu do svého projektu. Otevřete terminál ve složce řešení a spusťte:

```bash
dotnet add package Aspose.Words
```

> **Tip:** Pokud používáte Visual Studio, UI NuGet Package Manager funguje stejně dobře – vyhledejte „Aspose.Words“ a klikněte na Install.

Nyní vytvořte novou konzolovou aplikaci (nebo vložte kód do existující). `using` direktivy, které budete potřebovat, jsou:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Krok 2: Načtení zdrojového dokumentu

Musíme nasměrovat Aspose.Words na Word soubor, který obsahuje rovnice. Nahraďte `YOUR_DIRECTORY/input.docx` skutečnou cestou na vašem počítači.

```csharp
// Load the source .docx file
Document doc = new Document(@"C:\MyDocs\input.docx");
```

> **Proč je to důležité:** Načtení dokumentu poskytuje Aspose.Words plný přístup k interním objektům Office Math, které jsou jinak neviditelné pro jednoduchý textový exportér.

## Krok 3: Konfigurace TxtSaveOptions pro export do LaTeXu

Magie se odehrává v objektu `TxtSaveOptions`. Nastavením `OfficeMathExportMode` na `LaTeX` se každá rovnice převede na její LaTeX ekvivalent.

```csharp
// Configure save options to export Office Math as LaTeX
TxtSaveOptions txtOptions = new TxtSaveOptions
{
    // Export all Office Math objects as LaTeX code
    OfficeMathExportMode = OfficeMathExportMode.LaTeX,

    // Optional: keep line breaks similar to the original layout
    PreserveTableLayout = true
};
```

> **Co když potřebujete místo toho MathML?** Změňte `OfficeMathExportMode` na `MathML`. Stejné API podporuje několik výstupních formátů.

## Krok 4: Uložení dokumentu jako prostý text

Nyní zapíšeme soubor. Výsledný `Math.txt` bude obsahovat běžný text plus LaTeX fragmenty pro každou rovnici.

```csharp
// Save the document as a .txt file with LaTeX equations
doc.Save(@"C:\MyDocs\Math.txt", txtOptions);
Console.WriteLine("Document saved as txt with LaTeX equations.");
```

Spuštění programu vytvoří soubor, který vypadá zhruba takto:

```
This is a simple paragraph.

Here is an inline equation: $E = mc^2$

And a displayed equation:
\[
\int_{0}^{\infty} e^{-x} \, dx = 1
\]
```

Všimněte si, že inline rovnice používá `$…$`, zatímco display rovnice je obalena v `\[` a `\]`. To je standardní LaTeX konvence a Aspose.Words to provádí automaticky.

## Krok 5: Ověření výstupu (volitelné)

Pokud chcete dvakrát zkontrolovat, že LaTeX je platný, můžete `.txt` vložit do LaTeX kompilátoru jako `pdflatex` nebo online rendereru jako Overleaf. Text by se měl kompilovat bez chyb a rovnice se zobrazí přesně tak, jak byly ve Wordu.

```bash
pdflatex Math.txt
```

Pokud obdržíte „Undefined control sequence“, ujistěte se, že jsou v preambuli zahrnuty potřebné LaTeX balíčky (např. `amsmath`), když vkládáte text do většího LaTeX dokumentu.

## Zpracování běžných variant

### Konverze více souborů ve složce

```csharp
string[] files = Directory.GetFiles(@"C:\MyDocs\", "*.docx");
foreach (var file in files)
{
    Document d = new Document(file);
    d.Save(Path.ChangeExtension(file, ".txt"), txtOptions);
}
Console.WriteLine("Batch conversion complete.");
```

### Práce s inline a display rovnicemi

Aspose.Words automaticky detekuje typ rovnice na základě jejího rozložení ve Wordu. Pokud potřebujete vynutit konkrétní styl, můžete výstup následně upravit:

```csharp
string txt = File.ReadAllText(@"C:\MyDocs\Math.txt");
txt = txt.Replace("$", "\\(").Replace("$", "\\)"); // forces inline math delimiters
File.WriteAllText(@"C:\MyDocs\Math_fixed.txt", txt);
```

### Export do jiných formátů

Pokud LaTeX není vaším cílem, jednoduše přepněte režim exportu:

```csharp
txtOptions.OfficeMathExportMode = OfficeMathExportMode.MathML; // for MathML
```

Nebo použijte `HtmlSaveOptions`, pokud dáváte přednost MathML vloženému v HTML.

## Kompletní funkční příklad

Níže je kompletní, připravený k spuštění program. Zkopírujte a vložte jej do `Program.cs` .NET konzolového projektu.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;

namespace WordToLatexTxt
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the source document
            Document doc = new Document(@"C:\MyDocs\input.docx");

            // 2️⃣ Set up save options to export Office Math as LaTeX
            TxtSaveOptions saveOptions = new TxtSaveOptions
            {
                OfficeMathExportMode = OfficeMathExportMode.LaTeX,
                PreserveTableLayout = true
            };

            // 3️⃣ Save as plain‑text with LaTeX equations
            string outputPath = @"C:\MyDocs\Math.txt";
            doc.Save(outputPath, saveOptions);

            Console.WriteLine($"✅ Saved document as txt at: {outputPath}");
            Console.WriteLine("Open the file to see LaTeX‑formatted equations.");
        }
    }
}
```

Spusťte program (`dotnet run`), otevřete `Math.txt` a uvidíte obsah Wordu s LaTeX rovnicemi zachovanými.

## Často kladené otázky

**Q: Funguje to i se staršími .doc soubory?**  
A: Ano—Aspose.Words může otevřít starší soubory `.doc`, ale složité rovnice mohou být uloženy jako obrázky. V takovém případě exportér použije zástupný komentář.

**Q: Co když rovnice obsahuje vlastní symboly?**  
A: Aspose.Words mapuje většinu symbolů Office Math na standardní LaTeX příkazy. Pro skutečně vlastní symboly možná budete muset ručně upravit vygenerovaný LaTeX.

**Q: Je výstup kódován v UTF‑8?**  
A: Ve výchozím nastavení `TxtSaveOptions` zapisuje UTF‑8, což je bezpečné pro většinu jazyků a symbolů.

## Závěr

Nyní víte, jak **save document as txt** a zároveň zachovat každou rovnici jako čistý LaTeX markup. Tento přístup vám umožní **convert Word to LaTeX** bez nástrojů třetích stran a škáluje od jednoho souboru po celé složky. Dále můžete zkoumat **convert word equations to LaTeX** pro hromadné zpracování, nebo se ponořit do **export word math latex** pro HTML nebo Markdown pipeline.

Neváhejte experimentovat—vyměňte `OfficeMathExportMode` za MathML, upravte zpracování zalomení řádků nebo integrujte tento úryvek do většího workflow generování dokumentů. Šťastné programování a ať se vaše rovnice vždy vykreslí perfektně!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}