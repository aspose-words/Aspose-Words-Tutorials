---
category: general
date: 2026-03-30
description: hoe waarschuwingen vast te leggen bij het laden van een DOCX‑bestand
  – leer ontbrekende lettertypen te detecteren, lettertype‑instellingen te configureren
  en laadopties in C# in te stellen
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- configure font settings
- handle missing fonts
- set load options
language: nl
og_description: hoe waarschuwingen vast te leggen tijdens het laden van een DOCX‑bestand
  – stapsgewijze handleiding om ontbrekende lettertypen te detecteren en lettertype‑instellingen
  te configureren in C#
og_title: hoe waarschuwingen vast te leggen – configureer laadopties voor ontbrekende
  lettertypen
tags:
- Aspose.Words
- C#
- Font management
title: waarschuwingen vastleggen – laadopties configureren voor ontbrekende lettertypen
url: /nl/net/programming-with-loadoptions/how-to-capture-warnings-configure-load-options-for-missing-f/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# waarschuwingen vastleggen – laadopties configureren voor ontbrekende lettertypen

Heb je je ooit afgevraagd **hoe je waarschuwingen kunt vastleggen** die verschijnen wanneer een document een lettertype probeert te gebruiken dat je niet geïnstalleerd hebt? Het is een scenario dat veel ontwikkelaars die met Word‑verwerkingsbibliotheken werken, in de war brengt, vooral wanneer je **ontbrekende lettertypen moet detecteren** voordat ze je PDF‑exportpipeline breken.  

In deze tutorial laten we je een praktische, kant‑klaar oplossing zien die **fontinstellingen configureert**, **load options instelt**, en elke substitutiewaarschuwing naar de console print. Aan het einde weet je precies hoe je **ontbrekende lettertypen** kunt **afhandelen** op een manier die je applicatie robuust houdt en je gebruikers tevreden maakt.

## Wat je zult leren

- Hoe je **load options kunt instellen** zodat de bibliotheek fontproblemen meldt in plaats van ze stilletjes te vervangen.
- De exacte stappen om **fontinstellingen te configureren** voor het vastleggen van waarschuwingen.
- Manieren om **ontbrekende lettertypen** programmatisch te **detecteren** en dienovereenkomstig te reageren.
- Een volledige, copy‑paste C#‑voorbeeld dat werkt met de nieuwste Aspose.Words for .NET (v24.10 op het moment van schrijven).
- Tips om de oplossing uit te breiden om waarschuwingen te loggen, terug te vallen op aangepaste lettertypen, of de verwerking af te breken wanneer kritieke lettertypen ontbreken.

> **Voorvereiste:** Je moet het Aspose.Words for .NET NuGet‑pakket geïnstalleerd hebben (`Install-Package Aspose.Words`). Geen andere externe afhankelijkheden zijn vereist.

---

## Stap 1: Namespaces importeren en het project voorbereiden

Eerst voeg je de essentiële `using`‑directives toe. Dit is niet zomaar boilerplate; het vertelt de compiler waar `LoadOptions`, `FontSettings` en `Document` zich bevinden.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

> **Pro tip:** Als je .NET 6+ gebruikt, kun je *global using*‑statements inschakelen om te voorkomen dat je deze regels in elk bestand moet herhalen.

---

## Stap 2: Load options instellen en waarschuwingen voor lettertype‑substitutie inschakelen

De kern van **hoe je waarschuwingen kunt vastleggen** ligt in het `LoadOptions`‑object. Door een nieuwe `FontSettings`‑instantie te maken en een event‑handler aan `SubstitutionWarning` te koppelen, vertel je de bibliotheek elke keer te roepen wanneer een gevraagd lettertype niet gevonden kan worden.

```csharp
// Step 2: Create LoadOptions and turn on warning notifications
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Subscribe to the warning event – this is where we actually capture them
loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    // The warning message includes the missing font name and the fallback that was used
    Console.WriteLine($"[Font warning] {e.Message}");
};
```

**Waarom dit belangrijk is:** Zonder de event‑abonnement valt Aspose.Words stilletjes terug op een standaardlettertype, en je weet nooit welke glyphs zijn vervangen. Door te luisteren naar `SubstitutionWarning` krijg je een volledige audit‑trail – cruciaal voor omgevingen met strenge compliance‑eisen.

---

## Stap 3: Het document laden met de geconfigureerde opties

Nu de waarschuwingen zijn aangesloten, laad je je DOCX (of een ander ondersteund formaat) met de `loadOptions` die je zojuist hebt voorbereid. De `Document`‑constructor activeert de font‑controlelogica meteen.

```csharp
// Step 3: Load a document that intentionally references a missing font
string filePath = @"C:\Docs\WithMissingFonts.docx";   // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

Als het bestand bijvoorbeeld *“Comic Sans MS”* verwijst op een machine die alleen *“Arial”* heeft, zie je iets als:

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
```

Die regel wordt rechtstreeks naar de console geprint vanwege de handler die we eerder hebben toegevoegd.

---

## Stap 4: Vastgelegde waarschuwingen verifiëren en erop reageren

Waarschuwingen vastleggen is slechts de helft van de strijd; je moet vaak beslissen wat je vervolgens doet. Hieronder een snel patroon dat waarschuwingen in een lijst opslaat voor latere analyse – perfect als je ze naar een bestand wilt loggen of de import wilt afbreken wanneer een kritisch lettertype ontbreekt.

