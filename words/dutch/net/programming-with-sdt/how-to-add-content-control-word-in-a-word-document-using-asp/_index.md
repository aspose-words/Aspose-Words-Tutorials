---
category: general
date: 2026-10-07
description: Leer hoe je een inhoudsbesturingselement toevoegt in een Word‑document
  met Aspose.Words. Deze gids legt ook uit hoe je een inhoudsbesturingselement maakt
  voor een veld met een werknemers‑ID.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add content control word
- how to create content control
- add employee id field
- Aspose.Words content control
- C# Structured Document Tag
language: nl
lastmod: 2026-10-07
og_description: Voeg een inhoudsbesturingselement toe in een Word‑document met Aspose.Words.
  Volg deze volledige tutorial om te leren hoe je een inhoudsbesturingselement maakt
  en een veld voor een medewerker‑ID toevoegt.
og_image_alt: Screenshot of a Word document showing an employee ID content control
  created with Aspose.Words
og_title: Inhoudsbesturingselement toevoegen in Word met Aspose.Words – stapsgewijze
  handleiding
schemas:
- author: Aspose
  dateModified: '2026-10-07'
  description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  headline: How to add content control word in a Word document using Aspose.Words
  type: TechArticle
- description: Learn how to add content control word in a Word document with Aspose.Words.
    This guide also explains how to create content control for an employee ID field.
  name: How to add content control word in a Word document using Aspose.Words
  steps:
  - name: Open `EmployeeForm.docx` in Word.
    text: Open `EmployeeForm.docx` in Word.
  - name: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
    text: Click the gray box that says **Enter ID** – it should be replaced by **12345**.
  - name: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
    text: Open the **Developer** tab → **Design Mode** to see the control’s properties
      (Title = *EmployeeID*).
  type: HowTo
tags:
- Aspose.Words
- content control
- C#
title: Hoe een inhoudsbesturingselement toevoegen aan een Word‑document met Aspose.Words
url: /nl/net/programming-with-sdt/how-to-add-content-control-word-in-a-word-document-using-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe een content control word toe te voegen aan een Word‑document met Aspose.Words

Als je een **content control word** aan een Word‑bestand moet toevoegen, laat deze tutorial je precies zien hoe je dat doet met de Aspose.Words for .NET‑bibliotheek. Of je nu een formulier‑achtig document maakt of gegevensinvoer automatiseert, je leert **hoe je een content control** maakt die de ID van een werknemer in één stap vastlegt.

In deze gids zul je:

* Een leeg Word‑document programmatically aanmaken.  
* Een platte‑tekst Structured Document Tag (SDT) invoegen die fungeert als een content control.  
* De control vullen met een werknemer‑ID en het bestand opslaan.  

De enige vereisten zijn een recente versie van .NET (4.6+ aanbevolen) en een Aspose.Words‑licentie (of de gratis proefversie). Er zijn geen extra NuGet‑pakketten nodig naast `Aspose.Words`.

## Content control word toevoegen met Aspose.Words

De eerste grote stap is het aanmaken van de content control zelf. In Aspose.Words wordt een **content control** weergegeven door de `StructuredDocumentTag`‑klasse. Door een SDT aan het document toe te voegen, voeg je effectief een **content control word** toe die later in Microsoft Word kan worden bewerkt of programmatisch kan worden verwerkt.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// 1️⃣ Create a new blank document and a DocumentBuilder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Waarom dit belangrijk is*: `DocumentBuilder` biedt een cursor‑achtige interface waarmee je knooppunten (alinea's, tabellen, SDT’s, enz.) op de huidige positie kunt invoegen. Beginnen met een schoon document zorgt ervoor dat de content control precies op de gewenste plek verschijnt.

## Hoe een content control te maken voor een werknemer‑ID‑veld

Configureer vervolgens de SDT zodat deze fungeert als een platte‑tekst content control die de werknemersidentificatie bevat. De eigenschap `Title` is wat Word toont in het **Properties**‑paneel, terwijl `PlaceholderName` een hint geeft aan de gebruiker.

```csharp
// 2️⃣ Create a plain‑text Structured Document Tag (SDT) and set its metadata
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true);
sdt.Title = "EmployeeID";            // Visible title in Word's UI
sdt.PlaceholderName = "Enter ID";    // Placeholder text shown when empty
```

