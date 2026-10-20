---
category: general
date: 2026-02-21
description: Rij verbergen in tabel met C# en Aspose.Words. Leer hoe je een rij verbergt,
  hoe je een rij in Word verbergt, en hoe je een rij uit een tabel snel en veilig
  verwijdert.
draft: false
keywords:
- hide row in table
- how to hide row
- remove row from table
- hide row in word
- hide row c#
language: nl
og_description: Rij verbergen in tabel met C# en Aspose.Words. Deze gids laat zien
  hoe je een rij verbergt, een rij uit een tabel verwijdert en een rij verbergt in
  Word‑documenten.
og_title: Rij verbergen in tabel met C# – Snelle, betrouwbare methode
tags:
- C#
- Aspose.Words
- Word Automation
title: Rij verbergen in tabel met C# – Eenvoudige gids voor het verwijderen van tabelrijen
url: /nl/net/programming-with-tables/hide-row-in-table-with-c-simple-guide-to-removing-table-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rij verbergen in tabel – Complete C# Tutorial

Heb je ooit **rij verbergen in tabel** nodig gehad bij het programmatisch genereren van een Word‑document? Je bent niet de enige—ontwikkelaars vragen constant *hoe een rij te verbergen* zonder de lay-out te breken. Het goede nieuws? Met een paar regels C# en de krachtige Aspose.Words‑bibliotheek kun je een rij verbergen, waardoor deze effectief uit de uiteindelijke output wordt verwijderd, en houd je code schoon.

In deze gids lopen we het volledige proces stap voor stap door: een `.docx` laden, de exacte rij selecteren, de `Hidden`‑eigenschap instellen en het resultaat opslaan. Aan het einde weet je precies hoe je een rij in Word kunt verbergen, hoe je een rij uit een tabel kunt verwijderen als je liever verwijdert, en heb je een kant‑klaar fragment dat je in elk .NET‑project kunt gebruiken. Geen externe referenties nodig—alleen de code en duidelijke uitleg.

**Wat je krijgt**  
- Een stap‑voor‑stap walkthrough van de C#‑API.  
- Volledige, uitvoerbare code (inclusief imports).  
- Tips voor randgevallen zoals verborgen rijen in samengevoegde cellen.  
- Pro‑tips over wanneer *rij verbergen* versus *rij uit tabel verwijderen*.

