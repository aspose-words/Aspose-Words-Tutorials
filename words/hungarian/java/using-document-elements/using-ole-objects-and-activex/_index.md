---
title: OLE-objektumok és ActiveX-vezérlők használata az Aspose.Words for Java-ban
linktitle: OLE-objektumok és ActiveX-vezérlők használata
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg az OLE objektumok és ActiveX-vezérlők használatát az Aspose.Words for Java programban. Könnyedén hozhat létre interaktív dokumentumokat. Kezdje el most!
weight: 21
url: /hu/java/using-document-elements/using-ole-objects-and-activex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# OLE-objektumok és ActiveX-vezérlők használata az Aspose.Words for Java-ban

Ebben az oktatóanyagban megvizsgáljuk, hogyan dolgozhatunk OLE (Object Linking and Embedding) objektumokkal és ActiveX-vezérlőkkel az Aspose.Words for Java programban. Az OLE-objektumok és az ActiveX-vezérlők hatékony eszközök, amelyek lehetővé teszik a dokumentumok fejlesztését külső tartalom, például táblázatok, multimédiás fájlok vagy interaktív vezérlők beágyazásával vagy összekapcsolásával. Kövesse a példákat a kódpéldákban, és tanulja meg, hogyan kell ezeket a funkciókat hatékonyan használni.

### Előfeltételek

Mielőtt elkezdené, győződjön meg arról, hogy a következő előfeltételek teljesülnek:

1.  Aspose.Words for Java : Győződjön meg arról, hogy az Aspose.Words könyvtár telepítve van a Java projektben. Letöltheti innen[itt](https://releases.aspose.com/words/java/).

2. Java fejlesztői környezet: A rendszeren be kell állítani egy működő Java fejlesztői környezetet.

### OLE objektum beszúrása

Kezdjük egy OLE objektum beszúrásával egy Word dokumentumba. Létrehozunk egy egyszerű Word-dokumentumot, majd beillesztünk egy weboldalt képviselő OLE-objektumot.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlfile", true, true, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

Ebben a kódban létrehozunk egy új dokumentumot, és beillesztünk egy OLE objektumot, amely megjeleníti az Aspose webhelyet. Az URL-t lecserélheti a kívánt tartalomra.

### OLE objektum beszúrása OlePackage segítségével

Ezután vizsgáljuk meg, hogyan lehet OLE-objektumot beszúrni az OlePackage használatával. Ez lehetővé teszi külső fájlok beágyazását OLE objektumként a dokumentumba.

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

Ebben a példában egy OlePackage használatával szúrunk be egy OLE objektumot, amely lehetővé teszi külső fájlok beágyazott objektumként való felvételét.

### OLE objektum beszúrása ikonként

Most nézzük meg, hogyan illeszthetünk be egy OLE objektumot ikonként. Ez akkor hasznos, ha egy beágyazott fájlt jelképező ikont szeretne megjeleníteni.

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

Ebben a kódban egy OLE objektumot illesztünk be ikonként, amely a beágyazott tartalom tetszetősebb megjelenítését biztosítja.

### Az ActiveX-vezérlő tulajdonságainak olvasása

Most helyezzük át a hangsúlyt az ActiveX-vezérlőkre. Megtanuljuk, hogyan kell beolvasni az ActiveX-vezérlők tulajdonságait egy Word-dokumentumban.

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

Ebben a kódban egy Word-dokumentumban lévő alakzatokat iteráljuk, azonosítjuk az ActiveX-vezérlőket, és lekérjük azok tulajdonságait.

### Következtetés

Gratulálok! Megtanulta, hogyan kell OLE-objektumokkal és ActiveX-vezérlőkkel dolgozni az Aspose.Words for Java programban. Ezek a funkciók a lehetőségek világát nyitják meg dinamikus és interaktív dokumentumok létrehozásához.

### GYIK

### Mi a célja az OLE-objektumoknak egy Word-dokumentumban? 
   - Az OLE-objektumok lehetővé teszik külső tartalom, például fájlok vagy weboldalak beágyazását vagy hivatkozását egy Word-dokumentumba.

### Testreszabhatom az OLE objektumok megjelenését a dokumentumban? 
   - Igen, testreszabhatja az OLE-objektumok megjelenését, beleértve az ikonok és fájlnevek beállítását.

### Mik azok az ActiveX-vezérlők, és hogyan javíthatják a dokumentumaimat? 
   - Az ActiveX-vezérlők olyan interaktív elemek, amelyek funkcionalitást adhatnak a Word-dokumentumokhoz, például űrlapvezérlők vagy multimédia-lejátszók.

### Az Aspose.Words for Java alkalmas vállalati szintű dokumentumautomatizálásra? 
   - Igen, az Aspose.Words for Java egy hatékony könyvtár a dokumentumgenerálás és -kezelés automatizálására Java alkalmazásokban.

### Hol férhetek hozzá az Aspose.Words for Java-hoz? 
   -  Az Aspose.Words for Java letölthető innen:[itt](https://releases.aspose.com/words/java/).

Kezdje el az Aspose.Words for Java használatát még ma, és aknázza ki a dokumentumok automatizálásában és testreszabásában rejlő lehetőségeket!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
