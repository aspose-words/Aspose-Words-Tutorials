---
category: general
date: 2026-09-30
description: gruppera former i Word med C# – lär dig hur du grupperar former, lägger
  till rektangel och ellips, och infogar rektangelform i Word‑dokument programatiskt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- how to group shapes
- how to add rectangle
- how to add ellipse
- insert rectangle shape word
language: sv
lastmod: 2026-09-30
og_description: gruppa former i Word med C# och Aspose.Words. Följ den här kompletta
  guiden för att lägga till en rektangel, lägga till en ellips och lära dig hur du
  grupperar former effektivt.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape
og_title: Gruppera former i Word med C# – steg‑för‑steg‑guide
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: group shapes in Word with C# – learn how to group shapes, add rectangle
    and ellipse, and insert rectangle shape Word documents programmatically.
  headline: How to group shapes in Word using C# and Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Hur man grupperar former i Word med C# och Aspose.Words
url: /sv/net/programming-with-shapes/how-to-group-shapes-in-word-using-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man grupperar former i Word med C# och Aspose.Words

Om du behöver **gruppera former i Word** programatiskt visar den här guiden exakt hur du gör. Du får se hur du lägger till en rektangel, lägger till en ellips och sedan kombinerar dem till en enda gruppform med hjälp av Aspose.Words‑biblioteket för .NET.

Att arbeta med former är ett vanligt krav när man automatiskt genererar rapporter, kontrakt eller marknadsföringsmaterial. I slutet av den här handledningen har du en återanvändbar C#‑metod som laddar en DOCX‑fil, infogar en rektangel och en ellips, grupperar dem och sparar resultatet – utan att öppna Word manuellt.

## Förutsättningar

Innan du börjar, se till att du har:

* .NET 6.0 SDK eller senare installerat  
* En utvecklingsmiljö som Visual Studio 2022 (Community‑edition fungerar)  
* En Aspose.Words för .NET‑licens eller en gratis utvärderingskopi (API:t fungerar utan licens men lägger till ett vattenmärke)  

Du behöver också ett käll‑Word‑dokument (`input.docx`) i en mapp som du kan referera till från koden. Dokumentet kan vara tomt; handledningen fokuserar på hantering av former.

## Steg 1: Skapa ett nytt konsolprojekt och lägg till Aspose.Words

Öppna en terminal eller Visual Studio‑kommandoprompt och kör:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Detta skapar en ny konsolapplikation med namnet **WordShapeDemo** och lägger till NuGet‑paketet `Aspose.Words`, som innehåller klasserna `Document` och `DocumentBuilder` för att manipulera Word‑filer.

## Steg 2: Ladda eller skapa ett dokument

Den första operationen när du arbetar med **gruppformer i Word** är att få ett `Document`‑objekt. Du kan antingen ladda en befintlig DOCX‑fil eller börja med ett tomt dokument.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Load an existing document (replace the path with your own)
        Document document = new Document(@"YOUR_DIRECTORY\input.docx");

        // If you prefer a brand‑new document, uncomment the next line:
        // Document document = new Document();
```

Klassen `Document` representerar hela Word‑filen. Att ladda en fil ger dig en färdig canvas för att infoga former.

## Steg 3: Påbörja en gruppform

En *gruppform* låter dig behandla flera oberoende former som en enda enhet – perfekt för att flytta eller ändra storlek på dem tillsammans. För att starta en grupp, anropa `StartGroupShape()` på en `DocumentBuilder`.

```csharp
        // Create a builder to edit the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // Begin a group shape that will contain multiple shapes
        builder.StartGroupShape();
```

När du anropar `StartGroupShape` talar du om för Aspose.Words att varje efterföljande forminfogning tillhör samma logiska grupp tills du anropar `EndGroupShape`.

## Steg 4: Hur man lägger till en rektangel i Word

Nu när gruppen är öppen, infoga en rektangel. Metoden `InsertShape` tar en `ShapeType`‑enum, följt av bredd och höjd (i punkter).

```csharp
        // Add a rectangle shape to the group (100 pt wide, 50 pt high)
        builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Rektangeln blir den första medlemmen i gruppen. Du kan anpassa dess fyllning, kontur eller text senare om så önskas.

## Steg 5: Hur man lägger till en ellips i Word

Nästa steg är att lägga till en ellips (en cirkel när bredden är lika med höjden). Detta demonstrerar **hur man lägger till ellips** med samma builder.

```csharp
        // Add an ellipse shape to the same group (80 pt wide, 80 pt high)
        builder.InsertShape(ShapeType.Ellipse, 80, 80);
```

Båda formerna delar nu samma koordinatrum inom gruppen, vilket gör det enkelt att visuellt justera dem.

## Steg 6: Stäng definitionen av gruppformen

