---
category: general
date: 2026-01-13
description: Leer hoe je een LLM vanuit C# aanroept met een lokaal LLM‑eindpunt, Word‑bestanden
  bewerkt, alle inhoud verwijdert en de docx opslaat — allemaal in één tutorial.
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: nl
og_description: Hoe roep je een LLM aan vanuit C# met een lokaal model, bewerk Word‑documenten,
  verwijder alle inhoud en sla het docx efficiënt op.
og_title: Hoe roep je LLM op in C# – Stapsgewijze tutorial
tags:
- Aspose.Words
- C#
- LLM Integration
title: Hoe LLM aanroepen in C# – Complete gids met lokaal model
url: /nl/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hoe LLM aanroepen in C# – Complete gids met lokaal model

Heb je je ooit afgevraagd **hoe je LLM** kunt aanroepen vanuit een .NET‑applicatie zonder gegevens naar de cloud te sturen? Je bent niet de enige. Veel ontwikkelaars willen hun prompts en documenten on‑premises houden, vooral bij gevoelige tekst. In deze tutorial lopen we een real‑world scenario door: een zelf‑gehoste LLM‑endpoint gebruiken om een Word‑document te herschrijven, alle inhoud te verwijderen, het bestand te bewerken en uiteindelijk **hoe je docx** opslaat op schijf.  

We behandelen ook **lokale LLM gebruiken**, laten je de exacte code zien om **alle inhoud te verwijderen** uit een Aspose.Words `Document`, en leggen de nuances uit van het programmatic bewerken van Word‑bestanden. Aan het einde heb je een copy‑and‑paste oplossing die werkt met Aspose.Words 7+ en elk OpenAI‑compatibel lokaal model.

## Voorvereisten – Wat je nodig hebt voordat je begint

- **.NET 6+** (of .NET Framework 4.7.2 als je de klassieke versie prefereert)
- **Aspose.Words for .NET** NuGet‑package (`Aspose.Words` en `Aspose.Words.AI`)
- Een **lokaal LLM** dat een OpenAI‑compatibel `/v1`‑endpoint exposeert (bijv. een GPT‑Neo server op `http://localhost:8000/v1`)
- Een voorbeeld‑`input.docx` geplaatst in een map die jij beheert
- Visual Studio, Rider, of een andere editor naar keuze – ik gebruik VS Code in de screenshots

> **Pro tip:** Als je nog geen lokaal model hebt, bekijk dan de gratis Docker‑image voor GPT‑Neo 2.7B – die start binnen een minuut op en volgt exact dezelfde API‑contract die we hier gebruiken.

## Stap 1 – Configureer het lokale LLM‑endpoint (Hoe LLM aanroepen)

Het eerste wat je moet doen wanneer je **hoe je llm aanroept** vanuit C# is een client‑object aanmaken dat naar jouw zelf‑gehoste service wijst. Aspose.Words.AI levert een `LocalLargeLanguageModel`‑helper die de HTTP‑calls abstracteert.

```csharp
using Aspose.Words;
using Aspose.Words.AI;

// Configure the self‑hosted LLM endpoint
var llm = new LocalLargeLanguageModel
{
    Endpoint = "http://localhost:8000/v1",   // your local server
    ModelName = "my-gpt-neo"                // name as registered in the server
};
```

> **Waarom dit belangrijk is:** Door het endpoint zelf te configureren houd je volledige controle over request‑payloads, authenticatie en latency. Het is de kern van **hoe je llm aanroept** zonder afhankelijk te zijn van externe services.

## Stap 2 – Laad het bron‑Word‑document (Hoe Word bewerken)

Vervolgens laden we de originele `.docx` in een Aspose `Document`. Dit is de klassieke “hoe je word bewerkt” stap: zodra het bestand in het geheugen staat kun je het doorzoeken, aanpassen of volledig vervangen.

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Als het bestand niet bestaat krijg je een `FileNotFoundException`, zorg dus dat het pad klopt. Je kunt ook vanuit een `Stream` laden als je met uploads werkt.

## Stap 3 – Genereer herziene tekst met het lokale LLM (Hoe LLM aanroepen)

Nu volgt de magie: we vragen het LLM om de volledige tekst in een formele toon te herschrijven. De prompt wordt opgebouwd door een korte instructie te concatenaten met de ruwe tekst die via `document.GetText()` wordt opgehaald.

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **Randgeval:** Als het bron‑document enorm is (meer dan 10 k tokens) kun je de context‑limiet van het model bereiken. Splits in dat geval de tekst op in alinea’s en roep `GenerateText` per stuk aan.

## Stap 4 – Verwijder alle bestaande inhoud (Alle inhoud verwijderen)

Voordat we de nieuwe tekst invoegen, moeten we het document leegmaken. Aspose biedt `RemoveAllChildren()` dat secties, alinea’s, tabellen—alles—verwijdert. Dit is de canonieke manier om **alle inhoud te verwijderen** uit een Word‑bestand.

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **Wat als je alleen de body wilt verwijderen maar headers wilt behouden?** Gebruik `document.Sections.Clear()` en bouw daarna de benodigde secties opnieuw op.

## Stap 5 – Voeg de herziene tekst in (Hoe Word bewerken)

Met een schone lei kunnen we de LLM‑gegenereerde tekst terugschrijven. `DocumentBuilder` is de gebruiksvriendelijke wrapper waarmee je alinea’s, tabellen, afbeeldingen, enz. kunt toevoegen. Hier schrijven we simpelweg de volledige string als één alinea.

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

