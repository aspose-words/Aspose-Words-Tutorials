---
category: general
date: 2026-03-22
description: Spara Word-dokument och upptäck saknade teckensnitt med Aspose.Words.
  Lär dig hur du spårar saknade teckensnitt och fångar teckensnittsfel i C#.
draft: false
keywords:
- save word document
- detect missing fonts
- track missing fonts
- capture font errors
language: sv
og_description: Spara Word-dokument och upptäck saknade teckensnitt i C#. Den här
  guiden visar hur du spårar saknade teckensnitt och fångar teckensnittsfel med en
  varningscallback.
og_title: Spara Word-dokument – upptäck saknade teckensnitt med Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Spara Word-dokument – Upptäck saknade teckensnitt med Aspose.Words
url: /sv/net/working-with-fonts/save-word-document-detect-missing-fonts-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Spara Word-dokument – Upptäck saknade teckensnitt med Aspose.Words

Har du någonsin behövt **save word document** men varit osäker på om några av teckensnitten inuti skulle överleva rundresan? Det händer oftare än du tror, särskilt när dokument färdas mellan maskiner med olika teckensnittsbibliotek. Den goda nyheten? Aspose.Words ger dig ett inbyggt sätt att **detect missing fonts** medan du **save word document**, så att du kan logga, varna eller till och med ersätta dem innan filen visas på en användares skärm.

I den här handledningen går vi igenom ett komplett, färdigt‑att‑köra exempel som inte bara sparar ett Word-dokument utan också **tracks missing fonts** och **captures font errors** med en anpassad varningshanterare. I slutet vet du exakt varför varnings‑callbacken är viktig, hur du kopplar den och hur konsolutdata ser ut när en ersättning sker. Ingen extra fluff—bara koden du kan klistra in i ett .NET‑projekt just nu.

> **Förutsättningar**  
> • .NET 6 (eller någon recent .NET Framework) installerad  
> • Visual Studio 2022 eller din favoriteditor  
> • En licensierad kopia av **Aspose.Words for .NET** (gratis provversion fungerar för testning)  

Om du har det, låt oss börja.

---

## Spara Word-dokument och upptäck saknade teckensnitt

Kärnidén är enkel: innan du anropar `Document.Save`, tilldela ett objekt som implementerar `IWarningCallback` till `Document.WarningCallback`. Aspose.Words kommer att anropa detta objekt för varje varning den stöter på, inklusive **font substitution**‑varningar som uppstår när källdokumentet refererar till ett teckensnitt som ditt system inte kan hitta.

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

**Vad du kommer att se:**  
Om `input.docx` refererar till ett teckensnitt som inte är installerat, skriver konsolen ut något i stil med:

```
Font substitution: Font "Comic Sans MS" was substituted with "Arial".
```

Den raden visar exakt vilket teckensnitt som saknades och vad Aspose.Words använde istället—perfekt för **captures font errors** innan du levererar filen.

## Spåra saknade teckensnitt med en varnings‑callback (Steg‑för‑steg)

### 1️⃣ Installera Aspose.Words

Öppna ditt projekts NuGet‑konsol och kör:

```bash
dotnet add package Aspose.Words
```

Det här hämtar den senaste stabila versionen (för närvarande 24.10). Att hålla biblioteket uppdaterat säkerställer att du får de senaste **detect missing fonts**‑funktionerna och buggfixarna.

### 2️⃣ Definiera varningshanteraren

Varför behöver vi en separat klass? Att implementera `IWarningCallback` låter dig centralisera all varningslogik på ett ställe. Du kan också logga till en fil, skicka telemetri eller kasta ett undantag om ett saknat teckensnitt är ett kritiskt fel för ditt arbetsflöde.

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

> **Proffstips:** Om du behöver **track missing fonts** över många dokument, lagra meddelandena i en `List<string>` i hanteraren och exponera dem senare för rapportering.

### 3️⃣ Läs in ditt källdokument

`Document`‑konstruktorn kan ta emot en filsökväg, en ström eller till och med råa bytes. I de flesta fall pekar du den på en `.docx` som du fått från en användare eller ett annat system.

