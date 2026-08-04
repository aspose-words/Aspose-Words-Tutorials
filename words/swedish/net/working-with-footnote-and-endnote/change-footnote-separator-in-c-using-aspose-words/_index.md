---
category: general
date: 2026-08-04
description: Ändra fotnotseparator i C# med Aspose.Words – lär dig hur du redigerar
  fotnotseparatorn och ändrar slutnotseparatorn i Word-dokument.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: sv
lastmod: 2026-08-04
og_description: Ändra fotnotseparator i C# med Aspose.Words. Den här guiden visar
  hur du redigerar fotnotseparator, anpassar slutnotseparator och sparar det uppdaterade
  dokumentet.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Ändra fotnotseparator i C# – komplett Aspose.Words-guide
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Ändra fotnotseparator i C# med Aspose.Words
url: /sv/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ändra fotnotseparator i C# med Aspose.Words

Om du behöver **ändra fotnotseparator** i ett Word-dokument, guidar den här handledningen dig genom de exakta stegen med Aspose.Words för .NET. Oavsett om du vill ersätta standardlinjen med en symbol, eller tillämpa en annan stil på slutnotseparatorer, täcker koden nedan hela arbetsflödet.

Du kommer också att lära dig hur du **redigerar fotnotseparator** och den relaterade **ändra slutnotseparator**-operationen, så att samma dokument kan ha enhetlig formatering för både fotnoter och slutnoter. Inga externa verktyg krävs—bara några rader C#.

## Vad du kommer att uppnå

By the end of this guide you will be able to:

* Ladda en befintlig *.docx*-fil som innehåller fotnoter och slutnoter.  
* Åtkomst till separator‑noderna för fotnoter, fotnotfortsättningar och slutnoter.  
* Ersätt separator‑tecknet (t.ex. ändra standardlinjen till en asterisk).  
* Spara det modifierade dokumentet utan att förlora något annat innehåll.  

Handledningen förutsätter att du har en grundläggande förståelse för C# och har installerat **Aspose.Words** NuGet‑paketet (version 24.9 eller senare).  

---

## Förutsättningar

| Krav | Orsak |
|------|-------|
| .NET 6.0+ or .NET Framework 4.7.2+ | Krävd runtime för Aspose.Words |
| Aspose.Words for .NET library | Tillhandahåller `Document` och `FootnoteOptions` API:erna |
| En inmatnings‑Word‑fil (`input.docx`) med minst en fotnot eller slutnot | Demonstrerar separatorändringen |

Du kan lägga till Aspose.Words i ditt projekt med följande CLI‑kommando:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Steg 1: Ladda dokumentet som innehåller fotnoter

Den första operationen är att läsa källfilen till ett `Document`‑objekt. Detta objekt representerar hela Word‑filen i minnet och ger dig åtkomst till alla dess noder.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Varför detta är viktigt:** Att ladda dokumentet är startpunkten för all manipulation. Om filen inte kan hittas kastar Aspose.Words ett `FileNotFoundException`, så se till att sökvägen är korrekt innan du fortsätter.

---

## Steg 2: Åtkomst till fotnot‑ och slutnotseparator‑noderna

`Document.FootnoteOptions` exponerar tre separator‑noder:

* `Separator` – raden som visas efter fotnotssamlingen på den första sidan.  
* `ContinuationSeparator` – raden som används när fotnoter fortsätter på nästa sida.  
* `EndnoteSeparator` – raden som separerar huvudtexten från slutnotlistan.  

Du hämtar dessa noder som generiska `Node`‑objekt och kastar dem sedan till `Run` för att ändra texten.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Varför detta är viktigt:** Dessa noder är de enda ställena där det visuella separator‑tecknet finns. Att ändra någon annan nod (t.ex. ett vanligt stycke) kommer inte att påverka fotnotformateringen.

---

## Steg 3: Ändra fotnotseparator‑tecknet

