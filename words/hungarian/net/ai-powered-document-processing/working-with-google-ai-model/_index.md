---
"description": "Emeld magasabb szintre a dokumentumfeldolgozást az Aspose.Words for .NET és a Google AI segítségével, hogy könnyedén készíthess tömör összefoglalókat."
"linktitle": "A Google AI modelljével való munka"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "A Google AI modelljével való munka"
"url": "/hu/net/ai-powered-document-processing/working-with-google-ai-model/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# A Google AI modelljével való munka

## Bevezetés

Ebben a cikkben lépésről lépésre megvizsgáljuk, hogyan lehet dokumentumokat összefoglalni az Aspose.Words és a Google mesterséges intelligencia modelljeinek használatával. Akár egy hosszú jelentést szeretnél tömöríteni, akár több forrásból szeretnél információkat kinyerni, mi segítünk.

## Előfeltételek

Mielőtt belevágnánk a gyakorlati részbe, győződjünk meg róla, hogy készen állsz a sikerre. Íme, amire szükséged lesz:

1. C# és .NET alapismeretek: A programozási fogalmak ismerete segít jobban megérteni a példákat.
   
2. Aspose.Words .NET könyvtárhoz: Ez a hatékony könyvtár lehetővé teszi Word dokumentumok zökkenőmentes létrehozását és kezelését. [töltsd le itt](https://releases.aspose.com/words/net/).

3. API-kulcs a Google AI-modellhez: Az AI-modellek használatához API-kulcsra van szükség a hitelesítéshez. Tárolja biztonságosan a környezeti változókban.

4. Fejlesztői környezet: Győződjön meg arról, hogy rendelkezik egy működő .NET környezettel (Visual Studio vagy bármilyen más IDE).

5. Mintadokumentum: Az összefoglalás teszteléséhez minta Word-dokumentumokra lesz szükséged (pl. „Nagy dokumentum.docx”, „Dokumentum.docx”).

Most, hogy áttekintettük az alapokat, lássuk a kódot!

## Csomagok importálása

Az Aspose.Words használatához és a Google AI-modellek integrálásához importálnia kell a szükséges névtereket. Ezt így teheti meg:

```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

Most, hogy importálta a szükséges csomagokat, bontsuk le lépésről lépésre a dokumentumok összegzésének folyamatát.

## 1. lépés: A dokumentumkönyvtár beállítása

Mielőtt feldolgozhatnánk a dokumentumokat, meg kell adnunk, hogy hol találhatók a fájljaink. Ez a lépés elengedhetetlen ahhoz, hogy az Aspose.Words hozzáférhessen a dokumentumokhoz.

```csharp
// A dokumentumkönyvtárad
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Az Ön ArtifactsDir könyvtára
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```

Csere `"YOUR_DOCUMENT_DIRECTORY"` és `"YOUR_ARTIFACTS_DIRECTORY"` a rendszeren található tényleges elérési úttal, ahol a dokumentumok tárolva vannak. Ez szolgál majd alapként a dokumentumok olvasásához és mentéséhez.

## 2. lépés: A dokumentumok betöltése

Ezután be kell töltenünk azokat a dokumentumokat, amelyeket összegezni szeretnénk. Ebben az esetben két, korábban megadott dokumentumot fogunk betölteni.

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```

A `Document` Az Aspose.Words osztálya lehetővé teszi Word fájlok betöltését a memóriába. Győződjön meg arról, hogy a fájlnevek megegyeznek a könyvtárban található tényleges dokumentumokkal, különben „fájl nem található” hibákba ütközik!

## 3. lépés: Az API-kulcs lekérése

A mesterséges intelligencia modell használatához le kell kérned az API-kulcsodat. Ez szolgál hozzáférési engedélyként a Google mesterséges intelligencia szolgáltatásaihoz.

```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```

Ez a kódsor lekéri a környezeti változókban tárolt API-kulcsot. Biztonsági okokból ajánlott az olyan bizalmas információkat, mint az API-kulcsok, távol tartani a kódtól.

## 4. lépés: AI-modellpéldány létrehozása

Most itt az ideje létrehozni az AI-modell egy példányát. Itt kiválaszthatod, hogy melyik modellt szeretnéd használni – ebben a példában a GPT-4 Mini modellt választjuk.

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```

Ez a sor állítja be a dokumentumok összefoglalásához használni kívánt mesterséges intelligencia modellt. Feltétlenül tekintse meg a következőt: [a dokumentáció](https://reference.aspose.com/words/net/) a különböző modellekről és azok képességeiről szóló részletekért.

## 5. lépés: Egyetlen dokumentum összefoglalása

Koncentráljunk az első dokumentum összefoglalására. Itt választhatunk egy rövid összefoglalót.

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```

Ebben a lépésben a `Summarize` metódust az AI modellpéldányból az első dokumentum tömörítéséhez. Az összefoglaló hossza rövidre van állítva, de ezt az igényeidnek megfelelően testreszabhatod. Végül az összefoglalt dokumentum a műtermékek könyvtárába kerül mentésre.

## 6. lépés: Több dokumentum összefoglalása

Több dokumentumot szeretne egyszerre összefoglalni? Az Aspose.Words ezt is megkönnyíti!

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```

Itt hívjuk a `Summarize` metódust újra, de ezúttal dokumentumok tömbjével. Ez egy hosszú összefoglalót ad, amely mindkét fájl lényegét összefoglalja. Az eredmény, mint korábban, a megadott artifacts könyvtárba kerül mentésre.

## Következtetés

És íme! Sikeresen beállítottál egy környezetet dokumentumok összefoglalásához az Aspose.Words for .NET és a Google mesterséges intelligencia modelljeinek használatával. A dokumentumok betöltésétől a tömör összefoglalók elkészítéséig ezek a lépések leegyszerűsített megközelítést biztosítanak a nagy mennyiségű szöveg hatékony kezeléséhez.

## GYIK

### Mi az Aspose.Words?
Az Aspose.Words egy hatékony függvénykönyvtár, amellyel Word dokumentumokat hozhat létre, módosíthat és konvertálhat .NET használatával.

### Hogyan szerezhetek API-kulcsot a Google AI-hoz?
API-kulcsot általában úgy szerezhetsz be, hogy regisztrálsz a Google Cloudra és engedélyezed a szükséges API-szolgáltatásokat.

### Összefoglalhatok több dokumentumot egyszerre?
Igen! Ahogy bemutattuk, dokumentumok tömbjét adhatod át a summarization metódusnak.

### Milyen típusú összefoglalókat hozhatok létre?
Az igényeidnek megfelelően rövid, közepes és hosszú összefoglalók közül választhatsz.

### Hol találok további Aspose.Words forrásokat?
Nézd meg a [dokumentáció](https://reference.aspose.com/words/net/) további példákért és útmutatásért.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}