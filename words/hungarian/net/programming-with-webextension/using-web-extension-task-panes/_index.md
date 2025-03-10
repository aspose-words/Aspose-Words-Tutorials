---
title: Webbővítmény munkaablak használata
linktitle: Webbővítmény munkaablak használata
second_title: Aspose.Words Document Processing API
description: Ebből a részletes, lépésenkénti oktatóanyagból megtudhatja, hogyan adhat hozzá és konfigurálhat webbővítmény munkaablakokat Word dokumentumokhoz az Aspose.Words for .NET használatával.
weight: 10
url: /hu/net/programming-with-webextension/using-web-extension-task-panes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Webbővítmény munkaablak használata

## Bevezetés

Üdvözöljük ebben a részletes oktatóanyagban a webbővítmény munkaablakok használatáról Word-dokumentumban az Aspose.Words for .NET használatával. Ha valaha is szerette volna Word-dokumentumait interaktív munkaablakokkal bővíteni, akkor jó helyen jár. Ez az útmutató végigvezeti Önt minden lépésen, hogy ezt zökkenőmentesen elérje.

## Előfeltételek

Mielőtt belemerülnénk, győződjünk meg arról, hogy mindent megvan, amire szüksége van:

-  Aspose.Words for .NET: Letöltheti[itt](https://releases.aspose.com/words/net/).
- .NET fejlesztői környezet: Visual Studio vagy bármely más IDE, amit szeretne.
- Alapvető C# ismerete: Ez segít a kódpéldák követésében.
-  Licenc az Aspose.Words számára: Vásárolhat egyet[itt](https://purchase.aspose.com/buy) vagy ideiglenes engedélyt szerezni[itt](https://purchase.aspose.com/temporary-license/).

## Névterek importálása

kódolás megkezdése előtt győződjön meg arról, hogy a következő névtereket importálta a projektbe:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Útmutató lépésről lépésre

Most bontsuk le a folyamatot könnyen követhető lépésekre.

### 1. lépés: A dokumentumkönyvtár beállítása

Először is be kell állítanunk a dokumentumkönyvtár elérési útját. Ide kerül mentésre a Word-dokumentum.

```csharp
// A dokumentumok könyvtárának elérési útja.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Cserélje ki`"YOUR DOCUMENT DIRECTORY"` a dokumentummappa tényleges elérési útjával.

### 2. lépés: Új dokumentum létrehozása

Ezután létrehozunk egy új Word-dokumentumot az Aspose.Words használatával.

```csharp
Document doc = new Document();
```

 Ez a sor inicializálja a`Document` osztály, amely egy Word dokumentumot képvisel.

### 3. lépés: Feladatablak hozzáadása

Most hozzáadunk egy munkaablakot a dokumentumunkhoz. A munkaablakok hasznosak további funkciók és eszközök biztosításához a Word-dokumentumokban.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

 Itt létrehozunk egy újat`TaskPane` objektumot, és adja hozzá a dokumentumhoz`WebExtensionTaskPanes` gyűjtemény.

### 4. lépés: A munkaablak konfigurálása

A munkaablak láthatóvá tételéhez és tulajdonságainak beállításához a következő kódot használjuk:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` beállítja, hogy hol jelenjen meg a Feladatablak. Ebben az esetben a jobb oldalon van.
- `IsVisible` biztosítja a munkaablak láthatóságát.
- `Width` beállítja a munkaablak szélességét.

### 5. lépés: A webbővítmény referencia beállítása

Ezután beállítjuk a Web Extension Reference-t, amely tartalmazza az azonosítót, a verziót, az áruház típusát és az áruházat.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` webbővítmény egyedi azonosítója.
- `Version` megadja a kiterjesztés verzióját.
- `StoreType` az üzlet típusát jelzi (jelen esetben OMEX).
- `Store` megadja az üzlet nyelvi/kultúra kódját.

### 6. lépés: Tulajdonságok hozzáadása a webbővítményhez

Tulajdonságokat adhat a webbővítményhez, hogy meghatározza annak viselkedését vagy tartalmát.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

 Itt adunk hozzá egy nevű tulajdonságot`mailchimpCampaign`.

### 7. lépés: A webbővítmény összerendelése

Végül kötéseket adunk a webbővítményünkhöz. A kötések lehetővé teszik, hogy a kiterjesztést a dokumentum meghatározott részeihez kapcsolja.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` a kötés neve.
- `WebExtensionBindingType.Text` azt jelzi, hogy a kötés szöveges típusú.
- `194740422` a dokumentum azon részének azonosítója, amelyhez a kiterjesztés hozzá van kötve.

### 8. lépés: A dokumentum mentése

Miután mindent beállított, mentse el a dokumentumot.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Ez a sor menti a dokumentumot a megadott könyvtárba a megadott fájlnévvel.

### 9. lépés: A munkaablak információinak betöltése és megjelenítése

munkaablak információinak ellenőrzéséhez és megjelenítéséhez betöltjük a dokumentumot, és ismételjük a munkaablakokon.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Ez a kód betölti a dokumentumot, és kinyomtatja a konzol minden egyes munkaablakának szolgáltatóját, verzióját és katalógusazonosítóját.

## Következtetés

És ennyi! Sikeresen hozzáadott és konfigurált egy webbővítmény munkaablakot egy Word-dokumentumban az Aspose.Words for .NET használatával. Ez a hatékony funkció jelentősen javíthatja Word-dokumentumait, mivel további funkciókat biztosít közvetlenül a dokumentumon belül. 

## GYIK

### Mi az a munkaablak a Wordben?
A munkaablak olyan felületelem, amely további eszközöket és funkciókat biztosít a Word-dokumentumban, javítva a felhasználói interakciót és a termelékenységet.

### Testreszabhatom a munkaablak megjelenését?
 Igen, testreszabhatja a munkaablak megjelenését a tulajdonságok beállításával, mint pl`DockState`, `IsVisible` , és`Width`.

### Mik azok a webbővítmény tulajdonságai?
A webbővítmény tulajdonságai egyéni tulajdonságok, amelyeket hozzáadhat egy webbővítményhez, hogy meghatározza annak viselkedését vagy tartalmát.

### Hogyan köthetek webbővítményt a dokumentum egy részéhez?
 A webbővítményt a dokumentum egy részéhez kötheti a`WebExtensionBinding` osztályban, megadva a kötés típusát és a célazonosítót.

### Hol találhatok további információt az Aspose.Words for .NET-ről?
 Részletes dokumentációt találhat[itt](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