Als je rijkere opmaak nodig hebt (vet, koppen) kun je de LLM‑output parsen op markdown‑markers en de `builder.Font`‑instellingen dienovereenkomstig toepassen.

## Stap 6 – Sla het bijgewerkte document op (Hoe docx opslaan)

Tot slot persisteren we de wijzigingen naar een nieuw bestand. Dit demonstreert **hoe je docx opslaat** na programmatic bewerkingen.

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

De `Save`‑methode detecteert automatisch het formaat op basis van de bestandsextensie, dus je kunt ook exporteren naar PDF, HTML of ODT met één regel wijziging.

### Verwacht resultaat

Wanneer je `output.docx` opent, zie je de volledige originele inhoud herschreven in een gepolijste, formele stijl. Geen overgebleven tabellen, headers of footers van de bron—alleen de frisse tekst die je het LLM hebt laten genereren.

---

![Screenshot of output.docx opened in Word, showing formal rewritten text – how to call llm](/images/output-docx.png "how to call llm example")
*Afbeeldings‑alt‑tekst:* **how to call llm voorbeeld toont herschreven Word‑document**

## Veelgestelde vragen & probleemoplossing

### 1. “Wat als mijn LLM een fout retourneert?”

De `GenerateText`‑methode gooit een `HttpRequestException` voor niet‑2xx responses. Plaats de call in een `try/catch` en inspecteer `ex.Message`. Vaak is het een ontbrekende API‑key header of het overschrijden van de token‑limiet van het model.

```csharp
try
{
    string revisedText = llm.GenerateText(prompt);
}
catch (HttpRequestException ex)
{
    Console.WriteLine($"LLM call failed: {ex.Message}");
    // fallback logic, e.g., return the original text
}
```

### 2. “Kan ik specifieke delen van het document bewerken in plaats van alles te wissen?”

Absoluut. Gebruik `document.GetChildNodes(NodeType.Paragraph, true)` om alinea’s te enumereren, en vervang alleen de `Paragraph.Text`‑eigenschap waar je wijzigingen nodig hebt. Deze aanpak laat je **hoe je word bewerkt** op een granulaire manier terwijl je stijlen behoudt.

### 3. “Is er een manier om de originele opmaak te behouden?”

Als je stijlen wilt behouden, overweeg dan de LLM‑output als platte tekst te retourneren en vervolgens `builder.Font.StyleIdentifier` toe te passen op elke alinea op basis van je template. Alternatief kun je `DocumentBuilder.InsertHtml()` gebruiken als het LLM HTML kan outputten.

### 4. “Hoe ga ik om met grote documenten?”

Splits het document op in secties (`document.Sections`) en verwerk elke sectie afzonderlijk. Dit voorkomt niet alleen token‑limieten, maar vermindert ook de geheugenbelasting.

## Performance‑tips

- **Herbruik de `LocalLargeLanguageModel`‑instance** over meerdere calls; de onderliggende `HttpClient` houdt de verbinding alive.
- **Cache de herziene tekst** als je dezelfde prompt herhaaldelijk verwacht te gebruiken—LLM‑calls kunnen zelfs op lokale hardware kostbaar zijn.
- **Paralleliseer** sectie‑verwerking met `Parallel.ForEach` wanneer je een multi‑core CPU en een thread‑safe LLM‑client hebt.

## Volgende stappen – Workflow uitbreiden

Nu je weet **hoe je llm aanroept**, **lokale llm gebruiken**, **alle inhoud verwijderen**, **hoe je word bewerkt**, en **hoe je docx opslaat**, kun je verder gaan met:

- **Batch‑verwerking**: Loop over een map met `.docx`‑bestanden en pas dezelfde herschrijf‑logica toe.
- **Aangepaste prompts**: Stem de instructie af om samenvattingen, bullet‑lists of vertalingen te genereren.
- **Integratie met ASP.NET Core**: Exposeer een HTTP‑endpoint dat een bestandsupload accepteert, het LLM draait en het bewerkte document terugstuurt.
- **Geavanceerde styling**: Parse markdown van het LLM en map dit naar Word‑stijlen via `DocumentBuilder`.

Al deze uitbreidingen bouwen voort op het kernpatroon dat we hebben behandeld, zodat je de code met minimale inspanning kunt aanpassen.

---

## Conclusie

In deze gids hebben we **hoe je llm aanroept** vanuit C# met een zelf‑gehost endpoint behandeld, **lokale llm gebruiken** gedemonstreerd, de juiste manier getoond om **alle inhoud te verwijderen** uit een Word‑bestand, uitgelegd **hoe je word bewerkt** programmatic, en alles samengebracht met een duidelijk voorbeeld van **hoe je docx opslaat**. Het complete, uitvoerbare voorbeeld staat klaar om in elk .NET‑project te worden geplakt, en de toelichtingen geven je het “waarom” achter elke stap—zodat je kunt tweaken, uitbreiden of debuggen met vertrouwen.

Probeer het, experimenteer met verschillende prompts, en laat het lokale LLM het zware werk doen voor je document‑automatiserings‑pipelines. Als je tegen problemen aanloopt, wijst de probleemoplossingssectie je in de juiste richting. Veel programmeerplezier, en geniet van de kracht van on‑prem LLM’s!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}