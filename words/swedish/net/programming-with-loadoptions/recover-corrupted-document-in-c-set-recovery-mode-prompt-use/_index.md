---
category: general
date: 2026-01-11
description: Återställ korrupt dokument i C# med Aspose.Words. Lär dig hur du ställer
  in återställningsläge, laddar docx med återställning och visar ett meddelande till
  användaren vid fel i några enkla steg.
draft: false
keywords:
- recover corrupted document
- set recovery mode
- load docx with recovery
- prompt user on error
language: sv
og_description: Återställ korrupt dokument i C# genom att sätta återställningsläge,
  ladda en DOCX med återställning och visa ett meddelande till användaren vid fel.
  Komplett steg‑för‑steg‑handledning.
og_title: Återställ korrupt dokument i C# – Snabbguide
tags:
- Aspose.Words
- C#
- Document Recovery
title: Återställ korrupt dokument i C# – Ställ in återhämtningsläge och be användaren
url: /sv/net/programming-with-loadoptions/recover-corrupted-document-in-c-set-recovery-mode-prompt-use/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Återställ korrupt dokument i C# – Fullständig guide

Har du någonsin försökt öppna en DOCX som ser bra ut i Word men som kastar ett undantag i din kod? Du har förmodligen ett **recover corrupted document**‑scenario. Den goda nyheten är att Aspose.Words ger dig finjusterad kontroll över hur du hanterar dessa besvärliga filer—oavsett om du vill tyst fixa dem, kasta ett undantag eller fråga användaren vad som ska göras.

I den här handledningen går vi igenom allt du behöver för att **recover corrupted document**‑filer, från att installera biblioteket till att välja rätt **set recovery mode**‑alternativ, **load docx with recovery**, och slutligen **prompt user on error** när något går fel. Inga onödiga detaljer, bara ett komplett, körbart exempel som du kan lägga in i vilket .NET‑projekt som helst.

> **Snabb förhandsvisning:** Vid slutet har du en konsolapp som laddar en eventuellt trasig `corrupt.docx`, loggar eventuella varningar och frågar användaren om de vill fortsätta när återställningen misslyckas.

## Vad du behöver

- **.NET 6.0** eller senare (koden fungerar även på .NET Framework 4.6+).  
- **Aspose.Words for .NET** – installera via NuGet (`Install-Package Aspose.Words`).  
- En **corrupt DOCX**‑fil att ha till hands för testning (du kan medvetet skada en fil genom att öppna den i en hex‑editor eller byta namn på dess filändelse).  
- Valfri IDE du föredrar—Visual Studio, Rider eller till och med VS Code fungerar.

> *Proffstips:* Behåll en säkerhetskopia av originalfilen. Återställning kan skriva om delar av dokumentet, och du vill inte förlora de bra delarna.

## Steg 1 – Installera Aspose.Words och lägg till namnrymder

Först och främst. Hämta biblioteket från NuGet och importera de nödvändiga namnrymderna.

```csharp
// Install via Package Manager Console:
// Install-Package Aspose.Words

using System;
using Aspose.Words;
using Aspose.Words.Loading;
```

Det är allt du behöver för resten av handledningen. Namnrymden `Aspose.Words.Loading` innehåller klassen `LoadOptions`, som är nyckeln till **set recovery mode**.

## Steg 2 – Välj ett återställningsläge (Primär H2 med nyckelord)

### Återställ korrupt dokument – Ställ in rätt återställningsläge

Aspose.Words erbjuder tre återställningsbeteenden:

| Läge | Vad händer | När att använda |
|------|------------|-----------------|
| **PromptUser** | Visar en dialog (eller så kan du implementera din egen prompt) och försöker reparera filen. | Idealiskt för interaktiva verktyg där användaren kan bestämma. |
| **Silent** | Försöker reparera automatiskt, utan UI. | Bra för batchjobb eller tjänster. |
| **ThrowException** | Stoppar bearbetning och kastar ett undantag. | Använd när du vill ha strikt validering. |

Nedan visas hur du **set recovery mode** till `PromptUser`. Om du föredrar tyst hantering, byt bara enum‑värdet.

