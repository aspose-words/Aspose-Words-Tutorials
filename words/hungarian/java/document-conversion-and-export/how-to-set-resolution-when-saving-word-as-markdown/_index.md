---
category: general
date: 2026-05-04
description: Hogyan állítsuk be a felbontást a Wordből Markdown exportálásához. Ismerje
  meg a markdown képfelbontást, az egyenletek exportálásának módját, és a Word dokumentum
  markdown formátumba mentését Java-ban.
draft: false
keywords:
- how to set resolution
- markdown image resolution
- how to use markdown
- how to export equations
- save word as markdown
language: hu
og_description: Hogyan állítsuk be a felbontást a Wordből történő Markdown exportáláshoz.
  Ez az útmutató bemutatja a Markdown képfelbontását, az egyenletek exportálását és
  a Word mentését Markdown formátumban.
og_title: Hogyan állítsuk be a felbontást a Word Markdown formátumba mentésekor
tags:
- Aspose.Words
- Java
- Markdown
- Document Export
title: Hogyan állítsuk be a felbontást a Word Markdown formátumba mentésekor
url: /hu/java/document-conversion-and-export/how-to-set-resolution-when-saving-word-as-markdown/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan állítsuk be a felbontást a Word markdownként mentésekor

Gondolkodtál már azon, **hogyan állítsuk be a felbontást** a Word dokumentumból generált Markdown fájlban megjelenő képekhez? Nem vagy egyedül. Sok fejlesztő akad el, amikor az alapértelmezett rasterizált matematikai képek homályosak, különösen a nagy DPI‑s képernyőkön.  

Ebben a tutorialban lépésről‑lépésre bemutatjuk, hogyan szabályozhatod a *markdown image resolution*-t, miközben megmutatjuk, **hogyan exportáljuk az egyenleteket** LaTeX‑ként, és végül **hogyan mentjük a Word dokumentumot markdownként** az Aspose.Words for Java segítségével. A végére egy tiszta, termelés‑kész Markdown fájlt kapsz, amely tisztán rendereli az egyenleteket és a képeket a szükséges minőségben.

## Prerequisites

- Java 17 (vagy bármely friss JDK)  
- Aspose.Words for Java 23.6 vagy újabb – letöltheted a Maven Central‑ról  
- Egy Word dokumentum (`.docx`), amely OfficeMath objektumokat (egyenleteket) és esetleg raszteres képeket tartalmaz  
- Alapvető ismeretek Maven/Gradle‑ról és egy IDE‑ről (IntelliJ IDEA, Eclipse, VS Code, stb.)

Nem szükséges további könyvtár; minden mást az Aspose.Words kezel.

---

## How to Set Resolution for Markdown Export

> **Pro tip:** A választott felbontás közvetlenül befolyásolja a generált képek fájlméretét. A **300 dpi** érték jó egyensúlyt nyújt a legtöbb web‑alapú Markdown nézőhöz.

```java
// Step 1: Load the source Word document containing equations
Document doc = new Document("YOUR_DIRECTORY/Math.docx");

// Step 2: Create Markdown save options to control the export behavior
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions();

// Step 3: Export OfficeMath objects as LaTeX expressions
saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

// Step 4 (optional): Set image resolution for any rasterized Math images
saveOptions.setImageResolution(300);   // <-- this is where we set the resolution

// Step 5: Save the document as a Markdown file using the configured options
doc.save("YOUR_DIRECTORY/MathExport.md", saveOptions);
```

A `setImageResolution(int dpi)` hívás a **hogyan állítsuk be a felbontást** lényege. Ezzel az Aspose.Words‑nek azt mondjuk, hogy a fallback képeket (pl. amikor egy egyenletet nem lehet tisztán LaTeX‑ben ábrázolni) a megadott pont‑per‑hüvelyk értékkel rasterizálja. Ha ezt a sort kihagyod, a könyvtár az alapértelmezett 220 dpi‑t használja, ami retina kijelzőkön elmosódottnak tűnhet.

### Why Use LaTeX for Equations?

Amikor az egyenleteket LaTeX‑ként (`OfficeMathExportMode.LATEX`) exportálod, a keletkező Markdown nyers LaTeX kódot tartalmaz `$…$` vagy `$$…$$` jelek között. A legtöbb modern Markdown renderelő (GitHub, GitLab, MkDocs MathJax‑szal) ezeket tiszta, skálázható vektorgrafikaként jeleníti meg – nincs felbontási probléma. A felbontási beállítás csak **markdown image resolution**‑t érint, ha raster fallback képekről van szó, például beágyazott diagramokról vagy olyan képekről, amelyeket a Markdown natívan nem támogat.

---

## How to Use Markdown Image Resolution Effectively

Ha a Word fájlodba rendszeres képeket (pl. képernyőképeket) ágyazol be, azokat az Aspose.Words PNG‑ként konvertálja. Ugyanez a `setImageResolution` metódus érvényes, biztosítva, hogy a PNG‑k a megadott DPI‑t örököljék. Egy gyors ellenőrzőlista:

1. **Válassz DPI‑t, amely megfelel a célplatformnak** – 72 dpi régi webhez, 150 dpi szabványos kijelzőkhöz, 300 dpi nyomtatási minőségű PDF‑ekhez.  
2. **Teszteld a kimenetet** – nyisd meg a generált `.md` fájlt a kedvenc néződben, és nagyíts rá, hogy ellenőrizd a élességet.  
3. **Vedd figyelembe a fájlméretet** – magasabb DPI nagyobb PNG‑ket eredményez; ha a sávszélesség kritikus, kísérletezz 200 dpi‑vel, és hasonlítsd össze.

