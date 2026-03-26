---
category: general
date: 2026-03-25
description: Skapa en anpassad AI-modell för att redigera Word-dokument – lär dig
  hur du gör texten mer formell, ersätter stycketext och skriver om ett Word-stycke
  med Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: sv
og_description: Skapa en anpassad AI-modell för att redigera Word-dokument. Lär dig
  hur du gör texten mer formell, ersätter stycke‑text och skriver om ett Word‑stycke
  med hjälp av Aspose.Words AI.
og_title: Skapa anpassad AI-modell – Redigera Word‑paragrafer i Java
tags:
- Aspose.Words
- Java
- AI integration
title: Skapa anpassad AI-modell – Redigera Word-paragrafer i Java
url: /sv/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Skapa anpassad AI-modell – Redigera Word‑paragrafer i Java

Har du någonsin behövt **create custom AI model** som kan putsa ett stycke i en Word‑fil? Kanske har du en bunt kontrakt som alla låter lite för informella, och du skulle vilja göra texten mer formell med en enda kodrad. Den goda nyheten är att du kan göra exakt det – utan externa tjänster, utan tunga SDK:er, bara Aspose.Words for Java och en OpenAI‑kompatibel endpoint.

I den här handledningen går vi igenom varje steg som krävs för att **create custom AI model**, koppla den till en lokal LLM‑server och sedan använda den för att *ersätta stycke‑text* med en mer formell version. När du är klar har du ett körbart Java‑program som **edit paragraph with AI**, skriver om ett Word‑stycke och sparar resultatet tillbaka till disk. Inga onödiga utsvävningar, bara en praktisk lösning som du kan kopiera‑klistra in i ditt eget projekt.

> **Vad du behöver**  
> • Java 17 eller nyare (koden kompileras med tidigare versioner, men 17 är den optimala)  
> • Aspose.Words for Java 23.9 (eller den senaste releasen)  
> • En körande OpenAI‑kompatibel LLM‑server (t.ex. Ollama, LocalAI) som lyssnar på `http://localhost:8000/v1`  
> • Ett inmatnings‑Word‑dokument (`input.docx`) placerat i en mapp du kontrollerar  

Om du funderar på *varför bygga en egen modell* istället för att anropa OpenAI direkt, är svaret flexibilitet: du styr endpointen, du kan byta modeller utan kodändringar och du håller eventuella API‑nycklar utanför ditt källkodsförråd. Låt oss dyka ner.

---

## Create Custom AI Model – Setup and Configuration

Först måste vi tala om för Aspose.Words var vår LLM finns. Klassen `AiModelEndpoint` innehåller URL‑en och eventuell API‑nyckel. Eftersom vi använder en lokal server kan nyckeln vara en tom sträng, men parametern är obligatorisk.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** Om du någonsin byter till en hostad modell (t.ex. Azure OpenAI), ändra bara URL‑en och nyckeln – inga andra kodändringar behövs.

---

## Load the Word Document

Nu läser vi in källfilen i minnet. `Document` kan läsa `.docx`, `.doc`, `.rtf` och många andra format, men i det här exemplet håller vi oss till `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Se till att `YOUR_DIRECTORY` pekar på en riktig mapp; annars får du ett `FileNotFoundException`. I en riktig applikation kan du skicka sökvägen som ett kommandoradsargument eller läsa den från en konfigurationsfil.

---

## Initialize the Custom AI Model

Vi skapar ett `AiModel` av typen `CUSTOM` och ger det endpointen vi definierade tidigare. Detta talar om för Aspose.Words att routa alla AI‑anrop via vår egen server.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Bakom kulisserna bygger Aspose.Words en liten HTTP‑klient som kommunicerar med LLM:n enligt det standardiserade OpenAI‑chat/completion‑schemat. Därför måste endpointen vara *OpenAI‑compatible*.

---

## Retrieve and Rewrite the First Paragraph

Här är vi faktiskt **make text more formal**. Vi hämtar det första stycket, skickar dess råa text till modellen med en prompt och får tillbaka den redigerade versionen.

```java
        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");
```

Det andra argumentet (`"Make it more formal"`) är instruktionen vi ger modellen. Du kan ersätta det med vilken direktiv som helst – **replace paragraph text**, **summarize**, **translate**, osv. Metoden returnerar en vanlig sträng, som vi senare sätter in tillbaka i dokumentet.

> **Why this works:** `editText` skickar en JSON‑payload som `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. LLM:n ser det ursprungliga stycket och instruktionen, och svarar med den reviderade texten.

