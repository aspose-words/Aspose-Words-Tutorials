---
category: general
date: 2026-09-21
description: Maak een leeg Word‑document met een verborgen ellips met C#. Leer hoe
  je een vorm in Word verbergt en hoe je via code een verborgen vorm genereert.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: nl
lastmod: 2026-09-21
og_description: Maak een leeg Word‑document met een verborgen ellips met C#. Deze
  gids laat zien hoe je een vorm in Word verbergt en hoe je verborgen vormen programmeermatig
  maakt.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Maak een leeg Word‑document met een verborgen ellipsvorm in C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Hoe een leeg Word‑document te maken en een verborgen ellipsvorm toe te voegen
  in C#
url: /nl/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een leeg Word‑document te maken en een verborgen ellipsvorm toe te voegen in C#

Als je een **blank Word‑document** moet maken dat een onzichtbare afbeelding bevat, laat deze gids je precies zien hoe. Aan het einde van de tutorial heb je een .docx‑bestand dat er leeg uitziet, maar daadwerkelijk een ellipsvorm opslaat die verborgen is voor de lay‑out.

We gebruiken Aspose.Words for .NET om het document te bouwen, een ellips in te voegen, deze te verbergen en het bestand op te slaan. De stappen behandelen ook **how to create ellipse** objecten, de juiste manier om **hide shape in Word** toe te passen, en hoe je **create hidden shape** code maakt die werkt met elk .NET‑project.

## Vereisten

