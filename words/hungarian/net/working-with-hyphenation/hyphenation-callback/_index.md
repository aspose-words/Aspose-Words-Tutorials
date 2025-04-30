---
"description": "Tanuld meg, hogyan valósítsd meg az elválasztási visszahívást az Aspose.Words for .NET-ben a dokumentumok formázásának javítása érdekében ezzel az átfogó, lépésről lépésre haladó útmutatóval."
"linktitle": "Elválasztó visszahívás"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Elválasztó visszahívás"
"url": "/hu/net/working-with-hyphenation/hyphenation-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Elválasztó visszahívás


## Bevezetés

Sziasztok! Elkeseredtetek már a szövegformázás bonyolultságában, különösen, ha olyan nyelvekkel dolgoztok, amelyek elválasztást igényelnek? Nem vagy egyedül. Az elválasztás, bár elengedhetetlen a megfelelő szövegelrendezéshez, kissé fejfájást okozhat. De tudjátok mit? Az Aspose.Words for .NET a segítségedre lesz. Ez a hatékony függvénykönyvtár lehetővé teszi a szövegformázás zökkenőmentes kezelését, beleértve az elválasztást egy visszahívási mechanizmuson keresztül. Kíváncsiak vagytok? Nézzük meg részletesebben, hogyan valósíthattok meg elválasztási visszahívást az Aspose.Words for .NET segítségével.

## Előfeltételek

Mielőtt belekezdenénk a kódba, győződjünk meg róla, hogy minden szükséges dolog megvan:

1. Aspose.Words .NET-hez: Győződjön meg róla, hogy rendelkezik a könyvtárral. Tudja [töltsd le itt](https://releases.aspose.com/words/net/).
2. IDE: Egy fejlesztői környezet, mint például a Visual Studio.
3. C# alapismeretek: A C# és a .NET keretrendszer ismerete.
4. Elválasztó szótárak: Elválasztó szótárak a használni kívánt nyelvekhez.
5. Aspose licenc: Érvényes Aspose licenc. Szerezhet egy [ideiglenes engedély](https://purchase.aspose.com/temporary-license/) ha nincs ilyened.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez biztosítja, hogy a kódunk hozzáférjen az Aspose.Words összes szükséges osztályához és metódusához.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## 1. lépés: Regisztrálja az elválasztási visszahívást

Kezdésként regisztrálnunk kell az elválasztási visszahívásunkat. Itt utasítjuk az Aspose.Words-t, hogy használja az egyéni elválasztási logikánkat.

```csharp
try
{
    // Regiszter elválasztási visszahívása.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

Itt létrehozunk egy példányt az egyéni visszahívásunkból, és hozzárendeljük a következőhöz: `Hyphenation.Callback`.

## 2. lépés: A dokumentum elérési útjának meghatározása

Ezután meg kell határoznunk azt a könyvtárat, ahová a dokumentumainkat tároljuk. Ez kulcsfontosságú, mivel erről az elérési útról fogjuk betölteni és menteni a dokumentumokat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Csere `"YOUR DOCUMENT DIRECTORY"` a dokumentumok tényleges elérési útjával.

## 3. lépés: A dokumentum betöltése

Most töltsük be a kötőjelezést igénylő dokumentumot.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Itt egy német szöveges dokumentumot töltünk be. Lecserélheti `"German text.docx"` dokumentum fájlnevével.

## 4. lépés: A dokumentum mentése

A dokumentum betöltése után új fájlba mentjük, a folyamat során alkalmazva az elválasztási visszahívást.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Ez a sor PDF formátumban menti el a dokumentumot elválasztással.

## 5. lépés: Hiányzó elválasztási szótár kivétel kezelése

Előfordulhat, hogy hiányzik a kötőjelszótár. Nézzük ezt meg.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

Ebben a blokkban a hiányzó szótárakkal kapcsolatos specifikus kivételt fogjuk el, és kinyomtatjuk az üzenetet.

## 6. lépés: Az egyéni elválasztási visszahívási osztály megvalósítása

Most pedig implementáljuk a `CustomHyphenationCallback` osztály, amely a kötőszótárak iránti kérelmeket kezeli.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Regisztrálja a szótárat a kért nyelvhez.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

Ebben az osztályban a `RequestDictionary` A metódust minden alkalommal meghívjuk, amikor elválasztási szótárra van szükség. Ellenőrzi a nyelvet, és regisztrálja a megfelelő szótárat.

## Következtetés

És íme! Most megtanultad, hogyan implementálhatsz elválasztási visszahívást az Aspose.Words for .NET-ben. A következő lépéseket követve biztosíthatod, hogy dokumentumaid szépen formázottak legyenek, a nyelvtől függetlenül. Akár angolul, németül vagy bármilyen más nyelven dolgozol, ez a módszer lehetővé teszi az elválasztások egyszerű kezelését.

## GYIK

### Mi az Aspose.Words .NET-hez?
Az Aspose.Words for .NET egy hatékony dokumentumkezelő könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan hozzanak létre, módosítsanak és konvertáljanak dokumentumokat.

### Miért fontos a kötőjel használata a dokumentum formázásában?
A kötőjelek használata javítja a szöveg elrendezését azáltal, hogy a szavakat a megfelelő helyeken töri el, így biztosítva az olvashatóbb és vizuálisan vonzóbb dokumentumot.

### Ingyenesen használhatom az Aspose.Words-öt?
Az Aspose.Words ingyenes próbaverziót kínál. Letöltheted. [itt](https://releases.aspose.com/).

### Hogyan jutok hozzá egy kötőjelezési szótárhoz?
A kötőjeles szótárakat különböző online forrásokból töltheti le, vagy szükség esetén létrehozhat sajátokat.

### Mi történik, ha hiányzik egy elválasztási szótár?
Ha hiányzik egy szótár, akkor a `RequestDictionary` A metódus kivételt dob, amelynek kezelésével tájékoztathatod a felhasználót, vagy tartalék megoldást biztosíthatsz.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}