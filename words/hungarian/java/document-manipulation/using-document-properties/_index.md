---
title: A dokumentum tulajdonságainak használata az Aspose.Words for Java programban
linktitle: A dokumentum tulajdonságainak használata
second_title: Aspose.Words Java Document Processing API
description: Optimalizálja a dokumentumkezelést az Aspose.Words for Java segítségével. Ebben az átfogó oktatóanyagban tanulja meg a dokumentumtulajdonságok kezelését, egyéni metaadatok hozzáadását és még sok mást.
weight: 32
url: /hu/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# A dokumentum tulajdonságainak használata az Aspose.Words for Java programban


## Bevezetés a dokumentumtulajdonságokba

A dokumentum tulajdonságai minden dokumentum létfontosságú részét képezik. További információkat nyújtanak magáról a dokumentumról, például a címről, a szerzőről, a tárgyról, a kulcsszavakról és egyebekről. Az Aspose.Words for Java programban mind a beépített, mind az egyéni dokumentumtulajdonságokat módosíthatja.

## Dokumentumtulajdonságok felsorolása

### Beépített tulajdonságok

beépített dokumentumtulajdonságok lekéréséhez és kezeléséhez használja a következő kódrészletet:

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

Ez a kód megjeleníti a dokumentum nevét és a beépített tulajdonságait, beleértve az olyan tulajdonságokat, mint a „Cím”, „Szerző” és „Kulcsszavak”.

### Egyedi tulajdonságok

Az egyéni dokumentumtulajdonságok kezeléséhez a következő kódrészletet használhatja:

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

Ez a kódrészlet bemutatja, hogyan adhat hozzá egyéni dokumentumtulajdonságokat, beleértve a logikai értéket, a karakterláncot, a dátumot, a változatszámot és a numerikus értéket.

## A dokumentum tulajdonságainak eltávolítása

Adott dokumentumtulajdonságok eltávolításához a következő kódot használhatja:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Ez a kód eltávolítja az "Engedélyezett dátum" egyéni tulajdonságot a dokumentumból.

## Tartalomra mutató hivatkozás konfigurálása

Bizonyos esetekben érdemes lehet hivatkozásokat létrehozni a dokumentumban. A következőképpen teheti meg:

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

    // Hivatkozás hozzáadása a tartalomtulajdonhoz.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Ez a kódrészlet bemutatja, hogyan hozhat létre könyvjelzőt a dokumentumban, és hogyan adhat hozzá egy egyéni dokumentumtulajdonságot, amely a könyvjelzőre hivatkozik.

## Konvertálás a mértékegységek között

Az Aspose.Words for Java programban egyszerűen konvertálhatja a mértékegységeket. Íme egy példa, hogyan kell csinálni:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Állítsa be a margókat hüvelykben.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Ez a kódrészlet különböző margókat és távolságokat állít be hüvelykben, pontokká alakítva azokat.

## Vezérlőkarakterek használata

A vezérlőkarakterek hasznosak lehetnek szöveg kezelésekor. A következőképpen cserélhet le egy vezérlő karaktert a szövegben:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Cserélje ki a „\r” vezérlőkaraktert „\r\n”-re.
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

Ebben a példában lecseréljük a kocsivissza (`\r`) kocsi visszatéréssel, majd soremeléssel (`\r\n`).

## Következtetés

dokumentum tulajdonságai jelentős szerepet játszanak a dokumentumok hatékony kezelésében és rendszerezésében az Aspose.Words for Java programban. Akár beépített tulajdonságokkal, akár egyéni tulajdonságokkal dolgozik, akár vezérlőkaraktereket használ, számos eszköz áll rendelkezésére a dokumentumkezelési képességek javításához.

## GYIK

### Hogyan érhetem el a beépített dokumentumtulajdonságokat?

 Az Aspose.Words for Java beépített dokumentumtulajdonságainak eléréséhez használja a`getBuiltInDocumentProperties` módszer a`Document` objektum. Ez a metódus beépített tulajdonságok gyűjteményét adja vissza, amelyeken keresztül ismételhet.

### Hozzáadhatok egyéni dokumentumtulajdonságokat egy dokumentumhoz?

 Igen, egyéni dokumentumtulajdonságokat adhat a dokumentumhoz a segítségével`CustomDocumentProperties` gyűjtemény. Különféle adattípusokkal határozhat meg egyéni tulajdonságokat, beleértve a karakterláncokat, logikai értékeket, dátumokat és numerikus értékeket.

### Hogyan távolíthatok el egy adott egyéni dokumentumtulajdonságot?

 Egy adott egyéni dokumentumtulajdonság eltávolításához használhatja a`remove` módszer a`CustomDocumentProperties`gyűjtemény, paraméterként átadva az eltávolítani kívánt tulajdonság nevét.

### Mi a célja a dokumentumon belüli tartalomra való hivatkozásnak?

A dokumentumon belüli tartalomra való hivatkozás lehetővé teszi dinamikus hivatkozások létrehozását a dokumentum bizonyos részeire. Ez hasznos lehet interaktív dokumentumok vagy szakaszok közötti kereszthivatkozások létrehozásához.

### Hogyan konvertálhatok különböző mértékegységeket az Aspose.Words for Java programban?

 Az Aspose.Words for Java programban a különböző mértékegységek között konvertálhat a`ConvertUtil` osztály. Módszereket biztosít az olyan mértékegységek konvertálására, mint a hüvelyk pontokká, a pontok centiméterekké stb.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
