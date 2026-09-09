---
category: general
date: 2026-01-13
description: Lär dig hur du anropar LLM från C# med en lokal LLM-endpoint, redigerar
  Word-filer, tar bort allt innehåll och sparar docx—allt i en tutorial.
draft: false
keywords:
- how to call llm
- use local llm
- remove all content
- how to edit word
- how to save docx
language: sv
og_description: Hur man anropar LLM från C# med en lokal modell, redigerar Word-dokument,
  tar bort allt innehåll och sparar docx-filen effektivt.
og_title: Hur man anropar LLM i C# – Steg‑för‑steg‑handledning
tags:
- Aspose.Words
- C#
- LLM Integration
title: Hur man anropar LLM i C# – Komplett guide med lokal modell
url: /sv/net/remove-content/how-to-call-llm-in-c-complete-guide-with-local-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hur man anropar LLM i C# – Komplett guide med lokal modell

Har du någonsin funderat **how to call LLM** från en .NET‑applikation utan att skicka data till molnet? Du är inte ensam. Många utvecklare vill behålla sina prompts och dokument på plats, särskilt när de hanterar känslig text. I den här handledningen går vi igenom ett verkligt scenario: att använda en självhostad LLM‑endpoint för att skriva om ett Word‑dokument, ta bort allt innehåll, redigera filen och slutligen **how to save docx** tillbaka till disk.  

Vi kommer också att gå igenom **use local LLM**, visa dig den exakta koden för att **remove all content** från ett Aspose.Words `Document`, och förklara nyanserna i att programatiskt redigera Word‑filer. I slutet har du en kopiera‑och‑klistra‑lösning som fungerar med Aspose.Words 7+ och vilken OpenAI‑kompatibel lokal modell som helst.

## Förutsättningar – Vad du behöver innan du börjar

- **.NET 6+** (eller .NET Framework 4.7.2 om du föredrar klassisk)
- **Aspose.Words for .NET** NuGet‑paket (`Aspose.Words` och `Aspose.Words.AI`)
- En **local LLM** som exponerar en OpenAI‑kompatibel `/v1`‑endpoint (t.ex. en GPT‑Neo‑server på `http://localhost:8000/v1`)
- Ett exempel `input.docx` placerat i en mapp du kontrollerar
- Visual Studio, Rider eller någon editor du föredrar – jag använder VS Code i skärmbilderna

> **Pro tip:** Om du ännu inte har en lokal modell, kolla in den gratis Docker‑avbilden för GPT‑Neo 2.7B – den startar på under en minut och följer samma API‑kontrakt som vi använder här.

## Steg 1 – Konfigurera den lokala LLM‑endpointen (How to Call LLM)

Det första du måste göra när du vill **how to call llm** från C# är att skapa ett klientobjekt som pekar på din självhostade tjänst. Aspose.Words.AI levereras med en `LocalLargeLanguageModel`‑hjälpare som abstraherar HTTP‑anropen.

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

> **Why this matters:** Genom att konfigurera endpointen själv behåller du full kontroll över begäranspayloads, autentisering och latens. Det är kärnan i **how to call llm** utan att förlita dig på externa tjänster.

## Steg 2 – Ladda källdokumentet Word (How to Edit Word)

Nästa steg hämtar den ursprungliga `.docx`‑filen till ett Aspose `Document`. Detta är det klassiska “how to edit word”-steget: när filen är i minnet kan du fråga, modifiera eller helt ersätta dess innehåll.

```csharp
// Load the source document from disk
Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Om filen inte finns får du en `FileNotFoundException`, så se till att sökvägen är korrekt. Du kan också läsa in från en `Stream` om du hanterar uppladdningar.

## Steg 3 – Generera reviderad text med den lokala LLM (How to Call LLM)

Nu kommer magin: vi ber LLM:n att skriva om hela texten i en formell ton. Prompten byggs genom att konkatenera en kort instruktion med den råa texten som extraheras via `document.GetText()`.

```csharp
// Ask the model to rewrite the whole document in a formal tone
string prompt = "Rewrite the following in formal tone:\n" + document.GetText();

