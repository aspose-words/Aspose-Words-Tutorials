---
category: general
date: 2026-07-20
description: Könnyedén módosíthatja a lábjegyzetek távolságát DOCX fájlokban. Tanulja
  meg, hogyan állíthat be távolságot, szabályozhatja a lábjegyzet elválasztót, és
  állíthatja be a bekezdés sorközét Java segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote spacing
- how to set spacing
- adjust footnote separator
- set paragraph line spacing
- change line spacing docx
language: hu
lastmod: 2026-07-20
og_description: A lábjegyzetek távolságának gyors módosítása DOCX fájlokban. Ez az
  útmutató bemutatja, hogyan állítható be a távolság, módosítható a lábjegyzet-elválasztó,
  és testreszabható a bekezdés sortávolsága Java-ban.
og_image_alt: Screenshot showing Java code that changes footnote spacing in a DOCX
  document
og_title: Lábjegyzetek távolságának módosítása DOCX-ben – Lépésről lépésre útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-20'
  description: Change footnote spacing in DOCX files easily. Learn how to set spacing,
    adjust footnote separator, and set paragraph line spacing with Java.
  headline: Change footnote spacing in DOCX – Complete Guide
  type: TechArticle
tags:
- footnote
- docx
- java
- spacing
title: Lábjegyzetek távolságának módosítása DOCX-ben – Teljes útmutató
url: /hu/java/document-styling/change-footnote-spacing-in-docx-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Lábjegyzetek távolságának módosítása DOCX-ben – Teljes útmutató

Valaha szükséged volt már **lábjegyzetek távolságának módosítására** egy Word dokumentumban, de nem tudtad, hol kezdjed? Nem vagy egyedül. Legyen szó egy szakdolgozat csiszolásáról vagy egy szerződés finomhangolásáról, a lábjegyzet elválasztó megfelelő beállítása nagy különbséget jelenthet.

Ebben az útmutatóban végigvezetünk a **távolság beállításának** módján, a lábjegyzet elválasztó módosításán, és a **bekezdés sortávolságának** beállításán Java‑alapú könyvtárak segítségével. A végére egy azonnal futtatható példát kapsz, amelyet bármelyik projektbe beilleszthetsz.

## Amire szükséged lesz

- Java 17 vagy újabb (a kód a modern nyelvi funkciókat használja)
- Maven vagy Gradle a függőségkezeléshez
- Egy DOCX fájl legalább egy lábjegyzettel (vagy manuálisan is létrehozhatsz egyet)
- A **Aspose.Words for Java** könyvtár (vagy bármely kompatibilis API; a példában az Aspose‑t használjuk)

Ez minden—nincs nehéz keretrendszer, csak tiszta Java és egyetlen könyvtár.

![Lábjegyzetek távolságának módosítása DOCX példában](/images/footnote-spacing.png){alt="Lábjegyzetek távolságának módosítása DOCX példában"}

## 1. lépés: A DOCX dokumentum betöltése (Lábjegyzetek távolságának módosítása)

Az első dolog, amit tenned kell, hogy megnyitod a Word fájlt. Ez ad egy `Document` objektumot, amelyet manipulálhatsz.

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // Load the DOCX file – change the path to your own file
        Document doc = new Document("input.docx");
        
        // Continue with spacing adjustments...
        adjustFootnoteSeparator(doc);
        
        // Save the updated document
        doc.save("output.docx");
    }
}
```

*Miért fontos*: A dokumentum betöltése a kiindulópont a **lábjegyzetek távolságának módosításához**. `Document` példány nélkül nem érheted el a lábjegyzet elválasztót vagy bármelyik bekezdés formátumát.

## 2. lépés: A lábjegyzet elválasztó lekérése és módosítása (Lábjegyzet elválasztó módosítása)

A lábjegyzet elválasztó egy rejtett bekezdés, amely a főszöveg és a lábjegyzetlista között helyezkedik el. A sortávolság módosításához meg kell szerezni ezt a bekezdést, és finomhangolni a formátumát.

```java
private static void adjustFootnoteSeparator(Document doc) throws Exception {
    // Get the footnote separator (the first one is usually the default separator)
    FootnoteSeparator separator = doc.getFootnoteSeparator();
    
    // If the document has no separator (rare), create one
    if (separator == null) {
        separator = new FootnoteSeparator(doc);
        doc.getFootnotes().add(separator);
    }
    
    // Access the underlying paragraph and set line spacing
    Paragraph sepParagraph = separator.getSeparatorParagraph();
    ParagraphFormat fmt = sepParagraph.getParagraphFormat();
    
    // Set line spacing to 12 points – this is the core of "change footnote spacing"
    fmt.setLineSpacing(12.0);
    
    // Optional: also adjust spacing before/after if needed
    fmt.setSpaceBefore(0);
    fmt.setSpaceAfter(0);
}
```

### Hogyan oldja meg a problémát

- **A lábjegyzet elválasztó lekérése** – ez az a rész, amelyet valójában módosítani szeretnél, ezzel teljesítve az *lábjegyzet elválasztó módosítása* követelményt.
- **Sortávolság beállítása** – a `setLineSpacing(12.0)` közvetlenül megválaszolja, *hogyan állítsuk be a távolságot* az adott rejtett bekezdésnél.
- **Szélsőséges eset kezelése** – ha a dokumentum valamilyen módon nem tartalmaz elválasztót, akkor futás közben létrehozzuk, elkerülve a `NullPointerException`-t.

## 3. lépés: A változás ellenőrzése és mentése (Bekezdés sortávolságának beállítása)

Miután módosítottad az elválasztót, ellenőrizned kell, hogy a változás megmaradt-e. A mentett fájl Wordben való megnyitása megmutatja az új távolságot, de programozottan is ellenőrizheted.

```java
private static void verifySpacing(Document doc) throws Exception {
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
    System.out.println("Current footnote separator line spacing: " + spacing);
}
```

Adj hozzá egy `verifySpacing(doc);` hívást közvetlenül a `doc.save(...)` előtt a `main`‑ben. A program futtatásakor a következőt kell látnod:

```
Current footnote separator line spacing: 12.0
```

Ez megerősíti, hogy a **change line spacing docx** művelet sikeres volt.

## Gyakori hibák és profi tippek

- **Hiba**: `setLineSpacing` használata olyan értékkel, amely úgy néz ki, mint a “12”, de “12 pts” vagy “12 lines” értékként értelmeződik. Az Aspose pontokat vár, így a 12 12 pt‑ot jelent. Kétszeres sortávolsághoz használd a `24.0`‑t.
- **Profi tipp**: Ha egységes megjelenést szeretnél minden lábjegyzet típusnál (elválasztó, folytatási elválasztó stb.), ismételd meg ugyanazokat a lépéseket a `doc.getFootnoteContinuationSeparator()` és a `doc.getFootnoteContinuationNotice()` esetén.
- **Hiba**: Elfelejted meghívni a `save()`‑et a módosítások után. A memóriabeli dokumentum változik, de a lemezen lévő fájl változatlan marad.
- **Profi tipp**: Kombináld a távolságváltoztatásokat a stílusfrissítésekkel (`ParagraphStyle`) a teljesen kifinomult lábjegyzet szakasz érdekében.

## Teljes működő példa (Minden lépés egy fájlban)

```java
import com.aspose.words.*;

