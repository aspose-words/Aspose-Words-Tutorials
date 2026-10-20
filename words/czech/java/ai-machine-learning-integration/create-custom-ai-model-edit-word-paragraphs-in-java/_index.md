---
category: general
date: 2026-03-25
description: Vytvořte vlastní AI model pro úpravu dokumentů Word – naučte se, jak
  učinit text formálnější, nahradit text odstavce a přepsat odstavec ve Wordu pomocí
  Aspose.Words AI.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: cs
og_description: Vytvořte vlastní AI model pro úpravu dokumentů Word. Naučte se, jak
  učinit text formálnější, nahradit text odstavce a přepsat odstavec ve Wordu pomocí
  Aspose.Words AI.
og_title: Vytvořte vlastní AI model – upravte odstavce ve Wordu v Javě
tags:
- Aspose.Words
- Java
- AI integration
title: Vytvořte vlastní AI model – upravujte odstavce ve Wordu v Javě
url: /cs/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vytvořte vlastní AI model – úprava odstavců ve Wordu v Javě

Už jste někdy potřebovali **create custom AI model**, který dokáže vylepšit odstavec v souboru Word? Možná máte šarži smluv, které znějí příliš neformálně, a chtěli byste text učinit formálnějším jedním řádkem kódu. Dobrou zprávou je, že to můžete udělat přesně takto – žádné externí služby, žádná těžká SDK, jen Aspose.Words pro Java a OpenAI‑compatible endpoint.

V tomto tutoriálu projdeme každý krok potřebný k **create custom AI model**, připojíme jej k lokálnímu LLM serveru a poté jej použijeme k *replace paragraph text* s formálnější verzí. Na konci budete mít spustitelný Java program, který **edit paragraph with AI**, přepíše odstavec ve Wordu a výsledek uloží zpět na disk. Žádné zbytečnosti, jen praktické řešení, které můžete zkopírovat‑vložit do svého projektu.

> **Co budete potřebovat**  
> • Java 17 nebo novější (kód se kompiluje i s předchozími verzemi, ale 17 je ideální)  
> • Aspose.Words for Java 23.9 (nebo nejnovější vydání)  
> • Běžící OpenAI‑compatible LLM server (např. Ollama, LocalAI) naslouchající na `http://localhost:8000/v1`  
> • Vstupní Word dokument (`input.docx`) umístěný ve složce, kterou ovládáte  

Pokud se ptáte, *proč vůbec stavět vlastní model* místo přímého volání OpenAI, odpověď zní flexibilita: řídíte endpoint, můžete měnit modely bez úprav kódu a držíte API klíče mimo svůj zdrojový repozitář. Pojďme na to.

---

## Create Custom AI Model – Setup and Configuration

Nejprve musíme Aspose.Words říct, kde náš LLM sídlí. Třída `AiModelEndpoint` obsahuje URL a volitelný API klíč. Protože používáme lokální server, klíč může být prázdný řetězec, ale parametr je povinný.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Tip:** Pokud někdy přejdete na hostovaný model (např. Azure OpenAI), stačí změnit URL a klíč – žádné další úpravy kódu nejsou potřeba.

---

## Load the Word Document

Nyní načteme zdrojový soubor do paměti. `Document` umí číst `.docx`, `.doc`, `.rtf` a mnoho dalších formátů, ale pro tento příklad zůstáváme u `.docx`.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Ujistěte se, že `YOUR_DIRECTORY` ukazuje na skutečnou složku; jinak narazíte na `FileNotFoundException`. Ve skutečné aplikaci můžete cestu předat jako argument příkazové řádky nebo ji načíst z konfiguračního souboru.

---

## Initialize the Custom AI Model

Vytvoříme `AiModel` typu `CUSTOM` a přiřadíme mu endpoint, který jsme definovali výše. Tím říkáme Aspose.Words, aby všechny AI volání směroval přes náš vlastní server.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

Za scénou Aspose.Words sestaví malý HTTP klient, který komunikuje s LLM podle standardního OpenAI chat/completion schématu. Proto musí být endpoint *OpenAI‑compatible*.

---

## Retrieve and Rewrite the First Paragraph

Zde skutečně **make text more formal**. Načteme první odstavec, pošleme jeho surový text modelu s promptem a získáme upravenou verzi.

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

