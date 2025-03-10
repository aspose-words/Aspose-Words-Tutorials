---
title: Segítő módszerek az Aspose.Words for Java tartalom kinyeréséhez
linktitle: Segítő módszerek a tartalom kinyeréséhez
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan nyerhet ki hatékonyan tartalmat Word dokumentumokból az Aspose.Words for Java segítségével. Fedezze fel a segédmódszereket, az egyéni formázást és még sok mást ebben az átfogó útmutatóban.
weight: 14
url: /hu/java/document-manipulation/helper-methods-for-extracting-content/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Segítő módszerek az Aspose.Words for Java tartalom kinyeréséhez


## Bevezetés az Aspose.Words for Java tartalom kinyerésére szolgáló segédmódszerekbe

Az Aspose.Words for Java egy hatékony könyvtár, amely lehetővé teszi a fejlesztők számára, hogy programozottan dolgozzanak Word dokumentumokkal. A Word-dokumentumokkal végzett munka során az egyik gyakori feladat a tartalom kinyerése belőlük. Ebben a cikkben bemutatunk néhány segédmódszert a tartalom hatékony kibontásához az Aspose.Words for Java használatával.

## Előfeltételek

Mielőtt belemerülnénk a kódpéldákba, győződjön meg arról, hogy az Aspose.Words for Java telepítve van, és be van állítva a Java projektben. Letöltheti innen[itt](https://releases.aspose.com/words/java/).

## Segítő 1. módszer: Bekezdések kibontása stílus szerint

```java
public static ArrayList<Paragraph> paragraphsByStyleName(Document doc, String styleName) {
    // Hozzon létre egy tömböt a megadott stílusú bekezdések összegyűjtéséhez.
    ArrayList<Paragraph> paragraphsWithStyle = new ArrayList<Paragraph>();
    NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);

    // Nézze meg az összes bekezdést, hogy megtalálja azokat, amelyek a megadott stílusúak.
    for (Paragraph paragraph : (Iterable<Paragraph>) paragraphs) {
        if (paragraph.getParagraphFormat().getStyle().getName().equals(styleName))
            paragraphsWithStyle.add(paragraph);
    }
    return paragraphsWithStyle;
}
```

Ezzel a módszerrel kivonhatja azokat a bekezdéseket, amelyeknek meghatározott stílusa van a Word-dokumentumban. Ez akkor hasznos, ha meghatározott formázással, például címsorokkal vagy idézőjelekkel szeretne tartalmat kivonni.

## Segítő 2. módszer: Tartalom kinyerése csomópontok szerint

```java
public static ArrayList<Node> extractContentBetweenNodes(Node startNode, Node endNode, boolean isInclusive) {
    // Először ellenőrizze, hogy az ehhez a metódushoz átadott csomópontok használhatók-e.
    verifyParameterNodes(startNode, endNode);
    
    // Hozzon létre egy listát a kibontott csomópontok tárolására.
    ArrayList<Node> nodes = new ArrayList<Node>();

    // Ha bármelyik jelölő egy megjegyzés része, beleértve magát a megjegyzést is, mozgatnunk kell a mutatót
    // továbbítja a CommentRangeEnd csomópont után található megjegyzés csomóponthoz.
    if (endNode.getNodeType() == NodeType.COMMENT_RANGE_END && isInclusive) {
        Node node = findNextNode(NodeType.COMMENT, endNode.getNextSibling());
        if (node != null)
            endNode = node;
    }
    
    // Jegyezze fel a módszernek átadott eredeti csomópontokat, hogy szükség esetén feloszthassa a jelölőcsomópontokat.
    Node originalStartNode = startNode;
    Node originalEndNode = endNode;

    //Blokkszintű csomópontok (bekezdések és táblázatok) alapján bontsa ki a tartalmat. Keresse meg őket a szülőcsomópontokon.
    // Az első és az utolsó csomópont tartalmát felosztjuk, attól függően, hogy a marker csomópontok soron belül vannak-e.
    startNode = getAncestorInBody(startNode);
    endNode = getAncestorInBody(endNode);
    boolean isExtracting = true;
    boolean isStartingNode = true;
    // Az aktuális csomópont, amelyet a dokumentumból kinyerünk.
    Node currNode = startNode;

    // Kezdje el a tartalom kinyerését. Az összes blokkszintű csomópont feldolgozása, és az első felosztása
    // és szükség esetén az utolsó csomópontokat, így a bekezdésformázás megmarad.
    // Ez a módszer egy kicsit bonyolultabb, mint egy hagyományos elszívó, amit figyelembe kell vennünk
    // a kibontásban soron belüli csomópontok, mezők, könyvjelzők stb. használatával, hogy hasznos legyen.
    while (isExtracting) {
        // Másolat beszerzéséhez klónozza az aktuális csomópontot és gyermekeit.
        Node cloneNode = currNode.deepClone(true);
        boolean isEndingNode = currNode.equals(endNode);
        if (isStartingNode || isEndingNode) {
            // Minden jelölőt külön kell feldolgoznunk, ezért inkább adja át egy másik metódusnak.
            // A csomóponti indexek megtartásához először az Endet kell feldolgozni.
            if (isEndingNode) {
                // !isStartingNode: ne adja hozzá kétszer a csomópontot, ha a jelölők ugyanazok a csomópontok.
                processMarker(cloneNode, nodes, originalEndNode, currNode, isInclusive,
                        false, !isStartingNode, false);
                isExtracting = false;
            }
            // feltételes feltételeknek külön kell lenniük, mivel a blokkszintű kezdő- és végjelzők ugyanazok a csomópontok lehetnek.
            if (isStartingNode) {
                processMarker(cloneNode, nodes, originalStartNode, currNode, isInclusive,
                        true, true, false);
                isStartingNode = false;
            }
        } else
            // A csomópont nem kezdő vagy végjelző, egyszerűen adja hozzá a másolatot a listához.
            nodes.add(cloneNode);

        // Lépjen a következő csomópontra, és bontsa ki. Ha a következő csomópont nulla,
        // a többi tartalom egy másik részben található.
        if (currNode.getNextSibling() == null && isExtracting) {
            // Ugrás a következő szakaszra.
            Section nextSection = (Section) currNode.getAncestor(NodeType.SECTION).getNextSibling();
            currNode = nextSection.getBody().getFirstChild();
        } else {
            // Ugrás a test következő csomópontjára.
            currNode = currNode.getNextSibling();
        }
    }

    // A szövegközi könyvjelzőket tartalmazó móddal való kompatibilitás érdekében adja hozzá a következő bekezdést (üres).
    if (isInclusive && originalEndNode == endNode && !originalEndNode.isComposite())
        includeNextParagraph(endNode, nodes);

    // Állítsa vissza a csomópontokat a csomópontjelölők közé.
    return nodes;
}
```

Ez a módszer lehetővé teszi a tartalom kinyerését két megadott csomópont között, legyenek azok bekezdések, táblázatok vagy bármely más blokkszintű elem. Különféle forgatókönyveket kezel, beleértve a soron belüli jelölőket, mezőket és könyvjelzőket.

## Segítő 3. módszer: Új dokumentum generálása

```java
public static Document generateDocument(Document srcDoc, ArrayList<Node> nodes) throws Exception {
    Document dstDoc = new Document();
    
    // Távolítsa el az első bekezdést az üres dokumentumból.
    dstDoc.getFirstSection().getBody().removeAllChildren();
    
    // Importálja az egyes csomópontokat a listából az új dokumentumba. Tartsa meg a csomópont eredeti formázását.
    NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
    for (Node node : nodes) {
        Node importNode = importer.importNode(node, true);
        dstDoc.getFirstSection().getBody().appendChild(importNode);
    }
    
    return dstDoc;
}
```

Ez a módszer lehetővé teszi új dokumentum létrehozását a csomópontok listájának a forrásdokumentumból történő importálásával. Megőrzi a csomópontok eredeti formázását, így hasznos lehet új, meghatározott tartalmú dokumentumok létrehozásához.

## Következtetés

A Word dokumentumokból való tartalom kinyerése számos dokumentumfeldolgozási feladat döntő része lehet. Az Aspose.Words for Java hatékony segédmetódusokat kínál, amelyek leegyszerűsítik ezt a folyamatot. Akár stílus szerint, akár tartalom szerint kell bekezdéseket kivonnia a csomópontok között, vagy új dokumentumokat kell létrehoznia, ezek a módszerek segítenek hatékonyan dolgozni a Word-dokumentumokkal a Java-alkalmazásokban.

## GYIK

### Hogyan telepíthetem az Aspose.Words for Java programot?

 Az Aspose.Words for Java telepítéséhez letöltheti az Aspose webhelyéről. Látogatás[itt](https://releases.aspose.com/words/java/) hogy megszerezze a legújabb verziót.

### Kivonhatok tartalmat egy Word-dokumentum meghatározott szakaszaiból?

Igen, az ebben a cikkben említett módszerekkel kinyerhet tartalmat egy Word-dokumentum adott szakaszaiból. Egyszerűen adja meg a kibontandó szakaszt meghatározó kezdő és záró csomópontokat.

### Az Aspose.Words for Java kompatibilis a Java 11-gyel?

Igen, az Aspose.Words for Java kompatibilis a Java 11 és újabb verzióival. Probléma nélkül használhatja Java-alkalmazásaiban.

### Testreszabhatom a kivont tartalom formázását?

Igen, testreszabhatja a kivont tartalom formázását az importált csomópontok módosításával a generált dokumentumban. Az Aspose.Words for Java kiterjedt formázási lehetőségeket kínál az Ön igényeinek kielégítésére.

### Hol találok további dokumentációt és példákat az Aspose.Words for Java-hoz?

 Az Aspose.Words for Java-hoz átfogó dokumentációt és példákat találhat az Aspose webhelyén. Látogatás[https://reference.aspose.com/words/java/](https://reference.aspose.com/words/java/) részletes dokumentációért és forrásokért.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
