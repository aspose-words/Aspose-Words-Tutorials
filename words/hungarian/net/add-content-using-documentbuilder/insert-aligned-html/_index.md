---
title: Igazított HTML beszúrása Word dokumentumba az Aspose.Words for .NET használatával
weight: 210
limit:
description: Ismerje meg, hogyan szúrhat be HTML‑t meghatározott igazítással egy Word dokumentumba az Aspose.Words for .NET használatával.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Igazított HTML beszúrása Word dokumentumba az Aspose.Words for .NET használatával
Ez a bemutató azt mutatja be, hogyan használható az Aspose.Words for .NET DocumentBuilder-je HTML jelölőnyelv beágyazására egy Word dokumentumba, és annak igazításának szabályozására. Megtanulja, hogyan szúrja be a HTML‑t, hogyan állítsa be a bekezdés igazítását (balra, középre vagy jobbra), majd hogyan mentse el a kapott dokumentumot. A példa ideális fejlesztők számára, akiknek web‑stílusú formázást kell megőrizniük Word fájlok programozott generálása során.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: Használható a InsertHtml meglévő Word dokumentumba HTML hozzáadására egy új helyett?**
A: Igen. Hozzon létre egy Document objektumot a meglévő fájlból, helyezze a DocumentBuilder kurzort arra a pozícióra, ahová a HTML‑t be szeretné szúrni (például a builder.MoveToDocumentEnd() használatával), majd hívja meg a builder.InsertHtml‑t a jelölőnyelvvel.

**Q: Mely HTML attribútumokat veszi figyelembe az InsertHtml az igazításhoz?**
A: Az InsertHtml tiszteletben tartja a "align" attribútumot a blokk‑szintű elemeknél, mint a <p>, <div> és a címsor elemek, és a megfelelő bekezdés‑igazítást alkalmazza a kapott Word dokumentumban.

**Q: Mi történik, ha a HTML‑sztring nem támogatott címkéket vagy CSS‑t tartalmaz?**
A: A nem támogatott címkéket figyelmen kívül hagyja, és azok belső szövegét egyszerű szövegként szúrja be; az Aspose.Words által nem felismert beágyazott CSS‑stílusok is figyelmen kívül maradnak, így csak a támogatott HTML‑részhalmaz jelenik meg.

**Q: Szükséges bezárni a DocumentBuilder‑t a dokumentum mentése előtt?**
A: Nem szükséges kifejezett bezárás; a HTML beszúrása után közvetlenül meghívhatja a doc.Save‑t a kívánt fájlnévvel és formátummal, a builder erőforrásai automatikusan felszabadulnak.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}