> **Voorvereiste:** Visual Studio (of een andere C#‑IDE) en het Aspose.Words for .NET NuGet‑pakket (versie 23.9 of later). Als je nieuw bent met Aspose.Words, is de bibliotheek een puur beheerde oplossing—geen Office‑installatie nodig.

---

## Rij verbergen in tabel – Stap‑voor‑stap implementatie

Hieronder staat het volledige, zelfstandige voorbeeld. Het demonstreert de **primaire** taak—*rij verbergen in tabel*—en laat ook zien hoe je *rij uit tabel kunt verwijderen* als je besluit deze te verwijderen.

![Voorbeeld van rij verbergen in tabel](hide-row-in-table.png "Schermafbeelding van een Word‑tabel met de derde rij verborgen")

### 1. Laad het bron‑document  

Eerst moeten we het Word‑bestand in het geheugen laden. De `Document`‑klasse vertegenwoordigt het volledige bestand.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*Waarom dit belangrijk is:* Het laden van het document geeft je toegang tot secties, bodies en tabellen. Zonder deze stap kun je rijen niet manipuleren.

### 2. Zoek de gewenste tabel  

Voor de eenvoud pakken we de eerste tabel in de eerste sectie, maar je kunt zoeken op index, naam of zelfs inhoud.

```csharp
// Step 2: Get the first table in the document body
Table table = doc.FirstSection.Body.Tables[0];
```

> **Tip:** Als je document meerdere tabellen bevat, doorloop dan `doc.GetChildNodes(NodeType.Table, true)` en kies de gewenste.

### 3. Kies de rij die je wilt verbergen  

Hier richten we ons op de derde rij (nul‑gebaseerde index `2`). Je kunt ook `Rows.Count` gebruiken om te verifiëren dat de index bestaat.

```csharp
// Step 3: Choose the row you want to hide (third row, index 2)
Row rowToHide = table.Rows[2];
```

*Waarom dit belangrijk is:* Het selecteren van de juiste rij is de kern van **hoe een rij te verbergen**. Een verkeerde index verbergt de verkeerde inhoud.

### 4. Verberg de geselecteerde rij  

Het instellen van `Hidden = true` vertelt Aspose.Words de rij over te slaan bij het opslaan van het document. De rij blijft bestaan in het objectmodel, zodat je deze later kunt weergeven indien nodig.

```csharp
// Step 4: Hide the selected row – it will be omitted from the output
rowToHide.Hidden = true;
```

> **Pro tip:** Als je echt *rij uit tabel wilt verwijderen* in plaats van verbergen, roep dan `table.Rows.Remove(rowToHide);` aan. Verbergen behoudt rij‑metadata, wat handig kan zijn voor conditionele opmaak.

### 5. Sla het bijgewerkte document op  

Tot slot schrijf je de wijzigingen terug naar de schijf.

```csharp
// Step 5: Save the document with the hidden row applied
doc.Save(@"C:\MyDocs\output.docx");
```

Wanneer je `output.docx` in Word opent, zal de derde rij onzichtbaar zijn—precies wat **rij verbergen in Word** in de praktijk betekent.

---

## Hoe een rij verbergen – Veelvoorkomende variaties & randgevallen

### Meerdere rijen verbergen  

Als je meerdere rijen moet verbergen, loop dan door de collectie:

```csharp
int[] rowsToHide = { 1, 3, 5 }; // zero‑based indexes
foreach (int i in rowsToHide)
{
    table.Rows[i].Hidden = true;
}
```

### Omgaan met samengevoegde cellen  

Een verborgen rij die een verticaal samengevoegde cel bevat, kan lay‑outwaarschuwingen veroorzaken. De veilige aanpak is om de samenvoeging te splitsen vóór het verbergen:

```csharp
Cell mergedCell = rowToHide.Cells[0];
if (mergedCell.CellFormat.VerticalMerge != CellMerge.None)
{
    // Break the merge to avoid Word warnings
    mergedCell.CellFormat.VerticalMerge = CellMerge.None;
}
rowToHide.Hidden = true;
```

### Compatibiliteit met oudere Word‑versies  

Aspose.Words schrijft het `w:hideMark`‑attribuut, dat wordt begrepen door Word 2007+ en LibreOffice. Als je richt op Word 97‑2003 (`.doc`), wordt de verborgen rij nog steeds weggelaten, maar complexe tabellen kunnen anders worden weergegeven. Houd je aan `.docx` voor voorspelbare resultaten.

### Wanneer *rij verbergen* versus *rij uit tabel verwijderen*  

- **Rij verbergen** – Houd de rij voor later weergeven, behoud de rijhoogte voor paginabreak‑berekeningen.  
- **Rij verwijderen** – Verminder de bestandsgrootte, verwijder de gegevens permanent. Gebruik `table.Rows.Remove(row)` als je zeker weet dat de rij niet meer nodig is.

---

## Pro‑tips & valkuilen

- **Pro tip:** Controleer altijd `table.Rows.Count` voordat je een index benadert om `ArgumentOutOfRangeException` te voorkomen.  
- **Let op:** Verborgen rijen nemen nog steeds deel aan tabelberekeningen zoals totale hoogte. Als je onverwachte spatiëring ziet, overweeg dan `row.Height = 0` in te stellen na het verbergen.  
- **Prestaties:** Rijen verbergen is goedkoop; rijen verwijderen triggert een herindeling van de hele tabel, wat trager kan zijn bij enorme documenten.  
- **Testen:** Open het opgeslagen bestand in Word en gebruik **Reveal Formatting** (`Shift+F1`) om te verifiëren dat de `Hidden`‑vlag van de rij is ingesteld.

---

## Volledig werkend voorbeeld (klaar om te kopiëren‑plakken)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;

class HideRowInTableDemo
{
    static void Main()
    {
        // Load the source document (ensure the path exists)
        Document doc = new Document(@"C:\MyDocs\input.docx");

        // Get the first table – adapt if you have multiple tables
        Table table = doc.FirstSection.Body.Tables[0];

        // Verify we have at least three rows
        if (table.Rows.Count < 3)
        {
            Console.WriteLine("The table doesn't have a third row to hide.");
            return;
        }

        // Choose the third row (index 2) and hide it
        Row rowToHide = table.Rows[2];
        rowToHide.Hidden = true; // This hides the row in the output document

        // Save the modified document
        doc.Save(@"C:\MyDocs\output.docx");
        Console.WriteLine("Row hidden successfully. Check output.docx.");
    }
}
```

**Verwacht resultaat:** Open `output.docx` en je ziet dat de tabel de derde rij mist, terwijl de rest van de inhoud onaangeroerd blijft. De verborgen rij maakt nog steeds deel uit van het documentmodel, dus je kunt later `row.Hidden = false` instellen om deze weer zichtbaar te maken.

---

## Conclusie

We hebben zojuist **hoe een rij te verbergen** in een Word‑tabel met C# behandeld. Door het document te laden, de tabel te vinden, de doelrij te selecteren, deze als verborgen te markeren en op te slaan, bereik je een nette *rij verbergen in tabel*‑operatie zonder gegevens te verwijderen. Hetzelfde patroon laat je *rij uit tabel verwijderen* als je een permanente wijziging nodig hebt, en de extra tips zorgen ervoor dat je veelvoorkomende valkuilen bij samengevoegde cellen of oudere Word‑versies vermijdt.

Klaar voor de volgende uitdaging? Probeer deze techniek te combineren met conditionele logica—rijen verbergen op basis van gebruikersinvoer, of dynamische rapporten genereren waarbij bepaalde secties automatisch verdwijnen. Je kunt ook **rij verbergen in Word** verkennen voor kopteksten, voetteksten of zelfs volledige secties.

Heb je vragen over *rij verbergen c#* of heb je hulp nodig bij het integreren hiervan in een grotere workflow? Laat een reactie achter hieronder of bekijk onze gerelateerde tutorials over **tabellen manipuleren in Word met Aspose.Words**. Veel plezier met coderen!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}