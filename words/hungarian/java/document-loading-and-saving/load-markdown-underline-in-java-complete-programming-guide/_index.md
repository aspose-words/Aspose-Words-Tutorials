---
category: general
date: 2026-08-04
description: Töltsd be a markdown aláhúzást Java-ban, és őrizd meg a markdown formázást
  a markdown dokumentumba betöltés közben. Kövesd ezt a lépésről‑lépésre útmutatót.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- load markdown underline
- load markdown into document
- preserve markdown formatting
language: hu
lastmod: 2026-08-04
og_description: Töltsd be a markdown aláhúzást Java-ban, és őrizd meg a markdown formázást.
  Tanuld meg, hogyan töltsd be a markdownot a dokumentumba teljes aláhúzási támogatással.
og_image_alt: Diagram showing load markdown underline process
og_title: Markdown aláhúzás betöltése Java‑ban – lépésről‑lépésre útmutató
schemas:
- author: GroupDocs
  dateModified: '2026-08-04'
  description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  headline: Load markdown underline in Java – complete programming guide
  type: TechArticle
- description: Load markdown underline in Java and preserve markdown formatting while
    loading markdown into document. Follow this step‑by‑step tutorial.
  name: Load markdown underline in Java – complete programming guide
  steps:
  - name: Create `LoadOptions` for the document
    text: '`LoadOptions` lets you customize how the library parses the source file.
      Creating a fresh instance gives you a clean slate for later settings.'
  - name: Enable detection of underline formatting while loading
    text: By default the viewer may ignore underline tags because they are less common
      in Markdown. Enabling this flag tells the parser to keep underline spans intact.
  - name: Load the Markdown file using the configured options
    text: Now you can load the file. Pass the `loadOptions` object to the `Document`
      constructor so the parser respects the underline flag.
  - name: Verify that underline formatting is preserved
    text: A quick sanity check helps you confirm that **preserve markdown formatting**
      worked. The following snippet prints the text of each paragraph and marks underlined
      fragments with a tilde (`~`) for visibility.
  type: HowTo
tags:
- markdown
- Java
- document-processing
title: Markdown aláhúzás betöltése Java-ban – teljes programozási útmutató
url: /hu/java/document-loading-and-saving/load-markdown-underline-in-java-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Markdown aláhúzás betöltése Java-ban – teljes programozási útmutató

Ha **load markdown underline**-t kell betöltenie egy Markdown fájl `Document` objektummá konvertálása során, ez az útmutató pontosan megmutatja, hogyan kell ezt megtenni. Megtanulja, hogyan **load markdown into document**-et végezhet aláhúzási stílus elvesztése nélkül, biztosítva, hogy az eredeti Markdown formázás teljesen megmaradjon.

Az útmutató mindent lefed, amit tudnia kell: a szükséges könyvtárakat, minden konfigurációs lépést, és azt, hogyan ellenőrizheti, hogy az aláhúzási formázás túlélte-e az importálást. A végére egy újrahasználható kódrészletet kap, amelyet bármely Java projektbe beilleszthet.

## Előfeltételek

- Java 17 vagy újabb telepítve (a példa a modern modulrendszert használja)
- A **GroupDocs.Viewer** legújabb verziója (vagy egy kompatibilis könyvtár, amely biztosítja a `LoadOptions` és `Document` osztályokat)
- Egy Markdown fájl (`sample.md`), amely aláhúzott szöveget tartalmaz, például `<u>underlined</u>` vagy a GitHub‑stílusú szintaxis `__underlined__`
- Egy IDE, például IntelliJ IDEA vagy VS Code, bár bármely szövegszerkesztő is működik

Ezek a követelmények garantálják, hogy a kód további konfiguráció nélkül fut.

## Markdown aláhúzás betöltése – lépésről‑lépésre útmutató

A folyamat három fő lépésből áll: `LoadOptions` példány létrehozása, aláhúzás felismerésének engedélyezése, és végül a Markdown fájl betöltése ezekkel a beállításokkal. Minden lépést alább részletezünk.

### 1. lépés: `LoadOptions` létrehozása a dokumentumhoz

`LoadOptions` lehetővé teszi, hogy testreszabja, hogyan dolgozza fel a könyvtár a forrásfájlt. Egy új példány létrehozása tiszta alapot biztosít a későbbi beállításokhoz.

```java
import com.groupdocs.viewer.options.LoadOptions;

// Step 1: Create load options for the document
LoadOptions loadOptions = new LoadOptions();
```

A `LoadOptions` objektum az importtal kapcsolatos összes finomhangolás kiindulópontja. A következő lépésben használni fogja az aláhúzás felismerésének bekapcsolásához.

### 2. lépés: Aláhúzási formázás felismerésének engedélyezése betöltés közben

Alapértelmezés szerint a viewer figyelmen kívül hagyhatja az aláhúzási címkéket, mivel ezek a Markdownban kevésbé gyakoriak. Ennek a jelzőnek az engedélyezése azt mondja a parsernek, hogy tartsa meg az aláhúzott szakaszokat.

```java
// Step 2: Enable detection of underline formatting while loading
loadOptions.setImportUnderlineFormatting(true);
```

`setImportUnderlineFormatting(true)` beállítása biztosítja, hogy bármely `<u>` HTML címke vagy a GitHub‑stílusú aláhúzási szintaxis a `Document` modellben aláhúzott stílusként legyen lefordítva. Ez a kulcsfontosságú művelet, amely a **load markdown underline**-t a várt módon működteti.

### 3. lépés: A Markdown fájl betöltése a konfigurált beállításokkal

Most betöltheti a fájlt. Adja át a `loadOptions` objektumot a `Document` konstruktorának, hogy a parser figyelembe vegye az aláhúzás jelzőt.

