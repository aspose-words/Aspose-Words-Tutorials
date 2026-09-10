---
title: Vízszintes vonal alakzat beszúrása Word-dokumentumba az Aspose.Words for .NET használatával
weight: 110
limit:
description: Tanulja meg, hogyan adhat hozzá egy vízszintes vonal alakzatot egy Word-dokumentumhoz az Aspose.Words for .NET és a DocumentBuilder használatával.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vízszintes vonal alakzat beszúrása Word-dokumentumba az Aspose.Words for .NET használatával
Ebben a bemutatóban megtanulja, hogyan szúrhat be programozott módon egy vízszintes vonal alakzatot egy Word-dokumentumba az Aspose.Words for .NET segítségével. A Document és a DocumentBuilder osztályok használatával létrehozunk egy új dokumentumot, hozzáadunk egy szövegbekezdést, majd a kívánt helyre elhelyezünk egy vízszintes vonal alakzatot. A vízszintes vonal vizuális elválasztót biztosít, amely hasznos lehet szakaszszélekhez vagy vizuális hangsúlyozáshoz.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: A `builder.InsertHorizontalRule()` pontosan hová helyezi a vonalat a dokumentumban?**
A: `InsertHorizontalRule` a `DocumentBuilder` aktuális kurzorpozíciójába szúr be egy vízszintes vonal alakzatot; ha külön sorban szeretné, hívja meg a `builder.Writeln()`-t a beszúrás előtt.

**Q: Módosíthatom a beszúrt vízszintes vonal vastagságát, színét vagy szélességét?**
A: `InsertHorizontalRule` egy alapértelmezett stílusú vonalat ad hozzá, és nem teszi elérhetővé a formázási beállításokat; ezeknek a tulajdonságoknak a testreszabásához manuálisan kell beszúrni egy `Shape`-et (például `builder.InsertShape(ShapeType.HorizontalLine)`) és aztán beállítani a `LineFormat` tulajdonságait.

**Q: Lehetőség van több vízszintes vonal hozzáadására ugyanabban a dokumentumban?**
A: Igen — egyszerűen hívja meg a `builder.InsertHorizontalRule()`-t minden alkalommal, amikor új vonalat szeretne; minden hívás egy külön alakzatot hoz létre a builder aktuális helyén.

**Q: Látható lesz a vízszintes vonal, amikor a mentett .docx fájlt megnyitja a Microsoft Word?**
A: Természetesen; a vonal alakzatként van mentve a .docx fájlban, így a Word pontosan úgy jeleníti meg, ahogy a generált dokumentumban látható.

**Q: Mi történik, ha a `dataDir` mappa nem létezik, mielőtt meghívná a `doc.Save(...)`-t?**
A: A `doc.Save` `DirectoryNotFoundException`-t dob; győződjön meg arról, hogy a célkönyvtár létezik, vagy hozza létre programból a mentés előtt.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}