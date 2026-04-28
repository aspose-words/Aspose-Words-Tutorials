---
category: general
date: 2026-04-28
description: PDF/UA dokumentum létrehozása az Aspose.Words for Java segítségével.
  Tanulja meg, hogyan töltsön be docx-et helyreállítással, exportálja a képleteket
  LaTeX-be, mentse a markdownot a Wordből, és szerezze meg a hiányzó betűtípusokat.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: hu
og_description: PDF UA dokumentum létrehozása az Aspose.Words for Java segítségével.
  Lépésről lépésre útmutató a helyreállítási betöltés, LaTeX export, Markdown mentés
  és a hiányzó betűtípusok lekérése témakörében.
og_title: PDF UA dokumentum létrehozása – Teljes Java útmutató
tags:
- Aspose.Words
- Java
- PDF/UA
title: PDF UA dokumentum létrehozása az Aspose.Words segítségével – Teljes Java útmutató
url: /hu/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# PDF/UA dokumentum létrehozása – Teljes Java útmutató

Szükséged van **PDF UA dokumentum** létrehozására egy Word fájlból, miközben a sérült tartalmat is kezeli? Ebben az útmutatóban végigvezetünk a DOCX helyreállítással történő betöltésen, az egyenletek LaTeX‑be exportálásán, a Wordből Markdown mentésén, és a hiányzó betűtípusok lekérdezésén – mindezt az Aspose.Words for Java segítségével.  

Ha már valaha is egy sérült .docx‑et néztél, és azon tűnődtél, miért nem hozzáférhető a PDF‑ed, jó helyen vagy. A végére egy teljesen megfelelõ PDF/UA 1 fájlt, egy LaTeX egyenleteket tartalmazó Markdown változatot, valamint egy világos listát kapsz a betöltés során történt betűtípus‑helyettesítésekről.

## Szükséges eszközök

- **Aspose.Words for Java** (2026‑ig legújabb verzió) – add a Maven/Gradle függőséget vagy a JAR‑t a classpath‑hoz.  
- Java 17 vagy újabb (az API stream‑eket használ, ezért egy friss JDK ajánlott).  
- Egy minta `input.docx`, amely sérült szakaszokat, Office Math egyenleteket és lebegő alakzatokat tartalmazhat.

Nincs szükség extra könyvtárakra; minden az Aspose.Words‑ben található.

---

## 1. lépés – DOCX betöltése helyreállítási móddal  

Amikor egy dokumentum részben sérült, az alapértelmezett betöltő kivételt dob. A helyreállítási mód engedélyezésével azt mondod az Aspose.Words‑nek, hogy folytassa, és helyette figyelmeztetéseket jelenítsen meg.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Miért fontos:* A helyreállítási mód megakadályozza, hogy egyetlen hibás bekezdés miatt az egész folyamat megszakadjon. Emellett feltölti a `doc.getWarnings()`‑t, így később **lekérdezheted a hiányzó betűtípusokat** és egyéb problémákat.

## 2. lépés – Egyenletek exportálása LaTeX‑be egy Markdown fájlban  

A legtöbb fejlesztő szereti a Markdown‑ot a dokumentációhoz, de a Word beépített egyenletei másolása nehézkes. Az Aspose.Words közvetlenül LaTeX‑be tudja őket fordítani.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Pro tipp:* A visszahívás biztosítja, hogy minden kinyert kép az `imgs/` könyvtárba kerüljön. Ez tükrözi a GitHub Markdown renderelését – tiszta és hordozható.

## 3. lépés – PDF / UA dokumentum létrehozása megfelelő címkézéssel  

A PDF/UA (Universal Accessibility) megfelelőség sok közszféra projekt számára kötelező. A következő beállítások biztosítják, hogy az Aspose.Words helyesen címkézze a lebegő alakzatokat, és beállítsa a PDF/UA megfelelőségi jelzőt.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Mit fogsz látni:* Az `output.pdf` Adobe Acrobat Pro‑ban való megnyitásakor a dokumentum tulajdonságoknál a “PDF/UA‑1 compliant” felirat jelenik meg. Minden lebegő alakzat (szövegdoboz, kép) megfelelő címkékkel rendelkezik a képernyőolvasók számára.