```csharp
// Step 2: Configure LoadOptions with the desired recovery mode
LoadOptions loadOptions = new LoadOptions
{
    // Choose one of: RecoveryMode.PromptUser, RecoveryMode.Silent, RecoveryMode.ThrowException
    RecoveryMode = RecoveryMode.PromptUser
};
```

**Varför detta är viktigt:** Genom att explicit **set recovery mode** talar du om för Aspose.Words hur aggressiv den ska vara. Standard är `PromptUser`, men att vara explicit gör din avsikt kristallklar—både för framtida underhållare och för sökmotorer som genomsöker koden.

## Steg 3 – Ladda DOCX med återställning

Nu ska vi **load docx with recovery** med hjälp av `LoadOptions` som vi just konfigurerade. Om filen är skadad kommer Aspose.Words antingen att reparera den eller ge en varning, beroende på läget.

```csharp
// Step 3: Load the potentially corrupted DOCX
string filePath = @"C:\Temp\corrupt.docx"; // adjust to your environment
Document document;

try
{
    document = new Document(filePath, loadOptions);
}
catch (Exception ex)
{
    Console.WriteLine($"Failed to load document: {ex.Message}");
    // If you used ThrowException mode, you'll end up here.
    return;
}
```

`Document`‑konstruktorn gör det tunga arbetet. I **PromptUser**‑läge ser du en konsolprompt (eller en anpassad UI om du kopplar in dig på `LoadOptions`‑händelserna) som frågar om du vill fortsätta. I **Silent**‑läge försöker metoden bara så gott den kan och går vidare.

## Steg 4 – Inspektera varningar och fråga användaren

Aspose.Words registrerar alla problem den stöter på i samlingen `Warnings`. Låt oss iterera över dem och ge användaren en chans att bestämma vad som ska göras härnäst.

```csharp
// Step 4: Examine any warnings generated during loading
if (document.Warnings.Count > 0)
{
    Console.WriteLine("The following warnings were detected while loading the document:");
    foreach (WarningInfo warning in document.Warnings)
    {
        Console.WriteLine($"- {warning.Source}: {warning.Description}");
    }

    // Simple prompt – you can replace this with a GUI dialog if you prefer
    Console.Write("Do you want to continue processing this document? (y/n): ");
    string response = Console.ReadLine()?.Trim().ToLowerInvariant();

    if (response != "y")
    {
        Console.WriteLine("Operation aborted by the user.");
        return;
    }
}
else
{
    Console.WriteLine("Document loaded without any warnings.");
}
```

Kodsnutten ovan **prompt user on error** på ett konsolvänligt sätt. Om du bygger en Windows Forms‑ eller WPF‑app, byt ut `Console.ReadLine` mot en `MessageBox` eller en anpassad dialog.

## Steg 5 – Arbeta med det återställda dokumentet

Vid den här tidpunkten finns dokumentet i minnet, reparerat så gott som Aspose.Words kan. Du kan nu läsa dess innehåll, spara en ren kopia eller utföra vilken manipulation du behöver.

```csharp
// Example: Save a clean copy next to the original
string cleanPath = System.IO.Path.Combine(
    System.IO.Path.GetDirectoryName(filePath)!,
    "clean_copy.docx");

document.Save(cleanPath);
Console.WriteLine($"Clean copy saved to: {cleanPath}");
```

Att köra hela programmet mot en trasig fil kommer att producera konsolutdata liknande detta:

```
The following warnings were detected while loading the document:
- Document: The file contains an unexpected end tag.
Do you want to continue processing this document? (y/n): y
Clean copy saved to: C:\Temp\clean_copy.docx
```

Om filen faktiskt var i ordning kommer du att se “Document loaded without any warnings.” och den rena kopian kommer att vara identisk med källan.

## Fullt fungerande exempel

Här är hela programmet på ett ställe. Kopiera‑klistra in det i ett nytt konsolprojekt och tryck **F5**.