Det vanligaste kravet är att ersätta standardlinjen med en symbol, såsom en asterisk (`*`). Eftersom separatorn lagras som ett `Run` kan du säkert ändra dess `Text`‑egenskap.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Varför detta är viktigt:** Att direkt redigera `Run.Text` uppdaterar den visuella representationen i det slutgiltiga dokumentet utan att påverka annat fotnotinnehåll. Samma mönster kan användas för att tillämpa vilken sträng som helst, inklusive Unicode‑symboler.

---

## Steg 4: Ändra slutnotseparator (valfritt)

Om du också behöver **ändra slutnotseparator**, så speglar processen fotnotändringen. Ersätt texten i `endnoteSeparator` med ditt önskade tecken.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Varför detta är viktigt:** Slutnoter är ofta formaterade annorlunda än fotnoter. Att tillhandahålla en separat separator låter dig behålla visuell konsistens med ditt dokuments designriktlinjer.

---

## Steg 5: Spara det modifierade dokumentet

Efter alla ändringar, spara förändringarna med `Document.Save`. Du kan skriva över den ursprungliga filen eller spara till en ny plats.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Varför detta är viktigt:** `Save` skriver den minnes‑representationen till disk och bevarar alla andra element (stilar, bilder, tabeller) oförändrade.

---

## Fullt, körbart exempel

När alla delar sätts ihop, här är en fristående konsolapplikation som demonstrerar hela arbetsflödet:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Förväntat resultat:** Öppna *ModifiedSeparators.docx* i Microsoft Word. Fotnotseparatorlinjen längst ner på den första fotnotssidan kommer nu att vara en ensam asterisk (`*`). Om dokumentet innehåller slutnoter kommer linjen som separerar huvudtexten från slutnotlistan att visas som ett streck (`-`). Allt annat innehåll (text, bilder, tabeller) förblir orört.

---

## Vanliga frågor & hantering av kantfall

| Fråga | Svar |
|-------|------|
| **Vad händer om dokumentet saknar fotnoter?** | `FootnoteOptions.Separator` returnerar fortfarande en `Run`‑nod, men dess text kan vara tom. Koden kontrollerar säkert nodtypen innan den modifieras. |
| **Kan jag använda en sträng med flera tecken (t.ex. "***")?** | Ja. `Run.Text`‑egenskapen accepterar vilken sträng som helst, inklusive Unicode‑tecken. |
| **Kommer ändring av separatorn att påverka befintlig fotnotnumrering?** | Nej. Separatorn är oberoende av numreringsschemat. |
| **Behöver jag avyttra `Document`‑objektet?** | `Document` implementerar `IDisposable` implicit via `Node`. I en kortlivad konsolapp är det valfritt, men för långlivade tjänster kan du omsluta det i ett `using`‑block. |
| **Hur fungerar detta med .NET Core vs .NET Framework?** | API:et är identiskt över olika runtime‑miljöer; endast mål‑ramverkets version spelar roll (måste stödjas av Aspose.Words‑paketet). |

**Proffstips:** Om du behöver tillämpa olika separatorer för olika sektioner kan du iterera genom `doc.GetChildNodes(NodeType.Footnote, true)` och justera varje fotnot's `Separator`‑egenskap individuellt. Detta är mer avancerat men användbart för komplexa dokument.

---

## Slutsats

Du vet nu hur du **ändrar fotnotseparator** och **ändrar slutnotseparator** i en Word‑fil med Aspose.Words för C#. Guiden täckte hur man laddar dokumentet, får åtkomst till relevanta separator‑noder, modifierar deras text och sparar resultatet—allt i ett enda, fristående program.

Härifrån kan du utforska relaterade ämnen som **redigera fotnotseparatorstil**, anpassa fotnotnumrering, eller tillämpa villkorlig formatering baserat på sidlayout. Samma mönster (hämta en nod, kasta till `Run`, modifiera `Text`) fungerar för många andra Word‑bearbetningsscenarier.

Lycka till med kodandet, och känn dig fri att experimentera med olika symboler eller till och med bädda in bilder som separatorer för en riktigt unik dokumentlayout!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i denna guide. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Bearbetning av ord med fotnot och slutnot](/words/english/net/working-with-footnote-and-endnote/)
- [Hämta stycke‑stilsseparator i Word‑dokument](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Infoga dokument‑stilsseparator i Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}