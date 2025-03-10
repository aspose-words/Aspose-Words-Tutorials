---
title: Munkavégzés AI modellel
linktitle: Munkavégzés AI modellel
second_title: Aspose.Words Document Processing API
description: Ismerje meg, hogyan használhatja az Aspose.Words for .NET-et dokumentumok AI segítségével történő összefoglalására. Egyszerű lépések a dokumentumkezelés javításához.
weight: 10
url: /hu/net/ai-powered-document-processing/working-with-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Munkavégzés AI modellel

## Bevezetés

Üdvözöljük az Aspose.Words for .NET magával ragadó világában! Ha valaha is magasabb szintre akarta emelni a dokumentumkezelést, akkor jó helyen jár. Képzelje el, hogy képes a nagy dokumentumok automatikus összegzésére mindössze néhány sornyi kóddal. Elképesztően hangzik, igaz? Ebben az útmutatóban mélyrehatóan foglalkozunk az Aspose.Words használatával dokumentumok összefoglalóinak létrehozásához olyan hatékony AI nyelvi modellek segítségével, mint az OpenAI GPT. Függetlenül attól, hogy Ön fejlesztő, aki az alkalmazásait szeretné továbbfejleszteni, vagy egy technológiai rajongó, aki szívesen tanul valami újat, ez az oktatóanyag mindenre kiterjed.

## Előfeltételek

Mielőtt felgyűrjük az ingujjunkat, és a kódoláshoz kezdenénk, néhány alapvető dolognak a helyén kell lennie:

1. Visual Studio telepítve: Győződjön meg arról, hogy a Visual Studio telepítve van a gépen. Ingyenesen letöltheti, ha még nem rendelkezik vele.
  
2. .NET-keretrendszer: Győződjön meg arról, hogy az Aspose.Words .NET-keretrendszer kompatibilis verzióját használja. Támogatja a .NET-keretrendszert és a .NET Core-t is.

3.  Aspose.Words for .NET: Le kell töltenie és telepítenie kell az Aspose.Words programot. Megkaphatod a legújabb verziót[itt](https://releases.aspose.com/words/net/).

4. API-kulcs AI-modellekhez: Az AI-összegzés használatához hozzá kell férnie egy AI-modellhez. Szerezze be API-kulcsát olyan platformokról, mint az OpenAI vagy a Google.

5. Alapvető C# ismerete: A C# programozás alapvető ismerete szükséges ahhoz, hogy a legtöbbet hozhassa ki ebből az oktatóanyagból.

Megvan minden? Döbbenetes! Ugorjunk a szórakoztató részre – a szükséges csomagjaink importálására.

## Csomagok importálása

Az Aspose.Words képességeinek kiaknázása és az AI modellekkel való munka érdekében a szükséges csomagok importálásával kezdjük. Íme, hogyan kell csinálni:

### Hozzon létre egy új projektet

Először indítsa el a Visual Studio-t, és hozzon létre egy új konzolalkalmazás-projektet.

1. Nyissa meg a Visual Studio-t.
2. Kattintson az „Új projekt létrehozása” gombra.
3. Válassza a „Konzolalkalmazás (.NET-keretrendszer)” vagy a „Konzolalkalmazás (.NET Core)” lehetőséget a beállításoktól függően.
4. Nevezze el a projektet, és adja meg a helyszínt.

### Telepítse az Aspose.Words és az AI modellcsomagokat

Az Aspose.Words használatához telepítenie kell a csomagot a NuGeten keresztül.

1. Kattintson a jobb gombbal a projektre a Solution Explorerben, és válassza a „NuGet-csomagok kezelése” lehetőséget.
2. Keresse meg az „Aspose.Words” kifejezést, és kattintson az „Install” gombra.
3. Ha konkrét mesterségesintelligencia-modell-csomagokat (például OpenAI-t) használ, győződjön meg arról, hogy azok is telepítve vannak.
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```
Gratulálunk! Ha elkészültek a csomagok, mélyedjünk el a megvalósításban.

## 1. lépés: Állítsa be a dokumentumkönyvtárakat

Kódunkban könyvtárakat határozunk meg, amelyekkel kezelhetjük a dokumentumaink tárolási helyét és a kimeneteinket. 

```csharp
// Az Ön dokumentumkönyvtára
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Az Ön ArtifactsDir könyvtára
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

-  Tessék, cserélje ki`YOUR_DOCUMENT_DIRECTORY` azzal a hellyel, ahol a dokumentumokat tárolják, és`YOUR_ARTIFACTS_DIRECTORY` hova szeretné menteni az összesített fájlokat.

## 2. lépés: Töltse be a dokumentumokat

Ezután betöltjük programunkba azokat a dokumentumokat, amelyeket össze akarunk foglalni. Ez olyan egyszerű, mint a pite! Íme, hogyan:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

- Állítsa be a mentett fájlneveket. A példa feltételezi, hogy két „Big document.docx” és „Document.docx” nevű dokumentuma van.

## 3. lépés: Inicializálja az AI-modellt

Következő lépésünk az AI modellel való kapcsolat létrehozása. Itt lép életbe a korábban kapott API-kulcs.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

- Ügyeljen arra, hogy az API-kulcs környezeti változóként legyen tárolva. Ez olyan, mintha biztonságban tartaná a titkos szószt!

## 4. lépés: Hozzon létre egy összefoglalót az első dokumentumhoz

Most készítsünk egy összefoglalót az első dokumentumunkhoz. Paramétereket állítunk be az összegzés hosszának meghatározásához is.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

- Ez a részlet összefoglalja az első dokumentumot, és a kimenetet a megadott műtermékek könyvtárába menti. Az összefoglaló hosszát bátran változtasd kedvedre!

## 5. lépés: Hozzon létre egy összegzést több dokumentumhoz

Kalandvágyónak érzi magát? Egyszerre több dokumentumot is összesíthet! Íme, hogyan kell csinálni:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

- Így egyszerre két dokumentumot foglal össze! Beszéljünk a hatékonyságról, igaz?

## Következtetés

És megvan! Az útmutató követésével elsajátította a dokumentumok összefoglalásának művészetét az Aspose.Words for .NET és a hatékony AI modellek használatával. Ez egy izgalmas funkció, amellyel rengeteg időt takaríthat meg, akár személyes használatra, akár professzionális alkalmazásokba integrálva. Most menjen előre, engedje szabadjára az automatizálás erejét, és nézze meg, hogyan szárnyal termelékenysége!

## GYIK

### Mi az Aspose.Words for .NET?
Az Aspose.Words for .NET egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára Word-dokumentumok programozott létrehozását, módosítását, konvertálását és renderelését.

### Hogyan szerezhetek API-kulcsot AI modellekhez?
API-kulcsot olyan AI-szolgáltatóktól szerezhet be, mint az OpenAI vagy a Google. Ne felejtsen el létrehozni egy fiókot, és kövesse az utasításaikat a kulcs létrehozásához.

### Használhatom az Aspose.Words-t más fájlformátumokhoz?
Igen! Az Aspose.Words különféle fájlformátumokat támogat, beleértve a DOCX-et, az RTF-et és a HTML-t, így a szöveges dokumentumokon túlmenően széles körű lehetőségeket kínál.

### Létezik az Aspose.Words ingyenes verziója?
Az Aspose ingyenes próbaverziót kínál, amely lehetővé teszi a funkciók tesztelését. Letöltheti az oldalukról.

### Hol találok további forrásokat az Aspose.Words számára?
 Ellenőrizheti a dokumentációt[itt](https://reference.aspose.com/words/net/) átfogó útmutatókért és betekintésekért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
