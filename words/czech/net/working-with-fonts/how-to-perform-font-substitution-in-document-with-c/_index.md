---
category: general
date: 2026-10-13
description: Naučte se nahrazovat písma v dokumentu pomocí C#. Tento průvodce ukazuje,
  jak nastavit kódování big5, načíst DOCX a nahradit stará písma moderními.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- font substitution in document
- big5 encoding
- C# LoadOptions
- legacy font replacement
- document encoding for Chinese
- Docx loading C#
language: cs
lastmod: 2026-10-13
og_description: Nahrazení fontů v dokumentu je nezbytné při práci se staršími čínskými
  soubory. Postupujte podle tohoto krok‑za‑krokem návodu, jak načíst DOCX s kódováním
  big5 a nahradit staré fonty.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Nahrazení fontů v dokumentu pomocí C# – kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn font substitution in document using C#. This guide shows how
    to set big5 encoding, load a DOCX, and replace legacy fonts with modern ones.
  headline: How to perform font substitution in document with C#
  type: TechArticle
tags:
- C#
- Aspose.Words
- Unicode
- Chinese text
title: Jak provést nahrazení písma v dokumentu pomocí C#
url: /cs/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Náhrada fontu v dokumentu – kompletní C# tutoriál

Pokud potřebujete **font substitution in document** pro správné vykreslení starých čínských souborů, tento průvodce vám přesně ukáže, jak na to. Nastavením správného kódování textu a výměnou zastaralého fontu za moderní zajistíte, že finální DOCX bude zobrazen podle očekávání.

Zpracování dokumentů často selže, když zdroj používá staré kódování jako **big5** nebo odkazuje na font, který již v systému neexistuje. Tento tutoriál vás provede načtením DOCX s správným **big5 encoding**, aplikací **legacy font replacement** a vytvořením čistého výstupu, který funguje na jakémkoli počítači s Windows.

Naučíte se:

* Jak vytvořit objekt `LoadOptions` s **big5 encoding**.  
* Jak otevřít soubor DOCX pomocí **C# LoadOptions**.  
* Jak provést **font substitution in document** mapováním starého fontu na moderní ekvivalent.  
* Jak zacházet s okrajovými případy, jako jsou chybějící fonty a více fontových rodin.

Žádné externí nástroje nejsou potřeba kromě knihovny Aspose.Words pro .NET a kompletní kód lze zkopírovat do konzolového projektu a spustit okamžitě.

## Požadavky

* .NET 6.0 nebo novější (ukázka používá syntaxi .NET 6 console).  
* Aspose.Words pro .NET – instalace pomocí `dotnet add package Aspose.Words`.  
* Soubor DOCX uložený s **big5 encoding**, který odkazuje na starý font `MingLiU-ExtB`.  
* Základní znalost C# a Visual Studio nebo libovolného IDE dle vašeho výběru.

## Krok 1: Nastavení projektu a import jmenných prostorů

Vytvořte novou konzolovou aplikaci a přidejte požadované `using` direktivy. Tím zajistíte, že kód se zkompiluje bez dalších úprav.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The tutorial steps are called from here.
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // Steps 2‑4 are implemented inside this method.
        }
    }
}
```

> **Tip:** Udržujte metodu `Main` co nejstručnější; zlepšuje to čitelnost a usnadňuje sledování tutoriálu.

## Krok 2: Definování možností načtení s správným kódováním textu (big5 pro tradiční čínštinu)

Třída `LoadOptions` říká Aspose.Words, jak interpretovat surové bajty ve zdrojovém souboru. Použití **big5 encoding** je klíčové pro tradiční čínské znaky, které byly uloženy s touto starou stránkou kódu.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Proč je to důležité:** Pokud vynecháte nastavení kódování nebo použijete výchozí UTF‑8, mohou se znaky zobrazit jako poškozené symboly (mojibake). Specifikace `big5` zachová původní glyfy před jakoukoliv náhradou fontu.

## Krok 3: Načtení souboru DOCX s určeným kódováním

Předáte instanci `loadOptions` konstruktoru `Document`. Tím se soubor načte s respektem k **document encoding for Chinese**, kterou jste definovali dříve.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Pokud soubor nelze najít, program vyhodí `FileNotFoundException`. Ujistěte se, že cesta je správná a že aplikace má oprávnění ke čtení.

## Krok 4: Náhrada starého fontu moderním ekvivalentem

Mnoho starších čínských dokumentů odkazuje na `MingLiU-ExtB`, který nemusí být přítomen na novějších instalacích Windows. Mapování na `Microsoft JhengHei` (široce dostupný Unicode font) zajistí správné vykreslení.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Vysvětlení:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` registruje globální pravidlo náhrady. Pokaždé, když Aspose.Words narazí na `MingLiU-ExtB`, nahradí jej `Microsoft JhengHei`.  
* Volitelná smyčka vypíše mapování, což je užitečné při ladění ve velkých dokumentech s více fontovými rodinami.

