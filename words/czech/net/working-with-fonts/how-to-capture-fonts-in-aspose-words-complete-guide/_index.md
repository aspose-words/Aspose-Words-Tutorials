---
category: general
date: 2026-01-05
description: Jak rychle zachytit písma a řešit chybějící písma pomocí Aspose.Words.
  Naučte se krok za krokem řešení s kompletním C# kódem.
draft: false
keywords:
- how to capture fonts
- handle missing fonts
- Aspose.Words warnings
- font substitution callback
- missing font detection
language: cs
og_description: Jak zachytit písma v Aspose.Words a řešit chybějící písma. Postupujte
  podle tohoto podrobného průvodce pro spolehlivou implementaci v C#.
og_title: Jak zachytit písma v Aspose.Words – kompletní návod
tags:
- Aspose.Words
- C#
- Document Processing
title: Jak zachytit písma v Aspose.Words – kompletní průvodce
url: /cs/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak zachytit písma v Aspose.Words – Kompletní průvodce

Už jste se někdy zamýšleli **jak zachytit písma** při načítání Word dokumentu pomocí Aspose.Words? Nejste v tom sami. Chybějící písma mohou způsobit jemné chyby v rozložení a bez řádného varování si to možná nikdy neuvědomíte, dokud finální PDF nevypadá špatně. V tomto tutoriálu vám přesně ukážeme, jak **zachytit písma** **a** zpracovat chybějící písma, aby váš výstup zůstal pixel‑perfektní.

Provedeme vás reálným scénářem, nastavíme zpětné volání varování a poskytneme vám připravený C# příklad. Na konci budete vědět, proč je to důležité, jak to implementovat a na co si dát pozor, když písma zmizí z vašeho prostředí.

## Co se naučíte

- Jak nakonfigurovat **LoadOptions** pro naslouchání varování souvisejících s písmy.  
- Úlohu **IWarningCallback** a **WarningInfo** v Aspose.Words.  
- Praktické tipy pro odstraňování problémů a logování chybějících písem.  
- Kompletní, samostatný ukázkový kód, který můžete vložit do Visual Studia a okamžitě spustit.

**Požadavky:** .NET 6+ (nebo .NET Framework 4.7.2+), Aspose.Words pro .NET nainstalovaný přes NuGet a základní znalost C#. Žádné další knihovny nejsou vyžadovány.

---

## Krok 1: Nastavte Load Options pro zachycení písem

Prvním, co potřebujeme, je instance **LoadOptions**. Tento objekt říká Aspose.Words, jak se má chovat při čtení dokumentu. Přiřazením vlastního **IWarningCallback** můžeme zachytit jakákoliv varování o substituci písem, která se během načítání objeví.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

// Prepare load options and attach a warning callback
LoadOptions loadOptions = new LoadOptions
{
    // The callback will be invoked for every warning Aspose.Words raises
    WarningCallback = new FontWarningCollector()
};
```

**Proč je to důležité:**  
Aspose.Words tiše nahrazuje chybějící písma výchozím, pokud ho nepožádáte o upozornění. Připojením zpětného volání **zachytíme informace o písmě** právě při načítání, což nám dává možnost logovat, nahradit nebo dokonce operaci přerušit.

> **Tip:** Uchovávejte `loadOptions` jako znovupoužitelnou proměnnou, pokud zpracováváte mnoho dokumentů najednou. Tím se vyhnete opakovanému vytváření stejného zpětného volání.

---

## Krok 2: Načtěte dokument s nakonfigurovanými možnostmi

Nyní, když je zpětné volání nastaveno, načteme dokument. Konstruktor **Document** přijímá cestu a **LoadOptions**, které jsme právě nakonfigurovali.

```csharp
// Replace with the actual path to your .docx file
string inputPath = @"C:\Docs\input.docx";

Document doc = new Document(inputPath, loadOptions);
```

Pokud chybí jakékoli písmo, Aspose.Words vyvolá varování, které zachytí náš `FontWarningCollector`. Samotný dokument se stále načte, ale budete mít jasný záznam o tom, která písma byla nahrazena.

---

## Krok 3: Implementujte FontWarningCollector – Zpracování chybějících písem

Jádro **jak zachytit písma** spočívá ve třídě `FontWarningCollector`. Implementuje `IWarningCallback` a filtruje pouze události `WarningType.FontSubstitution`.

```csharp
// Helper class that receives warning callbacks from Aspose.Words
class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We care exclusively about font substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // Log the warning – you could also write to a file or database
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Vysvětlení:**  
- `info.Type` nám říká kategorii varování. Kontrolou `FontSubstitution` **zpracujeme chybějící písma** bez zaplňování výstupu nesouvisejícími zprávami (např. zastaralé funkce).  
- `info.Description` obsahuje lidsky čitelnou zprávu, např. „Font 'Comic Sans MS' byl nahrazen 'Arial'.“ To jsou přesně data, která potřebujete k auditu svého fondu písem.

