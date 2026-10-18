---
category: general
date: 2026-03-04
description: Jak nakonfigurovat LLM pro Document AI a nahradit text v DOCX pomocí
  AI – průvodce krok za krokem s kompletním Java kódem.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: cs
og_description: Jak nakonfigurovat LLM pro Document AI a nahradit text v DOCX pomocí
  AI – kompletní průvodce s spustitelným Java kódem.
og_title: How to Configure LLM – Replace Text in DOCX with AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: How to Configure LLM – Replace Text in DOCX with AI
url: /cs/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Jak nakonfigurovat LLM – Nahrazení textu v DOCX pomocí AI

Už jste se někdy zamýšleli **jak nakonfigurovat LLM**, aby pro vás upravoval soubor Word? Nejste v tom sami. Mnoho vývojářů narazí na problém, když potřebují programově nahradit frázi uvnitř `.docx` bez otevření Microsoft Wordu. Dobrá zpráva? S lokálním LLM a malým obalem Document AI můžete vyměnit text v souboru DOCX během několika řádků Javy.

V tomto tutoriálu projdeme celý proces: od nastavení připojení k LLM, načtení DOCX až po použití **Document AI** k nahrazení cílové fráze. Na konci budete mít samostatný, spustitelný příklad, který můžete vložit do libovolného projektu Maven nebo Gradle. Žádné externí API klíče, žádné poplatky za cloud – jen váš vlastní model naslouchající na `http://localhost:8080/v1`.

> **Rychlý úspěch:** Pokud už máte lokální LLM (např. Llama 3 nebo Mistral) vystavující OpenAI‑kompatibilní endpoint, níže uvedený kód funguje hned po vybalení.

---

![Diagram jak nakonfigurovat LLM pro Document AI](/images/configure-llm-diagram.png){: .center-image alt="diagram jak nakonfigurovat LLM"}

## Co budete potřebovat

- **Java 17** (nebo jakýkoli aktuální JDK)  
- **Lokální LLM** vystavující OpenAI‑styl `/v1` endpoint (např. Ollama, LMStudio)  
- **Document AI Java knihovna** (předpokládejme `com.example:document-ai:1.2.0` na Maven Central)  
- Vzorkový soubor DOCX (`input.docx`) umístěný ve známé složce  

Pokud vám něco z toho chybí, rychle spusťte Ollamu:

```bash
ollama serve &
ollama run llama3
```

Tím se spustí server na `http://localhost:8080/v1`, připravený přijímat požadavky.

---

## Jak nakonfigurovat LLM pro Document AI

Prvním krokem je říct klientovi `DocumentAi`, kde najít model a který model použít. Toto je krok **jak nakonfigurovat LLM**, který mnoho tutoriálů opomíjí.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Proč je to důležité:*  
Objekt `AiModelConfig` abstrahuje HTTP detaily, takže se `DocumentAi` může soustředit na obsah. Pokud někdy přejdete na hostovaného poskytovatele, stačí změnit `baseUrl` a `apiKey` – zbytek kódu zůstane nedotčený.

---

## Načtení a příprava DOCX dokumentu

Dále načteme Word soubor do paměti. Třída `Document` pod kapotou zvládá jak `.docx`, tak `.pdf`, ale zde nás zajímá jen DOCX.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Tip:* Použijte absolutní cestu během ladění, abyste se vyhnuli překvapení „soubor nenalezen“. Jakmile budete mít jistotu, přepněte zpět na relativní cestu pro přenositelnost.

---

## Nahrazení textu v DOCX pomocí AI

Nyní přichází jádro tutoriálu – **jak nahradit text** v DOCX souboru s pomocí AI. Metoda `replaceText` pošle obsah dokumentu do LLM, požádá ho o provedení substituce a vrátí upravený text.

```java
// Step 3: Initialise the Document AI client
DocumentAi documentAi = new DocumentAi(modelConfig);

// Step 4: Ask the LLM to replace the target phrase
String oldPhrase = "old phrase";
String newPhrase = "new phrase";

String revisedText = documentAi.replaceText(
        inputDocument,
        oldPhrase,
        newPhrase
);
```

*Co se děje v pozadí?*  
`DocumentAi` serializuje DOCX do prostého textu, vytvoří prompt jako:

