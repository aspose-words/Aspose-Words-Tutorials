---
category: general
date: 2026-07-06
description: Aktivera återställningsläge för att öppna en korrupt docx‑fil med Aspose.Words.
  Lär dig hur du snabbt återställer ett korrupt Word‑dokument.
draft: false
keywords:
- enable recovery mode
- recover corrupted word document
- recover damaged docx file
- how to open corrupted docx
language: sv
og_description: Aktivera återställningsläge låter dig öppna en korrupt docx‑fil och
  försöka återställa ett skadat Word‑dokument.
og_title: Aktivera återställningsläge – Återställ korrumperat Word-dokument
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Enable recovery mode to open a corrupted docx file with Aspose.Words.
    Learn how to recover corrupted Word document quickly.
  headline: Enable recovery mode – Recover corrupted Word document
  type: TechArticle
- questions:
  - answer: No. It only affects how the library reads the file in memory. The source
      remains untouched unless you explicitly call `Save`.
    question: Does enabling recovery mode modify the original file?
  - answer: Usually yes, as long as the underlying ZIP entry isn’t broken. If an image
      stream is missing, Aspose.Words will skip it and continue.
    question: Can I recover images that were embedded in the corrupted docx?
  - answer: Slightly, because the parser performs additional checks. The overhead
      is negligible for typical documents (<10 MB).
    question: Is recovery mode slower?
  - answer: '`RecoveryMode.Auto` (default) tries to recover only when an error occurs.
      `RecoveryMode.None` disables any recovery attempts. `RecoveryMode.Recover` forces
      the attempt every time. ## Full Working Example Below is a self‑contained console
      app you can copy‑paste into a new .NET project. It demonstrate'
    question: What other recovery options exist?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Document Recovery
- Word
title: Aktivera återställningsläge – Återställ korrupt Word-dokument
url: /sv/net/programming-with-loadoptions/enable-recovery-mode-recover-corrupted-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aktivera återställningsläge – Återställ korrupt Word-dokument

Har du någonsin försökt öppna en **korrupt docx** och sett felmeddelandet stirra tillbaka på dig? Det är frustrerande, särskilt när filen innehåller veckors arbete. Lyckligtvis ger Aspose.Words dig ett sätt att *aktivera återställningsläge* så att du kan försöka rädda innehållet utan manuell kopiering‑och‑klistring.

I den här guiden går vi igenom de exakta stegen för att **aktivera återställningsläge**, läsa in den trasiga filen och spara en användbar kopia. I slutet kommer du att veta hur man *återställer korrupta Word-dokument* programmässigt och även hanterar ett scenario för *återställning av skadad docx-fil* på ett smidigt sätt.

## Vad du behöver

- .NET 6 (eller någon nyare .NET‑runtime) – biblioteket fungerar också på .NET Framework.
- Visual Studio 2022 eller VS Code – ditt favorit‑IDE räcker.
- **Aspose.Words for .NET** NuGet‑paket (`Install-Package Aspose.Words`) – detta är det enda externa beroendet.
- Ett exempel på en korrupt `docx` (vi kallar den `corrupted.docx`).

Det är allt. Inga extra verktyg, ingen manuell XML‑klurning. Bara några rader C#.

![aktivera återställningsläge i Aspose.Words](image-url-placeholder.png)

*Bildtext: aktivera återställningsläge i Aspose.Words*

## Steg 1: Installera Aspose.Words och konfigurera projektet

Öppna din terminal (eller Package Manager Console) och kör:

```bash
dotnet add package Aspose.Words
```

