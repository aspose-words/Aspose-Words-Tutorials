---
category: general
date: 2026-06-20
description: Hogyan állítsunk be visszahívást az Aspose.Words Java-ban a hiányzó betűtípusok
  észleléséhez és a dokumentum betöltésének testreszabásához. Tanulja meg lépésről
  lépésre a betűtípus helyettesítési figyelmeztetések kezelését.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: hu
og_description: Hogyan állítsunk be visszahívást az Aspose.Words Java-ban a hiányzó
  betűtípusok észleléséhez, a helyettesítések kezeléséhez és a dokumentum betöltésének
  testreszabásához. Teljes útmutató kóddal.
og_title: Hogyan állítsunk be visszahívást – Hiányzó betűkészletek felderítése az
  Aspose.Words Java-ban
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Hogyan állítsunk be visszahívást az Aspose.Words Java-ban – Hiányzó betűkészletek
  felismerése és kezelése
url: /hu/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# hogyan állítsuk be a visszahívást az Aspose.Words Java-ban – Hiányzó betűkészletek észlelése és kezelése

Valaha is elgondolkodtál már azon, **hogyan állítsuk be a visszahívást** az Aspose.Words Java-ban, hogy észrevehesd a hiányzó betűkészleteket, mielőtt tönkretennék a PDF vagy DOCX fájlodat? Nem vagy egyedül. A hiányzó betűkészlet figyelmeztetések csendben tönkretehetik a megjelenést, és megfelelő figyelmeztető visszahívás nélkül előfordulhat, hogy csak a végső dokumentum nézetekor veszed észre a problémát.

Ebben az útmutatóban végigvezetünk egy teljes, azonnal futtatható példán, amely **észleli a hiányzó betűkészleteket**, **kíméletesen kezeli a hiányzó betűkészleteket**, és megmutatja, hogyan **szabhatod testre a dokumentum betöltését** egy figyelmeztető visszahívással. A végére egy önálló Java osztályod lesz, amelyet bármelyik projektbe beilleszthetsz – nincs szükség további dokumentáció keresgélésre.

## Amire szükséged lesz

- Java 8 vagy újabb (a kód Java 11+‑el is működik)  
- Aspose.Words for Java könyvtár (23.9 vagy újabb verzió)  
- Egy DOCX fájl, amely olyan betűkészletet hivatkozik, amely nincs telepítve a gépeden (pl. egy egyedi vállalati betűtípus)  

Ha még nem adtad hozzá az Aspose.Words‑t a Maven projektedhez, egyszerűen illeszd be:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Ennyi – nincs szükség extra pluginekre, nincs natív függőség.

---

## Step 1: A WarningCallback mechanizmus megértése

A **warning callback** az Aspose.Words módja annak, hogy figyelmeztesen, amikor valami váratlan történik a dokumentum betöltése vagy mentése közben. Az `IWarningCallback` implementálásával teljes irányítást kapsz arról, mi kerül naplózásra, mi kerül figyelmen kívül hagyásra, vagy akár mi válik kivétellé.

> **Miért fontos ez:**  
> Ha egy betűkészlet hiányzik, az Aspose egy helyettesítő betűt használ. A vizuális eredmény drámaian eltérhet, különösen a márka‑orientált PDF‑eknél. A `WarningType.FONT_SUBSTITUTION` elkapásával naplózhatod a pontos betűkészlet nevét, eldöntheted, hogy megszakítsd-e a folyamatot, vagy programozottan saját egyéni betűt helyettesíthetsz.

## Step 2: LoadOptions példány létrehozása

A `LoadOptions` a belépési pont a dokumentum betöltésének testreszabásához. A visszahívást ehhez az objektumhoz csatolod, mielőtt ténylegesen betöltenéd a fájlt.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

Ekkor a `loadOptions` csak egy egyszerű tároló – még semmi sem történik. A valódi varázslat akkor kezdődik, amikor beillesztjük a visszahívást.

## Step 3: A visszahívás implementálása és csatolása

Az alábbi kompakt anonim osztály implementálja az `IWarningCallback`‑t. Barátságos sorral ír a konzolra, valahányszor betűkészlet‑helyettesítés történik.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Pro tipp:** Ha **a hiányzó betűkészleteket** egy helyettesítővel szeretnéd kezelni, beállíthatod a `FontSettings`‑et a `LoadOptions`‑on, és a hiányzó betűkészleteket egy ismert helyettesítőre térképezheted.

## Step 4: Dokumentum betöltése egyéni beállításokkal

