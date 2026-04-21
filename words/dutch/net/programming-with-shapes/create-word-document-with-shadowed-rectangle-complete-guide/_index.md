---
category: general
date: 2026-04-21
description: Maak een Word‑document met een gestylede rechthoek en schaduw. Leer hoe
  je schaduw toevoegt, een rechthoekvorm invoegt, de schaduwkleur instelt en meer
  in C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: nl
og_description: Maak een Word‑document en voeg een rechthoek met schaduw toe in C#.
  Volg deze gids om eenvoudig de schaduwkleur, vervaging en offsets in te stellen.
og_title: Maak Word-document met schaduwrand – stap voor stap
tags:
- Aspose.Words
- C#
- Document Automation
title: Maak een Word‑document met een schaduwrechthoek – Complete gids
url: /nl/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak Word-document met Schaduwrechthoek – Complete Gids

Heb je ooit een **een Word-document maken** moeten die er net iets netter uitziet dan een eenvoudige tekstpagina? Misschien bouw je een rapporttemplate of een flyer en zou een eenvoudige rechthoek met een subtiele schaduw het gewenste effect geven. In deze tutorial lopen we precies dat stap voor stap door—hoe je een rechthoekvorm invoegt, de schaduw inschakelt en de kleur, vervaging en offsets aanpast—alles met C# en Aspose.Words.

We behandelen ook **hoe je schaduw toevoegt** op een manier die werkt, ongeacht of je richt op Word 2016, 2019 of de nieuwste Office 365‑versie. Aan het einde heb je een kant‑klaar *.docx*‑bestand dat een mooi gearceerde rechthoek toont, en begrijp je de “waarom” achter elke ingestelde eigenschap.

## Vereisten

- .NET 6 (of een recente .NET Framework‑versie)  
- Aspose.Words for .NET NuGet‑pakket (`Install-Package Aspose.Words`)  
- Basiskennis van C#‑syntaxis  
- Een IDE zoals Visual Studio (maar elke editor volstaat)

Er zijn geen extra bibliotheken nodig; alles anders zit in Aspose.Words.

## Stap 1 – Initialiseer het Document en de Builder (Create Word Document)

Om **een Word-document te maken** programmatically begin je met de `Document`‑klasse. De `DocumentBuilder` is je penseel; hiermee kun je tekst, vormen en andere elementen toevoegen.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Waarom dit belangrijk is:* Het `Document`‑object vertegenwoordigt het volledige .docx‑bestand. Zonder dit object heb je nergens om de rechthoek of de schaduw aan te koppelen.

## Stap 2 – Voeg een Rechthoekvorm In (Insert Rectangle Shape)

Nu voegen we daadwerkelijk **een rechthoekvorm in**. De `InsertShape`‑methode neemt een `ShapeType`‑enum, plus de breedte en hoogte in punten.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Pro tip:* 1 punt ≈ 1/72 inch, dus 200 pts is ongeveer 2,78 inch breed. Pas deze getallen aan om bij je lay‑out te passen.

## Stap 3 – Schakel de Schaduw In (How to Add Shadow)

Schaduwen zijn standaard uitgeschakeld. Zet de `Visible`‑vlag om deze in te schakelen.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Wat gebeurt er?* Wanneer `Visible` true is, zal Word een slagschaduw weergeven op basis van de andere eigenschappen die je vervolgens instelt.

## Stap 4 – Pas het Uiterlijk van de Schaduw Aan (Set Shadow Color, Blur, Offsets)

Hier stel je **de schaduwkleur** in, de vervagingsradius en de X/Y‑offsets. Voel je vrij om te experimenteren—verschillende waarden geven je een zachte gloed, een diepe slagschaduw, of zelfs een “zwevend” effect.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Waarom deze getallen?* Een vervaging van 5 pts geeft een zachte, geveerde rand, terwijl een offset van 4 pts de schaduw naar beneden‑rechts verplaatst, wat een lichtbron links‑boven nabootst. Verander `Color` naar `Color.Black` voor een sterker contrast, of gebruik `Color.FromArgb(128, 0, 0, 0)` voor een half‑transparante zwarte schaduw.

### Randgevallen & Variaties

