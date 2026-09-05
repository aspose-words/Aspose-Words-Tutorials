---
category: general
date: 2026-09-05
description: Maak een Word‑document met Aspose.Words, stel placeholder‑tekst in, voeg
  een controle toe en sla het document op als docx in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- set placeholder text
- save document as docx
- how to add control
- how to create tag
language: nl
lastmod: 2026-09-05
og_description: Maak een Word‑document met Aspose.Words voor .NET, stel placeholder‑tekst
  in, voeg een besturingselement toe en sla het document op als docx. Volg deze volledige
  tutorial.
og_image_alt: Screenshot showing a word document created with a content control placeholder
og_title: Maak een Word‑document met inhoudsbesturingselementen in C# – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create word document with Aspose.Words, set placeholder text, add control,
    and save document as docx in C#.
  headline: How to create word document with content controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Document Generation
title: Hoe maak je een Word-document met inhoudsbesturingselementen in C#
url: /nl/net/programming-with-sdt/how-to-create-word-document-with-content-controls-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een Word-document met content controls maken in C#

Als je een **Word-document** moet maken dat gestructureerde content controls bevat, laat deze gids je zien hoe je een platte‑tekst tag toevoegt, **placeholder‑tekst instelt**, en **het document opslaat als docx** met Aspose.Words for .NET. Het voorbeeld is volledig uitvoerbaar en demonstreert de aanbevolen aanpak voor programmatische Word‑generatie.

Je leert hoe je:

* Een leeg Word‑bestand initialiseren met `Document` en `DocumentBuilder`.
* **Hoe een control toe te voegen** (een `StructuredDocumentTag`) aan de documentbody.
* **Hoe een tag te maken** met een titel en placeholder die de eindgebruiker begeleidt.
* Het resultaat opslaan met `document.Save`, zodat het bestand een geldige `.docx` is.

De tutorial gaat ervan uit dat je een basis C# ontwikkelomgeving hebt en een licentie voor Aspose.Words (de gratis evaluatie werkt voor leerdoeleinden).

---

## Prerequisites

| Vereiste | Reden |
|----------|-------|
| .NET 6.0 of later | Levert de runtime voor Aspose.Words for .NET. |
| Aspose.Words for .NET NuGet package | Levert de klassen `Document`, `DocumentBuilder` en `StructuredDocumentTag`. |
| IDE zoals Visual Studio 2022 | Maakt het eenvoudig om het voorbeeld uit te voeren en te debuggen. |

Installeer het pakket met de .NET CLI:

```bash
dotnet add package Aspose.Words
```

---

## Stap 1: Het project instellen om **Word-document** te **maken**

Maak een nieuw console‑project (of voeg de code toe aan een bestaand project). De eerste regels maken een leeg Word‑bestand en een `DocumentBuilder` aan waarmee je inhoud kunt schrijven.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Initialize a new empty document.
Document document = new Document();

// Obtain a builder positioned at the start of the document.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` vertegenwoordigt de bestandsstructuur, terwijl `DocumentBuilder` het invoegpunt bijhoudt. Dit patroon is de basis voor elk Word‑generatiescenario.

---

## Stap 2: **Hoe een control toe te voegen** – maak een platte‑tekst content control (tag)

Een content control in Word wordt een *structured document tag* (SDT) genoemd. De volgende code maakt een platte‑tekst SDT, kent een titel toe en definieert de placeholder die verschijnt wanneer het document wordt geopend.

```csharp
// Create a plain‑text StructuredDocumentTag (SDT) at block level.
StructuredDocumentTag contentControl = new StructuredDocumentTag(
    document, SdtType.PlainText, MarkupLevel.Block);

// Assign a meaningful title – useful for later retrieval.
contentControl.Title = "CustomerName";

// Define the placeholder text that prompts the user.
contentControl.PlaceholderName = "Enter name";

// Insert the tag at the builder's current cursor location.
builder.InsertNode(contentControl);
```

**Waarom dit belangrijk is:**  
* De `Title`‑eigenschap fungeert als een stabiele identifier, waardoor je later de control programmatisch kunt vinden of vervangen.  
* `PlaceholderName` biedt visuele begeleiding aan de documentgebruiker zonder extra UI‑code.

![Word-document maken met content control placeholder](image.png)

*Afbeeldingsalt‑tekst: Word-document maken met een content control die placeholder‑tekst toont.*

---

## Stap 3: Verplaats de cursor naar binnen de control en schrijf standaardtekst

Na het invoegen van de control wijst de cursor van de builder nog steeds naar buiten. Verplaats de cursor naar de tag zodat volgende schrijfacties deel uitmaken van de inhoud van de control.

```csharp
// Position the builder inside the newly added content control.
builder.MoveTo(contentControl);

// Write default text that appears when the placeholder is cleared.
builder.Write("John Doe");
```

