---
category: general
date: 2026-01-10
description: Lär dig hur du använder LoadOptions för att hantera saknade teckensnitt
  i Aspose.Words. Steg‑för‑steg‑kod, tips och bästa praxis för robust dokumentladdning.
draft: false
keywords:
- how to use loadoptions
- handle missing fonts
- Aspose.Words warning callback
- font substitution handling
- document loading options
language: sv
og_description: Hur du använder LoadOptions för att hantera saknade teckensnitt i
  Aspose.Words. Få ett komplett, körbart exempel med förklaringar och praktiska tips.
og_title: Hur man använder LoadOptions i Aspose.Words – Komplett guide
tags:
- Aspose.Words
- C#
- .NET
title: Så använder du LoadOptions i Aspose.Words – Komplett guide
url: /sv/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man använder LoadOptions i Aspose.Words – Komplett guide

Har du någonsin funderat **hur man använder LoadOptions** när du laddar ett Word‑dokument som kanske saknar vissa teckensnitt? Du är inte ensam som kliar dig i huvudet över detta. I många verkliga projekt färdas dokument mellan maskiner, och målsystemet saknar ofta exakt de typsnitt som författaren använde. Resultatet? Oväntade teckensnittssubstitutioner som kan förstöra layouten, dölja viktiga tecken eller helt enkelt se felaktiga ut.  

Lyckligtvis ger Aspose.Words oss ett rent sätt att *hantera saknade teckensnitt* genom att exponera ett `LoadOptions`‑objekt med en varnings‑callback. I den här handledningen lär du dig exakt **hur man använder LoadOptions** för att fånga dessa teckensnittssubstitutionsvarningar, logga dem och hålla din bearbetningspipeline robust.

Vi kommer att gå igenom:

* Att skapa varnings‑callback‑klassen  
* Att konfigurera `LoadOptions` med den callback‑en  
* Att ladda ett dokument samtidigt som man spårar saknade teckensnitt  
* Tips för felsökning och utökning av lösningen  

Ingen extern dokumentation behövs – allt du behöver finns här.

---

## Vad du behöver

Innan vi dyker ner, se till att du har:

* **Aspose.Words for .NET** (senaste versionen 2026) installerad via NuGet  
* En .NET‑utvecklingsmiljö (Visual Studio, Rider eller VS Code)  
* Ett exempel‑DOCX som refererar till ett teckensnitt du inte har installerat (vi kallar det `input.docx`)  

Det är allt – inga extra bibliotek krävs.

---

## Steg 1 – Definiera en varnings‑callback för att fånga teckensnittssubstitution

Den första delen av pusslet är en klass som implementerar `IWarningCallback`. Aspose.Words kommer att anropa dess `Warning`‑metod när den stöter på något anmärkningsvärt – som ett saknat teckensnitt.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Custom warning handler that prints font‑substitution messages to the console.
/// </summary>
class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution detected: {info.Description}");
        }
    }
}
```

**Varför detta är viktigt:**  
Genom att filtrera på `WarningType.FontSubstitution` undviker du skräp från orelaterade varningar (t.ex. föråldrade funktioner). Callback‑en ger dig full kontroll – du kan logga till en fil, kasta ett undantag eller till och med försöka bädda in ett reservteckensnitt programatiskt.

---

## Steg 2 – Konfigurera LoadOptions med callback‑en

Nu när vi har en hanterare måste vi tala om för Aspose.Words att använda den. Här ser du **hur man använder LoadOptions** i praktiken.

```csharp
// Create a LoadOptions instance and attach our custom callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningCallback()
};
```

**Tips:** `LoadOptions` erbjuder många andra växlar (t.ex. `Password`, `LoadFormat`, `Encoding`). Du kan kedja dem tillsammans, men för att hantera saknade teckensnitt är `WarningCallback` stjärnan i showen.

---

## Steg 3 – Ladda dokumentet med de konfigurerade alternativen

Med `LoadOptions` redo är det enkelt att ladda dokumentet. Aspose.Words kommer automatiskt att anropa callback‑en för varje teckensnitt den inte kan hitta.

```csharp
// Path to the DOCX that may reference unavailable fonts.
string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

