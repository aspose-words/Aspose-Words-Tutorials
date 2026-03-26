---
category: general
date: 2026-03-25
description: Egyedi AI modell létrehozása Word dokumentumok szerkesztéséhez – tanulja
  meg, hogyan teheti a szöveget formálisabbá, cserélje ki a bekezdés szövegét, és
  írja át a Word bekezdést az Aspose.Words AI használatával.
draft: false
keywords:
- create custom ai model
- make text more formal
- replace paragraph text
- edit paragraph with ai
- rewrite word paragraph
language: hu
og_description: Készíts egyedi AI modellt a Word dokumentumok szerkesztéséhez. Tanulja
  meg, hogyan teheti a szöveget formálisabbá, cserélje ki a bekezdés szövegét, és
  írja át a Word bekezdést az Aspose.Words AI segítségével.
og_title: Egyedi AI modell létrehozása – Word bekezdések szerkesztése Java-ban
tags:
- Aspose.Words
- Java
- AI integration
title: Egyedi AI modell létrehozása – Word bekezdések szerkesztése Java-ban
url: /hu/java/ai-machine-learning-integration/create-custom-ai-model-edit-word-paragraphs-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Egyedi AI modell létrehozása – Word bekezdések szerkesztése Java-ban

Valaha szükséged volt már **create custom AI model**‑ra, amely fel tudja csiszolni a Word fájlban lévő bekezdést? Lehet, hogy van egy csomag szerződésed, amelyek mind kissé túl hétköznapi hangvételűek, és szeretnéd a szöveget egyetlen kódsorral formálisabbá tenni. A jó hír, hogy pontosan ezt megteheted – nincs szükség külső szolgáltatásokra, nehéz SDK‑kra, csak az Aspose.Words for Java és egy OpenAI‑compatible endpoint.

Ebben az útmutatóban végigvezetünk minden lépésen, amely a **create custom AI model** létrehozásához szükséges, csatlakoztatjuk egy helyi LLM szerverhez, majd használjuk a *replace paragraph text* feladat elvégzésére egy formálisabb változattal. A végére egy futtatható Java programod lesz, amely **edit paragraph with AI**, átír egy Word bekezdést, és elmenti az eredményt a lemezre. Nincs felesleges részlet, csak egy gyakorlati megoldás, amelyet egyszerűen beilleszthetsz a saját projektedbe.

> **Amire szükséged lesz**  
> • Java 17 vagy újabb (a kód korábbi verziókkal is lefordítható, de a 17 a legoptimálisabb)  
> • Aspose.Words for Java 23.9 (vagy a legújabb kiadás)  
> • Egy futó OpenAI‑compatible LLM szerver (pl. Ollama, LocalAI), amely a `http://localhost:8000/v1` címen hallgat  
> • Egy bemeneti Word dokumentum (`input.docx`), amelyet egy általad irányított mappában helyezel el  

Ha azon tűnődsz, *miért érdemes egyedi modellt építeni* ahelyett, hogy közvetlenül az OpenAI‑t hívnád, a válasz a rugalmasság: te irányítod az endpointot, modellcserét végezhetsz kómmódosítás nélkül, és az API kulcsokat a forráskódból távol tarthatod. Merüljünk bele.

---

## Egyedi AI modell létrehozása – Beállítás és konfiguráció

Először meg kell mondanunk az Aspose.Words-nak, hol található az LLM. Az `AiModelEndpoint` osztály tárolja az URL‑t és az opcionális API kulcsot. Mivel egy helyi szervert használunk, a kulcs lehet üres karakterlánc, de a paraméter kötelező.

```java
import com.aspose.words.ai.*;

public class LlmDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Define the LLM endpoint (OpenAI‑compatible)
        AiModelEndpoint llmEndpoint = new AiModelEndpoint(
                "http://localhost:8000/v1",   // URL of your LLM server
                "my-api-key");                // API key if required
```

> **Pro tip:** Ha valaha is egy hosztolt modellre váltasz (pl. Azure OpenAI), csak cseréld ki az URL‑t és a kulcsot – más kómbeli módosításra nincs szükség.

---

## Word dokumentum betöltése

Most betöltjük a forrásfájlt a memóriába. A `Document` képes beolvasni a `.docx`, `.doc`, `.rtf` és sok más formátumot, de ebben a példában a `.docx`‑re korlátozódunk.

```java
        // Step 2: Load the source Word document
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

Győződj meg róla, hogy a `YOUR_DIRECTORY` egy valós mappára mutat; ellenkező esetben `FileNotFoundException`-t kapsz. Egy valódi alkalmazásban az útvonalat átadhatod parancssori argumentumként vagy beolvashatod egy konfigurációs fájlból.

---

## Egyedi AI modell inicializálása

Létrehozunk egy `CUSTOM` típusú `AiModel`‑t, és megadjuk neki a korábban definiált endpointot. Ez azt mondja az Aspose.Words‑nak, hogy minden AI hívást a saját szerverünkön keresztül irányítson.

```java
        // Step 3: Create a custom AI model that uses the endpoint
        AiModel llmModel = new AiModel(AiModelType.CUSTOM, llmEndpoint);
