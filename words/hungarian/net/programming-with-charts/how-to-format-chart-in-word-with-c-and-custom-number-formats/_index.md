---
category: general
date: 2026-10-13
description: Hogyan formázzuk a diagramot a Wordben C#-al, egyedi számformátum, például
  pénznem alkalmazásával a diagram tengelyein. Lépésről lépésre kódrészlet is mellékelve.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to format chart
- apply custom number format
- custom number format word
- how to set chart
- change chart axis format
language: hu
lastmod: 2026-10-13
og_description: A C#-al Word diagram formázása lehetővé teszi egyedi számformátum
  alkalmazását a diagram tengelyein, biztosítva, hogy az értékek pénznemként, százalékban
  vagy bármilyen kívánt mintában jelenjenek meg. Kövesse a lépésről‑lépésre útmutatót.
og_image_alt: Word chart showing axis values formatted as currency after applying
  custom number format
og_title: Hogyan formázzuk a diagramot a Wordben C#‑val – egyéni számformátumok
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to format chart in Word with C# by applying a custom number format,
    such as currency, to chart axes. Step‑by‑step code example included.
  headline: How to format chart in Word with C# and custom number formats
  type: TechArticle
tags:
- Aspose.Words
- C#
- chart formatting
title: Hogyan formázzuk a diagramot a Wordben C#-val és egyéni számformátumokkal
url: /hu/net/programming-with-charts/how-to-format-chart-in-word-with-c-and-custom-number-formats/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Hogyan formázzuk a diagramot a Wordben C#-el és egyéni számformátumokkal

A diagram Wordben történő formázása C#-el gyakori követelmény, amikor professzionálisan kell adatokat bemutatni. Ez az útmutató megmutatja, hogyan alkalmazzunk egyéni számformátumot egy diagram tengelyére a **Aspose.Words for .NET** használatával, hogy az értékek pontosan úgy jelenjenek meg, ahogy elvárod.

Megtanulod, hogyan tölts be egy DOCX fájlt, keresd meg az első diagramot, olvasd ki a jelenlegi formátumot, majd állíts be egy új mintát, például pénznemet két tizedesjeggyel. Az útmutató azt is bemutatja, hogyan változtassuk meg a diagram tengelyformátumát további sorozatoknál, illetve hogyan állítsuk vissza a formátumot, ha szükséges.

## Előfeltételek

* .NET 6.0 vagy újabb telepítve  
* Visual Studio 2022 (vagy bármely .NET-et támogató IDE) projekt  
* A **Aspose.Words for .NET** NuGet csomag (`Aspose.Words`)  
* Egy Word dokumentum (`input.docx`), amely legalább egy diagramot tartalmaz

A csomagot a következő parancs segítségével adhatod hozzá:

```bash
dotnet add package Aspose.Words
```

## Hogyan formázzuk a diagramot Wordben az Aspose.Words használatával