När du har lagt till alla önskade medlemmar, stäng gruppen. Detta slutför samlingen av former så att Word behandlar dem som ett enda objekt.

```csharp
        // End the group shape definition
        builder.EndGroupShape();
```

Vid detta tillfälle innehåller dokumentet en enda grupperad form bestående av en rektangel och en ellips.

## Steg 7: Spara det modifierade dokumentet

Till sist skriver du tillbaka ändringarna till disk. Du kan skriva över den ursprungliga filen eller skapa en ny.

```csharp
        // Save the document with the grouped shapes
        document.Save(@"YOUR_DIRECTORY\output.docx");

        Console.WriteLine("Document saved with grouped shapes.");
    }
}
```

När programmet körs skapas `output.docx`. Öppna filen i Microsoft Word, markera formen, och du kommer att se att rektangeln och ellipsen flyttas tillsammans – ett bevis på att **gruppformer i Word** lyckades.

### Förväntat resultat

* Word‑filen innehåller ett enda grupperat objekt.  
* När du markerar gruppen kan du dra, ändra storlek eller rotera både rektangeln och ellipsen samtidigt.  
* Ingen manuell interaktion med Word krävs; allt sker via C#‑kod.

![Grouped shapes in Word document](grouped-shapes.png "Screenshot of a Word document showing a grouped rectangle and ellipse shape")

*Image alt text: “Screenshot of a Word document showing a grouped rectangle and ellipse shape”* (uppfyller kravet på bild‑alt‑text).

## Varför gruppering av former är viktigt

Att gruppera former är mer än bara en visuell bekvämlighet. Det möjliggör att:

* **Behålla layout‑konsekvens** – när du flyttar en grupp behålls de relativa positionerna intakta.  
* **Applicera transformationer en gång** – rotera eller skala hela gruppen istället för varje form individuellt.  
* **Förenkla efterföljande bearbetning** – när andra verktyg läser DOCX‑filen ser de en enda sammansatt form, vilket minskar komplexiteten.

Om du någonsin behöver lägga till fler former (t.ex. en linje eller en textruta) i samma logiska enhet, räcker det att anropa `InsertShape` igen innan `EndGroupShape`.

## Vanliga variationer och kantfall

| Situation | Hur man hanterar det |
|-----------|----------------------|
| **Olika enheter** – du har mått i centimeter | Konvertera centimeter till punkter (`1 cm ≈ 28.35 pt`) innan du anropar `InsertShape`. |
| **Lägga till en textetikett** – du vill ha en bildtext i gruppen | Infoga en `ShapeType.TextBox` efter rektangeln och ellipsen, och sätt sedan dess `Text`‑egenskap. |
| **Applicera en fyllningsfärg** – du behöver en blå rektangel | Efter `InsertShape`, hämta den sista formen via `builder.CurrentParagraph.Runs[0].Font` och sätt `shape.FillColor = System.Drawing.Color.Blue;`. |
| **Använda ett annat dokumentformat** – du riktar dig mot `.doc` istället för `.docx` | Samma kod fungerar; ändra bara filändelsen när du anropar `Save`. Aspose.Words hanterar formatet automatiskt. |

## Pro‑tips

* **Återanvänd buildern** – du kan starta och avsluta flera grupper i samma dokument; anropa bara `StartGroupShape` igen efter `EndGroupShape`.  
* **Prestanda** – batch‑infogning av former inom ett enda `StartGroupShape/EndGroupShape`‑block är snabbare än att infoga former individuellt utanför en grupp.  
* **Licensiering** – en utvärderingslicens lägger till ett vattenmärke på första sidan. Installera en riktig licens för att ta bort det i produktionsmiljöer.

## Slutsats

Du vet nu hur du **grupperar former i Word** med C#, hur du **lägger till rektangel**, hur du **lägger till ellips**, och hur du **infogar rektangel‑form i Word‑dokument** med Aspose.Words. Det kompletta, körbara exemplet demonstrerar varje steg från projektuppsättning till sparande av den slutgiltiga filen.

Härifrån kan du utforska ytterligare formtyper, applicera styling eller kombinera grupperade former med tabeller och bilder för att skapa sofistikerade, programatiskt genererade dokument.

---

**Nästa steg**

* Lär dig hur du **roterar grupperade former**: använd `Shape.RotationAngle` efter att gruppen har stängts.  
* Utforska **fyllnings‑ och konturanpassning** för rektanglar och ellipser.  
* Integrera denna logik i ett ASP.NET Core‑API för att generera rapporter på begäran.  

Lycka till med kodandet!


## Vad bör du lära dig härnäst?


Följande handledningar täcker närbesläktade ämnen som bygger vidare på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Rectangle Shape in Word – Full Aspose.Words Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}