// Load the document while the warning callback monitors font issues.
Document doc = new Document(docPath, loadOptions);

// At this point you can continue processing the document—saving, editing, etc.
Console.WriteLine("✅ Document loaded successfully.");
```

**Förväntad utskrift:**  

Om `input.docx` använder ett teckensnitt som heter *“GothicBold”* som inte är installerat, kommer du att se något i stil med:

```
⚠️ Font substitution detected: Font substitution applied. Original font: GothicBold, Substituted font: Arial.
✅ Document loaded successfully.
```

Varningsraden visas **exakt när det saknade teckensnittet påträffas**, vilket ger dig omedelbar återkoppling.

---

## Steg 4 – (Valfritt) Fortsätt bearbeta dokumentet

Vanligtvis vill du göra mer än bara ladda filen. Nedan följer några vanliga efter‑laddningsåtgärder som fungerar sömlöst med vår varningsinställning.

### 4.1 Spara dokumentet som PDF

```csharp
// Convert to PDF – the substituted fonts are already baked into the layout.
doc.Save("output.pdf", SaveFormat.Pdf);
Console.WriteLine("📄 PDF saved as output.pdf");
```

### 4.2 Ersätt saknade teckensnitt med ett känt reservteckensnitt

Om du föredrar ett specifikt reservteckensnitt (t.ex. *“Calibri”*), kan du justera `FontSettings` innan du sparar:

```csharp
var fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
    "GothicBold", new[] { "Calibri", "Arial" });

doc.FontSettings = fontSettings;
doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
Console.WriteLine("🔄 PDF saved with explicit fallback fonts.");
```

### 4.3 Logga alla varningar till en fil

```csharp
class FileLoggingWarningCallback : IWarningCallback
{
    private readonly string _logPath = "load-warnings.log";

    public void Warning(WarningInfo info)
    {
        File.AppendAllText(_logPath,
            $"{DateTime.Now:u} - {info.WarningType}: {info.Description}{Environment.NewLine}");
    }
}

// Use it:
var loadOptionsWithFileLog = new LoadOptions
{
    WarningCallback = new FileLoggingWarningCallback()
};
```

Dessa kodsnuttar illustrerar **hur man använder LoadOptions** bortom det grundläggande fallet och ger dig flexibilitet för produktionsklara lösningar.

---

## Vanliga fallgropar & hur man **hanterar saknade teckensnitt** på ett smidigt sätt

| Fallgrop | Varför det händer | Hur man åtgärdar / mildrar |
|----------|-------------------|----------------------------|
| **Ingen callback kopplad** | Du glömmer att sätta `WarningCallback`. | Skapa alltid en `LoadOptions`‑instans och tilldela din handler innan du laddar. |
| **Callback bara skriver ut, aldrig sparar** | I en webbtjänst försvinner konsolutskriften. | Byt ut `Console.WriteLine` mot en logger (Serilog, NLog) eller skriv till ett beständigt lagringsmedium. |
| **Flera saknade teckensnitt, bara det första rapporteras** | Din callback kastar ett undantag vid den första varningen. | Håll callback‑en lättviktig; undvik att kasta om du inte verkligen vill avbryta. |
| **Ersatt teckensnitt ser fel ut** | Standardsubstitutionen kan välja ett visuellt olikartat teckensnitt. | Använd `FontSettings.SubstitutionSettings.FontSubstitutionRules` för att prioritera ditt föredragna reservteckensnitt. |
| **Prestandapåverkan på stora dokument** | Varnings‑callback anropas tusentals gånger. | Samla varningar i en lista och bearbeta efter laddning, eller filtrera bara unika teckensnittsnamn. |

Att vara medveten om dessa scenarier hjälper dig att **hantera saknade teckensnitt** utan överraskningar.

---

## Fullt fungerande exempel – Alla bitar ihop

Nedan är det kompletta, färdiga programmet som demonstrerar hela flödet. Kopiera‑klistra in i ett konsolprojekt, lägg till Aspose.Words‑NuGet‑paketet, så fungerar det direkt.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCallback : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions with our warning handler.
        var loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCallback()
        };

        // 2️⃣ Path to the source DOCX.
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        // 3️⃣ Load the document – any missing fonts trigger our callback.
        Document doc = new Document(sourcePath, loadOptions);
        Console.WriteLine("✅ Document loaded.");

        // 4️⃣ Optional: Save as PDF to see the final appearance.
        string pdfPath = Path.Combine(Environment.CurrentDirectory, "output.pdf");
        doc.Save(pdfPath, SaveFormat.Pdf);
        Console.WriteLine($"📄 PDF saved to {pdfPath}");

        // 5️⃣ (Bonus) Set explicit fallback font for a known missing font.
        var fontSettings = new FontSettings();
        fontSettings.SubstitutionSettings.FontSubstitutionRules.AddSubstitutes(
            "GothicBold", new[] { "Calibri", "Arial" });
        doc.FontSettings = fontSettings;
        doc.Save("output-with-fallback.pdf", SaveFormat.Pdf);
        Console.WriteLine("🔄 PDF with explicit fallback saved.");
    }
}
```

