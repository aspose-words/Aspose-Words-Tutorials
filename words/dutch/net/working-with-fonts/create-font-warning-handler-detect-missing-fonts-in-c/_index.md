---
category: general
date: 2026-02-12
description: Maak een lettertype‑waarschuwinghandler om ontbrekende lettertypen te
  detecteren en bij te houden in Aspose.Words. Leer hoe je waarschuwingen efficiënt
  kunt loggen.
draft: false
keywords:
- create font warning handler
- detect missing fonts
- track missing fonts
- how to log warnings
language: nl
og_description: Maak een lettertype‑waarschuwingshandler in C# om ontbrekende lettertypen
  te detecteren en leer hoe u waarschuwingen kunt loggen wanneer Aspose.Words lettertypen
  vervangt.
og_title: Maak Lettertype‑waarschuwingshandler – Detecteer ontbrekende lettertypen
tags:
- Aspose.Words
- C#
- Document Processing
title: Maak Font‑waarschuwingshandler – Detecteer ontbrekende lettertypen in C#
url: /nl/net/working-with-fonts/create-font-warning-handler-detect-missing-fonts-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Font Warning Handler – Detecteer Ontbrekende Lettertypen in C#

Heb je ooit een **create font warning handler** moeten maken omdat een Word‑document stilletjes een lettertype vervangt dat je niet verwachtte? Je bent niet de enige. Wanneer Aspose.Words een DOCX laadt die verwijst naar een lettertype dat niet op de server aanwezig is, valt het stilletjes terug op een standaardlettertype—waardoor je lay‑out subtiel kapot gaat.  

In deze tutorial laten we je precies zien hoe je **detect missing fonts**, **track missing fonts**, en **how to log warnings** kunt uitvoeren zodat je die substituties kunt opsporen voordat ze je problemen bezorgen. Aan het einde heb je een herbruikbare warning handler die elk font‑substitution‑event naar de console (of elke logger die je verkiest) print. Geen mysterie, alleen duidelijke, bruikbare code.

## Vereisten

- .NET 6.0 of later (de API is hetzelfde voor .NET Framework 4.6+)
- Aspose.Words for .NET geïnstalleerd (`dotnet add package Aspose.Words`)
- Een Word‑bestand dat verwijst naar een lettertype dat niet op je machine geïnstalleerd is (bijv. `MissingFont.docx`)

Als je die al hebt, prima—laten we beginnen.

## Stap 1: LoadOptions instellen met een Warning Callback  

Het eerste dat je doet wanneer je een **create font warning handler** wilt maken is Aspose.Words vertellen een callback te activeren telkens wanneer het een probleem tegenkomt. `LoadOptions` is de container voor die configuratie.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

// Create LoadOptions and attach our custom handler
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

**Waarom dit belangrijk is:**  
`LoadOptions` is de enige plek waar je een `IWarningCallback` kunt aansluiten. Zonder dit zal Aspose.Words waarschuwingen intern loggen, maar je zult ze nooit zien. Door `FontWarningHandler` toe te wijzen krijgen we volledige controle over wat er gebeurt wanneer een ontbrekend lettertype wordt vervangen.

## Stap 2: De FontWarningHandler‑klasse implementeren  

Nu maken we daadwerkelijk de **create font warning handler**‑code. De klasse implementeert `IWarningCallback` en ontvangt een `WarningInfo`‑object voor elke waarschuwing die Aspose.Words geeft.

```csharp
// Step 2: Implement the warning handler that logs substitution details.
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.Type == WarningType.FontSubstitution)
        {
            // This is where we **track missing fonts** and **how to log warnings**
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Uitleg:**  
- `info.Type` vertelt ons de categorie van de waarschuwing. We zijn geïnteresseerd in `WarningType.FontSubstitution` omdat dat aangeeft dat een lettertype ontbreekt.  
- `info.Description` bevat een mens‑leesbare boodschap zoals *“Font 'Comic Sans MS' was not found. Substituted with 'Arial'.”*  
- Door naar `Console.WriteLine` te schrijven **log warnings** direct. In een echte applicatie kun je dat vervangen door `ILogger`, een bestandswriter, of een telemetrie‑service.

> **Pro tip:** Als je alle ontbrekende lettertypen later wilt rapporteren, sla `info.Description` op in een `List<string>` in plaats van het af te drukken.

## Stap 3: Het document laden met de geconfigureerde LoadOptions  

Met de callback ingesteld, zal het laden van een document automatisch onze handler activeren telkens wanneer een lettertype ontbreekt.

```csharp
// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Wat je zult zien:**  
Het uitvoeren van het programma print iets vergelijkbaars met:

```
Font substitution detected: Font 'Papyrus' was not found. Substituted with 'Times New Roman'.
```

Die regel bevestigt dat je met succes **detected missing fonts** hebt uitgevoerd en nu **track missing fonts** in realtime.

