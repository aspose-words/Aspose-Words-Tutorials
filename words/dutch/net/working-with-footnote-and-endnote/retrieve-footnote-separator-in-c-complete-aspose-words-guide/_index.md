---
category: general
date: 2026-08-07
description: Haal de voetnootscheiding op met Aspose.Words voor .NET. Leer hoe je
  voetnoot- en eindnootscheidingen kunt extraheren, knooptypes kunt inspecteren en
  ze in C# kunt aanpassen.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: nl
lastmod: 2026-08-07
og_description: Haal de voetnootscheiding op met Aspose.Words voor .NET. Deze gids
  laat zien hoe je voetnoot‑ en eindnootscheidingstekens kunt extraheren, hun knooptypes
  kunt controleren en wijzigingen kunt opslaan.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: footnote separator ophalen in C# – stap‑voor‑stap Aspose.Words tutorial
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: Voetnootseparator ophalen in C# – volledige Aspose.Words-gids
url: /nl/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# retrieve footnote separator in C# – volledige Aspose.Words gids

Als je een **retrieve footnote separator** uit een Word‑document moet halen, laat deze tutorial precies zien hoe je dit doet met Aspose.Words voor .NET. Of je nu een document‑verwerkingsservice bouwt of de opmaak van voetnoten opruimt, je ziet een volledig, uitvoerbaar voorbeeld dat zowel voetnoot‑ als eindnoot‑scheidingstekens extraheert.

In deze gids leer je hoe je een `.docx`‑bestand laadt, de `FootnoteSeparator`‑ en `EndnoteSeparator`‑eigenschappen aanroept, de geretourneerde `Node`‑objecten inspecteert, en optioneel de scheidingslijn vervangt. Er is geen externe documentatie nodig – alles wat je nodig hebt staat hieronder.

## Vereisten

* .NET 6.0 of later (de code werkt ook op .NET Framework 4.7.2)
* Aspose.Words for .NET NuGet‑pakket (versie 24.9 of nieuwer)
* Een Word‑document dat voetnoten en/of eindnoten bevat (bijv. `Footnotes.docx`)

Je kunt het Aspose.Words‑pakket toevoegen met het volgende CLI‑commando:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Stap 1: Het project opzetten en namespaces importeren

Maak een nieuw console‑project aan of voeg de code toe aan een bestaand project. De benodigde `using`‑directieven staan hieronder vermeld.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Deze namespaces geven je toegang tot de `Document`‑klasse, de `Node`‑hiërarchie en de `NodeType`‑enumeratie die nodig zijn voor **retrieve footnote separator**‑bewerkingen.

## Stap 2: Het document laden dat voetnoten en eindnoten bevat

De eerste bewerking in elke Aspose.Words‑workflow is het laden van het bronbestand. Vervang het tijdelijke pad door de daadwerkelijke locatie van je `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Het laden van het bestand bereidt de interne knoopboom voor, wat essentieel is voor **retrieve footnote separator**, omdat de scheidingsknooppunten zich in die boom bevinden.

## Stap 3: Het footnote separator‑knooppunt ophalen

Nu kun je **retrieve footnote separator** ophalen door de `FootnoteSeparator`‑eigenschap van het `Document`‑object te benaderen. Dit knooppunt vertegenwoordigt de lijn die voetnoten scheidt van de hoofdtekst.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

De `NodeType` zal `Paragraph` zijn voor een standaard scheidingslijn. Het kennen van het knooptype helpt je bepalen of je de separator moet aanpassen of volledig wilt vervangen.

## Stap 4: Het endnote separator‑knooppunt ophalen

Op dezelfde manier kun je **retrieve endnote separator** ophalen met de `EndnoteSeparator`‑eigenschap. Dit knooppunt scheidt eindnoten van de hoofdinhoud.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Beide separator‑knooppunten delen in de meeste documenten hetzelfde `NodeType` (`Paragraph`), maar ze kunnen onafhankelijk van elkaar worden aangepast.

## Stap 5: De inhoud van de separator inspecteren of aanpassen (optioneel)

Als je het visuele uiterlijk van de separator wilt wijzigen – bijvoorbeeld een reeks streepjes vervangen door een dunne lijn – kun je het `Paragraph`‑knooppunt direct bewerken. Hieronder staat een voorbeeld dat de standaard separator‑tekst vervangt door een aangepaste tekenreeks.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Na het aanpassen van de knooppunten kun je het document opslaan om de wijzigingen in Word te zien.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Verwachte console‑output

Wanneer je het programma uitvoert met de originele `Footnotes.docx`, zie je iets vergelijkbaars met:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Als je `Footnotes_Updated.docx` opent in Microsoft Word, zullen de voetnoot‑ en eindnoot‑separators de aangepaste tekst tonen die je hebt ingevoegd.

## Veelgestelde vragen en randgevallen

**Wat als het document geen voetnoten bevat?**  
De `FootnoteSeparator`‑eigenschap retourneert nog steeds een `Paragraph`‑knooppunt omdat Word altijd een placeholder voor de separator opneemt. Het knooppunt zal leeg zijn, dus je kunt er veilig inhoud aan toevoegen of het laten zoals het is.

**Kan ik de separator voor een specifieke sectie ophalen?**  
Footnote‑ en endnote‑separators gelden voor het hele document, niet per sectie. Als je controle per sectie nodig hebt, moet je werken met `Section.FootnoteOptions` en `Section.EndnoteOptions` in plaats van de globale separator‑knooppunten.

**Werkt dit met .NET Core?**  
Ja. Aspose.Words voor .NET is cross‑platform en dezelfde code draait op Windows, Linux en macOS met .NET 6+.

**Welk knooptype mag ik verwachten?**  
Zowel `FootnoteSeparator` als `EndnoteSeparator` retourneren een `Paragraph`‑knooppunt (`NodeType.Paragraph`). Als je een ander type tegenkomt, kan het document corrupt zijn; laad het opnieuw of valideer het bronbestand.

## Volledige broncode voor snel kopiëren‑plakken

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Kopieer de code naar een `Program.cs`‑bestand, pas de bestands‑paden aan en voer `dotnet run` uit. Het programma demonstreert de volledige **retrieve footnote separator**‑workflow, van het laden van het document tot het opslaan van wijzigingen.

## Conclusie

Je weet nu hoe je **retrieve footnote separator** en **endnote separator retrieval** kunt gebruiken met Aspose.Words voor .NET, hun `document node type` kunt inspecteren en optioneel hun inhoud kunt vervangen. Deze techniek stelt je in staat om voetnoot‑opmaak te automatiseren, aangepaste scheidingslijnen te genereren of de documentstructuur te valideren in elke C#‑applicatie.

Vervolgens kun je gerelateerde onderwerpen verkennen, zoals **C# footnote extraction** voor individuele voetnoot‑teksten, of leren hoe je **modify footnote reference marks** kunt aanpassen met `FootnoteOptions`. Beide concepten bouwen direct voort op de node‑tree‑fundamenten die hier behandeld zijn.

Veel programmeerplezier, en voel je vrij om te experimenteren met verschillende separator‑stijlen om ze af te stemmen op de branding van je project!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stap‑voor‑stap uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Woorden verwerken met voetnoot en eindnoot](/words/english/net/working-with-footnote-and-endnote/)
- [Inhoud toevoegen met Document Builder in Aspose.Words voor .NET](/words/english/net/add-content-using-document-builder/)
- [Werken met voetnoot en eindnoot](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}