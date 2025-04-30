---
"description": "Tanuld meg az OLE objektumok és ActiveX vezérlők használatát az Aspose.Words for Java programban. Hozz létre interaktív dokumentumokat könnyedén. Kezdj hozzá most!"
"linktitle": "OLE objektumok és ActiveX vezérlők használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "OLE objektumok és ActiveX vezérlők használata az Aspose.Words for Java programban"
"url": "/hu/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# OLE objektumok és ActiveX vezérlők használata az Aspose.Words for Java programban

Ebben az oktatóanyagban azt vizsgáljuk meg, hogyan használhatók az OLE (Object Linking and Embedding) objektumok és az ActiveX vezérlők az Aspose.Words for Java programban. Az OLE objektumok és az ActiveX vezérlők hatékony eszközök, amelyek lehetővé teszik a dokumentumok minőségének javítását külső tartalmak, például táblázatok, multimédiás fájlok vagy interaktív vezérlők beágyazásával vagy csatolásával. Kövesd a kódpéldákat, és tanuld meg, hogyan használhatod hatékonyan ezeket a funkciókat.

### Előfeltételek

Mielőtt belekezdenénk, győződjünk meg arról, hogy a következő előfeltételek teljesülnek:

1. Aspose.Words Java-hoz: Győződjön meg róla, hogy az Aspose.Words könyvtár telepítve van a Java projektjében. Letöltheti innen: [itt](https://releases.aspose.com/words/java/).

2. Java fejlesztői környezet: Rendelkeznie kell egy működő Java fejlesztői környezettel a rendszerén.

### OLE objektum beszúrása

Kezdjük egy OLE objektum beszúrásával egy Word dokumentumba. Létrehozunk egy egyszerű Word dokumentumot, majd beszúrunk egy weboldalt reprezentáló OLE objektumot.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", igaz, igaz, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

Ebben a kódban létrehozunk egy új dokumentumot, és beszúrunk egy OLE objektumot, amely megjeleníti az Aspose webhelyet. Az URL-t lecserélhetjük a kívánt tartalomra.

### OLE objektum beszúrása OlePackage használatával

Következő lépésként nézzük meg, hogyan szúrhatunk be egy OLE objektumot egy OlePackage használatával. Ez lehetővé teszi külső fájlok beágyazását OLE objektumként a dokumentumba.

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

Ebben a példában egy OLE objektumot illesztünk be egy OlePackage használatával, amely lehetővé teszi külső fájlok beágyazott objektumként való beillesztését.

### OLE objektum beszúrása ikonként

Most nézzük meg, hogyan szúrhatunk be egy OLE objektumot ikonként. Ez akkor hasznos, ha egy beágyazott fájlt ábrázoló ikont szeretnénk megjeleníteni.

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

Ebben a kódban egy OLE objektumot illesztünk be ikonként, amely vizuálisan vonzóbbá teszi a beágyazott tartalmat.

### ActiveX-vezérlő tulajdonságainak olvasása

Most pedig térjünk át az ActiveX-vezérlőkre. Megtanuljuk, hogyan olvashatjuk be az ActiveX-vezérlők tulajdonságait egy Word-dokumentumban.

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

Ebben a kódban végigmegyünk egy Word-dokumentum alakzatain, azonosítjuk az ActiveX-vezérlőket, és lekérjük azok tulajdonságait.

### Következtetés

Gratulálunk! Megtanultad, hogyan kell OLE objektumokkal és ActiveX vezérlőkkel dolgozni az Aspose.Words for Java programban. Ezek a funkciók a lehetőségek tárházát nyitják meg előtted dinamikus és interaktív dokumentumok létrehozására.

### GYIK

### Mi az OLE objektumok célja egy Word dokumentumban? 
   - Az OLE objektumok lehetővé teszik külső tartalmak, például fájlok vagy weboldalak beágyazását vagy hivatkozását egy Word dokumentumba.

### Testreszabhatom az OLE-objektumok megjelenését a dokumentumomban? 
   - Igen, testreszabhatja az OLE-objektumok megjelenését, beleértve a beállításikonokat és a fájlneveket.

### Mik azok az ActiveX-vezérlők, és hogyan javíthatják a dokumentumaimat? 
   - Az ActiveX-vezérlők interaktív elemek, amelyek funkciókat adhatnak a Word-dokumentumokhoz, például űrlapvezérlők vagy multimédia-lejátszók.

### Alkalmas-e az Aspose.Words for Java vállalati szintű dokumentumautomatizálásra? 
   - Igen, az Aspose.Words for Java egy hatékony könyvtár a dokumentumok generálásának és kezelésének automatizálására Java alkalmazásokban.

### Hol férhetek hozzá az Aspose.Words Java-hoz? 
   - Az Aspose.Words Java-hoz letölthető innen: [itt](https://releases.aspose.com/words/java/).

Kezdje el az Aspose.Words for Java használatát még ma, és aknázza ki a dokumentumautomatizálás és -testreszabás teljes potenciálját!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}