**När du kör programmet** kommer det att:

1. Skriva eventuella teckensnittssubstitutionsvarningar till konsolen.  
2. Spara den ursprungliga layouten som `output.pdf`.  
3. Spara en andra PDF (`output-with-fallback.pdf`) som tvingar reservteckensnittet till *Calibri* eller *Arial*.

---

## Vanliga frågor (FAQ)

**Q: Fungerar detta för DOC, RTF eller HTML‑filer?**  
A: Ja. `LoadOptions` är format‑agnostiskt; så länge du anger rätt filsökväg kommer varnings‑callbacken att triggas för saknade teckensnitt i alla stödda format.

**Q: Kan jag undertrycka varningarna helt?**  
A: Du kan tilldela en ingen‑gör‑callback (`new IWarningCallback { Warning = _ => {} }`) eller sätta `LoadOptions.WarningCallback = null`. Men att förlora synligheten innebär att du kan missa kritiska teckensnittsproblem.

**Q: Vad om jag behöver ersätta saknade teckensnitt med inbäddade?**  
A: Använd `FontSettings` för att bädda in ett ersättningsteckensnitt (`AddFontSource`). Kombinera detta med substitutionsreglerna för en sömlös upplevelse.

**Q: Är callback‑en trådsäker?**  
A: Callback‑en kan anropas från flera trådar när stora dokument laddas parallellt. Säkerställ att delade resurser (t.ex. loggfiler) är synkroniserade.

---

## Slutsats

Vi har gått igenom **hur man använder LoadOptions** i Aspose.Words för att **hantera saknade teckensnitt** på ett elegant sätt. Genom att definiera en anpassad `IWarningCallback`, fästa den på ett `LoadOptions`‑objekt och ladda ditt dokument med den konfigurationen får du insikt i realtid om alla teckensnittssubstitutionshändelser. Därefter kan du logga, ersätta eller bädda in reservteckensnitt för att hålla ditt resultat exakt som avsett.

Kom ihåg de viktigaste stegen:

1. Implementera en varnings‑callback som fokuserar på `WarningType.FontSubstitution`.  
2. Koppla callback‑en till ett `LoadOptions`‑objekt.  
3. Ladda ditt dokument med dessa alternativ.  
4. (Valfritt) Applicera ytterligare teckensnittssubstitutionsregler eller loggning efter behov.

Känn dig fri att experimentera – byt ut konsolloggern mot en strukturerad logger, lägg till e‑postvarningar för kritiska saknade teckensnitt, eller integrera detta mönster i en större dokument‑bearbetningspipeline. Metoden skalar bra oavsett om du hanterar en enda fil eller bearbetar tusentals i ett batchjobb.

Lycka till med kodandet, och må dina dokument alltid renderas med rätt teckensnitt!  

---

![how to use loadoptions example]

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}