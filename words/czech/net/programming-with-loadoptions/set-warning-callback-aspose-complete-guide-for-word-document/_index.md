---
category: general
date: 2026-05-23
description: Nastavte varovný callback v Aspose, aby zachytil varování o substituci
  fontů v Aspose.Words. Seznamte se s LoadOptions, FontSettings a implementací IWarningCallback.
draft: false
keywords:
- set warning callback aspose
- aspose words loadoptions
- aspose fonts substitution
- iwarningcallback implementation
- aspose document loading
language: cs
og_description: Nastavte výstražný callback v Aspose pro sledování nahrazování fontů
  v Aspose.Words. Tento tutoriál ukazuje LoadOptions, FontSettings a implementaci
  výstražného handleru.
og_title: Nastavit varovný callback Aspose – krok za krokem
schemas:
- author: Aspose
  dateModified: '2026-05-23'
  description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  headline: set warning callback aspose – Complete Guide for Word Document Loading
  type: TechArticle
- description: set warning callback aspose to capture font substitution warnings in
    Aspose.Words. Learn LoadOptions, FontSettings, and IWarningCallback implementation.
  name: set warning callback aspose – Complete Guide for Word Document Loading
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works on .NET Framework 4.5+ as well). -
      A valid Aspose.Words for .NET license or a trial key. - Visual Studio, Rider,
      or any C# editor you prefer. - A sample DOCX (`fontTest.docx`) that references
      a missing font (optional but helpful).'
  - name: Expected console output
    text: 'If `fontTest.docx` references a font that isn’t installed, you’ll see something
      like:'
  - name: When to use a custom LoadOptions
    text: '- **Batch processing** of many files where you want a uniform logging strategy.
      - **Cloud services** that need to report missing fonts back to the caller. -
      **Testing pipelines** that verify documents adhere to a corporate font policy.'
  type: HowTo
tags:
- Aspose.Words
- C#
- FontSettings
title: Nastavení varovného zpětného volání Aspose – Kompletní průvodce načítáním Word
  dokumentu
url: /cs/net/programming-with-loadoptions/set-warning-callback-aspose-complete-guide-for-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# set warning callback aspose – Kompletní průvodce načítáním Word dokumentů

Už jste se někdy zamysleli, jak **set warning callback aspose**, abyste už nikdy nepromeškali upozornění na náhradu písma? Nejste v tom sami. Když DOCX odkazuje na písmo, které není nainstalováno, Aspose.Words jej tiše nahradí a bez správného callbacku můžete o změně vůbec nevědět.

V tomto tutoriálu projdeme kompletním, spustitelným příkladem, který přesně ukazuje, jak zachytit tato varování. Na konci pochopíte **Aspose.Words LoadOptions**, jak nakonfigurovat **FontSettings**, a proč je implementace **IWarningCallback** nejčistším způsobem, jak zůstat v obraze. Žádné zbytečnosti – jen kód, který můžete dnes vložit do .NET projektu.

## Co se naučíte

- Jak **set warning callback aspose** na instanci `LoadOptions`.  
- Role **Aspose.Words LoadOptions** při otevírání dokumentu.  
- Konfigurace **Aspose fonts substitution** pomocí `FontSettings`.  
- Psání vlastní implementace **IWarningCallback** pro logování problémů s písmy.  
- Bezpečné načítání dokumentu podle osvědčených postupů **Aspose document loading**.

### Předpoklady

- .NET 6.0 nebo novější (kód funguje také na .NET Framework 4.5+).  
- Platná licence Aspose.Words pro .NET nebo zkušební klíč.  
- Visual Studio, Rider nebo jakýkoli C# editor, který preferujete.  
- Vzorek DOCX (`fontTest.docx`) odkazující na chybějící písmo (volitelné, ale užitečné).

> **Tip:** Pokud nemáte DOCX s chybějícím písmem, stačí přejmenovat písmo ve stylu dokumentu a sledovat, jak se varování spustí.

