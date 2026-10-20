---
category: general
date: 2026-04-04
description: Leer hoe je waarschuwingen kunt vastleggen, ontbrekende lettertypen kunt
  detecteren en hoe je substitutie‑gebeurtenissen kunt loggen met Aspose.Words LoadOptions
  in C#.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to log substitution
- Aspose.Words warning handling
- font substitution monitoring
language: nl
og_description: Hoe waarschuwingen vast te leggen, ontbrekende lettertypen te detecteren
  en substitutie‑gebeurtenissen te loggen met Aspose.Words LoadOptions in C#.
og_title: Hoe waarschuwingen in C# vast te leggen – Detecteer ontbrekende lettertypen
  en log vervanging
tags:
- C#
- Aspose.Words
- Document Loading
- Font Management
title: Hoe waarschuwingen in C# vast te leggen – Detecteer ontbrekende lettertypen
  en log vervanging
url: /nl/net/programming-with-loadoptions/how-to-capture-warnings-in-c-detect-missing-fonts-log-substi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe waarschuwingen vast te leggen in C# – Ontbrekende lettertypen detecteren & substitutie loggen

Heb je je ooit afgevraagd **hoe je waarschuwingen kunt vastleggen** die verschijnen wanneer je een Word‑document laadt met ontbrekende lettertypen? Je bent niet de enige. In veel real‑world projecten gaan lettertypen verloren tijdens migratie, en de stille fallback kan je lay‑out breken. Het goede nieuws? Aspose.Words biedt een nette manier om naar die waarschuwingen te luisteren, ontbrekende lettertypen te detecteren en zelfs elke substitutie te loggen zodat je later de bron kunt herstellen.

In deze tutorial lopen we een complete, kant‑klaar oplossing door die **hoe je waarschuwingen kunt vastleggen** laat zien, **ontbrekende lettertypen detecteert**, en **hoe je substitutie‑gebeurtenissen logt** uitlegt. Aan het einde heb je een herbruikbare warning‑handler, een volledig geconfigureerd `LoadOptions`‑object en een voorbeeld van console‑output die je kunt verifiëren.

> **Prerequisite:** Je hebt Aspose.Words for .NET (v24.x of later) geïnstalleerd via NuGet en een basis C#‑ontwikkelomgeving (Visual Studio 2022 of VS Code werkt prima).

---

## Hoe waarschuwingen vast te leggen bij het laden van documenten

De kern van de oplossing is een klasse die `IWarningCallback` implementeert. Aspose.Words roept deze callback automatisch aan voor elke waarschuwing die tijdens het laden van een document wordt gegenereerd, inclusief waarschuwingen over lettertype‑substitutie.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

/// <summary>
/// Handles warning callbacks from Aspose.Words.
/// </summary>
class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // We're only interested in font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // This line prints the warning to the console.
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Why this step?**  
> Door te filteren op `WarningType.FontSubstitution` vermijden we rommel van niet‑relevante waarschuwingen (zoals verouderde functies). Hierdoor blijft het logboek gericht op het exacte probleem dat je bezighoudt — ontbrekende lettertypen.

---

## Ontbrekende lettertypen detecteren met Aspose.Words

Wanneer een document een lettertype aanroept dat niet op de machine is geïnstalleerd, vervangt Aspose.Words het dichtstbijzijnde alternatief en geeft een waarschuwing. Onze handler hierboven vangt elke gebeurtenis op, waardoor je effectief **ontbrekende lettertypen detecteert**.

Om het in actie te zien, moeten we `LoadOptions` configureren en de handler koppelen:

```csharp
// Configure load options and attach the warning callback.
var loadOptions = new LoadOptions
{
    WarningCallback = new FontWarningHandler()
};
```

> **Tip:** Als je liever waarschuwingen verzamelt voor latere verwerking (bijv. naar een bestand schrijven), vervang je `Console.WriteLine` door code die het bericht toevoegt aan een `List<string>`.

---

## Hoe substitutie‑gebeurtenissen te loggen

Loggen is zo simpel als de waarschuwingoutput naar een permanente opslag leiden. Hieronder een kort voorbeeld dat elke substitutie‑waarschuwing schrijft naar een tekstbestand met de naam `font-warnings.log`.

```csharp
using System.IO;

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            // Append the message to the log file.
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

// Later, when creating LoadOptions:
var loadOptions = new LoadOptions
{
    WarningCallback = new FileLoggingWarningHandler()
};
```