## 4. lépés – Alakzat árnyékának finomhangolása (opcionális stílus)

Bár a hozzáférhetőséghez nem szükséges, a vizuális elemek finomhangolása hasznos lehet belső jelentésekhez.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*Miért érdemes?* Ha a PDF marketing anyag is, egy finom árnyék elegánsabbá teszi a megjelenést anélkül, hogy a megfelelőséget sértené.

## 5. lépés – Hiányzó betűtípusok és egyéb figyelmeztetések lekérdezése  

A helyreállítási betöltés során az Aspose.Words minden betűtípus‑helyettesítést rögzít. A listázás segít eldönteni, hogy beágyazzuk-e a megfelelő betűtípust, vagy elfogadjuk a helyettesítőt.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Tipikus kimenet* (a konzolod valami ilyesmit fog mutatni):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Ha kritikus betűtípusok hiányoznak, fontold meg azok telepítését a szerveren vagy a beágyazást a `PdfSaveOptions.setEmbedFullFonts(true)`‑val.

## Teljes működő példa  

Az alábbiakban a teljes, azonnal futtatható Java osztály található. Illeszd be az IDE‑dbe, állítsd be az elérési útvonalakat, és nyomd meg a **Run**‑t.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Várható eredmények**

| Kimenet | Leírás |
|--------|-------------|
| `output.md` | Markdown fájl, ahol minden Office Math egyenlet LaTeX‑ként (`$…$`) jelenik meg. A képek az `imgs/` könyvtárban tárolódnak. |
| `output.pdf` | PDF/UA‑1 kompatibilis dokumentum; nyisd meg Acrobatban, hogy a Fájl → Tulajdonságok → Szabványok alatt lásd a “PDF/UA‑1” feliratot. |
| Console | A hiányzó betűtípusok listája, például: “Missing: Calibri → substituted: Arial”. |

## Gyakran Ismételt Kérdések (GYIK)

**Q: Működik ez régebbi Aspose.Words verziókkal?**  
A: A `RecoveryMode`, `OfficeMathExportMode.LATEX` és `PdfCompliance.PDF_UA_1` enumok a 22.8‑as verzióban lettek bevezetve. Ha régebbi kiadást használsz, frissíts – a hozzáférhetőségi funkciók nem kerülnek visszaportolásra.

**Q: Mi a teendő, ha az eredeti betűtípusokat szeretném beágyazni a helyettesítés helyett?**  
A: Állítsd be a `pdfOptions.setEmbedFullFonts(true)`‑t, és győződj meg róla, hogy a betűtípus fájlok elérhetők a JVM betűtípus útvonalán.

**Q: Exportálhatok más jelölőnyelvekre (pl. HTML), miközben megtartom a LaTeX egyenleteket?**  
A: Igen. Használd a `HtmlSaveOptions`‑t, és állítsd be a `setOfficeMathExportMode(OfficeMathExportMode.LATEX)`‑t – ugyanaz az enum több formátumban is működik.

**Q: A DOCX‑em sok lebegő alakzatot tartalmaz; mindegyik címkézve lesz?**  
A: A `setExportFloatingShapesAsInlineTag(true)` használatával az Aspose.Words minden lebegő alakzatot egy `<Figure>` címkébe csomagol a PDF/UA‑hoz, ami a legtöbb képernyőolvasó ellenőrzést kielégíti.

## Összegzés  

Most bemutattuk, hogyan **hozzunk létre PDF UA dokumentumot** egy Word forrásból, miközben **docx‑et helyreállítással töltünk be**, **egyenleteket exportálunk LaTeX‑be**, **markdown‑ot mentünk a Word‑ből**, és **lekérdezzük a hiányzó betűtípusokat**. A kód teljesen önálló, bármely Java 17+ környezetben fut, és olyan eszközöket állít elő, amelyek készen állnak a hozzáférhetőségi auditokra és a fejlesztők számára

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}