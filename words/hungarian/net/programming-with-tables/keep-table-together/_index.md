---
title: Tartsa együtt az asztalt
linktitle: Tartsa együtt az asztalt
second_title: Aspose.Words Document Processing API
description: Az Aspose.Words for .NET segítségével megtudhatja, hogyan akadályozhatja meg, hogy a táblázatok oldalakra törjenek a Word-dokumentumokban. Kövesse útmutatónkat a professzionális, olvasható dokumentumok karbantartásához.
weight: 10
url: /hu/net/programming-with-tables/keep-table-together/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tartsa együtt az asztalt

## Bevezetés

Volt már olyan, hogy csalódott volt, amikor a Word-dokumentumban lévő táblázat két oldalra szakad? Mintha a gondosan összeállított információid hirtelen úgy döntöttek volna, hogy félúton szünetet tartanak! A táblázatok egy oldalon tartása kulcsfontosságú az olvashatóság és a megjelenítés szempontjából. Legyen szó jelentésről, projektjavaslatról vagy csak egy személyes dokumentumról, a táblázatok felosztása meglehetősen idegesítő lehet. Szerencsére az Aspose.Words for .NET remek megoldást kínál a probléma megoldására. Ebben az oktatóanyagban végigvezetjük azokat a lépéseket, amelyekkel az asztalok épek és élesek maradnak. Merüljünk el!

## Előfeltételek

Mielőtt elkezdenénk, győződjön meg arról, hogy rendelkezik a következőkkel:

1.  Aspose.Words for .NET – Ha még nem telepítette, letöltheti innen[itt](https://releases.aspose.com/words/net/).
2. Word-dokumentum táblázattal – Egy olyan mintadokumentummal fogunk dolgozni, amelynek több oldalt átívelő táblázata van.
3. Alapvető C# ismerete – Ez az oktatóanyag feltételezi, hogy rendelkezik a C# programozás alapvető ismereteivel.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez hozzáférést biztosít számunkra az Aspose.Words for .NET-hez szükséges osztályokhoz és metódusokhoz.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Bontsuk le a folyamatot könnyű, emészthető lépésekre. Kezdjük a dokumentumunk betöltésével, és a frissített dokumentum mentésével fejezzük be, ahol a táblázat együtt marad.

## 1. lépés: Töltse be a dokumentumot

 A Word-dokumentum használatához először be kell töltenünk azt. Használjuk a`Document` osztály erre.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## 2. lépés: Nyissa meg a táblázatot

Ezután meg kell szereznünk azt az asztalt, amelyet együtt szeretnénk tartani. Feltételezzük, hogy ez a dokumentum első táblázata.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## 3. lépés: Állítsa be a KeepWithNext beállítást a bekezdésekhez

 Ahhoz, hogy a táblázat ne törjön oldalakra, be kell állítanunk a`KeepWithNext` tulajdonságot a táblázat minden bekezdéséhez, kivéve az utolsó sor utolsó bekezdéseit.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
    foreach (Paragraph para in cell.Paragraphs)
    {
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
    }
}
```

## 4. lépés: Mentse el a dokumentumot

Végül elmentjük a frissített dokumentumot. Ez alkalmazza a módosításainkat, és biztosítja, hogy a táblázat egy oldalon maradjon.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

## Következtetés

És megvan! Csak néhány sornyi kóddal megakadályozhatja, hogy a táblázatok oldalakra váljanak a Word-dokumentumokban. Ez az egyszerű, de hatékony megoldás gondoskodik arról, hogy táblázatai tiszták és professzionálisak maradjanak, javítva a dokumentumok olvashatóságát. Az Aspose.Words for .NET megkönnyíti az ilyen formázási problémák kezelését, és lehetővé teszi, hogy a nagyszerű tartalom létrehozására összpontosítson.

## GYIK

### Tarthatok több táblát együtt ezzel a módszerrel?  
Igen, ugyanazt a logikát több táblára is alkalmazhatja, ha végigfut a dokumentumban minden táblán.

### Mi van, ha a táblázatom túl nagy ahhoz, hogy elférjen egy oldalon?  
Ha egy táblázat túl nagy ahhoz, hogy egyetlen oldalon elférjen, akkor is átfogja az oldalakat. Ez a módszer biztosítja, hogy a kisebb asztalok sértetlenek maradjanak szétválás nélkül.

### Van mód ennek automatizálására egy dokumentum összes táblájára?  
 Igen, végignézheti a dokumentum összes táblázatát, és alkalmazhatja a`KeepWithNext` tulajdonság minden bekezdéshez.

### Szükségem van fizetős licencre az Aspose.Words for .NET-hez?  
Kezdheti egy ingyenes próbaverzióval[itt](https://releases.aspose.com/), de a teljes funkcionalitás érdekében fizetős licenc ajánlott.

### Alkalmazhatok más formázást a táblázatra, miközben egyben tartom?  
Teljesen! A táblázatot szükség szerint formázhatja, miközben gondoskodik arról, hogy egy oldalon maradjon.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
