---
"description": "Tanuld meg, hogyan állíthatsz be betűtípus-kiemelési jeleket a Word-dokumentumokban az Aspose.Words for .NET segítségével ebből a részletes, lépésről lépésre haladó útmutatóból. Tökéletes .NET-fejlesztők számára."
"linktitle": "Betűtípus kiemelésjelének beállítása"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Betűtípus kiemelésjelének beállítása"
"url": "/hu/net/working-with-fonts/set-font-emphasis-mark/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Betűtípus kiemelésjelének beállítása

## Bevezetés

mai oktatóanyagban belemerülünk abba, hogyan állíthatunk be betűtípus-kiemelési jeleket egy Word-dokumentumban az Aspose.Words for .NET segítségével. Akár egyedi jellel szeretnél aláhúzni egy adott szöveget, akár egyszerűen csak kiemelni bizonyos szavakat, ez az útmutató segít. Szóval, csatold be a biztonsági övedet, és kezdjük is!

## Előfeltételek

Mielőtt belemerülnénk a részletekbe, győződjünk meg róla, hogy a következő feltételek teljesülnek:

- Aspose.Words for .NET könyvtár: Győződjön meg róla, hogy telepítve van az Aspose.Words for .NET könyvtár. Letöltheti innen: [itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Egy működőképes fejlesztői környezet, például a Visual Studio.
- .NET-keretrendszer: Győződjön meg róla, hogy telepítve van a .NET-keretrendszer.

## Névterek importálása

Az Aspose.Words for .NET használatához importálni kell a szükséges névtereket. Ezeket a kódfájl elejére kell hozzáadni:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Most bontsuk le a folyamatot egyszerű lépésekre. Kövesd figyelmesen az egyes lépéseket a betűtípus-kiemelési jelek beállításához a Word-dokumentumban.

## 1. lépés: A Document és a DocumentBuilder inicializálása

Először is inicializálni kell egy új dokumentumot és egy DocumentBuildert. A DocumentBuilder osztály metódusokat biztosít szöveg és más elemek beszúrásához a dokumentumba.

```csharp
// A dokumentumkönyvtár elérési útja 
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Új dokumentum inicializálása
Document document = new Document();

// A DocumentBuilder inicializálása a dokumentummal
DocumentBuilder builder = new DocumentBuilder(document);
```

## 2. lépés: Betűtípus kiemelésjelének beállítása

Miután a DocumentBuilder elkészült, beállíthatja a betűtípus kiemelési jelét. Ebben a példában az „UnderSolidCircle” kiemelési jelet fogjuk használni.

```csharp
// Betűtípus kiemelési jelének beállítása
builder.Font.EmphasisMark = EmphasisMark.UnderSolidCircle;

// Írj szöveget a kiemelésjellel
builder.Write("Emphasis text");
builder.Writeln();
```

## 3. lépés: Formázás törlése és normál szöveg hozzáadása

A hangsúlyjel beállítása után érdemes lehet hozzáadni némi normál szöveget hangsúlyozás nélkül. Ehhez törölni kell a formázást.

```csharp
// Törölje a betűtípus formázását
builder.Font.ClearFormatting();

// Normál szöveg írása
builder.Write("Simple text");
```

## 4. lépés: A dokumentum mentése

Miután hozzáadta az összes szükséges szöveget és formázást, az utolsó lépés a dokumentum mentése. Adja meg az elérési utat és a fájlnevet, ahová a dokumentumot menteni szeretné.

```csharp
// Mentse el a dokumentumot
document.Save(dataDir + "WorkingWithFonts.SetFontEmphasisMark.docx");
```

## Következtetés

És íme! A betűtípus-kiemelésjelek beállítása egy Word-dokumentumban az Aspose.Words for .NET segítségével ilyen egyszerű. Mindössze néhány sornyi kóddal kiemelheted a szövegedet, és professzionális megjelenést kölcsönözhetsz a dokumentumaidnak. Ne habozz kísérletezni a különböző kiemelésjelekkel és stílusokkal az igényeidnek megfelelően.

## GYIK

### Mik azok a betűtípus-kiemelési jelek?

A betűtípus-kiemelési jelek speciális szimbólumok, amelyeket a szöveghez adnak, hogy kiemeljék azt. Ilyenek lehetnek pontok, körök és egyéb díszítőjelek.

### Használhatok más hangsúlyjeleket az Aspose.Words for .NET-ben?

Igen, az Aspose.Words for .NET különféle hangsúlyjeleket támogat. A különböző lehetőségeket a következő hivatkozással tekintheti meg: [dokumentáció](https://reference.aspose.com/words/net/).

### Ingyenesen használható az Aspose.Words for .NET?

Az Aspose.Words for .NET teljes funkcionalitásához licenc szükséges. Ingyenes próbaverzió igényelhető. [itt](https://releases.aspose.com/) vagy vásároljon licencet [itt](https://purchase.aspose.com/buy).

### Hogyan kaphatok támogatást az Aspose.Words for .NET-hez?

Az Aspose közösségétől és támogató csapatától támogatást kaphatsz, ha felkeresed a következőt: [támogatási fórum](https://forum.aspose.com/c/words/8).

### Használhatom az Aspose.Words for .NET-et más .NET keretrendszerekkel?

Igen, az Aspose.Words for .NET kompatibilis számos .NET keretrendszerrel, beleértve a .NET Core-t és a .NET 5/6-ot.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}