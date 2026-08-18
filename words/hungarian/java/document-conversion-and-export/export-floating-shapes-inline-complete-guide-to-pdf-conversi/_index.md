---
category: general
date: 2026-07-03
description: Exportálja a lebegő alakzatokat beágyazott módon a Word PDF-be konvertálása
  közben. Ismerje meg, hogyan állíthatja be a PDF beállításokat, és hogyan mentheti
  a Word dokumentumot PDF-ként Java-ban.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: hu
og_description: Exportálja a lebegő alakzatokat beágyazott módon, amikor Word dokumentumot
  PDF‑be konvertál. Ez az útmutató bemutatja, hogyan állíthatja be a PDF‑beállításokat,
  és hogyan mentheti a Word‑dokumentumot PDF‑formátumban.
og_title: Lebegő alakzatok beágyazott exportálása – Java PDF konverziós útmutató
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Lebegő alakzatok beágyazott exportálása – Teljes útmutató a PDF konverzióhoz
url: /hu/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Export Floating Shapes Inline – Teljes útmutató a PDF konverzióhoz

Szükséged volt már arra, hogy **export floating shapes inline**-t használj, amikor egy Word dokumentumot PDF‑be konvertálsz? Nem vagy egyedül – sok fejlesztő találkozik ezzel a problémával, amikor a diagramok vagy ikonok titokzatosan külön rétegekre kerülnek. A jó hír, hogy egyetlen PDF‑opció is képes a alakzatokat szorosan a `<span>` címkékbe helyezni, megőrizve a megjelenést pontosan úgy, ahogy a Word‑ben látható.

Ebben az útmutatóban végigvezetünk a **how to set PDF options** Java‑ban, megmutatjuk a pontos kódot a **save Word as PDF options**-hez, és elmagyarázzuk, miért lehet érdemes **convert Word to PDF inline**-t használni az alapértelmezett blokk‑szintű export helyett. A végére egy készen‑futó kódrészletet kapsz, amelyet bármely Maven vagy Gradle projektbe beilleszthetsz.

## Mit fogsz megtanulni

- A különbség a lebegő alakzatok inline `<span>` és blokk `<div>` exportja között.  
- Hogyan konfiguráljuk a `PdfSaveOptions`‑t az inline renderelés kényszerítéséhez.  
- Lépésről‑lépésre kód, amely betölti a `.docx`‑et, alkalmazza a beállítást, és PDF‑ként írja ki.  
- Gyakori buktatók (hiányzó betűkészletek, nem támogatott alakzatok) és azok elkerülése.  
- Tippek a kimenet teszteléséhez és a megközelítés kiterjesztéséhez más dokumentumelemekre.

**Prerequisites** – szükséged lesz Java 8 vagy újabb verzióra, az Aspose.Words for Java könyvtárra (vagy bármely API‑ra, amely tükrözi a `PdfSaveOptions` osztályt), valamint egy mint Word fájlra, amely lebegő alakzatokat tartalmaz (az útmutató a `FloatingShapes.docx`‑et használja). Más külső eszközre nincs szükség.

---

## 1. lépés: A forrás Word dokumentum betöltése

Az első dolog, amit csinálsz, hogy megnyitod a kívánt `.docx` fájlt a transzformáláshoz. Ez egyszerű, de ügyelj arra, hogy az útvonal abszolút vagy helyesen feloldott legyen a classpath‑ból.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Miért fontos ez:*  
Ha a dokumentum nincs megfelelően betöltve, a következő PDF konverzió `FileNotFoundException`‑t dob. A `Document` használata biztosítja, hogy a belső objektummodell teljesen fel legyen töltve, beleértve az oldalon lévő lebegő alakzatokat is.

## 2. lépés: PDF mentési beállítások létrehozása és a lebegő alakzatok inline beállítása

Itt történik a varázslat. Alapértelmezés szerint az Aspose.Words a lebegő alakzatokat blokk‑szintű `<div>` elemekként exportálja, ami megzavarhatja a HTML‑alapú PDF‑ek áramlását. A `setExportFloatingShapesAsInlineTag(true)` beállítása azt mondja a motornak, hogy minden alakzatot egy inline `<span>`‑be csomagoljon.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Miért fontos ez:*  
- **Layout fidelity** – Az inline címkék a alakzatot a környező szöveggel igazítva tartják, elkerülve a nem kívánt hézagokat.  
- **Searchability** – Az inline elemek nagyobb valószínűséggel kerülnek helyesen indexelésre a PDF‑olvasók által.  
- **Styling control** – A `<span>`‑t CSS‑sel célozhatod meg, ha később vissza szeretnéd konvertálni a PDF‑et HTML‑re.

> **Pro tip:** Ha valaha is szükséged lenne a régi blokk viselkedésre egy adott dokumentumban, egyszerűen add meg a `false` értéket, vagy hagyd ki a hívást teljesen.

## 3. lépés: Dokumentum mentése PDF‑ként a beállított opciókkal

Most összevonod a betöltött `Document`‑et a `PdfSaveOptions`‑szal, és kiírod a fájlt. Ez az egyetlen sor végzi a nehéz munkát.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Miért fontos ez:*  
A `save` metódus figyelembe veszi a `pdfOptions`‑on beállított minden jelzőt. Ha elfelejted átadni az opciókat, visszatér az alapértelmezett blokk exporthoz, ezzel aláássa a **export floating shapes inline** célját.

---

## Teljes működő példa

