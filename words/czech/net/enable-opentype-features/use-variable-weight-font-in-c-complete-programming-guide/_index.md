---
category: general
date: 2026-06-02
description: Naučte se, jak v C# používat variabilní váhu písma a programově nastavit
  váhu písma při změně kódu roztažení písma pro dynamickou typografii.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: cs
og_description: Použijte variabilní font v C# k programovému nastavení váhy písma
  a změně kódu roztažení, což umožňuje dynamickou typografii ve vašich dokumentech.
og_title: Použití písma s proměnnou tloušťkou v C# – Kompletní průvodce
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Použití variabilního fontu s proměnnou tloušťkou v C# – Kompletní programovací
  průvodce
url: /cs/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití proměnného tloušťky písma v C# – Kompletní programovací průvodce

Chtěli jste někdy **použít proměnnou tloušťku písma** v .NET projektu, ale nejste si jisti, jak nechat váhu a roztažení reagovat na vstup uživatele? Nejste v tom sami. V mnoha UI nebo reportovacích scénářích chcete, aby se text přizpůsobil – třeba lehký nadpis, který se po najetí kurzorem ztuční, nebo odstavec, který se pro zdůraznění rozšíří. Dobrá zpráva je, že s Aspose.Words můžete **nastavit váhu písma programově** a dokonce **změnit kód roztažení písma** za běhu.

V tomto tutoriálu projdeme praktickým příkladem, který přesně ukazuje, jak načíst proměnný font, použít vlastní váhu a upravit nastavení roztažení – vše s přehledným C# kódem, který můžete zkopírovat a vložit. Na konci budete mít spustitelnou konzolovou aplikaci, která vytvoří PDF ukazující efekt.

---

## Co budete potřebovat

- **Aspose.Words for .NET** (v23.12 nebo novější). Knihovna obsahuje plnou podporu pro proměnné tloušťky fontů.
- Složku obsahující alespoň jeden soubor s proměnnou tloušťkou písma, např. *RobotoFlex‑Variable.ttf*. Můžete jej stáhnout z Google Fonts.
- .NET 6 SDK (nebo jakákoli aktuální verze .NET) a IDE dle vašeho výběru.
- Základní znalost C# – nic složitého, jen pár řádků kódu.

To je vše. Žádné další NuGet balíčky kromě Aspose.Words a žádné nejasné konfigurační soubory.

