---
category: general
date: 2026-04-10
description: Hur man använder LoadOptions i Aspose.Words för att fånga varningar om
  teckensnittssubstitution vid inläsning av dokument. Lär dig en steg‑för‑steg C#‑lösning
  med ett komplett kodexempel.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: sv
og_description: Hur man använder LoadOptions i Aspose.Words för att fånga varningar
  om teckensnittsbyte vid inläsning av dokument. Denna guide leder dig genom en komplett
  C#‑implementation.
og_title: Hur man använder LoadOptions i Aspose.Words – Komplett C#‑guide
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Hur man använder LoadOptions i Aspose.Words – Komplett C#‑guide
url: /sv/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man använder LoadOptions i Aspose.Words – Komplett C#‑guide

Att använda LoadOptions i Aspose.Words är ett vanligt hinder när du behöver exakt kontroll över dokumentladdning. I den här handledningen visar vi dig exakt **hur du använder LoadOptions** för att fånga varningar om teckensnittssubstitution och reagera på dem i C#.

Om du någonsin har öppnat en DOCX som refererade till ett saknat teckensnitt och undrat varför resultatet ser konstigt ut, är du på rätt plats. Vi går igenom hela processen, från att skapa en `LoadOptions`‑instans till att skriva ut varningsdetaljer i konsolen. I slutet har du ett färdigt kodexempel som du kan klistra in i vilket .NET‑projekt som helst.

## Vad du kommer att lära dig

- Varför `LoadOptions` är viktigt för pålitlig dokumentimport.  
- Hur du kopplar in en **WarningCallback** som specifikt övervakar **varningar om teckensnittssubstitution**.  
- Den exakta koden som behövs för att ladda en Word‑fil med dessa alternativ aktiverade.  
- Tips för att hantera kantfall, såsom dokument som innehåller flera saknade teckensnitt.  

Ingen extern dokumentation behövs – allt du behöver finns här.

## Förutsättningar

| Krav | Orsak |
|------|-------|
| .NET 6.0 eller senare | Tillhandahåller runtime för C# 10‑syntax som används i exemplen. |
| Aspose.Words för .NET (senaste versionen) | Biblioteket som levererar `LoadOptions` och varningsinfrastrukturen. |
| En DOCX‑fil som kan referera till teckensnitt du inte har installerade | För att se varnings‑callbacken i aktion. |
| Visual Studio 2022 (eller någon annan IDE du föredrar) | Gör felsökning och testning enkla. |

Om du redan har detta, bra – låt oss dyka in.

## Steg 1 – Skapa ett LoadOptions‑objekt och anslut WarningCallback

Det första du gör när du **hur man använder LoadOptions** är att instansiera det. Den avgörande delen är att tilldela en delegat till `WarningCallback`. Denna delegat triggas varje gång Aspose.Words stöter på en situation den vill informera dig om – främst ett saknat teckensnitt.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Varför detta är viktigt:** Utan callbacken byter Aspose.Words tyst ut saknade teckensnitt mot standardteckensnitt, och du kanske aldrig märker den visuella förändringen. Genom att registrera en `WarningCallback` får du en realtidslogg över varje substitution, vilket är avgörande för kvalitetssäkrade dokumentflöden.

## Steg 2 – Reagera endast på varningar om teckensnittssubstitution

Du kanske undrar om callbacken kommer att översvämma dig med irrelevanta varningar (som föråldrade funktioner). Svaret är *ja* – men vi kan filtrera dem. I kodsnutten ovan kontrollerar vi redan `args.WarningType == WarningType.FontSubstitution`. Den raden är **teckensnittssubstitutions‑varnings‑skyddet**, ett sekundärt nyckelord som håller utskriften fokuserad.

Om du någonsin behöver hantera andra varningstyper, utöka bara `if`‑blocket:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

Detta mönster visar hur flexibelt **warningcallback**‑mekanismen är, så att du kan skräddarsy svaren exakt för de scenarier du bryr dig om.

## Steg 3 – Ladda ditt dokument med de konfigurerade LoadOptions

