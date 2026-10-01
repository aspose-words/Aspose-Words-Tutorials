---
category: general
date: 2026-01-03
description: Maak een rechthoekvorm in Word met C# en voeg een schaduw toe aan de
  vorm. Leer hoe je een vorm in Word invoegt, een schaduw aan de vorm toevoegt en
  Word‑documenten via code genereert.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- insert shape in word
- how to add shape
- c# generate word document
language: nl
og_description: Maak een rechthoekvorm in Word met C# en voeg een schaduw toe aan
  de vorm. Volg deze handleiding om een vorm in Word in te voegen, schaduwen in te
  stellen en documenten automatisch te genereren.
og_title: Rechthoekvorm maken in Word met C# – Complete tutorial
tags:
- C#
- Word Automation
- Aspose.Words
title: Rechthoekvorm maken in Word met C# – Stapsgewijze handleiding
url: /nl/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rechthoekige vorm maken in Word met C# – Volledige tutorial

Heb je ooit een **create rectangle shape** nodig gehad in een Word‑document maar wist je niet waar je moest beginnen? Je bent niet de enige—veel ontwikkelaars lopen tegen hetzelfde probleem aan wanneer ze een **add shadow to shape** willen voor een gepolijste uitstraling. In deze tutorial lopen we de exacte stappen door om een **insert shape in Word** toe te voegen, een subtiele schaduw toe te passen, en uiteindelijk **c# generate word document**‑bestanden te maken die je naar gebruikers kunt verzenden.

We behandelen alles, van het opzetten van het project tot het aanpassen van schaduw‑eigenschappen, en we eindigen met een kant‑klaar code‑voorbeeld. Geen poespas, alleen de praktische zaken die het werk doen.

## Wat je zult leren

- Hoe je een **create rectangle shape** maakt met Aspose.Words (of Open XML) in C#  
- De exacte eigenschappen die je nodig hebt om **add shadow to shape** toe te voegen voor diepte  
- Waar je de vorm plaatst met `DocumentBuilder`  
- Hoe je het bestand opslaat zodat het correct opent in Microsoft Word  
- Tips, valkuilen en variaties voor real‑world scenario’s  

### Vereisten

- .NET 6.0 of later (de code werkt op .NET Core en .NET Framework)  
- Een NuGet‑pakket dat Word‑bestanden kan manipuleren – we gebruiken **Aspose.Words for .NET** omdat de API beknopt is. Als je de voorkeur geeft aan Open XML SDK, zijn de concepten hetzelfde, alleen de klassen verschillen.  
- Visual Studio, VS Code, of elke C#‑IDE die je wilt  

> **Pro tip:** Als je een beperkt budget hebt, biedt Aspose een gratis proefversie die perfect is om te leren. Vervang gewoon de licentielijn door een commentaar wanneer je test.

## Stap 1: Installeer de Word‑verwerkingsbibliotheek

Eerst voeg je de bibliotheek toe aan je project. Open een terminal in je solution‑map en voer uit:

```bash
dotnet add package Aspose.Words
```

Als je de Open XML SDK gebruikt, zou de opdracht `dotnet add package DocumentFormat.OpenXml` zijn. De rest van deze gids gaat uit van Aspose.Words, maar het verwisselen van de API‑aanroepen is eenvoudig.

## Stap 2: Maak een nieuw leeg document

Nu de bibliotheek klaar is, kunnen we een **create rectangle shape** maken door te beginnen met een schoon `Document`‑object. Beschouw dit als een leeg canvas.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 2: Initialize a blank Word document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);
```

De `DocumentBuilder` biedt ons een high‑level manier om inhoud in te voegen zonder in low‑level knooppuntenbomen te duiken.

## Stap 3: Voeg de rechthoekige vorm in

Met de builder in de hand kunnen we een **insert shape in Word**. De `InsertShape`‑methode neemt het vormtype en de afmetingen (breedte, hoogte) in points.

```csharp
// Step 3: Insert a rectangle shape – 150pt wide, 80pt high
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Op dit moment verschijnt de rechthoek in het document, maar hij ziet er een beetje plat uit. Daar komt de volgende stap om de hoek.

## Stap 4: Voeg een schaduw toe aan de vorm

Schaduwen geven de vorm een gevoel van diepte. Het `Shadow`‑object stelt ons in staat om blur, distance, angle, color en transparency fijn af te stemmen. Hieronder staat een volledige configuratie die goed werkt voor de meeste rapporten.

```csharp
// Step 4: Configure a subtle shadow
rectangle.Shadow = new Shadow
{
    BlurRadius = 5.0,          // Soft edges
    Distance = 4.0,            // How far the shadow is offset
    Angle = 45,                // Direction in degrees (45° = down‑right)
    Color = Color.Black,       // Shadow color
    Transparency = 0.3         // 30 % transparent for a gentle look
};
```

**Waarom deze waarden?**  
- **BlurRadius** van `5.0` houdt de rand glad zonder er wazig uit te zien.  
- **Distance** van `4.0` verplaatst de schaduw net genoeg om merkbaar te zijn.  
- **Angle** `45` bootst natuurlijk licht van links‑boven na, een veelvoorkomende UI‑conventie.  
- **Transparency** `0.3` voorkomt dat de schaduw de vulling van de vorm overheerst.