![Příklad použití proměnné tloušťky písma](https://example.com/variable-weight-sample.png "Ukázka použití proměnné tloušťky písma")

*Alt text: snímek obrazovky ukazující použití proměnné tloušťky písma v generovaném PDF dokumentu.*

## Krok 1: Nastavte FontSettings a ukazujte na složku s fonty  

Nejprve—Aspose.Words potřebuje vědět, kde se vaše proměnné fonty nacházejí. Uděláte to vytvořením objektu `FontSettings` a připojením `FolderFontSource`. Příznak `true` říká enginu, aby prohledával také podadresáře, což je užitečné, pokud máte více rodin fontů pohromadě.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Proč je to důležité:** Bez registrace složky se Aspose.Words vrátí k systémovým fontům a ignoruje data o proměnné tloušťce vložená ve vašem vlastním souboru fontu. Tento krok je základem pro vše, co následuje.

## Krok 2: Připojte FontSettings k dokumentu  

Nyní vytvoříme nový `Document` (nebo načteme existující) a řekneme mu, aby používal `FontSettings`, které jsme právě připravili. Toto propojení umožňuje, aby data o proměnné tloušťce byla dostupná každému `Run`, který později přidáme.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Pokud již máte šablonu – například soubor Word s místodržci – můžete nahradit `new Document()` za `new Document("Template.docx")`. Stejné `FontSettings` se použijí.

## Krok 3: Přidejte Run textu, který použije proměnný font  

**Run** je nejmenší jednotka formátování textu v Aspose.Words. Vytvoříme jej, vložíme do nového odstavce a později změníme jeho atributy písma.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

V tomto okamžiku se text vykreslí pomocí výchozího fontu (obvykle Times New Roman). Magie nastane, jakmile přiřadíme rodinu s proměnnou tloušťkou.

## Krok 4: Vyberte rodinu proměnného fontu  

Tady skutečně **používáme proměnnou tloušťku písma**. Nastavte `Font.Name` na přesný název rodiny definovaný uvnitř souboru proměnného fontu. Pro Roboto Flex je to `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Pokud si nejste jisti názvem rodiny, otevřete soubor `.ttf` ve fontovém prohlížeči nebo použijte metodu `fontSettings.GetFonts()`, která vypíše dostupné rodiny.

## Krok 5: Nastavte váhu a roztažení písma programově  

Nyní jádro tutoriálu: **nastavujeme váhu písma programově** a **měníme kód roztažení písma**. Obě vlastnosti přijímají celočíselné hodnoty, které odpovídají specifikaci OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Vyberte libovolnou hodnotu, kterou proměnný font podporuje.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Výchozí je 100 (Normal).

> **Tip:** Ne každý proměnný font poskytuje celý rozsah. Pokud nastavíte hodnotu, která není podporována, engine ji omezí na nejbližší dostupnou váhu nebo roztažení.

## Krok 6: Uložte dokument a ověřte výsledek  

Nakonec zapíšete dokument do PDF (nebo DOCX) a otevřete jej, abyste viděli efekt. PDF je skvělý formát pro vizuální ověření, protože vykreslování je konzistentní napříč platformami.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Když otevřete *VariableWeightDemo.pdf*, měli byste vidět frázi „Variable‑weight text demo“ vykreslenou v lehké, mírně rozšířené verzi Roboto Flex. Změňte `FontWeight` na `700` a `FontStretch` na `80` a spusťte znovu – sledujte, jak text ztuční a zkoncentruje se.

## Časté otázky a okrajové případy  

### Co když se font vůbec neobjeví?  

- **Chybějící FontSettings**: Zkontrolujte, že `doc.FontSettings = fontSettings;` je provedeno **před** přidáním jakéhokoli textu.
- **Nesprávný název rodiny**: Použijte `fontSettings.GetFonts()` k výpisu všech nalezených rodin; zkopírujte přesný řetězec.
- **Nesprávná váha/roztažení**: Některé proměnné fonty podporují jen podmnožinu rozsahu 100‑900. Použijte `run.Font.FontWeight = 400;` jako bezpečnou náhradní hodnotu.

### Můžu změnit váhu po uložení dokumentu?  

Ano. Objekt `Run` je měnitelný, takže můžete upravit `FontWeight` nebo `FontStretch` kdykoli před finálním `Save`. Pokud potřebujete váhy přepínat dynamicky (např. na základě interakce uživatele), zvažte generování samostatných runů pro každý stav.

### Funguje to s výstupem DOCX?  

Rozhodně. Metadata o proměnné tloušťce jsou uložena v podkladovém OpenXML a moderní verze Wordu je dokážou interpretovat. Starší verze Wordu však mohou nastavení roztažení ignorovat.

## Kompletní funkční příklad  

Níže je kompletní konzolový program, který můžete okamžitě zkompilovat a spustit. Obsahuje všechny potřebné `using` direktivy, ošetření chyb a komentáře.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Očekávaný výstup:** Konzole vypíše cestu uložení a vygenerované PDF zobrazí text v lehkém, rozšířeném stylu – přesně tak, jak jsme nakonfigurovali.

## Shrnutí  

Přehledně jsme si prošli, jak **použít proměnnou tloušťku písma** v C# s Aspose.Words, ukázali, jak **nastavit váhu písma programově**, a představili přesný **kód pro změnu roztažení písma**, který rozšiřuje nebo zužuje glyfy. Kroky jsou jednoduché: nakonfigurujte `FontSettings`, připojte je k `Document`, vytvořte `Run`, vyberte rodinu s proměnnou tloušťkou a nakonec upravte `FontWeight` a `FontStretch`.

## Co dál?  

- **Dynamická integrace UI**: Připojte stejnou logiku do aplikace WinForms nebo WPF, aby uživatelé mohli vybírat váhu/roztažení pomocí posuvníků.
- **Více runů**: Kombinujte několik runů s různými váhami ve stejném odstavci pro bohaté typografické hierarchie.
- **Pokročilé osy**: Některé proměnné fonty nabízejí další osy (např. sklon, optická velikost). Použijte `run.Font.FontStyle` nebo prozkoumejte `FontVariationSettings` pro ještě jemnější kontrolu.
- **Tipy pro výkon**: Kešujte instanci `FontSettings` při zpracování mnoha dokumentů, abyste se vyhnuli opakovanému skenování složek.

Klidně experimentujte – vyměňte *Roboto Flex* za *Inter Variable* nebo jakýkoli jiný OpenType proměnný font a sledujte, jak vaše dokumenty získají novou úroveň vizuální flexibility. Šťastné programování!

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Použít písmo z cílového počítače](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Použít písmo z cílového počítače](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Použít písmo z cílového počítače](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}