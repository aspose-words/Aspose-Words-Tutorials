---
title: Használja a célgépről származó betűtípust
linktitle: Használja a célgépről származó betűtípust
second_title: Aspose.Words Document Processing API
description: Az Aspose.Words for .NET segítségével megtudhatja, hogyan használhatja a célgép betűtípusait Word-dokumentumaiban. Kövesse lépésenkénti útmutatónkat a zökkenőmentes betűtípus-integráció érdekében.
weight: 10
url: /hu/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Használja a célgépről származó betűtípust

## Bevezetés

Készen állsz, hogy belemerülj az Aspose.Words for .NET lenyűgöző világába? Kapcsold be, mert mindjárt elvezetünk egy utazásra a betűtípusok varázslatos birodalmában. Ma arra összpontosítunk, hogyan használjunk betűtípusokat a célgépről a Word dokumentumokkal való munka során. Ez a remek funkció biztosítja, hogy a dokumentum pontosan úgy nézzen ki, ahogyan szeretné, függetlenül attól, hogy hol tekintik meg. Kezdjük is!

## Előfeltételek

Mielőtt belevágnánk a finom részletekbe, győződjünk meg arról, hogy mindennel rendelkezünk, amire szükségünk van:

1.  Aspose.Words for .NET: Győződjön meg arról, hogy telepítve van az Aspose.Words for .NET könyvtár. Ha még nem tette meg, letöltheti[itt](https://releases.aspose.com/words/net/).
2. Fejlesztői környezet: Be kell állítania egy .NET fejlesztői környezetet, például a Visual Studio-t.
3. Dolgozandó dokumentum: Készítsen Word-dokumentumot tesztelésre. Egy "Lonópontok alternatív fonttal.docx" nevű dokumentumot fogunk használni.

Most, hogy áttekintettük az alapokat, merüljünk el a kódban!

## Névterek importálása

Először is importálnunk kell a szükséges névtereket. Ez a projektünk gerince, amely összeköti az összes pontot.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## 1. lépés: Töltse be a Word-dokumentumot

 Oktatóanyagunk első lépése a Word dokumentum betöltése. Itt kezdődik minden. Használjuk a`Document` osztályt az Aspose.Words könyvtárból ennek eléréséhez.

### 1.1. lépés: Határozza meg a dokumentum elérési útját

Kezdjük a dokumentumkönyvtár elérési útjának meghatározásával. Itt található a Word-dokumentum.

```csharp
// A dokumentumkönyvtár elérési útja
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

### 1.2. lépés: Töltse be a dokumentumot

 Most betöltjük a dokumentumot a`Document` osztály.

```csharp
// Töltse be a Word dokumentumot
Document doc = new Document(dataDir + "Bullet points with alternative font.docx");
```

## 2. lépés: Konfigurálja a mentési beállításokat

Ezután konfigurálnunk kell a mentési beállításokat. Ez a lépés kulcsfontosságú, mivel biztosítja, hogy a dokumentumban használt betűtípusok a célgéptől származzanak.

 Létrehozunk egy példányt`HtmlFixedSaveOptions` és állítsa be a`UseTargetMachineFonts`tulajdonát`true`.

```csharp
// Konfigurálja a biztonsági mentési beállításokat a „Betűtípusok használata a célgépről” funkcióval
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions
{
    UseTargetMachineFonts = true
};
```

## 3. lépés: Mentse el a dokumentumot

Végül a dokumentumot rögzített HTML fájlként mentjük el. Itt történik a varázslat!

 Használjuk a`Save` módszerrel mentheti a dokumentumot a konfigurált mentési beállításokkal.

```csharp
// Konvertálja a dokumentumot rögzített HTML formátumba
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html", saveOptions);
```

## 4. lépés: Ellenőrizze a kimenetet

Végül, de nem utolsósorban, mindig jó ötlet ellenőrizni a kimenetet. Nyissa meg a mentett HTML-fájlt, és ellenőrizze, hogy a betűtípusok megfelelően vannak-e alkalmazva a célgépről.

Keresse meg azt a könyvtárat, ahová a HTML-fájlt mentette, és nyissa meg egy webböngészőben.

```csharp
// Ellenőrizze a kimenetet a HTML-fájl megnyitásával
System.Diagnostics.Process.Start(dataDir + "WorkingWithHtmlFixedSaveOptions.UseFontFromTargetMachine.html");
```

És megvan! Sikeresen használta a célgép betűtípusait a Word-dokumentumban az Aspose.Words for .NET használatával.

## Következtetés

A célgépről származó betűtípusok használatával a Word-dokumentumok konzisztensnek és professzionálisnak tűnnek, függetlenül attól, hogy hol tekintik meg őket. Az Aspose.Words for .NET ezt a folyamatot egyszerűvé és hatékonysá teszi. Az oktatóanyag követésével megtanulta, hogyan tölthet be egy dokumentumot, konfigurálhatja a mentési beállításokat, és hogyan mentheti a dokumentumot a kívánt betűtípus-beállításokkal. Boldog kódolást!

## GYIK

### Használhatom ezt a módszert más dokumentumformátumokkal?
Igen, az Aspose.Words for .NET különféle dokumentumformátumokat támogat, és a különböző formátumokhoz hasonló mentési beállításokat konfigurálhat.

### Mi van, ha a célgép nem rendelkezik a szükséges betűtípusokkal?
Ha a célgép nem rendelkezik a szükséges betűtípusokkal, előfordulhat, hogy a dokumentum nem a kívánt módon jelenik meg. Mindig célszerű betűtípusokat beágyazni, ha szükséges.

### Hogyan ágyazhatok be betűtípusokat egy dokumentumba?
 A betűtípusok beágyazása a`FontSettings` osztály az Aspose.Words for .NET-ben. Lásd a[dokumentáció](https://reference.aspose.com/words/net/) további részletekért.

### Van mód a dokumentum előnézetére mentés előtt?
 Igen, használhatod a`DocumentRenderer` osztályt a dokumentum előnézetének megtekintéséhez a mentés előtt. Nézze meg az Aspose.Words for .NET-et[dokumentáció](https://reference.aspose.com/words/net/) további információkért.

### Testreszabhatom a HTML kimenetet?
 Teljesen! A`HtmlFixedSaveOptions` osztály különféle tulajdonságokat biztosít a HTML-kimenet testreszabásához. Fedezze fel a[dokumentáció](https://reference.aspose.com/words/net/) az összes elérhető opcióhoz.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