---

## Replace the Original Paragraph Content

Nu **replace paragraph text** i Word‑objektmodellen. Vi rensar alla befintliga `Run`‑element (de lågnivå‑textbitarna) och sätter in ett nytt `Run` som innehåller den AI‑genererade strängen.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Var försiktig så att du inte anropar `firstParagraph.setText()` – den metoden skulle ta bort all formatering. Att använda `Run` bevarar styckets stil (rubrik, punktlista osv.) samtidigt som själva tecknen byts ut.

---

## Save the Edited Document

Till sist skriver vi det modifierade dokumentet tillbaka till disk. Du kan skriva över originalfilen eller, som vi gör här, skapa en ny kopia.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

När du öppnar `output.docx` bör du se att det första stycket nu låter betydligt mer formellt. Om LLM:n inte följde instruktionen perfekt kan du justera prompten eller prova en annan modellversion.

---

## Full Working Example

Nedan är hela programmet – kopiera det till `LlmDemo.java`, justera sökvägarna och kör det med `javac` + `java`.

```java
import com.aspose.words.*;
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required

        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");

        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);

        // Step 4: Retrieve the first paragraph and ask the model to rewrite it
        Paragraph firstParagraph = document.getFirstSection()
                                            .getBody()
                                            .getParagraphs()
                                            .get(0);
        String rewrittenText = llmModel.editText(
                firstParagraph.getText(),
                "Make it more formal");

        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));

        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Förväntat resultat:** Öppna `output.docx` och du kommer att se det ursprungliga stycket omvandlat. Till exempel kan en informell mening som “We’ll get the thing done soon.” bli “We shall complete the task promptly.” Den exakta formuleringen beror på den modell du använder.

---

## Common Questions & Edge Cases

### What if my document has multiple sections?

Koden ovan berör bara *det första* stycket i *den första* sektionen. För att **edit paragraph with AI** i hela filen, loopa igenom `document.getSections()` och sedan varje `section.getBody().getParagraphs()`. Kom ihåg att hoppa över tomma stycken, annars får LLM:n en tom sträng och returnerar inget.

### How do I handle large paragraphs that exceed token limits?

De flesta LLM‑er har en gräns på omkring 4 000 token. Om ett stycke är ovanligt långt, dela upp det i mindre bitar innan du anropar `editText`. Du kan återanvända samma `AiModel`‑instans; var bara medveten om hastighetsgränserna på din lokala server.

### Can I use a different instruction, like “summarize” or “translate to French”?

Absolut. Det andra argumentet till `editText` är fritt formulerat. För en sammanfattning kan du skicka `"Summarize in one sentence"`. För översättning fungerar `"Translate to French, keep the tone formal"` lika bra. Denna flexibilitet låter dig **replace paragraph text** i många scenarier utan att ändra någon kod.

### Does the model preserve paragraph styling (fonts, colors)?

Eftersom vi bara ersätter `Run` i samma `Paragraph`‑objekt, behålls befintliga stilar (rubriknivå, punktlista, indrag) intakta. Om du behöver ändra själva stilen kan du manipulera `Paragraph.getParagraphFormat()` efter ersättningen.

### What if my LLM server requires HTTPS with a self‑signed certificate?

`AiModelEndpoint` accepterar en URL med `https://`. Om certifikatet inte är betrott måste du konfigurera Javas SSL‑kontext för att lita på det, eller köra servern med ett giltigt certifikat. Den konfigurationen ligger utanför detta tutorials omfång men är väl dokumenterad i Java‑SSL‑guiderna.

---

## Tips for Production‑Ready Integration

| Tip | Why it matters |
|-----|----------------|
| **Cache the endpoint** | Re‑creating `AiModelEndpoint` on every request adds overhead. |
| **Batch edits** | If you have many paragraphs, send them in a single request (e.g., JSON array) to reduce latency. |
| **Validate LLM output** | Always check the returned string for null or empty values before inserting. |
| **Log prompts and responses** | Helpful for debugging and for compliance when you’re rewriting legal text. |
| **Graceful fallback** | If the LLM is down, fall back to the original paragraph or a simple heuristic rewrite. |

---

## Conclusion

Vi har visat hur du **create custom AI model** med Aspose.Words, ansluter den till en OpenAI‑compatible endpoint och sedan **edit paragraph with AI** för att **make text more formal**. Genom att följa de sex stegen – definiera endpointen, ladda dokumentet, initiera modellen,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}