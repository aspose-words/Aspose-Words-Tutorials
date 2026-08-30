---
category: general
date: 2026-04-28
description: Iterálja a dokumentumfigyelmeztetéseket egy Word-fájlban a hiányzó betűtípusok
  észleléséhez, szerezze be a hiányzó betűtípusok nevét, és nyomtassa ki a hiányzó
  betűtípus részleteit az Aspose.Words for Java használatával.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: hu
og_description: A dokumentum figyelmeztetéseinek bejárásával keresse meg a hiányzó
  betűtípusokat, szerezze be a hiányzó betűtípusok nevét, és nyomtassa ki a hiányzó
  betűtípusok részleteit egy teljes Java példával.
og_title: 'Iterálja a dokumentumfigyelmeztetéseket: Hiányzó betűtípusok észlelése
  Java‑ban'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iterálja a dokumentumfigyelmeztetéseket: Hiányzó betűtípusok észlelése Java‑ban'
url: /hu/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumfigyelmeztetések iterálása – Hiányzó betűkészletek észlelése Java-ban

Valaha is szükséged volt **dokumentumfigyelmeztetések iterálására**, amikor egy Word‑fájlt nyitsz meg, és kíváncsi vagy, hogy mely betűkészletek hiányoznak? Nem vagy egyedül. A hiányzó betűkészletek tönkretehetik egy jelentés megjelenését, és ha nincs mód a felderítésükre, előfordulhat, hogy egy olyan dokumentumot küldesz ki, ami egyáltalán nem hasonlít az eredetihez.  

Ebben az útmutatóban megmutatjuk, hogyan **észleld a hiányzó betűkészleteket** egy Word‑dokumentum betöltésével, a figyelmeztetések iterálásával, a hiányzó betűkészletek nevének lekérdezésével, és végül a hiányzó betűkészletek információjának kiírásával – mindezt az Aspose.Words for Java segítségével.  

Az első kódsortól a várt konzolkimenetig mindent lefedünk, így mostantól egy működő megoldást egyszerűen be tudsz másolni a projektedbe. Nem szükséges extra dokumentáció.

## Előfeltételek

- Java 8 vagy újabb telepítve.
- Aspose.Words for Java könyvtár (a legújabb verzió 2026‑04‑28 állapotában).
- Egy Word‑fájl, amely esetleg olyan betűkészleteket tartalmaz, amelyek nincsenek telepítve a gépeden (pl. `doc-with-missing-font.docx`).

Ha már megvannak ezek, nagyszerű – készen állsz a **word dokumentum betöltésére** és az iterálás megkezdésére.

## 1. lépés – Word dokumentum betöltése alapértelmezett beállításokkal

Mielőtt **dokumentumfigyelmeztetéseket iterálnánk**, a fájlt be kell tölteni a memóriába. Az Aspose.Words ezt egyetlen konstruktorhívással teszi lehetővé. Az alapértelmezett `LoadOptions` általában elegendő, de a tisztaság kedvéért megmutatjuk a kifejezett létrehozást.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Miért fontos:**  
> A dokumentum betöltésekor az Aspose.Words átvizsgálja a fájlt minden olyan erőforrás után, amelyet nem tud feloldani, például a helyileg nem telepített betűkészleteket. Ezek a problémák **figyelmeztetésként** kerülnek tárolásra, amelyeket a következő lépésben **dokumentumfigyelmeztetések iterálásával** dolgozunk fel.

## 2. lépés – Dokumentumfigyelmeztetések iterálása a betűkészlet‑problémák megtalálásához

Most jön a megoldás szíve: végigmegyünk minden figyelmeztetésen, amelyet a könyvtár a betöltés során gyűjtött. A `WarningInfo` objektumok elmondják, mi ment rosszul, és szűrhetünk `FontSubstitutionWarning` típusra, hogy **észleljük a hiányzó betűkészleteket**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Pro tipp:** Az `instanceof` ellenőrzés biztosítja, hogy csak a betűkészlet‑kapcsolódó figyelmeztetéseket kezeljük, a többi, például a képek betöltésével kapcsolatos problémát figyelmen kívül hagyva. Ez hatékonyabbá teszi a ciklust, és a kimenet csak a ténylegesen **hiányzó betűkészlet lekérdezéséhez** szükséges információkat tartalmazza.

