---
category: general
date: 2026-02-18
description: Maak een rechthoekvorm met Aspose.Words en leer hoe je een schaduw toevoegt,
  de grootte van de vorm instelt en een Word‑document in enkele minuten opslaat.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: nl
og_description: Maak een rechthoekvorm in een Word‑bestand, leer hoe je een schaduw
  toevoegt, stel de vormgrootte in en sla het document op met Aspose.Words in C#.
og_title: Rechthoekvorm maken in Word – Complete Aspose.Words-handleiding
tags:
- Aspose.Words
- C#
- Word automation
title: Rechthoekvorm maken in Word met Aspose.Words – Stapsgewijze handleiding
url: /nl/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Maak rechthoekige vorm in Word met Aspose.Words – Stapsgewijze gids

Heb je ooit **een rechthoekige vorm** in een Word‑bestand moeten **maken**, maar wist je niet waar te beginnen? Je bent niet de enige—ontwikkelaars vragen vaak: “hoe voeg ik een schaduw toe aan een vorm en houd ik het document toch bewerkbaar?” In deze tutorial beantwoorden we dat en laten we je ook zien hoe je **schaduw toevoegt**, **de vormgrootte instelt**, en **een Word‑document opslaat**, allemaal in één vloeiende stroom.

We lopen alles door wat je nodig hebt, van het initialiseren van een nieuw document (ja, dat is de eerste stap naar **hoe een document te maken**) tot het opslaan van het uiteindelijke *.docx* op schijf. Geen externe referenties, alleen een zelfstandige voorbeeldcode die je kunt copy‑paste in Visual Studio en vandaag nog kunt uitvoeren.

---

## Vereisten

- .NET 6+ (of .NET Framework 4.7+). Aspose.Words werkt met elke recente .NET‑runtime.
- Een geldige Aspose.Words‑licentie (of de gratis evaluatiesleutel) – anders zie je een watermerk.
- Visual Studio, Rider, of elke C#‑editor die je verkiest.
- Basiskennis van C#—niets ingewikkeld, alleen het vermogen om een console‑applicatie uit te voeren.

> **Pro tip:** Als je op een Mac werkt, draait dezelfde code onder .NET 6 met VS Code—zorg er alleen voor dat je de `Aspose.Words` NuGet‑package referereert.

## Stap 1: Initialiseer het document – de basis van **hoe een document te maken**

