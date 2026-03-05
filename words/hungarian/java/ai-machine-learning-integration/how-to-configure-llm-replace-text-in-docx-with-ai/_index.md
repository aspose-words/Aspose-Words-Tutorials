---
category: general
date: 2026-03-04
description: How to configure LLM for Document AI and replace text in DOCX using AI
  – step‑by‑step guide with full Java code.
draft: false
keywords:
- how to configure llm
- replace text in docx
- how to replace text
- how to use document ai
- replace phrase with ai
language: hu
og_description: Hogyan konfiguráljuk az LLM-et a Document AI-hoz, és cseréljünk szöveget
  DOCX-ben AI segítségével – teljes útmutató futtatható Java kóddal.
og_title: How to Configure LLM – Replace Text in DOCX with AI
tags:
- LLM
- Document AI
- Java
- DOCX
title: Hogyan konfiguráljuk az LLM-et – Szöveg cseréje DOCX-ben AI-val
url: /hu/java/ai-machine-learning-integration/how-to-configure-llm-replace-text-in-docx-with-ai/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan konfiguráljuk az LLM-et – Szöveg cseréje DOCX-ben AI-val

Valaha is elgondolkodtál **hogyan konfiguráljuk az LLM-et**, hogy szerkeszthesse a Word fájlt helyetted? Nem vagy egyedül. Sok fejlesztő elakad, amikor programozottan kell egy kifejezést kicserélni egy `.docx`‑ben anélkül, hogy megnyitná a Microsoft Word‑öt. A jó hír? Egy helyi LLM‑mel és egy apró Document AI burkolóval néhány Java sorral kicserélheted a szöveget egy DOCX fájlban.

Ebben a tutorialban végigvezetünk a teljes folyamaton: az LLM‑kapcsolat beállításától, a DOCX betöltéséig, egészen a **Document AI** használatáig a célkifejezés cseréjéig. A végére egy önálló, futtatható példát kapsz, amelyet bármely Maven vagy Gradle projektbe beilleszthetsz. Nincsenek külső API kulcsok, nincs felhő költség – csak a saját modelled, amely a `http://localhost:8080/v1` címen hallgat.

> **Gyors nyeremény:** Ha már van egy helyi LLM‑ed (például Llama 3 vagy Mistral), amely OpenAI‑kompatibilis végpontot biztosít, az alábbi kód azonnal működik.

---

![Diagram of how to configure LLM for Document AI](/images/configure-llm-diagram.png){: .center-image alt="hogyan konfiguráljuk az llm diagram"}

## Amire szükséged lesz

- **Java 17** (vagy bármely friss JDK)  
- Egy **helyi LLM**, amely OpenAI‑stílusú `/v1` végpontot biztosít (pl. Ollama, LMStudio)  
- A **Document AI Java könyvtár** (feltételezve `com.example:document-ai:1.2.0` a Maven Central‑on)  
- Egy minta DOCX fájl (`input.docx`) egy ismert mappában  

Ha valamelyik hiányzik, indítsd el gyorsan az Ollama-t:

```bash
ollama serve &
ollama run llama3
```

Ez egy szervert indít a `http://localhost:8080/v1` címen, amely készen áll a kérések fogadására.

---

## Hogyan konfiguráljuk az LLM-et a Document AI-hoz

Az első lépés, hogy elmondjuk a `DocumentAi` kliensnek, hol találja a modellt és melyik modellt használja. Ez a **hogyan konfiguráljuk az LLM-et** lépés, amelyet sok tutorial csak átfut.

```java
// Step 1: Set up the LLM connection details
AiModelConfig modelConfig = new AiModelConfig();
modelConfig.setBaseUrl("http://localhost:8080/v1");   // Local server address
modelConfig.setApiKey("dummy");                       // Not needed for local models, but the client expects a value
modelConfig.setModelName("local-llm");                // Replace with your model's identifier
```

*Miért fontos ez:*  
Az `AiModelConfig` objektum elrejti a HTTP részleteket, így a `DocumentAi` a tartalomra koncentrálhat. Ha valaha egy felhőszolgáltatóhoz váltasz, csak a `baseUrl`‑t és az `apiKey`‑t kell módosítanod – a kód többi része változatlan marad.

---

## A DOCX dokumentum betöltése és előkészítése

Ezután betöltjük a Word fájlt a memóriába. A `Document` osztály kezeli a `.docx`‑et és a `.pdf`‑et is a háttérben, de itt csak a DOCX érdekel.

