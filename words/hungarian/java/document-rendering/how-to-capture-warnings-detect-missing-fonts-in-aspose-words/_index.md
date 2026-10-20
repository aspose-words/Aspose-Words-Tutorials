---
category: general
date: 2026-03-19
description: Tanulja meg, hogyan rögzítse a figyelmeztetéseket az Aspose.Words for
  Java-ban, és hogyan észlelje a hiányzó betűtípusokat. Ez a lépésről‑lépésre útmutató
  azt is bemutatja, hogyan kezelje a hiányzó betűtípusokat elegánsan.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: hu
og_description: Hogyan rögzítsük a figyelmeztetéseket az Aspose.Words for Java-ban,
  észleljük a hiányzó betűtípusokat, és kezeljük őket egy teljes kódrészlettel.
og_title: Hogyan rögzítsünk figyelmeztetéseket – Hiányzó betűtípusok felderítése az
  Aspose.Words-ben
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Hogyan rögzítsünk figyelmeztetéseket – Hiányzó betűtípusok észlelése az Aspose.Words-ben
url: /hu/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan rögzítsünk figyelmeztetéseket – Hiányzó betűkészletek észlelése az Aspose.Words-ban

Gondolkodtál már azon, **hogyan rögzítsünk figyelmeztetéseket**, amikor egy Word-dokumentum betöltődik, és néhány betűkészlet nem érhető el a gépen? Nem vagy egyedül. Sok valós projektben a hiányzó betűkészletek csendes elrendezésváltozásokat okoznak, és az egyetlen módja annak, hogy megtudd, mi történt, ha figyeled az Aspose.Words által kibocsátott figyelmeztetési adatfolyamot.  

Ebben az útmutatóban végigvezetünk egy teljes, azonnal futtatható példán, amely **észleli a hiányzó betűkészleteket**, megmutatja, **hogyan lehet programozottan észlelni a hiányzó betűkészleteket**, és még egy gyors tippet ad a **hiányzó betűkészletek kezelése** kapcsán, hogy a kimenet előre látható maradjon.

> **Gyors megjegyzés:** A kód az Aspose.Words 23.9‑el (vagy újabb verzióval) működik, és Java 8+‑at igényel.

---

## Amire szükséged lesz

- **Aspose.Words for Java** (Maven/Gradle függőség vagy JAR az osztályúton)  
- Egy Word-fájl (`input.docx`), amely egy a rendszeredben nincs telepítve lévő betűkészletet hivatkozik (pl. „Comic Sans MS”)  
- Java IDE vagy egyszerű `javac`/`java` parancssori környezet  

Más könyvtárakra nincs szükség – minden más az Aspose.Words csomagban található.

---

## 1. lépés – LoadOptions beállítása a figyelmeztetések rögzítéséhez  

Ahhoz, hogy elkezdj figyelmeztetéseket hallgatni, létre kell hoznod egy `LoadOptions` példányt. Ez az objektum azt mondja a betöltőnek, hogy kövesse nyomon az összes felmerülő problémát, például a hiányzó betűkészleteket.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Miért fontos:** `LoadOptions` nélkül a betöltő csendben helyettesíti a hiányzó betűkészleteket az alapértelmezett rendszerbetűtípussal, és sosem tudnád, hogy helyettesítés történt. A figyelmeztetések engedélyezése teljes láthatóságot biztosít.

---

## 2. lépés – Dokumentum betöltése a LoadOptions használatával  

Most ténylegesen betöltjük a dokumentumot. A frissen létrehozott `LoadOptions` a konstruktorba kerül átadásra, így a feldolgozás során keletkezett figyelmeztetések rögzítésre kerülnek.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Pro tipp:** Ha sok fájlt dolgozol fel egy kötegben, használd újra ugyanazt a `LoadOptions` példányt, hogy elkerüld a felesleges objektumlétrehozást.

---

## 3. lépés – Rögzített figyelmeztetések bejárása  

Aspose.Words minden figyelmeztetést egy `WarningInfo` objektumban tárol. Csak a betűkészlettel kapcsolatos figyelmeztetések érdekelnek, ezért szűrünk a `FontSubstitutionWarningInfo` típusra.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Magyarázat:**  
- A `document.getWarnings()` egy listát ad vissza az összes betöltés közben keletkezett figyelmeztetésről.  
- A `FontSubstitutionWarningInfo` két kulcsfontosságú adatot tartalmaz: a **kért betűkészletet** (amelyet a DOCX kért) és a **valódi betűkészletet**, amelyre az Aspose.Words visszatér.  
- Mindkettő kiírásával azonnal látod, mely betűkészletek hiányoznak és milyen helyettesítés történt.

---

## 4. lépés – (Opcionális) Hiányzó betűkészletek kezelése programozottan  