```java
import com.groupdocs.viewer.Document;

// Step 3: Load the Markdown file using the configured options
Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);
```

Amikor a konstruktor befejeződik, a `markdownDoc` egy teljes memóriában lévő reprezentációt tartalmaz a Markdown forrásról, aláhúzott részekkel együtt.

### 4. lépés: Ellenőrizze, hogy az aláhúzási formázás megmaradt-e

Egy gyors ellenőrzés segít megerősíteni, hogy a **preserve markdown formatting** működött. Az alábbi kódrészlet kiírja minden bekezdés szövegét, és aláhúzott részeket hullámmal (`~`) jelöli a láthatóság érdekében.

```java
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;

for (Page page : markdownDoc.getPages()) {
    for (Paragraph paragraph : page.getParagraphs()) {
        StringBuilder line = new StringBuilder();
        for (TextFragment fragment : paragraph.getTextFragments()) {
            if (fragment.isUnderline()) {
                line.append("~").append(fragment.getText()).append("~");
            } else {
                line.append(fragment.getText());
            }
        }
        System.out.println(line.toString());
    }
}
```

**Várható kimenet** (feltételezve, hogy a `sample.md` tartalmazza a `This is __underlined__ text` szöveget):

```
This is ~underlined~ text
```

A hullámok azt jelzik, hogy az aláhúzási stílus túlélte az importálást, megerősítve, hogy a **load markdown into document** művelet megőrizte az eredeti formázást.

## Gyakori buktatók és hogyan kerülhetők el

| Tünet | Ok | Megoldás |
|---|---|---|
| Az aláhúzás eltűnik a betöltés után | `setImportUnderlineFormatting` alapértelmezett `false` értéken maradt | Győződjön meg róla, hogy a `Document` létrehozása előtt meghívja a `loadOptions.setImportUnderlineFormatting(true)`-t. |
| Csak a szöveg egy része van aláhúzva | Vegyes Markdown szintaxis (pl. HTML `<u>` keverve a `__underline__`-val) | A könyvtár mindkettőt támogatja; ellenőrizze, hogy a forrásfájl egységes aláhúzási jelölőt használ-e. |
| A dokumentum betöltése sikertelen | Helytelen fájlútvonal vagy hiányzó könyvtári függőségek | Használjon abszolút útvonalat vagy helyezze a `sample.md`-t a munkakönyvtárhoz relatívan; vegye fel a viewer JAR-okat a classpath-re. |

**Pro tipp:** Ha emellett a félkövér vagy dőlt stílusokat is meg szeretné tartani, engedélyezze őket a `setImportBoldFormatting(true)` és `setImportItalicFormatting(true)` segítségével. Ezen jelzők kombinálása teljes mértékben hiteles importot biztosít a leggyakoribb Markdown stílusokhoz.

## Teljes futtatható példa

Az alábbi önálló Java program mindent összevon. Másolja a kódot egy `LoadMarkdownUnderlineDemo.java` nevű fájlba, állítsa be a fájlútvonalat, és futtassa a `java LoadMarkdownUnderlineDemo` paranccsal.

```java
import com.groupdocs.viewer.Document;
import com.groupdocs.viewer.contents.Page;
import com.groupdocs.viewer.contents.Paragraph;
import com.groupdocs.viewer.contents.TextFragment;
import com.groupdocs.viewer.options.LoadOptions;

public class LoadMarkdownUnderlineDemo {

    public static void main(String[] args) {
        // 1️⃣ Create load options
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Enable underline detection
        loadOptions.setImportUnderlineFormatting(true);

        // 3️⃣ Load the Markdown file
        Document markdownDoc = new Document("YOUR_DIRECTORY/sample.md", loadOptions);

        // 4️⃣ Print each paragraph, marking underlined text with ~
        for (Page page : markdownDoc.getPages()) {
            for (Paragraph paragraph : page.getParagraphs()) {
                StringBuilder line = new StringBuilder();
                for (TextFragment fragment : paragraph.getTextFragments()) {
                    if (fragment.isUnderline()) {
                        line.append("~").append(fragment.getText()).append("~");
                    } else {
                        line.append(fragment.getText());
                    }
                }
                System.out.println(line.toString());
            }
        }
    }
}
```

A program futtatása kiírja a dokumentum tartalmát aláhúzott jelölőkkel, bizonyítva, hogy a **load markdown underline** funkció működik, és hogy a **preserve markdown formatting** egész importfolyamat során megőrizhető.

## Összegzés

Most már tudja, hogyan **load markdown underline**-t végezzen Java-ban, hogyan **load markdown into document**-et hajtson végre az eredeti stílus megtartásával, és hogyan ellenőrizze, hogy az aláhúzási formázás érintetlen maradt. Ez a megközelítés a legújabb GroupDocs.Viewer kiadásokkal működik, és kiterjeszthető további Markdown funkciók támogatására, mint a félkövér, dőlt és táblázatok.

Ezután fedezze fel a kapcsolódó témákat, mint a **preserve markdown formatting for tables**, **render Markdown to PDF**, vagy **custom styling of imported Markdown elements**. Állítsa be a `LoadOptions` jelzőket, hogy megfeleljenek alkalmazása pontos formázási követelményeinek, és finomhangolt irányítást kap minden importlépés felett. Boldog kódolást!

## Mit érdemes legközelebb megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsen elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket saját projektjeiben.

- [Markdown betöltési beállítások elsajátítása az Aspose.Words for Java segítségével](/words/english/java/document-operations/master-markdown-load-options-aspose-words-java/)
- [Markdown betöltési beállítások elsajátítása Aspose Words Java](/words/german/java/document-operations/master-markdown-load-options-aspose-words-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}