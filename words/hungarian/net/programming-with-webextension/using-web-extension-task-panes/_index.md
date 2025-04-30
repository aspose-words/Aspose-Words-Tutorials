---
"description": "Ebben a részletes, lépésről lépésre haladó oktatóanyagban megtudhatja, hogyan adhat hozzá és konfigurálhat webbővítmény-feladatpaneleket Word-dokumentumokban az Aspose.Words for .NET használatával."
"linktitle": "Webbővítmény feladatpanelek használata"
"second_title": "Aspose.Words dokumentumfeldolgozó API"
"title": "Webbővítmény feladatpanelek használata"
"url": "/hu/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Webbővítmény feladatpanelek használata

## Bevezetés

Üdvözlünk ebben a részletes oktatóanyagban, amely bemutatja a webbővítmény-feladatpanelek használatát Word-dokumentumokban az Aspose.Words for .NET segítségével. Ha valaha is szeretted volna interaktív feladatpanelekkel kiegészíteni Word-dokumentumaidat, jó helyen jársz. Ez az útmutató végigvezet a zökkenőmentes megvalósítás minden lépésén.

## Előfeltételek

Mielőtt belevágnánk, győződjünk meg róla, hogy minden megvan, amire szükséged van:

- Aspose.Words .NET-hez: Letöltheti [itt](https://releases.aspose.com/words/net/).
- .NET fejlesztői környezet: Visual Studio vagy bármilyen más IDE, amelyet előnyben részesítesz.
- C# alapismeretek: Ez segít majd követni a kódpéldákat.
- Aspose.Words licenc: Vásárolhatsz egyet [itt](https://purchase.aspose.com/buy) vagy szerezz ideiglenes jogosítványt [itt](https://purchase.aspose.com/temporary-license/).

## Névterek importálása

Mielőtt elkezdenénk a kódolást, győződjünk meg róla, hogy a következő névterek importálva vannak a projektünkben:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Lépésről lépésre útmutató

Most pedig bontsuk le a folyamatot könnyen követhető lépésekre.

### 1. lépés: A dokumentumkönyvtár beállítása

Először is be kell állítanunk a dokumentumok könyvtárának elérési útját. Ide lesz mentve a Word-dokumentum.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Csere `"YOUR DOCUMENT DIRECTORY"` a dokumentumok mappájának tényleges elérési útjával.

### 2. lépés: Új dokumentum létrehozása

Következő lépésként létrehozunk egy új Word dokumentumot az Aspose.Words használatával.

```csharp
Document doc = new Document();
```

Ez a sor inicializálja a(z) egy új példányát. `Document` osztály, amely egy Word dokumentumot jelöl.

### 3. lépés: Feladatpanel hozzáadása

Most hozzáadunk egy Feladatablakot a dokumentumunkhoz. A Feladatablakok további funkciók és eszközök biztosítására szolgálnak a Word-dokumentumokon belül.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

Itt létrehozunk egy újat `TaskPane` objektumot, és add hozzá a dokumentumhoz `WebExtensionTaskPanes` gyűjtemény.

### 4. lépés: A Feladatpanel konfigurálása

A Feladatpanel láthatóvá tételéhez és tulajdonságainak beállításához a következő kódot használjuk:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` beállítja, hogy hol jelenjen meg a Feladatpanel. Ebben az esetben a jobb oldalon található.
- `IsVisible` biztosítja, hogy a Feladatpanel látható legyen.
- `Width` beállítja a Feladatpanel szélességét.

### 5. lépés: Webbővítmény-referencia beállítása

Ezután beállítjuk a webbővítmény-referenciát, amely tartalmazza az azonosítót, a verziót, a tároló típusát és a tárolót.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` a webbővítmény egyedi azonosítója.
- `Version` meghatározza a kiterjesztés verzióját.
- `StoreType` az üzlet típusát jelzi (ebben az esetben OMEX).
- `Store` meghatározza az áruház nyelvi/kulturális kódját.

### 6. lépés: Tulajdonságok hozzáadása a webbővítményhez

Tulajdonságokat adhatsz hozzá a webbővítményedhez, hogy meghatározd annak viselkedését vagy tartalmát.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

Itt hozzáadunk egy nevű tulajdonságot `mailchimpCampaign`.

### 7. lépés: A webbővítmény összerendelése

Végül kötéseket adunk a webbővítményünkhöz. A kötések lehetővé teszik a bővítménynek a dokumentum adott részeihez való csatolását.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` a kötés neve.
- `WebExtensionBindingType.Text` azt jelzi, hogy a kötés szöveg típusú.
- `194740422` a dokumentum azon részének azonosítója, amelyhez a kiterjesztés kapcsolódik.

### 8. lépés: A dokumentum mentése

Miután mindent beállítottál, mentsd el a dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Ez a sor a megadott fájlnévvel menti a dokumentumot a megadott könyvtárba.

### 9. lépés: Feladatpanel információinak betöltése és megjelenítése

A feladatpanel információinak ellenőrzéséhez és megjelenítéséhez betöltjük a dokumentumot, és végighaladunk a feladatpaneleken.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Ez a kód betölti a dokumentumot, és kinyomtatja a konzolon az egyes feladatpanelek szolgáltatóját, verzióját és katalógusazonosítóját.

## Következtetés

És ennyi! Sikeresen hozzáadott és konfigurált egy webbővítmény-feladatpanelt egy Word-dokumentumban az Aspose.Words for .NET használatával. Ez a hatékony funkció jelentősen javíthatja Word-dokumentumait azáltal, hogy további funkciókat biztosít közvetlenül a dokumentumon belül. 

## GYIK

### Mi az a Feladatpanel a Wordben?
A Feladatpanel egy olyan felhasználói felületelem, amely további eszközöket és funkciókat biztosít a Word-dokumentumon belül, javítva a felhasználói interakciót és a termelékenységet.

### Testreszabhatom a Feladatpanel megjelenését?
Igen, testreszabhatja a Feladatpanel megjelenését olyan tulajdonságok beállításával, mint például `DockState`, `IsVisible`, és `Width`.

### Mik azok a webbővítmény-tulajdonságok?
A webbővítmény tulajdonságai olyan egyéni tulajdonságok, amelyeket hozzáadhat egy webbővítményhez, hogy meghatározza annak viselkedését vagy tartalmát.

### Hogyan köthetek egy webbővítményt a dokumentum egy részéhez?
A webbővítményt a dokumentum egy részéhez kötheti a következő használatával: `WebExtensionBinding` osztály, megadva a kötés típusát és a cél azonosítóját.

### Hol találok további információt az Aspose.Words for .NET-ről?
Részletes dokumentációt találhat [itt](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}