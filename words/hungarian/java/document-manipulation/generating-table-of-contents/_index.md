---
date: 2026-01-03
description: Tanulja meg, hogyan állíthatja be az oldalszámokat a tartalomjegyzék
  beszúrása közben az Aspose.Words for Java használatával. Testreszabhatja a TOC‑stílusokat,
  és könnyedén hozhat létre dokumentumokat.
linktitle: Generating Table of Contents
second_title: Aspose.Words Java Document Processing API
title: Oldalszámok módosítása és tartalomjegyzék létrehozása az Aspose.Words for Java
  segítségével
url: /hu/java/document-manipulation/generating-table-of-contents/
weight: 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Oldalszámok beállítása és tartalomjegyzék létrehozása az Aspose.Words for Java-ban

Ebben az útmutatóban megtudja, hogyan **állíthatja be az oldalszámokat** és **szúrhat be egy tartalomjegyzéket** (TOC) az Aspose.Words for Java segítségével. Egy jól felépített TOC megkönnyíti a hosszú dokumentumok navigálását, és az oldalszámok finomhangolása professzionális élményt nyújt az olvasóknak. Lépésről lépésre végigvezetjük a dokumentum létrehozásán, a TOC stílusok testreszabásán és a tabulátorok beállításán, hogy az oldalszámok pontosan a kívánt helyen jelenjenek meg.

## Gyors válaszok
- **Mit jelent a „oldalszámok beállítása”?** A tabulátorok módosítása, amelyek a TOC‑ban az oldalszámok igazításáért felelnek.  
- **Beszúrhatok automatikusan tartalomjegyzéket?** Igen – használja a `FieldToc` osztályt.  
- **Szükségem van licencre a kód futtatásához?** A ingyenes próba verzió fejlesztéshez megfelelő; a termeléshez licenc szükséges.  
- **Melyik Aspose verzió támogatott?** A példák a legújabb Aspose.Words for Java kiadással működnek.  
- **Lehet testreszabni a TOC stílusait?** Természetesen – megváltoztathatja a betűtípusokat, a félkövérséget és egyebeket.

## Mi az a tartalomjegyzék az Aspose.Words-ben?
A TOC egy mező, amely átvizsgálja a dokumentumot a címsor stílusok (pl. Heading 1, Heading 2) alapján, és egy oldalszámokkal ellátott bejegyzéslistát generál. Az Aspose.Words lehetővé teszi ennek a mezőnek a programozott beszúrását és a megjelenés teljes szabályozását.

## Miért kell beállítani az oldalszámokat egy TOC-ban?
A tabulátorok beállítása pontos irányítást biztosít az oldalszámok megjelenési helye felett, ami elengedhetetlen:

- Tiszta, oszlop‑igazított elrendezés fenntartása.  
- A vállalati stílus útmutatók követése.  
- Olvashatóság javítása nyomtatott és digitális dokumentumokban.

## Előfeltételek
- Aspose.Words for Java hozzáadva a projekthez (Maven/Gradle).  
- Alapvető ismeretek a Java szintaxisról.

## Lépésről‑lépésre útmutató

### 1. lépés: Új dokumentum létrehozása
Először hozzon létre egy üres `Document` objektumot, amely a tartalmat és a TOC‑t fogja tárolni.

```java
Document doc = new Document();
```

### 2. lépés: TOC stílusok testreszabása
Módosíthatja az egyes TOC szintek megjelenését. Ebben a példában az első szintű bejegyzéseket félkövérre állítjuk, ami gyakori formázási igény.

```java
doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_1).getFont().setBold(true);
```

### 3. lépés: Tartalom hozzáadása a dokumentumhoz
Illessze be a címsorokat (pl. `Heading1`, `Heading2`) és a normál bekezdéseket. A TOC mező később automatikusan fel fogja ismerni ezeket a címsorokat. *(A kód a rövidség kedvéért kihagyva – a fókusz a TOC generálásán van.)*

### 4. lépés: TOC mező beszúrása
Helyezze el a TOC‑t a kívánt helyen – általában a dokumentum elején.

```java
// Insert a TOC field at the desired location in your document.
FieldToc fieldToc = new FieldToc();
doc.getFirstSection().getBody().getFirstParagraph().appendChild(fieldToc);
```

