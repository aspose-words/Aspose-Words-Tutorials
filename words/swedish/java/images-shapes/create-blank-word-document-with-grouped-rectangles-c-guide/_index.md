---
category: general
date: 2026-07-23
description: Skapa ett tomt Word‑dokument och lägg till en rektangel i C#. Lär dig
  hur du infogar former och grupperar former i Word med Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: sv
lastmod: 2026-07-23
og_description: Skapa ett tomt Word‑dokument i C# och lär dig hur du infogar former,
  lägger till en rektangel och grupperar former i Word med Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Skapa tomt Word‑dokument med grupperade rektanglar – C#‑handledning
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Skapa tomt Word-dokument med grupperade rektanglar – C#‑guide
url: /sv/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa tomt Word-dokument med grupperade rektanglar – C#-guide

Har du någonsin behövt **create blank word document** som redan innehåller en uppsättning former, men var osäker på hur du får dem grupperade på ett snyggt sätt? Du är inte ensam. I många rapporterings- eller mallgenereringsscenarier vill du ha en ren duk med ett par rektanglar som fungerar som platshållare, och du vill att de ska röra sig tillsammans som en enhet.

I den här handledningen går vi igenom de exakta stegen för att **create blank word document**, **add rectangle shape**, och sedan **group shapes word** med hjälp av Aspose.Words-biblioteket. I slutet har du en färdig `.docx`-fil där de två rektanglarna är en del av en grupp, så all senare positionering eller storleksändring påverkar dem båda samtidigt.  

Vi kommer också att svara på de vanliga frågorna “**how to insert shapes**” och “**how to group shapes**” som dyker upp på forum och Stack Overflow. Ingen extern dokumentation behövs—allt du behöver finns här.

---

## Förutsättningar

- .NET 6 eller senare (koden kompileras även med .NET Core)  
- Aspose.Words för .NET (NuGet‑paketet `Aspose.Words`)  
- En grundläggande förståelse för C#‑syntax (om du har skrivit ett “Hello World”, är du klar)  

Om du ännu inte har installerat Aspose.Words, kör:

```bash
dotnet add package Aspose.Words
```

Det är allt—inga extra DLL‑filer, ingen COM‑interop, bara en ren NuGet‑referens.

---

## Steg 1: Skapa tomt Word-dokument och initiera byggaren

Det första vi gör är att skapa ett tomt `Document`‑objekt. Tänk på det som ett färskt papper. Sedan ansluter vi en `DocumentBuilder`, vilket är det praktiska verktyg som Aspose tillhandahåller för att infoga innehåll.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Varför detta är viktigt:** Utan en `DocumentBuilder` skulle du behöva manipulera nodträdet på låg nivå manuellt, vilket är felbenäget. Byggaren döljer XML‑komplexiteten i en `.docx`‑fil.

---

## Steg 2: Hur man infogar former – lägg till en gruppbehållare först

Aspose låter dig infoga en *group shape* som senare kan hålla andra former. Detta är grunden för **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Proffstips:** Gruppen själv är osynlig tills du lägger till barnformer, så du ser inga artefakter i det resulterande dokumentet förrän nästa steg.

---

## Steg 3: Lägg till rektangelform – de faktiska synliga objekten

Nu kommer vi att **add rectangle shape** två gånger, var och en med sin egen storlek. Metoden `InsertShape` tar en `ShapeType` och dimensioner i punkter (1 pt ≈ 1/72 tum).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Varför rektanglar?** De är den enklaste geometriska formen, perfekt för platshållare, knapp‑liknande UI‑mockups eller enkla grafiska element.

---

## Steg 4: Hur man grupperar former – fäst rektanglarna till gruppen

Med rektanglarna skapade, **how to group shapes** vi nu genom att lägga till dem som barn till gruppformen som vi infogade tidigare.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Vad händer under huven?** Gruppformen blir föräldranoden i dokumentets XML‑träd. Att flytta gruppen flyttar båda rektanglarna tillsammans och bevarar deras relativa positioner.

---

## Steg 5: Spara dokumentet – du har nu en Word‑fil med grupperade former

Till sist sparar vi dokumentet till disk. Ändra sökvägen till en plats som finns på din maskin.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Det är hela programmet. Kör det, öppna `GroupShape.docx`, och du kommer att se två rektanglar som sitter tillsammans. Om du markerar en, markeras hela gruppen—precis vad **group shapes word** ska göra.

---

## Fullständig källkod på ett ställe

För enkelhetens skull, här är det kompletta, kopiera‑och‑klistra‑klara exemplet:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Förväntat resultat:** När du öppnar `GroupShape.docx` visas en tom sida med två rektanglar grupperade tillsammans. Att markera en rektangel markerar automatiskt den andra, vilket bekräftar att gruppering lyckades.

---

## Vanliga frågor & hantering av kantfall

### Vad händer om jag behöver fler än två former?

Fortsätt bara anropa `builder.InsertShape(...)` och `group.AppendChild(...)` för varje ny form. Gruppen kan hålla valfritt antal barn.

### Kan jag sätta fyllningsfärg eller kant på rektanglarna?

Absolut. Efter att du skapat en rektangel kan du justera dess `FillColor`, `OutlineColor` och `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Hur flyttar jag hela gruppen efter att den har skapats?

Använd gruppens `Left` och `Top`‑egenskaper, mätta i punkter:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### Vad gäller skalning av gruppen?

Ställ in `group.Width` och `group.Height` eller använd `group.ScaleX` / `group.ScaleY`. Barnrektanglarna behåller sina proportioner i förhållande till gruppen.

### Fungerar detta med äldre .doc‑filer?

Aspose.Words abstraherar filformatet, så samma kod fungerar för `.doc` och `.docx`. Den enda begränsningen är att vissa nyare formfunktioner kan nedskalades när du sparar till det äldre binära formatet.

---

## Proffstips för produktionsklar kod

- **Dispose of resources** – Lägg `Document` i ett `using`‑block om du hanterar stora filer för att frigöra minnet snabbt.  
- **Error handling** – Fånga `Aspose.Words.Fonts.FontSettingsException` om du planerar att bädda in anpassade typsnitt.  
- **Performance** – När du infogar många former, inaktivera layout‑uppdateringar tillfälligt med `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` och återaktivera efteråt.

---

## Slutsats

Du vet nu **how to create blank word document**, **add rectangle shape**, och **group shapes word** med Aspose.Words i C#. Exemplet täcker de grundläggande “**how to insert shapes**” och “**how to group shapes**” stegen, förklarar varför varje rad finns, och berör även anpassning, kantfall och bästa praxis.

Nästa steg kan vara att utforska **how to insert images**, **add text inside grouped shapes**, eller **export the document to PDF**—alla följer samma mönster med `DocumentBuilder` och formmanipulation. Fortsätt experimentera; Aspose‑API:et är så omfattande att det kan hantera nästan alla Word‑automatiseringsscenarier du kan föreställa dig.

Lycka till med kodningen, och tveka inte att lämna en kommentar om du stöter på problem!

## Vad bör du lära dig härnäst?

Följande handledningar täcker närbesläktade ämnen som bygger på teknikerna som demonstrerats i den här guiden. Varje resurs innehåller kompletta fungerande kodexempel med steg‑för‑steg‑förklaringar för att hjälpa dig bemästra ytterligare API‑funktioner och utforska alternativa implementationsmetoder i dina egna projekt.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}