---

## Jak nastavit set warning callback aspose pro načítání dokumentu

Níže je kompletní, samostatný program. Uložte jej jako `Program.cs`, obnovte NuGet balíčky a spusťte. Konzole vypíše každé varování o náhradě písma, které Aspose.Words vygeneruje během načítání souboru.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// ------------------------------------------------------------
// Step 1: Create a warning handler that implements IWarningCallback
// ------------------------------------------------------------
class FontSubstitutionWarningHandler : IWarningCallback
{
    // This method is called by Aspose.Words for each warning.
    public void Warning(WarningInfo info)
    {
        // We only care about font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // The Description property tells you which font was substituted.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// ------------------------------------------------------------
// Step 2: Prepare FontSettings (default works for most cases)
// ------------------------------------------------------------
FontSettings fontSettings = new FontSettings();
// You could add custom font folders here if you want to avoid substitution:
// fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// ------------------------------------------------------------
// Step 3: Build LoadOptions and attach our warning callback
// ------------------------------------------------------------
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings,
    WarningCallback = new FontSubstitutionWarningHandler()
};

// ------------------------------------------------------------
// Step 4: Load the document using the configured LoadOptions
// ------------------------------------------------------------
try
{
    // Replace the path with the location of your test document.
    Document doc = new Document("YOUR_DIRECTORY/fontTest.docx", loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

### Očekávaný výstup v konzoli

Pokud `fontTest.docx` odkazuje na písmo, které není nainstalováno, uvidíte něco jako:

```
Font substitution: Font 'Comic Sans MS' was substituted with 'Arial'.
Document loaded successfully.
```

Pokud jsou všechna písma přítomna, jediný řádek, který se vypíše, bude *Document loaded successfully* — žádná varování, žádný šum.

![příklad nastavení varovného callbacku aspose](image.png "příklad nastavení varovného callbacku aspose")

---

## Porozumění LoadOptions v Aspose.Words

`LoadOptions` je vstupní bránou ke všem úpravám, které můžete provést při **aspose document loading**. Umožňuje vám:

1. **Zadat vlastní `FontSettings`** — užitečné, když vaše aplikace dodává vlastní písma.  
2. **Připojit varovný callback** — přesně to, co jsme udělali pro zachycení náhrad písma.  
3. Ovládat detekci formátu dokumentu, práci s hesly a další.

Protože se `LoadOptions` předává konstruktoru `Document`, nastavení se použijí **jednou**, právě ve chvíli, kdy je soubor parsován. To je důvod, proč můžeme garantovat, že náš handler varování uvidí každou náhradu ještě před tím, než je dokument vůbec vytvořen v paměti.

### Kdy použít vlastní LoadOptions

- **Dávkové zpracování** mnoha souborů, kde chcete jednotnou strategii logování.  
- **Cloudové služby**, které potřebují hlásit chybějící písma zpět volajícímu.  
- **Testovací pipeline**, která ověřuje, že dokumenty splňují firemní politiku písma.

---

## Konfigurace FontSettings pro Aspose fonts substitution

Objekt `FontSettings` řídí, jak Aspose.Words vyhledává písma. Ve výchozím nastavení prohledává systémové složky s fonty a poté se vrací k vestavěným náhradám. Toto chování můžete doladit:

```csharp
FontSettings fontSettings = new FontSettings();

// Add a folder that contains your corporate fonts.
fontSettings.SetFontsFolder(@"C:\Corporate\Fonts", recursive: true);

// Optionally, map a missing font to a specific substitute.
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "MissingFont", new[] { "Arial", "Times New Roman" });
```

Tyto řádky jsou volitelné pro základní scénář “set warning callback aspose”, ale ukazují, jak můžete **snížit** počet varování o náhradě tím, že předem poskytnete správná písma.

---

## Implementace IWarningCallback pro varování o náhradě písma

Rozhraní `IWarningCallback` je malé — má jen jednu metodu `Warning`. Přesto vám dává **plnou kontrolu** nad tím, jak jsou varování zpracovávána:

- **Logovat do souboru** místo konzole.  
- **Sbírat varování** do seznamu pro pozdější analýzu.  
- **Vyvolat výjimky** pro kritická varování (např. když chybí povinné písmo).

Zde je rychlý příklad, který ukládá varování do `List<string>`:

```csharp
class CollectingWarningHandler : IWarningCallback
{
    public List<string> Messages { get; } = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
            Messages.Add(info.Description);
    }
}
```

Pak můžete po načtení dokumentu zkontrolovat `handler.Messages` a rozhodnout, zda zpracování přerušit.

---

## Načítání dokumentu s vlastním zpracováním varování (kompletní workflow)

Když spojíme vše dohromady, finální vzor, který pravděpodobně budete znovu používat, vypadá takto:

```csharp
// 1️⃣ Create the warning handler.
CollectingWarningHandler handler = new CollectingWarningHandler();

// 2️⃣ Set up FontSettings (add custom fonts if needed).
FontSettings fs = new FontSettings();
fs.SetFontsFolder(@"C:\MyApp\Fonts", true);

// 3️⃣ Build LoadOptions with both FontSettings and the handler.
LoadOptions opts = new LoadOptions
{
    FontSettings = fs,
    WarningCallback = handler
};

// 4️⃣ Load the document.
Document doc = new Document("input.docx", opts);

// 5️⃣ React to any font‑substitution warnings.
if (handler.Messages.Any())
{
    Console.WriteLine("The following fonts were substituted:");
    foreach (var msg in handler.Messages)
        Console.WriteLine("- " + msg);
}
else
{
    Console.WriteLine("No font issues detected.");
}
```

Tento úryvek demonstruje **aspose document loading** tok, který použijete v produkci: konfigurace, načtení a následná reakce. Vzor se dobře škáluje, ať už zpracováváte jeden soubor nebo procházíte tisíce.

---

## Často kladené otázky a okrajové případy

**Co když je dokument chráněn heslem?**  
Přidejte `Password = "secret"` do inicializátoru `LoadOptions`. Callback varování stále funguje po dešifrování souboru.

**Bude callback spouštět i pro jiné typy varování?**  
Ano — `WarningInfo.Type` může být `DocumentStructure`, `UnsupportedFileFormat` a další. V našem příkladu filtrujeme jen `FontSubstitution`, ale můžete logovat vše odstraněním podmínky `if`.

**Ovlivní to výkon?**  
Negativně jen nepatrně. Callback se volá jen při výskytu varování, což je mnohem méně často než běžné kroky parsování.

**Mohu zakázat náhradu písma úplně?**  
Můžete nastavit `fontSettings.SubstitutionSettings.DefaultFontSubstitution = false;`, ale pak Aspose.Words vyhodí výjimku místo automatické náhrady chybějících písem.

---

## Závěr

Nyní přesně víte, jak **set warning callback aspose** pro sledování událostí náhrady písma během zpracování **Aspose.Words LoadOptions**. Konfigurací `FontSettings`, implementací lehké `IWarningCallback` a načtením dokumentu s těmito možnostmi získáte úplnou přehlednost o všech změnách písem, které Aspose provádí za scénou.  

Odtud můžete:

- Rozšířit handler varování tak, aby zapisoval do centrálního logovacího servisu.  
- Kombinovat callback s vlastní strategií náhrady písem.  
- Použít tento vzor při tvorbě cloudového API, které validuje nahrané dokumenty klientů.

Vyzkoušejte to na svých vlastních DOCX souborech, upravte `FontSettings` a sledujte, jak konzole přesně říká, která písma byla nahrazena. Šťastné programování a ať se vaše dokumenty vždy vykreslují podle očekávání!

## Související tutoriály

- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}