Alternativt, i Visual Studio öppna **Tools → NuGet Package Manager → Manage NuGet Packages** och sök efter *Aspose.Words*. När det är installerat, lägg till namnrymden högst upp i din fil:

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
```

> **Proffstips:** Håll dina paket uppdaterade. Återställningslogiken förbättras med varje version.

## Steg 2: Aktivera återställningsläge med `LoadOptions`

Kärnan i lösningen är klassen `LoadOptions`. Genom att sätta dess egenskap `RecoveryMode` till `RecoveryMode.Recover` instruerar du Aspose.Words att *aktivera återställningsläge* när dokumentet parsas.

```csharp
// Step 2: Create LoadOptions and enable recovery mode
LoadOptions loadOptions = new LoadOptions
{
    RecoveryMode = RecoveryMode.Recover   // <-- this line turns on recovery
};
```

Varför är detta viktigt? Utan återställningsläge avbryter Aspose.Words vid det första tecknet på korruption. Med det försöker biblioteket så gott det kan hoppa över trasiga delar och ändå producera ett användbart `Document`‑objekt.

## Steg 3: Läs in den potentiellt korrupta filen

Nu läser vi faktiskt in filen. Om dokumentet är oåterställbart kommer Aspose.Words fortfarande att returnera en `Document`‑instans, men vissa element kan saknas.

```csharp
// Step 3: Load the potentially corrupted document using the recovery options
Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
```

Observera att sökvägen är en absolut sträng; justera den till var din testfil finns. `Document`‑konstruktorn läser filen **med återställningsläge aktiverat**, vilket ger dig en chans att *återställa korrupt Word-dokument*-innehåll.

## Steg 4: Verifiera vad som återställdes (valfritt men användbart)

Det är god praxis att inspektera det inlästa dokumentet innan du bestämmer dig för att skriva över något. För en snabb kontroll kan du skriva ut de första paragraferna till konsolen:

```csharp
// Optional: Print first 3 paragraphs to verify recovery
for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
{
    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
}
```

Om du ser förvrängd text eller många tomma strängar kan filen vara **för skadad**. Ändå har du nu ett `Document`‑objekt som du kan manipulera – lägga till ett sidhuvud, ersätta saknade bilder osv.

## Steg 5: Spara det återställda dokumentet

Om kontrollen ser okej ut, skriv den återställda versionen till en ny fil. Detta steg återställer i praktiken *skadad docx‑fil* och ger dig en ren kopia som du kan öppna i Word.

```csharp
// Step 5: Save the recovered document
string outputPath = @"C:\Temp\recovered.docx";
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Recovered document saved to: {outputPath}");
```

Om originalfilen var en `.doc` eller ett annat format kan du ändra `SaveFormat` därefter (t.ex. `SaveFormat.Pdf` för PDF‑utmatning).

## Steg 6: Hantera undantag och kantfall

Även med återställningsläge är vissa katastrofer oåterställbara (t.ex. helt avkortade zip‑strukturer). Omslut laddningen i ett try‑catch‑block för att visa dessa problem:

```csharp
try
{
    Document doc = new Document(@"C:\Temp\corrupted.docx", loadOptions);
    // proceed with saving...
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to recover the document: {ex.Message}");
    // You might log the stack trace or notify the user.
}
```

En vanlig fråga är **”hur öppnar man en korrupt docx”** när filen är lösenordsskyddad. Återställningsläge **bypassar inte** kryptering; du behöver fortfarande lösenordet. I så fall, sätt `LoadOptions.Password` innan du laddar.

## Vanliga frågor (FAQ)

**Q: Påverkar aktivering av återställningsläge den ursprungliga filen?**  
A: Nej. Det påverkar bara hur biblioteket läser filen i minnet. Källfilen förblir orörd såvida du inte explicit anropar `Save`.

**Q: Kan jag återställa bilder som var inbäddade i den korrupta docx‑filen?**  
A: Vanligtvis ja, så länge den underliggande ZIP‑posten inte är trasig. Om en bildström saknas hoppar Aspose.Words över den och fortsätter.

**Q: Är återställningsläge långsammare?**  
A: Lite grann, eftersom parsern utför extra kontroller. Överheaden är försumbar för vanliga dokument (<10 MB).

**Q: Vilka andra återställningsalternativ finns?**  
A: `RecoveryMode.Auto` (standard) försöker återställa endast när ett fel uppstår. `RecoveryMode.None` inaktiverar alla återställningsförsök. `RecoveryMode.Recover` tvingar ett försök varje gång.

## Fullständigt fungerande exempel

Nedan är en fristående konsolapp som du kan kopiera‑och‑klistra in i ett nytt .NET‑projekt. Den demonstrerar hela flödet – från installation av paketet till sparande av den återställda filen.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

namespace RecoverCorruptedDocx
{
    class Program
    {
        static void Main(string[] args)
        {
            // Path to the corrupted document
            string inputPath = @"C:\Temp\corrupted.docx";
            // Where the recovered file will be written
            string outputPath = @"C:\Temp\recovered.docx";

            // Step 1: Create LoadOptions and enable recovery mode
            LoadOptions loadOptions = new LoadOptions
            {
                RecoveryMode = RecoveryMode.Recover
            };

            try
            {
                // Step 2: Load the document with recovery enabled
                Document doc = new Document(inputPath, loadOptions);

                // Optional sanity check – print first three paragraphs
                Console.WriteLine("=== First three paragraphs after recovery ===");
                for (int i = 0; i < Math.Min(3, doc.FirstSection.Body.Paragraphs.Count); i++)
                {
                    Console.WriteLine($"Paragraph {i + 1}: {doc.FirstSection.Body.Paragraphs[i].GetText().Trim()}");
                }

                // Step 3: Save the recovered document
                doc.Save(outputPath, SaveFormat.Docx);
                Console.WriteLine($"\nRecovered document saved to: {outputPath}");
            }
            catch (Exception ex)
            {
                Console.WriteLine($"Failed to open or recover the document: {ex.Message}");
            }
        }
    }
}
```

**Förväntad output (förutsatt att återställning lyckas):**

```
=== First three paragraphs after recovery ===
Paragraph 1: Project Overview
Paragraph 2: This document outlines...
Paragraph 3: ...

Recovered document saved to: C:\Temp\recovered.docx
```

Om filen är för skadad kommer du att se ett felmeddelande istället för paragrafutskriften.

## Slutsats

Vi har just visat hur man **aktiverar återställningsläge** i Aspose.Words, läser in en trasig `docx` och **återställer korrupt Word-dokument**‑data till en ny fil. Samma mönster låter dig *återställa skadad docx‑fil* i batch‑jobb, automatiserade e‑postbilagor, eller

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [hur man återställer docx – sätt återställningsläge & öppna korrupta Word‑filer](/words/english/net/programming-with-loadoptions/how-to-recover-docx-set-recovery-mode-open-corrupted-word-fi/)
- [hur man återställer docx med Aspose.Words – steg för steg](/words/english/net/programming-with-loadoptions/how-to-recover-docx-with-aspose-words-step-by-step/)
- [Återställ skadad Word‑fil – Komplett guide för att öppna korrupt DOCX & få sida](/words/english/net/programming-with-loadoptions/recover-damaged-word-file-complete-guide-to-open-corrupted-d/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}