```csharp
using System.Collections.Generic;

List<string> warningLog = new List<string>();

loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
{
    string msg = $"[Font warning] {e.Message}";
    Console.WriteLine(msg);
    warningLog.Add(msg);
};

// Load the document (same as Step 3)
Document doc = new Document(filePath, loadOptions);

// Example decision: abort if any warning mentions "Times New Roman"
bool hasCriticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
if (hasCriticalMissing)
{
    Console.WriteLine("Critical font missing – aborting processing.");
    // You could throw, return an error code, etc.
}
else
{
    Console.WriteLine("Document loaded successfully with acceptable font fallbacks.");
}
```

**Afhandeling van randgevallen:**  
- **Meerdere ontbrekende lettertypen:** De lijst bevat één item per substitutie, zodat je kunt itereren en een gedetailleerd rapport kunt opstellen.  
- **Aangepaste fallback-lettertypen:** Als je eigen lettertype‑bestanden hebt, voeg ze toe aan `FontSettings` vóór het laden: `fontSettings.SetFontsFolder(@"C:\MyFonts", true);`. De waarschuwingen zullen dan de aangepaste fallback tonen in plaats van de systeemstandaard.  

---

## Stap 5: Volledig werkend voorbeeld (klaar om te copy‑pasten)

Alles bij elkaar, hier is een zelfstandige console‑app die je nu kunt compileren en uitvoeren.

```csharp
// Full example – how to capture warnings while loading a DOCX file
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare load options and enable warning events
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        List<string> warningLog = new List<string>();
        loadOptions.FontSettings.SubstitutionWarning += (sender, e) =>
        {
            string msg = $"[Font warning] {e.Message}";
            Console.WriteLine(msg);
            warningLog.Add(msg);
        };

        // 2️⃣ (Optional) Point to a folder with custom fonts if you have any
        // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

        // 3️⃣ Load the document – this triggers the warning capture
        string filePath = @"C:\Docs\WithMissingFonts.docx"; // change as needed
        Document doc = new Document(filePath, loadOptions);

        // 4️⃣ React to the captured warnings
        bool criticalMissing = warningLog.Exists(w => w.Contains("Times New Roman"));
        if (criticalMissing)
        {
            Console.WriteLine("Critical font missing – aborting further processing.");
            // exit or throw as appropriate
            return;
        }

        Console.WriteLine("Document loaded – all fonts accounted for (or safely substituted).");
        // Continue with your processing (e.g., save as PDF, manipulate, etc.)
    }
}
```

**Verwachte console‑output** (wanneer de DOCX een ontbrekend lettertype verwijst):

```
[Font warning] Font "Comic Sans MS" is missing. Substituted with "Arial".
Document loaded – all fonts accounted for (or safely substituted).
```

Als een *kritiek* lettertype zoals “Times New Roman” ontbreekt, zie je in plaats daarvan het abort‑bericht.

---

## Veelgestelde vragen & valkuilen

| Vraag | Antwoord |
|----------|--------|
| **Moet ik `SetFontsFolder` aanroepen om waarschuwingen vast te leggen?** | Nee. Het waarschuwings‑event werkt met de standaard systeemlettertypen. Gebruik `SetFontsFolder` alleen wanneer je extra fallback‑lettertypen wilt bieden. |
| **Werkt dit op .NET Core / .NET 5+?** | Absoluut. Aspose.Words 24.10 ondersteunt alle moderne .NET‑runtime‑omgevingen. Zorg er alleen voor dat het NuGet‑pakket overeenkomt met je doel‑framework. |
| **Wat als ik waarschuwingen naar een bestand wil loggen in plaats van naar de console?** | Vervang `Console.WriteLine(msg);` door een aanroep van een logging‑framework, bijv. `File.AppendAllText("font_warnings.log", msg + Environment.NewLine);`. |
| **Kan ik waarschuwingen voor specifieke lettertypen onderdrukken?** | Ja. Binnen de event‑handler kun je filteren: `if (e.FontName == "SomeFont") return;`. Dit geeft fijnmazige controle. |
| **Is er een manier om ontbrekende lettertypen als fouten te behandelen?** | Gooi handmatig een uitzondering in de handler wanneer aan een voorwaarde wordt voldaan, of zet een vlag en breek af na de `Document`‑constructie zoals getoond in het voorbeeld. |

---

## Conclusie

Je hebt nu een solide, productie‑klaar patroon voor **hoe je waarschuwingen kunt vastleggen** die optreden bij het laden van documenten met ontbrekende lettertypen. Door **ontbrekende lettertypen te detecteren**, **fontinstellingen te configureren** en **load options** correct in te stellen, krijg je volledige zichtbaarheid op font‑substitutie‑events en kun je beslissen of je ze logt, een fallback gebruikt, of de verwerking afbreekt.  

Neem de volgende stap door deze logica in je PDF‑conversiepijplijn te integreren, aangepaste fallback‑lettertypen toe te voegen, of de waarschuwingslijst in een monitoringsysteem te voeren. De aanpak schaalt van kleine hulpprogramma’s tot enterprise‑grade documentverwerkingsservices.

---

### Verdere lectuur & volgende stappen

- **Verken meer FontSettings‑functies** – het insluiten van aangepaste lettertypen, het regelen van de fallback‑volgorde, en licentie‑overwegingen.  
- **Combineer met PDF‑conversie** – na het vastleggen van waarschuwingen roep je `doc.Save("output.pdf");` aan en controleer je of de PDF de verwachte lettertypen gebruikt.  
- **Automatiseer testen** – schrijf unit‑tests die documenten laden met bekende ontbrekende lettertypen en controleer dat de waarschuwingslijst de verwachte berichten bevat.  

Als je tegen problemen aanloopt of ideeën hebt voor verbetering, laat dan gerust een reactie achter. Happy coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}