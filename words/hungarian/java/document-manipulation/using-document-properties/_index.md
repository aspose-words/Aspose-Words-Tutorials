---
date: 2026-01-16
description: Tanulja meg, hogyan konvertálja a hüvelyket pontokra, olvassa el a dokumentum
  metaadatait Java‑ban, adjon hozzá egyéni tulajdonságokat Java‑ban, és állítsa be
  az oldalmargókat Java‑ban az Aspose.Words for Java segítségével.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Átváltás hüvelykből pontokra – Dokumentumtulajdonságok használata az Aspose.Words
  for Java-ban
url: /hu/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hüvelyk pontokra konvertálása – Dokumentumtulajdonságok használata az Aspose.Words for Java-ban

Ebben az útmutatóban megtudja, hogyan **konvertálhatja a hüvelyket pontokra** oldalmargók beállításakor, hogyan olvashatja a dokumentum metaadatait Java-ban, hogyan adhat hozzá egyéni tulajdonságokat Java-ban, és hogyan dolgozhat beépített dokumentumtulajdonságokkal az Aspose.Words for Java használatával. Akár jelentéseket, számlákat vagy jogi dokumentumokat generál, ezen technikák elsajátítása finomhangolt irányítást biztosít a Word-fájlok megjelenése és metaadatai felett.

## Gyors válaszok
- **Hogyan konvertálhatom a hüvelyket pontokra?** Használja az `ConvertUtil.inchToPoint(value)` metódust az Aspose.Words-ból.  
- **Olvashatok dokumentum metaadatokat Java-ban?** Igen – hívja a `doc.getBuiltInDocumentProperties()` vagy a `doc.getCustomDocumentProperties()` metódust.  
- **Hogyan adhatok hozzá egy egyéni tulajdonságot Java-ban?** Használja a `doc.getCustomDocumentProperties().add(name, value)` metódust.  
- **Melyik metódus állítja be az oldalmargókat pontokban?** A `PageSetup.setTopMargin`, `setBottomMargin` stb. metódusok pont értékeket fogadnak.  
- **Támogatott a könyvjelzőhöz való linkelés?** Igen – használja az `addLinkToContent` metódust az egyéni tulajdonságok gyűjteményén.

## Dokumentumtulajdonságok bevezetése

Dokumentumtulajdonságok minden Word-fájl létfontosságú részei. Információkat tárolnak, mint például cím, szerző, tárgy, kulcsszavak, valamint bármilyen egyéni metaadat, amelyre a további feldolgozáshoz szükség van. Az Aspose.Words for Java-ban manipulálhatja a beépített és az egyéni dokumentumtulajdonságokat, és a layout részleteket is szabályozhatja, például margókat, a mértékegységek konvertálásával (pl. **convert inches to points**).

## Mi az a „convert inches to points”?

A Wordben a layout mérései pontokban vannak kifejezve (1 pont = 1/72 hüvelyk). A hüvelyk pontokra konvertálása lehetővé teszi, hogy margókat, behúzásokat és távolságokat ismerős angolszász egységek használatával definiáljon, miközben az API belsőleg pontokkal dolgozik.

## Miért kezeljük a dokumentum metaadatait Java-ban?

A metaadatok beágyazása megkönnyíti a keresést, a kategorizálást és az automatizált munkafolyamatokat. Például egy szerződéshez hozzáadhat egy „Authorized” jelzőt, vagy tárolhat egy revíziószámot az audit nyomvonalakhoz. A metaadatok programozott olvasása és írása biztosítja a konzisztenciát nagy dokumentumkészletek esetén.

## Előfeltételek
- Java 17+ (vagy kompatibilis JDK)
- Aspose.Words for Java könyvtár hozzáadva a projekthez (Maven/Gradle)
- Egy minta `.docx` fájl (pl. `Properties.docx`) egy elérhető könyvtárban elhelyezve

## Lépésről‑lépésre útmutató

### Beépített dokumentumtulajdonságok felsorolása

Az alábbi egyszerű teszt megnyit egy dokumentumot, és kiírja az összes beépített tulajdonságot, például a Címet, a Szerzőt és a Kulcsszavakat.

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

> **Pro tipp:** Használja ezt a kódrészletet annak ellenőrzésére, hogy a metaadatai helyesen íródtak‑e a korábbi lépések során.

### Egyéni dokumentumtulajdonságok hozzáadása (add custom properties java)

Az egyéni tulajdonságok lehetővé teszik bármilyen szükséges adattípus tárolását – boolean, string, date, number stb.

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

> **Miért fontos:** Egy **Authorized** jelző hozzáadása elősegítheti a további jóváhagyási munkafolyamatokat anélkül, hogy módosítaná a dokumentum tartalmát.

### Egyéni tulajdonság eltávolítása

Ha egy tulajdonság már nincs szükség, tisztán törölheti.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Tartalomra mutató link beállítása (könyvjelző hivatkozás)

Létrehozhat egy könyvjelzőt, majd egy olyan egyéni tulajdonságot adhat hozzá, amely erre a könyvjelzőre mutat, ezáltal dinamikus kereszt‑hivatkozásokat tesz lehetővé.

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

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Mértékegységek közti konvertálás (oldalmargók beállítása java)