```

A háttérben az Aspose.Words egy apró HTTP klienst épít, amely a standard OpenAI chat/completion sémát használva kommunikál az LLM‑mel. Ezért az endpointnek *OpenAI‑compatible*‑nek kell lennie.

---

## Az első bekezdés lekérése és átírása

Itt történik a tényleges **make text more formal**. Kivesszük az első bekezdést, a nyers szövegét elküldjük a modellnek egy prompttal, és megkapjuk a szerkesztett változatot.

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

A második argumentum (`"Make it more formal"`) a modellnek adott utasítás. Bármilyen irányelvre cserélheted — **replace paragraph text**, **summarize**, **translate**, stb. A metódus egy egyszerű stringet ad vissza, amelyet később visszaillesztünk a dokumentumba.

> **Why this works:** `editText` egy JSON terhet küld, például `{ "model": "...", "messages": [{ "role":"user", "content":"<text>\\nMake it more formal"}] }`. Az LLM látja az eredeti bekezdést és az utasítást, majd a módosított szöveggel válaszol.

---

## Az eredeti bekezdés tartalmának cseréje

Most **replace paragraph text** a Word objektummodellben. Töröljük az esetleges meglévő run‑okat (a szöveg alacsony szintű darabjait), és beszúrunk egy új `Run`‑t, amely az AI‑által generált karakterláncot tartalmazza.

```java
        // Step 5: Replace the original paragraph content with the rewritten text
        firstParagraph.removeAllChildren();
        firstParagraph.appendChild(new Run(document, rewrittenText));
```

Légy óvatos, hogy ne hívd a `firstParagraph.setText()`‑t – ez a metódus eltávolítaná a formázást. A `Run` használata megőrzi a bekezdés stílusát (cím, felsorolás stb.), miközben a tényleges karaktereket cseréli.

---

## A szerkesztett dokumentum mentése

Végül visszaírjuk a módosított dokumentumot a lemezre. Felülírhatod az eredeti fájlt, vagy ahogy itt tesszük, létrehozhatsz egy új másolatot.

```java
        // Step 6: Save the edited document
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Amikor megnyitod a `output.docx`‑t, az első bekezdésnek sokkal formálisabb hangvételűnek kell lennie. Ha az LLM nem követte pontosan az utasítást, finomíthatod a promptot vagy kipróbálhatsz egy másik modellverziót.

---

## Teljes működő példa

Alább a teljes program – másold be a `LlmDemo.java`‑ba, állítsd be az útvonalakat, és futtasd a `javac` + `java` parancsokkal.

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

**Expected output:** Nyisd meg a `output.docx`‑t, és láthatod, hogy az eredeti bekezdés átalakult. Például egy hétköznapi mondat, mint „We’ll get the thing done soon.” „We shall complete the task promptly.”‑re változhat. A pontos megfogalmazás a használt modelltől függ.

---

## Gyakori kérdések és széljegyek

### Mi van, ha a dokumentumnak több szekciója van?

A fenti kód csak az *első* szekció *első* bekezdését érinti. Ahhoz, hogy **edit paragraph with AI** a teljes fájlra kiterjedjen, iterálj a `document.getSections()`‑en, majd minden `section.getBody().getParagraphs()` elemen. Ne felejtsd el kihagyni az üres bekezdéseket, különben az LLM üres stringet kap és semmit sem ad vissza.

### Hogyan kezelem a tokenkorlátot meghaladó nagy bekezdéseket?

A legtöbb LLM körülbelül 4 000 tokenre korlátozza a bemenetet. Ha egy bekezdés szokatlanul hosszú, oszd fel kisebb darabokra, mielőtt meghívod a `editText`‑et. Újra felhasználhatod ugyanazt az `AiModel` példányt; csak vedd figyelembe a helyi szervered sebességkorlátait.

### Használhatok más utasítást, például „summarize” vagy „translate to French”?

Természetesen. A `editText` második argumentuma szabad szöveg. Egy összefoglalóhoz például `"Summarize in one sentence"`‑t adhatod meg. Fordításhoz a `"Translate to French, keep the tone formal"` is megfelelő. Ez a rugalmasság lehetővé teszi, hogy **replace paragraph text** sokféle helyzetben anélkül, hogy kódot módosítanál.

### Megőrzi a modell a bekezdés stílusát (betűtípusok, színek)?

Mivel csak a `Run`‑t cseréljük ki ugyanabban a `Paragraph` objektumban, a meglévő stílusok (cím szint, felsorolás, behúzás) változatlanok maradnak. Ha a stílust magát is módosítani kell, a csere után manipulálhatod a `Paragraph.getParagraphFormat()`‑t.

### Mi van, ha az LLM szerverem HTTPS‑t igényel önaláírt tanúsítvánnyal?

Az `AiModelEndpoint` elfogad egy `https://`‑vel kezdődő URL‑t. Ha a tanúsítvány nem megbízható, be kell állítanod a Java SSL kontextust, hogy elfogadja, vagy futtasd a szervert érvényes tanúsítvánnyal. Ez a beállítás kívül esik az útmutató keretein, de a Java SSL útmutatókban részletesen dokumentált.

## Tippek a production‑ready integrációhoz

| Tip | Why it matters |
|-----|----------------|
| **Cache the endpoint** | Az `AiModelEndpoint` minden kérésnél való újra létrehozása plusz terhet jelent. |
| **Batch edits** | Ha sok bekezdésed van, küldd őket egyetlen kérésben (pl. JSON tömbként) a késleltetés csökkentése érdekében. |
| **Validate LLM output** | Mindig ellenőrizd a visszakapott stringet null vagy üres értékekre, mielőtt beillesztenéd. |
| **Log prompts and responses** | Hasznos hibakereséshez és a megfelelőséghez, amikor jogi szöveget írsz át. |
| **Graceful fallback** | Ha az LLM nem érhető el, térj vissza az eredeti bekezdéshez vagy egy egyszerű heurisztikus átíráshoz. |

## Következtetés

Megmutattuk, hogyan **create custom AI model** az Aspose.Words‑szal, hogyan csatlakoztasd egy OpenAI‑compatible endpoint‑hoz, és hogyan **edit paragraph with AI** a **make text more formal** érdekében. A hat lépés – az endpoint definiálása, a dokumentum betöltése, a modell inicializálása – követésével,

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}