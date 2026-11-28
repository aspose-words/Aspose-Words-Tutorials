---
category: general
date: 2026-10-13
description: Aspose.Words radiális diagram példa, amely bemutatja, hogyan lehet engedélyezni
  a graduációkat egy radiális diagramon C# és az Aspose.Words 24.9+ használatával.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- aspose.words radial chart example
- Aspose.Words chart API
- C# radial chart
- graduations visibility
- Aspose.Words version 24.9
- chart manipulation in .NET
language: hu
lastmod: 2026-10-13
og_description: Aspose.Words radiális diagram példája, amely bemutatja a fokozatok
  engedélyezését egy radiális diagramon C#-val és a legújabb 24.9+ verziójú könyvtárral.
og_image_alt: Aspose.Words radial chart example displaying graduations
og_title: Aspose.Words radiális diagram példa – osztások engedélyezése C#-ban
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  headline: 'Aspose.Words radial chart example: enable graduations in C#'
  type: TechArticle
- description: Aspose.Words radial chart example that shows how to enable graduations
    on a radial chart using C# and Aspose.Words 24.9+.
  name: 'Aspose.Words radial chart example: enable graduations in C#'
  steps:
  - name: Load the document that contains a radial chart
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing.Charts;'
  - name: Retrieve the first chart shape from the document
    text: '```csharp // NodeType.Shape selects shapes; the third argument (true) searches
      the whole tree. Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
      if (chart == null) { throw new InvalidOperationException("No chart shape found
      in the document."); } ```'
  - name: Enable graduations on the radial chart
    text: '```csharp // This property is available starting with Aspose.Words 24.9.
      chart.RadialChart.IsGraduationsVisible = true; ```'
  - name: Save the modified document
    text: '```csharp string outputPath = Path.Combine(Environment.CurrentDirectory,
      "RadialChart_Graduations.docx"); doc.Save(outputPath); Console.WriteLine($"Document
      saved to {outputPath}"); ```'
  - name: Expected output
    text: When you open `RadialChart_Graduations.docx` in Word, the radial chart will
      display tick marks (graduations) around the circular axis, similar to the screenshot
      shown earlier. The rest of the chart (data series, legend, title) remains unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Charts
title: 'Aspose.Words radiális diagram példa: osztások engedélyezése C#‑ban'
url: /hu/net/programming-with-charts/aspose-words-radial-chart-example-enable-graduations-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words radiális diagram példa: graduálások engedélyezése C#-ban

Ha **aspose.words radiális diagram példát** keresel, jó helyen jársz. Ez az útmutató végigvezet a pontos lépéseken, hogy hogyan kapcsoljuk be a graduálásokat egy radiális diagramhoz az Aspose.Words for .NET API segítségével.

A radiális diagramok hasznosak ciklikus adatok, például napszak‑metrikák vagy szezonális trendek megjelenítésére. Alapértelmezés szerint a graduálások (a kör alakú tengely körüli jelölések) rejtve vannak, ami nehezebbé teheti a diagram olvasását. Ezek engedélyezése egy egyetlen soros módosítás, de ismerned kell a megfelelő objektummodellt és azt a verziót, amely támogatja a funkciót.

Ebben az útmutatóban megtanulod, hogyan:

* Betölts egy Word dokumentumot, amely már tartalmaz radiális diagramot.  
* Hozzáférj a diagram alakzathoz az Aspose.Words diagram API-n keresztül.  
* Bekapcsold a **graduálások láthatóságát** (elérhető a **Aspose.Words 24.9-es verziójától**).  
* Elented a módosított dokumentumot és ellenőrzöd az eredményt.

A teljes, futtatható kód benne van, így egyszerűen bemásolhatod egy új konzolprojektbe, és azonnal láthatod a hatást.

![Aspose.Words radiális diagram példa graduálásokkal](https://example.com/images/radial-chart-graduations.png "Aspose.Words radiális diagram példa, amelyen a graduálások engedélyezve vannak")

## Előkövetelmények

| Követelmény | Miért fontos |
|-------------|---------------|
| .NET 6.0 vagy újabb | Az Aspose.Words for .NET 24.9+ a .NET Standard 2.0-t célozza, és .NET 6+ környezetben működik. |
| Aspose.Words for .NET **24.9** vagy újabb | Az `IsGraduationsVisible` tulajdonság a 24.9-es verzióban került bevezetésre. A régebbi kiadások `MissingMemberException`-t dobnak. |
| A Word dokumentum (`RadialChart.docx`) amely radiális diagramot tartalmaz | A példa egy meglévő diagramot módosít; egy új diagram létrehozása külön témakör. |
| C# IDE (Visual Studio, Rider, VS Code) | Bármely IDE, amely képes .NET projektek fordítására, működni fog. |
| NuGet csomag `Aspose.Words` | Telepítsd a `dotnet add package Aspose.Words --version 24.9.0` (vagy újabb) paranccsal. |

> **Pro tipp:** Ha nem tudsz 24.9-re frissíteni, továbbra is módosíthatod a diagram egyéb tulajdonságait, de a graduálások rejtve maradnak, mivel az API nem tette elérhetővé ezt a jelzőt.

## Aspose.Words radiális diagram példa – lépésről‑lépésre útmutató

A következő szakaszok a folyamatot önálló, könnyen követhető lépésekre bontják. Minden lépés tartalmazza a szükséges pontos kódot és egy rövid magyarázatot arra, hogy *miért* létezik a lépés.

### 1. lépés: Töltsd be a dokumentumot, amely radiális diagramot tartalmaz

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

// The file path can be absolute or relative to the executable directory.
string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");

// Load the Word document. Aspose.Words parses the entire file into a DOM tree.
Document doc = new Document(sourcePath);
```

**Miért fontos:**  
`Document` az **Aspose.Words diagram API** belépési pontja. Betölti a DOCX fájlt a memóriába, így hozzáférsz minden csomóponthoz – bekezdésekhez, táblázatokhoz és diagram alakzatokhoz. Ha a fájl nem található, a `Document` `FileNotFoundException`-t dob, amit a produkciós kódban kezelni kell.

### 2. lépés: Szerezd meg az első diagram alakzatot a dokumentumból

```csharp
// NodeType.Shape selects shapes; the third argument (true) searches the whole tree.
Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
if (chart == null)
{
    throw new InvalidOperationException("No chart shape found in the document.");
}
```

**Miért fontos:**  
A diagramok `Shape` csomópként vannak tárolva. A `GetChild` metódus `NodeType.Shape` paraméterrel bejárja a DOM-ot, és visszaadja az első egyező alakzatot. A `Chart` típusra való átkonvertálás hozzáférést biztosít a diagram-specifikus tulajdonságokhoz, például a `RadialChart`-hez. A null‑ellenőrzés biztosítja, hogy világos hibát kapj, ha a dokumentum nem tartalmaz diagramot, ami gyakori eset sablonok újrahasználatakor.

### 3. lépés: Engedélyezd a graduálásokat a radiális diagramon

```csharp
// This property is available starting with Aspose.Words 24.9.
chart.RadialChart.IsGraduationsVisible = true;
```

**Miért fontos:**  
`IsGraduationsVisible` szabályozza a kör alakú tengely körüli jelöléseket. Ha `true`-ra van állítva, a diagram megjeleníti a graduálásokat, javítva az olvashatóságot azok számára, akik pontosan szeretnék meghatározni az értékeket. A tulajdonság a `RadialChart` alatt található, amely a `Chart` alosztálya. Ha nem radiális diagramon (például oszlopdiagramon) próbálod használni, a `RadialChart` tulajdonság `null` lesz, ezért összetettebb esetekben előbb ellenőrizd a diagram típusát.

#### Nem radiális diagramok kezelése (opcionális)

```csharp
if (chart.ChartType == ChartType.Radial)
{
    chart.RadialChart.IsGraduationsVisible = true;
}
else
{
    Console.WriteLine("The chart is not radial; graduations are not applicable.");
}
```

Ez a védelem robusztusabbá teszi a kódot, ha a forrásdokumentum különböző diagramtípusokat tartalmazhat.

### 4. lépés: Mentsd el a módosított dokumentumot

```csharp
string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

**Miért fontos:**  
A `Save` hívás a memóriában lévő DOM-ot visszaírja egy .docx fájlba, ezzel elmentve a diagramon végrehajtott változtatást. A kimeneti fájl megnyitható a Microsoft Word, a LibreOffice vagy bármely DOCX‑t támogató megjelenítővel. Láthatod a radiális diagramot látható graduálásokkal.

## Teljes, futtatható példa

Az alábbiakban a teljes program látható, amelyet beilleszthetsz egy .NET konzolprojekt `Program.cs` fájljába.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // -----------------------------------------------------------------
        // 1. Load the source document that contains a radial chart.
        // -----------------------------------------------------------------
        string sourcePath = Path.Combine(Environment.CurrentDirectory, "RadialChart.docx");
        Document doc = new Document(sourcePath);

        // -----------------------------------------------------------------
        // 2. Locate the first chart shape in the document.
        // -----------------------------------------------------------------
        Chart chart = (Chart)doc.GetChild(NodeType.Shape, 0, true);
        if (chart == null)
        {
            Console.WriteLine("No chart found in the document.");
            return;
        }

        // -----------------------------------------------------------------
        // 3. Enable graduations (tick marks) on the radial chart.
        // -----------------------------------------------------------------
        // Ensure the chart is radial before accessing RadialChart.
        if (chart.ChartType == ChartType.Radial && chart.RadialChart != null)
        {
            chart.RadialChart.IsGraduationsVisible = true;
        }
        else
        {
            Console.WriteLine("The chart is not a radial chart; cannot set graduations.");
            return;
        }

        // -----------------------------------------------------------------
        // 4. Save the updated document.
        // -----------------------------------------------------------------
        string outputPath = Path.Combine(Environment.CurrentDirectory, "RadialChart_Graduations.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Radial chart with graduations saved to: {outputPath}");
    }
}
```

### Várható kimenet

Amikor megnyitod a `RadialChart_Graduations.docx` fájlt Wordben, a radiális diagram a kör alakú tengely körül jelöléseket (graduálásokat) fog mutatni, hasonlóan a korábban bemutatott képernyőképen. A diagram többi része (adat sorozatok, jelmagyarázat, cím) változatlan marad.

## Gyakori változatok és szélhelyzetek

| Helyzet | Megoldás |
|-----------|----------|
| **Régebbi Aspose.Words verzió (< 24.9)** | Frissíts a legújabb NuGet csomagra. Az `IsGraduationsVisible` tulajdonság a korábbi kiadásokban nem létezik. |
| **Több diagram ugyanabban a dokumentumban** | Használd a `doc.GetChild(NodeType.Shape, index, true)` metódust a megfelelő `index` értékkel, vagy iterálj a `doc.GetChildNodes(NodeType.Shape, true)` elemein, és szűrd a `ChartType.Radial` alapján. |
| **Programozottan létrehozott diagram** | Használd a `DocumentBuilder`-t diagram beszúrásához, majd állítsd be a `RadialChart.IsGraduationsVisible` értékét a |

## Mit érdemes legközelebb megtanulni?

A következő oktatóanyagok szorosan kapcsolódó témákat fednek le, amelyek a jelen útmutatóban bemutatott technikákra épülnek. Minden forrás teljes, működő kódrészleteket tartalmaz lépésről‑lépésre magyarázatokkal, hogy segítsenek elsajátítani további API funkciókat és alternatív megvalósítási megközelítéseket a saját projektjeidben.

- [Diagram sorozat adatainak frissítése Word dokumentumban az Aspose.Words for .NET használatával](/words/english/net/programming-with-charts/modify-chart-series/)
- [Diagram sorozat eltávolítása Word dokumentumból az Aspose.Words for .NET használatával](/words/english/net/programming-with-charts/remove-chart-series/)
- [Ábrázolási terület keretének elrejtése oszlopdiagramon az Aspose.Words for .NET segítségével](/words/english/net/programming-with-charts/hide-plot-border/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}