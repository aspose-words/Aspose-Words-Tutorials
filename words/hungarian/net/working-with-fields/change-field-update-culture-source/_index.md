---
title: Mezőfrissítési kultúraforrás módosítása
linktitle: Mezőfrissítési kultúraforrás módosítása
second_title: Aspose.Words Document Processing API
description: Ebből az útmutatóból megtudhatja, hogyan módosíthatja a helyszíni frissítési kultúraforrást az Aspose.Words for .NET-ben. Könnyen szabályozhatja a dátum formázását a különböző kultúrák alapján.
weight: 10
url: /hu/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mezőfrissítési kultúraforrás módosítása

## Bevezetés

Ebben az oktatóanyagban belemerülünk az Aspose.Words for .NET világába, és megvizsgáljuk, hogyan lehet megváltoztatni a helyszíni frissítési kultúraforrást. Ha olyan Word-dokumentumokkal foglalkozik, amelyek dátummezőket tartalmaznak, és szabályoznia kell, hogy ezek a dátumok hogyan legyenek formázva a különböző kultúrák alapján, akkor ez az útmutató az Ön számára készült. Lépésről lépésre járjuk végig a folyamatot, biztosítva, hogy minden koncepciót megértsen, és hatékonyan tudja alkalmazni projektjei során.

## Előfeltételek

Mielőtt belevágnánk a kódba, győződjön meg arról, hogy rendelkezik a következőkkel:

-  Aspose.Words for .NET: Letöltheti innen[itt](https://releases.aspose.com/words/net/).
- Fejlesztői környezet: Bármely .NET-kompatibilis IDE (pl. Visual Studio).
- Alapvető C# ismerete: Ez az oktatóanyag feltételezi, hogy alapvető ismeretekkel rendelkezik a C# programozásról.

## Névterek importálása

Először is importáljuk a projektünkhöz szükséges névtereket. Ez biztosítja, hogy hozzáférhessünk az Aspose.Words által biztosított összes szükséges osztályhoz és metódushoz.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Most bontsuk le a példát több lépésre, hogy segítsen megérteni, hogyan módosítható a helyszíni frissítési kultúraforrás az Aspose.Words for .NET-ben.

## 1. lépés: Inicializálja a dokumentumot

 Az első lépés egy új példány létrehozása a`Document` osztály és a`DocumentBuilder`. Ez megalapozza a Word-dokumentum létrehozását és kezelését.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## 2. lépés: Adott nyelvi beállítású mezők beszúrása

Ezután mezőket kell beszúrnunk a dokumentumba. Ebben a példában két dátummezőt szúrunk be. A betűtípus területi beállítását németre (LocaleId = 1031) állítjuk be, hogy bemutassuk, hogyan befolyásolja a kultúra a dátumformátumot.

```csharp
builder.Font.LocaleId = 1031; // német
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## 3. lépés: Állítsa be a mezőfrissítési kultúraforrást

 A mezők frissítése során használt kultúra szabályozásához beállítottuk a`FieldUpdateCultureSource` tulajdona a`FieldOptions`osztály. Ez a tulajdonság határozza meg, hogy a kultúra a mezőkódból vagy a dokumentumból származik-e.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## 4. lépés: Hajtsa végre a körlevél funkciót

Most egy körözést kell végrehajtanunk, hogy a mezőket tényleges adatokkal töltsük fel. Ebben a példában a második dátummezőt (`Date2`) 2011. január 1-jéig.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## 5. lépés: Mentse el a dokumentumot

Végül elmentjük a dokumentumot a megadott könyvtárba. Ez a lépés befejezi a helyszíni frissítési kultúraforrás módosításának folyamatát.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Következtetés

És megvan! Sikeresen módosította a mezőfrissítési kultúra forrását az Aspose.Words for .NET-ben. Az alábbi lépések követésével biztosíthatja, hogy a Word-dokumentumok dátumokat és egyéb mezőértékeket jelenítsenek meg a megadott kultúrabeállításoknak megfelelően. Ez különösen akkor lehet hasznos, ha nemzetközi közönség számára készít dokumentumokat.

## GYIK

###  Mi a célja a beállításnak a`LocaleId`?
 A`LocaleId` megadja a szöveg kultúra beállításait, amelyek befolyásolják a dátumok és más terület-érzékeny adatok formázását.

### Használhatok a némettől eltérő területi beállítást?
 Igen, beállíthatja a`LocaleId`bármely érvényes területi azonosítóra. Például 1033 angol (Egyesült Államok) esetén.

###  Mi történik, ha nem állítom be a`FieldUpdateCultureSource` property?
Ha ez a tulajdonság nincs beállítva, akkor a mezők frissítésekor a dokumentum alapértelmezett kultúrabeállításait fogja használni.

### Lehetséges a mezők frissítése a dokumentum kultúrája alapján a mezőkód helyett?
 Igen, beállíthatod`FieldUpdateCultureSource` hogy`FieldUpdateCultureSource.Document` a dokumentum kultúra beállításainak használatához.

### Hogyan formázhatom a dátumokat eltérő mintára?
 Módosíthatja a dátumformátum mintáját a`InsertField` módszer módosításával a`\\@` kapcsoló értéke.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