* .NET 6.0 SDK of later geïnstalleerd  
* Visual Studio 2022 (of een andere C#‑editor)  
* Een Aspose.Words for .NET‑licentie of een gratis evaluatiekopie  
* Basiskennis van C#‑syntaxis  

Er zijn geen extra NuGet‑pakketten vereist, behalve `Aspose.Words`.

## Maak een leeg Word‑document met Aspose.Words

De eerste stap is het genereren van een leeg Word‑bestand. Dit geeft ons een schoon canvas waarop we later verborgen afbeeldingen kunnen invoegen.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Waarom we beginnen met een leeg document** – Beginnen met een leeg bestand garandeert dat er geen ongewenste inhoud interfereert met de verborgen vorm. Het houdt ook de bestandsgrootte minimaal, wat nuttig is wanneer het document later als sjabloon wordt gebruikt.

## Hoe een ellips te maken in het lege document

Vervolgens hebben we een `DocumentBuilder` nodig om inhoud toe te voegen. De builder stelt ons in staat vormen precies te plaatsen waar we ze willen.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Uitleg** – `ShapeType.Ellipse` vertelt Aspose.Words om een cirkel‑achtige figuur te tekenen. De breedte en hoogte worden gemeten in punten (1 pt ≈ 1/72 inch). Je kunt deze waarden aanpassen aan je ontwerpbehoeften.

## Verberg vorm in Word zodat deze niet in de lay‑out verschijnt

Een vorm die verborgen is, blijft nog steeds aanwezig in de XML van het document, wat nuttig kan zijn voor metadata, voorwaardelijke opmaak, of latere programmatische wijzigingen. Om deze te verbergen, stellen we de eigenschap `Hidden` in op `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Waarom de vorm verbergen** – Verborgen vormen worden genegeerd door de lay‑outengine, zodat de pagina volledig leeg lijkt. De vormgegevens blijven echter behouden, wat nuttig kan zijn voor het opslaan van markeringen, bladwijzers, of aangepaste XML die door downstream processen kan worden gelezen.

## Sla het document op met de verborgen vorm

Tot slot schrijven we het bestand naar schijf. Het opgeslagen `.docx`‑bestand opent in Microsoft Word zonder zichtbare inhoud, maar de verborgen ellips is nog steeds aanwezig.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verificatie** – Open het gegenereerde bestand in Word, druk vervolgens op `Alt+F9` om veldcodes te schakelen en `Ctrl+A` → `Ctrl+Shift+F9` om verborgen objecten te bekijken. Je ziet de ellips in de XML van het document (`word/document.xml`), maar niets op de pagina.

---

## Volledig, uitvoerbaar voorbeeld

Hieronder staat het volledige programma dat je kunt kopiëren‑plakken in een nieuw console‑project. Het bevat alle `using`‑directieven en de `Main`‑methode, zodat je het kunt uitvoeren zonder extra scaffolding.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Verwachte output** – Wanneer je het programma uitvoert, toont de console het bestandspad, en het resulterende Word‑bestand bevat geen zichtbare objecten. Als je het document inspecteert met een zip‑tool (`.docx` is een zip‑archief), vind je het `<w:pict>`‑element dat de ellips beschrijft in `word/document.xml`.

---

## Veelvoorkomende variaties en randgevallen

| Scenario | Wat te wijzigen | Waarom het belangrijk is |
|----------|----------------|--------------------------|
| **Andere vorm** | Replace `ShapeType.Ellipse` with `ShapeType.Rectangle`, `ShapeType.Line`, etc. | Stelt je toe andere afbeeldingen te verbergen terwijl je dezelfde workflow behoudt. |
| **Meerdere verborgen vormen** | Call `InsertShape` several times and set `Hidden = true` on each. | Handig om een verzameling markeringen of tijdelijke aanduidingen in te sluiten. |
| **Voorwaardelijke zichtbaarheid** | Use `shape.Visible = false` together with `shape.Hidden = true` for extra safety. | Sommige oudere Word‑versies respecteren `Visible` anders; beide instellen dekt alle gevallen. |
| **Opslaan naar een stream** | Replace `doc.Save(path)` with `doc.Save(stream, SaveFormat.Docx)`. | Stelt je in staat het document direct via HTTP te verzenden of op te slaan in een database. |
| **Een stijl toepassen** | After insertion, modify `ellipse.FillColor`, `ellipse.LineWeight`, etc. before hiding. | De opmaak van de vorm blijft bewaard in de XML, wat nuttig kan zijn voor later weer zichtbaar maken. |

**Pro tip:** Test de verborgen vorm altijd op de doel‑Word‑versie (bijv. Word 2019, Word 365) omdat weergave‑eigenaardigheden af en toe optreden wanneer verborgen objecten interageren met complexe paginalay‑outs.

---

## Veelgestelde vragen

**Q: Heeft het verbergen van een vorm invloed op de documentgrootte?**  
A: De XML van de vorm voegt enkele honderden bytes toe, wat verwaarloosbaar is voor de meeste toepassingen. Het bestand blijft in wezen even groot als een echt leeg document.

**Q: Kan ik de vorm later programmatisch weer zichtbaar maken?**  
A: Ja. Laad het document, zoek de vorm (`doc.GetChildNodes(NodeType.Shape, true)`) en stel `shape.Hidden = false` in.

**Q: Zal de verborgen vorm verschijnen bij het afdrukken?**  
A: Nee. Verborgen objecten worden uitgesloten van de afdruklay‑out, dus de afgedrukte pagina blijft leeg.

**Q: Is deze aanpak alleen compatibel met Office Open XML (OOXML)?**  
A: De eigenschap `Hidden` maakt deel uit van de OOXML‑specificatie, dus elke Word‑processor die OOXML volledig implementeert (Word, LibreOffice, Google Docs) zal de verborgen‑vlag respecteren.

## Conclusie

Je weet nu hoe je een **blank Word document** maakt, **een ellips maakt**, **een vorm verbergt in Word**, en **een verborgen vorm** creëert met Aspose.Words for .NET. De tutorial besprak de volledige levenscyclus – van het initialiseren van een leeg bestand tot het invoegen, verbergen en opslaan van de vorm – plus verificatiestappen en veelvoorkomende variaties.

Vervolgens kun je verkennen:

* Het toevoegen van verborgen tekstvakken voor metadata (`hide shape in word`‑techniek toegepast op tekst)  
* Het gebruiken van aangepaste XML‑onderdelen om gestructureerde gegevens op te slaan naast verborgen vormen  
* Het converteren van het document met verborgen vorm naar PDF terwijl de verborgen elementen behouden blijven  

Experimenteer met verschillende vormen en zichtbaarheidinstellingen om te zien hoe verborgen inhoud kan dienen als een lichtgewicht gegevensopslag binnen Word‑bestanden.

Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap‑uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Rechthoekvorm maken in Word met C# – Stapsgewijze handleiding](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Groepvorm maken in Word‑document met Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Word‑document maken met een schaduwrijk rechthoek – Stapsgewijze handleiding](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}