```csharp
// RecoverCorruptedDocument.cs
using System;
using Aspose.Words;
using Aspose.Words.Loading;

class RecoverCorruptedDocument
{
    static void Main()
    {
        // 1️⃣ Configure recovery mode
        LoadOptions loadOptions = new LoadOptions
        {
            RecoveryMode = RecoveryMode.PromptUser // alternatives: Silent, ThrowException
        };

        // 2️⃣ Path to the possibly corrupted DOCX
        string filePath = @"C:\Temp\corrupt.docx";

        // 3️⃣ Attempt to load the document
        Document document;
        try
        {
            document = new Document(filePath, loadOptions);
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
            return;
        }

        // 4️⃣ Show warnings and ask the user what to do
        if (document.Warnings.Count > 0)
        {
            Console.WriteLine("The following warnings were detected while loading the document:");
            foreach (WarningInfo warning in document.Warnings)
            {
                Console.WriteLine($"- {warning.Source}: {warning.Description}");
            }

            Console.Write("Do you want to continue processing this document? (y/n): ");
            string response = Console.ReadLine()?.Trim().ToLowerInvariant();

            if (response != "y")
            {
                Console.WriteLine("Operation aborted by the user.");
                return;
            }
        }
        else
        {
            Console.WriteLine("Document loaded without any warnings.");
        }

        // 5️⃣ Save a clean copy
        string cleanPath = System.IO.Path.Combine(
            System.IO.Path.GetDirectoryName(filePath)!,
            "clean_copy.docx");

        document.Save(cleanPath);
        Console.WriteLine($"Clean copy saved to: {cleanPath}");
    }
}
```

Kör det, förstöra en testfil och se återställningen i aktion. 🎉

## Kantfall & variationer

| Scenario | Vad som ska ändras | Varför |
|----------|--------------------|--------|
| **Batch processing** (ingen användarinteraktion) | Sätt `RecoveryMode = RecoveryMode.Silent` och ta bort konsolprompten. | Håller pipeline igång automatiskt. |
| **Strict validation** (fail fast) | Använd `RecoveryMode.ThrowException`. Omslut laddningsanropet i en try/catch och logga undantaget. | Garanterar att du aldrig arbetar med en delvis reparerad fil. |
| **Custom UI** (WinForms/WPF) | Prenumerera på `LoadOptions.LoadingProgress` eller använd `Document.LoadOptions`‑händelser för att visa en dialog. | Ger en rikare upplevelse än konsolen. |
| **Large documents** (minnesbegränsningar) | Ladda med `LoadOptions.LoadFormat = LoadFormat.Docx` och överväg `Document.SaveOptions` för att strömma utdata. | Förhindrar OutOfMemory‑undantag. |

## Praktiska tips (E‑E‑A‑T‑signaler)

- **Behåll alltid en backup** innan du försöker återställa; processen kan skriva över delar av filen.  
- **Logga varningar** till en fil för senare analys; de ger ofta en ledtråd till grundorsaken (t.ex. saknade delar, korrupt XML).  
- **Testa med flera korrupta typer** – trunkera filen, förstöra XML‑taggar eller ändra zip‑strukturen för att se hur varje läge beter sig.  
- **Uppgradera Aspose.Words regelbundet**; nyare versioner förbättrar återställningsalgoritmer och lägger till nya varningstyper.  
- **Kombinera med validering** – efter återställning, kör snabbt `document.UpdateFields()` och `document.Save()` för att säkerställa att dokumentet är fullt funktionellt.

## Slutsats

Du vet nu hur du **recover corrupted document**‑filer i C# genom att **set recovery mode**, **load docx with recovery**, och **prompt user on error** när något går fel. Det fullständiga exemplet visar ett rent, end‑to‑end‑flöde som fungerar i konsolappar, tjänster eller UI‑projekt.

Nästa steg? Prova att byta ut konsolprompten mot en modal dialog i en WinForms‑app, experimentera med **Silent**‑läget för bakgrundsjobb, eller integrera återställningslogiken i en ASP.NET‑filuppladdnings‑endpoint så att användare kan ladda upp trasiga DOCX‑filer och omedelbart få en reparerad version.

Lycka till med kodningen, och må dina dokument förbli hela!  

---

![Recover corrupted document example](/images/recover-corrupted-document.png "recover corrupted document")

---

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}