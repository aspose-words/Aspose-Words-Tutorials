---
category: general
date: 2026-08-23
description: Vertaal een string naar het Spaans in C# met behulp van Aspose.Words
  AI Translator en de Google-provider. Volg de stapsgewijze handleiding om snel een
  string in C# te vertalen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- translate string to spanish
- translate string in c#
language: nl
lastmod: 2026-08-23
og_description: Vertaal string naar Spaans in C# met Aspose.Words AI. Deze tutorial
  laat zien hoe je de Google-provider instelt, een string vertaalt en het resultaat
  weergeeft.
og_image_alt: Console screenshot showing translate string to spanish output in a C#
  application
og_title: String vertalen naar Spaans in C# – volledig codevoorbeeld
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
title: Vertaal string naar Spaans in C# met Aspose.Words AI
url: /nl/net/ai-powered-document-processing/translate-string-to-spanish-in-c-with-aspose-words-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vertaal string naar Spaans in C# met Aspose.Words AI

Als je een **string naar Spaans moet vertalen** in een .NET‑applicatie, laat deze gids precies zien hoe je dat doet. Je ziet een compleet, uitvoerbaar voorbeeld dat een vertaler maakt, de Google‑service aanroept en de Spaanse tekst afdrukt.

De tutorial behandelt ook **string vertalen in C#** met behulp van de Aspose.Words AI‑bibliotheek, zodat je lokalisatie direct in je codebase kunt integreren zonder externe scripts.

## Wat je nodig hebt

- .NET 6.0 SDK of later (de code compileert met .NET Core en .NET Framework)
- Een actieve Google Cloud Translation API‑sleutel
- Het NuGet‑pakket `Aspose.Words.AI` (installeren met `dotnet add package Aspose.Words.AI`)
- Een code‑editor of IDE zoals Visual Studio 2022

Deze vereisten zorgen ervoor dat het voorbeeld direct werkt.

## String vertalen naar Spaans met Aspose.Words AI

Deze sectie maakt het `Translator`‑object aan, geconfigureerd voor de Google‑provider. De provider behandelt het HTTP‑verzoek naar het vertaal‑endpoint van Google.

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

**Waarom dit werkt:**  
- `Translator` abstracteert de HTTP‑aanroep en behandelt authenticatie met de API‑sleutel die je opgeeft.  
- `TranslationProvider.Google` vertelt de SDK om het verzoek naar Google Cloud Translation te sturen.  
- `Language.Spanish` selecteert de doeltaalcode (`es`).  
- De `Translate`‑methode retourneert de vertaalde string, die je overal in je applicatie kunt gebruiken.

## De Google‑vertalerprovider instellen

1. **Verkrijg een API‑sleutel** via de Google Cloud Console → APIs & Services → Credentials.  
2. **Schakel de Cloud Translation API** in voor je project.  
3. Sla de sleutel veilig op (omgevingsvariabele, secret manager, enz.). Het voorbeeld gebruikt een letterlijke waarde voor duidelijkheid, maar productcode moet hard‑coded geheimen vermijden.

## De string vertalen in C# – stap‑voor‑stap

| Stap | Actie | Reden |
|------|--------|--------|
| 1 | Instantieer `Translator` met `TranslationProvider.Google` | Verbindt de SDK met de Google‑service |
| 2 | Roep `Translate(source, Language.Spanish)` aan | Verstuurt de brontekst en ontvangt het Spaanse resultaat |
| 3 | Geef het resultaat weer met `Console.WriteLine` | Verifieert de vertaling en demonstreert het gebruik |

Het uitvoeren van het programma geeft het volgende weer:

```
¡Hola mundo!
```

> **Opmerking:** De exacte output kan enigszins variëren afhankelijk van het vertaalmodel van Google (bijv. “Hola mundo” vs. “¡Hola mundo!”). Beide zijn geldige Spaanse equivalenten.

## Voer uit en verifieer de output

1. Open een terminal in de projectmap.  
2. Voer `dotnet run` uit.  
3. Controleer of de console de Spaanse zin weergeeft.

Als de console een fout toont zoals *“401 Unauthorized”*, controleer dan of de API‑sleutel correct is en of de Cloud Translation API is ingeschakeld voor het project.

## Veelvoorkomende valkuilen en best practices

- **API‑quotalimieten** – Google handhaaft verzoeklimieten per factureringsaccount. Houd het gebruik in de Cloud Console in de gaten om onverwachte throttling te voorkomen.  
- **Netwerk‑latentie** – Vertaal‑aanroepen zijn externe HTTP‑verzoeken. Overweeg om vaak vertaalde strings te cachen om latentie te verminderen.  
- **Codering‑problemen** – De SDK werkt met UTF‑8‑strings; zorg ervoor dat je bronbestanden zijn opgeslagen met UTF‑8‑codering om speciale tekens te behouden.  
- **Foutafhandeling** – Plaats de `Translate`‑aanroep in een try‑catch‑blok om `ApiException` af te handelen en een fallback‑tekst te bieden.

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

## Voorbeeld uitbreiden

- **Vertalen naar andere talen** – Vervang `Language.Spanish` door `Language.French`, `Language.German`, enz.  
- **Batch‑vertaling** – Roep `Translate` aan binnen een lus om een lijst strings te verwerken.  
- **Integreren met UI** – Gebruik de vertaalde string in ASP.NET Core Razor‑pagina's, Windows Forms of WPF‑applicaties.

## Conclusie

Je weet nu hoe je **string naar Spaans kunt vertalen** in C# met Aspose.Words AI en de Google Translation‑service. De volledige oplossing omvat het instellen van de provider, de vertaal‑aanroep, foutafhandeling en verificatie van de output.

Vanaf hier kun je experimenteren met extra talen, resultaten cachen voor prestaties, en de vertaler integreren in grotere lokalisatie‑pijplijnen.

--- 

*Klaar om meer inhoud te lokaliseren? Bekijk de volgende tutorial over **string vertalen in C# met Azure Cognitive Services** voor een alternatieve cloudprovider.*

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Vervangen met string](/words/spanish/net/find-and-replace-text/replace-with-string/)
- [Vervangen met string](/words/english/net/find-and-replace-text/replace-with-string/)
- [Word‑document maken met Aspose.Words – Stapsgewijze gids](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}