Als je de control leeg wilt laten, laat dan de `Write`‑aanroep weg. De placeholder blijft zichtbaar totdat de gebruiker een waarde invoert.

---

## Stap 4: **Placeholder‑tekst instellen** (alternatieve aanpak)

Soms moet je de placeholder wijzigen nadat de tag is aangemaakt. Je kunt de `PlaceholderName`‑eigenschap direct aanpassen:

```csharp
contentControl.PlaceholderName = "Type the customer's full name here";
```

Het wijzigen van de placeholder **heeft geen** invloed op de bestaande inhoud, waardoor het veilig is om UI‑hints bij te werken zonder gebruikersgegevens te wijzigen.

---

## Stap 5: **Document opslaan als docx**

Sla het in‑memory document op naar een fysiek bestand. De `Save`‑methode bepaalt automatisch het formaat op basis van de bestandsextensie.

```csharp
// Save the document in DOCX format.
document.Save("YOUR_DIRECTORY/SdtExample.docx");
```

Als je een ander formaat nodig hebt (bijv. PDF of HTML), geef dan een `SaveFormat`‑enumwaarde op:

```csharp
document.Save("SdtExample.pdf", SaveFormat.Pdf);
```

---

## Stap 6: Volledig, uitvoerbaar voorbeeld

Door de onderdelen samen te voegen ontstaat een beknopt programma dat **laat zien hoe een tag te maken**, de placeholder instelt, en **het document opslaat als docx**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Create a plain‑text content control (tag).
        StructuredDocumentTag sdt = new StructuredDocumentTag(
            document, SdtType.PlainText, MarkupLevel.Block);
        sdt.Title = "CustomerName";
        sdt.PlaceholderName = "Enter name";

        // 3. Insert the control and move inside it.
        builder.InsertNode(sdt);
        builder.MoveTo(sdt);

        // 4. Write default text (optional).
        builder.Write("John Doe");

        // 5. Save the file as DOCX.
        document.Save("SdtExample.docx");
        Console.WriteLine("Word document created successfully.");
    }
}
```

**Verwachte output:**  
Het uitvoeren van het programma maakt `SdtExample.docx` aan met een enkele alinea met een platte‑tekst content control met de titel *CustomerName*. De control toont “John Doe” als initiële inhoud; als de standaardtekst wordt verwijderd, verschijnt de placeholder “Enter name” in lichtgrijs wanneer het bestand wordt geopend in Microsoft Word.

---

## Veelvoorkomende variaties en randgevallen

| Scenario | Aanbevolen aanpassing |
|----------|------------------------|
| **Meerdere controls** | Herhaal stappen 2‑4 voor elk veld en geef elk een unieke `Title`. |
| **Rich‑text control** | Gebruik `SdtType.RichText` in plaats van `PlainText`. |
| **Repeating section** | Kies `SdtType.RepeatingSection` en voeg kind‑controls toe binnen de sectie. |
| **Bestaand document** | Laad een bestaand bestand met `new Document("template.docx")` en voeg controls in op de gewenste locatie. |
| **Unicode placeholder** | Stel `PlaceholderName` in op een willekeurige Unicode‑string; Word rendert deze correct. |
| **Grote documenten** | Dispose `DocumentBuilder` na gebruik om geheugen vrij te maken (`builder.Dispose();`). |

**Pro tip:** Wanneer je later de door de gebruiker ingevoerde waarde wilt ophalen, roep je `StructuredDocumentTag.GetText()` aan nadat het document is opgeslagen en opnieuw is geopend. Deze methode retourneert de innerlijke tekst zonder de placeholder.

**Let op:** Het gebruik van een placeholder die overeenkomt met de standaardtekst kan verwarring veroorzaken, omdat Word de placeholder verbergt zodra er tekst aanwezig is. Houd ze verschillend.

---

## Conclusie

Je weet nu hoe je **een Word-document** programmatisch kunt **maken**, **een control kunt toevoegen**, **een tag kunt maken**, **placeholder‑tekst kunt instellen**, en **het document kunt opslaan als docx** met Aspose.Words for .NET. Het volledige voorbeeld kan in elk C#‑project worden gekopieerd en uitgebreid om extra control‑typen, herhalende secties of integratie met gegevensbronnen te ondersteunen.

Volgende stappen die je kunt verkennen zijn onder andere:

* Het toevoegen van **image content controls** (`SdtType.Picture`) om door de gebruiker geleverde afbeeldingen in te sluiten.  
* Het gebruik van **binding** om SDT's te koppelen aan XML‑gegevens voor mail‑merge‑scenario's.  
* Het converteren van de gegenereerde DOCX naar PDF (`SaveFormat.Pdf`) voor distributie.

Experimenteer met verschillende tag‑typen en placeholder‑berichten om ze af te stemmen op de workflow van je applicatie. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Word-document maken met Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Word-document maken met tabel met Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Word-document maken met kop‑ en voettekst met Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}