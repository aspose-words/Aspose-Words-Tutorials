---
category: general
date: 2026-06-27
description: Tanulja meg, hogyan rögzítse a betűtípus‑helyettesítési figyelmeztetéseket
  Java‑ban az Aspose.Words segítségével. Ez a lépésről‑lépésre útmutató a figyelmeztetési
  visszahívásokat és a LoadOptions használatát is bemutatja.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: hu
og_description: Rögzítse a betűtípuscsere figyelmeztetéseket Java-ban az Aspose.Words
  segítségével. Kövesse ezt az útmutatót a figyelmeztetési visszahívások beállításához,
  a LoadOptions használatához és a hiányzó betűtípusok kezeléséhez.
og_title: Betűkészlet-helyettesítési figyelmeztetések rögzítése Java-ban – Aspose.Words
  útmutató
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Betűtípus-helyettesítési figyelmeztetések rögzítése Java-ban az Aspose.Words
  használatával – Teljes útmutató
url: /hu/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus‑helyettesítési figyelmeztetések rögzítése Java‑ban az Aspose.Words segítségével – Teljes útmutató

Valaha is szükséged volt **betűtípus‑helyettesítési figyelmeztetések** rögzítésére egy olyan DOCX betöltésekor, amely egzotikus betűtípusokat használ? Nem vagy egyedül. Sok valós projektben—gondolj az automatizált jelentésgenerátorokra vagy kötegelt dokumentumkonvertálókra—hiányzó betűtípusok csendes helyettesítéseket váltanak ki, amelyek tönkretehetik a megjelenés pontosságát.  

Szerencsére az Aspose.Words tiszta módot biztosít ezeknek a figyelmeztetéseknek a figyelésére. Ebben az útmutatóban végigvezetünk a **LoadOptions** beállításán, egy **Aspose.Words warning callback** csatlakoztatásán, és minden *betűtípus‑helyettesítés* értesítés kiírásán a konzolra. A végére pontosan tudni fogod, mikor cserélődött ki egy betűtípus, és hogyan reagálhatsz programozottan.

> **Mit kapsz:** egy teljesen futtatható Java‑kódrészletet, egy magyarázatot arra, *miért* fontos minden részlet, valamint tippeket a széljegyek kezeléséhez, például egyedi betűtípus‑könyvtárak esetén.

## Előfeltételek és amire szükséged lesz

- Java 8 vagy újabb telepítve (a kód Java 11+‑el is működik).
- A legújabb Aspose.Words for Java JAR (letölthető a hivatalos oldalról vagy a Maven Central‑ról).
- Egy DOCX fájl, amely olyan betűtípusokra hivatkozik, amelyek nincsenek telepítve a gépeden (például egy *font‑rich.docx* a Aspose demókészletében).
- Egy megfelelő IDE (IntelliJ IDEA, Eclipse, vagy akár VS Code Java‑kiegészítőkkel).

Nem szükséges semmilyen külső könyvtár az Aspose.Words‑en kívül, és a példa egy egyszerű `main` metódusban fut.

## 1. lépés: LoadOptions beállítása – A testreszabott betöltés belépési pontja

`LoadOptions` az Aspose.Words konfigurációs tárolója, amely megmondja a könyvtárnak, *hogyan* olvassa be a dokumentumot. Alapértelmezés szerint csendben helyettesíti a hiányzó betűtípusokat, de ezt a viselkedést egy figyelmeztetési visszahívással megváltoztathatod.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Miért fontos:** `LoadOptions` nélkül a dokumentum csendben töltődik be, és elveszíted a láthatóságot a hiányzó betűtípusok felett. Egy példány létrehozásával csatlakozhatsz a figyelmeztetési rendszerhez.

## 2. lépés: Figyelmeztetési visszahívás definiálása a *betűtípus‑helyettesítési figyelmeztetések* rögzítéséhez

Az Aspose.Words a figyelmeztetési eseményeket az `IWarningCallback` interfészen keresztül küldi. Implementáld inline‑ban (vagy külön osztályként), és szűrd a `WarningType.FONT_SUBSTITUTION` típusú eseményeket.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Magyarázat:**  
- `info.getWarningType()` megadja a figyelmeztetés kategóriáját.  
- `WarningType.FONT_SUBSTITUTION` az a felsorolt érték, amely érdekel minket.  
- `info.getDescription()` egy ember által olvasható üzenetet tartalmaz, például *„Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

A leírás kiírásával **valós időben rögzíted a betűtípus‑helyettesítési figyelmeztetéseket**.

## 3. lépés: Dokumentum betöltése a konfigurált LoadOptions használatával

Most, hogy a visszahívás be van állítva, töltsd be a DOCX‑edet. A figyelmeztetési visszahívás automatikusan lefut a feldolgozás során.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Cseréld le a `YOUR_DIRECTORY`‑t a tesztfájlod tényleges elérési útjára. Amikor a `Document` konstruktor lefut, minden hiányzó betűtípus aktiválja a korábban definiált visszahívást, és a helyettesítési üzeneteket a konzolon láthatod.

## 4. lépés: A betöltött dokumentum ellenőrzése (opcionális, de hasznos)