public class FootnoteSpacingDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Load the DOCX document
        Document doc = new Document("input.docx");

        // 2️⃣ Adjust the footnote separator – this is where we "change footnote spacing"
        adjustFootnoteSeparator(doc);

        // 3️⃣ Verify the new line spacing (optional but handy for debugging)
        verifySpacing(doc);

        // 4️⃣ Save the result – now your footnotes have the desired spacing
        doc.save("output.docx");
        System.out.println("Footnote spacing updated and saved to output.docx");
    }

    private static void adjustFootnoteSeparator(Document doc) throws Exception {
        FootnoteSeparator separator = doc.getFootnoteSeparator();
        if (separator == null) {
            separator = new FootnoteSeparator(doc);
            doc.getFootnotes().add(separator);
        }
        Paragraph sepParagraph = separator.getSeparatorParagraph();
        ParagraphFormat fmt = sepParagraph.getParagraphFormat();

        // Core operation: "set paragraph line spacing" for the separator
        fmt.setLineSpacing(12.0);   // 12 pt line spacing
        fmt.setSpaceBefore(0);
        fmt.setSpaceAfter(0);
    }

    private static void verifySpacing(Document doc) throws Exception {
        FootnoteSeparator sep = doc.getFootnoteSeparator();
        double spacing = sep.getSeparatorParagraph().getParagraphFormat().getLineSpacing();
        System.out.println("Current footnote separator line spacing: " + spacing);
    }
}
```

Másold a fenti kódot egy új Java osztályba, add hozzá az Aspose.Words Maven függőséget, és futtasd. Az `output.docx` most már **12 pt**‑ra állított lábjegyzet elválasztó sortávolsággal rendelkezik, ezzel hatékonyan **módosítva a lábjegyzetek távolságát**.

### Maven függőség

Add this snippet to your `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.9</version> <!-- Use the latest stable version -->
</dependency>
```

Ha a Gradle‑t részesíted előnyben, az ekvivalens a következő:

```gradle
implementation 'com.aspose:aspose-words:24.9'
```

## Összegzés

Épp most tanultad meg, hogyan **változtasd meg a lábjegyzetek távolságát** egy DOCX fájlban Java használatával. A dokumentum betöltésével, a **lábjegyzet elválasztó** lekérésével és a **bekezdés sortávolság beállításával** pontos irányítást kapsz a lábjegyzetek megjelenése felett.  

Innen tovább felfedezheted a kapcsolódó finomhangolásokat, például a lábjegyzet szövegstílus módosítását, egyedi elválasztók hozzáadását, vagy akár a tömeges frissítések automatizálását több dokumentumon.  

További kérdéseid vannak a **lábjegyzet elválasztó módosítása** vagy más Word automatizálási feladatok kapcsán? Írj egy megjegyzést, és jó kódolást!

## Mit tanulj meg legközelebb?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódrészleteket lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Ázsiai bekezdéstávolság és behúzások módosítása Word dokumentumban](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Ázsiai bekezdéstávolság és behúzások módosítása](/words/german/net/document-formatting/change-asian-paragraph-spacing-and-indents/)
- [Ázsiai bekezdéstávolság és behúzások módosítása](/words/french/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}