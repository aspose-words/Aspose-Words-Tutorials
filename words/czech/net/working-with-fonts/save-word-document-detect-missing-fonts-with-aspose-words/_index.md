---
category: general
date: 2026-03-22
description: Uložte dokument Word a detekujte chybějící písma pomocí Aspose.Words.
  Naučte se, jak sledovat chybějící písma a zachytit chyby písma v C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: cs
og_description: Uložte dokument Word a detekujte chybějící písma v C#. Tento průvodce
  ukazuje, jak sledovat chybějící písma a zachytit chyby písma pomocí varovného zpětného
  volání.
og_title: Uložení dokumentu Word – Detekce chybějících písem pomocí Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Uložení dokumentu Word – Detekce chybějících fontů pomocí Aspose.Words
url: /cs/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uložení Word dokumentu – Detekce chybějících fontů pomocí Aspose.Words

Už jste někdy potřebovali **uložit Word dokument**, ale nebyli jste si jisti, zda některé fonty uvnitř přežijí při přenosu? Stává se to častěji, než si myslíte, zejména když dokumenty putují mezi počítači s různými knihovnami fontů. Dobrá zpráva? Aspose.Words vám poskytuje vestavěný způsob, jak **detekovat chybějící fonty** během **ukládání Word dokumentu**, takže je můžete zaznamenat, varovat nebo dokonce nahradit, než se soubor zobrazí na obrazovce uživatele.

V tomto tutoriálu projdeme kompletním, připraveným příkladem, který nejen ukládá Word dokument, ale také **sleduje chybějící fonty** a **zachycuje chyby fontů** pomocí vlastního handleru varování. Na konci přesně pochopíte, proč je callback varování důležitý, jak jej připojit a jak vypadá výstup do konzole, když dojde k substituci. Žádné zbytečné okrasy—pouze kód, který můžete hned vložit do .NET projektu.

> **Požadavky**  
> • .NET 6 (nebo jakýkoli recentní .NET Framework) nainstalovaný  
> • Visual Studio 2022 nebo vaše oblíbené IDE  
> • Licencovaná kopie **Aspose.Words for .NET** (zdarma zkušební verze funguje pro testování)  

Pokud je máte, pojďme na to.

---

## Uložení Word dokumentu a detekce chybějících fontů

Základní myšlenka je jednoduchá: před voláním `Document.Save` přiřaďte objekt implementující `IWarningCallback` k `Document.WarningCallback`. Aspose.Words tento objekt vyvolá pro každé varování, na které narazí, včetně varování o **substituci fontu**, která nastane, když zdrojový dokument odkazuje na font, který váš systém nemůže najít.

```csharp
using Aspose.Words;
using Aspose.Words.Warning;

// Step 1: Create a warning handler that prints font substitution messages
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Only react to font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

// Step 2: Load a document that may contain missing fonts
Document document = new Document("YOUR_DIRECTORY/input.docx");

// Step 3: Register the warning handler with the document
document.WarningCallback = new FontWarningHandler();

// Step 4: Save the document; any font substitution warnings will be output to the console
document.Save("YOUR_DIRECTORY/output.docx");
```

**Co uvidíte:**  
Pokud `input.docx` odkazuje na font, který není nainstalován, konzole vypíše něco jako:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Tento řádek vám přesně říká, který font chyběl a co Aspose.Words použil místo něj—ideální pro **zachycení chyb fontů** před odesláním souboru.

## Sledování chybějících fontů pomocí callbacku varování (krok za krokem)

### 1️⃣ Instalace Aspose.Words

Otevřete NuGet konzoli vašeho projektu a spusťte:

```bash
dotnet add package Aspose.Words
```

Tím se stáhne nejnovější stabilní verze (aktuálně 24.10). Udržování knihovny aktuální zajišťuje, že získáte nejnovější funkce **detekce chybějících fontů** a opravy chyb.

### 2️⃣ Definice handleru varování

Proč potřebujeme samostatnou třídu? Implementace `IWarningCallback` vám umožní centralizovat veškerou logiku varování na jednom místě. Můžete také zapisovat do souboru, posílat telemetry nebo vyhodit výjimku, pokud je chybějící font pro váš workflow kritickou chybou.