### Várt konzolkimenet

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Ha a dokumentumban nincs hiányzó betűkészlet, a ciklus egyszerűen csendben befejeződik – nincs mit **kiírni a hiányzó betűkészletről**.

## 3. lépés – Miért nem elég csak egy kivételt elkapni?

Gondolhatod, hogy „Miért ne csomagolnám a `new Document(...)` hívást egy try‑catch‑be, és figyelném a kivételt?” A válasz kettős:

1. **Részletes információ:** A kivételek csak azt mondják, hogy valami hibát okozott. A figyelmeztetések megadják a pontos betűkészlet‑nevet és a helyettesítő betűt, amelyet az Aspose.Words választott.
2. **Nem‑kritikus problémák:** A hiányzó betűkészletek általában nem kritikusak; a dokumentum betöltődik, de a vizuális hűség csorbul. **Dokumentumfigyelmeztetések iterálásával** megőrizheted a fájl további feldolgozásának lehetőségét.

## 4. lépés – A példa kiterjesztése: Hiányzó betűkészletek gyűjtése listába

Néha a hiányzó betűkészletekre további feldolgozásra van szükség – például beágyazásra vagy felhasználói értesítésre. Íme egy gyors módosítás, amely a neveket egy `Set<String>`‑be gyűjti.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Most már van egy tiszta módja annak, hogy **hiányzó betűkészletet lekérdezz** programozottan, amit továbbadhatsz egy jelentésmodulnak vagy egy betűkészlet‑telepítő varázslónak.

## 5. lépés – Gyakorlati megfontolások

- **Több helyettesítés:** Egyetlen hiányzó betűkészletet a dokumentum különböző részein különböző betűkészletek helyettesíthetnek. A figyelmeztetési lista minden előfordulást tartalmaz, így előfordulhatnak duplikált hiányzó‑betűkészlet bejegyzések.
- **Teljesítmény:** Nagyon nagy dokumentumok betöltése ezrek figyelmeztetését generálhatja. Ha csak a betűkészletek érdekelnek, szűrd le a ciklust már a kezdeti lépésben, hogy a feldolgozás gyors maradjon.
- **Keresztplatformos betűkészletek:** Linuxon az alapértelmezett helyettesítő betűkészlet gyakran *Liberation Sans*, Windowson pedig *Arial*. A helyettesítő ismerete segít eldönteni, szükséges‑e saját betűkészleteket szállítani az alkalmazással.

## 6. lépés – Vizuális segédlet

Alább látható a konzolkimenet képernyőképe (az alt‑szöveg tartalmazza a fő kulcsszót a SEO‑célokra).

![Iterate document warnings console output showing missing fonts and their substitutes](/images/iterate-document-warnings.png)

*Alt szöveg:* *dokumentumfigyelmeztetések iterálása példája, amely a hiányzó betűkészletek neveit és a helyettesítéseket jeleníti meg.*

## Összegzés

Most már tudod, hogyan **iteráld a dokumentumfigyelmeztetéseket** az Aspose.Words for Java‑ban, hogyan **észleld a hiányzó betűkészleteket**, hogyan **tölts be word dokumentumot** biztonságosan, hogyan **lekérdezd a hiányzó betűkészlet** információkat, és hogyan **írd ki a hiányzó betűkészlet** részleteit a konzolra. A teljes kódrészlet azonnal futtatható, és könnyen átalakítható fájlba naplózásra, UI‑párbeszédablak megjelenítésére vagy a hiányzó betűkészletek automatikus beágyazására.

A következő lépésként érdemes megvizsgálni, hogyan **tölts be word dokumentumot** egyedi betűkészlet‑forrásokkal (például egy vállalati betűkészlet‑mappával), vagy hogyan ágyazd be a hiányzó betűkészleteket közvetlenül a fájlba, hogy a megjelenés minden gépen megmaradjon. Mindkét téma természetes folytatása annak, amit itt megtanultál.

Boldog kódolást, és legyenek a PDF‑jeid mindig úgy formázva, ahogy elvárod!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}