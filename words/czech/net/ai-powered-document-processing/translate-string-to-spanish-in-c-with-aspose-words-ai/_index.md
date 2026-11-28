---
category: general
date: 2026-08-23
description: Přeložte řetězec do španělštiny v C# pomocí Aspose.Words AI Translator
  a poskytovatele Google. Postupujte podle krok‑za‑krokem průvodce a rychle přeložte
  řetězec v C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: cs
lastmod: 2026-08-23
og_description: Překlad řetězce do španělštiny v C# s Aspose.Words AI. Tento tutoriál
  ukazuje, jak nastavit poskytovatele Google, přeložit řetězec a zobrazit výsledek.
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: Překlad řetězce do španělštiny v C# – kompletní příklad kódu
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  headline: Translate string to Spanish in C# with Aspose.Words AI
  type: TechArticle
- description: Translate string to Spanish in C# using Aspose.Words AI Translator
    and Google provider. Follow the step‑by‑step guide to translate string in C# quickly.
  name: Translate string to Spanish in C# with Aspose.Words AI
  steps:
  - name: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
    text: '**Obtain an API key** from the Google Cloud Console → APIs & Services →
      Credentials.'
  - name: '**Enable the Cloud Translation API** for your project.'
    text: '**Enable the Cloud Translation API** for your project.'
  - name: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
    text: Store the key securely (environment variable, secret manager, etc.). The
      example uses a literal for clarity, but production code should avoid hard‑coding
      secrets.
  - name: Open a terminal in the project folder.
    text: Open a terminal in the project folder.
  - name: Execute `dotnet run`.
    text: Execute `dotnet run`.
  - name: Confirm that the console displays the Spanish phrase.
    text: Confirm that the console displays the Spanish phrase.
  type: HowTo
tags:
- Aspose.Words
- C#
- Localization
title: Přeložit řetězec do španělštiny v C# s Aspose.Words AI
url: /cs/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Překlad řetězce do španělštiny v C# s Aspose.Words AI

Pokud potřebujete **překládat řetězec do španělštiny** v .NET aplikaci, tento průvodce vám přesně ukáže, jak na to. Uvidíte kompletní, spustitelný příklad, který vytvoří překladač, zavolá službu Google a vypíše španělský text.

Tutoriál také pokrývá **překlad řetězce v C#** pomocí knihovny Aspose.Words AI, takže můžete integrovat lokalizaci přímo do vašeho kódu bez externích skriptů.

## Co budete potřebovat

- .NET 6.0 SDK nebo novější (kód se kompiluje s .NET Core a .NET Framework)
- Aktivní klíč Google Cloud Translation API
- NuGet balíček `Aspose.Words.AI` (nainstalujte pomocí `dotnet add package Aspose.Words.AI`)
- Editor kódu nebo IDE, např. Visual Studio 2022

Tyto předpoklady zajišťují, že ukázka běží hned po vybalení.

## Překlad řetězce do španělštiny s Aspose.Words AI

Tato sekce vytvoří objekt `Translator` nakonfigurovaný pro poskytovatele Google. Poskytovatel zpracovává HTTP požadavek na překladové rozhraní Google.

```csharp
using System;
using Aspose.Words.AI;          // Namespace for Translator
using Aspose.Words.AI.Translator; // Contains TranslationProvider and Language enums

class Program
{
    static void Main()
    {
        // Step 1: Create a translator that uses Google as the provider
        var translator = new Translator(
            provider: TranslationProvider.Google,
            apiKey: "YOUR_GOOGLE_KEY");   // Replace with your real API key

        // Step 2: Translate the source text into Spanish
        string spanishText = translator.Translate(
            "Hello world",
            Language.Spanish);

        // Step 3: Use the translated text (display it in the console)
        Console.WriteLine(spanishText);
    }
}
```

**Proč to funguje:**  
- `Translator` abstrahuje HTTP volání a zajišťuje autentizaci pomocí dodaného API klíče.  
- `TranslationProvider.Google` říká SDK, aby směrovalo požadavek na Google Cloud Translation.  
- `Language.Spanish` vybírá cílový jazykový kód (`es`).  
- Metoda `Translate` vrací přeložený řetězec, který můžete použít kdekoliv ve své aplikaci.

