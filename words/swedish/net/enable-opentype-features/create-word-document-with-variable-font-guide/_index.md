---
category: general
date: 2026-03-19
description: Skapa Word-dokument med Aspose.Words och ett variabelt teckensnitt. Lär
  dig hur du ändrar teckensnittsvikt, ställer in teckensnittsbredd och definierar
  teckensnittvariation i C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: sv
og_description: Skapa ett Word‑dokument med ett variabelt teckensnitt med Aspose.Words.
  Den här handledningen visar hur du laddar teckensnittet, ändrar teckensnittsvikt,
  ställer in teckensnittsbredd och definierar teckensnittvariation.
og_title: Skapa Word-dokument med variabelt teckensnitt – Komplett guide
tags:
- Aspose.Words
- C#
- Variable Font
title: Skapa Word-dokument med variabelt teckensnitt – guide
url: /sv/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa Word‑dokument med variabelt typsnitt – Guide

Har du någonsin behövt **skapa ett Word‑dokument** som använder ett modernt variabelt typsnitt, men inte vetat var du ska börja? Du är inte ensam. I många projekt – tänk dynamiska rapporter eller varumärkes‑konsekventa broschyrer – är möjligheten att **ändra teckensnittsvikt** i farten ett verkligt spelväxlare.  

I den här handledningen går vi igenom hela processen: från att ladda ett variabelt typsnitt i Aspose.Words, till att sätta dess vikt och bredd, och slutligen spara en DOCX som ser exakt ut som du designade. Inga vaga referenser, bara konkret kod som du kan klistra in i ditt C#‑projekt just nu.

## Vad du kommer att lära dig

- Hur du **laddar variabla typsnittsfiler** i Aspose.Words med `FontSettings`.
- Syntaxen för att **definiera typsnittvariation**‑axlar såsom `wght` (weight) och `wdth` (width).
- Sätt att **sätta teckensnittsbredde** och **ändra teckensnittsvikt** på ett enskilt `Run`.
- Tips för felsökning av vanliga fallgropar (saknade glyfer, felaktiga mappvägar, osv.).
- Ett komplett, körbart exempel som du kan kopiera‑klistra och testa omedelbart.

> **Förutsättningar**: .NET 6+ (eller .NET Framework 4.6+), Aspose.Words för .NET installerat via NuGet, och en variabel‑typsnittfil som *RobotoFlex.ttf* placerad i en lokal *Fonts*-mapp.

---

## Steg 1 – Ladda det variabla typsnittet i Aspose.Words

Först måste vi tala om för Aspose.Words var den ska leta efter våra egna typsnitt. Klassen `FontSettings` sköter det tunga arbetet.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Varför detta är viktigt**: Utan att registrera mappen faller Aspose.Words tillbaka på systemtypsnitt och ignorerar all OpenType‑variationsdata du försöker applicera senare. Genom att peka på en specifik katalog garanterar du att *RobotoFlex* (eller vilket annat variabelt typsnitt som helst) hittas varje gång koden körs.

> **Pro‑tips**: Sätt den andra parametern i `SetFontsFolder` till `true` om du vill att Aspose även ska söka i underkataloger. Detta hjälper när du organiserar typsnitt efter stil eller vikt.

---

## Steg 2 – Skapa ett nytt dokument och lägg till exempeltext