string revisedText = llm.GenerateText(prompt);
```

> **Edge case:** Om källdokumentet är enormt (över 10 k token) kan du nå modellens kontextgräns. I så fall dela upp texten i stycken och anropa `GenerateText` för varje del.

## Steg 4 – Ta bort allt befintligt innehåll (Remove All Content)

Innan vi infogar den nya texten måste vi rensa dokumentet. Aspose tillhandahåller `RemoveAllChildren()` som raderar sektioner, stycken, tabeller—allt. Detta är det kanoniska sättet att **remove all content** från en Word‑fil.

```csharp
// Clear the document completely
document.RemoveAllChildren();
```

> **What if you only wanted to delete the body but keep headers?** Använd `document.Sections.Clear()` och bygg sedan om de sektioner du behöver.

## Steg 5 – Infoga den reviderade texten (How to Edit Word)

Med en ren start kan vi skriva tillbaka den LLM‑genererade texten. `DocumentBuilder` är det vänliga omslaget som låter dig lägga till stycken, tabeller, bilder osv. Här skriver vi helt enkelt hela strängen som ett enda stycke.

```csharp
// Re‑populate the document with the revised text
DocumentBuilder builder = new DocumentBuilder(document);
builder.Writeln(revisedText);
```

Om du behöver rikare formatering (fetstil, rubriker) kan du parsra LLM‑utdata för markdown‑markörer och tillämpa `builder.Font`‑inställningar därefter.

## Steg 6 – Spara det uppdaterade dokumentet (How to Save Docx)

Till sist sparar vi förändringarna till en ny fil. Detta demonstrerar **how to save docx** efter programatiska redigeringar.

```csharp
// Save the edited document
document.Save("YOUR_DIRECTORY/output.docx");
```

`Save`‑metoden upptäcker automatiskt formatet från filändelsen, så du kan också exportera till PDF, HTML eller ODT med en enda rad förändring.

### Förväntat resultat

När du öppnar `output.docx` bör du se hela det ursprungliga innehållet omskrivet i en polerad, formell stil. Inga kvarvarande tabeller, rubriker eller sidfötter från källan—bara den nya texten du bad LLM:n att producera.

![Skärmbild av output.docx öppnad i Word, som visar formellt omskriven text – how to call llm](/images/output-docx.png "how to call llm exempel")

*Bild alt‑text:* **how to call llm exempel som visar omskrivet Word‑dokument**

## Vanliga frågor & felsökning

### 1. “Vad händer om min LLM returnerar ett fel?”

`GenerateText`‑metoden kastar ett `HttpRequestException` för svar som inte är 2xx. Omslut anropet i ett `try/catch` och inspektera `ex.Message`. Ofta beror problemet på ett saknat API‑nyckel‑header eller att modellens token‑gräns överskrids.

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

### 2. “Kan jag redigera specifika delar av dokumentet istället för att radera allt?”

Absolut. Använd `document.GetChildNodes(NodeType.Paragraph, true)` för att lista stycken, och ersätt sedan `Paragraph.Text`‑egenskapen endast där du behöver förändringar. Detta tillvägagångssätt låter dig **how to edit word** på en detaljerad nivå samtidigt som du bevarar stilar.

### 3. “Finns det ett sätt att behålla den ursprungliga formateringen?”

Om du vill bevara stilar, överväg att returnera LLM‑utdata som ren text och sedan tillämpa `builder.Font.StyleIdentifier` på varje stycke baserat på din mall. Alternativt, använd `DocumentBuilder.InsertHtml()` om LLM:n kan leverera HTML.

### 4. “Hur hanterar jag stora dokument?”

Dela upp dokumentet i sektioner (`document.Sections`) och bearbeta varje sektion individuellt. Detta undviker inte bara token‑gränser utan minskar också minnesbelastningen.

## Prestandatips

- **Återanvänd `LocalLargeLanguageModel`‑instansen** över flera anrop; den underliggande `HttpClient`‑instansen håller anslutningen levande.
- **Cacha den reviderade texten** om du förväntar dig att köra samma prompt upprepade gånger—LLM‑anrop kan vara kostsamma även på lokal hårdvara.
- **Parallellisera** sektionbearbetning med `Parallel.ForEach` när du har en flerkärnig CPU och en trådsäker LLM‑klient.

## Nästa steg – Utöka arbetsflödet

Nu när du vet **how to call llm**, **use local llm**, **remove all content**, **how to edit word**, och **how to save docx**, kanske du vill utforska:

- **Batch‑bearbetning**: Loopa igenom en mapp med `.docx`‑filer och tillämpa samma omskrivningslogik.
- **Anpassade prompts**: Skräddarsy instruktionen för att generera sammanfattningar, punktlistor eller översättningar.
- **Integration med ASP.NET Core**: Exponera en HTTP‑endpoint som tar emot en filuppladdning, kör LLM:n och returnerar det redigerade dokumentet.
- **Avancerad styling**: Parsra markdown från LLM:n och mappa den till Word‑stilar med `DocumentBuilder`.

Var och en av dessa utökningar bygger på det kärnmönster vi täckte, så du kan anpassa koden med minimal ansträngning.

## Slutsats

I den här guiden gick vi igenom **how to call llm** från C# med en självhostad endpoint, demonstrerade **use local llm**, visade det korrekta sättet att **remove all content** från en Word‑fil, förklarade **how to edit word** programatiskt, och avslutade med ett tydligt exempel på **how to save docx**. Det kompletta, körbara exemplet är redo att läggas in i vilket .NET‑projekt som helst, och förklaringarna ger dig “varför” bakom varje steg—så att du kan finjustera, utöka eller felsöka med förtroende.

Prova det, experimentera med olika prompts, och låt den lokala LLM:n göra det tunga arbetet för dina dokument‑automatiseringspipelines. Om du stöter på problem bör felsökningsavsnittet visa dig rätt riktning. Lycka till med kodandet, och njut av kraften i on‑prem LLM‑lösningar!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}