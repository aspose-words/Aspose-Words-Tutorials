---
"description": "Tanuld meg, hogyan módosíthatod a frissítési kultúra forrását az Aspose.Words for .NET programban ezzel az útmutatóval. A dátumformázást könnyedén szabályozhatod a különböző kultúrák alapján."
"linktitle": "Mező módosítása Kultúraforrás frissítése"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Mező módosítása Kultúraforrás frissítése"
"url": "/hu/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mező módosítása Kultúraforrás frissítése

## Bevezetés

Ebben az oktatóanyagban elmerülünk az Aspose.Words for .NET világában, és felfedezzük, hogyan módosítható a mező frissítési kulturális forrása. Ha olyan Word-dokumentumokkal dolgozol, amelyek dátummezőket tartalmaznak, és szeretnéd szabályozni, hogy ezek a dátumok hogyan legyenek formázva a különböző kultúrák alapján, akkor ez az útmutató neked szól. Lépésről lépésre végigvezetünk a folyamaton, biztosítva, hogy megértsd az egyes koncepciókat, és hatékonyan alkalmazd azokat a projektjeidben.

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjünk meg róla, hogy a következők megvannak:

- Aspose.Words .NET-hez: Letöltheti innen: [itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Bármely .NET kompatibilis IDE (pl. Visual Studio).
- C# alapismeretek: Ez az oktatóanyag feltételezi, hogy rendelkezel a C# programozás alapjaival.

## Névterek importálása

Először importáljuk a projektünkhöz szükséges névtereket. Ez biztosítja, hogy hozzáférjünk az Aspose.Words által biztosított összes szükséges osztályhoz és metódushoz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Most bontsuk le a példát több lépésre, hogy könnyebben megérthesd, hogyan módosíthatod az Aspose.Words for .NET mező kulturális forrásának frissítését.

## 1. lépés: A dokumentum inicializálása

Az első lépés egy új példány létrehozása a `Document` osztály és egy `DocumentBuilder`Ez megalapozza a Word-dokumentumunk létrehozását és kezelését.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Mezők beszúrása adott területi beállítással

Ezután mezőket kell beszúrnunk a dokumentumba. Ebben a példában két dátummezőt fogunk beszúrni. A betűtípus területi beállítását németre állítjuk (LocaleId = 1031), hogy bemutassuk, hogyan befolyásolja a kultúra a dátumformátumot.

```csharp
builder.Font.LocaleId = 1031; // német
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## 3. lépés: Mezőfrissítési kultúraforrás beállítása

A mezők frissítésekor használt kultúra szabályozásához beállítottuk a `FieldUpdateCultureSource` a tulajdona `FieldOptions` osztály. Ez a tulajdonság határozza meg, hogy a kultúra a mezőkódból vagy a dokumentumból származik-e.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## 4. lépés: Körlevél végrehajtása

Most körlevelet kell végrehajtanunk, hogy a mezőket tényleges adatokkal töltsük fel. Ebben a példában a második dátummezőt fogjuk beállítani (`Date2`) 2011. január 1-jéig.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## 5. lépés: A dokumentum mentése

Végül elmentjük a dokumentumot a megadott könyvtárba. Ez a lépés befejezi a mező frissítési kultúraforrásának módosítását.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Következtetés

És íme! Sikeresen módosítottad a mező frissítési kulturális forrását az Aspose.Words for .NET fájlban. A következő lépések követésével biztosíthatod, hogy a Word-dokumentumaid a megadott kulturális beállításoknak megfelelően jelenítsék meg a dátumokat és más mezőértékeket. Ez különösen hasznos lehet nemzetközi közönség számára létrehozott dokumentumok esetén.

## GYIK

### Mi a célja a beállításnak? `LocaleId`?
A `LocaleId` meghatározza a szöveg kulturális beállításait, amelyek befolyásolják a dátumok és más területi beállításokra vonatkozó adatok formázását.

### Használhatok a némettől eltérő területi beállítást?
Igen, beállíthatod a `LocaleId` bármely érvényes területi azonosítóra. Például 1033 az angol (Egyesült Államok) esetén.

### Mi történik, ha nem állítom be a `FieldUpdateCultureSource` ingatlan?
Ha ez a tulajdonság nincs beállítva, a mezők frissítésekor a dokumentum alapértelmezett kulturális beállításai lesznek érvényben.

### Lehetséges a mezőket a dokumentum kultúrája alapján frissíteni a mezőkód helyett?
Igen, beállíthatja `FieldUpdateCultureSource` hogy `FieldUpdateCultureSource.Document` dokumentum kulturális beállításainak használatához.

### Hogyan formázhatom a dátumokat más mintában?
A dátumformátum mintáját módosíthatja a `InsertField` módszer módosításával `\\@` kapcsoló értéke.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}