## Stap 4: Verifieer dat de handler werkt met verschillende scenario's  

Het is gemakkelijk aan te nemen dat de handler alleen werkt voor DOCX‑bestanden, maar Aspose.Words ondersteunt veel formaten. Probeer een PDF te laden die verwijst naar een ingebed lettertype, of een ouder `.doc`‑bestand. Dezelfde callback wordt geactiveerd voor elk formaat dat door de font‑resolutie‑pipeline gaat.

```csharp
// Loading a PDF that uses an unavailable font
Document pdfDoc = new Document("MissingFont.pdf", loadOptions);
```

Als de PDF een lettertype verwijst dat niet geïnstalleerd is, krijg je dezelfde console‑output. Dit toont aan dat jouw **create font warning handler**‑oplossing formaat‑agnostisch is.

## Stap 5: De handler uitbreiden – Loggen naar een bestand  

Console‑output is handig voor demo's, maar productcode schrijft meestal naar een logbestand. Hier is een snelle aanpassing.

```csharp
using System.IO;

class FontWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] {info.Description}";
            // Append to the log file
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}
```

Nu wordt elke keer dat een lettertype wordt vervangen, het bericht toegevoegd aan `font-warnings.log`. Dit voldoet aan het **how to log warnings**‑deel van de opdracht en geeft je een blijvend audit‑pad.

## Stap 6: Alles samenvoegen – Volledig, uitvoerbaar voorbeeld  

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een console‑applicatie. Er ontbreken geen onderdelen; vervang alleen het bestandspad door je eigen document.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warnings;

namespace FontWarningDemo
{
    // Step 2: Implement the warning handler
    class FontWarningHandler : IWarningCallback
    {
        private readonly string _logPath = "font-warnings.log";

        public void Warning(WarningInfo info)
        {
            if (info.Type == WarningType.FontSubstitution)
            {
                string message = $"[{DateTime.Now}] {info.Description}";
                Console.WriteLine(message);               // Immediate feedback
                File.AppendAllText(_logPath, message + Environment.NewLine);
            }
        }
    }

    class Program
    {
        static void Main()
        {
            // Step 1: Configure LoadOptions with our handler
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = new FontWarningHandler()
            };

            // Step 3: Load a document that likely has missing fonts
            string docPath = @"YOUR_DIRECTORY\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // Optional: Do something with the document (e.g., save as PDF)
            doc.Save("output.pdf");
            Console.WriteLine("Document processed. Check console and font-warnings.log for any font substitutions.");
        }
    }
}
```

**Verwacht resultaat:**  

- De console print elke substitutielijn.  
- `font-warnings.log` bevat nu een tijdstempel‑record van elk ontbrekend‑lettertype‑event.  
- Het `output.pdf`‑bestand wordt aangemaakt met de vervangen lettertypen, waardoor de conversie slaagt zelfs wanneer de originele lettertypen niet beschikbaar zijn.

## Veelgestelde vragen & randgevallen  

| Vraag | Antwoord |
|----------|--------|
| *Wat als ik bepaalde lettertypen wil negeren?* | Binnen `Warning` controleer je `info.Description` op de lettertype‑naam en `return;` vroegtijdig voor lettertypen die je acceptabel vindt. |
| *Wordt de handler geactiveerd voor ingebedde lettertypen?* | Nee—ingebedde lettertypen zijn altijd beschikbaar voor het document, dus er treedt geen substitutie‑waarschuwing op. |
| *Kan ik andere waarschuwings‑types vastleggen (bijv. image‑resolution issues)?* | Zeker. Verwijder de `if (info.Type == WarningType.FontSubstitution)` guard of voeg extra `if`‑blokken toe voor `WarningType.ImageResolution`. |
| *Is de handler thread‑safe?* | De getoonde standaardimplementatie schrijft naar een bestand zonder synchronisatie. Voor multi‑threaded scenario's, wikkel bestands‑schrijvingen in een lock of gebruik een concurrent logger. |

## Volgende stappen  

Nu je weet **how to log warnings** voor ontbrekende lettertypen, wil je misschien:

- **Detect missing fonts** tijdens een batch‑importproces en een samenvattend rapport genereren.  
- **Track missing fonts** over meerdere documenten en een e‑mail‑waarschuwing sturen wanneer een bepaald lettertype vaak voorkomt.  
- **Integrate with a monitoring system** (bijv. Azure Application Insights) om font‑substitution‑trends in de loop van de tijd zichtbaar te maken.  

Al deze uitbreidingen bouwen voort op dezelfde `IWarningCallback`‑basis die we hebben gemaakt.

*Happy coding!* Als je tegen eigenaardigheden aanloopt—misschien een aangepaste lettertype‑map of een netwerkschijf—laat dan een reactie achter. De community (en ik) helpen je graag je font‑warning‑strategie te verfijnen. 

![create font warning handler example](image-placeholder.png "create font warning handler example")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}