Itt jön a kulcsszó szerepe. Margókat hüvelykben állítunk be, majd a `ConvertUtil` segítségével **convert inches to points**.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Megjegyzés:** A `ConvertUtil` további módszereket is kínál, mint a `pointToInch`, `mmToPoint` stb., a rugalmas elrendezéskezeléshez.

### Vezérlőkarakterek használata (read document metadata java)

A vezérlőkarakterek segítenek a szövegfolyamok tisztításában. Ez a példa a carriage‑return (`\r`) karaktert a Windows sortörés szekvenciára (`\r\n`) cseréli.

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Gyakori problémák és megoldások

| Probléma | Ok | Megoldás |
|----------|----|----------|
| A margók hibásan jelennek meg a konvertálás után | Rossz mértékegység használata (pl. cm a hüvelyk helyett) | Ellenőrizze, hogy hüvelyk értékekhez a `ConvertUtil.inchToPoint` metódust hívja |
| Az egyéni tulajdonság nem jelenik meg | A tulajdonság a dokumentum mentése után lett hozzáadva | Hívja a `doc.save(...)` metódust a tulajdonságok hozzáadása után |
| A könyvjelző hivatkozás hibás | Könyvjelző név elírás | Győződjön meg róla, hogy a könyvjelző neve pontosan megegyezik az `addLinkToContent` hívásban |

## Gyakran ismételt kérdések

### Hogyan érhetem el a beépített dokumentumtulajdonságokat?

A beépített dokumentumtulajdonságok eléréséhez az Aspose.Words for Java-ban használja a `getBuiltInDocumentProperties` metódust a `Document` objektumon. Ez a metódus egy gyűjteményt ad vissza a beépített tulajdonságokból, amelyet végigiterálhat.

### Hozzáadhatok egyéni dokumentumtulajdonságokat egy dokumentumhoz?

Igen, egyéni dokumentumtulajdonságokat a `CustomDocumentProperties` gyűjteményen keresztül adhat hozzá. Különböző adattípusok definiálhatók, beleértve a stringeket, boolean értékeket, dátumokat és numerikus értékeket.

### Hogyan távolíthatok el egy konkrét egyéni dokumentumtulajdonságot?

Egy adott egyéni dokumentumtulajdonság eltávolításához használja a `remove` metódust a `CustomDocumentProperties` gyűjteményen, a tulajdonság nevét paraméterként megadva.

### Mi a célja a dokumentumon belüli tartalomra való hivatkozásnak?

A dokumentumon belüli tartalomra való hivatkozás dinamikus referenciákat hoz létre a dokumentum egyes részeihez. Ez hasznos interaktív dokumentumok vagy szekciók közötti kereszt‑hivatkozások létrehozásához.

### Hogyan konvertálhatok különböző mértékegységek között az Aspose.Words for Java-ban?

A különböző mértékegységek közti konvertáláshoz használja a `ConvertUtil` osztályt. Ez biztosít metódusokat, például hüvelyk pontokra, pont centiméterre és egyebek konvertálásához.

## Gyakran feltett kérdések

**Q: Hogyan olvashatom a dokumentum metaadatait Java-ban anélkül, hogy az egész fájlt betölteném?**  
A: Használja a `DocumentInfo` osztályt a főbb tulajdonságok lekéréséhez anélkül, hogy a dokumentum teljes tartalmát betöltené.

**Q: Programozottan beállíthatom a már meglévő dokumentumok oldalmargóit Java-ban?**  
A: Igen – nyissa meg a dokumentumot, módosítsa a `PageSetup` margókat (szükség esetén konvertálja a hüvelyket pontokra), majd mentse.

**Q: Lehetséges a egyéni tulajdonságok exportálása PDF metaadatokként?**  
A: PDF-be mentéskor az Aspose.Words automatikusan leképezi az egyéni dokumentumtulajdonságokat a PDF egyéni metaadataira.

**Q: Befolyásolják a vezérlőkarakterek a PDF konvertálást?**  
A: A konvertálás során megmaradnak; azonban a konzisztencia érdekében érdemes lehet normalizálni a sortöréseket.

**Q: Mely Aspose.Words verzió szükséges a `ConvertUtil` használatához?**  
A: A `ConvertUtil` már az Aspose.Words 16.5 verziótól elérhető; bármely újabb verzió támogatja.

## Összegzés

A **convert inches to points**, a dokumentum metaadatok Java-ban történő olvasása és az egyéni tulajdonságok Java-ban való hozzáadása elsajátításával teljes irányítást nyer a Word-fájlok vizuális elrendezése és rejtett adatai felett. Ezek a lehetőségek lehetővé teszik automatizált dokumentumcsővezetékek kiépítését, a megfelelőség érvényesítését és gazdag formázású jelentések létrehozását – mindezt az Aspose.Words for Java segítségével.

---

**Utolsó frissítés:** 2026-01-16  
**Tesztelve:** Aspose.Words for Java 24.11  
**Szerző:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}