Most, hogy a visszahívás be van kötve, töltsd be a dokumentumot. Ha a fájl olyan betűkészletet hivatkozik, amely nincs nálad, a figyelmeztetés megjelenik.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

A program futtatásakor a konzol például a következőt írhatja:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Ez a sor bizonyítja, hogy sikeresen **észlelted a hiányzó betűkészleteket**, és most már **kezelheted a hiányzó betűkészleteket** a saját igényeid szerint.

## Step 5: Opcionális – Hiányzó betűkészletek cseréje egy ismert betűkészletre

Ha automatikusan szeretnéd kicserélni a hiányzó betűkészletet, mondjuk `Times New Roman`‑ra, hozzáadhatsz egy `FontSettings` objektumot:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Most a dokumentum betöltődik, és minden `MyCustomFont` hivatkozás csendben `Times New Roman`‑ra vált. A konzol továbbra is jelzi, mi lett helyettesítve, így naprakész maradsz.

## Teljes működő példa

Az alábbi egyetlen Java osztály tartalmazza a fenti lépéseket. Másold be az IDE‑dbe, állítsd be a `docPath`‑t, és futtasd.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Várható kimenet**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Most már van egy reprodukálható módszered a **hiányzó betűkészletek észlelésére**, **kezelésére**, és a **dokumentum betöltésének testreszabására** – mindezt a **helyes visszahívás beállításának** megtanulásával.

## Gyakran Ismételt Kérdések

### Mi a teendő, ha azt szeretném, hogy a program leálljon a betöltés közben, ha egy betűkészlet hiányzik?

Kivételt dobunk a `warning` metódusban:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

Az alul lévő `catch` blokk elkapja, és eldöntheted, hogyan naplózod vagy értesíted a felhasználót.

### Működik ez a DOCX‑ből generált PDF‑eknél is?

Természetesen. A visszahívás a **betöltési** fázisban aktiválódik, ami minden kimeneti formátumnál (PDF, DOCX, HTML stb.) azonos. Amíg ugyanazt a `LoadOptions`‑t használod a forrásdokumentum betöltéséhez, a hiányzó betűkészleteket a végső PDF‑nél még megjelenés előtt elkapod.

### Rögzíthetek más figyelmeztetéstípusokat is (pl. képkonverzió)?

Igen – a `WarningInfo.getWarningType()` összehasonlítható más enumokkal, például `WarningType.IMAGE_CONVERSION`‑nal. Csak adj hozzá további `if` ágakat a visszahíváshoz.

### Van teljesítménybeli hatása?

Elhanyagolható. A visszahívás szinkron módon fut a betöltés során, és a plusz ellenőrzések könnyűek. Ha több ezer dokumentumot töltesz be, érdemes lehet a termelésben letiltani a figyelmeztetéseket a `loadOptions.setWarningCallback(null);` beállítással.

## Vizuális áttekintés

![példa a visszahívás beállítására az Aspose.Words Java-ban](https://example.com/images/callback-diagram.png "példa a visszahívás beállítására az Aspose.Words Java-ban")

*A diagram a folyamatot ábrázolja: `LoadOptions` → `IWarningCallback` → Dokumentum betöltése → Betűkészlet helyettesítés kezelése.*

## Összegzés

Áttekintettük, hogyan **állítsuk be a visszahívást** az Aspose.Words Java-ban, bemutattuk a **hiányzó betűkészletek észlelését**, gyakorlati módszereket a **hiányzó betűkészletek kezelésére**, és elmagyaráztuk, hogyan **szabhatod testre a dokumentum betöltését** a `LoadOptions`‑szal.  

Ezzel a tudással most már megvédheted a dokumentumfolyamataidat a csendes betűcsere ellen, megőrizheted a márka egységességét, és egyértelmű visszajelzést adhatsz a felhasználóknak, ha valami nem a terv szerint alakul.

### Mi a következő lépés?

- Fedezd fel a **betűkészlet‑helyettesítési táblákat** a hiányzó betűkészletek tömeges leképezéséhez.  
- Kombináld ezt a visszahívást **dokumentumvalidációval**, hogy érvényesítsd a stílusirányelveket.  
- Próbálj ki **egyedi figyelmeztető visszahívásokat**, amelyek naplófájlba vagy felügyeleti rendszerbe írnak a `System.out` helyett.  

Kísérletezz nyugodtan, és oszd meg velünk, hogyan testre szabtad a visszahívást a saját projektjeidben. Boldog kódolást!

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódrészleteket és lépésről‑lépésre magyarázatokat tartalmaz, hogy elsajátíthasd a további API‑funkciókat, és alternatív megvalósítási megközelítéseket fedezhess fel saját projektjeidben.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}