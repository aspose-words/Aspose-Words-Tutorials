---
category: general
date: 2026-09-11
description: Diagramcímke szerkesztése útmutató, amely bemutatja, hogyan változtatható
  meg a diagramcímke pozíciója, testreszabható a diagram adatcímke, elrejthető a diagram
  kategórianév, és megjeleníthető a diagramcímke értéke az Aspose.Words segítségével.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- edit chart label tutorial
- change chart label position
- customize chart data label
- hide chart category name
- show chart label value
language: hu
lastmod: 2026-09-11
og_description: A diagramcímke szerkesztése útmutató bemutatja, hogyan változtathatja
  meg a diagramcímke pozícióját, testreszabhatja a diagram adatcímkéjét, elrejtheti
  a diagram kategórianévét, és megjelenítheti a diagramcímke értékét az Aspose.Words
  for .NET használatával.
og_image_alt: Screenshot of a Word document displaying a chart with customized data
  labels
og_title: Diagramcímke szerkesztése – Word diagramcímkék testreszabása C#‑ban
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Edit chart label tutorial showing how to change chart label position,
    customize chart data label, hide chart category name, and show chart label value
    with Aspose.Words.
  headline: Edit chart label tutorial – modify Word chart labels in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Chart manipulation
title: Diagramcímke szerkesztése útmutató – Word diagramcímkék módosítása C#-ban
url: /hu/net/programming-with-charts/edit-chart-label-tutorial-modify-word-chart-labels-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Diagramcímke szerkesztése – Word diagramcímkék módosítása C#-ban

Ha **edit chart label tutorial**-ra van szükséged egy Word dokumentumhoz, ez az útmutató pontosan megmutatja, hogyan változtathatod meg a diagramcímke pozícióját, testreszabhatod a diagram adatcímkét, elrejtheted a diagram kategórianévét, és megjelenítheted a diagramcímke értékét az Aspose.Words for .NET segítségével. Egy teljes, futtatható példát láthatsz, amelyet bármely C# projektbe beilleszthetsz.

A diagramcímkékkel való munka gyakori követelmény jelentések, számlák vagy műszerfalak programozott generálásakor. Ez az útmutató minden lépést lefed – a dokumentum betöltésétől a módosítások mentéséig – így kifinomult diagramokat hozhatsz létre manuális szerkesztés nélkül.

## Előfeltételek

* .NET 6.0 vagy újabb telepítve  
* Érvényes Aspose.Words for .NET licenc (vagy ideiglenes értékelő kulcs)  
* Visual Studio 2022 vagy bármely C#‑kompatibilis IDE  
* Egy Word fájl (`Chart.docx`), amely legalább egy diagramot tartalmaz  

A `Aspose.Words`-on kívül nincs szükség további NuGet csomagokra.

## 1. lépés: A projekt beállítása és a névterek importálása

Hozz létre egy új konzolos alkalmazást, és add hozzá az Aspose.Words NuGet csomagot:

```bash
dotnet new console -n ChartLabelEditor
cd ChartLabelEditor
dotnet add package Aspose.Words
```

`Program.cs`-t nyisd meg, és importáld a szükséges névtereket:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;
```

Ezek a névterek hozzáférést biztosítanak a `Document` osztályhoz a Word fájlok kezeléséhez, valamint a `Chart` osztályokhoz a diagramelemek manipulálásához.

## 2. lépés: A diagramot tartalmazó Word dokumentum betöltése

Az első végrehajtható sor betölti a forrásdokumentumot. Cseréld le a `YOUR_DIRECTORY`-t a tényleges útvonalra, ahol a `Chart.docx` található.

```csharp
// Load the Word document containing the chart
Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");
```

A dokumentum betöltése egy memóriában létező reprezentációt hoz létre, amelyet bejárhatsz és módosíthatsz.

## 3. lépés: Az első diagram lekérése a dokumentumból

A diagramok `NodeType.Chart` típusú gyermekcsomópontokként tárolódnak. A `GetChild` metódus a dokumentumfában keres, és visszaadja a szerkeszteni kívánt diagramot.

```csharp
// Retrieve the first chart object (index 0)
Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
```

Ha a dokumentum több diagramot tartalmaz, módosíthatod az indexet, hogy egy másikat célozz meg.

## 4. lépés: Az első sorozat adatcímkéjének elérése és testreszabása

Minden diagram sorozat rendelkezik egy `DataLabel` objektummal, amely szabályozza a címke megjelenését. Az alábbi kód bemutatja a négy kulcsfontosságú testreszabást, amely a tutorial másodlagos kulcsszavaihoz szükséges.

```csharp
// Access the data label of the first series (index 0)
ChartDataLabel label = chart.Series[0].DataLabel;

// Change chart label position – place the label in the center of each data point
label.Position = DataLabelPosition.Center;

// Customize chart data label – use a custom separator between label parts
label.Separator = "; ";

// Hide chart category name – the category text will not be shown
label.ShowCategoryName = false;

