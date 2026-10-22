---
category: general
date: 2026-10-13
description: Leer lettertypevervanging in een document met C#. Deze gids laat zien
  hoe je big5‑encoding instelt, een DOCX laadt en verouderde lettertypen vervangt
  door moderne.
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
language: nl
lastmod: 2026-10-13
og_description: Lettertypevervanging in een document is essentieel bij het werken
  met legacy Chinese bestanden. Volg deze stapsgewijze tutorial om een DOCX met big5-codering
  te laden en oude lettertypen te vervangen.
og_image_alt: Screenshot of C# code that performs font substitution in document
og_title: Lettertypevervanging in document met C# – volledige gids
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
title: Hoe lettertypevervanging uit te voeren in een document met C#
url: /nl/net/working-with-fonts/how-to-perform-font-substitution-in-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lettertypevervanging in document – volledige C#‑handleiding

Als u **font substitution in document** nodig heeft om legacy Chinese bestanden correct weer te geven, laat deze gids u precies zien hoe u dit doet. Door de juiste tekencodering te configureren en een verouderd lettertype te vervangen door een modern lettertype, garandeert u dat de uiteindelijke DOCX wordt weergegeven zoals bedoeld.

Documentverwerking breekt vaak wanneer de bron een oude codering zoals **big5** gebruikt of verwijst naar een lettertype dat niet meer op het systeem aanwezig is. Deze tutorial leidt u stap voor stap door het laden van een DOCX met de juiste **big5‑codering**, het toepassen van **legacy font replacement**, en het produceren van een schone output die op elke Windows‑machine werkt.

U leert:

* Hoe u een `LoadOptions`‑object maakt met **big5‑encoding**.  
* Hoe u een DOCX‑bestand opent met **C# LoadOptions**.  
* Hoe u **font substitution in document** uitvoert door een oud lettertype te koppelen aan een modern equivalent.  
* Hoe u randgevallen afhandelt voor ontbrekende lettertypen en meerdere lettertype‑families.

Er zijn geen externe tools vereist buiten de Aspose.Words for .NET‑bibliotheek, en de volledige code kan direct in een console‑project worden gekopieerd en uitgevoerd.

## Voorwaarden

* .NET 6.0 of later (het voorbeeld gebruikt .NET 6 console‑syntaxis).  
* Aspose.Words for .NET – installeren via `dotnet add package Aspose.Words`.  
* Een DOCX‑bestand opgeslagen met **big5‑encoding** dat verwijst naar het legacy‑lettertype `MingLiU-ExtB`.  
* Basiskennis van C# en Visual Studio of een andere IDE naar keuze.

## Stap 1: Het project opzetten en namespaces importeren

Maak een nieuwe console‑applicatie en voeg de benodigde `using`‑directieven toe. Dit zorgt ervoor dat de code compileert zonder extra aanpassingen.

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

> **Pro tip:** Houd de `Main`‑methode minimaal; dit verbetert de leesbaarheid en maakt de tutorial makkelijker te volgen.

## Stap 2: Load‑opties definiëren met de juiste tekencodering (big5 voor Traditioneel Chinees)

De `LoadOptions`‑klasse vertelt Aspose.Words hoe de ruwe bytes in het bronbestand geïnterpreteerd moeten worden. Het gebruik van **big5‑encoding** is cruciaal voor Traditionele Chinese tekens die met die legacy‑codepagina zijn opgeslagen.

```csharp
// Step 2: Define load options with big5 encoding.
LoadOptions loadOptions = new LoadOptions
{
    // Explicitly set the encoding to the traditional Chinese code page.
    Encoding = Encoding.GetEncoding("big5")
};
```

**Waarom dit belangrijk is:** Als u de codering weglaten of de standaard UTF‑8 gebruiken, kunnen tekens verschijnen als onleesbare symbolen (mojibake). Het specificeren van `big5` behoudt de oorspronkelijke glyphs voordat er een lettertype‑vervanging plaatsvindt.

## Stap 3: Het DOCX‑bestand laden met de gespecificeerde codering

Geef de `loadOptions`‑instantie door aan de `Document`‑constructor. Hierdoor wordt het bestand geladen met inachtneming van de **document‑encoding voor Chinees** die u eerder hebt gedefinieerd.

```csharp
// Step 3: Load the DOCX file with the big5 encoding.
string inputPath = @"C:\Docs\big5_doc.docx"; // Update this path to your file location.
Document doc = new Document(inputPath, loadOptions);
```

Als het bestand niet gevonden kan worden, gooit het programma een `FileNotFoundException`. Zorg ervoor dat het pad correct is en dat de applicatie leesrechten heeft.

## Stap 4: Een legacy‑lettertype vervangen door een modern equivalent