*Waarom dit belangrijk is*: Het instellen van `Title` op **EmployeeID** maakt de control zelfbeschrijvend, wat handig is wanneer je later waarden extraheert met `StructuredDocumentTag.GetText()`. De placeholder verbetert de gebruikerservaring door het verwachte formaat aan te geven.

### Werknemer‑ID‑veld toevoegen binnen de content control

Voeg nu de SDT in het document in op de huidige locatie van de builder en schrijf het standaard werknemersnummer.

```csharp
// 3️⃣ Insert the SDT into the document at the current builder position
builder.InsertNode(sdt);

// 4️⃣ Add default content inside the SDT (e.g., an employee ID)
builder.Writeln("12345");   // This text becomes the initial value of the control
```

*Waarom dit belangrijk is*: `InsertNode` plaatst de SDT in de documentboom. De daaropvolgende `Writeln` schrijft inhoud **binnen** de control omdat de cursor van de builder zich nog steeds binnen het SDT‑knooppunt bevindt. Als je `Writeln` vóór het invoegen van de SDT had aangeroepen, zou de tekst buiten de control verschijnen.

## Document opslaan en de content control verifiëren

Sla tenslotte het document op schijf op. Het opgeslagen `.docx`‑bestand zal de content control bevatten die je in Microsoft Word kunt openen om de placeholder en de standaard werknemer‑ID te zien.

```csharp
// 5️⃣ Save the document with the SDT to a file
doc.Save(@"C:\Temp\EmployeeForm.docx");
```

*Waarom dit belangrijk is*: Het gebruik van een absoluut of relatief pad geeft je controle over waar het bestand wordt opgeslagen. Aspose.Words schrijft automatisch de benodigde XML‑onderdelen voor de content control, dus er zijn geen extra stappen nodig.

### Snelle verificatiestappen

1. Open `EmployeeForm.docx` in Word.  
2. Klik op het grijze vakje dat **Enter ID** toont – dit moet worden vervangen door **12345**.  
3. Open het **Developer**‑tabblad → **Design Mode** om de eigenschappen van de control te bekijken (Title = *EmployeeID*).

Als de control niet verschijnt, controleer dan of je Aspose.Words ≥ 23.10 gebruikt; eerdere versies hadden een andere constructor‑handtekening voor `StructuredDocumentTag`.

## Optionele variaties en randgevallen

| Scenario | Hoe de code aan te passen |
|----------|----------------------------|
| **Gebruik een rich‑text control** in plaats van platte‑tekst | Verander `SdtType.PlainText` naar `SdtType.RichText`. |
| **Voeg de control toe aan een bestaand document** | Laad het bestand met `new Document("Existing.docx")` en plaats de builder op de gewenste bladwijzer voordat je de SDT invoegt. |
| **Vergrendel de content control zodat gebruikers de waarde niet kunnen bewerken** | Stel `sdt.LockContentControl = true;` in na het aanmaken van de SDT. |
| **Pas een aangepaste tag toe voor latere extractie** | Gebruik `sdt.Tag = "EmpIdTag";` en haal deze later op met `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`. |
| **Maak een herhalende content control (meerdere ID’s)** | Maak de SDT binnen een tabelrij en dupliceer de rij indien nodig. |

**Pro tip**: Ruim altijd het `Document`‑object op (of wikkel het in een `using`‑blok) wanneer je in een langdurige service werkt, zodat native resources direct worden vrijgegeven.

## Conclusie

Je weet nu hoe je een **content control word** kunt toevoegen aan een Word‑document met Aspose.Words, hoe je **een content control** maakt die een werknemer‑identificatie vastlegt, en hoe je **een werknemer‑ID‑veld** programmatically toevoegt. Door de bovenstaande stappen te volgen kun je gestructureerde, bewerkbare velden in elk gegenereerd document embedden, waardoor het eenvoudig wordt om gegevens consistent te verzamelen of weer te geven.

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **content controls binden aan XML‑data**, **herhalende content controls maken voor tabellen**, of **de Aspose.Words‑API gebruiken om waarden uit ingevulde controls te extraheren**. Deze uitbreidingen stellen je in staat volledige, data‑gedreven Word‑formulieren te bouwen zonder het bestand handmatig te openen. Veel programmeerplezier!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden gedemonstreerd. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Add a Combo Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Add a Check Box Form Field to a Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}