- **Geen vervaging:** Stel `Blur = 0` in voor een scherpe, hard‑randige schaduw.  
- **Negatieve offsets:** Gebruik `OffsetX = -4` om de schaduw naar links te duwen.  
- **Verschillende vormen:** Dezelfde schaduweigenschappen werken voor cirkels, driehoeken, of zelfs vrij getekende vormen—verander gewoon `ShapeType` in Stap 2.  
- **Compatibiliteit:** Aspose.Words schrijft de schaduwgegevens in het Office Open XML‑formaat, dat werkt in Word 2010‑2021 en Office 365.

## Stap 5 – Sla het Document Op (Create Word Document)

Tot slot sla je het bestand op schijf op. Je kunt elk ondersteund formaat kiezen (`.docx`, `.pdf`, `.odt`, …), maar voor deze gids blijven we bij het klassieke Word‑formaat.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Wanneer je **ShadowRectangle.docx** opent in Microsoft Word zie je een grijze rechthoek met een subtiele, vervaagde schaduw die naar rechtsonder is verschoven—precies wat we hebben geprogrammeerd.

### Verwachte Output

- Een enkel‑pagina *.docx*‑bestand.  
- Een 200 pt × 100 pt‑rechthoek gecentreerd op de positie waar de cursor stond toen `InsertShape` werd aangeroepen.  
- Een grijze schaduw die 4 pts naar rechts en 4 pts naar beneden verschijnt, met een vervaging van 5 pt.

Als de vorm niet gecentreerd lijkt, kun je de cursor verplaatsen met `builder.MoveTo` vóór het invoegen, of de `Left`‑ en `Top`‑eigenschappen van de vorm aanpassen na het invoegen.

## Veelgestelde Vragen & Probleemoplossing

**Q: De schaduw wordt niet weergegeven in Word.**  
A: Zorg ervoor dat `ShadowFormat.Visible` `true` is. Controleer ook dat je een recente versie van Aspose.Words gebruikt (de schaduw‑functie werd toegevoegd in versie 20.3).  

**Q: Kan ik een verloop op de schaduw toepassen?**  
A: Niet rechtstreeks via `ShadowFormat`. De UI van Word ondersteunt verloopschaduwen, maar het Open XML‑schema (waar Aspose.Words zich aan houdt) biedt alleen effen kleurschaduwen. Je zou de onderliggende XML handmatig moeten bewerken—een meer geavanceerd scenario.

**Q: Wat als ik een transparante rechthoek nodig heb met alleen een schaduw?**  
A: Stel `rectangle.FillColor = Color.Transparent;` in na het invoegen. De schaduw wordt nog steeds weergegeven omdat deze onafhankelijk is van de vulling.

## Pro‑tips voor Productiecode

- **Herbruik de builder:** Als je meerdere vormen toevoegt, houd dezelfde `DocumentBuilder`‑instantie; een nieuwe instantie voor elke vorm veroorzaakt onnodige overhead.  
- **Batch‑opslaan:** Sla één keer op na alle wijzigingen; frequente I/O vertraagt het genereren van grote documenten.  
- **Foutafhandeling:** Plaats het hele blok in een `try / catch` en log `Aspose.Words`‑exceptions; deze bevatten vaak nuttige regelnummers als de document‑template corrupt is.

## Volgende Stappen (Gerelateerde Onderwerpen)

- **Hoe schaduw toe te voegen** aan afbeeldingen of tekstvakken (vergelijkbare `ShadowFormat`‑gebruik).  
- **Rechthoekvorm invoegen** in een tabelcel voor aangepaste celopmaak.  
- **Rechthoek maken in Word** met de native XML van Word (voor wie de ruwe Open XML prefereert).  
- **Schaduwkleur instellen** dynamisch op basis van gebruikersinvoer of themakleuren.

Experimenteer met verschillende kleuren, vervagingsradii en offsets—misschien een zachte blauwe gloed voor een bedrijfsrapport, of een diepe zwarte schaduw voor een dramatische flyer. De mogelijkheden zijn eindeloos, en de code‑wijzigingen zijn minimaal.

---

### Snelle Samenvatting

- We **hebben een Word-document** vanaf nul **gemaakt**.  
- We **hebben een rechthoekvorm ingevoegd** en de schaduw ingeschakeld.  
- We **hebben de schaduwkleur**, vervaging en offsets ingesteld om een professionele uitstraling te bereiken.  
- We hebben het bestand opgeslagen, klaar voor distributie.

Nu heb je een solide basis om visuele flair toe te voegen aan elk Word‑automatiseringsproject. Heb je meer ideeën? Laat een reactie achter, en laten we het gesprek voortzetten. Veel plezier met coderen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}