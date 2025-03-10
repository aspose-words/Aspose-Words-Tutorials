---
title: Könyvjelzővel ellátott tartalom elrejtése a Word-dokumentumban
linktitle: Könyvjelzővel ellátott tartalom elrejtése a Word-dokumentumban
second_title: Aspose.Words Document Processing API
description: Ebből a részletes, lépésenkénti útmutatóból megtudhatja, hogyan jeleníthet meg és rejthet el könyvjelzőkkel ellátott tartalmakat Word dokumentumokban az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-bookmarks/show-hide-bookmarked-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Könyvjelzővel ellátott tartalom elrejtése a Word-dokumentumban

## Bevezetés

Készen áll, hogy belemerüljön a dokumentumkezelés világába az Aspose.Words for .NET segítségével? Akár fejlesztő, aki a dokumentumfeladatokat automatizálni szeretné, akár csak valaki, aki kíváncsi a Word-fájlok programozott kezelésére, jó helyen jár. Ma azt vizsgáljuk meg, hogyan jeleníthet meg és rejthet el könyvjelzőkkel ellátott tartalmat egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ez a lépésenkénti útmutató profivá tesz a tartalom könyvjelzők alapján történő láthatóságának szabályozásában. Kezdjük is!

## Előfeltételek

Mielőtt belevágnánk a lényegbe, van néhány dolog, amire szükséged lesz:

1. Visual Studio: Bármilyen verzió, amely kompatibilis a .NET-tel.
2.  Aspose.Words for .NET: Töltse le[itt](https://releases.aspose.com/words/net/).
3. A C# alapjai: Ha tudsz egy egyszerű "Hello World" programot írni, akkor készen állsz.
4. Word-dokumentum könyvjelzőkkel: Ehhez az oktatóanyaghoz könyvjelzőkkel ellátott mintadokumentumot fogunk használni.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez biztosítja, hogy a feladatunkhoz szükséges összes eszköz rendelkezésre álljon.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Ha ezekkel a névterekkel a helyükre került, mindannyian készen állunk az utazás megkezdésére.

## 1. lépés: A projekt beállítása

Rendben, kezdjük a dolgokat azzal, hogy beállítjuk projektünket a Visual Studióban.

### Hozzon létre egy új projektet

Nyissa meg a Visual Studio-t, és hozzon létre egy új Console App (.NET Core) projektet. Nevezd valami fülbemászónak, például "BookmarkVisibilityManager".

### Adja hozzá az Aspose.Words for .NET-et

Hozzá kell adnia az Aspose.Words for .NET fájlt a projekthez. Ezt a NuGet Package Manager segítségével teheti meg.

1. Nyissa meg az Eszközök > NuGet-csomagkezelő > NuGet-csomagok kezelése a megoldáshoz menüpontot.
2. Keresse meg az "Aspose.Words" kifejezést.
3. Telepítse a csomagot.

Nagy! Most, hogy a projektünk elkészült, folytassuk a dokumentumunk betöltését.

## 2. lépés: A dokumentum betöltése

Be kell töltenünk a könyvjelzőket tartalmazó Word dokumentumot. Ehhez az oktatóanyaghoz a „Bookmarks.docx” nevű mintadokumentumot használjuk.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

 Ez a kódrészlet beállítja a dokumentumkönyvtár elérési útját, és betölti a dokumentumot a`doc` objektum.

## 3. lépés: A könyvjelzővel ellátott tartalom megjelenítése/elrejtése

Most jön a szórakoztató rész – a tartalom megjelenítése vagy elrejtése könyvjelzők alapján. Létrehozunk egy metódust, melynek neve`ShowHideBookmarkedContent` kezelni ezt.

A következő módszerrel kapcsolhatja be a könyvjelzővel ellátott tartalom láthatóságát:

```csharp
public void ShowHideBookmarkedContent(Document doc, string bookmarkName, bool isHidden)
{
    Bookmark bm = doc.Range.Bookmarks[bookmarkName];

    Node currentNode = bm.BookmarkStart;
    while (currentNode != null && currentNode.NodeType != NodeType.BookmarkEnd)
    {
        if (currentNode.NodeType == NodeType.Run)
        {
            Run run = currentNode as Run;
            run.Font.Hidden = isHidden;
        }
        currentNode = currentNode.NextSibling;
    }
}
```

### A módszer bontása

-  Könyvjelzők lekérése:`Bookmark bm = doc.Range.Bookmarks[bookmarkName];` lekéri a könyvjelzőt.
- Csomópont bejárás: Bejárjuk a könyvjelzőn belüli csomópontokat.
-  Láthatóság kapcsoló: Ha a csomópont a`Run` (egy összefüggő szövegsorozat), beállítjuk`Hidden` ingatlan.

## 4. lépés: A módszer alkalmazása

Ha a módszerünk a helyén van, alkalmazzuk a könyvjelzők alapján történő tartalom megjelenítésére vagy elrejtésére.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Ez a kódsor elrejti a tartalmat a "MyBookmark1" nevű könyvjelzőn belül.

## 5. lépés: A dokumentum mentése

Végül mentsük el módosított dokumentumunkat.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Ezzel elmenti a dokumentumot az általunk végzett módosításokkal.

## Következtetés

És megvan! Most tanulta meg, hogyan jeleníthet meg és rejthet el könyvjelzővel ellátott tartalmat egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ezzel a hatékony eszközzel gyerekjáték a dokumentumkezelés, legyen szó jelentések automatizálásáról, sablonok létrehozásáról vagy csak Word-fájlokkal való trükközésről. Boldog kódolást!

## GYIK

### Válthatok egyszerre több könyvjelzőt?
 Igen, felhívhatod a`ShowHideBookmarkedContent` módszert minden átváltani kívánt könyvjelzőhöz.

### A tartalom elrejtése befolyásolja a dokumentum szerkezetét?
Nem, a tartalom elrejtése csak annak láthatóságát befolyásolja. A tartalom a dokumentumban marad.

### Használhatom ezt a módszert más típusú tartalomhoz?
Ez a módszer kifejezetten a szöveg futtatását kapcsolja be. Más tartalomtípusok esetén módosítania kell a csomópont bejárási logikáját.

### Az Aspose.Words for .NET ingyenes?
 Az Aspose.Words ingyenes próbaverziót kínál[itt](https://releases.aspose.com/) , de a termelési felhasználáshoz teljes licenc szükséges. Megvásárolhatod[itt](https://purchase.aspose.com/buy).

### Hogyan kaphatok támogatást, ha problémákba ütközöm?
 Támogatást kaphat az Aspose közösségtől[itt](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