// Show chart label value – the numeric value of the point will be displayed
label.ShowValue = true;
```

**Miért fontosak ezek a beállítások**

* `DataLabelPosition.Center` a címkét az alapértelmezett ponton kívüli helyről a adatpont közepére helyezi, így a diagram könnyebben olvasható, ha a pontok szorosan vannak elhelyezve.  
* Egy egyedi `Separator` beállítása lehetővé teszi, hogy szabályozd, hogyan fűződnek össze a sorozat neve, az érték és egyéb részek.  
* A kategórianév (`ShowCategoryName = false`) elrejtése csökkenti a vizuális zsúfoltságot, ha a kategória már egyértelmű a tengelyből.  
* `ShowValue` engedélyezése biztosítja, hogy a tényleges adatérték látható legyen, ami gyakran szükséges pénzügyi vagy statisztikai jelentésekben.

## 5. lépés: A módosított dokumentum mentése

A címke tulajdonságainak módosítása után mentse el a változásokat egy új fájlba:

```csharp
// Save the updated document with customized chart labels
doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");
```

Az új fájl (`CustomLabelChart.docx`) ugyanazt a diagramelrendezést tartalmazza, de a megadott címke megjelenéssel.

## Teljes forráskód

Az alábbiakban a teljes, azonnal futtatható program található. Másold be a `Program.cs`-be, állítsd be a fájlútvonalakat, és futtasd a projektet.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

namespace ChartLabelEditor
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the Word document that contains a chart
            Document doc = new Document(@"YOUR_DIRECTORY\Chart.docx");

            // 2️⃣ Retrieve the first chart in the document
            Chart chart = (Chart)doc.GetChild(NodeType.Chart, 0, true);
            if (chart == null)
            {
                Console.WriteLine("No chart found in the document.");
                return;
            }

            // 3️⃣ Access the data label of the first series
            ChartDataLabel label = chart.Series[0].DataLabel;

            // 4️⃣ Customize the label appearance
            label.Position = DataLabelPosition.Center;   // change chart label position
            label.Separator = "; ";                      // customize chart data label
            label.ShowValue = true;                      // show chart label value
            label.ShowCategoryName = false;              // hide chart category name

            // 5️⃣ Save the modified document
            doc.Save(@"YOUR_DIRECTORY\CustomLabelChart.docx");

            Console.WriteLine("Chart label customization complete.");
        }
    }
}
```

### Várható eredmény

Nyisd meg a `CustomLabelChart.docx`-et a Microsoft Wordben. Látnod kell, hogy a diagram első sorozatának címkéje minden adatpont közepén van, csak a numerikus értéket jeleníti meg, és a „; ” karaktert használja elválasztóként. A kategórianév már nem jelenik meg az értékek mellett.

## Gyakori kérdések és szélhelyzetek

| Kérdés | Válasz |
|----------|--------|
| **Mi van, ha a dokumentum nem tartalmaz diagramot?** | A példa ellenőrzi, hogy a diagram `null`-e, és konzolüzenettel elegánsan kilép. |
| **Szerkeszthetek címkéket több sorozathoz?** | Igen. Iterálj a `chart.Series`-en, és alkalmazd ugyanazokat a `DataLabel` beállításokat minden `Series[i].DataLabel`-re. |
| **Hogyan változtathatom meg a címke betűtípusát?** | `label.Font` használatával (pl. `label.Font.Size = 10; label.Font.Color = Color.Blue;`). |
| **Támogatja a `DataLabelPosition.Center` minden diagramtípusnál?** | A legtöbb 2‑D diagramtípus támogatja. 3‑D diagramok esetén egyes pozíciókat a Word figyelmen kívül hagyhat. |
| **Szükség van licencre az Aspose.Words-hez?** | Az értékelő mód működik, de vízjelet ad. A licenc eltávolítja a vízjelet és feloldja a teljes funkcionalitást. |

## Profi tippek

* **Kötegelt feldolgozás:** Csomagold a betöltési és mentési logikát egy olyan metódusba, amely bemeneti és kimeneti útvonalakat fogad. Ez megkönnyíti tucatnyi dokumentum ciklusban történő feldolgozását.  
* **Teljesítmény:** Használj egyetlen `Document` példányt több diagram módosításakor ugyanabban a fájlban, hogy elkerüld az ismétlődő I/O műveleteket.  
* **Tesztelés:** Ellenőrizd a címke változásokat egy vizuális diff automatizálásával (pl. egy headless Word nézővel), ha a CI pipeline-ban kell az eredményt ellenőrizni.

## Következő lépések

Miután elsajátítottad a **edit chart label tutorial** alapjait, fontold meg a következőket:

* **Diagramcímke pozíciójának módosítása** más sorozatok vagy különböző diagramtípusok esetén  
* **Diagram adatcímke testreszabása** formázás, például számformátumok, betűszínek vagy háttérkitöltés  
* **Diagram kategórianév elrejtése** miközben a sorozat neve megmarad több sorozatos diagramoknál  
* **Diagramcímke érték megjelenítése** százalékos értékekkel együtt kördiagramoknál  

Ezek a témák mélyítik a Word diagramok esztétikájának irányítását, és felkészítenek a fejlett jelentéskészítési forgatókönyvekre.

---

*Boldog kódolást! Ha hasznosnak találtad ezt az útmutatót, oszd meg a csapattagokkal, vagy járulj hozzá fejlesztésekhez a GitHub-on.*

## Mit érdemes legközelebb megtanulni?

Az alábbi tutorialok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódpéldákat tartalmaz lépésről‑lépésre magyarázatokkal, hogy elsajátíthasd a további API funkciókat, és alternatív megvalósítási megközelítéseket fedezhess fel saját projektjeidben.

- [Diagram adatcímke testreszabása](/words/english/net/programming-with-charts/chart-data-label/)
- [Diagram adatcímke](/words/german/net/programming-with-charts/chart-data-label/)
- [Diagram adatcímke](/words/french/net/programming-with-charts/chart-data-label/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}