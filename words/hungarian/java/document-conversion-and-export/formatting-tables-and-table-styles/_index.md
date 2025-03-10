---
title: Táblázatok és táblázatstílusok formázása
linktitle: Táblázatok és táblázatstílusok formázása
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan formázhat táblázatokat és alkalmazhat stílusokat az Aspose.Words for Java használatával. Ez a lépésenkénti útmutató a szegélyek beállítását, a cellák árnyékolását és a táblázatstílusok alkalmazását ismerteti.
weight: 17
url: /hu/java/document-conversion-and-export/formatting-tables-and-table-styles/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Táblázatok és táblázatstílusok formázása


## Bevezetés

dokumentumok formázásakor a táblázatok döntő szerepet játszanak az adatok rendszerezésében és egyértelmű megjelenítésében. Ha Java-val és Aspose.Words-szel dolgozik, akkor hatékony eszközök állnak rendelkezésére a táblázatok létrehozásához és formázásához a dokumentumokban. Akár egyszerű táblázatot tervez, akár fejlett stílusokat alkalmaz, az Aspose.Words for Java számos olyan funkciót kínál, amelyek segítségével professzionális megjelenésű eredményeket érhet el.

Ebben az útmutatóban végigvezetjük a táblázatok formázásán és a táblázatstílusok alkalmazásán az Aspose.Words for Java használatával. Megtanulja, hogyan állíthat be táblázatszegélyeket, hogyan alkalmazhat cellaárnyékolást, és hogyan használhat táblázatstílusokat a dokumentumok megjelenésének javítására. A végére rendelkezni fog azzal a képességgel, hogy jól formázott táblázatokat készítsen, amelyek kiemelik adatait.

## Előfeltételek

Mielőtt elkezdenénk, néhány dolgot meg kell tennie:

