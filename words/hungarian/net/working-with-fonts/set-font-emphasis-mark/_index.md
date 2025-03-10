---
title: Állítsa be a Font Emphasis Mark
linktitle: Állítsa be a Font Emphasis Mark
second_title: Aspose.Words Document Processing API
description: Ebből a részletes, lépésenkénti útmutatóból megtudhatja, hogyan állíthat be betűtípus-kiemeléseket a Word dokumentumokban az Aspose.Words for .NET használatával. Tökéletes .NET fejlesztőknek.
weight: 10
url: /hu/net/working-with-fonts/set-font-emphasis-mark/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Állítsa be a Font Emphasis Mark

## Bevezetés

mai oktatóanyagban azt mutatjuk be, hogyan állíthatunk be betűtípus-kiemeléseket egy Word-dokumentumban az Aspose.Words for .NET használatával. Akár konkrét szöveget szeretne egyedi jelöléssel aláhúzni, akár egyszerűen csak kiemelni szeretne bizonyos szavakat, ez az útmutató segít Önnek. Szóval, csatt, és kezdjük!

## Előfeltételek

Mielőtt belemerülnénk a finom részletekbe, győződjön meg arról, hogy bejelölte a következő előfeltételeket:

-  Aspose.Words for .NET Library: Győződjön meg arról, hogy telepítve van az Aspose.Words for .NET könyvtár. Letöltheti innen[itt](https://releases.aspose.com/words/net/).
- Fejlesztési környezet: működő fejlesztői környezet, például a Visual Studio.
- .NET-keretrendszer: Győződjön meg arról, hogy a .NET-keretrendszer telepítve van.

## Névterek importálása

Az Aspose.Words for .NET használatához importálnia kell a szükséges névtereket. Adja hozzá ezeket a kódfájl tetejéhez:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Most bontsuk le a folyamatot egyszerű lépésekre. Gondosan kövesse az egyes lépéseket a betűk kiemelésének beállításához a Word-dokumentumban.

## 1. lépés: Inicializálja a Dokumentumot és a DocumentBuilder-t

Először is inicializálnia kell egy új dokumentumot és egy DocumentBuildert. A DocumentBuilder osztály módszereket biztosít a szöveg és más elemek dokumentumba való beillesztésére.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inicializáljon egy új dokumentumot
Document document = new Document();

// Inicializálja a DocumentBuilder programot a dokumentummal
DocumentBuilder builder = new DocumentBuilder(document);
```

## 2. lépés: Állítsa be a Font Emphasis Mark

Ha a DocumentBuilder készen áll, beállíthatja a betűk kiemelését. Ebben a példában az "UnderSolidCircle" hangsúlyjelet fogjuk használni.

```csharp
// Állítsa be a betűk kiemelését
builder.Font.EmphasisMark = EmphasisMark.UnderSolidCircle;

// Írjon szöveget a hangsúlyjellel
builder.Write("Emphasis text");
builder.Writeln();
```

## 3. lépés: Törölje a formázást és adjon hozzá normál szöveget

A hangsúlyjel beállítása után érdemes lehet normál szöveget kiemelés nélkül hozzáadni. Ehhez törölnie kell a formázást.

```csharp
// Törölje a betűtípus formázását
builder.Font.ClearFormatting();

// Írj rendes szöveget
builder.Write("Simple text");
```

## 4. lépés: Mentse el a dokumentumot

Miután hozzáadta az összes szükséges szöveget és formázást, az utolsó lépés a dokumentum mentése. Adja meg az elérési utat és a fájlnevet, ahová menteni szeretné a dokumentumot.

```csharp
// Mentse el a dokumentumot
document.Save(dataDir + "WorkingWithFonts.SetFontEmphasisMark.docx");
```

## Következtetés

És megvan! A betűtípus-kiemelések beállítása Word-dokumentumban az Aspose.Words for .NET használatával ilyen egyszerű. Csak néhány sornyi kóddal kiemelheti a szöveget, és professzionális hatást varázsolhat dokumentumaiba. Ne habozzon kísérletezni a különböző hangsúlyjelekkel és stílusokkal, hogy megfeleljen igényeinek.

## GYIK

### Mik azok a betűk kiemelő jelei?

A betűk kiemelő jelei speciális szimbólumok, amelyeket a szöveghez adnak, hogy kiemeljék azt. Pontokat, köröket és egyéb díszítő jeleket tartalmazhatnak.

### Használhatok más kiemelő jeleket az Aspose.Words for .NET-hez?

 Igen, az Aspose.Words for .NET támogatja a különböző kiemeléseket. Különböző lehetőségeket fedezhet fel a[dokumentáció](https://reference.aspose.com/words/net/).

### Ingyenesen használható az Aspose.Words for .NET?

 Az Aspose.Words for .NET használatához licenc szükséges a teljes funkcionalitáshoz. Ingyenes próbaverziót kaphat[itt](https://releases.aspose.com/) vagy vásároljon licencet[itt](https://purchase.aspose.com/buy).

### Hogyan kaphatok támogatást az Aspose.Words for .NET-hez?

 Támogatást kaphat az Aspose közösségtől és a támogató csapattól, ha felkeresi őket[támogatási fórum](https://forum.aspose.com/c/words/8).

### Használhatom az Aspose.Words for .NET-et más .NET-keretrendszerekkel?

Igen, az Aspose.Words for .NET kompatibilis különféle .NET-keretrendszerekkel, beleértve a .NET Core-t és a .NET 5/6-ot.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