Nu när lyssnaren är klar är sista steget att skicka `LoadOptions`‑instansen till `Document`‑konstruktorn. Detta är ögonblicket då **Aspose.Words LoadOptions‑exemplet** verkligen glänser.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**Vad du kommer att se:** Om DOCX‑filen refererar till ett teckensnitt som inte är installerat på maskinen, skriver konsolen ut en rad som:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

Denna utskrift bekräftar att du framgångsrikt **hur man använder LoadOptions** för att övervaka teckensnittsproblem.

## Fullt fungerande exempel (Klar‑för‑kopiering)

Nedan är det kompletta programmet som du kan kompilera och köra omedelbart. Det samlar alla tre stegen, lägger till ett par trevliga detaljer (som en vänlig banner) och demonstrerar felhantering.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### Förväntad utskrift

Att köra programmet på en maskin som saknar ett teckensnitt som refereras i `input.docx` ger något liknande:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

Om alla teckensnitt finns, ser du bara framgångsmeddelandena – inga varningsrader visas.

## Vanliga fallgropar & Pro‑tips

- **Fallgrop:** Glömmer att sätta `WarningCallback`. Koden laddar fortfarande, men du missar substitutionsdetaljerna.  
  **Pro‑tips:** Tilldela alltid callbacken omedelbart efter att du skapat `LoadOptions`; det är billigt och lönar sig senare.

- **Fallgrop:** Använder en relativ sökväg som pekar på fel mapp.  
  **Pro‑tips:** Använd `Path.Combine(Environment.CurrentDirectory, "input.docx")` för en mer robust filsökning.

- **Fallgrop:** Antar att varningen stoppar laddningen.  
  **Pro‑tips:** Varningar om teckensnittssubstitution är *informativa*; de avbryter inte laddningen. Om du behöver striktare validering, kasta ett undantag i callbacken när en substitution inträffar.

- **Fallgrop:** Kör på en server utan några installerade teckensnitt (t.ex. en minimal Docker‑image).  
  **Pro‑tips:** För‑installera de nödvändiga teckensnitten eller paketera dem med din app, och verifiera sedan med callbacken att inga substitutioner sker i produktion.

## När du ska använda LoadOptions vs. efter‑laddningsinspektion

Du kanske frågar, “Varför inte bara inspektera dokumentet efter att det har laddats?” Svaret ligger i prestanda och korrekthet. Genom att hantera varningar **under** laddningen fångar du problem tidigt – innan någon layoutberäkning eller PDF‑konvertering sker. Detta är särskilt värdefullt i batch‑processeringspipelines där varje extra steg kostar tid.

## Utöka exemplet: Spara en rapport över alla substituerade teckensnitt

Om du behöver ett permanent register (kanske för efterlevnad), modifiera callbacken så att den samlar meddelanden i en lista och skriver dem till en fil efter laddning:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

Nu har du både konsolfeedback och en hållbar logg.

## Relaterade ämnen du kanske vill utforska härnäst

- **Hur man bäddar in anpassade teckensnitt i Aspose.Words** – eliminerar substitution helt.  
- **Använda LoadOptions för att begränsa dokumentstorlek** – hjälper till att skydda mot skadligt stora filer.  
- **Konvertera Word till PDF med bevarad typografi** – passar bra ihop med varnings‑callback‑metoden.  

Var och en av dessa bygger på grunden du just etablerat med `LoadOptions`.

## Slutsats

Vi har gått igenom **hur man använder LoadOptions** i Aspose.Words från början till slut: skapa alternativen, anslut en `WarningCallback` som fokuserar på **varningar om teckensnittssubstitution**, och ladda ett dokument med förtroende. Det fullständiga exemplet körs direkt, och de extra tipsen hjälper dig undvika vanliga fallgropar.  

Känn dig fri att experimentera – byt ut callbacken mot andra varningstyper, logga till en databas, eller integrera logiken i en webbtjänst som validerar uppladdade Word‑filer. Mönstret är flexibelt, pålitligt och, viktigast av allt, ger dig insyn i den dolda teckensnittssubstitutionsprocessen som annars kan förstöra din dokumentrendering.

Lycka till med kodandet, och må dina dokument alltid renderas exakt som avsett! 

![Diagram som visar flödet för att använda LoadOptions med en varnings‑callback i Aspose.Words](https://example.com/images/loadoptions-flow.png "Diagram över hur man använder LoadOptions")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}