> „V následujícím dokumentu nahraď každé výskyt ‘old phrase’ za ‘new phrase’ a vrať pouze aktualizovaný text.“

LLM požadavek zpracuje a pošle zpět upravený obsah. Tento přístup funguje i tehdy, když se fráze rozkládá přes více běhů nebo odstavců – něco, co často unikne pouhému nahrazení řetězcem.

---

## Ověření a výpis upraveného textu

Nakonec vytiskneme AI‑upravený text do konzole. Ve skutečné aplikaci byste pravděpodobně výsledek zapsali zpět do nového DOCX, ale výpis vám umožní rychle ověřit výsledek.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Očekávaný výstup** (předpokládejme, že původní DOCX obsahoval „This is the old phrase we want to change.“):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Pokud se objeví nová fráze, gratulujeme – **právě jste se naučili používat Document AI k nahrazení fráze pomocí AI**.

---

## Kompletní funkční příklad

Spojením všech částí získáte kompletní, připravenou ke spuštění třídu v Javě. Klidně ji zkopírujte do `src/main/java/com/example/ReplaceInDocx.java`.

```java
package com.example;

import com.example.documentai.AiModelConfig;
import com.example.documentai.DocumentAi;
import com.example.documentai.Document;

import java.nio.file.Path;
import java.nio.file.Paths;

/**
 * Demonstrates how to configure LLM, load a DOCX, and replace a phrase using Document AI.
 */
public class ReplaceInDocx {

    public static void main(String[] args) {
        // 1️⃣ Configure the local LLM connection
        AiModelConfig modelConfig = new AiModelConfig();
        modelConfig.setBaseUrl("http://localhost:8080/v1");
        modelConfig.setApiKey("dummy");               // Not required for local models
        modelConfig.setModelName("local-llm");        // Change if needed

        // 2️⃣ Load the DOCX you want to modify
        Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
        Document inputDocument = new Document(docPath.toFile());

        // 3️⃣ Create the Document AI client using the configuration
        DocumentAi documentAi = new DocumentAi(modelConfig);

        // 4️⃣ Replace the target phrase with the new phrase using the AI model
        String oldPhrase = "old phrase";
        String newPhrase = "new phrase";

        String revisedText = documentAi.replaceText(
                inputDocument,
                oldPhrase,
                newPhrase
        );

        // 5️⃣ Output the AI‑revised text
        System.out.println("AI‑revised text:");
        System.out.println("-----------------------------------");
        System.out.println(revisedText);
    }
}
```

### Jak spustit

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Ujistěte se, že server LLM běží, než program spustíte; jinak dostanete timeout připojení.

---

## Okrajové případy a časté úskalí

| Situace | Na co si dát pozor | Navrhované řešení |
|-----------|-------------------|---------------|
| **Fráze nenalezena** | LLM vrátí původní text beze změny. | Zkontrolujte pravopis a citlivost na velikost písmen; pokud váš obal podporuje, můžete do promptu přidat `ignoreCase:true`. |
| **Velké dokumenty (>5 MB)** | Velikost promptu může překročit limit tokenů modelu. | Rozdělte DOCX na sekce, zpracujte každou zvlášť a pak výsledky spojte. |
| **Lokální LLM vrací chyby** | Často způsobeno nesprávným názvem modelu. | Ověřte, že název modelu v UI LLM (`ollama list`) odpovídá `modelConfig.setModelName`. |
| **Unicode znaky jsou poškozené** | Problémy s kódováním při čtení DOCX. | Ujistěte se, že vaše Java runtime používá UTF‑8 (přidejte `-Dfile.encoding=UTF-8` do JVM argumentů). |

---

## Další kroky

Nyní, když už víte **jak nahradit text v DOCX** pomocí AI, můžete zkusit:

- **Jak používat Document AI** pro složitější úkoly, jako je extrakce tabulek nebo zachování stylů.  
- **Nahradit frázi pomocí AI** v PDF změnou argumentu konstruktoru `Document`.  
- **Dávkové zpracování**: projít adresář s DOCX soubory a aplikovat stejnou náhradu.  

Všechny tyto scénáře staví na stejném základu `AiModelConfig` a `DocumentAi`, takže nebudete muset začínat od nuly.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}