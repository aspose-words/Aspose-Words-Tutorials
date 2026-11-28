---
category: general
date: 2026-08-23
description: Översätt sträng till spanska i C# med Aspose.Words AI Translator och
  Google‑leverantör. Följ steg‑för‑steg‑guiden för att snabbt översätta en sträng
  i C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: sv
lastmod: 2026-08-23
og_description: Översätt sträng till spanska i C# med Aspose.Words AI. Denna handledning
  visar hur du konfigurerar Google‑leverantören, översätter en sträng och visar resultatet.
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: Översätt sträng till spanska i C# – fullständigt kodexempel
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
title: Översätt sträng till spanska i C# med Aspose.Words AI
url: /sv/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Översätt sträng till spanska i C# med Aspose.Words AI

Om du behöver **översätta sträng till spanska** i en .NET‑applikation visar den här guiden exakt hur du gör det. Du får ett komplett, körbart exempel som skapar en översättare, anropar Google‑tjänsten och skriver ut den spanska texten.

Tutorialen täcker också **översätta sträng i C#** med Aspose.Words AI‑biblioteket, så att du kan integrera lokalisering direkt i din kodbas utan externa skript.

## Vad du behöver

- .NET 6.0 SDK eller senare (koden kompileras med .NET Core och .NET Framework)
- En aktiv Google Cloud Translation API‑nyckel
- NuGet‑paketet `Aspose.Words.AI` (installera med `dotnet add package Aspose.Words.AI`)
- En kodredigerare eller IDE såsom Visual Studio 2022

Dessa förutsättningar säkerställer att exemplet körs direkt.

## Översätt sträng till spanska med Aspose.Words AI

Detta avsnitt skapar `Translator`‑objektet konfigurerat för Google‑leverantören. Leverantören hanterar HTTP‑begäran till Googles översättnings‑endpoint.

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

**Varför detta fungerar:**  
- `Translator` abstraherar HTTP‑anropet och hanterar autentisering med den API‑nyckel du anger.  
- `TranslationProvider.Google` talar om för SDK att skicka begäran till Google Cloud Translation.  
- `Language.Spanish` väljer mål‑språkkoden (`es`).  
- Metoden `Translate` returnerar den översatta strängen, som du kan använda var som helst i din applikation.

## Ställ in Google‑översättningsleverantören

1. **Skaffa en API‑nyckel** från Google Cloud Console → APIs & Services → Credentials.  
2. **Aktivera Cloud Translation API** för ditt projekt.  
3. Förvara nyckeln säkert (miljövariabel, secret manager, osv.). Exemplet använder en literal för tydlighet, men produktionskod bör undvika att hårdkoda hemligheter.

## Översätt strängen i C# – steg‑för‑steg

| Steg | Åtgärd | Orsak |
|------|--------|--------|
| 1 | Instansiera `Translator` med `TranslationProvider.Google` | Kopplar SDK till Google‑tjänsten |
| 2 | Anropa `Translate(source, Language.Spanish)` | Skickar källtexten och mottar det spanska resultatet |
| 3 | Skriv ut resultatet med `Console.WriteLine` | Verifierar översättningen och demonstrerar användning |

När programmet körs skrivs följande ut:

```
¡Hola mundo!
```

> **Obs:** Det exakta resultatet kan variera något beroende på Googles översättningsmodell (t.ex. “Hola mundo” vs. “¡Hola mundo!”). Båda är giltiga spanska motsvarigheter.

## Kör och verifiera resultatet

1. Öppna en terminal i projektmappen.  
2. Kör `dotnet run`.  
3. Bekräfta att konsolen visar den spanska frasen.

Om konsolen visar ett fel som *“401 Unauthorized”*, dubbelkolla att API‑nyckeln är korrekt och att Cloud Translation API är aktiverat för projektet.

## Vanliga fallgropar och bästa praxis

- **API‑kvotgränser** – Google har begränsningar per faktureringskonto. Övervaka användningen i Cloud Console för att undvika oväntad begränsning.  
- **Nätverkslatens** – Översättningsanrop är fjärr‑HTTP‑förfrågningar. Överväg att cachea ofta översatta strängar för att minska latensen.  
- **Kodningsproblem** – SDK:n arbetar med UTF‑8‑strängar; se till att dina källfiler sparas med UTF‑8‑kodning för att bevara specialtecken.  
- **Felhantering** – Omge `Translate`‑anropet med en try‑catch‑block för att hantera `ApiException` och tillhandahålla reservtext.

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

## Utöka exemplet

- **Översätt till andra språk** – Byt ut `Language.Spanish` mot `Language.French`, `Language.German` osv.  
- **Batch‑översättning** – Anropa `Translate` i en loop för att bearbeta en lista med strängar.  
- **Integrera med UI** – Använd den översatta strängen i ASP.NET Core Razor‑sidor, Windows Forms eller WPF‑applikationer.

## Slutsats

Du vet nu hur du **översätter sträng till spanska** i C# med Aspose.Words AI och Google Translation‑tjänsten. Den kompletta lösningen täcker leverantörsinställning, översättningsanrop, felhantering och verifiering av resultatet.

Härifrån kan du experimentera med fler språk, cachea resultat för bättre prestanda och integrera översättaren i större lokalerings‑pipelines.

--- 

*Redo att lokalisera mer innehåll? Kolla in nästa tutorial om **translate string in C# with Azure Cognitive Services** för en alternativ molnleverantör.*


## Vad bör du lära dig härnäst?


Följande tutorials täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Ersätt med sträng](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [Ersätt med sträng](/words/english/net/find-and-replace-text/replace-with-string/)
- [Skapa Word‑dokument med Aspose.Words – Steg‑för‑steg‑guide](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}