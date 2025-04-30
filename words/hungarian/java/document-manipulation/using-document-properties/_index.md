---
"description": "Optimalizálja a dokumentumkezelést az Aspose.Words for Java segítségével. Tanulja meg, hogyan kell dolgozni a dokumentumok tulajdonságaival, hogyan adhat hozzá egyéni metaadatokat és sok mást ebben az átfogó oktatóanyagban."
"linktitle": "Dokumentumtulajdonságok használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Dokumentumtulajdonságok használata az Aspose.Words Java-ban"
"url": "/hu/java/document-manipulation/using-document-properties/"
"weight": 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dokumentumtulajdonságok használata az Aspose.Words Java-ban


## Bevezetés a dokumentum tulajdonságaiba

A dokumentumtulajdonságok minden dokumentum létfontosságú részét képezik. További információkat nyújtanak magáról a dokumentumról, például a címéről, szerzőjéről, tárgyáról, kulcsszavairól és egyebekről. Az Aspose.Words for Java programban mind a beépített, mind az egyéni dokumentumtulajdonságokat módosíthatja.

## Dokumentumtulajdonságok felsorolása

### Beépített tulajdonságok

A beépített dokumentumtulajdonságok lekéréséhez és használatához a következő kódrészletet használhatja:

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

Ez a kód megjeleníti a dokumentum nevét és beépített tulajdonságait, beleértve olyan tulajdonságokat, mint a „Cím”, a „Szerző” és a „Kulcsszavak”.

### Egyéni tulajdonságok

Egyéni dokumentumtulajdonságok kezeléséhez a következő kódrészletet használhatja:

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

Ez a kódrészlet bemutatja, hogyan adhat hozzá egyéni dokumentumtulajdonságokat, beleértve a logikai értéket, a karakterláncot, a dátumot, a verziószámot és a numerikus értéket.

## Dokumentumtulajdonságok eltávolítása

Adott dokumentumtulajdonságok eltávolításához a következő kódot használhatja:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Ez a kód eltávolítja az „Engedélyezés dátuma” egyéni tulajdonságot a dokumentumból.

## Tartalomra mutató hivatkozás konfigurálása

Bizonyos esetekben érdemes lehet hivatkozásokat létrehozni a dokumentumon belül. Így teheti meg:

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Tartalomhoz kapcsolt tulajdonság hozzáadása.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Ez a kódrészlet bemutatja, hogyan hozhat létre könyvjelzőt a dokumentumában, és hogyan adhat hozzá egy egyéni dokumentumtulajdonságot, amely erre a könyvjelzőre hivatkozik.

## Mértékegységek közötti átváltás

Az Aspose.Words Java-ban könnyedén átválthatsz mértékegységekre. Íme egy példa arra, hogyan teheted meg:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Margók beállítása hüvelykben.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Ez a kódrészlet különböző margókat és távolságokat állít be hüvelykben, pontokká konvertálva azokat.

## Vezérlőkarakterek használata

A vezérlőkarakterek hasznosak lehetnek szöveg kezelésekor. Így cserélhet le egy vezérlőkaraktert a szövegben:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Cserélje ki az „\r” vezérlőkaraktert „\r\n”-re.
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

Ebben a példában a kocsivissza karaktert (`\r`) kocsivissza karakterrel, majd soremeléssel (`\r\n`).

## Következtetés

dokumentumtulajdonságok jelentős szerepet játszanak a dokumentumok hatékony kezelésében és rendszerezésében az Aspose.Words for Java programban. Akár beépített tulajdonságokkal, akár egyéni tulajdonságokkal, akár vezérlőkarakterekkel dolgozik, számos eszköz áll rendelkezésére a dokumentumkezelési képességek fejlesztéséhez.

## GYIK

### Hogyan férhetek hozzá a beépített dokumentumtulajdonságokhoz?

Az Aspose.Words for Java beépített dokumentumtulajdonságainak eléréséhez használhatja a következőt: `getBuiltInDocumentProperties` módszer a `Document` objektum. Ez a metódus beépített tulajdonságok gyűjteményét adja vissza, amelyeken keresztül iterálhatsz.

### Hozzáadhatok egyéni dokumentumtulajdonságokat egy dokumentumhoz?

Igen, hozzáadhat egyéni dokumentumtulajdonságokat egy dokumentumhoz a használatával. `CustomDocumentProperties` gyűjtemény. Egyéni tulajdonságokat definiálhat különféle adattípusokkal, beleértve a karakterláncokat, logikai értékeket, dátumokat és numerikus értékeket.

### Hogyan távolíthatok el egy adott egyéni dokumentumtulajdonságot?

Egy adott egyéni dokumentumtulajdonság eltávolításához használhatja a `remove` módszer a `CustomDocumentProperties` gyűjtemény, paraméterként átadva az eltávolítani kívánt tulajdonság nevét.

### Mi a célja a dokumentumon belüli tartalomra mutató hivatkozásoknak?

A dokumentumon belüli tartalomra való hivatkozás lehetővé teszi dinamikus hivatkozások létrehozását a dokumentum adott részeire. Ez hasznos lehet interaktív dokumentumok vagy szakaszok közötti kereszthivatkozások létrehozásához.

### Hogyan tudok különböző mértékegységek között váltani az Aspose.Words for Java programban?

Az Aspose.Words for Java programban a következőképpen válthat a mértékegységek között: `ConvertUtil` osztály. Metódusokat biztosít olyan mértékegységek átváltoztatására, mint a hüvelyk pontokká, a pontok centiméterekké és egyebek.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}