Betöltés után érdemes lehet ellenőrizni a dokumentum integritását—oldalszám, szövegkinyerés stb. Ez a lépés nem kötelező a figyelmeztetések rögzítéséhez, de segít látni a helyettesítések hatását.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Ha egy betűtípust helyettesítettek, a layout enyhén eltolódhat; az oldalszám ellenőrzése feltárhatja ezeket a változásokat.

## 5. lépés: Haladó – Helyettesített betűtípusok programozott kezelése

Néha nem csak naplózni akarod a figyelmeztetést—szükséged lehet egy tartalék betűtípus beágyazására vagy a stílus módosítására. Az alábbi gyors minta segíthet.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Az Aspose.Words‑t egy olyan mappára irányítva, amely a eredeti betűtípusokat tartalmazza, *megelőzheted* a helyettesítést teljesen. Ha a mappa hiányzik, a figyelmeztetési visszahívás továbbra is rögzíti az eseményt, így van egy tartalék stratégiád.

## Teljes működő példa

Összegezve, itt a teljes, készen álló program:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Várható konzolkimenet** (ha hiányzó betűtípust talál):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Ha minden betűtípus jelen van, a visszahívás csendben marad—semmi sem kerül kiírásra, ami pontosan az elvárt viselkedés.

## Gyakori buktatók és profi tippek

| Buktató | Miért fordul elő | Javítás |
|---------|------------------|--------|
| **A visszahívás soha nem fut le** | Elfelejtetted csatolni a visszahívást a `LoadOptions`‑hez **vagy** a `Document` alapértelmezett konstruktorát használtad `loadOptions` átadása nélkül. | Mindig hívd meg a `loadOptions.setWarningCallback(...)`‑t **és** használd a `new Document(path, loadOptions)` túlterhelést. |
| **Túl sok figyelmeztetés tömöríti a naplót** | Nagy dokumentumok sok hiányzó betűtípussal minden helyettesítéshez egy figyelmeztetést generálnak. | Szűrd tovább a `info.getDescription()`‑t konkrét betűtípus‑nevekre, vagy gyűjtsd össze a figyelmeztetéseket egy listába későbbi feldolgozásra. |
| **A helyettesített betűtípusok befolyásolják a layoutot** | A tartalék betűtípus méretei (méret, távolság) eltérhetnek. | Adj meg egy egyedi betűtípus‑mappát (lásd 5. lépés) vagy állítsd be a dokumentum stílusát betöltés után. |
| **Futtatás fej nélküli szerveren** | Az alapértelmezett betűtípus‑tartalék a rendszer betűtípusaira támaszkodhat, amelyek a szerveren nincsenek telepítve. | Szállítsd a szükséges betűtípusokat az alkalmazásoddal, és irányítsd a `FontSettings`‑et arra a mappára. |

## Gyakran ismételt kérdések

**Q: Működik ez PDF‑el vagy más formátumokkal?**  
A: Igen. A figyelmeztetési visszahívás formátum‑független; minden olyan dokumentumtípusra aktiválódik, amelyet az Aspose.Words betölt (DOC, DOCX, RTF, HTML stb.). Az egyetlen különbség a megjelenő figyelmeztetések halmazában van.

**Q: Rögzíthetek más típusú figyelmeztetéseket is, például *képfelbontási* figyelmeztetéseket?**  
A: Természetesen. A `warning` metódusban vizsgáld meg a `info.getWarningType()`‑t más enum értékek, például `WarningType.IMAGE_RESOLUTION` esetén, és kezeld őket ennek megfelelően.

**Q: Mi van, ha a dokumentum betöltése után szükségem van a helyettesített betűtípusok listájára?**  
A: Tárold a `info.getDescription()`‑t egy `List<String>`‑ben a visszahíváson belül. Betöltés után egy gyűjteményed lesz, amelyet naplózhatsz, küldhetsz egy felügyeleti szolgáltatásnak, vagy betűtípus‑letöltési rutin indítására használhatsz.

## Összegzés

Most már tudod, **hogyan rögzítsd a betűtípus‑helyettesítési figyelmeztetéseket** Java‑ban az Aspose.Words segítségével, miért fontos minden komponens, és hogyan bővítheted a megoldást valós környezetekhez. A `LoadOptions`, egy `Aspose.Words warning callback` és opcionálisan a `FontSettings` használatával teljes láthatóságot nyersz a hiányzó betűtípusok felett, és megbízhatóvá teheted a dokumentum‑konverziós folyamatokat.

Készen állsz a következő lépésre? Cseréld le a `System.out.println`‑t egy SLF4J‑szerű loggerre, vagy integráld a figyelmeztetési listát egy UI‑ba, amely a felhasználókat értesíti a kötegelt konverzió véglegesítése előtt. Továbbá felfedezheted az **Aspose.Words warning callback** további típusait, például *nem támogatott funkciók* vagy *magas felbontású kép* figyelmeztetéseket.  

Boldog kódolást, és hogy a PDF‑jeid soha ne szenvedjenek váratlan betűtípus‑cseréktől!

![Screenshot showing console output of captured font substitution warnings](image-placeholder.png "capture font substitution warnings")

## Mi legyen a következő tanulnivalód?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljesen működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API‑funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Enable Font Substitution Warnings in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Create PDF Documents with Aspose.Words for Java | Document Processing API](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}