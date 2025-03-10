---
title: Elválasztás visszahívás
linktitle: Elválasztás visszahívás
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan valósíthat meg elválasztási visszahívást az Aspose.Words for .NET-ben a dokumentumok formázásának javítása érdekében ezzel az átfogó, lépésről lépésre szóló útmutatóval.
weight: 10
url: /hu/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Elválasztás visszahívás


## Bevezetés

Szia! Volt már olyan, hogy belegabalyodott a szövegformázás bonyolultságába, különösen, ha olyan nyelvekkel foglalkozik, amelyek elválasztást igényelnek? Nem vagy egyedül. Az elválasztás, bár kulcsfontosságú a megfelelő szövegelrendezéshez, egy kis fejfájást okozhat. De mit gondol? Az Aspose.Words for .NET hátat kapott. Ez a hatékony könyvtár lehetővé teszi a szöveg formázásának zökkenőmentes kezelését, beleértve az elválasztás kezelését visszahívási mechanizmuson keresztül. Érdekelt? Nézzük meg, hogyan valósíthat meg elválasztási visszahívást az Aspose.Words for .NET használatával.

## Előfeltételek

Mielőtt bepiszkítanánk a kódot, győződjünk meg arról, hogy mindennel megvan, amire szüksége van:

1. Aspose.Words for .NET: Győződjön meg arról, hogy rendelkezik a könyvtárral. Megteheti[töltse le itt](https://releases.aspose.com/words/net/).
2. IDE: Olyan fejlesztői környezet, mint a Visual Studio.
3. C# alapismeretek: C# és .NET keretrendszer ismerete.
4. Elválasztási szótárak: Elválasztási szótárak a használni kívánt nyelvekhez.
5.  Aspose licenc: Érvényes Aspose licenc. Kaphatsz a[ideiglenes engedély](https://purchase.aspose.com/temporary-license/) ha nincs ilyened.

## Névterek importálása

Először is importáljuk a szükséges névtereket. Ez biztosítja, hogy kódunk hozzáférjen az Aspose.Words összes osztályához és metódusához, amire szükségünk van.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## 1. lépés: Regisztrálja az elválasztási visszahívást

A kezdéshez regisztrálnunk kell az elválasztási visszahívásunkat. Itt mondjuk meg az Aspose.Words-nek, hogy használja az egyéni elválasztási logikánkat.

```csharp
try
{
    // Regisztráljon elválasztási visszahívást.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

 Itt létrehozzuk az egyéni visszahívásunk példányát, és hozzárendeljük`Hyphenation.Callback`.

## 2. lépés: Határozza meg a dokumentum elérési útját

Ezután meg kell határoznunk a könyvtárat, ahol a dokumentumainkat tároljuk. Ez kulcsfontosságú, mivel ezen az úton fogunk betölteni és elmenteni dokumentumokat.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a dokumentumok tényleges elérési útjával.

## 3. lépés: Töltse be a dokumentumot

Most töltsük be az elválasztást igénylő dokumentumot.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Itt egy német szöveges dokumentumot töltünk be. Cserélheted`"German text.docx"` a dokumentum fájlnevével.

## 4. lépés: Mentse el a dokumentumot

A dokumentum betöltése után elmentjük egy új fájlba, és közben alkalmazzuk az elválasztási visszahívást.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Ez a sor PDF-ként menti a dokumentumot elválasztással.

## 5. lépés: Kezelje a hiányzó elválasztási szótár kivételét

Néha olyan problémába ütközhet, hogy hiányzik az elválasztási szótár. Intézzük ezt.

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

Ebben a blokkban felfogjuk a hiányzó szótárak kivételét, és kinyomtatjuk az üzenetet.

## 6. lépés: Valósítsa meg az Egyéni elválasztási visszahívási osztályt

 Most pedig hajtsuk végre a`CustomHyphenationCallback` osztály, amely kezeli az elválasztási szótárak kérését.

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
        // Regisztráljon szótárt a kívánt nyelvhez.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

 Ebben az osztályban a`RequestDictionary` metódus hívódik meg, amikor elválasztási szótárra van szükség. Ellenőrzi a nyelvet és regisztrálja a megfelelő szótárt.

## Következtetés

És megvan! Most tanulta meg, hogyan valósítson meg elválasztási visszahívást az Aspose.Words for .NET-ben. Az alábbi lépések követésével biztosíthatja, hogy a dokumentumok gyönyörűen formázva legyenek, nyelvtől függetlenül. Legyen szó angolról, németről vagy bármilyen más nyelvről, ezzel a módszerrel könnyedén kezelheti az elválasztást.

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony dokumentummanipulációs könyvtár, amely lehetővé teszi a fejlesztők számára a dokumentumok programozott létrehozását, módosítását és konvertálását.

### Miért fontos az elválasztás a dokumentum formázásánál?
Az elválasztás javítja a szöveg elrendezését azáltal, hogy a megfelelő helyeken töri a szavakat, így olvashatóbb és látványosabb dokumentumot biztosít.

### Használhatom ingyenesen az Aspose.Words-t?
 Az Aspose.Words ingyenes próbaverziót kínál. Megkaphatod[itt](https://releases.aspose.com/).

### Hogyan juthatok el kötőjeles szótárhoz?
Elválasztási szótárakat letölthet különféle online forrásokból, vagy szükség esetén létrehozhat saját szótárakat.

### Mi történik, ha hiányzik egy elválasztási szótár?
 Ha hiányzik egy szótár, a`RequestDictionary`metódus kivételt dob, amelyet kezelve tájékoztathatja a felhasználót, vagy tartalékot adhat.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