Voordat we iets kunnen tekenen, hebben we een leeg canvas nodig. Aspose.Words noemt dit een `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Waarom dit belangrijk is:** Het `Document`‑object vertegenwoordigt het volledige *.docx*-bestand. Alle vormen, alinea’s en secties die je toevoegt, worden kinderen van dit object. Beginnen met een schoon document zorgt ervoor dat er geen verborgen stijlen je rechthoek beïnvloeden.

## Stap 2: Definieer de rechthoek en **stel de vormgrootte in**

Een rechthoek is simpelweg een `Shape` met `ShapeType.Rectangle`. We geven het expliciete afmetingen zodat het er precies uitziet zoals bedoeld.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Wat de getallen betekenen:** Aspose.Words gebruikt punten (1 pt = 1/72 in). Pas de waarden aan om bij je lay‑out te passen; voor een typische A4‑pagina is 200 pt een comfortabele breedte.

## Stap 3: **Hoe schaduw toe te voegen** – de vorm laten opvallen

Schaduwen geven een visueel signaal dat de vorm “van het blad” is getild. De `Shadow`‑eigenschap laat je kleur, afstand, transparantie en vervaging aanpassen.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Waarom transparantie gebruiken?** Een volledig ondoorzichtige schaduw kan hard overkomen. Instellen op 0,4 maakt het effect subtiel en professioneel.

## Stap 4: Positioneer de rechthoek – inline‑stroom met omringende tekst

Als je wilt dat de vorm zich gedraagt als een teken in een alinea, stel dan de `WrapType` in op `Inline`. Dit houdt de lay‑out voorspelbaar, vooral wanneer het document later wordt bewerkt.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Randgeval:** Als je wilt dat de rechthoek zweeft boven tekst (bijv. een watermerk), verander `WrapType` naar `Square` of `BehindText`.

## Stap 5: Voeg de vorm in de document‑body in

Nu plaatsen we de rechthoek daadwerkelijk in de eerste alinea. Als het document nog geen inhoud heeft, wordt `FirstParagraph` automatisch aangemaakt.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Tip:** Je kunt ook eerst een nieuwe alinea maken en vervolgens de vorm toevoegen—handig wanneer je omringende tekst nodig hebt.

## Stap 6: **Word‑document opslaan** – de laatste stap

Met alles op zijn plaats is het opslaan van het bestand een één‑regelige opdracht. Kies elk pad dat je wilt; het voorbeeld gebruikt een tijdelijke aanduiding die je moet vervangen door je eigen map.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Resultaat:** Open het gegenereerde *.docx* in Microsoft Word. Je ziet een zwart‑schaduwde rechthoek, 200 pt breed en 100 pt hoog, inline met de eerste alinea.

## Verwachte output

Wanneer je **ShadowShape.docx** opent, toont het document:

- Een enkele alinea met een rechthoekige vorm.
- De rechthoek heeft een subtiele zwarte schaduw met een offset van 5 pt.
- De vormgrootte komt overeen met de afmetingen die in Stap 2 zijn ingesteld.
- Er verschijnt geen extra tekst tenzij je die handmatig toevoegt.

Als de vorm niet verschijnt, controleer dan dubbel of je de juiste Aspose.Words‑versie hebt gerefereerd en of je licentie (of proefversie) actief is.

## Veelgestelde vragen & Variaties

| Vraag | Antwoord |
|-------|----------|
| *Kan ik de schaduwkleur wijzigen naar iets anders dan zwart?* | Absoluut—stel `rectangleShape.Shadow.Color = Color.Blue;` in of een andere `System.Drawing.Color`. |
| *Wat als ik een grotere rechthoek nodig heb?* | Pas de waarden van `Width` en `Height` aan. Onthoud dat ze in punten zijn; 72 pt = 1 in. |
| *Is het mogelijk de vorm op een absolute positie te plaatsen?* | Ja—gebruik `WrapType = WrapType.Absolute` en stel de eigenschappen `Top`/`Left` in. |
| *Werkt dit met .NET Core?* | Ja. Aspose.Words is cross‑platform; installeer gewoon het NuGet‑pakket voor .NET Standard. |
| *Kan ik tekst binnen de rechthoek toevoegen?* | Niet direct; je moet een `TextBox`‑vorm invoegen in plaats van een gewone rechthoek. |

## Volledig werkend voorbeeld (Klaar om te copy‑pasten)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Voer het programma uit, ga naar `C:\Temp\ShadowShape.docx`, en je ziet de rechthoek met een schaduw precies zoals beschreven.

## Conclusie

Je weet nu hoe je **een rechthoekige vorm** in een Word‑bestand maakt met Aspose.Words, hoe je **de vormgrootte instelt**, **schaduw toevoegt**, en uiteindelijk **het Word‑document opslaat** met de wijzigingen. Het volledige proces—van **hoe een document te maken** tot het opslaan van het resultaat—past in een handvol C#‑regels en kan worden uitgebreid voor complexere lay‑outs.

Klaar voor de volgende uitdaging? Probeer de rechthoek te vervangen door een vorm met afgeronde hoeken, experimenteer met verschillende schaduwkleur­en, of embed de vorm in een tabelcel. Elke aanpassing versterkt dezelfde kernconcepten die we hier hebben behandeld.

Als je deze gids nuttig vond, deel hem, laat een reactie achter met je eigen variaties, of verken onze andere tutorials over Word‑automatisering, zoals het invoegen van afbeeldingen of het genereren van tabellen met Aspose.Words. Veel programmeerplezier!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}