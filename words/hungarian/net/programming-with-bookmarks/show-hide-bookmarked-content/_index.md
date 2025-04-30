---
"description": "Tanulja meg, hogyan jelenítheti meg és rejtheti el a könyvjelzővel ellátott tartalmat a Word-dokumentumokban az Aspose.Words for .NET használatával ebből a részletes, lépésről lépésre haladó útmutatóból."
"linktitle": "Könyvjelzővel ellátott tartalom megjelenítése és elrejtése Word-dokumentumban"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Könyvjelzővel ellátott tartalom megjelenítése és elrejtése Word-dokumentumban"
"url": "/hu/net/programming-with-bookmarks/show-hide-bookmarked-content/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Könyvjelzővel ellátott tartalom megjelenítése és elrejtése Word-dokumentumban

## Bevezetés

Készen állsz belemerülni a dokumentumkezelés világába az Aspose.Words for .NET segítségével? Akár fejlesztő vagy, aki automatizálni szeretné a dokumentumkezelési feladatokat, akár csak kíváncsi vagy a Word-fájlok programozott kezelésére, jó helyen jársz. Ma azt vizsgáljuk meg, hogyan jelenítheted meg és rejtheted el a könyvjelzővel ellátott tartalmat egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ez a lépésről lépésre szóló útmutató profivá tesz a tartalom láthatóságának könyvjelzők alapján történő szabályozásában. Kezdjük is!

## Előfeltételek

Mielőtt belevágnánk a lényegbe, van néhány dolog, amire szükséged lesz:

1. Visual Studio: Bármely .NET-tel kompatibilis verzió.
2. Aspose.Words .NET-hez: Töltsd le [itt](https://releases.aspose.com/words/net/).
3. C# alapismeretek: Ha tudsz írni egy egyszerű "Hello World" programot, akkor indulhatsz is.
4. Könyvjelzőkkel ellátott Word-dokumentum: Ebben az oktatóanyagban egy könyvjelzőkkel ellátott mintadokumentumot fogunk használni.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez biztosítja, hogy minden szükséges eszközünk meglegyen a feladatunkhoz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Bookmark;
```

Miután ezeket a névtereket beállítottuk, készen állunk az utunk megkezdésére.

## 1. lépés: A projekt beállítása

Rendben, kezdjük a projekt beállításával a Visual Studio-ban.

### Új projekt létrehozása

Nyisd meg a Visual Studiot, és hozz létre egy új Console App (.NET Core) projektet. Nevezd el valami figyelemfelkeltőt, például a „BookmarkVisibilityManager”.

### Aspose.Words hozzáadása .NET-hez

Hozzá kell adnod az Aspose.Words for .NET csomagot a projektedhez. Ezt a NuGet csomagkezelőn keresztül teheted meg.

1. Lépjen az Eszközök > NuGet csomagkezelő > Megoldáshoz tartozó NuGet csomagok kezelése menüpontra.
2. Keresd az „Aspose.Words” kifejezést.
3. Telepítse a csomagot.

Remek! Most, hogy a projektünk beállítva, folytassuk a dokumentum betöltésével.

## 2. lépés: A dokumentum betöltése

Betöltenünk kell a könyvjelzőket tartalmazó Word-dokumentumot. Ebben az oktatóanyagban egy „Bookmarks.docx” nevű mintadokumentumot fogunk használni.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks.docx");
```

Ez a kódrészlet beállítja a dokumentumkönyvtár elérési útját, és betölti a dokumentumot a `doc` objektum.

## 3. lépés: Könyvjelzővel ellátott tartalom megjelenítése/elrejtése

Most jön a mókás rész – a tartalom megjelenítése vagy elrejtése könyvjelzők alapján. Létrehozunk egy metódust, melynek neve `ShowHideBookmarkedContent` hogy ezt kezelje.

Íme a módszer, amellyel ki- és bekapcsolhatja a könyvjelzővel ellátott tartalom láthatóságát:

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

### A módszer lebontása

- Könyvjelző lekérése: `Bookmark bm = doc.Range.Bookmarks[bookmarkName];` lekéri a könyvjelzőt.
- Csomópont bejárása: Bejárjuk a könyvjelzőn belüli csomópontokat.
- Láthatóság váltása: Ha a csomópont egy `Run` (egybefüggő szövegsorozat), beállítjuk a `Hidden` ingatlan.

## 4. lépés: A módszer alkalmazása

Miután elkészítettük a módszerünket, alkalmazzuk azt egy könyvjelző alapján tartalom megjelenítésére vagy elrejtésére.

```csharp
ShowHideBookmarkedContent(doc, "MyBookmark1", true);
```

Ez a kódsor elrejti a "MyBookmark1" nevű könyvjelző tartalmát.

## 5. lépés: A dokumentum mentése

Végül mentsük el a módosított dokumentumunkat.

```csharp
doc.Save(dataDir + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

Ez elmenti a dokumentumot az általunk végrehajtott módosításokkal.

## Következtetés

És tessék! Most megtanultad, hogyan jelenítheted meg és rejtheted el a könyvjelzővel ellátott tartalmat egy Word-dokumentumban az Aspose.Words for .NET segítségével. Ez a hatékony eszköz gyerekjátékká teszi a dokumentumok kezelését, akár jelentéseket automatizálsz, sablonokat hozol létre, vagy csak Word-fájlokkal bütykölsz. Jó kódolást!

## GYIK

### Több könyvjelzőt is ki- és bekapcsolhatok egyszerre?
Igen, felhívhatod a `ShowHideBookmarkedContent` metódust minden egyes ki-/bekapcsolni kívánt könyvjelzőhöz.

### A tartalom elrejtése befolyásolja a dokumentum szerkezetét?
Nem, a tartalom elrejtése csak a láthatóságát befolyásolja. A tartalom a dokumentumban marad.

### Használhatom ezt a módszert más típusú tartalmakhoz is?
Ez a metódus kifejezetten a szövegek futtatását kapcsolja ki. Más tartalomtípusok esetén módosítani kell a csomópontok bejárásának logikáját.

### Ingyenes az Aspose.Words .NET-hez?
Az Aspose.Words ingyenes próbaverziót kínál [itt](https://releases.aspose.com/), de az éles használathoz teljes licenc szükséges. Megvásárolhatja [itt](https://purchase.aspose.com/buy).

### Hogyan kaphatok támogatást, ha problémákba ütközöm?
Támogatást kaphatsz az Aspose közösségtől [itt](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}