Als je een dramatischer effect wilt, verhoog dan `BlurRadius` en verlaag `Transparency`. Voor een subtiele, bijna onzichtbare lift, verwissel die getallen.

## Stap 5: Sla het document op

Tot slot schrijf je het bestand naar de schijf. De `Save`‑methode detecteert het formaat aan de hand van de bestandsextensie, dus `.docx` geeft je het moderne Word‑formaat.

```csharp
// Step 5: Persist the document
string outputPath = @"C:\Temp\ShadowRectangle.docx";
document.Save(outputPath);
```

Open `ShadowRectangle.docx` in Microsoft Word, en je ziet een scherpe rechthoek met een zachte schaduw—precies wat je wilde toen je vroeg naar “**how to add shape**” met een professionele afwerking.

![Rechthoekige vorm maken met schaduw in Word](placeholder-image.png "Rechthoekige vorm maken met schaduw in Word")

*Afbeeldings‑alt‑tekst: Rechthoekige vorm maken met schaduw in Word*

## Volledig werkend voorbeeld

Alles bij elkaar, hier is het volledige, kant‑klaar programma. Kopieer‑en‑plak in een console‑app en druk op **F5**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordShapeDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a rectangle shape (150pt × 80pt)
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Add a subtle shadow
            rect.Shadow = new Shadow
            {
                BlurRadius = 5.0,
                Distance = 4.0,
                Angle = 45,
                Color = Color.Black,
                Transparency = 0.3
            };

            // 4️⃣ Save the file
            string filePath = @"C:\Temp\ShadowRectangle.docx";
            doc.Save(filePath);

            System.Console.WriteLine($"Document saved to {filePath}");
        }
    }
}
```

### Verwacht resultaat

- Het gegenereerde `ShadowRectangle.docx` bevat **one rectangle shape** gecentreerd waar de cursor stond.  
- De rechthoek toont een **soft, 30 % transparent black shadow** verschoven onder een hoek van 45°.  
- Er wordt geen andere inhoud toegevoegd, waardoor het bestand lichtgewicht blijft en gemakkelijk in grotere rapporten kan worden ingebed.

## Veelgestelde vragen & randgevallen

### Wat als ik een andere vorm nodig heb?

Vervang `ShapeType.Rectangle` door een andere `ShapeType`‑enumwaarde (bijv. `Ellipse`, `Triangle`). De shadow‑API werkt op dezelfde manier, dus je kunt de configuratie hergebruiken.

### Hoe wijzig ik de vulkleur?

```csharp
rect.FillColor = Color.LightBlue;   // or any System.Drawing.Color
```

### Kan ik de vorm toevoegen aan een specifieke alinea?

Ja. Verplaats de `DocumentBuilder` naar de doel‑alinea met `builder.MoveToParagraph(index)` voordat je `InsertShape` aanroept. Dit zorgt ervoor dat de vorm precies verschijnt waar je het nodig hebt.

### Hoe zit het met oudere Word‑formaten (.doc)?

Gewoon de extensie wijzigen:

```csharp
doc.Save(@"C:\Temp\ShadowRectangle.doc", SaveFormat.Doc);
```

De schaduw‑functie wordt ondersteund in Word 2003 en later, dus je zult het effect nog steeds zien.

### Open XML SDK gebruiken in plaats van Aspose?

De stappen blijven hetzelfde: maak een `WordprocessingDocument`, voeg een `Drawing`‑element toe, stel `<a:shadow>`‑eigenschappen in. De XML is uitgebreider, maar dezelfde concepten (size, blur, distance, angle) gelden.

## Tips om valkuilen te vermijden

- **Vergeet de licentie niet** als je een betaalde Aspose‑versie gebruikt; anders krijg je een watermerk.  
- **Eenheden zijn points**, niet pixels. Een typische schermpixel ≈ 0.75 pt, dus pas de afmetingen dienovereenkomstig aan.  
- **Shadow‑eigenschappen worden genegeerd** als de `WrapType` van de vorm op `Inline` staat. Gebruik `WrapType = WrapType.Square` voor zwevende vormen die schaduwweergave respecteren.  
- **Opslaan naar een netwerkschijf** kan juiste permissies vereisen; test altijd eerst het pad.

## Conclusie

Je weet nu hoe je een **create rectangle shape** in een Word‑document maakt met C#, **add shadow to shape**, en **c# generate word document**‑bestanden die direct een gepolijste uitstraling hebben. De kernstappen—installeer de bibliotheek, instantiate `Document`, insert the shape, configure the shadow, en save—zijn makkelijk te onthouden en aanpasbaar aan andere vormen, kleuren, of zelfs dynamische data.

Wat is de volgende stap? Probeer meerdere vormen te stapelen, afbeeldingen in te sluiten, of een volledig rapport te genereren met tabellen en grafieken. Je kunt ook conditionele opmaak verkennen—de schaduwdichtheid aanpassen op basis van gegevenswaarden—om je documenten niet alleen functioneel maar ook visueel aantrekkelijk te maken.

Voel je vrij om te experimenteren, en als je tegen eigenaardigheden aanloopt, laat dan een reactie achter. Veel plezier met coderen, en moge je Word‑documenten altijd die perfecte slagschaduw hebben!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}