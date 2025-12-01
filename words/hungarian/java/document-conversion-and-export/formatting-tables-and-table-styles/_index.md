---
date: 2025-11-28
description: Ismerje meg, hogyan változtathatja meg a cellák szegélyeit és formázhatja
  a táblázatokat az Aspose.Words for Java segítségével. Ez a lépésről‑lépésre útmutató
  lefedi a szegélyek beállítását, az első oszlop stílusának alkalmazását, a táblázat
  tartalmának automatikus méretezését, valamint a táblázat stílusainak alkalmazását.
language: hu
linktitle: How to Change Cell Borders in Tables – Aspose.Words for Java
second_title: Aspose.Words Java Document Processing API
title: Hogyan változtassuk meg a cellaszegélyeket táblázatokban – Aspose.Words for
  Java
url: /java/document-conversion-and-export/formatting-tables-and-table-styles/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan változtassuk meg a cellaszegélyeket táblázatokban – Aspose.Words for Java

## Bevezetés

A dokumentumformázásnál a táblázatok kulcsfontosságú szerepet játszanak, és **tudni, hogyan változtassuk meg a cellaszegélyeket** elengedhetetlen a tiszta, professzionális elrendezések létrehozásához. Ha Java-val és Aspose.Words-szel fejlesztesz, már egy erőteljes eszközkészlet áll a rendelkezésedre. Ebben az útmutatóban végigvezetünk a táblázatok formázásának teljes folyamatán, a cellaszegélyek módosításán, az *első oszlop stílus* alkalmazásán és az *auto‑fit táblázattartalom* használatán, hogy dokumentumaid kifinomultak legyenek.

## Gyors válaszok
- **Mi a fő osztály a táblázatok építéséhez?** A `DocumentBuilder` programozottan hoz létre táblázatokat és cellákat.  
- **Hogyan változtassam meg egyetlen cella szegélyvastagságát?** Használd a `builder.getCellFormat().getBorders().getLeft().setLineWidth(value)` metódust.  
- **Alkalmazhatok előre definiált táblázatstílust?** Igen – hívd a `table.setStyleIdentifier(StyleIdentifier.YOUR_STYLE)` metódust.  
- **Melyik metódus auto‑fit-eli a táblázatot a tartalmához?** `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)`.  
- **Szükség van licencre a termeléshez?** Érvényes Aspose.Words licenc szükséges a nem‑próba használathoz.

## Mi az a „cellaszegélyek módosítása” az Aspose.Words-ben?

A cellaszegélyek módosítása azt jelenti, hogy testre szabod a cellákat elválasztó vizuális vonalakat – szín, szélesség és vonalstílus. Az Aspose.Words gazdag API-t biztosít, amely lehetővé teszi ezen tulajdonságok beállítását a táblázat, sor vagy egyedi cella szintjén, így finomhangolt kontrollt kapsz a dokumentumaid megjelenése felett.

## Miért használjuk az Aspose.Words for Java táblázatstílusait?

- **Konzisztens megjelenés platformok között** – ugyanaz a stíluskód működik Windows, Linux és macOS rendszereken.  
- **Nincs függőség a Microsoft Wordtől** – szerver‑oldalon generálhatsz vagy módosíthatsz dokumentumokat.  
- **Gazdag stíluskönyvtár** – beépített táblázatstílusok (pl. *első oszlop stílus*) és teljes auto‑fit képességek.  

## Előkövetelmények