```java
// Step 2: Load the DOCX you want to edit
Path docPath = Paths.get("YOUR_DIRECTORY/input.docx");
Document inputDocument = new Document(docPath.toFile());
```

*Pro tipp:* Hibakeresés közben használj abszolút elérési utat, hogy elkerüld a „file not found” meglepetést. Ha már biztos vagy benne, térj vissza relatív útra a hordozhatóság érdekében.

---

## Szöveg cseréje DOCX-ben AI segítségével

Most jön a tutorial szíve – **hogyan cseréljünk szöveget** egy DOCX fájlban AI támogatással. A `replaceText` metódus elküldi a dokumentum tartalmát az LLM‑nek, kéri a helyettesítést, és visszaadja a módosított szöveget.

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

*Mi történik a háttérben?*  
A `DocumentAi` a DOCX‑et egyszerű szöveggé alakítja, majd egy ilyen promptot épít:

> “In the following document, replace every occurrence of ‘old phrase’ with ‘new phrase’ and return only the updated text.”

Az LLM feldolgozza a kérést és visszaküldi a módosított tartalmat. Ez a megközelítés akkor is működik, ha a kifejezés több futtatásra vagy bekezdésre terjed – amit a sima karakterlánc‑csere gyakran kihagy.

---

## Az új szöveg ellenőrzése és kiírása

Végül kiírjuk az AI‑által módosított szöveget a konzolra. Egy valódi alkalmazásban valószínűleg egy új DOCX‑be írnád vissza az eredményt, de a kiírás gyors ellenőrzést tesz lehetővé.

```java
// Step 5: Show the AI‑revised output
System.out.println("AI‑revised text:");
System.out.println("-----------------------------------");
System.out.println(revisedText);
```

**Várható kimenet** (feltételezve, hogy az eredeti DOCX a következőt tartalmazta: “This is the old phrase we want to change.”):

```
AI‑revised text:
-----------------------------------
This is the new phrase we want to change.
```

Ha az új kifejezést látod, gratulálok – **most már tudod, hogyan használjuk a Document AI‑t egy kifejezés AI‑val történő cseréjéhez**.

---

## Teljes működő példa

Mindent összevonva, itt egy komplett, azonnal futtatható Java osztály. Nyugodtan másold be a `src/main/java/com/example/ReplaceInDocx.java` fájlba.

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

### Hogyan futtassuk

```bash
# Compile
mvn clean compile

# Execute
mvn exec:java -Dexec.mainClass="com.example.ReplaceInDocx"
```

Győződj meg róla, hogy az LLM szerver fut, mielőtt elindítod a programot; különben kapcsolat‑időtúllépést kapsz.

---

## Szélsőséges esetek és gyakori buktatók

| Helyzet | Mit kell figyelni | Javasolt megoldás |
|-----------|-------------------|---------------|
| **Kifejezés nem található** | Az LLM visszaadja az eredeti szöveget változtatás nélkül. | Ellenőrizd a helyesírást és a kis‑nagybetű érzékenységet; ha a burkolód támogatja, adhatsz hozzá `ignoreCase:true`‑t a prompthoz. |
| **Nagy dokumentumok (>5 MB)** | A prompt mérete meghaladhatja a modell token‑korlátját. | Oszd fel a DOCX‑et szakaszokra, dolgozd fel külön-külön, majd fűzd össze az eredményeket. |
| **Helyi LLM hibákat ad** | Gyakran a modell neve nem egyezik. | Ellenőrizd, hogy a modell neve az LLM UI‑ban (`ollama list`) megegyezik a `modelConfig.setModelName`‑nel. |
| **Unicode karakterek eltorzulnak** | Kódolási problémák a DOCX olvasásakor. | Biztosítsd, hogy a Java futtatókörnyezet UTF‑8‑at használ (`-Dfile.encoding=UTF-8` a JVM argumentumokhoz). |

---

## Következő lépések

Most, hogy már **tudod, hogyan cserélj szöveget DOCX‑ben AI‑val**, érdemes tovább felfedezni:

- **Hogyan használjuk a Document AI‑t** összetettebb feladatokhoz, például táblázatok kinyeréséhez vagy a stílus megőrzéséhez.  
- **Kifejezés cseréje AI‑val** PDF‑ekben a `Document` konstruktor argumentumának megváltoztatásával.  
- **Kötegelt feldolgozás**: egy könyvtár DOCX fájljainak bejárása és ugyanazon csere alkalmazása.  

Ezek mind ugyanazon `AiModelConfig` és `DocumentAi` alapokon nyugszanak, így nem kell a nulláról kezdened.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}