Veel oudere Chinese documenten verwijzen naar `MingLiU-ExtB`, dat mogelijk niet aanwezig is op nieuwere Windows‑installaties. Het koppelen ervan aan `Microsoft JhengHei` (een breed beschikbare Unicode‑lettertype) zorgt voor correcte weergave.

```csharp
// Step 4: Perform font substitution in document.
doc.FontInfos.Substitution.Add("MingLiU-ExtB", "Microsoft JhengHei");

// Optional: Verify that the substitution succeeded.
foreach (FontInfo fontInfo in doc.FontInfos)
{
    Console.WriteLine($"Original: {fontInfo.FontFamilyName}, Substituted: {fontInfo.SubstitutedFontFamilyName}");
}
```

**Uitleg:**  
* `FontInfos.Substitution.Add(oldFont, newFont)` registreert een globale vervangingsregel. Elke keer dat Aspose.Words `MingLiU-ExtB` tegenkomt, wordt het vervangen door `Microsoft JhengHei`.  
* De optionele lus print de mapping, wat handig is voor debugging in grote documenten met meerdere lettertype‑families.

## Stap 5: Het verwerkte document opslaan

Na de vervanging schrijft u het document naar een nieuw bestand. De output toont de Chinese tekst met het moderne lettertype, waardoor waarschuwingen over ontbrekende glyphs verdwijnen.

```csharp
// Step 5: Save the updated document.
string outputPath = @"C:\Docs\big5_doc_fixed.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to {outputPath}");
```

Open het resulterende bestand in Microsoft Word of een andere DOCX‑viewer; u zou de Traditionele Chinese tekens schoon moeten zien weergegeven met `Microsoft JhengHei`.

## Randgevallen en veelvoorkomende valkuilen

| Situatie | Aanbevolen aanpak |
|-----------|----------------------|
| **Het bron‑lettertype staat niet in het document** | Gebruik `doc.FontInfos.Substitution.Add` met een wildcard‑patroon, bijvoorbeeld `doc.FontInfos.Substitution.Add("*MingLiU*", "Microsoft JhengHei")`. |
| **Meerdere legacy‑lettertypen moeten worden vervangen** | Roep `Add` aan voor elk paar, of laad een substitutie‑dictionary vanuit een configuratie‑bestand. |
| **Het doel‑lettertype is niet beschikbaar op de doelsysteem** | Kies een lettertype dat standaard met Windows wordt geleverd (bijv. `Arial Unicode MS`) of embed het lettertype met `doc.FontInfos.EmbeddingMode = FontEmbeddingMode.EmbedAll`. |
| **Coderingsfouten blijven verschijnen** | Controleer of het bronbestand daadwerkelijk **big5** gebruikt; u kunt het bestand inspecteren met een hex‑editor of `File.ReadAllBytes` gebruiken en byte‑patronen vergelijken. |

## Volledig werkend voorbeeld

Hieronder staat het complete, zelfstandige programma. Kopieer het naar `Program.cs`, pas de bestands‑paden aan en voer het uit.

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

**Verwacht resultaat:** Het openen van `big5_doc_fixed.docx` toont alle Traditionele Chinese tekens correct weergegeven, zonder waarschuwingen over ontbrekende glyphs, omdat `MingLiU-ExtB` is vervangen door `Microsoft JhengHei`.

## Conclusie

U beschikt nu over een betrouwbare methode voor **font substitution in document**‑taken met C#. Door **big5‑encoding** te configureren, de DOCX te laden met `LoadOptions` en legacy‑lettertypen te koppelen aan moderne equivalenten, elimineert u weergaveproblemen die oudere Chinese bestanden teisteren.  

Vanaf hier kunt u:

* De substitutie‑map uitbreiden om extra legacy‑lettertypen te dekken.  
* Het proces automatiseren voor batches documenten (doorloop een map).  
* Lettertype‑vervanging combineren met andere documenttransformaties zoals watermerken of PDF‑conversie.

Voel u vrij om te experimenteren met verschillende doel‑lettertypen of aangepaste lettertypen te embedden voor volledige draagbaarheid. Als u tegen problemen aanloopt, raadpleeg dan opnieuw de tabel met randgevallen of de Aspose.Words‑documentatie voor geavanceerde lettertype‑handling.

Veel plezier met coderen!

## Wat moet u hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids zijn gedemonstreerd. Elke bron bevat complete werkende code‑voorbeelden met stap‑voor‑stap uitleg om u te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in uw eigen projecten te verkennen.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Log Font Substitution Warnings – Complete Aspose.Words Guide](/words/english/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/)
- [Load With Encoding In Word Document](/words/english/net/programming-with-loadoptions/load-with-encoding/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}