> **Pozor:** Pokud potřebujete zastavit zpracování, když chybí kritické písmo, vyhoďte výjimku uvnitř bloku `if` místo pouhého výpisu.

---

## Krok 4: Ověřte výstup – Co očekávat

Spusťte program z konzole nebo IDE. Pro každé chybějící písmo uvidíte řádek jako:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
```

Pokud jsou všechna písma přítomna, zpětné volání zůstane tiché a dokument se načte bez problémů. Nyní můžete bezpečně pokračovat v ukládání, konverzi nebo tisku dokumentu, s jistotou, že jste **zachytili informace o písmě**.

---

## Krok 5: Kompletní funkční příklad (vše dohromady)

Níže je kompletní program připravený ke zkopírování a vložení. Obsahuje using direktivy, implementaci zpětného volání a malou ukázku uložení načteného dokumentu jako PDF.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Loading;

namespace FontCaptureDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Configure load options with our warning collector
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningCollector()
            };

            // 2️⃣ Path to the source DOCX (adjust as needed)
            string inputPath = @"C:\Docs\input.docx";

            // 3️⃣ Load the document – any missing fonts trigger our callback
            Document doc = new Document(inputPath, loadOptions);

            // 4️⃣ Optional: Save as PDF to see the final result
            string outputPdf = @"C:\Docs\output.pdf";
            doc.Save(outputPdf);

            Console.WriteLine("Document processed successfully.");
        }
    }

    // 5️⃣ Our custom warning collector – handles missing fonts
    class FontWarningCollector : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                // You could log to a file, raise an event, or collect into a list
                Console.WriteLine($"Font substitution detected: {info.Description}");
            }
        }
    }
}
```

**Spuštění kódu:**  
1. Vytvořte nový konzolový projekt (`dotnet new console -n FontCaptureDemo`).  
2. Přidejte balíček Aspose.Words (`dotnet add package Aspose.Words`).  
3. Nahraďte vygenerovaný `Program.cs` výše uvedeným úryvkem.  
4. Umístěte DOCX, který úmyslně odkazuje na písmo, které nemáte (např. „Papyrus“).  
5. Spusťte (`dotnet run`). Sledujte konzoli pro zprávy o substituci a poté otevřete `output.pdf` a ověřte rozložení.

---

## Časté otázky a okrajové případy

### Co když potřebuji později seznam chybějících písem?

Uložte zprávy do `List<string>` uvnitř `FontWarningCollector` a zpřístupněte je přes vlastnost. Tímto způsobem můžete seznam zapsat do souboru protokolu po zpracování mnoha dokumentů.

### Funguje to s šifrovanými nebo chráněnými soubory heslem?

Ano, ale musíte také zadat heslo pomocí `LoadOptions.Password`. Zpětné volání varování funguje stejně po dešifrování dokumentu.

### Můžu nahradit chybějící písmo vlastním záložním písmem?

Určitě. V metodě `Warning` můžete zavolat `doc.FontSettings.SubstitutionSettings.FontSubstitutes.AddMissing("MissingFont", "MyFallback")`. Tím zajistíte deterministickou substituci.

### Ovlivní to výkon?

Zátěž je minimální – v podstatě jeden volání metody na každé varování. Ve šarži tisíců dokumentů je dopad zanedbatelný ve srovnání s I/O náklady na načítání každého souboru.

## Závěr

Probrali jsme **jak zachytit písma** v Aspose.Words, ukázali vám, jak **zpracovat chybějící písma** pomocí čistého zpětného volání varování, a poskytli kompletní spustitelný příklad. Začleněním tohoto vzoru do vašeho pipeline pro zpracování dokumentů už nikdy nebudete překvapeni tichými substitucemi písem.

Jste připraveni na další krok? Zkuste rozšířit kolektor tak, aby zapisoval JSON logy, integroval se s monitorovacím panelem, nebo automaticky vkládal chybějící písma do výstupního PDF. Možnosti jsou neomezené a nyní máte pevný základ.

Šťastné programování! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}