Druhý argument (`"Make it more formal"`) je instrukce, kterou modelu předáváme. Můžete ji nahradit libovolným pokynem – **replace paragraph text**, **summarize**, **translate**, atd. Metoda vrací prostý řetězec, který později vložíme zpět do dokumentu.

> **Proč to funguje:** `editText` odesílá JSON payload jako `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\nMake it more formal"}] }`. LLM vidí původní odstavec i instrukci a odpoví revidovaným textem.

---

## Replace the Original Paragraph Content

Nyní **replace paragraph text** uvnitř objektového modelu Wordu. Vymažeme všechny existující `Run` (nízkoúrovňové kusy textu) a vložíme nový `Run` obsahující AI‑generovaný řetězec.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Dejte pozor, abyste nevolali `firstParagraph.setText()` – tato metoda by odstranila veškeré formátování. Použití `Run` zachová styl odstavce (nadpis, odrážka, atd.) a pouze vymění samotné znaky.

---

## Save the Edited Document

Nakonec zapíšeme upravený dokument zpět na disk. Můžete přepsat původní soubor nebo, jak děláme zde, vytvořit novou kopii.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Když otevřete `output.docx`, měli byste vidět, že první odstavec nyní zní podstatně formálněji. Pokud LLM instrukci neprovedl perfektně, můžete prompt vyladit nebo zkusit jinou verzi modelu.

---

## Full Working Example

Níže je kompletní program – zkopírujte jej do `LlmDemo.java`, upravte cesty a spusťte pomocí `javac` + `java`.

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

**Očekávaný výstup:** Otevřete `output.docx` a uvidíte, že původní odstavec byl transformován. Například neformální věta „We’ll get the thing done soon.“ může být přeformulována na „We shall complete the task promptly.“ Přesná formulace závisí na použitém modelu.

---

## Common Questions & Edge Cases

### Co když má můj dokument více sekcí?

Výše uvedený kód upravuje jen *první* odstavec *první* sekce. Pro **edit paragraph with AI** v celém souboru projděte `document.getSections()` a poté každou `section.getBody().getParagraphs()`. Nezapomeňte přeskočit prázdné odstavce, jinak LLM dostane prázdný řetězec a nic nevrátí.

### Jak zacházet s dlouhými odstavci, které překračují limit tokenů?

Většina LLM má limit vstupu kolem 4 000 tokenů. Pokud je odstavec neobvykle dlouhý, rozdělte jej na menší úseky před voláním `editText`. Stejnou instanci `AiModel` můžete použít opakovaně; jen mějte na paměti omezení rychlosti na vašem lokálním serveru.

### Můžu použít jinou instrukci, např. „summarize“ nebo „translate to French“?

Určitě. Druhý argument `editText` je volný text. Pro souhrn můžete předat `"Summarize in one sentence"`. Pro překlad např. `"Translate to French, keep the tone formal"` funguje stejně dobře. Tato flexibilita vám umožní **replace paragraph text** v mnoha scénářích bez změny kódu.

### Zachová model styl odstavce (písma, barvy)?

Protože nahrazujeme jen `Run` uvnitř stejného objektu `Paragraph`, existující styly (úroveň nadpisu, odrážka, odsazení) zůstávají nedotčeny. Pokud potřebujete změnit samotný styl, můžete po výměně manipulovat s `Paragraph.getParagraphFormat()`.

### Co když můj LLM server vyžaduje HTTPS s vlastním certifikátem?

`AiModelEndpoint` přijímá URL s `https://`. Pokud certifikát není důvěryhodný, musíte nakonfigurovat SSL kontext Javy, aby jej akceptoval, nebo spustit server s platným certifikátem. Toto nastavení přesahuje rámec tohoto tutoriálu, ale je dobře zdokumentováno v Java SSL průvodcích.

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

Ukázali jsme vám, jak **create custom AI model** s Aspose.Words, připojit jej k OpenAI‑compatible endpointu a následně **edit paragraph with AI** tak, aby **make text more formal**. Dodržením šesti kroků – definice endpointu, načtení dokumentu, inicializace modelu, získání a úprava odstavce, nahrazení obsahu a uložení souboru – získáte funkční řešení připravené k nasazení.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}