```csharp
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Om filen är stor, överväg att använda `LoadOptions` för att aktivera lazy loading, vilket minskar minnesbelastningen.

### 4️⃣ Anslut callbacken

Tilldela instansen till `doc.WarningCallback`. Från och med nu kommer varje varning (inklusive teckensnittsersättningar) att gå genom din hanterare.

```csharp
doc.WarningCallback = new FontWarningHandler();
```

### 5️⃣ Spara dokumentet

Nu kan du säkert anropa `Save`. Varningshanteraren kör **synchronously** under spara‑operationen, så du ser utdata omedelbart.

```csharp
doc.Save("YOUR_DIRECTORY/output.docx");
```

Om du föredrar att spara till ett annat format (PDF, HTML, etc.) fungerar samma varningsmekanism—Aspose.Words kommer fortfarande att rapportera saknade teckensnitt innan konverteringen.

## Fånga teckensnittsfel – Vanliga kantfall

Även om det grundläggande flödet täcker de flesta scenarier, stöter verkliga projekt ofta på några problem. Nedan är några variationer du kan stöta på och hur du hanterar dem.

### Saknat teckensnitt i sidhuvud/sidfot

Sidhuvuden och sidfötter är separata noder, men varningssystemet behandlar dem på samma sätt som brödtext. Ingen extra kod behövs; callbacken kommer att triggas för dessa teckensnitt också. Se bara till att du läser in hela dokumentet (standardbeteendet gör detta).

### Flera ersättningar i ett dokument

Om ett dokument använder flera okända teckensnitt, kommer hanteraren att anropas en gång per ersättning. För att undvika att översvämma konsolen kan du deduplicera meddelanden:

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

### Gör om varningar till undantag

Ibland är ett saknat teckensnitt ett kritiskt fel. Kasta ett undantag inuti hanteraren för att avbryta sparandet:

```csharp
if (info.Type == WarningType.FontSubstitution)
{
    throw new InvalidOperationException($"Missing font detected: {info.Description}");
}
```

Kom ihåg att omsluta `doc.Save` i ett `try/catch`‑block för att hantera undantaget på ett smidigt sätt.

## Verifiera resultatet – Vad du kan förvänta dig

När sparandet är klart, öppna `output.docx` i Microsoft Word (eller någon kompatibel visare). Du bör se samma visuella layout som originalet, men de ersatta teckensnitten kommer att visas som den reserv du såg i konsolen. För att dubbelkolla kan du:

1. Öppna **File → Options → Advanced → Show document content → Use draft quality** – detta tvingar Word att visa eventuella dolda teckensnittsersättningar.
2. Använd Words **Replace Fonts**‑dialog (`Ctrl+Shift+F`) för att se vilka teckensnitt som faktiskt är inbäddade.

Om allt stämmer har du framgångsrikt **saved word document** medan du **detecting missing fonts** och **capturing font errors**. 🎉

## Fullt fungerande exempel (Klar att kopiera‑klistra in)

Nedan är hela programmet som du kan klistra in i ett nytt Console‑App‑projekt. Byt bara ut `YOUR_DIRECTORY` mot en faktisk sökväg på din maskin.

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

**Förväntad konsolutdata** (exempel):

```
Font substitution: Font "Times New Roman" was substituted with "Arial".
Document saved successfully.
```

Det är hela historien—inga dolda steg, inga externa dokument du måste jaga.

## Slutsats

Vi har just visat dig hur du **save word document** samtidigt som du aktivt **detect missing fonts**, **track missing fonts**, och **capture font errors** med Aspose.Words varnings‑callback. Genom att koppla en liten `IWarningCallback`‑implementation får du full insyn i teckensnittsersättningar vid sparning, vilket ger dig möjlighet att logga, ersätta eller avbryta vid behov.  

Redo för nästa utmaning? Prova att utöka hanteraren så att den skriver varningar till en strukturerad JSON‑logg, eller kombinera den med Aspose.PDF för att konvertera samma dokument samtidigt som du bevarar teckensnittsinformation. Du kan också utforska att bädda in saknade teckensnitt direkt i utdatafilen—Aspose.Words stödjer teckensnitts‑inbäddning via `LoadOptions.FontSettings`.  

Ge det ett försök, justera koden så den passar din pipeline, och låt oss veta hur det fungerar för dig. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}