---

## How to Export Equations as LaTeX

A `saveOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);` sor azt mondja az Aspose.Words‑nek, hogy minden OfficeMath objektumot LaTeX‑be fordítson. Ez a javasolt megközelítés, mert:

- **Skálázhatóság** – A LaTeX bármilyen méretben megjelenik minőségromlás nélkül.  
- **Szerkeszthetőség** – Később közvetlenül a Markdown fájlban módosíthatod a LaTeX‑et.  
- **Kompatibilitás** – A legtöbb statikus weboldalkészítő és dokumentációs eszköz már támogatja a LaTeX renderelést.

Ha valaha is a régi képalapú fallback‑re van szükséged, egyszerűen válts `OfficeMathExportMode.IMAGE`‑re. Ebben az esetben a beállított felbontás még fontosabbá válik.

---

## Save Word as Markdown – Full End‑to‑End Example

Az alábbiakban egy teljes, futtatható Maven projekt részletet láthatsz, amely bemutatja a teljes folyamatot a függőségdeklarációtól a végrehajtásig.

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" ...>
    <modelVersion>4.0.0</modelVersion>
    <groupId>com.example</groupId>
    <artifactId>markdown-export</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>
    <dependencies>
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>23.6</version>
        </dependency>
    </dependencies>
</project>
```

```java
// src/main/java/com/example/MarkdownMathExport.java
package com.example;

import com.aspose.words.*;

public class MarkdownMathExport {
    public static void main(String[] args) throws Exception {
        // Load the source Word document containing equations and images
        Document doc = new Document("src/main/resources/Math.docx");

        // Configure Markdown export options
        MarkdownSaveOptions options = new MarkdownSaveOptions();
        options.setOfficeMathExportMode(OfficeMathExportMode.LATEX); // export equations as LaTeX
        options.setImageResolution(300); // set resolution for rasterized images

        // Save as Markdown
        doc.save("output/MathExport.md", options);

        System.out.println("✅ Markdown export complete! Check output/MathExport.md");
    }
}
```

**Várható eredmény:** A `MathExport.md` tartalmazni fog LaTeX blokkokat minden egyenlethez, és minden beágyazott kép PNG hivatkozásként jelenik meg, amelynek DPI‑ja 300. Nyisd meg a fájlt egy MathJax‑ot támogató Markdown nézőben (pl. VS Code a Markdown Preview Enhanced kiegészítővel), és tökéletesen éles egyenleteket és képeket látsz majd.

---

## Common Questions & Edge Cases

### What if I need a different DPI for only one image?

Az Aspose.Words a DPI‑t globálisan alkalmazza a `setImageResolution`‑nal. Egyedi képre vonatkozó DPI kezeléséhez a generált Markdown‑ot kell utólag feldolgozni: cseréld le a PNG fájlt egy magasabb felbontású változatra, és módosítsd a kép hivatkozását manuálisan. Nem ideális, de néhány speciális esetben megoldható.

### Does this work on Linux/macOS?

Természetesen. A könyvtár tisztán Java, így ugyanaz a kód bárhol fut, ahol a JDK elérhető. Ügyelj csak arra, hogy a fájlutakat perjel (`/`) vagy a `Paths.get(...)`‑t használjad a platform‑független kezeléshez.

### What about SVG output?

Ha vektoros képeket (diagramok) szeretnél, beállíthatod a `saveOptions.setExportImagesAsSvg(true);` opciót. Az SVG‑k figyelmen kívül hagyják a DPI‑t, így a **markdown image resolution** kérdés megszűnik. Azonban nem minden Markdown renderelő kezeli kifogástalanul az SVG‑t, ezért előbb teszteld a célplatformon.

### Can I embed the generated Markdown into a static site generator?

Igen. A kimenet egy egyszerű `.md` fájl szabványos Markdown szintaxissal és LaTeX delimitekkel. A legtöbb generátor (Jekyll, Hugo, MkDocs) gond nélkül elfogadja. Csak ne felejtsd engedélyezni a MathJax‑ot vagy KaTeX‑et a webhely konfigurációjában.

---

## Conclusion

Áttekintettük, **hogyan állítsuk be a felbontást** a képekhez, amikor **Word‑ot mentünk markdownként**, megvizsgáltuk a **markdown image resolution** finomságait, bemutattuk, **hogyan exportáljuk az egyenleteket** LaTeX‑ként, és bemutattuk a teljes Java implementációt. A `setImageResolution` és a megfelelő `OfficeMathExportMode` beállításával pontosan szabályozhatod a vizuális hűséget és a fájlméretet.

Készen állsz a következő lépésre? Próbáld ki ezt a megközelítést az Aspose.PDF‑vel, hogy ugyanazt a Word forrást közvetlenül PDF‑be konvertáld, vagy kísérletezz a `setExportImagesAsSvg(true)` opcióval vektor‑alapú grafikákhoz. Az itt tanult technikák bármely automatizált dokumentációs csővezeték építőkövei.

Ha hasznosnak találtad a leírást, csillagozd a GitHub‑on, oszd meg a csapattagokkal, vagy hagyj egy megjegyzést alább a saját tippeiddel. Boldog kódolást!  

![Felbontás beállításának példája](resolution.png "Felbontás beállítása Word markdownként mentésekor")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}