1. **Java Development Kit (JDK) 8+** – győződj meg róla, hogy a `java` elérhető a PATH‑on.  
2. **IDE** – IntelliJ IDEA, Eclipse vagy bármely kedvenc szerkesztőd.  
3. **Aspose.Words for Java** – töltsd le a legújabb JAR‑t a [hivatalos oldalról](https://releases.aspose.com/words/java/).  
4. **Alapvető Java ismeretek** – képesnek kell lenned Maven/Gradle projekt létrehozására és külső JAR‑ok hozzáadására.

## Csomagok importálása

A táblázatokkal való munka megkezdéséhez szükséged van az alapvető Aspose.Words osztályokra:

```java
import com.aspose.words.*;
```

Ez az egyetlen import hozzáférést biztosít a `Document`, `DocumentBuilder`, `Table`, `StyleIdentifier` és számos egyéb segédeszközhöz.

## Hogyan változtassuk meg a cellaszegélyeket

Az alábbiakban egy egyszerű táblázatot hozunk létre, módosítjuk a teljes szegélyeit, majd egyedi cellákat szabunk testre.

### 1. lépés: Új dokumentum betöltése

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### 2. lépés: Táblázat létrehozása és globális szegélyek beállítása

```java
Table table = builder.startTable();
builder.insertCell();

// Set the borders for the entire table.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Set the cell shading for this cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Specify a different cell shading for the second cell.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### 3. lépés: Egyetlen cella szegélyeinek módosítása

```java
// Clear the cell formatting from previous operations.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Create larger borders for the first cell of this row.
builder.getCellFormat().getBorders().getLeft().setLineWidth(4.0);
builder.getCellFormat().getBorders().getRight().setLineWidth(4.0);
builder.getCellFormat().getBorders().getTop().setLineWidth(4.0);
builder.getCellFormat().getBorders().getBottom().setLineWidth(4.0);
builder.writeln("Cell #3");

builder.insertCell();
builder.getCellFormat().clearFormatting();
builder.writeln("Cell #4");
        
doc.save("FormatTableAndCellWithDifferentBorders.docx");
```

#### Mit csinál a kód
- **Globális szegélyek** – a `table.setBorders` 2‑pontos fekete vonallal látja el az egész táblázatot.  
- **Cellaszín** – bemutatja, hogyan színezzük ki az egyes cellákat (piros és zöld).  
- **Egyedi cellaszegélyek** – a harmadik cella 4‑pontos szegélyt kap minden oldalon, így kiemelkedik.

## Táblázatstílusok alkalmazása (beleértve az Első oszlop stílust)

A táblázatstílusok lehetővé teszik egy konzisztens megjelenés alkalmazását egyetlen hívással. Megmutatjuk, hogyan engedélyezzük az *első oszlop stílust* és hogyan auto‑fit-eljük a táblázatot a tartalmához.

### 4. lépés: Új dokumentum létrehozása a stílushoz

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// We must insert at least one row first before setting any table formatting.
builder.insertCell();
```

### 5. lépés: Előre definiált stílus alkalmazása és az Első oszlop formázás engedélyezése

```java
// Set the table style based on a unique style identifier.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Apply which features should be formatted by the style.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);

// Auto‑fit the table so columns shrink or expand to fit the content.
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### 6. lépés: A táblázat feltöltése adatokkal

```java
builder.writeln("Item");
builder.getCellFormat().setRightPadding(40.0);
builder.insertCell();
builder.writeln("Quantity (kg)");
builder.endRow();

builder.insertCell();
builder.writeln("Apples");
builder.insertCell();
builder.writeln("20");
builder.endRow();

builder.insertCell();
builder.writeln("Bananas");
builder.insertCell();
builder.writeln("40");
builder.endRow();

builder.insertCell();
builder.writeln("Carrots");
builder.insertCell();
builder.writeln("50");
builder.endRow();

doc.save("BuildTableWithStyle.docx");
```

#### Miért fontos ez
- **Stílusazonosító** – a `MEDIUM_SHADING_1_ACCENT_1` tiszta, árnyékolt megjelenést ad a táblázatnak.  
- **Első oszlop stílus** – az első oszlop kiemelése javítja az olvashatóságot, különösen jelentésekben.  
- **Sorcsíkok** – váltakozó sor színek könnyebbé teszik a nagy táblázatok áttekintését.  
- **Auto‑fit** – biztosítja, hogy a táblázat szélessége a tartalomhoz igazodjon, elkerülve a szöveg levágását.

## Gyakori problémák és hibaelhárítás

| Probléma | Tipikus ok | Gyors megoldás |
|----------|------------|----------------|
| A szegélyek nem jelennek meg | `clearFormatting()` használata a szegélyek beállítása után | Állítsd be a szegélyeket **a** formázás törlése **után**, vagy alkalmazd újra őket. |
| A színezés figyelmen kívül marad egyesített cellákon | Színezés alkalmazása a cellák egyesítése előtt | Alkalmazd a színezést **a** cellák egyesítése **után**. |
| A táblázat szélessége meghaladja az oldal margóit | Nincs auto‑fit alkalmazva | Hívd a `table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS)` metódust, vagy állíts be fix szélességet. |
| A stílus nem kerül alkalmazásra | Hibás `StyleIdentifier` érték | Ellenőrizd, hogy az azonosító létezik‑e az általad használt Aspose.Words verzióban. |

## Gyakran feltett kérdések

**K: Használhatok egyedi táblázatstílusokat, amelyek nincsenek az alapértelmezett opciók között?**  
V: Igen, programozottan létrehozhatsz és alkalmazhatsz egyedi stílusokat. Tekintsd meg a [Aspose.Words dokumentációt](https://reference.aspose.com/words/java/) a részletekért.

**K: Hogyan alkalmazhatok feltételes formázást a cellákra?**  
V: Használd a szokásos Java logikát a cellaértékek ellenőrzéséhez, majd hívd meg a megfelelő formázó metódusokat (pl. háttérszín módosítása, ha az érték meghalad egy küszöböt).

**K: Lehet-e ugyanúgy formázni az egyesített cellákat, mint a normál cellákat?**  
V: Természetesen. Az egyesítés után ugyanazokat a `CellFormat` API‑kat használhatod a színezéshez vagy szegélyekhez.

**K: Mit tehetek, ha a táblázatnak dinamikusan kell méreteződnie a felhasználói bemenet alapján?**  
V: Állítsd be az oszlopszélességeket, vagy hívd újra az `autoFit` metódust az új adatok beszúrása után, hogy újraszámolja a layoutot.

**K: Hol találok további példákat a táblázatstílusokra?**  
V: A hivatalos [Aspose.Words API dokumentáció](https://reference.aspose.com/words/java/) átfogó mintakészletet tartalmaz.

## Összegzés

Most már teljes eszköztárral rendelkezel a **cellaszegélyek módosításához**, az *első oszlop stílus* alkalmazásához és a **auto‑fit táblázattartalom** használatához az Aspose.Words for Java segítségével. Ezeknek a technikáknak a elsajátításával olyan dokumentumokat hozhatsz létre, amelyek egyszerre adatgazdagok és vizuálisan vonzóak – tökéletesek jelentésekhez, számlákhoz és bármely üzleti kritikus kimenethez.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Utoljára frissítve:** 2025-11-28  
**Tesztelve a következővel:** Aspose.Words for Java 24.12 (a cikk írásakor legújabb)  
**Szerző:** Aspose