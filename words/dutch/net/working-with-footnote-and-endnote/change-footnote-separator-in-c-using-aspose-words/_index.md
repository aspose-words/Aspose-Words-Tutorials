---
category: general
date: 2026-08-04
description: Voetnootseparator wijzigen in C# met Aspose.Words – leer hoe je de voetnootseparator
  bewerkt en de eindnootseparator wijzigt in Word‑documenten.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: nl
lastmod: 2026-08-04
og_description: Wijzig de voetnootscheiding in C# met Aspose.Words. Deze gids laat
  zien hoe je de voetnootscheiding bewerkt, de eindnootscheiding aanpast en het bijgewerkte
  document opslaat.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Voetnootseparator wijzigen in C# – volledige Aspose.Words-gids
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Voetnootseparator wijzigen in C# met Aspose.Words
url: /nl/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Wijzig voetnootseparator in C# met Aspose.Words

Als je de **footnote separator wijzigen** in een Word‑document moet, leidt deze tutorial je door de exacte stappen met Aspose.Words voor .NET. Of je nu de standaardlijn wilt vervangen door een symbool, of een andere stijl wilt toepassen op eindnootseparatoren, de onderstaande code behandelt de volledige workflow.

Je leert ook hoe je de **footnote separator bewerken** en de gerelateerde **endnote separator wijzigen** operatie, zodat hetzelfde document een consistente opmaak heeft voor zowel voetnoten als eindnoten. Er zijn geen externe tools nodig—slechts een paar regels C#.

## Wat je zult bereiken

* Laad een bestaand *.docx*‑bestand dat voetnoten en eindnoten bevat.  
* Toegang tot de separator‑knooppunten voor voetnoten, voortzetting van voetnoten en eindnoten.  
* Vervang het separator‑teken (bijvoorbeeld de standaardlijn vervangen door een sterretje).  
* Sla het gewijzigde document op zonder andere inhoud te verliezen.  

De tutorial gaat ervan uit dat je een basisbegrip van C# hebt en het **Aspose.Words** NuGet‑pakket (versie 24.9 of later) hebt geïnstalleerd.

---

## Vereisten

| Vereiste | Reden |
|-------------|--------|
| .NET 6.0+ of .NET Framework 4.7.2+ | Vereiste runtime voor Aspose.Words |
| Aspose.Words for .NET library | Biedt de `Document` en `FootnoteOptions` API's |
| Een invoer‑Word‑bestand (`input.docx`) met ten minste één voetnoot of eindnoot | Demonstreert het wijzigen van de separator |

Je kunt Aspose.Words aan je project toevoegen met de volgende CLI‑opdracht:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Stap 1: Laad het document met voetnoten

De eerste bewerking is het lezen van het bronbestand in een `Document`‑object. Dit object vertegenwoordigt het volledige Word‑bestand in het geheugen en geeft je toegang tot al zijn knooppunten.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Waarom dit belangrijk is:** Het laden van het document is het startpunt voor elke manipulatie. Als het bestand niet gevonden kan worden, gooit Aspose.Words een `FileNotFoundException`, dus zorg ervoor dat het pad correct is voordat je doorgaat.

---

## Stap 2: Toegang tot de voetnoot‑ en eindnoot‑separator‑knooppunten

`Document.FootnoteOptions` biedt drie separator‑knooppunten:

* `Separator` – de lijn die verschijnt na de voetnootverzameling op de eerste pagina.  
* `ContinuationSeparator` – de lijn die wordt gebruikt wanneer voetnoten doorgaan op de volgende pagina.  
* `EndnoteSeparator` – de lijn die de hoofdtekst scheidt van de eindnootlijst.

Je haalt deze knooppunten op als generieke `Node`‑objecten en cast ze vervolgens naar `Run` om de tekst te wijzigen.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Waarom dit belangrijk is:** Deze knooppunten zijn de enige plaatsen waar het visuele separator‑teken zich bevindt. Het wijzigen van een ander knooppunt (bijv. een gewone alinea) heeft geen invloed op de voetnootopmaak.

---

## Stap 3: Wijzig het voetnoot‑separator‑teken

De meest voorkomende eis is om de standaardlijn te vervangen door een symbool, zoals een sterretje (`*`). Omdat de separator is opgeslagen als een `Run`, kun je veilig de `Text`‑eigenschap wijzigen.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Waarom dit belangrijk is:** Direct het bewerken van `Run.Text` werkt de visuele weergave bij in het uiteindelijke document zonder andere voetnootinhalte te beïnvloeden. Hetzelfde patroon kan worden gebruikt om elke tekenreeks toe te passen, inclusief Unicode‑symbolen.