Összevonva mindent, itt egy kompakt program, amelyet most azonnal lefordíthatsz és futtathatsz. Cseréld le a `YOUR_DIRECTORY`‑t a géped tényleges útvonalára.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output** – A program futtatása után nyisd meg a `FloatingShapes.pdf`‑et. Látni fogod, hogy az alakzatok a szöveggel egy vonalban helyezkednek el, nincs extra fehér tér, és a HTML reprezentáció (ha megvizsgálod a PDF belső struktúráját) `<span>` címkéket tartalmaz minden alakzat körül.

![Export floating shapes inline példa](https://example.com/export-inline.png "Képernyőkép, amely a PDF‑ben inline renderelt lebegő alakzatokat mutatja")

*Kép alternatív szöveg:* **export floating shapes inline** képernyőkép a PDF‑ről inline alakzatokkal.

---

## Gyakori kérdések és szélhelyzetek

### 1. “Mi van, ha a dokumentumom összetett SmartArt‑ot tartalmaz?”

A SmartArt rajzobjektumként van kezelve. Az inline jelző a legtöbb vektor alakzatra működik, de a nagyon összetett SmartArt még mindig képként jelenhet meg. Ilyen esetben fontold meg a SmartArt laposítását a Word‑ben a konverzió előtt, vagy használd a `pdfOptions.setExportSmartArtAsImage(true)`‑t a képként való export kényszerítéséhez.

### 2. “Kombinálhatom az inline és block exportot ugyanabban a dokumentumban?”

Sajnos az API globálisan alkalmazza a beállítást. Ha vegyes viselkedésre van szükséged, oszd fel a dokumentumot szakaszokra, exportáld minden szakaszt különböző opciókkal, majd egyesítsd a PDF‑eket a `PdfMerger` használatával.

### 3. “Ez befolyásolja a betűkészlet beágyazását?”

Nem. A betűkészlet beágyazását a `pdfOptions.setEmbedFullFonts(true)` (alapértelmezett) szabályozza. Nyugodtan engedélyezheted vagy letilthatod anélkül, hogy az inline alakzat jelzőt módosítanád.

### 4. “Hogyan ellenőrizhetem, hogy az alakzatok valóban `<span>`‑ek?”

Nyisd meg a keletkezett PDF‑et egy olyan eszközzel, mint a **PDF.js** vagy az **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Látni fogod, hogy az alakzat egy `<span>` elembe van csomagolva az alapszintű XML‑ben. Ha `<div>`-et látsz, az opció nem került alkalmazásra.

---

## A megközelítés kiterjesztése – Kapcsolódó opciók

Miközben itt vagy, érdemes lehet felfedezni a többi PDF konverziós beállítást is:

| Opció | Mit csinál | Tipikus felhasználási eset |
|--------|--------------|------------------|
| `setCompressImages(true)` | Csökkenti a képek méretét | Gyorsabb letöltések |
| `setUseHighQualityRendering(true)` | Javítja a vektor renderelést | Nyomtatásra kész PDF‑ek |
| `setExportDocumentStructure(true)` | Strukturális címkéket ad hozzá a hozzáférhetőséghez | WCAG megfelelés |
| `setSaveFormat(SaveFormat.PDF)` | Kifejezetten beállítja a formátumot (ritkán szükséges) | Többformátumú folyamatok |

Ezek a beállítások jól kombinálhatók a **convert word to pdf inline** szcenáriókkal, ahol a layout fidelity és a teljesítmény egyaránt fontos.

---

## A konverzió tesztelése

1. **Visual check** – Nyisd meg a PDF‑et két nézőben (Chrome és Adobe Reader), hogy ellenőrizd, az alakzatok egy vonalban vannak-e.  
2. **Automated diff** – Használj egy könyvtárat, például `pdfbox`‑t, hogy kinyerd az XML‑t és ellenőrizd a `<span>` címkék jelenlétét.  
3. **Performance benchmark** – Mérd a szükséges időt `setCompressImages` használatával és anélkül, hogy lásd a kompromisszumot.

Egy gyors JUnit példa:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

---

## Következtetés

Most már egy szilárd, vég‑végi megoldásod van a **export floating shapes inline** számára, amikor **convert Word to PDF inline**-t végzel. A `PdfSaveOptions` konfigurálásával szabályozhatod, hogy melyik HTML címke legyen használva minden alakzatra, így a PDF‑ek rendezettek és kereshetők maradnak. Ne felejtsd el tesztelni a kimenetet, beállítani a kapcsolódó opciókat, például a képtömörítést, és kezelni a szélhelyzeteket, mint a komplex SmartArt.

Készen állsz a következő lépésre? Próbáld ki ugyanazt a technikát a **export floating tables inline** esetén, vagy kísérletezz CSS‑stílusú PDF‑ekkel az Aspose `HtmlSaveOptions`‑ával. Ugyanaz a minta – betöltés, konfigurálás, mentés – szinte minden dokumentum‑PDF konverziós helyzetre érvényes.

További kérdéseid vannak a **how to set pdf options**‑ról, vagy segítségre van szükséged a **save word as pdf options** egy másik könyvtárhoz? Hagyj egy megjegyzést, és jó kódolást!

## Mit érdemes még megtanulni?

A következő útmutatók szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás tartalmaz teljesen működő kódpéldákat lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Word PDF‑re konvertálása Aspose.Words for Java segítségével](/words/english/java/document-converting/)
- [Dokumentum PDF‑ként mentése Aspose.Words for Java‑val](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Word dokumentum struktúrájának exportálása PDF dokumentumba](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}