1. Java Development Kit (JDK): Győződjön meg arról, hogy a JDK 8 vagy újabb verziója van telepítve. Az Aspose.Words for Java megfelelő futtatásához kompatibilis JDK szükséges.
2. Integrált fejlesztői környezet (IDE): Az olyan IDE-k, mint az IntelliJ IDEA vagy az Eclipse, segítenek a Java-projektek kezelésében és a fejlesztési folyamat egyszerűsítésében.
3.  Aspose.Words for Java Library: Töltse le az Aspose.Words for Java legújabb verzióját[itt](https://releases.aspose.com/words/java/) és vegye fel a projektjébe.
4. Mintakód: Néhány minta kódrészletet fogunk használni, ezért győződjön meg arról, hogy rendelkezik alapvető ismeretekkel a Java programozásról és a könyvtárak projektbe való integrálásáról.

## Csomagok importálása

Az Aspose.Words for Java program használatához importálnia kell a megfelelő csomagokat a projektbe. Ezek a csomagok biztosítják a dokumentumok kezeléséhez és formázásához szükséges osztályokat és módszereket.

```java
import com.aspose.words.*;
```

Ez az importálási utasítás hozzáférést biztosít a dokumentumokban lévő táblázatok létrehozásához és formázásához szükséges összes alapvető osztályhoz.

## 1. lépés: Táblázatok formázása

Az Aspose.Words for Java tábláinak formázása magában foglalja a szegélyek beállítását, a cellák árnyékolását és a különféle formázási beállítások alkalmazását. A következőképpen teheti meg:

### Töltse be a dokumentumot

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Hozzon létre és formázza meg a táblázatot

```java
Table table = builder.startTable();
builder.insertCell();

// Állítsa be a szegélyeket az egész táblázathoz.
table.setBorders(LineStyle.SINGLE, 2.0, Color.BLACK);
        
// Állítsa be a cella árnyékolását ehhez a cellához.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.RED);
builder.writeln("Cell #1");

builder.insertCell();
        
// Adjon meg más cellaárnyékolást a második cellához.
builder.getCellFormat().getShading().setBackgroundPatternColor(Color.GREEN);
builder.writeln("Cell #2");

builder.endRow();
```

### A cellaszegélyek testreszabása

```java
// Törölje a cellaformázást a korábbi műveletekből.
builder.getCellFormat().clearFormatting();

builder.insertCell();

// Hozzon létre nagyobb kereteket a sor első cellájához.
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

### Magyarázat

Ebben a példában:
- Szegélyek beállítása: A teljes táblázat szegélyeit egyetlen vonalstílusra állítottuk, 2,0 pont vastagsággal.
- Cellaárnyékolás: Az első cella piros, a második cella zöld árnyalatú. Ez segít vizuálisan megkülönböztetni a sejteket.
- Cellaszegélyek: A harmadik cellához vastagabb szegélyeket hozunk létre, hogy a többitől eltérően kiemeljük.

## 2. lépés: Táblázatstílusok alkalmazása

Az Aspose.Words for Java táblázatstílusai lehetővé teszik, hogy előre meghatározott formázási beállításokat alkalmazzon a táblákra, megkönnyítve ezzel a konzisztens megjelenés elérését. A következőképpen alkalmazhat stílust az asztalra:

### Készítse el a dokumentumot és a táblázatot

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

Table table = builder.startTable();
        
// A táblázat formázása előtt legalább egy sort be kell szúrnunk.
builder.insertCell();
```

### Táblázatstílus alkalmazása

```java
// Állítsa be a táblázat stílusát egyedi stílusazonosító alapján.
table.setStyleIdentifier(StyleIdentifier.MEDIUM_SHADING_1_ACCENT_1);
        
// Alkalmazza, hogy mely jellemzőket kell a stílus szerint formázni.
table.setStyleOptions(TableStyleOptions.FIRST_COLUMN | TableStyleOptions.ROW_BANDS | TableStyleOptions.FIRST_ROW);
table.autoFit(AutoFitBehavior.AUTO_FIT_TO_CONTENTS);
```

### Táblázatadatok hozzáadása

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

### Magyarázat

Ebben a példában:
- Táblázatstílus beállítása: Egy előre meghatározott stílust alkalmazunk (`MEDIUM_SHADING_1_ACCENT_1`) az asztalra. Ez a stílus magában foglalja a táblázat különböző részeinek formázását.
- Stílusbeállítások: Meghatározzuk, hogy az első oszlopot, a sorsávokat és az első sort a stílusbeállításoknak megfelelően kell formázni.
-  AutoFit: használjuk`AUTO_FIT_TO_CONTENTS` hogy a táblázat méretét a tartalom alapján állítsa be.

## Következtetés

És megvan! Sikeresen formázta a táblázatokat és alkalmazta a stílusokat az Aspose.Words for Java segítségével. Ezekkel a technikákkal olyan asztalokat készíthet, amelyek nem csak funkcionálisak, hanem látványosak is. A táblázatok hatékony formázásával nagyban javíthatja a dokumentumok olvashatóságát és professzionális megjelenését.

Az Aspose.Words for Java egy robusztus eszköz, amely kiterjedt szolgáltatásokat kínál a dokumentumkezeléshez. A táblázat formázásának és stílusainak elsajátításával egy lépéssel közelebb kerülhet a könyvtár teljes erejének kiaknázásához.

## GYIK

### 1. Használhatok olyan egyéni táblázatstílusokat, amelyek nem szerepelnek az alapértelmezett beállításokban?

 Igen, az Aspose.Words for Java segítségével egyéni stílusokat határozhat meg és alkalmazhat a táblákra. Ellenőrizze a[dokumentáció](https://reference.aspose.com/words/java/) további részletekért az egyéni stílusok létrehozásáról.

### 2. Hogyan alkalmazhatom a feltételes formázást a táblázatokban?

Az Aspose.Words for Java lehetővé teszi a táblázat formázásának programozott beállítását a feltételek alapján. Ezt úgy teheti meg, hogy ellenőriz bizonyos feltételeket a kódban, és ennek megfelelően alkalmazza a formázást.

### 3. Formázhatom az egyesített cellákat egy táblázatban?

Igen, az egyesített cellákat ugyanúgy formázhatja, mint a normál cellákat. Győződjön meg róla, hogy a cellák egyesítése után formázást alkalmaz, hogy a változások tükröződjenek.

### 4. Lehetséges-e dinamikusan beállítani a táblázat elrendezését?

Igen, dinamikusan módosíthatja a táblázat elrendezését a cellák méretének, a táblázat szélességének és egyéb tulajdonságainak módosításával a tartalom vagy a felhasználói bevitel alapján.

### 5. Hol kaphatok további információkat a táblázat formázásával kapcsolatban?

 Részletesebb példákért és lehetőségekért keresse fel a[Aspose.Words API dokumentáció](https://reference.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