---

## Stap 4: Wijzig de eindnoot‑separator (optioneel)

Als je ook de **endnote separator** moet wijzigen, volgt het proces het voetnoot‑wijzigingsproces. Vervang de tekst van `endnoteSeparator` door het gewenste teken.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Waarom dit belangrijk is:** Eindnoten worden vaak anders opgemaakt dan voetnoten. Het bieden van een aparte separator stelt je in staat om visuele consistentie met de ontwerprichtlijnen van je document te behouden.

---

## Stap 5: Sla het gewijzigde document op

Na alle wijzigingen, sla je de aanpassingen op met `Document.Save`. Je kunt het oorspronkelijke bestand overschrijven of naar een nieuwe locatie schrijven.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Waarom dit belangrijk is:** `Save` schrijft de in‑memory weergave naar schijf, waarbij alle andere elementen (stijlen, afbeeldingen, tabellen) ongewijzigd blijven.

---

## Volledig, uitvoerbaar voorbeeld

Alle onderdelen samengevoegd, hier is een zelfstandige console‑applicatie die de volledige workflow demonstreert:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Verwacht resultaat:** Open *ModifiedSeparators.docx* in Microsoft Word. De voetnoot‑separatorlijn onderaan de eerste voetnootpagina zal nu een enkel sterretje (`*`) zijn. Als het document eindnoten bevat, zal de lijn die de hoofdtekst van de eindnootlijst scheidt verschijnen als een streepje (`-`). Alle andere inhoud (tekst, afbeeldingen, tabellen) blijft onaangeroerd.

---

## Veelgestelde vragen & afhandeling van randgevallen

| Vraag | Antwoord |
|----------|--------|
| **Wat als het document geen voetnoten heeft?** | `FootnoteOptions.Separator` retourneert nog steeds een `Run`‑knooppunt, maar de tekst kan leeg zijn. De code controleert veilig het knooppunttype voordat het wordt aangepast. |
| **Kan ik een tekenreeks met meerdere tekens gebruiken (bijv. "***")?** | Ja. De `Run.Text`‑eigenschap accepteert elke tekenreeks, inclusief Unicode‑tekens. |
| **Heeft het wijzigen van de separator invloed op de bestaande voetnootnummering?** | Nee. De separator staat los van het nummeringsschema. |
| **Moet ik het `Document`‑object vrijgeven?** | `Document` implementeert impliciet `IDisposable` via `Node`. In een kortlevende console‑app is het optioneel, maar voor langdurige services kun je het in een `using`‑blok plaatsen. |
| **Hoe werkt dit met .NET Core versus .NET Framework?** | De API is identiek over runtimes; alleen de doel‑frameworkversie is van belang (moet worden ondersteund door het Aspose.Words‑pakket). |

**Pro tip:** Als je verschillende separatoren voor verschillende secties wilt toepassen, kun je itereren over `doc.GetChildNodes(NodeType.Footnote, true)` en de `Separator`‑eigenschap van elke voetnoot afzonderlijk aanpassen. Dit is geavanceerder maar nuttig voor complexe documenten.

---

## Conclusie

Je weet nu hoe je de **footnote separator** en de **endnote separator** in een Word‑bestand kunt wijzigen met Aspose.Words voor C#. De gids besprak het laden van het document, het benaderen van de relevante separator‑knooppunten, het aanpassen van hun tekst en het opslaan van het resultaat—alles in één zelfstandige programma.

Vanaf hier kun je gerelateerde onderwerpen verkennen, zoals **edit footnote separator style**, het aanpassen van voetnootnummering, of het toepassen van voorwaardelijke opmaak op basis van paginalay-out. Hetzelfde patroon (een knooppunt ophalen, casten naar `Run`, `Text` wijzigen) werkt voor veel andere Word‑verwerkingsscenario's.

Veel programmeerplezier, en voel je vrij om te experimenteren met verschillende symbolen of zelfs afbeeldingen als separatoren voor een echt uniek documentontwerp!

## Wat moet je hierna leren?

De volgende tutorials behandelen nauw verwante onderwerpen die voortbouwen op de technieken die in deze gids worden getoond. Elke bron bevat volledige werkende code‑voorbeelden met stapsgewijze uitleg om je te helpen extra API‑functies onder de knie te krijgen en alternatieve implementatie‑benaderingen in je eigen projecten te verkennen.

- [Woorden verwerken met voetnoot en eindnoot](/words/english/net/working-with-footnote-and-endnote/)
- [Paragraphstijlseparator ophalen in Word‑document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Documentstijlseparator invoegen in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}