Nu när teckensnittsmotorn vet var den ska leta, startar vi ett tomt `Document` och infogar ett stycke med ett `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Vad som händer**: `Run` representerar ett sammanhängande textstycke med enhetlig formatering. Genom att skapa det först håller vi formateringslogiken isolerad – perfekt för att senare applicera olika variationsaxlar på separata runs om så behövs.

---

## Steg 3 – Definiera de önskade variationsaxlarna (Vikt & Bredd)

Variabla typsnitt exponerar *axlar* som du kan justera vid körning. De två vanligaste är `wght` (font weight) och `wdth` (font width). Aspose.Words modellerar detta med samlingen `OpenTypeFontVariation`.  

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Varför dessa siffror**: I OpenType‑specifikationen sträcker sig `wght` från typsnittets minsta till största vikt (ofta 100–900). Ett värde på **700** motsvarar ett fetstil‑utseende. `wdth` fungerar på samma sätt; **100** betyder standard (normal) bredd, medan värden under 100 komprimerar glyferna.

> **Edge case**: Vissa variabla typsnitt stödjer inte en viss axel. Om du anger en icke‑stödd tagg kommer Aspose att ignorera den tyst. Kontrollera alltid typsnittets specifikation (vanligtvis finns den i `.ttf`‑ eller `.otf`‑filens metadata).

---

## Steg 4 – Applicera variationen på Run‑en med typsnittsnamnet

Nu binder vi variationsdata till den faktiska texten. Klassen `FontInfo` innehåller typsnittsfamiljens namn och axelsamlingen.  

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Förklaring**: Genom att sätta `FontInfo` kringgår vi den vanliga `Font.Name`‑egenskapen och ger motorn en fullständigt specificerad typsnittskonfiguration. Detta är det enda sättet att tala om för Aspose.Words att använda ett variabelt typsnitt med egna axlar.

> **Vanligt misstag**: Att glömma att matcha exakt familjenamn i typsnittsfilen (`RobotoFlex` i detta exempel). Ett stavfel får Aspose att falla tillbaka på ett standardsnitt, och din variation går förlorad.

---

## Steg 5 – Spara dokumentet och verifiera resultatet

Till sist skriver vi dokumentet till disk. Den genererade DOCX‑filen kommer att innehålla instruktionerna för variabelt typsnitt, vilket Microsoft Word (2016+) kan rendera korrekt.  

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Öppna den resulterande filen i Word, markera texten och titta i **Font**‑dialogen. Du bör se *Roboto Flex* listat, och texten kommer att visas fetare än den omgivande texten – exakt vad vår inställning `wght = 700` begärde.

> **Verifieringstips**: Om texten ser oförändrad ut, dubbelkolla att typsnittsfilen verkligen stödjer `wght`‑axeln. Vissa “variabla” typsnitt exponerar bara `ital` (italic) eller `opsz` (optical size).

---

## Valfritt: Lägg till fler variationer – Ändra bredd dynamiskt

Om du vill *sätta teckensnittsbredde* annorlunda för ett annat stycke, upprepa bara steg 3‑4 med en ny `OpenTypeFontVariation`‑samling.  

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Nu har du två runs – en fet, en något bredare – som demonstrerar både **ändra teckensnittsvikt** och **sätta teckensnittsbredde** i samma dokument.

---

## Fullt fungerande exempel

Kopiera snippet‑en nedan till en ny konsolapp (`Program.cs`) och kör den. Se till att `Fonts`‑mappen innehåller `RobotoFlex.ttf` (eller vilket variabelt typsnitt du föredrar).  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Förväntat resultat**: En `VariableFont.docx`‑fil där frasen “Variable‑weight text” visas i fet stil, tack vare `wght = 700`‑axeln, samtidigt som standardbredden behålls.

---

## Vanliga frågor & Edge Cases

| Fråga | Svar |
|----------|--------|
| *Vad händer om typsnittet inte hittas?* | Kontrollera mappvägen, säkerställ att filnamnet stämmer och att processen har läsbehörighet. Du kan också anropa `fontSettings.GetFonts()` för att lista upptäckta typsnitt. |
| *Kan jag kombinera flera runs med olika variationer?* | Absolut. Varje `Run` kan ha sin egen `FontInfo`. Upprepa bara steg 3‑4 för varje run. |
| *Stöder äldre versioner av Word variabla typsnitt?* | Word 2016 (Build 16.0.8001) introducerade grundläggande stöd. Om du riktar dig mot äldre versioner faller dokumentet tillbaka till den närmaste statiska instansen av typsnittet. |
| *Finns det någon gräns för hur många axlar jag kan sätta?* | Du kan sätta så många som typsnittet definierar. Vanliga taggar är `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Att ange en icke‑stödd tagg har helt enkelt ingen effekt. |
| *Hur felsöker jag saknade glyfer?* | Använd `FontSettings.GetFontSources()` för att inspektera laddade typsnitt, och `FontInfo.HasGlyph(char)` för att testa enskilda tecken. |

---

## Slutsats

På några få steg har vi visat **hur du skapar Word‑dokument** som utnyttjar kraften i variabla typsnitt, så att du kan **ändra teckensnittsvikt**, **sätta teckensnittsbredde**, **ladda variabla typsnittsfiler** och **definiera typsnittvariation**‑axlar – allt med Aspose.Words för .NET.  

Kärnidén är enkel: registrera typsnittsmappen, beskriv önskade axlar, fäst dem på ett `Run`, och spara. Därefter kan du utöka tekniken till hela sektioner, tabeller eller till och med programatiskt generera varumärkes‑specifika rapporter.

**Nästa steg**: prova att byta ut `RobotoFlex` mot ett annat variabelt typsnitt, experimentera med `ital`‑axeln, eller generera en PDF‑version av samma dokument med Aspose.PDF. Samma mönster gäller – ladda, definiera, applicera, spara.

Lycka till med kodandet, och njut av den flexibilitet som variabla typsnitt ger dina Word‑automatiseringsprojekt!  

<img src="variable-font-demo.png" alt="Skapa word‑dokument med variabelt typsnitt exempel">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}