## Nastavení poskytovatele Google Translation

1. **Získejte API klíč** z Google Cloud Console → APIs & Services → Credentials.  
2. **Povolte Cloud Translation API** pro váš projekt.  
3. Uložte klíč bezpečně (proměnná prostředí, secret manager, atd.). Příklad používá doslovnou hodnotu pro přehlednost, ale produkční kód by se měl vyhnout tvrdému kódování tajemství.

## Překlad řetězce v C# – krok za krokem

| Krok | Akce | Důvod |
|------|--------|--------|
| 1 | Vytvořte instanci `Translator` s `TranslationProvider.Google` | Připojí SDK ke službě Google |
| 2 | Zavolejte `Translate(source, Language.Spanish)` | Odesílá zdrojový text a získá španělský výsledek |
| 3 | Vypište výsledek pomocí `Console.WriteLine` | Ověří překlad a demonstruje použití |

Spuštěním programu se vypíše:

```
¡Hola mundo!
```

> **Poznámka:** Přesný výstup se může mírně lišit v závislosti na modelu překladu Google (např. „Hola mundo“ vs. „¡Hola mundo!“). Obě jsou platné španělské ekvivalenty.

## Spusťte a ověřte výstup

1. Otevřete terminál ve složce projektu.  
2. Spusťte `dotnet run`.  
3. Ověřte, že konzole zobrazí španělskou frázi.

Pokud konzole zobrazí chybu jako *„401 Unauthorized“*, zkontrolujte, že je API klíč správný a že je pro projekt povolen Cloud Translation API.

## Časté úskalí a osvědčené postupy

- **Limity kvóty API** – Google vynucuje limity požadavků na fakturační účet. Sledujte využití v Cloud Console, abyste se vyhnuli neočekávanému omezení.  
- **Síťová latence** – Překladové volání jsou vzdálené HTTP požadavky. Zvažte cachování často překládáných řetězců pro snížení latence.  
- **Problémy s kódováním** – SDK pracuje s UTF‑8 řetězci; ujistěte se, že vaše zdrojové soubory jsou uloženy v kódování UTF‑8, aby se zachovaly speciální znaky.  
- **Zpracování chyb** – Zabalte volání `Translate` do bloku try‑catch, abyste zachytili `ApiException` a poskytli náhradní text.

```csharp
try
{
    string spanishText = translator.Translate("Hello world", Language.Spanish);
    Console.WriteLine(spanishText);
}
catch (ApiException ex)
{
    Console.Error.WriteLine($"Translation failed: {ex.Message}");
    // Fallback to original text
    Console.WriteLine("Hello world");
}
```

## Rozšíření příkladu

- **Překlad do dalších jazyků** – Nahraďte `Language.Spanish` za `Language.French`, `Language.German` atd.  
- **Dávkový překlad** – Zavolejte `Translate` uvnitř smyčky pro zpracování seznamu řetězců.  
- **Integrace s UI** – Použijte přeložený řetězec v ASP.NET Core Razor stránkách, Windows Forms nebo WPF aplikacích.

## Závěr

Nyní víte, jak **překládat řetězec do španělštiny** v C# pomocí Aspose.Words AI a služby Google Translation. Kompletní řešení zahrnuje nastavení poskytovatele, volání překladu, zpracování chyb a ověření výstupu.

Odtud můžete experimentovat s dalšími jazyky, cachovat výsledky pro výkon a integrovat překladač do rozsáhlejších lokalizačních pipeline.

--- 

*Chcete lokalizovat další obsah? Podívejte se na další tutoriál o **překladu řetězce v C# s Azure Cognitive Services** pro alternativního poskytovatele cloudu.*

## Co byste se měli naučit dál?

Následující tutoriály pokrývají úzce související témata, která staví na technikách předvedených v tomto průvodci. Každý zdroj obsahuje kompletní funkční ukázky kódu s podrobnými vysvětleními, které vám pomohou zvládnout další funkce API a prozkoumat alternativní přístupy k implementaci ve vašich projektech.

- [Nahradit řetězcem](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [Nahradit řetězcem](/words/english/net/find-and-replace-text/replace-with-string/)
- [Vytvořit Word dokument s Aspose.Words – krok za krokem](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}