```csharp
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only the warnings we care about
        if (info.Type == WarningType.FontSubstitution)
        {
            // Here we simply write to the console,
            // but you could replace this with any logging framework.
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

> **Tip:** Pokud potřebujete **sledovat chybějící fonty** napříč mnoha dokumenty, uložte zprávy do `List<string>` uvnitř handleru a později je zpřístupněte pro reportování.

### 3️⃣ Načtení zdrojového dokumentu

Konstruktor `Document` může přijmout cestu k souboru, stream nebo dokonce surové bajty. Ve většině případů na něj nasměrujete `.docx`, který jste obdrželi od uživatele nebo jiného systému.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Pokud je soubor velký, zvažte použití `LoadOptions` pro povolení lazy loadingu, což snižuje zatížení paměti.

### 4️⃣ Připojení callbacku

Přiřaďte instanci k `doc.WarningCallback`. Od tohoto okamžiku bude každé varování (včetně substitucí fontů) procházet vaším handlerem.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Uložení dokumentu

Nyní můžete bezpečně zavolat `Save`. Handler varování běží **synchronně** během operace ukládání, takže výstup uvidíte okamžitě.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Pokud raději ukládáte do jiného formátu (PDF, HTML, atd.), stejný mechanismus varování funguje—Aspose.Words i nadále nahlásí chybějící fonty před konverzí.

## Zachycení chyb fontů – Běžné okrajové případy

Zatímco základní tok pokrývá většinu scénářů, reálné projekty často narazí na několik problémů. Níže jsou některé varianty, na které můžete narazit, a jak je řešit.

### Chybějící font v záhlaví/pati

Záhlaví a patičky jsou samostatné uzly, ale systém varování je zachází stejně jako s tělem textu. Žádný extra kód není potřeba; callback se spustí i pro tyto fonty. Jen se ujistěte, že načítáte celý dokument (výchozí chování to dělá).

### Více substitucí v jednom dokumentu

Pokud dokument používá několik neznámých fontů, handler se zavolá jednou pro každou substituci. Pro zabránění zaplavení konzole můžete zprávy deduplikovat:

```csharp
class FontWarningHandler : IWarningCallback
{
    private readonly HashSet<string> _seen = new();

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution && _seen.Add(info.Description))
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}
```

### Převod varování na výjimky

Někdy je chybějící font kritický. Vyhoďte výjimku uvnitř handleru, aby se ukládání přerušilo:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Nezapomeňte obalit `doc.Save` do `try/catch` bloku, abyste výjimku ošetřili elegantně.

## Ověření výsledku – Co očekávat

Po dokončení ukládání otevřete `output.docx` v Microsoft Word (nebo jakémkoli kompatibilním prohlížeči). Měli byste vidět stejný vizuální rozvrh jako originál, ale substituované fonty se objeví jako záložní fonty, které jste viděli v konzoli. Pro dvojí kontrolu můžete:

1. Otevřete **File → Options → Advanced → Show document content → Use draft quality** – tím přinutíte Word odhalit jakékoli skryté substituce fontů.
2. Použijte dialog **Replace Fonts** ve Wordu (`Ctrl+Shift+F`) a zjistěte, které fonty jsou skutečně vložené.

Pokud vše souhlasí, úspěšně jste **uložili Word dokument** při **detekci chybějících fontů** a **zachycení chyb fontů**. 🎉

## Kompletní funkční příklad (připravený ke kopírování)

Níže je celý program, který můžete vložit do nového projektu Console App. Stačí nahradit `YOUR_DIRECTORY` skutečnou cestou ke složce na vašem počítači.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Warning;

namespace FontWarningDemo
{
    // Step 1: Create a warning handler that prints font substitution messages
    class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            // Only handle font‑substitution warnings
            if (info.Type == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substitution: {info.Description}");
            }
        }
    }

    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Load a document that may contain missing fonts
            Document document = new Document("YOUR_DIRECTORY/input.docx");

            // Step 3: Register the warning handler with the document
            document.WarningCallback = new FontWarningHandler();

            // Step 4: Save the document; any font substitution warnings will be output to the console
            document.Save("YOUR_DIRECTORY/output.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Očekávaný výstup do konzole** (příklad):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

To je celý příběh—žádné skryté kroky, žádné externí dokumenty, které byste museli hledat.

## Závěr

Právě jsme vám ukázali, jak **uložit Word dokument** a zároveň aktivně **detekovat chybějící fonty**, **sledovat chybějící fonty** a **zachytit chyby fontů** pomocí warning callbacku Aspose.Words. Připojením malé implementace `IWarningCallback` získáte úplnou přehlednost o substitucích fontů při ukládání, což vám dává možnost zaznamenat, nahradit nebo přerušit proces podle potřeby.  

Jste připraveni na další výzvu? Zkuste rozšířit handler tak, aby zapisoval varování do strukturovaného JSON logu, nebo jej zkombinovat s Aspose.PDF pro konverzi stejného dokumentu při zachování informací o fontech. Můžete také prozkoumat vkládání chybějících fontů přímo do výstupního souboru—Aspose.Words podporuje vkládání fontů pomocí `LoadOptions.FontSettings`.  

Vyzkoušejte to, upravte kód podle svého pipeline a dejte nám vědět, jak to funguje u vás. Šťastné programování!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}