Az alábbi teljes program bemutatja a **diagram formázásához** szükséges minden lépést. Mentsd a fájlt `Program.cs` néven, és futtasd a parancssorból vagy az IDE-ből.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Step 1: Load the Word document that contains the chart
        Document doc = new Document("input.docx");

        // Step 2: Retrieve the first chart shape from the document
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // Step 3: Access the X‑value collection of the first data series
        ChartXValueCollection xValues = chart.ChartData.Series[0].XValues;

        // Optional: Show the current number format code
        Console.WriteLine($"Current format code: {xValues.FormatCode}");

        // Step 4: Apply a custom number format (currency with two decimals)
        // The format string follows Excel/Word conventions.
        xValues.FormatCode = "\"$\"#,##0.00";

        // Step 5: Save the modified document
        doc.Save("output_formatted.docx");
        Console.WriteLine("Chart axis format applied and document saved as output_formatted.docx");
    }
}
```

### Az egyes lépések magyarázata

| Lépés | Miért fontos | Kulcs kód |
|------|----------------|----------|
| **A dokumentum betöltése** | Szükséged van egy `Document` objektumra a Word fájl kezeléséhez. | `new Document("input.docx")` |
| **A diagram lekérése** | `Chart` objektumok `Shape` csomópontként tárolódnak; az átkonvertálás lehetővé teszi a diagram-specifikus API-k használatát. | `(Chart)doc.GetChild(NodeType.Shape, 0, true)` |
| **X‑értékek elérése** | A tengely formázása az adat-sor értékgyűjteményére vonatkozik. | `chart.ChartData.Series[0].XValues` |
| **Aktuális formátum olvasása** | Az aktuális `FormatCode` ismerete segít eldönteni, hogy cserélni vagy kiegészíteni kell-e. | `xValues.FormatCode` |
| **Egyéni formátum beállítása** | A `FormatCode` tulajdonság bármilyen Excel‑kompatibilis mintát elfogad, lehetővé téve pénznemek, százalékok, dátumok stb. használatát. | `xValues.FormatCode = "\"$\"#,##0.00"` |
| **A dokumentum mentése** | A változtatások mentése visszaírja az új tengelyformátumot a DOCX fájlba. | `doc.Save("output_formatted.docx")` |

A program futtatása `output_formatted.docx`-et hoz létre. Nyisd meg Wordben, és a diagram X‑tengelye **$1,234.00**, **$2,345.00**, … értékekkel jelenik meg, a sima számok helyett.

## Egyéni számformátum alkalmazása a diagram tengelyére

Ha a **egyéni számformátumot** a Y‑tengelyre vagy további sorozatokra szeretnéd alkalmazni, a folyamat azonos – csak egy másik gyűjteményt célozz meg:

```csharp
// Apply format to Y‑values of the second series
ChartYValueCollection yValues = chart.ChartData.Series[1].YValues;
yValues.FormatCode = "0%"; // percentage format
```

> **Pro tipp:** Használj dupla idézőjeleket a formátum karakterláncban, hogy szó szerinti karaktereket ágyazz be (pl. `"$"` a pénznemhez). Az idézőjeleket a fenti módon kell escape‑elni.

## Egyéni számformátum a Wordben – a Word nyelvi beállításainak kezelése

A Word a dokumentum nyelvi beállításait veszi figyelembe a számformátumok értelmezésekor. Ha a dokumentum nem‑US nyelvi beállítást használ, előfordulhat, hogy a formátum karakterláncot módosítanod kell:

```csharp
// German locale – uses comma as decimal separator
xValues.FormatCode = "\"€\" #.##0,00";
```

A formátum tesztelése egy német nyelvi beállítású dokumentumban megerősíti, hogy az értékek **€ 1.234,00** formában jelennek meg.

## Hogyan állítsuk be a diagram tulajdonságait programozottan

A tengelyformázás mellett gyakran szeretnél **diagram** címeket, jelmagyarázatokat vagy adatcímkéket beállítani. Íme egy gyors kódrészlet, amely bemutatja, hogyan állíts be egy diagram címet a tengely formázása után:

```csharp
chart.Title.Text = "Sales by Quarter";
chart.Title.IsVisible = true;
```

Ennek a saját egyéni számformátummal való kombinálása egy teljesen kifinomult diagramot eredményez, amely készen áll a jelentéskészítésre.

## Diagram tengelyformátum dinamikus módosítása felhasználói bemenet alapján

Valós alkalmazásokban lehetővé teheted a felhasználók számára, hogy futásidőben válasszanak formátumot. Az alábbi metódus kapszulázza a formázási logikát:

```csharp
static void SetAxisFormat(Chart chart, int seriesIndex, string formatCode)
{
    var xVals = chart.ChartData.Series[seriesIndex].XValues;
    xVals.FormatCode = formatCode;
}
```

A `SetAxisFormat(chart, 0, "\"$\"#,##0.00")` hívással pénznemet állíthatsz be, vagy a `SetAxisFormat(chart, 0, "0%")`-tel százalékot. Ez a megközelítés tisztán tartja a fő kódot, és támogatja a jövőbeli bővítéseket.

## Szélsőséges esetek és gyakori buktatók

| Helyzet | Mire figyelj | Javasolt megoldás |
|-----------|-------------------|---------------|
| A dokumentum **nem tartalmaz diagramot** | `GetChild` `null`-t ad vissza, ami cast kivételt okoz. | Ellenőrizd a `null` értéket a cast előtt (lásd példát). |
| Több diagram is van ugyanabban a dokumentumban | A kód mindig az első diagramot veszi (`index 0`). | Iterálj a `doc.GetChildNodes(NodeType.Shape, true)`-en, és szűrd a `ShapeType.Chart` alapján. |
| Sorozat **X‑értékek nélkül** (pl. kördiagramok) | `XValues` elérése `ArgumentOutOfRangeException`-t dobhat. | Ellenőrizd, hogy a `Series[i].XValues` nem üres a formázás előtt. |
| Nyelvi beállítás eltérés | A pénznem szimbóluma helytelenül jelenhet meg. | Állítsd be explicit módon a `xValues.FormatCode`-ot a megfelelő nyelvi szimbólumokkal. |

## Várt kimenet

A mintaprogram futtatása után nyisd meg a **output_formatted.docx**-et. A diagram X‑tengelyének a kiválasztott egyéni formátumban kell megjelenítenie a számokat. A pénznem példához a tengelycímkék így néznek ki:

```
$1,000.00
$2,000.00
$3,000.00
```

Ha a százalékos formátumot alkalmaztad a Y‑értékekre, a Y‑tengely címkéi a következőképpen jelennek meg:

```
10%
20%
30%
```

## Összegzés

Ez az útmutató megmutatta, **hogyan formázzuk a diagramot** a Wordben C#-el, **egyéni számformátum alkalmazásával** a tengelyértékekre. Most már rendelkezel egy újrahasználható mintával a pénznem, százalék vagy bármely más numerikus minta beállításához, valamint útmutatással a nyelvi beállítások, több sorozat és dinamikus felhasználói bemenet kezeléséhez.

Ezután érdemes lehet **diagram** címeket, adatcímkéket beállítani, vagy akár a diagramot képként exportálni a `ChartRenderer` használatával. Ezek a témák közvetlenül az itt bemutatott koncepciókra épülnek, és segítenek teljesen automatizált jelentéskészítési megoldásokat létrehozni.

---

## Mit érdemes még megtanulni?

Az alábbi oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Számformátum a diagram tengelyén](/words/english/net/programming-with-charts/number-format-for-axis/)
- [Adatcímke számának formázása egy diagramon](/words/english/net/programming-with-charts/format-number-of-data-label/)
- [Másodlagos X‑tengely formázása és megjelenítési egységek ezrekre állítása Word vonaldiagramokban az Aspose.Words for .NET használatával](/words/english/net/programming-with-charts/format-secondary-axis/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}