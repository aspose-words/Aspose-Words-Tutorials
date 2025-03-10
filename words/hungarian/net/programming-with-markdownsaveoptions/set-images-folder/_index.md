---
title: Képek mappa beállítása
linktitle: Képek mappa beállítása
second_title: Aspose.Words Document Processing API
description: Konvertálja a Word dokumentumokat Markdown formátumba megfelelő táblázatigazítással az Aspose.Words for .NET segítségével. Kövesse részletes útmutatónkat a tökéletes eredmény érdekében.
weight: 10
url: /hu/net/programming-with-markdownsaveoptions/set-images-folder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Képek mappa beállítása

## Bevezetés

Szerette már Word-dokumentumát Markdown formátumba exportálni, miközben gondoskodik arról, hogy a táblázatok és a tartalom tökéletesen illeszkedjenek egymáshoz? Az Aspose.Words for .NET a megfelelő megoldás erre a feladatra. Ebben a cikkben végigvezetjük az Aspose.Words beállításán, a dokumentum előkészítésén, valamint a megfelelő táblázattartalom-igazítás mellett a Markdownba exportálásán. Az egyes lépéseket lebontjuk, hogy könnyebben követhető és érthető legyen. Tehát merüljünk bele, és alakítsa át Word-dokumentumait gyönyörűen igazított Markdown-fájlokká!

## Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy rendelkezik a következőkkel:

-  Aspose.Words for .NET: Letöltheti[itt](https://releases.aspose.com/words/net/).
-  Érvényes licenc: Szerezzen ingyenes próbaverziót[itt](https://releases.aspose.com/) vagy ideiglenes engedélyt[itt](https://purchase.aspose.com/temporary-license/).
- Visual Studio: Vagy bármely más IDE, amely támogatja a .NET fejlesztést.
- C# alapismeretek: C# programozási nyelv ismerete.

## Névterek importálása

A kezdéshez importálnia kell a szükséges névtereket a C# projektbe. Ezek a névterek lehetővé teszik az Aspose.Words funkció elérését.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
using System.IO;
```

## 1. lépés: Állítsa be projektjét

Először is állítsa be .NET-projektjét az IDE-ben. Hozzon létre egy új konzolalkalmazást, és adjon hozzá egy hivatkozást az Aspose.Words for .NET-hez.

### 1.1 Hozzon létre egy új projektet

Nyissa meg a Visual Studio-t, és hozzon létre egy új konzolalkalmazás-projektet. Nevezd el "MarkdownExporter"-nek vagy valami hasonlónak.

### 1.2 Az Aspose.Words Reference hozzáadása

 Az Aspose.Words projekthez való hozzáadásához letöltheti a DLL-t a következő webhelyről[Aspose honlapja](https://releases.aspose.com/words/net/) és adja hozzá manuálisan, vagy használja a NuGet Package Managert:

```bash
Install-Package Aspose.Words
```

## 2. lépés: Írja be az exportálandó kódot Markdownként

Most írjuk meg a Word-dokumentum olvasásához szükséges kódot, és mentsük el Markdown fájlként, megfelelő táblázatigazítással.

### 2.1 Határozza meg a dokumentum elérési útját

Állítsa be a Word-dokumentum elérési útját és azt a mappát, ahová a képeket menteni szeretné.

```csharp
string dataDir = "YOUR_DOCUMENT_DIRECTORY";
```

### 2.2 Töltse be a dokumentumot

Töltse be a Word-dokumentumot az Aspose.Words használatával.

```csharp
Document doc = new Document(dataDir + "Image bullet points.docx");
```

### 2.3 A Markdown mentési beállításainak konfigurálása

 Konfigurálja a`MarkdownSaveOptions` a képek tárolási helyének megadásához.

```csharp
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    ImagesFolder = dataDir + "Images"
};
```

### 2.4 Mentse el a dokumentumot Markdown néven

 Használja a`MemoryStream` a dokumentum Markdown formátumban történő mentéséhez.

```csharp
using (MemoryStream stream = new MemoryStream())
{
    doc.Save(stream, saveOptions);
}
```

## Következtetés

A Word-dokumentum exportálása a Markdownba a táblázattartalom-igazítással az Aspose.Words for .NET használatával egyszerű, ha követi ezeket a lépéseket. Néhány sornyi kóddal automatizálhatja a konverziós folyamatot, és gondoskodhat arról, hogy a tartalom megfelelően legyen formázva. Mostantól könnyedén megoszthatja dokumentumait Markdown formátumban, tudva, hogy nagyszerűen fognak kinézni és megőrzik szerkezetüket.

## GYIK

### Használhatom az Aspose.Words for .NET-et más programozási nyelvekkel?

Igen, az Aspose.Words for .NET használható bármely .NET-kompatibilis nyelvvel, például VB.NET-tel, F#-mal stb.

### Hogyan szerezhetek ideiglenes licencet az Aspose.Words számára?

Kaphat ideiglenes engedélyt[itt](https://purchase.aspose.com/temporary-license/).

### Milyen típusú dokumentumokat konvertálhatok Markdown-ba?

Különféle Word-dokumentumokat konvertálhat, beleértve a .doc, .docx, .rtf és egyebeket.

### Vannak korlátozások az Aspose.Words próbaverziójában?

 próbaverziónak vannak korlátozásai, például vízjelek a kimeneti fájlokban. Ingyenes próbaverziót kaphat[itt](https://releases.aspose.com/).

### Hol találok további példákat és dokumentációt az Aspose.Words-hez?

 Részletes dokumentációt és példákat találhat a[Aspose honlapja](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