A figyelmeztetések rögzítése csak a történet felét jelenti. Miután tudod, hogy egy betűkészlet hiányzik, érdemes **kezelni a hiányzó betűkészleteket** egy egyedi helyettesítéssel vagy a probléma naplózásával későbbi áttekintés céljából.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**Miért érdemes ezt tenni?**  
- Biztosítja a következetes megjelenítést a különböző gépek között.  
- Megakadályozza a váratlan elrendezésváltozásokat a később generált PDF-ekben vagy képekben.  

A figyelmeztetés részleteit tárolhatod adatbázisban, küldhetsz e‑mailt a tartalmi csapatnak, vagy akár megszakíthatod a folyamatot, ha kritikus betűkészlet hiányzik.

---

## Teljes működő példa  

Az alábbiakban a teljes, futtatható program látható. Csak cseréld le a `YOUR_DIRECTORY/input.docx`-t a tesztfájlod elérési útjára, add hozzá az Aspose.Words JAR-t az osztályúthoz, és futtasd.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Várható kimenet** (ha a „Comic Sans MS” hiányzik):

```
Requested: Comic Sans MS → Substituted: Arial
```

A opcionális helyettesítő kód futtatása után a mentett `output.docx` **Arial**-t használ mindenhol, ahol eredetileg a „Comic Sans MS” volt hivatkozva.

---

## Gyakori kérdések és szélhelyzetek  

| Kérdés | Válasz |
|----------|--------|
| *Mi van, ha a dokumentumnak több hiányzó betűkészlete van?* | A ciklus minden egyes hiányzó betűkészlethez kiad egy figyelmeztetést. Gyűjtheted őket egy `Map<String, String>`-ben kötegelt feldolgozáshoz. |
| *Működik ez a dokumentumból generált PDF-ekkel is?* | Természetesen. A betűkészlet helyettesítés a betöltési fázisban történik, így bármely későbbi export (PDF, HTML, kép) a feloldott betűkészleteket használja. |
| *Elnyomhatom a figyelmeztetéseket a rögzítés helyett?* | Igen – állítsd be a `loadOptions.setWarningCallback(null);` értéket, de elveszíted a hiányzó betűkészletek láthatóságát. |
| *A figyelmeztetési lista törlődik mentés után?* | A figyelmeztetési gyűjtemény a `Document` példányhoz tartozik. A `document.save()` hívása után a lista változatlan marad, hacsak nem hozol létre új `Document`-ot. |
| *Mi van a DOCX-be beágyazott egyedi betűkészletekkel?* | A beágyazott betűkészleteket elérhetőnek tekinti; az Aspose.Words használni fogja őket akkor is, ha nincsenek telepítve a gazdagépen. |

---

## Profi tippek éles környezethez  

- **FontSettings gyorsítótárazása:** Ha több száz fájlt dolgozol fel, hozz létre egyetlen `FontSettings`-et a kívánt helyettesítésekkel, és használd újra, hogy elkerüld a többletterhelést.  
- **Strukturált adatok naplózása:** A sima `System.out` helyett írd a figyelmeztetéseket egy JSON naplóba – ez egyszerűvé teszi a downstream elemzéseket (pl. „legtöbb hiányzó betűkészlet”).  
- **Korai validálás:** Futtass egy gyors „száraz‑betöltést” `LoadOptions`-szel a nehéz feldolgozás előtt; ha kritikus betűkészletek hiányoznak, állj le időben.  
- **Szálbiztonság:** A `Document` objektumok nem szálbiztosak. Tartsd minden fájl feldolgozását külön szálon vagy használj szál‑lokális `LoadOptions`-t.  

---

## Összegzés  

Most már tudod, **hogyan rögzítsünk figyelmeztetéseket** az Aspose.Words for Java-ban, **észleld a hiányzó betűkészleteket**, és **kezelheted a hiányzó betűkészleteket** egy tiszta helyettesítési stratégiával. A `LoadOptions` használatával és a `document.getWarnings()` bejárásával teljes rálátást kapsz a betűkészlet helyettesítési eseményekre, biztosítva, hogy a generált dokumentumok minden környezetben pontosan úgy néznek ki, ahogy elvárod.  

Készen állsz a következő lépésre? Próbáld meg kiterjeszteni ezt a mintát **hiányzó képek észlelésére**, **nem támogatott funkciók nyomon követésére**, vagy akár **hiányzó betűkészletek automatikus beágyazására** a kimeneti fájlba. Ugyanaz a figyelmeztetés‑rögzítési megközelítés sok más dokumentumfeldolgozási helyzetben működik, így a kódod robusztus és jövőbiztos lesz.  

Boldog kódolást, és legyenek a dokumentumaid mindig gyönyörűen megjelenítve!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}