### 5. lépés: Dokumentum mentése
Mentse a dokumentumot a lemezre. Bármely támogatott formátumot választhat, például DOCX, PDF vagy HTML.

```java
doc.save("your_output_path_here");
```

## Tabulátorok testreszabása a TOC-ban (Oldalszámok beállítása)
Ha az alapértelmezett tabulátor nem igazítja az oldalszámokat a kívánt módon, végigiterálhat az összes TOC bekezdésen és módosíthatja a tabulátor pozíciókat.

```java
Document doc = new Document("Table of contents.docx");

for (Paragraph para : (Iterable<Paragraph>) doc.getChildNodes(NodeType.PARAGRAPH, true))
{
    if (para.getParagraphFormat().getStyle().getStyleIdentifier() >= StyleIdentifier.TOC_1 &&
        para.getParagraphFormat().getStyle().getStyleIdentifier() <= StyleIdentifier.TOC_9)
    {
        // Get the first tab used in this paragraph, which aligns the page numbers.
        TabStop tab = para.getParagraphFormat().getTabStops().get(0);
        
        // Remove the old tab.
        para.getParagraphFormat().getTabStops().removeByPosition(tab.getPosition());
        
        // Insert a new tab at a modified position (e.g., 50 units to the left).
        para.getParagraphFormat().getTabStops().add(tab.getPosition() - 50.0, tab.getAlignment(), tab.getLeader());
    }
}

doc.save("output.docx");
```

Most a TOC bejegyzések pontosan ott jelenítik meg az oldalszámokat, ahol szeretné, így a dokumentum kifinomult megjelenést kap.

## Gyakori problémák és tippek
- **Hiányzó címsorok a TOC-ban:** Győződjön meg róla, hogy a címsorok beépített stílusokat (`Heading1`, `Heading2`, stb.) használnak, vagy rendelje hozzá a saját stílusait a TOC szintekhez.  
- **A tabulátor nem alkalmazott:** Ellenőrizze, hogy a bekezdés valóban egy TOC stílushoz (`TOC_1`‑`TOC_9`) tartozik.  
- **Teljesítmény nagy dokumentumoknál:** Hívja meg a `doc.updateFields()` metódust a TOC beszúrása után, hogy egy lépésben frissítse a bejegyzéseket.

## Gyakran feltett kérdések

**K: Hogyan változtathatom meg a TOC bejegyzések formázását?**  
V: Használja a `doc.getStyles().getByStyleIdentifier(StyleIdentifier.TOC_X)` metódust, ahol *X* a szint (1‑9), és módosítsa a betűtípust, színt vagy bekezdés beállításait.

**K: Hogyan adhatok hozzá több szintet a TOC-hoz?**  
V: Módosítsa a `FieldToc` kapcsolót `\o "1-3"` (például) úgy, hogy további címsor szinteket is tartalmazzon, majd frissítse a megfelelő `TOC_X` stílusokat.

**K: Megváltoztathatom a tabulátor pozíciókat egyes TOC bejegyzésekhez?**  
V: Igen – iteráljon a bekezdéseken a „Tabulátorok testreszabása” szakaszban bemutatott módon, és módosítsa egyenként a tabulátorokat.

**K: Lehet-e TOC‑t generálni PDF kimenetben?**  
V: Természetesen. Mentse a dokumentumot PDF‑ként (`doc.save("output.pdf")`) a TOC generálása után; a mező automatikusan megjelenik.

**K: Kézzel kell meghívni az `updateFields()` metódust?**  
V: Amikor beszúr egy `FieldToc` mezőt, az Aspose.Words mentéskor frissíti, de a `doc.updateFields()` meghívása azonnali eredményt ad a hibakereséshez.

## Összegzés
Megtanulta, hogyan **állíthatja be az oldalszámokat**, **szúrhat be egy tartalomjegyzéket**, és **testreszabhatja a TOC stílusait** az Aspose.Words for Java segítségével. Ezek a technikák lehetővé teszik, hogy tiszta, könnyen navigálható és professzionálisan formázott dokumentumokat hozzon létre, amelyek megfelelnek bármely kiadási szabványnak.

---  

**Utoljára frissítve:** 2026-01-03  
**Tesztelve:** Aspose.Words for Java (legújabb kiadás)  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}