> **Why log to a file?**  
> Permanente logs laten je lettertype‑problemen over meerdere runs auditten, alerts automatiseren, of de data in een build‑pipeline‑check verwerken.

---

## Volledig werkend voorbeeld

Alles samengevoegd vind je hier een zelfstandige console‑applicatie die je kunt kopiëren, plakken en uitvoeren. Het demonstreert **hoe je waarschuwingen vastlegt**, **ontbrekende lettertypen detecteert**, en **hoe je substitutie logt** in één stap.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Warning;

class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution: {info.Description}");
        }
    }
}

class FileLoggingWarningHandler : IWarningCallback
{
    private readonly string _logPath = "font-warnings.log";

    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            string message = $"[{DateTime.Now}] Font substitution: {info.Description}";
            File.AppendAllText(_logPath, message + Environment.NewLine);
        }
    }
}

class Program
{
    static void Main()
    {
        // Choose which handler you want:
        // var handler = new FontWarningHandler();          // console output
        var handler = new FileLoggingWarningHandler();    // file logging

        var loadOptions = new LoadOptions
        {
            WarningCallback = handler
        };

        // Path to the document that may contain missing fonts.
        string docPath = Path.Combine(Environment.CurrentDirectory, "input.docx");

        try
        {
            // Load the document – warnings are raised automatically.
            Document doc = new Document(docPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Failed to load document: {ex.Message}");
        }

        // If you used the file logger, show where the log lives.
        if (handler is FileLoggingWarningHandler)
        {
            Console.WriteLine($"Font warnings have been written to 'font-warnings.log'.");
        }
    }
}
```

### Verwachte console‑output

Als `input.docx` een lettertype aanroept dat niet geïnstalleerd is, zie je iets als:

```
Font substitution: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
Document loaded successfully.
```

Als je overschakelt naar `FileLoggingWarningHandler`, verschijnen dezelfde regels in `font-warnings.log` met tijdstempels.

![hoe waarschuwingen vastleggen console-output](image-placeholder.png)

---

## Veelgestelde vragen & randgevallen

### Wat als ik *alle* waarschuwingen moet vastleggen, niet alleen lettertype‑substitutie?

Verwijder simpelweg de controle `if (info.Type == WarningType.FontSubstitution)`. De callback ontvangt dan elk type waarschuwing (`WarningType.DegradedDocument`, `WarningType.UnexpectedContent`, enz.). Je kunt vervolgens op `info.Type` vertakken om elk geval anders af te handelen.

### Werkt dit met PDF’s of alleen Word‑documenten?

`LoadOptions` en `IWarningCallback` maken deel uit van Aspose.Words, dus ze gelden voor Word‑compatibele formaten (`.docx`, `.doc`, `.rtf`, `.html`). Voor PDF’s gebruik je de eigen waarschuwingsmechanismen van Aspose.PDF.

### Hoe kan ik waarschuwingen onderdrukken in plaats van ze te loggen?

Stel `LoadOptions.WarningCallback = null` in of implementeer de callback maar laat de methode‑body leeg. De bibliotheek voert de substitutie nog steeds stil uit.

### Hoe zit het met thread‑veiligheid?

De callback‑instantie wordt aangeroepen op dezelfde thread die het document laadt, dus extra synchronisatie is niet nodig tenzij je dezelfde handler deelt over parallelle loads. In dat geval bescherm je gedeelde bronnen (bijv. het log‑bestand) met een lock of gebruik je thread‑veilige collecties.

---

## Conclusie

We hebben **hoe je waarschuwingen kunt vastleggen** vanuit Aspose.Words behandeld, laten zien hoe je **ontbrekende lettertypen detecteert**, en uitgelegd **hoe je substitutie‑gebeurtenissen logt** voor latere analyse. Door een eenvoudige `IWarningCallback`‑implementatie in `LoadOptions` te injecteren, krijg je volledige zichtbaarheid op lettertype‑gerelateerde problemen zonder je codebase te vervuilen.

Volgende stappen? Breid de logger uit om e‑mails te versturen, integreer met Azure Monitor, of installeer automatisch ontbrekende lettertypen op een build‑server. Je kunt ook andere waarschuwings‑types verkennen — `WarningType.DegradedDocument` kan je waarschuwen voor functionaliteit die niet is overgebleven na een conversie.

Heb je meer vragen over lettertype‑beheer of Aspose.Words in het algemeen? Laat een reactie achter of open een nieuw issue op de Aspose‑forums. Happy coding, en moge je documenten altijd renderen met het juiste lettertype!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}