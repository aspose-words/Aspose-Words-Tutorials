---
category: general
date: 2026-10-13
description: Lär dig teckensnittsbyte i dokument med C#. Den här guiden visar hur
  du ställer in big5‑kodning, laddar en DOCX och ersätter äldre teckensnitt med moderna.
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
language: sv
lastmod: 2026-10-13
og_description: Teckensnittsbyte i dokumentet är avgörande när du arbetar med äldre
  kinesiska filer. Följ den här steg‑för‑steg‑handledningen för att ladda ett DOCX
  med big5‑kodning och ersätta gamla teckensnitt.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Teckensnittssubstitution i dokument med C# – komplett guide
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
title: Hur man utför teckensnittssubstitution i ett dokument med C#
url: /sv/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Teckensnittsbyte i dokument – komplett C#-handledning

Om du behöver **font substitution in document** för att rendera äldre kinesiska filer korrekt, visar den här guiden exakt hur du gör det. Genom att konfigurera rätt textkodning och byta ut ett föråldrat teckensnitt mot ett modernt, garanterar du att den slutgiltiga DOCX-filen visas som avsett.

Dokumentbehandling går ofta sönder när källan använder en gammal kodning som **big5** eller refererar till ett teckensnitt som inte längre finns på systemet. Denna handledning guidar dig genom att läsa in en DOCX med korrekt **big5 encoding**, tillämpa **legacy font replacement**, och producera en ren utdata som fungerar på vilken Windows‑maskin som helst.

Du kommer att lära dig:

* Hur du skapar ett `LoadOptions`‑objekt med **big5 encoding**.  
* Hur du öppnar en DOCX‑fil med **C# LoadOptions**.  
* Hur du utför **font substitution in document** genom att mappa ett gammalt teckensnitt till ett modernt motsvarande.  
* Hantering av edge‑case för saknade teckensnitt och flera teckensnittsfamiljer.

Inga externa verktyg krävs utöver Aspose.Words för .NET‑biblioteket, och den kompletta koden kan kopieras in i ett konsolprojekt och köras omedelbart.

## Förutsättningar

* .NET 6.0 eller senare (exemplet använder .NET 6‑konsolsyntax).  
* Aspose.Words för .NET – installera via `dotnet add package Aspose.Words`.  
* En DOCX‑fil sparad med **big5 encoding** som refererar till det äldre teckensnittet `MingLiU-ExtB`.  
* Grundläggande kunskap om C# och Visual Studio eller någon annan IDE du föredrar.

## Steg 1: Ställ in projektet och importera namnrymder

Skapa en ny konsolapplikation och lägg till de nödvändiga `using`‑direktiven. Detta säkerställer att koden kompileras utan extra ändringar.

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

> **Pro tip:** Håll `Main`‑metoden minimal; det förbättrar läsbarheten och gör handledningen enklare att följa.

## Steg 2: Definiera load‑alternativ med korrekt textkodning (big5 för traditionell kinesiska)

`LoadOptions`‑klassen talar om för Aspose.Words hur de råa bytena i källfilen ska tolkas. Att använda **big5 encoding** är kritiskt för traditionella kinesiska tecken som sparades med den äldre kodsidan.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Varför detta är viktigt:** Om du utelämnar kodningen eller använder standard‑UTF‑8 kan tecken visas som förvrängda symboler (mojibake). Att specificera `big5` bevarar de ursprungliga glyferna innan något teckensnittsbyte sker.

## Steg 3: Läs in DOCX‑filen med den angivna kodningen

Skicka `loadOptions`‑instansen till `Document`‑konstruktorn. Detta läser in filen samtidigt som den respekterar den **document encoding for Chinese** du definierade tidigare.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Om filen inte kan hittas kastar programmet ett `FileNotFoundException`. Säkerställ att sökvägen är korrekt och att applikationen har läsbehörighet.

## Steg 4: Ersätt ett äldre teckensnitt med ett modernt motsvarande

Många äldre kinesiska dokument refererar till `MingLiU-ExtB`, vilket kanske inte finns på nyare Windows‑installationer. Att mappa det till `Microsoft JhengHei` (ett allmänt tillgängligt Unicode‑teckensnitt) säkerställer korrekt rendering.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Förklaring:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` registrerar en global ersättningsregel. Varje gång Aspose.Words stöter på `MingLiU-ExtB` byter det ut det mot `Microsoft JhengHei`.  
* Den valfria loopen skriver ut mappningen, vilket är användbart för felsökning i stora dokument med flera teckensnittsfamiljer.

## Steg 5: Spara det bearbetade dokumentet

Efter ersättningen skriv dokumentet till en ny fil. Utdata kommer att visa den kinesiska texten med det moderna teckensnittet, vilket eliminerar varningar om saknade glyfer.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Öppna den resulterande filen i Microsoft Word eller någon DOCX‑visare; du bör se de traditionella kinesiska tecknen renderade rent med `Microsoft JhengHei`.

## Hantering av edge cases och vanliga fallgropar

| Situation | Rekommenderad åtgärd |
|-----------|----------------------|
| **Källteckensnittet finns inte listat i dokumentet** | Använd `doc.FontInfos.Substitution.Add` med ett wildcard‑mönster, t.ex. `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Flera äldre teckensnitt behöver ersättas** | Anropa `Add` för varje par, eller ladda en ersättningsordbok från en konfigurationsfil. |
| **Måtteckensnittet är inte tillgängligt på målmaskinen** | Välj ett teckensnitt som levereras med Windows (t.ex. `Arial Unicode MS`) eller bädda in teckensnittet med `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Kodningsfel visas fortfarande** | Verifiera att källfilen verkligen använder **big5**; du kan inspektera filen med en hex‑editor eller använda `File.ReadAllBytes` och jämföra byte‑mönster. |

## Fullt fungerande exempel

Nedan är det kompletta, fristående programmet. Kopiera det till `Program.cs`, justera filsökvägarna och kör det.

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

**Förväntat resultat:** När du öppnar `big5_doc_fixed.docx` visas alla traditionella kinesiska tecken korrekt renderade, utan varningar om saknade glyfer, eftersom `MingLiU-ExtB` har ersatts av `Microsoft JhengHei`.

## Slutsats

Du har nu en pålitlig metod för **font substitution in document**‑uppgifter med C#. Genom att konfigurera **big5 encoding**, läsa in DOCX‑filen med `LoadOptions` och mappa äldre teckensnitt till moderna motsvarigheter, eliminerar du renderingsproblem som drabbar äldre kinesiska filer.

Från här kan du:

* Utöka ersättningsmappen för att täcka ytterligare äldre teckensnitt.  
* Automatisera processen för batchar av dokument (loopa över en katalog).  
* Kombinera teckensnittsbyte med andra dokumenttransformationer såsom vattenmärkning eller PDF‑konvertering.

Känn dig fri att experimentera med olika målteckensnitt eller bädda in anpassade teckensnitt för full portabilitet. Om du stöter på problem, gå tillbaka till tabellen med edge‑cases ovan eller konsultera Aspose.Words‑dokumentationen för avancerad teckensnittshantering.

Lycka till med kodningen!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Aktivera varningar för teckensnittsbyte i Aspose.Words – komplett guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Logga varningar för teckensnittsbyte – komplett Aspose.Words‑guide](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Läs in med kodning i Word‑dokument](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}