## Krok 5: Uložení zpracovaného dokumentu

Po provedení náhrady zapíšete dokument do nového souboru. Výstup zobrazí čínský text pomocí moderního fontu, čímž odstraní varování o chybějících glyfech.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Otevřete výsledný soubor v Microsoft Word nebo libovolném prohlížeči DOCX; měli byste vidět tradiční čínské znaky čistě vykreslené pomocí `Microsoft JhengHei`.

## Řešení okrajových případů a běžných úskalí

| Situace | Doporučený postup |
|-----------|----------------------|
| **Zdrojový font není v dokumentu uveden** | Použijte `doc.FontInfos.Substitution.Add` s wildcard vzorem, např. `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Je potřeba nahradit více starých fontů** | Zavolejte `Add` pro každý pár, nebo načtěte slovník náhrad z konfiguračního souboru. |
| **Cílový font není na cílovém počítači dostupný** | Vyberte font, který je součástí Windows (např. `Arial Unicode MS`) nebo vložte font pomocí `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Chyby kódování přetrvávají** | Ověřte, že zdrojový soubor skutečně používá **big5**; můžete soubor prozkoumat hex editorem nebo použít `File.ReadAllBytes` a porovnat bajtové vzory. |

## Kompletní funkční příklad

Níže je kompletní, samostatný program. Zkopírujte jej do `Program.cs`, upravte cesty k souborům a spusťte.

```csharp
using System;
using System.Text;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace FontSubstitutionDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            PerformFontSubstitution();
        }

        static void PerformFontSubstitution()
        {
            // 1️⃣ Define big5 encoding for Traditional Chinese.
            LoadOptions loadOptions = new LoadOptions
            {
                Encoding = Encoding.GetEncoding("big5")
            };

            // 2️⃣ Load the DOCX that uses the legacy font.
            string inputPath = @"C:\Docs\big5_doc.docx";
            Document doc = new Document(inputPath, loadOptions);

            // 3️⃣ Substitute MingLiU-ExtB with Microsoft JhengHei.
            doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

            // 4️⃣ (Optional) Log substitution details for verification.
            foreach (FontInfo fontInfo in doc.FontInfos)
            {
                Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
            }

            // 5️⃣ Save the corrected document.
            string outputPath = @"C:\Docs\big5_doc_fixed.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"✅ Font substitution in document completed. Output saved to {outputPath}");
        }
    }
}
```

**Očekávaný výsledek:** Otevření `big5_doc_fixed.docx` zobrazí všechny tradiční čínské znaky správně vykreslené, bez varování o chybějících glyfech, protože `MingLiU-ExtB` byl nahrazen `Microsoft JhengHei`.

## Závěr

Nyní máte spolehlivý postup pro úlohy **font substitution in document** pomocí C#. Nastavením **big5 encoding**, načtením DOCX s `LoadOptions` a mapováním starých fontů na moderní ekvivalenty eliminujete problémy s vykreslováním, které trápí starší čínské soubory.  

Dále můžete:

* Rozšířit mapu náhrad o další staré fonty.  
* Automatizovat proces pro dávky dokumentů (procházet adresář).  
* Kombinovat náhradu fontu s dalšími transformacemi dokumentu, jako je vodoznak nebo konverze do PDF.

Neváhejte experimentovat s různými cílovými fonty nebo vložit vlastní fonty pro úplnou přenositelnost. Pokud narazíte na problémy, podívejte se znovu na tabulku okrajových případů výše nebo konzultujte dokumentaci Aspose.Words pro pokročilé zacházení s fonty.

Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční příklady kódu s krok‑za‑krokem vysvětlením, aby vám pomohl zvládnout další funkce API a prozkoumat alternativní implementační přístupy ve vašich projektech.

- [Povolení varování o náhradě fontů v Aspose.Words – Kompletní průvodce](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Zaznamenání varování o náhradě fontů – Kompletní Aspose.Words průvodce](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Načtení s kódováním ve Word dokumentu](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}